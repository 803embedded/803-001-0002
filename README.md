# 803-001-002-A - Digi cellular radio adapter for Toradex Viola

This KiCad 9 project is a native reconstruction of **803-001-001-B** from its released ODB++ manufacturing data. Connector and mounting-hole locations, board outline, signal routing, ground copper, and artwork are carried over from Rev B.

## Cellular modification

The original C3 10 uF / 1206 capacitor is replaced by:

- **C3: 220 uF, 16 V, polymer tantalum, 7343-31**
- KEMET `T521D227M016ATE025` (25 mΩ ESR)
- Digi-Key `399-T521D227M016ATE025CT-ND`

C3 is polarized; pad 1 / the marked end is VCC. Its center is shifted 0.94 mm left from the old C3 center to clear C2, and both pads have short 1.2 mm-wide connections into the unchanged VCC/GND copper.

TODO: update the below info

Digi's XBee Cellular 3G Global guide recommends at least 220 uF of bulk capacitance at VCC because cellular startup/wakeup inrush can approach 2 A. The existing 47 pF and 1 uF high-frequency bypass capacitors are retained. Reference:
<https://docs.digi.com/resources/documentation/digidocs/90001541/reference/r_cell_power_supply.htm>

## Validation notes

The schematic passes KiCad ERC with zero violations. Board DRC has zero errors. It retains warnings associated with the source reconstruction: legacy vector silkscreen contacts, custom footprints that intentionally differ from current KiCad library copies, and isolated same-net shapes carried over from ODB++. There are no unconnected items. The C3 area has no clearance, crossing, short-circuit, or unconnected-item violation. The WA-SMST spacer's intentional NPTH-in-copper construction is handled by two reference-scoped custom rules in `803-001-002-A.kicad_dru`.

## Project files

- `803-001-002-A.kicad_pro` - KiCad project
- `803-001-002-A.kicad_sch` - schematic
- `803-001-002-A.kicad_pcb` - two-layer PCB
- `803-001-002-A_BOM.csv` - assembly BOM

The XBee module itself is user-installed and is not part of the assembly BOM.
