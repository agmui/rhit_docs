---
weight: 999
title: "Retroterm"
description: ""
icon: "article"
date: "2023-11-30T17:38:28-05:00"
lastmod: "2023-11-30T17:38:28-05:00"
draft: false
toc: true
---

currently only works well with Putty  
screen, minicom, and serial terminal have mixed results

```cpp
#include <stdio.h>
#include <iostream>
#include "pico/stdlib.h"
// #include <retroTerm.h>

#include "rm_pico_dev/src/Debug/UI_tests/terminalTest.cpp"
// #include "widgetTest.cpp"

uint8_t widgetId = 0; //Record the widget ID globally
uint32_t numberOfClicks = 1; // Record the number of clicks

int main()
{
    stdio_init_all();

    for (int i = 0; i < 6; i++)
    {
        sleep_ms(1000);
        printf("%d,", 8 - i);
    }
    setup();

    while (1)
    {
        loop();
    }
    return 0;
}
```