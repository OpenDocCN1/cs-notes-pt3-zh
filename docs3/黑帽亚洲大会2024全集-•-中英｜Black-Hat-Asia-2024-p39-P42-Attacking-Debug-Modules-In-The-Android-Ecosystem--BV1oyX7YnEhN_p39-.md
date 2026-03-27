# 黑帽亚洲大会2024全集-•-中英｜Black-Hat-Asia-2024-p39-P42-Attacking-Debug-Modules-In-The-Android-Ecosystem--BV1oyX7YnEhN_p39-

Thank you， Blackhead I， for providing this opportunity。

This is my first time participating in Black hat， and I feel incredibly incredibly honored。 Today。

 I will be sharing a presentation titled Attacking Debug Models in the Android ecosystem。

 My name is Li Wei， and I will be the speaker for this session。First， let me introduce myself。

 Im currently working at a self driving company in China called Mogo Autoto。

 amm responsible for the implementation of the car to road cloud integrated solution in China。

I oversee the management and technical work of the entire security team。 Currently。

 I'm leading the team to protect the security of the car to roll cloud integrated infrastructure and enhance the company's network and data security。

Previously， I gained five years of work experience at Baidu。

 primarily focusing on mobile and I O T security。 I have submitted a significant number of security vulnerabilities to Google Android Media tech at Uniisoc。

500 CV vulnerabilities has been credit to me。 and I'm also the top one buck hunter in the Uniisoc product security acknowledgecment。

😊，In 2000， in 2022， I was awarded the title of top buck hunter by Google。 I have。

 I have participated as a speaker in multiple industry security conferences。

 sharing my knowledge and insights。I will present the topic in four sections， background frame model。

 case study and summary。In the background section， I will begin by introducing the fragmentation of the Android system。

 Next， I will discuss the native debugging architecture of Android。 Furthermore。

 I will delve into the property debugging architectures developed by two major vendors。

 I will provide an overview of their unique debugging frameworks， tools and features。

In the the model section。I will focus focus on conducting an attack surface analysis of debugging models。

In the case study section， I will provide practical examples of vulnerability discovery that， again。

 with the attack surface analysis conducted earlier in these cases。

 case study will illustrate real world incident where vulnerababilityities in debugging models were were identified and exploit by examining these cases。

 we can gain insight into the potential。Impact and consequences of such vulnerabilities。

In the summary section， I will provide an overview of the key points discussed throughout the presentation and offer recommendations based on insight gained。

This section aims to summarize the importance of securing debug models in the Android ecosystem and providing provide guidelines for developers security。

And organizations。The Android ecosystem is composed of several components as depict in the diagram。

Studying from the bottom， we have the system on chip layer。

 which includes major associate chip manufacturers such as quantum Mediatech Uniisoc。

 providing the underlying hardware and board sport package capabilities。

The second layer is the well known Android open source。Project。

 which not only provides capability at the S O C level。

 but also offers open source code for upstream customization and develop development。

The third layer consists of various products， including smartphones， tablets。

 in vertical and A L O T devices。The four， the fourth layer represents familiar OEM E M brands such as Samsung。

 Xiaomi， Huawei and Google's self developed pixel devices。

This layered structure contributes to the complexity of the supply chain and introduce fragmentation with the within the Android ecosystem。

Fragmentation is primarily manifested at three levels。Product fragmentation。

 vendors customize their own launches and operating systems such as Mi U I， magicic U and Harony O S。

 along with customer development at the system level A P， including debug models。

 notads and device interconectivity features。System fragmentation vendors perform customized development as the framework layer of USP to adapt to their hardware。

Characteristics。They also implement low level implementations as the hardware abstraction layer to bridge the framework and driver layers。

BSP fragment。Vs customized the， the hardware related driver models。

 which are reflected in video processing Wifi， Bluetooth。

 G S S 4G and 5G audio processing display acceleration and security related components。

Based on the analysis above， it is the fragmentation of the Android ecosystem that leads to a myriad of security issues affecting various aspects of the entire industry。

To address the security issues introduced by fragmentation。

 Google has implemented the following four strategies， In the vendor petition。

 Google introduced the vendor petition in the Android O。

 which is especially designed to host vendor specific B SP code。

 This allows for better management and isolation of vendor specific components。

 hardware abstraction layer。 Google established the hardware abstraction layer as a bridge between the user level and driver level components。

Hardware abstraction layer provides a standardized interface and abstraction layer。

 enabling high higher level applications to interact with underlying hardware operations without the direct dependence on the specific drivers。

