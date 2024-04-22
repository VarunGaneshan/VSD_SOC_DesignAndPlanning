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
      <ul>
   	 <li><a href="#header-1_1">How to talk to computers</a>
 		 <ul>
   		 <li><a href="#header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</a></li>
   		 <li><a href="#header-1_1_2">Introduction to RISC-V</a></li>
   		 <li><a href="#header-1_1_3">From Software Applications to Hardware</a></li>
 		 </ul>
   	 </li>
   	 <li><a href="#header-1_2">Soc design and OpenLANE</a>
 		 <ul>
   		 <li><a href="#header-1_2_1">Introduction to all components of open-source digital asic design</a></li>
   		 <li><a href="#header-1_2_2">Simplified RTL2GDS flow</a></li>
   		 <li><a href="#header-1_2_3">Introduction to OpenLANE and Strive chipsets</a></li>
   		 <li><a href="#header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</a></li>
 		 </ul>
   	 </li>
   	 <li><a href="#header-1_3">Get familiar to open-source EDA tools</a>
 		 <ul>
   		 <li><a href="#header-1_3_1">OpenLANE Directory structure in detail</a></li>
   		 <li><a href="#header-1_3_2">Design Preparation Step</a></li>
   		 <li><a href="#header-1_3_3">Review files after design prep and run synthesis</a></li>
   		 <li><a href="#header-1_3_4">OpenLANE Project Git Link Description</a></li>
   		 <li><a href="#header-1_3_5">Steps to characterize synthesis results</a></li>
 		 </ul>
   	 </li>
      </ul>
    </li>
  </ul>
</div>

<div class="toc">
  <ul>
    <li><a href="#header-2">Section 2 - Good floorplan vs bad floorplan and introduction to library cells (13/03/2024 - 14/03/2024)</a>
      <ul>
   	 <li><a href="#header-2_1">Chip Floor planning consideration</a>
 		 <ul>
   		 <li><a href="#header-2_1_1">Utilization factor and aspect ratio</a></li>
   		 <li><a href="#header-2_1_2">Concept of pre-placed cells</a></li>
   		 <li><a href="#header-2_1_3">De-coupling capacitors</a></li>
   		 <li><a href="#header-2_1_4">Power planning</a></li>
   		 <li><a href="#header-2_1_5">Pin placement and logical cell placement blockage</a></li>
   		 <li><a href="#header-2_1_6">Steps to run floorplan using OpenLANE</a></li>
   		 <li><a href="#header-2_1_7">Review floorplan files and steps to view floorplan</a></li>
   		 <li><a href="#header-2_1_8">Review floorplan layout in Magic</a></li>
 		 </ul>
   	 </li>
   	 <li><a href="#header-2_2">Library building and Placement</a>
 		 <ul>
   		 <li><a href="#header-2_2_5">Congestion aware placement using RePlAce</a></li>
 		 </ul>
   	 </li>
   	 </li>
      </ul>
    </li>
  </ul>
</div>

<div class="toc">
  <ul>
    <li><a href="#header-3">Section 3 - Design library cell using Magic Layout and ngspice characterization (15/04/2024 - 16/03/2024)</a></li>
      <ul>
        <li><a href="#header-3_1">Labs for CMOS inverter ngspice simulations</a></li>
        <ul>
          <li><a href="#header-3_1_0">IO placer revision</a></li>
        </ul>
         <ul>
          <li><a href="#header-3_1_5">Lab steps to git clone vsdstdcelldesign</a></li>
        </ul>
      </ul>
      <ul>
        <li><a href="#header-3_2">Inception of layout ̂A CMOS fabrication process </a></li>
         <ul>
          <li><a href="#header-3_2_8">Lab introduction to Sky130 basic layers layout and LEF using inverter</a></li>
        </ul>
        <ul>
          <li><a href="#header-3_2_9">Lab steps to create std cell layout and extract spice netlist</a></li>
        </ul>
      </ul>
    <ul>
        <li><a href="#header-3_3">Sky130 Tech File Labs</a></li>
        <ul>
          <li><a href="#header-3_3_1">Lab steps to create final SPICE deck using Sky130 tech</a></li>
        </ul>
        <ul>
          <li><a href="#header-3_3_2">Lab steps to characterize inverter using sky130 model files</a></li>
        </ul>
        <ul>
          <li><a href="#header-3_3_4">Lab introduction to Sky130 pdk's and steps to download labs</a></li>
        </ul>
        <ul>
          <li><a href="#header-3_3_5">Lab introduction to Magic and steps to load Sky130 tech-rules</a></li>
        </ul>
        <ul>
          <li><a href="#header-3_3_6">Lab exercise to fix poly.9 error in Sky130 tech-file</a></li>
        </ul>
        <ul>
          <li><a href="#header-3_3_7">Lab exercise to implement poly resistor spacing to diff and tap</a></li>
        </ul>
          <ul>
          <li><a href="#header-3_3_8">Lab challenge exercise to describe DRC error as geometrical construct</a></li>
        </ul>
        <ul>
          <li><a href="#header-3_3_9">Lab challenge to find missing or incorrect rules and fix them</a></li>
        </ul>
      </ul>
   </div>
    
<div class="toc">
  <ul>
    <li><a href="#header-4">Section 4 - Pre-layout timing analysis and importance of good clock tree (17/04/2024 - 18/03/2024) </a></li>
    <ul>
        <li><a href="#header-4_1">Timing modeling using delay tables</a></li>
         <ul>
          <li><a href="#header-4_1_1">Lab steps to convert grid info to track info</a></li>
        </ul>
        <ul>
          <li><a href="#header-4_1_2">Lab steps to convert magic layout to std cell LEF</a></li>
        <ul>
          <li><a href="#header-4_1_7">Lab steps to configure synthesis settings to fix slack and include vsdinv</a></li>
        </ul>
      </ul>
      <ul>
        <li><a href="#header-4_2">Timing analysis with ideal clocks using openSTA</a></li>
        <ul>
          <li><a href="#header-4_2_3">Lab steps to configure OpenSTA for post-synth timing analysis</a></li>
        </ul>
          <ul>
          <li><a href="#header-4_2_4">Lab steps to optimize synthesis to reduce setup violations</a></li>
        </ul>
        <ul>
          <li><a href="#header-4_2_5">Lab steps to do basic timing ECO</a></li>
        </ul>
      </ul>
    <ul>
        <li><a href="#header-4_3">Clock tree synthesis TritonCTS and signal integrity</a></li>
          <ul>
          <li><a href="#header-4_3_3">Lab steps to run CTS using TritonCTS</a></li>
        </ul>
          <ul>
          <li><a href="#header-4_3_4">Lab steps to verify CTS runs</a></li>
        </ul>
      </ul>
      <ul>
        <li><a href="#header-4_4">Timing analysis with real clock using openSTA</a></li>
          <ul>
          <li><a href="#header-4_4_3">Lab steps to analyze timing with real clocks using OpenSTA</a></li>
        </ul>
          <ul>
          <li><a href="#header-4_4_4">Lab steps to execute OpenSTA with right timing libraries and CTS assignment</a></li>
        </ul>
        <ul>
          <li><a href="#header-4_4_5">Lab steps to observe impact of bigger CTS buffers on setup and hold timing</a></li>
        </ul>
      </ul>
