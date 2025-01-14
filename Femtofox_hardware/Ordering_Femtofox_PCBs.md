## Femtofox - Ordering PCBs

This page gives information on how to order PCBs for the Femtofox Community Edition (CE). This guide is written around the JLCPCB process, although many other PCB makers exist and may be preferable to you based on price, options, and manufacturing and shipping times.

### Selecting the right files
Please bear in mind that although the PCB is essentially the same, the parts list (BOM) and associated Pick and Place file will differ based on your choice.
The PCB comes in 3 variants based on the radio module being used - Ebyte E22-900M30S (a 30db, 5V module), Ebyte E22-900M22S (a 22db 3.3V module), or the Seeed WIO SX1262 (an alternative 22db 3.3v module).
If you only require the bare PCB, or you intend to fit your own radio to a part-assembled board then either of the 22db radio boards will do.

### Ordering the PCBs

 1. Select the [release files](tbc) that suit your requirements. 
 2. Upload the Gerber file (which is bundled as a .zip file and does not require extraction) to the quote engine of the site.
 3. Select additional options, such as surface finish, and removal of any order number information. The specific recommended options are as follows:
 - Lead-free HASL finish
 - 1.6mm thick PCB
 - Removal of order number marks (there is no anchor information provided in the Gerber files to limit where it is placed)
4. Select the PCB assembly option
5. Upload the BOM file and Pick & Place file to the relevant boxes on the next page.
6. Check which parts you actually require, and those that are in stock. If an item is no longer available, it is worth reviewing the specs for the original part and finding an alternative. Pay special care that replacement connectors such as JST-PA (2.0mm) are used where they are called for. The following items require specific attention:
 - D1 and D1A are alternative parts. D1 is a 5V uni-directional TVS diode, and D1A is a 7V bidirectional TVS diode. D1 will provide some voltage limiting if the input exceeds 5V, but D1A was (at the time of release) a "basic" part, and therefore much cheaper whilst still providing ESD protection.
 - If neither D1 nor D1A is required, then D2 and D3 may be used to provide ESD and some over-voltage protection. If 
 - PHR1/PHL1 and SHR1/SHL1 are pin headers and socket headers respectively. They cannot be soldered at the same time, so pick one.
 - 
 - 2.54mm pin headers for UART2, UART4 and I2C are offered as an option, or 2.00mm pin headers are available in the same physical space.
8. Check the 2D and 3D renders of the board to check that all modules are in the correct locations.
9. Submit the design using a suitable origin code, and complete the ordering process.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMjg3NDYyMzgwLDkwMTkxMjkwNSw5MzI2Mz
kwNTQsLTY4MTE2MTIyNSwtMjEzNDUzMjcwOV19
-->