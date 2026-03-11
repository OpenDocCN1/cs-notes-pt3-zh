# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p32 -32-Lec16 Video_ Minix I_O and Device Drivers (03_17_20).zh_en -BV1iP2CBaEHr_p32-

![](img/628a5944565a9bc86bcda7bf64db469c_0.png)

Okay， so in today's lecture， we are going to continue our discussion from last time where we were talking about the IO subsystem and today we are going to focus on the Linuxix subsystem。

 and we are going to look at both the device independent IO subsystem code within Linux as well as the device drivers that are presented Minix and how they are implemented and so on。

So。What this slide shows us is the highlel layered architecture of the IO subsystem in Linux and as we can see at the very lowest level we actually have the hardware which are the IO devices in this case。

 the hardware typically interfaces with the rest of the machine through interruption and hence as well as the lowest layer of Linux is concerned within the kernel we have interrupttanglers and those intertanglers interface with the device drivers as well as upper layers in the IO subsystem software type。

Setting above the inter handlers are the device drivers and theres a device driver for each device as we have seen last time a device consists of the device itself and a device controller and the device driver is responsible for interfacing with each device so we have this device driver layer and onede driver per device that is ordered to be interfacing with the device itself a device driver includes all the device specific code all the specific details of how to communicate with the device and capsulated in each device driver。

Setting above the device drivers is the device independent OS Sc。

 and so this is scored as we will see that deals with devices at a higher level of abstraction such as block devices and character devices as well as interfacing with user level software and so on。

And then about this as the user level software， eta。

Now this picture although we are discussing it in the context of Linux。

 is actually general and any OS kernel will employ this architecture for interfacing with devices now in the Linux specific context some of this code that we see in this stack is actually part of the kernel。

 some of it is in various system level tasks including device drivers that we see are user level processes。

 the file system tasks and so on， so we are going to see how this picture is realized in the Linux context by taking these various layers and putting them in different components within Linux。

So。As far as the highest level layer is concerned which is the device independent layer。

 there are several different functions in it， as is been shown here。

 you need a uniform interface to communicate with all device drivers because this code is independent of any device specific details so it needs a standard interface to communicate with all other device drivers and it includes other functions that are common across device drivers such as buffering which we saw last time it's used to deal with mismatches between the device speeds and the CPU speeds it includes error reporting or error handling because I devices are slow and you're dealing with hardware that could be errors and then youve got to decide how to deal with these errors so some of that is encapsulated in this layer and higherle task line allocating and releasing devices。

decidingiding the size of the block that is used to communicate with the device server。

 all of these functions are actually handled and the device independently。

Now this picture says a cartoon picture but it tries to illustrate how device drivers are built in two different contexts。

 one is where the OSs does not have a standard interface and one where there is now the first picture is supposed to illustrate how you can build device drivers even though the OSs does not provide a standard。

In this case， each device driver implements device specific code but exports its own interface to the rest of the OS and the interface is one that makes the most sense for that device。

 including how you write to the device， how you write to the device。

 how you can send other kinds of commands to the device and so on now the。

The Lego like pieces since they are of different shapes。

 what this is supposed to indicate to us is that the interface。

In terms of how the device driver interfaces with the rest of the kernel is different in case of each device server。

 because each device driver is doing its own thing， it has its own interface that it has implemented。

Figurd on the right， which is labeled B， actually shows a different。

Way of implementing device drivers in this case， the OS kernel has standardized the interface for device drivers So what that means is the OS has said the kernel has said that all device drivers must support these functions that are used to communicate with it and every device driver has to adhere to that standard so there's a common way by which the rest of the OS actually interfaces with device driver and hence every device driver has to support exactly the same interface and all of the details of how those interfaces are realized are inside the driver so that interface needless to say must be general enough so that it supports a large class of devices regardless of the hardware details in the first。

Fure each device driver could implement its own interface。

 which means that you could decide based on the type of the device what the interface should be and some devices could have more functions in their interfaces and some less in the figure B。

 every device driver supports exactly the same interface in some side it has to be a union of what you need from all of the devices that you want to support in your system。

Now， I should also say that most operating systems used to in the old days did not have a standard interface。

 so they look more like the figure label A， but now pretty much any general purpose OS has a standard way by which you implement a device driver。

 so they look more or less like B so that is going to include Linux as well。

