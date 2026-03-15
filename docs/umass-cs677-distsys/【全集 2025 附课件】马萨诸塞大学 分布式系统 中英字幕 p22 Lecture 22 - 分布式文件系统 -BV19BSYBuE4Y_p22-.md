# 【全集 2025 附课件】马萨诸塞大学 分布式系统 中英字幕 p22 Lecture 22 - 分布式文件系统 -BV19BSYBuE4Y_p22-

So let's get started it's a minute early， but we can start。

So today we'll talk about a new topic which is distributed file systems but we have three or four slides left over from last time so I'm going to go through them then we'll switch to the distributed file system topic but I also had another announcement actually a couple announcements to make so I had said a few days back or maybe a couple weeks back that we will give you an estimated grade just so that you know how you're doing in the class but I think maybe later today we will give you a estimated letter grade that letter grade is based on whatever has happened so far about a third of the grade is still up for grabs because the final exam lab three still a substantive part of the overall letter grade so this is just an estimate right if you do better in the remaining things your grade might actually improve if for any reason you do less good than you have。

It may actually drop， but it should give you some notion of where you are so just take a look if you have any questions about your performance or anything like that。

 come talk to us right so we will youll hand it out later today is that the so it we should come out later today as the first announcement second announcement is we will have a final homework next week no homework this week but we will have one last one next week with a final lablet and that will be it other than the final exam as for the course system so so we will make sure that the due date for the homework is after lab three so you still have a little bit of time after that or it's a busy time end of the semester so manage your time well because you probably have other things due in other classes as well allright so with that let's get started we were talking about content distribution networks and then I said these content distribution networks now provide more。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_1.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_2.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_3.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_4.png)

edge computing services so so I wanted to spend maybe a few minutes talking about edge computing So if you remember what I said last time edge computing essentially is a complementary approach to cloud computing where rather than putting all your servers and storage in large data centers that are somewhat remote from the users you deploy these servers and storage at the boundary of the network which are close to the end users so the idea is the network。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_6.png)

Distance from the end users is small， so the latency for users to access a servers is also small。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_8.png)

🤧Okay。So this is especially useful for running latency sensitive applications so one very popular class of applications that runs on the edge is edge AI right so so you can essentially run inference and not training you don't train your models at the edge although there are some people who think that's a good idea as well but you can certainly take train model deployed at the edge and provide what is called edge AI inference where you can have requests coming in from users or it could be from devices and then you can essentially perform low latency inference and send results right so many examples one is like home security cameras that are essentially streaming video Fe 247 typically they go to the cloud and get process but now there are approaches where you can just send them to a nearby edge server it can run whatever detection object detection that needs to be performed on these security cameras and。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_10.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_11.png)

Back results low latency offload is another important use case。

 So when you have scenarios like autonomous vehicles or robots that are now autonomously。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_13.png)

Going around in the environment， you essentially may not have all of the compute resources on these vehicles or on robots to perform all the processing so they can use nearbyed servers to do that。

 but they need low latency answers because youre essentially going to use this responses to navigate and figure out where to go and so on so it has to be fairly low latency which is why edge is a better place to perform that computation than cloud which has higher latence right so so these are some of the use cases and I mentioned this last time。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_15.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_16.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_17.png)

Hedge computing is now really seen as an extension to the cloud these two areas kind of emerge independently of one another。

 but the way edge platforms are deployed their resources it is just seen as an extension so if you can go to AWS or Azure or Google Cloud and you can request servers now in local regions which are closer to you rather than asking for them in larger data centers elsewhere you can also request caching services from cloud providers that theyre deployed lots of these caches you can also perform things like low serverless computing where you are functions that are executing on the edge all kinds of use cases where cloud applications benefit from。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_19.png)

Being deployed on servers at the edge of the network rather than on other systems okay。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_21.png)

这个。The other use case where this has become popular is mobile edge computing where your mobile devices that are resource constrain。

 they don't have enough processing capacity， maybe they don't have powerful GPUus or what have you and these devices can also off to nearby machines augmented reality virtual reality mixed reality AR as it's called that's a very popular use case where you have a headset you are performing some interactive action but your headset may not have onboard processing capability to do something that requires some amount of computation so you might offload them to nearby edge GPUus so maybe it connected to your local machine or aned server that can perform all of the computation and send back the results which are then displayed to you on the headset so that's an popular use case for what is called mobile edge computing there are many。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_23.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_24.png)

use cases as well one last thing I want to say is mobile devices have also become more powerful now so if you have a smartphone its quite as quite a bit of F1 it as several cores of CPU it has a small GP it might have a neural accelerator it allows you to perform local small amounts of local MLl computation so some of these devices don't require edge processing because they can now perform processing locally but there are many applications that still do in those cases you might still need to use edge resources to offload your computations and so cellular providers are making good use of these edge resources because their cell towers everywhere so next to cell towers you can essentially put some servers so when your phone is actually trying to offload computation and its already connected to cell tower it can offload its computation。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_26.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_27.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_28.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_29.png)

on servers that are fairly close to so that's another use case where phone companies are trying to provide edge computing services as well in addition to cloud computing companies right so to many different use cases。

 many different types of providers but let me show you some examples of hardware where you can actually perform all of these edge computing but use special purpose hardware to essentially get capabilities that would require big server normally when you do things like machine learning computations you go to the cloudware there are big servers。

 big GPUs so you can perform all of these computations on these bigger servers but over the past several years there has been a steady evolution of special purpose hardware that is designed to accelerate very specific tasks these are called these hardwares referred to accelerators you taken a course on computer architecture you might have seen this type of devices。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_31.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_32.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_33.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_34.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_35.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_36.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_37.png)

So there are many， many of these that have come out There are some pictures here that are shown so that's an example of a Google accelerator it's called an HtPu TpU stands for Tensor processing unit there's one that came out of Intel which was called a VPU vision processing unit that was designed to accelerate vision type applications here's a small GPU from Nvi it's called a jettson GPU costs about $200 it's a small GPU but quite capable it can do some local inference tasks without having to look at other cloud services and so on and then that's your Apple that's the Apple neural chips called a neural engine is there in every phone and tablet that you can buy these days and it can accelerate all kinds of mostly simple machine learning computation so so you put all of these devices either on sorry accelerators either on end devices or but you can also put them on。

