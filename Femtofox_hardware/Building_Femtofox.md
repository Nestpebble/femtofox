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


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0Mzc1OTc1MjgsMjYyMDIzOThdfQ==
-->