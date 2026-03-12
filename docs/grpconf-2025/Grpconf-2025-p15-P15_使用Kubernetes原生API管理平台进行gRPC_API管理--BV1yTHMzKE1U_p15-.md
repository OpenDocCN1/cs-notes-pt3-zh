# Grpconf-2025-p15-P15_使用Kubernetes原生API管理平台进行gRPC_API管理--BV1yTHMzKE1U_p15-

Hello， Ron， Wee to the session today。

![](img/9748434176c77d71bbe1fdac55d51c4d_1.png)

We will talk about the GRPC API management with Kubernetes's native API management platform， right。

So before that， we go into the detail of how we have implemented。 Let me brief about myself。

 So I'm Duuchhan Aberruan， and I'm a director of solutions architecture at W S or2 I believe you must have heard about our company if you do。

 but I will de brief about what we do basically So if you want to connect with me through please scan it through the Barcode。

 and I'm pretty happy to connect with you guys and discuss the interesting projects as a company we are developing right。

😊。

![](img/9748434176c77d71bbe1fdac55d51c4d_3.png)

Okay， so get into the API management， so。So you guys heard about that this is the concept。

 This is basically the known concept that why we need A management as a life cycle， right。

 So I believe when you're developing because we are in the GRP conference。

 and most of you guys developing applications back end applications， B to B applications。

 applications that connecting consumer applications， right。

 and I've been to like many great sessions since morning hearing what the developer。

Commitments and the practical challenges they are facing。 So in every case like。

 So what the main problem， right， So when you have many B to be point to point connections still the same problem that we have to resolve over the time。

 So that's why the management is a real deal to resolve with。

 So as it mentioned that its basically A management solution is allowing you to secure you expose in digital applications providing AI tools to control application controllability and then the obability right So basically we need to essentially resolve these problems when we have any application it doesn't matter when you have GRP application or anything。

 So what we are doing as a company So we are an open source company being in this industry almost 20 years and we are developing products like A management integration code pro code and management solutions and basically within the management also in the industry like almost 18 years So we are the first few like incumbent who introduces A。

And solution to the market。 And then， of course， then other the windows checking up quite quickly。

 So basically， if you look at the API management as our solution， it is available open source。

 And even someone want to download and customize and make it run in your premises data center or maybe the cloud hybrid years our tool is there are to customer to use。

😊，And then， of course， the Sa solution， which is a Vira。 we call bjira。 This is our Sa platform。

 that the same solution that available as A management solution， Sa option。 So basically。

 if you look at this solution， even So we have this。

Differentiated the control plane and the data plane part。 So if you at the control plane。

 basically we we offer different type of commodities， which is a Kubernetes native gateway。

 which is I will talk about to how we incorporate GRP protocols through that one。

 And then of course we have immut gateway based on a certain requirements like certain customer that you want to run your data workloads in private data centers So then you could use this immut gateway construct And of course you gateway that we can support mediation support multiple protocols and so forth of course we do support A federation。

 which is that if you want to manage AW Google gateway So we have this thirdpart gateway management supportability through the central control plane So we are on body more and more gateway in coming up solutions coming up releases as well So it is a bit of like a high level sort of like A management and of course this is most important part that nowadaysI is become more and more topic in the industry So what we do is we do support。

design， testing， searching and governance through the AI capabilities。

 If you want to learn more more about this capabilities please come through our documentation or maybe you can connect me through so we can dive through all these features in depth let let move on to the next section that gives you like more of of what this component structure all about。

 So starting with the plane that we provide this API lifecycl governance and of course managing ingress andgress API and of course we do is API developer API development design and of course API monetization capabilities plugging with all the tools available in the market connect our analytics tool and then we recently acquire about that product so we we have like first class first class supportability that and all all the other observ tools and of course if we look at the gateway construct So gateway construct type of gate that we do and G is one of the protocol that we are onboarding to our gateway component。

 which is。😊。

![](img/9748434176c77d71bbe1fdac55d51c4d_5.png)

