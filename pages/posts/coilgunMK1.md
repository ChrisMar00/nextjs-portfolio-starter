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

<p>This is the first coilgun I've ever made, the Coilgun MK.I. Me and my friend [Alex](https://github.com/AlessandroBonomo28) used a Raspberry Pi 3 to time the firing of the relays to discharge the capacitors into the BAD wound coils. We've been using a small metal pin as projectile, weighting ~2g. This prototype didn't work at all, but surely was a good test bench to learn the basics of electronics and programming.</p>

### Features
- Raspberry Pi 3 as the MCU
- 3 Stages, each one with 4x 25V@4700μF capacitors in parallel
- Relays with manual firing timing
- SMPS to charge up the capacitor bank
- Efficency unkown