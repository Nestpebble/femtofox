## Femtofox - Building from PCBs

This page gives information on how to build the Femtofox  Community Edition (CE) from PCBs. This guide is written around the JLCPCB process, although many other PCB makers exist and may be preferable to you based on price, options, and manufacturing and shipping times.

### Selecting the right parts
When assembling the parts for the Femtofox, there are choices to be made about which TVS diodes are used, which type of header is used, and whether sockets or header pins are provided for the peripheral interfaces.

Check which parts you actually require. The following items require specific attention:
 - D1 and D1A are alternative parts. D1 is a 5V uni-directional TVS diode, and D1A is a 7V bidirectional TVS diode. D1 will provide some voltage limiting if the input exceeds 5V, but D1A was (at the time of release) a "basic" part, and therefore much cheaper whilst still providing ESD protection. If either of these is chosen, D2 and D3 are not required.
 - If neither D1 nor D1A is required, then D2 and D3 may be used to provide ESD and some over-voltage protection.
 - PHR1/PHL1 and SHR1/SHL1 are pin headers and socket headers respectively. They cannot be soldered at the same time, so pick one.
 - Likewise, ETH and ETHS are pins and sockets for the ethernet pads. Choose one only.
 - 2.54mm pin headers for UART2, UART4 and I2C are offered as an option, or 2.00mm pin headers are available in the same physical space. 2.54mm pins are designated with _HDR at the end. Choose one or the other.
 - Choose one of the 30db and 22db versions of the E22 module only.

### Parts list

  

Part number/value

Part description

Designation (PCB, Schematic)

Packaging

AO3400A

N-Mosfet

AO0

SOT-23

AO3401A

P-Mosfet

AO1

SOT-23

100uF

Capacitor

C1

C1206

100nF

Capacitor

C2

C0603

100uF

Capacitor

C3

C1206

100nF

Capacitor

C4

C0603

10nF

Capacitor

C7

C0603

10nF

Capacitor

C8

C0603

B2B-PH-K-S(LF)(SN)

2-pin JST PH connector

CN5V

CONN-TH_B2B-PH-K-S

PESD5V0S2BT

TVS diode

D1

SOT-23

PSM712-LF-T7

TVS diode

D1A

SOT-23

GBLC03CI_C5173269

TVS diode

D2

SOD-323

GBLC05CI-LF-T7

TVS diode

D3

SOD-323

E22-900M22S

LoRa Radio Module

E22-900M22S

SMD module

E22-900M30S

LoRa Radio Module

E22-900M30S

SMD module

HDR-M-2.54_1x5

5-pin header

ETH

HDR-M-2.54_1X5

ZX-PM2.54-1-5PY

5-socket header

ETHS

HDR-TH_5P-P2.54-V-F-B

0603L100/12AR

polyfuse

F1

F0603

B4B-PH-K-R(LF)(SN)

4-pin JST PH connector

I2C_1

CONN-TH_B4B-PH-K-S-LF-SN

B4B-PH-K-R(LF)(SN)

4-pin JST PH connector

I2C_2

CONN-TH_B4B-PH-K-S-LF-SN

HDR2.54-LI-2X4P

4-pin header

I2C_HDR

HDR-TH_4P-P2.54-V-M

HDR2.54-LI-2X4P

4-pin header

I2C_HDR2

HDR-TH_4P-P2.54-V-M

HDR2.54-LI-2X4P

4-pin header

I2C_HDR3

HDR-TH_4P-P2.54-V-M

HR911105A_C12074

RJ45 socket

J4

RJ45-TH_HR911105A

DS1021-1X11SF11-B

11-pin header

PHL1

HDR-TH_11P-P2.54-V-M

DS1021-1X11SF11-B

11-pin header

PHL2

HDR-TH_11P-P2.54-V-M

DS1021-1X11SF11-B

11-pin header

PHR1

HDR-TH_11P-P2.54-V-M

DS1021-1X11SF11-B

11-pin header

PHR2

HDR-TH_11P-P2.54-V-M

AO3401A

P-Mosfet

Q1

SOT-23_L2.9-W1.3-P1.90-LS2.4-BR

100kΩ

Resistor

R1

R0603

100kΩ

Resistor

R2

R0603

KH-2.54FH-1X11P-H8.5

11-socket header

SHL1

HDR-TH_11P-P2.54-V-F-2

KH-2.54FH-1X11P-H8.5

11-socket header

SHR1

HDR-TH_11P-P2.54-V-F-2

B4B-PH-K-R(LF)(SN)

4-pin JST PH connector

UART2

CONN-TH_B4B-PH-K-S-LF-SN

HDR2.54-LI-2X4P

4-pin header

UART2_HDR

HDR-TH_4P-P2.54-V-M

B4B-PH-K-R(LF)(SN)

4-pin JST PH connector

UART4

CONN-TH_B4B-PH-K-S-LF-SN

HDR2.54-LI-2X4P

4-pin header

UART4_HDR

HDR-TH_4P-P2.54-V-M

Seeed-wio-SX1262

LoRa Radio Module

WIO-SX1262

SEEED_WIO_SX1262_NOSILK
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNTU5NTE3NjksLTE0Mzc1OTc1MjgsMj
YyMDIzOThdfQ==
-->