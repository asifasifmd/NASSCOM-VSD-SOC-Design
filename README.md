# NASSCOM-VSD-SOC-Design
## VSD_SOC_Design using OpenLANE paltform and Sky-130nm under the guidance of Director and co-founder of VLSI System Design (VSD) Corp. Pvt. Ltd, *Kunal Ghosh*

## Table Of Contents
  1. Inception of open-source, OpenLane ans sky130 PDK
  2. Good Floorplan Vs Bad Floorplan and Introduction to Library Cells
  3. Library cell design using Magic Layout and ngspice characterisation
  4. Pre-Layout timing analysis and and importance of good clock-tree
  5. Final Steps for RTL2GDS using TritonRoue and openSTA

     
## Day 01: Inception of open-source, OpenLANE and Sky130 PDK

### Arduino UNO introduction
The figure shown below is Arduino Uno whsich is used for several applications such as educational projects, prototyping, robotics, IoT, environmental monitoring, wearable technology, art and interactive installations, agriculture etc..
![Screenshot (140)](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/40e48abc-58a4-4c04-bd81-2594a57156d6)

### Block Diagram of a processor
The below shown figure is the Block diagram of a processor consistin of of **Memoty Chip** and other supporting modules such as SDRAM, SPI, GPIO, PWM, I2C etc..
![Screenshot_20240511_152252_Chrome](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/54de3256-48a5-4192-8c82-1decdda1193d)

### Important components of Chip
   1. **Pads**: It is used to sent signals inside and outside of the chip and executes the instructions.
   2. **Core**: It is a place where all digital logics are present.
   3. **Die** : It is place that contain the ICs.
![Screenshot_20240511_153034_Chrome](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/9497bdeb-29d4-4383-815e-fc6fbd7b4b4a)

### Digital AISC Design
   1. **RTL design**: In the OpenLane flow, RTL (Register-Transfer Level) design tools are used to handle the initial stages of the digital design process, 
      converting high-level descriptions of a circuit's behavior into a lower-level representation suitable for synthesis and further physical design steps. 
      OpenLane integrates several open-source tools to facilitate the RTL design, synthesis, and verification stages.Some of the RTL design tools used in OpenLane 
      are ABC (A System for Sequential Synthesis and Verification), yosys, OpenSTA (Open Source Static Timing Analyzer).
   2. **EDA tools** : Electronic Design Automation (EDA) tools are software applications used for designing electronic systems such as integrated circuits (ICs), 
      printed circuit boards (PCBs), and other complex electronic components. These tools facilitate various stages of the design process, from initial concept 
      and design entry to simulation, verification, and physical implementation. Some EDA tools use in OpenLane are OpenSTA (Open Source Static Timing Analyzer), 
      Fault (Fault Injection and Analysis), OpenROAD (Open Rapid Analog and Digital), Magic, KLayout, SpefExtractor
   3. **PDK data**  : A Process Design Kit (PDK) is a comprehensive set of files and documentation provided by semiconductor foundries to facilitate the design 
      and manufacturing of integrated circuits (ICs). In the context of OpenLane, a PDK contains technology-specific information that enables the tools within the 
      OpenLane flow to correctly synthesize, place, route, and verify an IC design for a particular manufacturing process. Process design rules are DRC, LVS and 
      PEX.
![WhatsApp Image 2024-05-18 at 13 28 49](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/42c38966-ff62-4c2c-9f5e-43f9303af5d7)
 
### RTL to GDS Flow
  1. **Synthesis**: Process of converting RTL to a circuit from the components of SCL(Standard Cell Library).
  2. **Floor/Power Planning**: Its objective is to create required silicon area.
  3. **Placement**: Process of placing the cells on the floorplan rows laigned with the sits.
  4. **Clock Tree Synthesis(CTS)**: Main onjective is to create a clock distribution network for synchronized operations.
  5. **Routing**: Implementing the interconnect using available metal layers.
  6. **Sign-Off**: Physical (DRC and LVS) and timing (STA) verifications are performed. 
![WhatsApp Image 2024-05-18 at 13 28 49 (2)](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/27d75cc3-cbf2-4882-851b-cbcaaae31bc7)

