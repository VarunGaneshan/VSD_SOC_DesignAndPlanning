![Screenshot 2024-04-13 at 18-51-16 Digital VLSI SoC Design and Planning](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8dac8fb8-1ab9-496e-9938-8b69647660f3)

# Digital VLSI SoC Design and Planning

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/6cd44a71-c8f5-4936-aaeb-f33dddae42f5)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d13750d8-9dab-424a-b840-5bb354610722)


The VSD Squadron board's chip was designed using the flow discussed in this workshop.This chip is a 48 pin QFN package.Inverter is used as the macro in this workshop.

> https://vsdsquadron.vlsisystemdesign.com/digital-vlsi-soc-design-and-planning/

# Contents 

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a443bbce-ef34-4128-8685-337cf54be8e1)

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

</head>
<body>

<div class="toc">
  <ul>
    <li><a href="#header-1">Section 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK (11/04/2024 - 12/03/2024)</a>
    </li>
  </ul>
</div>

<div class="toc">
  <ul>
    <li><a href="#header-2">Section 2 - Good floorplan vs bad floorplan and introduction to library cells (13/03/2024 - 14/03/2024)</a>
    </li>
  </ul>
</div>

</body>
</html>

# <h1 id="header-1">Section 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK (11/04/2024 - 12/03/2024) </h1>	 

## <h1 id="header-1_1">1.1 -  How to talk to computers?</h1>

### <h1 id="header-1_1_1">1.1.1 - Introduction to QFN-48 Package, chip, pads, core, die and IPs</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/391e3b2e-0c68-498f-9493-b459bb51dafc)

This a typical Board that contains an SOC with peripherals.Our focus is on the chip/processor.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/1650187e-f4a5-4670-aaa3-6baf7e8d82b5)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/04d5aa7f-a716-4009-8ec6-a7bb37e482ce)

This is an example of QFN-48 package.The chip is connected with the package using wirebonds.

- Package : A package is the external casing that surrounds and protects the integrated circuit (IC) die. This casing provides mechanical support, electrical connections, and protection against environmental factors such as moisture, dust, and physical damage. The package also facilitates the connection of the chip to external components or circuitry, typically through pins or solder balls.Packages come in various forms and sizes, ranging from small, surface-mount packages like quad flat no-leads (QFN) and ball grid arrays (BGAs) to larger, through-hole packages like dual in-line packages (DIPs) and small outline integrated circuits (SOICs). The choice of package depends on factors such as the intended application, space constraints, thermal considerations, and manufacturing requirements.

- QFN-48 : A QFN-48 package is a type of integrated circuit packaging commonly used in modern semiconductor devices. This package features a square shape measuring 7mm by 7mm, with leads on all four sides, providing a compact and efficient solution for mounting semiconductor chips onto printed circuit boards (PCBs). The absence of traditional wire leads reduces the overall size of the package and enhances thermal performance, making it suitable for applications where space and heat dissipation are critical concerns, such as mobile devices, consumer electronics, and automotive systems.

- Wirebonds : Wire bonding is a method used in semiconductor manufacturing to create electrical connections between the integrated circuit (IC) die and the external leads of the chip package. Thin wires made of gold or aluminum are attached to bond pads on the die and the package substrate using specialized equipment. 

**Components of a chip:**
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a0c09423-1663-4a32-a59e-235d42654601)

- Pads: These are areas on the surface of the chip used for making electrical connections. Pads typically connect the chip to external components or the package.
  
- Core: The core of a chip refers to its central processing unit (CPU) or the primary computational component where most of the processing tasks occur.
  
- Die: The die is the small, square or rectangular piece of semiconductor material that contains the integrated circuitry of the chip. It's typically made from silicon and contains the transistors, resistors, and other components that make up the chip's functionality.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/3cb6faea-c21d-45d1-bba2-1e2b136f94f6)

This is an example of a typical RISC-V chip.

- Foundary : A foundry is a specialized facility that manufactures integrated circuits for semiconductor design companies. It provides the equipment and expertise for high-volume production of chips, allowing companies to prototype and produce electronics without their own manufacturing facilities.

