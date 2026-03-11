# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p34 -34-Lec17 Video_ File System Overview (03_18_20).zh_en -BV1iP2CBaEHr_p34-

。

![](img/803134ed70f3d96a55f714978c4960bb_1.png)

Okay so today we are going to look at file systems and this is going to be the last key component of an OS that we cover in this class。

 this slide here shows us what we have done so far and where we are so our first big component was looking at processes looked a little bit at threads and saw how the OS provides the abstractions of processes and threads and then maps them onto the CPU it's a way to manage the CPU we looked at address spaces and memory management which was a way to manage the RA on your machine and today we are going to start talking about files and file systems and the hardware resource that the OS uses to manage files and file systems is obviously the hard disk。

So we are going to look at several key functions that a file system provides us。

 which include naming， how files are named， protections。

 how do you enforce protection across between files and users， we look at the persistence。

 how data is made to persist on disk across reboots。

 we are also going to look at how the OS and the file system provide fast access to files。

Now designing a file system involves two key components。

 the first is how your data which is your files and folders are organized and stored on disk whatever the on disk data structures that are used to layout the files on disk provide access to these files at a later time in an efficient fashion and so so that's all on diskk layout and on diskk data structures now the file system is also a piece of code that is part of your OS in most monolithic kernels the file system code resides inside the OS and we'll see in mens it resides in user space but regardless of where it resides the file system also implements inmemory data structures that allow you access to the on diskk files and it implements all can。

of interfaces that both users processes and users themselves use to get access to their files so designing a file system involves both of these components。

 how are you going to lay out your data on disk and how are you going to implement the file system code itself in the OS。

We are going to look at both of these components today's class is an overview of general concepts and then next time we are going to look at how Min is going to implement these concepts so I'm going to start with the second point first which is how the file system is implemented in the OS and towards the latter part of this lecture we are going to look at on diskk data structures for the file system。

So this slide here shows us a picture of what kinds of abstraction a file system provides to its user and how it actually maps into the OS itself。

 now you will see some similarity between this picture and what I shown you in the previous class when I talked about IO systemss and device drivers and so on because remember that the file system and the hard disk is also related closely to IO subsystem within within an OS so you will see two components here which should already be familiar to you you see that there is a device interface which provides access to the hard disk and that's done through a device driver as we saw on last time in case of the disk driver there are interfaces that allow you access to a disk which include reading writing to specific blocks on disk and so on。

Inters that are designed for magnetic hard disk， they no longer apply to modern disks which are solid state disks。

 they don't move， but if you have the oldest style magnetic hard disk in your machine。

 you still have interfaces like C and so on。Then above this layer is the device independent layer which is now now abstracting away some of the lower layer details of how disks work and just providing a higherle abstraction to users in this case abstraction is one of a file because the file system is implementing that interface for us so we have things like opening a file closing a file reading writing to files and so and then this interface is also exposed to a system called interface to application processes and you might have libraries that provide a still higherle interface to application processes as well。



![](img/803134ed70f3d96a55f714978c4960bb_3.png)

So let's start first with trying to understand what are some highlevel design requirements on accessing data so from a user's perspective we want any data that you store on your hard disk to be persistent which means that the data should stay there across rebos。

 remember that memory is a volatile storage medium so we do not have this requirement or anything stored in memory it assume that whatever is in RAM is going to go away if you power cycle your machine。

 but that is not the case for a disk whatever you store on your disk to stay there。

 so when you implement a file system in your final project you will have a key requirement which means that if you shut down your virtual machine and the OS that's running inside the virtual machine and restarted all the data that you stored on your file system that you implement should still stay there。

 if should still be available。So that's the first requirement， the second requirement is speed。

 which means that the data structures that you use to access data on your disk or in this case access files should be efficient。

 should allow you to access this data efficiently quickly。The third is size。

 which means that you want the ability to store lots of data on your disk。

 you want the ability to create large files on your disk。

 so there should not be any restrictions on how much data you can store or how large the files could be with the caveat that of course you cannot store more data than the size of your disk but you shouldn't have to the extend possible limits on file sizes。

 for example， your files should be your file system should support large files to allow you to store things like videos or other kinds of large files on your disk。

Sharing and protection is the fourth requirement where we want users to be able to share their files in other users in a fine grain manner。

 so you should be able to as a user tell the OS that certain files can be accessible to certain users or certain groups of users but others are not and last but not least you want ease of use where you should be able to get to your data at a later time and modify it and so on。

