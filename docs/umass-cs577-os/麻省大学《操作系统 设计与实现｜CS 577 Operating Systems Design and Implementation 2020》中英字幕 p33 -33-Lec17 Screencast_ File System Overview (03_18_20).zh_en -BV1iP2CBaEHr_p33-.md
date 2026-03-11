# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p33 -33-Lec17 Screencast_ File System Overview (03_18_20).zh_en -BV1iP2CBaEHr_p33-

Okay so today we are going to look at file systems and this is going to be the last key component of an OS that we cover in this class this slide here shows us what we have done so far and where we are so our first big component was looking at processes it looked a little bit at threads and saw how the OS provides the abstractions of processes and threads and then maps them onto the CPU it's a way to manage the CPU we looked at address spaces and memory management which was a way to manage the RAM on your machine and today we are going to start talking about files and file systems and the hardware resource that the OS uses to manage files and file systems is obviously the hard disk。



![](img/ce1967add5856a438e3f6d102b8907bf_1.png)

So we are going to look at several key functions that a file system provides us which include naming how files are named。

 protections， how do you enforce protection across between files and users we look at persistence。

 how data is made to persist on disk across reboots。

 we are also going to look at how the OS and the file system provide fast access to files on the hard disk。



![](img/ce1967add5856a438e3f6d102b8907bf_3.png)

Now designing a file system involves two key components the first is how your data which is your files and folders are organized and stored on disk what are the on disk data structures that are used to layout the files on disk provide access to these files at a later time in an efficient fashion and so so that that's all on disk layout and on disk data structures now the file system is also a piece of code that is part of your OS in most monolithic kernels the file system code resides inside the OS and we'll see in mens it resides in user space but regardless of where it resides the file system also implements in memory data structures that allow you access to the on disk files and it implements all kinds。

of interfaces that both users processes and users themselves use to get access to their files so designing a file system involves both of these components。

 how are you going to lay out your data and disk and how are you going to implement the file system code itself in the OS。

We are going to look at both of these components today's class is an overview of general concepts and then next time we are going to look at how Min is going to implement these concepts。

 so Im going to start with the second point first which is how the file system is implemented in the OS and towards the latter part of this lecture we are going to look at on disk data structures for the file system。



![](img/ce1967add5856a438e3f6d102b8907bf_5.png)

![](img/ce1967add5856a438e3f6d102b8907bf_6.png)

So this slide here shows us a picture of what kinds of abstraction a file system provides to its user and how it actually maps into the OS etc now you will see some similarity between this picture and what I shown you in the previous class when I talked about IO systems and device drivers and so on because remember that the file system and the hard disk is also related closely to i subsystem within within an OS so you will see two components here which should already be familiar to you you see that there is a device interface which provides access to the hard disk and that's done through a device driver as we saw first saw last time in case of the disk driver there are interfaces that allow you access to a disk which include reading writing to specific blocks on disk and so on and then。

Interfaces that are designed for magnetic hard disk。

 they no longer apply to modern disks which are solid trade disk they dont move。

 but if you have the older style magnetic hard disk in your machine。

 you still have interfaces like C and so on。Then above this layer is the device independent layer which is now no abstracting away some of the lower level details of how disks work and just providing a higherle abstraction to users in this case the abstraction is one of a file because the file system is implementing that interface for us so we have things like opening a file closing a file reading writing to files and so and then and then this interface is also exposed through a system called interface to application processes then you might have libraries that provide a still higher level interface to application processes as well。



![](img/ce1967add5856a438e3f6d102b8907bf_8.png)

So let's start first with trying to understand what are some highleve design requirements on accessing data so from a user's perspective。

 we want any data that you store on your hard disk to be persistent which means that the data should stay there across reboots remember that memory is a volatile storage medium so we do not have this requirement on anything stored in memory it's assumed that whatever is in RAM is going to go away if you power cycle your machine but that is not the case for a disk。

 whatever you store on your disk so stay there So when you implement a file system in your final project。

 you will have the key requirement which means that if you shut down your virtual machine and the OS that's running inside the virtual machine and restart it。

 all the data that you stored on your file system that you implement should still stay there which should still be available。

So that's the first requirement， the second requirement is speed。

 which means that the data structures that you use to access data on your disk or in this case access files should be efficient should allow you to access this data efficiently and quickly。

The third is size， which means that you want the ability to store lots of data on your disk。

 you want the ability to create large files on your disk。

 so there should not be any restrictions on how much data you can store or how large the files could be with a caveat that of course you cannot store more data than the size of your disk。

 but you shouldn't have to the extent possible limits on file sizes， for example。

 your files should be your file system should support large files to allow you to store things like videos or other kinds of large files on your disk。

Sharing and protection is the fourth requirement where we want users to be able to share their files with other users in a fine grain manner。

 so you should be able to as a user tell the OS that certain files can be accessible to certain users or certain groups of users but others are not。

