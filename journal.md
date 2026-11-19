# Alvonomic
Alice style keyboard | keys count - 65

# Project journal

## Journal 1 - The schematic and the layout

I decided to make a 65 keys keyboard in alice style as it looks a bit attractive and hard to build. 

I started with layout design in [keyboard layout editor](https://www.keyboard-layout-editor.com/#/). Then I used KiCAD for achematic and pcb designing. 

<img width="611" height="221" alt="image" src="https://github.com/user-attachments/assets/280420a9-3786-45bc-bfa9-a5b1f31190eb" />


parts I used in the schematic 
* Rapberry pi pico : I decided to use pico as it's small and has enough pins to connect rows and columns
* sw_push : Used sw_push symbol as switchs
* Diode : As diodes are important for row and column connections, I used 1N4148 diode as it's a basic ideal choice for DIY keyboards and easy to find in small electronics markets. 

I started by placing switches devided in 2 parts left and right. Annonated the keys on the left side from 1 to 32 and on the right side from 33 to 65

Added diodes on every switches annonating them the same number as switches. 

Wired them in rows and columns. I used 2 colors in wires for better visibility
* Red : for rows 
* Green : for columns

<img width="1053" height="833" alt="image" src="https://github.com/user-attachments/assets/97a48ab6-bc28-40da-9cc1-4e5c11b1c6b9" />
<img width="715" height="571" alt="image" src="https://github.com/user-attachments/assets/631752fb-3def-41a1-ae36-d639dee09682" />


connected all switches in 
* 16 columns
* 10 rows


## Journal 2 - Wiring the head

Used Pico as the head of the keyboard. 

After connecting all the switches in columns ans rows, added labels on them like `col_1` `row_1` and so on. 

Placed a pico symbol in the schematic. I downloaded the pico symbol and footprint from [SnapEDA](https://www.snapeda.com/home/)

for the footprints I used THT version over SMD cause I will do hand soldering and soldering SMD mcu is way too hard as beginner. 

Connected all columns and rows in pico GP pins. 

<img width="1132" height="899" alt="image" src="https://github.com/user-attachments/assets/5dd49c4e-99d2-4bff-8a61-9c692709a258" />

For better visualisation I added a pico diagram to make it easier to understand if someone wants to reuse this schematic. 

<img width="1129" height="920" alt="image" src="https://github.com/user-attachments/assets/8e5513ae-6175-448f-afde-49441b6e8443" />


Extras
* Added name on top
* Attached a layout image on the schematic sheet

Added 2 tables row and col labels and their pin numbers to make it easy during coding the firmware. 


> **Finally the schematic sheet is temporarily done to move to the PCB editor**



## Journal 3 : The biggest mess

After commpleting the schematic and moving to the PCB editor. 

Assigned final footprint to all switches and diodes. 

Used Cherry mx 1u footprint for switches

### Used keyboard plugin to sort and arrange keys in the actual order.

### **But But But!!!!!!!!!!!! Here is an issue**

My switches were annotated with Y coordinates from 1 to 32 on the left and 33 to 65 on the right side. 

But the keyboard plugin doesn't see how switches are sorted in the schematic, this plugin uses the layout json and arranges them in the Y coordinates of the PCB editor. And made my full PCB a mess cause it's an Alice-style keyboard and in alice style all keys are not in same row or column, keys are rotated placed differently. So, using keyboard plugin that uses only json reference is not working to make an Alice-style layout. 

### After searching all on the internet I tried many ways to solve this issue but nothing was working. All were sorting them in a messy y-coordinate. 

Later I found out another plugin called `KLE Placer` but in KiCAD plugin settings it was out of date, so i needed to install it manually. 

Here is the github repo of the plugin, guidelines are here if u want to install
[KLE placer](https://github.com/zykrah/kicad-kle-placer)

KLE placer works in a different way. It uses number used on the key legend in the layout editor. 

Means during making the layout you need to add number on the keycaps legend. Then the plugin will use the keycap legend number to place the switches in the PCB editor. 

So, I wrote the same numbers on the keycaps legend as annotations of the schematic. 

<img width="1067" height="395" alt="image" src="https://github.com/user-attachments/assets/dd935b88-3e6f-4535-a7c7-4e6ed5f87439" />

Downloaded the json again and this time used KLE placer to sort the switches and fortunately it worked the way I needed. 