Creing point for this internal B to B integration and， of course， the federation and， of course。

 integrating Sa systems and providing the develop extension for adding API。

 So this is more of like API management component in design。 I still I won't go into detail。

 So if you want to know about this information about this product in detail。

 I would welcome you to join with me in after this of the session。 So yeah。

 let's focus quickly on why GRPC APII management is required， right。

 So as I say that in the beginning，😊，It's a。''s a very perform protocol。

That you could deploy to integrate with application inter internal application development。

 especially for inter application communications， right， But still。

 when you deploy these applications， I believe within this group audience。

 you might implement all these applications and you might know that。 Okay。

 if I want to implement something that I want to imp enforce some policies。 How can I do that one。

 right， So the problem is that you might have to embed that policy into applications。

The best designing always has been。 you need to decouple that one。

 that that's the requirement of GRP and A management。 So we can talk about that one indeed。

 So how what are the problems again， So if you go through this security and access control like you want to apply different type of security protocol like maybe you might have to might need to bring a different type of third party I to manage security and then second these second option is second requirement is traffic governance you need to limit the traffic rate who you can access how you can impose enforce policies for different user context and then of course apply different type of operational policies like you might have to do like head based transformation mediation to request and responses based on the payload construct So you have to do all these management those management problems are still there。

 and then of course， plug in observability and then of course。

 when you have many ARP again and A and then you need to manage。All the versions of APIs。

 how you can get it done， How properly manage B to B conversation。

 So all these problems are still there。 And those are the real key needs why you need this A management solution。

So the resolution for that one is right now we have incorporate and we built a API gateta commodity。

 which is called Kubernetes gateway earlier， we call this one as a API platform Kubernetes but you can scan through this Q code and you can get to know about the design and architecture of this product So basically what we try to do here is that we work with this Kubernetes gateway specification and then what we do is like if you look at through the API Kubernetes gateway It works is roots specification right and accessories。

 So basically what we have done is we incorporate those specification to implement with our gateta construct。

 So this gateway is basically built on top of any。😊，So generally， what we are doing right now。

 if someone is familiar with the Kubernetes A specification， someone want to write STB route， right。

 so they can still use thatB route specification and what we have done is we have built certain adapters that convert those specification where itll deploy into gateway and the beauty beauty of this is that you can scale and it become more of like Kubernetes eco friendlyend deployment。

 So you can scale it and it has this automatic fail load balancing So this gateway has really become more of a commodity。

 So in our internal cloud solutions。 we now more of a deploy this Kubernetes gateway in the production。

 So we have proved proved that scale and address the throughput needs as well。 So yeah again。

 welcome you to read through this the specification how we have built it and you will get a lot more information around that。

😊，Right， so。Since this is like more like a short， you know session。

 I'll try to quickly go through and showcase some scenarios。

 how we have built up and what are the GRP use cases that you can think of right So so I'm going through like few use cases first is that deployRP A configuration authentication con meeting enable header modification and implement these interceptor layer。

 So before that， Ill quickly show you something。 you can quickly go to our documentation。

 which is the same It's very easy that you have the quick start guidance And following like few steps with comes we already pack everything through the he charts just a matter of fundamental requirements is that you need to have Kubernetes。

 of course， Ra any other cloud platform that you have Kubernetes and then you just have to go through these steps and install the。

😊。

![](img/9748434176c77d71bbe1fdac55d51c4d_7.png)

Kubernetes framework。 So that has a fundamental。 And once it is done。 So itll up and red up and run。

 So I'll go through the component that itll install So itll in install multiple A K components that will be ready to run right。

 So you don't need to customize it。 If you want to customize it。 of course。

 this help just you can download and customize as you wish。

 So let me try to go through the presentation again。😊。

And then I will start with like deploying a GRP application。 So we go through the recording。

