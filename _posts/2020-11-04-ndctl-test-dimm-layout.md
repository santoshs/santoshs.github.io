---
layout: post
title: DIMM and region layout required for ndctl test
date:   2020-11-04 11:56:00 +0530
categories: architecture
author: santosh
tags: [ndctl, nvdimm, linux]
---

![region layout](/images/region_layout.png)

## Bus 0

|  DIMM | id | handle | phys_id |
|-------+----+--------+---------|
|     0 | -  |    0x0 |     0x0 |
|     1 | -  |    0x1 |     0x1 |
|     2 | -  |  0x100 |     0x2 |
|     3 | -  |  0x101 |     0x3 |
| 4[^1] | -  | 0x1000 |         |


[^1]: This is a hotpluggable DIMM

## Bus 1

| DIMM | id |  handle | phys_id |
|------+----+---------+---------|
|    5 | -  | 0x10000 |     0x0 |
|    6 | -  | 0x10001 |     0x0 |


## Mappings

### Region 0
- size: 32M
- Namespace type: PMEM
- mapping:

  | DIMM | start | size | position |
  |------+-------+------+----------|
  |    0 |     0 | 16M  |        0 |
  |    1 |     0 | 16M  |        1 |
  |------+-------+------+----------|


### Region 1
- size: 32M
- Namespace type: PMEM
- mapping:

  | DIMM | start | size | position |
  |------+-------+------+----------|
  |    0 | 16M   | 16M  |        0 |
  |    1 | 16M   | 16M  |        1 |
  |    2 | 16M   | 16M  |        2 |
  |    3 | 16M   | 16M  |        3 |
  |------+-------+------+----------|

### Region 2
- size: 32M
- Namespace type: BLK
- mapping:

  | DIMM | start | size | position |
  |------+-------+------+----------|
  |    0 |     0 | 32M  |        0 |
  |------+-------+------+----------|

### Region 3
- size: 32M
- Namespace type: BLK
- mapping:

  | DIMM | start | size | position |
  |------+-------+------+----------|
  |    1 |     0 | 32M  |        0 |
  |------+-------+------+----------|

### Region 4
- size: 32M
- Namespace type: BLK
- mapping:

  | DIMM | start | size | position |
  |------+-------+------+----------|
  |    2 |     0 | 32M  |        0 |
  |------+-------+------+----------|

### Region 5
- size: 32M
- Namespace type: BLK
- mapping:

  | DIMM | start | size | position |
  |------+-------+------+----------+
  |    3 |     0 | 32M  |        0 |
  |------+-------+------+----------+

### Region 6
- size: 32M
- Namespace type: IO
- mapping:

  | DIMM | start | size | position |
  |------+-------+------+----------|
  |    4 |     0 | 32M  |        0 |

### Region 7
- size: 4M
- Namespace type: IO
- mapping:

  | DIMM | start | size | position |
  |------+-------+------+----------|
  |    5 |     0 |    0 |        0 |
