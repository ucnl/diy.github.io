
| ![logo](https://ucnl.github.io/documentation/sm_logo.png) | ![pic](uSwitch_TX.png) |
| :---: | ---: |
| [www.unavlab.com](https://www.unavlab.com/) <br/> [support@unavlab.com](mailto:support@unavlab.com) | **uSwitch** - a hydroacoustic remote control system <br/> Data brief |

# **uSwitch** - A hydroacoustic remote control system <br/> Data brief

<div style="page-break-after: always;"></div>

## 0. Motivation
We develop a wide range of professional hydroacoustic communication and navigation equipment using the most advanced technologies in our field. Such equipment is very difficult (and very expensive!) to develop and test, which naturally affects its availability to a wide range of consumers.
At the same time, we believe that the availability of technology, especially for new generations of researchers and engineers, is extremely important. That is why we are moving towards the popularization of hydroacoustics, and we hope that **uSwitch** will become one of those projects that will allow a large number of enthusiasts and fans to _dive_ into the world of underwater communications. After all, most of the world's oceans have not yet been explored!

## 1. Operating principle
[uSwitch TX](uSwitch_TX_Specification_en) and [uSwitch RX](uSwitch_RX_Specification_en) are two small printed circuit boards (modules): transmitter and receiver. With the help of them, you can transmit up to **8** different **control signals** through the water column, at a distance of **up to 300 meters**.

Working with the modules is extremely simple: just connect the hydroacoustic antennas and turn on the power.
Each of the modules has pins **STROBE**, **BIT 0**, **BIT 1** and **BIT 2**. In the _transmitter_ these are _digital inputs_, and in the _receiver_ they are _digital outputs_.
By default, all of these pins on both the receiver and transmitter are set to digital one (3.3 Volts).

The transmitted code is formed by the state of the contacts (pins) **BIT 0**, **BIT 1** and **BIT 2**, and the transfer occurs when the state of the pin **STROBE** changes from the state of a digital one to the state of digital zero.

On the receiving side, the received code causes a change in pins **BIT 0**, **BIT 1** and **BIT 2**, and the fact of reception - by the transition of pin **STROBE** to the state of digital zero.

Since there are three _information_ pins (**BIT 0**, **BIT 1** and **BIT 2**) and each can have two digital states, 8 different codes can be transmitted in total.

Moreover, the transmitter board can act as a pinger of the tracking system [WAYU](https://docs.unavlab.com/navigation_and_tracking_systems_ru.html#wayu), thus providing the ability to get not only an acknowledgement that a command has been received but also to determine the geographic coordinates of the vessel while submerged.
This function is activated by pin **W_PING**. When the state of the **W_PING** pin changes to active, the transmitter module emits a signal that can be received by navigation [buoys](https://docs.unavlab.com/documentation/RU/RWLT/RWLT_GIB_Specification_ru.html) of the [WAYU](https://docs.unavlab.com/navigation_and_tracking_systems_ru.html#wayu) system.

This architecture allows using the **uSwitch** modules both with various platforms like **Arduino**, and with simple elements such as buttons, LEDs, relays and others, controlled by TTL levels.

## 2. Using modules

Figures 1 and 2 show the connection diagrams.

Both modules are powered from a DC source with a voltage of 5 to 15 volts, which allows using both PC **USB port**, **Power bank**, **lead-acid** 12-volt batteries, assemblies based on **Li-Ion** batteries and usual 9-V "transistor" type batteries to power the modules.

The hydroacoustic transmitting antenna is connected to the **OUT** and **GND** pads located on the right side of the transmitter module PCB.

| |
| :---: |
| ![tx](uSwitch_TX_connection.png) |
| Fig. 1 - [uSwitch TX](uSwitch_TX_Specification_en) wiring diagram |

The hydroacoustic receiving antenna is connected to the **IN** and **GND** pads located on the right side of the receiver module PCB.

| |
| :---: |
| ![rx](uSwitch_RX_connection.png) |
| Fig. 2 - [uSwitch RX](uSwitch_RX_Specification_en) wiring diagram |

On both modules, the same pins are used for interfacing with external devices, on the transmitter these are digital inputs pulled to one, and on the receiver, they are digital outputs with an open collector.
The active state of the transmitter inputs is digital zero.
For ease of connection, the bottom of the connector is connected to the ground.

To transmit one of the four codes, using pins **3**, **5** and **7** (**BIT 0**, **BIT 1** and **BIT 2**, respectively) the transmitted code is formed. The correspondence of the code number and the state of the pins is shown in table 1.

When the code is received by the receiver module, it, using pins **3**, **5** and **7* (**BIT 0**, **BIT 1** and **BIT 2**, respectively) forms the received code and translates pin **1** (**STROBE**) to digital zero for 100 milliseconds. Thus, the system connected to it should read the state of pins **3**, **5** and **7** after the transition of pin **1** to the state of digital zero.

#### Table 1 - Correspondence of the state of pins and transmitted/received codes

| **BIT 0** (pin 3) | **BIT 1** (pin 5) | **BIT 2** (pin 7) | Transmitted code |
| :---: | :---: | :---: | :---: |
| 0 | 0 | 0 | 0 | 
| 1 | 0 | 0 | 1 |
| 0 | 1 | 0 | 2 |
| 1 | 1 | 0 | 3 |
| 0 | 0 | 1 | 4 |
| 1 | 0 | 1 | 5 |
| 0 | 1 | 1 | 6 |
| 1 | 1 | 1 | 7 |

After the formation of the transmitted code, for its transmission via the hydroacoustic channel, pin **1** (**STROBE**) must be set to digital zero for a time of at least 100 milliseconds. The retransmission can be performed no earlier than 500 milliseconds after the beginning of the previous one.

The timing diagram of interaction with modules is shown in Figure 3:

| |
| :---: |
| ![tx/rx time chart](uSwitch_txrx_diagram.png) |
| FIg. 3 - The timing diagram of interaction with modules |

In the [WAYU](https://docs.unavlab.com/navigation_and_tracking_systems_ru.html#wayu) pinger mode the minimal time between two pings is 2 secinds (2000 milliseconds).

## 3. Hydroacoustic antennas
The [transmitter module](uSwitch_TX_Specification_en) is designed to work with the antenna [RT-1.332820-1](https://docs.unavlab.com/documentation/EN/Transducers/RT_1_332820_1_Specification_en.html), and to the [receiver module](uSwitch_RX_Specification_en) you can connect almost any piezoceramic hydroacoustic antenna, for example, an inexpensive [RT-1.d23h03-1](/products/Transducers/RT_1_d23h03_1_ru) based on a disk piezoelectric element.
If you wish, you can make it yourself using [our instructions](/projects/disk_hydrophone/README_EN.html).

## 4. Limitations
### 4.1. Limitations from the side of sound propagation in water
The hydroacoustic communication channel is one of the most difficult to transmit information, therefore, the following conditions must be borne in mind for the operation of any hydroacoustic communication system:
- you always need a "line of sight" to work. This means that there should be no obstacles in the path of the acoustic signal between the transmitter and receiver: elements of the underwater landscape, dense thickets of algae, infrastructure elements (for example, vessels with low draft, bridge supports, quay walls, etc.).
- antennas of both the receiver and the transmitter should be at a sufficient depth, at least 1-1.5 meters in large bodies of water.
- strong noisiness in water bodies (for example, due to active navigation or some natural factors) can also significantly affect the quality of communication and the maximum range of operation of hydroacoustic systems.

### 4.2. Architecture limitations
We tried to make the most affordable and most functional devices, in some ways we had to compromise. Because different codes are transmitted by sequentially transmitted tone bursts, then the reliability of the codes is not the same and decreases with increasing code. If you need to use less than four codes, then you should give preference to lower codes.

## 5. Warning
**Piezoceramic hydroacoustic antennas are designed in such a way that the pressure they develop strongly depends on the voltage applied to them, therefore, a life-threatening high voltage arises in the transmitter module at the time of signal emission, the amplitude of which reaches 200 volts. Take all required protective measures: while the transmitter is operating, never touch the board and the hydroacoustic antenna connection with your hands or any other parts of your body !!!**

## 6. FAQ
**Q**: *Is there a limit on the number of receivers working with one transmitter?*  
**A**: **There are no such restrictions: all devices operate in a common frequency band. Any number of receivers will receive the signal from the transmitter, provided that it reaches them. However, given the speed of sound in water (about 1500 m/s), this can happen at different times, with a delay proportional to the range.**  

**Q**: *Is it possible to work on one reservoir with several sets of the system?*  
**A**: **It should be borne in mind that all devices operate in a common range and any receiver will respond to any transmitter if the signal reaches it. The user will have to independently ensure the separation of signals in time.**  

**Q**: *Can the receiver distinguish between signals from different transmitters?*  
**A**: **No. This option is not provided.**  

**Q**: *Why is there such a difference in ranges when using antennas [RT-1.332820-1](https://docs.unavlab.com/documentation/EN/Transducers/RT_1_332820_1_Specification_en.html) and [RT-1.d23h03 -1](/products/Transducers/RT_1_d23h03_1_en) as transmitters, 300 meters versus 40?*  
**A**: **In simple terms, the transmission range is determined by the sensitivity of the receiver and the pressure developed by the transmitting antenna. A flat and inexpensive antenna does not allow the required power to be pumped into it.**  
