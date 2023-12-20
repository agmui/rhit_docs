---
weight: 112
title: "Hello World"
description: ""
icon: "article"
date: "2023-11-30T17:22:34-05:00"
lastmod: "2023-11-30T17:22:34-05:00"
draft: false
toc: true
---

imports all the libraries that will be used
```cpp
#include <iostream>
#include <stdio.h>
#include "pico/stdlib.h" // the pico-sdk lib
```

Sets up the pico to be able to print
```cpp
stdio_init_all();
```
2 ways of Printing Hello world
```cpp
std::cout << "hello world" << std::endl; // c++ style print
printf("hello world\n");//c style print 
```

#### Code:

```cpp
#include <iostream>
#include <stdio.h>
#include "pico/stdlib.h" // the pico-sdk lib


int main(int argc, char const *argv[])
{
    stdio_init_all();// allows printing to terminal

    while (1)
    {
        //print hello world
        std::cout << "hello world" << std::endl;
        printf("hello world\n");
    }
}
```
{{< alert context="info" text="to upload to the pico press `ctrl+shift+B`" />}}

TODO: talk about Wokwi

## Common issues:
- **[build failed](docs/getting_started/#uploading)**  
![no_kit](images/did_not_init_kit.png)  


- **[Why do I see no output? ](docs/getting_started/#step2)**
