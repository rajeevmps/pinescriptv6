# Pine Script® v6 Documentation Manifest

**Purpose:** a directory map for LLMs and RAG pipelines. Identify the user's intent,
locate the file below, retrieve *only* that file.

**Contents:** all 77 pages of the official
[Pine Script® v6 User Manual](https://www.tradingview.com/pine-script-docs/welcome/)
plus the [API reference dictionary](reference/README.md). Retrieved 2026-08-20.
Every page carries its source URL in an HTML comment at the top.

**Always enforce `//@version=6`.** If an identifier is not in
[`reference/`](reference/README.md), do not invent it.

---

## 0. Start here

| File | When to read it |
| --- | --- |
| [`welcome.md`](welcome.md) | What Pine Script is, at a glance |
| [`primer/first-steps.md`](primer/first-steps.md) | Absolute beginner orientation |
| [`primer/first-indicator.md`](primer/first-indicator.md) | Building a first working indicator |
| [`primer/next-steps.md`](primer/next-steps.md) | Where to go after the first script |

## 1. Language mechanics

*Read these when the question is about how the language itself behaves — execution
order, types, scoping, control flow, or data structures.*

| File | Keywords |
| --- | --- |
| [`language/execution-model.md`](language/execution-model.md) | bar-by-bar execution, historical vs realtime, rollback, `calc_on_every_tick` |
| [`language/type-system.md`](language/type-system.md) | `const`/`input`/`simple`/`series`, qualifiers, auto-casting, `na` |
| [`language/script-structure.md`](language/script-structure.md) | script anatomy, comments, line wrapping, compiler directives |
| [`language/identifiers.md`](language/identifiers.md) | naming rules, camelCase vs SNAKE_CASE |
| [`language/declaration-statements.md`](language/declaration-statements.md) | `indicator()`, `strategy()`, `library()` |
| [`language/variable-declarations.md`](language/variable-declarations.md) | `var`, `varip`, `:=`, declaration modes, scope |
| [`language/operators.md`](language/operators.md) | arithmetic, comparison, logical, `[]` history-reference, `?:` |
| [`language/conditional-structures.md`](language/conditional-structures.md) | `if`, `switch`, as statements and as expressions |
| [`language/loops.md`](language/loops.md) | `for`, `for...in`, `while`, `break`, `continue` |
| [`language/built-ins.md`](language/built-ins.md) | how namespaces work, built-in variables vs functions |
| [`language/user-defined-functions.md`](language/user-defined-functions.md) | `=>`, single-line and multi-line functions, scope |
| [`language/objects.md`](language/objects.md) | user-defined types (`type`), `new()`, fields, `na` objects |
| [`language/enums.md`](language/enums.md) | `enum`, enum fields, `input.enum()` |
| [`language/methods.md`](language/methods.md) | built-in and user-defined `method`, dot-notation calls |
| [`language/arrays.md`](language/arrays.md) | `array.*`, declaration, looping, history-referencing |
| [`language/matrices.md`](language/matrices.md) | `matrix.*`, rows/columns, linear algebra |
| [`language/maps.md`](language/maps.md) | `map.*`, key/value pairs, `map.put`, `map.get` |

## 2. Visual output

*Read these when the question is about what appears on the chart.*

| File | Keywords |
| --- | --- |
| [`visuals/overview.md`](visuals/overview.md) | which drawing tool to reach for; limits on drawing counts |
| [`visuals/plots.md`](visuals/plots.md) | `plot()` — every parameter, styles, offsets, scale |
| [`visuals/fills.md`](visuals/fills.md) | `fill()`, gradient fills, fills between plots and hlines |
| [`visuals/levels.md`](visuals/levels.md) | `hline()`, horizontal levels |
| [`visuals/backgrounds.md`](visuals/backgrounds.md) | `bgcolor()` |
| [`visuals/bar-coloring.md`](visuals/bar-coloring.md) | `barcolor()` |
| [`visuals/bar-plotting.md`](visuals/bar-plotting.md) | `plotbar()`, `plotcandle()` |
| [`visuals/colors.md`](visuals/colors.md) | `color.new()`, `color.rgb()`, `color.from_gradient()`, transparency |
| [`visuals/lines-and-boxes.md`](visuals/lines-and-boxes.md) | `line.*`, `box.*`, `polyline.*`, `linefill.*` |
| [`visuals/text-and-shapes.md`](visuals/text-and-shapes.md) | `label.*`, `plotshape()`, `plotchar()`, `plotarrow()` |
| [`visuals/tables.md`](visuals/tables.md) | `table.*`, positioning, cell formatting |

## 3. Concepts

*Read these for feature-level "how do I do X" questions.*

| File | Keywords |
| --- | --- |
| [`concepts/alerts.md`](concepts/alerts.md) | `alert()`, `alertcondition()`, order-fill events, placeholders |
| [`concepts/bar-states.md`](concepts/bar-states.md) | `barstate.isfirst`, `islast`, `isrealtime`, `isconfirmed` |
| [`concepts/chart-information.md`](concepts/chart-information.md) | `syminfo.*`, `timeframe.*`, `chart.*`, session info |
| [`concepts/inputs.md`](concepts/inputs.md) | `input.int()`, `input.source()`, `input.timeframe()`, groups, inline, tooltips |
| [`concepts/libraries.md`](concepts/libraries.md) | `library()`, `export`, `import`, versioning |
| [`concepts/non-standard-charts-data.md`](concepts/non-standard-charts-data.md) | Heikin Ashi, Renko, Kagi, `ticker.*` |
| [`concepts/other-timeframes-and-data.md`](concepts/other-timeframes-and-data.md) | `request.security()`, `request.financial()`, MTF, lookahead |
| [`concepts/repainting.md`](concepts/repainting.md) | why values change, `barmerge.*`, realtime vs historical |
| [`concepts/sessions.md`](concepts/sessions.md) | session strings, `time()` with sessions, RTH/ETH |
| [`concepts/strategies.md`](concepts/strategies.md) | broker emulator, order types, position sizing, strategy report |
| [`concepts/strings.md`](concepts/strings.md) | `str.format()`, `str.tostring()`, concatenation, formatting |
| [`concepts/time.md`](concepts/time.md) | timestamps, timezones, `time()`, `timestamp()`, date arithmetic |
| [`concepts/timeframes.md`](concepts/timeframes.md) | timeframe strings, comparing timeframes, `timeframe.in_seconds()` |

## 4. Writing better scripts

| File | Keywords |
| --- | --- |
| [`writing/style-guide.md`](writing/style-guide.md) | naming, spacing, script organization |
| [`writing/debugging.md`](writing/debugging.md) | `log.*`, plotting intermediate values, labels, Pine Logs |
| [`writing/profiling-and-optimization.md`](writing/profiling-and-optimization.md) | Pine Profiler, runtime cost, memory |
| [`writing/publishing.md`](writing/publishing.md) | house rules, script descriptions, publishing workflow |
| [`writing/limitations.md`](writing/limitations.md) | plot counts, `max_bars_back`, loop limits, script size, run time |

## 5. Errors and warnings

*Read these when the user pastes a compiler or runtime error.*

- [`errors/overview.md`](errors/overview.md) — how error codes are structured
- [`errors/CE10101.md`](errors/CE10101.md), [`errors/CE10117.md`](errors/CE10117.md) — compile errors
- [`errors/CW10003.md`](errors/CW10003.md) — compile warning
- [`errors/RE10139.md`](errors/RE10139.md), [`errors/RE10143.md`](errors/RE10143.md) — runtime errors
- [`errors/legacy-error-messages.md`](errors/legacy-error-messages.md) — the retired "Error messages" page.
  Covers nine errors the coded pages do not yet document ("if statement is too long",
  "Script requesting too many securities", "Loop is too long", "Script has too many
  local variables", "Memory limits exceeded", and others). Check here when an error
  message has no `CE`/`CW`/`RE` code.

## 6. FAQ

*Task-shaped recipes straight from TradingView. Often the fastest answer to
"how do I …" questions.*

[`faq/general.md`](faq/general.md) ·
[`faq/programming.md`](faq/programming.md) ·
[`faq/techniques.md`](faq/techniques.md) ·
[`faq/indicators.md`](faq/indicators.md) ·
[`faq/strategies.md`](faq/strategies.md) ·
[`faq/alerts.md`](faq/alerts.md) ·
[`faq/visuals.md`](faq/visuals.md) ·
[`faq/data-structures.md`](faq/data-structures.md) ·
[`faq/functions.md`](faq/functions.md) ·
[`faq/variables-and-operators.md`](faq/variables-and-operators.md) ·
[`faq/strings-and-formatting.md`](faq/strings-and-formatting.md) ·
[`faq/times-dates-and-sessions.md`](faq/times-dates-and-sessions.md) ·
[`faq/other-data-and-timeframes.md`](faq/other-data-and-timeframes.md)

## 7. API reference (the dictionary)

See [`reference/README.md`](reference/README.md) for the full breakdown, coverage
details, and how to refresh it.

- [`reference/variables.md`](reference/variables.md) — `close`, `bar_index`, `syminfo.*`
- [`reference/constants.md`](reference/constants.md) — `color.red`, `shape.*`, `plot.style_*`
- [`reference/keywords.md`](reference/keywords.md) · [`reference/types.md`](reference/types.md) · [`reference/operators.md`](reference/operators.md) · [`reference/annotations.md`](reference/annotations.md)
- [`reference/functions/ta.md`](reference/functions/ta.md) · [`strategy.md`](reference/functions/strategy.md) · [`request.md`](reference/functions/request.md) · [`collections.md`](reference/functions/collections.md) · [`drawing.md`](reference/functions/drawing.md) · [`general.md`](reference/functions/general.md)
- [`reference/full-reference.md`](reference/full-reference.md) — all 941 entries in one file

## 8. Version history and migration

- [`release-notes.md`](release-notes.md) — what changed, newest first
- [`migration-guides/to-pine-version-6.md`](migration-guides/to-pine-version-6.md) — v5 → v6 (the one that matters)
- [`migration-guides/overview.md`](migration-guides/overview.md) and the v5/v4/v3/v2 guides
- [`where-can-i-get-more-information.md`](where-can-i-get-more-information.md) — official community resources

---

## Routing logic

| User asks | Retrieve |
| --- | --- |
| "Write an RSI indicator" | `reference/functions/ta.md` + `visuals/plots.md` |
| "Moving average crossover strategy" | `reference/functions/ta.md` + `concepts/strategies.md` |
| "Draw a box around the last 10 bars" | `visuals/lines-and-boxes.md` + `reference/functions/drawing.md` |
| "Why does my variable reset every bar?" | `language/variable-declarations.md` + `language/execution-model.md` |
| "My indicator repaints" | `concepts/repainting.md` + `concepts/other-timeframes-and-data.md` |
| "Higher-timeframe data" | `concepts/other-timeframes-and-data.md` + `concepts/timeframes.md` |
| "Send an alert with the price" | `concepts/alerts.md` + `concepts/strings.md` |
| "Show a stats panel on the chart" | `visuals/tables.md` |
| "Store values across bars" | `language/arrays.md` or `language/maps.md` |
| "Convert my v5 script" | `migration-guides/to-pine-version-6.md` |
| Pastes a compile/runtime error | `errors/overview.md`, then the specific code |
| "How many plots can I have?" | `writing/limitations.md` |
| "My script is too slow" | `writing/profiling-and-optimization.md` |
