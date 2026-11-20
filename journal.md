---
title: "Alice Keyboard"
author: "Adnanosman9"
description: "Custom Alice-layout mechanical keyboard"
created_at: "2026-11-15"
---

# Project journal

# November 15th: Journal 1 - The schematic and the layout

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

**Total time spent: 1h**
---

# November 15th: Journal 2 - Wiring the head

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

**Total time spent: 1h 6m**

---
# November 16th: Journal 3 - The biggest mess

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

**Total time spent: 32m**
---
# November 16th Journal 4 : Refactor

Using KLE placer plugin worked properly, but here was a problem, during making the schematic I placed 8 keys in a row and 5 in a column, which was technically correct and practically here is an issue. Like a column has 5 keys and another have 4 another 3 and a row has 9 keys. Basically this was not static. 

So, I hade to do some changes in the schematic rows and columns. 

then rearranged the switches in the PCB. 

To start the PCB, I needed a border -

I made the layout order in dxf format for [swillkb](http://builder.swillkb.com/)

Using this keyswitch layout as a reference I made the the border in Fusion 360

<img width="801" height="498" alt="image" src="https://github.com/user-attachments/assets/bd426601-dd88-4c0c-bcc2-b65664205799" />


Making this border was kinda difficult as I was trying to make something unique but feels like a mess. 

After many changes, reformations, deletions, I made myy border using spline tool. 

Exported it in DXF format and imported in PCB editor as a graphic for edge cuts

But in PCB editor I got an issue. The edge cut is not working...............

<img width="480" height="298" alt="Fah Desert Sunset GIF" src="https://github.com/user-attachments/assets/cc2fbfee-d422-4949-8451-75e2d374a8b9" />


<img width="1026" height="518" alt="image" src="https://github.com/user-attachments/assets/4a47fccc-0dc5-4d8b-b6f3-dae389877979" />


I faced it for the first time so I did not know what is the issue here. 

After some searches I found out that the main issue is the graphic I imported is not grouped properly. 

And the reason is KiCAD does not support spline lines. So I found a solution and I made the same border using **3 point arc** tool. 

And this time it was imported fine and working as an edge cut..

<img width="1017" height="436" alt="image" src="https://github.com/user-attachments/assets/411f2d34-12b6-4d17-9c41-dba898b444ec" />


### FInally rearranging and making a border ends here. 

**Total time spent: 1h 18m**
---

# November 16th: journal 5 - Wire the hell

I started the switches all pre arrangement was done.

During wiring I found and issue and it was diodes. Basics diodes are simply too bulky to attach under a switch will hot swap socket. 

So I needed to change the diode footprint. 

I tried several footprints such as smd and tht versions. after some searches I used SMD-D-SOD-123 footprint as it's good for handsoldering
<img width="974" height="309" alt="image" src="https://github.com/user-attachments/assets/38d41523-5b96-4c62-9c11-355795b3c664" />


Diodes arrangement was done but another issue was wirign the down slope switches. Switches in down slope was hard to wire in defalut 45 degree turns. 

So I used curve but curves were making it like waves. After some searches I got to know about free angle mode in interactive router setting in KiCAD, then after this setting I wired the switches properly

For this setting
* Click on the route button next to file and edit button on very top of the window.
* Go to interactive router setting
* Click on Highlight collison and then check free angle mode.

  <img width="654" height="406" alt="image" src="https://github.com/user-attachments/assets/0e9ae0ed-b931-426e-a0f0-a64381761d0e" />


**Now you can route in free angles instead 45 degree default turns**

### Finally wiring all the columns and rows was done. 

**Total time spent: 54m**
---
# November 16th: Journal 6 - Head is not working

As columns and rows were routed previously. This was high time to route all the switches to the pico and get the hardest part of the project done. 

### Buuuttttttt here was an issue in the schematic. 

My pico symbol had an issue and the issue was that the pico symbol uses pin names as both pin name and number. But kiCAD PCB editor tracks pin via their number not names, so during wiring switches to the pico, it was not working. 

<img width="576" height="453" alt="image" src="https://github.com/user-attachments/assets/61cc1acc-5799-47f1-81e2-342cedc3f2f3" />

I got to know about it after some findings. I found a suggestion to edit the symbol in KiCAD. 

I edited the symbol by changing names to number in pin number and saved it. 

<img width="1132" height="899" alt="Screenshot 2026-11-19 124925" src="https://github.com/user-attachments/assets/102cef7c-ed19-4afb-9c95-f7f4643dcf74" />

### It actually worked, The PCB editor was able to track pins and showing blue traces. 

I just simply routed them the same way I did for switches. 

To make it compact I made some turns too short angle that the electric may get stuck at some points. 

So, I used **Round Tracks** plugin but some round round tracks were so round that these were overlapping. 

I had to manually solve and fillet some tracks and vias. 

### FInallyy the head was fixed and the switches were routed properly. 

**Total time spent: 1h 12m**
---
# November 17th: Journal 7 - Align 

The border design was good but the top part was curvy so maybe this will face some issues during mounting it in real. 

So I decided to make it's top border plain 

Redesigned the top part in Fusion and reimported in KiCAD again. 

<img width="938" height="419" alt="image" src="https://github.com/user-attachments/assets/0d6dc5c8-2f53-4023-9970-7bb4cf83ad4b" />


Mounting pico was good but had to reroute the wire track again as the pico moved. 

### I needed to mount the switches in middle of the border so that it becomes easyy to make the physical parts in Fusion.

I edited the Pico footprint. I just removed a graphic, nothing major:

* Removed the **possible antenna keepout** mark
  
  <img width="350" alt="Removed USB cable mark" src="https://github.com/user-attachments/assets/0ca02902-9f23-49a3-b5f6-736ad73c481b" />

* Removed the USB cable mark on top
  
  <img width="200" alt="Removed antenna keepout mark" src="https://github.com/user-attachments/assets/3d8e8377-f511-4db6-b8c2-49285bcf2877" />


These two parts were making two issues
- **possible antena mark** was giving a routing error for it's own hole on the side
- **USB cable mark** was making issues in center calculation. KiCAD was counting it as main part and moving the vertical center from actual center position of the PCB

Grouped the switches and pico to get it's center. 

Aligned the horizontal center of switch group and the border. 

<img width="792" height="331" alt="image" src="https://github.com/user-attachments/assets/6fb0a3d4-ce16-4c08-990f-4b77c96de87d" />


Aligning vertical center was not quite good so manually placed the border on the top of pico. 

<img width="581" height="381" alt="image" src="https://github.com/user-attachments/assets/f8cb3807-3698-43ba-a169-bc40ba5ee64c" />

**Total time spent: 1h 5m**
---

# November 17th Journal 8 - Whatever!!!!!!!!!

### As the 
* Schematic was done
* Switches were routed
* Pico was connected
* Border was aligned 

It was time to move to build the physical side. 

But for the further part I need the exact calculation of my PCB for the holes, walls etc calculation. 

I tried to plot dxf of the PCB, tried several times but Fusion was failing to import the DXF. 

I imported the dxf in KiCAD and got that the top line was not in the DXF. 

<img width="429" height="202" alt="Screenshot 2026-11-19 193740" src="https://github.com/user-attachments/assets/eee2ec06-9d65-44b5-b7d9-400b1f73462a" />


I tried in man ways. Later I found an issue that the wall thickness maybe stopping from working. 

So, I increased the wall thickness and guess what! 

This time top layer was generated in the dxf but still it was error while importing in Fusion. 

I tried solve this issue in inspace too. But still no solution. 

Later I tried to do this with SVG insted DXF. But working with SVG is quite hard. I found it hard, not sure about others. 

### No solution worked, so I had no other way than working with step as it's the best possible way for Fusion. 

Before exporting the 3d step file, I added 3d model of MX switch on every switch footprint for better visualization in Fusion. **(It was quite time taking)**

At the end the step file generation worked and it was imported in the Fusion properly makign it easy for further design work. 

<img width="1130" height="556" alt="image" src="https://github.com/user-attachments/assets/359025ce-2f07-4bc0-b41c-3042e95efc25" />


Whatever!! some issues were here those could not be solved by me, but still here is a way. 

**Total time spent: 1h 20m**
---

---
## -------------Chapter 2 : CAD is a mess-------------------
---

# November 17th: Journal 9 - Started CAD

As the PCB was done, it was time to begin the next chapter

Started from the case

Used a prebuilt keyboard (I got from github)as reference for calculation. 

Used the previous dxf border as sketch and using offset tool I made the wall. 

<img width="945" height="532" alt="Screenshot 2026-11-19 203922" src="https://github.com/user-attachments/assets/81ec2b69-a35e-4ccb-8873-a066fbdce36a" />


I decided to make it sandwich mount so I needed to make wall with a inner edge. Made the case in 3 step
* Bottom part
* Inner edge wall to place the switch layer to hang the pcb. 
* Outer edge wall to fit the top layer

### Then I needed the switch layer. 

Started the switch layer from using switch hole layout DXF I got from [swillkb](http://builder.swillkb.com/)

Used the previous border around it to make the top layer sketch. Extruded the top layyer 1.5mm and keeping the holes in the extruded layer. 

Added the PCB step model in the top layer model and hanged it under the top layer the way it will hang in real. Grouped them in one model making it a complete **Top Layer**

Added this top layer on the case making the Case work slightly done. 

<img width="796" height="475" alt="Screenshot 2026-11-19 204433" src="https://github.com/user-attachments/assets/1ee19bf7-ca9a-443c-bd5d-fb00ebc9b6ba" />

**Total time spent: 1h 20m**
---

# November 18th: Journal 10 - The top

I needed to make the top layer to hold the switch layer with the case. 

I started it's sketch from top layer sketch I got from [swillkb](http://builder.swillkb.com/)

Used the same previous border as it's border. 

Extruded it 6mm. 

<img width="1521" height="875" alt="image" src="https://github.com/user-attachments/assets/289f7fa7-12f7-4e91-9159-47f1561ed6e8" />

Imported it in the case model tab. Aligning it on the top of the case and switch layer. 

Now the parts modeling is done but some serious parts are left. 
* Screw holes to connect the Top layer with the case. 
* Side cut out to open space to connect cable to the pico


To check if everything is going is well or not I started adding keycaps on the switches. 

Added 1u cap on the normal switches and longer keycaps on the switches where needed. 

<img width="926" height="403" alt="image" src="https://github.com/user-attachments/assets/9b90900b-6907-4b93-bd1a-2063dfedd6f1" />

**Total time spent: 2h 28m**
---

# November 18th: Journal 11 - The Pretty one

I wanted to make it look good before going further. 

So I added some colors on the objects. It was looking quite good. 

<img width="935" height="349" alt="image" src="https://github.com/user-attachments/assets/9d2fed2a-fa67-411e-af61-e1fbd3684fb4" />

### But I found some issues in the walls.

To attach the top layer with the case I needed to insert screw threads and holes. But the walls were not thick enough to hold a heat inseart in it. 

To insert a heat insert in the walls I needed atleast a 3.6mm thick wall only for holes and the heat may melt some pats so it needs a thicker wall. 

I decided to add ears in 4 corners for screw holes. But the keyboard was already too bulky and the distance to closest key was nearly 23mm. 

Adding ears in this will make the keyboard too bulky and hard to use also increasing printing amount.

I literally underestimated how big every mm distance can be. 

**Total time spent: 25m**
---

# November 18th: Journal 12 - Solve the mistake

As previously, found out some issues. It's time to solve them. 

### So, It was better to redesign the case considering these issues. 


I started redesigning from making the border the same way I did first time. 

This time I kept the border close to the switch hole to save width for walls instead wasting on PCB. 

<img width="825" height="374" alt="image" src="https://github.com/user-attachments/assets/f979c3f8-5a70-43d2-afc4-d9eba2168b82" />


USed this border in KiCAD as edge cut to reshape the PCB in the new size. 

Imported the new shape PCB in the Fusion as step model. 

<img width="1019" height="661" alt="image" src="https://github.com/user-attachments/assets/31bd39e3-acbc-461b-a54f-de1a1a22dbce" />


Again used the new border and made the bottom layer and the walls. 

After many changes and calculation I made the wall 5mm thick. 2mm inner edge and 3mm outer edge. 

<img width="950" height="419" alt="image" src="https://github.com/user-attachments/assets/baeeb6ed-1ff2-4ca0-88cf-0a70e755e69b" />


Made the switch layer again as well. 

Made the switch layer the same way I did before. 

This time made a cutout for pico too in the switch layer. 

Placed the PCB under the switch layer properly so that I can calculate if the wall height is enough. 

Imported the switch layer in the case tab and aligned it on the case. 

<img width="404" height="264" alt="image" src="https://github.com/user-attachments/assets/61bc5dcc-9fa4-42c7-827b-e37bcb7f55cb" />

### This time it was quite good looking too. 

**Total time spent: 1h 25m**
---

# November 18th: Journal 13 - Reassemble

Aligned the PCB step file with the switch layer and grouped them into one object. 

Aligned the group switch layer on the case

Made a cut in the case to check if alignment is good from in side. 

**ANd yess! This was good.**

rechecked the wall thickness and after changing some offset and extrusion, moved to build the top layer. 

Made the top layer the samw way I did before.

Deleted some small overlaping extruded part to fit the switches. 

<img width="807" height="336" alt="image" src="https://github.com/user-attachments/assets/6e9374ef-cad5-4fc7-aafa-8834cf3bbf8b" />


Imported it in the case tab and aligned it on the case. 

Placed the keycaps on top of the switches. 

Keyboard modeling part is done till now. 

<img width="620" height="385" alt="image" src="https://github.com/user-attachments/assets/cbb51d1c-9012-4e64-b13d-04c4a0eae6da" />

### We have reassembled the Keyboard part as we had done before. 

**Total time spent: 50m**
---

# November 18th: Journal 14 - Fit the parts

As part modeling was done

Now it was time to make the screw holes to hold all the parts together. 

I mistakenly made screw holes one top layer which was cutting through the pcb layer, needed to delete them. 

<img width="374" height="374" alt="dog-scroll" src="https://github.com/user-attachments/assets/cb3e09eb-ca5a-4934-9874-61e4fdfd4b54" />


for proper inserting, I made the holes on the case outer walls. But the outer edge is too thin so it's hard to enter a heat inster in it. So needed to make only screw holes. 

Made the screw holes on the 4 corners

<img width="775" height="444" alt="image" src="https://github.com/user-attachments/assets/e17bd30b-49da-43d1-9f85-ba8e5a501b84" />

Now I needed to make same screw hole on the top layer, but it was quite hard to make the same holes. 

Later I found out about **Edit in place** option. Easily made the same hole on the top layer using this mode. 

<img width="823" height="387" alt="image" src="https://github.com/user-attachments/assets/c4e01563-f226-42ff-89eb-c7acf43fe8b8" />


### Attachment done. 

**Total time spent: 40m**
---

# November 18th: Journal 15 -  Ears are the pillars

Fitting the screws was done but....!

screw upper diameter was crossing the wall, so I decided to make ears on the corner so that it does not break

Deleted previous screw holes made ear corners on the case and top layer. 

As ear corners were thick enough to hold m2 inserts so I made m2 heat insert holes on them

Now it fits properly. 

Inserted 8 M2 heat insert 3d model on the 4 corners of both case and top layer. 

Also added 4 screws on top through the heat inserts

<img width="606" height="328" alt="image" src="https://github.com/user-attachments/assets/bb657b88-ceb6-434e-9ef2-3af55b090b64" />


But, 4 round circles on the corners were looking too bad. So I decided to blend them with the case. 

So I edited the sketch, made some lines connecting to the case wall like a tangent from the circle ear border. 

And this was looking good even better than all previous designs. 

To make the final design added colors on the profiles. 

<img width="775" height="373" alt="image" src="https://github.com/user-attachments/assets/13f4b6ea-c9cd-4983-b2b4-898d71caf79c" />



### As usual I again did a mistake.
During the blend extrusion, circle ears were extruded from inside and these were taking place from inside PCB area. So needed to use spline tool to cut out the circles from inside

<img width="814" height="419" alt="image" src="https://github.com/user-attachments/assets/d7ce1a5c-6962-4b56-8461-5a8187b9c9cb" />

### And personally I am impressed with those colors. 

**Total time spent: 1h 42m**
---

## Journal 16 - The final hit

### Now the final touch

To make the cable connection space for pico, I had to make some cuts in front of the pico cable area.

<img width="741" height="412" alt="image" src="https://github.com/user-attachments/assets/4ce3523b-c64f-4ca6-9e6f-8e505bbfb18c" />


edited the switch layer so that it does not over lap the pico. edited the switch layer so that it does not over lap the pico

had to reimport a keycap as it was overlapping


> ### Finally, Checked everything again, all was ok as planned. everything was aligned properly. Keyboard was lookign good too. Also it was well fitted without compromising in compact size and making it too bulky.

**Total time spent: 1h 16m**

## Everythign is fit and fine. Saved everything and exported all models and keycaps in `.step` and `Fusion archive` file. 


### The journal ends here. Hope the journal was helpful. I tried my best to document everything in my building process. Hpe I did not miss anything. 



<img width="899" height="490" alt="image" src="https://github.com/user-attachments/assets/7d76b2d4-c420-4af2-b1a1-9995d9d9a64e" />

<img width="1119" height="539" alt="image" src="https://github.com/user-attachments/assets/48180f7a-1522-4c25-9d70-f073726610c6" />

<img width="520" height="532" alt="baby-chick" src="https://github.com/user-attachments/assets/44222d59-8af6-4994-9c66-e8b8f47e7248" />


## Lapse are here

[Alice_1](https://lapse.hackclub.com/timelapse/vRUkqbIR1GNu)

[Alice_2](https://lapse.hackclub.com/timelapse/FAn1JrFx1Ehw)

[Alice_3](https://lapse.hackclub.com/timelapse/XYBnWtpQnxaK)

[Alice_4](https://lapse.hackclub.com/timelapse/bvH86aeBpvCf)

[Alice_5](https://lapse.hackclub.com/timelapse/yhQVpwzFq72U)

[Alice_6](https://lapse.hackclub.com/timelapse/eEiHiZV7hcFO)

[Alice_7](https://lapse.hackclub.com/timelapse/zV_VjTVJjf_t)

[Alice_8](https://lapse.hackclub.com/timelapse/Fsgb9ltkq90S)

[Alice_9](https://lapse.hackclub.com/timelapse/ReRCCm1_bAK2)
