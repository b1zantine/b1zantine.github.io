---
layout: section
title: EDA - Data Sourcing and Cleaning
home: pgdmlai-notes
---

---
### Data Sourcing

To solve a business problem using analytics, you need to have historical data. Data is the key — the better the data, the more insights you can get out of it. Typically, data comes from various sources and as the first task before doing analysis work is to procure the data from them.

There are two major kinds of data which can be classified according to the source:

1. Public data
2. Private data

A large amount of data collected by the government or other public agencies is made public for the purposes of research. Such data sets do not require special permission for access and are therefore called public data.

On the other hand, private data is that which is sensitive to organisations and is thus not available in the public domain. Banking, telecom, retail, and media are some of the key private sectors that rely heavily on data to make decisions.


Public datasets:

- https://github.com/awesomedata/awesome-public-datasets
- https://data.gov.in
- http://censusindia.gov.in/
- https://github.com/datameet

---

### Data Cleaning

Once you have procured the data, the next step is to clean it to get rid of data quality issues. There are various types of quality issues when it comes to data, and that’s why data cleaning is one of the most time-consuming steps of data analysis. For example, there could be formatting errors (e.g. rows and columns are ill-formatted, unclearly named etc.), missing values, repeated rows, spelling inconsistencies etc. These issues could make it difficult to analyse data and could lead to errors or irrelevant results. Thus, these issues need to be corrected before data is analysed.


There is no **single structured process** for cleaning the data. However, these are some of the steps usually involved in data cleaning.

1. [Fix rows and columns](#fixing-rows-and-columns)
2. [Fix missing values](#treating-missing-values)
3. [Standardise values](#standardizing-values)
4. [Fix invalid values](#fixing-invalid-values)
5. [Filter data](#filtering-data)

> <mark>Data Cleaning Checklist</mark> :  [__Download__](../assets/Data+Cleaning+_+Checklist.xlsx)


#### Fixing Rows and Columns

**_Checklist for Fixing Rows :_**

* __Delete summary rows:__ *Total, Subtotal rows*
* __Delete incorrect rows:__ *Header rows, Footer rows*
* __Delete extra rows:__ *Column number, indicators, Blank rows, Page No.*


**_Checklist for Fixing Columns :_**

* __Merge columns for creating unique identifiers if needed:__ *E.g. Merge State, City into Full address*
* __Split columns for more data:__ *Split address to get State and City to analyse each separately*
* __Add column names:__ *Add column names if missing*
* __Rename columns consistently:__ *Abbreviations, encoded columns*
* __Delete columns:__ *Delete unnecessary columns*
* __Align misaligned columns:__ *Dataset may have shifted columns*


#### Treating Missing Values


* __Set values as missing values:__ *Identify values that indicate missing data, and yet are not recognised by the software as such, e.g treat blank strings, "NA", "XX", "999", etc. as missing.*

* __Adding is good, exaggerating is bad:__ *You should try to get information from reliable external sources as much as possible, but if you can’t, then it is better to keep missing values as such rather than exaggerating the existing rows/columns.*

* __Delete rows, columns:__ *Rows could be deleted if the number of missing values are insignificant in number, as this would not impact the analysis. Columns could be removed if the missing values are quite significant in number.*

* __Fill partial missing values using business judgement:__ *Missing time zone, century, etc. These values are easily identifiable.*

Additional Reading:
1. [Working with missing data in Python](https://pandas.pydata.org/pandas-docs/stable/missing_data.html){:target="_blank"}

#### Standardizing values

* Checklist for standarising numbers:

    * __Standardise units:__ *Ensure all observations under a variable have a common and consistent unit, e.g. convert lbs to kgs, miles/hr to km/hr, etc.*

    * __Scale values if required:__  *Make sure the observations under a variable have a common scale*

    * __Standardise precision__ *for better presentation of data, e.g. 4.5312341 kgs to 4.53 kgs.*

    * __Remove outliers:__ *Remove high and low values that would disproportionately affect the results of your analysis.*


* Checklist for standardising text:

    * __Remove extra characters__ *like such as common prefix/suffix, leading/trailing/multiple spaces, etc. These are irrelevant to analysis.*

    * __Standardise case:__ *There are various cases that string variables may take, e.g. UPPERCASE, lowercase, Title Case, Sentence case, etc.*

    * __Standardise format:__ *E.g. 23/10/16 to 2016/10/20, “Modi, Narendra" to “Narendra Modi", etc.*


Additional Reading:
* [Why Outlier treatment is required](http://r-statistics.co/Outlier-Treatment-With-R.html){:target="_blank"}


#### Fixing Invalid Values

* __Encode unicode properly:__ *In case the data is being read as junk characters, try to change encoding, E.g. CP1252 instead of UTF-8.*

* __Convert incorrect data types:__ *Correct the incorrect data types to the correct data types for ease of analysis. E.g. if numeric values are stored as strings, it would not be possible to calculate metrics such as mean, median, etc. Some of the common data type corrections are — string to number: "12,300" to “12300”; string to date: "2013-Aug" to “2013/08”; number to string: “PIN Code 110001” to "110001"; etc.*

* __Correct values that go beyond range:__ *If some of the values are beyond logical range, e.g. temperature less than -273° C (0° K), you would need to correct them as required. A close look would help you check if there is scope for correction, or if the value needs to be removed.*

* __Correct values not in the list:__ *Remove values that don’t belong to a list. E.g. In a data set containing blood groups of individuals, strings “E” or “F” are invalid values and can be removed.*

* __Correct wrong structure:__ *Values that don’t follow a defined structure can be removed. E.g. In a data set containing pin codes of Indian cities, a pin code of 12 digits would be an invalid value and needs to be removed. Similarly, a phone number of 12 digits would be an invalid value.*

* __Validate internal rules:__ *If there are internal rules such as a date of a product’s delivery must definitely be after the date of the order, they should be correct and consistent.*

#### Filtering Data

* __Deduplicate data:__ *Remove identical rows, remove rows where some columns are identical*

* __Filter rows:__ *Filter by segment, filter by date period to get only the rows relevant to the analysis
Filter columns: Pick columns relevant to the analysis*

* __Aggregate data:__ *Group by required keys, aggregate the rest*