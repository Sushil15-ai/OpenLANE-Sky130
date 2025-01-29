# Sky130 - Digital VLSI SoC Design and Planning
![Static Badge](https://img.shields.io/badge/OS-linux%2C_Windows-orange)
![Static Badge](https://img.shields.io/badge/EDA%20Tools-OpenLANE--Flow%2C_Yosys%2C_abc%2C_OpenROAD%2C_TritonRoute%2C_OpenSTA%2C_magic%2C_netgen%2C_GUNA-purple)
![Static Badge](https://img.shields.io/badge/languages-verilog%2C_bash%2C_TCL-blue)

> 2 Week digital VLSI SoC design and planning workshop with complete RTL2GDSII flow organised by VSD and NASSCOM

<details>  

***<summary> *NOTES* </summary>***

## Day-1 - Inception of open-source EDA, OpenLANE and Sky130 PDK

### Section 1 - Introduction to Digital Design
<details>
<summary>
Theory
</summary>

#### Package vs. Chip

* What we usually consider to be a **chip** is the tiny black box circled on the board. However, that is just a **package** for the actual **integrated circuit (IC)**, or chip, inside. If we zoom into the package as seen in image 2, we get the IC in the center connected to the pins on the boundary by wires.

![image](https://github.com/user-attachments/assets/53d6412f-dc24-4f84-bf19-6ca40646bdaa)

![image](https://github.com/user-attachments/assets/2d915553-162e-4969-8171-c701a57ebfb8)

#### Die, Pads, and Core

* **Pads** help transmit signals between the outside world and the interior of the package.
* **Core** is the area where the digital logic circuits are placed.
* **Die** refers to the size of the silicon chip itself, excluding the surrounding packaging material.

![image](https://github.com/user-attachments/assets/5d7282fa-6634-42ec-940f-b2c0a4e424b9)

#### C Program to Hardware

* A C program is first compiled into assembly language (typically RISC-V for this workshop).
* We then use a hardware description language (HDL) like Verilog or SystemVerilog to describe the hardware functionality. This HDL code represents the desired behavior of the circuit.
* The HDL code is then synthesized into a netlist, which is a low-level representation of the circuit's connectivity. 
* Finally, the netlist is placed and routed on the chip layout using Electronic Design Automation (EDA) tools.

![image](https://github.com/user-attachments/assets/59f2a2d8-1f66-4997-a7a1-851a9881dd3c)

![image](https://github.com/user-attachments/assets/49e26767-6a67-40be-bd95-528c9eade4d4)

![image](https://github.com/user-attachments/assets/28e34cf4-0b72-4cf4-8103-745b78b835f6)

### Section 2 - SoC design and OpenLANE

#### ASIC Design Requires
* Hardware Description Language and RTL IP's
* Electron Design Automation tools.
* **PDK** Data

![image](https://github.com/user-attachments/assets/4e3898f3-abbe-4700-9cf7-4539fca1877d)

#### Process Design Kit (PDK)

* A Process Design Kit (PDK) is a collection of files used to model the specific fabrication process for the EDA tools used to design an integrated circuit (IC). The PDK contains information about the available logic cells, routing rules and device parameters for a particular chip fabrication process.

![image](https://github.com/user-attachments/assets/a33b6ed0-2544-4d52-86ea-490c3e1d09cb)

#### RTL to GDSII Flow
* **Synthesis:** This stage converts the HDL code (e.g., Verilog) into a gate-level netlist. The netlist represents the circuit's functionality using basic logic gates.

![image](https://github.com/user-attachments/assets/edd36bad-aade-4703-aaa4-bb7537adbc59)

* **Floor and Power Planning:** In this stage, the chip layout is planned. The die area is divided into sections for different functional blocks and I/O pads. The power supply network is also designed to ensure proper power distribution throughout the chip.
 
* **Placement:** This stage involves positioning the logic cells from the netlist onto the chip layout. The goal is to find optimal locations for the cells considering factors like timing and area constraints. There are two main placement steps:

    * **Global placement:** This provides an initial placement for all cells, aiming for optimal positions but not necessarily following all layout rules. The placement in this step may not always be legal.
    * **Detailed placement:** This refines the initial placement to ensure all cells adhere to the design rules.

![image](https://github.com/user-attachments/assets/d7eba5be-7b87-4aef-a5ca-50e0b81ae6c8)

![image](https://github.com/user-attachments/assets/9fe021aa-a7c2-42d2-bbdb-a10760e62990)

* **Clock Tree Synthesis (CTS):** A clock tree is a network of buffers and wires that distributes the clock signal to all sequential elements (flip-flops) in the design. CTS aims to minimize clock skew, which is the variation in arrival time of the clock signal at different flip-flops.

* **Routing:** This stage involves creating connections between the placed cells using metal layers available in the fabrication process. Routing is typically done in two steps:

    * **Global routing:** This defines the general paths for the connections between cells.
    * **Detailed routing:** This implements the actual wiring connections based on the global routing plan.

* **Sign-off:** This stage involves various checks to ensure the design meets the desired functionality and manufacturing requirements. Here are some common sign-off checks:

    * **Design Rule Checking (DRC):** This verifies if the layout adheres to the design rules specified by the PDK for the fabrication process.
    * **Layout vs Schematic (LVS):** This compares the final layout with the original gate-level netlist to ensure they are equivalent.
    * **Static Timing Analysis (STA):** This analyzes the timing delays in the design to ensure all signals meet the timing constraints and the circuit operates at the required frequency.

![image](https://github.com/user-attachments/assets/feb256ed-4dfc-4569-9fc5-f883e1552900)

* **Introduction to OpenLANE and StriVe**

* OpenLANE is an open-source design flow that aims to automate the entire process of generating a GDSII file from an RTL design, without requiring manual intervention.
* StriVe is a collection of open-source resources for SoC design, including open PDKs, EDA tools, and RTL examples. It provides features like Design Space Exploration to help find optimal design configurations and offers a growing collection of design examples (43 and growing).

Versions:

![image](https://github.com/user-attachments/assets/2f3d96a3-2617-4adf-a3d6-46fe1ba06da9)

#### OpenLANE ASIC Design Flow:

![image](https://github.com/user-attachments/assets/39b1dfd1-20c0-435f-b80e-d04265f0689f)

</details>

## Day 2-Good Floorplan vs Bad Floorplan and Introduction to Library Cells
### Section 1-Chip Floor planning considerations
<details>
<summary>
Theory
</summary>

#### Defining Width and Height of the Chip

![image](https://github.com/user-attachments/assets/aa53f632-8a83-447c-bd18-48fc034137e8)

* Let us begin with a _netlist_.
* **Netlist:** A netlist is a list of all the components (like flip-flops, gates) and their connections in a circuit.

![image](https://github.com/user-attachments/assets/3f96a19c-3ccf-47ad-bff9-0189384c7941)

* FF-Flip Flops
* A1, O1-AND Gate and OR Gate
* **Gates:** We assign a size (width and height) to each gate in the netlist, creating a unique box for each one.

![image](https://github.com/user-attachments/assets/ba6b1661-176e-4dc8-8c66-c15ddc05ddb5)

* **Cell Areas:** We estimate the size of each cell in the netlist and calculate its area.

![image](https://github.com/user-attachments/assets/b098e3c6-5679-4dc1-95d2-5369b10fe569)

![image](https://github.com/user-attachments/assets/a9287ce7-e226-4893-95b9-1f0bdc27ca02)

* **Core Placement:** We arrange all the logic cells (gates, flip-flops) inside the central area called core.

![image](https://github.com/user-attachments/assets/7c95b04f-4892-436e-993e-79026e240a65)

![image](https://github.com/user-attachments/assets/a4197965-a4ce-4665-ab1f-c82f8c8c304c)

* **Utilization Factor (UF):** This measures how efficiently the core area is used by the logic cells. UF is calculated as the area occupied by the netlist divided by the total core area. In real chips, UF is typically around 0.5-0.6.
* UF = Ar. occupied by netlist/total area of core.
* **Aspect Ratio:** This is the ratio of the core's height to its width. A value of 1 indicates a square core.

#### Preplaced Cells

* Preplaced cells are groups of predefined logic gates that are treated as a single unit.
* To create a preplaced cell, we first partition or divide the netlist into functional blocks or parts. We then create boxes around each part.

![image](https://github.com/user-attachments/assets/c51824ba-67a8-49ed-96c2-cf8ca51bab68)

* Then we extend the input and output io pins such that they are jutting out of the box.

![image](https://github.com/user-attachments/assets/8d59cb64-34df-431f-bf25-f0374b832599)

* **Blackboxing:** We hide the internal details of each block by treating it as a black box with a specific number of input and output pins.

![image](https://github.com/user-attachments/assets/15d24e48-52b2-4ee3-861e-01bfdd482c76)

* After that, we separate the 2 boxes, each with their own inputs and outputs. Each peice or IP can be reused individually anywhere else in the circuit.

![image](https://github.com/user-attachments/assets/65e6a9c4-fc5f-493d-98c5-52ea84a03452)

* The arrangement of these IP's in the chip is known as floorplanning. These blocks have user defined locations and are placed before the automated placement and routing phase. Hence they are known as preplaced cells.

#### Defining Locattions of Pre-placed Cells

* **Preplaced Cell Locations:** Input pins are typically placed on one side of the chip (left or bottom), and output pins are placed on the opposite side (right or top). Preplaced cells are positioned closer to the input side for better connectivity.

![image](https://github.com/user-attachments/assets/133a020b-ae42-40f2-b4a6-03bfe1062574)

#### Decoupling Capacitors

* Real-world (Practical) wires have resistance, which can reduce the voltage difference (voltage drop) between different parts of the circuit.

![image](https://github.com/user-attachments/assets/2f5f89c5-73ce-4872-aa5f-bbe2f0129a9b)

* This causes the voltage difference applied between the IP's to reduce.
* If this reduction is high, then the voltage will not be enough to trigger a logic 1 and will lie in the undefined region.

![image](https://github.com/user-attachments/assets/0dcf107f-67e1-4625-85ec-84d7f6f30fd8)

* So to ensure that the piece of circut always has enough of a voltage drop, we use a decoupling capacitor.
* **Decoupling capacitors** are used to maintain a stable voltage supply for the circuit. They act as tiny batteries that can quickly release stored energy to compensate for voltage fluctuations.

![image](https://github.com/user-attachments/assets/b2a6fbc0-fc31-41d2-b18f-2e3cc35fcadb)

* Decoupling capacitors are placed near pre-placed cells throughout the core area of the chip.

![image](https://github.com/user-attachments/assets/93f22b9c-9b7f-4f76-8c42-9e5e18990d05)

#### Power Planning

* Ground Bounce- It's a sudden change in the ground voltage due to simultaneous switching (dumping of current) of many components (capacitors). If the bounce is very high then the ground can enter into an undefined state.
* Voltage Drop- This occurs when a single power source is tasked with recharging multiple capacitors. It's a decrease in voltage along the power supply lines due to the immense amount of current drawn by the circuit. This leads to the power line to experiance a voltage drop, leading the voltage difference to go into the undefined region.
* The above problems are caused by an overloaded power line/ground line. This can be fixed by having multiple power and ground lines throughout the chip.
(The below image is representing a 16-bit bus when set as input for an inverter)

![image](https://github.com/user-attachments/assets/6c51746e-1f4e-40d8-bc12-abb8f53d8a9b)

![image](https://github.com/user-attachments/assets/93d99c70-2bb4-476e-8b3b-76a1bd3ade9f)

![image](https://github.com/user-attachments/assets/aec37dcc-85cf-4204-b0ef-1bf010c0ae51)

(Power is coming from a single source)

![image](https://github.com/user-attachments/assets/6b60e995-83d0-438e-b377-6b5e061fe6c7)

(Power is coming from multiple sources. In this system, the power line's and ground line's are arranged in the form of a mesh)

![image](https://github.com/user-attachments/assets/0939b3c0-109e-40e5-b091-6857d1830c9d)

#### Pin Placement

* The goal is to optimize pin placement for better performance.
* Input and output pins are placed close to their corresponding pre-placed cells to minimize signal path lengths.
* Clock pins (input and output) are placed directly opposite each other to minimize resistance.
* Pre-placed cells are placed close together whenever possible to reduce the number of decoupling capacitors needed.

![image](https://github.com/user-attachments/assets/b4ba35f1-e906-461b-b29f-affc1c4101a3)

#### Logical Cell Placement and Blockage

* The space between the core and the die is filled with special blockages. These blockages reserve the area for pin placements and prevent the automated placement and routing tool from placing cells there.

![image](https://github.com/user-attachments/assets/d0f00886-808c-4d11-aeb6-8eed0b778539)

</details>

### Section - 2: Library Binding and Placement
<details>
<summary>
Theory
</summary>
	
#### Libraries
* A **netlist** is a list of all the components (like flip-flops, gates) and their connections in a circuit. 
* Below is a netlist.

![image](https://github.com/user-attachments/assets/2a6b9bf3-863a-43d6-9bd2-59d7900891b7)

* We take all the cells in the netlist and place them in a shelf known as the **library**.

![image](https://github.com/user-attachments/assets/9763eb63-1245-422c-83b9-bdcb94cd10d1)

* A **library** contains detailed information about each cell, including:

    * Dimensions (size)
    * Delay characteristics (how long it takes for a signal to pass through the cell)
    * Environmental requirements (e.g., voltage range)
    * Threshold voltage (minimum voltage required for the cell to switch states)
    * Below is a picture of libraries with same cells but different properties.

![image](https://github.com/user-attachments/assets/8ba23fb2-e97d-45a6-86f0-900a7a9ac8a3)

#### Placement

* **Placement** is the stage where we estimte wire length and capacitance and, based on that, place repeaters. The placement process involves these steps:
    1. **Pre-placed cell placement:**  Placing specially designated cells at predefined locations.
    2. **Standard cell placement:**  Placing the remaining cells based on their connectivity to pins and other cells. Cells are positioned closer to the pins they connect with to minimize the wirelength. 
    3. **Repeater insertion:** If the distance between a cell and its connected pin is too large, buffers or repeaters are inserted to ensure reliable signal transmission.
       
![image](https://github.com/user-attachments/assets/985d4d79-e5d3-4f11-94da-d4d727f6715e)

![image](https://github.com/user-attachments/assets/c81cc697-8fbb-4293-89df-7458fa971426)

</details>

#### LAB tasks:-
1. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
```bash
run_placement
```
![image](https://github.com/user-attachments/assets/f754d6f7-1f14-4ece-a006-a056bde8d73d)

* Goals for placement:
	* Cutting down on wire length
 	* Making sure placement is legal (cells don't overlap)

![image](https://github.com/user-attachments/assets/109f9a23-d6ef-4be7-b360-a69a7dec2cf8)

![image](https://github.com/user-attachments/assets/2cd2b1b0-c8a3-4a14-ae05-8a654945ebc5)

2. Load generated placement def in magic tool and explore the placement.
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/<date>/results/placement/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

![image](https://github.com/user-attachments/assets/b3f95826-4def-4cfa-9b1e-2ac5927891bd)

![image](https://github.com/user-attachments/assets/f994383c-1c11-43a3-8b4f-e774d40cbab5)

### Section 3 - Cell design and characterization flows
<details>
<summary>
Theory
</summary>
	
![image](https://github.com/user-attachments/assets/3c88277d-24df-479f-88f6-178e379db640)

</details>

### Section 4 - Timing threshold definitions
<details>
<summary>
Theory
</summary>

#### Slew Thresholds
* Slew_low_rise threshold: lower point in rising curve
* Slew_high_rise threshold: upper point in rising curve
* Slew_low_fall threshold: lower point in falling curve
* Slew_high_fall threshold: upper point in falling curve
```
Transition time = Slew_high - Slew_low
```
![image](https://github.com/user-attachments/assets/99ee5e9e-37d6-4e00-aae1-49e44c4ba61a)

#### Delay Thresholds
* in_fall_thr: input fall threshold
* out_rise_thr: output rise threshold

![image](https://github.com/user-attachments/assets/cb02af64-9b7f-44d8-b511-252ddd1b0ab9)

* in_rise_thr: input rise threshold 
* out_fall_thr: output fall threshold

![image](https://github.com/user-attachments/assets/e32cffcd-6418-44af-8322-8c0b26e628c0)

```
Delay = out_thr - in_thr
(Huge wire delays and inaccuracy in setting threshold may result in negative delay)
```
</details>

## Day 3 - Design library cell using Magic Layout and ngspice characterization
<details>
<summary>
Theory
</summary>
	
### Section 1 - Labs for CMOS inverter ngspice simulations
* We set the *env(FP_IO_MODE)* variable to 2 to make sure the cells are no longer equididstant.

![image](https://github.com/user-attachments/assets/3a02b972-a57b-41e3-b013-e443c1cae51e)

Pins overlap

![image](https://github.com/user-attachments/assets/3e200a95-1d0f-43d9-9497-85205f22b458)

#### Spice Simulations
**PMOS**

![image](https://github.com/user-attachments/assets/231e003d-92c5-4c4a-b065-c0d04bd8d162)

**NMOS**

![image](https://github.com/user-attachments/assets/382de0de-a60e-4422-b8bc-ca73b24a4568)

**Creation of spice Deck**
* We start from a netlist with component connectivity.

![image](https://github.com/user-attachments/assets/c9f94883-7ea1-4864-962f-e6cfa9d2bc38)

* We then define the component values. This includes input and supply voltage, load values, MOSFET values.

![image](https://github.com/user-attachments/assets/8d2d17b1-14c4-4c60-b2ac-27e665b92cc6)

* Then we identify *nodes*.
* *Nodes* are 2 points lying on either side of a component.

![image](https://github.com/user-attachments/assets/f8d87ac8-72f8-49f7-8dc2-3d3af7ce4a48)

* We name nodes and define MOSFETs by the name, followed by the nodes around it in the order drain-gate-source-substrate. Then we decribe it as NMOS or PMOS. This is folllowed by the width and length.

![image](https://github.com/user-attachments/assets/28c2da0e-71dd-4fc3-843d-bab5cd6b1304)

* We describe load and Voltage sources in a similar manner.

![image](https://github.com/user-attachments/assets/075a7473-dac9-48f3-85d2-92b1ee1a3419)

* We then give simulation commands.
* The order(essentially the syntax) Vcc <from> <to> <in steps of>

![image](https://github.com/user-attachments/assets/e13d1929-cee2-4dd6-8a31-ac7738c31a78)

* We then show the location of the model file which has all the technological parameters of everything in the netlist.

![image](https://github.com/user-attachments/assets/c73c6e71-83c7-4ba1-a3a9-f6facd18ad87)

Different w/l (width/length) ratios of PMOS can have changes on the output waveform.

#### Switching Threshold

![image](https://github.com/user-attachments/assets/d87830aa-c277-486f-bfad-b27ae7c8c8f7)

* Switching Threshold is the point where V<sub>in</sub> = V<sub>out</sub>

![image](https://github.com/user-attachments/assets/0719b00b-6d26-4fcf-96d8-03473785e542)

Switching threshold is the intersection of the lines.
* In this area both the NMOS and PMOS are in the saturation region.

![image](https://github.com/user-attachments/assets/56efd70a-d3cf-444b-81f8-7cfbd165fd90)

If Vin = Vout means gate voltage = drain voltage, Vgs = Vds
* the currents of the NMOS and PMOS will be the same, however the directions will be different.
* I<sub>dsP</sub> = I<sub>dsn</sub>
* Pulse definition in spice deck: V <location based on nodes> pulse <start voltage> <end voltage> <shift(delay in start)> <rise time> <fall time> <pulse width> <width of complete cycle>

![image](https://github.com/user-attachments/assets/807ae7ff-cc9b-4995-a8cc-8813ebe985ea)

Delay(rise or fall): Out-In(at 50% w.r.t. time)

![image](https://github.com/user-attachments/assets/1891d848-73a1-495b-8882-5fdd498b0d71)
</details>

### Section 2 - Inception of Layout ÃÂ CMOS fabrication process

#### 16 Mask CMOS proscess

1) Select a substrate - The part on which everything is fabricated on. The doping level should be less than well doping.
2) Creating active region(pockets) for transistors - We keep gaps and isolation between each and every pocket to avoid interference.
	* Grow a layer of silicon dioxide (insulator) on the substrate.
 	* Then deposit a later of Silicon Nitride on it.
 	* After that, deposit a layer of photoresist on top of the Silicon Nitride layer.
  	* Add a protectional layer of Mask 1 on the area where the pockets are to be made. UV light is shined on top of the mask.

![image](https://github.com/user-attachments/assets/cc9b8631-7eb2-49d6-b854-f2a920ed42e2)

   * Wash out the unmasked area in developing solution.

![image](https://github.com/user-attachments/assets/9a5c5850-e216-436b-878c-9cc72817fca9)

   * Remove the Mask and etch off the Silicon Nitride that is not protected by photoresist.
   * Remove all the photoresist chemically.

![image](https://github.com/user-attachments/assets/3c0a6410-a99a-4635-8569-07c9a7f2c158)

   * Grow the Silicon di-oxide once more by placing it in an oxidation furnace. You will observe that the area under the silicon dioxide remains untouched. The area under the edges of the silicon di-oxide though, is not protected due to strong growth. This creates isolation areas between pockets. This proscess is known as LOCOS(Local oxidation of Silicon).

![image](https://github.com/user-attachments/assets/09c3f19b-329b-408d-b7bb-9376a3bd6c74)

![image](https://github.com/user-attachments/assets/086f7cf4-6d2d-477b-8048-8337fe6d63db)

   * The silicon Nitride is stripped using hot phosphoric acid.

![image](https://github.com/user-attachments/assets/795d783c-139f-43a8-8f56-651e7b5c5149)

3) N-well and P-well formation:
	* Photoresist is added again and a portion is protected by Mask 2.
	* Mask 2 in layout.

![image](https://github.com/user-attachments/assets/a85fda01-3afb-4827-b19f-4e169188b302)
‎ 
	* It is again subjected to UV light and wahed. The mask is removed and then subjected to Boron in a process called ion-implantation to form a P-well.(High energy, about 200keV is needed). The oxide layer is damaged.
	 
![image](https://github.com/user-attachments/assets/c0e5b3e2-0c86-44be-b14a-432592052e12)
‎
	* The same step is done using Mask 3 to form a N-well except this time we replace bororn with phosphorus.
 
![image](https://github.com/user-attachments/assets/b4e0984e-a73c-43cd-9be4-e3f279ca68a3)
‎
	* We now have a N-well and a P-well.
 
![image](https://github.com/user-attachments/assets/aaa8bd60-f975-4adf-9bc0-fd1dd8df1e79)
‎
	* We then do drive-on diffusion and diffuse the wells to about half the substrates height by placing it in a high temprature furnace.(This is known as theh twin tub proscess)
 
![image](https://github.com/user-attachments/assets/3d76c7aa-404c-46df-a547-1736b75b87cb)

4) Formation of gate: 
	* The doping concentration and oxide capacitance impact the threshold voltage.
	* We repeat the steps done with mask 2 again with mask 4.

![image](https://github.com/user-attachments/assets/3e0046ae-ca90-45ae-aeef-8f1d6939cfd4)
‎
	* We again put it under the effect of boron with leser energy to create a smaller P-well with doping concentration adjusted to meet requirements.

![image](https://github.com/user-attachments/assets/bd9bdafd-4c9d-414f-ba0a-bf9f6e46c392)
‎
 	* Same thing is one with mask 5, similar to the steps done with mask 3. This time, arsenic can be used in place of phosphorus. The oxide layer will be damaged.

![image](https://github.com/user-attachments/assets/d0b05ff9-9b06-418b-b050-bd3c7bbf4473)
‎
 	* The original damaged oxide is then etched/stripped using dilut hydrofluric (HF) solution.

![image](https://github.com/user-attachments/assets/19186b03-f06c-4f5e-89fd-eb1c2ca2b4c4)
‎
	* Then, it is regrown to give high quality oxide. The oxide thickness (corresponding to oxide capacitance) is maintained as per required threshold voltage.

![image](https://github.com/user-attachments/assets/f545a9bd-9994-4e9b-a872-d2107495dfb7)
‎
	* After this, a polysilicon layer is deposited on the oxide layer. We then dope it with N-type ion implants for low gate resistance.

![image](https://github.com/user-attachments/assets/a493d527-f9ac-4e24-a1e0-5cbc80b0550c)
‎
	* Another photoresist layer is deposited and shaped as shown in figure with the help of mask 6 (polysilicon). Then mask 6 is removed followed by the photoresist. Also given below is how mask 6 looks in a loyout.

![image](https://github.com/user-attachments/assets/78927ccd-0a2c-4792-ba8f-b3f608237e08)

![image](https://github.com/user-attachments/assets/b7b1da0b-3e4f-4e85-83cf-ecd8a75c3bf3)
	
![image](https://github.com/user-attachments/assets/1ca5a125-359b-463a-8d0c-b921d6a74f97)
	
5) Lightly doped drain formation:
	* This is done mainly for 2 reasons-
		i) Hot electron effect: when we decrease the size of the chip, the electric feild value becomes high as we dont usually change the power supply. The high energy carriers break Si-Si bonds. It might also break the 2eV barrier between the Si conduction band and the Silicon-dioxide condution band and get into the oxide layer.

		ii) Short channel effect: for short channels, it becomes harder for the gate to control the source and the drain current.

	* Build a photoresist layer over the N-well using Mask 7. Then we implant phosphorus in our P-well to create a N- implant. The energy is also regulated to make sure the N-implant does  not penetrate deep into the well. Remove the photoresist.

![image](https://github.com/user-attachments/assets/a41f311f-7b37-4e38-b24e-5890360e22f1)

	* Do the same thing on the other side using Boron and Mask 8 to create a P- implant.

![image](https://github.com/user-attachments/assets/dc859621-2273-49ac-afb0-c1cac15837db)

	* ***Side wall spacers:*** Deposit a thick layer of Silicon Nitride or Silicon di-oxide. Then perform anisotropic plasma etching. This remoed all the silicon di-oxide, oxide layer and nitride except for where the polysilicon is.

![image](https://github.com/user-attachments/assets/fe3e99b0-04ea-4371-876a-ccc0b6a0001e)

![image](https://github.com/user-attachments/assets/eabf7c1c-9bf3-4e70-82ee-dc4a00532413)
‎
 	* The side wall spacers help in making sure that some of the N- and P- dopings are preserved.
 
6) Source and drain formtion:
	* We add a thin oxide layer to prevent ions from interfering with the P-substrate (chanelling).

![image](https://github.com/user-attachments/assets/269c2333-b864-4cc4-9dcf-dc8e99cfc89c)

 * Steps done to create ligtly dope drains are repeated.
 * The N- and P- implants are still present thanks to the polysilicon and the side wall spacers.

![image](https://github.com/user-attachments/assets/e6973f1f-d9d6-4dc5-9d84-6c2a953b82a2)

![image](https://github.com/user-attachments/assets/b608089c-79e8-47dc-a8d0-54b6903e4b03)

 * Annealing is done in high temprature. The implants will go deeper into the wells.

7) Steps to form contacts and interconnects(local)
	* Remove the thin screen oxide layer.
	* Titanium (low resistance) is deposited on the wafer surface using *sputtering*.
	* In *sputtering* titanium metal is bombarded with argon gas. The titanium atoms will get sputtered out and get deposited onto the substrate.

![image](https://github.com/user-attachments/assets/2479e875-19fe-4645-b03d-afed9e3d47f0)
‎
 	* Wafer is heated at tempratures of 650-700°C in N<sub>2</sub> ambient for about 60s. This results in Titanium Silicon di-oxide(low resistant contacts)

![image](https://github.com/user-attachments/assets/27e22e87-1d13-4ec7-b548-d1a24345adf9)
‎ 
	* TiN is also formed due to nitrogen ambient. It is used only for local communication.
	* Polysilicon placed with help of mask 11 as so. Mask is removed.

![image](https://github.com/user-attachments/assets/f5002e59-04f5-4dcc-8416-f3e7efd013ba)
‎
	* Excess TiN is etched using RCA cleaning which consists of-

![image](https://github.com/user-attachments/assets/f8009e39-c85c-4617-b95f-f3e8e4f4c2bb)

![image](https://github.com/user-attachments/assets/ebcf630a-b33c-4264-9b33-0485bd901635)

8) Higher metal level formation:
	* Now we deposit a thick layer of SiO<sub>2</sub> doped with phosphorus or boron. This is done to give a protection against mobile sodium ions(phosphorus). Doping with boron reduces temperature.

![image](https://github.com/user-attachments/assets/90bd4ad4-f0f6-4ccf-8f7a-5f1364146278)
‎
	* Chemical Mechanical Polishing(CMP) is done to flatten out wafer surface.

![image](https://github.com/user-attachments/assets/dbb05cde-60ba-4356-a295-0183c5b6a7f1)
‎
	* Next we use mask 12 and photoresist on areas where we do not need contact holes. We also etch off the SiO<sub>2</sub> in places where we need the contact holes. We remove the photoresist.

![image](https://github.com/user-attachments/assets/82dcbb8a-0863-4f62-93e7-77e0b2dc5637)
‎
	* We then deposit a thin layer of Titanium Nitride.
	* We then deposit a blanket tungsten layer on top of the TiN. It serves as a good interconnect between the bottom and top layers.

![image](https://github.com/user-attachments/assets/02359a99-db2f-4341-b6d7-ca8f9434dc52)
‎
	* We again do CMP to remove excess Tungsten and planarise the wafer surface.
	* Next we add an aluminium layer to take it to the top layer. We remove unnecesarry parts using mask 13 and photoresist as shown in diagram. Plasma etch out the remaining Al. Remove photoresist.

![image](https://github.com/user-attachments/assets/ec1443ad-f6af-423f-ae58-7955f27b5344)
‎
	* We now already have 2 matal layers. To make another one, we deposit more Silicon di-oxide and perform CMP to make the surface planar.
	* Using mask 14, define contact holes.

![image](https://github.com/user-attachments/assets/7d41d948-fa02-43ea-8952-2d6d89622643)
‎
	* Deposit a small layer of tin, and a layer of tungsten, before removing excess using CMP.

![image](https://github.com/user-attachments/assets/013ddf38-32ee-4c6d-aa2a-131b4de02439)
‎
	* Using mask 15, make another deposit of Al interconnects over the tungsten as shown in diagram. This layers interconnects should be thicker than the ones on the prepious layer.

![image](https://github.com/user-attachments/assets/2bd51079-1375-4066-aed9-ba82c121bb31)
‎
	* Deposit the top layer of dielectric (Silicon Nitride or Silicon dioxide) to protect the chip.

![image](https://github.com/user-attachments/assets/4932d211-3282-4bf5-9bf2-330a05c4edbb)
‎	
	* Finally use mask 16 to drill contat holes and bring contacts outside the chip.

![image](https://github.com/user-attachments/assets/94dff425-11de-475a-9d13-7de4d78da520)


## Day 4 - Pre-layout timing analysis and importance of good clock tree

### Section 1 - Timing modelling using delay tables

* Logic gates can be used to regulate clock too.

![image](https://github.com/user-attachments/assets/7d9fe2a5-17eb-4813-baf5-7ed37d10ba2c)

</details>

# LABS

### Section 3-Familliarization with open-source EDA tools

#### LAB tasks:- 

1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
```bash
docker
```
```bash 
./flow.tcl -interactive
# The -interactive flag opens flow.tcl in interactive mode
```
```bash
package require openlane 0.9
```
```bash
prep -design picorv32a
# This command makes sure that future commands follow the design specifications as set in picorv32a
```
```bash
run_synthesis
```
![image](https://github.com/user-attachments/assets/874a00f9-85c9-4e44-8d39-1d44bd88af46)

![image](https://github.com/user-attachments/assets/6b1396a1-016c-4d45-a4ea-ebe9d5fd7b52)

![image](https://github.com/user-attachments/assets/2b138155-aa87-41d4-a8f2-20036667f654)

2. Calculating Flop Ratio
```
Flop Ratio = No. of D flip flops / No. of cells = 1613 / 14876 = 0.10842968539
```
![image](https://github.com/user-attachments/assets/890e8e00-ff6f-4550-9af8-a657e4e7dd49)

```
% of D Flip Flops = Flop Ratio*100 = 0.10842968539 * 100 = 10.842968539%
```

#### LAB tasks:- 

1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
```bash
# Perform all the previous steps as shown in Day 1 labs and then continue
run_floorplan
```
```bash
cd Desktop/work/tools/openlane_working_dir/designs/picorv32a/runs/date/results/floorplan
less picorv32a.floorplan.def
# From here you can calculate die area etc.
```
2. Calculate the die area in microns from the values in floorplan def.

![image](https://github.com/user-attachments/assets/8bcc2477-cded-435e-a1f2-18064bec439b)

![image](https://github.com/user-attachments/assets/8a6f804f-744b-4f9a-b12d-8a2745c0c74f)

![image](https://github.com/user-attachments/assets/bc04d36e-6b8a-4369-bef9-1048c725f64a)

```
Lower left coordinate or die: (0,0)
Upper right coordinate of die: (660685,671405)
Die area: 443,587.212425 square microns (µm²)
```
3. Load generated floorplan def in magic tool and explore the floorplan.
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-01_17-06/results/floorplan
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
# This command opens a visual representation of out floorplan step
```
```bash
# After this, perform the placement step.
run_placement
```
![image](https://github.com/user-attachments/assets/6b128393-9fcd-4359-880d-d44f9a764650)

![image](https://github.com/user-attachments/assets/173590a2-68f5-45b5-99ab-b1d9847f79e1)

![image](https://github.com/user-attachments/assets/fcdbe37f-068e-415c-ab90-18f7e39b16c8)

![image](https://github.com/user-attachments/assets/0bf5211f-ef1c-4392-a842-4358f059dd1a)

![image](https://github.com/user-attachments/assets/746f85f4-f83e-46cc-af03-f5782f261563)

![image](https://github.com/user-attachments/assets/93b4d29c-901c-4a89-8621-f3856192ed0f)
```bash
# cd to path containing placement.def
cd eDesktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-01_17-06/results/placement/

# Load the placement def in magic
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

#### LAB tasks:-

1. Clone custom inverter standard cell design from github repo
```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
```bash
git clone https://github.com/nickson-jose/vsdstdcelldesign
```
```bash
cd vsdstdcelldesign
```
![image](https://github.com/user-attachments/assets/0382aa51-46c6-4ad2-81df-e1eed0ee84ae)

2. Copy the sky103A.tech file to /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/
```bash
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech
```
```bash
magic -T sky130A.tech sky130_inv.mag &
```

![image](https://github.com/user-attachments/assets/0aa4feb4-b91a-4cdc-9030-07f4b69d1b85)

3. Load the custom inverter layout in magic and explore

Opening inverter in magic

![image](https://github.com/user-attachments/assets/1d85541c-2fc9-4eb5-a441-7e80c355d20f)

Identifying PMOS

![image](https://github.com/user-attachments/assets/d1438810-7b1f-4d1d-bf57-05a81b58d435)

Identifying NMOS

![image](https://github.com/user-attachments/assets/762ade6f-cc8a-4e90-b80b-9821c7ba6805)

Output Y's connectipn to NMOS and PMOS verifies

![image](https://github.com/user-attachments/assets/2c2e8abb-e36a-431a-9c14-023fc89b9fe6)

4. Spice extraction of inverter in Magic
```bash
# Print working directory
pwd
```
```bash
# Extract to .ext format
extract all
```
```bash
ext2spice cthresh 0 rthresh 0
```
```bash
# convert extracted file to spice format
ext2spice
```
![image](https://github.com/user-attachments/assets/4957f7ff-0a6f-403b-a017-25e22898f3ad)

5. Editing the spice model file for analysis through simulation.

![image](https://github.com/user-attachments/assets/1d229b45-f02d-44ee-b003-50a20096738c)

### Section 3 - Sky130 Tech File Labs

#### LAB tasks:-

open /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/sky130_inv.spice in text editor (preferably, in terminal it is harder) and edit the text to the following
```
* SPICE3 file created from sky130_inv.ext - technology: sky130A

* Scale adjusted according to minimum box size
.option scale=0.01u

* Including pmos and nmos libs
.include ./libs/pshort.lib
.include ./libs/nshort.lib

//.subckt sky130_inv A Y VPWR VGND

M1000 Y A VPWR VPWR pshort_model.0 w=37 l=23
* ad=1.44n pd=0.152m as=1.52n ps=0.156m
M1001 Y A VGND VGND nshort_model.0 w=35 l=23
* ad=1.44n pd=0.152m as=1.37n ps=0.148m

* Adding VDD and VSS
VDD VPWR 0 3.3V
VSS VGND 0 0V
* adding load capacitance
C6 Y 0 2fF

* Defining input pulse
Va A VGND PULSE(0V 3.3V 0 0.1ns 0.1ns 2ns 4ns)
C0 A VPWR 0.0774fF
C1 Y VPWR 0.117fF
C2 A Y 0.0754fF
C3 Y VGND 0.279fF
C4 A VGND 0.45fF
C5 VPWR VGND 0.781fF
//.ends

* Analysis type
.tran 1n 20n
.control
run
.endc
.end
~   
```
```bash
open file in vim using terminal
vim sky130_inv.spice
```
![image](https://github.com/user-attachments/assets/fd9ae7be-8f4a-4b09-9efb-eda5d78e452e)

```bash
# install ngspice
sudo apt install ngspice
ngspice sky130_1nv.spice
```
![image](https://github.com/user-attachments/assets/8b8c0acd-c1e7-406e-bc52-f9c23062fa15)

```bash
plot y vs time a
```
![image](https://github.com/user-attachments/assets/ee2396e3-d7da-4cce-8551-fd8e5387f25c)

Rise transition time calculation
```
Rise transition time=Time taken for output to rise to 80%−Time teken for output to rise to 20%
```
```math
20\%\ of\ output = 0.66\ V
```
20% screenshot

![image](https://github.com/user-attachments/assets/276bf143-4cc0-468c-9552-a87fd757ad1e)

```math
80\%\ of\ output = 2.64\ V
```
80% screenshot

![image](https://github.com/user-attachments/assets/b218d622-3b30-48ef-b930-53b95f2c3914)

![image](https://github.com/user-attachments/assets/82e47a7f-8b78-48ba-ab8b-b36945f1f327)

```math
Rise\ transition\ time = 2.24179 - 2.18217 = 0.05962\ ns = 59.62\ ps
```
Fall transition time calculation
```math
Fall\ transition\ time = Time\ taken\ for\ output\ to\ fall\ to\ 20\% - Time\ taken\ for\ output\ to\ fall\ to\ 80\%
```
```math
20\%\ of\ output = 0.66\ V
```
```math
80\%\ of\ output = 2.64\ V
```
20% screenshots

![image](https://github.com/user-attachments/assets/74b85270-c030-4184-9b82-fa672d536fc2)

80% screenshots

![image](https://github.com/user-attachments/assets/7757335e-1294-4a15-9463-d24906fc69e8)

```
x0 = 4.09167e-09, y0 = 0.66

x0 = 4.05075e-09, y0 = 2.64043
```

![image](https://github.com/user-attachments/assets/94b247a1-044e-4d26-b235-eb49a422a218)

```math
Fall\ transition\ time = 4.09167 - 4.05075 = 0.04092\ ns = 40.92\ ps
```

Rise Cell Delay Calculation

```math
Rise\ Cell\ Delay = Time\ taken\ for\ output\ to\ rise\ to\ 50\% - Time\ taken\ for\ input\ to\ fall\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```
50% screenshots

![image](https://github.com/user-attachments/assets/a66ab6aa-a2d6-4ba7-8e6f-0206de6405d0)

![image](https://github.com/user-attachments/assets/ed49b397-3eda-4988-a8fd-cebef3fba8ed)

x0 = 2.15e-09, y0 = 1.65006

x0 = 2.21133e-09, y0 = 1.64997

```math
Rise\ Cell\ Delay = 2.21133 - 2.15 = 0.06133\ ns = 61.33\ ps
```

Fall Cell Delay Calculation

```math
Fall\ Cell\ Delay = Time\ taken\ for\ output\ to\ fall\ to\ 50\% - Time\ taken\ for\ input\ to\ rise\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```

50% Screenshots

![image](https://github.com/user-attachments/assets/5f80b4e9-9c8c-45ab-81b9-5bee369b27e1)

![image](https://github.com/user-attachments/assets/c6ea7bd9-5b75-4371-af9d-a823d5131a6d)

x0 = 4.05e-09, y0 = 1.65019

x0 = 4.077e-09, y0 = 1.65

```math
Fall\ Cell\ Delay = 4.077 - 4.05 = 0.027\ ns = 27\ ps
```
Magic webpage: http://opencircuitdesign.com/magic/
Skywater docs: https://skywater-pdk.readthedocs.io/en/main/

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections

```bash
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Extract the file
tar xfz drc_tests.tgz

cd drc_tests

ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool with better graphics
magic -d XR &
```
.magicrc file screenshot

![image](https://github.com/user-attachments/assets/edf24ed9-9f0e-4194-bf55-8d3d0a6d6c4e)

Screenshot opening metal layer 3

![image](https://github.com/user-attachments/assets/93daf94e-b5dc-4968-a1fd-6d2a5d30a526)

Screenshot of difftap rules.

![image](https://github.com/user-attachments/assets/6c834417-4641-4073-918b-e17cccc26d1e)

Identifying inaccuracy

![image](https://github.com/user-attachments/assets/93ff18de-81c5-45bb-a1e2-d4b6ae46b6e6)

Correction to sky130A.tech

![image](https://github.com/user-attachments/assets/483cde1f-bc1e-48ca-8f54-15b4f167bd67)

The DRC error is now showing with respect to the new rule entered by us.

![image](https://github.com/user-attachments/assets/c1f05e4e-5165-4a92-99c9-51155f8f0eed)

### Nwell.4 Complex rule correction

Identify the nwell withut the tap.

![image](https://github.com/user-attachments/assets/f71efdce-c302-4ce6-92ca-b285ced8657b)

Nwell rules page:

![image](https://github.com/user-attachments/assets/094309a3-2742-4030-958e-81d8844a7d84)

No drc error shown!

Edit sky130A.tech file to update drc rules
![image](https://github.com/user-attachments/assets/505a66b4-1b77-4502-bba7-3d91dc016074)

(illegal spelling changed)

![image](https://github.com/user-attachments/assets/672cc72c-5233-4bb1-accc-408cfce9d1ba)

```bash
# Load updated .tech file
tech load sky130A.tech

drc style drc(full)

# re-run drc check
drc check

drc why
```

DRC error shown

![image](https://github.com/user-attachments/assets/c4e251ef-c39d-45cb-b81d-8ae520a19cfc)
 
#### LAB tasks:-

1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

magic -T sky130A.tech sky130_inv.mag &
```
Conditions to be verified before moving forward with custom designed cell layout:

Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.
Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.

Screenshot of tracks.infoof sky130_fd_sc_hd

![image](https://github.com/user-attachments/assets/926e41cd-f1d4-4896-91cc-0a7790dc55e7)

```bash
# To understand the syntax
help grid
```
```bash
# Setting grid values
grid 0.46um 0.34um 0.23um 0.17um
```
Grid

![image](https://github.com/user-attachments/assets/0cf2de43-b4cb-4eca-8428-338161612e37)

![image](https://github.com/user-attachments/assets/b08fa1a9-149d-41b9-9906-413b3f14dd84)

*Conditions Verified*

```math
Horizontal\ track\ pitch = 0.46\ um
```
```math
Width\ of\ standard\ cell = 1.38\ um = 0.46 * 3
```
```math
Vertical\ track\ pitch = 0.34\ um
```
```math
Height\ of\ standard\ cell = 2.72\ um = 0.34 * 8
```
```bash
save sky130_vsdinv.mag
```
Open the newly saved layout using
```bash
magic -T sky130A.tech sky130_vsdinv.mag &
```

![image](https://github.com/user-attachments/assets/63e76f6c-18ae-43b4-822a-ac91897962ba)

2. Generate lef from the layout.

![image](https://github.com/user-attachments/assets/92c2b43c-b96d-47c4-9bba-54a101199d4f)

```bash
lef write
```
3. Copy lef and lib files to /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```bash
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```
```bash
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```
```bash
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```
```bash
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```
![image](https://github.com/user-attachments/assets/e844d6ca-db15-410a-87fd-543ab76d86c5)

Open picorv32A/config.tcl with GVIM

![image](https://github.com/user-attachments/assets/0a8cbb61-b51c-4c09-a2d7-919d477e3e35)

Edit config.tcl to this (This step will be easier if you do it with notepad instead of terminal)

![image](https://github.com/user-attachments/assets/bb47954f-0936-4464-9e00-e8be3b5f6a3c)

Now perform steps to open OPENLane and prep picorv32a.

![image](https://github.com/user-attachments/assets/8c47d657-fc3c-4262-a739-eae5d7b66726)

Include newly added lef to flow using
```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```
Run synthesis

![image](https://github.com/user-attachments/assets/78188cb4-6ef8-4d8d-ba3f-38a6bbc4d739)

![image](https://github.com/user-attachments/assets/aa53b025-5ffb-4976-a8f9-6a92dde83098)

Perform these modifications

![image](https://github.com/user-attachments/assets/2e5d3bcc-631b-4520-a07e-e9c6d1435e99)

Run synthesis

Negative slack becomes 0

![image](https://github.com/user-attachments/assets/2ea9d87c-7f73-407a-8e0c-3dbdd4e30ae0)

```bash
run_floorplan
```
Due to the error experienced while running, we use the following set of commands available instead of `run_floorplan`  based on information from `Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl` and also based on `Floorplan Commands` section in `Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md`
```bash
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```
![image](https://github.com/user-attachments/assets/85519be6-574e-4219-b0a9-825a3fccf83d)

Next we run placement

![image](https://github.com/user-attachments/assets/59ca231d-3ade-4313-bfc7-d1b70c44166b)

Open placements results using
```bash
cd /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image](https://github.com/user-attachments/assets/9d60b463-7c65-4b02-8069-a22ceef87046)

![image](https://github.com/user-attachments/assets/7957c209-a4a0-4add-86b0-0735c219a364)

![image](https://github.com/user-attachments/assets/f41d34dd-7bd9-4256-8700-27dba91001de)

Expand to view internal activity of layers

![image](https://github.com/user-attachments/assets/55ca54a8-7eaf-4775-a36f-daab7439b339)

#### Post synthesis STA with OpenSTA.
 1) Run all steps untill synthesis again.
 2) Create pre_sta.conf in openlane dir and my_base.sdc in openlane/designs/picorv32a/src.
 
 ![Taken from https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main]![image](https://github.com/user-attachments/assets/552ca5db-a571-4085-9c5c-088b4d261f40)

![image](https://github.com/user-attachments/assets/5346df71-2e30-48d4-a9fd-cf9cc63a4bb5)
 
![image](https://github.com/user-attachments/assets/54d772b9-f7a3-4f1b-ae32-4e9b680ac92d)

```bash
cd Desktop/work/tools/openlane_working_dir/openlane

sta pre_sta.conf
```
![image](https://github.com/user-attachments/assets/27e6a695-9a0d-4f67-891c-830aeac05b26)

 4) Commands to reduce fanout and reduce delay.
```bash
prep -design picorv32a -tag 21-01_15-54 -overwrite
```
```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
```
```bash
add_lefs -src $lefs
```
```bash
set ::env(SYNTH_SIZING) 1
```
```bash
set ::env(SYNTH_MAX_FANOUT) 4
```
```bash
echo $::env(SYNTH_DRIVING_CELL)
```
```bash
run_synthesis
```
![image](https://github.com/user-attachments/assets/18efa115-acee-4bdb-b247-c8ad837c7930)

Open the STA file and run it
```bash
cd Desktop/work/tools/openlane_working_dir/openlane

sta pre_sta.conf
```
![image](https://github.com/user-attachments/assets/1df58c4e-ab45-43bc-a65f-b2dea89b8fe5)

5) Make timing ECO fixes to remove all violations.

6) Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Commands to make a copy of the netlist.

```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/results/synthesis/

ls

cp picorv32a.synthesis.v picorv32a.synthesis_old.v

ls
```
![image](https://github.com/user-attachments/assets/24c02130-da8f-4c9e-b688-e8ae4147592a)

Commands to write verilog

```bash
help write_verilog
```
```bash
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/results/synthesis/picorv32a.synthesis.v
```
```bash
exit
```
![image](https://github.com/user-attachments/assets/feaad044-d490-419d-95dd-52986db6f349)

Commands load the design and run necessary stages

```bash
prep -design picorv32a -tag 21-01_15-14 -overwrite
```
```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
```
```bash
add_lefs -src $lefs
```
```bash
set ::env(SYNTH_STRATEGY) "DELAY 3"
```
```bash
set ::env(SYNTH_SIZING) 1
```
Running synthesis
```bash
run_synthesis
```
Running floorplan (alternative steps)
```bash
init_floorplan
```
```bash
place_io
```
```bash
tap_decap_or
```
Running placement
```bash
run_placement
```
Runnning command to synthesis the clock tree.
```bash
run_cts
```
![image](https://github.com/user-attachments/assets/52f6f240-94b2-4f22-81b7-ac18ea98d5c5)

```bash
# run OpenROAD
openroad
```
```bash
# Read lef file
read_lef /openLANE_flow/designs/picorv32a/runs/21-01_16-03/tmp/merged.lef
```
```bash
# Read def file
read_def /openLANE_flow/designs/picorv32a/runs/21-01_16-03/results/cts/picorv32a.cts.def
```
```bash
# Create OpenROAD database
write_db pico_cts.db
```
![image](https://github.com/user-attachments/assets/f8612236-d9a1-48b8-8e3e-79a686ab0b92)

```bash
# Loading the created database
read_db pico_cts.db
```
![image](https://github.com/user-attachments/assets/9d7a2345-ea11-49c4-ac38-22cfb4f709f5)

```bash
# Read netlistS
read_verilog /openLANE_flow/designs/picorv32a/runs/21-01_15-14/results/synthesis/picorv32a.synthesis_cts.v
```
```bash
# Read library
read_liberty $::env(LIB_SYNTH_COMPLETE)
```
```bash
link_design picorv32a
```
```bash
# Read the custom sdc
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
```
![image](https://github.com/user-attachments/assets/f040917c-b816-40a4-9de8-c307942fd35b)

```bash
# Set all cloks as propagated clocks
set_propagated_clock [all_clocks]
```
```bash
help report_checks
```
```bash
# Generating timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
```
![image](https://github.com/user-attachments/assets/f3720244-848a-4225-af75-24690a48d57f)

```bash
exit
```

7) Post CTS Openroad timing analysis
Commands for executing OpenROAD timing analysis. Exploration by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing `CTS_CLK_BUFFER_LIST`

```bash
echo $::env(CTS_CLK_BUFFER_LIST)
```
```bash
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]
```
```bash
echo $::env(CTS_CLK_BUFFER_LIST)
```
```bash
echo $::env(CURRENT_DEF)
```
```bash
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/21-01_15-14/results/placement/picorv32a.placement.def
```
___________________________________________________________________________________
IMAGE
___________________________________________________________________________________
```bash
run_cts
```
```bash
echo $::env(CTS_CLK_BUFFER_LIST)
```

```bash
openroad
```
```bash
read_lef /openLANE_flow/designs/picorv32a/runs/21-01_15-14/tmp/merged.lef
```
```bash
read_def /openLANE_flow/designs/picorv32a/runs/21-01_15-14/results/cts/picorv32a.cts.def
```
![image](https://github.com/user-attachments/assets/0acca5fa-95bd-45e4-a503-815b70313372)

```bash
write_db pico_cts1.db
```
```bash
read_db pico_cts.db
```
```bash
read_verilog /openLANE_flow/designs/picorv32a/runs/21-01_15-14/results/synthesis/picorv32a.synthesis_cts.v
```
![image](https://github.com/user-attachments/assets/11f6059b-a46c-4a4c-87eb-5b0281a29545)

```bash
read_liberty $::env(LIB_SYNTH_COMPLETE)
```
```bash
link_design picorv32a
```
Read the .sdc file we created
```bash
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
```
![image](https://github.com/user-attachments/assets/1f6cef54-af12-474f-8e99-9888277b2c74)

```bash
set_propagated_clock [all_clocks]
```
```bash
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
```
![image](https://github.com/user-attachments/assets/da1ced87-689e-48d4-9c43-f70eb6e941ed)

```bash
report_clock_skew -hold
```
```bash
report_clock_skew -setup
```
![image](https://github.com/user-attachments/assets/f1a18c34-b690-431c-ba7f-d8e4087fd891)

```bash
exit
```
```bash
echo $::env(CTS_CLK_BUFFER_LIST)
```
```bash
# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]
```
```bash
echo $::env(CTS_CLK_BUFFER_LIST)
```
![image](https://github.com/user-attachments/assets/8145e430-876d-4f19-ba56-c15b726221ed)

#### LAB Tasks:-

1) Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

Commands to perform all necessary stages up until now

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```
```bash
docker
```
```bash
./flow.tcl -interactive
```
```bash
package require openlane 0.9
```
```bash
prep -design picorv32a
```
![image](https://github.com/user-attachments/assets/8fcf3ddf-b308-41cf-b290-bfa869b74b4c)

```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```
```bash
set ::env(SYNTH_STRATEGY) "DELAY 3"
```
```bash
set ::env(SYNTH_SIZING) 1
```
![image](https://github.com/user-attachments/assets/9050f15e-b8f7-4b50-a0df-6dcef1caa0b5)

```bash
run_synthesis
```
![image](https://github.com/user-attachments/assets/657df435-e4a9-4c59-be3d-cee1a21bdf61)

Alternative for running floorplan
```bash
init_floorplan
place_io
tap_decap_or
```
![image](https://github.com/user-attachments/assets/5c4d7677-93fa-4c45-bda9-ed721269e034)

Running placement
```bash
run_placement
```
![image](https://github.com/user-attachments/assets/bdb63914-cb40-43a1-84e0-d29209365349)

```bash
unset ::env(LIB_CTS)
```
Running Clock Tree Synthesis (CTS)
```bash
run_cts
```
![image](https://github.com/user-attachments/assets/007124db-11ed-4fb0-830d-0bdb47f72e9d)

Generate the PDN
```bash
gen_pdn 
```
![image](https://github.com/user-attachments/assets/3f796954-9d6a-47dc-bb43-abb2fc613692)

Commands to load PDN def in magic in another terminal

```bash
# Change directory to path containing pdn def file
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/tmp/floorplan/
```
Open in magic
```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```
![image](https://github.com/user-attachments/assets/0d789788-76d2-4fc3-a477-deac972c1428)

![image](https://github.com/user-attachments/assets/b6e01c8e-da2d-458e-92f3-42b1832db9f7)


2) Perfrom detailed routing using TritonRoute and explore the routed layout.

Commands to run routing

```bash
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing
```
![image](https://github.com/user-attachments/assets/14ea1fc0-b044-4096-bef1-dd278122079a)

![image](https://github.com/user-attachments/assets/8f7be911-3f03-4cfb-9cf1-7b5e30a403c9)



*Commands to load routed def in magic in another terminal*

Change directory to the one that contains the routing .def
```bash
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/results/routing/
```
Open in magic.
```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```
![image](https://github.com/user-attachments/assets/147b504f-4fd9-4d9f-a1b7-c4fd16368267)

![image](https://github.com/user-attachments/assets/e7d77a7e-d063-445a-8858-4750f80c8d79)


3) Post-Route parasitic extraction using SPEF extractor.

*Commands for SPEF extraction using external tool (not nescessary in new openlane)*
Github link: https://github.com/HanyMoussa/SPEF_EXTRACTOR
```bash
# Change directory to the one where you have cloned the github repo
cd Desktop/work/tools/SPEF_EXTRACTOR
```
```bash
# Extract the spef
python3 main.py /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/results/routing/picorv32a.def
```

4) Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad
```
Read the .lef file we have created.
```bash
read_lef /openLANE_flow/designs/picorv32a/runs/21-01_15-14/tmp/merged.lef
```
![image](https://github.com/user-attachments/assets/94d7b9f2-8da3-4a37-a2a4-a50c35d11402)

read the .def file we have created.
```bash
read_def /openLANE_flow/designs/picorv32a/runs/21-01_15-14/results/routing/picorv32a.def
```
![image](https://github.com/user-attachments/assets/9d46d462-f187-40dd-a2c7-361121d51714)

```bash
write_db pico_route.db
```
```bash
read_db pico_route.db
```
Read the verilog file created in the synthesis step.
```bash
read_verilog /openLANE_flow/designs/picorv32a/runs/21-01_15-14/results/synthesis/picorv32a.synthesis_preroute.v
```
```bash
read_liberty $::env(LIB_SYNTH_COMPLETE)
```
```bash
link_design picorv32a
```
![image](https://github.com/user-attachments/assets/0ddf1360-a184-4b82-a59d-cdfda83c7df4)

```bash
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
```
![image](https://github.com/user-attachments/assets/434c24de-6542-44a2-b341-ff17cc34c69c)

```bash
set_propagated_clock [all_clocks]
```
Read the spef file we just extracted(not nescessary in new openlane)
```bash
read_spef /openLANE_flow/designs/picorv32a/runs/21-01_15-14/results/routing/picorv32a.spef
```
![image](https://github.com/user-attachments/assets/8023e356-da48-4a4b-abc8-34ef867e4799)

```bash
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
```
![image](https://github.com/user-attachments/assets/46d0eade-3990-45ed-96cf-5d4c46ae107c)

Exit the openlane flow.
```bash
exit
```
![image](https://github.com/user-attachments/assets/5aaa9402-afc1-45e1-9f03-6f2dbff93ef7)

# Acknowledgements

* [Kunal Ghosh](https://github.com/kunalg123), Co-founder, VSD Corp. Pvt. Ltd.
* [Nickson P Jose](https://github.com/nickson-jose), Physical Design Engineer, Intel Corporation.
* [R. Timothy Edwards](https://github.com/RTimothyEdwards), Senior Vice President of Analog and Design, efabless Corporation.

> To get a better grasp and understanding of certain parts of the course, [Fayiz Ferosh's repo](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd), shared as an example repo by Kunal Ghosh was reffered to. Some screenshots in the notes section have been taken from the lecture videos.
