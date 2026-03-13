# 【Amazon Web Services】AWS云基础 ｜ The ABCs of AWS： Learn the Basics of the AWS Cloud p12 03_01_01_l-is-for-aws-lambda -BV1MnrHBCEmT_p12-

This is AWS ABCs。 Today's letter is L， and the service we'll be covering is AWS Lambda。

 AWS Lambda is a serverless compute service that allows you to run code for virtually any type of application or backend without having to provision and manage servers Now that was a pretty broad definition so let's go ahead and get into some specifics when using AWs Lada you create what are called AWs Lambda functions these functions contain your code and they run in response to events or triggers This means that Lambda functions don't run your code all over the time like you would see with an application being hosted somewhere like Amazon E C2 Instead。

 your code runs in response to events so it only runs when you need it to run Lambda functions can run for a max duration of up to 15 minutes。

 you can configure the timeout for your functions from anywhere between one second up to 15 minutes you can run file processing application。



![](img/6976cf488686c0fa7da8fdbcb1869055_1.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_2.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_3.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_4.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_5.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_6.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_7.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_8.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_9.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_10.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_11.png)

Web application backends， event processing logic and so much more on AWS Lambda。

 The thing about Lambda code is that it's actually your code and it's just packaged in a way that AWS Lambda can use So that's why we say that you can run virtually any type of application on Lambda So what languages does AWS Lada support。

 Well， there's a long list but a few examples are Python no Js or Java or if you want to use a language that isn't supported by an existing runtime in AWS Lada。

 you can provide your own runtime。 So you really have flexibility here on what language you want to use when you're creating your functions。

 your code must include something called a handler which is essentially the entry point for where your codes going to start to run once it's been invoked when you create a Lada function you also need to choose a trigger。

 This is where you can figure where exactly these events are going to be coming from this。



![](img/6976cf488686c0fa7da8fdbcb1869055_13.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_14.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_15.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_16.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_17.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_18.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_19.png)

Could be an API call being made through Amazon API gateway。

 It could be an event happening an Amazon S3 or an event that's being filtered through Amazon eventbri or it could be data being streamed through Amazon kesis just as a few examples Now once your Lambda function has been invoked the AWs Lambda service will spin up your code and run it in something called an execution environment execution environment provides a secure and isolated runtime environment for your Lambda function the execution environments are reused when it makes sense to do so but that whole process of managing the execution environment's lifecycle is managed by the AWS service itself not managed by you the scaling of your lambmbda function is handled by AW which is a good thing because it lifts some of that operational burden off of you but you can't control certain aspects of the scaling of your lambmbda function through configuration that's it for AWS lambmbda this is。



![](img/6976cf488686c0fa7da8fdbcb1869055_21.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_22.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_23.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_24.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_25.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_26.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_27.png)

![](img/6976cf488686c0fa7da8fdbcb1869055_28.png)

A tiny amount of the information that you would need to know about AWS Lambda to get started。

 so I highly recommend that you check out the documentation and as always。

 stay tuned for more AWS ABCs。

![](img/6976cf488686c0fa7da8fdbcb1869055_30.png)