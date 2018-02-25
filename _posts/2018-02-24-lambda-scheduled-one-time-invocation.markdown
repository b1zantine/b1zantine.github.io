---
layout: post
title:  "How To: Schedule a one-time invocation of an AWS Lambda function."
description: A simple and elegant approach to invoke a Lambda function only once at the scheduled time.
date:   2018-02-24 10:18:00
categories: HowTo AWS Lambda StepFunctions
---

AWS Lambda supports Event-Driven Model when it comes to invoking a function. Lambda functions can be considered like a Callback function (handler) in a JavaScript Code which is invoked upon some event like a mouse button click, a user scrolling the page down and such. In case of AWS, an event could be something like an object uploaded to an S3 bucket, Termination of an EC2 instance and so on. A Lambda function could be triggered (invoked) whenever such an event occurs. This is made possible through AWS CloudWatch. AWS Cloudwatch can be used to invoke a Lambda function when any such event occurs in your AWS Account. 

In addition to this, AWS CloudWatch can also be used to set up `cron` jobs in the cloud. This feature helps a Lambda function to be invoked periodically, say every five mins. 

Wait, but how do you schedule a job to invoke the Lambda function only once ??

<a href="https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html" target="_blank">AWS Step Functions</a> to the rescue.  AWS Step Functions helps you orchestrate the tasks using the serverless approach. You can build your workflow which consists of states and initiate an execution. AWS Step Functions can be considered a simplified version Amazon SWF.


Following is the approach to creating a state machine using Step Functions to schedule an invocation of a Lambda function. 

---

1. Create a State Machine [2] with two states. 

    * First state (CountDownTimer) is a "Wait" state, which waits for the specified amount of time and calls the next state (State B)

    * Second state (InvokeLambda) is a "Task" state, which invokes a Lambda.

2. Execute the State Machine any number of times with the "Timestamp" as the input.

---

Following are the Amazon States Language (ASL) (schedule-lambda-asl.json) for creating a State Machine and the input (schedule-lambda-input.json) to its execution.

<script src="https://gist.github.com/SudarAbisheck/aac585776c344343b87b544411fb83c5.js"></script>

<blockquote>
    <cite>
    Note: 
    <ol>
        <li> Replace the <mark>Resource</mark> field value with your Lambda ARN.</li>
        <li> Mention the <mark>invocationTime</mark> value in UTC.</li>
    </ol>
    </cite>
</blockquote>


To create a state machine, execute the following the command using AWS CLI.
{% highlight bash %}
aws stepfunctions create-state-machine --name OneTimeLambdaScheduler --definition file://schedule-lambda-asl.json --role-arn ROLE_ARN --region us-east-1
{% endhighlight %}

On successful execution, this command creates a state machine named **OneTimeLambdaScheduler** and returns the `stateMachineArn` of it. Copy the `stateMachineArn` value. 

To schedule the invocation, you have to create a new execution of the State Machine we just created using the following command.
{% highlight bash %}
aws stepfunctions start-execution --state-machine-arn STATE_MACHINE_ARN --input file://schedule-lambda-input.json --region us-east-1
{% endhighlight %}


That's it. Your Lambda function will be triggered once at the specified time.