So we'll go through some of these concepts in more detail in the rest of the lecture。So now let me。

Also say given those requirements what's the division of labor who does what so from a hardware perspective it's going to provide us persistence because disks are non-vol memory。

 whatever is stored on disk stays there across power cycles so you get persistence from disk you get speed also from disk because disks support random access and this is true for both magnetic disks where you can go to any location on disk can retrieve data as well as solid state disks which only support random access size is also requirement that your disk support discs just keep getting bigger typical disks now range from anywhere from hundreds of gigabytes to a few terabytes and that's just one disk even on a laptop or a phone might actually have hundreds of gigabytes of。

Sustainment。As OS is concerned， it is also going to provide us persistence by providing redundancy to allow us to recover from failures and so on。

 it's going to provide some of the other requirements that I mentioned which is sharing and protection by using things like protection bits or access control list that allow us access to files and it's going to provide ease of use through many different mechanisms so for example files will have names that are human readable internally files are actually represented as integer IDs but that's not something users can be expected to remember so users are given abstraction of file names and the OS actually maps file names to the internal IDs and a user can pick whatever name that make sense for a file for example project1。

 C it tells you that this is a C source file that is related to project1 and furthermore you are also have that。

Atraction or folders or directories where you can group related files in one folder so all of these concepts allow you tea of use and modern file systems also allow you search feature so even though you may have a well organizedized file systems because you lots in lots of files sometimes you may not remember where the file is located so you might have a search feature in OSX that's called spotlight and Windows as a desktop search and so on that allow you to search your file systems so you can not only search for file names but also search based on contents of files and then get access to your data。



![](img/803134ed70f3d96a55f714978c4960bb_5.png)

So with that background now， let's now start looking at files and the interfaces provided by the file system to access these files。

A typical definition of a file is that it's a named collection of related information that is recorded on secondary storage。

 all that means is a file actually has a name which is assigned by a user typically and it has some related information it might have blocks or lines of code or whatever you put on a file that's related which is why it is stored in this container or a file and it's stored on secondary stored so it's essentially from user's perspective that is the logical unit of storage although underneath disks use blocks to store data from a user's perspective you don't see blocks you only see files in directory so from a user's perspective the smallest unit of data that is stored on a hard disk is essentially a file。

Filees could contain source code or binary data， so it could contain programs， binary data and so on。

 they can be structured or unstructured typical example of。

Unix file systems is one where you assume files don't have a structure that the file system knows about even though the file we have a structure。

 the file system does not care about it， it just sees files as a sequence of bytes but there are file systems that are related to database programs that mainframes implement where they impose structure on a file so you could say a file is a series of records or a series of objects that are structured in some format。

 but those are more special purpose file systems and most Unix like file systems just assume that files are not structured。

Now files will have other attributes such as a name I already mentioned that they may have a type and again depending on the file system。

 you may or may not care about the type， certain file systems don't assign a type of file file which means that you don't actually know what type of a file it is what other file systems do so they might say that this is word document or this is a source code or this is a binary object or it's an HTML file so the file system actually knows the contents of a file and there are different tradeoffs based on whether you use the file type as a key attribute within the file system or you oblivious of the file and you may have other attribute。



![](img/803134ed70f3d96a55f714978c4960bb_7.png)

![](img/803134ed70f3d96a55f714978c4960bb_8.png)

![](img/803134ed70f3d96a55f714978c4960bb_9.png)

Like location， size， protection， time of creation， and so on and we'll get to some of these。

Now coming to the interface that the file system exposes these are typically exposed to users to system call interface so for accessing a file we have familiar operations here like opening a file。

 closing a file， reading a file， writing a file creating and deleting files and so on and then there are operations that allow you to change the attributes of the file and attributes are also referred to as metadata metadata is essentially data about the data so you can change the attributes of a file such as the protection information。

 the owner of a file and so on and then there are interfaces like get attributes。

 set attribute that allow you to either read or change the attribute as well as some other interfaces that we talk about that allow you to create hard links and soft links。



![](img/803134ed70f3d96a55f714978c4960bb_11.png)

Now I'm going to go through some of this material。Rather quickly because it is supposed to be a refresher from an undergrad concepts on OS and next time you'll actually look at some of these in more detail in the Min context。

