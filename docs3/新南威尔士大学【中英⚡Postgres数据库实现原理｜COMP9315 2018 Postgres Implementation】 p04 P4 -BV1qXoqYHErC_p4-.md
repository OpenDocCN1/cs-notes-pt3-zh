# 新南威尔士大学【中英⚡Postgres数据库实现原理｜COMP9315 2018 Postgres Implementation】 p04 P4 -BV1qXoqYHErC_p4-

43，2，1。 Oh let's continue。

![](img/bc75b94c830c0ff14c4bc3a74a766963_1.png)

Okay， so。On an early slide we saw that Postgres had all these different kindss of objects， users。

 databases， views， functions， da da da。All right， how does it manage all of those things。

 how does it represent them， how does it present them to us as existing in the database， the catalog？

诶。Few things about so obviously you can represent Data， maybe not obviously。

 but there's a table in the catalog that says what databases there are， who owns them。

 what access controls there are。Similarly for schemas and table spaces so schemas are effectively name spaces and table spaces allow you to specify whereabouts on the file system that you want to locate tables obviously you can use that kind of thing for load balancing if you've got a system that's got multiple disks and you're done everything too。

Be hammering one disc you can say I want this table to be on this one to be on that disc that's what table spaces are for Obviously we need representations of tables。

 a list of tables stored in the catalog the attributes of each of those tables and the tus in the records are not stored in the catalog they're stored in the actual tables constraints and assertions are however stored in the catalog similar views stored procedures。

 triggers and rules。A lot of these objects have got names。

 in fact I'd say most of them have names and。Pretty much most of them also have a unique object identify。

 which I talked about the other day。If you go and look at a database。



![](img/bc75b94c830c0ff14c4bc3a74a766963_3.png)

I don't know whether this will actually work， but let's pick。😔。



![](img/bc75b94c830c0ff14c4bc3a74a766963_5.png)

系。Really defined datab。

![](img/bc75b94c830c0ff14c4bc3a74a766963_7.png)

So there's a table that's got two attributes， two visible attributes。Relieve。

And this probably won't work。And you can actually get to look at the OI， you can。

 because I haven't defined Oids for these things， but。



![](img/bc75b94c830c0ff14c4bc3a74a766963_9.png)

Certain other tables will have a unique object identified defined for each tubble and you can reference to tu that way。

 and if you've allowed that for that table， then that invisible column is actually there and you can use it。

But certainly， he's in。Let's say， page G。So anyway， so all of the。Catalog tables。

Are available through PD， underscore something or other so there's a table that represents the database is if Ipell database correctly。



![](img/bc75b94c830c0ff14c4bc3a74a766963_11.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_12.png)

传问你。And。Here it doesn't mention。no ID， but there is no ID。え。



![](img/bc75b94c830c0ff14c4bc3a74a766963_14.png)

Associated with each of them， okay so you can see that while it doesn't appear here。

 it is actually in the table， each tu in the table in this table as an OIT。



![](img/bc75b94c830c0ff14c4bc3a74a766963_16.png)

And you can see there's a couple of places where OIDs are reference there。

 so basically the catalog tables refer you any fine key references in the catalog tables are typically to OID values of tus in another catalog table。



![](img/bc75b94c830c0ff14c4bc3a74a766963_18.png)

What else we've got here database name database DA， who is the person who manages this。

 you can see that's an OID and if we look down here that references。



![](img/bc75b94c830c0ff14c4bc3a74a766963_20.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_21.png)

can tell you what it references that so annoying or only chunk in the indexes probably let me see。



![](img/bc75b94c830c0ff14c4bc3a74a766963_23.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_24.png)

I don't think there's a user's table， there is cool。



![](img/bc75b94c830c0ff14c4bc3a74a766963_26.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_27.png)

What。嗯了。哇。Why is Nilo Is？Could be because they're not stored there， there's also a roles table。诶。

I don't want to fiddle around trying to find it， but let's quick。😔。



![](img/bc75b94c830c0ff14c4bc3a74a766963_29.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_30.png)

嗯。あの。Possibly there， oh， look， it's got no idea and it actually appears explicitly wow， what are you？

呃嗯。

![](img/bc75b94c830c0ff14c4bc3a74a766963_32.png)

So。At some point when we run an Escol query， we say select star from students。So we good的我也 care啊。

Is the word students a real table name in this particular schema。

 where's the file that contain the data for the students and so on and so on so at some point the query process that has to reference these catalog tables to work out whether all the names that you use in the query are actually relevant and other things you can say select X from students。

 the query process it can work out， yes there's a table called students but there's no attribute X existing in that table。

 so obviously it's got to store information about the attributes and what tables they're associated with as well。



![](img/bc75b94c830c0ff14c4bc3a74a766963_34.png)

so for relations， we need to know all of this kind of information and similarly for all the other kinds of DBMS objects like who triggers。

And so on， functions。So that information installed in system catalog tables now you may have noticed that I was doing P underscore that sounds a little bit Postgre specific and that's true。

The notion of standardized catalogs didn't come along until about 2000。

 clearly all of these databases existed long before 2000 and they all need a catalog so they all came up with their own catalog structures。

 but they also support the catalog standard which is information schema and if you want to find out about it。



![](img/bc75b94c830c0ff14c4bc3a74a766963_36.png)

You can look can here somewhere， somewhere。

![](img/bc75b94c830c0ff14c4bc3a74a766963_38.png)

![](img/bc75b94c830c0ff14c4bc3a74a766963_39.png)

没意。

![](img/bc75b94c830c0ff14c4bc3a74a766963_41.png)

This is talking about system catalogs and this is actually referring to the Postgre specific catalogs。



![](img/bc75b94c830c0ff14c4bc3a74a766963_43.png)

Somewhere in this。诶。

![](img/bc75b94c830c0ff14c4bc3a74a766963_45.png)

Somewhere in here there's also the information schema。😔。



![](img/bc75b94c830c0ff14c4bc3a74a766963_47.png)

so I can't so that gives you all the standardized names for things so these are really just views onto the Postgres scheme but。



![](img/bc75b94c830c0ff14c4bc3a74a766963_49.png)

They recognize the standard of。Trying to look out some information and you've got a。



![](img/bc75b94c830c0ff14c4bc3a74a766963_51.png)

I think from another database you can probably port it to here。All right， so。

When does the catalog itself get changed， obviously tables get changed by update and delete。

 the catalog gets changed by those kind of operations so when you create a new kind of object I can create a table or you can create a type。

When you're creating a table， obviously in define attributes。

 they also get included in the catalogue， you can drop an object。You can alter an object and you can。

Specify what access controls。系。An object has。So。When I say drop table groups at the SQl level。

 what actually happens is that it makes a change to the。Tables catalog table if such a thing exist。

 in fact， in Postgres that table is called PG underscore class。



![](img/bc75b94c830c0ff14c4bc3a74a766963_53.png)

And if you want to find out about you what tables are available， then all。



![](img/bc75b94c830c0ff14c4bc3a74a766963_55.png)