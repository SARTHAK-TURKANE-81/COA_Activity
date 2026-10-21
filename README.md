# Pipeline Execution Simulator

COA CO5 Micro Project, Sanjivani University (Topic 4: Pipeline execution: stages, hazards, stalls)

A step-by-step simulator of a five-stage RISC pipeline (IF, ID, EX, MEM, WB). It runs a small assembly program one clock cycle at a time and shows hazards, stalls, flushes and forwarding as they happen.

**Author:** Sarthak Turkane, PRN 2125UIDM1080


**Faculty:** Prof. Ankita A

## Files

| File | Purpose |
|---|---|
| `PipelineSimulator.html` | The simulator. One self-contained file (HTML, CSS, JS), no libraries, works offline. |
| `Pipeline_Simulator_Documentation.docx` | Full project report with theory, design, user manual, tests, viva Q&A and source code. |

## How to run

Double-click `PipelineSimulator.html`. It opens in any modern browser. No installation or internet needed.

## Features

- Cycle-by-cycle execution with **Step**, **Back**, **Play**, **Run to end** and **Reset**
- Stage boxes showing what each stage is doing, with the reason for every stall or flush
- Live timing diagram (hatched cell = stall, black X cell = flushed instruction)
- Data hazards (RAW, load-use), control hazards (branches, jumps) and memory wait states
- Register file, data memory and performance statistics (cycles, CPI, stalls, speedup)
- **Compare configurations** button to test several pipeline designs on the same program
- Automatic check of every result against a non-pipelined execution
- Black-and-white, print-friendly design; keyboard shortcuts (Right = step, Left = back, Space = play)

## Adjustable parameters

| Parameter | Options |
|---|---|
| Data forwarding | On or off |
| Branch resolved in stage | ID, EX or MEM |
| Branch policy | Predict not taken (flush) or stall fetch |
| Memory latency | 1 to 6 cycles for `lw` / `sw` |

You can also edit the program and set initial registers (`r1=5`) and memory words (`m0=10`).

## Example programs included

Dependent chain, independent instructions, load-use hazard, taken branch, array-sum loop, Fibonacci loop.

## Supported instructions

`add` `sub` `and` `or` `slt` `addi` `lw` `sw` `beq` `bne` `j` `nop` `halt`, plus pseudo instructions `li` and `move`.
32 registers (`r0` to `r31`, `r0` is always 0), 256 words of data memory, labels with `name:`, comments with `#`.

## Testing

- Cycle counts checked against hand calculation (for example, 5 independent instructions take 9 cycles)
- 9,036 randomised runs matched the non-pipelined reference with 0 mismatches
- Timing rules checked on 11,016 further runs with 0 failures
- Interface tested in a headless browser with no errors

## Limitations

Fixed five-stage depth, static branch prediction, no caches, integer instructions only, single-issue in-order execution.