- Intellectual Property : It refers to inventions, designs, and processes, that are legally protected under patents, copyrights, or trade secrets.

- Foundary IPs:In chip design, IP can include pre-designed circuit blocks, algorithms, or software modules that are licensed or owned by companies for integration into their own designs, saving time and resources.Foundry IPs can include standard cell libraries, memory compilers, I/O libraries, analog and mixed-signal IPs, and various other building blocks required for chip design. 
  
-  Macros : They are pre-designed and pre-verified blocks of digital circuitry that perform specific functions. These macros are often complex and can include components such as arithmetic units, memory controllers, or communication interfaces. Designers use macros to expedite the development process by integrating proven, reusable blocks into their designs, rather than designing them from scratch. This approach saves time and effort and helps ensure reliability and consistency in chip design.

### <h1 id="header-1_1_2">1.1.2 - Introduction to RISC-V</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a0f3ebb5-fe4d-419b-ba63-9e03b715601d)

If a user wants to run a certain program in a chip (here a swap c code) , the abstract flow goes like compiling the program,what happens behind is converting the code(Specs) to a assembly langugae program/instructions based on its architecture(here RISC-V) which is then converted to a machine language program(binary).Concurrently,a RTL corresponding to the specs(here picorv32) is generated which through RTL2GDSII flow can be physically realized on a chip.

- RISC-V : RISC-V is an open-source instruction set architecture (ISA) that defines the instructions and functionalities of a computer's central processing unit (CPU).
  
- PicoRV32 CPU core : It is a lightweight and compact implementation of the RISC-V ISA.It is known for its small size, low power consumption, and ease of integration into FPGA (Field-Programmable Gate Array) designs. Despite its simplicity, PicoRV32 still provides essential features such as pipelining, branch prediction, and support for both 32-bit and 64-bit RISC-V instructions. 
  
- Qflow layout : Qflow is an open-source digital synthesis and layout tool flow used in the design of integrated circuits (ICs). It provides a suite of tools for performing various steps in the chip design process, including synthesis, place and route, and layout generation. 

### <h1 id="header-1_1_2">1.1.3 - From Software Applications to Hardware</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8b83cddf-91ec-44e5-a57b-3b99d270e079)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d57d4c1d-0ea5-4907-a05b-2f100115e2e9)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d88c02fb-f5e4-4379-ad79-9932dabe1cd9)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ba11217d-c80d-43a7-8c5e-d1581b292c31)
Similar to the flow discussed in the previous section,we see the flow starting from a software application.

- Instruction Set Architecture : ISA defines the set of instructions and how they are encoded for a specific CPU architecture. It dictates how software communicates with the hardware, specifying operations like arithmetic, data movement, and control flow. ISAs can vary widely, influencing factors such as performance, power efficiency, and software compatibility.

- RTL : It is a hardware description language abstraction level used in digital circuit design. It describes the behavior of a digital system by detailing the flow of data between registers and logic elements. RTL designs are closer to the hardware implementation, making them suitable for synthesis and subsequent physical design stages.

- synthesized netlist : It is a digital blueprint of a circuit created after synthesis. It lists the electronic components and connections, representing the logical structure of the circuit without detailing its physical layout. This netlist serves as an intermediate step for further optimization and analysis in the chip design process before actual implementation.

- Physical Design : Physical design involves the transformation of a logical design (such as RTL) into a physical layout that can be manufactured as a semiconductor chip.It encompasses tasks like floorplanning, placement, routing, and verification

## <h1 id="header-1_2">1.2 - Soc design and OpenLANE</h1>

### <h1 id="header-1_2_1">1.2.1 - Introduction to all components of open-source digital asic design</h1>

**Asic Enablers:**

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/e580415b-7394-4195-8f47-5d523ec339a9)

- EDA tools : Electronic Design Automation tools are software applications used in electronic system and integrated circuit design. They automate tasks like schematic capture, simulation, synthesis, place and route, timing analysis, physical verification, and power analysis. These tools are crucial for creating complex electronic systems efficiently and accurately, reducing development time and cost.

