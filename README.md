Palm IIIc LED backlight replacement
===================================

This repo contains a PCB designed to replace the CCFL backlight of Palm
IIIc PDAs with a LED based backlight.  
The LED based backlight can provide higher fidelity of displayed colors
and prologned battery runtime.

# LED pcb

## Top

![Render of PCB top side](/assets/pcb_top.png)

## Bottom

![Render of PCB bottom side](/assets/pcb_bottom.png)

# Assembly

Assembly of the PCB can be a bit of a tedious job since both the board and
components are relatively small. I recommend either pretinning the pads on
the PCB and applying liberal amounts of flux to stick the components into
place or using solder paste. Using hot air at a low airflow setting the
components can then be reflowed into place.  
For connecting the power supply wiring it is best to connect one wire on
the top and one at the back opposite to the first wire. Use thin enamel
wire (~0.2 mm diameter) to ensure there are no fittment problems after
installation into the Palm.

# Installation

As a first step the Palm has to be fully disassembled. This includes
removing the bare LCD cell from the LCD assembly. After removal of the LCD
cell the white tape over the CCFL tube in the white backlight diffuser
assembly can be pulled up. Then the CCFL tube can be removed.  
Next the assmbled LED PCB can be placed into the diffuser assembly in the
same spot where the CCFL tube was previously located. After reassembly of
the LCD assembly it can be playced back into the case, also reassembling
the midframe.  
Finally it is necessary to peform a small modification of the Palm's 
mainboard to disable the original CCFL inverter and enable control of the
LED backlight.  
The Palm IIIc employs a LX1686CPW CCFL controller for backlight control.
The PWM signal controlling backlight brightness can be tapped of Pin 11
on the IC.  
To minimize overall weight of the Palm I choose to remove the CCFL
backlight transformer to disable the original backlight.  
To allow for control of the new LED backlight a small MOSFET has to be
added to the mainboard. On my Palm IIIc I used a 2N7002K, a good option
due to low gate charge and relatively low RdsOn. The complete mod can be
seen in the following picture:

![Picture of modded mainboard](/assets/mainboard_modded.JPG)

Here I just connected the MOSFET source to GND on a conveniently placed
capacitor to fix it in place. I then connected the PWM backlight control
signal from pin 11 on the CCFL controller IC to the MOSFET gate. Finally
I connected the negative LED board connection to the MOSFET's drain and
the positive LED board connection to a conveniently placed, large
testpoint providing direct B+ battery power next to the battery connector.

# Results

After installing this mod the backlight is substantially brighter and
reaches full brighness immediately after waking up the Palm. Also colors
look a lot more vibrant. The following photo tries to capture how good the
colors look but really does not quite do the improvement justice.

![Picture of colors on screen post mod](/assets/colors_modded.JPG)