Now as far as the user space IO is concerned， remember that Linux is a micro kernelnel so as we' have seen in the past and I'm going to show you again。

 many of the device driver， not many all of the device drivers actually are implemented as user space processes most of the kernel tasks are also implemented as user space processes and so so a lot of the IO code actually resides outside the kernel there is still some code that is inside but a lot of it is outside So it's instructed to see how a typical IO request is handled in the context of using user space software and so on so this is a layered picture that shows how requests from user processes are handled in different layers and then all the way down to the hardware and all the responses so at the top level you have the user processes itself it could be any process that is trying to make an IO request let's say for simplicity you're trying to。

from a fight， that's an I request。So the user process is going to issue the read request that's going to come to some device independent software in case of Linux。

 this is going to be a system process that typically is going to be a file system process。

 which is going to basically handle your read request and the device independence layer in addition to interfacing with user processes in case of Linux is going to implement various features that I discussed two slides ago which include things like naming and protection。

 deciding block sizes， implementing buffer cacheiers and so on。

So this device independent software then takes the request and decides determines rather which device is supposed to handle it and it handed it off to that right device driver。

 so remember that there will be more than one device in your system there could even be more than one disk in your system in case of a read call you have to decide which device that your request is could be handled by and order to hand to the specific device driver。

So in this case the device driver is responsible for implementing device specific code in terms of how that command read command in this case is going to be issued to that device and so on。

 it will have the ports that we had discussed last time that allow you to read or write data have status register command registers and so on。

 so the device driver is going to set up this device register and then maybe wait for an interrupt to come from the device when the request is that。

So once the command has been issued， you just wait in the device driver and then eventually there is going to be an in from the device controller that tells the device driver。

 the request is finished and you see that the reply is now going to percolate up from the device driver back to the device independent software and back to the user process where it is going to receive the results of its read command。

So now let's look at some more details of how some of this is implemented in Min as I mentioned。

 Min device drivers run in user space and you've seen this previously as well because the kernel is bareboards it implements a system task a clock task and some IPC。

 everything else in Min is actually handled in user space so all device drivers run in user space there's one process for each device server so each device driver is simply a user process。

So what this also means is that device drivers cannot actually access either kernel memory or IO ports this is of course different from monolithic kernels where the device drivers not only sit inside the kernel they are the lowest level of the kernel and they are directly interfacing with the hardware in this case although that highlevel concept is true device drivers are not neither inside the kernel nor are the lowest layer of the kernel they are sitting outside in user space and yet they must somehow access all of the devices and do whatever a typical device driver does。

So what this means is user space device drivers need a mechanism to communicate with their iO devices。

 but all of that has to go through the kernel and depending on what the device driver is trying to do there will be different levels of access it might need so for this slide actually it talks about four different types of IO accesses that are typical device driver。

The first one is the device driver simply needs access to some memory that's outside data space。

 This is not for interfacing with an IO device， this may be for other reasons so for example we are soon going to see a Ram disc driver where the data for this Ram disk is stored in a different region of memory and the device driver here will need access to that piece of memory so that's the first kind of access the second type of access is what a typically device driver does which is the ability to read or write to iO ports and since IO ports can only access through the kernel the code for accessing them even in Minex in the kernel and the device driver has to essentially use kernel calls to access。

Acces these aisle ports。The third task that a device driver has to perform is handle interrupts typically in a monolithic kernel when the device controller issues an interrupt you essentially go to the interrupt handler which is typically handle by the device driver in this case the device driver is a user process so the hardware interrupt is actually going to come to the Linux kernel not to the device driver and the Linux kernel needs to be able to handle this。

interrupt by essentially forwarding it to a device driver so all device drivers need to be able to handle interrupts and here we are doing a distinguish between predictable interrupts and unpredictable interrupt。

Predictable interrupts are one that you know are going to arrive because you have let's say an IO request outstanding if you issued an IO request the device driver is going to wait for an I interrupt that will signal its completion so that's in our case a predictable interrupt。

Unpredictable interrupts are those that we don't know when they might occur examples might be network packets arriving on your ethernet interface card。

 you don't know when communication is likely to occur a packet might arrive at an arbitrary instead or a keyboard interrupt is also an unpredictable interrupt because you don't know when the user might type the next keystroke it may happen in a few seconds or few hours and the OSs is not neither the OSs nor the device driver actually knows when that is going to occur so we will refer to these kinds of interrupts as unpredictable interrupt regardless of whether interrupts are predictabletable or unpredictable they have to be handled by the device driver with sets in user space and the way this is going to be done as we will see shortly is through messages that go between the kernel and device drives now。

Having said that all of the accesses that device drivers need from the kernel are actually implemented in the system task within theix micro kernelnel and let's look at each of these four types of iaxes in a little more detail so the first one is where the device driver needs access to some region of memory that is outside its address space and the example we gave here was one of a RAis so in this case we are going to leverage a functionality of the system task because the system task is within the micro kernelnel it has the ability to access any process segments belonging to other processes accessible to a given process so we are going to use that functionality to take let's say memory segment belonging to the RA disk which is essentially going to be a piece of memory and make it accessible to the Ramdi driver normally you would not be able to do this because the Ramis。

