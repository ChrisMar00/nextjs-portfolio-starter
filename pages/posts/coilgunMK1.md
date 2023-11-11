---
title: The CoilGun MK.I Project
date: 2023/10/16
description: The CoilGun MK.I project breakdown
tag: Arduino, Electronics, Electromagnetism, Programming
author: Chris
---

# CoilGun MK.I

import Image from 'next/image'

<Image
  src="/images/Coilgun_MK1/Coilgun_MK1.png"
  alt="Coilgun MK.I"
  width={1920}
  height={1080}
  priority
  className="next-image"
/>

<p>This is the first coilgun I've ever made, the Coilgun MK.I.</p> 

<p>When me and my friend [Alex](https://github.com/AlessandroBonomo28) started this project back in 2014, we had very little knowledge on electronics and programming, so we went out on a limb.</p> 

<p>The 3 coils were wound very badly on a 10mm PVC pipe using scrap enamel copper wire of various sizes.</p> 

<p>To power the coils we used 3 capacitor banks with 4x 25V@4700μF capacitors in parallel, that didn't give us much power to be honest, but we didn't know. An SMPS was used to charge up the capacitors to ~25V.</p>

<p>Then to discharge the capacitors into the coils we used a relay board paired with a Raspberry Pi 3 to time the firing. A little python script did the job.</p> 

<p>We've been using a small metal pin as projectile, weighting ~2g.</p>

<p>This prototype didn't work at all, but surely was a good test bench to learn the basics of electronics and programming.</p>

### Features
- Raspberry Pi 3 as the MCU
- 3 Stages, each one with 4x 25V@4700μF capacitors in parallel
- Relays with manual firing timing
- SMPS to charge up the capacitor bank
- Efficency unkown