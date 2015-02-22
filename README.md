#nodela
##Browser Interface for the Roland MDX-15/20

Nodela was developed for PCB fabrication using the MDX-15/20 milling machines. It is a browser-based interface for quickly sending PCB designs and toolpaths from an Eagle `.brd` file to the milling machine.

###Install

This version must be run on a Window's PC, with the Roland MDX-15/20 drivers already installed. Using the Modela without any drivers requires further research and probably some USB sniffing...

Node.js and npm must already be installed on the Window's PC.

Download  .zip, or using Git:
```
git clone https://github.com/andySigler/nodela
```
Install dependencies with npm:
```
cd nodela
npm install
```
###Use

To run with node:
```
node nodela.js
```
The script will attempt to open `localhost` in your default browser, and the interface will prompt you to drag your `.brd` Eagle file onto the screen.

When installing the Roland driver, the machine will have been assigned a port name like `com3`. To change this, open `nodela.js` in an editor and edit the following line to match your setup:

```
var rolandPortName = 'com3';
```



###Sofware Features

#####Node.js script
 - Creates final file and writes to MDX-15/20 drivers

#####Drag .brd Eagle file into interface to parse the gerber
 - Recognizes Wires (pre-designed toolpaths)
 - Recognizes Part Holes
 - Recognizes Vias

#####Jog the mills's head to select the cut's origin
 - Mill anywhere on your copper by jogging the head around with HTML5 buttons

###What nodela does NOT do

#####Does NOT mill Routes
 - Toolpath lines for making Routes must be designed in eagle using the Wire command (these are simple lines)
 - I prefer drawing these by hand, but for the lazy check out this great ULP: [fablab-mill-n-drill.ulp](http://mlab.taik.fi/paja/?p=1874)

#####Does NOT interpret arcs or circles
 - The current version parses Wires in your .brd file, and assumes they are all straight lines
 - If you want a curve in your mill job, draw tons of little lines, or use the ULP linked to above (which just draws tons of little lines...)

###Included in this repo

Repository also includes a redesigned bed plate, in order to avoid using any tape. The `roland_bed.ai` file inside `./resources` was designed to be laser cut into flat delrin. Threaded inserts are then hammered in, and washers are used to hold down the PCB.