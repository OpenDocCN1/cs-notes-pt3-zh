# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p36 -36-Lec18 Video_ Minix File System and File Server (03_19_20).zh_en -BV1iP2CBaEHr_p36-

![](img/790b5f19d8d66c4299fb6f757748717e_0.png)

![](img/790b5f19d8d66c4299fb6f757748717e_1.png)

Okay， so we will continue the discussion from where we left off last time。

 which was basically a discussion of general concepts in。

File systems and how operating systems kernels provide support for file systems so with that background today we are going to look at the Min file system in particular and see how Min can actually enable the implementation of multiple file systems as well。

So before I get into Min， I want to present a concept that is used by many Uniux like operating systems。

 including Min which is called the virtual file system or the VFS so a VFS is essentially saw layer within within the OS kernel that allows you to have different file systems present in the OS and yet provide an abstraction that allows access to this file system so as is shown in this figure the VFS layer which is also called the VFS switch sits above the implementations of different file systems within the kernel and this picture actually is Linuxux specific but the same concepts are going to apply to Min as we will see shortly so you see underneath the VFS layer are different file system so there's an EXD file system is a riser file system。

And the VFS layer is actually sitting on top of these file systems and providing a file system independent abstraction to the rest of the OS and to user processes so what happens is system calls that our file system specific always come to the VFS layer first the VFS layer then examines which file system is responsible for processing that call and then it is simply going to forward that call to a specific module that implements the file system so if it is a read or an EXT3 file system the VFS layer is going to then invoke the read or forward that read to the EXT3 implementation of read and so on and so forth。

So this mechanism allows us to add new file systems to the OS kernel very easily because you just have to write that file system to work with the VFS layer and then everything about the VFS layer is going to be file system agnostic。

So the same concepts are actually going to be true in Min as well。

 except that unlike this picture where we have a Linux kernel which is monolithic and all of these components reside inside the kernel we are going to have in Min。

 these components being separate system processes。So in Minix we have observer server process which is called the VFS process。

 the VFS process as the name suggests is implementing the virtual file server or the virtual file system functionality in addition to several other functions but that is by and largege what it mainly does and as shown in the previous slide it is essentially a user process or a system process that sits between the actual user processes and the file system or file server processes that implement specific file system functionality so the VFS switch essentially is implemented by the VFS process and as we will see each file system in Minix is going to be a separate user process that's going to interact with this VFS process。

Now we will see that not only is a file system a separate process。

 each mounted partition of a file system is also going to be a separate process。

So I'm going to talk a little bit about the functionality provided by the VFS layer of the VFS server process in Linux and you will see today that the slides actually have more content on them as compared to some of the previous classes this is because all of the classes are recorded going forward and I wanted the slides to be more informative than just presenting high-level bullets and explaining more of that you will see more details on these slides going forward as so coming back to VFS VFS as I said。

 provides an abstraction to the other file server processes it implements a number of data structures and functional functions but by and large it is responsible for two or three different things the first is it implements a positive system called interface that allows user processes to invoke these system calls and it also supports。

Additional le so you will see here that the two classes are system calls that are implemented in the VFS are all the file management system calls which you will include and there's a long list of them on this slide so these include file specific ones such as open close readwr directory specific ones that allow you to create directories and whatnot system calls that allow you to change file attributes like change more chunk change directory and so on as well as several others that are specific to mounting and unmounting file systems。

And the VFS process also supports several process management system calls。

 remember that there are other processes such as the VM and the PM that also implement a lot of the process specific functionality。

 but there are a couple of calls that are process specific but also tied closely to the file system and those calls are actually supported implemented rather by the VFS process specifically the select call that allow you to actually。

Deal with the。All you to deal with some file I as well as file descriptors and file position manipulation calls are implemented by the VFS layer and process and the VFS layer also the VFS server or other。

 also interacts with the process manager， when you are to deal with things like Fork can execute and so on。

 because some of this when you start a new process required to read a new file from this and that call is actually handled by the VFS process。

