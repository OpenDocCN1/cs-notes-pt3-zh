# 【Amazon Web Services】AWS云基础 ｜ The ABCs of AWS： Learn the Basics of the AWS Cloud p01 01_01_02_a-is-for-amazon-api-gateway -BV1MnrHBCEmT_p1-

I'm kicking off a new series AWS ABcs and today we're starting with A So let's talk about Amazon API gateway。

 What is Amazon API gateateway。 This is a fully managed serverless service where you can create publish。

 maintain and host your As on AWS It offers support for different types of APIs like HttP APIs。

 rest APIs and web sockets It offers integrations with many different backend AWS services but one very common integration that I see is integrating with an AWS Lambda function so you confront your AW Lambda function with A gateway and allow people to invoke that Lambda function through API gateway as far as security goes there are different ways you can secure your APIs It supports API keys it supports using different authorizers like coognito or a custom AW Lambda authorizer or you can use IAM authorization through the use of IEM roles。

 for example。

![](img/90d7483e7305e07edf6fdf817d4cb37d_1.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_2.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_3.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_4.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_5.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_6.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_7.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_8.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_9.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_10.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_11.png)

I a fully managed service， which means that the scalability of the service is built in and you don't need to do anything to scale it up and down besides managing your quotas。

 There are certain things you can set up for throttling APIs and you also have quotas within your account that determines how many concurrent API calls can be made you can turn those dials a little bit but the underlying scalability of this services managed by AWS whenever you're making changes to your API gateway you deploy it to what are called stages stages could point to different environments like production QA development it could also host multiple versions of your As in parallel so if you have multiple API consumers that need different versions you can have those hosted in different stages and it also supports you doing things like canary releases also through the use of stages then for monitoring A gateway does integrate with cloudwatch as well as Xr so that you have good insights into what's going on with your APIs right that's a very quick rundown for Amazon API gateway and for this AWS ABc series。



![](img/90d7483e7305e07edf6fdf817d4cb37d_13.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_14.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_15.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_16.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_17.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_18.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_19.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_20.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_21.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_22.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_23.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_24.png)

We want it to be just a quick way for you to become familiar with the AWS services that exist so for the next video we have B follow along if you want to learn more about AWS。



![](img/90d7483e7305e07edf6fdf817d4cb37d_26.png)

![](img/90d7483e7305e07edf6fdf817d4cb37d_27.png)