Well let's start with the data structure that an OS is actually going to maintain or a file system is going to maintain within an OSs。

 so there are two key data structures that a file system maintains。

 which are essentially two types of file types。Theres something called an open file table which is shared by all processes and that basically there's one entry for each open file in the system so this table tracks all files that are currently open by all processes within OS that are currently accessing files。

Since multiple processes can also open the same file for reading or writing concurrently you will have something on an open account that tracks how many processes currently have this file open for reading or writing as well as several other things like the file attributes。

 location on disc pointers to location in memory and so on。

 and you look at this in more detail as well。And then for each process in your OS。

 you have a per process file table and this table tracks what files that process。

 a specific process has opened for reading or writing and here again you will have an entry to the open file table that tracks where this file is in within the open file table you will have something that's in time within that file。

 that specific remember to each process even though multiple processes may have open this file for IO each process is going to have its own offset as well as the board in which the process is opened the file whether it's a read write or read right？



![](img/803134ed70f3d96a55f714978c4960bb_13.png)

And then some pointers to the OS buffer and remember that last time when I was talking with device drivers and so on I mentioned that every device is going to have a buffer cache and the file system in particular makes heavy use of the buffer cache so the per process file table is also going to have a pointer to file buffers Now keep in mind that these are in memory OSs data structures this is what the OS maintains in memory for the file system when it's executing these are separate from on disk structures that we are going to look at soon which are maintained by the file system on disk itself。

Okay so now we can quickly go through some key operations and see how these two data structures。

 the per process file table and the global open file table are used to implement certain interfaces so the first one is create create is file a system call heres we just have a generate name for it but it's a system called it allows us to create a new file in your file system so every time you try to save a file and give it a new file name within that same editor internally you actually have to create the file first before you can actually save data tool it so create is the system called it gets called for that purpose。

So the steps shown in create are listed here so first you've got to check whether there is sufficient disk space for creating a new file。

 whether the user actually has permissions to create a file within the specified director and so on and assuming all of that is true we are going to then create a new file descriptor for this file and the file descriptor that as we will see is an on disk data structure so so it will basically store the name of the file。

 the location or the file on disk and other file attributes and we are going to essentially add the file descriptor to the directory and then。



![](img/803134ed70f3d96a55f714978c4960bb_15.png)

![](img/803134ed70f3d96a55f714978c4960bb_16.png)

We are going to essentially see whether there are other things to track for the file。

 which include the file type and so on。So that's very quickly how a create operation or a create system call is going to get implemented。

 so essentially you do some checks and if the checks pass you basically allocate a new entry in on this data structure saying a new file has been。

然后。Whether there are some tradeoffs and whether the file system needs to keep track of the file type whether say it's a word file document or an executive and so on the advantage of doing this is when you do things like double click on a file you the OS knows what type of file it is so it can launch the appropriate program and it can also do better error detection because you know what type of a file it is and so on or even optimize the layout for different types of but the disadvantages now the file system needs to know every possible file type that exists out there which may complicate the file system and if new file types are created at a later point either the file system will not know about them or you have to extend the file system to get it to over so so those are some tradeoffs so Uni does not have the notion of a file type most file systems in Uni assume that files are a sequence of by there is no type S。



![](img/803134ed70f3d96a55f714978c4960bb_18.png)

Now even though that is indeed the case， you can still track file types outside the file system。

 which is what things like explainend those as well as the graphical user interface on your Mac do because the Mac will still allow you to double click on a file and open a particular program to access that file。

Okay now the delete operation is going to do the opposite of what the create operation does which is release the space allocated to the file and delete the entry for that file from on disk data structures so here to do delete you were to first find a directory containing the file now you go to go and release all the disk blocks allocated to the file and put them back on the free list and then remove the file descriptor from the delete。

And we'll get to ref counts and so on in a little bit because there are some subtleties that are associated with delete based on if multiple names。

P to the same fight and so。let's come to open close read and write which are the key operation of the file system actually supports。

 So when you try to open a file using the open call。

 you're going to specify the name of the file you want to open and the mode which you read right and here you are going to first check has the file already been opened by some other process in which case there's going to be entry in a global file table if not you create a new entry and then you check where the。

The file protection bit allow you to open that file in that mode。

 if not you're going to give an error otherwise you know create an entry in the per process file table and initialize the pointer to0。

 which is offset zero and that allows you to open a new file so youre going to create two entries one in the open file table which is global and one in the per process file table。

