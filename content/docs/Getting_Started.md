---
weight: 001
title: "Getting Started"
description: ""
icon: "rocket_launch"
date: "2023-11-30T17:01:55-05:00"
lastmod: "2023-11-30T17:01:55-05:00"
draft: false
toc: true
---
## Install
{{< tabs tabTotal="4">}}
{{% tab tabName="Windows" %}}

Download and run: [rm-pico-installer](https://github.com/agmui/sample_rm_pico_app/blob/main/windows_install.exe)

It automatically installs all the tools and vscode.

### Zadig install
TODO: add zadig install guide


{{% /tab %}}
{{% tab tabName="WSL" %}}

Follow the linux guide but currently some methods do not work (also ur kinda on ur own hehe)

TODO: make separate guide for vscode section

{{% /tab %}}
{{% tab tabName="MacOS" %}}


TODO: for now just read the [linux_init.sh](https://github.com/agmui/sample_rm_pico_app/blob/main/linux_init.sh)


<details>
<summary>might not work lol</summary>

`brew install libusb pkg-config`

Next install: [vscode](https://code.visualstudio.com/Download)  
</details>


{{% /tab %}}
{{% tab tabName="Linux (ubuntu)" %}}

{{% alert context="danger" %}}
**Warning** do not update recursively
<details>
<summary>why tho?</summary>
There are some submodules that may go on for a while (like tinyusb) and I highly
recommend you don't need to get them.
If you want to see what submodules I update just look in `linux_init.sh`
</details>
{{% /alert %}}


```bash
git clone https://github.com/agmui/sample_rm_pico_app.git
cd sample_rm_pico_app
./linux_init.sh && source ~/.bashrc
```

## Install VScode
[vscode](https://code.visualstudio.com/Download)  

{{% /tab %}}
{{< /tabs >}}


## VScode extensions

Have vscode open this repo
When first opining vscode should ask you to install the plugins  
![install plugins](images/install_plugins.png)

If not just type `@recommended` here  
![recommened](images/recommended.png)

## Uploading

{{< alert context="info" text="Make sure the pico is **pluged in**" />}}

{{< tabs tabTotal="3">}}
{{% tab tabName="Method 1" %}}

#### Step1:  
select kit
![no kit selected button](images/noKitBtn.png)
![selecting arm kit](images/armKit.png)

#### Step2:  
press `CTRL + SHIFT + B`  

#### Step3:
select the usb port the pico is plugged in it should look like this:  
![serial monitor](images/serial_monitor.png)  
then hit **Start Monitoring**

{{% alert context="warning" %}}
<details>
<summary>The pico did not show up?</summary>

- is the pico plugged in!?    
plugin then re press `CTRL + SHIFT + B`


- **(Windows users)** did you install the [Zidag drivers](#zadig-install)
</details>
{{% /alert %}}



{{% /tab %}}
{{% tab tabName="Method 2" %}}


{{< alert context="warning" text="run in project **root**" />}}

Manual build
```bash
mkdir build
cd build
cmake ..
make -j4
picotool load -f pico_app.uf2
```

{{% /tab %}}
{{% tab tabName="Reset pico (If all else fails)" %}}
#### Reset pico
```bash
mkdir build
cd build
cmake ..
make -j4
```

unplug the pico  
Hold the bootsel button on the pico  
![bootsel](images/bootsel.png)  
while still holding the button plug the pico back in

A usb stick should pop up in your file explorer  
TODO: add pic

drag and drop the `pico_app.u2f` file in the build folder
![copying over uf2 file](images/copy_uf2_over.png)


{{% /tab %}}
{{< /tabs >}}


## Running in [Wokwi](https://wokwi.com/) 👀

{{< alert icon="🤯 " text=" **No pico no problem!** We can just **simulate** it: [setup guide](Wokwi/Set_up.md) "/>}}


## Building

{{< tabs tabTotal="2">}}
{{% tab tabName="Method 1" %}}
Just press `f7` **if** you installed all [plugins](#vscode-extensions)

{{% /tab %}}
{{% tab tabName="Method 2" %}}

run:
```bash
mkdir build
cd build
cmake ..
make -j4
```

{{% /tab %}}
{{< /tabs >}}

## I borked my pico
If the pico bricks you **CAN'T** just use `CTRL + SHIFT + B` you have to [reset](#uploading) it or do [Method 2 ](#uploading)

slides install guide: https://docs.google.com/presentation/d/1am9qFasZtjAnBu1M_k-8S4nNLxHHzSmExr1Sa2NGVAE/edit?usp=sharing

### Compiling example folder files TODO: maybe make own page

You can either compile the files in the examples folder or just copy the code form the guides and paste it in main.cpp

## [Get Started coding on the pico Basic C++ tutorial](Guides/pico_basics/C++_basics.md)