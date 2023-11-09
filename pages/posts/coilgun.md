---
title: The CoilGun Project
date: 2023/10/16
description: The CoilGun project breakdown
tag: Electronics, Esp32, Electromagnetism
author: Chris
---

# Preamble

<p>One of my favorite projects that I ever made.</p>

<p>Many years ago, when I was still in middle school, I started watching ElectroBoom and one of his [video](https://www.youtube.com/watch?v=mdZo_keUoEs) sparked my curiosity.
The possibility to create a "gun" that runs purely on electricity trilled me. So I started designing one on my own, with zero experience in electronics and programming.</p>

## Working principle
### Definition

<p>The coilgun is an electromagnetic gun based on [magnetic propulsion](https://en.wikipedia.org/wiki/Electromagnetic_propulsion). Using solenoids we can accelerate a metal projectile to high speed.</p>

### Coilgun Stages

<p>Usually a coilgun is made of stages, each one made up of:</p>

- solenoid a.k.a. Coil
- capitor bank
- charger cirucit for the latter
- firing circuit
- and a bullet sensor

### The Solenoid

<p>The most important part of a coilgun its the coil itself. A solenoid is just a piece of wire, usually enamel copper wire, wound to resamble a cilinder.</p>

<p>By passing an electric current into the solenoid we generate a magnetic field that can attrack ferromagnetic objects insiede of it. The attraction can be calculated using this formula:</p>

import Image from 'next/image'

<Image
  src="/images/Formulas/Solenoid_Magnetic_Flux.png"
  alt="Solenoid magnetic flux"
  width={800}
  height={400}
  priority
  className="next-image"
/>

<p>where B is the magnetic flux generated from the solenoid, μ0 is the magnetic costant of the material, N is the number of spires, I the current intensity and l the lenght of the solenoid.</p>

<p>When we talk about solenoid it's really important to consider how we wind it:</p>

- use an appropriate wire gauge when building a solenoid, higher gauge means higher current that directly translates into higher magnetic flux
- always wind in the same direction
- use super glue to secure the wire so it doesn't unspool itself
- after finishing a layer in one direction, go backwards maintaing the winding direction

<p>If we make mistakes during the winding, the solenoid will not work as intended. Usual problems could be coils shooting backwards or not shooting at all.</p>

### Power the solenoid

<p>To power the solenoids we have 2 options:</p>

- use high capacity LiPo batteries
- use high voltage capacitors

<p>The difference between the two is that while batteries are able to discharge more times in a certain time frame and are easier to use, capacitors are way more powerful and can store much more energy.</p> 

<p>The capacitors store a defined amount of energy, and Using a simple formula we can calculate the stored energy E:</p>

<Image
  src="/images/Formulas/Capacitors_Energy.png"
  alt="Capacitors energy"
  width={800}
  height={400}
  priority
  className="next-image"
/>

<p>where C is the capacitance of capacitor and V is the voltage across the latter.</p>

### Switching Operations

<p>To switch the capacitors on the coils you should use an electronic switch such as Mosfets or SCRs. Avoid using relays, they're too slow and in higher currents the contacts inside of the relay can get stuck. Also it's really important to use some kind of isolation to separate the high voltage side from the low voltage side.</p>

### Bullet sensor

<p>It's really important to have some kind of sensor to detect the bullet entering/exiting a stage for a few reasons:</p>

- turn off the exiting stage and turn on the entering stage
- check if the bullet actually fired

<p>The best sensor in my opinion is the infrared one, evenif I've seen mechanical sensors, like metal tabs at the end of the stage, been used in other designs.</p>

## CoilGun MK.I

<Image
  src="/images/Coilgun_MK1/Coilgun_MK1.png"
  alt="Coilgun MK.I"
  width={1920}
  height={1080}
  priority
  className="next-image"
/>

<p>This is the first coilgun I've ever made, the Coilgun MK.I. Me and my friend [Alex](https://github.com/AlessandroBonomo28) used a Raspberry Pi 3 to time the firing of the relays to discharge the capacitors into the BAD wound coils. We've been using a small metal pin as projectile, weighting ~2g. This prototype didn't work at all, but surely was a good test bench to learn the basics of electronics and programming.</p>

### Features
- Raspberry Pi 3 as the MCU
- 3 Stages, each one with 4x 25V@4700μF capacitors in parallel
- Relays with manual firing timing
- SMPS to charge up the capacitor bank
- Efficency unkown

## CoilGun MK.II

<Image
  src="/images/Coilgun_MK2/Coilgun_MK2.png"
  alt="Coilgun MK.II"
  width={5120}
  height={3840}
  priority
  className="next-image"
/>

<p>Later on with another friend, [Peppe](https://github.com/A-Common-Guy), we started another coilgun project. We started studying the topics we needed to create a functioning coilgun, starting from electromagnetism to power electronics and C++ programming. Then I bought a 3D printer that made the prototyping much more easier than before. A little bit of thinkering and we came up with the Coilgun MK.II. </p>

<Image
  src="/images/Coilgun_MK2/Coilgun_MK2_2.png"
  alt="Coilgun MK.II"
  width={5120}
  height={3840}
  priority
  className="next-image"
/>

<p>This iteration was the first one that actually worked and didn't just made us waste money.</p>

#### Overall
<p>We used an Arduino Nano as the brain, controlling everything from the firing routine to the sensing of the bullet. The firing tecnique was changed, from a manual timed firing routine to an automated one, using IR led and IR receiver positioned at the end of every stage.</p>

<p>The MK.II had 4 stages and each one of them had 2 capacitors in parallel, specifically 400V@1500μF [ItelCond capacitors](https://www.itelcond.it/prodotti/acc-acs-85-5000hrs/), coming to a total of 400V@3000μF. We also added for each stage's coil a flyback diode in anti-parallel to preserve and protect the semiconductors used to switch the capacitors. To charge up these capacitors I built a very simple boost converter that, while being highly inefficient, helped us with the charging of a total of 8 capacitors. At the end of each stage there were an IR led and an IR receiver used to sense the passing of the bullet, this way we could turn off the current stage and trigger the next one.</p>

<p>To switch the capacitors on the coils we started using N-Channel Mosfets; unfortunatly they've all blown up because of the high power generated by the capacitors. The solution was found in the [SCR](https://en.wikipedia.org/wiki/Thyristor). We designed the circuit to drive the SCRs and ordered the corrisponding PCBs from JLCPCB. Each PCB had an octocoupler to isolate the low voltage arduino side from the high voltage capacitors side.</p>

<p>The bullet used was a headless 4.5 mm steel nail, weighting ~5g and long ~4cm.</p>

<Image
  src="/images/Coilgun_MK2/Coilgun_MK2_Lattina.gif"
  alt="Coilgun MK.II penetration"
  width={640}
  height={352}
  priority
  className="next-image"
/>

<p>Here you can see the coilgun penetrating a soda can.</p>

### Features
- Arduino Nano as the MCU
- 4 Stages, each one with 2x 400V@1500μF capacitors in parallel
- SCR with IR sensors as the automated firing tecnique
- Boost converter to charge up the capacitor bank
- Efficency unkown

### CoilGun MK.III prototype

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

###