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


# <h3 id="header-3">Section 3 - Design library cell using Magic Layout and ngspice characterization</h3>	 
## <h3 id="header-3_1">Labs for CMOS inverter ngspice simulations</h3>
### <h3 id="header-3_1_1">IO placer revision</h3>
### <h3 id="header-3_1_2">SPICE deck creation for CMOS inverter</h3>
### <h3 id="header-3_1_3">SPICE simulation lab for CMOS inverter</h3>
### <h3 id="header-3_1_4"> Switching Threshold Vm</h3>
### <h3 id="header-3_1_5"> Static and dynamic simulation of CMOS inverter</h3>
### <h3 id="header-3_1_6"> Lab steps to git clone vsdstdcelldesign</h3>

## <h3 id="header-3_2">Inception of layout ̂A CMOS faabrication process</h3>
### <h3 id="header-3_2_1">Create Active regions</h3>
### <h3 id="header-3_2_2">Formation of N-well and P-well</h3>
### <h3 id="header-3_2_3"> Formation of gate terminal</h3>
### <h3 id="header-3_2_4">Lightly doped drain (LDD) formation</h3>
### <h3 id="header-3_2_5">Source ÃÂ drain formation</h3>
### <h3 id="header-3_2_6">Local interconnect formation</h3>
### <h3 id="header-3_2_7"> Higher level metal formation</h3>
### <h3 id="header-3_2_8"> Lab introduction to Sky130 basic layers layout and LEF using inverter</h3>
### <h3 id="header-3_2_9">Lab steps to create std cell layout and extract spice netlist</h3>

## <h3 id="header-3_3">Sky130 Tech File Labs</h3>
### <h3 id="header-3_3_1">Lab steps to create final SPICE deck using Sky130 tech</h3>
### <h3 id="header-3_3_2">Lab steps to characterize inverter using sky130 model files</h3>
### <h3 id="header-3_3_3">Lab introduction to Magic tool options and DRC rules</h3>
### <h3 id="header-3_3_4">Lab introduction to Sky130 pdk's and steps to download labs</h3>
### <h3 id="header-3_3_5">Lab introduction to Magic and steps to load Sky130 tech-rules</h3>
### <h3 id="header-3_3_6">Lab exercise to fix poly.9 error in Sky130 tech-file</h3>
### <h3 id="header-3_3_7">Lab exercise to implement poly resistor spacing to diff and tap</h3>
### <h3 id="header-3_3_8">Lab challenge exercise to describe DRC error as geometrical construct</h3>
### <h3 id="header-3_3_9">Lab challenge to find missing or incorrect rules and fix them</h3>

# <h4 id="header-4">Section 4 - Pre-layout timing analysis and importance of good clock tree</h4>	 
## <h4 id="header-4_1">Timing modeling using delay tables</h4>
### <h4 id="header-4_1_1">Lab steps to convert grid info to track info</h4>
### <h4 id="header-4_1_2">Lab steps to convert magic layout to std cell LEF</h4>
### <h4 id="header-4_1_3">Introduction to timing libs and steps to include new cell in synthesis</h4>
### <h4 id="header-4_1_4">Introduction to delay tables</h4>
### <h4 id="header-4_1_5">Delay table usage Part 1</h4>
### <h4 id="header-4_1_6">Delay table usage Part 2</h4>
### <h4 id="header-4_1_7">Lab steps to configure synthesis settings to fix slack and include vsdinv</h4>

## <h4 id="header-4_2">Timing analysis with ideal clocks using openSTA</h4>
### <h4 id="header-4_2_1">Setup timing analysis and introduction to flip-flop setup time</h4>
### <h4 id="header-4_2_2">Introduction to clock jitter and uncertainty</h4>
### <h4 id="header-4_2_3">Lab steps to configure OpenSTA for post-synth timing analysis</h4>
### <h4 id="header-4_2_4">Lab steps to optimize synthesis to reduce setup violations</h4>
### <h4 id="header-4_2_5">Lab steps to do basic timing ECO</h4>

## <h4 id="header-4_3">Clock tree synthesis TritonCTS and signal integrity</h4>
### <h4 id="header-4_3_1">Clock tree routing and buffering using H-Tree algorithm</h4>
### <h4 id="header-4_3_2">Crosstalk and clock net shielding</h4>
### <h4 id="header-4_3_3">Lab steps to run CTS using Triton</h4>
### <h4 id="header-4_3_4">Lab steps to verify CTS runs</h4>

## <h4 id="header-4_4">Timing analysis with real clock using openSTA</h4>
### <h4 id="header-4_4_1">Setup timing analysis using real clocks</h4>
### <h4 id="header-4_4_2">Hold timing analysis using real clocks</h4>
### <h4 id="header-4_4_3">Lab steps to analyze timing with real clocks using OpenSTA</h4>
### <h4 id="header-4_4_4">Lab steps to execute OpenSTA with right timing libraries and CTS assignment</h4>
### <h4 id="header-4_4_5">Lab steps to observe impact of bigger CTS buffers on setup and hold timing</h4>

# <h5 id="header-5">Section 5 -Final step for RTL2GDS using tritinRoute and openSTA</h5>	 
## <h5 id="header-5_1">Routing and design rule check (DRC)</h5>
### <h5 id="header-5_1_1">Introduction to Maze Routing ÃÂ LeeÃÂs algorithm</h5>
### <h5 id="header-5_1_2">LeeÃÂs Algorithm conclusion</h5>
### <h5 id="header-5_1_3">Design Rule Check</h5>

## <h5 id="header-5_2">Power Distribution Network and routing</h5>
### <h5 id="header-5_2_1">Lab steps to build power distribution network</h5>
### <h5 id="header-5_2_2">Lab steps from power straps to std cell power</h5>
### <h5 id="header-5_2_3">Basics of global and detail routing and configure TritonRoute</h5>

## <h5 id="header-5_3">TritonRoute Features</h5>
### <h5 id="header-5_3_1">TritonRoute feature 1 - Honors pre-processed route guides</h5>
### <h5 id="header-5_3_2">TritonRoute Feature2 & 3 - Inter-guide connectivity and intra- & inter-layer routing</h5>
### <h5 id="header-5_3_3">TritonRoute method to handle connectivity</h5>
### <h5 id="header-5_3_4">Routing topology algorithm and final files list post-route</h5>




















##  <h6 id="header-6">References</h6>	

> https://futureskillsprime.in/course/digital-vlsi-soc-design-and-planning

> Repo Documentation format inspired from [Ms.Kalpana](https://github.com/kmkalpana2001/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/tree/main) , [Mr.Mohammed Fayiz Ferosh](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/tree/main?tab=readme-ov-file)