is a user process that can only access its own stack and heat it kilo access some other region of RA and in this case the RamMdik resides outside the address space of the Ramisk driver。

 so we are going to use the system task to make this possible。

Another example where this is needed is where the console driver or the graphics driver really needs access to memory belonging to a video adapter or a GPU Para card so in this case the graphics card memory is not going to be accessible directly to the。

Driver， but the system task can take that piece of memory and make it accessible to the driver so that it can directly read or write to it。

 whereas you could normally not do that。So the second concept is where the Min kernel has to provide access to IO ports to device drivers and typically IO ports are going to be not accessible to drivers in user space。

And again， we are going to leverage the system task that is going to perform IO on behalf of the device driver and we'll see how the hard disk driver is actually going to use it to perform IO through the system task。

The third thing that we have spoke about in the previous slide is where you are the highly predictable。

So here again we are going to leverage the system task so the system task has a generic interrupt handler which is called generic handler that it has instantd any interrupt that comes in is handled by this generic interrupt handler and it is then going to convert this interrupt into a message specifically a notification message and send it to the right device driver for handle so interrupt essentially become messages messages are then sent to the drivers and then each driver is essentially going to be sitting in a loop waiting for a message or is's going to be doing a blocking call which waits for a message from in this case the system task and when that message is sent to the driver it's going to receive it and handle so this is how we are going to allow interrupts which arrive at the microcuror to essentially get forwarded to a device track。

And the last type of IO access that a device driver needs are ones where you need to handle unpredictable income。

And because by definition， interrupts。And then Linux are any other OS for that matter unpredictable。

 you don't know how frequently they occur。 you might have a second interrupt when the first one is still and a process and so on and furthermore。

 you don't even know the source of where the interrupt is coming from it may come from any device for example。

 an ethernet card a keyboard a mouse and so on。 So the way you have to deal with this is slightly different from a predictable task a predictable interrupt in a predictable interrupt a device driver knows that the interrupt is going to come from a specific device because it has issued a command to that device it is expecting an interrupt to come from a device So it can specifically do a receive for a message from that device in that case of unpredictable interrupt you cannot you don't know where the interrupt is coming from So you cannot receive from a specific device because you don't even know which device is going to cause the interrupt So you have to deal with this somewhat。

So so you can do several things First is that interrupt handlingling has to be fast because the longer it takes the other interrupts that are also unpredictable and that arrive in the meantime and not get handling so you want extremely fast interprettangling you want to do both non-blocking sends and nonblocking receives because you can do it equivalent of things like polling or asynchronous receives so that you don't actually block on a specific device and a combination of these methods are actually used in the context of Linux to handling。

P predictdictable interests。Now this picture having with those concepts。

 this picture shows us again how device drivers are implemented both in a monolithic kernel and in Linux so the picture on the right shows us a typical monolithic kernel and you see the horizontal line is the one that divides kernel space from user space。

 everything about that line of user processes everything below is the monolithic kernel so the way IO works is user processes issue IO requests if file IO request or do something that triggers IO the request then comes down to the kernel in this case the file system is known to receive that request it translates it into a read of a block。

 it hands that to the device driver so that's how a device driver is or receive that request and handle it。

Now the picture to the left label A shows us how Linux device drivers work and as I already mentioned。

 the only thing we have inside the kernel is a very bare bones micro kernel which has basic capabilities for handling things like interrupts and message passing and so on as we can see the device driver is a user process that sit outside the kernel the file system is a user process or a system process that sit outside the kernel and all user processes on outside so in this case when the user process issues a read call it is going to arrive at the file system process the file system process is going to hand back to the device driver to perform a disc the device driver is going to essentially issue a request to the device diskcontroller through the system task and then it's going to just wait for an interrupt to arrive the system task at some。

Later point is going to receive an interrupt from the diskcontroller saying that your read is completed and that is going to be received。

 it's going to be turned into a notification message and sent after the device driver。

 the device driver is expecting this interrupt so it's sitting in a receive waiting for this interrupt and the message is received it's going to handle that interrupt。

 get the contents of the read hand that to the system task file system task step5 and then in step six which is where the read。

Finished from a system perspectives hand the contents of the reader handed back to the user process。

So you can see how an IO request involves multiple components that are basically used to handle the request。

