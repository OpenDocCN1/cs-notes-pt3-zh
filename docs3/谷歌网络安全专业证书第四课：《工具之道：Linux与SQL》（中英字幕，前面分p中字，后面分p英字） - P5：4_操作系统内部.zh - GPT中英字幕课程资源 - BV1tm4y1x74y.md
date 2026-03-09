# 谷歌网络安全专业证书第四课：《工具之道：Linux与SQL》（中英字幕，前面分p中字，后面分p英字） - P5：4_操作系统内部.zh - GPT中英字幕课程资源 - BV1tm4y1x74y

![](img/ea17b84d7c72438bb6e64ddba86a6f1d_0.png)

Previously， you learned about what operating systems are。 Now， let's discuss how they work。

 In this video， you'll learn what happens with an operating system or O。

 when someone uses a computer for a task。 Think about when someone drives a car。

 They push the gas pedal and the car moves forward。

 They don't need to pay attention to all the mechanics to allow the car to move。

 Just like a car can't work without its engine。 A computer can't work without its operating system。

 The job of an O is to help other computer programs run efficiently。

 The O does this by taking care of all the messy details related to controlling the computer's hardware。

 so you don't have to。😊，First， let's see what happens when you turn on the computer When you press the power button。

 you're interacting with the hardware。 This boosts the computer and brings up the operating system。

 Booting the computer means that a special microchip called the Bios is activated On many computers built after 2007。

 the chip was replaced by the UEFI Both Bi and UEFI contained booting instructions that are responsible for loading a special program called the bootloader。

Then the bootloader is responsible for starting the operating system， and just like that。

 your computer is on。As a security analyst， understanding these processes can be helpful for you。

Vulnerabilities can occur in something like a booting process。 Often。

 the bio is not scanned by the antivirus software， so it can be vulnerable to malware infection。

Now that you learn how to boot the operating system。

 let's look at how you and all users communicate with the system to complete a task。

The process starts with you， the user， and to complete tasks， you use applications on your computer。

 an application is a program that performs a specific task。When you do this。

 the application sends your request to the operating system from there。

 the operating system interprets this request and directs it to the appropriate component of the computer's hardware。

In the previous video， we learned that the hardware consists of all the physical components of the computer。

The hardware will also send information back to the operating system。

 and this in turn is sent back to the application。Let's give a simple overview of how this works when you want to use the calculator on your computer。

You use your mouse to click on the calculator application on your computer When you type in the number you want to calculate。

 the application communicates with the operating system。

 your operating system then sends a calculation to a component of the hardware。

 the central processing unit or CPU Once the hardware does the work of determining the final number。

 it sends the answer back to your operating system。

 then it can be displayed in your calculator application。



![](img/ea17b84d7c72438bb6e64ddba86a6f1d_2.png)

Understanding this process is helpful when investigating security events。

 security analysts should be able to trace back through this process flow to analyze where security event could have occurred。

 just like a mechanic needs to understand the inner workings of a car more than an average driver。

 recognizing how operating systems work is important knowledge for a security analyst。

