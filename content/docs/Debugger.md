---
weight: 200
title: "Debugger"
description: ""
icon: "pest_control"
date: "2023-12-02T00:59:56-05:00"
lastmod: "2023-12-02T00:59:56-05:00"
draft: false
toc: true
---

Wire up two picos like this  
![picoprobe wiring](pic/../images/picoprobe_wiring.png)

upload this file
[pico-debug.uf2](https://github.com/essele/pico_debug/releases/tag/v0.3)
to the left pico in the picture using any method from [above](#uploading)

Next select the right debugger and run  
![pico debug](images/pico_debug.png)

You can also open serial monitor if you want bc uart is passed through

> side note: I don't use picoprobe or openocd. I use this for those who care
[pico_debug](https://github.com/essele/pico_debug/tree/v0.3)

### Don't have a second pico?

Just upload this file:
[pico-debug-gimmecache.uf2](https://github.com/majbthrd/pico-debug/releases/download/v10.05/pico-debug-gimmecache.uf2)

Then choose Duo_Core_Debug  
![duo core debug pic](images/duo_core_debug.png)

github: [pico-debug](https://github.com/majbthrd/pico-debug)

### NOTE!!!  HAVING `stdio_init_all()` IN YOUR CODE WILL CRASH THIS DEBUGGER