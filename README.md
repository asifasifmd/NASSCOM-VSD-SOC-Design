# NASSCOM-VSD-SOC-Design
## VSD_SOC_Design using OpenLANE paltform and Sky-130nm under the guidance of Director and co-founder of VLSI System Design (VSD) Corp. Pvt. Ltd, *Kunal Ghosh*

## Table Of Contents
     1.

     
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
   1. **RTL design**: RTL(Register-Transfer Level) design describes how data moves between registers and how the logical operations are performed on that data.
   2. **EDA tools** : EDA(Electronic Design Automation) tools are essential for the design, simulation, verification, and manufacturing of electronic systems.
   3. **PDK data**  : PDK(Process Design Kits) are the collection of files used to model a fabrication process for EDA tools. Process design rules are DRC, LVS and PEX.
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
OpenLane is an open-source, end-to-end flow for integrated circuit design. It integrates multiple tools from the OpenROAD project and other open-source EDA tools to provide a complete suite for RTL-to-GDSII design.
![WhatsApp Image 2024-05-18 at 13 28 48](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/6394d017-439a-4246-bc35-9e39b9f9b964)

### OpenLane ASIC Flow
![WhatsApp Image 2024-05-18 at 13 28 49 (1)](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/a6365e75-2334-4443-9d69-d4f56caf9284)

### OpenLane Prepearion Set-Up Steps
Open the **Terminal** and write the commandes given below
```
cd Desktop/work/tools/openlane_working_dir/openlane/
docker //to enter into bash-4.2
./flow.tcl -interactive // -interactive for manul operation
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

#### Synthesis
Open the **OpenLane Prperation Set-Up** back and synthesise using the command,
```
run_synthesis
```
![image 7](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/79fb2933-a1ee-420a-b433-26a6d181f032)

*Synthesis* process takes some time and after the completion *Synthesis was successful* appears denoting the successful completion of synthesis process.
![image 14a](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/25ba37b9-7d3f-4400-87fb-c6a95582e256)

#### Utilization Factor
Utilization Factor is the total amount of area occupied by *Netlist* in the core.
  Utilization factor = area occupied by Netlist / area of core
![image 8](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/44c9d56c-5438-43bc-80c1-7e4255b6a6fb)
From above picture,
  Utilization factor = (1613 / 14876) = 0.1084

![image 14](https://github.com/asifasifmd/NASSCOM-VSD-SOC-Design/assets/154309294/646d1e20-6043-4fed-8015-7fbd12296bfb)