- PDK : Process Design Kit is a collection of files and documents provided by semiconductor foundries to support the design of ICs using their manufacturing processes. PDKs contain information about the foundry's fabrication processes, including design rules, device models, parameterized cells (PCells), technology files, and simulation models. Designers use PDKs with EDA tools to create custom IC layouts and verify their designs before manufacturing. 

-  Open Source PDK : The Open Source PDK from Google and SkyWater Technology Foundry offers a freely available Process Design Kit (PDK) based on the 130nm technology node. [Github](https://github.com/google/skywater-pdk)

**Is 130nm old and not in use?**

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d5b2302f-b775-4309-acd3-2dd5f7c9ee75)

6%-4.5B revenue.Despite its age, 130nm technology still finds use in various specialized applications where cost, power efficiency, and reliability are more critical than cutting-edge performance or density.Intel

**Is 130nm fast?**

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/425b9c99-813c-44f2-ae69-66506f00c56c)

- It is capable of supporting clock speeds sufficient for various applications, especially when coupled with optimized designs and modern design methodologies.
- Intel P4EE(Q4'o4) : The Intel Pentium 4 Extreme Edition (P4EE) processor, released in Q4 of 2004, operated at a clock speed of 3.46 GHz. This high clock speed was achieved through aggressive transistor scaling and optimization techniques available at the time

- sky130_OSU (single cycle RV32i CPU) : Designed using the open-source PDK for the 130nm process node, it can achieve a clock speed of more than 1 GHz.

### <h1 id="header-1_2_2">1.2.2 -  Simplified RTL2GDS flow</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/b01efcad-b8b3-4d27-82a8-f7eca7003978)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/25ca3433-d156-446d-8a14-c7fe64b7c647)

Several steps-Methodology-RT2GDS/Automated Pnr/Physical Implementation

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/95bb7d19-b041-4c0d-a908-90d861364b1d)

- Synthesis : This stage involves translating a high-level hardware description into a netlist of logic gates and flip-flops. It's the process of converting RTL design into a gate-level representation.

- Standard cells : Standard cells are basic components in digital integrated circuit design, comprising pre-designed logic gates and flip-flops.Provided by semiconductor foundries as part of a PDK, standard cells offer benefits such as faster design turnaround time and improved manufacturability.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/2cb4d4ff-a82d-45fd-b11d-0af9a1dd7ec4)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ab2135b8-7d11-448f-a5d2-9c8025a68667)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/55cff142-d192-4339-ac64-67d6c5b2ef16)

- Floor/Power Planning : In this stage, designers decide how to partition the chip's layout space and allocate resources such as power supplies and signal routing channels. It involves making decisions about where to place major components and how to manage power distribution.

- Chip Floorplan involves the initial layout planning of the various components and functional blocks on a semiconductor chip. It determines the placement of major elements such as the CPU core, memory blocks, I/O interfaces, and other components to optimize factors like signal routing, power distribution, and thermal considerations.

- Macro Floorplan is a more detailed level of floorplanning focusing on specific macro-level functional blocks within the chip. These macros could include complex components such as memory arrays, processors, or specialized IP blocks. Macro floorplanning involves determining the physical placement and interconnection of these blocks to meet performance, area, and power targets while adhering to design constraints and specifications.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/de14506f-09d0-47aa-af2d-d5126f0fc13f)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/dcbfb1de-8227-4b96-bdfd-78b9ecc99bfe)

- Placement : Placement involves determining the physical location of each logic gate, flip-flop, and other components on the chip's layout. It aims to minimize wire length and optimize performance metrics such as timing and power consumption.

- Global placement : Also known as coarse placement or initial placement, is the first stage of the placement process. It involves roughly positioning the cells or modules of the design on the chip's layout while considering factors like timing, power, and area constraints. Global placement aims to achieve a rough approximation of the final placement layout before refining the positions in the detailed placement stage.