Now delving into a little more details of how Linuxix drivers work， each as I already mentioned。

 each driver runs as a userbased process for each type of device there is as a driver because you need driver for each I device and each of them runs as a full user process they communicate the system task through message passing and typically well see that simple drivers can be written in Linux and just a single file and you will score if you go through the drivers directly in the Linux in the Linux GitHub you will see that there are several folders。

 each folder represents a device driver I'm going to talk about some of them in this class but I would encourage you to go and look at the source three for Linuxix and look at how some device drivers are written and you will see that simple ones and maybe one file and some are maybe more than one but by and large simple ones。

return in a single file which means theyre fairly simple and compact to write now as far as the structure of each of these drivers is concerned each of them has to accept requests from other processes could be the file system process or the currentren system task or something else and carry out whatever request is actually being sent to them all drivers in Min are strictly sequential they do not support concurrency to keep them simple so some of the synchronization primitives that you might need in a multithed kernels do not not required in minutes it's much simpler to write a device driver and by and large as I said they need to do three things they need to receive a message they need to process that message and send a reply。



![](img/628a5944565a9bc86bcda7bf64db469c_2.png)

Now each device driver needs to it gets two types of request。

 a work request that comes from either the file server process or something else and interrupts that come to the device driver from the cur。

 So these are the two types of request or messages that the drivers can receive and you will use the receive。

Call to essentially receive interrupt messages as well as other kinds of messages and while you' are handling any request whether it's interrupt or some other request because this is single threaded and sequential all other requests are going to arrive and just wait so youre basically theyre going to keep them pending and is especially true during interrupt handlinging but also during processing of other requests so it is essential that the processing of requests happen quickly because there may be things that urgent interrupts that are come in and if have to wait for a while that makes the system less responsive。

So this。Slide just as shows us some example types of messages that a device driver。

 a generic device driver needs to handle。 I'm not going to go through all of them。

 but I just want to to look at these because the first table here shows us the request messages that are saying and the second types and shows us some of the reply messages and you will see that typical fields of a message I will include things like the type of the message which is going to be the operation that is requested that is essentially the device number that is basically used to address the device I should mention here something that I should have mentioned earlier that devices in Uniix in general as well as Min are going to be numbered So each device has a number and typically what you have are something called the major number and a minor number for each device the major number for a device tells us the type of a device so major number one could be disks major number two could be graphic card。

Then three could be network cards and so on so those are classes or devices and a minor number refers to a specific device within that class so you might have major number one which is disc class and minor number one which is disk one of the disc class or device one of the disk class and so on so in this case the device field that is shown here is actually the minor number which is specifically addressing a certain type of device you don't need a major number here because the device driver already knows what type of device it is behind so it needs to just know which device within that class to actually send that request to or is that request meant for。

And then you have other fields like what process request that IO the byte count or the Iocal code which I'm going to talk in a little bit position of the device and so and as far reply is concerned again you the reply time which is what kind of a reply it is typically in this case it's always going to be driver reply saying this is a reply from the driver and then it's going to talk about the process number and what bytes。

 the status next and what bytes how many bytes are transferred of the。

Now this figure the slide shows us a typical pseudocode of a device driver and you will see that all I drivers essentially involves sitting in the loop waiting for a request to arrive and that has basically been done through the receive call saying I can receive any message and then once the message has been received。

 you essentially look at the type of the message and then you hand it so you could have a read message or write message or other kinds of message so you basically do whatever you need to do to handle those requests in this case if it's a read you call a device read which is where the code for actually reading from that device is implemented in the driver and so on。

And then once you are done you basically send back a reply。

 that's the last line of that while loop and then you continue and you accept the next request so it's a strictly sequential while loop that implements a typical device driver and meics and what we are going to do is actually soon look at several types of device driver and try to understand how some of the code that is implemented by the device actually differs from device to device。

So youll specifically look at three or four different types of devices。

 two block devices and two character devices so we look at block devices are concerned we look at the Ram disk can harness driver as well as character devices are concerned we look at the terminal driver and keyboard driver now recall that from the last class I mentioned that all devices are either going to be block devices or character devices block devices are those where the unit of i is essentially a block of data and character devices are those the unit of i is one character of one byte at a time keyboard is an example of a character device because each key press generates one byte that tells us what that key press is。

Whereas a disk is an example of a blog device because you' are reading or writing entire blocks on data from the disk at a one time。

 so keep that distinction in mind because we are going to look at how Linux implements block devices as well as character devices and we look at four examples。

