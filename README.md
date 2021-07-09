# CANBus_SaleaeLogic_Analyzer
Sniffing CAN Bus with Saleae Logic Analyzer


## Getting Started
In this repository, I will talk about how to use the Sealea Logic analyzer for sniffing CAN Bus.

## The Wiring
The Saleee logic analyzer doesn't support working with differential busses like CAN bus, so we have to wire a CAN bus transceiver with it in order to convert the bus to single ended, here is the wiring diagram:

<img src="./Pictures/CAN_bus_Transceiver.jpg" width="881" height="446">

Examples for CAN transceiver modules:

* NXP TJA1051
* Microchip MCP2551
* Microchip MCP2542

| CAN Bus Transceiver Module  | Connected To |
| ------------- | ------------- |
| VCC  | External Power Supply 5V |
| GND  | GND |
| CTX  | Not Connected |
| CRX  | Connect to any Saleae Logic's digital pin |
| CANH  | Connect CANH to the CAN Bus to be sniffed |
| CANL  | Connect CANL to the CAN Bus to be sniffed |
| S  | Not Connected |
| NC | Not Connected |



## Configuring Saleae Logic Software
After configuring the connection, we will need to open our logic analyzer's software, I will use [Logic 1.2.18](https://downloads.saleae.com/logic/1.2.18/Logic+Setup+1.2.18.exe) for example.

After opening the software, you will see this picture for the program.

<img src="./Pictures/Saleae_Logic_Software.jpg" width="881" height="446">

On the right hand side you will se a small pannel called "Analyzers"

<img src="./Pictures/Analyzers_Panel.jpg" width="243" height="212">

Click the "+" button on this panel, a menu will show like this:

<img src="./Pictures/Analyzers_Menu_UnExpanded.jpg" width="152" height="117">

Choose "Show more analyzers", the menu will be expanded. Choose "CAN"

<img src="./Pictures/Analyzers_Menu_Expanded.jpg" width="151" height="558">

A small screen will show like this

<img src="./Pictures/CAN_Analyzer_Settings.jpg" width="450" height="169">


| Analyzer Settings  | Value |
| ------------- | ------------- |
| CAN  | Choose the channel that will be connected to the CAN bus transceiver's Rx pin  |
| Bit Rate (Bits/s)  | Choose the bit rate of the CAN bus |
| Inverted (CAN High)  | Leave this unchecked |

Press save.

Now we will set the triggering settings for the CAN's pin, it simply keeps the program waiting until it find the "Falling edge of the signal", then it samples the signal and recording it for a certain ammount of time. Click on the triggering icon on the channel and choose "Trigger on Falling Edge".

<img src="./Pictures/Select_Triggering.jpg" width="649" height="424">

Now we will need to set the record time ( Choose the required duration of your recorded data ), I have choosed 5 Seconds.
<img src="./Pictures/Record_Data_For.jpg" width="835" height="421">

Now press the "Start" button on the left, the following window will show, it tells you that the program will wait until it finds any "Falling Edge on the Bus", that means if any data is found on the bus at any time it will trigger the  program to record for 5 Seconds.

<img src="./Pictures/Waiting_For_Trigger.jpg" width="300" height="207">

when the program finds any data on the CAN bus, the window will tell you that its sampling now and the data will be showen.

<img src="./Pictures/Sampling_The_Data.jpg" width="300" height="207">

Now after the sampling period is ended, the data will be shown on the program like this.

<img src="./Pictures/Sampled_Data.jpg" width="1000" height="800">

Happy Reverse Engineering :upside_down_face::joy:.


## Support Me
If you seen my work and it helped you, please support me on LinkedIn by endorsing my skills. It will be appreciated :grinning:.
<p>
  <a href="https://www.linkedin.com/in/omar-mekkawy/" rel="nofollow noreferrer">
    <img src="https://img.shields.io/badge/linkedin%20-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white"  height="40" width="90" alt="linkedin">
  </a> &nbsp;
</p>
