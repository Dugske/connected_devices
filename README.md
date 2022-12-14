# Connecting a PLC with zigbie and external I/O's using Home assistant using Modbus TCP/IP + Modbus Serial


<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#requirements">Requirements</a></li>
        <li><a href="#products-i-used">Products I used</a></li>
      </ul>
    </li>
    <li>
      <a href="#setup">Setup</a>
      <ul>
        <li><a href="#setup-a-server">Server</a></li>
        <li><a href="#setup-zigbie-devices">Zigbie devices</a></li>
        <li><a href="#setup-eq3-max">EQ3 Max!</a></li>
        <li><a href="#setup-a-visiologic-plc">PLC</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

***
<br/>

## About the project:
I made this project as a school task. Ive spent time on it, but I won't get maintained, this project also is not finished yet, neither is the documentation


***

<br/>

## Getting started:
### Requirements:
* Router
* Server/ device to run homeassistant on
* PLC, with ethernet +/ RS485 *
* External IO, with ethernet *
* raspberry pi pico *
* Zigbie gateway *
* Zigbie devices *


> *(You don't have to use all these things, since my project 
links a lot of different devices, you could just connect two with homeassistant)

<br/>

### Products I used: 
>* [Router](https://www.tp-link.com/nl-be/home-networking/wifi-router/archer-c7/#overview)
>* [PLC: Vision 280](https://www.unitronicsplc.com/vision-series-vision280/)
>* [IO with ethernet: ADAM-5000/TCP](https://www.advantech.com/en/products/38d14508-c3eb-43f8-ab8f-a0dd5f2f7708/adam-5000-tcp/mod_7d8ea69c-0ac7-4ff6-a27e-ed2af71ed7e6)
>* [Raspberrpy pi zero2-w](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/)
>* [Zigbie gateway](https://www.lidl.be/p/nl-BE/silvercrest-gateway-smart-home/p100337892)
>* [Zigbie light](https://www.lidl.be/p/nl-BE/livarno-home-ledsfeerverlichting-smart-home/p100339626)
>* [Zigbie temperature sensor](https://nl.aliexpress.com/item/1005004989301439.html?spm=a2g0o.productlist.0.0.1d1a3b52rA5ArW&algo_pvid=98185350-5d22-47a1-9b5e-60ed13fc394d&algo_exp_id=98185350-5d22-47a1-9b5e-60ed13fc394d-30&pdp_ext_f=%7B"sku_id"%3A"12000031257188069"%7D&pdp_npi=2%40dis%21EUR%2128.52%218.56%21%21%21%21%21%40210318cb16695978022277448e6557%2112000031257188069%21sea&curPageLogUid=mpVm6jEhZCH5)
>* [Zigbie radiator valve](https://nl.aliexpress.com/item/1005004876742600.html?spm=a2g0o.productlist.0.0.1d1a3b52rA5ArW&algo_pvid=98185350-5d22-47a1-9b5e-60ed13fc394d&aem_p4p_detail=20221127171002209668958601040006196055&algo_exp_id=98185350-5d22-47a1-9b5e-60ed13fc394d-29&pdp_ext_f=%7B"sku_id"%3A"12000030857327420"%7D&pdp_npi=2%40dis%21EUR%21165.01%21123.76%21%21%21%21%21%40210318cb16695978022277448e6557%2112000030857327420%21sea&curPageLogUid=Rn7QdzVjQ0Oy&ad_pvid=20221127171002209668958601040006196055_6&ad_pvid=20221127171002209668958601040006196055_6)
>* [Server: PineA64](https://www.pine64.eu/shop/bundles.html)
>* Server: Simple desktop pc Windows

***

## Setup:

1.  Connect your router to the internet, and your server device using an ethernet cable.


2. ### Setup a server
    <details>
        <summary></summary>
    <br/>

    > For a <a href="#desktop">desktop server</a>, for a <a href="#pinecone">pinecone A64</a>.


    * ### Desktop:
        * > This will explain how I did it, you can use another installer, but I used a windows PC

        1. Install Home asistant using [this](https://www.home-assistant.io/installation/windows) link on your server. I used the Virtual box version.

        2. Proceed when you have gotten home assistant running

    * ### Pinecone:
        * WIP

    </details>

* ### Setup Zigbie devices
    <details>
        <summary></summary>

    1. Connect zigbie gateway to the router

    1. Install the Tuya smart home app, and add your devices in there

    2. Follow [this](https://www.home-assistant.io/integrations/tuya/) tutorial to setup tuya with homeassistant

    3. After restarting home assistant you should be able to enable/ disable/ do other stuff with your zigbie devices.
    </details>


* ### Setup EQ3 Max!
    1. Follow [this](https://www.home-assistant.io/integrations/maxcube/) tutorial to setup the EQ3 max!

* ### Setup a (visiologic) plc.
    <details>
        <summary></summary>
        <p>First in the project settings add these settings: </p>
        <img src="images/IP-Project-Settings.png" alt="IP Address: 192.168.0.28, Protocol: TCP, Port Number: 20256, PLC Name: PLC Name"/>
    <blockquote> You can use your own IP address and a custom name </blockquote>
    
    [Here](steps_pdf/VisioLogicModbusSetupProjectSteps.pdf) are the steps recorded.

    <hr></hr>

    This is the code I used to setup the PLC:
    ![](images/imagesFull-PLC-Code.png)

    <details>
        <summary>Settings</summary>

    The card init settings are these:
        ![](images/PLC-Code-Card-Init.png)

    The socket 1 settings are these:
    ![](images/PLC-Code-Socket-1.png)

    The socket 2 settings are these:
    ![](images/PLC-Code-Socket-2.png)

    The socket 3 settings are these:
    ![](images/PLC-Code-Socket-3.png)
    </details>

    [Here](steps_pdf/VisioLogicModbusSetupCodeSteps.pdf) are the steps recorded.

    </details>
    
* ### Setup external ethernet I/O (ADAM 5000)
    <details>
        <summary></summary>
    </details>

    * Connect the external I/O to the router

    * Connect your laptop to the router (via ethernet)

    * [Download](https://www.advantech.com/en/support/details/utility?id=1-2AKUDB) the most recent version.

    * Open the ADAM/APAX utility software, and press the searchglass.
    
    * Let it search the network

    * When it finds the device, you can select it, go to the network tab and you can change/ see the IP address.

    [Here](steps_pdf/AdvantechSetupSteps.pdf) are the steps recorded.

    * Now in homeassistant add the file editor plugin and change the `configuration.yaml`, we will be adding mobus lines there! You can use [this](https://www.home-assistant.io/integrations/modbus/) to find more info about the below commands!

    ### The code:

    ```
    modbus:
      - name: NAME
      close_comm_on_error: true
      type: tcp
      host: IP_ADDRESS
      port: 502
    ```

    The slave number is like the key, you start with 1, and with every different thing you check, you add +1

    The address is the place where the sensor is 'stored' in the adam, you can check it using the tool

    ### Reading digital outputs:
    ```
    binary_sensors:
      - name: NAME
        address: 1
        slave: 1
        scan_interval: 20
        unique_id: NAME
    ```
    ### Writing digital inputs:
    ```
    switches:
      - name: NAME
        address: 12
        slave: 2
        write_type: coil
        unique_id: NAME
    ```
    ### Reading analog outputs:
    ```
    sensors:
      - name: NAME
        slave: 3
        address: 43
        input_type: holding       
        state_class: measurement       
        count: 1       
        scale: 1       
        offset: 0       
        precision: 1       
        data_type: int16
        unique_id: NAME
    ```