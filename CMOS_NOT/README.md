# CMOS NOT Gate (Inverter)

A transistor-level CMOS inverter designed in Electric VLSI and simulated with LTspice. The project includes a schematic, a layout, and SPICE decks exported from both views.

## Logic and truth table

The output is the complement of the input: **Y = ¬A**. Logic `0` represents a low voltage and logic `1` represents a high voltage.

| Input A | Output Y |
|:-------:|:--------:|
| 0 | 1 |
| 1 | 0 |

The PMOS pulls `Y` toward `VDD` when `A` is low. The NMOS pulls `Y` toward ground when `A` is high.

## Design files

| File | Purpose |
| --- | --- |
| [`../inv.jelib`](../inv.jelib) | Electric library containing `inverter{sch}` and `inv_layout{lay}`. |
| [`inverter.spi`](inverter.spi) | SPICE deck exported from the inverter schematic. |
| [`inv_layout.spi`](inv_layout.spi) | SPICE deck exported from the layout. |
| [`inverter.log`](inverter.log), [`inv_layout.log`](inv_layout.log) | LTspice run logs. |

The two simulation decks contain their transistor models and use a **3 V** supply with a pulsed input. The schematic and layout decks use different transistor dimensions, so their timing and current results should not be treated as a direct comparison.

## Open and simulate

1. Open [`../inv.jelib`](../inv.jelib) in **Electric VLSI 9.08** and inspect the `inverter{sch}` and `inv_layout{lay}` cells.
2. Open either `inverter.spi` or `inv_layout.spi` in **LTspice** and run its transient analysis.
3. Plot `V(in)` and `V(out)` for the schematic, or `V(A)` and `V(Y)` for the layout. The output should be high while the input is low, and low while the input is high, after each transition settles.

The included logs show that LTspice 26.1.1 completed the operating-point calculation. A measured propagation delay, power figure, and schematic-versus-layout comparison have not been documented yet.