- Detailed placement : Also known as fine placement, follows global placement and involves refining the positions of individual cells or modules on the chip's layout. Detailed placement focuses on optimizing factors such as wirelength, timing, and congestion while ensuring that design constraints are met. This stage often employs advanced algorithms and techniques to achieve high-quality placement results, which directly impact the performance and manufacturability of the chip.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/61e91706-1b14-493f-9d89-52c70417d8a5)
  
- Clock Tree Synthesis : This stage involves designing the clock distribution network on the chip to ensure that clock signals reach all parts of the design with minimal skew and jitter. It includes synthesizing buffers and routing clock signals to different parts of the chip.

- Clock Skew : It refers to variations in the arrival times of clock signals at different parts of a digital circuit. It can cause timing issues and impact the performance of the circuit. Minimizing clock skew is crucial for ensuring reliable operation.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/3b68c3e3-f8e7-4172-8637-1fa9b53a703e)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/b78f4fbe-7f96-4df5-a343-11e290907c6a)

- Routing : Routing is the process of determining the paths for connecting the various components on the chip layout while obeying design rules and constraints. It involves routing wires to connect the outputs of one component to the inputs of another.

- Global routing : Also known as rough routing, is the initial stage of routing where the approximate paths for interconnecting the various components of the design are determined. It involves finding high-level routes between blocks or modules while considering factors such as wirelength, congestion, and timing constraints. Global routing creates a rough layout of the routing tracks and establishes the overall connectivity of the design.

- Detailed routing : Also known as fine routing, follows global routing and involves refining the routing paths to meet design specifications and constraints. In this stage, individual wires or nets are routed within the routing tracks established during global routing.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/7d5fa184-ee18-495f-b863-a11f23a2e7d5)

- Sign-off : Sign-off refers to the final stage of the design process, where the chip design is verified against various criteria such as timing, power, and signal integrity. It involves running extensive simulations and tests to ensure that the design meets all specifications and requirements before sending it for fabrication.

- Design Rule Checking : DRC is a process used in semiconductor design to ensure that the layout of an integrated circuit adheres to the manufacturing rules and constraints specified by the foundry or design team. It involves automatically checking the layout against a set of design rules to identify violations such as minimum feature sizes, spacing requirements, overlap violations, and other geometric violations. DRC is essential for detecting potential manufacturing defects and ensuring the manufacturability and reliability of the chip.
  
- Layout vs. Schematic : LVS is a verification process used to ensure the accuracy and consistency between the layout of an integrated circuit and its corresponding schematic or netlist representation. LVS compares the geometric layout of the transistors, wires, and other components against the connectivity and electrical properties specified in the schematic. It checks for discrepancies such as missing connections, extra connections, and electrical mismatches. LVS is critical for identifying design errors and ensuring the functional correctness of the chip.
  
- Static Timing Analysis : STA is a method used to analyze and verify the timing behavior of an integrated circuit design. It evaluates the timing characteristics of the digital circuit to ensure that signals propagate correctly and meet timing requirements such as setup and hold times. STA considers factors such as gate delays, wire delays, clock skew, and signal arrival times to predict the circuit's performance under different operating conditions. STA helps identify timing violations and ensures that the design operates reliably at the desired clock frequency.

### <h1 id="header-1_2_3">1.2.3 - Introduction to OpenLANE and Strive chipsets</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/6e847155-ad89-4353-9dec-8ccd5430c768)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8b47234e-fc01-4702-a408-2ae804e8b5e7)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/427a83db-d6e9-420d-a858-aebe3b2a0d86)

- OpenLane is an open-source digital ASIC (Application-Specific Integrated Circuit) design flow framework developed by efabless and Google. It provides a complete RTL-to-GDSII design flow for designing and fabricating integrated circuits using standard cell libraries and open-source tools.It can be used to harden Macros and chips.Two mode of operation-Autonomus,Interactive.It has large number of design examples(43 designs with their best configurations).

- striVe is a family of open everything SoCs: Open PDK, Open EDA and Open RTL.

- clean GDSII means No LVS/DRC/timing violations.

