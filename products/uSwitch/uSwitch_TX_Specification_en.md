| ![logo](https://ucnl.github.io/documentation/sm_logo.png) | ![pic](uSwitch_TX.png) |
| :---: | ---: |
| [www.unavlab.com](https://www.unavlab.com/) <br/> [support@unavlab.com](mailto:support@unavlab.com) | **uSwitch TX** - Hydroacoustic remote control system (TX module) <br/> Device specifications |

## KEY FEATURES

* **Maximum ease of use and integration**
* **Transmits up to 4 control codes**
* **Communication range up to 300 <sup>[1](#footnote1), [2](#footnote2)</sup> m**
* **Low power consumption (Standby/Tx) 20/500 mA**
* **Compatibility with [WAYU](https://docs.unavlab.com/navigation_and_tracking_systems_en.html#wayu) tracking system (in the next version)**

## DESCRIPTION
The module is made in the form of a printed circuit board to which the hydroacoustic transmitting antenna is connected. The device allows transmitting up to 8 control codes using a hydroacoustic (ultrasonic) signal, which can then be received and transmitted to the user using the [uSwitch RX](uSwitch_RX_Specification_en) receiving module.

The TX and RX modules are specially designed by us for the DIY community, enthusiasts, underwater RC model makers as an affordable underwater telecontrol system.

Transmission control is made as simple as possible and is carried out by three digital inputs on the module board, to which you can connect a control system: a microcontroller, Arduino or similar board, or even an ordinary button.  

<div style="page-break-after: always;"></div>

## TECHNICAL SPECIFICATIONS

| PARAMTER | VALUE |
| :--- | :--- |
| DIMENSIONS (L х W х H) | 46 x 75 х 28 mm |
| MAX. ACOUSTIC RANGE<sup>[1](#footnote1),[2](#footnote2),[5](#footnote5)</sup> | 300 m |
| POWER CONSUMPTION Standby/Tx | 20/500 mA |
| SUPPLY VOLTAGE<sup>[2](#footnote2),[3](#footnote3)</sup> | 5 .. 15 V |
| DATA LINES VOLTAGE<sup>[3](#footnote3)</sup> | 0 .. 5 V |
| BANDWIDTH<sup>[4](#footnote4)</sup> | 21 .. 29 kHz |
| ACOUSTIC SOURCE LEVEL<sup>[2](#footnote2),[5](#footnote5)</sup> | 140 dB re 1 μPa @ 1 m |
| MAX. NUMBER OF CONTROL CODES | 4 |
| MIN. TIME BETWEEN TWO MESSAGES | 500 ms |
| MAX. MESSAGE DURATION | 100 ms |
| MAX. RELATIVE VELOCITY | +/- 2 m/s |
| WORKING TEMPERATURE RANGE | -5 .. 50 °C |
| DIGITAL INPUTS | TTL |

________________
<a name="footnote1"><sup>1</sup></a> A parameter that determines the maximum range at which a signal can be received, based on the electro-acoustic parameters of the transmitter and receiver, the spatial decrease in the intensity of sound energy, attenuation in the medium and the level of hydroacoustic noise.  
<a name="footnote2"><sup>2</sup></a> The maximum output power in the transmission mode, and therefore the maximum communication range, is achieved when the device is powered with a voltage of 15 V.  
<a name="footnote3"><sup>3</sup></a> The specified voltage limits, functionality and serviceability of the module is not guaranteed beyond the specified range.  
<a name="footnote4"><sup>4</sup></a> The module uses narrowband tones located in the specified frequency range.  
<a name="footnote5"><sup>5</sup></a> The module is optimized for working with [RT-1.332820-1](https://docs.unavlab.com/documentation/EN/Transducers/RT_1_332820_1_Specification_en.html) antenna and the maximum range was determined experimentally with this antenna, when working with other piezoceramic antennas, the range can differ significantly.  
 
