# Trigorilla-Pro
An Anycubic Trigorilla Pro from a Predator reverse


Anycubic Trigorilla pro specs and mcu pinout

- 32bit Cortex-M3 MCU (STM32F103ZET6) 8MHz crystal
- Soldered 5x A4988 stepper drivers configured to 16 microsteps (MS all to 3v3)
- WIFI slot for ESP-01S
- Onboard Winbond W25Q16JV 16Mbit SPI Flash
- Onboard 24C16 I2C 16Kbit EEPROM
- 1F SuperCapacitor for blackout data backup with a mosfet for pwm charge
- Onboard SD Card slot and pin header
- USB Serial communication
- Buzzer, sw controlled internal led
- Second Extruder-Hotend DaughterBoard predisposition
- Mounted in Anycubic Predator, I3 Mega and ecc 
- Custom touch lcd 3.5 inch 320x480 ILI9488 with TSC2046 spi touch controller

I have recostructed the schematics of this board from my predator, i hope that 
in some time is possible to implement a custom firmware for this board without
change it. The schematics is designed with eagle cad free and is for only for
study purpose, only the foundamental signals are drawed, and some components
that i have selected are incorrect for the pcb, but for the digital wiring sense
is ok. The library for the drawing are all included, created from the 
respectively authors.


Jumpers
- JP1 =         Bootloader, remove and power up for flashing
- SW1 =         5V From usb or internal psu, is used for flash w/out psu


Stepper controllers and cpu pin cross table
- X-MOTOR
    * DIR =       PE6
    * STEP =      PE5
    * nENABLE =   PC13
- Y-MOTOR
    * DIR =       PE3
    * STEP =      PE2
    * nENABLE =   PE4
- Z-MOTOR
    * DIR =       PE0
    * STEP =      PB9
    * nENABLE =   PE1
- EXTRUDER-MOTOR
    * DIR =       PB5
    * STEP =      PB4
    * nENABLE =   PB8
- Z2-MOTOR (not used in predator)
    * DIR =       PC6
    * STEP =      PC7
    * nENABLE =   PG8


Digital Sensors all pull-upped to 5v
- FILAMENT1 = PA15
- Z- =        PA14
- Z+ =        PA13    (autolevel removable switch un predator)
- Y- =        PA12
- X- =        PG10


Analog Sensors all pull-upped to 3v3
- E-TEMP =    PA1
- B-TEMP =    PA0


Fans
- M-FAN =     PD6     (internal motherboard for predator)
- FAN0 =      PG13    (duct blowers for predator)
- FAN1 =      PG14    (hotend fan for predator)


Heaters
- HOT-END1 =  PG12
- HOTBED =    PG11    (inverted)


Second Extruder-Hotend Headers (no signal conditioning, direct connected to cpu)
- JP3
    * 1-EXT =     PC5     (Extruder STEP?)
    * 2-RVO =     PB1     (Extruder DIR?)
    * 3-HOT2 =    PG7     (HotEnd control out?)
    * 4-COOL2 =   PG6     (HotEnd fan control out?)
    * 5-TEMP2 =   PA2     (HotEnd ADC sensor in?)
- JP6
    * 1-GND
    * 2-12/24V
    * 3-12/24V
    * 4-GND
    * 5-GND
    * 6-3V3
    * 7-FILAMENT2 = PA3   (Second filament runout sensor?)

    
Voltage Alarm, SuperCapacitor and signaling
- ALARM =     PG2     (12/24V monitoring comparator output, to trigger backup)
- PWM-OUT =   PG4     (PWM generated from CPU for charge supercap w/out damange)
- BUZZER =    PB0     (frequency generated from cpu)
- LED =       PD3     (internal led inverted logic)


Memory
- 24C16
    * SCL =     PG0
    * SDA =     PG1    
- W25W16JV on SPI2 Interface
    * nCS =     PB12
    * CLK =     PB13
    * DO  =     PB14
    * DI  =     PB15    
- SD Card slot and pin header JP2  on SDIO
    * CMD =     PD2
    * CK        PC12
    * D0        PC8
    * D1        PC9
    * D2        PC10
    * D3        PC11
    
    