And last but not least you want ease of use where you should be able to get to your data at a later time and modify it and so on。

So we will go through some of these concepts in more detail in the rest of the lecture。



![](img/ce1967add5856a438e3f6d102b8907bf_10.png)

So now let me also say given those requirements what's the division of labor who does what So from a hardwares perspective it' is going to provide us persistence because disks are nonvolatile memory whatever you store on disk stays there across power cycle so you get persistence from disk you get speed also from disk because disks support random access and this is true for both magnetic disks where you can go to any location on disk can retrieve data as well as solid state disks where which only support random access size is also and requirement that your disk support discs just keep getting bigger typical disks now range from anywhere from hundreds of gigabytes to a few terabytes and thats just one disk even on laptop or a phone might actually have。

Hundreds of gigabytes of persistent memory。NowAs far as OS is concerned。

 it is also going to provide us persistence by providing redundancy to allow us to recover from failures and so on。

 It's going to provide some of the other requirements that I mentioned which is sharing and protection by using things like protection bits or access control list that allow us access to files and it's going to provide ease of use through many different mechanisms So for example files will have names that are human readable internally files are actually represented as integer IDs but that's not something users can be expected to remember so users are given abstraction of file names and the OS actually maps file names to the internal Is and a user can pick whatever name that makes sense for a file for example project1 do C tells you that this is a C source file that is related to project1 and so and furthermore you are also have that。



![](img/ce1967add5856a438e3f6d102b8907bf_12.png)

Atraction of folders or directories where you can group related files in one folder。

 So all of these concepts allow you ease of use and modern file systems also allow you search feature so even though you may have a well organizedized file systems because your lots and lots of files sometimes you may not remember where a file is located so you might have a search feature in OSX that's called spotlight and Windows has a desktop search and so on that allow you to search their file system so you can not only search for file lane but also search based on contents of files and then get access to your data。



![](img/ce1967add5856a438e3f6d102b8907bf_14.png)

So with that background， lets now start looking at files and the interfaces provided by the file system to access these files。

A typical definition of a file is that it's a named collection of related information that is recorded on secondary storage。

 All that means is a file actually has a name which is assigned by a user typically and it has some related information。

 So it might have blocks or lines of code or whatever you put in a file that's related。

 which is why it is stored in this container called a file and it's stored on secondary storage。

 So it its essentially from user's perspective。 that is the logical unit of storage。

 although underneath disks use blocks to store data from a user's perspective， you don't see blocks。

 you only see files and director So from a user's perspective。

 the smallest unit of data that you stored on on hard disk is essentially a file。



![](img/ce1967add5856a438e3f6d102b8907bf_16.png)

Filees could contain source code or binary data so it could contain programs。

 binary data and so on they can be structured or unstructured。

 typical example of UniX file systems is one where you assume files don't have a structure that the file systems knows about even though the file may have a structure the file systems does not care about it it just sees files as a sequence of bytes but there are file systems that are related to database programs that mainframes implement where you impose a structure in a file so you could say a file is a series of records or a series of objects that are structured in some format。

 but those are more special purpose file systems and most Uniix like file systems just assume that files are not structured。

Now files will have other attributes such as a name I already mentioned that they may have a type and again。

 depending on the file system， you may or may not care about the time。

Certain file systems don't assign a type of files file which means that you don't actually know what type of a file it is but other file systems do so they might say that this is a word document or this is a source code or this is binary object or it's an HTML file so the file system actually knows the content of a file and there are different tradeoffs based on whether you use the file type as a key attribute within the file system or youre oblivious of the file type and you may have other attributes like location size protection time of creation and so on and it'll get to some of these。



![](img/ce1967add5856a438e3f6d102b8907bf_18.png)

Now coming to the interface that the file system exposes these are typically exposed to users through system call interface so for accessing a file we have familiar operations here like opening a file。

 closing a file， reading a file， writing a file， creating and deleting files and so on and then there are operations that allow you to change the attributes of the file and attributes are also referred to as metadata metadata is essentially data about the data so you can change the attributes of a file such as the protection information the owner of a file and so on and then there are interfaces like get attributes at attribute that allow you to either read or change the attribute as well as some other interfaces that we talk about that allow you to create hard links and soft links。



![](img/ce1967add5856a438e3f6d102b8907bf_20.png)

Now I'm going to go through some of this material rather quickly because it is supposed to be a refresher from an undergrad concept in an OS and next time we will actually look at some of these in more detail in the Min context so let's start with the data structure that an OS is actually going to maintain or a file system is going to maintain within an OS so there are two key data structures that a file system maintains which are essentially two types of file tape。

Theres something called an open file table which is shared by all processes and that basically there's one entry for each open file in the system and so this table tracks all files that are currently open by all processes within within the OS that are currently accessing files and so since multiple processes can also open the same file for reading or writing concurrently you will have something called an open count that tracks how many processes currently have this file open for reading or writing as well as several other things like the file attributes location on disk pointers to location in memory and so on and we look at this in more detail as well。

