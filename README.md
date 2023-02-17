# DevTerm-ExtCart

An extension board for the DevTerm, with Commodore64-style 44pin cartridge.
 ![PCB](https://raw.githubusercontent.com/yatli/DevTerm-ExtCart/main/img/PCB.PNG)

## Design desiderata

Pin assignment:
- Maximum compatibility and function alignment.
- Strong coupling of differential pairs.
- Avoid damage.
All power pins are mirror safe.
Expansion port requirement:
- Pin 21 MUST connect to Pin 23.
- Pin 24 MUST be NC
ROUTE_EN disconnects all routed pins when cartridge is:
- Disconnected
- Inserted the wrong direction
Resource overview:
- 8x internal GPIOs
- 8x external GPIOs
- MIPI-CSI
- 3x USB 2.0
- 1x SPI
- 1x I2C
- 1x UART (Debug)
Resource management pins:
- IO36 for power management
- IO43 for cartridge detection

## Bill of materials

| Item | Qty | Reference(s)                                                                 | Value               | Footprint                                                                    | Datasheet                                                                                  |
|------|-----|------------------------------------------------------------------------------|---------------------|------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| 1    | 3   | C1, C4, C5                                                                   | 10uF                | Capacitor_SMD:C_0805_2012Metric                                              | ~                                                                                          |
| 2    | 3   | C2, C9, C10                                                                  | 1uF                 | Capacitor_SMD:C_0805_2012Metric                                              | ~                                                                                          |
| 3    | 9   | C3, C6, C7, C8, C11, C14, C15, C16, C17                                      | 100nF               | Capacitor_SMD:C_0805_2012Metric                                              | ~                                                                                          |
| 4    | 2   | C12, C13                                                                     | 20pF                | Capacitor_SMD:C_0805_2012Metric                                              | ~                                                                                          |
| 5    | 17  | D1, D2, D3, D4, D5, D6, D9, D10, D11, D12, D13, D14, D15, D16, D17, D18, D19 | ESD                 | Diode_SMD:D_SOD-323                                                          | https://www.onsemi.com/pub/Collateral/ESD9B-D.PDF                                          |
| 6    | 2   | D7, D8                                                                       | LED                 | LED_SMD:LED_0603_1608Metric                                                  | ~                                                                                          |
| 7    | 2   | FB1, FB2                                                                     | FerriteBead         | Capacitor_SMD:C_0805_2012Metric                                              | ~                                                                                          |
| 8    | 2   | J1, J3                                                                       | USB_A               | devterm-ext-outline:USB_A_PCBCUT                                             | ~                                                                                          |
| 9    | 1   | J2                                                                           | EXT_miniPCIe        | mpcie:mini-PCIe                                                              | https://pcisig.com/specifications/pciexpress/base                                          |
| 10   | 1   | J4                                                                           | USB_B_Micro         | Connector_USB:USB_Micro-B_Amphenol_10118194_Horizontal                       | ~                                                                                          |
| 11   | 1   | J5                                                                           | Conn_01x02          | Connector_Molex:Molex_PicoBlade_53048-0210_1x02_P1.25mm_Horizontal           | ~                                                                                          |
| 12   | 1   | J6                                                                           | Conn_01x04          | Connector_PinSocket_2.00mm:PinSocket_1x04_P2.00mm_Vertical                   | ~                                                                                          |
| 13   | 1   | J9                                                                           | Conn_02x22_Odd_Even | devterm-ext-outline:C64-Cart-Socket-Horizontal                               | ~                                                                                          |
| 14   | 1   | JP1                                                                          | A0                  | Jumper:SolderJumper-3_P1.3mm_Open_Pad1.0x1.5mm                               | ~                                                                                          |
| 15   | 1   | JP2                                                                          | A1                  | Jumper:SolderJumper-3_P1.3mm_Open_Pad1.0x1.5mm                               | ~                                                                                          |
| 16   | 1   | JP3                                                                          | A2                  | Jumper:SolderJumper-3_P1.3mm_Open_Pad1.0x1.5mm                               | ~                                                                                          |
| 17   | 2   | R1, R9                                                                       | 30K                 | Resistor_SMD:R_0805_2012Metric                                               | ~                                                                                          |
| 18   | 1   | R2                                                                           | 680R/1%             | Resistor_SMD:R_0805_2012Metric                                               | ~                                                                                          |
| 19   | 5   | R3, R6, R15, R16, R19                                                        | 100K                | Resistor_SMD:R_0805_2012Metric                                               | ~                                                                                          |
| 20   | 3   | R4, R5, R10                                                                  | 10K                 | Resistor_SMD:R_0805_2012Metric                                               | ~                                                                                          |
| 21   | 2   | R7, R11                                                                      | 6.8K/1%             | Resistor_SMD:R_0805_2012Metric                                               | ~                                                                                          |
| 22   | 1   | R8                                                                           | 47K                 | Resistor_SMD:R_0805_2012Metric                                               | ~                                                                                          |
| 23   | 4   | R12, R14, R17, R18                                                           | 1K                  | Resistor_SMD:R_0805_2012Metric                                               | ~                                                                                          |
| 24   | 1   | R13                                                                          | 15K                 | Resistor_SMD:R_0805_2012Metric                                               | ~                                                                                          |
| 25   | 1   | SW1                                                                          | SW_DIP_x02          | Button_Switch_SMD:SW_DIP_SPSTx02_Slide_6.7x6.64mm_W8.61mm_P2.54mm_LowProfile | ~                                                                                          |
| 26   | 1   | SW2                                                                          | SW_SPDT             | Button_Switch_THT:SW_CuK_OS102011MA1QN1_SPDT_Angled                          | ~                                                                                          |
| 27   | 1   | U1                                                                           | GL850G              | GL850G:SSOP28                                                                | ~                                                                                          |
| 28   | 2   | U2, U3                                                                       | SY6280              | SY6280:SOT23-5P95_285X100L45X40N                                             | ~                                                                                          |
| 29   | 1   | U4                                                                           | DS1307+             | devterm-ext-outline:SOIC-8                                                   | https://datasheets.maximintegrated.com/en/ds/DS1307.pdf                                    |
| 30   | 1   | U5                                                                           | MCP23008-xSS        | Package_SO:SOIC-20W_7.5x12.8mm_P1.27mm                                       | http://ww1.microchip.com/downloads/en/DeviceDoc/MCP23008-MCP23S08-Data-Sheet-20001919F.pdf |
| 31   | 1   | U6                                                                           | CH340N              | Package_SO:SOP-8_3.9x4.9mm_P1.27mm                                           |                                                                                            |
| 32   | 4   | U7, U8, U10, U11                                                             | 4052                | Package_SO:SOIC-16_3.9x9.9mm_P1.27mm                                         | http://www.intersil.com/content/dam/Intersil/documents/cd40/cd4051bms-52bms-53bms.pdf      |
| 33   | 1   | U9                                                                           | gp7101              | Package_SO:SOP-8_3.9x4.9mm_P1.27mm                                           |                                                                                            |
| 34   | 1   | U12                                                                          | TXS0102DCT          | Package_SO:MSOP-8_3x3mm_P0.65mm                                              | http://www.ti.com/lit/gpn/txs0102                                                          |
| 35   | 1   | Y1                                                                           | 12MHz               | Crystal:Crystal_SMD_3225-4Pin_3.2x2.5mm_HandSoldering                        | ~                                                                                          |
| 36   | 1   | Y2                                                                           | 32.768KHz           | Crystal:Crystal_DS26_D2.0mm_L6.0mm_Horizontal                                | ~                                                                                          |
