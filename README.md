Shift-and-Add 32-bit Signed Multiplier (Verilog FPGA Design)
Project Overview

This project implements a 32-bit signed sequential multiplier using the shift-and-add algorithm in Verilog HDL. The design is structured using a Finite State Machine (FSM) and a datapath architecture, enabling efficient hardware multiplication over 32 clock cycles. It supports signed inputs and produces a 64-bit signed output.

The design was simulated and verified using GTKWave and a self-checking Verilog testbench.

Features
32-bit signed multiplication
64-bit output result
FSM-based control (IDLE, LOAD, COMPUTE, DONE)
Shift-and-add sequential algorithm
Signed number handling (two’s complement)
Automated testbench verification
GTKWave simulation support
Project Structure
/src
   shift_add_multiplier_fsm.v   → Main design (FSM + datapath)
/testbench
   tb_multiplier.v              → Verification testbench
/waveform
   wave.vcd                     → GTKWave simulation output
/gtkwave
   screenshots                  → Simulation results images
Algorithm Summary

The multiplier works by iterating through each bit of the multiplier:

If the current bit is 1 → add shifted multiplicand to product
Shift multiplicand left each cycle
Shift multiplier right each cycle
Repeat for 32 cycles

Sign handling is done using XOR of input signs and final negation if required.

How to Run Simulation
1. Compile Verilog Code

Using Icarus Verilog:

iverilog -o sim shift_add_multiplier_fsm.v tb_multiplier.v
2. Run Simulation
vvp sim
3. View Waveform in GTKWave
gtkwave wave.vcd
Testbench

The testbench automatically verifies correctness using multiple test cases including:

Positive × Positive
Positive × Negative
Negative × Negative
Edge cases (0, 1, large numbers)

It uses a task-based structure:

run_test(13, 11, 143, 1);

Results are printed as PASS/FAIL along with expected vs actual output.

Simulation Results

GTKWave confirms correct operation:

Proper FSM transitions (IDLE → LOAD → COMPUTE → DONE)
Correct shift-and-add behavior per cycle
Accurate accumulation in product
Proper sign correction at the end
Stable done signal indicating completion
GitHub Repository

All source code, testbench, and simulation files are available at:

https://github.com/minevoria/32-bit-Shift-Add-Multiplier

The repository also includes:

Full Verilog source code
Testbench files
GTKWave screenshots
Installation instructions