### OPENLANE
OpenLane is an open-source, end-to-end flow for integrated circuit design. It was designed to automate many of the steps involved in designing and fabricating integrated circuits. It provides a complete RTL-to-GDSII flow, including synthesis, floorplanning, placement, routing, and verification. It supports multiple foundries and technology nodes, allowing designers to target different manufacturing processes.
![WhatsApp Image 2024-05-18 at 13 28 48](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/6394d017-439a-4246-bc35-9e39b9f9b964)

### OpenLane ASIC Flow
![WhatsApp Image 2024-05-18 at 13 28 49 (1)](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/a6365e75-2334-4443-9d69-d4f56caf9284)

### OpenLane Prepearion Set-Up Steps
Open the **Terminal** and write the commandes given below
```
cd Desktop/work/tools/openlane_working_dir/openlane/
docker   //to enter into bash-4.2
./flow.tcl -interactive   // -interactive for manual operation
```
Now, **OpenLane** will appear
![image 2c](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/96ada520-0468-4bd4-b66a-40b9833cd4bf)

```
package require openlane 0.9
prep -design picorv32a
```
**OpenLane** Preperation is completed
![image 2](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/a1e6fc8a-bfe4-48eb-bf2e-9a39ff03ba69)

Now,open a new **Terminal** and open the directory **picorv32a** that contain **runs** folder in it. **runs** directory contain a folder with the date of creation (Fro example: 18-05_06-08) and open *mergef.lef*, *config.tcl* and *cmds.log* files.
![image 13](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/0c4f985a-934b-4b74-8963-b6b786cc752a)

### Synthesis
Synthesis refers to the process of converting a high-level description of a digital circuit, typically written in a hardware description language (HDL) like Verilog, into a gate-level netlist. This netlist represents the circuit in terms of logic gates and their interconnections.

Open the **OpenLane Prperation Set-Up** back and synthesise using the command,
```
run_synthesis
```
![image 7](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/79fb2933-a1ee-420a-b433-26a6d181f032)

*Synthesis* process takes some time and after the completion *Synthesis was successful* appears denoting the successful completion of synthesis process.
![image 14a](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/25ba37b9-7d3f-4400-87fb-c6a95582e256)

#### Utilization Factor
Utilization Factor is the total amount of area occupied by *Netlist* in the core.
<br>
Utilization factor = area occupied by Netlist / area of core
![image 8](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/44c9d56c-5438-43bc-80c1-7e4255b6a6fb)
From above picture,
<br>
Utilization factor = (1613 / 14876) = 0.1084

## DAY 02: Good Floorplan Vs Bad Floorplan and Introduction to Library Cells

### Floorplaning
Floorplanning is the process of arranging the major functional blocks of an integrated circuit (IC) within the chip's layout area, optimizing for performance, area, power consumption, and other design constraints.

#### Aspect Ratio
Aspect Ratio is the ratio of height to the width of netlist.
<br>
Aspect ratio = Height of Netlist(W) / Width of Netlist(L)
<br>

After the *Synthesis* process, run floorplan using the command given,
```
run_floorplan
```
![image 14](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/646d1e20-6043-4fed-8015-7fbd12296bfb)

*Floorplan* process taeks some time and after the completion *PDN generation was successful* will appear.
![image 15](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/c5e750a8-c828-47c5-887e-e065a5f24726)

Open other terminal at different directory levels to see the *VMETAL* and *HMETAL* in different files.
![image 21](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/299461ac-0ee3-49cb-83d2-5789fc20977e)

Open *confir.tcl* file present in *18-05_06-08* using the command given.
```
less config.tcl
```
![image 17](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/e3699f00-d913-40ca-84cc-0ed8ef3c57ea)

Open *floorplan.tcl* file present in *configuration* using below command,
```
less floorplan.tcl
```
![image 18](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/d2928454-6ce1-4d7c-ad9f-2c64745b5d3a)

Open *4-ioplacer.def* file present in *floorplan* to see the total DIE area using command,
```
less 4-ioplacer.def
```
![image 20](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/fcf68a2b-8b93-467b-bad4-844d338c98d3)
From the figure,
<br>
DIEAREA = 660685 * 671405
<br>
UNITS DISTANCE = 1000 in Microns

To open the **Magic** write the command,
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image 23](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/cf0e7849-cdc9-4d18-b48f-39a134abbba1)
Now, *Magic* is opened.