The second key set of functions that are implemented here are to track endpoints for device drivers because the VFS layer is of the VFS server or rather。

 so also the process where all of the IO function functions flow so it has to track what kinds of device drivers that present character device drivers block device drivers or their device names are because if you remember last time I mentioned that two classes I mentioned that all devices also have file names that reside in the slash dev director so when you are accessing a device through file name that call actually has to flow through through the VFS process the process has to track the endpoints which are the drivers that are will be responsible for implementing device specific functions and can forward the calls to those drivers when when they receipt。

So here in this slide we have a picture that shows us the typical control flow of how an IO request will flow from a user process to a specific file system what is not shown here are things that are kind at a device driver layer and below those functions were described in an earlier lecture that's still the case so we are only looking at file system specific layers and processes in this in this picture so as I shown you how a user process that is a read system call and the read system call is I going arrive at the VFS process which in Min is implementing a VFS functionality or the VFS switch functionality and in this case let's say it is a read to a Min first file system so it is going to take the read request and then forward it to one of the Min file server processes in this picture you will see that there are three different。

Partitions that are mounted， there's a root partition s there's a slash user partition and a slash form partition and each of these could be separate processes sitting within within the system and depending on which partition the read is reading the file from you will actually forward it to the right right process so pretty quickly the user process executes a read。

 the VFS is going to verify that the read is on a valid file and then forwards the request to the file server that is going to handle it the file server is going to read that data。

 remember that in doing so it has to deal with the block drivers and device drivers and the hard disk and so on which you are looked at separately and once you read the data you're going to copy it back to the user process and reply to the VFS process that it has executed the request and the VFS process can then subsequently process other operation。

Now shown in this picture is a more detailed version of the simplified picture that I showed earlier。

 I put this picture only here because one of the labs of the projects is going to require some modifications to the file server and the implementation of a file system so it's instructive to understand whatever I showed in the previous slide。

 however it actually is implemented in more detail within minutes so that。

The processes by the same it is just that more steps are shown here that implement the higher level description I presented previously so in this case rather than doing a read we have a different system called so it's called Sta that's going to look at status or files and so on so you have a user process that executes a small program thats a snippet of which is shown in this slide that called stack on a particular file。

And so that request is going to come to the VFS process。

 the VFS process is then going to essentially do a lookup to the root partition。

 the root partition is going to then essentially resolve that request by actually going to the device driver and trying to read the file。

 read the file or not to read the file read the directlyy， and so on， and then。

You will basically eventually get back a request in this case the stack is on a file that actually belongs to a slash user partition as you will see in that snippet of code so the root partition actually needs to the file server process handling the root partition needs to forward that to the slash user file server process so the figure is also illustrating that although you have a single Min file system on the disk。

 you have multiple partitions， each partition is its own independent Min file system。

 the s is an independent Min file system Partition and slash user is one so there's a file server process for each of them so it's not just one server process for all devices。

 it one server process for each partition so you will see that in this case the request gets forwarded to the slash user file server process and。

eventually after it's processed through the device driver。

 you are going to send back a reply to the VFS process and then eventually to the user process。

 so multiple processes， system processes are involved in handling the system call as is typical in most of the calls that are coming to the file system。

Okay， so with that control flow background， let's talk about some more details of how the VFS process is implemented。

NowOne of the things that is true of the VFS process which we have not encountered so far is that it implements threading。

 it implements threads to handle concurrent I requests because that lacks a good way to handle concurrency it's worth noting and as I've also mentioned previously Min has no support for kernel level threads at all。

 so we have not actually encountered threads so far in any of the other components within Minix but this is one of the places where threads are used extensively。

And because Manix has no support for kernel level threads。

 VFS threading is actually implemented using a user level Ts library， which is called Ss thread。

