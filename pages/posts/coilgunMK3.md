---
title: The CoilGun MK.III Project
date: 2023/10/16
description: The CoilGun MK.III project breakdown
tag: Electronics, Electromagnetism, Esp32, Programming
author: Chris
---

### CoilGun MK.III prototype

import Image from 'next/image'
import Link from 'next/link'

<Image
  src="/images/Coilgun_MK3/Coilgun_MK3_Prototype.png"
  alt="Coilgun MK.III prototype"
  width={2016}
  height={1134}
  priority
  className="next-image"
/>

<p>After few years from the MK.II I decided to start a new coilgun. As you can see the model itself doesn't differ much from the MK.II but a few major changes were made:</p>

- Instead of using an Arduino Nano as the MCU I switched to the more powerful Esp32
- The IR led and receiver were replaced with an easier to use [CNY70](https://www2.mouser.com/ProductDetail/Vishay-Semiconductors/CNY70?qs=%2Fjqivxn91cdreAm7vR28%252BA%3D%3D) IR sensor
- The old boost converter was trashed and replaced with a much more efficient and powerful [ZVS Driver]()

<p>In the end I decided to scrap this design beacuse I wanted something more modular and easier to assemble. So all of these changes where channeled in the final MK.III design.</p>

## Coilgun MK.III

<Image
  src="/images/Coilgun_MK3/Coilgun_MK3.png"
  alt="Coilgun MK.III"
  width={2016}
  height={1134}
  priority
  className="next-image"
/>

<p>Everything changed.</p>

<p>This is the best design I've come up with in the last 2 years. All the experience gathered in the span of 10 years is inside this design, from the electronic circuit to the 3D model itself.</p>

<p>Let's start!</p>

### Breakdown

<p>Unlike the MK.II, this iteration is fully modular, meaning that stages can be added/removed by simply modifing a couple of lines of code.
Here's the list of features that'll be broken down:</p>

1. <Link href="#Modular_Stages">Plug and Play modular stages</Link>
2. Esp32-WROOM-32 DEVKITC custom PCB
3. Separeted SCRs firing circuit PCB
4. Capacitor Charge Feedback Circuit (CCFC) PCB
5. CNY70 IR sensor custom PCB
6. SCR custom PCB
7. OLED interface
8. ZVS Drivers as the capacitors banks chargers

<div id="Modular_Stages">

## 1.Modular stages

<p>The main goal of this coilgun was the modalurity so that there's the possibility to build a user defined number of stage coilgun. For example the MK.III is a 4 stage coilgun that can be expanded in a 5, 6 or even 8 stage without problems.</p>

<p>Creating a modular stage wasn't hard at all, it's a pin based design as you can see here:</p>

<Image
  src="/images/Coilgun_MK3/Stage.gif"
  alt="Coilgun MK.III Stage"
  width={1920}
  height={1080}
  priority
  className="next-image"
/>

<p>The model is quite simple: </p>

- holes are present on both stage ends to insert the pins that will link the other stages togheter 
- in the middle the solenoid is wound and incapsulated within the stage 
- at the end of the stage there's the socket for the CNY70 IR sensor
- on top there're holes to attach the firing circuit
- on the bottom there're holes to attach the stage to the base of the coilgun

<p>One of the most important changes it's the positioning of the firing circuit directly on top of the stage itself, this way the wires coming from the coil are shorter that the previous versions, ensuring less energy dissipation from wire resistance.</p>

</div>