</div>

<div class="toc">
  <ul>
    <li><a href="#header-5">Section 5 - Final step for RTL2GDS using tritinRoute and openSTA (19/04/2024 - 20/03/2024)</a></li>
    <ul>
        <li><a href="#header-5_1">Lab steps to build power distribution network</a></li>
        <li><a href="#header-5_2">Detailed routing using TritonRoute and explore the routed layout</a></li>
        <li><a href="#header-5_3">Post-Route parasitic extraction using SPEF extractor</a></li>
      </ul>
	
<div class="toc">
  <ul>
	<li><a href="#header-6">References</a></li>
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

- Foundry : A foundry is a specialized facility that manufactures integrated circuits for semiconductor design companies. It provides the equipment and expertise for high-volume production of chips, allowing companies to prototype and produce electronics without their own manufacturing facilities.

- Intellectual Property : It refers to inventions, designs, and processes, that are legally protected under patents, copyrights, or trade secrets.

- Foundry IPs:In chip design, IP can include pre-designed circuit blocks, algorithms, or software modules that are licensed or owned by companies for integration into their own designs, saving time and resources.Foundry IPs can include standard cell libraries, memory compilers, I/O libraries, analog and mixed-signal IPs, and various other building blocks required for chip design. 
  
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

- TritonRoute : TritonRoute is a detailed router included in OpenLANE for performing global and detailed routing. It optimizes the routing paths while adhering to design rules and constraints, ensuring signal integrity and manufacturability.
  
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

**Physical Verification DRC&LVS :**

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/51882d20-e3b8-404e-ae36-b4c66ea33c41)

- Magic : Magic is a layout tool used for viewing, editing, and verifying physical layout designs. It allows designers to inspect the layout at different levels of abstraction and perform manual optimizations if needed.

- Netgen : Netgen is a tool for performing LVS (Layout vs. Schematic) and DRC (Design Rule Checking) verification. It compares the layout against the schematic and checks for discrepancies and violations to ensure design correctness.

## <h1 id="header-1_3">1.3 - Get familiar to open-source EDA tools</h1>

### <h1 id="header-1_3_1">1.3.1 - OpenLANE Directory structure in detail</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/dee4d9d1-cfea-43f1-8d03-c3fc73639b69)

```bash
cd Desktop/work/tools/openlane_working_dir/
cd pdks
cd sky130A
cd libs.ref
cd ..
cd libs.tech
```

<p><b>SKY130 PDK libraries:</b></p>
There are seven standard cell libraries provided directly by the SkyWater Technology foundry available for use on SKY130 designs, which differ in intended applications and come in three separate cell heights.Libraries in the SKY130 PDK are named using the following scheme:

```bash
<Process name> _ <Library Source Abbreviation> _ <Library Type Abbreviation> [_ <Library Name>]	
```

<p><b>sky130_fd_sc_hd.lib:</b></p>
The sky130_fd_sc_hd library is designed for high density. This library enables higher routed gated density, lower dynamic power consumption, and comparable timing and leakage power. As a trade-off it has lower drive strength.

- Sky130 : It is the name of the process technology.
- fd     : It is abbreviation for who created and is responsible for the library, here the SkyWater Foundry.
- sc 	 : It is abbreviation for the type of content found in the library, here the Digital Standard Cells.
- hd	 : It represents high density.
  
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/081a3722-a0ba-4b9d-b9fa-884a82fc26e4)

```bash
cd sky130_fd_sc_hd
cd lib
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/e5bca05c-8c51-40af-92d5-809cda64fe11)

```bash
cd ..
cd lef
cd ..
cd techlef
```

### <h1 id="header-1_3_2">1.3.2 - Design Preparation Step</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/39685a82-6ae7-43f2-a1b5-ac1fe8979c4c)

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
docker
pwd
ls -ltr
./flow.tcl -interactive
package require openlane 0.9
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/300cd604-c683-48a4-b902-b8c447f730b2)

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
cd designs
ls -ltr
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/cfce6b01-4765-48e3-b863-4e5ee5e4c433)

```bash
cd picorv32a/
ls-ltr
cd src
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8c9b894a-624b-4b83-ad1d-e17c88e29a40)

```bash
less config.tcl #exit by pressing q
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/dbba392e-b174-4ae4-a04a-60e376876630)

```bash
less sky130A_sky130_fd_sc_hd_config.tcl
```

### <h1 id="header-1_3_3">1.3.3 - Review files after design prep and run synthesis</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/2dcb0ec4-a6a0-413e-a2ab-79a675313646)

```bash
ls -ltr 
cd runs
cd 14-04-19-44/
cd tmp
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/f68636f9-3766-46e7-9b93-1ee23ba12b23)

```bash
less merged.lef
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/791aa500-a11c-4cb4-a91e-9b09298885cb)

```bash
cd results
cd synthesis
cd reports
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/9063d675-d442-4c9f-856b-26666588ad29)

```bash
ls
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/b41d0788-760e-43f0-b60e-5a3207bf6937)

```bash
less config.tcl #go to end by pressing "Ctrl + End" or "Fn + Right Arrow" and exit by pressing q
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/55fc23be-d8ad-4f0a-b7fc-f7533f5b610d)


