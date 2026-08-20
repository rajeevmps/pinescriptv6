# Pine Script® v6 API reference

The strict API dictionary — every built-in variable, constant, function, keyword,
type, operator, and annotation in Pine Script v6.

**Source:** [Pine Script® v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/)

## Files

| File | Contents | Entries |
| --- | --- | --- |
| [`full-reference.md`](full-reference.md) | Every entry in one file, grouped by section. Use this for full-text search. | 884 |
| [`variables.md`](variables.md) | Built-in read-only variables (`close`, `bar_index`, `syminfo.*`, `barstate.*`) | 160 |
| [`constants.md`](constants.md) | Named constants (`color.red`, `shape.triangleup`, `plot.style_columns`) | 204 |
| [`keywords.md`](keywords.md) | Language keywords (`if`, `for`, `var`, `method`, `enum`, `export`) | 15 |
| [`types.md`](types.md) | Type system entries (`int`, `series`, `array`, `chart.point`) | 18 |
| [`operators.md`](operators.md) | Operators (`:=`, `[]`, `?:`, `==`, `and`) | 20 |
| [`annotations.md`](annotations.md) | Compiler annotations (`//@version`, `//@function`, `//@param`) | 10 |
| [`functions/ta.md`](functions/ta.md) | Technical analysis — the `ta.*` namespace | 59 |
| [`functions/strategy.md`](functions/strategy.md) | Backtesting — `strategy()` and the `strategy.*` namespace | 48 |
| [`functions/request.md`](functions/request.md) | External data — `request.*`, `ticker.*`, `syminfo.*` | 21 |
| [`functions/collections.md`](functions/collections.md) | `array.*`, `matrix.*`, `map.*` | 115 |
| [`functions/drawing.md`](functions/drawing.md) | `plot*`, `fill`, `hline`, `box.*`, `line.*`, `label.*`, `polyline.*`, `table.*` | 120 |
| [`functions/general.md`](functions/general.md) | `math.*`, `str.*`, `input.*`, `color.*`, time, alerts, `log.*`, declarations | 94 |

Every one of the 457 functions appears in exactly one `functions/` file.

## Entry anatomy

A function entry carries a description, a **Syntax** block, an **Arguments** list,
and then `Returns` / `Remarks` / `Code Example` where the reference provides them:

````markdown
## ta.rsi()

Relative strength index. It is calculated using the ta.rma() of upward and
downward changes of source over the last length bars.

### Syntax

```pine
ta.rsi(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*simple int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot).
Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.rsi).*

### Returns
Relative strength index.
````

## Provenance — read this before trusting a signature

The reference manual at tradingview.com is rendered client-side and cannot be
scraped page by page, so this directory is assembled from three sources. Each
entry states which one its signature came from.

| Part of an entry | Source | Currency |
| --- | --- | --- |
| Description, Returns, Remarks, Code Example | Official v6 reference manual snapshot | Current — includes v6 additions such as `backadjustment.*`, `text.format_none`, `box.set_xloc()` |
| **Syntax** for 53 identifiers | Signature blocks printed in the official v6 User Manual pages in this repository | Current — e.g. `plot()` shows all 16 parameters, `request.security()` includes `calc_bars_count` |
| **Syntax** for the remaining ~398, and **all Arguments** | TradingView's Pine Editor docs data (`pineDocs.json`), via a public mirror | **Early-v6 snapshot** — a parameter added to a function after that snapshot will be missing |

The editor data was cross-checked against the official text before being merged:
of 797 entries present in both, 735 descriptions matched closely, and the
mismatches were all cases where the official snapshot carried *newer* wording.
That is why the official text is kept as primary and only Syntax/Arguments are
taken from the editor data.

**Practical rule:** treat a signature marked *"official v6 User Manual"* as
authoritative. Treat one marked *"early-v6 snapshot"* as correct for the parameters
it lists, but possibly incomplete at the tail end of the parameter list. When a
call fails on an argument the signature does not mention, check the
[live reference manual](https://www.tradingview.com/pine-script-reference/v6/).

## Known gaps

**451 of 457 functions have a signature.** These six do not — they postdate the
editor snapshot and are not covered by a User Manual signature block:
`box.set_text_formatting()`, `box.set_xloc()`, `input.enum()`,
`label.set_text_formatting()`, `ta.rci()`, `table.cell_set_text_formatting()`.
Their descriptions and examples are present.

**25 newer entries are absent entirely.** Cross-checking against every
`pine-script-reference/v6/#…` anchor linked from the 77 User Manual pages
(808 distinct anchors) found these missing:

- **Footprint data** (new in v6): `request.footprint()`, `footprint.buy_volume()`,
  `footprint.sell_volume()`, `footprint.total_volume()`, `footprint.delta()`,
  `footprint.poc()`, `footprint.vah()`, `footprint.val()`, `footprint.rows()`,
  `footprint.get_row_by_price()`, and the `volume_row.*` accessors
  (`buy_volume`, `sell_volume`, `total_volume`, `delta`, `up_price`,
  `down_price`, `has_buy_imbalance`, `has_sell_imbalance`)
- **Types:** `footprint`, `volume_row`
- **Variables:** `syminfo.isin`
- **Constants:** `plot.linestyle_solid`, `plot.linestyle_dashed`, `plot.linestyle_dotted`
- **Operators:** `=`

The remaining 783 of 808 linked anchors resolve to an entry here. Footprint
functions are described in [`../release-notes.md`](../release-notes.md) under
January 2026.

For narrative explanations of how any of this fits together, start from the
[User Manual](../LLM_MANIFEST.md) rather than here.
