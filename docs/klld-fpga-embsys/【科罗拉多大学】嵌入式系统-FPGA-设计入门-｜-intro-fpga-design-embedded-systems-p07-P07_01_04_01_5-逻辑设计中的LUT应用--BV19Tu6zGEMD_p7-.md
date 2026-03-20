# 【科罗拉多大学】嵌入式系统-FPGA-设计入门-｜-intro-fpga-design-embedded-systems-p07-P07_01_04_01_5-逻辑设计中的LUT应用--BV19Tu6zGEMD_p7-

![](img/437b44edb6d4741734b697a935ecc049_0.png)

Let's learn about designing logic with lu。In this video。

 we will consider the use of Luts in logic design。 FgaAs you look up tables。

 Lus as the base logic element。 Luts are quite versatile for logic design。

 Learning to love Lus takes some time， but it'll be worth the effort。In the previous video。

 we discussed how Luts can be used to implement any end input logic expression and being the number of inputs to the Lut as in this example。

For a three input lot， we need eight memory locations， for four inputs， 16 memory locations。

 and so on。A lead is typically built out of SRAM bits to hold the configuration memory， lett mask。

 and a set of multiplexors to select the bit of the SM that drives the output。

The figure shows a four lott which consists of 16 bits of S RAM and a 16 to1 multiplexer implemented as a tree of two to1 multiplexors。

 The four lot can implement any function of four input， inputs being A， B。

 C or D by setting the appropriate value on the lut mask。

It can also be built from two to three lus connected by a two to one multipleer。

We can implement more logic in the larger let devices。 however。

 theres a trade off between let size and the amount of routing needed。Bigger lus mean less routing。

 but also more memory locations。 Let's look at some examples to see why。

If we used an8 input Lut to create an 8 B address decoder， only one logic cell would be needed。

 The figure shows an implementation in app pal， but the8 input Lu would look similar。 However。

 if we use three input Lus， then four levels of logic elements and the associated routing between them will be needed as shown。

Let's determine how many lots are needed to make a four bit comparator。

The X nor of the first two bits can be implemented in one4 input Lu， as can bits 3 and 4。

 the four input and on the end can be created in a four input let。

 So the answer is three total four input lotss are required to implement a 4 bit comparator。

How many four input Lus will a full add require？Think about this。

And we will look at it in depth in our next video。In this video， we have learned。

FPGs use lets of various sizes to implement logic。 There is a tradeoff between the size of the lut and the amount of routing required。

 La Lus can create more logic， which will require less routing。 Small lets will require more routing。

 but offer better logic efficiency。 Ls can be used to create a variety of combinatorial logic functions。



![](img/437b44edb6d4741734b697a935ecc049_2.png)