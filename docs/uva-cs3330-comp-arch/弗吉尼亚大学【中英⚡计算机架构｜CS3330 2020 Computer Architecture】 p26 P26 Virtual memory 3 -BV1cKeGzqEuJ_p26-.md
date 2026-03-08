# 弗吉尼亚大学【中英⚡计算机架构｜CS3330 2020 Computer Architecture】 p26 P26 Virtual memory 3 -BV1cKeGzqEuJ_p26-

Good afternoon。So， last time。

![](img/4364ac58e2233347e1856d4b178fc42e_1.png)

We looked at the problem。 our first step along the problem of。

Dealing with our page tables being rather large。 And one part of that problem was that it wouldn't be reasonable to just store the page table in the processor because we found out that for。



![](img/4364ac58e2233347e1856d4b178fc42e_3.png)

![](img/4364ac58e2233347e1856d4b178fc42e_4.png)

![](img/4364ac58e2233347e1856d4b178fc42e_5.png)

Typical virtual address sizes and typical page sizes that these tables would be very， very large。



![](img/4364ac58e2233347e1856d4b178fc42e_7.png)

And in particular， at the least， larger than we would typically want to keep in cash。



![](img/4364ac58e2233347e1856d4b178fc42e_9.png)

So we have the solution of keeping them in memory and we can access memory through a cache or we can cache parts of them so maybe it won't be so bad。

 we'll find out later today that you know that's not going to be fast enough and we'll have a solution and also that this reverse scheme of keeping it in memory is not going to be space efficient to not so we're going to extend it to be a little more space efficient。

But our original scheme was that we'd have a flat table in memory where we take each page table entry and represent it as byte。

 So we just choose some way of laying out the information in each page table entry。

 which remember was like a valid bit。

![](img/4364ac58e2233347e1856d4b178fc42e_11.png)

And some permission bits。

![](img/4364ac58e2233347e1856d4b178fc42e_13.png)

And the physical page number and putting them as some bytes。

 And we have an array of page table entries represented as you know a sequence of bytes。

 basically you know。

![](img/4364ac58e2233347e1856d4b178fc42e_15.png)

You know，So I'm fixed sized integer。That we decode into a physical page number of valid datata in the permission bit。



![](img/4364ac58e2233347e1856d4b178fc42e_17.png)

And we'd had this array and wed just give the hardware， you know。



![](img/4364ac58e2233347e1856d4b178fc42e_19.png)

We'll get a pointer to the beginning of the red。And it would do an array lookup where it would know。

 okay， I have this virtual page number that's， you know， if it's virtual page 17。

 that's element 17 of the array， it would compute the address of that element of the array。

 read it from the cache and then decode it to get the valid bit permission bin and the physical page number。

 process those and then get take the physical page number and the physical sorry in the page offset to make a physical address and send that to the cache to you know。



![](img/4364ac58e2233347e1856d4b178fc42e_21.png)

![](img/4364ac58e2233347e1856d4b178fc42e_22.png)

![](img/4364ac58e2233347e1856d4b178fc42e_23.png)

Actually access the virtual our stick program was looking at。

So this had sort of two problems that we're going to talk in detail today about addressing so one。

Is this fundamental issue that we're kind of increasing the number of physical memory accesses。

 most hopefully just catch accesses， but that's still going to be pretty slow。

 so we're going to run away of making that faster。 we'll talk about that as our last topic today。



![](img/4364ac58e2233347e1856d4b178fc42e_25.png)

![](img/4364ac58e2233347e1856d4b178fc42e_26.png)

And another problem is that we found out when doing some calculations that though this scheme at least makes it possible to fit the sort of page tables we'd want for a 30 2bit system。

Somewhere， it has a lot of overhead and when we think about 604 bit systems。

 even when we're not using all the bits of a virtual address。😡。

It ends up being impractical that we need terabytes of memory to store our page tables for a typical system running a couple processes。

 and that's just not acceptable， so we're going to have a more complex scheme that extends this into something where we have a practical amount of space。

 but we're going to briefly make this problem of accessing the cache more times worse to do that。😡。