### <h1 id="header-1_2_4">1.2.4 - Introduction to OpenLANE detailed ASIC design flow</h1>
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/64ac72c3-fb06-4588-9502-866078270ff5)

- Yosys : Yosys is an open-source synthesis tool that transforms RTL (Register Transfer Level) code into a gate-level netlist. It performs logic optimization and technology mapping, converting the design into a format suitable for physical implementation.

- abc : ABC is used for logic optimization and technology mapping during synthesis. It converts RTL descriptions into optimized gate-level netlists, enhancing design efficiency and effectiveness.

**Static Timing Analysis:**
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/54041f46-a07d-4cde-aec2-878ac6b417a4)

- OpenSTA : OpenSTA is a static timing analysis tool used for analyzing and verifying timing constraints. It evaluates timing paths in the design to ensure that signals meet timing requirements and identifies timing violations.
  
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/466c4a6f-36b6-4f8e-8c0f-0a76ea6cf9b6)

- Synthesis Exploration: Refers to the process of exploring various synthesis options and parameters to optimize the RTL-to-gate-level conversion. Designers can experiment with different synthesis configurations to achieve better results in terms of area, power, and timing.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/43a30ea5-97f3-434b-8efd-5612f5e00d66)

- Design Exploration: Involves exploring different design configurations and constraints to achieve desired performance metrics. Designers can iterate through multiple design options, adjusting parameters such as clock frequency, power constraints, and design goals to find the best design solution.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/1f97eb60-d1ee-42f1-b204-212fc2a6560d)

- Regression Testing: Is the practice of running automated tests on a set of design revisions or configurations to ensure that changes do not introduce regressions or unintended side effects. In OpenLANE, regression testing helps validate design changes and optimizations while maintaining design integrity and quality.

**DFT:**
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/aa7b03b9-6035-4ac6-a8b7-b7bb2602fc91)

- Fault : Fault is a tool for performing fault simulation and testing to verify the robustness and reliability of the design. It identifies potential faults and assesses the impact on circuit functionality.

- Design for Test : It encompasses techniques and methodologies in chip design to enhance testing efficiency and effectiveness. It includes methods like scan chains, built-in self-test (BIST), boundary scan (JTAG), memory BIST, and logic BIST, ensuring thorough testing and fault detection in integrated circuits. DFT aims to improve testability, reduce test costs, and expedite time-to-market.

**Physical Implementation:**
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/96308357-21c4-4cbe-acb0-404a54ad0fa9)

- OpenROAD : OpenROAD is a set of open-source tools for RTL-to-GDSII implementation. It includes tools for floorplanning, placement, and routing, enabling physical design optimization while considering factors like area, timing, and power.

**Dealing with Antenna Rules Violations:**
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/1e6648b6-7a2b-4eba-9265-c07bfff4dbaf)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8482e50a-a6f5-418a-8f40-1260acab56c9)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d25eeec4-dfd1-4b7e-9fdd-9b0a2ddd99a2)

- Antenna rule violations : It can occur during the manufacturing process of integrated circuits when certain regions of the chip become susceptible to charge accumulation or depletion. These violations can lead to reliability issues, such as gate oxide breakdown or circuit malfunction, and need to be addressed during the design phase.

- Bridging : It involves adding metal connections to neutralize the charge buildup or depletion in susceptible regions. By connecting these regions to a power or ground rail, the charge is dissipated, mitigating the risk of reliability issues.

- Inserting Antenna Diodes:Antenna diodes are specialized diodes inserted into vulnerable regions of the chip to provide a low-resistance path for charge dissipation. These diodes divert any accumulated charge to prevent reliability problems.

- Fake Antenna Diodes: It refers to a technique used to address antenna rule violations during physical design optimization. Instead of inserting actual diodes, fake diodes are virtually inserted into the design layout to satisfy the antenna rules without altering the circuit's functionality. This approach allows designers to meet manufacturing requirements without introducing unnecessary components into the design.

**LEC:**
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/81895ec9-15da-43d3-a9e5-3e87d33434e8)