Security bulletin。 Google published monthly Android security bulletin that include critical and high severity vulnerabilities reported by the wind panels。

This ensures timely disclosure and awareness of the security vulnerabilities presented present in various vendor specific implementations。

Android Chipsset security Re program。 In 2019， Google initiated the Android Chipsset security Re program。

Aimed at at identifying and reward， rewarding security vulnerabilities， specially targeting。S O Cs。

 unfortunately， as， as as of May 2023， Google discontinued the A SRP。

These strategies reflect Google's efforts to enhance security in the Android ecosystem and mitigate the risk associated the fragmentation。

Android's native debugging architecture consists various of components as deficit in the given standard Android architecture diagram from top to bottom system。

 A P's Java API framework， native C and C glass library。

 Android runtime hardware abstraction layer and Linux kernel。

The standard debugging architecture in the Android serve three main purpose。 mock capture。

 This includes capturing E P P log， kernel log and subsystem log， for example。

 modern DS SP wfi Bluetooth。These logs are captured to analyze and debug the behavior of of applications。

 system components and specific subsystems。Function verification。

 This involves validating the functionality negative of of models such as the camera， display。

 hardware and GPU rendering。It ensures that these components are working as expected。Factory testing。

 this refers to the testing and validation of specific function negatives during the manufacturing and verification phase。

 It often involves vendor specific tests to verify the proper functioning of hardware and software components。

When it comes to the Android debug architecture， the first thing that comes to mind is the developer options。

 The developer option provide following basic flash function negatives。

 which can also be found in the Android standard development document general option。

 This includes options such as memory management error reporting and OEM M unlocking debugging related options。

 This includes USB debugging and Android debug bridge debugging。

 which allows for debugging and communication between a computer and an Android device。

 network related options。 This includes options related to Wifi and Bluetooth settings。

Input related option。 This includes options for touch feedback and input settings。

Session related options。 this include the option to display layout boundaries。

 which can be useful for debugging and optimizing the user interface。

Here is the translation of the provided explanation about the debugging process。

 using Android debug bridge。As shown in the diagram from left to right， first。

 the user enable enables USB debugging。 The action is performed in the settings AP。

 especially in the settings provider， where the flag settings point global point it B enable is set2。

At the framework layer， there is a system server called Android point Debug point I A B manager。

 this service。Continuously monitors the flag settings point Global point A B enable。

 When it detects that the flag is set true。 It star the native diamond A B D using the C， T。

 L point start method。At this point， the user can use debugging tools to connect to E B D for a debugging purpose。

Here is the translation of the provided explanation about G capturing in Android。

 Both Android A T layers， logs and native layer logs are involved through Java native interface and accessed where the Android system library called livelog。

Lvelog maintains continuously communication with the native diamond O D through unique domain soets。

 allowing the output of application level logs to be sent to log D。

When using log cat to capture logs， it also communicates with log D through unique domains to read the relevant log outputs。

Through the as the Linux rules of the log D， we can see that log D itself has permission to read kernel logs and system files。

Based on the analysis of the two aspects of Android debug architecture。

 we can draw the following conclusions。The debu， the debug model involvesvoke complex IP PC communication。

 including vendor calls， Uni domain content providers， hardware。Inter how interface。Definition。

 language and more。The data flow within the debu debug models is intricate。

 Use level data is progressively passed to hire， privileged native diamonds and drivers。

After introducing the debug architecture of Android。

 let's now shift our focus to the vendor debugging architecture。Firstly， let's consider the question。

Why do vendors need to do the customize the debugging。

I have summarized the forging three points not capturing it is necessary to often debu logs from subsystem and have standardized the debug capabilities。

 which include capturing debug information from all models such as mediat AEE and Uniisofs vialog。

Fun function verification involves testing multiple hardware related function negatives。

 such as telephony， connectivity， hardware and location。

Factory testing tools are used to perform basic checks on hardware components during the factory stage。

 such as the screen and and others。Let's take a look at the log capturing capabilities of vendor U in the diagram from the left to right at the user level。

 there is a system AP called engineering mode exposed。 This appP can be accessed through two method。

 a security code and evocation from a third party AP。Within this engineering mode AP。

 multiple activities are introduced。 For example， log management is used to control logs。

 Android log control is used to control Android logs。

 A T command control is used to test the effectiveness of80 commands and modern is used to configure configure mode related log switches。

These various activity or applications communicate through IP PC to pass data flow to value level models such as native diamond and hardware extractionion layer service。

Most of these low level。Modelles are implemented in C plus plus and have system and route level permissions。