And when you close the file all of these entries essentially have to be removed from the global file table and the per process file table。

 so the per process file table entry gets deleted in the global file table you reduce the Ref count or the open count by one and if that count goes to zero that means there are no other processes accessing that file at the current time so you can delete that entry from the systemite file table as well。



![](img/803134ed70f3d96a55f714978c4960bb_20.png)

![](img/803134ed70f3d96a55f714978c4960bb_21.png)

Read and write operations given that you open the file are somewhat straightforward so when you try to read from a file。

 which is the random access， what you're going to do is you're going to essentially look for where the data is on disk and read from that location but first you' want to look at whether the data already exists in the buffer cache and if so you're going to read it from and we talk about this last time everyIO operation first looks in the buffer cache and if it's a hit you support it from there if it's a miss you actually go and read or it from disk or right to this so in case of random access you basically go to a specific location on disk where that offset ors and then you start reading from there and in case of sequential offset sequential access rather you just look at where the file offset is pointed and then you go to that location on disk can read from that location so both of these operations can be supported。



![](img/803134ed70f3d96a55f714978c4960bb_23.png)

based on the data structures that you maintain within the file tables and on this。

And write is going to do similar things rather than reading。

 it's going to write to a specific location on this。

You also have a seek call which allows you to change the file offset of a particular location so typically seek points to where to read next。

 but you can actually read from any location or within that file by manipulating seekQ。

And then I have already mentioned memory mapping before just as you can memory map i devices you can also memory map files when you memory map a file you essentially take that file and map it to address space that extends RA and that allows you to access that file as if it's basically part of RA and then this allows you to read or write to that file as if you're reading a right to memory location rather than issuing specific read or write code so the same concepts we used for memory mapping i devices also hold for memory mapping of files。

As far as file access methods are concerned， you can have either sequential access or random access to a file depending on the application right if there are things like databases where you are making queries。

 queries can access different records the access pattern may be random but if you have a compiler that's compileiling a file you are going to read that file sequentially and read the entire file in memory and then you're going to compile it and then you are going to sequentially write out the results of the compiled code back to this so so depending on whether or what kinds of process it is you will get either sequential access where youre reading the file one by at a time or one block at a time from the start to end or random access where you can and access it。

Any location on this。Now from a design perspective you have to support both kinds of access。

 so the data structures that we are going to maintain on disk to access a fine has to be designed so that it will support both sequential and random access efficiently and soon we are going to look at the data structures and also examine the tradeoffs from perspective of sequential and random access。

Now let's talk a little bit about naming so naming essentially means two things one is how do you access the file using its file name and then the second which is related to directory structures is how are you actually going to organize the file or disk every file has the name and the full name of the file is essentially the name or the file in terms of how you access it from the root director so you might have something like slash user slash localslash bin slash code that's the full name of a file and it basically has the directory structure and where in it as we can see so there are many naming strategy is that file systems the simplest one is single level directory which essentially means you can't have any director that only be one rule directories all files are stored in there very primitive file systems would support this no sophisticated file system is going to support on a single director Okay now the issue in single director。

I all file names have to be unique if you have directories structures where you are multiple directories。

 you can have two fines named fo in two different directories and that's okay， but not in the single。

And in multile directories you can have arbitrary organization where you have a tree structure and you can have directories and they are nested and you can other subdirecties in them can have arbitrary nesting and the leaves can all be all files that are stored within that director structure。

Okay， so when you try to open a file， the file system actually has to track that file down by doing what is called the lookup or。

啊。Where it starts on the root and it descends down the file structure hierarchy until it gets to the specific file you are to and we'll get to that in just a little bit let me also say something about differential meaning the typical assumption you made so far is the files have a name。

And every file needs to have a name but its file systems are also going to allow us to give multiple names to file so file can have more than one name if this is done using what are called either soft links or hard links in then Uni and then Windows these are also called shortcuts shortcuts are the same as soft link and you use the LM command to actually create either of these an minus S creates soft links and Ln creates a hard and as you shown here let's say your file name A which is file0 on your file system if you do LN AB that essentially say state the file with the name A and assign it a second name called B so now you will get a second so the file has two names so when you do an Ls you're going to see if both of these names exist in the same directory if you do an Ls you are going to see two files although there are two names that point actually the same file internal。