In a little more detail now before we get to whether there's a block device or a character device。

 let's start with a device independent layer。Now in case of Linuxix the designers decided that iOS handling is closely tied to file system file handling because the disk is a very common device that is present in all machines and this IO certainly is very closely in to file so what they decided is all device independent code is going to sit within the file server process now this is simply a design decision there is no need to do this you could have had a separate iO process that did IO handling and the file server process that just specifically looked at file system handling but in this case they put all the code the VFS process or the file server process and we are going to get look at the file server process in two classes from now。



![](img/628a5944565a9bc86bcda7bf64db469c_4.png)

So that's something you want to keep in mind and the VFS process implements the device independent layer that I showed you this picture earlier in the class where。

Some generic handling of interrupts and so on is actually implemented。

excusecus me the handling of interrupts is done by the device tri。

 but the device independent code is implemented within the VFS VFS process。

So here is now a simple pseudocode for a block device driver and you' will see that this structure is not different from the pseudocode for a device driver that I showed you earlier clearly the pseudocode for the device driver is going to apply to both blocked devices and character devices so the structure is by and large always going to be very similar and here we have a generic pseudocode for a block device driver again you see that there is an infinite while loop where you sit and you receive a message and then you look at whether it's a read or write and now you're going to essentially look for devicespec or block specific reads and writes and then youre going to call those messages and what you see here are essentially function pointer so so in the case read you see something that says star entry point pointer they read so that star entry is essentially a function pointer which means that you can use this code。

To call different leagues for different types of device file， because it a general sort of。

So you can essentially instantiate with functions for handling there disc block drivers and other kinds of block drivers like graphics cardss and so on。

 so this gives you a very generic structure to implement these various kinds of IO requests。

And then once you' are done handling this， you are going to also just send back the reply through to a send command So what is also shown here。

 but now as a comment but without any code， in addition to readwrite。

 of course you have to do other things like open a device。

 close a device it'll talk a little bit about I controller ioctails in just a little bit。

So typical block devices need to handle six types of operations so within that my loop that I showed you in that switch statement you will have to handle a readr but you also need to handle open close iO control and scattered I so I think the names of these message types indicate what the operation does open says you open a device for IO just as you open a file for IO the device driverer also has to open a device for IO close tells you that you can close the device are done when the device read and write allow you to read or write to the device IO tells or IocCL which are called IO tells or IO control our message that allow you to get and set parameter specific to the hardware so for example you might have things like transmission speed to the device parity of the device in some cases you might be able to set the chunk of data that。



![](img/628a5944565a9bc86bcda7bf64db469c_6.png)

Use to sell it or right to the device so some of these parameters can be controlled through software and the command that is used within Uniix in general as well as Min is called Iocts or IO control so that is implemented by every device driver to allow you to change device specific characteristics that you might need to control after boott at rent time when the last operation is called scattered Iio and this is basically an operation that is part of a general concept called scattered gather Iio。

Now， in scatterga I， what happens is you are trying to read multiple blocks or write multiple blocks at a time。

So what happens is rather than reading or writing one block at a time you issue concurrent requests read requests so you basically scatter them out they go off the device let's say the disk and the disc performs concurrent reads and then you gather all of the responses and you construct one reply message and send it out so this is called scatter gap So you allow it's essentially one way to think of this is batched IU you batch multiple requests and you send them out because they random the scatter。

 meaning they go to different locations on a disk in case a disc card if you're trying to write to different parts of a screen they will scatter to different portions in a graphic card and then in case of a disk at least you have the gather operation where the replies come back and you essentially gather all of the requests and so devices such as disk are going to implement this operation for more efficient I。

And basically ba this request and get higher throughput。

 so this is going to be an addition to the read and write which allow you to read one block at a time or write one block at a time。

So with that concept now let's look at some specific block device driver。

 we'll start with a simple one called a Ram disk Ram disk is very similar to hard disk except that the contents of this disk set in memory Now clearly memory is a volatile device so you cannot actually use it for longter persistent storage of files so you're not to use RA disk for as a temporary storage region but this portion of memory essentially looks like a disk rather than memory now what's the difference between a disk and memory in case of RA you can address individual words and Ram so you give a memory address in terms of a pointer and you can go address that specific memory region Now disks are block devices which means that the granularity of i is one block you cannot access one word or one byte within the。

the IO operations as you read the entire block or write an entire block。

 So so when a region of memory is being used as a Ramdes you can think of iO being done in terms of blocks or essentially pages or something like that where you can only the Ramdes driver allows you to read the right entire blocks not not portions of a block at a time so that's something you want to keep in mind So now why are do you need Ram disks typically most of your files are actually going to be stored on a persistent storage device such as actual hard disk but Ram disks are especially useful when you are booting your machine So before you have access to the hard disk you can construct a temporary Ram disk。

 you can load the boot image which is the kernel part of the boot image or other things with the boot image into the Ram disk So now that portion of memory looks like a user process。