Ed servers to also put them on cloud servers right so all of these devices and servers are getting special hardware capabilities that allow them to take certain types of tasks in this case I'm showing you machine learning as the canonical example。

 but there doesn't have to be m It could be graphics it could be other kinds of tasks and accelerate those stuff right so you don't need to use general purpose CPU to perform this computation。

 which is how things have been for a very long time you can use these these types of hardware to accelerate many types of computation that allows us to do all kinds of interesting new ways of performing distributed computation So here are three pictures that show you how。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_39.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_40.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_41.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_42.png)

Io devices and Iot stands for internet of things These are sensing devices or devices that you can buy for a variety of tasks including health tracking like Fitbit like devices that you wear or cameras that you can put in homes or many other kinds of devices so so there are three ways you can actually deploy this in a distributed computing system so the assumption is that devices or resource poor they have cheap devices they don't have powerful CPUs or GPUs to perform computation they can perform some sensing tasks they can do some very limited amount of processing but not a whole lot so so for a long time the approach was essentially。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_44.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_45.png)

Cloud based offload where you an Io device it collects some data sends that data to the cloud all the processing happens in the cloud if there are any results to be sent back they are sent back to the device or often the results are a notification is sent to the user so this is called cloud offload where heres a resource constrained device that is using cloud resources to offload its data processing tasks。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_47.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_48.png)

哎。Here is our edge computing paradigm where you have an edge sir were sitting between the cloud and the Io device in this case the Io device can offload to the edge and then perform all of its processing to the edge okay some of those results might be sent to the cloud but not necessary you can do all of the processing at the edge but often maybe some things are sent to the cloud while other data is processed at the edge that is a three tier architecture this is a two tier architecture for processing IoT data okay Io device plus cloud this is a three tier architecture。

🤧Okay。This third picture is showing what I was talking about。

Well all of those three tiers have been augmented with specialized hardware accelator right so here you might have an ioT device with an accelerator you might have edge nodes with local GPs or you can have es and GPs and of course you still have cloud servers with powerful GPs so thats the。

World we are living in today where all of these tiers have both general purpose compute but also special purpose compute so that is an interesting question from a distributed system standpoint as to now where do you perform what types of computation your device is more capable because it has a local accelerator on it it could be a phone with a neural engine。

It could be a camera with onboard chip to actually perform phase detection so you don't even have to send your data elsewhere so you can perform more computations locally but if you send your data to the edge it also has accelerator So perhaps you can do more sophisticated computations than was possible before at the edge which normally would have to send to the cloud for example and the cloud also has powerful GPU so maybe you use it to train more powerful models that are then deployed on your device and so on so where you perform these types of computation has actually changed over the year so this is where we were maybe 10 years just at a device and cloud edge computing became popular So this was architecture that was being looked at now we are in this word where you have a three tier architecture。

So I'm going to stop there， but see if there are any questions before you switch to the。

Topic of today's class， which is distributed file system。 Any questions on this。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_50.png)

Okay， so let's move on to the next topic， so this is new chapter in the in the course。

And also from the book， so this is distributed file system。

So today is going to be taking us two or three lectures。

Today we start with the basics I' will give you a quick introduction to what our file systems will talk about distributed file systems and well spend much of the class talking about a specific one which is NFS network file system its a popular file system used in the UniX world so we willll start with that next time。

We are going to go into more advanced versions of distributed file systems which will be quoda XFs log structured file system。

 HDFS we look at Google file system， several others that are actually more modern versions of these distributed file system Okay so start with the basics。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_52.png)

就这。So just as some definitions what is a file okay essentially a file is an abstraction that your operating system provides you which makes it easy for you to store your data right so the more technical definition of a file is its a named collection of logically related data what that means is a file has a name that a user can assign to it which helps you remember where you kept all of your information because you give it a name that you can then go and look at and that the file itself is a container of data which is why it's called logically related data and that's information you actually store in the file that's a very basic definition of a file now files are implemented in several different ways in different file systems if you take a typical un like file system that you see in Linuxux even in on a Mac。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_54.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_55.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_56.png)

Your file essentially is just a sequence of bytes from the operating systems perspective each file has some collection of byte it's a sequence it does not interpret what those bytes are a file could be a PDF file or it could be source code that you return or it could be a binary file but as far as the OSsS concerned it just looks at it as a sequence of bytes it doesn't interpret the contents of the bytes so it does not attach semantic meaning to to the file now there are other file systems that actually do they actually have files with types so it file will have a type associated with there can is a PDF files word document this is a binary file and so on and it will attach some semantic meaning to file types it can perform certain operations on it so there have been different philosophies in terms of how to design the file system Unix took a very basic approach saying that it user can figure it out user can store whatever data they want。

the file the OS does not interpret them in the user is to figure out how to access that file and process that file and so on so that's something you want to keep in mind but as far as a file system itself is concerned it is providing an easier abstraction for users to access data store data and so on it provides the interface which is typically file names and you might have graphical interfaces that are stored that are created on top and there are system calls that the OS provides for file management directory management and so on this all you should know so I'm assuming you at least know the basics of file system so well build on that but let me start with a quick overview of a Uniix file system because said that's a very basic file system that you will see in many Linuxux operating systems and others where you essentially treat a file as a linear array of byte so the files don't have structures they don't。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_58.png)

records in them or anything like that they don't have types associated with them okay in fact in Unix file systems a directory is also a file okay a directory is simply a special type of a file which is a table and the table essentially contains all the files that are contained in that directory okay and essentially the index that you use to access those file that is what is a directory。

So it is essentially treated as a special type of a file okay which keeps information about other files which are files that are stored in the fold directories might have subdirectors and so on you get a hierarchical structure for your file system。

😊，Now， the thing that I want you to know is this notion of data and metadata。😊。