- Logical Equivalence Checking : LEC is a formal verification technique used to compare two designs or design representations to ensure that they are functionally equivalent. It checks whether the behavior specified in the RTL description matches that of the gate-level netlist after synthesis
  
- TritonRoute : TritonRoute is a detailed router included in OpenLANE for performing global and detailed routing. It optimizes the routing paths while adhering to design rules and constraints, ensuring signal integrity and manufacturability.

**Physical Verification DRC&LVS :**
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/51882d20-e3b8-404e-ae36-b4c66ea33c41)

- Magic : Magic is a layout tool used for viewing, editing, and verifying physical layout designs. It allows designers to inspect the layout at different levels of abstraction and perform manual optimizations if needed.

- Netgen : Netgen is a tool for performing LVS (Layout vs. Schematic) and DRC (Design Rule Checking) verification. It compares the layout against the schematic and checks for discrepancies and violations to ensure design correctness.





## <h1 id="header-1_3">1.3 - Get familiar to open-source EDA tools</h1>

### <h1 id="header-1_3_1">1.3.1 - OpenLANE Directory structure in detail</h1>
### <h1 id="header-1_3_2">1.3.2 - Design Preparation Step</h1>
### <h1 id="header-1_3_3">1.3.3 - Review files after design prep and run synthesis</h1>
### <h1 id="header-1_3_4">1.3.4 - OpenLANE Project Git Link Description</h1>
### <h1 id="header-1_3_5">1.3.5 - Steps to characterize synthesis results</h1>

# <h1 id="header-2">Section 2 - Good floorplan vs bad floorplan and introduction to library cells (13/03/2024 - 14/03/2024)</h1>	

## <h1 id="header-2_1">2.1 - Chip Floor planning consideration</h1>

### <h1 id="header-2_1_1">2.1.1 - Utilization factor and aspect ratio</h1>
### <h1 id="header-2_1_2">2.1.2 - Utilization factor and aspect ratio</h1>
### <h1 id="header-2_1_3">2.1.3 - De-coupling capacitors</h1>
### <h1 id="header-2_1_4">2.1.4 - Power planning</h1>
### <h1 id="header-2_1_5">2.1.5 - Pin placement and logical cell placement blockage</h1>
### <h1 id="header-2_1_6">2.1.6 - Steps to run floorplan using OpenLANE</h1>
### <h1 id="header-2_1_7">2.1.7 - Review floorplan files and steps to view floorplan</h1>
### <h1 id="header-2_1_8">2.1.8 - Review floorplan layout in Magic</h1>


## <h1 id="header-2_2">2.2 - Library building and Placement</h1>

### <h1 id="header-2_2_1">2.2.1 - Netlist binding and initial place design</h1>
### <h1 id="header-2_2_2">2.2.2 - Optimize placement using estimated wire-length and capacitance</h1>
### <h1 id="header-2_2_3">2.2.3 - Final placement optimization</h2>
### <h1 id="header-2_2_4">2.2.4 - Need for libraries and characterization</h1>
### <h1 id="header-2_2_5">2.2.5 - Congestion aware placement using RePlAce</h1>

## <h1 id="header-2_3">2.3 - Cell design and characterization flows</h1>

### <h1 id="header-2_3_1">2.3.1 - Inputs for cell design flow</h1>
### <h1 id="header-2_3_2">2.3.2 - Circuit design steps</h1>
### <h1 id="header-2_3_3">2.3.3 - Layout design step</h1>
### <h1 id="header-2_3_4">2.3.4 - Typical characterization flow</h1>

## <h1 id="header-2_4">2.4 - General timing characterization parameters</h1>

### <h1 id="header-2_4_1">2.4.1 - Timing threshold definitions</h1>
### <h1 id="header-2_4_2">2.4.2 - Propagation delay and transition time</h1>



# References 
> https://futureskillsprime.in/course/digital-vlsi-soc-design-and-planning

> Repo Documentation format inspired from [Ms.Kalpana](https://github.com/kmkalpana2001/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/tree/main) , [Mr.Mohammed Fayiz Ferosh](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main?tab=readme-ov-file)