So it looks like a hard disk and you can then access that hard disk through through the RA disk as if you're reading or writing files to the local disk。

So so that's the concept of Ramis and it is used by most Uni like operating systems for access to files during the boot process before the actual hard disk becomes available so you basically bootstrap the OS through a small ra disk then you access the hard disk and then you can load the remaining files from the hard disk so so so now as far as the Ram disk driver is concerned the typical block driver is going to read or write a block the Ram disk is going to。

Essentially have a pre allocatelocated region of memory where you can read or write these blocks and then there's a file system that is going to be running on top of that Ramis Now the Linuxix Ramis driver actually uses six much more simpler drivers to implement Ramdi functionality and those are listed in the slide and each of them looks like a device so if you remember what I said last time you basically access devices to a file name and the file system interface all devices are essentially present in the s de directory within Minix or even in Uniix and the name of a file tells you what kind of device it is and we have six different devices that are accessed to a slash dev interface and that implement the Ramis functionality so s Ram is the actual Ramis so that device is going to essentially when you try to read or write to that device it looks like a file because it looks as a file name and。

Quote unqu file essentially points to a Ram disc in memory so you can basically go and read or write blocks from their Rs slash de slash memory is a device that essentially allows you to access physical memory by addressing it。

Now， this is essentially only accessible to the kernel and the kernel can use this interface to actually read write to specific regions of memory。

 The R driver is also going to use this this device s slash kmen， as you can imagine。

 is essentially a device that refers to kernel memory。

So this is the part of RAM where the kernel resides and that entire region of the kernel ladder space is exposed to the RAis driver through a device called slash their/lash kman so in this case byte off so again it looks like a file。

 the entire region of memory although it's not really a file it's just a region of memory and you can offset any byte and that points you to a specific region of kernel。

Slash de slash boot is a device that is used during boot time。

 It holds the boot image and your two other devices s s null which is an output device that allows you to out write on output and the output is discarded and slash de s0 which is an input device basically if you try to read from the device it's going only allow you to read a zero every time so typically it used to0 or regions of。

So the cord for the Rammbish driver is in the driver's folder in the Linux sub and you can see it under the RA disc and the memory folder that is scattered between those two because as I said。

 the Ramish driver uses six different devices to implement its functionality。



![](img/628a5944565a9bc86bcda7bf64db469c_8.png)

the next driver that we are going to talk about is the hard disk driver now typically you have different types of hard disks。

 the old style has been magnetic hard disks which are spinning discs that look like c arms they are circular platters that spin and you have data thats written to them in terms of cylinders which are essentially platters each cylinder essentially has concentric circles that are called track right data on the track and each track is divided into sectors we are going to look at disks again in the next class and I'm going to show you some pictures that illustrate how this are done but for the purposes of this class all we need to know is the hard disk driver takes the disc geometry which is cylinder track and sector and disc addresses which are essentially going to refer to cylinder number a track on that cylinder in a sector and just turn that into a linear address single space which is。

Lo block accuracy so essentially you can take all the sectors on the disk doesn't matter what geometry they are in and you can just number them0 through n and now you can just access them as sector0 and sector1 and sector2 and so on those are logical addresses and they can simply be translated within the device driver to physical addresses which are each logical block number essentially becomes a sector a track and a cylinder number so that mapping can be done internally so devices the hardest can be accessed either through through logical block address or through physical block addresses。

Now within minutes the code for the hard disk driver is in the 80 slash W and need folder and that essentially refers to Winchester drives because another name for hard disk in the old days used to be Winchester drive and that is where the code is stored and the thing I do want to mention is it's from a hardware perspective you can actually a more than one disk connected to machine so you can have more than one ID disks or more than one seta disk Seta is just aron that stands for serial80 attachment it it's a hardware standard that allows you to essentially interface with a disk so you can have up to four disks and to figure out which disk you're reading a writing tool as I said you're going to have a major number and a minor number So slash devlash c0 d0 is going to refer to as the first number C0 refers to。

the class called this and D0 says disk zero in that class and D1 will say disk1 if you're more than one in your machine so I would encourage you to actually go into your Linux virtual box Vm and type the Df command and you will see a whole bunch of devices that are mounted and you will see things like s dev slash D0 which is the disk and you might see additional suffixes there it say that's a partition within that disk that get mounted as the root directory and so on and so forth。

Now that this driver has to interface with the disk controllerroll and the way youre going to do this is the controller will essentially have ports as we mentioned last time each device a ports。

 will have controller register， which is a control port where you can essentially。Saend complaints。

