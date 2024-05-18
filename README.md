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

### Important components of chip in a packge are-
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
