---
weight: 116
title: "Motors"
description: ""
icon: "article"
date: "2023-11-30T17:23:04-05:00"
lastmod: "2023-11-30T17:23:04-05:00"
draft: false
toc: true
---

needed for [PID](https://www.youtube.com/watch?v=wkfEZmsQqiA)

```cpp
#include "rm_pico_dev/src/algorithms/smooth_pid.hpp"
```

Get drivers object (controls basically everything)

```cpp
pico::Drivers *drivers = new pico::Drivers();
```

creates motor object

```cpp
pico::motor::DjiMotor motor_one = pico::motor::DjiMotor(drivers, pico::motor::MotorId::MOTOR1, pico::can::PioNum::CAN_BUS0, true, "ID1", 0, 0);
```

initialize [PID](https://www.youtube.com/watch?v=wkfEZmsQqiA) algorithm

```cpp
static pico::algorithms::SmoothPidConfig pid_conf_dt = {20, 0, 0, 0, 8000, 1, 0, 1, 0, 0, 0};
pico::algorithms::SmoothPid pidController = pico::algorithms::SmoothPid(pid_conf_dt);
```

initialize CanBus to send motor information

```cpp
drivers->can.initialize();
```

adds motor_one to `motorHandler` class

```cpp
motor_one.initialize();

```

checks to see if a message is waiting

```cpp
drivers->motorHandler.pollCanData(); 
```

do the pid algorithm

```cpp
pidController.runControllerDerivateError(0 - motor_one.getShaftRPM(), 1);
```

set up msg so its ready to be sent

```cpp
motor_one.setDesiredOutput(static_cast<int32_t>(pidController.getOutput()));
```

send all msg to the motors

```cpp
drivers->motorHandler.encodeAndSendCanData();
```

### Code

```cpp
#include <iostream>
#include <drivers.h>
#include "pico/stdlib.h"
#include "rm_pico_dev/src/algorithms/smooth_pid.hpp"

int main(int argc, char const *argv[])
{
    pico::Drivers *drivers = new pico::Drivers();

    stdio_init_all();

    //init motor object
    pico::motor::DjiMotor motor_one = pico::motor::DjiMotor(drivers, pico::motor::MotorId::MOTOR1, pico::can::PioNum::CAN_BUS0, true, "ID1", 0, 0);

    // init PID algorithm
    // PID explained: https://www.youtube.com/watch?v=wkfEZmsQqiA
    static pico::algorithms::SmoothPidConfig pid_conf_dt = {20, 0, 0, 0, 8000, 1, 0, 1, 0, 0, 0};
    pico::algorithms::SmoothPid pidController = pico::algorithms::SmoothPid(pid_conf_dt);

    // init CanBus to send motor information
    drivers->can.initialize();

    //init motor
    motor_one.initialize();

    while (1)
    {
        std::cout << "=============" << std::endl;
        sleep_ms(1050);

        std::cout << "poll" << std::endl;
        // checks to see if a msg is waiting
        drivers->motorHandler.pollCanData(); 

        std::cout << "pid" << std::endl;
        // do the pid algorithm 
        // PID explained: https://www.youtube.com/watch?v=wkfEZmsQqiA
        pidController.runControllerDerivateError(0 - motor_one.getShaftRPM(), 1);

        std::cout << "set output" << std::endl;
        // set up msg so its ready to be sent
        motor_one.setDesiredOutput(static_cast<int32_t>(pidController.getOutput()));

        std::cout << "send data" << std::endl;
        // send all msg to the motors
        drivers->motorHandler.encodeAndSendCanData();
    }
}
```
