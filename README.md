# BulgarINO / БългарINO 
**The name is just a joke** ... с ударение на И :)<br> 
and sorry for my English

# IoT Concept
How to scale complex technology: **Make it easy and accessible !!!**

_"A complex system that works is invariably found to have evolved from a simple system that worked. A complex system 
designed from scratch never works and cannot be patched up to make it work. You have to start over with a working 
simple system."_ **Gall's Law**

In short: For the last 10 years I have been trying to make Things easier<br>
BTW: Last three months I talked to almost all the big manufacturers: they all rejected the idea :)

Some time ago I had to design a cheap EV Charger ( EVSE )<br>
![hmi](https://raw.githubusercontent.com/Wiz-IO/BulgarINO/main/images/hmi-iot.jpg) 
Trivial and cheap solution, the part **HMI-IoT** I designed it with ESP32 + RMII + LTE

* ESP32 - connection to the EV controller, Display ( HMI ) and WiFi ( for local remote control )
* RMII - Ethernet - Internet capability
* LTE - same as RMII - Internet
  
By the way **ESP32 + RMII** + LTE is the most used combination for **industrial** purposes<br>

Due to the fact that the PCB board had to be of minimal dimensions, I stacked the components several times<br>
-- Damn it... it's the 21st century, Isn't there some **SMART** solution to the above combination<br>
I'm very familiar with what's on the market and started searching the web for: **a cheap and easy solution** <br>
The very first results surprised me, there are countless **DEMO** boards and none of them work for me<br>
These boards **cannot be EMBEDDED** on my PCB board ( industrial project ) !!! <br>

1. I won't be wiring them from scratch
2. I will not explore their SDK and OS at all
3. Unnecessary waste of time... etc

Expanding the search ... The Result: **NONE cheap and easy solution !!!** <br>
There is NOT even an ESP32 + RMII in module form<br>
( check yourself )<br>

The "puzzle" automatically popped into my head. Only then did I analyze the "problem": why everything is **COMPLICATED and EXPENSIVE**
1. The "problem" is created by the company's "economist" - he sets an economic goal without understanding the market, technology and trends...
2. Each piece of the puzzle is the work of specialists who only see their piece, but do not see the big picture and are busy fulfilling the goal of the manager who set the task

![vacancy](https://raw.githubusercontent.com/Wiz-IO/BulgarINO/main/images/vacancy.jpg) 

I jokingly trolled the public with the picture and the text: **C'mon guys, Do Something**<br>
The result in the comments was ... point 1 and 2<br>
EVERYONE reacted like it was a logical task<br>
And it actually is:<br> **These are the most recognizable concepts that have changed the World of Things in recent years**<br>
( arranged by possibilities, and VACANCY is approximately between 500 MHz and 1GHz - MCU / SoC / SiP )<br>
  - **Arduino** - Easy and Cheap, **The biggest ecosystem** !!! is there anyone who hasn't flashed the LED ?
  - **Espressif** - Easy, Cheap and Mass ( over 200 million units per year, reference: 2021 Annual Report )
  - **Rasberry PI** ( no commnets !!! and they officially gave up on the concept )

and so on...<br>
![jungle](https://raw.githubusercontent.com/Wiz-IO/BulgarINO/main/images/jungle.jpg)
<br><br>How do you navigate such a jungle?<br>
( the small boards are missing, but the meaning is the same )<br><br>

I haven't found the "warm water", I'm just trying to get "the puzzle" right<br>
From a historical point of view, embedded solutions start from 2003 Motorola A760 base <br> 
the basis of Android **SMART** phones<br>
( and others before that )<br>
And one of the first mass SBCs was the BeagleBoard ( 2008 )<br>

# What is missing and how it needs to be in order to be:<br> **CHEAP and EASY, therefore MASS**<br>

![wires](https://raw.githubusercontent.com/Wiz-IO/BulgarINO/main/images/soft.jpg) 

## HARDWARE

There are well over 5 IoT chips on the market right now that are well under $5 <br>and around $5 demo boards
and many more unusable chips under NDA ... ( [as an example](https://jaycarlson.net/embedded-linux/) )<br>
It is understood from the article that we will talk about Embedded Linux ( doesn't have to be Linux )<br>
So the condition **CHEAP** can be met<br>

Examples of incorrectly positioned products
* [SigmaStar SSD210 tiny dual-core Arm Cortex-A7](https://www.cnx-software.com/2021/03/19/sigmastar-ssd210-tiny-dual-core-arm-cortex-a7-soc-64mb-ram-rgb-display/)
* [$6 Pine64 Ox64 SBC](https://www.cnx-software.com/2022/12/02/pine64-ox64-sbc-bl808-risc-v-multi-protocol-wisoc-64mb-ram/)
* ALL PI Zero Clonings

Examples of correctly positioned products
* [Sipeed M1 RISC-V](https://www.cnx-software.com/2018/10/22/sipeed-m1-risc-v-computer-vision-module/)

**MODULE colleagues, MODULES !!!**
* whoever wants to build a project from scratch is his problem and no one limits him
* easily embed into **industrial** and hobby projects
* hardware bugs are avoided
* saves design time
* there are chips with many and different cores ... 1 for OS, 1 for FreeRTOS ?! lots of room for creativity...
* they have specialized peripherals - displays, 2D acceleration, and even AI...

You can imagine from where the condition will be fulfilled: MASS USE - **industrial projects**<br>
as an example<br>
![form](https://raw.githubusercontent.com/Wiz-IO/BulgarINO/main/images/form-factor.jpg) <br>
From a marketing perspective, you sell 4 products ( last image ):<br><br>
0. CHIP - HI Level Users ( applies to chipmakers )
1. **MODULE** - HI & MID Level Users
2. Demo board -  MID & LO Level Users, fast experiments ... etc
3. Just extended board

I'm not advertising the above module - it costs $5 and has over 5x the capabilities of the ESP32<br>

## SOFTWARE
In this section, we will talk about **embedded Linux** ( for some chips, understand **NuttX** )<br>
We all know about its "complexity" - compiling, settings, etc.<br>
All manufacturers need to test the functionality of the demo board before releasing it to the market. <br>
Why isn't a Linux image published as **FIRMWARE** when it's already compiled and tested? ( just logic )<br>
It's crystal clear that high-level clients can handle the challenges, and there are no comments for them.<br>
( I emphasize the medium and small business, including hobbies. )<br>
Basic **FIRMWARE**, 99% of the clients want to power up the module/board and have everything work.<br> 
They don't want to deal with OS compilation, and for some, it will also be an opportunity for learning.<br>

**Firmware Uploader** - most of them have it, and modules/boards can also be installed at the factory.

We power up the board, and all of us want to start creating and experimenting with **our projects** and ideas,<br> 
not dealing with kernel compilation and its settings.<br>

Where is the Power of Linux apart from being Open Source, **is in its standard ANSI C, C++, POSIX** for Userware Applications<br>
Personally, I don't know an embedded developer who doesn't know C. <br>
ANSI C is at the core of the smallest MCUs, Arduino Core, microPython, etc. <br>
C is taught in "every" school and university, and everyone should start with it. <br>
Even Arduino is the same and works in the same way ( with simplified function names ).<br>

**Userware Applications** (  multiple applications can be executed )<br>
and to begin writing printf("Hello World"), there must be a **USER API** to the kernel and peripherals...<br>

ANSI C, C++, POSIX is available at the client level, meaning: <br>
**This category will inherit ALL Ecosystems from all junior categories** <br> 
as well as parts of the next SBC category. <br>
**The entire zoo of existing Hardware and Software solutions exists up to now !!!** <br>

The Linux can easily execute (in parallel) both Arduino and Python, JS, LUA ... Can you imagine the possibilities?<br>
Can you imagine the level of education that can be achieved with just a "simple" board? <br>
Does ANSI C, C++, POSIX suffice for **industry**?<br>

**Userware Uploader** - the easiest and most commonly used solution for upload and access to the file system is the **ADB daemon**<br>
The **GDB daemon** allows interactive debugging of client applications without hardware interfaces.<br>

## INTEGRATION
Works with the simplest text editor - MAKE - GCC ( **multi-platform** )<br>
I personally don't know a developer who hasn't worked with the following:
* Eclipse
* VSCode
* **PlatformIO** ( 10 Desktop IDEs )
* Arduino IDE

Create New Project ( C, C++, Arduino ... etc )<br>
User code ... Compile, Upload/Debug, Monitor<br>
Something complex for industrial and hobby projects?<br>

## SUMMARY 
What are the basic trivial things to make it easy and massive:
1. **MODULE**
2. **FIRMWARE**
3. **USER API / USERWARE APPLICATIONS**
4. **ADB**
5. **GDB**
6. **INTEGRATION**

Now do you understand how easy the "puzzle" is and why no one saw it until now?<br>
Again, I reiterate, I haven't discovered hot water...<br>
The concept: **Firmware - Userware** has existed for a long time and widely,<br>
every phone, and not only, works this way<br>
and this IoT category should work just like that

especially in embedded systems:<br>
[**BeagleBone**](https://en.wikipedia.org/wiki/BeagleBoard) 2008 worked with Python client-side by default, <br>
perhaps the first mass-market SBC, there was no Raspberry Pi at that time.<br>

[**Microsoft AzureSphere ( Mediatek MT3620, A7 + several M4 cores )**](https://www.avnet.com/wps/portal/us/products/avnet-boards/avnet-board-families/ms-azure-sphere/) <br>
Unfortunately, Microsoft overshot by 300%, and the project is actually a **total failure** <br>
The project satisfies corporate interests, one of its goals being MAXIMUM SECURITY and for that to happen, it really needs: <br>
**FIRMWARE - USERWARE**<br>
DEMONSTRATIONS:
* [Azure Sphere MQTT to Google IoT - Arduino PlatformIO](https://www.youtube.com/watch?v=HCDTlCzEmw0)
* [Azure Sphere MQTT to Amazon - Arduino PlatformIO](https://www.youtube.com/watch?v=ucOvjfXg0-o)
* [Arduino Azure Sphere - PubSub MQTT Client](https://www.youtube.com/watch?v=-hhSmKoT8T0)
* [Azure Sphere - Wiring ( Arduino ) MT3620 Cortex-M4](https://www.youtube.com/watch?v=bdG8GsRaUSA)
* [Azure Sphere M4F FreeRTOS](https://www.youtube.com/watch?v=9-ozj0XCyF8)
* [Azure Sphere microPython](https://www.youtube.com/watch?v=EVx8pP0rD1Q)

**Qualcomm LTE Linux Modems (e.g., Uqectel EC2x)** <br>
The concept exists, yet no one uses it - it's an outdated and very expensive solution...<br>
DEMONSTRATIONS:
* [PlatformIO Arduino - Quectel EC25 - MQTT Amazon IoT](https://www.youtube.com/watch?v=sbLJNXTRLxc)
* [PlatformIO Arduino - Quectel EC25 - HTTP / HTTPS](https://www.youtube.com/watch?v=nw-W78SpLRQ)
* [PlatformIO Quectel EC25 Arduino](https://www.youtube.com/watch?v=YgKAmD0tVig)

![all](https://raw.githubusercontent.com/Wiz-IO/BulgarINO/main/images/all.jpg)

If you don't do them, someone else will and you'll chase them...

>If you want to help / support:   
[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ESUP9LCZMZTD6)
