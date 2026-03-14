# 【Cpponsea】C++-On-Sea-2025大会-p04-P04_C++_中的_智能指针-库什布_维尔马_2025--BV17V4GzjE6p_p4-

Good morning， everyone。 Thank you so much for joining me today for our talk on smart pointers dumb mistakes。

 It's a lovely morning。 The view is perfect from here。 and I'm super excited。

 you gonna talk about this topic。 just a brief background know when I first started like my first programming language was C。

 know when I started。 So I started with C and eventually I moved to C and I also did Java for a bit。

 And I know that one of the most dreaded topics that anyone has to you know encounter when they start learning C plus is pointers because you know it's really hard to understand know what's happening what memory is a reference to so we all know that a pointer is reference to some memory。

 right， So memory management becomes an issue in large scale systems。

 you know there are so many scenarios where memory leaks are happening and system alarms are going off So it's really interesting to see how memory management works in C plus and as C plus+ is advancing more there are better ways to do memory。

😊，mananagement and smart pointers were introduced just for that so before I begin I would like to give a quick introduction about myself so I'm Fuushpo Verma and I'm traveling here from India this is my first time at CPP onC and the energy here is in traveling I'm really loving the vis so I currently work at a company called Appite I'm a platform engineer there App is an open source back as a service and we offer function server list function sites storage authentication and everything under Onero so。

😊，Now before we start let's do like a quick exercise。

 so you would see like a quick snippet on the screen and I just want you to spot the bug like just tell me like you know what's what's going on。

 what's wrong here， anyone who would like to you know share。😊，I think we have someone there。

Can you pass。有。And you嗯。There are two pointers are like two own point in within or a7。Yeah。

 that's correct。 So if you all have been working with C++ for some time。

 you all know that the powered pointers give to us， but at the same time。

 they also you know bring a lot of pain and managing them is difficult and we all make obvious mistakes in code now and then for decades managing memory in C++ involved a lot of manual knew and delete operations right which let's to be honest it was like little hard sometimes they used to forget you know call delete in different flows where the flow was going if the errors were coming and situations like these happen you know where we might address memory and we do not realize like what's exactly happening behind the scenes So you know let's say that this is like a bug that you know it's very frequent to see so we can see in the first line that we are using a unique pointer and we are using make unique to point it to a particular address and then in the second position I'm again doing So I'm referencing that pointer which is A and I'm doing A do get and I'm。

😊，You know addressing it。 So initially， if you look at the first one。

 it is like a pointer to a10 array of size 10。 So if I do array get plus 5。

 it is pointing to the sixth position in the array right So unique pointers as we see further as well in the slice that they automatically get deleted。

 So in this particular case it will try to delete it twice when the memory goes out of scope。

 So this is exactly the problem that's happening here a double deletion is happening So as I said earlier like the array was actually pointing the array was like array of size 10 and it would have called the delete array operation and when I to get operation。

 it is pointing the sixth position and when you know that line ends。

 it is gonna try to delete that location again So as the rule of thumb always try to you know have clear ownership like okay what if a memory is there like who is exactly owning it who is responsible to manage it and who is responsible to clean it。

 So there needs to be clear ownership there。😊，So。😊，Now。

 let's just take a step back and let's talk about， you know why are we even discussing this topic。

 why this talk is even important。 So you know we all know that there are so many big companies and there are so many bugs that happen in production。

 So these are some statistics that I was looking at recently that Google has reported that 70% of the security bugs happen because of memory issues and I have personally seen a lot of memory issues in production and I'm sure that all of us have and even Windows has been having a lot of these issues are used to work at Microsoft before and I have seen you know how these challenges used to creep in every now and then and we know that smart pointers are introduced but smart does not just mean magical there has to be certain gotcha to it like certain things that we need to take care of as developers just because it is smart does not mean it is gonna take care of everything automatically and so what we will cover in this particular slide first of all we'll talk about draw pointers and why they are still relevant today and then we'll talk about different。

😊，Sove smart pointers like unique pointer， Sha pointer V pointer。

 And we'll also talk about the tools that we can use to catch these issues early on。

