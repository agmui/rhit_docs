---
weight: 100
title: "Basic_io"
description: ""
icon: "article"
date: "2023-11-30T17:39:00-05:00"
lastmod: "2023-11-30T17:39:00-05:00"
draft: false
toc: true
---

From here on its recommend you don't mess with the pico-sdk because it may mess with the
rm_pico_dev. So only use its functions if you need to.

## basic input output

```cpp
#include <stdio.h>
#include "pico/stdlib.h"

// guide: https://forums.raspberrypi.com/viewtopic.php?t=336230
int main(){
    //Initialise I/O
    stdio_init_all(); 

    // Initialise GPIO (Green LED connected to pin 25)
    gpio_init(25);
    gpio_set_dir(25, GPIO_OUT);

    char userInput;

    //Main Loop 
    while(1){
        //Get User Input
        printf("Command (1 = on or 0 = off):\n");
        userInput = getchar();

        if(userInput == '1'){
            // Turn On LED
            gpio_put(25, 1); // Set pin 25 to high
            printf("LED switched on!\n");
        }
        else if(userInput == '0'){
            // Turn Off LED
            gpio_put(25, 0); // Set pin 25 to high.
            printf("LED switched off!\n");
        }
        else{
            printf("Invalid Input!\n");
        }
    }
}
```