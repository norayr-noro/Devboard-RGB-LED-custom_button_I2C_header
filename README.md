# THE MEOWBOARD™
For this project ill be designing the schematic and a custom PCb from that schematic based on the STasis Devboard starter guide, the difference between mine and the guide's board is that mine adds an extra button for reset, an LED for knowing if the PCB is on, and a custom RGB LED on the deboard itself (and dont forget the silkscreen art on the PCB!!)

# 📖 Overview
In short, ill be using the the guide from hackclub stasis starter projects ( https://stasis.hackclub.com/starter-projects/devboard ) of which ill be using the same RP2040 MCU chip which is the same chip used in the rasberry pico and would act the base of the whole devboard. By using this guide i made my own basic devboard, which then i added a i2c header, a extra reset button and more..

🛠️ Design & Components
In my design i have used:
* 1** RP2040 - RP2040 - f.p. (Package_DFN_QFN:QFN-56-1EP_7x7mm_P0.4mm_EP3.2x3.2mm)
* 2** buttons - SW_Push - f.p (Button_Switch_SMD:SW_Push_SPST_NO_Alps_SKRK)
* 4** mounting holes - MountingHole (H) - f.p (MountingHole:MountingHole_2.2mm_M2)
* 1** USB-C receptacle - USB_C_Receptacle_2.0_14P - f.p (Connector_USB:USB_C_Receptacle_HRO_TYPE-C-31-M-12)
* 1** fixed voltage regulator - NCP1117-3.3_SOT223 - f.p (Package_TO_SOT_SMD:SOT-223-3_TabPin2)
* 1** SRAM (storage) - W25Q128JVS - (Package_SON:Winbond_USON-8-1EP_3x2mm_P0.5mm_EP0.2x1.6mm)
* 1** crystal oscillator - 12MHz crystal_GND24 - (Crystal:Crystal_SMD_3225-4Pin_3.2x2.5mm_HandSoldering)
* 1** I2C header pins 01x04 - Conn_01x04 - Connector_PinHeader_2.54mm:PinHeader_1x04_P2.54mm_Vertical
* 1** header pins 01x03 - Conn_01x03 - Connector_PinHeader_2.54mm:PinHeader_1x03_P2.54mm_Vertical
* 2** header pins 01*20 - Conn_01x20 - Connector_PinHeader_2.54mm:PinHeader_1x20_P2.54mm_Vertical
* 1** LED (on/off) - LED - LED_SMD:LED_0805_2012Metric_Pad1.15x1.40mm_HandSolder
* 1** RGB-LED - WS2812B - LED_SMD:LED_WS2812B_PLCC4_5.0x5.0mm_P3.2mm
* 2** 5.1K ohm resistors - R - Resistor_SMD:R_0402_1005Metric_Pad0.72x0.64mm_HandSolder
* 2** 27 ohm resistors - R - Resistor_SMD:R_0402_1005Metric_Pad0.72x0.64mm_HandSolder
* 3** 1K ohm resistors - R - Resistor_SMD:R_0402_1005Metric_Pad0.72x0.64mm_HandSolder
* 2** 10K ohm resistors - R - Resistor_SMD:R_0402_1005Metric_Pad0.72x0.64mm_HandSolder
* 2** 4.7K ohm resistors - R - Resistor_SMD:R_0402_1005Metric_Pad0.72x0.64mm_HandSolder
* 1** 330 resitor - R - Resistor_SMD:R_0402_1005Metric_Pad0.72x0.64mm_HandSolder
* 11* 0.1 uF capacitors - C - Capacitor_SMD:C_0402_1005Metric_Pad0.74x0.62mm_HandSolder
* 4** 1 uF capacitor - C - Capacitor_SMD:C_0402_1005Metric_Pad0.74x0.62mm_HandSolder
* 2** 15 pF capcitors - C -  Capacitor_SMD:C_0402_1005Metric_Pad0.74x0.62mm_HandSolder
  
And for designing the PCB, I used KiCad.

# ⚙️ Tools & Process
Using the base guide on stasis i made a template schematic for my devboard. After which i added my own things to the devboard including:
* reset button using the run pin to gnd
* I2C pin header using 3v3 GND and GPIO pins 4 and 5 and 2 pullup resistors connected to the 3v3 to the gpio pins
* LED for knowing if the pcb is powered or off
* a customisable RGB LED and the on i used is WS2812B
after adding all of that the ending schematic looked like this:

<img width="775" height="551" alt="Screenshot 2026-04-28 124610" src="https://github.com/user-attachments/assets/56822a89-0b96-4364-9922-d6972d3109a8" />

# 📈 Progress
After this, the project went into the PCB stage. Which was quite difficult at first trying to cram all of this into such a small profile so the first prototype model of the PCB looked not that great. Knowing this will not be a sufficent for submition i did a complete reword of the PCB and learnt a few things doing it like, the data wires from the usb-c should be around equal, or that the storage,decopling capacitors and the crystal oscillator should be really close to not cause errors in their own cases.
Another big think i learnt is how to check for errors and at the same time learnt how to make custom silkscreen art from images using the image converter on KiCad. Simply put you import the image into the converter slide the black/white indicator slider to your liking and then use the negative or not which suits best. After that you export the footprint as silkscreen then add that fooptint to the pcb maker on Kicad after which you could use the silkscreen footprint to you liking (i put my silkscreen and the reference images in the photos folder in this repository dont ask why its all cats i just though its might be funny and cool) after all of that the pcb looks something like this:

<img width="1360" height="722" alt="Screenshot 2026-05-01 105045" src="https://github.com/user-attachments/assets/41305687-90f7-4dbc-a22a-95170a3d9635" />

And also heres the final 3d model (back and front):

<img width="1259" height="703" alt="Screenshot 2026-05-01 105021" src="https://github.com/user-attachments/assets/f532aa77-d431-4c77-a110-ef5024199f82" />
<img width="1268" height="703" alt="Screenshot 2026-05-01 104954" src="https://github.com/user-attachments/assets/ffe5c0e2-c89a-4b66-b79a-66872a3693b6" />

# Ordering 
For ordering this pcb i though that jlcpcbs might be best due to their "comparatively" cheap assembly of PCBs. If you want to order this PCB for yourself, check the stasis guide for a full explanation here(https://stasis.hackclub.com/starter-projects/devboard), but in a nutshell, you'd need to put the .gerber file (it's the zip file for this repository, no need to extract it!) and the select the settings youd want then select the PCBA option and then when you start to check out it would want a BOM file (the excel file where all the BILL OF MATTERIALS are) and a position file where they should go, after all of that it should select "most" of the parts for you, then you could just select and approve which part goes for which. All of that and you're done!

# 💭 Final Thoughts + Conclusion
Overall, this project was not as difficult as expected, so while learning how devboards mainly function and actually work i had fun while doing it which was the main part for the, to actually understand how it works. And now ill just be waiting till the MEOWBOARD^(tm) comes!!!
