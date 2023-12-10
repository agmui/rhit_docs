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

Get drivers object (controls basically everything)

```cpp
pico::Drivers *drivers = new pico::Drivers();
```

allows for printing

```cpp
stdio_init_all();
```

init remote class

```cpp
drivers->remote.initialize();
```

prints "....." while waiting for controller to connect

```cpp
    std::cout << "." << std::endl;
```

Reading the remote before we check if it is connected yet or not.

```cpp
    drivers->remote.read();
```

Returns true if connected

```cpp
    drivers->remote.isConnected()
```

get value of left horizontal "joystick"
```cpp
float remoteValue = drivers->remote.getChannel(pico::communication::serial::Remote::Channel::LEFT_HORIZONTAL);
```

prints value 

```cpp
        std::cout << "remote: " << drivers->remote.getChannel(pico::communication::serial::Remote::Channel::LEFT_HORIZONTAL) << std::endl;
```

### Code:
```cpp
#include <iostream>
#include <drivers.h>
#include "pico/stdlib.h"

int main(int argc, char const *argv[])
{
    //get drivers(controls basically everything)
    pico::Drivers *drivers = new pico::Drivers();

    stdio_init_all();

    // init remote
    drivers->remote.initialize();
    while (1)
    {
        std::cout << "." << std::endl;
        drivers->remote.read(); // Reading the remote before we check if it is connected yet or not.
        if (drivers->remote.isConnected())
        {
            // get remote value
            float remoteValue = drivers->remote.getChannel(pico::communication::serial::Remote::Channel::LEFT_HORIZONTAL);
            // print out value
            std::cout << "remote: " << remoteValue << std::endl;
        }
    }
}

```