The diagram on the on the right showcase the control status of various of subsystems by the debugging app。

 P。The second case is about We Ams debugging architecture。

 It also features a generic debugger U I as an entry point with various native diamonds and the background。

 Communication between them is established through Uni stone socket。

 data flows gradually from the debugger U I to the native diamonds undergoes the processing and is then transmitted to the driver layer。

Ms move on to the third case， which involves vendor use feature testing and factory testing tools。

 The AP in question is a system AP called S PR D auto S L T。

 which is introduced by default in its B SP model。 this model can be invoked by third party A P with within this system A P。

 various testing model are include such as Wifi test， Kelly test， R TC test， back test， camera test。

 system test， GPS test， Bluetooth test， Sim card test， O T T test and more。

Behind each of these testing function negatives is an AP PCC。

Mechanism that directly reaches the low level components。For example。

 the framework is invoked through banner core。 nativeative diamonds are accessed where unique and system files are read and are are read read using field rate operations。

The diagram from the right demonstrates the presentation of the final information results。

Let's take a look at a real life case。 One plus phones are discovered to have a back door vulnerability that could allow direct routing of the device。

The issue stemmed from the inclusion of a customized engineering mode A P by quantum in the phones components。

 Aters could exploit the agency in engineering mode system A P to gain rude access to the device。

 This highlights the following two issues。The first point is that the B SP often includes factory testing tools which can introduce high risk security vulnerabilities。

These tools， if not properly secured or removed before the device reaches the end user。

 can be exploitd by attackers to gain unauthorized access or control over the device。

The second point is that OE Ms or OD Ms often lack security awareness and fail to remove debugging tools from their fer package packages。

 These these oversights can leave devices vulnerable to exploration as the debugging tools may provide unauthorized access or control over the device function negatives。

This diagram illustrates the attack surfaces， surface of the analysis， the debug models。

 which can be div into four parts from the。Persspecive of system A， P。

 they are vulnerable to attacks from the network and local attacks from third party A Ps in terms of network attacks。

 system A Ps may often concern point parts and。And and accept abnormal parameters to perform high privileged operations。

In terms， in terms of local attacks， system A， P accept parameters through exported interfaces such as activity。

 service， broadcasts and provider。Since system A P have have high privileged。

 if they are compromised， attackers can gain system level access and carry out further privileged escalation attacks。

Moving on to the framework layer， parameters from the user space are received through AI D L。

 If there are efficient permission checks in the debugging components in this layer。

 it can lead to local privilege escalation。For native diamonds。

 they often receive data from the application layer through unique domain soet。

 Iroper handling of the data can make them vulnerable to attacks。

Hardware abstraction layer service receive parameters through H I D L and， and drive。

And driver and drivers receive parameters from every control。

 If these parameters are not properly processed， the models can also become targets targets of attack。

Attacking debu debug attacking debug apps。The attack path involved involved invoking high privileged components of the A P through a。

 through a third party A P。 The targets of the attacks are ex exported components of system A P。

 which can lead to local privileged escalation for information leak leakage。Additionally。

 system Aps may listen on socket ports， which can result in remote command execution。

The followingging diagram illustrates two types of vulnerabilities found in real life cases。

 I will provide detailed explanation of these vulnerabilities in the subsequent case study section。

Attacking debu debug diamonds， the attack entry point is the uniqueix do soet。

Possible security issue that can be triggered include include memory corruption， information leaks。

 command injection and so on。Attacking debuk hardware abstraction layer services。

The attack entry points are the unique to circuitet or H I D L possible security issues that can be triggered include memory corruption。

 information， leakage and command injection。Att attacking debu drivers。

 The attack entry point is through the through file operations。

 possible issues that can be triggered include memory related programs such as memory corruption and information leaks。

Through vulnerability research on debug models， we conducted investigations on three popular vendors and discovered hundreds of security vulnerabilities earning 49 C E credits。

Let's take a look at C E 2，2，0，2，2，2，0，0，9，8， an information disclosure vulnerability in the debug model of a certain vendor。

The affected debug model is called A E E A E， D， which is abu debugging native diamond。

The model is post a unique toet named Com point M T K point A E point8 D64。

The model accepts parameters from UD S。 Among the parameters。

 there is one for transmitting any process I D， which the A E E module pur the command passed through the UD S。

 It extracts the P I D and dumps the corresponding process memory information。

 resulting in information disclosure。The diagram on the right shows the complete proof POC。

 indicating that the transmitted P ID can be arbitrary。

 This allows a molecularous process to gain unauthorized access to the memory information of other processes。

