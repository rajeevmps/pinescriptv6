# Pine Script® v6 API reference

The strict API dictionary — every built-in variable, constant, function, keyword,
type, operator, and annotation in Pine Script v6.

**941 entries**, extracted from the rendered
[Pine Script® v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/)
on 2026-08-20. Single source, no third-party data.

## Files

| File | Contents | Entries |
| --- | --- | --- |
| [`full-reference.md`](full-reference.md) | Every entry in one file, grouped by section. Use this for full-text search. | 941 |
| [`variables.md`](variables.md) | Built-in read-only variables (`close`, `bar_index`, `syminfo.*`, `barstate.*`) | 161 |
| [`constants.md`](constants.md) | Named constants (`color.red`, `shape.triangleup`, `plot.style_columns`) | 239 |
| [`keywords.md`](keywords.md) | Language keywords (`if`, `for`, `var`, `method`, `enum`, `export`) | 15 |
| [`types.md`](types.md) | Type system entries (`int`, `series`, `array`, `footprint`, `volume_row`) | 20 |
| [`operators.md`](operators.md) | Operators (`=`, `:=`, `[]`, `?:`, `==`, `and`) | 21 |
| [`annotations.md`](annotations.md) | Compiler annotations (`//@version`, `//@function`, `//@param`) | 10 |
| [`functions/ta.md`](functions/ta.md) | Technical analysis — the `ta.*` namespace | 59 |
| [`functions/strategy.md`](functions/strategy.md) | Backtesting — `strategy()` and the `strategy.*` namespace | 48 |
| [`functions/request.md`](functions/request.md) | External data — `request.*`, `ticker.*`, `syminfo.*`, `footprint.*`, `volume_row.*` | 39 |
| [`functions/collections.md`](functions/collections.md) | `array.*`, `matrix.*`, `map.*` | 115 |
| [`functions/drawing.md`](functions/drawing.md) | `plot*`, `fill`, `hline`, `box.*`, `line.*`, `label.*`, `polyline.*`, `table.*` | 120 |
| [`functions/general.md`](functions/general.md) | `math.*`, `str.*`, `input.*`, `color.*`, time, alerts, `log.*`, declarations | 94 |

Every one of the 475 functions appears in exactly one `functions/` file.

## Coverage

- **475 / 475 functions carry an official signature.** 473 also carry a full
  per-argument table; the two without take no arguments.
- **269 functions include a runnable code example**, copied verbatim from the manual.
- **All 808 reference anchors linked from the 77 User Manual pages resolve** to an
  entry here — no dangling cross-references.

## Entry anatomy

~~~markdown
## ta.rsi()
Relative strength index. It is calculated using the ta.rma() of upward and
downward changes of source over the last length bars.

### Syntax
```pine
ta.rsi(source, length) → series float
```

### Arguments
- `source` (*series int/float*) — Series of values to process.
- `length` (*simple int*) — Number of bars (length).

### Example
```pine
//@version=6
indicator("ta.rsi")
plot(ta.rsi(close, 7))
```

### Returns
Relative strength index.

### Remarks
na values in the source series are ignored; the function calculates on the
length quantity of non-na values.

### See also
`ta.rma()`
~~~

Sections appear only when the manual provides them. `Type` replaces `Syntax`
on variables and constants.

## Keeping it current

The reference manual is rendered client-side, so it cannot be fetched with an
ordinary HTTP request — the page returns an empty shell. To refresh:

1. Open <https://www.tradingview.com/pine-script-reference/v6/> in a browser and
   let it finish rendering.
2. Save it with `Ctrl+S` as **Webpage, Single File (.mhtml)**.
3. Re-run the extraction against the saved file.

Compare the entry count against the 941 recorded here to see whether TradingView
has shipped anything new. For narrative explanations rather than lookups, start
from the [User Manual](../LLM_MANIFEST.md).
