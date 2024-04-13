![Screenshot 2024-04-13 at 18-51-16 Digital VLSI SoC Design and Planning](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8dac8fb8-1ab9-496e-9938-8b69647660f3)

# Digital VLSI SoC Design and Planning
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/6cd44a71-c8f5-4936-aaeb-f33dddae42f5)


The VSD Squadron board's chip was designed using the flow discussed in this workshop.This chip is a 48 pin QFN package.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d13750d8-9dab-424a-b840-5bb354610722)

Inverter is used as the macro in this workshop.

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
            <li><a href="#header-2_2_1">Netlist binding and initial place design</a></li>
            <li><a href="#header-2_2_2">Optimize placement using estimated wire-length and capacitance</a></li>
            <li><a href="#header-2_2_3">Final placement optimization</a></li>
            <li><a href="#header-2_2_4">Need for libraries and characterization</a></li>
            <li><a href="#header-2_2_5">Congestion aware placement using RePlAce</a></li>
          </ul>
        </li>
        <li><a href="#header-2_3">Cell design and characterization flows</a>
          <ul>
            <li><a href="#header-2_3_1">Inputs for cell design flow</a></li>
            <li><a href="#header-2_3_2">Circuit design steps</a></li>
            <li><a href="#header-2_3_3">Layout design step</a></li>
            <li><a href="#header-2_3_4">Typical characterization flow</a></li>
          </ul>
        </li>
        <li><a href="#header-2_4">General timing characterization parameters</a>
          <ul>
            <li><a href="#header-2_4_1">Timing threshold definitions</a></li>
            <li><a href="#header-2_4_2">Propagation delay and transition time</a></li>
          </ul>
        </li>
      </ul>
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








### <h1 id="header-1_1_2">1.1.2 - Introduction to RISC-V</h1>
### <h1 id="header-1_1_2">1.1.3 - From Software Applications to Hardware</h1>

## <h1 id="header-1_2">1.2 - Soc design and OpenLANE</h1>

### <h1 id="header-1_2_1">1.2.1 - Introduction to all components of open-source digital asic design</h1>
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