```bash
less cmds.log
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/2879187f-b169-4a91-bff3-74c8d98fc2ac)

```bash
prep -design picorv32a
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/84873a04-1ca2-44de-b89c-370f490171b9)

```bash
run_synthesis
```

### <h1 id="header-1_3_4">1.3.4 - OpenLANE Project Git Link Description</h1>

> [Openlane Github](https://github.com/efabless/OpenLane/tree/de223b4c5339aaf932845cbf301638eba75a1971)

**Autonomous mode:**
```
./flow.tcl -design designname
```

**Interactive Mode:**
You may run the flow interactively by using the `-interactive` option:

```
./flow.tcl -interactive
```

A tcl shell will be opened where the openlane package is automatically sourced:
```
% package require openlane
```

Then, you should be able to run the following main commands:

0. Any tcl command.
1. `prep -design <design> -tag <tag> -config <config> -init_design_config -overwrite` similar to the command line arguments, design is required and the rest is optional
2. `run_synthesis`
3. `run_floorplan`
4. `run_placement`
5. `run_cts`
6. `run_routing`
7. `write_powered_verilog` followed by `set_netlist $::env(routing_logs)/$::env(DESIGN_NAME).powered.v`
8. `run_magic`
9. `run_magic_spice_export`
10. `run_magic_drc`
11. `run_lvs`
12. `run_antenna_check`


The above commands can also be written in a file and passed to `flow.tcl`:

```
./flow.tcl -interactive -file <file>
```


### <h1 id="header-1_3_5">1.3.5 - Steps to characterize synthesis results</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d4de2d4b-9258-48a4-ae99-7b7c498d1d14)

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}  = \frac{1613}{14876} = 0.1084
```
```math
Percentage\ of\ DFF's = Flop\ Ratio * 100 = 0.1084* 100 = 10.84\ \%
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a12c042c-99a2-4f17-8940-a21d773938b1)

```bash
cd results
cd synthesis
cd ..
cd ..
cd reports
cd synthesis
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/17179411-a001-4512-bdad-eb2b64c462bf)

```bash
less picorv32a.synthesis.v
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/bde08f35-16fe-4811-8f0b-ece09791d72e)

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/171f37cf-01e5-4710-9cdf-383959b4cb87)

```bash
less 1-yosys_4.stat.rpt
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ddab9c7f-1a90-48a7-b6e0-4c95f27cde6d)

```bash
less 2-opensta.rpt
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/0780bfb2-1c32-4ffb-b20b-32370e1f8b2d)

```bash
less 2-opensta.timing.rpt
```

# <h1 id="header-2">Section 2 - Good floorplan vs bad floorplan and introduction to library cells (13/03/2024 - 14/03/2024)</h1>    

## <h1 id="header-2_1">2.1 - Chip Floor planning consideration</h1>

### <h1 id="header-2_1_1">2.1.1 - Utilization factor and aspect ratio</h1>

Defining the width and height of oore and die is the first step PD flow

**Finding values of H&W:**

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ef4cde48-124d-4927-8f94-ff987e3b90cc)

Basic Netlist (launch flop and capture flop with combinational logic)

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/3035f14d-959d-4c8f-ab7c-921275633570)

Providing proper dimensions to the logic gates

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8d68e90b-54e5-4a8c-8db5-b3d354d123fc)

Dimensions of the wire can be neglected for the calculation

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/046d7749-83df-443e-a1de-bf50be96e7f1)

Clubing them to a single plate
```math
Length = 2 units , Width = 2 units , Area = 4 sq.units
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/112e2924-662e-4251-a40f-b70b7cf3b49c)

Place the cells inside core
```math
Utilization\ Factor = \frac{Area\ occupied\ by\ netlist}{Total\ area\ of\ core} = \frac{4}{4} = 1 
```
In case of 100% Utilization,Adding extra cells is not allowed,ideally 50/60% is prefered .
```math
Aspect\ Ratio = \frac{Height}{Width} = \frac{4}{4} = 1 
```
In case of Aspect Ratio = 1,then its a square shaped core,otherwise rectangle.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5268dbb5-9376-414c-9a08-8a3273402c68)

In a diff dimension,
```math
Utilization\ Factor = \frac{4}{8} = 0.5 
```
UF < 1,Some more area is present which can be utilized/Optimisation required.

```math
Aspect\ Ratio = \frac{2}{4} = 0.5 
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/15f63572-2841-4b1c-a370-effd713d32b5)

### <h1 id="header-2_1_2">2.1.2 - Utilization factor and aspect ratio</h1>
### <h1 id="header-2_1_3">2.1.3 - De-coupling capacitors</h1>
### <h1 id="header-2_1_4">2.1.4 - Power planning</h1>
### <h1 id="header-2_1_5">2.1.5 - Pin placement and logical cell placement blockage</h1>

### <h1 id="header-2_1_6">2.1.6 - Steps to run floorplan using OpenLANE</h1>

```bash
cd configuration
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/cb59a395-6545-4535-b3fa-aa58636314bd)

Before running floorplan command enable certain switches

```bash
less README.md
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/bbb75265-114f-41cf-a7a8-f1780e4dbac2)

```bash
less floorplan.tcl
```
(FP_IO MODE) 1 = 0 means pin positioning is random but it is on equal distance.

priority : system default (floorplanning.tcl) < config.tcl < PDK varient.tcl (sky130A_sky130_fd_sc_hd_congig.tcl)

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/50088d2b-4736-4b41-87f1-78fb90e2578a)

```bash
run_floorplan
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ab77b8f2-e5c1-48b8-b5dd-38c0a483fff9)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/57fe513b-845b-46f4-a6fa-95e3f7a77e69)

### <h1 id="header-2_1_7">2.1.7 - Review floorplan files and steps to view floorplan</h1>

```bash
cd runs
ls -ltr
cd logs/floorplan
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/366fd370-27e4-47bb-aa12-76abdfc8369e)

