=================================
Tutorial for RAIL Getting Started
=================================

**Author**：Chixiao Chen

This a simple tutorial on how to implement a RAIL flow to design an AMS module from scratch to a LVS/DRC clean GDS.
To reveil the truth of RAIL, we illustrate the RAIL flow step by step, rather than providing a makefile based fully automatic flow.

To begin with, we need to download the following files from RAIL/rail65 repo, unzip if necessary, and put them onto your VLSI design server,

- analog/cdk_oa/rail.zip cds.lib
- digital/front_end/rail65.db
- digital/backe_end/FRAM_only/rail65.zip
- analog/gds/rail65.gds (This file is not open for download due to NDA issues, plz contact rail4open@gmail.com to get them).

To complete the sample, please confirm your enviroment already have installed Cadence IC6, Synopsys ICC and Mentor Calibre.

Step 1: Load a Verilog Netlist
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In this example, we are going to design a CMOS transmission gate whose on-resistance is less than 200 Ohm at 0.6V operating point. We are going to use the RAIL cell, TGAT, and some digital gate from standard cell library.
The RAIL compiler will generate a verilog based netlist as follow, 

.. code-block:: Verilog

   // File: swbk01.v
   `timescale 1ns/1ps
   module module SW_BANK_01 (
     input  SW,
     output POS, NEG 
     );
     BUFFD3 b01  (.I(SW),.Z(SWB));
     TGAT   sw00 (.SW(SWB),.POS(POS),.NEG(NEG));
     TGAT   sw01 (.SW(SWB),.POS(POS),.NEG(NEG));
     TGAT   sw02 (.SW(SWB),.POS(POS),.NEG(NEG));
     TGAT   sw03 (.SW(SWB),.POS(POS),.NEG(NEG));
     TGAT   sw04 (.SW(SWB),.POS(POS),.NEG(NEG));
     TGAT   sw05 (.SW(SWB),.POS(POS),.NEG(NEG));
   endmodule

The design paralles 6 TGAT cells, which are drived by BUFFD3 from standard cell. The top cell name is named as *SW_BANK_01*.
The verilog file can be found under the RAIL repo, rail65/sample_getting_started .

Step 2: Generate an OA-based Schematic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Modify the netlist with the power supply ports,

.. code-block:: Verilog

   // File: swbk01_sch.v
   `timescale 1ns/1ps
   module SW_BANK_01 (
     inout  VDD,VSS,  // Power supply ports
     input  SW,
     output POS, NEG
     );
     BUFFD3 b01  (.I(SW),.Z(SWB), .VDD(VDD),.VSS(VSS));
     TGAT   sw00 (.SW(SWB),.POS(POS),.NEG(NEG), .VDD(VDD),.VSS(VSS));
     TGAT   sw01 (.SW(SWB),.POS(POS),.NEG(NEG), .VDD(VDD),.VSS(VSS));
     TGAT   sw02 (.SW(SWB),.POS(POS),.NEG(NEG), .VDD(VDD),.VSS(VSS));
     TGAT   sw03 (.SW(SWB),.POS(POS),.NEG(NEG), .VDD(VDD),.VSS(VSS));
     TGAT   sw04 (.SW(SWB),.POS(POS),.NEG(NEG), .VDD(VDD),.VSS(VSS));
     TGAT   sw05 (.SW(SWB),.POS(POS),.NEG(NEG), .VDD(VDD),.VSS(VSS));
   endmodule

Before launching the virtuoso, make sure cds.lib has been configured correctly that rail65/tsmcN65/tcbn65lp/analogLib/basic can show up in the library manager.

Launch Virtuoso, create a libary named as *rail_design* or any name you want

File --> Import --> Verilog, configure the VerilogIn as follow,

.. image:: ../image/verilogin1.png
     :align: center
     :width: 200
     
The target library is the library you created, the reference library should include basic/tcbn65lp(standard cell)/rail65. 
And most importantly, add the verilog netlist.
To avoid global pin mess, we recommand filling out some name different from your power/gound pin, as shown below

.. image:: ../image/verilogin2.png
     :align: center
     
Click the OK or Apply. Virtuoso supports a structual verilog schematic generation. If verilog imports successfully, you will see a new schemtaic in the *rail_design* library, thought the wires are ugly.

.. image:: ../image/verilogin3.png
     :align: center

The generated schematic can be used for pre-layout simulation and LVS.

Step 3: Generate an Milkyway-based Physcal Design
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

adf

Step 4: Merge the GDS and Import to Virtuoso
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

adf

Step 5: RUN the DRC/LVS/PEX and post-simulation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

