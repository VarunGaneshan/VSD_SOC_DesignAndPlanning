![Screenshot 2024-04-13 at 18-51-16 Digital VLSI SoC Design and Planning](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/8dac8fb8-1ab9-496e-9938-8b69647660f3)

# Digital VLSI SoC Design and Planning
![squadron-02_TOP-1-720x380](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/5c0419bc-6be6-4581-bcb6-3272072488b2)

The VSD Squadron board's chip was designed using the flow discussed in this workshop.This chip is a 48 pin QFN package.

![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/d13750d8-9dab-424a-b840-5bb354610722)

Inverter is used as the macro in this workshop.

> https://vsdsquadron.vlsisystemdesign.com/digital-vlsi-soc-design-and-planning/

# Contents 
![image](https://github.com/VarunGaneshan/VSD_SOC_DesignAndPlanning/assets/94780009/a443bbce-ef34-4128-8685-337cf54be8e1)

 <div class="toc">
  <ul>
    <li><a href="#header-1">Section 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK (11/04/2024 - 12/03/2024) </a></li>
	<ul>
        <li><a href="#header-1_1"> How to talk to computers</a></li>
		<ul>
			<li><a href="#header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_1_2">Introduction to RISC-V</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_1_3">From Software Applications to Hardware</a></li>
		</ul>
      </ul>
      <ul>
        <li><a href="#header-1_2">Soc design and OpenLANE</a></li>
	      <ul>
			<li><a href="#header-1_2_1">Introduction to all components of open-source digital asic design</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_2_2"> Simplified RTL2GDS flow</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_2_3">Introduction to OpenLANE and Strive chipsets</a></li>
		</ul>
	      <ul>
			<li><a href="#header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</a></li>
		</ul>
      </ul>
	<ul>
        <li><a href="#header-1_3">Get familiar to open-source EDA tools</a></li>
		<ul>
			<li><a href="#header-1_3_1">OpenLANE Directory structure in detail</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_2">Design Preparation Step</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_3">Review files after design prep and run synthesis</a></li>
		</ul>
	      <ul>
			<li><a href="#header-1_3_4">OpenLANE Project Git Link Description</a></li>
		</ul>
		<ul>
			<li><a href="#header-1_3_5">Steps to characterize synthesis results</a></li>
		</ul>
      </ul>
   </div>
  
<div class="toc">
  <ul>
    <li><a href="#header-2">Section 2 - Good floorplan vs bad floorplan and introduction to library cells (13/03/2024 - 14/03/2024) </a></li>
	<ul>
        <li><a href="#header-2_1"> Chip Floor planning consideration</a></li>
		<ul>
			<li><a href="#header-2_1_1">Utilization factor and aspect ratio</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_2">Concept of pre-placed cells</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_3">De-coupling capacitors</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_1_4">Power planning</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_5">Pin placement and logical cell placement blockage</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_6">Steps to run floorplan using OpenLANE</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_1_7">Review floorplan files and steps to view floorplan/a></li>
		</ul>
	      <ul>
		      <li><a href="#header-2_1_8">Review floorplan layout in Magic</a></li>
		</ul>
      </ul>
      <ul>
        <li><a href="#header-2_2">Library building and Placement</a></li>
	      <ul>
			<li><a href="#header-2_2_1">Netlist binding and initial place design</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_2">Optimize placement using estimated wire-length and capacitance</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_3">Final placement optimization</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_2_4">Need for libraries and characterization</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_2_5">Congestion aware placement using RePlAce</a></li>
		</ul>
      </ul>
	<ul>
        <li><a href="#header-2_3">Cell design and characterization flows</a></li>
		 <ul>
			<li><a href="#header-2_3_1">Inputs for cell design flow</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_3_2">Circuit design steps</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_3_3">Layout design step</a></li>
		</ul>
	      <ul>
			<li><a href="#header-2_3_4">Typical characterization flow</a></li>
		</ul>
      </ul>
	  <ul>
        <li><a href="#header-2_4">General timing characterization parameters</a></li>
		   <ul>
			<li><a href="#header-2_4_1"> Timing threshold definitions</a></li>
		</ul>
		<ul>
			<li><a href="#header-2_4_2">Propagation delay and transition time</a></li>
		</ul>
      </ul>
</div>
  
# <h1 id="header-1">Section 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK (11/04/2024 - 12/03/2024) </h1>	 
## <h1 id="header-1_1">How to talk to computers?</h1>
### <h1 id="header-1_1_1">Introduction to QFN-48 Package, chip, pads, core, die and IPs</h1>
### <h1 id="header-1_1_2">Introduction to RISC-V</h1>
### <h1 id="header-1_1_2">From Software Applications to Hardware</h1>

## <h1 id="header-1_2">Soc design and OpenLANE</h1>
### <h1 id="header-1_2_1">Introduction to all components of open-source digital asic design</h1>
### <h1 id="header-1_2_2"> Simplified RTL2GDS flow</h1>
### <h1 id="header-1_2_3">Introduction to OpenLANE and Strive chipsets</h1>
### <h1 id="header-1_2_4">Introduction to OpenLANE detailed ASIC design flow</h1>

## <h1 id="header-1_3">Get familiar to open-source EDA tools</h1>
### <h1 id="header-1_3_1">OpenLANE Directory structure in detail</h1>
### <h1 id="header-1_3_2">Design Preparation Step</h1>
### <h1 id="header-1_3_3">Review files after design prep and run synthesis</h1>
### <h1 id="header-1_3_5">Steps to characterize synthesis results</h1>

# <h2 id="header-2">Day 2 - Good floor planning considerations</h2>	 
## <h2 id="header-2_1">Chip Floor planning consideration</h2>
### <h2 id="header-2_1_1">Utilization factor and aspect ratio</h2>
### <h2 id="header-2_1_2">Utilization factor and aspect ratio</h2>
### <h2 id="header-2_1_3">De-coupling capacitors</h2>
### <h2 id="header-2_1_4">Power planning</h2>
### <h2 id="header-2_1_5">Pin placement and logical cell placement blockage</h2>
### <h2 id="header-2_1_6">Steps to run floorplan using OpenLANE</h2>
### <h2 id="header-2_1_7">Review floorplan files and steps to view floorplan</h2>
### <h2 id="header-2_1_8">Review floorplan layout in Magic</h2>


## <h2 id="header-2_2">Library building and Placement</h2>
### <h2 id="header-2_2_1">Netlist binding and initial place design</h2>
### <h2 id="header-2_2_2">Optimize placement using estimated wire-length and capacitance</h2>
### <h2 id="header-2_2_3">Final placement optimization</h2>
### <h2 id="header-2_2_4">Need for libraries and characterization</h2>
### <h2 id="header-2_2_5">Congestion aware placement using RePlAce</h2>

## <h2 id="header-2_3">Cell design and characterization flows</h2>
### <h2 id="header-2_3_1">Inputs for cell design flow</h2>
### <h2 id="header-2_3_2">Circuit design steps</h2>
### <h2 id="header-2_3_3">Layout design step</h2>
### <h2 id="header-2_3_4">Typical characterization flow</h2>

## <h2 id="header-2_4">General timing characterization parameters</h2>
### <h2 id="header-2_4_1">Timing threshold definitions</h2>
### <h2 id="header-2_4_2">Propagation delay and transition time</h2>




















##  <h6 id="header-6">References</h6>	

> https://futureskillsprime.in/course/digital-vlsi-soc-design-and-planning

> Repo Documentation format inspired from [Ms.Kalpana](https://github.com/kmkalpana2001/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/tree/main) , [Mr.Mohammed Fayiz Ferosh](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main?tab=readme-ov-file)
