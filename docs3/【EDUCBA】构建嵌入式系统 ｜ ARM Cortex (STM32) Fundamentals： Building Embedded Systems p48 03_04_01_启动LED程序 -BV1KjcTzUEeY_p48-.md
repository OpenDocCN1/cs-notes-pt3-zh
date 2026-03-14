# 【EDUCBA】构建嵌入式系统 ｜ ARM Cortex (STM32) Fundamentals： Building Embedded Systems p48 03_04_01_启动LED程序 -BV1KjcTzUEeY_p48-

![](img/61aa157f5171d17940e2bec48f4624fc_0.png)

Hey ons， welcome back。So now in this particular video， we will understand。

The procedure to turn on the LED Okay well learn to write code to turn on the LED and that is not so easy。

 So that's what makes the embedded system programming so unique that you know you must know so many things such as the memory map。

 the peripheralpher registers， the register addresses。

 the hardware connections and so many things So that's why be patient until we cover all the required things to do the particular exercise。

 Okay so now the procedure to turn on the LED right so the first of all you will need to identify the。

GPIO port。Okay， now that is a ferif ferral which is used to connect to the LED。

So in this case we have identified the GPIO port which is used to connect to the LED which is your GPIOD right we have to also identify the GPIO pin where the LED is connected and we have identified that over here which is to2 right so we have identified the pin。

Okay， the third procedure over here is to activate the GP Io ferfer by default in the macrocont。

 most of the peripheralfers are dead。 Okay， so basically this is our first step。 Okay。

 I'll just mention over here so that it makes your concepts very much clear we have to。Identify the。

GPIO port。That is used to。Connect thee。LED and that is GPIod。

 The second thing that we have identified is。Dgp。A you pin。Where the LED is。

Connected and that is2 now coming to the next process， which is activate。GPO。Veryairy ferll。Okay。

 so we will have to activate this basically we will have to enable the clock。Now。

Until you basically enable the clock okay for a ferferral。

 the ferferral is dead and it neither function or nor it takes any configuration values which are set by you。

 so once you activate the clock of the ferferral it is ready to take your configurations and control related commands or arguments as well as you can also say it as configuration values。

Now for some macrocontrollers the ferifferel may be on by default and you need not do any activation So for that you should explore by the device data sheet for reference manual so this actually depends upon what kind of macrocontroller you are using or who is the vendor so different vendors adopt different design goals so that's why in most of the macrocontroller design by ST macrosystems macroelectrons。

 the feriffers are dead by default and it should enable the clock first right so our next step after this would be to configure the GP Iop pin mode as output so this would be our fourth step。

To configure the GPI open pin mode as。Output， so since your。

Driving an LED okay which is to on or to off the operation mode of the GPI op has to be configured as output mode right After that we have to write to the。

GPIO pin， so you'll have to write there one that is high to make the pin state which is 3。3volt。

 you will have to market0 which is low to make the pin state to0volt which means to on it or to of so to summarize the procedure you are supposed to go through the P steps given over here first is identify the GPIO port used to connect the LED next is identify the GPIO pin where the LED is connected then activate the GPIO ferrifer which is enabling the clock configurefi the GPIO pin mode as output then write the GPIO pin Now next comes is how to enable this particular clock so through the ferifferal clock registers of the macrocont will understand how can we enable this particular ferifferal clock in the upcoming video tune。

Until then， have a nice day。 Thank you。

![](img/61aa157f5171d17940e2bec48f4624fc_2.png)