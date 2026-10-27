# veryl2chip-book

[veryl2chip](https://github.com/ccc-eda/veryl2chip) 的書籍與使用手冊：一本講解 EDA
（電子設計自動化）原理的書，以 veryl2chip 的 Rust 原始碼作為貫穿全書的實作案例，
另附一份由淺入深的使用手冊。

veryl2chip 本身是一條從 Veryl HDL 到晶片的完整開源工具鏈：
模擬 → 邏輯綜合 → FPGA（iCE40 / ECP5，含自製佈局繞線）→ ASIC（SKY130 開源 PDK，到 GDS）。

## 本倉庫內容

| 目錄 | 內容 |
|---|---|
| [`book/`](book/) | 《從 HDL 到晶片：EDA 原理與 veryl2chip 實作》，約 60 章。目錄見 [book/README.md](book/README.md) |
| [`manual/`](manual/) | 使用手冊（安裝、`v2c` 各子命令、開發與驗證），見 [manual/README.md](manual/README.md) |
| [`code/01-counter/`](code/01-counter/) | 貫穿全書的計數器實例：`counter.veryl` 與 `v2c` 產生的所有輸出（`.json/.v/.pcf/.bin/.gds/.def`、`wave.vcd`） |
| `_doc/note/` | 作者的私人筆記，不屬於書籍內容 |

## 閱讀方式

純 Markdown，不需建置。建議從 [book/README.md](book/README.md) 的目錄進入，
第 1 章給閱讀路線；只想上手工具的人直接看 [manual/](manual/)。

書中實驗需要安裝 `v2c`，見 [manual/02-install.md](manual/02-install.md)；
工具原始碼與 `examples/` 在 [veryl2chip 本體倉庫](https://github.com/ccc-eda/veryl2chip)。