Wi-Fi ESP01S ESP8266 Module socket J1 to USART3
- 1 RX =      PB10         USART3 TX
- 2 3V3
- 3 GND
- 4 GPIO =    PD12         RESET
- 5 NC
- 6 3V3
- 7 GND
- 8 TX        PB11         USART3 RX

orientation

*|1|2|        =>  CPU
*|3|4|          
*|5|6|
*|7|8|


USB Serial communication    USART1
- USART1 TX = PA9           (to RX pin of the PL2303)
- USART1 RX = PA10          (to TX pin of the PL2303)


LCD Touch Display connector 39 pin start from X- connector, on FSMC as lcd cont.
- 1 = 3V3
- 2 = NC
- 3 = NC
- 4 = NC
- 5 = GND
- 6 = PD14          lcd pin 9 of 40
- 7 = PD15          lcd pin 10 of 40
- 8 = PD0           lcd pin 11 of 40
- 9 = PD1           lcd pin 12 of 40
- 10 = PD7          lcd pin 4 of 40
- 11 = PD11         lcd pin 5 of 40
- 12 = PD5          lcd pin 6 of 40
- 13 = PD4          lcd pin 7 of 40
- 14 = PD13         Backlight on
- 15 = PE7          lcd pin 13 of 40
- 16 = PE11         lcd pin 17 of 40
- 17 = PE12         lcd pin 18 of 40
- 18 = PE13         lcd pin 19 of 40
- 19 = PE14         lcd pin 20 of 40
- 20 = PE15         lcd pin 21 of 40
- 21 = PD8          lcd pin 22 of 40
- 22 = PD9          lcd pin 23 of 40
- 23 = PD10         lcd pin 24 of 40
- 24 = PB6          TSC2046 Touch nIRQ
- 25 = PA6          TSC2046 Touch DO
- 26 = PA7          TSC2046 Touch DI
- 27 = PB7          TSC2046 Touch nCS
- 28 = PA5          TSC2046 Touch CLK
- 29 = PF11         lcd pin 8 of 40
- 30 = PE8          lcd pin 14 of 40
- 31 = PE9          lcd pin 15 of 40
- 32 = PE10         lcd pin 16 of 40
- 33 = GND
- 34 = GND
- 35 = GND
- 36 = 5V
- 37 = 5V
- 38 = 3V3
- 39 = 3V3
- 40 = 3V3


Resistive touch controller TSC2046 on SPI1
- PB6 = nIRQ
- PA6 = DO
- PA7 = DI
- PB7 = nCS
- PA5 = CLK


LCD 3.5 inch 320x480 ILI9488 controller model FXD035HV20-FPC-A0 on custom board.
Unfortnately i don't know if this pinout is correct for all digital signals
 names
- 1 = GND
- 2 = 3V3
- 3 = 3V3
- 4 = CSX             PD7          FSMC_NE1/FSMC_NCE2
- 5 = D/CX            PD11         FSMC A16
- 6 = WRX             PD5          FSMC_NWE
- 7 = RD              PD4          FSMC_NOE
- 8 = RESET           PF11         FSMC_NIOS16
- 9 = DB0             PD14         FSMC_Dx
- 10 = DB1            PD15         *
- 11 = DB2            PD0          *
- 12 = DB3            PD1          *
- 13 = DB4            PE7          *
- 14 = DB5            PE8          *
- 15 = DB6            PE9          *
- 16 = DB7            PE10         *
- 17 = DB8            PE11         *
- 18 = DB9            PE12         *
- 19 = DB10           PE13         *
- 20 = DB11           PE14         *
- 21 = DB12           PE15         *
- 22 = DB13           PD8          *
- 23 = DB14           PD9          *
- 24 = DB15           PD10         *
- 25 = GND
- 26 = Y+
- 27 = Y-
- 28 = Y-
- 29 = X+
- 30 = K
- 31 = K
- 32 = K
- 33 = K
- 34 = K
- 35 = K
- 36 = 3V3
- 37 = GND
- 38 = NC
- 39 = NC
- 40 = NC