So these statistics just show the importance of you know why it's so important and we'll see some examples of you know commonly introduced bugs that we can all make time to time。

 So yeah before starting， let's talk a bit about draw pointers which are the foundational topic right so why we start here because smart pointers are actually built on the concept of raw pointers underneath it is still doing the same thing。

 it is still using the new and delete keywords right so it's really important to understand the ownership and the semantics of what's exactly happening and exception safety is nearly impossible to get right manually like I have made a lot of mistakes and again and again。

 we keep seeing those bugs where some memory unique is happening or something is going wrong in very few scenarios and it's really hard to debug it and smart pointers actually help us automate RAIi for us which we talk in just a second。

 but if we look at the code snippet in the slide so it it is using the new keyword to allocate。😊。

MeoryAnd you know whenever we have use the new keyword。

 it's very important to also delete and delocate the memory that is being used。

 So if you look at the snippet， let's say that there is an error condition， right。

 which is unexpectedly terminating the entire flow。

 So in that particular case as we can see here that the return statement is you know returning it and somehow the developer for know call the delete operation there。

 So it would lead to a memory leak right So as we can see that in the normal flow we had added the delete operation。

 but there are certain scenarios where you know an error might occur an exception might occur at a certain line in the code。

 and it might not delocate the memory and you know in small scale it might not be relevant。

 but if you're running huge production systems then these small leaks become huge right and they can bring an entire server down So it's very important to start there。

😊，Now we all know about RII principle。 It is the resource acquisition is initialization right so what it helps in ensuring is that you know first of all。

 automatic cleanup happens so whenever anything goes out of scope there needs to be an automatic cleanup that happens so that you know we do not make those mistakes and there needs to be exception safety whenever an exception is occurring we need to ensure that we exit through the program in a safe manner we just do not terminate the program in an unexpected manner and no memory or resource leaks should happen so some common RII classes that you know we all have been using in C+ plus are unique pointer and shared pointer which we are going to talk about so these are the smart pointers and then we also have vector and string in C++ and that's the reason we do not do new vector it's automatically you taken care of in terms of managing this dynamic of memory and then we also have I stream and all of these file handling things you know all the file handling classes there。

😊，Following RII and then the mutex logs， the logguard and the scope logs they're also you know using this。

 So we all know that any resource which you know it could be memory or it could be socks or files or logs you need to have a constructor and a deor and what happens is that inII it ensures that you know the resource it ties the resource management to the object' lifetime。

 So once the object goes out of scope， it automatically does the memory cleaner for us So the deor is automatically called when the object goes out of scope and exception safety is there by default but implementing all of this correctly could be error true and this is where know smart pointer shine they implementII for us so we do not make the mistake that you know there in raw pointers previously So let's first talk about what is unique pointer so unique pointer as a name suggests it is pointing to a unique location in the memory and。

😊，It means that it has exclusive ownership over the resource that it is accessing。

 which means that unique pointer cannot be assigned to two memory locations at the same time。

 it can only be moved， right。😊，If we look at the code on the screen it says that auto pointer is we use the make unique you function and you know you always use this and we pass the resource that we're trying to make unique and what it promises us that there is gonna be automatic cleanup so whenever the scope goes out the memory is gonna be clean so you do not need to call delete manually and then there is it is exception safe it has the move semantics as we mentioned it is gonna move the pointer so if it was pointing to one location in the memory and then you want to access another location it's now going move from here to here it's not gonna point to both the locations at the same time and it has0 overhead and we'll talk about in a performance just in a bit but if we look at the basic Q sets synts there so you can initialize unique pointer I would like to point out that it is a part of the memory header so if you want to use unique pointer you can do hash include memory and it's gonna be included and so you can initialize it it has like the template。

