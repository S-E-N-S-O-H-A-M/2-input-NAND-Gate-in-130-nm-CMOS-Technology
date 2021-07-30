# Design and Analysis of a 2-input NAND Gate in 130 nm CMOS Technology
<p>Readme.txt presents process of design and simulation of a 2-input CMOS NAND gate using esim and sky130 technology.The specifications of the design can be found here.</p>
---------------------------------------------------------------------------------------------------------------------------------------------
<p>&gt;&gt;Table Of Contents</p>
<p>(1)Circuit Details</p>
<p>(2)Tools</p>
<p>(3)Circuit Design</p>
<p>(4)Circuit Simulation</p>
<p>(5)Observation</p>
<p>(6)Contributor</p>
<p>(7)Acknowledgement</p>
---------------------------------------------------------------------------------------------------------------------------------------------
<p>&gt;&gt;Circuit Details</p>
<p>Logic gates perform basic logical functions and are the elemental building blocks of digital integrated circuits.Most logic gates take an input of two binary values, and output one value of a 1 or 0. NAND circuit is one of the important logic gates.CMOS is the combination of PMOS and NMOS. Figure 1 shows the realization of a 2 input CMOS NAND gate. It consists of two series NMOS transistors between Vout and GND and two parallel PMOS transistors between Vout and Vdd i.e. at 5V. If both inputs Va and Vb are low i.e. at 0V, both of the NMOS transistors will be OFF and both of the PMOS transistors will be ON. Hence, the output Vout will be high i.e. 5V. If any one of the inputs is high i.e at 5V and the other input is low i.e at 0V, one of the NMOS transistors will be ON and one among the two parallel PMOS transistors will be ON, creating a path from Vout to Vdd. Hence, the output Vout will be high i.e. at 5V. If both inputs are high i.e. 5V, both of the NMOS transistors will be ON and both of the PMOS transistors will be OFF. Hence, the output will be low i.e at 0V. When any of the inputs are low, then the output is pulled high through the parallel PMOS transistors. When all of the inputs are high, then the output is pulled low through the series NMOS transistors. If we apply 2 different clock signals as the inputs of NAND gate Va and Vb, then the output of the NAND gate is shown in Figure 2 where Va, Vb are inputs and Vout is output.&nbsp;</p>
<p>----------------------------------------------------------------------------------------------------------------------------------------------</p>
<p>&gt;&gt;Tools</p>
<p>The tools used for circuit design and simulations are:</p>
<p>(1)eSim</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>(1.1)Steps to download and install esim</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.1) Download the latest eSim release for Windows OS from the link: https://esim.fossee.in/downloads .</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.2) Locate the installer file in the folder where your downloaded files are kept.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.3)Double click on the file.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.4) If a pop-up window appears asking &rdquo;Do you want to allow the following program from an unknown publisher to make changes <span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>to this computer?&rdquo;,click YES.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.5)Then in the &rdquo;License Agreement&rdquo; window, select the I Agree option.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.6). Click Next when the program asks for you to &rdquo;Choose Install Location&rdquo;.We have taken care to auto-select the destination <span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>folder path.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.7)In the next window that appears, select Install.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1.1.8)A progress bar will appear; once it reaches 100%, &rdquo;Installation Complete&rdquo; message will be shown at the top of the eSim <span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>setup window. Click on Close. eSim shortcut icon will be on your Desktop.</p>
<p><br></p>
<p>(2)SkyWater SKY130 PDK</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>(2.1)Steps to download</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(2.1.1)Download using this link and unzip: https://static.fossee.in/esim/installation-files/sky130_fd_pr.zip</p>
<p>(3)ngspice</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>It is already installed with esim.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span></p>
<p>The schematics for 2-input CMOS NAND gate was designed in eSim and simulated in ngspice.</p>
----------------------------------------------------------------------------------------------------------------------------------------------
<p>&gt;&gt;Circuit Design</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>--&gt;Steps:</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1)Design the crcuit in esim</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(2)Genreate the netlist in esim&nbsp;</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(3)Open the workspace folder where esim projects are saved. Open the &quot;2-input_CMOS_NAND_gate&quot; folder.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(4)Copy the .cir.out file and save in the sky_fd_pr folder downloaded earlier as .cir file.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(5)Open with notepad and add the path .lib &quot;models/sky130.lib.spice&quot; tt at the top.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(6)Replace with CMOSP, mos_p with sky130_fd_pr__pfet_01v8 and CMOSN, mos_n with &nbsp;sky130_fd_pr__nfet_01v8.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(7) To replace inductor, capacitor, resistor do it this way for example: L1 out gnd 1m by x1 &nbsp;out gnd mid 0 sky130_fd_pr__ind_03_90.</p>
<p>Note: For more details go to the cells folder in sky_fd_pr. Open the specific component folder which you want to use. Then open the test folder and check the SPICE file. The SPICE file is an example of implementation of that component. You will get to know how to use the component in your ckt.</p>
----------------------------------------------------------------------------------------------------------------------------------------------
<p>&gt;&gt;Circuit Simulation</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>--&gt;Steps:</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(1)Right click on .cir file.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(2)Click on Open With</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(3)Browse for the ngspice.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(4)If ngspice not present scroll down click on More Apps.</p>
<p><span style="white-space:pre;">&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;</span>(5)Go to the FOSSEE folder search for Ngspice. Run it</p>
----------------------------------------------------------------------------------------------------------------------------------------------
<p>&gt;&gt;Observation</p>
<p>It was observed that the output waveform matches with reference to the truth table of NAND gate for different combination of inputs.</p>
----------------------------------------------------------------------------------------------------------------------------------------------
<p>&gt;&gt;Contributor</p>
<p><span style="white-space:pre;">&nbsp; &nbsp;&nbsp;</span>-Soham Sen, B.Tech (Electronics and Communication Engineering), Amity University Kolkata - sohamsen25420001@gmail.com</p>
----------------------------------------------------------------------------------------------------------------------------------------------

