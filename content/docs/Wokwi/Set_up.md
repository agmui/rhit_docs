---
weight: 999
title: "Set_up"
description: ""
icon: "article"
date: "2023-12-01T01:46:57-05:00"
lastmod: "2023-12-01T01:46:57-05:00"
draft: false
toc: true
---


### Step1

press `CTRL + SHIFT + P` and type `Wokwi: Request a new License`
![wokwi license](images/wokwi_license.png)

its going to ask to open a webpage  
![wokwi trust open webpage](images/wokwi_license_open.png)

click get you license and make an account  
![wokwi get license](images/wokwi_get_license.png)

this should pop up when it works  
![wokwi got license](images/license_worked.png)

### Step2

do `Ctrl + SHIFT + P` again  
type `Wokwi: Start Simulator and Wait for Debugger`
![wokwi debugging](images/wokwi_debug_prompt.png)  

<details>
<summary>Select a Kit?</summary>

if it asks to select kit  
choose arm as kit  
![selecting kit for wokwi debug](images/wokwi_select_kit.png)

</details>  

### Step3

Next select the right debugger and run  
![debug setup](images/wokwi_debug_setup.png)

then open up `main.cpp` to add breakpoints

to set up any wiring go here and copy the `diagram.json` when done [pico wokwi](https://wokwi.com/projects/new/pi-pico)

> **NOTE:** `pico_enable_stdio_uart(${PROJECT_NAME} 1)` has to be on to get output