Filees contain data that is the data that users create and put in that file you write code you hit save okay that's the code that gets saved into the file that is the data you put but the file system in order to manage all of this files creates additional information which is called metadata metadata means is data about the data so all extra information thats stored with every file and every directory that allows the OS and the file system to manage these files on behalff of the user so will keep coming back to this notion of metadata over and over again so it's important that you understand that all file systems how to keep track of metadata data of course they keep track of that information in the file now in the Uni world the metadata is stored in a special structure called the in。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_60.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_61.png)

iodeode essentially stands for index node I stands for index so the iode is essentially a data structure that is going to keep track of all of the metadata for the file so what type of metadata do you think a file should have。

Size of the file first it should have file name right the name of the file is itself metadata thats not stored in the file thats stored external with metadata there is a file name it is a file size that so many bytes are in the file it has a timestamp that is the last time you modified the file all kinds of metada the owner of the file which the user who created the file all of this information is referred to as metadata is kept in a separate structure in UniX world is kept in an iNot but other file systems keep it in other places okay but in addition to all of that there is some additional information that is metadata which is。

Essentially how do you get to the data of the file itself where is the are the blocks of the file stored on disk so that's created that's essentially kept as an index so if you want to say where is the first block of the file you essentially go to the iode you look up its index and it will point to the first block of the file and because the files are not going to be stored continuouslytuous on disk different chunks of the file will be placed on different parts on the disk so you are to keep track of where they are thats stored as an index structure which is why it's called an in that basically an index in Uni is a multilevel index for our purposes that is not really important in this case but it is a multilevel index that makes the access very efficient and I'll just say that and leave it at that we'll talk about other types of metadata and distributed file system so you will get some field for what this metadata is used for and so is this clear any questions here remove。

😊，お？

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_63.png)

Okay， so now let's talk about distributed file systems。So。

 when I use the term file system or a distributed file system there is a we are to differentiate between what is called the file service and the file server the files think of the file service as the interface that is exported by the server。

That is the API or those are the methods that a client can call in order to access data that are stored on the file server and the file server is the machine that actually runs this file service。

now， typically we will start with a very simple client server architecture where the server。😊。

storetores data okay and it allows other clients to access data stored on that server or file stored on that server okay so then the question is what is the interface that your file system will expose that will allow clients to actually request data okay we will see in case of NFS it is an RPRPC interface。

But there will be other systems that will use other types of interface okay so we will talk about NFS in just a moment but the service in case of NFS is essentially the RPpC interface that is exporting the machine where the server keeps this data and exports this interface is called the file server so let me now explain。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_65.png)

A little more details about how the file service can work。😊。

So there are two different ways a typical distributed file system is going to implement as file service the first picture here is referred to as the remote access model the second picture here is called the upload download model and let me explain the difference between the two the remote access model is what you should implicitly have in your mind。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_67.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_68.png)

The file server is going to store files okay it will make these files accessible to the client the client wants to access a file on the server it is going to make a request okay the file server will process the request and send back the response which is give me this file or give me the first 10 bytes of the file or write something to this file thats the request to send the file server implements that interface it executes the request sends back a response。

So， that is called the remote access model where all access to contents are remote and you are sending requests to a remote machine which will execute those requests and send back responses。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_70.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_71.png)

So that is a very simple way to implement any client server application and so and distributed file systems are also a client server application the second one is going to work differently its called the upload download model in this case the client wants to access a file it sends a request to the server so what happens in this case is server will send a copy of the file over to the client so there is a copy now sitting at the client all subsequent accesses to the file are going to be local to that copy。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_73.png)

Because you essentially you downloaded the file， you are working on it locally and then once you close the file you will send the file back to the server and you will upload it back is is called the upload download model。

😊，So as you can imagine， there are some differences between the two approaches。

In terms of how they work， efficiency and so on。哎。So in the upload download model。

 as you can imagine， once you get the file， all accesses are local。

 so all the reads and writes subsequent to the first access are going to be fast because they are all local reads and right。

In the remote access model， every read and write is an RPC call to the server because the file always stays at the server you are sending all your requests just getting responses。

😊，Is that clear so there's going to be RPRPC calls going back and forth so network RPRPC calls will be more expensive in terms of latency than local reads and writes in the upload download model so you will essentially see that in terms of performance now there are other issues here in terms of the server server in the remote access model the server has to be keeping some state as to which files are open and so on in the upload download model you can implement this in a stateless manner although model versions of this still have to keep state of which files have been downloaded by which client if you want to implement consistency and so on because you might have multiple clients that are working on the same file if they all have copies and they are trying to write to it then you have to implement consistency in some way you'll get to consistency in a few slides when we talk about NFs but these are the two models you want to keep in mind。

Many file systems stick with a remote access model。

 but we will see that the upload download model has advantages and used in many cases。

I clear any questions here？

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_75.png)

Okay， so let me talk a little bit about stateful and stateless servers and then we can start talking about NFS if you design your distributed file system to be stateless what that means is the server cannot keep track of any information about clients it does not have any information about which clients have access the server which clients have opened word file states the server is stateless by definition so you have to design your file system in a different way as we will see when we talk about NFS so essentially no information is kept at the server between client request all the information needed to process a request has to be sent with every call because theres no record what the client did previously okay so all the information has to be selfcon but because the server is stateless okay it's more tolerant to crashes because the server can restart reboot but there are no state that was kept so there is nothing that。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_77.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_78.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_79.png)

You lose from a state perspective。Now。State full servers are the exact opposite The server keeps track of which clients are accessing what files all that is state information right what files are currently open。

 which clients have them open and so on this basically makes it from a request perspective a little more efficient because once you have state information you don't have to send all the information all over again every time you make a request to the server theres somewhat better performance and we'll get to item portency and see why that's easier that's not worry about that right now and we'll see that if you state full servers consistency maintenance is easier because you know precisely which clients have opened what file if the file is changed at the server。

 you can send notification just as we talked about last time in the web case where the server was sending notifications to the proxies here the servers have to send notifications to clients if they cache some data saying the file has changed。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_81.png)

