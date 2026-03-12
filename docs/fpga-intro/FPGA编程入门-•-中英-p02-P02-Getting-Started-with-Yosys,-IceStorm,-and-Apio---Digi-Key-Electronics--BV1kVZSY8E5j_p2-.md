# FPGA编程入门-•-中英-p02-P02-Getting-Started-with-Yosys,-IceStorm,-and-Apio---Digi-Key-Electronics--BV1kVZSY8E5j_p2-

Previously， we talked about what an F PGA is and what it's good for。

 Before we get our hands dirty with vera log， we need to install the tool chain。 Lucky for us。

 there are free and open source tools that work with the FPGA on our dev board。 Let's get started。😊。

If you head to YosishQ。net， you can learn about these tools The Yosis tool synthesizes Verlog Rtl code note that it specifically supports the 2005 version of Verlo so that's what we're going to use If you check the FAQ you can see the different FPG targets that it supports we'll be using a lattice Ice 40 click on next PNR and you'll be taken to a Github page here you can see a visualization of how next PNR works It's quite literally making connections between cells in the FPG The output of the place and route step。

 then goes to tools in the project I storm suite Sc down and you can read about the individual tools we'll be using I pack to convert the ASI output of the PNR tool to a binary that's readable by the FPG Finally Iceprog uploads the binary file to the FPGA。



![](img/2ab5a16471ce7b635bf723673e1f2099_1.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_2.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_3.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_4.png)

To make life easier， we're going to use opio。 This is a tool that manages all of the tools we just looked at。

 It provides methods for installing them on all of the major operating systems through Python。

 It also comes with a number of examples that can be good starting points。 However。

 note that where the tools can be made to work with just the chips on custom boards。

 Opio is really intended to support various development boards that you can buy。

 If you do make a custom development board I'm sure you can do a pull request to have it supported in opio I also want to point out this I studio project。

 Ice Studio is a blockbased coding environment for Verlog。

 You can see it in action in some of these gifts。 It runs opio and the other tools we saw earlier in the background so it only supports lattice I 40 chips at the moment For now I want to stick with veralog and the command line tools so you can get a sense of how raw HDL works。

 If there's interest。😊，Come back to Iudio later in the series。 For example。

 here is a Ri5 softcore CPU being used in Iududio。 This graphical environment might be an easier way for some to visualize and organize larger projects than say pure hardware description language Opio is still a relatively new projects so expect some changes as it's updated read the Docs page for opio is the best place I have found for information on installing and using it you'll want to follow the installation guide for your particular operating system。

 but I'll show you the process on Windows Note that you need to have Python 3。

5 or greater installed on your computer in the user guide section you can see how to use opio to build。

 simulate and upload your design to the board Note that each of these commands actually calls one or more tools in the background like Yosis and next PNR。



![](img/2ab5a16471ce7b635bf723673e1f2099_6.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_7.png)

To start， make sure you're using a version of Python that's 3。5 or greater。

 go through the process of installing Python if it's not already on your system from there we're going to use PIP to install ApppiO。

However， note that I'm specifically installing version 06。7 of Aio， at least at this time。

 the newest version had issues with installing some of the tools， so I'm going be sticking with 0。6。

7 as that's known to work on my system In the future current versions may work and you may not run into some bugs。

 but this was noted on the issues page in the Github repository for Aio that they are currently updating a lot of the things and backend for Aio so I recommend sticking with 0。

6。7 for now Opio should now work as a command line tool in your console if you have issues where it's not recognized as being part of a path you might have to add wherever Opio is located to your path I ran into this on some flavors of Linux but for Windows it seems to work out of the box after installing it using Pip from there we need to install the tool suite This is things like Yois and I storm It doesn't come。

Packd with Opio。 so we need to use Opio to install them。

From there we tell Aio to install the various drivers to support talking to our board Take a look at your board if it has an FTDI chip。

 you will need to install the specific drivers to work with that FTDI chip if you're using an It like I am it does contain an FTDI chip so we need to do this extra step if you're on Windows you'll want to open a command prompt as administrator。



![](img/2ab5a16471ce7b635bf723673e1f2099_9.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_10.png)

To install the FTDI drivers we'll need to call opio drivers FTD enable when we run that at least in Windows you'll get Zig to pop up and we have to go through this process manually if you're on another operating system you shouldn't need to do this step in Zig click options and list all devices plug in your FPGA devboard click the dropdown list and you should see your devboard listed it might say something like lattice if you've used a board like this before it might also be an FTDI chip or something like that you can also view the list before and after plugging it in to find the new addition to the list so I'm gonna click my lattice devboard here and Opio wants the LibB USBK driver to be installed so we'll select that and click replace driver Give it a moment to install the specific driver for communicating with the FTDI chip。