Some commands to perform operate the Magic are, 
  1. To select the layout, press 's' and preee 'v' to set layout at the center of screen.
  2. To zoom at a particular part, press *Right click* + *Left click* + 'z'. Press 'z' till the required zoom.
  3. To select an object in layout, keep the cursor on object and press 's'.
![image 24a](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/4b612dd1-d4fe-4be6-91bc-f6bae2e25448)

Logic View after certain magnification.
![image 26](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/9ab1789d-8577-4d3b-a102-90b3e206741f)

To see the information about a component in logic, put cursor on component and press 's to select the component. Now, go to *tkcon 2.4 main* window and give **what** command.
![image 28](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/1dc7d95c-e272-4523-abd1-8dd48f93141e)
![image 29](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/6743cabd-4081-452a-8c22-95597f941dc3)

### Placement
Placement refers to the process of positioning the standard cells and macros (large functional blocks) within the defined core area of the chip layout.

Go to **OpenLane Preperation Set-Up** terminal and run placement using the command given,
```
run_placement
```
![image 31](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/98d27307-edf3-43bb-b293-44e401cd588f)

*Placement* process take some time and *Screenshot taken* will appear after completion.
![image 34](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/33ff798d-7115-48f0-b555-da7dda59b3f8)
Placement process also gives the information about *utilization area* and *padded utilization area*
<br>
**utilization** - 36%
<br>
**utilization padded** - 55%

Open the other **Terminal** now, and open **Magic** for Placement using given command,
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image 35](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/974e7a50-86b7-4810-a0b2-b8726d2d1916)

*Magic* is opened now.
![image 36](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/83c8cc08-0fba-4248-a1d4-8778f08b24bd)

Magnified images of Magic logic.
![image 39](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/b9623588-5bd3-48cb-b389-84115e288d87)
![image 40](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/e76fc921-e096-4886-8af2-310a68086599)
<br>

## DAY 03: Library cell design using Magic Layout and ngspice characterisation

### CMOS inverter creation in SPICE deck

Do git clone using
```
git clone https://github.com/nickson-josevsdstdcelldesign.git
```
<br>

and open *SPICE* using command
```
magic -T sky130A.tech sky130__inv.mag &
```

![image 41](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/3ff12934-42ca-4071-bf39-7372e0b283bc)

<br>
Now the Spice design of Inverter is opened.

![image 45](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/d21c47bd-3ed5-4d0b-ac7f-52787c97a169)
<br>
Use below commands to link SPICE model to Openlane
```
extract all
ext2spice cthresh 0 rthresh 0
ext2spice
```

![image 48a](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/98afb0fc-0747-42be-8bb2-6eb2d1ad0f49)
<br>
Use below commands to install **ngspice**
```
sudo apt install ngspice
```
and use below given command to open *sky130_inv file* do required changes
```
vim sky130_inv.ngspice
```
![image 57](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/b43783c0-825f-4cec-bcce-5bc3f94676fd)
<br>

The spice code is given,
![image 58](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/ad1e2294-4545-4da8-b2b5-cf7a52605fcb)
<br>
To see the **Transient Analysis Graph** of the Inverter use command and to plot the graph, command is-
```
ngspice sky130_inv.spice
plot y vs time a
```
![image 62](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/e7317cb7-0bf7-4eaf-bfa5-39441885c9b9)
<br>

The graph obtained is,
![image 61](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/aca9ca89-110b-4f05-bc16-79c069888e09)
<br>

#### Rise Time Calculation
![image 67](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/0be22bc5-88ea-4d82-aaec-53710183e16d)
![image 69](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/5e1996fd-1aaa-473e-b437-8cf54d030250)
**Rise Time**: It is calculated from 20% and 80% of the output graph.
<br>
Since, VDD is 3.3V, we take 0.66V (20%) and 2.64V (80%) of it.
<br>
From Graph, the rise time is-
<br>
Rise Time = (2.20593e-09 - 2.16547e-09) = 40.46ps
<br>

#### Fall Time Calculation
![image 75](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/acb2a8b8-c768-4d73-9354-9d9e99a3f0e9)
![image 77](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/62d33e1c-32d1-4f17-aec9-beeaa764e79b)
**Fall Time**: It is calculated from 80% to 20% of the output graph.
<br>
From graph, the fall time is-
<br>
Fall Time = (4.6689e-09 - 4.04092e-09) = 27.48ps
<br>