So this thread is a user level library that was written specifically for system processes so if you need to write a system process that works with the micro kernelnel you can actually use this user level threads library and it will allow you to implement threading functionality of course there are other threads packages that are also available for user processes。

 this one was written specifically to make the VFS process concurrent。



![](img/790b5f19d8d66c4299fb6f757748717e_3.png)

So the way it works is through a standard master slave process architecture where theres a main thread that is waiting for request and there are a set of our pool of worker threads whenever the main thread is going to receive a request it's going to look for an I worker thread and hand that request to that worker thread and once the worker thread is finished with that request it's going to go back to the IDU pool again。

 that's a very standard way by which you write any concurrent or multithreadread server and the VFS server also uses the same concept to implement the multithread worker pool architecture。

Now it's worth noting that in this architecture if you start with a certain number of worker threads and you get more simultaneous requests than if you have worker threads then youre going to have to wait。

 meaning that which all the worker threads are busy and a new IO request arrive。

 that request will be queue in more sophisticated servers the size of the worker thread pool itself can be very dynamically so for example in the Apache web server you have a dynamic worker pool but the size of the pool actually varies based on the load that you see in the system。

 but in Linux you have a much simpler static worker thread pool which means that if you have morecurrent requests than you have worker threads then some of those requests will have to wait until a new thread becomes available。

So the VFS server is going to use these worker threads to interact with all the file server processes and it does so asynchronously so while waiting for a reply worker thread is blocked so it is synchronous on a per thread basis but in general the whole process is not going to block that in user level thread packages if one thread blocks。

 all threads are going to block and entire entire process blocks since we don't want that to happen each thread has to use asynchronous IO or asynchronous request because if you makes a blocking call then all of the other threads can blocked as well so while waiting for a reply a thread is going to be waiting but in an asynchronous fashion which allows other worker threads to execute。

And when you receive a reply from the other files are our process。

 that worker threat can continue execution and eventually finish processing of that request。

Now this picture here， which I'm not going to go into too much detail。

 shows us the three types of worker threads that a VFS process supports and they're called a normal thread which just does normal work there's a deadlock thread which actually is a deadlock resolver if there's a problem deadlock in the system that's the one that is going to be used and then there's a system worker thread that is used for by the process manager and then to handle notifications from kernel the micro kernelnel and so so the normal threads handle requests that come from user processes。

 the system threads handle requests that come from other system tasks such as the process manager or the kernel and the deadlock thread is actually handling。

There are deadlocks in the system。Now I'm going to also go through a little more detail of where some of the code for the VFS process resides。

 it is spread across multiple files but all of them are in the VFS folder in the servers directory within within the Linux source tree so here are some of the key data structures that are shown on this slide so there is Fpro there is VMo there is V node there is flipped there are a couple others on the next slide so Fpro is essentially our process file table if you remember the concepts I talked about last time I said there are file tables that are maintained for each process so in this case you essentially have the Fpro data structure that is implementing that functionality VMo essentially tracks all mounted file system that are currently presented in the system and it will have。

Information like the device major number， minor number， the mo flags and several other attributes。

The Vn data structure as the name suggests， essentially is going to track all the iNots in your system so essentially for every disk file you're going to have an in and all of those are tracked in the Vn table。

The flip of data structure which is basically the file position table for every open file。

 you're going to have an offset that tells you where that file is where the file pointer is pointing to and the flip data structure is going to track that for us。

And there are a few others like the lock data structure that allows us to lock certain parts of a file。

And as been noted here， it is basically used in advisory locking at the process level。

 not within the current in the current group， the select essentially is used to implement the select call and then there is essentially a DMmap object that is going to be mapping from the device minor number toward device major number。

 excuse me， to a specific device drive so that you can forward the request to the appropriate device drive。

Now I should mention that because the VFS process is concurrent it has multiple threads。

 many of these objects will need locking， but the type of locking that is used will vary from object object based on how threads actually access them and at the bottom of the slides are several pointers where some more information about these data structures is available and the best place of course is to go to the Linux sourcery and then look at some of these files to understand these data structures better。

