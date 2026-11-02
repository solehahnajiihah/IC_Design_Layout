A transistor-level two-input NAND gate designed in Electric VLSI and simulated with LTspice. The project includes a schematic, a layout, and SPICE decks exported from both views.

## Logic and truth table

The output is low only when **both** inputs are high: **Y = ¬(A · B)**. Logic `0` represents a low voltage and logic `1` represents a high voltage.

| Input A | Input B | Output Y |
|:-------:|:-------:|:--------:|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Two PMOS transistors form a parallel pull-up network, and two NMOS transistors form a series pull-down network. The output reaches ground only when both NMOS transistors conduct.

## Design files

| File | Purpose |
| --- | --- |
| [`../nand.jelib`](../nand.jelib) | Electric library containing `nand_sc{sch}` and `nand_layout{lay}`. |
| [`nand_sc.spi`](nand_sc.spi) | SPICE deck exported from the schematic. |
| [`nand_layout.spi`](nand_layout.spi) | SPICE deck exported from the layout. |
| [`nand_sc.log`](nand_sc.log), [`nand_layout.log`](nand_layout.log) | LTspice run logs. |

Both decks include their transistor models and pulsed inputs. The schematic simulation uses **1.2 V**, while the layout simulation uses **3 V** and different transistor widths. Their timing and current results therefore cannot be directly compared.

## Open and simulate

1. Open [`../nand.jelib`](../nand.jelib) in **Electric VLSI 9.08** and inspect the `nand_sc{sch}` and `nand_layout{lay}` cells.
2. Open either `nand_sc.spi` or `nand_layout.spi` in **LTspice** and run its transient analysis.
3. Plot `V(a)`, `V(b)`, and `V(y)`. Check all four settled input combinations against the truth table above.

The included logs show that LTspice 26.1.1 completed the operating-point calculation. The exported layout deck also contains an Electric warning: `no power connection for P-transistor wells`. The well tie should be corrected and the layout rechecked before claiming a verified physical design. Measured delay, power, and schematic-versus-layout equivalence have not been documented yet.