😊，Any type of you know data it could be an intesure it could be a string or any other data type you could initialize it and if you use the make unique it is gonna initialize it properly and you can also use it for arrays as you can see on the screen here so and if you want to move it now then there is the move function that you can just call so essentially just to summarize it is representing exclusive ownership it cannot be cop。

 it can only be moved and it has zero overhead but there is a cache there that if your builds are optimized then unique pointer does not have much of an overhead it is pretty similar in performance to raw pointers and it is exception safe you can prefer it over new always and the array version automatically uses delete array instead of just delete so it automatically takes care of all of that for us now。

😊，To talk about some go jars， you know， some things that you know can happen。

 some common mistakes that we can make the first one， as I mentioned is double delete。

 So in the previous example as well that we saw that you know whenever we use get。

 it is actually returning the raw pointer。 but it does not transfer the ownership。

 So if you do something like this like if you do make unique。 And then you try to do pR dot get。

 that's just going to return a reference to the raw pointer and if you try to do that its the deor will try to trigger again。

 and it will try to delete every location， which has already been delocated。

 So double deletions are very common。 So just a rule of count there is to keep in mind that do not try to use get and then delete at the same time。

 So。😊，This is one of the most common unique pointers bugs， I think that you know is that happens。

 and you know even in the second example， like we can see that。

 you know when we are doing install row and we are doing point or get and then I'm again trying to know use that pointer inside my unique pointer in both of these cases。

 you know theyre gonna be unexpected behaviors that we will see and both will try to delete the resource when you know they go out of scope。

 So only use get when you're trying to pass you know raw pointers to functions。

 do not try to use them in conjunction with unique pointers if you are doing。

 please try to understand that please try to ensure it is not trying to delete memory multiple times it is only deleting it once。

 So this could be one of those scenarios which could be problematic。😊。

The other one is where you know we might confuse between arrays and single objects。 So again。

 just to look at the code in the first one so there is this undefined behavior happening where I'm initializing the unique pointer and I'm pointing it to an array so I'm again initializing it to an array of size 10 and whenever it's gonna go out of scope it would so notice here that I'm creating a unique pointer of type integer but then I inside the array I'm doing new in so Im using new keyword and unique pointer in the same exact line and what it's gonna do is that because it is a unique pointer of type intesger where it goes out of scope it would call delete and not delete array right so in that case it would be having unexpected behavior so what would be a better way to write the same code what we can do is that we can actually initialize it if if I'm doing an array inside it then I need to pass array here as well So in the unique pointer I need to do in and then array and otherwise I can obviously。

😊，Make unique and that's gonna take care of it for me。 So this is a subtle but critical distinction。

 And using delete on memory allocated with new array is undefined behavior。

 So the compiler might not cast this mistake And you know there is it' always a good idea to use the array versions for arrays and single objects versions for single objects。

 So try not to mix both of them。 So。😊，Unique pointer integer will expect a single object like new and not new in array。

 So that was another butcha。 Now the third one that you know can usually happen is when custom deletes go wrong right so let's say that in the core example here So there is like a cleanup counter that's an integer that I'm maintaining and then I have a lambda function which is delete and as you can see that it has like a pointer and here I'm trying to capture it by reference。

 And if you see after below this lambda function I'm creating a unique pointer where I'm using this delete right So custom deletes are very powerful as we all know。

 but they can also be dangerous if not you know managed well。

 So if we try to capture local variables by reference it could be a common mistake。

 So the delete might be called after the captured variables are destroyed right So it could happen that it goes out of scope and after that we are trying to delete that particular memory location。

 So in this。😊，Particular case， the pointer can outli the function。 And after that， it would try to。

 you know， delete some dead memory， which does not really exist there， so。In this particular case。

 we are capturing the cleanup count by reference by inside the lambda function， as you can see。

 and then I'm trying to use this Lada as a custom delete inside my unique pointer。

 So in this case the cleanup count is a stack variable right and it would be destroyed whenever the dangerous delete function is gonna return but the lambda inside the unique pointer will still hold a dangling reference to this particular memory location and when this pr would be destroyed later on。

 it will try to access the cleanup count variable， which is a dangling reference。

 it does not exist now right it would cause an undefined behavior So why is a dangerous right it is dangerous because the unique pointer is storing the delete by value It is not storing it by reference and this means that the lambda is actually copied inside the unique pointer and the lambda is capturing a reference to a local variable and the reference becomes invalid when the function returns and any access to any。