The interesting thing here is now if you have two names for a file and you delete a。

 the entry for a is going to be removed but the file itself is still going to exist because there is another name for it B which allows you to access the file only if you remove both A and B will you actually delete the contents of the file as well and this is why you need to track within the file system a Ref count which says how many names does a file have and every time you delete one name to decrement it and only when the Ref con goes to zero do you actually delete the file。

The common case is of course that the file has only one name。

 so the Refcon is typically one and when you delete the file it goes to zero you immediately delete。

 but that need not be the case if the file has multiple names to accessing。

Now thing to keep in mind is these names can also exist in multiple directories you don't and this is why you have links or shortcuts to allow you to access the file that's stored somewhere else from another location on this。

Now one thing I should mention here is the difference between soft links and hard links softlink essentially is a pointer that tells you that if you want to open a file go there and look elsewhere。

 but when you make a hard link you actually create two entries in the file system that point to the same file and there are some implications of hardling also soft links when you when you have a soft link and you delete the original file it gets deleted and you might have a dangling pointer which is a missing shortcut in Windows but when you have hard links。

 this does not happen because the file system knows that there are multiple names sort of file you delete a file it only decrements a F count and does not delete it if there are other names map profile。

The other thing that is a restriction is you cannot actually have。

Hard links for directories because this can create circular loops within the file system if your parent directly is pointing to a rule or child directlyy that goes and points to another upper level directlyy this might create a loop and that causes all kinds of problems because the file system hierarchy is an basically graph it's a da so you don't want loops which will cause problems for things like backup programs because they never term it they just sit in the loop trying to essentially keep backing the same data over。

So you can have soft links for directories， but not hardly。For individual files。

 you can create both hard links and soft links。So those are all things to keep in mind。

Now I'm not going to go into directory operations in any detail just as you can create a file。

 you can create a directory， you can essentially list all files in a directory。

 you can rename a file and so on。 so these are all standard operations that the file system needs to support but for manipulating directories as opposed to files。

So very quickly as far as protection is concerned there are two methods by which file systems allow you to decide which user on that machine gets access to file so these are called either access to create what is called access control list or AC is the acronym for access control list so what an access control listers is essentially a list of user names that have permissions to access the file and what kinds of permissions or write they have on the file so for each file you will have a list but default that list will have only one entry which is the owner of that file created the file so the owner has obviously access to the file and depending on whether it's executable or just a source file you might read write Ex access on the file but you can keep adding entries to this a saying this other user has access to the file and that is going to be used by the OS。

When you open a file saying， does the user is he or she present in the a and should I allow that user to access that。

 So that's the Windows bay。

![](img/803134ed70f3d96a55f714978c4960bb_25.png)

Uix does something different so rather than creating an arbitrary list。

 it essentially groups users into three categories and they're called user group and world so and it create givess three bits for each group so a user can have readwr or execute permission the Unix group that the user belongs to which we can contain many other users also gets three bits and then you have word so essentially you divide all users into three groups。

 the owner the Unix group and everyone else and so you have more coar grain control than an access control list where you can specify an arbitrary list of users or arbitrary groups and so on。

 so it's a more coar grain method but it's more efficient from a storage perspective because you essentially need only nine bits readwr three readwrite execute bits for users3 for the group and three for world。

As opposed to an a which could be arbitrary size and it might take more space so this is more codes grain but more to storage efficient so that's the tradeoff And the meta point here is using either of these two mechanisms you can control so for example。

 if you don't want to give access to anyone else in Uni you set the readr execute bits for the group and the user and world to be all zeros which means only you have access in no one else as access or you can give access to users within your group and so on and so forth。

Okay now with that in mind， so we have quickly gone through inmemory data structures that the file system maintains。

 which are the process file table in the global file table as well as some highleve concepts of how open close read write and all of these things work So in the remainder of the lecture I'm now going to switch to on disk data structure So this is the complementary part of a file system where we are going to discuss what does the file system do on disk how does it actually store data and disks and so on so in other words going back to this picture I showed you earlier we are now going to look at the lower layer which is the hard disk and how you can implement a file system data structures on your disk。

so let me show you first how typically magnetic disks work。

 This is now getting somewhat outdated because most of your computers have solid state disks that don't look anything like what Im going to talk about。

 but it's still instructive to see this because there are still plenty of servers that use magnetic disks as well。

