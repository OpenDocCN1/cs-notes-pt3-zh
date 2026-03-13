# 【Amazon Web Services】AWS云基础 ｜ The ABCs of AWS： Learn the Basics of the AWS Cloud p07 02_01_01_g-is-for-aws-glue -BV1MnrHBCEmT_p7-

![](img/b6dc23cfc95f820d5c46840337b97bdc_0.png)

This is AWS ABcs where we cover a different AWS service for every letter of the alphabet。

 Today's letter is G and the service is AWS glue AWS glue is a serverless data integration service that has a lot of the different data integration capabilities that you need to complete tasks related to big data and data analytics these data integration capabilities include things like data discovery。

 creating and running ETL or ELT jobs， data cleansing data transformation and centralized cataloging for your data data is often scattered across many different sources so to effectively analyze this data it's common to use ETL or ELT processes to create a unified view of this data and to improve data quality before analysis So what is ETL ETL stands for extract transform and load The first step for ETL is to extract the data from the relevant sources Once the data is extract。



![](img/b6dc23cfc95f820d5c46840337b97bdc_2.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_3.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_4.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_5.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_6.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_7.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_8.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_9.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_10.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_11.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_12.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_13.png)

It's staged somewhere like Amazon S3， for example， which is a commonly used AWS service for these storage layer for data lakes The data is then modified or transformed into a more consumable format for data analysis tools like Amazon Quickite Amazon Athena or Amazon EMR then finally data is loaded into a target database or data warehouse for analysis and reporting ELT is a very similar process except that the data is loaded into the target and then transformed at a later date when it's needed you can create AWS glue jobs to automate the work that is required for this movement and of your data to effectively organize and use data at scale you'll want to catalog this data so that you know what you have and what you can work with there is the AWS glue data catalog for this purpose This is a centralized hub for metadata about your data the AWS glue data catalog can be used to guide operation。



![](img/b6dc23cfc95f820d5c46840337b97bdc_15.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_16.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_17.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_18.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_19.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_20.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_21.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_22.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_23.png)

Like transforming your data before performing analysis on it AWS glue jobs really shines when it comes to transforming your data and you'll need some sort of code or script to do this part AWS glue can generate the script for you or you can provide the script yourself you can also use AWS glue studio where you can visually compose and run data transformation workflows you can choose from a variety of data sources and targets in AWS glue Studio and you can then prepare that data for data analysis in data lakes or data warehouses One example of a data transformation is let's say you have a cv file in Amazon S3 that you want to transform into a columnar format that can then be stored in Amazon Redshift This type of process you can handle with AWS glue jobs Once all of the pieces are in place in AWS glue you are then ready to kick off your ETL job you can run it on demand you can set up triggers to run it whenever。



![](img/b6dc23cfc95f820d5c46840337b97bdc_25.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_26.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_27.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_28.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_29.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_30.png)

![](img/b6dc23cfc95f820d5c46840337b97bdc_31.png)