```bash
less picorv32a.floorplan.def
```
```math
Given\ 1000\ Unit\ Distance = 1\ Micron
```
```math
Die\ width\ in\ unit\ distance = 660685 - 0 = 660685
```
```math
Die\ height\ in\ unit\ distance = 671405 - 0 = 671405
```
```math
Distance\ in\ microns = \frac{Value\ in\ Unit\ Distance}{1000}
```
```math
Die\ width\ in\ microns = \frac{660685}{1000} = 660.685\ Microns
```
```math
Die\ height\ in\ microns = \frac{671405}{1000} = 671.405\ Microns
```
```math
Area\ of\ die\ in\ microns = 660.685 * 671.405 = 443587.212425\ Sq\ Microns
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/0d5ca9a0-ae1c-4dd0-9414-bcb96e25ac38)

### <h1 id="header-2_1_8">2.1.8 - Review floorplan layout in Magic</h1>

```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/7b5350f4-440e-450c-b920-9173291621f2)


press S+V - fit layout
To Zoom, Left click & Right click & Press Z

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/7e3132ee-2095-497c-a24f-2cf55c2feb70)

Place cursor on object and Press S,open tkcon app and type what

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/c65c03b9-0e02-4e16-aa57-35cccf794c71)

**Decap Cells and Tap Cells**

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/6b704c81-3df6-49e1-8561-38a2c2b4da5a)

**Standard Cells** at the bottom left

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4e108f17-7ad1-41e1-900b-0290d29760d3)


## <h1 id="header-2_2">2.2 - Library building and Placement</h1>

### <h1 id="header-2_2_1">2.2.1 - Netlist binding and initial place design</h1>
### <h1 id="header-2_2_2">2.2.2 - Optimize placement using estimated wire-length and capacitance</h1>
### <h1 id="header-2_2_3">2.2.3 - Final placement optimization</h2>
### <h1 id="header-2_2_4">2.2.4 - Need for libraries and characterization</h1>
### <h1 id="header-2_2_5">2.2.5 - Congestion aware placement using RePlAce</h1>

```bash
run_placement
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/46f7c6e2-70ba-46b9-900d-9d4c599cbbdf)

```bash
cd ../placement
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/0b3338e3-8199-4ca4-a1d2-d2910359ef20)

standard cells are correctly placed in standard cell rows

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/e60edef2-15f6-432f-af03-3e8538d71bf6)

## <h1 id="header-2_3">2.3 - Cell design and characterization flows</h1>

### <h1 id="header-2_3_1">2.3.1 - Inputs for cell design flow</h1>
### <h1 id="header-2_3_2">2.3.2 - Circuit design steps</h1>
### <h1 id="header-2_3_3">2.3.3 - Layout design step</h1>
### <h1 id="header-2_3_4">2.3.4 - Typical characterization flow</h1>

## <h1 id="header-2_4">2.4 - General timing characterization parameters</h1>

### <h1 id="header-2_4_1">2.4.1 - Timing threshold definitions</h1>
### <h1 id="header-2_4_2">2.4.2 - Propagation delay and transition time</h1>


# <h1 id="header-3">Section 3 - Design library cell using Magic Layout and ngspice characterization (15/03/2024 - 16/03/2024)</h1>

## <h1 id="header-3_1">3.1 - Labs for CMOS inverter ngspice simulations</h1>

### <h1 id="header-3_1_1">3.1.1 - IO placer revision</h1>

Rerun till floorplan

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d63e3844-81d4-471a-9427-50dfdd245f69)

```bash
less floorplan.txt
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/1e7f9527-ca7d-4e23-bb33-af1b7e1c7494)

```bash
% set ::env(FP_IO_MODE) 2
% run_floorplan
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/42dd3e91-44d9-406a-8656-7903009c2aa0)

Opening the newly run directory

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/b30bf80e-9b36-4a7b-a2cb-3f744da93d03)


```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
Pins are not equidistant here

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/1a2dfa49-dfd9-45ef-9a43-3a1601631051)

### <h1 id="header-3_1_2">3.1.2 - SPICE deck creation for CMOS inverter</h1>
### <h1 id="header-3_1_3">3.1.3 - SPICE simulation lab for CMOS inverter</h1>
### <h1 id="header-3_1_4"> 3.1.4 - Switching Threshold Vm</h1>
### <h1 id="header-3_1_5">3.1.5 - Static and dynamic simulation of CMOS inverter</h1>
### <h1 id="header-3_1_6">3.1.6 - Lab steps to git clone vsdstdcelldesign</h1>

```bash
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
cd vsdstdcelldesign
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d341373d-aabc-4607-8392-95b3ece7985c)

Copy the tech file
```bash
cd Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic
cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/660c9cb6-e5df-49a1-a15f-360c6ad798b5)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/7a34d492-7b5e-4058-bc12-c8ca2acf39ef)

```bash
magic -T sky130A.tech sky130_inv.mag &
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4591d37d-a3ef-461b-8bb0-c0acd111c8ac)

Custom CMOS inverter
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/22c2fae7-8d3d-4ae6-b940-6eda022f13b6)


## <h1 id="header-3_2">3.2 - Inception of layout ̂A CMOS faabrication process</h1>
### <h1 id="header-3_2_1">3.2.1 - Create Active regions</h1>
### <h1 id="header-3_2_2">3.2.2 - Formation of N-well and P-well</h1>
### <h1 id="header-3_2_3">3.2.3 - Formation of gate terminal</h1>
### <h1 id="header-3_2_4">3.2.4 - Lightly doped drain (LDD) formation</h1>
### <h1 id="header-3_2_5">3.2.5 - Source Ã  drain formation</h1>
### <h1 id="header-3_2_6">3.2.6 - Local interconnect formation</h1>
### <h1 id="header-3_2_7">3.2.7 - Higher level metal formation</h1>
### <h1 id="header-3_2_8">3.2.8 - Lab introduction to Sky130 basic layers layout and LEF using inverter</h1>

Polycross N-diffusion -PMOS

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/41c11501-da58-4aec-b25a-112e3a13f982)

Polycross P-diffusion -NMOS

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/44861c40-32b6-4001-98f8-f9ca5c1a36f9)

Y output port connected to PMOS & NMOS

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8a7a1e75-44bd-4531-9167-76b9e05af277)

PMOS source connected to VDD

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/072b55ed-75a3-4b26-9696-c67f735cbaeb)

NMOS source connected to VDD

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/6a720498-dd51-4b3d-b384-fcaf1a84e55e)

### <h1 id="header-3_2_9">3.2.9 - Lab steps to create std cell layout and extract spice netlist</h1>