Yeah so typical disk looks like what a C looks like。

 you've seen what DCd or a DVD So it includes a circular platter where data is recorded and this picture here shows us that data is recorded and concentric tracks concentric circles called tracks and each track is divided into a smaller chunks per sector a sector is the smallest unit of data that you can read or right from disk so you will basically tracks are going to get numbered so maybe the innermost track is0 and the outermost track is n so to address something on a single platter you specify the track number and then you specify sector number within that track So you say track5 and sector cell So within each track the sectors are going to be numbered0 to and the tracks are also numbered0 to and going from the innermost track or the outermost track and typical disk is actually going to have more than one of these。

Platterters， as is shown in this picture。 So think of them as a stack of Cd wrong。

 All of them are spinning。 So you essentially also have the。The platter number。

 which is called a cylinder。 So you essentially will have cylinder and a track number and then a second。

So typical access to the sector of。A fileile is going to involve some overhead because you have the disc head that the sptter is spinning and the disc head is positioned at a certain location which means that it is going to be positioned on a certain track so if you want to read data elsewhere you have to mechanically move the disc head to another track that's called the seek time and the time to actually move the disc head to another track or a cylinder and once the disc head is positioned on the right track you still have to wait for the sector to spin by and go under the disc head when you can read the right that's called the rotational latency and then your transfer time which is when you actually reading the right。

All the time spent in doing seeks and rotations are raisedted time because the disk cannot actually do any IO it is simply trying to move the disc head to where it needs to be to actually do I so many file systems that are designed for magnet and disk are going to spend some effort in trying to reduce the seek and rotational latency and this is done by efficient layout on the file of the files on disk to reduce your seek and rotational。

so that's something we want to keep in mind now none of this is going to apply to magnetic disk because switching to another block is instantaneous。

 it's like going and reading to another location in Ram。

 there is no overhead regardless of how far the next location is with relation to the current location in magnetic disk。

 the further away the next sector is on the current location。

 the more the seek time and potentially the rotational latency the higher the overhead in SSDs and in。

are similar to similar to where there is no such over。

 so many of the optimizations that file systems will have performed for hard disk no longer apply to SSs and SSD file systems can be designed differently because some of these overheadst need to be don't exist and you don't need to account from them。

So with that in mind， let's look at how files are organized on this。

 So essentially for every file you're going to have a table and that table is going to track where blocks of the file are stored on this。

 So will say each file is going to be numbered So let's say you have file 0 you say where is block 0 stored and you have address which says it's on platter0 cylinder 0 sector0 and block one is on platter4 cylinder 3 sector and so again。

 like in memory and process layout， we can have disks that are contiguous or not。

 which is why you need this table to track where the file are stored。

 So this file table is similar to a page table for a process page table tracks where the pages of a process are stored in on disk file table tracks。



![](img/803134ed70f3d96a55f714978c4960bb_27.png)

Now which refer to as an i note in just a moment or a file descriptor tracks where the blocks of the file are stored。

 So there are similar concept。 remember that last time I also mentioned that you can have logical block addressing where rather than using this。

Tple of pla number， cylinder number sector number， you can just uniformly address the blocks from0 through n and then translate it internally to this to this triple so you can use either of these to addressing mechanisms in your file。

So now the question is， how are we going to lay out the files so that they support sequential and random access efficiently so that you can figure out where the blocks are on the file and so So So to do this we need a key data structure for every file that is stored on disk which we call the file descriptor this is separate from the per process and the global file table those are in memoryory data structure this is an on disk data structure So for every file is stored on disk you're going to have a file descriptor file descriptor is going to track all the information that you need to access that file from disk so it is basically the metadata structure for the file the file has data which is the contents of the the file descriptors metadata for the file now to efficiently store the files on disk we make a couple of observation which is that most files are going to be small the mean file size of files on disk is still between four and。

8 kilo but most of the storage space is taken by a small number of large files so there are lots of small files but they don't actually take a lot of space and aggregate。

 but most of the space is taken by a small number of large files So what this means is you need to provide good access to both small files and large files while optimizing for the common case and the common cases that files are actually small so you want to allow sequential and random access。

 you want to make sure that you can access small files efficiently as well as large files maybe as somewhat efficiently so you look at three different layouts here。

For all your store your files on this this simple one is contiguous allocation So this is like what you had in for process allocation where you allocate a chunk of disk space and the file is stored contiguously so here all you need to know is the starting location or the file or this the starting address and the size of the file so because all the blocks are stored contiguously once you go to the start location you can just access all the blocks without any additional information So the file descriptor just needs the start address and the size of the file。

