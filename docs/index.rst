.. Read the Docs Template documentation master file, created by
   sphinx-quickstart on Tue Aug 26 14:19:49 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

RAIL: Resilient Analog Instance Language Enabled Mixed-Signal Circuits
======================================================================

It is an open source project for integrated circuits design. 
The project first releases a 65nm-based RAIL cell libary and a tutorial to complete a simple RAIL design on September 2018.

The motivation of the RAIL project is,

- **to accelerate the analog/mixed-signal (AMS) designs**. Traditional analog/mixed-signal integrated circuit design exploits a fully custom follow, in other words, all work is done manually. RAIL reforms it by introducing a verilog-like topology description language (TDL) and generates its behavior/schematic/layout automatically.

- **to enable process-portable design methodology**. Traditional AMS designs are high process dependent, which makes it hard to port among different technology. This feature is the main issues concerning by the AMS open source technology. Conventionally, even an IP is released, designers using other process still spend similar developing effort to re-build it. RAIL want to change this status by the TDL and automatic flow. 



RAIL Project Repo link
^^^^^^^^^^^^^^^^^^^^^^^
Release 0.1: https://github.com/rail-posh/rail65

Contents
^^^^^^^^

.. toctree::
   :maxdepth: 2
   :glob:
   
   railib
   tutgst
   

