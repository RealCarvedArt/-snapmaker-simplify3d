# Snapmaker 2.0 - Simplify3D Profiles
![s3d](https://user-images.githubusercontent.com/78761379/151668325-55a1a181-8240-4961-992f-4c3ba77e63f4.jpeg)

This repo contains Simplify3D slicer profiles specifically made for Snapmaker 2.0 3D printers.

![snapmakers](https://user-images.githubusercontent.com/78761379/151666961-fd520123-3e0f-47ac-8923-9fed15d056e9.png)

- [ ] Includes settings for PLA, ABS, PVA and Nylon

- [ ] Includes commented custom starting and ending scripts:


## G-Code
```
; Snapmaker 2.0 startingGcode
M140 S[bed0_temperature] ; Set heated bed temp
M104 S[extruder0_temperature] T0 ; Set extruder temp
G28 ; Home all axes
M107 ; Turn fan off
G90 ; Set all axes to absolute
G1 X-12 Y10 F3000 ; Move to X-12 & Y10 & set the feedrate to 3000mm/min
G1 Z0 F1800 ; Move to Z0 & set the feedrate to 1800mm/min
M109 S[extruder0_temperature] T0 ; Wait for extruder temp
M190 S[bed0_temperature] ; Wait for heated bed temp
G92 E0 ; Set extruder position to 0
G1 Z0.15 F1200 ; Move Z to .15mm
G1 E11 F300 ; Extrude 11mm of filament at 300mm/min
G1 X10 E20 F1200 ; Extrude 20mm and slow wipe extruder
G1 Z0.5 F4000 ; Lift Z to .5mm
G92 E-1 ; Set filament position to -1
G1 E0 F200 ; Move filament position to 0 & Prime the extruder
; End of startingGcode
```
```
; Snapmaker 2.0 endingGcode
G1 E-1 F300 ; Retract the filament a bit before lifting the nozzle
M104 S0 ; Extruder off
M140 S0 ; Heated bed off
M84 ; Disable steppers
M107 ; Turn fan off
G28 Z ; Home Z
; End of endingGcode
```

- Does NOT include backlash compensation in starting script (Example):
M425 X0.02 Y0.02 Z0.02 F1 S0

***NOTE: Backlash compensation should only be added if you have performed a backlash calibration and use the numbers from your test. Simply add the gcode to the beginning of your Starting Script.***


## Build Platform Dimensions:
- [ ] Snapmaker 2.0 A350 Build Platform:<br>
X-Axis = 320<br>
Y-Axis = 350<br>
Z-Axis = 330<br>

*NOTE: Could be adapted to A150 and A250 by updating the build platform dimensions:*<br>
*• "Simplify3D" → "Edit Process Settings" → "G-Code" → "Update Machine Definition" → "Build volume"*

- [ ] Snapmaker 2.0 A150 Build Platform:<br>
X-Axis = 160<br>
Y-Axis = 160<br>
Z-Axis = 145<br>

- [ ] Snapmaker 2.0 A250 Build Platform:<br>
X-Axis = 230<br>
Y-Axis = 250<br>
Z-Axis = 235<br>


# How to use

These profiles are exported as FFF config files, to import them:<br>
- "Simplify3D" → "File" → "Import FFF profile" and import each profile.
