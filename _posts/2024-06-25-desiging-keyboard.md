---
title: Designing my own mechanical keyboard from scratch
date: 2024-06-25 05:52:20 +0800
categories: [Blogging, Keyboard]
tags: [keyboard, design] # TAG names should always be lowercase
media_subpath: /images/designing-keyboard/
---

### Introduction

Ever since I first laid my fingers on a mechanical keyboard, I was hooked. The feeling, feedback and the satisfying clack with every stroke was incredibly satisfying compare to the mushy rubber domes I was used to. It's been almost six years since I dip my toes in this hobby. Only last year I'm started to think about designing my own keyboard. That's when I decided - why not try building one myself from scratch? Yes, from the PCB to the case.

This blog will chronicle my journey into the world of custom keyboard building. From designing the PCB, to configuring custom firmware and lastly the keyboard case itself. This is not a tutorial but I'll be documenting some of the steps, hurdles and the triumphs along the way so you can get a grasp on how to start designing your own keyboards.

### Design Decisions

So the first things that have to be decided is the keyboard layout. I am a fan of Function Row Less(FRL) layout but I don't want just the usual layout. I'm thinking that if I want to make my own custom keyboard, I better use a unique layout. So I'm thinking of adding extra keys(XT) on the left side. So it will be five more extra keys on top of the typical FRL layout. I also decided to make the top key interchangeable with a rotary encoder. This adds a touch of versatility for volume control or custom functions, depending on your preference. ANSI support only because I ~~hate~~ don't use ISO.

![img-description](/layout.png){: width="700" height="400" }
_Layout_

For the initial design decisions, I've opted to choose a comfortable 6-8 degree typing angle. The exact typing angle will be adjust during my process of designing the case later. For mounting, I'm using the the tadpole pin system from GEON, because that's what I had handy at the time. I'm making this keyboard a year ago, but if I'm doing it now, I think there are better mounting options. This will be later on my next keyboard.

For the USB connectivity, the keyboard will use Unified Daughterboard C3. This decision keeps the main PCB clean by moving the USB-C port to a separate board. This also helps me when I want to trace on my PCB later and also keep the port on the center of the keyboard. Speaking of the PCB, the PCB will be 1.6mm thickness and has and most importantly the microcontroller(MCU) must has QMK/VIAL firmware support for wired connectivity.

### PCB

The most common software for designing PCB in the custom keyboard building scene is KiCad. There are useful guide on Youtube on how to start design the PCB, I recommend start with video from [Noah Kiser](https://www.youtube.com/@noahkiser/videos) on RP2040. But there is latest guide using STM32, which template is provided for the controller and USB port, it helps for the most part making the design decisions about routing the microcontroller. The PCB Guide from [Zykrah](https://guide.zykrah.me/) and [ai03](https://www.masterzen.fr/2020/05/03/designing-a-keyboard-part-1/) are also a good reading for those who want to start making their own PCBs. The frequent MCU use on keyboard PCB are ATMega32u4 and STM32. But for this project, I choose RP2040, a newer MCU which has QMK support. Besides the availability, it's has more memory and capabilities than the ATMega and STM32. A bigger flash memory maybe useful if you want to use something like an OLED screen later down the road. Also, it's so much cheaper at only \$1 per piece compare to \$5 for the ATMega32u4, at least last year on JLCPCB. I'm not sure about the availability and the prices of right now.

As you can see on the schematic below, the PCB just has simple features on it. This is my third time making PCB but its only my first time designing using integrated MCU on board. This is also my learning experience for me and I'm try to keep it simple for now. If you notice, I only add an encoder and a 3mm LED for the capslock. There are no backlight because it will add complexity for me. This will be on my next project. I'm trying to keep the important features work first.

![MCU schematic](/sch-mcu.png){: width="700" height="400" }
_MCU schematic_

For the keys, it's pretty simple. Just a bunch of switch layout in rows and columns which called as matrix.

![Switch schematic](/sch-matrix.png){: width="700" height="400" }
_Switch schematic_

Once the schematic is completed, now its time for routing the PCB.

![PCB Rounded](/pcb-rounded.png){: width="700" height="400" }
_PCB Rounded_

### Firmware

### Case
