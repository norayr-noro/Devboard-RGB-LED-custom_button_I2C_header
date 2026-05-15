# THE MEOWBOARD™
For this project, I'll be designing the schematic and a custom PCB from that schematic based on the Stasis Devboard starter guide. The difference between mine and the guide's board is that mine adds an extra reset button, an LED for knowing if the PCB is on, and a custom RGB LED on the deboard itself (and don't forget the silkscreen art on the PCB!!)

# 📖 Overview
In short, I'll be using the guide from Hack Club Stasis starter projects ( https://stasis.hackclub.com/starter-projects/devboard ) of which I'll be using the same RP2040 MCU chip, which is the same chip used in the rasberry pico and would act as the base of the whole devboard. By using this guide, I made my own basic devboard, which then I added an I2C header, an extra reset button, and more.

🛠️ Design & Components
In my design, I have used:
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
* 2** 15 pF capacitors - C -  Capacitor_SMD:C_0402_1005Metric_Pad0.74x0.62mm_HandSolder
  
And for designing the PCB, I used KiCad.

# ⚙️ Tools & Process
Using the base guide on stasis, I made a template schematic for my devboard. After which I added my own things to the devboard including:
* reset button using the run pin to GND
* I2C pin header using 3v3, GND, and GPIO pins 4 and 5, and 2 pull-up resistors connected to the 3v3 to the GPIO pins
* LED for knowing if the PCB is powered or off
* a customisable RGB LED, and the on i used is WS2812B
After adding all of that, the ending schematic looked like this:

<img width="775" height="551" alt="Screenshot 2026-04-28 124610" src="https://github.com/user-attachments/assets/56822a89-0b96-4364-9922-d6972d3109a8" />

# 📈 Progress
After this, the project went into the PCB stage. This was quite difficult at first, trying to cram all of this into such a small profile, so the prototype model of the PCB did not look that great. Knowing this would not be a sufficent for submition i did a complete re-work of the PCB and learnt a few things doing it, like the data wires from the USB-C should be around equal, or that the storage decoupling capacitors and the crystal oscillator should be really close to not cause errors in their own cases.
Another big think i learnt is how to check for errors and at the same time learnt how to make custom silkscreen art from images using the image converter on KiCad. Simply put, you import the image into the converter, slide the black/white indicator slider to your liking, and then use the negative or not, which suits best. After that, you export the footprint as silkscreen, then add that footprint to the pcb maker on KiCad, after which you could use the silkscreen footprint to your liking (i put my silkscreen and the reference images in the photos folder in this repository dont ask why its all cats i just though its might be funny and cool) after all of that the pcb looks something like this:

<img width="444" height="539" alt="PCB_screenshot(2d)" src="https://github.com/user-attachments/assets/0bc071dc-1d07-4409-b048-9a6d36416843" />


And also here's the final 3d model (back and front):


<img width="1366" height="707" alt="PCB_screenshot(example)" src="https://github.com/user-attachments/assets/d43ccb01-0c77-44ee-8be0-3023f0a0689c" />
<img width="680" height="415" alt="PCB_screenshot(3d-back)" src="https://github.com/user-attachments/assets/a0ed36e1-7084-4149-ac9f-fea24de64531" />

# Ordering 
For ordering this pcb i though that JLCPCBs might be best due to their "comparatively" cheap assembly of PCBs. If you want to order this PCB for yourself, check the stasis guide for a full explanation here(https://stasis.hackclub.com/starter-projects/devboard), but in a nutshell, you'd need to put the .gerber file (it's the zip file for this repository, no need to extract it!) and the select the settings youd want then select the PCBA option and then when you start to check out it would want a BOM file (the excel file where all the BILL OF MATTERIALS are) and a position file where they should go, after all of that it should select "most" of the parts for you, then you could just select and approve which part goes for which. All of that and you're done!

# BOM 
Also, I'll be adding the BOM file showing roughly where you can get all the parts and which parts I have used in this project.
	Price valued per unit and total price PER BOARD				
| Item	 |   URL	         |  Price (per unit )	| Quantity needed	|Quantity to order (min on JLCPCB) |	Total |
|1uf caps |	https://jlcpcb.com/partdetail/53938-CL05A105KA5NQNC/C52923 |	0.0039	| 4 |	8 |	$0.01 |
|0.1uf (100nf) caps |	https://jlcpcb.com/partdetail/1877-CL05B104KO5NNNC/C1525 |	0.0013	| 11 |	22 |	$0.01 |
|8pf caps |	https://jlcpcb.com/partdetail/1930-0402CG8R0C500NT/C1578 |	0.0012 |	2 |	4 |	$0.01 |
|SK6812MINI-E (RGB-LED) |	https://jlcpcb.com/partdetail/OPSCOOptoelectronics-SK6812MINIE/C5149201 |	0.086 |	1 |	2 |	$0.17 |
|LED |	https://jlcpcb.com/partdetail/85425-NCD0805R1/C84256 |	0.0133 |	1  |	2 |	$0.03 |
|USB-C female surface mount |	https://jlcpcb.com/partdetail/Korean_HropartsElec-TYPE_C_31_M12/C165948	 | 0.1832 |	1  |	2  |	$0.37  |
|5.1K resistors |	https://jlcpcb.com/partdetail/26648-0402WGF5101TCE/C25905 |	0.0009 |	2  |	4 |	$0.01 |
|27 ohm resistors	| https://jlcpcb.com/partdetail/25843-0402WGF270JTCE/C25100 |	0.0008 |	2  |	4	|$0.01 |
|10K resistors |	https://jlcpcb.com/partdetail/26487-0402WGF1002TCE/C25744 |	0.0013 |	2  |	4  |	$0.01 |
|330 ohm resistors |	https://jlcpcb.com/partdetail/25847-0402WGF3300TCE/C25104 |	0.0011 |	1  |	2  |	$0.01 |
|1K resistors	 | https://jlcpcb.com/partdetail/12256-0402WGF1001TCE/C11702	 | 0.001 |	3 |	6 |	$0.01 |
|4.7K resistors |	https://jlcpcb.com/partdetail/26643-0402WGF4701TCE/C25900	 | 0.001 |	2 |	4 |	$0.01 |
|push buttons	 | https://jlcpcb.com/partdetail/XUNPU-TS_1088AR02016/C720477	 | 0.0555 |	2 |	4 |	$0.11 |
|RP2040 |	https://jlcpcb.com/partdetail/RaspberryPi-RP2040/C2040	           | 0.9764	| 1 |	2 |	$1.95 |
|AMS1117-3.3	 | https://jlcpcb.com/partdetail/Advanced_MonolithicSystems-AMS1117_33/C6186 |	0.2118 |	1 |	2 |	$0.42  |
|W25Q128JVSIQ	 |https://jlcpcb.com/partdetail/WinbondElec-W25Q128JVSIQ/C97521	 | 1.892 |	1 |	2 |	$3.78  |
|NX3225GA  |12MHZ	https://jlcpcb.com/partdetail/NDK-NX3225GA_12MHZ_STD_CRG2/C481407 |	0.249 |	1 |	2 | $0.50  |
Subtotal (only parts)	8.23				
Shipping and handling	1.5				
PCB	4				
Total (without assembly fees)	13.73				
Total (with fees)	38.09
# Updates - Notes
After reviewing the files, I have changed quite a few things with the help of a reviewer. My first thing is that I added the .csv a nd .xlsx files of all the parts for the PCB. Secondly, I updated the silkscreen design to remove the dotted lines, as they might cause some manufacturing difficulties. Continuing with the updates, I changed the WS2812B to an SK6812MINI-E and routed it's vdd to 5V instead of 3V3 due to it being out of spec for both cases. Finally, I changed the SRAM for a cheaper version, the W25Q128JVSIQ TR to the W25Q128JVSIQ, which is bigger, but it was quite cheaper than the last model. Other than that, I checked for any errors, did some polishing, and got there to be 0 DRC errors in sight.

# 💭 Final Thoughts + Conclusion
Overall, this project was not as difficult as expected, so while learning how devboards mainly function and actually work, I had fun while doing it, which was the main part to actually understand how it works. And now I'll just be waiting till the MEOWBOARD^(tm) comes!!!