Because it a very simple organization It is going to allow us sequential and random access because once you know the start address。

 you know the fifth block is stored which is five blocks from the start location of the file and so on and sequential access is also fine because you are going to just do one C can just read that entire file from starting to the end so both C can sequential and random access are efficient the problem though is that this can cause disk fragmentation just as continuousiguous allocation in memory cost in memory fragmentation so the file grows and there is no space to grow because you store another file right next to it then you are going to have to move the file or given error So you have all the problem that occur when you fragmentation once you start the adding and deleting files youre going to have holes and so on and this is addressed through disk deramentation programs that are going to go and move files around to reduce fragmentation all of them post overheads。

A contigious， although it's very simple。A method is not used in sophisticated file systems just to avoid fragmentation issue but theyre still used in things like CD roms and DVD roms where you only write ones so there's no fragmentation so if you're trying to create a DVD and write a bunch of movie files just write them sequentially one after the other because these are right one's devices you don't delete any files once you write to them so it's fine to use the simple allocation it's sufficient and it's simple to。

Next author is a linked list， so you keep files as linked list but each block of the file has a pointer to the next block and as shown in this picture here where you file descriptor。

That is the pointer， the head pointer to this link list which is the first block of the file on this can you see the address at the last location on the file deor and then you in the block of the file you store data but the last byte or two of the file or three bytes in this case or three or three words are going to essentially have a pointer to the next block and so。

So so that's an organization。 It is actually used by some primitive file systems as well。

 such as the doOS。OfRe file system use the linked list organization。 Now， as you can imagine。

 in this case。Sequential access is fine where you access each block and then you have a pointer the next block and so on。

 but random access is not going to be efficient Now just turns in any linked list if I say go access the Ih location of that list。

 you have to start from the head and sequentially scan through the linked list until you get to the Ih location so random access is not going to be efficient here but sequential access is fine and to access all n blocks sequentially you're going to incur n6 because the blocks are no longer assumed to be continuous and you got to go through each block to access the next block and so on。

Now there is no fragmentation in this case because any block can be anywhere so you got rid of the fragmentation problem。

 you can increase the size of the file by just adding entry to one more block in the linked list and so。

so the last organization that we want to discuss here is the indexed organization where you essentially have an index which is a table and it has pointers to blocks on this so there's a simple single level index shown here it's essentially an area where you want to access the I element to go to the I location in that index。

It gives you discarders to go to that location， read the block。

 and you have the eye block of the file。So this is an organization that's going allow efficient access to both sequential and sequential and random axis to a file。

 and all you've got to do is read the file descriptor into memory and then essentially the indexes looks like an array。

 you can scan it sequentially and read blocks or you can just go to any location I in the index and get the Ih block。

Now one issue with the index organization is that file descriptors are preallocated by the file system when you format the file system it file system creation time so when you create a file you have to allocate this descriptors and you have to decide how large that index needs to be at creation time and since files can be a arbitrary size you don't know ahead of time how much any particular file is going to be so this file descriptor has to be preallocated to be large and the size of the entries in the index also determine the maximum file size。

Now since I already mentioned most files are small。

 allocating a large index for every single file of preallocating a large index where every single file is going to be enormously wasteted because all these entries in your file the script are going to be wasted but you have no choice but to do that because you don't know ahead of time how large that file。

 any particular file might be when the the user creates them at a load later time。

So to address this issue the system do is a multile index this is in a unique terminology or an i note on an index node where you basically have a multi level index。



![](img/803134ed70f3d96a55f714978c4960bb_29.png)

So as I shown here， the file descriptor only has2 entries。

Or other 14 entries the first 12 entries of that file descriptors are direct pointers they point to disc blocks that are would be part of that file if the file is larger than 12 blocks then the 13th entry is actually a pointer to a indirect block which has another 10。

24 entries as is shown here so that is called a single level indirect。

And the file goes beyond 12 plus 10，24 blocks in size。

 you use the 14th entry where you point a block each other's block point。

 another block and those are the ones that have pointers to block so there are two levels of indirect so these are called a double in and modern file system have a 15th entry which is a triple indirect block。

