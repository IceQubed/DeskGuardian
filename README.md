# DeskGuardian

This is a project designed to teach basic KiCad usage. The end goal of the project is to produce an active desk ornament used to signal that you are not to be disturbed, using lights and a distance sensor.

This project was created by Ben Adamson and is licensed under the MIT License.

## Instructions

The following instructions give a high-level overview of the steps required. More detailed information about KiCad usage is available online. The instructions are intended to be followed sequentially, completing each section before beginning the next.

#### Setup

1. Install KiCad from [their website](https://kicad-pcb.org/)
2. Edit KiCad settings to disable 'Center and warp cursor on zoom' if desired
3. Add a title and date to the page using File -> Page Settings
4. Take a look at the 'Place' drop-down menu to see keyboard shortcuts for placing components and connections

#### Adding new libraries

1. Download the circuit symbol, PCB footprint and 3D model for the HC-SR04 ultrasonic distance sensor from [SnapEDA](https://www.snapeda.com/parts/HC-SR04/ICS/view-part/)

2. Create a 'Libraries' folder inside your KiCad project folder, create subfolders for each file type (symbols, footprints, 3D models) and extract the component files you just downloaded into these folders

3. Within the main KiCad window (not EEschema), open the Preferences -> Manage Symbol Libraries tool. Select the 'Project Specific Libraries' tab, click the folder icon to add an existing library, then select the .lib file you added to the project folder earlier

   *Notice the '${KIPRJMOD}' path substitution variable. This makes the path relative to the root folder of your project, making the project 'portable' as it does not reference your PC's folder structure outside the project*

4. Repeat this step with 'Manage Footprint Libraries' to add the footprint library

5. Download the circuit symbol, PCB footprint and 3D model for the 1825910-6 push-button switch from [SnapEDA](https://www.snapeda.com/parts/1825910-6/TE%20Connectivity/view-part/) and repeat the previous steps to add this component to the libraries

#### Schematic Basics

1. Using the 'symbol place' tool, search the menu for Arduino Nano, and select v3.x

2. Move the component name and designator for the Arduino from the bottom of the component up to the top right hand corner of the component so that they do not block pins 4 and 29

3. Place 'GND', '3V3' and +5V' power ports and connect them to the Arduino Nano using the power port and wire tools respectively:

   <img src=".\Images\SchStep3.png" alt="SchStep3" width="300" />

4. Place three 'LED' symbols and three 'R' (resistor) symbols. Connect the anode (wide side of symbol) of each LED to a resistor. Connect the other side of the resistor to the arduino pins 9, 10 and 11 respectively, then the other side of each LED to ground. Use the 'Label' tool to name each of the wires from the Arduino.

5. Edit the 'Value' field of each resistor, changing it to 100 - the LEDs should now be connected as shown below:

   <img src=".\Images\SchStep5.png" alt="SchStep5" width="500" />

6. Connect the HC-SR04 as shown below:

   <img src=".\Images\SchStep6.png" alt="SchStep6" width="400" />

7. Add three pushbutton switches (1825910-6) to the schematic together with a 10K pull-down resistor for each switch. Add net labels to the 'outputs' of the switches:

   <img src=".\Images\SchStep7.png" alt="SchStep7" width="300" />

8. Connect wires with the same names as those used on the buttons onto the Arduino pins D2, D3 and D4 - even though there is no wire drawn between the pin and the button they will still be connected as they have the same net name:

   <img src=".\Images\SchStep8.png" alt="SchStep8" width="200" />



###### Useful keyboard shortcuts - Schematic Design

| Key    | Usage                                                 |
| ------ | ----------------------------------------------------- |
| a      | Place symbol                                          |
| w      | Begin wire                                            |
| k      | End wire                                              |
| p      | Place power port                                      |
| CTRL+h | Place global label                                    |
| c      | Copy (hover over what you want to duplicate)          |
| m      | Move (hover over what you want to move)               |
| r      | Rotate (can be used while moving, copying or placing) |
| e      | Edit symbol properties                                |
| x      | Mirror symbol (x axis)                                |
| y      | Mirror symbol (y axis)                                |



#### Annotating and assigning PCB footprints

1. Click the 'pen and paper' icon to annotate the schematic symbols. Use the default settings and press "Annotate". The reference designators for the symbols will be populated and the schematic will be complete:

   <img src=".\Images\AnnotateStep1.png" alt="AnnotateStep1" width="800" />

2. Click the 'Assign footprints' button (to the right of the ladybug symbol) to open the footprint assign window. In the central column the components in the schematic will be listed. In the left-hand column footprint libraries can be selected. On the right-hand column the footprints in each library can be selected. The Arduino Nano and HC-SR04 should be automatically selected, however you will have to select PCB footprints for the other parts of the circuit:

   <img src=".\Images\AnnotateStep2.png" alt="AnnotateStep2" width="800" />

3. Select the footprints for the non-auto-populated parts as follows:

   <img src=".\Images\AnnotateStep3.png" alt="AnnotateStep3" width="600" />