So that becomes easier if you have a stateful server the server is stateless it doesnt know which clients are what files so it can't actually send notification direct you have to use pool based approaches in that case。

So that's somewhat abstract so let's start making all of this more concrete because we will do a case study of nFS and we look at all of this in some detail here's the picture so nFs first of all stands。

Network file system here that's an acronym NFS it's widely used all Linuxux。Operating systems。

 Uni operating system supported and actually many other flavors of operating systems as well。Good。

Here's the picture you want to keep in mind it's a very standard client server architecture the server has some disk you can store files on the disk and the server makes these files accessible to the client So what NFS allows you to do is access files that are stored on another machine very seamlessly it just looks like you're accessing local files but internally you're actually accessing files stored somewhere else not on your local machine so you should keep that in mind because usually when you have a laptop all your files are local but if you have a network drive allows you to access remote file not unlike some types of cloud storage that allows you to access files remotely and make it look like their local file but let's talk about how NFS does this so first thing I want to point out in both of these pictures is there is as a system call layer at the top that's how users are going to send request to the file system but the first level there is called the virtual files。

System layer or the VFS layer。Does anybody recall this from any undergrad OS plus what a VFS layer does？

Yes， translates address。Theres some translation of addresses more specifically you're right but also translates calls to specific file system so so what what is this virtual file system has the name virtual file system suggests it's an abstraction layer your OS can support many different kinds of file system you can have let's say standard local file system in Windows world it's NtFS that's a file system but Windows will support many other types of file system if you have a USB drive that you plug in the file system on the USB drive is typically not NtFS it may be fact or EXTFS or some other file system or you put a C into a CD rom drive it has yet another file system is called an Io FS and there are support for lots of other file systems as well so you can have a scenario where you have OS where there are many different disks set。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_83.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_84.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_85.png)

To the machine is this as a file system of a different type altogether so inside the OS you have a code for supporting all of those file systems in there so what the VFS layer does is it abstracts all the file system specific details and provides a file system independent interface to the rest of the application so the rest of the application just use open close readr and they don't have to care about how maybe ExtFS implements it versus NFS implement each of them will have their own implementation of these file system calls you don't need to worry about it so you have this abstraction layer so and readwrite request come here the virtual file system layer has to do two things there's something called a VFS switch which says what file system does this file belong to so it will then and you will hear inside you will have many different drivers that are specific to each file system that call。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_87.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_88.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_89.png)

Then be forwarded to that specific code instead though that is a specific file system and then that file system will handle your read and write it so thats the purpose of the VFS layer here you see two file systems you will see a local file system that is the local disc on this machine and you say second file system which is nFS so you have essentially two file systems so all read requests right requests open close that come in how to mean in this case either sent to the left box or the right box depending on whether the user is accessing local files or remote file this the VFS layer will do for you I mean for users so。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_91.png)

So that's the purpose of the VF there， but there could be many more file system than the two that are shown you but for our purposes we are only going to look at the NFS path we don't care about the local path that's a local file system so here as a user who is now trying to access a file thats stored on a different machine they make a read call the realizes that that's a remote file sends it to the NFS client NFS client is going to make an RPC request and send it off to the server the server will handle that request so you will see that here the RC request comes in goes to the NFS server NFS server sends it to which your file system layer because the file is actually stored on a local file system it goes down the local file path you do the readwrite or whatever the call is and on the responses come back the reverse path。

That clear。So NFS makes heavy use of RPpCs in fact NFS was the very first application where RpCs became popular in many decades ago Sun which was actually the company that implemented the very first NFS essentially wrote an RpC tool just to implement NFS and then they realized this tool can be used to write any arbitrary distributed system application or clienter or application so they released the tool as well so that you could use things like RC gen to write your own code but this was actually the reason the wrote the NFS compiler to begin with to implement NF so was the first early use or large scale use of RpC was in the NFS context so all we need to know here is that the RPC request going back and forth between the client and the server。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_93.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_94.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_95.png)

That clear okay all right so now let' us talk a little more details so here is a table okay you are not going to look at all the entries here but this is your NFS interface that is the file service so these are all the RPRPC calls not all actually this is just a subset of them okay that an NFS implementation will support okay so those are names of RC calls that you can make。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_97.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_98.png)

And you will see that you have a create to make a create a file thats open and then you will see somewhere this read and write at the bottom there are many others that are directory operations and so on so you don't need to go into too many details here but I'm just going to point to maybe one row here which is the open call open call is used to open a file that you use file open right so that is going to translate to an open call and youll see there are two columns here one is labeled v3 that' version 3 of NFS there's another column it says v4 which is version4 of NFS and then you will see when you look at the open call you say version 3 it says no which means version 3 does not support file open but version4 does。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_100.png)

So now let's ask what does it mean why is version 3 saying that when you open a file。

 it will not actually implement internally an open RPC card。

That's what it effectively means that when you actually open a file there is no RPC call that the NFS client is going to implement for you you have to implement and open some other way that's what effect doesn't mean you can't open files just simply means that there is no open RPRPC call so go to understand this I'm going to go back to the stateful and stateless examples not example discussion I just had okay so NFS was designed to be a stateless server。

And for a long time for many decades， it was stateless between the server kept no track of what clients have access。

 what files and so on。😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_102.png)

So that now what does that mean so when you open a file what happens when you open a file？



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_104.png)

This OS is going to open a file and hand you back a file descriptive。

That here you get the file descriptor when you open the file the file descriptor is essentially a pointer to internal OS state where the OS is tracking that this user or this process has opened this file this is the current position of the file pointer and so on that is all state。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_106.png)

Okay that the OS has to track an open call can only be implemented in a stateful file system because the OS will actually have to keep track of which process opened the file。

 what file was opened， what is the current position of the file pointer。

 all of that has to be tracked internal。😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_108.png)

But I just said that NFS is a stateless server， so it cannot keep track of this state。😊。