So now let's come to locking again， this is the first time we are encountering threading within the kernel and whenever you are threads your need for synchronization because if there are multiple threads that access the same object。

 then you are going to have race conditions and。Problems with multiple threads trying to overwride for another。

 so you need to implement mutual exclusion of locking to avoid these problems。

Now we'll get to how each of these objects implements locking but what is shown on this slide are higher levelve design requirements and we'll see that VFS locking uses a set of design principles that are very similar to asset properties if you have taken a course in databases you would have heard that asset properties which is an acronym that stands atomicity。

 consistency isolation and durability and relation databases implement concurrency and locking using asset semantics now file system don' use database semantics like asset properties but they have their own set of requirements and the requirements are listed here and'm just mentioning that some of them have a similar flavor to asset properties although I should also say that this is really not providing database like asset semantics at all it's a weaker form of guarantees。

So the first is you want consistency of the replicated data。

 which means that any system call that access the accesses data structures like that modify things like file sizes when you write to a file you might end up making the file bigger so that requires a stop the file size so any system call that makes these kinds of changes have to be mutually exclusive within the VFS process there has to be some isolation which means that。

When system calls are composed of multiple requests。

 you are to ensure that the result of a system call should not be impacted by what is happening elsewhere so it should look like this system call executed by itself and you do not even know that there are system calls executed that's called isolation property which is similar to how database transactions were integrity of objects essentially says that you should keep objects in a consistent fashion so。

Since locking is itself a blocking operation we will see that integrity of locks requires some extra locking functions and some of this is non-preemptive so you want to ensure that you maintain the integrity of all objects in the kernel you have no dead of requirement which seems to be an obvious requirement that we have whenever you are trending and you acquiring all kinds of logs you want to ensure that you are not going to have any deadlocks very easy principle that you can use even in user level code that you write which is also used here is to order the operations in terms of how they acquire locks so Linux also does the same thing of the VFS and Linux does the same thing and it is going to essentially a conflicts between locks by keeping in order and require locks in that order which always ensure that there are no cycles deadlocks of course when your cycle and。

Bocks are bitwired。So you can avoid that by simply enforcing an order and we don't want any starvation in the system where because of blocking。

 so you need to make sure that all system calls execute efficiently。

 you must ensure that one request does not block other request。

 you must also ensure that read only operations can be concurrent。

And we'll see how some of this is implemented so within the VFS process we essentially have three types of locks which are very similar to readwrite locks I hope some of you heard the concept of a readwrite lock a typical lock essentially is mutually exclusive which means any thread that holds a log blocks all other threads that are trying to acquire the log so that's a standard lock which means that only one thread can hold that lock at any given time。

Now readwrite lock generalize that concept a little bit by allowing a bit more concurrency and what this says in a readWrite lock is that multiple threads can acquire the lock in read mode where theyre only reading the object but not modifying that object。

But if youre trying to modify the object you have to acquire the lock in right mode。

 which means that it now looks like a normal lock where only that thread holds the lock and all other readers as well as writers in the system are blocked from accessing the object so the Linux and VFS also support a similar concept and this allows you to have more concurrency during read but safety during the write where only one writer can write to a data structure。

So there are actually three types of locks there is a TTL read which is a standard read lock that allows multiple readers to read that object as a TTL write which is a write lock that allows only one writer to hold a lock。

 no readers or writers allow and there is something called a TTL read serial which allows you to hold read locks on multiple parts of the file so you can hold a lock on only a part of the file rather than the entire file resource rather than the entire resource so read locks are somewhat similar to write locks in that。

You can essentially you dont block other concurrent reads。

 but you can be upgraded to a right lock and then the thread wheel block until the last three lock has left and so on so think of this as a way to serialize some of the reading when you don't want full concurrency。

So again， there is a link at the bottom that has some more information on these locking primitives within the VFS layer and well see that there other parts of the system。