And the table here shows us the different types of register values you can write and what they mean so you can essentially have multiple registers in the control register not not just what in the case of the ID hard and you can essentially say I want to do or I want to do right and you can specify the address either in the LBM word which means it's a logical address or you can specify them as as a cylinder track and the sector which is a physical address you can address either way typically you would like to do it logical and then the controller can do translation for you so again this slide essentially shows us the fields of the drive and head register which basically again which tells us how you actually do the addressing the device which driver has to read or write registers here in this case to this values the specify addresses of what you're going to read or write。

Okay， so again， you can use the LBA mode if the LbaA field is zero。

 you're essentially using the cylinder head sector mode if it's one year more using the LBS trial。

So I'm going to now quickly move on to two other types two other types of devices which are terminals and keyboard so typically they character devices but we see that terminals don't have to be they can be block or characters what this figure shows is the various kinds of terminals a terminal is a generic concept within units that refers to all kinds of monitors where you can actually see output from your machine and then there are different kinds of monitors that have evolved over the ages and you will basically see that some of them are memory mapped interfaces some of them use serial R232 interfaces still others use network interfaces monitors or terminals can come in many different flavors depending on whether they're connected to a graphics card in which case they become memory mapped terminals whether they are using a simple R32 serial interface is that the old style terminals。

you can simply see a character console but nothing more that uses an R232 interface or you can actually use an actual network to communicate with the remote terminal in this case X terminal where the communication to the terminal actually goes over a network and so terminal drivers as you can imagine are quite complex depending on what type of terminal it is how you are communicating in that terminal so so let's go into this in a little more detail。

So this figure here shows us memory map terminals so this is the standard kind of monitor that you will see today where you have a graphic card or a graphics adapter and you connected a monitor to that graphic card so keep in mind here that the input and output are different the input is coming from a keyboard so theres a keyboard driver thats separate and then the output is going to a graphic card and the graphics card is displaying that output or to a monitor。

So you will see that the graphics card essentially has some video memory thats separate from physical memory so the video Ram or the graphics RA is separate from physical memory and typically to output something to a monitor you have to write to that video memory and based on what you've written the graphics controller is essentially going to take that content and display at the right location the monitor when typically these are memory mapped that if you remember what I mentioned last time a memory map I essentially means that you take the device memory and you make it as part of physicalm so in this case video Ram just becomes an extension to physical Ram so you can think of physical actual RA and video Ram and you concateate the two so you have one larger address space and so some addresses when you write to those addresses you write to video Ram some addresses when you write to them or read from them you basically。

Psical so so you are using memory map I， which makes it very simple to write to a graphics card。

 you just write to a specific address and then the graphics controller simply outputs whatever you return to the screen。

So here is an example of a very simple character display displays come in two types。

 one is character and one is bitbap character display simply show you it like a console or external you simply shows you characters So in this case you are not outputting pixels you're outputting character so you can write eight of the screen and it's going to display A And so so what happens is you take your screen and essentially you have a screen that is in this case show to your right it has 25 characters sorry 25 lines by 80 characters there are so you can output the number of characters you can output is 80 by 25 so you can think of that as an error。

So your video Ram is going to essentially mirror what is the screen so there's an array in video Ram and you can essentially write a character to think of this as a two dimensionmensal array So if you write a specific character to a specific region of that array that character is going to be displayed at that location on the screen so there is a one to one mapping between the two dimensionmensal array that is represented by the video Ram and what is actually represented on the screen so to output something on the screen you're simply going to write to a specific region of this video Ram where a specific location of this two dimensionmensal array in the video Ram and the corresponding character is going to be shown so what is shown here as you can see is at the bottom you' essentially written ABCD and then ABCD appears on the screen and the mapping here is from the lowest line of the video Ram as the top line of the screen ignore that for a moment so you can write any region and that character is going to appear。

So so that's how you can work with character displays you have other kinds of displays are big So those are the displays we have on our laptops from our phones and on on our desktops So here rather than writing characters the screen is essentially a set of pixels and so each pixel can be written to individually so you can essentially decide the color of the pixel and the and so on and then you have video Ram where each so again it's a two dimensional array but each entry is now a pixel as opposed to character so you can address each pixel individually by writing a value to that pixel and that value is a color code so you can say it's you can the color code specifies what color of the pixel is going to display on the screen so simply by writing to that video Ram you can essentially change the color of any pixel and so on on the screen。

