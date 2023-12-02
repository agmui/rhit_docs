---
weight: 100
title: "Basic_CLI"
description: ""
icon: "article"
date: "2023-11-30T17:37:55-05:00"
lastmod: "2023-11-30T17:37:55-05:00"
draft: false
toc: true
---


```cpp
#include <iostream>
#include <drivers.h>
#include <stdio.h>
#include "pico/stdlib.h"
#include <Command.h>


int main()
{
    stdio_init_all();

    for (int i = 0; i < 5; i++)
    {
        sleep_ms(1000);
        printf("%d,", 5 - i);
        if(getchar_timeout_us(100)!=-1) break;
    }

    pico::Drivers *drivers = new pico::Drivers();
    // pico::Drivers *drivers = pico::Drivers::getDrivers();

    gpio_init(25);
    gpio_set_dir(25, GPIO_OUT);


    while (1)
    {
        // waits like 1ms for cmd to come in
        // if nothing it continues
        drivers->debug.runNextCommand();
        // prevent the pico from turning into a 1 use smoke machine
        tight_loop_contents(); 
    }
}

```