😊，Cleanup count variable after that， it's gonna result into use after free error。

 which means that you're trying to use a variable after the memory has been freed。

 So try to avoid these you know， scenarios where you're trying to access something which might go out of scope。

 you know， even before you try to access it。😊，So that was about unique pointers。

 Another popular smart pointer we have is shared pointers。

 and as the name again suggests it has shared ownership right So if we look at this in it promises that you know if I create a pointer which is pointing to one memory location this pointer can also point to another memory locations。

 So it's like a shared pointer between both of these memory locations。

 So just like we had them make unique here we have make shared。

 and I can pass the resource inside it。 now this resource could be any data type。

 it could be intesures， it could be string， it could be arrays。

 and as we can see in the second line I'm doing auto pr2 equals to pr1 So what shared pointer actually does is that it maintains a reference count underneath So it tells me like how many memory locations am I trying to access with the shared pointer and object is destroyed when all shared pointer resources are destroyed。

 So when the last one gets destroyed that is when。😊，Sd pointer is also destroyed。

 So if I talk about a couple of key concepts here， it is going to track how many shed pointers are pointing to a single object right and it is going to store these reference counts and other metadata inside it。

 which is why it has a bit more overhead as compared to raw pointers because it is keeping count of how many objects of how many pointers are refercing to a particular object and。

😊，It is this reference counting。 It uses atomic operations。

 I would like to point out that reference counting is threads safe。

 So if multiple threads are initializing pointers to the same memory location in that case。

 it's gonna be a threads save operation。 It's gonna you know perfectly fine and objects are destroyed when the count reaches zero。

 So if the multiple pointers pointing the same location。

 it would be destroyed when the reference count becomes zero right So it enables shared ownership。

 it has multiple pointers to the same object and the reference counting is automatic and it has more overhead over unique pointer as well because it has control block and the atomic operations but it solves problems that unique pointers you know h that that is why it is important to use shared pointers in multiple scenarios。

 but。😊，There are you know let's talk about the control block that happens with shed pointers So if we look at the example here。

 so I'm making two allocations here， if we look at the first line so I'm initializing a sharedd pointer of type integer and it is called PTr1 and inside it I'm doing new int 42 so as you can see in the same line I'm also doing sharedd pointer and I'm also using the new keyword so it is an object allocation and also a control block allocation and if you look at the second line I'm doing autoPr2 and I'm doing make shared and I'm creating an integer right so in this particular case it's just a single allocation。

😊，So the control block is having the reference count。 it will also have a weak reference count。

 and it will have custom deletes and allocators。 So basically each shared pointer has some metadata that it is storing there。

 So it has some memory overhead as compared to unique pointers and it is gonna maintain all of this internally for us。

 So this is a crucial performance consideration。 So you know the weak reference count for weak pointer support we're gonna see in a bit。

 So there are also a couple of gold charts with shared pointer。

 So when I' using shared pointers in production there are a few things to keep in mind the first one is a circular reference。

 you know there could be a circular reference deck where a parent class is referring to the child pointer and the child is pointing to the parent So in the below example you can see that we have a parent class inside in the parent structure I have like a shared pointer and it is pointing to the child。

 and then I have a child structure and it has a shared pointer and it is pointing to the parent So as we can see there's a。