So those are memory mapped terminals you also have character terminals or other Rs232 terminals where these are character terminals but you are not using a graphics adapter you're using a serial interface as shown in this picture the terminal actually in this case is the one shown to the right it has both a display and a keyboard so it is basically both an input and an output device and you have a serial cable that is connected from a computer to the terminal the serial cable allows to make communication it allows you to send characters to the screen。

 it also allows you to read keyboard input from the keyboard and and read it here so you have a Rs 232 driver that is basically going to take whatever characters you're writing that converts it into the serial command sense it over the serial interface the serial commands are basically using a protocol called。

You art， which you really don't need to go into， but you art allows you to do serious communication。

 so it allows you to go transmit and receive the to the tongue。

Now these are no longer used in practice， but there are some special cases。

 embeddeded systems and so on where they're still used。

 but you will not see RS 232 terminals connected to a laptop or a PC but there when you go to emed devices and things of that sort you might still use RS232 for communicating with the terminal。

Now the way this terminals work is essentially you have a buffer pool which is like a circular buffer where you can read or write so keyboard input arrives and it essentially sits in a circular pool and then the device driver in this case is going to keep reading those characters and then processing them and so on and to write also you have this kind of buffer that is being used to output to the terminal。

Now very quickly the terminal driver has to in this case do a few different things you can read from the terminal again the read commands essentially arrive to the VFS server and then on behalf of a user process and then are handled by the device driver the read only is true if you are using an RS232 terminal if you have a standard graphics card。

 the monitor you are not going to be reading from it except that more modern monitors might have a touch screen in which case they become both input and output but in only the older Rs232 terminals actually have a keyboard that is part of the terminal device but not more modern screens except for a touch screen you can of course write to the terminal which is your output in characters or pixels to the terminal or you can essentially use IF commands which allow you to set terminal parameters how frequently you want to communicate case of the graphics card this is maybe the frequency of output are you。



![](img/628a5944565a9bc86bcda7bf64db469c_10.png)

In 30 htz or 60 herz or are you changing the resolution and so on。

 So these are all done through the IR telcot。有。You also need to handle a certain other types of messages such as there was an IO from the screen which could be a keyboard inter。

 you might have to also do things like standard thing like opening and closing devices and so on。

So all of that is shown in this picture here where your user process that is trying to read from a terminal。

 let's say there's a touch screen you will receive some there's been some touch input。

 you basically since the device is exposed as a file you essentially handle it through the file server process so you read from the file server process that sends it to the TT wide driver。

 in this case there's a terminal driver， the terminal driver is going to ask wait for a receive from the system task whenever there's a keyboard input that generates an interrupt。

 it comes to the system task， the system task makes a notification message sends it to the terminal driver that step four and then a terminal driver is going to essentially read from the buffer and then decide what it needs to do and then finally hand that input through the user process forhand。

The output is very similar， you have a terminal task it's going to do right it's going to go through some event handler and then output characters to the screen and then you flush to the screen and remember that dial level concept as if it is a memory map device。

 you have a video Ram where you're essentially writing this output to the video of essentially uses the graphics card controller to output that to your s。

And the last。Driver I want to talk about very briefly is the keyboard driver and typically on most machines。

 the keyboard driver is separate from the terminal driver except in R232 there part of the same device but typically the keyboard could be a USB keyboard and the graphics card is separate so the keyboard drivers actually very simple every time you press a key on your keyboard it generates an integer code card generated that represents what key has been pressed So for every key on your keyboard there's an integer code a key would have a code and the P you would have a code and the function key would have a code and so on and some of that mapping is actually shown in this in this figure here So every time you press key it generates a code that code goes and sits in a small buffer and the keyboard generates an in the keyboard driver is then going to have to more read that keyboard input。

From the keyboard buffer and then hand it to whatever process was actually receiving that input at the current time at any time some process that is this designated as active and that's the one that's going to receive input now I should also mention that because you can press this key key on your keyboard very rapidly is a small buffer on your keyboard which will buffer this and this is done because the keyboard driver may not be able to process inputs as quickly as you press them sometimes you want a key and press it down it generates rapid amount of input and typically you may not be able to handle buffer them and then you wait for the keyboard driver to receive them one character at a time because it is going to be doing one character at time processing so。

Again I would encourage you to go and look at some of these drivers in the source code3 of Min some of them are very simple。

 some of them are little more complicated the device drivers are in the drivers's retreat some of the other code which is the device independent code we have to go into the VFS system process and look at the file server process and as part of the final project we have to implement a very simple device drivers are instructive to go and understand how all of this works so with that I'm going to end this today and then in the next class we are going to switch to with file systems and file server process within Linuxix and so on which will be the last big component of this course。



![](img/628a5944565a9bc86bcda7bf64db469c_12.png)

![](img/628a5944565a9bc86bcda7bf64db469c_13.png)