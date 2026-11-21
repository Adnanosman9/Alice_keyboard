<img width="1119" height="539" alt="Screenshot 2026-11-20 152346" src="https://github.com/user-attachments/assets/ca3172fa-48d8-436b-b840-6fc5c6272fc0" />

# Alvonomic

### This is an alice style keyboard

It has 65 keys

## Key Features
* Brain - It has a pico as braim as it has enough pins for a larg keybord
* Firmware - It usws QMK firmware built with QMK MSYS
* Keys - It has 65 keys (32 on left and 33 on right)

# Layout

This keyboard is built in Alice style. So, it has 2 sides. 

The layout was built using [Keyboard Laoyt Editor](https://www.keyboard-layout-editor.com/#/)

<img width="1067" height="395" alt="Screenshot 2026-11-19 142240" src="https://github.com/user-attachments/assets/95bdc6e7-342b-4aa5-aa70-cc3d44d0ca7b" />

Compulsory sketch for this layout was geenrated with [swillkb](http://builder.swillkb.com/)

# The board

The board schematic and PCB is made in KiCAD 10. 

Tried to keep all files minimalistic and easy to understand. 

## Schematic

<img width="1270" height="896" alt="image" src="https://github.com/user-attachments/assets/dff36810-5965-40c7-9850-814e47f2b5a0" />

The schematic has all the details you need to understand it. 

Here is also a pico diagram if u need

<img width="1129" height="920" alt="Screenshot 2026-11-19 124949" src="https://github.com/user-attachments/assets/0f7754b7-e13a-46fc-97d4-d4adde9afa2c" />


## PCB

The board is made in PCB editor of KiCAD

The layout is arranged using [KLE Placer](https://github.com/zykrah/kicad-kle-placer) plugin

It uses Kalih hot swap socket switches footprint to make it hot swappable. 

The board has 2 layers. 

<img width="1261" height="511" alt="image" src="https://github.com/user-attachments/assets/57c4fcfb-1441-4f3e-af1b-09f85969beba" />

<img width="863" height="463" alt="image" src="https://github.com/user-attachments/assets/47240429-5092-4139-b9eb-efc1398edb71" />


# The enclosure

The case to hold the keyboard is built using Fusion 360

This keyboard uses sandwich mount mechanism. 

The wall of the case is 5mm (2mm inner edge and 3mm outer edge) 

It has 3 parts
* Case
* Switch layer: The layer that holds the PCB hanging with switches attached
* Top layer: The layer that holds the switch layer attached with the case.

To attach all parts, I used M2 heat inserts to insert M2 screws.

<img width="899" height="490" alt="Screenshot 2026-11-20 152358" src="https://github.com/user-attachments/assets/9d32b24e-7854-47b0-a16a-ad81ffef12e8" />

## Case 

<img width="1408" height="704" alt="image" src="https://github.com/user-attachments/assets/d1c4145d-46f6-4018-b901-766f735c66b2" />

## Switch layer 

<img width="1392" height="724" alt="image" src="https://github.com/user-attachments/assets/22f6a495-183a-4471-aafd-3bb8bd2abec6" />

## Top Layer

<img width="807" height="336" alt="Screenshot 2026-11-20 150431" src="https://github.com/user-attachments/assets/10561b65-b72c-4ba5-8511-49335be9c722" />


# BOM

| Type | Product | Reason | Link | Number | Price (in USD) |
| :--- | :--- | :--- | :--- | :--- | ---: |
| MCU | Raspberry Pi Pico | This is the main head | [RoboticsBD](https://store.roboticsbd.com/raspberry-pi/1599-raspberry-pi-pico-robotics-bangladesh.html) | 1 | $7 |
| Switches | 3 PIN RK 35 PCS BOX SWITCH | Main switch of the keyboard | [Vibe Gaming](https://vibegaming.com.bd/product/royal-kludge-coffee-3-pin-rk-35-pcs-box-switch/) | 2 (one box has 35 switches; need 65) | $24 |
| Sockets | Kailh hot swap socket | To keep the switches safe from soldering | [KeeBD](https://keebd.com/products/kailh-mx-hotswap-sockets?srsltid=AYCX9vItRFrba52Sznx3OyVxSVSZ6HQtzewSawFc_UnNEYX08d0Pu2D8) | 7 (1 packet has 10) | $22 |
| Diodes | 1N4148 SMD - SOD 123 | For column and row connection | [Daraz](https://www.daraz.com.bd/products/100pcs-schottky-diodes-smd-diode-0805-sod-123-1n5819-1n4007-1n4148-sod123-sod-323-1206-1n4148ws-1n5819ws-b5819ws-sod323-i1613397264-s12729157906.html?) | 1 | $3 |
| PCB | JLCPCB | To hold the keys | [JLCPCB](https://jlcpcb.com/) | 1 | $44 |
| Physical parts | Locally printed | Main case | - | Case, Top, and switch layer | $10 (expected) |
| **Total** | | | | | **$110** |

# Tool summery and inspiration

This keyboard is a hobby project inspired from Unique and pretty designs of ALice style keyboards

Tools I have used
- [KiCAD](https://www.kicad.org/)
- [Fusion 360](https://www.autodesk.com/products/fusion-360/overview)
- [KLE Placer](https://github.com/zykrah/kicad-kle-placer)
- [Keyboard Laoyt Editor](https://www.keyboard-layout-editor.com/#/)
- [swillkb](http://builder.swillkb.com/)