😊，And since both of these objects have interdependency on each other。

 it's never gonna go out of scope。 and it's never gonna get cleaned up。

 right So if you look at my code below， I'm initializing both of these structures。

 I'm making them shared。 and I am trying to you know make the parent has reference to child and child has reference to parent。

 and it is going result in a memory leak right So the key insight here is the reference counting cannot handle cycles。

 So this is a fundamental limitation of reference countings。

 garbage collector languagens like Python have cycle detectors， but C+ does not。

 So we need to break the cycle manually somehow right So how can we do that right。😊，In this case。

 we can actually use something called as a weak pointer。

 so the weak pointer or I can also call it the cycle breaker in this particular case。

 So I will like to show you how I'm using this in the below example。

 so similarly just like previous example， I'm creating a parent structure and I'm creating a shared pointer to the child structure but inside the child I'm not creating a shared pointer now I'm creating a weak pointer so the weak pointer is now pointing to the parent and this is now a correct implementation and it is a safe usage because as you can see that now the parent is alive and you know I can just track like when iss the parent alive。

 So weak pointer is basically holding a weak reference which does not affect the reference count so whenever we are using weak pointers。

 please note that you need to use locks there for safe access so try to use lock whenever you are using weak pointers and the lock will return an empty shared pointer if object was already destroyed so if。

😊，I want to check if the object actually exists。 I can check if the lock is returning an empty pointed to me。

 and if I do that， I know that when the cycle is breaking and I can you know just end the logic there。

 So only the parent in this particular case is holding a strong reference to the child's structure。

 the childs structure is holding a weak reference to the parent and when the parent is destroyed。

 the child the child will also be destroyed basically。😊。

So there are certain usage patterns where I think weak pointers would very well。

 So in this particular case in the observer pattern。

 so the observer pattern is a perfect use case to you know for weak pointers So the observers let's say that there is a subject and there are multiple observers there right so you know observers should be destroyed without notifying the subject or having any dependency on the subject lifetime right so the subject should automatically clean up all the dead observers right it should not happen that you know they have interdependency and one is know there's like a dead situation where one is trying to depend on the other lifecycle so in this particular case there would be no memory leaks there will not be any dangling pointers and this pattern is actually extensively used in all the gray frameworks so if I talk about the quote very quickly so I have a subject class and inside it I have a vector of a weak pointer so basically I'm maintaining a vector of all the observers that I have and then I。

😊，Using a notify function and I'm I trading over all the observers that I have and I'm trying to first check if the lock is returning something right only if the lock is valid in that case。

 I'm updating my observers and I'm incrementing the counter otherwise I know that there is the subject is probably not there anymore and I can clean up all my dead observers。

 So this is a safe thing。 No cycles would happen here。

 So try to use weak pointers in conjunction with shed pointers to make sure that the memory is cleaned up properly。

😊，But let's also look at how the lifetime or life cycle of a weak pointer works。

 so inside the scope the weak pointer can be locked to access the value and outside the scope the shared pointer is destroyed so weak pointer becomes expired so let's talk about the code line by line so I am initializing the weak pointer life cycle inside it Im initializing a weak pointer and inside that I'm initializing a shared pointer。

😊，So I'm then pointing the weak pointer to the shared pointer。

 So the weak pointer is observing my shared pointers location。

 and then I'm checking if the lock is still there。 So if I'm checking if the weak dot lock is that means that my weak pointer is still alive。

 So I'm going enter that condition and let I'm just doing some logic in this case I'm just printing that that I'm inside the scope and the pointer is alive。

 otherwise if the lock returns an empty reference， it means that you know strong the shared pointer is no longer alive and I can see that the weak pointer has expired right and after that the shared pointer is going out of scope and I can also check if the weak pointer has expired outside the scope as well and it will tell me if it is expired or it is still alive So basically it is preventing these dangling references by not extending the object's lifecycle or lifetime。

😊，Now there are more gotchas to using shared pointers。

 Another thing that could happen is aliasing the constructor trap so the aliasing constructor is a little known but dangerous right so it creates a shared pointer that points to a different object that than it owns and it is useful for pointing to memories of larger object so if we talk about the code I have a big data structure here and inside it I have a vector which let's say it's a huge vector it could be1 in size or 10 ms in size and then I have a small integer in small value and then I have a big data and I'm making this a shared pointer now if I try to make a shared pointer with this small pointer where I'm refercing this big data so let's say that I just wanted to access a small integer or a small value right in this big data and I'm using you know this pointer for that in this case the big data won't actually be destroyed because the small reference is still pointing to that big data。

