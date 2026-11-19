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

