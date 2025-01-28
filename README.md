# Sky130 - Digital VLSI SoC Design and Planning
![Static Badge](https://img.shields.io/badge/OS-linux%2C_Windows-orange)
![Static Badge](https://img.shields.io/badge/EDA%20Tools-OpenLANE--Flow%2C_Yosys%2C_abc%2C_OpenROAD%2C_TritonRoute%2C_OpenSTA%2C_magic%2C_netgen%2C_GUNA-purple)
![Static Badge](https://img.shields.io/badge/languages-verilog%2C_bash%2C_TCL-blue)

> 2 Week digital VLSI SoC design and planning workshop with complete RTL2GDSII flow organised by VSD and NASSCOM
![image](https://github.com/user-attachments/assets/19e505a6-89ae-471c-9f41-71b564b79899)


![image](https://github.com/user-attachments/assets/19e505a6-89ae-471c-9f41-71b564b79899)

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

![image](https://github.com/user-attachments/assets/19e505a6-89ae-471c-9f41-71b564b79899)
<image src = https://github.com/user-attachments/assets/19e505a6-89ae-471c-9f41-71b564b79899></image>

![image](https://github.com/user-attachments/assets/d205568a-d825-4035-98dc-01b19b7e3482)

#### Die, Pads, and Core

* **Pads** help transmit signals between the outside world and the interior of the package.
* **Core** is the area where the digital logic circuits are placed.
* **Die** refers to the size of the silicon chip itself, excluding the surrounding packaging material.

![image](https://github.com/user-attachments/assets/3ed62cd7-5ee8-41da-bbd1-f45354494a83)

#### C Program to Hardware

* A C program is first compiled into assembly language (typically RISC-V for this workshop).
* We then use a hardware description language (HDL) like Verilog or SystemVerilog to describe the hardware functionality. This HDL code represents the desired behavior of the circuit.
* The HDL code is then synthesized into a netlist, which is a low-level representation of the circuit's connectivity. 
* Finally, the netlist is placed and routed on the chip layout using Electronic Design Automation (EDA) tools.

![image](https://github.com/user-attachments/assets/b1d5077e-af87-445f-858d-eda2dfe0e4ca)

![image](https://github.com/user-attachments/assets/8fa7910e-9f64-4c50-b0e2-1f6aa5d3e535)

![image](https://github.com/user-attachments/assets/ae3569fe-ed0c-42e1-bd4b-3782a755d17b)

### Section 2 - SoC design and OpenLANE

#### ASIC Design Requires
* Hardware Description Language and RTL IP's
* Electron Design Automation tools.
* **PDK** Data

![image](https://github.com/user-attachments/assets/4b6c6cd7-45ad-4c47-a67c-98717669cd40)

#### Process Design Kit (PDK)

* A Process Design Kit (PDK) is a collection of files used to model the specific fabrication process for the EDA tools used to design an integrated circuit (IC). The PDK contains information about the available logic cells, routing rules and device parameters for a particular chip fabrication process.


![image](https://github.com/user-attachments/assets/0e605a89-6b0d-43c5-b453-119f8a0eb4e0)

#### RTL to GDSII Flow
* **Synthesis:** This stage converts the HDL code (e.g., Verilog) into a gate-level netlist. The netlist represents the circuit's functionality using basic logic gates.

![image](https://github.com/user-attachments/assets/0c936d2c-1744-4c30-8c41-33408bbfc768)

* Floor and Power Planning - In this stage, the chip layout is planned. The die area is divided into sections for different functional blocks and I/O pads. The power supply network is also designed to ensure proper power distribution throughout the chip.
 
* **Placement:** This stage involves positioning the logic cells from the netlist onto the chip layout. The goal is to find optimal locations for the cells considering factors like timing and area constraints. There are two main placement steps:

    * **Global placement:** This provides an initial placement for all cells, aiming for optimal positions but not necessarily following all layout rules. The placement in this step may not always be legal.
    * **Detailed placement:** This refines the initial placement to ensure all cells adhere to the design rules.

![image](https://github.com/user-attachments/assets/e239f1de-743b-4944-8f4e-85a1622e4003)

![image](https://github.com/user-attachments/assets/875a17e2-da54-4f09-a622-91ad19ba684d)

* **Clock Tree Synthesis (CTS):** A clock tree is a network of buffers and wires that distributes the clock signal to all sequential elements (flip-flops) in the design. CTS aims to minimize clock skew, which is the variation in arrival time of the clock signal at different flip-flops.

* **Routing:** This stage involves creating connections between the placed cells using metal layers available in the fabrication process. Routing is typically done in two steps:

    * **Global routing:** This defines the general paths for the connections between cells.
    * **Detailed routing:** This implements the actual wiring connections based on the global routing plan.

* **Sign-off:** This stage involves various checks to ensure the design meets the desired functionality and manufacturing requirements. Here are some common sign-off checks:

    * **Design Rule Checking (DRC):** This verifies if the layout adheres to the design rules specified by the PDK for the fabrication process.
    * **Layout vs Schematic (LVS):** This compares the final layout with the original gate-level netlist to ensure they are equivalent.
    * **Static Timing Analysis (STA):** This analyzes the timing delays in the design to ensure all signals meet the timing constraints and the circuit operates at the required frequency.

![image](https://github.com/user-attachments/assets/79c6679e-307d-43d4-8d86-875601805404)

* **Introduction to OpenLANE and StriVe**

* OpenLANE is an open-source design flow that aims to automate the entire process of generating a GDSII file from an RTL design, without requiring manual intervention.
* StriVe is a collection of open-source resources for SoC design, including open PDKs, EDA tools, and RTL examples. It provides features like Design Space Exploration to help find optimal design configurations and offers a growing collection of design examples (43 and growing).

Versions:

![image](https://github.com/user-attachments/assets/f4b80642-c7cc-4daa-8306-69bf3c7b7b4c)

#### OpenLANE ASIC Design Flow:

![image](https://github.com/user-attachments/assets/8d4c71b0-cf4d-4733-b1e7-dc6fc1ca1c08)

</details>

## Day 2-Good Floorplan vs Bad Floorplan and Introduction to Library Cells
### Section 1-Chip Floor planning considerations
<details>
<summary>
Theory
</summary>

#### Defining Width and Height of the Chip

![image](https://github.com/user-attachments/assets/9da17abc-dcb6-4483-b39b-0000e497c3cf)

* Let us begin with a _netlist_.
* **Netlist:** A netlist is a list of all the components (like flip-flops, gates) and their connections in a circuit.

![image](https://github.com/user-attachments/assets/878bfc10-b7ce-4413-a482-cfae027308e2)

* FF-Flip Flops
* A1, O1-AND Gate and OR Gate
* **Gates:** We assign a size (width and height) to each gate in the netlist, creating a unique box for each one.

![image](https://github.com/user-attachments/assets/8f4da4ec-c6dd-45a2-80fe-4049130f0d30)

* **Cell Areas:** We estimate the size of each cell in the netlist and calculate its area.

![image](https://github.com/user-attachments/assets/bbd15cd5-d91d-4cc3-9cd5-38ffe2b3030b)

![image](https://github.com/user-attachments/assets/a3e52aea-4646-4283-bd05-b96929f47915)

* **Core Placement:** We arrange all the logic cells (gates, flip-flops) inside the central area called core.

![image](https://github.com/user-attachments/assets/2811b693-b9af-4cb1-968e-1dffabdbc891)

![image](https://github.com/user-attachments/assets/a19c7cfe-f198-439b-a853-f7a8cfd16a2f)

* **Utilization Factor (UF):** This measures how efficiently the core area is used by the logic cells. UF is calculated as the area occupied by the netlist divided by the total core area. In real chips, UF is typically around 0.5-0.6.
* UF = Ar. occupied by netlist/total area of core.
* **Aspect Ratio:** This is the ratio of the core's height to its width. A value of 1 indicates a square core.

#### Preplaced Cells

* Preplaced cells are groups of predefined logic gates that are treated as a single unit.
* To create a preplaced cell, we first partition or divide the netlist into functional blocks or parts. We then create boxes around each part.

![image](https://github.com/user-attachments/assets/bc8e5ab9-4292-4d08-b487-04729a10f2b4)

* Then we extend the input and output io pins such that they are jutting out of the box.

![image](https://github.com/user-attachments/assets/fee27d62-090c-4fb4-bd5b-77c1f69c78d4)

* **Blackboxing:** We hide the internal details of each block by treating it as a black box with a specific number of input and output pins.

![image](https://github.com/user-attachments/assets/456a9cc5-6051-4ff7-aff4-674b1e9c08b0)

* After that, we separate the 2 boxes, each with their own inputs and outputs. Each peice or IP can be reused individually anywhere else in the circuit.

![image](https://github.com/user-attachments/assets/3e35c0de-b7c7-4c88-96cf-870e56260ac5)

* The arrangement of these IP's in the chip is known as floorplanning. These blocks have user defined locations and are placed before the automated placement and routing phase. Hence they are known as preplaced cells.

#### Defining Locattions of Pre-placed Cells

* **Preplaced Cell Locations:** Input pins are typically placed on one side of the chip (left or bottom), and output pins are placed on the opposite side (right or top). Preplaced cells are positioned closer to the input side for better connectivity.

![image](https://github.com/user-attachments/assets/88f4e2cf-154f-4e5c-b2d5-ffb05375ddbd)

#### Decoupling Capacitors

* Real-world (Practical) wires have resistance, which can reduce the voltage difference (voltage drop) between different parts of the circuit.

![image](https://github.com/user-attachments/assets/55d74ea2-6dbc-45be-9ba7-640665608993)

* This causes the voltage difference applied between the IP's to reduce.
* If this reduction is high, then the voltage will not be enough to trigger a logic 1 and will lie in the undefined region.

![image](https://github.com/user-attachments/assets/ba64b8ed-757c-4a96-982b-484c38908314)

* So to ensure that the piece of circut always has enough of a voltage drop, we use a decoupling capacitor.
* **Decoupling capacitors** are used to maintain a stable voltage supply for the circuit. They act as tiny batteries that can quickly release stored energy to compensate for voltage fluctuations.

![image](https://github.com/user-attachments/assets/26033d29-02d5-4a69-9b05-eac487368ba6)

* Decoupling capacitors are placed near pre-placed cells throughout the core area of the chip.

![image](https://github.com/user-attachments/assets/90442a41-de68-43e0-99f1-ab762705fbe0)

#### Power Planning

* Ground Bounce- It's a sudden change in the ground voltage due to simultaneous switching (dumping of current) of many components (capacitors). If the bounce is very high then the ground can enter into an undefined state.
* Voltage Drop- This occurs when a single power source is tasked with recharging multiple capacitors. It's a decrease in voltage along the power supply lines due to the immense amount of current drawn by the circuit. This leads to the power line to experiance a voltage drop, leading the voltage difference to go into the undefined region.
* The above problems are caused by an overloaded power line/ground line. This can be fixed by having multiple power and ground lines throughout the chip.
(The below image is representing a 16-bit bus when set as input for an inverter)

![image](https://github.com/user-attachments/assets/0e063592-1a59-4981-8473-8c986f3c913c)

![image](https://github.com/user-attachments/assets/d0e9736d-27cb-4d99-a542-2f4730df86e0)

![image](https://github.com/user-attachments/assets/bb9bfe6c-a732-4df0-bf14-f121c4df0a61)

(Power is coming from a single source)

![image](https://github.com/user-attachments/assets/2f6c18c1-702a-48f0-b947-ccce9bf38b4a)

(Power is coming from multiple sources. In this system, the power line's and ground line's are arranged in the form of a mesh)

![image](https://github.com/user-attachments/assets/0f2fb3d0-d276-451e-ba04-d01dd81cb2bb)

#### Pin Placement

* The goal is to optimize pin placement for better performance.
* Input and output pins are placed close to their corresponding pre-placed cells to minimize signal path lengths.
* Clock pins (input and output) are placed directly opposite each other to minimize resistance.
* Pre-placed cells are placed close together whenever possible to reduce the number of decoupling capacitors needed.

![image](https://github.com/user-attachments/assets/26379b57-883c-4344-9bfa-4ec735c0b480)

#### Logical Cell Placement and Blockage

* The space between the core and the die is filled with special blockages. These blockages reserve the area for pin placements and prevent the automated placement and routing tool from placing cells there.

![image](https://github.com/user-attachments/assets/c665ca47-10ad-4b38-b4e9-25c1fb800744)
</details>

### Section - 2: Library Binding and Placement
<details>
<summary>
Theory
</summary>
	
#### Libraries
* A **netlist** is a list of all the components (like flip-flops, gates) and their connections in a circuit. 
* Below is a netlist.

![image](https://github.com/user-attachments/assets/b65ad27e-6a11-4d7f-9fb5-b53b8f2fe265)

* We take all the cells in the netlist and place them in a shelf known as the **library**.

![image](https://github.com/user-attachments/assets/7d35f2dc-f855-43a3-9e3a-a95d110b1ca6)

* A **library** contains detailed information about each cell, including:

    * Dimensions (size)
    * Delay characteristics (how long it takes for a signal to pass through the cell)
    * Environmental requirements (e.g., voltage range)
    * Threshold voltage (minimum voltage required for the cell to switch states)
    * Below is a picture of libraries with same cells but different properties.

![image](https://github.com/user-attachments/assets/d2fc8881-16ba-450e-bc36-35b480f2cc4b)

#### Placement

* **Placement** is the stage where we estimte wire length and capacitance and, based on that, place repeaters. The placement process involves these steps:
    1. **Pre-placed cell placement:**  Placing specially designated cells at predefined locations.
    2. **Standard cell placement:**  Placing the remaining cells based on their connectivity to pins and other cells. Cells are positioned closer to the pins they connect with to minimize the wirelength. 
    3. **Repeater insertion:** If the distance between a cell and its connected pin is too large, buffers or repeaters are inserted to ensure reliable signal transmission.
    4. 
![image](https://github.com/user-attachments/assets/fd531659-19d3-473c-879a-48c2dbf76c44)

![image](https://github.com/user-attachments/assets/2d31f2e1-44d5-480e-897c-9c318014a717)
</details>

#### LAB tasks:-
1. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
```bash
run_placement
```
![image](https://github.com/user-attachments/assets/bad70e03-e9da-444a-8f77-6332389fcf0d)

* Goals for placement:
	* Cutting down on wire length
 	* Making sure placement is legal (cells don't overlap)

![image](https://github.com/user-attachments/assets/edd540ad-7e35-4e55-bb6a-5d4327502ad1)

![image](https://github.com/user-attachments/assets/077806b4-63a3-45be-9b8d-09ea0ef2f6fd)

2. Load generated placement def in magic tool and explore the placement.
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/<date>/results/placement/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

![image](https://github.com/user-attachments/assets/b1ef5506-8500-456b-9905-9b681a3c65fd)

![image](https://github.com/user-attachments/assets/618f4769-3c98-4e57-b9ca-270f39769f39)

### Section 3 - Cell design and characterization flows
<details>
<summary>
Theory
</summary>
	
![image](https://github.com/user-attachments/assets/a68ebd74-f7b0-46bd-9b6d-8f72615e0746)

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
![image](https://github.com/user-attachments/assets/e6f427e8-78be-41a6-bbe4-8008dad0abc4)

#### Delay Thresholds
* in_fall_thr: input fall threshold
* out_rise_thr: output rise threshold

![image](https://github.com/user-attachments/assets/6a8dc9c5-a86a-4148-8f04-c008dd1170b8)

* in_rise_thr: input rise threshold 
* out_fall_thr: output fall threshold

![image](https://github.com/user-attachments/assets/8bee2460-8cec-44cd-9562-231ebdf091ab)

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

![image](https://github.com/user-attachments/assets/53902d59-84f7-429b-b232-294f1c4235e1)

Pins overlap

![image](https://github.com/user-attachments/assets/cc6057c9-1a26-4fa2-9b04-4b2291e0bef7)

#### Spice Simulations
**PMOS**

![image](https://github.com/user-attachments/assets/f167cd44-b576-4eaf-8e2e-49848f303fca)

**NMOS**

![image](https://github.com/user-attachments/assets/ee07e099-8802-4587-838f-e1a3e2eeb5a5)

**Creation of spice Deck**
* We start from a netlist with component connectivity.

![image](https://github.com/user-attachments/assets/e6a81bb6-78e1-49de-aa9b-125ccd06daf6)

* We then define the component values. This includes input and supply voltage, load values, MOSFET values.

![image](https://github.com/user-attachments/assets/5f4e6fd4-d6a2-4f23-b0a6-92712fb0ec4e)

* Then we identify *nodes*.
* *Nodes* are 2 points lying on either side of a component.

![image](https://github.com/user-attachments/assets/59f9000d-fea4-4eb6-8a22-4650f3e56303)

* We name nodes and define MOSFETs by the name, followed by the nodes around it in the order drain-gate-source-substrate. Then we decribe it as NMOS or PMOS. This is folllowed by the width and length.

![image](https://github.com/user-attachments/assets/9e1d034c-e129-4120-9466-731b5c110557)


* We describe load and Voltage sources in a similar manner.

![image](https://github.com/user-attachments/assets/ac9e1c6b-2eae-4d60-8b51-8ea3100076da)

* We then give simulation commands.
* The order(essentially the syntax) Vcc <from> <to> <in steps of>

![image](https://github.com/user-attachments/assets/0dc42831-f8c2-4253-b312-3ef3e3ca9ed0)

* We then show the location of the model file which has all the technological parameters of everything in the netlist.

![image](https://github.com/user-attachments/assets/e27aabfe-7e11-41fc-ae84-89fc37d805ac)

Different w/l(width/length) ratios of PMOS can have changes on the output waveform.

#### Switching Threshold

![image](https://github.com/user-attachments/assets/7de4c7c4-b8f4-47ef-b9e2-30a2654dc414)

* Switching Threshold is the point where V<sub>in</sub> = V<sub>out</sub>

![image](https://github.com/user-attachments/assets/af97923f-1ad9-4ac6-bfd0-a24ccad3342c)

Switching threshold is the intersection of the lines.
* In this area both the NMOS and PMOS are in the saturation region.

![image](https://github.com/user-attachments/assets/342e498e-9610-4c51-841f-f612d7e86c40)

if Vin = Vout means gate voltage = drain voltage, Vgs = Vds
* the currents of the NMOS and PMOS will be the same, however the directions will be different.
* I<sub>dsP</sub> = I<sub>dsn</sub>
* Pulse definition in spice deck: V <location based on nodes> pulse <start voltage> <end voltage> <shift(delay in start)> <rise time> <fall time> <pulse width> <width of complete cycle>

![image](https://github.com/user-attachments/assets/7825843b-73ca-4958-8e71-7f7469e7ee0b)

Delay(rise or fall): Out-In(at 50% w.r.t. time)

![image](https://github.com/user-attachments/assets/b4926dae-1d83-4957-bf84-735d6e3768fc)
</details>

### Section 2 - Inception of Layout ÃÂ CMOS fabrication process

#### 16 Mask CMOS proscess

1) Select a substrate - The part on which everything is fabricated on. The doping level should be less than well doping.
2) Creating active region(pockets) for transistors - We keep gaps and isolation between each and every pocket to avoid interference.
	* Grow a layer of silicon dioxide (insulator) on the substrate.
 	* Then deposit a later of Silicon Nitride on it.
 	* After that, deposit a layer of photoresist on top of the Silicon Nitride layer.
  	* Add a protectional layer of Mask 1 on the area where the pockets are to be made. UV light is shined on top of the mask.

![image](https://github.com/user-attachments/assets/b7c7712b-f912-489f-b22c-c4295832bb8d)

   * Wash out the unmasked area in developing solution.

![image](https://github.com/user-attachments/assets/7a5e3b6a-e91e-40ab-bc26-3d86dc9a0c3d)

   * Remove the Mask and etch off the Silicon Nitride that is not protected by photoresist.
   * Remove all the photoresist chemically.

![image](https://github.com/user-attachments/assets/4921420e-b0af-458a-afb6-103eb8c8501b)

   * Grow the Silicon di-oxide once more by placing it in an oxidation furnace. You will observe that the area under the silicon dioxide remains untouched. The area under the edges of the silicon di-oxide though, is not protected due to strong growth. This creates isolation areas between pockets. This proscess is known as LOCOS(Local oxidation of Silicon).

![image](https://github.com/user-attachments/assets/f9e80655-be60-49d2-8f80-c2efd5b0f4e2)

![image](https://github.com/user-attachments/assets/8044a472-e676-498c-a7f4-13103c4c84cf)

   * The silicon Nitride is stripped using hot phosphoric acid.

![image](https://github.com/user-attachments/assets/6d473439-e500-43f5-a29e-e535d858177a)

3) N-well and P-well formation:
	* Photoresist is added again and a portion is protected by Mask 2.
	* Mask 2 in layout.

![image](https://github.com/user-attachments/assets/8e7f8738-dee1-4538-acbd-85747adc0f31)
‎ 
	* It is again subjected to UV light and wahed. The mask is removed and then subjected to Boron in a process called ion-implantation to form a P-well.(High energy, about 200keV is needed). The oxide layer is damaged.
	 
![image](https://github.com/user-attachments/assets/30c86043-291d-4b8d-8813-936bb9a3b8b9)
‎
	* The same step is done using Mask 3 to form a N-well except this time we replace bororn with phosphorus.
 
![image](https://github.com/user-attachments/assets/d19c0e18-96c0-493e-8f51-4133c94830d7)
‎
	* We now have a N-well and a P-well.
 
![image](https://github.com/user-attachments/assets/51a10612-958d-4ef0-a8a9-488a7bb49e8f)
‎
	* We then do drive-on diffusion and diffuse the wells to about half the substrates height by placing it in a high temprature furnace.(This is known as theh twin tub proscess)
 
![image](https://github.com/user-attachments/assets/7874f69a-96ae-488f-b780-719215a143aa)

4) Formation of gate: 
	* The doping concentration and oxide capacitance impact the threshold voltage.
	* We repeat the steps done with mask 2 again with mask 4.

![image](https://github.com/user-attachments/assets/86e388c2-82a4-4415-8875-54fce77059dc)
‎
	* We again put it under the effect of boron with leser energy to create a smaller P-well with doping concentration adjusted to meet requirements.

![image](https://github.com/user-attachments/assets/b5daa49c-463c-4c8d-8bb1-0532053ebcc8)
‎
 	* Same thing is one with mask 5, similar to the steps done with mask 3. This time, arsenic can be used in place of phosphorus. The oxide layer will be damaged.

![image](https://github.com/user-attachments/assets/5bcd82b0-b922-4d5c-a1b2-e3b0e8bb3b73)
‎
 	* The original damaged oxide is then etched/stripped using dilut hydrofluric (HF) solution.

![image](https://github.com/user-attachments/assets/b22e5495-efad-431b-8af4-795322f4db53)
‎
	* Then, it is regrown to give high quality oxide. The oxide thickness (corresponding to oxide capacitance) is maintained as per required threshold voltage.

![image](https://github.com/user-attachments/assets/1cbc77b1-6672-4352-9dbe-f125b6e1895d)
‎
	* After this, a polysilicon layer is deposited on the oxide layer. We then dope it with N-type ion implants for low gate resistance.

![image](https://github.com/user-attachments/assets/c85a201d-857a-47b5-ad5c-6ea7a965d23e)
‎
	* Another photoresist layer is deposited and shaped as shown in figure with the help of mask 6 (polysilicon). Then mask 6 is removed followed by the photoresist. Also given below is how mask 6 looks in a loyout.

![image](https://github.com/user-attachments/assets/6b8f5ff8-8b65-4c4e-a21d-5cb763f8938f)

![image](https://github.com/user-attachments/assets/3d539bc6-e56f-4053-96d4-6b4a7610e904)
	
![image](https://github.com/user-attachments/assets/fdfc8448-0bd7-4cd4-9fa6-45f1447d3750)
	
5) Lightly doped drain formation:
	* This is done mainly for 2 reasons-
		i) Hot electron effect: when we decrease the size of the chip, the electric feild value becomes high as we dont usually change the power supply. The high energy carriers break Si-Si bonds. It might also break the 2eV barrier between the Si conduction band and the Silicon-dioxide condution band and get into the oxide layer.

		ii) Short channel effect: for short channels, it becomes harder for the gate to control the source and the drain current.

	* Build a photoresist layer over the N-well using Mask 7. Then we implant phosphorus in our P-well to create a N- implant. The energy is also regulated to make sure the N-implant does  not penetrate deep into the well. Remove the photoresist.

![image](https://github.com/user-attachments/assets/bea95150-8ee1-4b71-9fe9-58691aaf6336)
‎
	* Do the same thing on the other side using Boron and Mask 8 to create a P- implant.

![image](https://github.com/user-attachments/assets/31460010-ec14-45c5-8972-cbd38b2ec84c)
‎
	* ***Side wall spacers:*** Deposit a thick layer of Silicon Nitride or Silicon di-oxide. Then perform anisotropic plasma etching. This remoed all the silicon di-oxide, oxide layer and nitride except for where the polysilicon is.

![image](https://github.com/user-attachments/assets/95163ffb-b3c2-4fc4-90a2-8ca0a1655f31)

![image](https://github.com/user-attachments/assets/f617ea2c-1fb9-4b91-8f5f-ed1645a31963)
‎
 	* The side wall spacers help in making sure that some of the N- and P- dopings are preserved.
 
6) Source and drain formtion:
	* We add a thin oxide layer to prevent ions from interfering with the P-substrate (chanelling).

![image](https://github.com/user-attachments/assets/09828b58-90a5-4764-aab8-90036e061193)

 * Steps done to create ligtly dope drains are repeated.
 * The N- and P- implants are still present thanks to the polysilicon and the side wall spacers.

![image](https://github.com/user-attachments/assets/573d6246-e5a5-4935-bea8-1283245f0c1e)

![image](https://github.com/user-attachments/assets/ad7eef9e-713f-4671-a495-7de5d6e81cd3)

 * Annealing is done in high temprature. The implants will go deeper into the wells.

7) Steps to form contacts and interconnects(local)
	* Remove the thin screen oxide layer.
	* Titanium (low resistance) is deposited on the wafer surface using *sputtering*.
	* In *sputtering* titanium metal is bombarded with argon gas. The titanium atoms will get sputtered out and get deposited onto the substrate.

![image](https://github.com/user-attachments/assets/9b56ee2a-164d-4eca-8da3-a9bdeaaf8237)
‎
 	* Wafer is heated at tempratures of 650-700°C in N<sub>2</sub> ambient for about 60s. This results in Titanium Silicon di-oxide(low resistant contacts)

![image](https://github.com/user-attachments/assets/1759c36d-6b7d-48a9-a41e-336374c4296a)
‎ 
	* TiN is also formed due to nitrogen ambient. It is used only for local communication.
	* Polysilicon placed with help of mask 11 as so. Mask is removed.

![image](https://github.com/user-attachments/assets/b052ceb1-ea27-4461-8d03-20fcbd75527c)
‎
	* Excess TiN is etched using RCA cleaning which consists of-

![image](https://github.com/user-attachments/assets/830bba66-1c56-4a17-90ae-9bee8a107945)

![image](https://github.com/user-attachments/assets/44c4df01-778e-44c5-89df-8bb6da3c5948)

8) Higher metal level formation:
	* Now we deposit a thick layer of SiO<sub>2</sub> doped with phosphorus or boron. This is done to give a protection against mobile sodium ions(phosphorus). Doping with boron reduces temperature.

![image](https://github.com/user-attachments/assets/58875442-8edc-44bb-ae75-6a9e0de9442b)
‎
	* Chemical Mechanical Polishing(CMP) is done to flatten out wafer surface.

![image](https://github.com/user-attachments/assets/9c5220d6-1464-4e43-8745-12d1c849e8bc)
‎
	* Next we use mask 12 and photoresist on areas where we do not need contact holes. We also etch off the SiO<sub>2</sub> in places where we need the contact holes. We remove the photoresist.

![image](https://github.com/user-attachments/assets/f98eb323-c235-4e28-89b1-f49d7d1a7e28)
‎
	* We then deposit a thin layer of Titanium Nitride.
	* We then deposit a blanket tungsten layer on top of the TiN. It serves as a good interconnect between the bottom and top layers.

![image](https://github.com/user-attachments/assets/cb96d804-ec61-4e52-a831-e6a09c01fa30)
‎
	* We again do CMP to remove excess Tungsten and planarise the wafer surface.
	* Next we add an aluminium layer to take it to the top layer. We remove unnecesarry parts using mask 13 and photoresist as shown in diagram. Plasma etch out the remaining Al. Remove photoresist.

![image](https://github.com/user-attachments/assets/30141880-0e05-4f24-92bc-b12190501a21)
‎
	* We now already have 2 matal layers. To make another one, we deposit more Silicon di-oxide and perform CMP to make the surface planar.
	* Using mask 14, define contact holes.

![image](https://github.com/user-attachments/assets/9376c43f-57f9-4368-b5c8-3e3d1f23baca)
‎
	* Deposit a small layer of tin, and a layer of tungsten, before removing excess using CMP.

![image](https://github.com/user-attachments/assets/417e9910-2bda-4b52-ae94-97a9687911a3)
‎
	* Using mask 15, make another deposit of Al interconnects over the tungsten as shown in diagram. This layers interconnects should be thicker than the ones on the prepious layer.

![image](https://github.com/user-attachments/assets/563342f6-a0a2-40d7-9aa2-d4190c1ec85c)
‎
	* Deposit the top layer of dielectric (Silicon Nitride or Silicon dioxide) to protect the chip.

![image](https://github.com/user-attachments/assets/f06a7420-af7c-466c-9dfa-0422ee80371f)
‎	
	* Finally use mask 16 to drill contat holes and bring contacts outside the chip.

![image](https://github.com/user-attachments/assets/d5e617b5-bf70-4d07-8027-d29457b0f2b1)


## Day 4 - Pre-layout timing analysis and importance of good clock tree

### Section 1 - Timing modelling using delay tables

* Logic gates can be used to regulate clock too.

![image](https://github.com/user-attachments/assets/57f2833a-32d2-4eef-9c39-f24a218765ed)

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
![image](https://github.com/user-attachments/assets/2f58c120-ae46-4009-8a59-a85f8e616fc7)

![image](https://github.com/user-attachments/assets/1652e4ff-3b96-4ba2-99fc-e993baa316b2)

![image](https://github.com/user-attachments/assets/53f57a33-5b1d-44ef-97a1-64aa3dea2dfe)

2. Calculating Flop Ratio
```
Flop Ratio = No. of D flip flops / No. of cells = 1613 / 14876 = 0.10842968539
```
![image](https://github.com/user-attachments/assets/5402f41f-636d-48e9-aabe-75c9e7fb2655)

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

![image](https://github.com/user-attachments/assets/a1fcd5d0-6bbf-4b0f-b599-77f287edd878)

![image](https://github.com/user-attachments/assets/bf37a35f-db76-4600-9cbc-a4de94e0543b)

![image](https://github.com/user-attachments/assets/079157d1-d1f9-49e4-a914-66f3cbb0dac6)

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
![image](https://github.com/user-attachments/assets/03e1155e-29d2-4677-bcbe-6f88e8980271)

![image](https://github.com/user-attachments/assets/90f45ac7-8a77-4f72-9ed2-6bb9aadd6299)

![image](https://github.com/user-attachments/assets/4eee6ebc-24c1-4ed1-a495-03c00b5ea8dd)

![image](https://github.com/user-attachments/assets/e6f40de7-5321-426d-a9ba-da8a94ffcc60)

![image](https://github.com/user-attachments/assets/14bf557a-6bed-4ade-b205-29eea86844d3)

![image](https://github.com/user-attachments/assets/a7c48652-9cfd-479f-a504-f7ad1e941f12)
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
![image](https://github.com/user-attachments/assets/395c90f1-d744-480b-9498-493d7fe40506)

2. Copy the sky103A.tech file to /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/
```bash
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech
```
```bash
magic -T sky130A.tech sky130_inv.mag &
```

![image](https://github.com/user-attachments/assets/ee2f43e0-f17c-4a70-9d41-d46ca3b12221)

3. Load the custom inverter layout in magic and explore

Opening inverter in magic

![image](https://github.com/user-attachments/assets/774029c2-bc6d-4b3d-9c89-7e6cf6830768)

Identifying PMOS

![image](https://github.com/user-attachments/assets/c3e909cb-7418-4d9e-9c09-b42eec88ae1c)

Identifying NMOS

![image](https://github.com/user-attachments/assets/49a47ff4-71d6-44c1-9fe0-2ca88898e05c)

Output Y's connectipn to NMOS and PMOS verifies

![image](https://github.com/user-attachments/assets/37fc7f81-c8a4-4f0e-a4e7-7aa23960351f)

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
![image](https://github.com/user-attachments/assets/dbd03871-4ffb-4957-ab6e-551812abf258)

5. Editing the spice model file for analysis through simulation.

![image](https://github.com/user-attachments/assets/f4a95d27-55e7-4847-9e57-c13aeb9edd8d)

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
![image](https://github.com/user-attachments/assets/83917415-afc0-4956-bef8-a5ab91455b4d)

```bash
# install ngspice
sudo apt install ngspice
ngspice sky130_1nv.spice
```
![image](https://github.com/user-attachments/assets/0581c877-dd6c-440f-897c-89506d7d8f3f)

```bash
plot y vs time a
```
![image](https://github.com/user-attachments/assets/9f326ae0-5e7d-4760-8341-4c81c0501c96)

Rise transition time calculation
```
Rise transition time=Time taken for output to rise to 80%−Time teken for output to rise to 20%
```
```math
20\%\ of\ output = 0.66\ V
```
20% screenshot

![image](https://github.com/user-attachments/assets/bd95a1aa-ee4c-4574-b9da-7ca66ea61143)

```math
80\%\ of\ output = 2.64\ V
```
80% screenshot

![image](https://github.com/user-attachments/assets/485d4c41-4207-4238-8709-8b5b33e9ebc7)

![image](https://github.com/user-attachments/assets/10ce95f1-2933-4d85-9d53-6a33be202944)

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

![image](https://github.com/user-attachments/assets/ac8dc74a-5a1c-4e82-a808-81d7b9773e8e)

80% screenshots

![image](https://github.com/user-attachments/assets/68732488-46bc-43a4-ba4c-ac4d514af9d0)

```
x0 = 4.09167e-09, y0 = 0.66

x0 = 4.05075e-09, y0 = 2.64043
```

![image](https://github.com/user-attachments/assets/6580edbb-ca6a-4183-b43e-fed1a87f04ba)

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

![image](https://github.com/user-attachments/assets/1abea775-c041-4360-a13c-dc7f82c53668)

![image](https://github.com/user-attachments/assets/e2bcff5c-60da-4503-81c3-fad294fbd979)

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

![image](https://github.com/user-attachments/assets/ba0bc505-07ed-4c46-9462-c20adad7e1cd)

![image](https://github.com/user-attachments/assets/b134cb72-3d2b-4562-83d5-c5606c07615a)

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

![image](https://github.com/user-attachments/assets/c0e678b8-4368-4ea5-86a7-fc021664193a)

Screenshot opening metal layer 3

![image](https://github.com/user-attachments/assets/4c42c18d-91b5-4539-a817-bcf8db0afc59)

Screenshot of difftap rules.

![image](https://github.com/user-attachments/assets/77365844-9ac3-43c7-9a4a-781cd9143ff3)

Identifying inaccuracy

![image](https://github.com/user-attachments/assets/1161831d-db87-4147-916a-e74aa2796044)

Correction to sky130A.tech

![image](https://github.com/user-attachments/assets/e76928cc-476e-4b2c-88fe-f2ce8a49dab6)

The DRC error is now showing with respect to the new rule entered by us.

![image](https://github.com/user-attachments/assets/854e8092-296a-441d-be83-b71e5fda9279)

### Nwell.4 Complex rule correction

Identify the nwell withut the tap.

![image](https://github.com/user-attachments/assets/cf31c6ae-5d8f-4ce4-ac13-ceb559f71503)

Nwell rules page:

![image](https://github.com/user-attachments/assets/0c3ce633-6ffd-42de-a9f8-c3c499724b13)

No drc error shown!

Edit syy130A.tech file to update drc rules
![image](https://github.com/user-attachments/assets/8e956683-67a5-41a5-97d7-2a1032bf95da)

(illegal spelling changed)

![image](https://github.com/user-attachments/assets/e4651710-46b7-455a-961d-b6f8456536b0)

```bash
# Load updated .tech file
tech load sky130A.tech

drc style drc(full)

# re-run drc check
drc check

drc why
```

DRC error shown

![image](https://github.com/user-attachments/assets/667decbc-e03d-430b-8a72-c182d5c50abd)
 
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

![image](https://github.com/user-attachments/assets/d41bb4b3-a82a-4a9d-9afd-d4acefe53b3a)

```bash
# To understand the syntax
help grid
```
```bash
# Setting grid values
grid 0.46um 0.34um 0.23um 0.17um
```
Grid

![image](https://github.com/user-attachments/assets/34e6762f-7582-4ad2-880c-3dd6471067cb)

![image](https://github.com/user-attachments/assets/36b52c24-fb1b-444a-9542-60b7917cefde)

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

![image](https://github.com/user-attachments/assets/d56daaa4-4f0d-45a2-8238-11adfa40548b)

2. Generate lef from the layout.

![image](https://github.com/user-attachments/assets/f76d941a-c8ce-4916-b543-2a2e781de94b)

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
![image](https://github.com/user-attachments/assets/3d32e417-146c-42b8-b7b1-33dab0bfa48b)

Open picorv32A/config.tcl with GVIM

![image](https://github.com/user-attachments/assets/6bf0b561-04ab-4bf0-aa75-79b1f6111c60)

Edit config.tcl to this

![image](https://github.com/user-attachments/assets/4840e18f-f0b6-4501-8656-4fa94e1a8c92)

Now perform steps to open OPENLane and prep picorv32a.

![image](https://github.com/user-attachments/assets/927c7b63-6d8d-41fb-b07e-407bb9ea6d4f)

Include newly added lef to flow using
```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```
Run synthesis

![image](https://github.com/user-attachments/assets/d2f57daf-8182-426b-9b80-0459b10a506e)

![image](https://github.com/user-attachments/assets/ef9318fa-55cb-4720-a205-c4d26c37c9fc)

Perform these modifications

![image](https://github.com/user-attachments/assets/89eafcfa-592e-445b-92bf-911e120a27b2)

Run synthesis

Negative slack becomes 0

![image](https://github.com/user-attachments/assets/e59d9bf0-f0f6-4044-9ac0-36ce689c95b0)

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
![image](https://github.com/user-attachments/assets/42aec05f-e216-4232-9cb5-f5b43155e373)

Next we run placement

![image](https://github.com/user-attachments/assets/8e8f69df-a633-455a-83fc-6668856be0db)

Open placements results using
```bash
cd /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image](https://github.com/user-attachments/assets/82294020-ee0f-4252-8246-6d6fd94ef44f)

![image](https://github.com/user-attachments/assets/b57d71a5-df69-4829-92a0-72bc20a14c00)

![image](https://github.com/user-attachments/assets/4e918dad-bce2-4124-96fd-0ef91d76a6ba)

Expand to view internal activity of layers

![image](https://github.com/user-attachments/assets/18aae716-f813-47e4-998b-32ffe02e22cf)

#### Post synthesis STA with OpenSTA.
 1) Run all steps untill synthesis again.
 2) Create pre_sta.conf in openlane dir and my_base.sdc in openlane/designs/picorv32a/src.
 
 ![Taken from https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main](https://github.com/user-attachments/assets/5ea6e341-cc89-437e-a16b-abb395c44422)

 ![image](https://github.com/user-attachments/assets/ded68e6f-f07f-4d99-9742-42c53a536669)
 
 ![image](https://github.com/user-attachments/assets/74e303e8-f2f3-4c8f-90ac-e8488f916680)

```bash
cd Desktop/work/tools/openlane_working_dir/openlane

sta pre_sta.conf
```
![image](https://github.com/user-attachments/assets/12e8551c-0b55-4238-b0f2-8b5f5ce17cdd)

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
![image](https://github.com/user-attachments/assets/aad6f5a5-b5a7-4711-b0db-a4239b5d3fd1)

Open the STA file and run it
```bash
cd Desktop/work/tools/openlane_working_dir/openlane

sta pre_sta.conf
```
![image](https://github.com/user-attachments/assets/fbfad683-57bc-4569-9c22-0f9e642f55f8)

5) Make timing ECO fixes to remove all violations.

6) Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Commands to make a copy of the netlist.

```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/21-01_15-14/results/synthesis/

ls

cp picorv32a.synthesis.v picorv32a.synthesis_old.v

ls
```
![image](https://github.com/user-attachments/assets/ba46efae-7c7a-40f9-b0ae-6f5d75852ea9)

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
![image](https://github.com/user-attachments/assets/f1807441-4c35-4146-a181-5b9c2e69e5b4)

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
![image](https://github.com/user-attachments/assets/41d0d81b-9bc6-460b-a582-a25dd35b8c14)

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
![image](https://github.com/user-attachments/assets/a049a01d-e444-4367-9542-f2b237029317)

```bash
# Loading the created database
read_db pico_cts.db
```
![image](https://github.com/user-attachments/assets/140d2889-fd99-407a-99bd-fcf955727aa5)

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
![image](https://github.com/user-attachments/assets/2321ca77-3053-4a3d-aa64-814897ccff96)

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
![image](https://github.com/user-attachments/assets/e1ab81c7-768a-4f7b-b813-4e900f1d0d1c)

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
![image](https://github.com/user-attachments/assets/2239e209-25f5-483a-b626-d82da84adcdf)

```bash
run_cts
```
```bash
echo $::env(CTS_CLK_BUFFER_LIST)
```
![image](https://github.com/user-attachments/assets/bcb37aeb-7527-437d-86a2-5643b7897451)

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
