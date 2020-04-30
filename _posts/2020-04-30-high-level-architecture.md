---
layout: post
title: High Level Architecture of IBM Server Platforms
date:   2020-04-30 15:05:14 +0530
categories: architecture
author: linuxppc
tags: [powerpc, hypervisor]
---


   | MSR_{SE} | MSR_{HV} | MSR_{PR} | State                   |
   |----------+----------+----------+-------------------------|
   |        0 |        0 |        0 | Unsecure VM kernel      |
   |        0 |        0 |        1 | Unsecure VM application |
   |        0 |        1 |        0 | Hypervisor              |
   |        1 |        0 |        0 | Secure VM kernel        |
   |        1 |        0 |        1 | Secure VM guest         |
   |        1 |        1 |        0 | Ultravisor (hcall)      |
   |        1 |        2 |        0 | Ultravisor (ultracall)  |
   |----------+----------+----------+-------------------------|

## Bare Metal/PowerNV

![Bare Metal](/images/powernv.png)


## PowerVM/phyp

![phyp](/images/phyp.png)
