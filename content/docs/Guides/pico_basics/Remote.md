---
weight: 113
title: "Remote"
description: ""
icon: "article"
date: "2023-11-30T17:22:48-05:00"
lastmod: "2023-11-30T17:22:48-05:00"
draft: false
toc: true
---


```cpp
#include <iostream>
#include <drivers.h>
#include <Debug.h>
#include "pico/stdlib.h"

int main(int argc, char const *argv[])
{
    //get drivers(controls basically everything)
    pico::Drivers *drivers = new pico::Drivers(); 
    // pico::Drivers *drivers = pico::Drivers::getDrivers();

    stdio_init_all();
    gpio_init(25);
    gpio_set_dir(25, GPIO_OUT);

    // init remote
    drivers->remote.initialize();
    while (1)
    {
        // Turn On LED
        gpio_put(25, 1); // Set pin 25 to high
        sleep_ms(250);
        printf("LED switched on!\n");
        // Turn Off LED
        gpio_put(25, 0); // Set pin 25 to high.
        sleep_ms(250);
        printf("LED switched off!\n");

        // ====
        std::cout << "." << std::endl;
        drivers->remote.read(); // Reading the remote before we check if it is connected yet or not.
        if (drivers->remote.isConnected())
        {
            // print out value
            std::cout << "remote: " << drivers->remote.getChannel(pico::communication::serial::Remote::Channel::LEFT_HORIZONTAL) << std::endl;
        }
    }
}

```