And then for each process in your OS， you have a per process file table and this table tracks what files that process。

 a specific process has opened for reading or writing and here again you will have an entry to the open file table that tracks where this file is in within the open file table you will have something that's specific to a process which is the file offset which is where you are reading or writing at the current time within that file。

 that specific remember to each process even though multiple processes may have opened this file for IO each process is going to have its own offset as well as the mode in which the process is opened the file whether it's a read write or read right。

And then some pointers to the OS buffer remember that last time when I was talking about device drivers and so on I mentioned that every device is going to have a buffer cache and the file system in particular makes heavy use of the buffer cache So the file per process file table is also going to have a pointer to file buffers Now keep in mind that these are in memory OS data structures this is what the OSs maintains in memory for the file system when it's executing these are separate from on disk structures that we are going to look at soon which are maintained by the file system on disk itself。



![](img/ce1967add5856a438e3f6d102b8907bf_22.png)

![](img/ce1967add5856a438e3f6d102b8907bf_23.png)

Okay， so now we can quickly go through some key operations and see how these two data structures。

 the per process file table and the global open file table are used to implement certain interfaces So the first one is create so create is a system call here we just have a generic name for it。

 but it's a system call that allows us to create a new file in your file system So every time you try to save a file and give it a new file name within let's say editor internally you actually are to create the file first before you can actually save data to it。

 so create is the system call that gets called for that purpose。

So the steps shown in creator listed here。 So first youve got to check whether there is sufficient disk space for creating a new file。

 whether the user actually has permissions to create a file within the specified directory and so on and assuming all of that is true we are going to then create a new file descriptor for this file and the file descriptor as we will see is an on disk data structure so so it will basically store the name of the file the location or the file on disk and other file attributes and we are going to essentially add the file descriptor to the directory and then。

We are going to essentially see whether there are other things to track for the file。

 which include the file type and so on。So， thats very quickly how a create operation or a create system call is going to get implemented so essentially you do some checks and if the checks pass you basically allocate a new entry in the on this data structure saying a new file has been created。

Now。Whether there are some tradeoffs and whether the file system needs to keep track of the file type whether say it's a word file document or an executable and so on。

 The advantage of doing this is when you do things like double click on a file the OS knows what type of file it is so it can launch the appropriate program and it can also do better error detection because you know what type of a file it is and so on or even optimize the layer for different types of but the disadvantages now the file system needs to know about every possible file type that exists out there which may complicate the file system and if new file types are created at a later point either the file system will not know about them or you have to extend the file system to get it to know about so those are some tradeoffs now Uniix does not have the notion of a file type most file system in Uni assume that files are a sequence of bytes there is no type。



![](img/ce1967add5856a438e3f6d102b8907bf_25.png)

![](img/ce1967add5856a438e3f6d102b8907bf_26.png)

![](img/ce1967add5856a438e3f6d102b8907bf_27.png)

![](img/ce1967add5856a438e3f6d102b8907bf_28.png)

ated with them。Now， even though that is indeed the case。

 you can still track file types outside the file system。

 which is what things like X Windows as well as the graphical user interface on your Mac do because the Mac will still allow you to double click on a file and open a particular program to access that file。



![](img/ce1967add5856a438e3f6d102b8907bf_30.png)

Okay now the delete operation is going to do the opposite of what the create operation does which is release there the space allocated to the file and delete the entry for that file from on disk data structures so here to do delete you are to first find a directory containing the file now you got to go and release all the disk blocks allocated to the file and put them back on the free list and then remove the file descriptor from the directory。

And we'll get to ref counts and so on in a little bit because there are some subtleties associated with delete based on if multiple names point to the same file and so on。



![](img/ce1967add5856a438e3f6d102b8907bf_32.png)

Now let's come to open close read and write， which are the key operations the file system actually supports。

 So when you try to open a file using the open call。

 you are going to specify the name of the file you want open and the mode which is read right and here you are going to first check has the file already been opened by some other process in which case there's going to be entry in the global file table If not you create a new entry and then you check whether the。

The file protection bit allow you to open that file in that mode if not you are going to give an error otherwise you now create an entry in the per process file table and initialize the pointer to0 which is offset zero and that allows you to open a new file so you are going to create two entries one in the open file table which is global and one in the per process file table。

And when you close the file all all of these entries essentially have to be removed from the global file table and the per process file table so the per process file table entry gets deleted in the global file table you reduce the ref count or the open count by one and if that count goes to zero that means there are no other processes accessing that file at the current time so you can delete that entry from the system wide file table as well。



![](img/ce1967add5856a438e3f6d102b8907bf_34.png)

Now read and write operations given that you opened a file are somewhat straightforward。

 so when you try to read from a file which is a random access。

 what you are going to do is you are going to essentially look for where the data is on disk and read from that location。