so as a result， there is no implementation of an open call because you you will not be allowed to keep track of that instead what an open call does is essentially cause this other call call lookup which just performs the first part of any file open operation it says does the user have permissions to open the file is this a valid file name because you could give a file name that's invalid and then the open call will fail or you can try to open a file for which you have no read access and your call will fail as well so the first part of open is going to perform all of these checks to make sure the user actually has permissions to open the file is valid and so on and then the next part of open will create this extra state and stick it in the OS so lookup will do the first part for it and lookup is supported so when when in NFS version3 you call open is just going to call lookup and say is this okay is this file valid is it present does a user have access to。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_110.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_111.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_112.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_113.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_114.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_115.png)

If lookup succeeds， your open call will say fine， I'm done。

And then when you read and write that RPRPC call has to specify all of the information that's what I said in specifically every time you are going to have to keep track of where your file pointer is on the client and and tell the server I want to read the next hundred bytes from this position this file offset because the file offset will not be stored at the OS level because it stateless the client part of NFS has to keep track of it and every time it makes an RC call it has to pass that as an argument so you will have reads and writes but they will have to pass strictly more information than if you had a stateful server。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_117.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_118.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_119.png)

So these are just implementation details of what you have to do if you say I want a statelesser or because it looks good right you don't want to keep state it' is resilient to crashes and so on。

 but a lot more things have to happen when you implement very simple things like file open operations or other things like leadss and rights and so on。

Is that clear？Now NFS version4 was the first time they said we need to have a stateful server because there are other issues that you can never deal with with stateless server so they made NFS version4 stateful and well see some things you can do with stateful servers so you will see that it does support open call so it just looks like a normal file system where you can make an open call and O will keep track of things for you or the server and and so on but for almost three decades version 12 and3 of NFS were stateless so they made that design choice and they to do all this extra work to implement certain operations。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_121.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_122.png)

Is that clear any questions here？

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_124.png)

Okay， so let's look at。Some RPRPC calls that go back and forth so here your two diagrams the first one actually talks about version3 how it works and the second one is showing you some things that have been implemented in version4 Okay so here you essentially have an open call followed by a read so the user has opened a file and is trying to read some information from a file okay open。

Essentially is just a lookup in an FS version 3 because there is no open R equal I just mentioned that okay so I just do a lookup。

 you look up the name， the name is valid， you get a success。

the user can read some information from the file。So your two RPC calls open and read。

 open trans to lookup， sorry two user operations open and read。

 they become two RPC calls lookup and read。In NFS version 3 sorry， version4， you do have an open。😊。

And you have lookups and reads as well， so what what the version4 is going to do is when you try to open a file it's first going to send make a lookup operation the lookup operation is successful and it will actually open the file by making an open RPC call and I'll try to read some data。

Okay， now version three。Use a standard RPC call version4 implemented something called a compound RPC some not something you have seen until now a compound RC is a batched RC operation where one RPC requests includes multiple calls multiple independent RPC call so in particular this compound RPC call actually has a lookup open and read all in the same RPC requests so three requests are going as one single requests to the server the server is performing all of those operations and sending backers now this is allowing you to batch RC operation just to reduce the round trip overhead of making individual RC call so it's a performance optimization you don't have to use it you could have just made three independent RPC calls so you would just have this picture with an open sitting in between thats what version4 would have done if you are not used compound RPC but that's just showing you one optimization they added to the server。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_126.png)

Where you could batch our PC request into one and send them off to the server。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_128.png)

OkayAll right so that's something to keep in mind let me talk a little bit about the mount protocol in NFS so so this is the protocol that is used for the client to associate the file system the local file system its some remote directories so this is referred to as mounting in the NFS world so here is an example that makes that clear so there is a server there are three machines here theres a server sitting in between labeled server there are two machines client a and client B okay all the files are on the server okay when a user logs in。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_130.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_131.png)

They log into a client machine okay and then what happens is the client machine runs some mount protocol that takes the user files that are stored on the server and makes them available on the client machine that is called a mount operation where you create a mapping from the remote file system 3 to the local file system3。

So in this particular example you are essentially creating the mapping for your mail directory but you can do the exact same thing for your home directories if you actually any of you use the Ed labb or use any of youred labb accounts that's how theed labb is set up as well all your files your home directories are stored on aned lab server but when you log into client your home directories mounted to that client machine where all your files are accessible as if they are stored locally so you are essentially using the mount protocol to do this so going back to this example you will see that this user essentially has。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_133.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_134.png)

A directory which is shown in the dotted arrow there when they log in here you will see that that directory is mapped here okay so what is in the dotted triangle on client they are not actual files there are just a mapping to the remote file so these files don't exist here that exist there but this is just a mapping so when the user tries to access this file this will trigger an RPC call that goes to the server。

When the user tries to access a local file， it is accessed locally or when you try to access this remote file。

 you are to send a request to the server to access it。

Is that clear what what mount protocols does so here are some more interesting aspects of mount protocols which essentially involve nesting and whether you have transitive properties and so on。

 so heres a a simple use kit okay so there are two servers here server A and server B and a single client machine。

哎。So， the server B has a directory called install that it is exported that made available to server A so that directory is mapped to this location called drawaw and servery now there is some parent directory of that directory called packages that is now exported to the client so the client now has access to everything that is in packages。

嗯。That clear what I just said so you have a directory from B that is mapped to a some parent directory of that map directory is now essentially mapped the client machine the question is from a client's perspective should it now have access to the files on server B。

because server or B made those files available to a not to the client directly right so server or B has simply made them available to a a has made some parent of that hold available to the client so should the client have access to that director that is the question。

And the answer is actually depends on which version or NFs you are going to talk about， but。😊。

va to C should C have access to Ace files because they are nested within whatever volume was made accessible。

Yes， no， only two answers。Okay， so in FS version3。You are not allowed to have recursive moms。

Because it was a matter of trust so A B trust A and makes some files available to a B might have no idea who a is exporting its files to so a just goes and export some parent directly suddenly our security problem where I trust my friend and give them access to my files they can then re export my files to someone else I did not give permission for them right so that's one way to think about it so so from a security standpoint trust is not transit I trust someone they trust somebody doesn't mean I trust the third person right so that if I did that I would have made that files accessible directly to the third part so in NFs version3 this is not allowed specifically B has to make its files available directly to the client for it to access it you cannot access it to a third part so that's the decision they made but in version 4 they relaxed they actually have a different security model where。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_136.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_137.png)

