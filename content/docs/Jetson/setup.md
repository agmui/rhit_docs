---
weight: 999
title: "uart coms"
description: ""
icon: "article"
date: "2024-03-15T22:38:47-04:00"
lastmod: "2024-03-15T22:38:47-04:00"
draft: true
toc: true
---

make sure you are installing everything with sudo

`sudo pip install pyserial`

uart.py 
```python
import serial

#ser = serial.Serial("/dev/ttyAMC0",115200,timeout =1)
ser = serial.Serial("/dev/ttyTHS0",115200,timeout =1)
try:
    ser.open()
    print("port has been opened")
except Exception:
    print("err")
    exit()

while(True):
    ser.write("pilk\n\0".encode())
    print("send pilk")

```

to run:
`sudo python3 uart.py`