When it's done， click close， close out of Zig and you can close the administrator command prompt Now you should be able to say opio system Lsfttdi to list the various FTD connected parts you should see a lattice FtUSB interface cable that means it's connected to our devboard there is an issue I have found specifically with Windows if you have another FTdi chip connected in addition to your devboard you will probably run into this LibusB open failed in this example I plugged in my analog discovery too which uses something similar to communicate with USB and having both the Itick and the analog discovery2 plugged in caused this error so if you see this that probably means you need to disconnect all of your other FTD devices except for your particular devboard So when I disconnect my analog discovery too I run that command again and sure enough it pops up with my devboard being connected。

First thing we want to do is create a folder that houses all of our projects that we're going to be creating for me I'm going to go into my documents folder in my home directory and create a directory called Opio we'll go into Opio and store our various projects here one of the cool things about Opio is that it comes with a bunch of examples we can call Opio examples L to list out the examples that are available feel free to scroll through these to get an idea of what we can instantiate look at and modify。

I'm going to be working with the I stick examples specifically let's start with LEDs as that one's pretty simple。

 we can just call the name of that example with Opio examples D and then It backslash examples。

As you can see， that creates an ice stick directory。If we go into there。

 you can see that it creates an LEDs directory inside of Itick， if we go in there。

 we can see all of the files that were created as part of this example。



![](img/2ab5a16471ce7b635bf723673e1f2099_12.png)

Let's go into the file browser and take a look at what was actually made。

 so we created this opio directory， we created It and LEDs inside of that。Our main design。

 it's not actually a program， is in the LEDs。v file。



![](img/2ab5a16471ce7b635bf723673e1f2099_14.png)

So let's open that and take a look。Feel free to look through this， this is a basic Ho world example。

 all it does is tie all of the LEDs。

![](img/2ab5a16471ce7b635bf723673e1f2099_16.png)

Too high and it just turns them on the other important file is this dot PCF file。

 which is the physical constraints file or maybe pinned constraint file as it tells us how things are connected on the actual board or chip itself。

 this isn't really ver log codeke， comments are given by these pound signs or hashtags。



![](img/2ab5a16471ce7b635bf723673e1f2099_18.png)

And then what it does is it gives a label in this case。

 D1 and assigns it to the physical pin number on the chip so on our FPGA pin 99。

 that's physical pin 99 is mapped to D1 and that's the first LED on the board and that's how we get these names when we call them in our LEDs Barlog file if we head to the lattice semi。

com I 40 page you can zoom down and you're looking for。



![](img/2ab5a16471ce7b635bf723673e1f2099_20.png)

I believe it's documentation。We're using the Ice 40 Hx 1K。

 that is the FPGA chip that's on our ice stick。So click that to download。This spreadsheet。

 and you'll want to open it in something like Excel。The Itick has the 144 pin TQFP package。

 so these are the physical part numbers。Labeled one through 144。

And I mentioned that 99 is connected to that first LED。So here's P 99。

You can see that it is indeed a PIO connected to one of the IO banks。

And the next thing you want to do is find the Itick user manual， and if you scroll through this。

 you can usually find something like a schematic。Here are the Ls。So D1。

 that's what the label was that's connected to a net called LED zero。

And the actual FPGA schematic symbol is divided up into a number of these blocks。

 but you can see here pin 99， physical P 99 is connected to LED0， and you can also find this chart。

 user iOs and LEDs， so D1 is connected to 99 and so on。And it gives you the color of the LED。

 so hopefully those two documents can help you figure out how the pins are connected to various things on the dev board and where you can find the physical pin number when you're creating that do PCf file。



![](img/2ab5a16471ce7b635bf723673e1f2099_22.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_23.png)

The other thing worth looking at is the test benchch so the first test benchch is written in Verlo and you can see it here we're actually not going to be using test benchnes or writing our own for at least a few episodes because we want to get the basics of Verlog down before we start writing these however it's always a good idea to create a test benchch to simulate your design and see if it works before sending it off to your FPJ and especially before deployment。



![](img/2ab5a16471ce7b635bf723673e1f2099_25.png)

The LEDs underscore TB。v is the verlog test benchch that actually runs the test benchch The program that reads that in and runs simulation is GtK wave this is a save state so that when we load up GtK wave it reads this in and it runs the simulation right away basically The other thing you'll notice is this APO。

 Ii initialization file If we look in here it just says hey the board that's supported for this project is the Itick we can actually create this file by using opio what I'm going to do here is delete it。



![](img/2ab5a16471ce7b635bf723673e1f2099_27.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_28.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_29.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_30.png)

And then go back to my console and we can say opio boards dash dash list。

 and you can see the list of supported boards， at least for this particular version。

 and we want the I stick。 So I'm going to do opio in。