Of the scenario。 So here what we are doing is before get into more in detail。

 So there are two patterns， two methods。 If you want to deploy an GRP API into the Kubernetes gate that you can follow One is as a developer。

 you can use the controllers like control As。 So we do support two types of control one is to the rest APIpis as well as the customer resources。

 So here based on the developer preference， they can go and deploy the API。

 So here the first way that we are doing is the first thing we are doing is we deploy the API using the rest API method。

 So here what we are doing first right， So we want to deploy backend services in this demo。

 which is the GRP enabled backend services。 and then we try to control accessibility of that API through the Kubernetes So let me try to play through that again。

😊。

![](img/9748434176c77d71bbe1fdac55d51c4d_9.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_10.png)

Right， so yeah， we deploy the API。 and then the second that we are doing is that we will check to the Kubernetes commands through the name spaces。

 whether the back end has been deployed and you will find it all the all the other components of port up and running。



![](img/9748434176c77d71bbe1fdac55d51c4d_12.png)

The next thing that we do is that we have set of commands， talent command。

 we use the GRPC configuration。 and then the definition。

 So here what we are doing here that can stop from here again are explain the situation。

 So what we did basically we use the API configuration and we generate a specification known as or the AK configuration。

 So it's coming from your pro。 you point to the pros and it generate the specification for you。

 And then here it come with the type and the information that the operations and then you can introduce other operations like backend service and so and so forth。

 So let me try to continue this。 So we will find out that the next step that what we are doing is we adding the backend services and here we go and add the A K configuration the backend services here you can add any circuit breaker logic as well here right and then we redm these API definition with the base path。

😊。

![](img/9748434176c77d71bbe1fdac55d51c4d_14.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_15.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_16.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_17.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_18.png)

Yeah， providing the I because of if you want to identify this API specifically and then we we gonna deploy this APII into the Kuberes gate。

 And then basically before that， what we're doing is the。



![](img/9748434176c77d71bbe1fdac55d51c4d_20.png)

Kubbernnet G come up with its only IDP inter key generator。 So key manager。

 So we generate the token and then we'll check the API diploma。

 So the A has deployed and come with automatically the security enable。

 And then the next step is that we will。😊。

![](img/9748434176c77d71bbe1fdac55d51c4d_22.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_23.png)

Try to invo this API。 So we are using this generate cur command like GRPC curl command。

 and then we will invoke the API， right， So basically， the idea of this is you deploy the APII。

 it comes with the interior security with the JW token。 and then it will validate the API API。

 So you just invoke the API。

![](img/9748434176c77d71bbe1fdac55d51c4d_25.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_26.png)

Yeah， so we will find out that intended result is the the next use case。

 I will quickly go through the next use case。

![](img/9748434176c77d71bbe1fdac55d51c4d_28.png)

The next few case is that。

![](img/9748434176c77d71bbe1fdac55d51c4d_30.png)

But sorryrry。Using the resource definition， custom resource definition。

 So the same if developers are pretty much comfortable working with the resource definition is itself。

 So basically what you can do is you can point out the protocol。

 It generate the custom resource definitions for you。

 and then you can work around this custom resource definition applying all the policies you need。

 So here what we are doing is same like earlier previous session。 We will get the A K definition。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_32.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_33.png)

Right， so let it。 So we copy the commands or the AP K configuration。

 And then basically if you are doing this， we will。Output， the C is。

 the customer resource definition。 So it will create the folder for us。And then， yeah， uned。

And then you will find out itll create for API， the audio pification， the roots。

 and then definition information and so so forth。 right， So it'll change all this information。

 And then if you need to apply any of that additional policy。

 what you can do is just change it and deploy that。 So， so basically， wait for until it is deploy。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_35.png)

Rightright， so the， we will check the API definition， right， and then it is deploy。

 So I quickly go through and sh finish up that part。 And yeah， so the API has been deployed。



![](img/9748434176c77d71bbe1fdac55d51c4d_37.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_38.png)

