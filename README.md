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
- Mounted in Anycubic Predator, I3 Mega and ecc with 4 inch Touch LCD

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
- W25W16JV
    * nCS =     PB12
    * CLK =     PB13
    * DO  =     PB14
    * DI  =     PB15    
- SD Card slot and pin header JP2  (all pull-upped to 3v3 except CK)
    * CMD =     PD2
    * CK        PC12
    * D0        PC8
    * D1        PC9
    * D2        PC10
    * D3        PC11
    
    
Wi-Fi ESP01S ESP8266 Module socket J1
- 1 RX =      PB10
- 2 3V3
- 3 GND
- 4 GPIO =    PD12         (reset?)
- 5 NC
- 6 3V3
- 7 GND
- 8 TX        PB11

orientation

- |1|2|          CPU
- |3|4|          
- |5|6|
- |7|8|


USB Serial communication
- TX =        PA9           (to RX pin of the PL2303)
- RX =        PA10          (to TX pin of the PL2303)


LCD Touch Display connector 39 pin start from X- connector
- 1 = 3V3
- 2 = NC
- 3 = NC
- 4 = NC
- 5 = GND
- 6 = PD14
- 7 = PD15
- 8 = PD0
- 9 = PD1
- 10 = PD7
- 11 = PD11
- 12 = PD5
- 13 = PD4
- 14 = PD13
- 15 = PE7
- 16 = PE11
- 17 = PE12
- 18 = PE13
- 19 = PE14
- 20 = PE15
- 21 = PD8
- 22 = PD9
- 23 = PD10
- 24 = PB6
- 25 = PA6
- 26 = PB7
- 27 = PA5
- 28 = PF11
- 29 = PE8
- 30 = PE9
- 31 = PE10
- 32 = GND
- 33 = GND
- 34 = GND
- 35 = 5V
- 36 = 5V
- 37 = 3V3
- 38 = 3V3
- 39 = 3V3