cursive mounting is allowed but your OS has to actually reveal that it not that it's automatic and you just B will know that the request actually came not from a but from a client so what will happen in this case is when you try to access the file the client will send the first RPC request to a A will figure out that the request is still accessing a remote file on another machine it will make a second RPC request which will forward that to B but B will know that this request came from some other machine and then it can decide whether it wants to export that or not depending on what the trust parameters。

So in version 4 it is allowed but you will actually have to do some extra work to decide what level of trust to extend to someone else beyond the machines you directly export in this volume so different trust models but but you kind of understand what happens when you try to make files accessible to a remote machine they can then reex that so you want to control how the information who can access what types of files。

Okay， yes。Thank you for the version。The client tries to access the bottom right part of the data。

OtherSo the the request to server B and was to server A。 So how will the be now。Because。

That's that part of。Is it your question is for version4 or3？In version3。

 this is going to be disallowed。Vion 3 does not allow transitative export for security reasons。

 so in version 3 if client is trying to access let us say slash bin slash draw slash install that is in the inner nested file you will send that request to a a will see that it is not a local file and it will return an error。

Okay， because the NFS client is not going to reward the request。

 but in version 4 if you access that file that first RPC request will go to a。

 which will then forward it to B and perform the operation and send vendors。Okay。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_139.png)

Any other questions here？Alright so there is something called auto mounting which allows you to do mount on demand that's just optimization where you don't have to mount all the volumes that a client has access to you can mount on demand when some user or process is trying to access it when the access is done and you can unmount it's a popular way to handle home directories so when you try to log into anedlab server for example your directory is mounted on demand so you access to it on that machine but after you log out that mapping is removed because you are not accessing those files why keep mappings when no one is accessing so auto mounting is essential in optimization that allows the mount protocol to be run on demand when clients or users are trying to access files on a server do you establish that mapping on the fly and then you remove the mapping when no user or process is accessing the but beyond that it works the same way as a mount protocol that I was talkinging。

Al right， so now let' us look at the interface aspects of NFS in a little more detail so NFS is a standard which means that it has published an interface that any NFS client and server actually have to support。

So anyone can use that document to write their own NFS server or client so long as you。

Meet the requirements of the interface you can call your code an NFS client or a server so there are two types of interfaces the NFS standard supports are not support specifies theres something called mandatory file attributes and then there's something called optional what mandatory file attribute say is that any file system that has these features that are called mandatory features can be used in conjunction with an NFS file system what you have to realize is NFs is not a real file system it simply a layer thats sitting on top of a local file system so if you go back the picture I showed you at the very beginning you will see that NFS client and NFS server are simply providing access to files that are stored on the server that are part of the local file system so NFS should be thought of a layer that sits on top of a local file system and makes that files on the local file system accessible on a different machine。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_141.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_142.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_143.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_144.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_145.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_146.png)

So you can take any local file system that is compatible with NFS and NFS will make those files accessible elsewhere so then the question is what what should the file system support in terms of features for it to be compatible with NFS so the NFS specification actually specifies these as mandatory and optional features？

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_148.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_149.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_150.png)

So the mandatory features as far as the file system go are very limited by design so that NFS is compatible with the broadest array of file system it is compatible youll see that NFS clients work with dozens and dozens of different types of file system and the reason is they don't require much so the file system just need to have a file type it needs to have a file size it needs to have a file system ID and needs to have indicator to know whether the file is changed or not so long as your file system supports this poor features then file system is compatible with NFS and you'll see that these are such basic features it is not even saying there has to be owner of the file or anything like that or permissions on the file all things that you expect in a file system they are not mandatory feature this allows NFS to work with lots of file systems that may not even have those types of feature but there are recommended attributes which do have all of that extra information like owners or。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_152.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_153.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_154.png)

File file handle file ID this is the location that is the index of the file access time modification time if the file system supports these additional features it works better with nFS but not required nFS will be compatible with any file system that just supports the very basic mandate reacts but it works much better if you have these extra items so this was done by design to allow nFS to work with all kinds of file system and been very successful。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_156.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_157.png)

You can get NFS clients and server or practically any operating system or any type of file system。

 they just work because client in the server don't have to do much for them to work with the local file system whatever that is on that machine。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_159.png)

Okay， so let's talk a little bit now about sharing aspects of the。

File system which will get us to consistency so the thing that you want to keep in mind when we have NFS is that the consistency that NFS is going to provide to us will be weaker than what you will see in a local file system and the way to understand this is through an example so I'm going to show you an example of what happens if you are modifying a file on a local file system and I'll show you that same example of what will happen when you run that using a network file system or nFS example is very simple you have a file that file has now two characters in it A and B。

So， this file is going to be now accessed by two processes okay big and big B maybe I should use different names but what they will do is they will read and write to that file in particular the first process is going to append a character C to the file so the file content is now become a B and C and the second process is now going to read that file。

The question is what should happen if this was a local file and you have one process that opens the file and apps a character and then there's a second process that opens that same file and reads it it will see A B and C that is guaranteed to you by the files whatever some processes written become immediately visible to all other processes or other local processes that is what are called Uniix semantics Uni semantic says that whenever you write to a file any subsequent process sees the results of the most recent right so which means write are immediately visible there is no consistency problem here you make an update anyone else that accesses the file see is that update that's it here's what might happen in NFS so you have a file server here same file A and B now two processes are accessing that file except that they are running on two different client machines first processes on client machine one second processes on client machine two。

😊，Process A is going to append C to the file， so the file content on process a and client machine1 has become A。

 B and C。😊，Okay now if the other process tries to read the file that file read is going to go to the server if the server has not yet seen the update to the file from client machine1 okay you are going to return the old contents of the file you will return aB because the server doesnt even know that the file has changed on machine one because the changes haven't been sent to the server they have been kept locally cache local。