![](img/2ab5a16471ce7b635bf723673e1f2099_32.png)

Dash dash board and say ice stick。

![](img/2ab5a16471ce7b635bf723673e1f2099_34.png)

All that does is recreate that opio。ini file。 so if you're creating a project from scratch。

 you'll probably want to do this so that it tells opio that you're working with the It。

 you can tell the syntax is a little different， but either should work now that we have all of the components for our project together。



![](img/2ab5a16471ce7b635bf723673e1f2099_36.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_37.png)

The first thing I recommend doing is calling Opio Verify， this performs a verification step。



![](img/2ab5a16471ce7b635bf723673e1f2099_39.png)

Using this IVa log tool and this just kind of says， hey the syntax looks good。

 we think you can synthesize this and you're ready to go from there。

 you'll probably want to simulate this is always a good idea before actually sending out the project or design to the actual board。



![](img/2ab5a16471ce7b635bf723673e1f2099_41.png)

In this case， the simulation step opens up GTK wave。

 it loads in that test benchch ver log code and it also loads in that dot GtKw save state so that GTK wave opens up with certain signals here and toggles them in a certain pattern but for now we're just looking at the output LEDs and they should just be always on when you're happy with the way this looks。

 close out of GTK wave and we want to say opO build。



![](img/2ab5a16471ce7b635bf723673e1f2099_43.png)

This calls Yososis to perform the synthesis step for our Vlo code。

 and then it calls next PNR to do placing and routing this is where that。Pins。

Configuration file or the physical constraints file is read in and it figures out how to route the individual connections and set the cells in the chip itself。

 which is the Ice 40 Hx1K because the ver log code was agnostic to a particular chip but placing and routing then takes that agnostic design and creates some output that is unique to this particular chip Ice pack then takes that ASI file and packages it up into a binary file that can be read by the chip itself。

 assuming we get a success here we can call opio upload。

 make sure your board is plugged in and on this will call Iprog that will take the binary file and send it over to the flash memory of your board assuming the upload process worked all of the LEDs on the board should be on。



![](img/2ab5a16471ce7b635bf723673e1f2099_45.png)

I highly recommend going back to the lattice page where we downloaded the pinout document。

Clicking on data sheet and finding the data sheet for the Ice 40Hx part。

 so we're going to download that。And open it up， scroll through here and I recommend using this as a reference and you're going to find this diagram which kind of shows the internal working of the actual FPGA these PLB or programmable logic blocks contain a number of cells and in fact on the next page you can see that each block contains eight logic cells and these are the cells we looked at in the first episode and we're going be looking at the individual parts of a cell in future episodes and breaking it down as we learn about things like lookup tables and combinatorial logic as well as the de fliplip flops and how these can be combined to create your digital logic but for this overall view note that these blocks can be connected to one another we have access to some RA there's also IObank and these IObank have a little bit of their own logic you can think of many of the pins as being similar to what you would find on a microcontroller and you can。

fire them to be an input pin an output pin。 you can sometimes configure pull ups or pull down resistors that are inside of these IO banks and connected to each pin or groupings of pins。

 this particular part also has some dedicated spy logic There's also a phased lock loop that will provide us with clock signals and we're gonna to explore those in a future episode。

 you also have this nonvolatile configuration memory note and this is very important this particular memory on this part is a one time right only So if you are satisfied with your design and you don't want to change it any longer and you're ready for deployment。

 you can burn it to this little amount of memory here。

 but once you do that's it that part is burned and ready to go Otherwise there's configuration logic that will read from an externally connected flash chip from spy usually and that's what gets read in and。

fiigures the chip and that sets the cells to behave in certain ways。

 makes connection between cells and among the blocks to create your design on the actual component itself on the FPGA you can read in that configurationgu any number of times but that's why you'll often see external spy flash chips accompanying FPGA components on boards and indeed our Itick has an external flash chip on it so that when we send our program that binary file using opio upload that gets loaded into the spy flash chip every time you restart or disconnect power from this FPGA it loses all of the memory and all of the configuration so each time you boot it up it has to read it in from that flash chip and then reconfigure everything which is why it will take a few moments before the FPGA starts doing anything when you give it power your challenge。

For this lesson is to modify the LEDs。v example so that one of the LEDs is off you can see here that I've turned off the green LED your solution might be a little different。

 but I'll make sure that a link to my solution is in the description if you'd like to compare answers。

At this point， we're ready to start creating our own FPGA projects。 In the next episode。

 I'll show you how to make combinations of logic gates in Verlog， happy hacking。😊，え。え。



![](img/2ab5a16471ce7b635bf723673e1f2099_47.png)

![](img/2ab5a16471ce7b635bf723673e1f2099_48.png)