😊，So basically it is creating a shared pointer and it is useful for pointing to the larger object but what is happening is that it is keeping the entire object alive even if you only need a small part so let's say that there was a really big file of multiple Ms and you just still needed a reference to a small portion that's not good practice because it is still gonna keep the entire object alive in the memory and it can cause significant memory bloat in the long-run application。

😊，So after that， another one that could happen is the threat safety misconceptions that you know people usually have with pointers。

 So very common misconception that people have with shared pointers is that many people think that shared pointers are truly threat safe。

 That's not the case。 So the atomic reference counting is protecting against double delete So the reference count inside a shared pointer is thread safe。

 but shared pointer itself is not always thread safe So you know copying or assigning shared pointer needs synchronization and the object being pointer to needs its own thread safety So whenever you're using shared pointers please ensure that you take care of threat safety you ensure that know multiple threads might not cause problem and whenever you're using shared pointers always try to use mut textes and locks to ensure that know shared pointers have proper sharing between different objects。

 So just to give an example of what could go wrong in。😊。

systemtem is that if I'm creating a shared pointer。

 which let's say in my case is called global pointer。 the first thread is actually。

 you know global pointer is said one。 it is referring to the shared pointer by using the make shed and it is referring to a position。

 but then I also try to create another thread by using the get you know auto local is global pointer。

 So in this case it's gonna have a race condition right So the shared pointer itself is not threadsa and only the reference counting is threads safe。

 So please make sure that you are handling it properly with logs and mut tes wherever applicable。😊。

Now， again， another gotcha that in sharedd pointers that could happen is that exception safety is a common thing。

 So you know this is subtle but critical exception safety issue that could happen So in this case if I show you what I'm doing is I'm creating a process where I'm initializing a shared pointer and I'm doing new a inside it right and again I'm doing shared pointer new B So you know it could happen in any order。

 so but what we you try to do is it will try to do new a new B and it will try to create a shared pointer using that but let's say that if the new a happens and the new B fails it's gonna the new a is still gonna be dangling somewhere you know there is not gonna be a proper cleaner that would happen for that new a that was already done So in case any exception occurs in this particular line then I'm gonna have again dangling pointers and memory leaks So this is not a good way to write this particular line so just below I have。

😊，Sn a safer way of writing the same thing。 So if Im I can just actually create a shared pointer for a and then I can do for B。

 basically inside behind the scenes， it is again calling the new pointer。

 But if I'm calling the first line it ensures that you know the a was completely like clear created properly and there were no exceptions or no dangling memory。

 the me is gonna be cleaned if any exception occurs in the first line and the second line won't be executed。

 And then once I have initialized both of these using make shared then I should call then pass them inside the process function that I have so。

😊，Basically there's no particular order in which it might happen。

 but if one of these pairs is gonna you know co me D leaks and the make she will actually prevent this by ensuring that no raw pointers are existing and make shed and make unique are strongly preferred。

 So whenever you are doing like a sharedd pointer initialization please try to use it along with make shared just like unique pointers have make unique in in case of sharedd pointers always try to use make share right So that's that。

 And now let's do like a quick overhead comparison between different pointers so。😊。

In this particular presentation we have talked about raw pointers and then unique pointers and shared pointers If I talk about a typical 64 bit system in that case all of if I talk about in terms of size a raw pointer is gonna take8 bytes of memory a unique pointer is also gonna take 8 bytes of memory a shared pointer might take 16 bytes of memory the reason is that you know raw pointers do not have any overhead in the previous example I also mentioned that unique pointers also will not have any overhead if the build is optimized if the build is not optimized then might be some overhead in comparison to raw pointers but in case of shared pointers we have the control block and were also keeping a lot of metadata in terms of metadata we have the reference count we have the weak reference count and we also have you know the delete and allocator and stuff like that so it is gonna have some overhead so。