But first youve were to look at whether the data already exists in the buffer cache and if so youre going to read it from and we talked about this last time where every IO operation first looks in the buffer cache and if it's hit you support from there if it's a miss you actually go and read it from disk or right toward disk so in case of random access you basically go to a specific location on disk where that offset resides and then you start reading from there and in case of sequential offset it sequential access rather you just look at where the file offset is pointing and then you go to that location on disk can read from that location so both of these operations can be supported based on the data structures that you in the file tables and on disk。



![](img/ce1967add5856a438e3f6d102b8907bf_36.png)

![](img/ce1967add5856a438e3f6d102b8907bf_37.png)

And write is going to do similar things， so it is going to rather than reading it is going to write to a specific location on this。

You also have a seek call which allows you to change the file offset to a particular location so typically seek points to where to read next。

 but you can actually read from any location within that file by manipulating seek。

And then I have already mentioned memory mapping before just as you can memory map IO devices you can also memory map files and when you memory map a file you essentially take that file and map it to address space with that extend RA and that allows you to access that file as if it is basically part of RA and then this allows you to read or write to that file as if you are reading a right to memory location rather than issuing specific read or write code so the same concepts be used for memory mapping IO devices also hold for memory mapping of files。



![](img/ce1967add5856a438e3f6d102b8907bf_39.png)

Now as far as file access methods are concerned， you can have either sequential access or random access to a file depending on the application right if there are things like databases where you are making queries queries can access different records the access pattern may be random but if you have a compiler that' is compiling a file you are going to read that file sequentially and read that entire file in memory and then you are going to compile it and then you are going to sequentially write out the results of the compiled code back to disk so so depending on whether or what kinds of process it is you will get either sequential access where youre reading the file one byte at a time or one block at a time from the start to then or random access where you can access it。

Any location on this。Now from a design perspective you have to support both kinds of access。

 so the data structures that we are going to maintain on disk to access a file has to be designed so that it will support both sequential and random access efficiently and soon we are going to look at the data structures and also examine the tradeoffs from a perspective of sequential and random access。



![](img/ce1967add5856a438e3f6d102b8907bf_41.png)

![](img/ce1967add5856a438e3f6d102b8907bf_42.png)

Now let's talk a little bit about naming so naming essentially means two things one is how do you access the file using its file name and then the second which is related to directory structures is how are you actually going to organize the file on disk okay every file has the name and of the full name of the file is essentially the name of the file in terms of how you access it from the root directory so you might have something like slash user slash local slash bin slash chromrome that is the full name of a file and it basically has the directory structure embedded in it as we can see。

So there are many naming strategies that file systems provide the simplest one is single level directory which essentially means you can't have any directories There's only one rule directories。

 all files are stored in there very primitive file systems would support this no sophisticated file system is going to support only a single director okay now the issue in single directories all file names have to be unique if you have directories structures where your multiple directories you can have two files named fo in two different directories and thats okay but not in a single level directory。



![](img/ce1967add5856a438e3f6d102b8907bf_44.png)

And in multilevel directories you can have arbitrary organization where you have a tree structure and you can have directories and they are nested and you can other subdirecties in them can have arbitrary nesting and the leaves can all be all files that are stored within that directory structure。



![](img/ce1967add5856a438e3f6d102b8907bf_46.png)

![](img/ce1967add5856a438e3f6d102b8907bf_47.png)

so when you try to open a file， the file system actually has to track that file down by doing what is called a lookup or。



![](img/ce1967add5856a438e3f6d102b8907bf_49.png)

啊。Where it starts on the root and it descends down the file structure hierarchy until it gets to the specific file we are looking it and we will get to that in just a little bit now let me also say something about referential naming the typical assumption you made so far is the files have a nameme。

And every file needs to have a name but its file systems are also going to allow us to give multiple names to a file so a file can have more than one name and this is done using what are called either soft links or hard links in within Uniix and in Windows these are also called shortcut shortcuts are the same as soft link and you use the LN command to actually create either of these Ln minus S creates soft links and Ln creates hardling and as is shown here let's say your file name a which is file0 on on your file system if you do Ln A B that essentially says take the file with the name A and assign it a second name called B so now you get a second so the file has two names so when you do an Ls youre going to see if both of these names exist in the same directory if you do an Ls you are going to see two files although there are two names that point to actually the same file internally。

The interesting thing here is now if you have two names for a file and you delete a。

 the entry for a is going to be removed， but the file itself is still going to exist because there is another name for it B which allows you to access the file only if you remove both A and B will you actually delete the contents of the file as well。

And this is why you need to track within the file system a Ref count which says how many names does a file have and every time you delete one name you decrement it and only when the F count goes to0 do you actually delete the file。

Now the common case is of course that the file has only one name。

 so the Ref count is typically one and when you delete the file it goes to0 you immediately delete it。

 but that need not be the case if the file has multiple names to access it。

