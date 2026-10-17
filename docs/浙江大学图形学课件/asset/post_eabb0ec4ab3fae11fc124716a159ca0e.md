

## Accelerated Graphics Port (AGP)

A dedicated bus that allows direct access of main memory

![](img/94fd648dd12ff5c2cbed197b5038ba1a_404_0.png)

## AGP

- AGP 1x is four times as fast compared to PCI!  
  (now we have AGP 8x)  
- No more local bus congestion!  
- More geometry can be processed!  
- Direct execution of many graphics operations  
  from main memory

## ISA、PCI、AGP及PCI Express

- 在80年代，最當紅的高速匯流排是ISA（Industry Standard Architecture），它的傳輸速率每秒只有8.33MB  
- 90年代，PCI（Peripheral Component Interconnect）的每秒133MB  
- 繪圖卡等須高速運作的多採用AGP，它每秒可傳輸2.1GB  
- 現在走紅的是PCI Express，它也稱為3GIO。PCI Express的傳輸速率為每秒2.5GB，還有潛力再增加好幾倍。

![](img/94fd648dd12ff5c2cbed197b5038ba1a_406_0.png)

| 总线类型 | 数据传输率 |
|---|---|
| ISA | 8.33MB/S |
| EISA | 133MB/S |
| VISA | 133MB/S |
| PCI | 133MB/S |
| AGP-1X | 266MB/S |
| AGP-2X | 533MB/S |
| AGP-4X | 1.066GB/S |
| AGP-8X | 2.133GB/S |
| PCI Express1X（双通道） | 500MB/S |
| PCI Express2X（双通道） | 1GB/S |
| PCI Express4X（双通道） | 2GB/S |
| PCI Express8X（双通道） | 4GB/S |
| PCI Express16X（双通道） | 8GB/S |

## PCI Express Bandwidth Improvements (NVIDIA)

- Improved Write Bandwidth is Critical for Rendering Directly to System Memory

|    | Bandwidth (GB/s) |
|---|---|
|    | READ¹ | WRITE² |
| AGP-8X | 2 | 0.2 |
| PCI Express x16 | 4 | 4 |

¹ READ from system memory to GPU  
² WRITE from GPU to system memory

## Other Input Devices

### Physical Devices:

Scanners: work on the same principle as laser printers.

Voice recognisers: speaker dependent/independent

3D Sonic Tablet: for 3D locator input

Pressure sensitive tablet: adds a value to location

## Input Device Access Modes

### Request Mode:

Blocked mode of input; synchronous with the program. Input device status on request. Wait until input is completed.

### Event Mode:

Asynchronous with program; supply service routines for handling events and inputting a device status.

### Sample Mode:

Polling mode for inputting a device status or an event.

## Virtual Reality Devices

**HMD:** Head mounted display with two one inch CRT monitors in each eye to display stereo images.

**Cave:** using projection displays.

**Stereo glasses.**

**Sensors and trackers:** 6 degree measure - (x,y,z and orientation)

**Gloves:** wrist and finger movement.

**Force feedback gloves:** for haptic output.

Body suits: for sensing body movement

**Video input recognisers** for movement, gesture, facial expression, etc.

## Head Mounted Display

![](img/94fd648dd12ff5c2cbed197b5038ba1a_414_0.png)

Boom Technology,  
[http://www.fakespace.com/](http://www.fakespace.com/)

## CybergIove

![](img/94fd648dd12ff5c2cbed197b5038ba1a_414_1.png)

([http://www.virtex.com](http://www.virtex.com))

## CAVE

(http://www.pyramidsystems.com/)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_415_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_415_1.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_415_2.png)

[http://evlweb.eecs.uic.edu/pape/CAVE/](http://evlweb.eecs.uic.edu/pape/CAVE/)

## Immersive Wall

![](img/94fd648dd12ff5c2cbed197b5038ba1a_416_0.png)

![](img/94fd648dd12ff5c2cbed197b5038ba1a_416_1.png)

## Color

## Why study Color ?

- *Synthesis of realistic images* has been the primary goal of computer graphics  
- In this quest for *realism* it is necessary to relate the perceptual processing of visual information to the image display technology  
- Understanding *color perception* and its relationship to both *color computation* and *color reproduction* becomes important

## What is color ?

- **Color** is the brain’s reaction to a specific visual stimulus  
- Subjective sensation experienced by the observer. There is no such thing called color without an observer  
- Depends upon  
  - Physics of light  
  - Interaction of light with physical materials  
  - Interpretation of the resulting phenomenon by the human visual system and the human brain

