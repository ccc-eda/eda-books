```sh
(.venv) cccuser@cccimacdeiMac 01-counter % v2c sim counter.veryl
=== simulating TestCounter ===
$finish called at time 95
TestCounter: PASS
(.venv) cccuser@cccimacdeiMac 01-counter % v2c synth -o counter.json --verilog counter.v counter.veryl
=== Counter ===
  port input    1 i_clk
  port input    1 i_rst
  port input    1 i_en
  port output   4 o_count
  cells: 14
    $_AND_         2
    $_DFF_PN0_     4
    $_MUX_         4
    $_NOT_         1
    $_XOR_         3
wrote counter.json
wrote counter.v
(.venv) cccuser@cccimacdeiMac 01-counter % v2c fpga --pnr veryl --pcf counter.pcf --bin counter.bin counter.veryl
=== Counter ===
  port input    1 i_clk
  port input    1 i_rst
  port input    1 i_en
  port output   4 o_count
  cells: 10
    SB_DFFR        4
    SB_LUT4        6
  veryl pnr: 6 LCs, 52 routing pips, 0.2s
  power: 0.199 mW at 122.1 MHz = dynamic 0.109 + static 0.090; per cycle 0.9 pJ (nets 0.1, clock 0.8, RAM 0.0)
  timing: critical path 8.19 ns, Fmax 122.10 MHz (wirelength-only pass 122.10 MHz)
wrote /var/folders/hp/1n4dfq317b1cv0dtd9w9dw040000gp/T/veryl-eda-6065/out.asc (+ .pcf)
wrote counter.bin
(.venv) cccuser@cccimacdeiMac 01-counter % v2c gatesim ice40 counter.veryl
=== simulating TestCounter ===
$finish called at time 95
TestCounter: PASS
gate-level simulation: Counter as 10 cells (ice40)
(.venv) cccuser@cccimacdeiMac 01-counter % v2c asic counter.veryl
=== Counter ===
  port input    1 i_clk
  port input    1 i_rst
  port input    1 i_en
  port output   4 o_count
  cells: 14
    AND2           2
    DFFR           4
    INV            1
    MUX2           4
    XOR2           3
asic: area 240.0 µm² (cells), die 18.5 × 20.0 µm, 5 rows, utilization 65%, fullest 16 µm bin 72% (target 80%)
asic: wirelength 184 µm, 68 vias, overflow 0 after 1 routing iterations
power: 0.099 mW at 1398.5 MHz = dynamic 0.099 + leakage 0.0000; per cycle 0.07 pJ (nets 0.02, clock 0.03, internal 0.02, SRAM 0.00); IR drop worst 0.04 mV (1000 random cycles)
asic: power grid 6 rails, 2 straps, 12 via stacks; 16 filler cells
asic: detailed routing 249 µm (M2 66 / M3 98 / M4 65 / M5 20), 145 vias, 0 conflicts, 0 opens after 2 iterations
asic: clock tree 0 buffers (), insertion 0.000 ns, skew 0.000 ns; hold: worst slack 0.083 ns, 0 delay buffers
timing: critical path 0.715 ns, Fmax 1398.5 MHz (8 endpoints; ideal clock 1402.3 MHz, wirelength-only placement 1402.3 MHz)
(.venv) cccuser@cccimacdeiMac 01-counter % v2c asic --pdk sky130 --def counter.def --gds counter.gds counter.veryl
asic: technology sky130_fd_sc_hd (2.72 µm rows, 0.46 µm sites)
=== Counter ===
  port input    1 i_clk
  port input    1 i_rst
  port input    1 i_en
  port output   4 o_count
  cells: 14
    sky130_fd_sc_hd__and2_1 2
    sky130_fd_sc_hd__dfrtp_1 4
    sky130_fd_sc_hd__inv_1 1
    sky130_fd_sc_hd__mux2_1 4
    sky130_fd_sc_hd__xor2_1 3
asic: area 187.7 µm² (cells), die 17.9 × 19.0 µm, 7 rows, utilization 55%, fullest 16 µm bin 66% (target 70%)
asic: wirelength 203 µm, 77 vias, overflow 0 after 1 routing iterations
power: 0.057 mW at 747.0 MHz = dynamic 0.057 + leakage 0.0000; per cycle 0.08 pJ (nets 0.02, clock 0.02, internal 0.03, SRAM 0.00); IR drop worst 0.00 mV (1000 random cycles)
asic: power grid 8 rails, 0 straps, 0 via stacks; 37 filler cells
asic: DRC 1999 shapes: 0 shorts, 0 spacing, 0 min-area, 0 opens; 11 taps (0 sites too far)
asic: detailed routing 283 µm (met1 67 / met2 114 / met3 52 / met4 51), 149 vias, 0 conflicts, 0 opens after 1 iterations
asic: clock tree 0 buffers (), insertion 0.000 ns, skew 0.000 ns; hold: worst slack 0.343 ns, 0 delay buffers
timing: critical path 1.339 ns, Fmax 747.0 MHz (8 endpoints; ideal clock 753.9 MHz, wirelength-only placement 752.8 MHz)
wrote counter.gds (83834 bytes: 62 cell instances, 555 shapes, 7 labels)
wrote counter.def
```