Now the thing to keep in mind is these names can also exist in multiple directories you dont and this is why you have links or shortcuts to allow you to access the file that is stored somewhere else from another location on this。



![](img/ce1967add5856a438e3f6d102b8907bf_51.png)

Now one thing I should mention here is the difference between soft links and hard links softlink essentially is a pointer that tells you that if you want to open a file go go there and look elsewhere。

 but when you make a hard link you actually create two entries in the file system that point to the same file and there are some implications of hard links its a soft links when you delete when you have a soft link and you delete the original file it gets deleted and you might have a dangling pointer which is a missing shortcut in windows but when you have hard links this does not happen because the file system knows that there are multiple names sort of file you delete a file it only the decrements a f count and does not delete it if there are other names map to a file the other thing that is a restriction is you cannot actually have。



![](img/ce1967add5856a438e3f6d102b8907bf_53.png)

![](img/ce1967add5856a438e3f6d102b8907bf_54.png)

![](img/ce1967add5856a438e3f6d102b8907bf_55.png)

![](img/ce1967add5856a438e3f6d102b8907bf_56.png)

![](img/ce1967add5856a438e3f6d102b8907bf_57.png)

![](img/ce1967add5856a438e3f6d102b8907bf_58.png)

Hard links for directories because this can create circular loops within the file system。

 If your parent directory is pointing per rule or child directory that goes and points to another upper level directory this might create a loop and that causes all kinds of problems because the file system hierarchy is an basically graph it's a dag so you don't want loops which will cause problems for things like backup programs because theyll never terminate they'll just sit in a loop trying to essentially keep backing the same data over and over again so you can have soft link for directories but not hard linkss for individual files you can create both hard links and soft links。



![](img/ce1967add5856a438e3f6d102b8907bf_60.png)

So those are all things to keep in mind。Now I am not going to go into directory operations in any detail just as you can create a file you can create a directory。

 you can essentially list all files in a directory you can rename a file and so on。

 so these are all standard operations that a file system needs to support but for manipulating directories as opposed to files。



![](img/ce1967add5856a438e3f6d102b8907bf_62.png)

Okay so very quickly as far as protection is concerned。

 there are two methods by which file systems allow you to decide which user on that machine gets access to files。

So these are called either access control lists or access control bits And now Windows allows you to create what is called access control list or ales ACL is the acronym for access control list So what an access control list is essentially a list of user names that have permissions to access the file and what kinds of permissions or writes they have on the file so so for each file you will have a list by default that list fill only one entry which is the owner of that file who created the file so the owner has obviously access to the file and depending on whether it's executable or just a source file you might have rewrite execute access on the file but you can keep adding entries to this a saying this other user has access to the file and that is going to be used by the OS when you open a file saying does the user is he or she present in the a and should I allow that user to access that。

So thats the Windows bay UniX does something different so rather than creating an arbitrary list it essentially groups users into three categories when they are called user group and world so and it create keeps three bits for each group so a user can have readwr or execute permission the UniX group that the user belongs to which we can contain many other users also gets three bits and then you have word so essentially you divide all users into three groups the owner the UniX group and everyone else and so you have more course grain control then an access control list where you can specify an arbitrary list of users or arbitrary groups and so on。

So it's a more coarse grain method， but it's more efficient from a storage perspective because you essentially need only9 bits can readwrite three readwrite execute bits for users3 for the group and three for world as opposed to an a which could be of arbitrary size and it might take more space。

 so this is more coarse grain but more storage efficient。

 So that's the trade off And the meta point here is using either of these two mechanisms you can control So for example。

 if you don't want to give access to anyone else in Uni you set the readwr execute bits for the group and the use and world to be all zeros which means only you have access in no one else as access or you can give access to users within your group and so on and so forth。



![](img/ce1967add5856a438e3f6d102b8907bf_64.png)

Okay， now with that in mind， so we have quickly gone through inmemory data structures that the file system maintains。

 which are the process file table and the global file table as well as some high level concepts of how open close read write and all of these things work。

 So in the remainder of the lecture。 I'm now going to switch to on disk data structure。

 So this is the complementary part of a file system where we are going to discuss what does the file system do on disk。

 How does it actually store data on disks and so on。 So in other words。

 going back to this picture I showed you earlier， we are now going to look at the lower layer。

 which is the hard disk and how you can implement a files file system data structures on your disk。



![](img/ce1967add5856a438e3f6d102b8907bf_66.png)

So let me show you first how typically magnetic disks work this is now getting somewhat outdated because most of your computers have solid state disks that don't look anything like what Im going to talk about but it is still instructive to see this because there are still plenty of servers that use magnetic discs as well。