Of the Linux system that also use locking and use the same concept。

Now earlier I mentioned that to avoid deadlocks， Linux will Linux requires that code has to acquire locks in a certain order and that order is shown here so you see a set of tasks or data structures Z going from Fpro to exact V or v node flip and so on and that's the order in which that order that you to respect So what so as an example thread cannot lock an f object if it actually holds a lock on something down that chain such as a V movement and so on so you won't only hold one lock at a time and if you hold a lower lock you cannot actually acquire a higher order lock until you release that first so I think that's the general concept and if you do that that you will not have any cycles because you're always holding locks in increasing increasing order that shown。

picture and that basically means you cannot hold a lower ordered lock and get higher ordered lock together that because a dead lock so this concept is respected in many parts of the code which is in things like v mode v node flip lock and so on so all of these code has to respect this order but there are several other details of what the locking does what kinds of locks are actually required in each of those components that we are going to look at next。

So let's start with the webound locking So here we are trying to grab a lock when mounting and unmounting processes so this locks entire Vn and the main goal here is if you're trying to unmount a process when there are still active IO operations that is unsafe because there are still reading reads and write that are going through files within a partition and you're trying to unmount an entire file system so you don't want that to happen and this is done by using a lock and as is shown here。

 the way you actually do that is when you try to read you hold a concurrent log that's a read lock that's mentioned as TLL underscore concur So read operations and are essentially allowed to proceed in a concurrent fashion when you。

Whatant to do or write you are essentially going to use serial which basically means that you are going to wait for all the readers to finish and then you are going to be the only one that has the lock and then you can proceed and so you can use this to look create and modify and then exclusive essentially is actually a real right lock where you are going to block everyone else until。

Until the read is finished or until that write is finished。No。

If you look at the next data structure which is Vn or open file locking again you have similar concepts when you want to do a read or open the file and read mode。

 you are going to essentially provide lock the Vn using a read lock when you want to do operations such as create open destroying V nodes or i nodes you are going to use the serial mode and when you want to do write axis youre going to over the write lock so by and large reads use the concurrent read lock right use write locks and when you want to serialize operations。

 make sure they go on at a time you use the serialized lock which looks like write lock but it serializes operations。

Now as far as locking the flip object is concerned。

 this is the table that stores the file offset for each open file so there are two variables in here which is the flip code or the Ref count which is how many processes have opened that file for reading or writing and for each of that process you flipped position which is the offset within the file okay and in this case you are just going to use a mut text lock so essentially the locking order is going to help us in this case where。

You don't you basically hold a simple new text law。 And whenever you hold you have a flip。

Object processes file descriptor， you essentially lock the V。

 which implicitly means that the flip object gets locked as well。

And there are several other concepts there other data structures。

 there is essentially the log data structure itself and here you need mutual exclusion for grabbing the lock on because you need a log on so we assume here that our thread model is nonpreemptive which means all accesses to the structures are automatically automatic so that's how you going to implement integrity of the log object if you are doing a select that you essentially use one large global mutex which is a simple。

Solution， no concurrency allowed， and when you're talking about device drivers and so on。

 again you essentially access them in a non blocking fashion so you don't need a lock in this case。

Let me say a few words about how crashes are handled by the VFS process VFS process is also going to play an important role in all kinds of crash recovery when you device drivers crash when the file system process crash and youve got to do something because remember that the VFS process is essentially the process that is routing requests to all of these other processes which are device drivers file system processes and so on So you have to say answer the question what is going to happen if one of these processes crashes because the user process might still send a request to the VFS server and then the VFS server will find that there is no process to forward it so the way this is done is somehow the VFS processes to track and the health of these processes whenever they crash then you've got to see whether you can recover from them so now。

DiseDriver itself crashes， then the file system process that is interfacing with the device driver will try first to restart that driver and if it is not able to do that then the VFS process will try to restart the driver through a restart mechanism。