So， you will now see older version of the file okay so you will immediately see now there is a consistency problem in any distributed file system that you didn't have in a local file system because all accesses went to the same copy of the file okay in a network file system there is a copy in the server there may be a copy in the cache on each of the clients and depending on which copy you access they may not be in sync with one another。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_161.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_162.png)

So consistency becomes an important issue in case of a network file system in particular in NFS you have to assume that the consistency guarantees are relaxed when you open a file and you read it you are not guaranteed that is the most recent version of the file some other client may have just updated the file and those changes have not in sent to the server。

So you are to essentially assume your applications not you your applications are to assume the guarantees you get to the local file system they're not going to get in a network file system because it does not give you any strong can guarantee that can cause problems in certain applications but let's come back to that so I just wanted to give you four different types of guarantees the unique semantics is what you expect to see in a local file system every operation on the file is immediately visible to all other processes on that machine that's what we assume but now there are other semantics that a network file system or a distributed file system provide one is called session semantic session semantics is the changes are not made visible until the process closes the file。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_164.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_165.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_166.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_167.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_168.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_169.png)

This is almost like a private workspace in the database world right remember in the private workspace you took a database you made a copy in the private workspace transactions made changes to the private workspace the database did not see those changes until the transactions committed right session semantics give you something similar in the file system world you can open a file you may get your own copy that's cache locally the process can make updates to the file all the updates are made to the local copy the file or the server has not changed any other process that reads it will still read the old version but when you close the file the updates are sent to the server。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_171.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_172.png)

Session semanal much weaker than unique semantics， but it is still a semantic that you can understand how the file system is behaving in terms of consistency。

A immutable file basically says it is not consistency necessarily but it is a way to think about how updates are made saying that once you create a file you cannot actually make changes to that file。

 you change the file you create a new version of the file and you update that work。😊。

Another way to say this is the file system is versioned every update of the file creates a new version of the file and you make a change to it and then if you change it youll create new version over and over again so so all the changes essentially have a version number so you don't have a single copy you just have many different versions of a file that's called immutable files so some file system support that they will never update a file theyll make a copy create a new version and change the file so you can look at the old copy or new copy depending on what applications is trying to do that's immutable and then there are some file system that actually provide database like guarantees where they provide transactional semantics you can make updates for the files and you can assume at Thomas city where all the changes go to the server or none at all。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_174.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_175.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_176.png)

so you can have some certain file system like NFS actually can even provide transactional semantics and thats useful if the underlying file is actually a part of a database so then you can use file system。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_178.png)

Punctionality is is already giving you atomicity to implement database level for normal applications you don't need transactional semantics you can just do read sunrites and use other mechanism。

 but there are some file systems that do support this。All right。

 so what does NFS do NFS as somewhere close to session semantic not exactly does not give you。😊。

Unix semantics I already mentioned that， but it is somewhere close to session semantics because it uses caching right so I am going to show you some examples。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_180.png)

so here is an example where you have a client NFS server and you have a client so when the client application accesses a file or some parts of the file from the server and the RPC request returns。

 those contents are stored in the local cache。If that process accesses that same part of the file you are not going to send a new RPC request to the server because that part of the P file is already cache so youll work on the local cache version similarly if you update the file which means you' right to the file and that portion of the file that you are writing to is already cache here you will just update the local copying the cache so that means you are to now ask what is the cache consistency guarantee we are providing if there is an update what does the NFS client do NFS client basically uses very weak semantic it does provide no guarantees at all because NFS protocol does not specify any guarantee that the client has to support that is left to the designer every implementation can choose its own。

Consistency approach and by and large， most。Implementation just say every 30 seconds take all the data that has been modified in the file。

 send it off to the server。😊，That is what many implementations do。

 which is no so what that means if you write profile file it may take up to 30 seconds for your client to actually send those changes to the server so for 30 seconds the server will have out out date information。

😊，Okay， so。30 second is not a requirement that just what many implementations do because as I said the NFS standard does not require any consistency at all。

 the most implementations don't implement any consistency guarantees they just have this rule that says track all dirty contents in the cache and then flush them to the server every 30 second。

So very weak semantics， which means that。😊，Any other client that was accessing that file from the server will see out of date information for up to half a minute until that client is going to flush it。

😊。

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_182.png)

Okay， so let' us go back one and talk a little bit about locking the reason NFs version 4。

What was made state is because they wanted to implement locking functionality so so first of all what is file locking file locking is the ability you know what locks right you seen locks read write lock that you implement on inmeory data structures file systems also support locking functionality you can open a file and then you can lock the file you can take a write lock on that file if you take a write lock and a file is some other process opens a file it will be denied because you hold a lock you can have read write locks you can have a read lock some other process can open it and also get a read lock so all the locking things that you learn there also implement in file systems。

Specifically local file systems have implemented file locking， you can also lock parts of a file。😊。

So you can essentially lock a range of bytes you don't have to lock the whole file you can say I lock bytes off 10 to 20 so only those bytes are locked other parts of the file can be open for read so you can lock the entire file you can lock a range of some range in the file and so there are all kinds of locking functionality you can implement but here is the problem NFS cannot support file locking because it was stateless。

Okay。A lock is a stateful object at a minimum you have to know whether the file the lock is available or free or what ranges are logged and so so to implement locking you need a stateful server because lock information is stateful by definition so until NFS version3 you could not implement locking at an NFS level your local file system could implement locking but if that file was accessed by some other client you could not expose locking functionality so you just couldn't do it but it was stateless but once they made it stateful now NFS supports all of the locking functionality that underneath the local file system support so this was an advantage by making the server stateful you could implement this higher level features and there are many applications that fundamentally require locking not just databases there are many other applications that require it simple one to think about is your email。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_184.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_185.png)

so where does your email come it comes to something called an inbox and inbox is essentially a file on the mail server。

But you should ask why should the inbox be locked because there are multiple processes that are accessing the inbox at the same time at a minimum if your a mail client that is connected to the mail server your mail client is trying to read your inbox receive new mail has arrived right but there is a mail server that where incoming mail is coming in and then that mail can be delivered to your inbox so the mail server is writing to your inbox your mail client is reading that inbox and maybe if you delete some email messages it will update the inbox you will read and write。