So typical disk looks like what a C looks like you seen a DCD or a DVD so it lose a circular platter where data is recorded and this picture here shows us that data is recorded in concentric tracks concentric circles called tracks and each track is divided into smaller chunks called sector a sector is the smallest unit of data that you can read or right from disk okay so you will basically so tracks are going to get numbered so maybe the innermost track is0 in the outermost track is n so to address something on a single platter you specify the track number and then you specify sector number within that track so you say track5 and sector 7 so within each track the sectors are going to be numbered0 to n the tracks are also numbered0 to and going from the innermost track or the outermost and typical disk is actually going to have more than one of these platters as is shown in this。



![](img/ce1967add5856a438e3f6d102b8907bf_68.png)

Picture， so think of them as a stack of Cd Ros。 All of them are spinning。

 So you essentially also have the。The platter number which is called a cylinder。

 so you essentially will have cylinders and and then track number and then a sector number within the disk。



![](img/ce1967add5856a438e3f6d102b8907bf_70.png)

So our typical access to the sector on a file is going to involve some overhead because you have the disc head the platter is spinning and the disc head is positioned at a certain location which means that it is going to be positioned on a certain track so if you want to read data elsewhere you have to mechanically move the disc head to another track that is called the seekq time and the time to actually move the disc head to another track or a cylinder。

And once the disc head is positioned on the right track。

 you still have to wait for the sector to spin by and come under the dischead when you can read or write to that is called the rotational latency and then your transfer time which is when you are actually reading or write。

All the time spent in doing seeks and rotations are wasted time because the disc cannot actually do any IO it is simply trying to move the disc head to where it needs to be to actually do IO so many file systems that are designed for magnetic disk are going to spend some effort in trying to reduce the seek and rotational latency and and this is done by efficient layout on a file of the files on disk to reduce your seek and rotational la。



![](img/ce1967add5856a438e3f6d102b8907bf_72.png)

Okay， so。That's something we want to keep in mind。 Now。

 none of this is going to apply to magnetic disk because switching to another block is instantaneous。

 It's like going and reading to another location in Ram。 There is no overhead。

 regardless of how far the next location is with relation to the current location in magnetic disk the further away the next sector is on the current location。

 the more the seek time and potentially the rotational latency the higher the overhead it in SSDs and in are similar to similar to Ram where there is no such overhead it。

 So many of the optimizations that file systems have performed for hard disk no longer applied to SSDs and SSD file systems can be designed differently because some of these overheads don't need to be don't exist and you don't need to account for them。



![](img/ce1967add5856a438e3f6d102b8907bf_74.png)

OkaySo with that in mind， let's look at how files are organized on this。

 So essentially for every file you're going to have a table and that table is going to track where blocks of the file are stored on this。

 So you will say each file is going to be numbered。

 So let's say you have file 0 you say where is block 0 stored and you have address which says it's on platter 0 cylinder 0 sector 0 and block1 is on platter 4 cylinder 3 sector  and so Okay again。

 like in memory and process layout， we can have disks that are contiguous or not。

 which is why you need this table to track where the files are stored So this file table is similar to page table for a process page table tracks where the pages of a process are stored in Ram on disk file table tracks。

Now which we will refer to as an in in just a moment or a file descriptor tracks where the blocks of the file are stored on so they are similar concept。

remember that last time I also mentioned that you can have logical block addressing where rather than using this triple of platter number。

 cylinder number sector number， you can just uniformly address the blocks from0 through n and then translate it internally to the triple so you can use either of these to addressing mechanisms in your file table。

So now the question is， how are we going to lay out our files so that they support sequential and random access efficiently so that you can figure out where the blocks are on the file and so on So So to do this we need a key data structure for every file that you store on disk which will call the file descriptor this is separate from the per process and the global file table those are in memory data structure This is an on disk data structure So for every file you store on disk you're going to have a file descriptor file descriptor is going to track all the information that you need to access that file from disk So it is basically the metadata structure for the file the file has data which is the content of the file and the file descriptor is metadata for the file now to efficiently store the files on disk we make a couple of observation which is that most files are going to be small the mean file size of files on disk is still between four and。



![](img/ce1967add5856a438e3f6d102b8907bf_76.png)

8 kiloB but most of the storage space is taken by a small number of large files so so there are lots of small files but they don't actually take a lot of space in the aggregate but most of the space is taken by a small number of large files So what this means is you need to provide good access to both small files in large files while optimizing for the common case and the common case is that files are actually small so you want to allow sequential and random access you want to make sure that you can access small files efficiently as well as large files maybe as somewhat efficiently。



![](img/ce1967add5856a438e3f6d102b8907bf_78.png)

![](img/ce1967add5856a438e3f6d102b8907bf_79.png)

![](img/ce1967add5856a438e3f6d102b8907bf_80.png)

So we look at three different layouts here。For how you store your files on this。

 the simplest one is contiguous allocation。 So this is like what you add in for process allocation where you allocate a chunk of disk space and the file is stored contiguously So here all you need to know is the starting location or the file on disk the starting address and the size of the file So because all the blocks are stored contiguously once you go to the start location。

 you can just access all the blocks without any additional information So the file descriptor just needs the start address and the size of the file。