The character devices are similar process， but in this case is's the VFS process that's going to try to recover or restart these drives so those are device driver crashes so the either handled directly by the VFS process or the file system process that's interfacing with the device drive now you could also ask what happens if the server the file server process itself crashes in this case first thing is that the VFS server has to do some cleanup because the process is crashed all open files that are accessing data from that file system etc are no longer valid so you are going to mark them in。

 clean them up and so on and then all pending requests are also going to have to be terminated and then you have to try to restart the file server process and try to recover from the crash by making integrity checks and so on。

So the VFS process is going to be responsible for doing some of this and in this context I also want to remind you of another component that we had talked about a long time ago which was called the reincarnation server of the R process and the goal of the reincarnation server was also to restart processes when they fade so the VFS server is playing a role here the reincarnation server it would also have been used to do similar things。

Okay now I'll move on to talking about the Linux file system， etc ce。

 the discussion thus far has focused on the Vfs。The VFS Pro server process。

 but it is also instructive to understand how the Linux file server process is implemented and how it stores data on disk as part of the Linux file system。

So the interesting thing about the way this is implemented is first of all。

 the Linux file system is a completely user level process that works with the partition。

 it is written as if it's a network server process which means that it receives messages from in this case the VFS server。

 but messages could have come from anywhere else as well if so so the other good part is you can make modifications to the file system without having to touch any of the rest of the kernel which is a nice functionality that we have here。

 so long as the interface to the VFS layer is not changed everything else internally can be changed without having to know anything about the rest of Linux。

The other point that the Linux file system designers make is they return the process in a standalone fashion that you can actually move this to a non Linux OS as well because it's written and C you can compile it so it just looks like a process that is receiving messages from outside and then reading or write into partition so rather than receiving messages from the VSS layer。

 you could essentially easily turn that into on another system a process that's receiving messages from some other component and then implement a user space file system it's very easy to use this concept to implement a user space file system I mentioned this because as part of the process we will be looking at implementing a user space file system as well and so this gives us a way by which we can implement process and some data structures that are independent of the OSQ。

Now the picture on this slide shows us the layout of a Linux file system okay so essentially a Linux file system is created on a dispartation it is going to have all of the information that are needed to store files which as well as the metadata information such as iNot so as is shown in the picture if you think of the disk is sequence of blocks the first block is going to be the boot block the second block is going to be superb the next few blocks are going to store iNots so these are all met this is all metadata information and then all subsequent blocks are going to be data blocks where you actually store blocks of the file that's how the file system is laid out。

And in this context I want to mention that this data structure， nondata structure。

 this layout rather， is going to work for any type of underlying storage device。

 whether it's a USB thumb drive， whether it's a floppid disk which we don't use anymore， of course。

 or whether it's actually in hard disk or an SSD same layout is going to be used。

Now I want to bring back a picture that Ive shown you in lecture5 when we are talking about the boot process so this is the same picture as the previous slide but it shows you how that logical sequence of blocks is actually laid out on a disk a magnetic hardness because that's remember I mentioned last time that you have essentially track cylinders and tracks and sectors and so so you will see here that the first sector is essentially the master boot record that is a disk specific block that's not a file system block and then that has pointers to partition then you have essentially partition one that is shown here and that partition one is essentially this this block you can have multiple partitions in which case this array is going to be replicated in each of those disc partition so each partition can have its own boot block and super block and so on。

So that's what you want to keep in mind and you will see that the first block of a partition is the boot block。

🤧So the first block of the disc is the master boot recorder。

 so these are all concepts you want to keep in mind in terms of how blocks are laid out on a disk。

 how blocks are laid out on a partition in the file system。

So let's talk a little bit about each of these entities， the boot block， the superb。

 the Iros and so on Now if you remember again the discussion from lecture5 when I was talking about how the OS boot up so once you look at the master boot record on the disk it is going to point it to a boot partition the boot partition will actually have the first block as its as the boot block the boot block is going to have a little small snippet of executable the size of that boot block is over 1024 byte so it's two disk sectors and when you essentially start booting youre going to read from that boot block and read those instructions into memory and start executing those instructions and more details of how you figure out where the instructions are we actually discussed in lecture5 so I would instruct you to go back to that lecture and look at some of the。