😊，It also has this atomic operations that you know it performs it is keeping the increment of incrementation of the reference check is checking if it is zero or not。

 So lot is going on there。 So in terms of performance， you know in shared pointers。

 the atomic increment and decrement are happening on copy and destroy So these numbers are actually typical they are not exactly they might vary based on different systems but these are just like a reference of know general system and the unique pointer like to try to optimize it in that case。

 you will not have any major performance shows as compared to raw pointers and the atomic operations that happen in the shared pointers can be expensive if are happening in highly contented scenarios where they are like multiple shared pointers pointing the same object So it might get messy there but again like as I said that smart pointers are not a perfect solution to every scenario So if you have a use case where you do not need a shared pointer where there is no shared ownership of a resource I think you might be better。

😊，use you know unique pointers or pointers。 so it's not the best solution to every problem。

 but it is good enough in situations you know where your use case is actually suitable。

 So there are actually certain tools that you you can use to detect and prevent these scenarios from happening I know that a lot of modern compilers also you issue these warnings when you try to access the unique pointers or the memory in an unsafe way like for example。

 when I run a couple of code examples， it tells me that you know there is a use after free error which means that I'm trying to use a memory after I've already freed it but not all compilers might point out these issues so what I can suggest is that you can use static analysis tools whenever you are know writing production code and you can just run these static analysis to see like if your code is violating one of these you know things and if there are any memory leaks or any resources that you know might not be properly delocated so the Cang static。

😊，Analyer is actually built in into the C line。 It catches， you know。

 many smart pointer issues when you try to run it。 Then there is also a paid solution。

 which is the PVS studio。 It's a commercial product and it has this smart pointer specific checks that will point out if you know your smart pointers are not used in an appropriate way。

 And then if you want to use something free and open source， then there are CPP check。

 which is open source library， which has basic smart pointer validation。

 it can do some basic validations for you。 and these tools are essential。

 So if you're running any production system， I would highly encourage you to implement them in your CicD pipelines to make sure that you know we catch issues early on before they happen in production systems。

 and。😊，If you if you want to do it in the runtime， then there are also certain options on the right side of the screen。

 The first one is the address sanitizer。 I think it is best for use after free or double deletion errors。

 so it is gonna point out at runtime and you can look at the logs and it is gonna tell you so there is this command that you can actually run at runtime to check it。

 It is g plus plus F sanitize address and you can run it video your program so it is incredibly fast。

 It is going catch most of the issues that might happen in terms of smart pointers The other option which is very comprehensive。

 but it could be a bit slower is this wellgri so you can actually run it as well and it is gonna go through our entire code it's going to point out any potential issues that might be happening and。

😊，Then there is also thread sanitizer that you can actually use to check race condition between threads and whenever you have highly concurrent systems in that case。

 it might be better to you know check if multiple threads are trying to access the same memory location in an unsafe way So for that you can run this if sanitized thread and this is gonna tell you like if there are any certain things happening in the system and static analysis will catch things at compile time and these are the runtime tools that you can use at runtime and I would say that there is no excuse not to use these tools in modern application development because if know we can catch issues early on and they can prevent huge down times then I think you know it's really good to check but this is like these are tools for detection but I think as developers the best thing is whenever we are writing any code which is involving the pointers we just need to ensure that no flows are broken there and we just ensure that memories properly allocated and thed and also it's very important to check for every scenario that could happen right if there could be。

😊，Multiple exceptions just need to make sure that you know every single flow is taken care of there there shouldn't be no situations where memory leaks could be happening because even I have organ production systems where happens at only one% of those users are facing an error of there's a which is really hard to reproduce it happens only in certain scenarios it's really good to you know make sure to keep these practices in mind but you know so if I have to summarize the best practices as developers that you know I also keep in mind and you all can also keep in mind is that you know。