Because its a very simple organization。 It is going to allow us sequential and random access because once you know the start address。

 you know the fifth where the fifth block is stored。

 which is five blocks from the start location of the file and so on and sequential access is also fine because you are going to just do one C can just read that entire file from starting to the end so both C can sequential and random access are efficient。

 The problem though， is that this can cause disk fragmentation just as contiguous allocation in memory cost in memory fragmentation So the file grows and there is no space to grow because you stored another file right next to it。

 then you are going to have to move the file or given error。

 So you have all the problems that occur when you are fragmentation once you start adding and deleting files you are going to have holes and so on。

 and this is address through disk de fragmentmentation programs that are going to go and move files around to reduce fragmentation all of them impose overheads。

A conigious allocation， although it's a very simple method is not used in sophisticated file systems just to avoid fragmentation issue but they are still used in things like CD roms and DVD ros where you only right ones so there is no fragmentation so if you are trying to create a DVD and write a bunch of movie files just write them sequentially one after the other because there not these are write ones devices you don't delete any files once you write to them so it's fine to use the simple allocation it's sufficient and simple to implement。



![](img/ce1967add5856a438e3f6d102b8907bf_82.png)

Next organization is a linked list so you keep files as linked list where each block of the file has a pointer to the next block and as shown in this picture here where your file isscripted。

That has the pointer， the head pointer to this link list which is the first block of the file on this can you see the address at the last location on the file descripted and then you in the block of the file you store data but the last byte or two of the file or three bytes in this case or three or three words are going to essentially have a pointer to the next block and so on。



![](img/ce1967add5856a438e3f6d102b8907bf_84.png)

So so that is an organization it is actually used by some primitive file systems as well such as the doOS early file system use the linked list organization now as you can imagine in this case。

Sequential access is fine where you access each block and then you have pointer to the next block and so on。

 but random access is not going to be efficient I just as in any linked list。

 if I say go access the Ih location of that list you have to start from the head and sequentially scan through the linked list until you get to the Ih location so random access is not going to be efficient here but sequential access is fine and to access all n block sequentially you're going to incur N6 because the blocks are no longer assumed to be continuousig and youve got to go through each block to access the next block and so on。



![](img/ce1967add5856a438e3f6d102b8907bf_86.png)

Now there is no fragmentation in this case because any block can be anywhere so you got rid of the fragmentation problem。

 you can increase the size of the file by just adding entry to one more block in the linked list and so on。



![](img/ce1967add5856a438e3f6d102b8907bf_88.png)

Go right so the last organization that we want to discuss here is the indexed organization where you essentially have an index which is a table and it has pointers to blocks on disk so there is a simple single level index shown here it is essentially an area where you want to access the I element to go to the I location in that index it gives you a discard you go to that location read the block and you have the I block of the file。

So this is an organization that is going to allow us efficient access to both sequential and sequential and random axis to a file and all youve got to do is read the file descriptor into memory and then essentially the indexes looks like an array。

 you can scan it sequentially and read blocks or you can just go to any location I in the index and get the Ih block。

Now one issue with the index organization is that file descriptors are pre allocatelocated by the file system when you format the file system at file system creation time so when you create a file you have to allocate this descriptors and you have to decide how large that index needs to be at creation time and since files can be of arbitrary size you don't know ahead of time how much or what how big any particular file is going to be so this file descriptor has to be preallocated to be large and the size of the entries in the index also determine the maximum file size。

Now since I already mentioned most files are small allocating a large index for every single file or preallocating a large index where every single file is going to be enormously wasteful because you all these entries in your file descriptor are going to be wasted but you have no choice but to do that because you don't know ahead of time how large that file any particular file might be when the file the user creates them at a load later time。



![](img/ce1967add5856a438e3f6d102b8907bf_90.png)

So to address this issue to have a more efficient file descriptor what most file systems do is a multilevel index this is in a unique terminology called an in where are an index node where you basically have a multile index structure so as I shown here the file descriptor only has 2 entries or another 14 entries。

The first 12 entries of that file descriptors are direct pointers they point to disk blocks that are going to be part of that file if the file is larger than 12 blocks then the 13th entry is actually a pointer to a indirect block which has another 10。

24 entries as is shown here so that is called a single level indirect。

And if the file grows beyond 12 plus 1024 blocks in size。

 you use the 14th entry where you point a block each of those block point another block and those are the ones that have pointers to block so there are two levels of indirect so these are called a double indirect and modern file system have a 15th entry which is a triple indirect block。

So the reason this is more efficient is because most files are small。

 You are never going to use the 13th and the 14th entry of the file descriptor。

 maybe you're going to be okay by just using the first 2 entries So all you need to do is read the file descriptor and most of the contents the file you can access through the first2 entries because most files are going to be one or two blocks in size as we saw but in some files are large you can also support larger file file sizes by using the single indirect。

 the double indirect and the triple indirect blocks of the file so this is how the innodeote structure is created and the important thing is only the file descriptor is preallocated so only the 15 entries of that area are preallocated that single double in indirect blocks can be allocated on demand just as you allocate blocks to any file you can also allocate this blocks with the file descriptor so you never waste any space by preallocating a giant structure for large file。



