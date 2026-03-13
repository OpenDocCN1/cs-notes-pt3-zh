# 中英-•-树莓派Pico初学者入门｜微控制器｜编程｜电子学｜MicroPython-p18-P18-Sourcing-Power-from-the-Pico---Chapter-2.10--BV1eKXLYzEP4_p18-

Allright， our final video for chapter2 and it's an important one because if you get this wrong。

 you can damage your Pico very easily。 We aren't going be running any code or wearingiring anything up such as sit back relax and let's have a talk about power We just talked about powering your Pico which is the easy one but now we're going to talk about powering the things connected to your Pico how to source power from your Pco The two most important things when it comes to powering your devices is voltage and current remembering that voltage is like electrical water pressure and current is like electrical flow rate First let's talk about the three main places on the Pco that you can source power from and then go over some scenarios of powering some different components the simplest of them all is the 3V3 outpin which is the one that we connected to the power rails earlier in the chapter and we've been sourcing all of our power from there so far This pin will output 3。

3volts and up to 300m as of power that's not an incredible。But it's good enough for most of your 3。

3 devices。 The Vbu pin is another place to source power from。

 but it's a bit more complicated than Vs V of hijacks power coming from the USB you will only have power on Vbu if your Pico is plugged in with USB and that's gonna give you a if you don't plug it withB you're going get nothing out of it the amount of current it can supply also depends on what you plug the USB into This phone charger for example has a5volt output we can read it on the label so you can get up to onemp from V if you plug yourco into it if plugged it into this battery bank Vbu will supply up to two amps of current but this is not an infinite power supply glitch there is an overall limit of about two as of current regardless of what you plug the Pico into let's say if this battery bank had three amps of current that it could output I could only safely pull about。

2 amps through Vbu So Vbus is going to supply5 volts when plugged into USB and well have however much current the USB source can supply with a continuous maximum of two amps overall the final one is from the GPO pins themselves which we have been using as well These aren't a typical power supply and I wouldn't choose to power things off of them but when we plug things like our LED and resistors into them。

 we are technically sourcing power from the GPO pins themselves we know what voltages we can supply with digital and analog outputs。

 but the pins themselves can only output a maximum of 12 milliamps of current one amp is 1000 milliamps。

 So 12 milliamps is 0。01 to amps which is tiny in comparison to what you can source from Vbu and so the GPO pins should only be used for things like these simple LEDs and buzzes and only very low powered components that you directly drive with the GPO pins。

Now for all the power sources I've mentioned， the important things to remember are the voltage and the maximum current。

 If I had something that I wanted to de power from one of these sources。

 I have to ensure and here's the rule of thumb that the voltages match and that the thing Iing uses less current than the maximum current that the source can provide。

 that's a lot of information so let's go through one component at a time and see where we would draw power from the Pco to power that component。

 This is a display module that we can plug into the Pco It has two signal pins that we will learn how to use in a later video and it also has a ground and VCC pin that we will use to supply it with power I've gone and check the documentation and it says that it needs 3。

3volts so the 3V3 out pin is a good choice to power it as we want the voltages to match but we also need to check its current requirements The documentation also said that it draws up to 20ms of current the 3V3 out。

Pin can supply up to 300 milliamps of current， so we have plenty of milliamps to spare and it's perfectly safe to use this as a power supply for the display。

😊，This is a little array of LEDs in a rainbow， and this device can be powered with anything between 3。

3 and 5 Vs。 You will find that it is very common for components to have a voltage range that it can be powered with instead of an exact voltage 3。

3 Vs means that we could use the same 3 v3 out as before， because the voltages match。

 But this LED matrix can draw up to 4， maybe even 500 mamps of power at full brightness。

 and 3 v3 out has a maximum current output of 300 millamps。

 So we will probably damage the pico if we tried to power one of these off of 3 v3 out。

 A better choice would be to use a vbu， which can provide up to 5volts and 2 amps or 2000 mamp of current。

 The voltage ranges match， and we are under Vbues maximum current。

 Let's say we wanted to power this servo here。 It has three wires，2 of them supply power to the ser。

 and the other one takes a PWM signal to control it。 This signal wire doesn't supply。

Power to the ser so we can just happily plug it into one of our GPO pins and the ser can take any voltage between 4。

