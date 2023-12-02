---
weight: 100
title: "Drivers_class"
description: ""
icon: "article"
date: "2023-11-30T17:26:06-05:00"
lastmod: "2023-11-30T17:26:06-05:00"
draft: false
toc: true
---

The library is a port from [taproot](https://github.com/uw-advanced-robotics/taproot)
to work on the pico.

### drivers

The drivers class is a [singleton](https://refactoring.guru/design-patterns/singleton)
and has everything. If you need to do any library operation it is General through the
drivers object.
ex:

```cpp
drivers->remote.isConnected();
drivers->motorHandler.pollCanData(); 
...
```

see the [examples](#examples) to learn more.