Apply to say circular secretary token。 and then you just invoke the A。 So we talk about two methods。

 One is rest A based deployment。 This is custom resource definition。

 which is like a Yama definition file that you want to deal with。

 So you can get it done to that part。

![](img/9748434176c77d71bbe1fdac55d51c4d_40.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_41.png)

The third use case， I want to get it done。 Show you here is。Let me go to。



![](img/9748434176c77d71bbe1fdac55d51c4d_43.png)

Sorry。Right， so the second thing is third use case is that how you can change authenticators authentication。

 So whenever you expose an API， you want to apply different type of authentication， right。

 Maybe itll customize authentication。 So what we do here is that since we have work with this custom resource definitions。

 you can enable custom resource definition to a specific gate if you wish right。

 So that's the effort that we try to do here。 So you you defined authentication and we we just stating that okay。

 you need to apply the security to the order API and then you deploy that authentication， right。

 So let it let's wait until it is getting deployed。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_45.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_46.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_47.png)

Apply that authentication M file to the environment。



![](img/9748434176c77d71bbe1fdac55d51c4d_49.png)

And then now the authentication has applied。 you can check the authentication through the security。

 right， and then it' will showcase that， okay， this is authentication stuff。

 So then next you will do is with that， we will generate the token and then it will deploy and will invoke the get use operation。

 So it'll work。 The next option is if you wish to disable authentication for certain internal internal communication。

 You could enable that one for that API also。 So what here， what we are doing is right now。

 we disabling authentication。 and we try to invogue this API。 So generally it'll fail。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_51.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_52.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_53.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_54.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_55.png)

Right， so itll will。 if you put like minus speaker command。

 So we'll find out that itll fail with the message。 Now we'll go to。Sorry， yeah。



![](img/9748434176c77d71bbe1fdac55d51c4d_57.png)

Command and then the next thing is what we can do here is that we will do the configure rate limiting。

 So here the requirement is that now you want to invoke API but you want to enforce certain policy saying that okay that API can be you know invoke maybe two times like you can enforce the security So here what you' are doing is again。

 we will create a API specification and then we say okay。

 it's going be a rate tMl file and then we apply that policy definition there right So what we say is like we change this definition saying okay。

 this API the rate policy should be applied to this particular API。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_59.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_60.png)

Right， so let us go through that one。 So we'll set the it or a period rate limit and we'll say like maybe two requests per second。

 right。Right， and then we will change okay， the API that I want to apply this API because you find out that in that definition。

 the API kind。 So it can be applied for a resource level， API level， right。

 and then operational level。 So here we say its should be apply for the kind of API。

 It says or the API。 and then we'll apply this policy to that particular API right。

 So let's let it be deployed。

![](img/9748434176c77d71bbe1fdac55d51c4d_62.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_63.png)

Right。So we are waiting now the API to be check like ok we are。

 we are checking with the that API available， right？ So let's go further， yeah。Right。

 so the re tape is getting deployed。

![](img/9748434176c77d71bbe1fdac55d51c4d_65.png)

So it says that word API limit has5 seconds like like it has been deployed like in five seconds。

 And then the next thing is that we will check the API definition where it dis apply correctly and then we will we gonna use the core command again to check the API whether the red limiting has apply correctly。

 So we will try few more cur request here and then generally what would happen is if you make like two more requests generally the the server should the gate should reject the request saying that okay。

 the red limit has you know， enforced。 So you find out that yes。

 here the red limit has enforce you come it came through the header that these are enforced policies and then the client would not not be able to access the API anymore So okay some it has to be reset after some time。

 So this is a very quick demo on how you can set the rate limit for GRP API。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_67.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_68.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_69.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_70.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_71.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_72.png)

The the next thing is I want to show you is the enable header modification。 So the same way。

 like if someone wants to modify the headers， like， so GRP again， you can。

 you can send to send certain headers。 and basically the idea of this one is someone can change the headers。

 And instead of the original one。 So I'll quickly go through we are running out of time。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_74.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_75.png)