8 and6volts。 We're gonna have the pico plugged in with USB so the5 volts from vbu will be suitable to power this as the vbu matches the voltage range of the ser ground to ground and then the positive terminal of the servo to vbu and that works nicely that server can draw up to 600 millampmps or 0。

6 amps of current right now the Pico is plugged into a 1 amp USB power source so vbu will provide one amp of current and will have 04 amps to spare if I wanted to plug in a second ser though it would still use5volts but the current drawer would double these two sers combined now need 1。

2 amps but because our USB power source is only one amp Vbu can't provide enough power to fix this I could just plug it into a more powerful USB source like this two amp battery bank here or find a USB wall charger that can supply up。

2 amps we have been powering the LED and resistor off of our GPO pins。 They will happily run of 3。

3volts and will draw up to 5 milliamps of power with the way we have them wired up。

 Our GPO pins can happily supply 3。3 volts as we know and up to 12 milliamps of power。

 So we have about 7 millamps to spare and we're all good here for things like LED or buzzes。

 powering them directly off of the GPO pins is perfectly fine as these components consume a tiny amount of power。

 It's always worth double checking though that they use less than 12miamps of power。

 You don't want to destroy one of your picos pins What the GPO pins aren't good for is powering things like this solenoid or motor here。

 Even this really small one Both of them can run off of 3。3volts。

 but they draw much more current than 12 milliamp。 This solenoid here draws up to 500 milliamps and this motor here。

 even this really it's really small motor。 This still draws up to 800 milliamps of current。

So how do we power these Both of these take five volts and can be happily powered off Vbus like so this is spinning and working you're gonna have to trust me on that。

 However， it just spins continuously and we have no control over it The problem is I want to control the speed of it but if we can only control things with code through GPO pins but the thing that we want to control draws too much power for those pins what do we do Well we're going to need to use a driver or control board these boards let you use the power from another power source like Vbus but also let you plug a GPO pin from the Pco into it so you can write code to control the motor through that GPO pin but it takes power from somewhere else that can supply enough current This course is not going to show you how to use these driver boards because there are thousands of them out there to choose from and everyone has a slightly different setup we just want to make sure that you're aware of them and why you would use them don't worry though because they usually really straightforward to use and。

Be able to find many tutorials and guides on how to use some of the more popular ones out there And one of the first things you'll probably use one of these four is controlling motors to make like a little car or line following robot or something like that long video with lots of information I apologize but we have one more thing and it's really easy you need to ensure that the connections between your components can support the current that you are pushing through them This is a much bigger server that can draw up to about two as of current and I've got connected to vbu with power supplyB it's all fine but these jumper wires can only support up to about one a of current these ones are on the thinner side can get thicker ones that can support two as if were to put this server under full load and draw two amps continuously these wires would probably start to heat up and melt and maybe even start a fire if I draw that much current for a really long period of time A period of time is in like five minutes even that's how long it might even。

So I would need to ensure that the ground and positive terminals of my servo are connected with wired that is rated up to two amps。

 the signal one is fine because it's a signal wire doesn't use much power The other thing to watch out for is the breadboard itself it has a current limit as well up to about two amps it's all kind of a weakest link in a chain sort of deal which going from the power source to the component all those chains and all those links have to be rated to that current that was a big video and there is an incredible amount of components out there all needing different voltages and currents and you'll usually need to check data sheets or website listings to find that information if you're ever unsure it might be worth checking with somebody who knows what's up or feel free to drop a forum post with your power related questions on our site we're always happy to help different this video but four key takeaways when powering components off of the pico you must ensure that the voltages match and that the components draw。

Less current than the source's maximum current output2 3V3 out provides 3。

3volts and up to 300 millamps of current3， when the PiCO is plugged in via USB。

 VB provides5volts and however many amps the USB can provide with a hard limit of up to two amps and4。

 the GPOO pins of the PiCO are only suitable for powering small components like LEDs as they can only supply up to 12 milliamps of power。



![](img/5618c23dc99ef0a808b0fa3f6010b461_1.png)

![](img/5618c23dc99ef0a808b0fa3f6010b461_2.png)

![](img/5618c23dc99ef0a808b0fa3f6010b461_3.png)