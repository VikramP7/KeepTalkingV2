*<div align="right"> Vikram Procter | June 29 to July 30, 2025 </div>*

# Keep Talking and No One Explodes Inspired - Fake Bomb PCB Design

## Purpose Overview
-   A fun project to learn a STM32 microcontrollers and RTOSs
-   A great prank ffriends 
-   A fun game to play with friends

## TODO:


## Overview:
### <a href="#difusal-modules-details" style="color:inherit">Difusal Modules:</a>
-   Wires
-   Red Button
-   Symbols
-   Capacitive Simon Slider
-   Morse Code (LED)

### <a href="#display-modules-details" style="color:inherit">Display Modules:</a>
-   Strikes display
-   7-Segment Count down timer
-   Buzzer/Beeper
-   Dramatic LEDs
-   Fake Batteries

### <a href="#microprocessor-specs" style="color:inherit">Microprocessor</a>:
-	[STM32L412CB processor](https://www.digikey.ca/en/products/detail/stmicroelectronics/STM32L412CBT6/9656217)
-	[ABLS-16.000MHZ-B2-T](https://www.digikey.ca/en/products/detail/abracon-llc/ABLS-16-000MHZ-B2-T/675266)



## Module Specs:

### Wires Module
-   Two 6 position screw terminals will be used to hold 6 wires
-   Through cuting the correct wires in the correct sequence an LED inidcator next to the module will light green
-   Each wire will connect to ground and the GPIO pins will have an external pullup (3V3)
-   [6 position terminal 1988846](https://www.digikey.ca/en/products/detail/phoenix-contact/1988846/950896)

### Red Button Module
-   Small red button with colour [light indicator](https://www.digikey.ca/en/products/detail/cree-led/CLMVC-FKA-CL1D1L71BB7C3C3/4794065) next to it.
-   Based on colour and pattern of light the button should be clicked or held
-   The light indicator will indicate if it has been diffused
-   [Tactile push button](https://www.digikey.ca/en/products/detail/te-connectivity-alcoswitch-switches/FSM103/701085), with [red cap](https://www.digikey.ca/en/products/detail/omron-electronics-inc-emc-div/B32-1380/9702) or [yellow cap](https://www.digikey.ca/en/products/detail/omron-electronics-inc-emc-div/B32-1330/9741) 
-   External Pull up

### Symbols
-   Because I am cheap 32 leds arranged in a 6x6 without the corners will be used to display a symbol. (Good luck soldering)
-   Based on the symbol or set of symbols a knob must be turned to the right position position should be descrete and described by whos son first words.  
-   Use 2x 16-bit shift reg LED driver [STP16CPC26PTR](https://www.digikey.ca/en/products/detail/stmicroelectronics/STP16CPC26PTR/2757642) to drive all 32 leds. Could be daisy chained for even fewer MCU pins

### Capacitive Simon Slider
-   An 4 coloured through-hole LED will indidicate which dirrection the slider should be slid and in what order to difuse the module.
-   Slider will use the [AT42QT2120-MMHR](https://www.digikey.ca/en/products/detail/microchip-technology/AT42QT2120-MMHR/3678733) chip for Self-Capacitance sensing 
-   Altiums library for making capacitive footprints find at `C:\Users\Public\Documents\Altium\AD25\Library\QTouch`


### Morse Code
-   LED (through hole) will blink morse code
-   Based on the message the positions of a 6pos dip switch [1825057-5](https://www.digikey.ca/en/products/detail/te-connectivity-alcoswitch-switches/1825057-5/969175) must be set
-    Input to microcontroller will be through ADC and resistor ladder [4610X-R2R-103LF](https://www.digikey.ca/en/products/detail/bourns-inc/4610X-R2R-103LF/3787967) connected to dipswitch pins.

### Strikes Display Module
-   3D printed case with the three X marks cut out
-   Three LEDs will be placed behind each X, some diffusion film (paper or wax paper) could be used
-   LEDs [LTST-C170KAKT](https://www.digikey.ca/en/products/detail/liteon/LTST-C170KAKT/386773?s=N4IgTCBcDaIDIBUDKCC0BhAjAdgAwGkBBfBEAXQF8g) will be connected to the LED controller used for RGB status LEDs

### 7-Segment Countdown Timer Module
-   Use a 4 character [TDCR1060M](https://www.digikey.ca/en/products/detail/vishay-semiconductor-opto-division/TDCR1060M/4074711) 7-segment display
    - Using 162 ohm resisistors each segment should draw 5.5mA
    - Total current draw of up to 8*5.5=44mA
    - Only one digit will ever be on at one time
-   Seven segment driver [SN74LS247DR](https://www.digikey.ca/en/products/detail/texas-instruments/SN74LS247DR/15904701)
    - nBI should be held high
    - nRBI should be held high
    - LT should be held hight

### LED Controller
-   Using the [IS31FL3235A-QFLS2-TR](https://www.digikey.ca/en/products/detail/lumissil-microsystems/IS31FL3235A-QFLS2-TR/7219609) 

### Buzzer Beeper and Dramatic LEDs Module
-   Using 3V magnetic buzzer [WT-0904T](https://www.digikey.ca/en/products/detail/soberton-inc/WT-0904T/16384510)
-   Attach to PWM pin through npn transistor [MMBT3904-TP](https://www.digikey.ca/en/products/detail/mcc-micro-commercial-components/MMBT3904-TP/717280)

### Fake Batteries Module
-   Screw terminal on side of board that connect to leads of battery case.
-   High resistance voltage divider to keep current draw in miliamp range for maximum use of batteries
-   No voltage divider voltage < 3V. Connected to ADC for measurment 

### Configuration Jumpers (no pins left :disappointed:)
-   Any remaining GPIO pins can be connected to jumper switches to allow for game configuration.


### Power Regulation Specs
-   Device will be powered by 3 AA batteries providing nominal voltage of 4.5V
-   3V3 Regulator [LDL1117S33R](https://www.digikey.ca/en/products/detail/stmicroelectronics/LDL1117S33R/7102071) used for all components as 3V3 is good for logic and power
-   Reverse polarity protection diode [RB161MM-20TR](https://www.digikey.ca/en/products/detail/rohm-semiconductor/RB161MM-20TR/5001867)
-   Indicator LED that power is on working
-   Can be powered via usb or battery, controlled using power switch

### Microprocessor Specs
-   Figure out what programming pins are needed
-   Planning on using the [STLINK-V3MINIE](https://www.digikey.at/en/products/detail/stmicroelectronics/STLINK-V3MINIE/16284301?srsltid=AfmBOopIx4ocnLGSitlX52VvPF4tIXacUyRYL3eHyHwXfcPgu7cQNPwkt0E&gQT=2) debugger/programmer
-   Boot mode selector switch. Pull Boot0 pin high for I2C/UART/USB programming, or pull low for run mode (SWD can overide run and program)
    - We want to pretty much always be in run mode so weak pull down to ground, if I don't want to add the switch.
-   External High frequency oscillator being used
    - Crystal [ABLS-16.000MHZ-B2-T](https://www.digikey.ca/en/products/detail/abracon-llc/ABLS-16-000MHZ-B2-T/675266)
    - Load Capacitance is $C_{L}=18pF$ and stray board Capacitance is in the range of 2-10pF
    - External load capacitors are calculated by $C_{load}=2*(C_{L}-C_{stray})=24pF$
    - External resistor is calculated to be very small, therefor omitted

-   See CubeIDE for specifications on connectivity

### Total Current Draw 
-   LED Controller (Red button led, module diffused status LEDs, strikes LEDS)
    - Each LED has current max of 8.3mA
    - Max current draw **140mA** (with all leds on)
-   Matrix LEDS and Controllers
    - Each LED has current max of 3.2mA
    - With all LEDS on max current draw is 144*3.2mA=**460mA**
-   Seven Segment Display
    - Using resistor based current limmiting each LED is limmited to 5.5mA
    - Only 8LEDs could be on at one time, as controller strobes. Therefore max current draw is **44mA**
- Buzzer
    - Could run up to **80mA**
-   Wires
    - If all wires are connected they burn 1mA
-   Microcontroller
    - Micro controller runs up to 74uA/MHz
    - With 16MHz, total operating current draw is **1.2mA**

-   Total Current draw = **725.2mA**