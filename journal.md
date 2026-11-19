# Alvonomic
Alice style keyboard | keys count - 65

## Project journal

### Journal 1 - The schematic and the layout

I decided to make a 65 keys keyboard in alice style as it looks a bit attractive and hard to build. 

I started with layout design in keyboard layout editor. Then I used KiCAD for achematic and pcb designing. 

[layout image here]

parts I used in the schematic 
* Rapberry pi pico : I decided to use pico as it's small and has enough pins to connect rows and columns
* sw_push : Used sw_push symbol as switchs
* Diode : As diodes are important for row and column connections, I used 1N4148 diode as it's a basic ideal choice for DIY keyboards and easy to find in small electronics markets. 

I started by placing switches devided in 2 parts left and right. Annonated the keys on the left side from 1 to 32 and on the right side from 33 to 65

Added diodes on every switches annonating them the same number as switches. 

Wired them in rows and columns. I used 2 colors in wires for better visibility
* Red : for rows 
* Green : for columns

[Wiring image here]

connected all switches in 
* 16 columns
* 10 rows