we had on the lecture slides that gave us more details of how the boot process itself so once the system has booted。

 you are not going to use the boot block anymore that's only used in the boot process but the rest of the file system you' are still going to use which includes the super block and the iOs and things of that。

not all partitions have to be bootable but we still assume that the first block is the bootb。

 if the file system is not a bootable partition， then you will have an entry or a field in that boot block or a magic number that says this is not a bootable partition so there's no code to load from the boot block and but the boot block is always present regardless of whether it's a bootable partition which means it has boot code like the root partition or a non bootable partition like slash user where there is no boot code present。

Now the picture here shows us the super block of the Linux file system this is very similar to some of the concepts I was talking about briefly towards the end of the last lecture so the super block is essentially distinguished block in the file system that's always stored at the beginning of the file system so it appears directly after the boot block okay it has information important information about the file system itself so you will see it has things about iNots and what is the maximum file size and what are the number of zones and things of that sort are specific to that file system so when you create the file system you can actually specify this parameter but default the format program for the file system may have some default parameters but you could say create a file system with thousand i nodes or 500 i nodes and then basically you will do so and some of that information。

I's going to get recorded in the super Bowl。Now there are several data structures I should also mention the superblock。

 so although the superblock is stored on disk when you mount this file system。

 a copy of the superb is also kept in memory so that the VFS or rather the MFS or the mini file system process can use it to access other information。

And whenever you modify the super block and memory it has to be written back to this schedule。

Now the file system is also going to maintain many data structures in the form of bitmaps that allow us to track things like free iNots and free blocks in the file system and things of there so so the in Bimap tells us of all the iNots that are kept。

 which ins are in use which means they are actually far valid files and which iNots are empty。

 which means they can be used to create new files。And as far as disc blocks or the data blocks for our files are concerned。

 they are allocated in terms of2 to the power and blocks。

 so you allocate them in chunks of2 to the power and these chunks are referred to as zones in context of Linuxs。

 so you basically have multiple zones and then in each zone you can actually have specific blocks。

Now this zone concept allows us to allocate blocks next to one another when you create a newer。

 that's merely a urusistic it's not a requirement， it allows us to not have the blocks of a file spread across the disk which can increase seek overheads if they were stored on the magnetic disk and so on。

Now to create a file， you first try to get a free in and then to allocate data for the file。

 you order to scan the list of blocks and try to find at least one free block if not a sequence of free block and the point are to some of the data structures are actually there in the supern。

 as if you go back to the previous slide here， you will see that towards the end。

 there are some entries that point to the in bitmap and the Zoom bit those are the last two entries in the table that shown in this super block picture。

Okay now here is a picture of what an in looks like The concept is very similar to the multile index inode I showed you last time so the first few entries of the inode are going to store the user who created idea the user who created the file the file and so on you essentially each the size of the file access time of the file last modification time and so on and then you have block pointers which are called zone pointers here you will see that there are seven direct pointers referred to as zone zero through zone6 those are direct block pointers。

 the point to blocks that are stored on desk so if your file has less than six seven blocks you are going to access them to direct point if it grows beyond seven you are going to have indirectrant zone pointer that itself going to point another block where there are multiple pointers so your one level of indirect and then you can also have double indirect。

As I shown here there is an unused entry that is kept for future use if you want to support even larger files in the file system。

 you can use that entry to create a triple indirect which is also what I mentioned in the last class。

 so exactly the same concepts are true here。Now， one interesting thing you have to note here is。

