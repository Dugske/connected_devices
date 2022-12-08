# Connecting a PLC with zigbie and external I/O's using Home assistant using Modbus TCP/IP + Modbus Serial

>Please keep in mind that I am still working on the project, and this wont be filled fully at the start

***

## Requirements:
* PLC, with ethernet + RS485
* External IO, with ethernet
* raspberry pi pico

> You don't have to use all these things, since my project links a lot of different devices, you could just connect two with homeassistant

> I used: 
>* [PLC: Vision 280](https://www.unitronicsplc.com/vision-series-vision280/)
>* [IO with ethernet: ADAM-5000/TCP](https://www.advantech.com/en/products/38d14508-c3eb-43f8-ab8f-a0dd5f2f7708/adam-5000-tcp/mod_7d8ea69c-0ac7-4ff6-a27e-ed2af71ed7e6)
>* [a raspberrpy pi pico](https://www.raspberrypi.com/products/raspberry-pi-pico/)