So the reason this is more efficient is because most files are small you are never going to use the 13th and the 14th entry of the file descriptor maybe you're going to be okay by just using the first2 entries So all you need to do is read the file descriptor and most of the contents。

 the file you can access to the first2 entries because most files are going to be the one or two blocks in size as we saw but in some files are large you can also support larger file file sizes by using the single indirect the double indirect and the total indirect blocks of the file so this is how the Android structure is created and the important thing is only the file descriptor is preallocated so only the 15 entries of that area are preallocated that single double in indirect blocks can be allocated on demand just as you allocate blocks when the file can also allocate this blocks with the file descript so you never waste any space by preallocating a giant structure for large files。

so this is a multilevel index， it supports incremental file growth it's efficient for small files。

 but it's also reasonably efficient for large files because well just have either one two or three levels wind directions are still not bad as a linked list where you order essentially scanning the with file so its。

Its some less efficient for very large files because the level of indirect grows。

 but it still supports it with no more than three level3 block6s and three rotational latencies because to get to a block in a large file you will have it most read the file description or read the single double in triple indirect blocks to get the address and then you can read the block。

The file size is still bounded by the maximum file size is still bounded by the number of entries you can store in this multileve index which is going to be 12 plus 1024 plus 1024 square plus 2104 cube those are the number of entries maximum of entries you can store in this in the structure。

The last thing I want to say here is how does the file system know which blocks are in rules and which blocks are。

Not in use or free。 And this is done through free space management。

 So so you can essentially do the same thing as what are did for tracking free pages in memory。

 you can have a bitmap one for each sector of the disk or block or the file where zero says that that sector is available one says it's not and so on。

 So if you want to now allocate a new file you can scan through bitmap and look for some chunks of zeros so you can create that file you need only one zero to create allocate one block but if you want to create a new file a Uuristic might be find a region where there are a chunk of free block so that you can store blocks of the file close to one another and they don't have continuous the closer they are the lower the seek over it that's not an issue in SSDs but still a good heuristic for normal files for a magnetic disk for the system。

Now in the free deleteta file， the blocks are basically marked free in the free block list。

And when you allocate a blocks to file， you're going to scan and find entries that are allocate and then turn them into one and allocate them to a file。

Now one thing is the bitmap itself might be too large to keep in memory a very small2 gigy disk。

 which is like a USB thumb drive might have as much as 4 million entries and if youre two terytes that is three orders sub magnitude to large so you don't want to keep gigantic bitmas in memory So what file systems will do is they'll partition the bit maps into zones of a file or regions of the disk rather not file and then only bring them into memory as needed So this is one way by which you can reduce the amount memory needed to keep that entire free blocklist in Ram at all times。

Okay， the last thing I want to mention is a picture of what the disc looks like。 Okay， so here。

We basically ignored the circular structure of a magnetic disk and we are using logical block addressing and well address the blocks from 0 to 127 and as you can see here block zero is typically called a super block the superb keeps metadata for the file system and you'll see here it has the free block list this is a toy file system there only 127 block so there are 128 entries and then there are inots that you preallocated in the super block typically a real file system will have more than one super block because you precreate a large number of inots the max number of files is determined by how many file descriptors you are located at format time and so youll have multiple super blocks at multiple locations on this that are stored all of these i notess in there here you are only one but you will have more than so so your super blocks and regular data block So anything that's not a superb。

And creation time is marked as with a zero， so it's a data block and it is available for use and as you create files。

 you are going to start using these iode entries。Up for allocating them for new files and then you're going to start using your blocks on disk to allocate data to storage space to each file directories are also stored in the same fashion。

 every directory is an i note because from Uni perspective a directory is just a file but it's a special file where it has a table of other files contained in it So the data blocks of a directory will actually a pointers of file names and their i note numbers so they are stored in a similar organization so this is a picture you want to keep in mind for your all disk data structure this is how typical disk layer is going to look like and then everything that you have inside in ran are other data structure like the process file table and global file table name so。

So with that background I'm going to end the lecture for today and what I'm going to do in the next class is to talk a little bit about the Linux file system。

 how is it organized on disk how INots within Linux work and so on as well as the Linux file server process which is now called a virtual file server process that tells us how Linux actually implements a file system in the kernel itself as a user space process rather not in the microcon。

 but within the OS as a user process So let me stop here for today。



![](img/803134ed70f3d96a55f714978c4960bb_31.png)

![](img/803134ed70f3d96a55f714978c4960bb_32.png)