Ultimately， leading to information disclosure。Another issue related to information disclosure is the corresponding debug A。

 P。 The AP logs various unique identifiers of the devices such as M， E， I， M， I I。

 calling address and so on。Let's take a look look at C E 22， O22，4，8，3，8，2。

 a memory corruption issue。The affected a process is a debu service called vendorpoint S P D point hardware point log at 1。

0 service。 The entry point of this process is the HDL common soet。

 which is a unique soet in the first image on the left。 There is a buffero vulnerability。

 It can be that the S represents the stack base with a default size of 24096 bys。

The data passed into the function is received ex externally through UD S and can have a lens。

 This vulnerability occurs when the length of the input exceeds。

4096 bys resulting in the buffer overflow。The image on the right shows a P C。

 which passing data with a length of 10000 bys cause a crash in the affected debu haul service。😔。

Let's take a look at another memory corruption issues at the driver layer。

 The problem is identified as C E 2022，3，9，1，1，1，1，8。 and the affected debugging driver is an SPD C。

 The attack entry point is is through fail operation。

 The issue here is an auto bound right vulnerability。 when writing an。Exively long byte sequence。

 it triggers a panic in the kernel， and the PC is shown in the image on the right。

This case is a local privilege escalation vulnerability identified as C E 2022，4，7，3，3，9。

 The affected process is a root privileged。 the debu diamond called CD service。

 The attack entry point is the unique named C D S K T by default CD service is not enable it only starts when the property flag C Y S point C D service enable is is set to enable CD service accepts complex parameters through the Uni S K T and eventually passes the parameter to be open for command execution。

This ultimately needs to command injection， allowing for local local privilege escalation and arbitrary command execution with root privileges。

The last case， let's take a look at a。Complete vendorability exploration process。

This vulnerability is identified as C V E 2022。2，7，2，5，0。It is a recurring issue。

 duplicated issue that was initially discovered by the security company。Sware。

 the problem occurs in a factory testing tool called S PI T auto S L T。 This E P。

 P accepts various debugging components such as camera debugging， phone debugging， FM debugging。

 Bluetooth debugging and more。The A P P listens on point7878 and accepts commands。

 The command list include the ability to execute shell commands。 However。

 the supported commands may vary depending on the device by connecting to point7878 and sending arbitrary share commands。

 We can remotely often system level privileges。 The S Linux contacts of the A P is S I D auto S L T A P。

Let further analysis CV E 2022，4，7，3，3，9， this vulnerability allows arbitrary command execution with route privilege。

 but it has some limitations。 Firstly， enable the C MD service flag require the system level permissions to set property。

Ordinarily ordinary shell or AP or third party AP cannot invoke CD service。 Secondly。

 the CD service listens on a unique domainet named CD S， K T。

 and connections are subjected to I C Linux restrictions。

 not every third party AP can connect to CD S K T and send command。

We examined the S Linux policy for CD service and found that C D S。

 K T can be accessed by the S Linux context of S I D auto S L T A， P。Therefore。

 the attack pass is is clear as shown in the in the image on the right。

The attacker initiates a remote attack to execute commands on SRD auto S， L T。

 gaining system level privileges and acquiring the context of SD auto S， L T A， P。

Then with system level privileges， the attacker execute the set property command to launch the sameD service process。

Finally， due to the S C Linux security context of SP I D auto S L T A， P。

 the attackers can directly send commands to C M D S。

 K T and execute arbitrary commands with route privileges。The end result is remote。

Acquisition of rude access of the device。 It is worth nothing that that this rude access is。

 is within the S Linux security context of CD service， but the impact is significant。



![](img/b2f824f963e5b7910dd51e83b2f8fc5a_1.png)

Finally， let's， let's summarize the key points of the discussion。 Firstly。

 the model module cover multiple layers of the system from the AP level to the driver level。

 resulting in multiple attack services， primarily focused on。Inter process communication。Secondly。

 some debu function negative require ex executing high privileged commands across processes。

 improper handling of these commands can lead to local privilege escalation。 Lastly。

 factory testing tools often invoke Wiifi Bluetooth and telephone function negative。

 Ier handling of these tools can result in information leakage， such as exposing wfi address。

 Bluetooth address， M E I numbers and other sensitive sensitive information。

The security recommendations can be summarized in the following three aspects for vendors。

 Some debug models should should not release to downstreams such as factory testing for OEMEM and ODMs B SP models should be selectively choosing based on specific needs and not accepted in in their entirety for users regular perform device security upgrades。

That concludes my presentation。 Thank you for listening。 Thank you。