But before we get to that， we had a bunch。 We had sort of an interlude yesterday talking about something I called sort of。



![](img/4364ac58e2233347e1856d4b178fc42e_28.png)

I might call page table tricks。So these are things we can do with page tables， you know， things。

 the OS， I should say， the software that runs multiple programs together。



![](img/4364ac58e2233347e1856d4b178fc42e_30.png)

Can do with page tables。Besides， provide programs independent memory。



![](img/4364ac58e2233347e1856d4b178fc42e_32.png)

And we had some mechanisms from the hardware to help this out。 So one thing， for example。

 we found out we wanted to do was we wanted to。

![](img/4364ac58e2233347e1856d4b178fc42e_34.png)

Give read only access。

![](img/4364ac58e2233347e1856d4b178fc42e_36.png)

For share data， so we wanted to have two programs share。

 say some machine code and we wanted to know that when we were doing this。

 that we could still at least preserve the illusion that the programs are operating independently。

 meaning that if one program messes up and tries to overwrite its machine code that it's not going to affect the other program。

😡。

![](img/4364ac58e2233347e1856d4b178fc42e_38.png)

![](img/4364ac58e2233347e1856d4b178fc42e_39.png)

Because that right shouldn't succeed。The hardware can help us with this by adding these permission bits where we can。

 for example， disable writing， given a particular page table entry and how this would work in the hardware is just like the hardware would check a valid bit to see if the page table entry mapped to any physical page。

 it would also check， say a writeriable bit to see whether。😡。



![](img/4364ac58e2233347e1856d4b178fc42e_41.png)

![](img/4364ac58e2233347e1856d4b178fc42e_42.png)

![](img/4364ac58e2233347e1856d4b178fc42e_43.png)

Writing was allowed before it would do a write using that page table entry as part of the translation。

😡。

![](img/4364ac58e2233347e1856d4b178fc42e_45.png)

![](img/4364ac58e2233347e1856d4b178fc42e_46.png)

And we can extend this to other sorts of controls。 We saw our original example of。

Is it allowed to be used in kernel mode， we can also have， is it allowed to be executed。

 We can imagine hardware work could add other features like this if they felt it would help operating systems do。



![](img/4364ac58e2233347e1856d4b178fc42e_48.png)

![](img/4364ac58e2233347e1856d4b178fc42e_49.png)

Interesting things。

![](img/4364ac58e2233347e1856d4b178fc42e_51.png)

This was an important form of metadata。

![](img/4364ac58e2233347e1856d4b178fc42e_53.png)

And after we looked at sort of。嗯。

![](img/4364ac58e2233347e1856d4b178fc42e_55.png)

This extra feature of the hardware provided to be more convenient for things the OS would want to do beyond just independent memory for different programs。

 we also examined the implications of exceptions being involved when page table lookups encounter and error。



![](img/4364ac58e2233347e1856d4b178fc42e_57.png)

![](img/4364ac58e2233347e1856d4b178fc42e_58.png)

![](img/4364ac58e2233347e1856d4b178fc42e_59.png)

And。😡。

![](img/4364ac58e2233347e1856d4b178fc42e_61.png)

We were originally just saying， okay， you know， the page isn't valid or it's read only。

 We're just going to have the OS run to crash the program and run something else。

 We have to run the OS for that because the OS is the only piece of software。

 which is going to know about those other programs， but。



![](img/4364ac58e2233347e1856d4b178fc42e_63.png)

![](img/4364ac58e2233347e1856d4b178fc42e_64.png)

![](img/4364ac58e2233347e1856d4b178fc42e_65.png)

![](img/4364ac58e2233347e1856d4b178fc42e_66.png)

You know， our assumption was basically that it would just， you know， run something else。

 but the US doesn't have to do that。

![](img/4364ac58e2233347e1856d4b178fc42e_68.png)