As far as the in is concerned， each in has an ID that is the number that that is a unique ID for a file so essentially from the file system' perspective files are numbered and the number of a file is essentially the in number okay so if you type LS minus I on any Uniix file system you'll essentially see file names with the in numbers that are associated with that tell you internally how does the OS identify files file names are the mechanism by which users identify file but the OS itself or the file system uses numbers that are associated with the file to identify。

Now the interesting thing here that you will see in this picture of an in is the file name is actually not included in the in itself because file node the file names are actually kept in the directory structure so think of a directory as a table where for each file in that directory you have a file name and that file name points to a numbers are stored in the directory and once you have the number that is associated with the file you look up that specific in and then you get this data structure it gives you access to all of the other information in the file so the important point I'm making is the name of the file is actually not stored in the in itself it's stored in the directory。

Now as far as how to get to a specific Iode because iOs are kept in a known location。

 you can and there of a fixed size， as you will see here there are 64 bytes inside size。

 you can directly find the location of a Iode specific Iode， so going back to three pictures。

So you will see here in this picture in the file system layer the inode is essentially stored right after the superb and each block data block on the disk is 1024 bytes each iode is 64 bytes and so you can essentially say find the offset of every iode because they are stored in sequence in other words there is no table telling us where inode 17 is stored you just compute that using a simple equation it's offset 64 times 17 starting with the beginning of the inode blocks that are shown in this picture so that is how once you actually go to a table directly and find the file name and find its file ID or the iode number you are going to index into these blocks or specific offset and you can read that iode from that location。



![](img/790b5f19d8d66c4299fb6f757748717e_5.png)

So there are a few other data structures to keep in mind was what does the file system block cache and I mentioned that both when we talked about device drivers as well as very briefly last time and this is basically an LRU cache which cache is recently read data blocks for a file for by the file system so the idea is if you're going to repeatedly do i on the blocks。

 you don't have to read it over and over again from the disk you keep it in the buffer cache and then you just modify a read from that buffer cache and then remember also last time I said you modify a block it becomes dirty and dirty blocks can be written to the cache using a write through or write back mechanism most file systems opt for performance or a and goes right back so when you write to a block of a file it's only going to come to the buffer cache and modify the corresponding cache block and then the right is going to return。

At a later time the block is going to get eviced from the cache and put on this or you're going to have a sync operation that writes it to this or in many file system of your periodic background process when there's no file activity is going to write out all the dirty block so that they eventually go to this so that's some of the block cache is actually implemented。

Now the file system looks like any other Uni file system。

 which means that there are partitions each partition has to be mounted using the mount operation before you can actually access that okay so the mount operation essentially takes a partition and attaches it to some part of the file system hierarchy so that's what is shown here saying you have a root file system and then you mounted slash user file system and then you basically mount two more file systems which basically allows you to。

Extend that file system hierarchy so from the user's perspective they don't actually see that different partition amount and it looks like one uniform file system hierarchy starting from slash and then you just descend down the hierarchy and the fact that your crossing mount point etc is only known to the OS but you don't actually see this unless you know that there's one point exclusively。

So as far as the mounting process is concerned you use the mount system called to do this and you will mount using the UMo system called。

 there are all kinds of issues that can arise such as errors and you try to mount and so on and all of those things are essentially going to be handled by the VFS layer theres a list of these shown here。

 but I'm not going to go into the details of this error handling except to say that they are implemented within the VFS layer and specifically in many cases。

 the files server or process that implement that file system functionality。

Okay so with that I'm going to end the lecture on Manex file system so just to briefly recap we talked about two concepts we talked about the VFS server process and how it uses the VFS switch concept to implement to allow multiple file systems to be implemented each file system is also its own server process or each mount file system。

 its own server process they collaborate with the VFS process to implement file system functionality and I talked about the Linux file system that is the key file system that Linux implements and how that implement some of the file system functionality using a user server process so well end that discussion here today and then next time we'll talk about a new concept within the OS which is networking。



![](img/790b5f19d8d66c4299fb6f757748717e_7.png)

![](img/790b5f19d8d66c4299fb6f757748717e_8.png)