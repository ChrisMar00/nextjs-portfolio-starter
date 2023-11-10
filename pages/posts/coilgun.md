---
title: The CoilGun Project
date: 2023/10/16
description: The CoilGun fundamentals
tag: Electronics, Electromagnetism, Programming
author: Chris
---

# The CoilGun

<p>One of my favorite projects that I ever made.</p>

<p>Many years ago, when I was still in middle school, I started watching ElectroBoom and one of his [video](https://www.youtube.com/watch?v=mdZo_keUoEs) sparked my curiosity.
The possibility to create a "gun" that runs purely on electricity trilled me. So I started designing one on my own, with zero experience in electronics and programming.</p>

<p>Here you can find the differents designs me and my friends have created in the last years:</p>

1. [CoilGun MK.I](coilgunMK1)
2. [CoilGun MK.II](coilgunMK2)
3. [CoilGun MK.III](coilgunMK3)

## Working principle
### Definition

<p>The coilgun is an electromagnetic gun based on [magnetic propulsion](https://en.wikipedia.org/wiki/Electromagnetic_propulsion). Using solenoids we can accelerate a metal projectile to high speed.</p>

### Coilgun Stages

<p>Usually a coilgun is made of stages, each one made up of:</p>

- solenoid a.k.a. Coil
- capacitor bank
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

<p>When we talk about solenoids it's really important to consider how we wind it:</p>

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