```bash
extract all
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ea59d216-1491-432c-a551-10944ca7ef47)

```bash
ext2spice cthresh 0 rthresh 0
ext2spice
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/503cbbd9-e9a5-4a19-be71-5720a3a1e194)

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/f0d9b4c0-1df5-4a8d-afd5-e5fb4299b9b3)


## <h1 id="header-3_3">3.3 - Sky130 Tech File Labs</h1>
### <h1 id="header-3_3_1">3.3.1 - Lab steps to create final SPICE deck using Sky130 tech</h1>

```bash
gvim sky130_inv.spice
```
M1000 - Pmos : Drain-Y , Gate-A , Source-VPWR
M1001 - Nmos : Drain-Y , Gate-A , Source-VGND

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/02566cd4-57ac-4c93-82de-780d656789d1)

Change scale value,include pmos nmos libraries,add missing connections-VDD,VSS,define input pulse,specify type of analysis 
```bash
.option scale=0.01u

.include ./libs/pshort.lib
.include ./libs/nshort.lib

//.subckt sky130_inv A Y VPWR VGND
M1001 Y A VGND VGND nshort_model.0 w=35 l=23 
+ ad=1.44n pd=0.152m as=1.37n ps=0.148m
M1000 Y A VPWR VPWR pshort_model.0 w=37 l=23
+ ad=1.44n pd=0.152m as=1.52n ps=0.156m
VDD VPWR 0 3.3V
VSS VGND 0 0V

Va A VGND PULSE(0V 3.3V 0 0.1ns 0.1ns 2ns 4ns)
C0 A Y 0.05fF
C1 Y VPWR 0.11fF
C2 A VPWR 0.07fF
C3 Y 0 0.24fF
C4 VPWR 0 0.59fF
//.ends
.tran 1n 20n
.control
run
.endc
.end

```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5ebc1d73-9019-48e3-893f-5a27eee49943)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/1c716ed9-7578-4f7b-aa1a-767bdfe0ae28)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/1eea1db1-c8d2-47cb-886e-48ba61ae3fdf)

### <h1 id="header-3_3_2">3.3.2 - Lab steps to characterize inverter using sky130 model files</h1>

```bash
sudo apt-get install ngspice
ngsspice sky130_inv.spic
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/c76fe38a-885c-4fcd-924b-28f1727e2916)
```bash
change in gvim - C3 Y 0 2fF
plot y vs time a
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/690c7fb2-f880-4c85-bad9-ab8adb526da2)

Right click to zoom 
Rise time transition 20%-0.66 to 80%-2.64 - time value = 60ps

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8e8f1d85-c67a-4512-a54a-86f5eae213b2)

Fall time transition 80%-2.64 to 20%-0.66 - time value = 40ps
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a3305826-e0ea-4955-aa27-59016ec56eab)

Cell rise delay 50%-1.65 - time value = 50ps

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ef031b08-7508-492d-b7ff-26ec3539be56)

Cell fall delay 50%-1.65 - time value = 30ps 

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4a68051c-a858-4894-8852-3e6a66115ee5)

### <h1 id="header-3_3_3">3.3.3 - Lab introduction to Magic tool options and DRC rules</h1>
### <h1 id="header-3_3_4">3.3.4 - Lab introduction to Sky130 pdk's and steps to download labs</h1>
```bash
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
tar xfz drc_tests.tgz
cd drc_tests
ls -al
gvim .magicrcmagic -d 
magic -d XR &
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/b85ffd10-7a52-4100-ba58-e2053884d1a8)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/6fe27f61-b5e2-4b6c-bcdb-add9ecebf17f)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/875c09fd-2aa5-4699-a82a-c761d7b76613)

### <h1 id="header-3_3_5">3.3.5 - Lab introduction to Magic and steps to load Sky130 tech-rules</h1>

File -> Open -> met3.mag
Sky130 Periphery rules: [Link](https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html)

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/b1816e0a-1eb3-4fdc-8572-2eb825378e6a)

### <h1 id="header-3_3_6">3.3.6 - Lab exercise to fix poly.9 error in Sky130 tech-file</h1>
poly.mag

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/b7992cc4-012a-49a1-b973-0e62cb724a4e)

```bash
gvim sky130A.tech
```
change to allpolynonres rule

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/13f219bf-675e-446c-978b-5a8b6954fd72)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/edda916c-5a05-473b-9d27-261867266e7f)

### <h1 id="header-3_3_7">3.3.7 - Lab exercise to implement poly resistor spacing to diff and tap</h1>

```bash
tech load sky130A.tech
drc check
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ec67eb9d-0c5c-4500-8b71-a7e20aa336b5)

### <h1 id="header-3_3_8">3.3.8 - Lab challenge exercise to describe DRC error as geometrical construct</h1>

nwell.mag
```bash
% cif ostyle drc
% cif see dnwell_shrink
% feed clear
% cif see nwell_missing
% feed clear
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/74d08d5c-4a9e-479a-bed9-ae55e6a4a3cf)


### <h1 id="header-3_3_9">3.3.9 - Lab challenge to find missing or incorrect rules and fix them</h1>
Not a simple edge rule 

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/9e24c712-5ae5-494b-bf6b-1764d80b32ff)

```bash
 templayer nwell_tapped
 bloat-all nsc nwell

 templayer nwell_untapped nwell
 and-not nwell_tapped

 variants (full)
  cifmaxwidth nwell_untapped 0 bend_illegal \
  "Nwell missing tap (nwell.4)"
 variants *
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a58b9eca-ff90-4116-8427-40a096da320b)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/563ad423-e2c6-4505-a2f8-1de880add63e)

```bash
% tech load sky130A.tech
% drc style drc(full)
% drc check
% drc why
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4f0566e3-ead5-44dd-96c6-16b54c9a3c4b)


# <h1 id="header-4">Section 4 - Pre-layout timing analysis and importance of good clock tree (17/03/2024 - 18/03/2024)</h1>
## <h1 id="header-4_1">4.1 - Timing modeling using delay tables</h1>

### <h1 id="header-4_1_1">4.1.1 - Lab steps to convert grid info to track info</h1>

```bash
Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/9427e9d2-39f8-42e4-a15a-df4347391442)

```bash
less tracks.info
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/f02ca141-a354-4730-8973-575907e37734)

```bash
help grid
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/ff22addf-799b-4337-836b-77af6eae666f)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/652a530b-6be9-40ea-93d8-5edf4b9d57bd)

