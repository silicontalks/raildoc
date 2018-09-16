====================
Rail Library
====================

The first release of RAIL libary consists of analog and digital library. 
The analog library is virtuoso based, including the RAIL cells' schematics, symbols, layouts and testbenchs.
The digital library is milkyway based, including a db file, and CEL/FRAM library compatible for backend place and routing tools.

The following table describes the current released files.

+-----------+----------+-------------------------------+
| Lib Type  | CAD Tool | Supportted Cells              |
+===========+==========+===============================+
| Analog    | Virtuoso | TGATE,PSW,NSW,MUX2,BUFT,PXRO, |
|           |          |                               |
| Cell      |          | DEL, VCDC, PCAP, NCAP, MOMCAP |
+-----------+----------+-------------------------------+
| Analog    | Virtuoso | TB_SWICH,TB_DELAY, TB_CAP     |
|           |          |                               |
| Testbench |          |                               |
+-----------+----------+-------------------------------+
| Analog    | GDS-II   | TGATE,PSW,NSW,MUX2,BUFT,PXRO, |
|           |          |                               |
| Layout *  | Calibre  | DEL, VCDC, PCAP, NCAP, MOMCAP |
+-----------+----------+-------------------------------+
| Digital   | library- | TGATE,PSW,NSW,MUX2,BUFT,PXRO, |
|           |          |                               |
| db Lib    | compiler | DEL, VCDC, PCAP, NCAP, MOMCAP |
+-----------+----------+-------------------------------+
| Digital   | IC       | TGATE,PSW,NSW,MUX2,BUFT,PXRO, |
|           |          |                               |
| Milkway   | Compiler | DEL, VCDC, PCAP, NCAP, MOMCAP |
+-----------+----------+-------------------------------+

Note: Due to the confidential issues, the layout files only released with those users already signed NDAs.


.. toctree::
   :maxdepth: 2
      
   tutgst
   analog
