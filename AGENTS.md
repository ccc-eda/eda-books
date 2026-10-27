# AGENTS.md

Docs-only repo: a Traditional-Chinese book (`book/`) + user manual (`manual/`) about the
**veryl2chip** EDA toolchain (github.com/ccc-eda/veryl2chip). No build system here —
nothing to compile, lint, or test in this repo itself.

## Layout

- `book/` — the book, ~60 numbered chapters (01–06 + appendices A.1/A.2), filename = `NN.N-標題.md`. `book/README.md` is the table of contents; **update it when adding/renaming chapters**.
- `manual/` — usage manual, numbered `01-intro.md` … `14-reference.md`.
- `code/01-counter/` — worked example: `counter.veryl` plus all `v2c` outputs (`counter.json/.v/.pcf/.bin/.gds/.def`, `wave.vcd`).
- `_doc/note/` — author's private notes (project history, TODOs, grammar notes); useful context, not part of the book.

## Conventions

- Write content in **Traditional Chinese**; keep technical terms in English. `book/A.1-術語對照表.md` is the canonical 中英 term mapping — follow it.
- All technical claims (commands, flags, file names, line counts, architecture) must match the actual veryl2chip repo. Cross-check against `manual/13-develop.md` (dev/verification chapter) and `book/A.2-原始碼檔案索引.md` (source file map) before writing about internals.
- Key facts to keep straight: the tool binary is `v2c` (subcommands: `sim list synth fpga asic gatesim cc pdk`); two Rust crates `veryl-sim` (simulator) and `veryl-eda` (synth + FPGA/ASIC backends); ASIC targets SKY130 (`sky130_fd_sc_hd`); FPGA targets iCE40/ECP5 with an in-house P&R (`--pnr veryl`) requiring the IceStorm `chipdb-5k.txt` via `VERYL_EDA_CHIPDB`.
- Command examples must use `--release` builds (debug is 10–100× slower and misleading).
- Chapters use mermaid flowcharts and tables of real command output; keep that style.
- Don't confuse this book repo with the tool repo: source code like `elab.rs`, `pnr/`, `build.sh`, `test.sh` is referenced from here but does not exist in this repo.
