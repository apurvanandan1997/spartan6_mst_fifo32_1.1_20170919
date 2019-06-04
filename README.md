Module structure
  - mst_fifo_top.v
    o mst_fifo_io.v
    o mst_fifo_fsm.v
    o mst_fifo_ctl.v
    o sp_sram_16k36.v
    o mst_data_chk.v
    o mst_data_gen.v
    o mst_pre_fet.v
2.4.2 Module mst_fifo_top.v
This is the top module of the FIFO master; it contains all the sub modules as well as memory used in the
design. Its interface is identical to the Pin Out (Section 2.2).
2.4.3 Module mst_fifo_io.v
This module connects signals between ports and internal modules. It also controls the direction of
bidirectional IOs DATA and BE.
2.4.4 Module mst_fifo_fsm.v
This module controls all operations of the FIFO master. It controls the state machine, round robin of the
FT600 mode, loopback or streaming data classification as well as the OOB procedure.
2.4.5 Module mst_fifo_ctl.v
This module controls the write and read operations of the internal buffers. When configured to FT245
mode, it uses all 16k36 memory for buffering. In FT600 mode, the memory is divided into 4 equal 4k36
buffers for 4 channels.
2.4.6 Module sp_sram_16k36.v
Module sp_sram_16k36.v is a Single Port SRAM macro generated by Altera Quartus or Xilinx ISE. It is
16K deep and 36 bits wide memory, 32 bits for DATA[31:0] and 4 bits for BE[3:0].
2.4.7 Module mst_data_chk.v
This module checks the sequence of received data in the streaming test. It asserts an error if there is any
sequence mismatch between two consecutive data. It is able to check 1 data stream in FT245 mode or 4
data streams concurrently in FT600 mode. If ERDIS is asserted, this function will be disabled.
2.4.8 Module mst_data_gen.v
This module generates sequential data for the streaming test. Similar to mst_data_chk.v, it is able to
generate 1 or 4 data streams depending on whether FT245 or FT600 mode is configured.
2.4.9 Module mst_pre_fet.v
This module temporarily stores pre-fetch data that will be sent to IOs in master write mode. It optimizes
the timing for FPGAs.