```bash
grid 0.46um 0.34um 0.23um 0.17um
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/37db7043-3822-467a-8b26-00ec4684f1be)

Ports lie on the intersection of the vertical and horizontal tracks.Width of the standard cell should be odd multiples of the horizontal track pitch.Height of the standard cell should be even multiples of the vertical track pitch.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/75e87b2a-2372-432c-b474-8a0464570636)



### <h1 id="header-4_1_2">4.1.2 - Lab steps to convert magic layout to std cell LEF</h1>

Defining ports

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/7faa7519-2579-46a6-86b0-fd7926f1cdb2)

```bash
save sky130_varun.mag #custom name
lef write
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/432bd01b-c2a4-4cfc-8b9a-6742d5e5a375)

```bash
less sky130_varun.lef
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/3416df13-b680-42dd-8478-8825e752b451)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5fa9b66c-71e7-4259-9a3d-c28977c8353e)

Copy necessary files to 'picorv32a' design 'src' directory
```bash
cp sky130_varun.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/91400b7f-96de-4d77-8cb7-f01d24ffe8b1)

### <h1 id="header-4_1_3">4.1.3 - Introduction to timing libs and steps to include new cell in synthesis</h1>
### <h1 id="header-4_1_4">4.1.4 - Introduction to delay tables</h1>
### <h1 id="header-4_1_5">4.1.5 - Delay table usage Part 1</h1>
### <h1 id="header-4_1_6">4.1.6 - Delay table usage Part 2</h1>
### <h1 id="header-4_1_7">4.1.7 - Lab steps to configure synthesis settings to fix slack and include vsdinv</h1>
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8f502c5c-5c4f-411d-845d-aaa74cb72384)

Edit config.tcl to include the added lef and change library to ones we added in src directory
```bash
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

```bash
package require openlane 0.9
prep -design picorv32a
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
run_synthesis
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5b5df876-e663-4b28-b24a-ab811dcfa957)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/948490cd-cbb5-4b28-9c91-5abfdcc3996c)

Note down values of newly introduced violations with the introduction of custom inverter cell

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/216d964c-9d53-4b14-a9bf-a260ecfd2dd0)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8a9119db-ffbb-4448-a77f-9a52a24861f3)

Stratergy to reduce the violations 

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/c17bedc3-7372-4b2c-abb9-663d2f4c8e31)
```bash
prep -design picorv32a -tag 22-04_08-29 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
echo $::env(SYNTH_STRATEGY) # Command to display current value of variable SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3" # Command to set new value for SYNTH_STRATEGY
echo $::env(SYNTH_BUFFERING)# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_SIZING) # Command to display current value of variable SYNTH_SIZING
set ::env(SYNTH_SIZING) 1 # Command to set new value for SYNTH_SIZING
echo $::env(SYNTH_DRIVING_CELL) # Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
run_synthesis
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/eb3a39b3-2e0d-4e3c-b1bf-0f62fa2d6bbd)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4c856a14-8108-4bae-b224-3504d6a6c732)

Area has increased,Worst negative slack has become 0
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a3dca152-827d-485b-853d-0cbc7d637cd6)

```bash
run_floorplan
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/759cfb53-3207-4a4b-93c4-aad245ea677b)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4d804445-e7e8-49ec-a496-3c696da8abcd)

Since we are facing unexpected un-explainable error while using run_floorplan command,run the below instead
```bash
init_floorplan
place_io
tap_decap_or
run_placement
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/adc1a288-125a-4db6-877a-588ad5096eac)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8e51965a-257f-4cc3-9e37-3cb5aa24ee64)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a915d260-fca4-440d-a6f7-4b594ff78d9e)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/e5931a02-d713-4a3b-8c65-683ef108f653)

```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-04_08-29/results/placement/
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/f1401aa7-17f1-4850-ab12-d2a29272c3f7)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/f8bdf49b-86d7-42d2-8614-437aa8cd95bd)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/6830afae-cef6-4cb0-9940-df21d9dc65b0)


## <h1 id="header-4_2">4.2 - Timing analysis with ideal clocks using openSTA</h1>
### <h1 id="header-4_2_1">4.2.1 - Setup timing analysis and introduction to flip-flop setup time</h1>
### <h1 id="header-4_2_2">4.2.2 - Introduction to clock jitter and uncertainty</h1>
### <h1 id="header-4_2_3">4.2.3 - Lab steps to configure OpenSTA for post-synth timing analysis</h1>

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Created pre_sta.conf for STA analysis 
```bash
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
set ::env(SYNTH_SIZING) 1
run_synthesis
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/9fe61f72-8115-4d97-a08e-62cca38365f8)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/756c70c7-e11f-4246-965a-b4be6f357ff0)

```bash
gvim pre_sta.conf
set_cmd_units -time ns -capacitance pF -current mA -voltage V -resistance kOhm -distance um

read_liberty -max /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib

read_liberty -min /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib

read_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-04_09-28/results/synthesis/picorv32a.synthesis.v

link_design picorv32a

read_sdc /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/my_base.sdc

report_checks -path_delay min_max -fields {slew trans net cap input_pin}
report_tns
report_wns
```
Created pre_sta.conf for STA analysis in openlane directory 
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/9f313a4f-7143-45ad-a107-783edececee1)

```bash
set ::env(CLOCK_PORT) clk
set ::env(CLOCK_PERIOD) 24.73
#set ::env(SYNTH_DRIVING_CELL) sky130_vsdinv
set ::env(SYNTH_DRIVING_CELL) sky130_fd_sc_hd__inv_8
set ::env(SYNTH_DRIVING_CELL_PIN) Y
set ::env(SYNTH_CAP_LOAD) 17.653
set ::env(IO_PCT) 0.2
set ::env(SYNTH_MAX_FANOUT) 6

create_clock [get_ports $::env(CLOCK_PORT)]  -name $::env(CLOCK_PORT)  -period $::env(CLOCK_PERIOD)
set input_delay_value [expr $::env(CLOCK_PERIOD) * $::env(IO_PCT)]
set output_delay_value [expr $::env(CLOCK_PERIOD) * $::env(IO_PCT)]
puts "\[INFO\]: Setting output delay to: $output_delay_value"
puts "\[INFO\]: Setting input delay to: $input_delay_value"