So the inbox is a shared file。If you didn't have file locking your mail inbox will immediately get corrupted if you are trying to access your inbox and the mail comes in to your mail client and the mail server try to write to it at the same time it itll get corrupted so you need to have file locking for mail to properly very simple application but you need file lock now if you are just operating a local file system that's fine but if your mail server was running on an NFS client all the mail files are actually NFS mounted you could not do that because there was no locking supported right so there were many times where users did not know this they ran the mail server on an NFS client and the mail files are stored on the server and they mail corruption and somebody's mail actually got deleted by accident because the whole inbox got corrupt so to avoid problems like this eventually they went and added locking you didn't have to deal with these types of problems。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_187.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_188.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_189.png)

So， but that requires you to have a state full server， this is why after many。

 many decades they decided yes the stateless part does not work for certain things specifically file locking。

 which is important for many application。Okay， any questions here？

All right so I talked about caching i'll talk about delegation and then maybe we will talk about a couple more things and end today so nFS remember earlier in the lecture I said there are two module for a distributed file system remote access model and the upload download model。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_191.png)

Until version 3 of NFS， everything was remote access okay you make a local call。

 you send RPZ requests to the server， server processes or request sends back the response that is remote access。

As a version4， it still support remote access， but added the upload download part to NfS or as a performance optimization。

😊，In the NFS world this is called delegation file delegation so here is an example of what delegation mean so here as a client and a server the client opens the file meaning it asks for the file so you may send a request to the server if this is the only client and the system that has asked for this file meaning its only one that's opened the file the server is going to say rather than having the client send RC request let me send that entire file over to the client so its going to delegate that file to the client and then the client has the master copy at this point so all subsequent accesses from that client go to its local copy you don't have to send RC request because you have the master copy the copy on the server is now out of date because it delegated it to the client so it no longer has the master copy and when the server and the client closes the file。

The client can send the file back saying that I am done here is the file。

 but there may be other issues where some second client comes in and tries to open the same file。

the file has now been delegated to the client no longer at the server so second machine tries to open that file you have to let that happen you cant say oh the class circle file has been sent to another machine you can't open the file that is not something the file system will do so you are going to have to bring the file back。

You will have to essentially recall the delegation and say now there is concurrent access to the file。

 delegation is only possible when there is a single reader or writer。

 not when there are multiple processes accessing the file， so you recall the delegation。

 the file comes back to the server and then you fall back to your usual RPC request model where multiple clients can send RPC request and the server will process them。

😊，So that is still not an issue， so so NFS version4 will support both it will support delegation as a performance optimization。

 but when there are concurrent accesses from multiple processes it will fall back to the RPC case。

 our remote access model。Yes。I。What。Okay question is if the client is updating a file and then the server recalls the file recalls the delegation what happens to the update and that is the question right so so it is fine for the client to perform all outstanding operations。

Have them finish and then send the file back you dont have to cancel the right request that's in progress because you got your file but delegated you can let existing calls finish take that version of the file move it over and then all subsequent accesses to that file will have to be sent to the server because there is no local copy so you don't have to cancel operations in progress it is fine for you to wait as the client wait until they are finished then send them。

File back because it's not like the open request has to finish in some period of time it will just take longer for the open call to return because the file has to come back to the server。

 but after that you are back to your RPC keys。对。みュ another questionです。

Yeah question is does it have security consent can the file make unsanctioned update so the unsanctioned update is not an issue because if the process has access to the file it can write whatever it wants whether the file is at the server or you right so so long as you have read and write access to a file as a process you can open the file and write to it whether it's sanctioned or not is not the OSS problem that's somebody else's problem so we'll leave that part aside but there is another problem which is somewhat of a security problem saying you delegated a file it said the client client just crashes。

so now the server does not have access to the latest copy it can't recall delegation so that problem is still there okay I mean the server can say it just reverts back to the old version because that's all it has and that then you will just essentially discard all the updates that were made to them so you do have to deal with some problem not quite security but crashes and failures。

Yeah。做好啲。When you compose a male， how does locking have a hazard audio of question。

So essentially when you start to send email there is no locking problem so think about how mail work all your incoming mail goes to a file called an inbox which has all the mail that has arrived to you and the mail client can then open the file and look at all the mail that has arrived。

When you send a mail it does not touch the inbox you just compose the mail in the mail client and when you hit send it directly goes to the server and then the server sends it up you can additionally append that mail to a different holder called a send mail which is different from the inbox so the send mail is a separate file from the inbox so inbox is only incoming mail。

Signing of mail does not go through the inbox because you don't actually append it to the inbox you might not store it at all or at most you might store it to sent mail folder。

So the sent mail folder you can still take a lock and add to that's a different problem okay but the inbox is when you are accessing incoming emails you do whenever you open your mail client and you look at all your messages your mail client has to have open the inbox it has to travel a lock on that inbox read all the mail release the lock okay and then if this new mail coming in the mail server will take a lock on your inbox deliver the mail release the lock and then when your mail client checks again it will reopen the file and you see new mail list so but each operation it a read or write operation where you are to take a lock。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_193.png)

![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_194.png)

Just when you access any other shared data structure where two threads are accessing it here two processes are accessing。

 but the shared files you need locking on。都不。Yeah， so question is if we open the file and some new mail appears what has happened right so when you open an inbox the mail client is just displaying the emails that it。

Soaw when it opened the file last doesn't mean it has to hold the lock the whole time okay what your mail client is doing is it is periodically checking with the server saying has new mail arrived when it checks with the server it grabs a lock and if there's new mail then it will reopen the file and fetch the inbox over and display the new mail but just because you have your mail client open doesn't mean you have a lock on the inbox it just showing you what the contents of the inbox where the last time it checked it and the server but it will periodically check。

Any other questions here？Okay， so let's stop here， we ran out of time， we'll continue next time。



![](img/81ff57e8ceea29ea96a04a9a6f40e9e2_196.png)