#### Propagation Delay
![image 72](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/8ace525f-4ef2-41a4-91d8-e20669e32b72)
**Propagation Delay**: It is the time taken by the output singal to change its state when the input signal change its state. It is generally calculated at 50% state change from input to output.
<br>
From graph, 50% of VDD is 1.65V.
<br>
Propagation Delay = (2.18645e-09 - 2.15004e-09) = 36.41ps
<br>

The values obtained from graph are,
![image 79](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/f69073c9-25d4-42bf-8a7a-d45ba8f590d6)
<br>

#### Poly.9 correction

Use the below commands to  intake the different cell-parts  such as poly.9, n-well, etc. into OpenLane and to open the magic file.
```
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.dgz
magic -d XR
```
![image 81](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/68a72c51-3041-4279-b039-b54214d5b321)
<br>

Now, the **Magic** file is opened.
![image 82](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/2063657e-a5fa-4354-850a-fec12f5a7edb)
<br>

Use given command in **TKcon.tcl**to load the files,
```
load poly
```
![image 83](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/23f9c1ba-1904-48ce-8f6f-c73e5c7edbb6)
<br>

Cell components created using poly, nwell, and p-well.
![image 87](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/0d435e3f-a0d3-4193-af48-a9d2ad4c6baf)
<br>

Commands are used in **TKcon.tcl** to run the **Magic** file and to run **DRC Check** are given,
```
tech load sky130A.tech
drc check
drc why
load nwell
cif ostyle drc
cif see dnwell shrink
cif see dnwell_missing
feed clear
drc style drc(full)
```
![image 91](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/00025eca-9a88-4568-8826-851070ed11a1)
<br>

To load *n-well types* use command,
```
load nwell
```
*Incorrect* implementation of the nweel.4 type is depicted,
![image 96](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/368f4b14-bb9f-48c6-ad14-aed2f303966c)
<br>

Correctd *nwell types* using **DRC rule book**
![image 97](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/07b83d4f-3084-4bbd-9161-8a3ba7cf98db)

## DAY 04: Pre-Layout timing analysis and and importance of good clock-tree

### Naming of Pins of Inverter in Magic

Open the **Magic** using the command provided from *vsdstdcelldesign* file git cloned before,
```
magic -T sky130A.tech sky130_inv.mag &
```
Now, Inverter design is opened.
Use, the command given to fix the grid dimensions of Inverter in the cell.
```
grid 0.46um 0.34um 0.23um 0.12um
```
![image 2](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/a1b88512-b497-42f3-97c4-6968359013ee)
<br>

Click on *edit* option and go to *Texthelper* to put custon name for pins.
![image 3](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/3e29bc2d-0d8a-4977-b119-ee3170d57130)
<br>

Use given commands to know the function of specified pins,
```
port class input
port class power --> (power for VPWR)
what
```
![image 5](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/979accca-c1d2-4391-a77b-fdd00993bdb3)
<br>

Use command to open **sky130_vsdinv.lef** file in *vsdstdcelldesign* file to see complete information about each specified pin,
```
less sky130_vsdinv.lef
```
![image 7](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/2c6c5aa3-58f7-49e1-bf15-bd8606ab708b)
<br>

### Attaching of Different file configurations to the OpenLane Set_up

Use the command given to open the **sky130_fd_sc_hd__typical.lib** file present in *libs* file.
```
less sky130_fd_sc_hd__typical.lib
```
*Typical* file operates at a voltage of 1.80
<br>
![image 8](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/48b07e51-16c9-489b-83c9-9e520f9afe6b)
<br>

Use the command given to open the **sky130_fd_sc_hd__slow.lib** file present in *libs* file.
```
less sky130_fd_sc_hd__slow.lib
```
*slow* file operates at a voltage of 1.80V
<br>
![image 9](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/dd38db00-6fbc-4b0b-a1c4-2e6b5503e5e6)
<br>


Use the command given to open the **sky130_fd_sc_hd__fast.lib** file present in *libs* file.
```
less sky130_fd_sc_hd__fast.lib
```
*fast* file operates at a voltage of 1.95V
<br>
![image 10](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/7323773e-a9b5-472c-a24d-25e0355c17bf)
<br>

Open **config.tcl** file using the command given and edit the file as per the requirement
<br>
**(Press INSERT button to enable editing of file and press esc + : w + q + ! to come out of the file)**
<br>
![image 13](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/d222f4ea-72ce-4dd4-8683-86ad8e21d28a)
<br>

