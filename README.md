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

**Components of a chip**
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

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5a03f636-9323-4289-ad27-73e272387fa8)

- EDA tools : Electronic Design Automation tools are software applications used in electronic system and integrated circuit design. They automate tasks like schematic capture, simulation, synthesis, place and route, timing analysis, physical verification, and power analysis. These tools are crucial for creating complex electronic systems efficiently and accurately, reducing development time and cost.

- PDK : Process Design Kit is a collection of files and documents provided by semiconductor foundries to support the design of ICs using their manufacturing processes. PDKs contain information about the foundry's fabrication processes, including design rules, device models, parameterized cells (PCells), technology files, and simulation models. Designers use PDKs with EDA tools to create custom IC layouts and verify their designs before manufacturing. 

-  Open Source PDK : The Open Source PDK from Google and SkyWater Technology Foundry offers a freely available Process Design Kit (PDK) based on the 130nm technology node. [Github](https://github.com/google/skywater-pdk)
  

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d5b2302f-b775-4309-acd3-2dd5f7c9ee75)







### <h1 id="header-1_2_2">1.2.2 -  Simplified RTL2GDS flow</h1>
### <h1 id="header-1_2_3">1.2.3 - Introduction to OpenLANE and Strive chipsets</h1>
### <h1 id="header-1_2_4">1.2.4 - Introduction to OpenLANE detailed ASIC design flow</h1>

## <h1 id="header-1_3">1.3 - Get familiar to open-source EDA tools</h1>

### <h1 id="header-1_3_1">1.3.1 - OpenLANE Directory structure in detail</h1>
### <h1 id="header-1_3_2">1.3.2 - Design Preparation Step</h1>
### <h1 id="header-1_3_3">1.3.3 - Review files after design prep and run synthesis</h1>
### <h1 id="header-1_3_4">1.3.4 - OpenLANE Project Git Link Description</h1>
### <h1 id="header-1_3_5">1.3.5 - Steps to characterize synthesis results</h1>

# <h2 id="header-2">Section 2 - Good floorplan vs bad floorplan and introduction to library cells (13/03/2024 - 14/03/2024)</h2>	

## <h2 id="header-2_1">2.1 - Chip Floor planning consideration</h2>

### <h2 id="header-2_1_1">2.1.1 - Utilization factor and aspect ratio</h2>
### <h2 id="header-2_1_2">2.1.2 - Utilization factor and aspect ratio</h2>
### <h2 id="header-2_1_3">2.1.3 - De-coupling capacitors</h2>
### <h2 id="header-2_1_4">2.1.4 - Power planning</h2>
### <h2 id="header-2_1_5">2.1.5 - Pin placement and logical cell placement blockage</h2>
### <h2 id="header-2_1_6">2.1.6 - Steps to run floorplan using OpenLANE</h2>
### <h2 id="header-2_1_7">2.1.7 - Review floorplan files and steps to view floorplan</h2>
### <h2 id="header-2_1_8">2.1.8 - Review floorplan layout in Magic</h2>


## <h2 id="header-2_2">2.2 - Library building and Placement</h2>

### <h2 id="header-2_2_1">2.2.1 - Netlist binding and initial place design</h2>
### <h2 id="header-2_2_2">2.2.2 - Optimize placement using estimated wire-length and capacitance</h2>
### <h2 id="header-2_2_3">2.2.3 - Final placement optimization</h2>
### <h2 id="header-2_2_4">2.2.4 - Need for libraries and characterization</h2>
### <h2 id="header-2_2_5">2.2.5 - Congestion aware placement using RePlAce</h2>

## <h2 id="header-2_3">2.3 - Cell design and characterization flows</h2>

### <h2 id="header-2_3_1">2.3.1 - Inputs for cell design flow</h2>
### <h2 id="header-2_3_2">2.3.2 - Circuit design steps</h2>
### <h2 id="header-2_3_3">2.3.3 - Layout design step</h2>
### <h2 id="header-2_3_4">2.3.4 - Typical characterization flow</h2>

## <h2 id="header-2_4">2.4 - General timing characterization parameters</h2>

### <h2 id="header-2_4_1">2.4.1 - Timing threshold definitions</h2>
### <h2 id="header-2_4_2">2.4.2 - Propagation delay and transition time</h2>


# References 
> https://futureskillsprime.in/course/digital-vlsi-soc-design-and-planning

> Repo Documentation format inspired from [Ms.Kalpana](https://github.com/kmkalpana2001/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/tree/main) , [Mr.Mohammed Fayiz Ferosh](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main?tab=readme-ov-file)