set_max_fanout $::env(SYNTH_MAX_FANOUT) [current_design]

set clk_indx [lsearch [all_inputs] [get_port $::env(CLOCK_PORT)]]
#set rst_indx [lsearch [all_inputs] [get_port resetn]]
set all_inputs_wo_clk [lreplace [all_inputs] $clk_indx $clk_indx]
#set all_inputs_wo_clk_rst [lreplace $all_inputs_wo_clk $rst_indx $rst_indx]
set all_inputs_wo_clk_rst $all_inputs_wo_clk

# correct resetn
set_input_delay $input_delay_value  -clock [get_clocks $::env(CLOCK_PORT)] $all_inputs_wo_clk_rst
#set_input_delay 0.0 -clock [get_clocks $::env(CLOCK_PORT)] {resetn}
set_output_delay $output_delay_value  -clock [get_clocks $::env(CLOCK_PORT)] [all_outputs]

# TODO set this as parameter
set_driving_cell -lib_cell $::env(SYNTH_DRIVING_CELL) -pin $::env(SYNTH_DRIVING_CELL_PIN) [all_inputs]
set cap_load [expr $::env(SYNTH_CAP_LOAD) / 1000.0]
puts "\[INFO\]: Setting load to: $cap_load"
set_load  $cap_load [all_outputs]

```

Created my_base.sdc for STA analysis in openlane/designs/picorv32a/src directory based on the file openlane/scripts/base.sdc
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/aa083ed9-caa7-423f-9a35-22e8a419400d)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/f9646992-24be-4e9e-887b-c6ce09fbfb69)

```bash
sta pre_sta.conf
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/2b7dda9d-fbba-4849-b900-f2e7e353dba9)

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/181efd70-6975-404a-b3da-e4847e3db807)

### <h1 id="header-4_2_4">4.2.4 - Lab steps to optimize synthesis to reduce setup violations</h1>

Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

```bash
prep -design picorv32a -tag 22-04_08-29 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
set ::env(SYNTH_SIZING) 1
set ::env(SYNTH_MAX_FANOUT) 4
echo $::env(SYNTH_DRIVING_CELL)
run_synthesis
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/c64646cf-eafc-4007-b230-731569748ea8)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/b3a4a632-635d-48fd-8d6b-acdbbb02e636)

Make changes in pre_sta.conf 

```bash
sta pre_sta.conf
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/9966ad10-d4a9-4851-9c61-ad9e45b7f860)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/dc460a62-1ab1-4cc4-ac04-a67b7795d88d)

OR gate of drive strength 2 is driving 4 fanouts
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/0580d31f-336c-4529-b0f2-76781687cb15)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```bash
report_net -connections _11672_
help replace_cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4
report_checks -fields {net cap slew input_pins} -digits 4
```
We observe slack is reduced

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/83093846-a77e-4044-bcae-436d93e8b84a)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/e589b902-69a8-4b3a-a921-6c69b42fefb7)

Another OR gate of drive strength 2 is driving 4 fanouts
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/72d5a803-2c07-4e49-9f2f-8ff7c1bf48bd)

```bash
report_net -connections _11675_
replace_cell _14514_ sky130_fd_sc_hd__or3_4
report_checks -fields {net cap slew input_pins} -digits 4
```
We observe slack is reduced again 
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4517abf5-f99a-4d25-a1cd-c18a4c8b60c3)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8067e205-0f89-49ce-9bc7-eaf1a4a4bc99)

### <h1 id="header-4_2_5">4.2.5 - Lab steps to do basic timing ECO</h1>

OR gate of drive strength 2 driving OA gate has more delay
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a92f9dc0-ec20-4134-853c-c45d4a621269)

```bash
report_net -connections _11643_
replace_cell _14481_ sky130_fd_sc_hd__or4_4
report_checks -fields {net cap slew input_pins} -digits 4
```
We observe slack is reduced again 
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/06263831-3cdc-4b8b-8f41-df67599d4dcb)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/e7c6af99-a357-4980-ae4e-e719bda16700)

Another OR gate of drive strength 2 driving OA gate has more delay
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/0e7e2cbe-a9bf-465b-aaab-ad999ddf66d1)

```bash
report_net -connections _11668_
replace_cell _14506_ sky130_fd_sc_hd__or4_4
report_checks -fields {net cap slew input_pins} -digits 4
```
We observe slack is reduced again 
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4f3250fb-ab5d-4760-9210-20e37a58af23)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/095b690d-435d-42d5-94bb-304aef242326)


Verify instance _14506_ is replaced with sky130_fd_sc_hd__or4_4
```bash
report_checks -from _29043_ -to _30440_ -through _14506_
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/78eea0d7-4e50-4007-8263-85c17b3db379)

Around 1.2827 ns of violation reduced.

## <h1 id="header-4_3">4.3 - Clock tree synthesis TritonCTS and signal integrity</h1>
### <h1 id="header-4_3_1">4.3.1 - Clock tree routing and buffering using H-Tree algorithm</h1>
### <h1 id="header-4_3_2">4.3.2 - Crosstalk and clock net shielding</h1>

### <h1 id="header-4_3_3">4.3.3 - Lab steps to run CTS using Triton</h1>
Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/ 22-04_08-29/results/synthesis/
ls
cp picorv32a.synthesis.v picorv32a.synthesis_old.v
ls
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/df64c4e1-694c-43e4-8641-4e75db996ef4)

```bash
help write_verilog
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-04_08-29/results/synthesis/picorv32a.synthesis.v
exit
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d7b6b837-ea7f-4e36-815e-28d9632eb532)

Verified that the netlist is overwritten by checking that instance _14506_ is replaced with sky130_fd_sc_hd__or4_4
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/05df8dd8-a4f6-4870-8b9a-72ff498055ee)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5a348a52-dc0a-4f86-9513-e6c137ea552b)

Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