![](img/ce1967add5856a438e3f6d102b8907bf_92.png)

Yeah， so this is a multi level index。 It supports incremental file growth。

 It's efficient for small files， but it's also reasonably efficient for large files because youll just have either one。

 two or three level。 wind directions are still not bad as a linked list where you are to essentially scan linearly through a file。

 so it's。It's some less efficient for very large files because the level the level of indirect grows。

 but it still supports it with no more than three level 3 block I6s and three rotational latencies because to get to a a block in a large file you may have it most read the file description or read the single double in triple indirect blocks to get the address and then you can read the block。

The file size is still bounded by the maximum file size is still bounded by the number of entries you can store in this multilevel index which is going to be 12 plus 1024 plus 1024 square plus 2104 cubed those are the number of entries max number of entries you can store in this in the structure。



![](img/ce1967add5856a438e3f6d102b8907bf_94.png)

The last thing I want to say here is how does the file system know which blocks are in use and which blocks are？



![](img/ce1967add5856a438e3f6d102b8907bf_96.png)

Not in use or free。 And this is done through free space management。

 So so you can essentially do the same thing as what you did for tracking free pages in memory。

 you can have a bitmap， one for each sector of the disk or block or the file where0 says that that sector is available one says it's not and so on。

 So if you want to now allocate a new file， you can scan through this bitmap and look for some chunks of zeros。

 So you can create that file。 you need only one0 to create allocate one block。

 but if you want to create a new file。 a Uuristic might be find a region where there are chunk of free block so that you can store blocks of the file close to one another。

 and they don't have to be contiguous but the closer they are the lower the seek over it。

 That's not an issue in SSD， but still a good heuristic for normal files for a magnetic disk file system。



![](img/ce1967add5856a438e3f6d102b8907bf_98.png)

Now in a free deleteta file， the blocks are basically marked free in the free block list the others bit mapap。



![](img/ce1967add5856a438e3f6d102b8907bf_100.png)

And when you allocate a blocks to file， you are going to scan and find entries that are allocatelocd and turn them into one and allocate them to a file。



![](img/ce1967add5856a438e3f6d102b8907bf_102.png)

Now one thing is the bitmap itself might be too large to keep in memory a very small2 GB disk。

 which is like a USB thumb drive might have as much as 4 million entries and if youre two terabytes that is three orders of magnitude larger than so you don't want to keep gigantic bit maps in memory So what file systems will do is they'll partition the bit maps into zones of a file or regions of of the disk rather not file and then only bring them into memory as needed So this is one way by which you can reduce the amount of memory needed to keep that entire free block listing ra at all times。



![](img/ce1967add5856a438e3f6d102b8907bf_104.png)

![](img/ce1967add5856a438e3f6d102b8907bf_105.png)

![](img/ce1967add5856a438e3f6d102b8907bf_106.png)

The last thing I want to mention is a picture of what the disk looks like okay so here we basically ignore the circular structure of magnetic disk and we are using logical block addressing and we address the blocks from0 to 127 and as you can see here block0 is typically called a super block the super block keeps metadata for the file system and you'll see here it has a free block list this is a toy file system where only 127 block so there are 128 entries and then there are ins that you are preallocated in the super block typically real file system will have more than one super block because you precreate a large number of iNots okay the max number of files is determined by how many file descriptors you ared at format time and so you will have multiple super blocks at multiple locations on disk that have stored all of these inots in them。

Here you have only one， but you will have more than one。 Okay。

 so so your super blocks and regular data block。 So anything that's not a super block。

creation time is marked as with0， saying it's a data block and it's available for use。

 And as you create files， you are going to start using these in entries up for allocating them for new files and then you are going to start using your blocks on disk to allocate storage space to each file directories are also stored in the same fashion。

 every directory has an in because some unique perspective。

 directory is just a file but it's a special file where it has a table of other files contained in it。

 So the data blocks of a directory will actually a pointers of file names and their in numbers So they are stored in a similar organization So this is a picture you want to keep in mind for your on disk data structure。

 this is how a typical disk layout is going to look like。

 and then everything that you have inside in Ram are other data structures like the process file table and global file table and so on。

So with that background I'm going to end the lecture for today and what Im going to do in the next class is to talk a little bit about the Linux file system。

 how is it organized on disk how I nodes within the Linux work and so on as well as the Linux file server process which is now called the virtual file server process that tells us how Linux actually implements a file system in in the kernel itself as a user space process rather not in the micro kernel but within the OS as a user process so let me stop here for today。



![](img/ce1967add5856a438e3f6d102b8907bf_108.png)