### OpenLane Set-Up for new cell configurations  

Open a new file and the *OpenLane* in it using the commands provided,
```
docker
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
```
![image 14](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/c5f296f7-2410-4d5e-8463-06014cae1e7b)
<br>

Use the commands given to run the synthesis process.
```
set lefs [glob $::env(DESIGN_DIR))/src/*.lef]
add_lefs -src $lefs
run_synthesis
```
![image 15](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/ae66c8bb-a963-4a52-a494-c60edfaaae9d)
<br>

*Synthesis* process will complete in sometime.
<br>
![image 17](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/fe29d8e0-a599-49b7-b427-1b641db8a007)
From above pictures, 
<br>
Area of picorv32a chip = 147712.918400
<br>
We can see that, **sky130_vsdinv** = 1554 is present in *synthesis* process.
<br>

After the completion of *Synthesis* process, we are given with **tns** **wns** values.
![image 16](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/639e2670-c2d8-4251-bc55-e6810800244d)
<br>

Write the commands given below and run the *Synthesis* process again,
```
echo $::env(SYNTH_STRATEGY)
set ::env(SYNTH_STRATEGY)
ech0 $::env(SYNTH_BUFFERING)
echo $::env(SYNTH_SIZING)
set ::env(SYNTH_SIZING)
echo $::env(SYNTH_SIZING)
```
```
run_synthesis
```
![image 22](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/0c3e15c0-03e9-4ba2-93f3-3ea08aad3ff5)
<br>
*Synthesis* will will complete in time.
<br>

Now, run the floorplan using the command given,
```
run_floorplan
```
![image 23](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/e017e96f-2238-457e-8b88-41b74791a398)
<br>

If error arises in *floorplan* execution use the below commands,
```
init_floorplan
place_io
tap_decap_or
```
![image 25](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/0173aa41-ab28-4242-be05-7b2220843d1e)
<br>

Now, run the placement execution using command provided,
```
run_placement
```
![image 26](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/14357d68-a725-4d14-b761-fd450c600208)
<br>
*Placement* will complete in sometime.

Now, go to other **Terminal** and run command given to open the **Magic**,
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image 33](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/0f806937-3daf-41a8-9887-cc8f2be7923a)
<br>

Now, **Magic** is open.
<br>
  1. Zoom-in the cell by presasing 'z' to required size.
  2. Select a *picorv32a* cell area.
  3. Go to **TKcon.tcl** Terminal and run given command and **sky130_vsdinv** cell will appear.
     ```
     expand
     ```
![image 30](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/92824536-f3b0-4b5e-9242-b48170d60ae0)
![image 32](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/5311d80d-7c34-4660-8bd9-2540c02b0488)
<br>

### New Set_Up for reduced time-delay

Open **my_base.sdc** and **base.sdc** using provides commands and do required change for set-up.
```
vim my_base.sdc
vim base.sdc
```
![image 36](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/4f9ae81e-b47b-4b3d-a2a7-13f53977a6fb)
![image 37](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/fb6701ab-0dfe-48dd-a2b6-47756a7c0fd7)
![image 35](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/af1cfd51-9285-4053-aa75-09cb6e32418b)
<br>

Now, open **pre_sta.conf** file using command provided,
```
vim pre_sta.conf
```
![image 34](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/c3612fe5-107a-4d8c-b0ad-ae23895db96d)
<br>

Now, run **pre_sta.comf** file using given command,
```
sta pre_sta.conf
```
![image 38](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/1b1baec5-c0b6-45d3-bb62-a7fdb1eb66a7)
<br>

After successful completion we can see that tns = -711.5,  wns = -23.89 and time = -23.89
![image 39](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/236184ba-633d-464f-9dfa-b8d601728eaa)
<br>

Now,run below commands to reduce the *Time* of the cell design
```
report_net -connections _10566_
replace_cell _13165_ sky130_fd_cs_hd__or3_4
report_checks -fields {net cap slew input_pins} -digits 4
```

and to reduce the time more, run the commands given,
```
report_net -connection _10916_
replace_cell _13165_ sky130_fd_cs_hd__or3_4
report_checks -fields {net cap slew input_pins} -digits 5
```
![image 41](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/e68a38f0-3bab-421e-a979-379d275ff161)
<br>