😊，Always prefer to use， you know， make unique or make sharedd over the new keyword or the delete keyword because。

 you know， these are implemented to make sure that the common mistakes do not happen。

 And as a developer you do not need to manually handle all the things that happen behind the scene and whenever you are using shared pointers try to use weak pointers to you know break cycles to ensure that no deadlocks happen。

 no cyclic dependencies happen and。😊，Whenever you are using gett。

 only try to use it when you are using with C APIpis。

 because as we saw in a couple of examples that if you are trying to use gett with unique pointers or shared pointers。

 double deletion or more errors scenarios can happen。

 So avoid to use you know get wherever possible and be very explicit it about you know custom deletes you need to know like when it is being used what exactly is it doing and properly clean enough needs to happen and in your Cic pipelines at sanitrs。

 make sure that there are static code analyzers and runtime analyzers which are capturing these errors and you can cache them early on and you should also have some profilers you know which are optimizing and the reference counting is happening properly。

 So this。😊，And also try to understand the ownership of the semantics clearly please understand like you need to know like this is my pointer which memory location is it pointing to and what exactly needs to be the ownership of this pointer if you feel that you know this is a location which this pointer is not supposed to access or this might not be you know even relevant right now make sure to clean up all of that code and it also you know becomes relevant when we are doing code reviews so if you are someone who is doing code reviews and make sure that you know the raw new and delete pointers are not mixed with shared and unique pointers there needs to be like a clear distinction if we try to use everything in the same line it might you know to unexpected behaviors。

😊，And whenever you say that the get is followed by delete。

 please make sure that you know double deletion or something like that might not be happening and you know whenever there are single owner you know use cases where there needs to be a single owner of a resource and someone has use a shared pointer please try to see if it was actually relevant there and you know if there are parent childil relationships make sure that it is a weak pointer is also used in conjunction with the parent shared pointer so that you know the cyclic dependencies to not happen So these rules will most likely prevent 90% of the issues that you might face with smart pointers and every team every engineering team should make it a part of their gender know coding standards or code review practices and code reviews you know if if your company has any code guidelines。

 please make sure you know mention that developers need to look for these particular patterns in their codes and obviously as I mentioned that a lot of。

😊，matic tools are available there， which are going to detect these issues for you。

 but it would be great know if this do not happen in the first place and the goal here is to make the code safe by default and not in exception scenarios where you know an error occurs and then we go and debug what happen in the first place。

 So if we just keep know good coding standards and practices in mind。

 it will help us avoid a lot of production scenarios but you know there are a lot of cases where。

 you know people will say that， you know hey we already have you know legacy code and you know there are already know new and pointers and you know it happens。

 you know there are multiple organizations which have know huge code base since a couple of years and there are know places in your code where these might already be there。

 and if you are someone who is trying to migrate from you know that previous standards to using smart pointers in your code。

 I have a couple of strategies that you can use to migrate your legacy code。

 So the first one is I would recommend starting with leaf functions functions。😊。

Don't call other functions， which are， you know， simpler functions。 try to start there， you know。

And then you can also use static analysis in your existing tool。 So make small changes。

 make sure you run the static analysis to make sure that no new bugs are introduced。 I mean。

 we all know that the the horrors of touching legacy code。😊，Soty。So。

That's legacy code carefully do not break it and whenever you' are making small changes try to start with you know flows which are not very closely coupled try to find leaf functions which are you know not having dependencies on other functions and you know migrate one module at a time。

 try to ensure that it is working as expected try to run the static code analysis analysis and also there are time analysis to see that no new bugs or unexpected behaviors are introduced and。

😊，If possible， try to add tests， unit tests and end tests for all possible scenarios so that you know these whatever code changes you make they do not cause any unexpected new behaviors in the systems and use tools to verify that there no code regressions happening and some common patterns so for example if before you had a function like avoid process data where you had a data pointer and it used to work with a pointer what you can do is you can actually replace this data pointer with this shared pointer right and you can just pass it it would work the same way but the ownership would be clearer there would be like a clear distinction of who is owning a particular resource and there probably will not be any mixups so I know like legacy codes are really hard to change but if you want to make systems better and you avoid know pastting half of a time in just solving bulks that happen repeatedly I think it's better to slowly transition into newer standards。

You know， just make code better。 So that's it from my side today。

 thank you so much for all your time。 And now I would be open to take some questions。😊。



![](img/2e37a17d4e74d56b7f8ef41531f3225b_1.png)

![](img/2e37a17d4e74d56b7f8ef41531f3225b_2.png)