So here idea is that we will get the information or give the de get the definition definition。

 And then here what it says is that right now， the header requires a test header right。

 So we apply that test header definition there。 and then we will check we will go through the deployment process again。



![](img/9748434176c77d71bbe1fdac55d51c4d_77.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_78.png)

Right。Let's wait until it is getting deployed。And then we'll take the headers and then we'll paste the torken there。



![](img/9748434176c77d71bbe1fdac55d51c4d_80.png)

And then now generally you can find out that here we send the authorization header General the authorization header is not one not the one that we expect for the authorization section。

 right so it should be tested right ideally， this will fail So basically what you need to do is you need to send instead of authorization header。

 you need to change it as a test header right So' one scenario。

 So if you change that authorization header as a test scenario now since the policy is defining that way。

 it should be able to accept the invocation right So it will work。

 So this is how you can quickly enable header modification through the specification。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_82.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_83.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_84.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_85.png)

The other command is that scenario I want to showcase here is。En。Meation part。 So again。

 this is again， how you can enable the interceptors， right， So that's again。

 another valid requirement that you should be able to intercept JRP locations， right。

 either request or response。 And then of course， you can enforce your own customized you know policy in between。

 So generally this explains you that how you can enable this backend specific resource。

 So here we have written like a simple Java interceptor。 and it says that okay。

 once you deploy this Java interceptor we say the interceptor service name can through the Kubernetes resource operations And then basically it says that okay。

 this is image and so and so forth。 And here we enforce some certain rules here。

 what we do what we showing here as of right now， we just add a customized header to showcase that。

 this is how the policy is getting engaged Now what we do is like we have this image。

 we will redeplo this image。😊。

![](img/9748434176c77d71bbe1fdac55d51c4d_87.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_88.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_89.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_90.png)

Let's wait until this is getting re deployed。

![](img/9748434176c77d71bbe1fdac55d51c4d_92.png)

Yeah。So。Well check the pos。 So the the。Yeah， so the interceptor port has already deployed。

And then we will try to invoke the API， right， so we can just go through the cube controllers and then find out okay。

 what are the interceptors that implemented。 Next thing is that what we do is we just try to invoke the API。

 right。

![](img/9748434176c77d71bbe1fdac55d51c4d_94.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_95.png)

And then you will get the response。 And then in between。

 you will find out theres additional headers getting added to the response。

 So that's how you can enable like interceptors between request or response。 right。

 So this are very quick sort of like of the power that you can accommodate it。

 or maybe you can enforce into into your implementation using GRP you know Kub gateways， right。

 So this is more of like a short demo sessions that we have done。 yeah。

 so we are already running out of the time。 So and that's all from my end。 I'm。

 I'm willing to hear any questions。 If you guys have any questions。 please raise yeah。

 I'm more than happy to help you out answering。😊。

![](img/9748434176c77d71bbe1fdac55d51c4d_97.png)

![](img/9748434176c77d71bbe1fdac55d51c4d_98.png)

Alright， do we any questions， I hope， yes， go ahead。A real know like customer。are yourYes， yes， yes。

 We have a set of large scale banking。Customers within in the apeEC region。

 So they want to have this high scalability。 and because they are moving all the workloads towards the Kubernetes as their organization policy。

 So ask us like， okay， what is the Kubernetes gateway that they want implement。 So yes。

 So there are customers and also we are working with multiple are the vendors in the market to push this the product。

 Also our internal tools right now， the cloud source products internally。

 this is the gateway that we accommodate。 and something that we are working on right now。

 as of we might have seen that we only done everything through like command line。

 So it like a developer friendly。 But since this is like first version that we did like more of like early adapters。

 we plan to bring like through the control plane like a U can control all these features。

 So thats something that we try to put in in our road map。Yeah。Alright， if there's no question。

 we on top of the time。 Thanks for listening to And hope course have any questions。

 please reach me out。 I'm staying outside。 So yeah， thanks。😊。



![](img/9748434176c77d71bbe1fdac55d51c4d_100.png)