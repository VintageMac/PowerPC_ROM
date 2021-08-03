# PowerPCROM

### Overview

Start | End | Size | Description
--- | --- | --- | ---
0 | 3,145,728 | 3.1 MB | 68K ROM
3,211,264 | 3,240,136 | 28.8 KB | NanoKernel
3,276,800 | 3,452,396 | 175.5 KB | HWInit


### 68K ROM

Start | End | Size | Description
--- | --- | --- | ---
0 | 112 | 112 B | Header
112 | 850,800 | 850.6 KB | Code
850,800 | 3,145,728 | 2.3 MB | Resources





On most systems, the processor starts up in big-endian mode with the exception prefix set to 0xFFF0_0000. This means that upon system reset (exception vector 0x0100), the processor executes code beginning at 0xFFF0_0100.
The code located at the system reset vector must handle system initialization. Exception vectors for the PowerPC are located at increments of 0x0000_0100 from the vector table start address. Since the initialization code must fit between the allocated hard reset exception space between 0xFFF0_0100 and 0xFFF0_01FF, it is customary for the reset code to branch to an address beyond the end of the exception table’s allocated space and execute the instruction sequence located there. Addresses starting at 0xFFF0_0100 and ending at 0xFFF0_3000 are reserved for the exception vector table.