```bash
prep -design picorv32a -tag 22-04_08-29 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
set ::env(SYNTH_STRATEGY) "DELAY 3"
set ::env(SYNTH_SIZING) 1
run_synthesis
init_floorplan
place_io
tap_decap_or
run_placement
run_cts
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d5ec414e-b2cb-4480-930f-5bc553238af4)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/59841774-e0e3-4124-8e8d-fdb722579306)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/32adde6e-14ff-4a9e-9269-0847f74e90fd)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/fafecfe0-0af8-4bef-a684-563ac4b2262b)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/c53ccb89-1e3f-424e-baa1-433530859f99)

### <h1 id="header-4_3_4">4.3.4 - Lab steps to verify CTS runs</h1>

```bash
echo $::env(LIB_SYNTH_COMPLETE)
echo $::env(LIB_TYPICAL)
echo $::env(CURRENT_DEF)
echo $::env(SYNTH_MAX_TRAN)
echo $::env(CTS_MAX_CAP)
echo $::env(CTS_CLK_BUFFER_LIST)
echo $::env(CTS_ROOT_BUFFER)
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/03d70742-c902-46ab-a2bc-0cda353c7cb1)

## <h1 id="header-4_4">4.4 - Timing analysis with real clock using openSTA</h1>
### <h1 id="header-4_4_1">4.4.1 - Setup timing analysis using real clocks</h1>
### <h1 id="header-4_4_2">4.4.2 - Hold timing analysis using real clocks</h1>
### <h1 id="header-4_4_3">4.4.3 - Lab steps to analyze timing with real clocks using OpenSTA</h1>
```bash
openroad

read_lef /openLANE_flow/designs/picorv32a/runs/22-04_08-29/tmp/merged.lef

read_def /openLANE_flow/designs/picorv32a/runs/22-04_08-29/results/cts/picorv32a.cts.lef

write_db pico_cts.db

read_db pico_cts.db

read_verilog /openLANE_flow/designs/picorv32a/runs/22-04_08-29/results/synthesis/picorv32a.synthesis_cts.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock [all_clocks]

help report_checks

report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

exit
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/affe3111-ce0d-47fb-a693-d85ded29b559)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/812d2015-a71a-46da-8310-94dc58d5d6ff)

This analysis is incorrect

### <h1 id="header-4_4_4">4.4.4 - Lab steps to execute OpenSTA with right timing libraries and CTS assignment</h1>
```bash
echo $::env(CTS_CLK_BUFFER_LIST)

set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

echo $::env(CTS_CLK_BUFFER_LIST)

echo $::env(CURRENT_DEF)

set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/22-04_08-29/results/placement/picorv32a.placement.def

run_cts

echo $::env(CTS_CLK_BUFFER_LIST)

```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5b9c3dae-231d-4b7d-93a7-4983180e0324)

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/9211517c-f62e-4088-9555-c29570348c41)

### <h1 id="header-4_4_5">4.4.5 - Lab steps to observe impact of bigger CTS buffers on setup and hold timing</h1>

```bash
openroad

read_lef /openLANE_flow/designs/picorv32a/runs/22-04_08-29/tmp/merged.lef

read_def /openLANE_flow/designs/picorv32a/runs/22-04_08-29/results/cts/picorv32a.cts.def

write_db pico_cts1.db

read_db pico_cts.db

read_verilog /openLANE_flow/designs/picorv32a/runs/22-04_08-29/results/synthesis/picorv32a.synthesis_cts.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock [all_clocks]

report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

report_clock_skew -hold

report_clock_skew -setup

exit

echo $::env(CTS_CLK_BUFFER_LIST)

set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

echo $::env(CTS_CLK_BUFFER_LIST)
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/2e1b04bf-9b79-4faa-8dd0-63b36c90d7d5)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/e9213640-f67f-43bf-98f7-e0a729ab83d4)

# <h1 id="header-5">Section 5 -Final step for RTL2GDS using tritinRoute and openSTA (19/03/2024 - 20/03/2024)</h1>
## <h1 id="header-5_1">5.1 - Routing and design rule check (DRC)</h1>
### <h1 id="header-5_1_1">5.1.1 - Introduction to Maze Routing Ã  LeeÃ s algorithm</h1>
### <h1 id="header-5_1_2">5.1.2 - LeeÃ s Algorithm conclusion</h1>
### <h1 id="header-5_1_3">5.1.3 - Design Rule Check</h1>


## <h1 id="header-5_2">5.2 - Power Distribution Network and routing</h1>
### <h1 id="header-5_2_1">5.2.1 - Lab steps to build power distribution network</h1>

```bash
gen_pdn
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/48cfb62b-af40-48a1-a39b-69f189117fe9)

Load PDN def
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-04_08-29/tmp/floorplan/
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 19-pdn.def &
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/aca1bc83-ab38-4d7d-b10a-31eb13c3b0ff)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/0bdfaebd-acea-4b27-a027-220449bd5c99)

### <h1 id="header-5_2_2">Detailed routing using TritonRoute and explore the routed layout.</h1>

```bash
echo $::env(CURRENT_DEF)
run_routing
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a4653f78-b816-4d1f-b41b-9def36ce4df1)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5abbae2c-c1aa-415a-95c2-82ef6ca30172)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/4f214f0c-f629-47b5-bc0a-f58e7271af82)

```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-04_08-29/results/routing/

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/f18e6cc1-5aaf-47b2-ab6d-0b60dd468035)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/091c5df8-665d-4f59-afbd-2dc44a61fe44)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/cb4127df-68d7-458d-969a-6a4d58c162ea)

```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/22-04_08-29/tmp/routing
gvim 20-fastroute.guide
```
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/6dce73b4-6f6a-4f34-a42e-4299527e7908)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d2d9589c-dd61-4da0-8278-95a4e7390876)

### <h1 id="header-5_3_4">Post-Route parasitic extraction using SPEF extractor</h1>

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/193a8311-3448-4bbd-ae7c-6b1b3e156f88)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/00d88204-5737-4a8b-b51a-6401d44ea378)

Final generated layout
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/f752e167-ebe7-4d04-881a-0ead8b17f2dd)
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/feb008d4-b448-45b8-8b2e-8bee3ff64aea)

# <h1 id="header-6">References</h1>	
> https://futureskillsprime.in/course/digital-vlsi-soc-design-and-planning

> [Openlane](https://github.com/The-OpenROAD-Project/OpenLane)

> Repo Documentation format inspired from [Ms.Kalpana](https://github.com/kmkalpana2001/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/tree/main) , [Mr.Mohammed Fayiz Ferosh](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main?tab=readme-ov-file)