And one example of what it could do instead is it could load pages on demand， it could say， okay。

 this page wasn't accessible， but rather than just assuming the program messed up。

 let's look at what the program you thought should be there。

 so we had one example that the OS might track where the program stack should be and not allocate it right away。

😡。

![](img/4364ac58e2233347e1856d4b178fc42e_70.png)

![](img/4364ac58e2233347e1856d4b178fc42e_71.png)

![](img/4364ac58e2233347e1856d4b178fc42e_72.png)

![](img/4364ac58e2233347e1856d4b178fc42e_73.png)

![](img/4364ac58e2233347e1856d4b178fc42e_74.png)

And instead， it can wait until the program tries to use it and detect。

 okay it tried to access something that wasn't allocated。

 let's figure out whether it was really never allocated in which case it's an error or it's just something that I the OS didn't allocate it right away and if I didn't I can fix that I can update the page table to allocate it and rerun the instruction that triggered the fault and the hardware can make this more possible by giving the OS a little help in figuring out this out and then rewriting that instruction。

😡。

![](img/4364ac58e2233347e1856d4b178fc42e_76.png)

![](img/4364ac58e2233347e1856d4b178fc42e_77.png)

![](img/4364ac58e2233347e1856d4b178fc42e_78.png)

![](img/4364ac58e2233347e1856d4b178fc42e_79.png)

![](img/4364ac58e2233347e1856d4b178fc42e_80.png)

![](img/4364ac58e2233347e1856d4b178fc42e_81.png)

![](img/4364ac58e2233347e1856d4b178fc42e_82.png)

So it can tell the OS， here's the address that the program is trying to access and make sure that when the OS returns from its exception handler。

 normally that it does the same instruction over again。



![](img/4364ac58e2233347e1856d4b178fc42e_84.png)

![](img/4364ac58e2233347e1856d4b178fc42e_85.png)

![](img/4364ac58e2233347e1856d4b178fc42e_86.png)

And an extension of this， which was actually the original sort of motivation for virtual memory and page tables。

 is that we can treat all of memory as a cash for disk that rather than allocating program space in memory。

 we allocate program space on a hard drive or。

![](img/4364ac58e2233347e1856d4b178fc42e_88.png)

![](img/4364ac58e2233347e1856d4b178fc42e_89.png)

![](img/4364ac58e2233347e1856d4b178fc42e_90.png)

Say that this part of the program's memory comes from a file， for example。😡。



![](img/4364ac58e2233347e1856d4b178fc42e_92.png)

And we can load data from that hard drive as the program needs it。

 and if we run out of space for all the data programs are' using， we can evict something。😡。



![](img/4364ac58e2233347e1856d4b178fc42e_94.png)

![](img/4364ac58e2233347e1856d4b178fc42e_95.png)

From what one of those programs are using to that space on disk and know that well。

 if we's needed it again， we'll load it back and this is the same kind of thing we can kind of think of our normal processor cache is doing。



![](img/4364ac58e2233347e1856d4b178fc42e_97.png)

![](img/4364ac58e2233347e1856d4b178fc42e_98.png)

![](img/4364ac58e2233347e1856d4b178fc42e_99.png)

When we think of interfacing the catch and main memory that there。



![](img/4364ac58e2233347e1856d4b178fc42e_101.png)

![](img/4364ac58e2233347e1856d4b178fc42e_102.png)

好。YouSing stuff from memory that's as it gets used and when they run out of space to store stuff from memory。

 they evicted back。 The difference here is that this is something that the OS would do without the hardware actually needing to do anything special to support it beyond implementing this translation and making sure that the OS you know。

 gets enough information when。

![](img/4364ac58e2233347e1856d4b178fc42e_104.png)

![](img/4364ac58e2233347e1856d4b178fc42e_105.png)

![](img/4364ac58e2233347e1856d4b178fc42e_106.png)

![](img/4364ac58e2233347e1856d4b178fc42e_107.png)

That translation fails when we find an invalid page table entry。



![](img/4364ac58e2233347e1856d4b178fc42e_109.png)

食。

![](img/4364ac58e2233347e1856d4b178fc42e_111.png)