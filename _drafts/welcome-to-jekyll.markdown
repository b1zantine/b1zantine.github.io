---
layout: post
title:  "Welcome to Jekyll!"
description: This is the first blog post using jekyll
date:   2013-11-10 10:18:00
categories: Thriller Comedy Horror
---

You'll find this post in your `_posts` directory - edit this post and re-build (or run with the `-w` switch) to see your changes!
To add new posts, simply add a file in the `_posts` directory that follows the convention: YYYY-MM-DD-name-of-post.ext.
#### Blockquote
<blockquote><p>This is a paragraph blockquote</p></blockquote>
<blockquote><cite>This is a cite blockquote</cite></blockquote>
<blockquote><p>A great philosopher once said to keep things tidy.</p><small>Small Tag</small></blockquote>
> Markdown blockquote

___

We are right now inside the <mark>mark</mark> tag.

To copy this line use <kbd>Ctrl+C</kbd> shortcut?

---

#### Images

<figure>
 <img class="small-img" src="../../assets/images/profile.jpg" alt="Image of author">
 <figcaption>.small-img - A close-up view of the author :)</figcaption>
</figure>  

<figure>
 <img class="med-img" src="../../assets/images/profile.jpg" alt="Image of author">
 <figcaption>.med-img - A close-up view of the author :)</figcaption>
</figure>  

<figure>
 <img class="full-img" src="../../assets/images/reading.jpg" alt="Book Reading"/>
 <figcaption>.full-img</figcaption>
</figure>   



***

<script src="https://gist.github.com/lxr3000/a777e3df2c36aecc71ef64ee5a0dfac8.js"></script>

#### Table

<table>
 <caption>HTML Table</caption>
 <tr>
   <th>Month</th>
   <th>Savings</th>
 </tr>
 <tr>
   <td>January</td>
   <td>$100</td>
 </tr>
 <tr>
   <td>February</td>
   <td>$50</td>
 </tr>
</table>

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

***

#### Code

<code>hello</code> or `code`

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Checking markdown code highlight support
{% highlight python %}
def hello():
  pass
{% endhighlight %}

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll's GitHub repo][jekyll-gh].

[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
