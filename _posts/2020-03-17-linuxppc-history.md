---
layout: post
title: History of Linux Kernel for PowerPC
date:   2020-03-17
categories: kernel
author: linuxppc
tags: [powerpc]
---

*A better rendered version of the 
[original wiki page](https://github.com/linuxppc/wiki/wiki/History)*

In the beginning there was [the `arch/ppc` port](https://github.com/mpe/linux-fullhistory/commit/238327caacec57ec3c9e6a1db02370f3deec0c93)

Later [the `arch/ppc64` port](https://github.com/mpe/linux-fullhistory/commit/c3aa9878533e724f639852c3d951e6a169e04081) was merged.

Other notable events:
* [Initial pseries NUMA suport](https://github.com/mpe/linux-fullhistory/commit/68eb1b0e9bc286fe221a4813d96eae36e916b0a2)

The ppc/ppc64 merge:
* [Beginning of the merge](https://github.com/mpe/linux-fullhistory/commit/564ee7a5668e8b6d3b369fd807c75c77285c88d4) (2005), ie. first appearance of `arch/powerpc`.
* [End of the ppc64 merge](https://github.com/mpe/linux-fullhistory/commit/8a5abdf80ecf3ad3fa052878778c7185c5911a53) (2005), ie. last occurence of `arch/ppc64`.
* [End of the ppc merge](https://github.com/mpe/linux-fullhistory/commit/917f0af9e5a9ceecf9e72537fabb501254ba321d) (2008), ie. last occurence of `arch/ppc`.

<!-- | 1995 | [the `arch/ppc` port](https://github.com/mpe/linux-fullhistory/commit/238327caacec57ec3c9e6a1db02370f3deec0c93)         |      | -->
<!-- | 2002 | [the `arch/ppc64` port](https://github.com/mpe/linux-fullhistory/commit/c3aa9878533e724f639852c3d951e6a169e04081)       |      | -->
<!-- | 2002 | [Initial pseries NUMA suport](https://github.com/mpe/linux-fullhistory/commit/68eb1b0e9bc286fe221a4813d96eae36e916b0a2) |      | -->


![PowerPC Linux History](/images/lppc-history.png)
