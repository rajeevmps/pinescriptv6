# Pine Script® language reference manual

# Variables 

---

## ask

The ask price at the time of the current tick, which represents the lowest price an active seller will accept for the instrument at its current value. This information is available only on the "1T" timeframe. On other timeframes, the variable's value is na.

**Type:** series float

### Remarks
If the bid/ask values change since the last tick but no new trades are made, these changes will not be reflected in the value of this variable. It is only updated on new ticks.

---

## bar_index

**Type:** series int

Current bar index. Numbering is zero-based, index of the first bar is 0.

### Remarks
Note that bar_index has replaced n variable in version 4. Note that bar indexing starts from 0 on the first historical bar. Please note that using this variable/function can cause indicator repainting.

### Code Example
```pine
//@version=6
indicator("bar_index")
plot(bar_index)
plot(bar_index > 5000 ? close : 0)
```

---

## barstate.isconfirmed

**Type:** series bool

Returns true if the script is calculating the last (closing) update of the current bar. The next script calculation will be on the new bar data.

### Remarks
Pine Script® code that uses this variable could calculate differently on history and real-time data. It is NOT recommended to use barstate.isconfirmed in request.security expression. Its value requested from request.security is unpredictable. Please note that using this variable/function can cause indicator repainting.

---

## barstate.isfirst

**Type:** series bool

Returns true if current bar is first bar in barset, false otherwise.

### Remarks
Pine Script® code that uses this variable could calculate differently on history and real-time data. Please note that using this variable/function can cause indicator repainting.

---

## barstate.ishistory

**Type:** series bool

Returns true if current bar is a historical bar, false otherwise.

### Remarks
Pine Script® code that uses this variable could calculate differently on history and real-time data. Please note that using this variable/function can cause indicator repainting.

---

## barstate.islast

**Type:** series bool

Returns true if current bar is the last bar in barset, false otherwise. This condition is true for all real-time bars in barset.

### Remarks
Pine Script® code that uses this variable could calculate differently on history and real-time data. Please note that using this variable/function can cause indicator repainting.

---

## barstate.islastconfirmedhistory

**Type:** series bool

Returns true if script is executing on the dataset's last bar when market is closed, or script is executing on the bar immediately preceding the real-time bar, if market is open. Returns false otherwise.

### Remarks
Pine Script® code that uses this variable could calculate differently on history and real-time data. Please note that using this variable/function can cause indicator repainting.

---

## barstate.isnew

**Type:** series bool

Returns true if script is currently calculating on new bar, false otherwise. This variable is true when calculating on historical bars or on first update of a newly generated real-time bar.

### Remarks
Pine Script® code that uses this variable could calculate differently on history and real-time data. Please note that using this variable/function can cause indicator repainting.

---

## barstate.isrealtime

**Type:** series bool

Returns true if current bar is a real-time bar, false otherwise.

### Remarks
Pine Script® code that uses this variable could calculate differently on history and real-time data. Please note that using this variable/function can cause indicator repainting.

---

## bid

**Type:** series float

The bid price at the time of the current tick, which represents the highest price an active buyer is willing to pay for the instrument at its current value. This information is available only on the "1T" timeframe. On other timeframes, the variable's value is na.

### Remarks
If the bid/ask values change since the last tick but no new trades are made, these changes will not be reflected in the value of this variable. It is only updated on new ticks.

---

## box.all

**Type:** array<box>

Returns an array filled with all the current boxes drawn by the script.

### Remarks
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.

### Code Example
```pine
//@version=6
indicator("box.all")
//delete all boxes
box.new(time, open, time + 60 * 60 * 24, close, xloc=xloc.bar_time, border_style=line.style_dashed)
a_allBoxes = box.all
if array.size(a_allBoxes) > 0
    for i = 0 to array.size(a_allBoxes) - 1
        box.delete(array.get(a_allBoxes, i))
```

---

## chart.bg_color

**Type:** input color

Returns the color of the chart's background from the "Chart settings/Appearance/Background" field. When a gradient is selected, the middle point of the gradient is returned.

---

## chart.fg_color

**Type:** input color

Returns a color providing optimal contrast with chart.bg_color.

---

## chart.is_heikinashi

**Type:** simple bool

### Returns
Returns true if the chart type is Heikin Ashi, false otherwise.

---

## chart.is_kagi

**Type:** simple bool

### Returns
Returns true if the chart type is Kagi, false otherwise.

---

## chart.is_linebreak

**Type:** simple bool

### Returns
Returns true if the chart type is Line break, false otherwise.

---

## chart.is_pnf

**Type:** simple bool

### Returns
Returns true if the chart type is Point & figure, false otherwise.

---

## chart.is_range

**Type:** simple bool

### Returns
Returns true if the chart type is Range, false otherwise.

---

## chart.is_renko

**Type:** simple bool

### Returns
Returns true if the chart type is Renko, false otherwise.

---

## chart.is_standard

**Type:** simple bool

### Returns
Returns true if the chart type is not one of the following: Renko, Kagi, Line break, Point & figure, Range, Heikin Ashi; false otherwise.

---

## chart.left_visible_bar_time

**Type:** input int

The time of the leftmost bar currently visible on the chart.

### Remarks
Scripts using this variable will automatically re-execute when its value updates to reflect changes in the chart, which can be caused by users scrolling the chart, or new real-time bars. Alerts created on a script that includes this variable will only use the value assigned to the variable at the moment of the alert's creation, regardless of whether the value changes afterward, which may lead to repainting.

---

## chart.right_visible_bar_time

**Type:** input int

The time of the rightmost bar currently visible on the chart.

### Remarks
Scripts using this variable will automatically re-execute when its value updates to reflect changes in the chart, which can be caused by users scrolling the chart, or new real-time bars. Alerts created on a script that includes this variable will only use the value assigned to the variable at the moment of the alert's creation, regardless of whether the value changes afterward, which may lead to repainting.

---

## close

**Type:** series float

Close price of the current bar when it has closed, or last traded price of a yet incomplete, realtime bar.

### Remarks
Previous values may be accessed with square brackets operator [], e.g. close[1], close[2].

---

## dayofmonth

**Type:** series int

Date of current bar time in exchange timezone.

### Syntax

```pine
dayofmonth(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Note that this variable returns the day based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the day of the trading day.

---

## dayofweek

**Type:** series int

Day of week for current bar time in exchange timezone.

### Syntax

```pine
dayofweek(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Note that this variable returns the day based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the day of the trading day. You can use dayofweek.sunday, dayofweek.monday, dayofweek.tuesday, dayofweek.wednesday, dayofweek.thursday, dayofweek.friday and dayofweek.saturday variables for comparisons.

---

## dividends.future_amount

**Type:** series float

Returns the payment amount of the upcoming dividend in the currency of the current instrument, or na if this data isn't available.

### Remarks
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected Payment date of the next dividend.

---

## dividends.future_ex_date

**Type:** series int

Returns the Ex-dividend date (Ex-date) of the current instrument's next dividend payment, or na if this data isn't available. Ex-dividend date signifies when investors are no longer entitled to a payout from the most recent dividend. Only those who purchased shares before this day are entitled to the dividend payment.

### Returns
UNIX time, expressed in milliseconds.

### Remarks
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected Payment date of the next dividend.

---

## dividends.future_pay_date

**Type:** series int

Returns the Payment date (Pay date) of the current instrument's next dividend payment, or na if this data isn't available. Payment date signifies the day when eligible investors will receive the dividend payment.

### Returns
UNIX time, expressed in milliseconds.

### Remarks
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected Payment date of the next dividend.

---

## earnings.future_eps

**Type:** series float

Returns the estimated Earnings per Share of the next earnings report in the currency of the instrument, or na if this data isn't available.

### Remarks
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected time of the next earnings report.

---

## earnings.future_period_end_time

**Type:** series int

Checks the data for the next earnings report and returns the UNIX timestamp of the day when the financial period covered by those earnings ends, or na if this data isn't available.

### Returns
UNIX time, expressed in milliseconds.

### Remarks
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected time of the next earnings report.

---

## earnings.future_revenue

**Type:** series float

Returns the estimated Revenue of the next earnings report in the currency of the instrument, or na if this data isn't available.

### Remarks
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected time of the next earnings report.

---

## earnings.future_time

**Type:** series int

Returns a UNIX timestamp indicating the expected time of the next earnings report, or na if this data isn't available.

### Returns
UNIX time, expressed in milliseconds.

### Remarks
This value is only fetched once during the script's initial calculation. The variable will return the same value until the script is recalculated, even after the expected time of the next earnings report.

---

## high

**Type:** series float

Current high price.

### Remarks
Previous values may be accessed with square brackets operator [], e.g. high[1], high[2].

---

## hl2

**Type:** series float

Is a shortcut for (high + low)/2

---

## hlc3

**Type:** series float

Is a shortcut for (high + low + close)/3

---

## hlcc4

**Type:** series float

Is a shortcut for (high + low + close + close)/4

---

## hour

**Type:** series int

Current bar hour in exchange timezone.

---

### Syntax

```pine
hour(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

## label.all

**Type:** array<label>

Returns an array filled with all the current labels drawn by the script.

### Remarks
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.

### Code Example
```pine
//@version=6
indicator("label.all")
//delete all labels
label.new(bar_index, close)
a_allLabels = label.all
if array.size(a_allLabels) > 0
    for i = 0 to array.size(a_allLabels) - 1
        label.delete(array.get(a_allLabels, i))
```

---

## last_bar_index

**Type:** series int

Bar index of the last chart bar. Bar indices begin at zero on the first bar.

### Returns
Last historical bar index for closed markets, or the real-time bar index for open markets.

### Remarks
Please note that using this variable can cause indicator repainting.

### Code Example
```pine
//@version=6
strategy("Mark Last X Bars For Backtesting", overlay = true, calc_on_every_tick = true)
lastBarsFilterInput = input.int(100, "Bars Count:")
// Here, we store the 'last_bar_index' value that is known from the beginning of the script's calculation.
// The 'last_bar_index' will change when new real-time bars appear, so we declare 'lastbar' with the 'var' keyword.
var lastbar = last_bar_index
// Check if the current bar_index is 'lastBarsFilterInput' removed from the last bar on the chart, or the chart is traded in real-time.
allowedToTrade = (lastbar - bar_index <= lastBarsFilterInput) or barstate.isrealtime
bgcolor(allowedToTrade ? color.new(color.green, 80) : na)
```

---

## last_bar_time

**Type:** series int

Time in UNIX format of the last chart bar. It is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### Remarks
Please note that using this variable/function can cause indicator repainting. Note that this variable returns the timestamp based on the time of the bar's open.

---

## line.all

**Type:** array<line>

Returns an array filled with all the current lines drawn by the script.

### Remarks
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.

### Code Example
```pine
//@version=6
indicator("line.all")
//delete all lines
line.new(bar_index - 10, close, bar_index, close)
a_allLines = line.all
if array.size(a_allLines) > 0
    for i = 0 to array.size(a_allLines) - 1
        line.delete(array.get(a_allLines, i))
```

---

## linefill.all

**Type:** array<linefill>

Returns an array filled with all the current linefill objects drawn by the script.

### Remarks
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.

---

## low

**Type:** series float

Current low price.

### Remarks
Previous values may be accessed with square brackets operator [], e.g. low[1], low[2].

---

## minute

**Type:** series int

Current bar minute in exchange timezone.

---

### Syntax

```pine
minute(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

## month

**Type:** series int

Current bar month in exchange timezone.

### Syntax

```pine
month(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Note that this variable returns the month based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the month of the trading day.

---

## na

**Type:** simple na

A keyword signifying "not available", indicating that a variable has no assigned value.

### Syntax

```pine
na(x) → series bool
```

### Arguments

- `x` (*series any*) — Value to be tested.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Do not use this variable with comparison operators to test values for na, as it might lead to unexpected behavior. Instead, use the na function. Note that na can be used to initialize variables when the initialization statement also specifies the variable's type.

### Code Example
```pine
//@version=6
indicator("na")
// CORRECT
// Plot no value when on bars zero to nine. Plot `close` on other bars.
plot(bar_index < 10 ? na : close)
// CORRECT ALTERNATIVE
// Initialize `a` to `na`. Reassign `close` to `a` on bars 10 and later.
float a = na
if bar_index >= 10
    a := close
plot(a)

// INCORRECT
// Trying to test the preceding bar's `close` for `na`.
// The next line, if uncommented, will cause a compilation error, because direct comparison with `na` is not allowed.
// plot(close[1] == na ? close : close[1])
// CORRECT
// Use the `na()` function to test for `na`.
plot(na(close[1]) ? close : close[1])
// CORRECT ALTERNATIVE
// `nz()` tests `close[1]` for `na`. It returns `close[1]` if it is not `na`, and `close` if it is.
plot(nz(close[1], close))
```

---

## ohlc4

**Type:** series float

Is a shortcut for (open + high + low + close)/4

---

## open

**Type:** series float

Current open price.

### Remarks
Previous values may be accessed with square brackets operator [], e.g. open[1], open[2].

---

## polyline.all

**Type:** array<polyline>

Returns an array containing all current polyline instances drawn by the script.

### Remarks
The array is read-only. Index zero of the array references the ID of the oldest polyline object on the chart.

---

## second

**Type:** series int

Current bar second in exchange timezone.

---

### Syntax

```pine
second(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

## session.isfirstbar

**Type:** series bool

Returns true if the current bar is the first bar of the day's session, false otherwise. If extended session information is used, only returns true on the first bar of the pre-market bars.

### Code Example
```pine
//@version=6
strategy("`session.isfirstbar` Example", overlay = true)
longCondition = year >= 2022
// Place a long order at the `close` of the trading session's first bar.
if session.isfirstbar and longCondition 
    strategy.entry("Long", strategy.long)

// Close the long position at the `close` of the trading session's last bar.
if session.islastbar and barstate.isconfirmed
    strategy.close("Long", immediately = true)
```

---

## session.isfirstbar_regular

**Type:** series bool

Returns true on the first regular session bar of the day, false otherwise. The result is the same whether extended session information is used or not.

### Code Example
```pine
//@version=6
strategy("`session.isfirstbar_regular` Example", overlay = true)
longCondition = year >= 2022
// Place a long order at the `close` of the trading session's first bar.
if session.isfirstbar and longCondition
    strategy.entry("Long", strategy.long)
// Close the long position at the `close` of the trading session's last bar.
if session.islastbar_regular and barstate.isconfirmed
    strategy.close("Long", immediately = true)
```

---

## session.islastbar

**Type:** series bool

Returns true if the current bar is the last bar of the day's session, false otherwise. If extended session information is used, only returns true on the last bar of the post-market bars.

### Remarks
This variable is not guaranteed to return true once in every session because the last bar of the session might not exist if no trades occur during what should be the session's last bar. This variable is not guaranteed to work as expected on non-standard chart types, e.g., Renko.

### Code Example
```pine
//@version=6
strategy("`session.islastbar` Example", overlay = true)
longCondition = year >= 2022
// Place a long order at the `close` of the trading session's last bar.
// The position will enter on the `open` of next session's first bar.
if session.islastbar and longCondition
    strategy.entry("Long", strategy.long)
 // Close 'Long' position at the close of the last bar of the trading session
if session.islastbar and barstate.isconfirmed
    strategy.close("Long", immediately = true)
```

---

## session.islastbar_regular

**Type:** series bool

Returns true on the last regular session bar of the day, false otherwise. The result is the same whether extended session information is used or not.

### Remarks
This variable is not guaranteed to return true once in every session because the last bar of the session might not exist if no trades occur during what should be the session's last bar. This variable is not guaranteed to work as expected on non-standard chart types, e.g., Renko.

### Code Example
```pine
//@version=6
strategy("`session.islastbar_regular` Example", overlay = true)
longCondition = year >= 2022
// Place a long order at the `close` of the trading session's first bar.
if session.isfirstbar and longCondition
    strategy.entry("Long", strategy.long)
// Close the long position at the `close` of the trading session's last bar.
if session.islastbar_regular and barstate.isconfirmed
    strategy.close("Long", immediately = true)
```

---

## session.ismarket

**Type:** series bool

Returns true if the current bar is a part of the regular trading hours (i.e. market hours), false otherwise.

---

## session.ispostmarket

**Type:** series bool

Returns true if the current bar is a part of the post-market, false otherwise. On non-intraday charts always returns false.

---

## session.ispremarket

**Type:** series bool

Returns true if the current bar is a part of the pre-market, false otherwise. On non-intraday charts always returns false.

---

## strategy.account_currency

**Type:** simple string

Returns the currency used to calculate results, which can be set in the strategy's properties.

---

## strategy.avg_losing_trade

**Type:** series float

Returns the average amount of money lost per losing trade. Calculated as the sum of losses divided by the number of losing trades.

---

## strategy.avg_losing_trade_percent

**Type:** series float

Returns the average percentage loss per losing trade. Calculated as the sum of loss percentages divided by the number of losing trades.

---

## strategy.avg_trade

**Type:** series float

Returns the average amount of money gained or lost per trade. Calculated as the sum of all profits and losses divided by the number of closed trades.

---

## strategy.avg_trade_percent

**Type:** series float

Returns the average percentage gain or loss per trade. Calculated as the sum of all profit and loss percentages divided by the number of closed trades.

---

## strategy.avg_winning_trade

**Type:** series float

Returns the average amount of money gained per winning trade. Calculated as the sum of profits divided by the number of winning trades.

---

## strategy.avg_winning_trade_percent

**Type:** series float

Returns the average percentage gain per winning trade. Calculated as the sum of profit percentages divided by the number of winning trades.

---

## strategy.closedtrades

**Type:** series int

Number of trades, which were closed for the whole trading range.

---

## strategy.closedtrades.first_index

**Type:** series int

The index, or trade number, of the first (oldest) trade listed in the List of Trades. This number is usually zero. If more trades than the allowed limit have been closed, the oldest trades are removed, and this number is the index of the oldest remaining trade.

---

## strategy.equity

**Type:** series float

Current equity (strategy.initial_capital + strategy.netprofit + strategy.openprofit).

---

## strategy.eventrades

**Type:** series int

Number of breakeven trades for the whole trading range.

---

## strategy.grossloss

**Type:** series float

Total currency value of all completed losing trades.

---

## strategy.grossloss_percent

**Type:** series float

The total value of all completed losing trades, expressed as a percentage of the initial capital.

---

## strategy.grossprofit

**Type:** series float

Total currency value of all completed winning trades.

---

## strategy.grossprofit_percent

**Type:** series float

The total currency value of all completed winning trades, expressed as a percentage of the initial capital.

---

## strategy.initial_capital

**Type:** series float

The amount of initial capital set in the strategy properties.

---

## strategy.losstrades

**Type:** series int

Number of unprofitable trades for the whole trading range.

---

## strategy.margin_liquidation_price

**Type:** series float

When margin is used in a strategy, returns the price point where a simulated margin call will occur and liquidate enough of the position to meet the margin requirements.

### Remarks
The variable returns na if the strategy does not use margin, i.e., the strategy declaration statement does not specify an argument for the margin_long or margin_short parameter.

### Code Example
```pine
//@version=6
strategy("Margin call management", overlay = true, margin_long = 25, margin_short = 25, 
  default_qty_type = strategy.percent_of_equity, default_qty_value = 395)

float maFast = ta.sma(close, 14)
float maSlow = ta.sma(close, 28)

if ta.crossover(maFast, maSlow)
    strategy.entry("Long", strategy.long)

if ta.crossunder(maFast, maSlow)
    strategy.entry("Short", strategy.short)

changePercent(v1, v2) => 
    float result = (v1 - v2) * 100 / math.abs(v2)

// exit when we're 10% away from a margin call, to prevent it.
if math.abs(changePercent(close, strategy.margin_liquidation_price)) <= 10
    strategy.close("Long")
    strategy.close("Short")
```

---

## strategy.max_contracts_held_all

**Type:** series float

Maximum number of contracts/shares/lots/units in one trade for the whole trading range.

---

## strategy.max_contracts_held_long

**Type:** series float

Maximum number of contracts/shares/lots/units in one long trade for the whole trading range.

---

## strategy.max_contracts_held_short

**Type:** series float

Maximum number of contracts/shares/lots/units in one short trade for the whole trading range.

---

## strategy.max_drawdown

**Type:** series float

Maximum equity drawdown value for the whole trading range.

---

## strategy.max_drawdown_percent

**Type:** series float

The maximum equity drawdown value for the whole trading range, expressed as a percentage and calculated by formula: Lowest Value During Trade / (Entry Price x Quantity) * 100.

---

## strategy.max_runup

**Type:** series float

Maximum equity run-up value for the whole trading range.

---

## strategy.max_runup_percent

**Type:** series float

The maximum equity run-up value for the whole trading range, expressed as a percentage and calculated by formula: Highest Value During Trade / (Entry Price x Quantity) * 100.

---

## strategy.netprofit

**Type:** series float

Total currency value of all completed trades.

---

## strategy.netprofit_percent

**Type:** series float

The total value of all completed trades, expressed as a percentage of the initial capital.

---

## strategy.openprofit

**Type:** series float

Current unrealized profit or loss for all open positions.

---

## strategy.openprofit_percent

**Type:** series float

The current unrealized profit or loss for all open positions, expressed as a percentage and calculated by formula: openPL / realizedEquity * 100.

---

## strategy.opentrades

**Type:** series int

Number of market position entries, which were not closed and remain opened. If there is no open market position, 0 is returned.

---

## strategy.opentrades.capital_held

**Type:** series float

Returns the capital amount currently held by open trades.

### Remarks
This variable returns na if the strategy does not simulate funding trades with a portion of the hypothetical account, i.e., if the strategy function does not include nonzero margin_long or margin_short arguments.

### Code Example
```pine
//@version=6
strategy(
   "strategy.opentrades.capital_held example", overlay=false, margin_long=50, margin_short=50, 
   default_qty_type = strategy.percent_of_equity, default_qty_value = 100
 )

// Enter a short position on the first bar.
if barstate.isfirst
    strategy.entry("Short", strategy.short)

// Plot the capital held by the short position.
plot(strategy.opentrades.capital_held, "Capital held")
// Highlight the chart background if the position is completely closed by margin calls.
bgcolor(bar_index > 0 and strategy.opentrades.capital_held == 0 ? color.new(color.red, 60) : na)
```

---

## strategy.position_avg_price

**Type:** series float

Average entry price of current market position. If the market position is flat, 'NaN' is returned.

---

## strategy.position_entry_name

**Type:** series string

Name of the order that initially opened current market position.

---

## strategy.position_size

**Type:** series float

Direction and size of the current market position. If the value is > 0, the market position is long. If the value is < 0, the market position is short. The absolute value is the number of contracts/shares/lots/units in trade (position size).

---

## strategy.wintrades

**Type:** series int

Number of profitable trades for the whole trading range.

---

## syminfo.basecurrency

**Type:** simple string

Returns a string containing the code representing the symbol's base currency (i.e., the traded currency or coin) if the instrument is a Forex or Crypto pair or a derivative based on such a pair. Otherwise, it returns an empty string. For example, this variable returns "EUR" for "EURJPY", "BTC" for "BTCUSDT", "CAD" for "CME:6C1!", and "" for "NASDAQ:AAPL".

---

## syminfo.country

**Type:** simple string

Returns the two-letter code of the country where the symbol is traded, in the ISO 3166-1 alpha-2 format, or na if the exchange is not directly tied to a specific country. For example, on "NASDAQ:AAPL" it will return "US", on "LSE:AAPL" it will return "GB", and on "BITSTAMP:BTCUSD it will return na.

---

## syminfo.currency

**Type:** simple string

Returns a string containing the code representing the currency of the symbol's prices. For example, this variable returns "USD" for "NASDAQ:AAPL" and "JPY" for "EURJPY".

---

## syminfo.current_contract

**Type:** simple string

The ticker identifier of the underlying contract, if the current symbol is a continuous futures contract; na otherwise.

---

## syminfo.description

**Type:** simple string

Description for the current symbol.

---

## syminfo.employees

**Type:** simple int

The number of employees the company has.

### Code Example
```pine
//@version=6
indicator("syminfo simple")
//@variable A table containing information about a company's employees, shareholders, and shares.
var result_table = table.new(position = position.top_right, columns = 2, rows = 5, border_width = 1)
if barstate.islastconfirmedhistory
    // Add header cells
    table.cell(table_id = result_table, column = 0, row = 0, text = "name")
    table.cell(table_id = result_table, column = 1, row = 0, text = "value")
    // Add employee info cells.
    table.cell(table_id = result_table, column = 0, row = 1, text = "employees")
    table.cell(table_id = result_table, column = 1, row = 1, text = str.tostring(syminfo.employees))
    // Add shareholder cells.
    table.cell(table_id = result_table, column = 0, row = 2, text = "shareholders")
    table.cell(table_id = result_table, column = 1, row = 2, text = str.tostring(syminfo.shareholders))
    // Add float shares outstanding cells.
    table.cell(table_id = result_table, column = 0, row = 3, text = "shares_outstanding_float")
    table.cell(table_id = result_table, column = 1, row = 3, text = str.tostring(syminfo.shares_outstanding_float))
    // Add total shares outstanding cells.
    table.cell(table_id = result_table, column = 0, row = 4, text = "shares_outstanding_total")
    table.cell(table_id = result_table, column = 1, row = 4, text = str.tostring(syminfo.shares_outstanding_total))
```

---

## syminfo.expiration_date

**Type:** simple int

A UNIX timestamp representing the start of the last day of the current futures contract. This variable is only compatible with non-continuous futures symbols. On other symbols, it returns na.

---

## syminfo.industry

**Type:** simple string

Returns the industry of the symbol, or na if the symbol has no industry. Example: "Internet Software/Services", "Packaged software", "Integrated Oil", "Motor Vehicles", etc. These are the same values one can see in the chart's "Symbol info" window.

### Remarks
A sector is a broad section of the economy. An industry is a narrower classification. NASDAQ:CAT (Caterpillar, Inc.) for example, belongs to the "Producer Manufacturing" sector and the "Trucks/Construction/Farm Machinery" industry.

---

## syminfo.main_tickerid

**Type:** simple string

A ticker identifier representing the current chart's symbol. The value contains an exchange prefix and a symbol name, separated by a colon (e.g., "NASDAQ:AAPL"). It can also include information about data modifications such as dividend adjustment, non-standard chart type, currency conversion, etc. Unlike syminfo.tickerid, this variable's value does not change when used in the expression argument of a request.*() function call.

---

## syminfo.mincontract

**Type:** simple float

The smallest amount of the current symbol that can be traded. This limit is set by the exchange. For cryptocurrencies, it is often less than 1 token. For most other types of asset, it is often 1.

---

## syminfo.minmove

**Type:** simple int

Returns a whole number used to calculate the smallest increment between a symbol's price movements (syminfo.mintick). It is the numerator in the syminfo.mintick formula: syminfo.minmove / syminfo.pricescale = syminfo.mintick.

---

## syminfo.mintick

**Type:** simple float

Min tick value for the current symbol.

---

## syminfo.pointvalue

**Type:** simple float

Point value for the current symbol.

---

## syminfo.prefix

**Type:** simple string

Prefix of current symbol name (i.e. for 'CME_EOD:TICKER' prefix is 'CME_EOD').

### Syntax

```pine
syminfo.prefix(symbol) → series string
```

### Arguments

- `symbol` (*series string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL".

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("syminfo.prefix")

// If current chart symbol is 'BATS:MSFT' then syminfo.prefix is 'BATS'.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, text=syminfo.prefix)
```

---

## syminfo.pricescale

**Type:** simple int

Returns a whole number used to calculate the smallest increment between a symbol's price movements (syminfo.mintick). It is the denominator in the syminfo.mintick formula: syminfo.minmove / syminfo.pricescale = syminfo.mintick.

---

## syminfo.recommendations_buy

**Type:** series int

The number of analysts who gave the current symbol a "Buy" rating.

### Code Example
```pine
//@version=6
indicator("syminfo recommendations", overlay = true)
//@variable A table containing information about analyst recommendations.
var table ratings = table.new(position.top_right, 8, 2, frame_color = #000000)
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    // Add header cells.
    table.cell(ratings, 0, 0, "Start Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 0, "End Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 0, "Buy", bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 0, "Sell", bgcolor = color.maroon, text_color = #000000, text_size = size.large)
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor = color.red, text_color = #000000, text_size = size.large)
    table.cell(ratings, 6, 0, "Hold", bgcolor = color.orange, text_color = #000000, text_size = size.large)
    table.cell(ratings, 7, 0, "Total", bgcolor = color.silver, text_color = #000000, text_size = size.large)
    // Recommendation strings
    string startDate         = str.format_time(syminfo.recommendations_date, "yyyy-MM-dd")
    string endDate           = str.format_time(YTD, "yyyy-MM-dd")
    string buyRatings        = str.tostring(syminfo.recommendations_buy)
    string strongBuyRatings  = str.tostring(syminfo.recommendations_buy_strong)
    string sellRatings       = str.tostring(syminfo.recommendations_sell)
    string strongSellRatings = str.tostring(syminfo.recommendations_sell_strong)
    string holdRatings       = str.tostring(syminfo.recommendations_hold)
    string totalRatings      = str.tostring(syminfo.recommendations_total)
    // Add value cells
    table.cell(ratings, 0, 1, startDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 1, endDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 1, buyRatings, bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 1, sellRatings, bgcolor = color.maroon, text_color = #000000, text_size = size.large)
```

---

## syminfo.recommendations_buy_strong

**Type:** series int

The number of analysts who gave the current symbol a "Strong Buy" rating.

### Code Example
```pine
//@version=6
indicator("syminfo recommendations", overlay = true)
//@variable A table containing information about analyst recommendations.
var table ratings = table.new(position.top_right, 8, 2, frame_color = #000000)
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    // Add header cells.
    table.cell(ratings, 0, 0, "Start Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 0, "End Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 0, "Buy", bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 0, "Sell", bgcolor = color.maroon, text_color = #000000, text_size = size.large)
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor = color.red, text_color = #000000, text_size = size.large)
    table.cell(ratings, 6, 0, "Hold", bgcolor = color.orange, text_color = #000000, text_size = size.large)
    table.cell(ratings, 7, 0, "Total", bgcolor = color.silver, text_color = #000000, text_size = size.large)
    // Recommendation strings
    string startDate         = str.format_time(syminfo.recommendations_date, "yyyy-MM-dd")
    string endDate           = str.format_time(YTD, "yyyy-MM-dd")
    string buyRatings        = str.tostring(syminfo.recommendations_buy)
    string strongBuyRatings  = str.tostring(syminfo.recommendations_buy_strong)
    string sellRatings       = str.tostring(syminfo.recommendations_sell)
    string strongSellRatings = str.tostring(syminfo.recommendations_sell_strong)
    string holdRatings       = str.tostring(syminfo.recommendations_hold)
    string totalRatings      = str.tostring(syminfo.recommendations_total)
    // Add value cells
    table.cell(ratings, 0, 1, startDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 1, endDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 1, buyRatings, bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 1, sellRatings, bgcolor = color.maroon, text_color = #000000, text_size = size.large)
```

---

## syminfo.recommendations_date

**Type:** series int

The starting date of the last set of recommendations for the current symbol.

### Code Example
```pine
//@version=6
indicator("syminfo recommendations", overlay = true)
//@variable A table containing information about analyst recommendations.
var table ratings = table.new(position.top_right, 8, 2, frame_color = #000000)
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    // Add header cells.
    table.cell(ratings, 0, 0, "Start Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 0, "End Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 0, "Buy", bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 0, "Sell", bgcolor = color.maroon, text_color = #000000, text_size = size.large)
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor = color.red, text_color = #000000, text_size = size.large)
    table.cell(ratings, 6, 0, "Hold", bgcolor = color.orange, text_color = #000000, text_size = size.large)
    table.cell(ratings, 7, 0, "Total", bgcolor = color.silver, text_color = #000000, text_size = size.large)
    // Recommendation strings
    string startDate         = str.format_time(syminfo.recommendations_date, "yyyy-MM-dd")
    string endDate           = str.format_time(YTD, "yyyy-MM-dd")
    string buyRatings        = str.tostring(syminfo.recommendations_buy)
    string strongBuyRatings  = str.tostring(syminfo.recommendations_buy_strong)
    string sellRatings       = str.tostring(syminfo.recommendations_sell)
    string strongSellRatings = str.tostring(syminfo.recommendations_sell_strong)
    string holdRatings       = str.tostring(syminfo.recommendations_hold)
    string totalRatings      = str.tostring(syminfo.recommendations_total)
    // Add value cells
    table.cell(ratings, 0, 1, startDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 1, endDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 1, buyRatings, bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 1, sellRatings, bgcolor = color.maroon, text_color = #000000, text_size = size.large)
```

---

## syminfo.recommendations_hold

**Type:** series int

The number of analysts who gave the current symbol a "Hold" rating.

### Code Example
```pine
//@version=6
indicator("syminfo recommendations", overlay = true)
//@variable A table containing information about analyst recommendations.
var table ratings = table.new(position.top_right, 8, 2, frame_color = #000000)
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    // Add header cells.
    table.cell(ratings, 0, 0, "Start Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 0, "End Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 0, "Buy", bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 0, "Sell", bgcolor = color.maroon, text_color = #000000, text_size = size.large)
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor = color.red, text_color = #000000, text_size = size.large)
    table.cell(ratings, 6, 0, "Hold", bgcolor = color.orange, text_color = #000000, text_size = size.large)
    table.cell(ratings, 7, 0, "Total", bgcolor = color.silver, text_color = #000000, text_size = size.large)
    // Recommendation strings
    string startDate         = str.format_time(syminfo.recommendations_date, "yyyy-MM-dd")
    string endDate           = str.format_time(YTD, "yyyy-MM-dd")
    string buyRatings        = str.tostring(syminfo.recommendations_buy)
    string strongBuyRatings  = str.tostring(syminfo.recommendations_buy_strong)
    string sellRatings       = str.tostring(syminfo.recommendations_sell)
    string strongSellRatings = str.tostring(syminfo.recommendations_sell_strong)
    string holdRatings       = str.tostring(syminfo.recommendations_hold)
    string totalRatings      = str.tostring(syminfo.recommendations_total)
    // Add value cells
    table.cell(ratings, 0, 1, startDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 1, endDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 1, buyRatings, bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 1, sellRatings, bgcolor = color.maroon, text_color = #000000, text_size = size.large)
```

---

## syminfo.recommendations_sell

**Type:** series int

The number of analysts who gave the current symbol a "Sell" rating.

### Code Example
```pine
//@version=6
indicator("syminfo recommendations", overlay = true)
//@variable A table containing information about analyst recommendations.
var table ratings = table.new(position.top_right, 8, 2, frame_color = #000000)
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    // Add header cells.
    table.cell(ratings, 0, 0, "Start Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 0, "End Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 0, "Buy", bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 0, "Sell", bgcolor = color.maroon, text_color = #000000, text_size = size.large)
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor = color.red, text_color = #000000, text_size = size.large)
    table.cell(ratings, 6, 0, "Hold", bgcolor = color.orange, text_color = #000000, text_size = size.large)
    table.cell(ratings, 7, 0, "Total", bgcolor = color.silver, text_color = #000000, text_size = size.large)
    // Recommendation strings
    string startDate         = str.format_time(syminfo.recommendations_date, "yyyy-MM-dd")
    string endDate           = str.format_time(YTD, "yyyy-MM-dd")
    string buyRatings        = str.tostring(syminfo.recommendations_buy)
    string strongBuyRatings  = str.tostring(syminfo.recommendations_buy_strong)
    string sellRatings       = str.tostring(syminfo.recommendations_sell)
    string strongSellRatings = str.tostring(syminfo.recommendations_sell_strong)
    string holdRatings       = str.tostring(syminfo.recommendations_hold)
    string totalRatings      = str.tostring(syminfo.recommendations_total)
    // Add value cells
    table.cell(ratings, 0, 1, startDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 1, endDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 1, buyRatings, bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 1, sellRatings, bgcolor = color.maroon, text_color = #000000, text_size = size.large)
```

---

## syminfo.recommendations_sell_strong

**Type:** series int

The number of analysts who gave the current symbol a "Strong Sell" rating.

### Code Example
```pine
//@version=6
indicator("syminfo recommendations", overlay = true)
//@variable A table containing information about analyst recommendations.
var table ratings = table.new(position.top_right, 8, 2, frame_color = #000000)
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    // Add header cells.
    table.cell(ratings, 0, 0, "Start Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 0, "End Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 0, "Buy", bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 0, "Sell", bgcolor = color.maroon, text_color = #000000, text_size = size.large)
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor = color.red, text_color = #000000, text_size = size.large)
    table.cell(ratings, 6, 0, "Hold", bgcolor = color.orange, text_color = #000000, text_size = size.large)
    table.cell(ratings, 7, 0, "Total", bgcolor = color.silver, text_color = #000000, text_size = size.large)
    // Recommendation strings
    string startDate         = str.format_time(syminfo.recommendations_date, "yyyy-MM-dd")
    string endDate           = str.format_time(YTD, "yyyy-MM-dd")
    string buyRatings        = str.tostring(syminfo.recommendations_buy)
    string strongBuyRatings  = str.tostring(syminfo.recommendations_buy_strong)
    string sellRatings       = str.tostring(syminfo.recommendations_sell)
    string strongSellRatings = str.tostring(syminfo.recommendations_sell_strong)
    string holdRatings       = str.tostring(syminfo.recommendations_hold)
    string totalRatings      = str.tostring(syminfo.recommendations_total)
    // Add value cells
    table.cell(ratings, 0, 1, startDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 1, endDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 1, buyRatings, bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 1, sellRatings, bgcolor = color.maroon, text_color = #000000, text_size = size.large)
```

---

## syminfo.recommendations_total

**Type:** series int

The total number of recommendations for the current symbol.

### Code Example
```pine
//@version=6
indicator("syminfo recommendations", overlay = true)
//@variable A table containing information about analyst recommendations.
var table ratings = table.new(position.top_right, 8, 2, frame_color = #000000)
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    // Add header cells.
    table.cell(ratings, 0, 0, "Start Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 0, "End Date", bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 0, "Buy", bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 0, "Strong Buy", bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 0, "Sell", bgcolor = color.maroon, text_color = #000000, text_size = size.large)
    table.cell(ratings, 5, 0, "Strong Sell", bgcolor = color.red, text_color = #000000, text_size = size.large)
    table.cell(ratings, 6, 0, "Hold", bgcolor = color.orange, text_color = #000000, text_size = size.large)
    table.cell(ratings, 7, 0, "Total", bgcolor = color.silver, text_color = #000000, text_size = size.large)
    // Recommendation strings
    string startDate         = str.format_time(syminfo.recommendations_date, "yyyy-MM-dd")
    string endDate           = str.format_time(YTD, "yyyy-MM-dd")
    string buyRatings        = str.tostring(syminfo.recommendations_buy)
    string strongBuyRatings  = str.tostring(syminfo.recommendations_buy_strong)
    string sellRatings       = str.tostring(syminfo.recommendations_sell)
    string strongSellRatings = str.tostring(syminfo.recommendations_sell_strong)
    string holdRatings       = str.tostring(syminfo.recommendations_hold)
    string totalRatings      = str.tostring(syminfo.recommendations_total)
    // Add value cells
    table.cell(ratings, 0, 1, startDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 1, 1, endDate, bgcolor = color.gray, text_color = #000000, text_size = size.large)
    table.cell(ratings, 2, 1, buyRatings, bgcolor = color.teal, text_color = #000000, text_size = size.large)
    table.cell(ratings, 3, 1, strongBuyRatings, bgcolor = color.lime, text_color = #000000, text_size = size.large)
    table.cell(ratings, 4, 1, sellRatings, bgcolor = color.maroon, text_color = #000000, text_size = size.large)
```

---

## syminfo.root

**Type:** simple string

Root for derivatives like futures contract. For other symbols returns the same value as syminfo.ticker.

### Code Example
```pine
//@version=6
indicator("syminfo.root")

// If the current chart symbol is continuous futures ('ES1!'), it would display 'ES'.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, syminfo.root)
```

---

## syminfo.sector

**Type:** simple string

Returns the sector of the symbol, or na if the symbol has no sector. Example: "Electronic Technology", "Technology services", "Energy Minerals", "Consumer Durables", etc. These are the same values one can see in the chart's "Symbol info" window.

### Remarks
A sector is a broad section of the economy. An industry is a narrower classification. NASDAQ:CAT (Caterpillar, Inc.) for example, belongs to the "Producer Manufacturing" sector and the "Trucks/Construction/Farm Machinery" industry.

---

## syminfo.session

**Type:** simple string

Session type of the chart main series. Possible values are session.regular, session.extended.

---

## syminfo.shareholders

**Type:** simple int

The number of shareholders the company has.

### Code Example
```pine
//@version=6
indicator("syminfo simple")
//@variable A table containing information about a company's employees, shareholders, and shares.
var result_table = table.new(position = position.top_right, columns = 2, rows = 5, border_width = 1)
if barstate.islastconfirmedhistory
    // Add header cells
    table.cell(table_id = result_table, column = 0, row = 0, text = "name")
    table.cell(table_id = result_table, column = 1, row = 0, text = "value")
    // Add employee info cells.
    table.cell(table_id = result_table, column = 0, row = 1, text = "employees")
    table.cell(table_id = result_table, column = 1, row = 1, text = str.tostring(syminfo.employees))
    // Add shareholder cells.
    table.cell(table_id = result_table, column = 0, row = 2, text = "shareholders")
    table.cell(table_id = result_table, column = 1, row = 2, text = str.tostring(syminfo.shareholders))
    // Add float shares outstanding cells.
    table.cell(table_id = result_table, column = 0, row = 3, text = "shares_outstanding_float")
    table.cell(table_id = result_table, column = 1, row = 3, text = str.tostring(syminfo.shares_outstanding_float))
    // Add total shares outstanding cells.
    table.cell(table_id = result_table, column = 0, row = 4, text = "shares_outstanding_total")
    table.cell(table_id = result_table, column = 1, row = 4, text = str.tostring(syminfo.shares_outstanding_total))
```

---

## syminfo.shares_outstanding_float

**Type:** simple float

The total number of shares outstanding a company has available, excluding any of its restricted shares.

### Code Example
```pine
//@version=6
indicator("syminfo simple")
//@variable A table containing information about a company's employees, shareholders, and shares.
var result_table = table.new(position = position.top_right, columns = 2, rows = 5, border_width = 1)
if barstate.islastconfirmedhistory
    // Add header cells
    table.cell(table_id = result_table, column = 0, row = 0, text = "name")
    table.cell(table_id = result_table, column = 1, row = 0, text = "value")
    // Add employee info cells.
    table.cell(table_id = result_table, column = 0, row = 1, text = "employees")
    table.cell(table_id = result_table, column = 1, row = 1, text = str.tostring(syminfo.employees))
    // Add shareholder cells.
    table.cell(table_id = result_table, column = 0, row = 2, text = "shareholders")
    table.cell(table_id = result_table, column = 1, row = 2, text = str.tostring(syminfo.shareholders))
    // Add float shares outstanding cells.
    table.cell(table_id = result_table, column = 0, row = 3, text = "shares_outstanding_float")
    table.cell(table_id = result_table, column = 1, row = 3, text = str.tostring(syminfo.shares_outstanding_float))
    // Add total shares outstanding cells.
    table.cell(table_id = result_table, column = 0, row = 4, text = "shares_outstanding_total")
    table.cell(table_id = result_table, column = 1, row = 4, text = str.tostring(syminfo.shares_outstanding_total))
```

---

## syminfo.shares_outstanding_total

**Type:** simple int

The total number of shares outstanding a company has available, including restricted shares held by insiders, major shareholders, and employees.

### Code Example
```pine
//@version=6
indicator("syminfo simple")
//@variable A table containing information about a company's employees, shareholders, and shares.
var result_table = table.new(position = position.top_right, columns = 2, rows = 5, border_width = 1)
if barstate.islastconfirmedhistory
    // Add header cells
    table.cell(table_id = result_table, column = 0, row = 0, text = "name")
    table.cell(table_id = result_table, column = 1, row = 0, text = "value")
    // Add employee info cells.
    table.cell(table_id = result_table, column = 0, row = 1, text = "employees")
    table.cell(table_id = result_table, column = 1, row = 1, text = str.tostring(syminfo.employees))
    // Add shareholder cells.
    table.cell(table_id = result_table, column = 0, row = 2, text = "shareholders")
    table.cell(table_id = result_table, column = 1, row = 2, text = str.tostring(syminfo.shareholders))
    // Add float shares outstanding cells.
    table.cell(table_id = result_table, column = 0, row = 3, text = "shares_outstanding_float")
    table.cell(table_id = result_table, column = 1, row = 3, text = str.tostring(syminfo.shares_outstanding_float))
    // Add total shares outstanding cells.
    table.cell(table_id = result_table, column = 0, row = 4, text = "shares_outstanding_total")
    table.cell(table_id = result_table, column = 1, row = 4, text = str.tostring(syminfo.shares_outstanding_total))
```

---

## syminfo.target_price_average

**Type:** series float

The average of the last yearly price targets for the symbol predicted by analysts.

### Remarks
If analysts supply the targets when the market is closed, the variable can return na until the market opens.

### Code Example
```pine
//@version=6
indicator("syminfo target_price")
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    //@variable A line connecting the current `close` to the highest yearly price estimate.
    highLine = line.new(time, close, YTD, syminfo.target_price_high, color = color.green, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the lowest yearly price estimate.
    lowLine = line.new(time, close, YTD, syminfo.target_price_low, color = color.red, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the median yearly price estimate.
    medianLine = line.new(time, close, YTD, syminfo.target_price_median, color = color.gray, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the average yearly price estimate.
    averageLine = line.new(time, close, YTD, syminfo.target_price_average, color = color.orange, xloc = xloc.bar_time)
    // Fill the space between targets
    linefill.new(lowLine, medianLine, color.new(color.red, 90))
    linefill.new(medianLine, highLine, color.new(color.green, 90))
    // Create a label displaying the total number of analyst estimates.
    string estimatesText = str.format("Number of estimates: {0}", syminfo.target_price_estimates)
    label.new(bar_index, close, estimatesText, textcolor = color.white, size = size.large)
```

---

## syminfo.target_price_date

**Type:** series int

The starting date of the last price target prediction for the current symbol.

### Remarks
If analysts supply the targets when the market is closed, the variable can return na until the market opens.

### Code Example
```pine
//@version=6
indicator("syminfo target_price")
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    //@variable A line connecting the current `close` to the highest yearly price estimate.
    highLine = line.new(time, close, YTD, syminfo.target_price_high, color = color.green, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the lowest yearly price estimate.
    lowLine = line.new(time, close, YTD, syminfo.target_price_low, color = color.red, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the median yearly price estimate.
    medianLine = line.new(time, close, YTD, syminfo.target_price_median, color = color.gray, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the average yearly price estimate.
    averageLine = line.new(time, close, YTD, syminfo.target_price_average, color = color.orange, xloc = xloc.bar_time)
    // Fill the space between targets
    linefill.new(lowLine, medianLine, color.new(color.red, 90))
    linefill.new(medianLine, highLine, color.new(color.green, 90))
    // Create a label displaying the total number of analyst estimates.
    string estimatesText = str.format("Number of estimates: {0}", syminfo.target_price_estimates)
    label.new(bar_index, close, estimatesText, textcolor = color.white, size = size.large)
```

---

## syminfo.target_price_estimates

**Type:** series float

The latest total number of price target predictions for the current symbol.

### Remarks
If analysts supply the targets when the market is closed, the variable can return na until the market opens.

### Code Example
```pine
//@version=6
indicator("syminfo target_price")
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    //@variable A line connecting the current `close` to the highest yearly price estimate.
    highLine = line.new(time, close, YTD, syminfo.target_price_high, color = color.green, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the lowest yearly price estimate.
    lowLine = line.new(time, close, YTD, syminfo.target_price_low, color = color.red, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the median yearly price estimate.
    medianLine = line.new(time, close, YTD, syminfo.target_price_median, color = color.gray, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the average yearly price estimate.
    averageLine = line.new(time, close, YTD, syminfo.target_price_average, color = color.orange, xloc = xloc.bar_time)
    // Fill the space between targets
    linefill.new(lowLine, medianLine, color.new(color.red, 90))
    linefill.new(medianLine, highLine, color.new(color.green, 90))
    // Create a label displaying the total number of analyst estimates.
    string estimatesText = str.format("Number of estimates: {0}", syminfo.target_price_estimates)
    label.new(bar_index, close, estimatesText, textcolor = color.white, size = size.large)
```

---

## syminfo.target_price_high

**Type:** series float

The last highest yearly price target for the symbol predicted by analysts.

### Remarks
If analysts supply the targets when the market is closed, the variable can return na until the market opens.

### Code Example
```pine
//@version=6
indicator("syminfo target_price")
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    //@variable A line connecting the current `close` to the highest yearly price estimate.
    highLine = line.new(time, close, YTD, syminfo.target_price_high, color = color.green, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the lowest yearly price estimate.
    lowLine = line.new(time, close, YTD, syminfo.target_price_low, color = color.red, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the median yearly price estimate.
    medianLine = line.new(time, close, YTD, syminfo.target_price_median, color = color.gray, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the average yearly price estimate.
    averageLine = line.new(time, close, YTD, syminfo.target_price_average, color = color.orange, xloc = xloc.bar_time)
    // Fill the space between targets
    linefill.new(lowLine, medianLine, color.new(color.red, 90))
    linefill.new(medianLine, highLine, color.new(color.green, 90))
    // Create a label displaying the total number of analyst estimates.
    string estimatesText = str.format("Number of estimates: {0}", syminfo.target_price_estimates)
    label.new(bar_index, close, estimatesText, textcolor = color.white, size = size.large)
```

---

## syminfo.target_price_low

**Type:** series float

The last lowest yearly price target for the symbol predicted by analysts.

### Remarks
If analysts supply the targets when the market is closed, the variable can return na until the market opens.

### Code Example
```pine
//@version=6
indicator("syminfo target_price")
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    //@variable A line connecting the current `close` to the highest yearly price estimate.
    highLine = line.new(time, close, YTD, syminfo.target_price_high, color = color.green, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the lowest yearly price estimate.
    lowLine = line.new(time, close, YTD, syminfo.target_price_low, color = color.red, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the median yearly price estimate.
    medianLine = line.new(time, close, YTD, syminfo.target_price_median, color = color.gray, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the average yearly price estimate.
    averageLine = line.new(time, close, YTD, syminfo.target_price_average, color = color.orange, xloc = xloc.bar_time)
    // Fill the space between targets
    linefill.new(lowLine, medianLine, color.new(color.red, 90))
    linefill.new(medianLine, highLine, color.new(color.green, 90))
    // Create a label displaying the total number of analyst estimates.
    string estimatesText = str.format("Number of estimates: {0}", syminfo.target_price_estimates)
    label.new(bar_index, close, estimatesText, textcolor = color.white, size = size.large)
```

---

## syminfo.target_price_median

**Type:** series float

The median of the last yearly price targets for the symbol predicted by analysts.

### Remarks
If analysts supply the targets when the market is closed, the variable can return na until the market opens.

### Code Example
```pine
//@version=6
indicator("syminfo target_price")
if barstate.islastconfirmedhistory
    //@variable The time value one year from the date of the last analyst recommendations.
    int YTD = syminfo.target_price_date + timeframe.in_seconds("12M") * 1000
    //@variable A line connecting the current `close` to the highest yearly price estimate.
    highLine = line.new(time, close, YTD, syminfo.target_price_high, color = color.green, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the lowest yearly price estimate.
    lowLine = line.new(time, close, YTD, syminfo.target_price_low, color = color.red, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the median yearly price estimate.
    medianLine = line.new(time, close, YTD, syminfo.target_price_median, color = color.gray, xloc = xloc.bar_time)
    //@variable A line connecting the current `close` to the average yearly price estimate.
    averageLine = line.new(time, close, YTD, syminfo.target_price_average, color = color.orange, xloc = xloc.bar_time)
    // Fill the space between targets
    linefill.new(lowLine, medianLine, color.new(color.red, 90))
    linefill.new(medianLine, highLine, color.new(color.green, 90))
    // Create a label displaying the total number of analyst estimates.
    string estimatesText = str.format("Number of estimates: {0}", syminfo.target_price_estimates)
    label.new(bar_index, close, estimatesText, textcolor = color.white, size = size.large)
```

---

## syminfo.ticker

**Type:** simple string

Symbol name without exchange prefix, e.g. 'MSFT'.

---

### Syntax

```pine
syminfo.ticker(symbol) → series string
```

### Arguments

- `symbol` (*series string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL".

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

## syminfo.tickerid

**Type:** simple string

A ticker identifier representing the chart's symbol or a requested symbol, depending on how the script uses it. The variable's value represents a requested dataset's ticker ID when used in the expression argument of a request.*() function call. Otherwise, it represents the chart's ticker ID. The value contains an exchange prefix and a symbol name, separated by a colon (e.g., "NASDAQ:AAPL"). It can also include information about data modifications such as dividend adjustment, non-standard chart type, currency conversion, etc.

### Remarks
Because the value of this variable does not always use a simple "prefix:ticker" format, it is a poor candidate for use in boolean comparisons or string manipulation functions. In those contexts, run the variable's result through ticker.standard to purify it. This will remove any extraneous information and return a ticker ID consistently formatted using the "prefix:ticker" structure. To always access the script's main ticker ID, even within another context, use the syminfo.main_tickerid variable.

---

## syminfo.timezone

**Type:** simple string

Timezone of the exchange of the chart main series. Possible values see in timestamp.

---

## syminfo.type

**Type:** simple string

The type of market the symbol belongs to. The values are "stock", "fund", "dr", "right", "bond", "warrant", "structured", "index", "forex", "futures", "spread", "economic", "fundamental", "crypto", "spot", "swap", "option", "commodity".

---

## syminfo.volumetype

**Type:** simple string

Volume type of the current symbol. Possible values are: "base" for base currency, "quote" for quote currency, "tick" for the number of transactions, and "n/a" when there is no volume or its type is not specified.

### Remarks
Only some data feed suppliers provide information qualifying volume. As a result, the variable will return a value on some symbols only, mostly in the crypto sector.

---

## ta.accdist

**Type:** series float

Accumulation/distribution index.

---

## ta.iii

**Type:** series float

Intraday Intensity Index.

### Code Example
```pine
//@version=6
indicator("Intraday Intensity Index")
plot(ta.iii, color=color.yellow)

// the same on pine
f_iii() =>
    (2 * close - high - low) / ((high - low) * volume)

plot(f_iii())
```

---

## ta.nvi

**Type:** series float

Negative Volume Index.

### Code Example
```pine
//@version=6
indicator("Negative Volume Index")

plot(ta.nvi, color=color.yellow)

// the same on pine
f_nvi() =>
    float ta_nvi = 1.0
    float prevNvi = (nz(ta_nvi[1], 0.0) == 0.0) ? 1.0 : ta_nvi[1]
    if nz(close, 0.0) == 0.0 or nz(close[1], 0.0) == 0.0
        ta_nvi := prevNvi
    else
        ta_nvi := (volume < nz(volume[1], 0.0)) ? prevNvi + ((close - close[1]) / close[1]) * prevNvi : prevNvi
    result = ta_nvi

plot(f_nvi())
```

---

## ta.obv

**Type:** series float

On Balance Volume.

### Code Example
```pine
//@version=6
indicator("On Balance Volume")
plot(ta.obv, color=color.yellow)

// the same on pine
f_obv() =>
    ta.cum(math.sign(ta.change(close)) * volume)

plot(f_obv())
```

---

## ta.pvi

**Type:** series float

Positive Volume Index.

### Code Example
```pine
//@version=6
indicator("Positive Volume Index")

plot(ta.pvi, color=color.yellow)

// the same on pine
f_pvi() =>
    float ta_pvi = 1.0
    float prevPvi = (nz(ta_pvi[1], 0.0) == 0.0) ? 1.0 : ta_pvi[1]
    if nz(close, 0.0) == 0.0 or nz(close[1], 0.0) == 0.0
        ta_pvi := prevPvi
    else
        ta_pvi := (volume > nz(volume[1], 0.0)) ? prevPvi + ((close - close[1]) / close[1]) * prevPvi : prevPvi
    result = ta_pvi

plot(f_pvi())
```

---

## ta.pvt

**Type:** series float

Price-Volume Trend.

### Code Example
```pine
//@version=6
indicator("Price-Volume Trend")
plot(ta.pvt, color=color.yellow)

// the same on pine
f_pvt() =>
    ta.cum((ta.change(close) / close[1]) * volume)

plot(f_pvt())
```

---

## ta.tr

**Type:** series float

True range, equivalent to ta.tr(handle_na = false). It is calculated as math.max(high - low, math.abs(high - close[1]), math.abs(low - close[1])).

---

### Syntax

```pine
ta.tr(handle_na) → series float
```

### Arguments

- `handle_na` (*simple bool*) — How NaN values are handled. if true, and previous day’s close is NaN then tr would be calculated as current day high-low. Otherwise (if false) tr would return NaN in such cases. Also note, that [ta.atr](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.atr) uses ta.tr(true).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

## ta.vwap

**Type:** series float

Volume Weighted Average Price. It uses hlc3 as its source series.

---

### Syntax

```pine
ta.vwap(source, anchor) → series float
ta.vwap(source, anchor, stdev_mult) → [series float, series float, series float]
```

### Arguments

- `source` (*series int|float*) — Source used for the VWAP calculation.
- `anchor` (*series bool*, default `1D`) — The condition that triggers the reset of VWAP calculations. When [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), calculations reset; when [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), calculations proceed using the values accumulated since the previous reset. Optional. The default is equivalent to passing [timeframe.change](https://www.tradingview.com/pine-script-reference/v6/#fun_timeframe.change) with "1D" as its argument.
- `stdev_mult` (*series int|float*, default `na`) — If specified, the function will calculate the standard deviation bands based on the main VWAP series and return a [vwap, upper_band, lower_band] tuple. The `upper_band`/`lower_band` values are calculated using the VWAP to which the standard deviation multiplied by this argument is added/subtracted. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), in which case the function returns a single value, not a tuple.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

## ta.wad

**Type:** series float

Williams Accumulation/Distribution.

### Code Example
```pine
//@version=6
indicator("Williams Accumulation/Distribution")
plot(ta.wad, color=color.yellow)

// the same on pine
f_wad() =>
    trueHigh = math.max(high, close[1])
    trueLow = math.min(low, close[1])
    mom = ta.change(close)
    gain = (mom > 0) ? close - trueLow : (mom < 0) ? close - trueHigh : 0
    ta.cum(gain)

plot(f_wad())
```

---

## ta.wvad

**Type:** series float

Williams Variable Accumulation/Distribution.

### Code Example
```pine
//@version=6
indicator("Williams Variable Accumulation/Distribution")
plot(ta.wvad, color=color.yellow)

// the same on pine
f_wvad() =>
    (close - open) / (high - low) * volume

plot(f_wvad())
```

---

## table.all

**Type:** array<table>

Returns an array filled with all the current tables drawn by the script.

### Remarks
The array is read-only. Index zero of the array is the ID of the oldest object on the chart.

### Code Example
```pine
//@version=6
indicator("table.all")
//delete all tables
table.new(position = position.top_right, columns = 2, rows = 1, bgcolor = color.yellow, border_width = 1)
a_allTables = table.all
if array.size(a_allTables) > 0
    for i = 0 to array.size(a_allTables) - 1
        table.delete(array.get(a_allTables, i))
```

---

## time

**Type:** series int

Current bar time in UNIX format. It is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### Syntax

```pine
time(timeframe, session, timezone) → series int
```

### Arguments

- `timeframe` (*series string*) — Timeframe. An empty string is interpreted as the current timeframe of the chart.
- `session` (*series string*, default `""`) — Session specification. Optional argument, session of the symbol is used by default. An empty string is interpreted as the session of the symbol.
- `timezone` (*series string*, default `syminfo.timezone`) — Timezone of the `session` argument. Can only be used when a `session` is specified. Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone). Can be specified in GMT notation (e.g. "GMT-5") or as an [IANA time zone database name](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (e.g. "America/New_York").

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Note that this variable returns the timestamp based on the time of the bar's open. Because of that, for overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this variable can return time before the specified date of the trading day. For example, on EURUSD, dayofmonth(time) can be lower by 1 than the date of the trading day, because the bar for the current day actually opens one day prior.

---

## time_close

**Type:** series int

The time of the current bar's close in UNIX format. It represents the number of milliseconds elapsed since 00:00:00 UTC, 1 January 1970. On tick charts and price-based charts such as Renko, line break, Kagi, point & figure, and range, this variable's series holds an na timestamp for the latest realtime bar (because the future closing time is unpredictable), but valid timestamps for all previous bars.

---

### Syntax

```pine
time_close(timeframe, session, timezone) → series int
```

### Arguments

- `timeframe` (*series string*) — Resolution. An empty string is interpreted as the current resolution of the chart.
- `session` (*series string*, default `""`) — Session specification. Optional argument, session of the symbol is used by default. An empty string is interpreted as the session of the symbol.
- `timezone` (*series string*, default `syminfo.timezone`) — Timezone of the `session` argument. Can only be used when a `session` is specified. Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone). Can be specified in GMT notation (e.g. "GMT-5") or as an [IANA time zone database name](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (e.g. "America/New_York").

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

## time_tradingday

**Type:** series int

The beginning time of the trading day the current bar belongs to, in UNIX format (the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970).

### Remarks
The variable is useful for overnight sessions, where the current day's session can start on the previous calendar day (e.g., on FXCM:EURUSD the Monday session will start on Sunday, 17:00 in the exchange timezone). Unlike time, which would return the timestamp for Sunday at 17:00 for the Monday daily bar, time_tradingday will return the timestamp for Monday, 00:00 UTC. When used on timeframes higher than 1D, time_tradingday returns the trading day of the last day inside the bar (e.g. on 1W, it will return the last trading day of the week).

---

## timeframe.isdaily

**Type:** simple bool

Returns true if current resolution is a daily resolution, false otherwise.

---

## timeframe.isdwm

**Type:** simple bool

Returns true if current resolution is a daily or weekly or monthly resolution, false otherwise.

---

## timeframe.isintraday

**Type:** simple bool

Returns true if current resolution is an intraday (minutes or seconds) resolution, false otherwise.

---

## timeframe.isminutes

**Type:** simple bool

Returns true if current resolution is a minutes resolution, false otherwise.

---

## timeframe.ismonthly

**Type:** simple bool

Returns true if current resolution is a monthly resolution, false otherwise.

---

## timeframe.isseconds

**Type:** simple bool

Returns true if current resolution is a seconds resolution, false otherwise.

---

## timeframe.isticks

**Type:** simple bool

Returns true if current resolution is a ticks resolution, false otherwise.

---

## timeframe.isweekly

**Type:** simple bool

Returns true if current resolution is a weekly resolution, false otherwise.

---

## timeframe.main_period

**Type:** simple string

A string representation of the script's main timeframe. If the script is an indicator that specifies a timeframe value in its declaration statement, this variable holds that value. Otherwise, its value represents the chart's timeframe. Unlike timeframe.period, this variable's value does not change when used in the expression argument of a request.*() function call.

---

## timeframe.multiplier

**Type:** simple int

Multiplier of resolution, e.g. '60' - 60, 'D' - 1, '5D' - 5, '12M' - 12.

---

## timeframe.period

**Type:** simple string

A string representation of the script's main timeframe or a requested timeframe, depending on how the script uses it. The variable's value represents the timeframe of a requested dataset when used in the expression argument of a request.*() function call. Otherwise, its value represents the script's main timeframe (timeframe.main_period), which equals either the timeframe argument of the indicator declaration statement or the chart's timeframe.

### Remarks
To always access the script's main timeframe, even within another context, use the timeframe.main_period variable.

---

## timenow

**Type:** series int

Current time in UNIX format. It is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### Remarks
Please note that using this variable/function can cause indicator repainting.

---

## volume

**Type:** series float

Current bar volume.

### Remarks
Previous values may be accessed with square brackets operator [], e.g. volume[1], volume[2].

---

## weekofyear

**Type:** series int

Week number of current bar time in exchange timezone.

### Syntax

```pine
weekofyear(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Note that this variable returns the week based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the week of the trading day.

---

## year

**Type:** series int

Current bar year in exchange timezone.

### Syntax

```pine
year(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Note that this variable returns the year based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the year of the trading day.

# Constants
---

## adjustment.dividends

**Type:** const string

Constant for dividends adjustment type (dividends adjustment is applied).

---

## adjustment.none

**Type:** const string

Constant for none adjustment type (no adjustment is applied).

---

## adjustment.splits

**Type:** const string

Constant for splits adjustment type (splits adjustment is applied).

---

## alert.freq_all

**Type:** const string

A named constant for use with the freq parameter of the alert() function.

---

## alert.freq_once_per_bar

**Type:** const string

A named constant for use with the freq parameter of the alert() function.

---

## alert.freq_once_per_bar_close

**Type:** const string

A named constant for use with the freq parameter of the alert() function.

---

## backadjustment.inherit

**Type:** const backadjustment

A constant to specify the value of the backadjustment parameter in ticker.new and ticker.modify functions.

---

## backadjustment.off

**Type:** const backadjustment

A constant to specify the value of the backadjustment parameter in ticker.new and ticker.modify functions.

---

## backadjustment.on

**Type:** const backadjustment

A constant to specify the value of the backadjustment parameter in ticker.new and ticker.modify functions.

---

## barmerge.gaps_off

**Type:** const barmerge_gaps

Merge strategy for requested data. Data is merged continuously without gaps, all the gaps are filled with the previous nearest existing value.

---

## barmerge.gaps_on

**Type:** const barmerge_gaps

Merge strategy for requested data. Data is merged with possible gaps (na values).

---

## barmerge.lookahead_off

**Type:** const barmerge_lookahead

Merge strategy for the requested data position. Requested barset is merged with current barset in the order of sorting bars by their close time. This merge strategy disables effect of getting data from "future" on calculation on history.

---

## barmerge.lookahead_on

**Type:** const barmerge_lookahead

Merge strategy for the requested data position. Requested barset is merged with current barset in the order of sorting bars by their opening time. This merge strategy can lead to undesirable effect of getting data from "future" on calculation on history. This is unacceptable in backtesting strategies, but can be useful in indicators.

---

## color.aqua

**Type:** const color

Is a named constant for #00BCD4 color.

---

## color.black

**Type:** const color

Is a named constant for #363A45 color.

---

## color.blue

**Type:** const color

Is a named constant for #2962ff color.

---

## color.fuchsia

**Type:** const color

Is a named constant for #E040FB color.

---

## color.gray

**Type:** const color

Is a named constant for #787B86 color.

---

## color.green

**Type:** const color

Is a named constant for #4CAF50 color.

---

## color.lime

**Type:** const color

Is a named constant for #00E676 color.

---

## color.maroon

**Type:** const color

Is a named constant for #880E4F color.

---

## color.navy

**Type:** const color

Is a named constant for #311B92 color.

---

## color.olive

**Type:** const color

Is a named constant for #808000 color.

---

## color.orange

**Type:** const color

Is a named constant for #FF9800 color.

---

## color.purple

**Type:** const color

Is a named constant for #9C27B0 color.

---

## color.red

**Type:** const color

Is a named constant for #F23645 color.

---

## color.silver

**Type:** const color

Is a named constant for #B2B5BE color.

---

## color.teal

**Type:** const color

Is a named constant for #089981 color.

---

## color.white

**Type:** const color

Is a named constant for #FFFFFF color.

---

## color.yellow

**Type:** const color

Is a named constant for #FDD835 color.

---

## currency.AUD

**Type:** const string

Australian dollar.

---

## currency.BTC

**Type:** const string

Bitcoin.

---

## currency.CAD

**Type:** const string

Canadian dollar.

---

## currency.CHF

**Type:** const string

Swiss franc.

---

## currency.EGP

**Type:** const string

Egyptian pound.

---

## currency.ETH

**Type:** const string

Ethereum.

---

## currency.EUR

**Type:** const string

Euro.

---

## currency.GBP

**Type:** const string

Pound sterling.

---

## currency.HKD

**Type:** const string

Hong Kong dollar.

---

## currency.INR

**Type:** const string

Indian rupee.

---

## currency.JPY

**Type:** const string

Japanese yen.

---

## currency.KRW

**Type:** const string

South Korean won.

---

## currency.MYR

**Type:** const string

Malaysian ringgit.

---

## currency.NOK

**Type:** const string

Norwegian krone.

---

## currency.NONE

**Type:** const string

Unspecified currency.

---

## currency.NZD

**Type:** const string

New Zealand dollar.

---

## currency.PKR

**Type:** const string

Pakistani rupee.

---

## currency.PLN

**Type:** const string

Polish zloty.

---

## currency.RUB

**Type:** const string

Russian ruble.

---

## currency.SEK

**Type:** const string

Swedish krona.

---

## currency.SGD

**Type:** const string

Singapore dollar.

---

## currency.TRY

**Type:** const string

Turkish lira.

---

## currency.USD

**Type:** const string

United States dollar.

---

## currency.USDT

**Type:** const string

Tether.

---

## currency.ZAR

**Type:** const string

South African rand.

---

## dayofweek.friday

**Type:** const int

Is a named constant for return value of dayofweek function and value of dayofweek variable.

---

## dayofweek.monday

**Type:** const int

Is a named constant for return value of dayofweek function and value of dayofweek variable.

---

## dayofweek.saturday

**Type:** const int

Is a named constant for return value of dayofweek function and value of dayofweek variable.

---

## dayofweek.sunday

**Type:** const int

Is a named constant for return value of dayofweek function and value of dayofweek variable.

---

## dayofweek.thursday

**Type:** const int

Is a named constant for return value of dayofweek function and value of dayofweek variable.

---

## dayofweek.tuesday

**Type:** const int

Is a named constant for return value of dayofweek function and value of dayofweek variable.

---

## dayofweek.wednesday

**Type:** const int

Is a named constant for return value of dayofweek function and value of dayofweek variable.

---

## display.all

**Type:** const plot_simple_display

A named constant for use with the display parameter of plot*() and input*() functions. Displays plotted or input values in all possible locations.

---

## display.data_window

**Type:** const plot_display

A named constant for use with the display parameter of plot*() and input*() functions. Displays plotted or input values in the Data Window, a menu accessible from the chart's right sidebar.

---

## display.none

**Type:** const plot_simple_display

A named constant for use with the display parameter of plot*() and input*() functions. plot*() functions using this will not display their plotted values anywhere. However, alert template messages and fill functions can still use the values, and they will appear in exported chart data. input*() functions using this constant will only display their values within the script's settings.

---

## display.pane

**Type:** const plot_display

A named constant for use with the display parameter of plot*() functions. Displays plotted values in the chart pane used by the script.

---

## display.price_scale

**Type:** const plot_display

A named constant for use with the display parameter of plot*() functions. Displays the plot’s label and value on the price scale if the chart's settings allow it.

---

## display.status_line

**Type:** const plot_display

A named constant for use with the display parameter of plot*() and input*() functions. Displays plotted or input values in the status line next to the script's name on the chart if the chart's settings allow it.

---

## dividends.gross

**Type:** const string

A named constant for the request.dividends function. Is used to request the dividends return on a stock before deductions.

---

## dividends.net

**Type:** const string

A named constant for the request.dividends function. Is used to request the dividends return on a stock after deductions.

---

## earnings.actual

**Type:** const string

A named constant for the request.earnings function. Is used to request the earnings value as it was reported.

---

## earnings.estimate

**Type:** const string

A named constant for the request.earnings function. Is used to request the estimated earnings value.

---

## earnings.standardized

**Type:** const string

A named constant for the request.earnings function. Is used to request the standardized earnings value.

---

## extend.both

**Type:** const string

A named constant for line.new and line.set_extend functions.

---

## extend.left

**Type:** const string

A named constant for line.new and line.set_extend functions.

---

## extend.none

**Type:** const string

A named constant for line.new and line.set_extend functions.

---

## extend.right

**Type:** const string

A named constant for line.new and line.set_extend functions.

---

## false

Literal representing a bool value, and result of a comparison operation.

### Syntax

```pine
bool false
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
See the User Manual for comparison operators and logical operators.

---

## font.family_default

**Type:** const string

Default text font for box.new, box.set_text_font_family, label.new, label.set_text_font_family, table.cell and table.cell_set_text_font_family functions.

---

## font.family_monospace

**Type:** const string

Monospace text font for box.new, box.set_text_font_family, label.new, label.set_text_font_family, table.cell and table.cell_set_text_font_family functions.

---

## format.inherit

**Type:** const string

Is a named constant for selecting the formatting of the script output values from the parent series in the indicator function.

---

## format.mintick

**Type:** const string

Is a named constant to use with the str.tostring function. Passing a number to str.tostring with this argument rounds the number to the nearest value that can be divided by syminfo.mintick, without the remainder, with ties rounding up, and returns the string version of said value with trailing zeros.

---

## format.percent

**Type:** const string

Is a named constant for selecting the formatting of the script output values as a percentage in the indicator function. It adds a percent sign after values.

### Remarks
The default precision is 2, regardless of the precision of the chart itself. This can be changed with the 'precision' argument of the indicator function.

---

## format.price

**Type:** const string

Is a named constant for selecting the formatting of the script output values as prices in the indicator function.

### Remarks
If format is format.price, default precision value is set. You can use the precision argument of indicator function to change the precision value.

---

## format.volume

**Type:** const string

Is a named constant for selecting the formatting of the script output values as volume in the indicator function, e.g. '5183' will be formatted as '5.183K'.

---

## hline.style_dashed

**Type:** const hline_style

Is a named constant for dashed linestyle of hline function.

---

## hline.style_dotted

**Type:** const hline_style

Is a named constant for dotted linestyle of hline function.

---

## hline.style_solid

**Type:** const hline_style

Is a named constant for solid linestyle of hline function.

---

## label.style_arrowdown

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_arrowup

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_circle

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_cross

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_diamond

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_flag

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_center

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_down

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_left

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_lower_left

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_lower_right

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_right

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_up

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_upper_left

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_label_upper_right

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_none

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_square

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_text_outline

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_triangledown

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_triangleup

**Type:** const string

Label style for label.new and label.set_style functions.

---

## label.style_xcross

**Type:** const string

Label style for label.new and label.set_style functions.

---

## line.style_arrow_both

**Type:** const string

Line style for line.new and line.set_style functions. Solid line with arrows on both points.

---

## line.style_arrow_left

**Type:** const string

Line style for line.new and line.set_style functions. Solid line with arrow on the first point.

---

## line.style_arrow_right

**Type:** const string

Line style for line.new and line.set_style functions. Solid line with arrow on the second point.

---

## line.style_dashed

**Type:** const string

Line style for line.new and line.set_style functions.

---

## line.style_dotted

**Type:** const string

Line style for line.new and line.set_style functions.

---

## line.style_solid

**Type:** const string

Line style for line.new and line.set_style functions.

---

## location.abovebar

**Type:** const string

Location value for plotshape, plotchar functions. Shape is plotted above main series bars.

---

## location.absolute

**Type:** const string

Location value for plotshape, plotchar functions. Shape is plotted on chart using indicator value as a price coordinate.

---

## location.belowbar

**Type:** const string

Location value for plotshape, plotchar functions. Shape is plotted below main series bars.

---

## location.bottom

**Type:** const string

Location value for plotshape, plotchar functions. Shape is plotted near the bottom chart border.

---

## location.top

**Type:** const string

Location value for plotshape, plotchar functions. Shape is plotted near the top chart border.

---

## math.e

**Type:** const float

Is a named constant for Euler's number. It is equal to 2.7182818284590452.

---

## math.phi

**Type:** const float

Is a named constant for the golden ratio. It is equal to 1.6180339887498948.

---

## math.pi

**Type:** const float

Is a named constant for Archimedes' constant. It is equal to 3.1415926535897932.

---

## math.rphi

**Type:** const float

Is a named constant for the golden ratio conjugate. It is equal to 0.6180339887498948.

---

## order.ascending

**Type:** const sort_order

Determines the sort order of the array from the smallest to the largest value.

---

## order.descending

**Type:** const sort_order

Determines the sort order of the array from the largest to the smallest value.

---

## plot.style_area

**Type:** const plot_style

A named constant for the 'Area' style, to be used as an argument for the style parameter in the plot function.

---

## plot.style_areabr

**Type:** const plot_style

A named constant for the 'Area With Breaks' style, to be used as an argument for the style parameter in the plot function. Similar to plot.style_area, except the gaps in the data are not filled.

---

## plot.style_circles

**Type:** const plot_style

A named constant for the 'Circles' style, to be used as an argument for the style parameter in the plot function.

---

## plot.style_columns

**Type:** const plot_style

A named constant for the 'Columns' style, to be used as an argument for the style parameter in the plot function.

---

## plot.style_cross

**Type:** const plot_style

A named constant for the 'Cross' style, to be used as an argument for the style parameter in the plot function.

---

## plot.style_histogram

**Type:** const plot_style

A named constant for the 'Histogram' style, to be used as an argument for the style parameter in the plot function.

---

## plot.style_line

**Type:** const plot_style

A named constant for the 'Line' style, to be used as an argument for the style parameter in the plot function.

---

## plot.style_linebr

**Type:** const plot_style

A named constant for the 'Line With Breaks' style, to be used as an argument for the style parameter in the plot function. Similar to plot.style_line, except the gaps in the data are not filled.

---

## plot.style_stepline

**Type:** const plot_style

A named constant for the 'Step Line' style, to be used as an argument for the style parameter in the plot function.

---

## plot.style_stepline_diamond

**Type:** const plot_style

A named constant for the 'Step Line With Diamonds' style, to be used as an argument for the style parameter in the plot function. Similar to plot.style_stepline, except the data changes are also marked with the Diamond shapes.

---

## plot.style_steplinebr

**Type:** const plot_style

A named constant for the 'Step line with Breaks' style, to be used as an argument for the style parameter in the plot function.

---

## position.bottom_center

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## position.bottom_left

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## position.bottom_right

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## position.middle_center

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## position.middle_left

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## position.middle_right

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## position.top_center

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## position.top_left

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## position.top_right

**Type:** const string

Table position is used in table.new, table.cell functions.

---

## scale.left

**Type:** const scale_type

Scale value for indicator function. Indicator is added to the left price scale.

---

## scale.none

**Type:** const scale_type

Scale value for indicator function. Indicator is added in 'No Scale' mode. Can be used only with 'overlay=true'.

---

## scale.right

**Type:** const scale_type

Scale value for indicator function. Indicator is added to the right price scale.

---

## session.extended

**Type:** const string

Constant for extended session type (with extended hours data).

---

## session.regular

**Type:** const string

Constant for regular session type (no extended hours data).

---

## settlement_as_close.inherit

**Type:** const settlement

A constant to specify the value of the settlement_as_close parameter in ticker.new and ticker.modify functions.

---

## settlement_as_close.off

**Type:** const settlement

A constant to specify the value of the settlement_as_close parameter in ticker.new and ticker.modify functions.

---

## settlement_as_close.on

**Type:** const settlement

A constant to specify the value of the settlement_as_close parameter in ticker.new and ticker.modify functions.

---

## shape.arrowdown

**Type:** const string

Shape style for plotshape function.

---

## shape.arrowup

**Type:** const string

Shape style for plotshape function.

---

## shape.circle

**Type:** const string

Shape style for plotshape function.

---

## shape.cross

**Type:** const string

Shape style for plotshape function.

---

## shape.diamond

**Type:** const string

Shape style for plotshape function.

---

## shape.flag

**Type:** const string

Shape style for plotshape function.

---

## shape.labeldown

**Type:** const string

Shape style for plotshape function.

---

## shape.labelup

**Type:** const string

Shape style for plotshape function.

---

## shape.square

**Type:** const string

Shape style for plotshape function.

---

## shape.triangledown

**Type:** const string

Shape style for plotshape function.

---

## shape.triangleup

**Type:** const string

Shape style for plotshape function.

---

## shape.xcross

**Type:** const string

Shape style for plotshape function.

---

## size.auto

**Type:** const string

Size value for plotshape, plotchar functions. The size of the shape automatically adapts to the size of the bars.

---

## size.huge

**Type:** const string

Size value for plotshape, plotchar functions. The size of the shape constantly huge.

---

## size.large

**Type:** const string

Size value for plotshape, plotchar functions. The size of the shape constantly large.

---

## size.normal

**Type:** const string

Size value for plotshape, plotchar functions. The size of the shape constantly normal.

---

## size.small

**Type:** const string

Size value for plotshape, plotchar functions. The size of the shape constantly small.

---

## size.tiny

**Type:** const string

Size value for plotshape, plotchar functions. The size of the shape constantly tiny.

---

## splits.denominator

**Type:** const string

A named constant for the request.splits function. Is used to request the denominator (the number below the line in a fraction) of a splits.

---

## splits.numerator

**Type:** const string

A named constant for the request.splits function. Is used to request the numerator (the number above the line in a fraction) of a splits.

---

## strategy.cash

**Type:** const string

This is one of the arguments that can be supplied to the default_qty_type parameter in the strategy declaration statement. It is only relevant when no value is used for the ‘qty’ parameter in strategy.entry or strategy.order function calls. It specifies that an amount of cash in the strategy.account_currency will be used to enter trades.

### Code Example
```pine
//@version=6
strategy("strategy.cash", overlay = true, default_qty_value = 50, default_qty_type = strategy.cash, initial_capital = 1000000)

if bar_index == 0
    // As ‘qty’ is not defined, the previously defined values for the `default_qty_type` and `default_qty_value` parameters are used to enter trades, namely 50 units of cash in the currency of `strategy.account_currency`.
    // `qty` is calculated as (default_qty_value)/(close price). If current price is $5, then qty = 50/5 = 10.
    strategy.entry("EN", strategy.long)
if bar_index == 2
    strategy.close("EN")
```

---

## strategy.commission.cash_per_contract

**Type:** const string

Commission type for an order. Money displayed in the account currency per contract.

---

## strategy.commission.cash_per_order

**Type:** const string

Commission type for an order. Money displayed in the account currency per order.

---

## strategy.commission.percent

**Type:** const string

Commission type for an order. A percentage of the cash volume of order.

---

## strategy.direction.all

**Type:** const string

It allows strategy to open both long and short positions.

---

## strategy.direction.long

**Type:** const string

It allows strategy to open only long positions.

---

## strategy.direction.short

**Type:** const string

It allows strategy to open only short positions.

---

## strategy.fixed

**Type:** const string

This is one of the arguments that can be supplied to the default_qty_type parameter in the strategy declaration statement. It is only relevant when no value is used for the ‘qty’ parameter in strategy.entry or strategy.order function calls. It specifies that a number of contracts/shares/lots will be used to enter trades.

### Code Example
```pine
//@version=6
strategy("strategy.fixed", overlay = true, default_qty_value = 50, default_qty_type = strategy.fixed, initial_capital = 1000000)

if bar_index == 0
    // As ‘qty’ is not defined, the previously defined values for the `default_qty_type` and `default_qty_value` parameters are used to enter trades, namely 50 contracts.
    // qty = 50
    strategy.entry("EN", strategy.long)
if bar_index == 2
    strategy.close("EN")
```

---

## strategy.long

**Type:** const strategy_direction

A named constant for use with the direction parameter of the strategy.entry and strategy.order commands. It specifies that the command creates a buy order.

---

## strategy.oca.cancel

**Type:** const string

A named constant for use with the oca_type parameter of the strategy.entry and strategy.order commands. It specifies that the strategy cancels the unfilled order when another order with the same oca_name and oca_type executes.

### Remarks
Strategies cannot cancel or reduce pending orders from an OCA group if they execute on the same tick. For example, if the market price triggers two stop orders from strategy.order calls with the same oca_* arguments, the strategy cannot fully or partially cancel either one.

---

## strategy.oca.none

**Type:** const string

A named constant for use with the oca_type parameter of the strategy.entry and strategy.order commands. It specifies that the order executes independently of all other orders, including those with the same oca_name.

---

## strategy.oca.reduce

**Type:** const string

A named constant for use with the oca_type parameter of the strategy.entry and strategy.order commands. It specifies that when another order with the same oca_name and oca_type executes, the strategy reduces the unfilled order by that order's size. If the unfilled order's size reaches 0 after reduction, it is the same as canceling the order entirely.

### Remarks
Strategies cannot cancel or reduce pending orders from an OCA group if they execute on the same tick. For example, if the market price triggers two stop orders from strategy.order calls with the same oca_* arguments, the strategy cannot fully or partially cancel either one. Orders from strategy.exit automatically use this OCA type, and they belong to the same OCA group by default.

---

## strategy.percent_of_equity

**Type:** const string

This is one of the arguments that can be supplied to the default_qty_type parameter in the strategy declaration statement. It is only relevant when no value is used for the ‘qty’ parameter in strategy.entry or strategy.order function calls. It specifies that a percentage (0-100) of equity will be used to enter trades.

### Code Example
```pine
//@version=6
strategy("strategy.percent_of_equity", overlay = false, default_qty_value = 100, default_qty_type = strategy.percent_of_equity, initial_capital = 1000000)

// As ‘qty’ is not defined, the previously defined values for the `default_qty_type` and `default_qty_value` parameters are used to enter trades, namely 100% of available equity.
if bar_index == 0
    strategy.entry("EN", strategy.long)
if bar_index == 2
    strategy.close("EN")
plot(strategy.equity)

 // The ‘qty’ parameter is set to 10. Entering position with fixed size of 10 contracts and entry market price = (10 * close).
if bar_index == 4
    strategy.entry("EN", strategy.long, qty = 10)
if bar_index == 6
    strategy.close("EN")
```

---

## strategy.short

**Type:** const strategy_direction

A named constant for use with the direction parameter of the strategy.entry and strategy.order commands. It specifies that the command creates a sell order.

---

## text.align_bottom

**Type:** const string

Vertical text alignment for box.new, box.set_text_valign, table.cell and table.cell_set_text_valign functions.

---

## text.align_center

**Type:** const string

Text alignment for box.new, box.set_text_halign, box.set_text_valign, label.new and label.set_textalign functions.

---

## text.align_left

**Type:** const string

Horizontal text alignment for box.new, box.set_text_halign, label.new and label.set_textalign functions.

---

## text.align_right

**Type:** const string

Horizontal text alignment for box.new, box.set_text_halign, label.new and label.set_textalign functions.

---

## text.align_top

**Type:** const string

Vertical text alignment for box.new, box.set_text_valign, table.cell and table.cell_set_text_valign functions.

---

## text.format_bold

**Type:** const text_format

A named constant for use with the text_formatting parameter of the label.new(), box.new(), table.cell(), and *set_text_formatting() functions. Makes the text bold.

---

## text.format_italic

**Type:** const text_format

A named constant for use with the text_formatting parameter of the label.new(), box.new(), table.cell(), and *set_text_formatting() functions. Italicizes the text.

---

## text.format_none

**Type:** const text_format

A named constant for use with the text_formatting parameter of the label.new(), box.new(), table.cell(), and *set_text_formatting() functions. Signifies no special text formatting.

---

## text.wrap_auto

**Type:** const string

Automatic wrapping mode for box.new and box.set_text_wrap functions.

---

## text.wrap_none

**Type:** const string

Disabled wrapping mode for box.new and box.set_text_wrap functions.

---

## true

Literal representing one of the values a bool variable can hold, or an expression can evaluate to when it uses comparison or logical operators.

### Syntax

```pine
bool true
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
See the User Manual for comparison operators and logical operators.

---

## xloc.bar_index

**Type:** const string

A constant that specifies how functions that create and modify Pine drawings interpret x-coordinates. If xloc = xloc.bar_index, the drawing object treats each x-coordinate as a bar_index value.

---

## xloc.bar_time

**Type:** const string

A constant that specifies how functions that create and modify Pine drawings interpret x-coordinates. If xloc = xloc.bar_time, the drawing object treats each x-coordinate as a UNIX timestamp, expressed in milliseconds.

---

## yloc.abovebar

**Type:** const string

A named constant that specifies the algorithm of interpretation of y-value in function label.new.

---

## yloc.belowbar

**Type:** const string

A named constant that specifies the algorithm of interpretation of y-value in function label.new.

---

## yloc.price

**Type:** const string

A named constant that specifies the algorithm of interpretation of y-value in function label.new.

---

# Functions

## alert()

Creates an alert trigger for an indicator or strategy, with a specified frequency, when called on the latest realtime bar. To activate alerts for a script containing calls to this function, open the "Create Alert" dialog box, then select the script name and "Any alert() function call" in the "Condition" section.

### Syntax

```pine
alert(message, freq) → void
```

### Arguments

- `message` (*series string*) — Message sent when the alert triggers. Required argument.
- `freq` (*input string*, default `alert.freq_once_per_bar`) — The triggering frequency. Possible values are: [alert.freq_all](https://www.tradingview.com/pine-script-reference/v6/#var_alert.freq_all) (all function calls trigger the alert), [alert.freq_once_per_bar](https://www.tradingview.com/pine-script-reference/v6/#var_alert.freq_once_per_bar) (the first function call during the bar triggers the alert), [alert.freq_once_per_bar_close](https://www.tradingview.com/pine-script-reference/v6/#var_alert.freq_once_per_bar_close) (the function call triggers the alert only when it occurs during the last script iteration of the real-time bar, when it closes). The default is [alert.freq_once_per_bar](https://www.tradingview.com/pine-script-reference/v6/#var_alert.freq_once_per_bar).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_alert).*

### Remarks
The alert() function does not display information on the chart. In contrast to alertcondition, calls to this function do not count toward a script's plot count. Additionally, alert() calls are allowed in local scopes, including the scopes of exported library functions. See this article in our Help Center to learn more about activating alerts from alert() calls.

### Code Example
```pine
//@version=6
indicator("`alert()` example", "", true)
ma = ta.sma(close, 14)
xUp = ta.crossover(close, ma)
if xUp
    // Trigger the alert the first time a cross occurs during the real-time bar.
    alert("Price (" + str.tostring(close) + ") crossed over MA (" + str.tostring(ma) + ").", alert.freq_once_per_bar)
plot(ma)
plotchar(xUp, "xUp", "▲", location.top, size = size.tiny)
```

---

## alertcondition()

Creates alert condition, that is available in Create Alert dialog. Please note, that alertcondition does NOT create an alert, it just gives you more options in Create Alert dialog. Also, alertcondition effect is invisible on chart.

### Syntax

```pine
alertcondition(condition, title, message) → void
```

### Arguments

- `condition` (*series bool*) — Series of boolean values that is used for alert. True values mean alert fire, false - no alert. Required argument.
- `title` (*const string*, optional) — Title of the alert condition. Optional argument.
- `message` (*const string*, optional) — Message to display when alert fires. Optional argument.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_alertcondition).*

### Remarks
Please note that an alertcondition call generates an additional plot. All such calls are taken into account when we calculate the number of the output series per script.

### Code Example
```pine
//@version=6
indicator("alertcondition", overlay=true)
alertcondition(close >= open, title='Alert on Green Bar', message='Green Bar!')
```

---

## array.abs()

Returns an array containing the absolute value of each element in the original array.

---

### Syntax

```pine
array.abs(id) → array<float|int>
```

### Arguments

- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.abs).*

## array.avg()

The function returns the mean of an array's elements.

### Syntax

```pine
array.avg(id) → series float|int
```

### Arguments

- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.avg).*

### Returns
Mean of array's elements.

### Code Example
```pine
//@version=6
indicator("array.avg example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
plot(array.avg(a))
```

---

## array.binary_search()

The function returns the index of the value, or -1 if the value is not found. The array to search must be sorted in ascending order.

### Syntax

```pine
array.binary_search(id, val) → series int
```

### Arguments

- `val` (*series int|float*) — The value to search for in the array.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.binary_search).*

### Remarks
A binary search works on arrays pre-sorted in ascending order. It begins by comparing an element in the middle of the array with the target value. If the element matches the target value, its position in the array is returned. If the element's value is greater than the target value, the search continues in the lower half of the array. If the element's value is less than the target value, the search continues in the upper half of the array. By doing this recursively, the algorithm progressively eliminates smaller and smaller portions of the array in which the target value cannot lie.

### Code Example
```pine
//@version=6
indicator("array.binary_search")
a = array.from(5, -2, 0, 9, 1)
array.sort(a) // [-2, 0, 1, 5, 9]
position = array.binary_search(a, 0) // 1
plot(position)
```

---

## array.binary_search_leftmost()

The function returns the index of the value if it is found. When the value is not found, the function returns the index of the next smallest element to the left of where the value would lie if it was in the array. The array to search must be sorted in ascending order.

### Syntax

```pine
array.binary_search_leftmost(id, val) → series int
```

### Arguments

- `val` (*series int|float*) — The value to search for in the array.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.binary_search_leftmost).*

### Remarks
A binary search works on arrays pre-sorted in ascending order. It begins by comparing an element in the middle of the array with the target value. If the element matches the target value, its position in the array is returned. If the element's value is greater than the target value, the search continues in the lower half of the array. If the element's value is less than the target value, the search continues in the upper half of the array. By doing this recursively, the algorithm progressively eliminates smaller and smaller portions of the array in which the target value cannot lie.

### Code Example
```pine
//@version=6
indicator("array.binary_search_leftmost")
a = array.from(5, -2, 0, 9, 1)
array.sort(a) // [-2, 0, 1, 5, 9]
position = array.binary_search_leftmost(a, 3) // 2
plot(position)

//@version=6
indicator("array.binary_search_leftmost, repetitive elements")
a = array.from(4, 5, 5, 5)
// Returns the index of the first instance.
position = array.binary_search_leftmost(a, 5) 
plot(position) // Plots 1
```

---

## array.binary_search_rightmost()

The function returns the index of the value if it is found. When the value is not found, the function returns the index of the element to the right of where the value would lie if it was in the array. The array must be sorted in ascending order.

### Syntax

```pine
array.binary_search_rightmost(id, val) → series int
```

### Arguments

- `val` (*series int|float*) — The value to search for in the array.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.binary_search_rightmost).*

### Remarks
A binary search works on sorted arrays in ascending order. It begins by comparing an element in the middle of the array with the target value. If the element matches the target value, its position in the array is returned. If the element's value is greater than the target value, the search continues in the lower half of the array. If the element's value is less than the target value, the search continues in the upper half of the array. By doing this recursively, the algorithm progressively eliminates smaller and smaller portions of the array in which the target value cannot lie.

### Code Example
```pine
//@version=6
indicator("array.binary_search_rightmost")
a = array.from(5, -2, 0, 9, 1)
array.sort(a) // [-2, 0, 1, 5, 9]
position = array.binary_search_rightmost(a, 3) // 3
plot(position)

//@version=6
indicator("array.binary_search_rightmost, repetitive elements")
a = array.from(4, 5, 5, 5)
// Returns the index of the last instance.
position = array.binary_search_rightmost(a, 5) 
plot(position) // Plots 3
```

---

## array.clear()

The function removes all elements from an array.

### Syntax

```pine
array.clear(id) → void
```

### Arguments

- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.clear).*

### Code Example
```pine
//@version=6
indicator("array.clear example")
a = array.new_float(5,high)
array.clear(a)
array.push(a, close)
plot(array.get(a,0))
plot(array.size(a))
```

---

## array.concat()

The function is used to merge two arrays. It pushes all elements from the second array to the first array, and returns the first array.

### Syntax

```pine
array.concat(id1, id2) → type[]
```

### Arguments

- `id2` (*any[]*) — The second array object.
- `id1` (*any[]*) — The first array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.concat).*

### Returns
The first array with merged elements from the second array.

### Code Example
```pine
//@version=6
indicator("array.concat example")
a = array.new_float(0,0)
b = array.new_float(0,0)
for i = 0 to 4
    array.push(a, high[i])
    array.push(b, low[i])
c = array.concat(a,b)
plot(array.size(a))
plot(array.size(b))
plot(array.size(c))
```

---

## array.copy()

The function creates a copy of an existing array.

### Syntax

```pine
array.copy(id) → type[]
```

### Arguments

- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.copy).*

### Returns
A copy of an array.

### Code Example
```pine
//@version=6
indicator("array.copy example")
length = 5
a = array.new_float(length, close)
b = array.copy(a)
a := array.new_float(length, open)
plot(array.sum(a) / length)
plot(array.sum(b) / length)
```

---

## array.covariance()

The function returns the covariance of two arrays.

### Syntax

```pine
array.covariance(id1, id2, biased) → series float
```

### Arguments

- `id2` (*array<int|float>*) — An array object.
- `biased` (*series bool*, optional, default `true`) — Determines which estimate should be used. Optional. The default is true.
- `id1` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.covariance).*

### Returns
The covariance of two arrays.

### Remarks
If biased is true, function will calculate using a biased estimate of the entire population, if false - unbiased estimate of a sample.

### Code Example
```pine
//@version=6
indicator("array.covariance example")
a = array.new_float(0)
b = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
    array.push(b, open[i])
plot(array.covariance(a, b))
```

---

## array.every()

Returns true if all elements of the id array are true, false otherwise.

### Syntax

```pine
array.every(id) → series bool
```

### Arguments

- `id` (*array<bool>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.every).*

### Remarks
This function also works with arrays of int and float types, in which case zero values are considered false, and all others true.

---

## array.fill()

The function sets elements of an array to a single value. If no index is specified, all elements are set. If only a start index (default 0) is supplied, the elements starting at that index are set. If both index parameters are used, the elements from the starting index up to but not including the end index (default na) are set.

### Syntax

```pine
array.fill(id, value, index_from, index_to) → void
```

### Arguments

- `value` (*any*) — Value to fill the array with.
- `index_from` (*series int*, optional, default `0`) — Start index, default is 0.
- `index_to` (*series int*, optional, default `na`) — End index, default is na. Must be one greater than the index of the last element to set.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.fill).*

### Code Example
```pine
//@version=6
indicator("array.fill example")
a = array.new_float(10)
array.fill(a, close)
plot(array.sum(a))
```

---

## array.first()

Returns the array's first element. Throws a runtime error if the array is empty.

### Syntax

```pine
array.first(id) → series type
```

### Arguments

- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.first).*

### Code Example
```pine
//@version=6
indicator("array.first example")
arr = array.new_int(3, 10)
plot(array.first(arr))
```

---

## array.from()

The function takes a variable number of arguments with one of the types: int, float, bool, string, label, line, color, box, table, linefill, and returns an array of the corresponding type.

### Syntax

```pine
array.from(arg0, arg1, ...) → type[]
```

### Arguments

- `arg0, arg1, ...` (*any*) — Array arguments.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.from).*

### Returns
The array element's value.

### Remarks
This function can accept up to 4,000 'int', 'float', 'bool', or 'color' arguments. For all other types, including user-defined types, the limit is 999.

### Code Example
```pine
//@version=6
indicator("array.from_example", overlay = false)
arr = array.from("Hello", "World!") // arr (array<string>) will contain 2 elements: {Hello}, {World!}.
plot(close)
```

---

## array.get()

The function returns the value of the element at the specified index.

### Syntax

```pine
array.get(id, index) → series type
```

### Arguments

- `index` (*series int*) — The index of the element whose value is to be returned.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.get).*

### Returns
The array element's value.

### Remarks
If the index is positive, the function counts forwards from the beginning of the array to the end. The index of the first element is 0, and the index of the last element is array.size() - 1. If the index is negative, the function counts backwards from the end of the array to the beginning. In this case, the index of the last element is -1, and the index of the first element is negative array.size(). For example, for an array that contains three elements, all of the following are valid arguments for the index parameter: 0, 1, 2, -1, -2, -3.

### Code Example
```pine
//@version=6
indicator("array.get example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i] - open[i])
plot(array.get(a, 9))
```

---

## array.includes()

The function returns true if the value was found in an array, false otherwise.

### Syntax

```pine
array.includes(id, value) → series bool
```

### Arguments

- `value` (*any*) — The value to search in the array.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.includes).*

### Returns
True if the value was found in the array, false otherwise.

### Code Example
```pine
//@version=6
indicator("array.includes example")
a = array.new_float(5,high)
p = close
if array.includes(a, high)
    p := open
plot(p)
```

---

## array.indexof()

The function returns the index of the first occurrence of the value, or -1 if the value is not found.

### Syntax

```pine
array.indexof(id, value) → series int
```

### Arguments

- `value` (*any*) — The value to search in the array.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.indexof).*

### Returns
The index of an element.

### Code Example
```pine
//@version=6
indicator("array.indexof example")
a = array.new_float(5,high)
index = array.indexof(a, high)
plot(index)
```

---

## array.insert()

The function changes the contents of an array by adding new elements in place.

### Syntax

```pine
array.insert(id, index, value) → void
```

### Arguments

- `index` (*series int*) — The index at which to insert the value.
- `value` (*any*) — The value to add to the array.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.insert).*

### Remarks
If the index is positive, the function counts forwards from the beginning of the array to the end. The index of the first element is 0, and the index of the last element is array.size() - 1. If the index is negative, the function counts backwards from the end of the array to the beginning. In this case, the index of the last element is -1, and the index of the first element is negative array.size(). For example, for an array that contains three elements, all of the following are valid arguments for the index parameter: 0, 1, 2, -1, -2, -3.

### Code Example
```pine
//@version=6
indicator("array.insert example")
a = array.new_float(5, close)
array.insert(a, 0, open)
plot(array.get(a, 5))
```

---

## array.join()

The function creates and returns a new string by concatenating all the elements of an array, separated by the specified separator string.

### Syntax

```pine
array.join(id, separator) → series string
```

### Arguments

- `separator` (*series string*) — The string used to separate each array element.
- `id` (*array<int|float|string>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.join).*

### Code Example
```pine
//@version=6
indicator("array.join example")
a = array.new_float(5, 5)
label.new(bar_index, close, array.join(a, ","))
```

---

## array.last()

Returns the array's last element. Throws a runtime error if the array is empty.

### Syntax

```pine
array.last(id) → series type
```

### Arguments

- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.last).*

### Code Example
```pine
//@version=6
indicator("array.last example")
arr = array.new_int(3, 10)
plot(array.last(arr))
```

---

## array.lastindexof()

The function returns the index of the last occurrence of the value, or -1 if the value is not found.

### Syntax

```pine
array.lastindexof(id, value) → series int
```

### Arguments

- `value` (*any*) — The value to search in the array.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.lastindexof).*

### Returns
The index of an element.

### Code Example
```pine
//@version=6
indicator("array.lastindexof example")
a = array.new_float(5,high)
index = array.lastindexof(a, high)
plot(index)
```

---

## array.max()

The function returns the greatest value, or the nth greatest value in a given array.

### Syntax

```pine
array.max(id, nth) → series float|int
array.max(id) → series float|int
array.max(id, nth) → series float|int
```

### Arguments

- `nth` (*series int*, default `0`) — The nth greatest value to return, where zero is the greatest. Optional. The default is 0.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.max).*

### Returns
The greatest or the nth greatest value in the array.

### Code Example
```pine
//@version=6
indicator("array.max")
a = array.from(5, -2, 0, 9, 1)
thirdHighest = array.max(a, 2) // 1
plot(thirdHighest)
```

---

## array.median()

The function returns the median of an array's elements.

### Syntax

```pine
array.median(id) → series float|int
```

### Arguments

- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.median).*

### Returns
The median of the array's elements.

### Code Example
```pine
//@version=6
indicator("array.median example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
plot(array.median(a))
```

---

## array.min()

The function returns the smallest value, or the nth smallest value in a given array.

### Syntax

```pine
array.min(id, nth) → series float|int
array.min(id) → series float|int
array.min(id, nth) → series float|int
```

### Arguments

- `nth` (*series int*, default `0`) — The nth smallest value to return, where zero is the smallest. Optional. The default is 0.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.min).*

### Returns
The smallest or the nth smallest value in the array.

### Code Example
```pine
//@version=6
indicator("array.min")
a = array.from(5, -2, 0, 9, 1)
secondLowest = array.min(a, 1) // 0
plot(secondLowest)
```

---

## array.mode()

The function returns the mode of an array's elements. If there are several values with the same frequency, it returns the smallest value.

### Syntax

```pine
array.mode(id) → series float|int
```

### Arguments

- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.mode).*

### Returns
The most frequently occurring value from the id array. If none exists, returns the smallest value instead.

### Code Example
```pine
//@version=6
indicator("array.mode example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
plot(array.mode(a))
```

---

## array.new_bool()

The function creates a new array object of bool type elements.

### Syntax

```pine
array.new_bool(size, initial_value) → array<bool>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series bool*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_bool).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("array.new_bool example")
length = 5
a = array.new_bool(length, close > open)
plot(array.get(a, 0) ? close : open)
```

---

## array.new_box()

The function creates a new array object of box type elements.

### Syntax

```pine
array.new_box(size, initial_value) → array<box>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series box*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_box).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("array.new_box example")
boxes = array.new_box()
array.push(boxes, box.new(time, close, time+2, low, xloc=xloc.bar_time))
plot(1)
```

---

## array.new_color()

The function creates a new array object of color type elements.

### Syntax

```pine
array.new_color(size, initial_value) → array<color>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series color*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_color).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("array.new_color example")
length = 5
a = array.new_color(length, color.red)
plot(close, color = array.get(a, 0))
```

---

## array.new_float()

The function creates a new array object of float type elements.

### Syntax

```pine
array.new_float(size, initial_value) → array<float>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series int|float*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_float).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("array.new_float example")
length = 5
a = array.new_float(length, close)
plot(array.sum(a) / length)
```

---

## array.new_int()

The function creates a new array object of int type elements.

### Syntax

```pine
array.new_int(size, initial_value) → array<int>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series int*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_int).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("array.new_int example")
length = 5
a = array.new_int(length, int(close))
plot(array.sum(a) / length)
```

---

## array.new_label()

The function creates a new array object of label type elements.

### Syntax

```pine
array.new_label(size, initial_value) → array<label>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series label*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_label).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("array.new_label example", overlay = true, max_labels_count = 500)

//@variable The number of labels to show on the chart.
int labelCount = input.int(50, "Labels to show", 1, 500)

//@variable An array of `label` objects.
var array<label> labelArray = array.new_label()

//@variable A `chart.point` for the new label.
labelPoint = chart.point.from_index(bar_index, close)
//@variable The text in the new label.
string labelText = na
//@variable The color of the new label.
color labelColor = na
//@variable The style of the new label.
string labelStyle = na

// Set the label attributes for rising bars.
if close > open
    labelText  := "Rising"
    labelColor := color.green
    labelStyle := label.style_label_down
// Set the label attributes for falling bars.
else if close < open
    labelText  := "Falling"
    labelColor := color.red
    labelStyle := label.style_label_up

// Add a new label to the `labelArray` when the chart bar closed at a new value.
if close != open
    labelArray.push(label.new(labelPoint, labelText, color = labelColor, style = labelStyle))
// Remove the first element and delete its label when the size of the `labelArray` exceeds the `labelCount`.
if labelArray.size() > labelCount
    label.delete(labelArray.shift())
```

---

## array.new_line()

The function creates a new array object of line type elements.

### Syntax

```pine
array.new_line(size, initial_value) → array<line>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series line*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_line).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("array.new_line example")
// draw last 15 lines
var a = array.new_line()
array.push(a, line.new(bar_index - 1, close[1], bar_index, close))
if array.size(a) > 15
    ln = array.shift(a)
    line.delete(ln)
```

---

## array.new_linefill()

The function creates a new array object of linefill type elements.

### Syntax

```pine
array.new_linefill(size, initial_value) → array<linefill>
```

### Arguments

- `size` (*series int*) — Initial size of an array.
- `initial_value` (*series linefill*) — Initial value of all array elements.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_linefill).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

---

## array.new_string()

The function creates a new array object of string type elements.

### Syntax

```pine
array.new_string(size, initial_value) → array<string>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series string*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_string).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("array.new_string example")
length = 5
a = array.new_string(length, "text")
label.new(bar_index, close, array.get(a, 0))
```

---

## array.new_table()

The function creates a new array object of table type elements.

### Syntax

```pine
array.new_table(size, initial_value) → array<table>
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*series table*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new_table).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0.

### Code Example
```pine
//@version=6
indicator("table array")
tables = array.new_table()
array.push(tables, table.new(position = position.top_left, rows = 1, columns = 2, bgcolor = color.yellow, border_width=1))
plot(1)
```

---

## array.new<type>()

The function creates a new array object of <type> elements.

### Syntax

```pine
array.new<type>(size, initial_value) → type[]
```

### Arguments

- `size` (*series int*, optional, default `0`) — Initial size of an array. Optional. The default is 0.
- `initial_value` (*<array_type>*, optional, default `na`) — Initial value of all array elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.new<type>).*

### Returns
The ID of an array object which may be used in other array.*() functions.

### Remarks
An array index starts from 0. If you want to initialize an array and specify all its elements at the same time, then use the function array.from.

### Code Example
```pine
//@version=6
indicator("array.new<string> example")
a = array.new<string>(1, "Hello, World!")
label.new(bar_index, close, array.get(a, 0))

//@version=6
indicator("array.new<color> example")
a = array.new<color>()
array.push(a, color.red)
array.push(a, color.green)
plot(close, color = array.get(a, close > open ? 1 : 0))

//@version=6
indicator("array.new<float> example")
length = 5
var a = array.new<float>(length, close)
if array.size(a) == length
    array.remove(a, 0)
    array.push(a, close)
plot(array.sum(a) / length, "SMA")

//@version=6
indicator("array.new<line> example")
// draw last 15 lines
var a = array.new<line>()
array.push(a, line.new(bar_index - 1, close[1], bar_index, close))
if array.size(a) > 15
    ln = array.shift(a)
    line.delete(ln)
```

---

## array.percentile_linear_interpolation()

Returns the value for which the specified percentage of array values (percentile) are less than or equal to it, using linear interpolation.

### Syntax

```pine
array.percentile_linear_interpolation(id, percentage) → int|float
array.percentile_linear_interpolation(id, percentage) → series float|int
```

### Arguments

- `percentage` (*series int|float*) — The percentage of values that must be equal or less than the returned value.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.percentile_linear_interpolation).*

### Remarks
In statistics, the percentile is the percent of ranking items that appear at or below a certain score. This measurement shows the percentage of scores within a standard frequency distribution that is lower than the percentile rank you're measuring. Linear interpolation estimates the value between two ranks.

---

## array.percentile_nearest_rank()

Returns the value for which the specified percentage of array values (percentile) are less than or equal to it, using the nearest-rank method.

### Syntax

```pine
array.percentile_nearest_rank(id, percentage) → series float|int
```

### Arguments

- `percentage` (*series int|float*) — The percentage of values that must be equal or less than the returned value.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.percentile_nearest_rank).*

### Remarks
In statistics, the percentile is the percent of ranking items that appear at or below a certain score. This measurement shows the percentage of scores within a standard frequency distribution that is lower than the percentile rank you're measuring.

---

## array.percentrank()

Returns the percentile rank of the element at the specified index.

### Syntax

```pine
array.percentrank(id, index) → series float|int
```

### Arguments

- `index` (*series int*) — The index of the element for which the percentile rank should be calculated.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.percentrank).*

### Remarks
Percentile rank is the percentage of how many elements in the array are less than or equal to the reference value.

---

## array.pop()

The function removes the last element from an array and returns its value.

### Syntax

```pine
array.pop(id) → series type
```

### Arguments

- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.pop).*

### Returns
The value of the removed element.

### Code Example
```pine
//@version=6
indicator("array.pop example")
a = array.new_float(5,high)
removedEl = array.pop(a)
plot(array.size(a))
plot(removedEl)
```

---

## array.push()

The function appends a value to an array.

### Syntax

```pine
array.push(id, value) → void
```

### Arguments

- `value` (*any*) — The value of the element added to the end of the array.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.push).*

### Code Example
```pine
//@version=6
indicator("array.push example")
a = array.new_float(5, 0)
array.push(a, open)
plot(array.get(a, 5))
```

---

## array.range()

The function returns the difference between the min and max values from a given array.

### Syntax

```pine
array.range(id) → series float|int
```

### Arguments

- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.range).*

### Returns
The difference between the min and max values in the array.

### Code Example
```pine
//@version=6
indicator("array.range example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
plot(array.range(a))
```

---

## array.remove()

The function changes the contents of an array by removing the element with the specified index.

### Syntax

```pine
array.remove(id, index) → series type
```

### Arguments

- `index` (*series int*) — The index of the element to remove.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.remove).*

### Returns
The value of the removed element.

### Remarks
If the index is positive, the function counts forwards from the beginning of the array to the end. The index of the first element is 0, and the index of the last element is array.size() - 1. If the index is negative, the function counts backwards from the end of the array to the beginning. In this case, the index of the last element is -1, and the index of the first element is negative array.size(). For example, for an array that contains three elements, all of the following are valid arguments for the index parameter: 0, 1, 2, -1, -2, -3.

### Code Example
```pine
//@version=6
indicator("array.remove example")
a = array.new_float(5,high)
removedEl = array.remove(a, 0)
plot(array.size(a))
plot(removedEl)
```

---

## array.reverse()

The function reverses an array. The first array element becomes the last, and the last array element becomes the first.

### Syntax

```pine
array.reverse(id) → void
```

### Arguments

- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.reverse).*

### Code Example
```pine
//@version=6
indicator("array.reverse example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
plot(array.get(a, 0))
array.reverse(a)
plot(array.get(a, 0))
```

---

## array.set()

The function sets the value of the element at the specified index.

### Syntax

```pine
array.set(id, index, value) → void
```

### Arguments

- `index` (*series int*) — The index of the element to be modified.
- `value` (*any*) — The new value to be set.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.set).*

### Remarks
If the index is positive, the function counts forwards from the beginning of the array to the end. The index of the first element is 0, and the index of the last element is array.size() - 1. If the index is negative, the function counts backwards from the end of the array to the beginning. In this case, the index of the last element is -1, and the index of the first element is negative array.size(). For example, for an array that contains three elements, all of the following are valid arguments for the index parameter: 0, 1, 2, -1, -2, -3.

### Code Example
```pine
//@version=6
indicator("array.set example")
a = array.new_float(10)
for i = 0 to 9
    array.set(a, i, close[i])
plot(array.sum(a) / 10)
```

---

## array.shift()

The function removes an array's first element and returns its value.

### Syntax

```pine
array.shift(id) → series type
```

### Arguments

- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.shift).*

### Returns
The value of the removed element.

### Code Example
```pine
//@version=6
indicator("array.shift example")
a = array.new_float(5,high)
removedEl = array.shift(a)
plot(array.size(a))
plot(removedEl)
```

---

## array.size()

The function returns the number of elements in an array.

### Syntax

```pine
array.size(id) → series int
```

### Arguments

- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.size).*

### Returns
The number of elements in the array.

### Code Example
```pine
//@version=6
indicator("array.size example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
// note that changes in slice also modify original array
slice = array.slice(a, 0, 5)
array.push(slice, open)
// size was changed in slice and in original array
plot(array.size(a))
plot(array.size(slice))
```

---

## array.slice()

The function creates a slice from an existing array. If an object from the slice changes, the changes are applied to both the new and the original arrays.

### Syntax

```pine
array.slice(id, index_from, index_to) → type[]
```

### Arguments

- `index_from` (*series int*) — Zero-based index at which to begin extraction.
- `index_to` (*series int*) — Zero-based index before which to end extraction. The function extracts up to but not including the element with this index.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.slice).*

### Returns
A shallow copy of an array's slice.

### Code Example
```pine
//@version=6
indicator("array.slice example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
// take elements from 0 to 4
// *note that changes in slice also modify original array 
slice = array.slice(a, 0, 5)
plot(array.sum(a) / 10)
plot(array.sum(slice) / 5)
```

---

## array.some()

Returns true if at least one element of the id array is true, false otherwise.

### Syntax

```pine
array.some(id) → series bool
```

### Arguments

- `id` (*array<bool>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.some).*

### Remarks
This function also works with arrays of int and float types, in which case zero values are considered false, and all others true.

---

## array.sort()

The function sorts the elements of an array.

### Syntax

```pine
array.sort(id, order) → void
```

### Arguments

- `order` (*simple sort_order*, optional, default `order.ascending`) — The sort order: order.ascending (default) or order.descending.
- `id` (*array<int|float|string>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.sort).*

### Code Example
```pine
//@version=6
indicator("array.sort example")
a = array.new_float(0,0)
for i = 0 to 5
    array.push(a, high[i])
array.sort(a, order.descending)
if barstate.islast
    label.new(bar_index, close, str.tostring(a))
```

---

## array.sort_indices()

Returns an array of indices which, when used to index the original array, will access its elements in their sorted order. It does not modify the original array.

### Syntax

```pine
array.sort_indices(id, order) → array<int>
```

### Arguments

- `order` (*series sort_order*, optional, default `order.ascending`) — The sort order: order.ascending or order.descending. Optional. The default is order.ascending.
- `id` (*array<int|float|string>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.sort_indices).*

### Code Example
```pine
//@version=6
indicator("array.sort_indices")
a = array.from(5, -2, 0, 9, 1)
sortedIndices = array.sort_indices(a) // [1, 2, 4, 0, 3]
indexOfSmallestValue = array.get(sortedIndices, 0) // 1
smallestValue = array.get(a, indexOfSmallestValue) // -2
plot(smallestValue)
```

---

## array.standardize()

The function returns the array of standardized elements.

### Syntax

```pine
array.standardize(id) → array<float|int>
```

### Arguments

- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.standardize).*

### Returns
The array of standardized elements.

### Code Example
```pine
//@version=6
indicator("array.standardize example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
b = array.standardize(a)
plot(array.min(b))
plot(array.max(b))
```

---

## array.stdev()

The function returns the standard deviation of an array's elements.

### Syntax

```pine
array.stdev(id, biased) → series float|int
```

### Arguments

- `biased` (*series bool*, optional, default `true`) — Determines which estimate should be used. Optional. The default is true.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.stdev).*

### Returns
The standard deviation of the array's elements.

### Remarks
If biased is true, function will calculate using a biased estimate of the entire population, if false - unbiased estimate of a sample.

### Code Example
```pine
//@version=6
indicator("array.stdev example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
plot(array.stdev(a))
```

---

## array.sum()

The function returns the sum of an array's elements.

### Syntax

```pine
array.sum(id) → series float|int
```

### Arguments

- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.sum).*

### Returns
The sum of the array's elements.

### Code Example
```pine
//@version=6
indicator("array.sum example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
plot(array.sum(a))
```

---

## array.unshift()

The function inserts the value at the beginning of the array.

### Syntax

```pine
array.unshift(id, value) → void
```

### Arguments

- `value` (*any*) — The value to add to the start of the array.
- `id` (*any[]*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.unshift).*

### Code Example
```pine
//@version=6
indicator("array.unshift example")
a = array.new_float(5, 0)
array.unshift(a, open)
plot(array.get(a, 0))
```

---

## array.variance()

The function returns the variance of an array's elements.

### Syntax

```pine
array.variance(id, biased) → series float|int
```

### Arguments

- `biased` (*series bool*, optional, default `true`) — Determines which estimate should be used. Optional. The default is true.
- `id` (*array<int|float>*) — An array object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_array.variance).*

### Returns
The variance of the array's elements.

### Remarks
If biased is true, function will calculate using a biased estimate of the entire population, if false - unbiased estimate of a sample.

### Code Example
```pine
//@version=6
indicator("array.variance example")
a = array.new_float(0)
for i = 0 to 9
    array.push(a, close[i])
plot(array.variance(a))
```

---

## barcolor()

Set color of bars.

### Syntax

```pine
barcolor(color, offset, editable, show_last, title, display) → void
```

### Arguments

- `color` (*series color*, default `color.blue`) — Color of bars. You can use constants like 'red' or '#ff001a' as well as complex expressions like 'close >= open ? color.green : color.red'. Required argument.
- `offset` (*series int*, optional, default `0`) — Shifts the color series to the left or to the right on the given number of bars. Default is 0.
- `editable` (*const bool*, optional, default `true`) — If true then barcolor style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of bars (from the last bar back to the past) to fill on chart.
- `title` (*const string*, optional) — Title of the barcolor. Optional argument.
- `display` (*input plot_simple_display*, optional, default `display.all`) — Controls where the barcolor is displayed. Possible values are: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_barcolor).*

### Code Example
```pine
//@version=6
indicator("barcolor example", overlay=true)
barcolor(close < open ? color.black : color.white)
```

---

## bgcolor()

Fill background of bars with specified color.

### Syntax

```pine
bgcolor(color, offset, editable, show_last, title, force_overlay) → void
```

### Arguments

- `color` (*series color*) — Color of the filled background. You can use constants like 'red' or '#ff001a' as well as complex expressions like 'close >= open ? color.green : color.red'. Required argument.
- `offset` (*series int*, optional, default `0`) — Shifts the color series to the left or to the right on the given number of bars. Default is 0.
- `editable` (*const bool*, optional, default `true`) — If true then bgcolor style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of bars (from the last bar back to the past) to fill on chart.
- `title` (*const string*, optional) — Title of the bgcolor. Optional argument.
- `display` (*input plot_simple_display*, optional, default `display.all`) — Controls where the bgcolor is displayed. Possible values are: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_bgcolor).*

### Code Example
```pine
//@version=6
indicator("bgcolor example", overlay=true)
bgcolor(close < open ? color.new(color.red,70) : color.new(color.green, 70))
```

---

## bool()

Converts the x value to a bool value. Returns false if x is na, false, or an int/float value equal to 0. Returns true for all other possible values.

### Syntax

```pine
bool
bool(x) → series bool
```

### Arguments

- `x` (*series color*) — 'na' to cast to color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_bool).*

### Returns
The value of the argument after casting to bool.

---

## box()

Casts na to box.

### Syntax

```pine
box
box(x) → series box
```

### Arguments

- `x` (*series box*) — 'na' to cast to box.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box).*

### Returns
The value of the argument after casting to box.

---

## box.copy()

Clones the box object.

### Syntax

```pine
box.copy(id) → series box
```

### Arguments

- `id` (*series box*) — Box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.copy).*

### Code Example
```pine
//@version=6
indicator('Last 50 bars price ranges', overlay = true)
LOOKBACK = 50
highest = ta.highest(LOOKBACK)
lowest = ta.lowest(LOOKBACK)
if barstate.islastconfirmedhistory
    var BoxLast = box.new(bar_index[LOOKBACK], highest, bar_index, lowest, bgcolor = color.new(color.green, 80))
    var BoxPrev = box.copy(BoxLast)
    box.set_lefttop(BoxPrev, bar_index[LOOKBACK * 2], highest[50])
    box.set_rightbottom(BoxPrev, bar_index[LOOKBACK], lowest[50])
    box.set_bgcolor(BoxPrev, color.new(color.red, 80))
```

---

## box.delete()

Deletes the specified box object. If it has already been deleted, does nothing.

---

### Syntax

```pine
box.delete(id) → void
```

### Arguments

- `id` (*series box*) — A box object to delete.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.delete).*

## box.get_bottom()

Returns the price value of the bottom border of the box.

### Syntax

```pine
box.get_bottom(id) → series float
```

### Arguments

- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.get_bottom).*

### Returns
The price value.

---

## box.get_left()

Returns the bar index or the UNIX time (depending on the last value used for 'xloc') of the left border of the box.

### Syntax

```pine
box.get_left(id) → series int
```

### Arguments

- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.get_left).*

### Returns
A bar index or a UNIX timestamp (in milliseconds).

---

## box.get_right()

Returns the bar index or the UNIX time (depending on the last value used for 'xloc') of the right border of the box.

### Syntax

```pine
box.get_right(id) → series int
```

### Arguments

- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.get_right).*

### Returns
A bar index or a UNIX timestamp (in milliseconds).

---

## box.get_top()

Returns the price value of the top border of the box.

### Syntax

```pine
box.get_top(id) → series float
```

### Arguments

- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.get_top).*

### Returns
The price value.

---

## box.new()

Creates a new box object.

### Syntax

```pine
box.new(top_left, bottom_right, border_color, border_width, border_style, extend, xloc, bgcolor, text, text_size, text_color, text_halign, text_valign, text_wrap, text_font_family, force_overlay, text_formatting) → series box
box.new(left, top, right, bottom, border_color, border_width, border_style, extend, xloc, bgcolor, text, text_size, text_color, text_halign, text_valign, text_wrap, text_font_family, force_overlay, text_formatting) → series box
```

### Arguments

- `left` (*series int*) — Bar index (if xloc = [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index)) or UNIX time (if xloc = [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time)) of the left border of the box. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `top` (*series int|float*) — Price of the top border of the box.
- `right` (*series int*) — Bar index (if xloc = [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index)) or UNIX time (if xloc = [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time)) of the right border of the box. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `bottom` (*series int|float*) — Price of the bottom border of the box.
- `border_color` (*series color*, optional, default `color.blue`) — Color of the four borders. Optional. The default is [color.blue](https://www.tradingview.com/pine-script-reference/v6/#var_color.blue).
- `border_width` (*series int*, optional, default `1`) — Width of the four borders, in pixels. Optional. The default is 1 pixel.
- `border_style` (*series string*, optional, default `line.style_solid`) — Style of the four borders. Possible values: [line.style_solid](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_solid), [line.style_dotted](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_dotted), [line.style_dashed](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_dashed). Optional. The default value is [line.style_solid](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_solid).
- `extend` (*series string*, optional, default `extend.none`) — When [extend.none](https://www.tradingview.com/pine-script-reference/v6/#var_extend.none) is used, the horizontal borders start at the left border and end at the right border. With [extend.left](https://www.tradingview.com/pine-script-reference/v6/#var_extend.left) or [extend.right](https://www.tradingview.com/pine-script-reference/v6/#var_extend.right), the horizontal borders are extended indefinitely to the left or right of the box, respectively. With [extend.both](https://www.tradingview.com/pine-script-reference/v6/#var_extend.both), the horizontal borders are extended on both sides. Optional. The default value is [extend.none](https://www.tradingview.com/pine-script-reference/v6/#var_extend.none).
- `xloc` (*series string*, optional, default `xloc.bar_index`) — Determines whether the arguments to 'left' and 'right' are a bar index or a time value. If xloc = [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index), the arguments must be a bar index. If xloc = [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time), the arguments must be a UNIX time. Possible values: [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) and [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time). Optional. The default is [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index).
- `bgcolor` (*series color*, optional, default `color.blue`) — Background color of the box. Optional. The default is [color.blue](https://www.tradingview.com/pine-script-reference/v6/#var_color.blue).
- `text` (*series string*, optional, default `""`) — The text to be displayed inside the box. Optional. The default is empty string.
- `text_size` (*series string*, optional, default `size.auto`) — The size of the text. An optional parameter, the default value is [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto). Possible values: [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v6/#var_size.tiny), [size.small](https://www.tradingview.com/pine-script-reference/v6/#var_size.small), [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal), [size.large](https://www.tradingview.com/pine-script-reference/v6/#var_size.large), [size.huge](https://www.tradingview.com/pine-script-reference/v6/#var_size.huge).
- `text_font_family` (*series string*, optional, default `font.family_default`) — The font family of the text. Optional. The default value is [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default). Possible values: [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default), [font.family_monospace](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_monospace).
- `text_color` (*series color*, optional, default `color.black`) — The color of the text. Optional. The default is [color.black](https://www.tradingview.com/pine-script-reference/v6/#var_color.black).
- `text_halign` (*series string*, optional, default `text.align_center`) — The horizontal alignment of the box’s text. Optional. The default value is [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center). Possible values: [text.align_left](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_left), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_right](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_right).
- `text_valign` (*series string*, optional, default `text.align_center`) — The vertical alignment of the box’s text. Optional. The default value is [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center). Possible values: [text.align_top](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_top), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_bottom](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_bottom).
- `text_wrap` (*series string*, optional, default `text.wrap_none`) — Defines whether the text is presented in a single line, extending past the width of the box if necessary, or wrapped so every line is no wider than the box itself (and clipped by the bottom border of the box if the height of the resulting wrapped text is higher than the height of the box). Optional. The default value is [text.wrap_none](https://www.tradingview.com/pine-script-reference/v6/#var_text.wrap_none). Possible values: [text.wrap_none](https://www.tradingview.com/pine-script-reference/v6/#var_text.wrap_none), [text.wrap_auto](https://www.tradingview.com/pine-script-reference/v6/#var_text.wrap_auto).
- `top_left` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object that specifies the top-left corner location of the box.
- `bottom_right` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object that specifies the bottom-right corner location of the box.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.new).*

### Returns
The ID of a box object which may be used in box.set_*() and box.get_*() functions.

### Code Example
```pine
//@version=6
indicator("box.new")
var b = box.new(time, open, time + 60 * 60 * 24, close, xloc=xloc.bar_time, border_style=line.style_dashed)
box.set_lefttop(b, time, 100)
box.set_rightbottom(b, time + 60 * 60 * 24, 500)
box.set_bgcolor(b, color.green)
```

---

## box.set_bgcolor()

Sets the background color of the box.

---

### Syntax

```pine
box.set_bgcolor(id, color) → void
```

### Arguments

- `color` (*series color*) — New background color.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_bgcolor).*

## box.set_border_color()

Sets the border color of the box.

---

### Syntax

```pine
box.set_border_color(id, color) → void
```

### Arguments

- `color` (*series color*) — New border color.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_border_color).*

## box.set_border_style()

Sets the border style of the box.

---

### Syntax

```pine
box.set_border_style(id, style) → void
```

### Arguments

- `style` (*series string*) — New border style.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_border_style).*

## box.set_border_width()

Sets the border width of the box.

---

### Syntax

```pine
box.set_border_width(id, width) → void
```

### Arguments

- `width` (*series int*) — Width of the four borders, in pixels.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_border_width).*

## box.set_bottom()

Sets the bottom coordinate of the box.

---

### Syntax

```pine
box.set_bottom(id, bottom) → void
```

### Arguments

- `bottom` (*series int|float*) — Price value of the bottom border.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_bottom).*

## box.set_bottom_right_point()

Sets the bottom-right corner location of the id box to point.

---

### Syntax

```pine
box.set_bottom_right_point(id, point) → void
```

### Arguments

- `point` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object.
- `id` (*series box*) — A [box](https://www.tradingview.com/pine-script-reference/v6/#op_box) object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_bottom_right_point).*

## box.set_extend()

Sets extending type of the border of this box object. When extend.none is used, the horizontal borders start at the left border and end at the right border. With extend.left or extend.right, the horizontal borders are extended indefinitely to the left or right of the box, respectively. With extend.both, the horizontal borders are extended on both sides.

---

### Syntax

```pine
box.set_extend(id, extend) → void
```

### Arguments

- `extend` (*series string*) — New extending type.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_extend).*

## box.set_left()

Sets the left coordinate of the box.

---

### Syntax

```pine
box.set_left(id, left) → void
```

### Arguments

- `left` (*series int*) — Bar index or bar time of the left border. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_left).*

## box.set_lefttop()

Sets the left and top coordinates of the box.

---

### Syntax

```pine
box.set_lefttop(id, left, top) → void
```

### Arguments

- `left` (*series int*) — Bar index or bar time of the left border.
- `top` (*series int|float*) — Price value of the top border.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_lefttop).*

## box.set_right()

Sets the right coordinate of the box.

---

### Syntax

```pine
box.set_right(id, right) → void
```

### Arguments

- `right` (*series int*) — Bar index or bar time of the right border. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_right).*

## box.set_rightbottom()

Sets the right and bottom coordinates of the box.

---

### Syntax

```pine
box.set_rightbottom(id, right, bottom) → void
```

### Arguments

- `right` (*series int*) — Bar index or bar time of the right border.
- `bottom` (*series int|float*) — Price value of the bottom border.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_rightbottom).*

## box.set_text()

The function sets the text in the box.

---

### Syntax

```pine
box.set_text(id, text) → void
```

### Arguments

- `text` (*series string*) — The text to be displayed inside the box.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_text).*

## box.set_text_color()

The function sets the color of the text inside the box.

---

### Syntax

```pine
box.set_text_color(id, text_color) → void
```

### Arguments

- `text_color` (*series color*) — The color of the text.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_text_color).*

## box.set_text_font_family()

The function sets the font family of the text inside the box.

### Syntax

```pine
box.set_text_font_family(id, text_font_family) → void
```

### Arguments

- `text_font_family` (*series string*, default `font.family_default`) — The font family of the text. Possible values: [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default), [font.family_monospace](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_monospace).
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_text_font_family).*

### Code Example
```pine
//@version=6
indicator("Example of setting the box font")
if barstate.islastconfirmedhistory
    b = box.new(bar_index, open-ta.tr, bar_index-50, open-ta.tr*5, text="monospace")
    box.set_text_font_family(b, font.family_monospace)
```

---

## box.set_text_formatting()

Sets the formatting attributes the drawing applies to displayed text.

---

## box.set_text_halign()

The function sets the horizontal alignment of the box's text.

---

### Syntax

```pine
box.set_text_halign(id, text_halign) → void
```

### Arguments

- `text_halign` (*series string*, default `text.align_left`) — The horizontal alignment of a box’s text. Possible values: [text.align_left](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_left), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_right](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_right).
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_text_halign).*

## box.set_text_size()

The function sets the size of the box's text.

---

### Syntax

```pine
box.set_text_size(id, text_size) → void
```

### Arguments

- `text_size` (*series string*) — The size of the text. Possible values: [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v6/#var_size.tiny), [size.small](https://www.tradingview.com/pine-script-reference/v6/#var_size.small), [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal), [size.large](https://www.tradingview.com/pine-script-reference/v6/#var_size.large), [size.huge](https://www.tradingview.com/pine-script-reference/v6/#var_size.huge).
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_text_size).*

## box.set_text_valign()

The function sets the vertical alignment of a box's text.

---

### Syntax

```pine
box.set_text_valign(id, text_valign) → void
```

### Arguments

- `text_valign` (*series string*, default `text.align_center`) — The vertical alignment of the box’s text. Possible values: [text.align_top](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_top), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_bottom](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_bottom).
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_text_valign).*

## box.set_text_wrap()

The function sets the mode of wrapping of the text inside the box.

---

### Syntax

```pine
box.set_text_wrap(id, text_wrap) → void
```

### Arguments

- `text_wrap` (*series string*) — The mode of the wrapping. Possible values: [text.wrap_auto](https://www.tradingview.com/pine-script-reference/v6/#var_text.wrap_auto), [text.wrap_none](https://www.tradingview.com/pine-script-reference/v6/#var_text.wrap_none).
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_text_wrap).*

## box.set_top()

Sets the top coordinate of the box.

---

### Syntax

```pine
box.set_top(id, top) → void
```

### Arguments

- `top` (*series int|float*) — Price value of the top border.
- `id` (*series box*) — A box object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_top).*

## box.set_top_left_point()

Sets the top-left corner location of the id box to point.

---

### Syntax

```pine
box.set_top_left_point(id, point) → void
```

### Arguments

- `point` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object.
- `id` (*series box*) — A [box](https://www.tradingview.com/pine-script-reference/v6/#op_box) object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_box.set_top_left_point).*

## box.set_xloc()

Sets the left and right borders of a box and updates its xloc property.

---

## chart.point.copy()

Creates a copy of a chart.point object with the specified id.

---

### Syntax

```pine
chart.point.copy(id) → chart.point
```

### Arguments

- `id` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.copy).*

## chart.point.from_index()

Returns a chart.point object with index as its x-coordinate and price as its y-coordinate.

### Syntax

```pine
chart.point.from_index(index, price) → chart.point
```

### Arguments

- `index` (*series int*) — The x-coordinate of the point, expressed as a bar index value.
- `price` (*series int|float*) — The y-coordinate of the point.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.from_index).*

### Remarks
The time field values of chart.point instances returned from this function will be na, meaning drawing objects with xloc values set to xloc.bar_time will not work with them.

---

## chart.point.from_time()

Returns a chart.point object with time as its x-coordinate and price as its y-coordinate.

### Syntax

```pine
chart.point.from_time(time, price) → chart.point
```

### Arguments

- `time` (*series int*) — The x-coordinate of the point, expressed as a UNIX time value.
- `price` (*series int|float*) — The y-coordinate of the point.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.from_time).*

### Remarks
The index field values of chart.point instances returned from this function will be na, meaning drawing objects with xloc values set to xloc.bar_index will not work with them.

---

## chart.point.new()

Creates a new chart.point object with the specified time, index, and price.

### Syntax

```pine
chart.point.new(time, index, price) → chart.point
```

### Arguments

- `time` (*series int*) — The x-coordinate of the point, expressed as a UNIX time value.
- `index` (*series int*) — The x-coordinate of the point, expressed as a bar index value.
- `price` (*series int/float*) — The y-coordinate of the point.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.new).*

### Remarks
Whether a drawing object uses a point's time or index field as an x-coordinate depends on the xloc type used in the function call that returned the drawing. It's important to note that this function does not verify that the time and index values refer to the same bar.

---

## chart.point.now()

Returns a chart.point object with price as the y-coordinate

### Syntax

```pine
chart.point.now(price) → chart.point
```

### Arguments

- `price` (*series int|float*, optional, default `close`) — The y-coordinate of the point. Optional. The default is [close](https://www.tradingview.com/pine-script-reference/v6/#var_close).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_chart.point.now).*

### Remarks
The chart.point instance returned from this function records values for its index and time fields on the bar it executed on, making it suitable for use with drawing objects of any xloc type.

---

## color()

Casts na to color

### Syntax

```pine
color
color(x) → series color
```

### Arguments

- `x` (*series color*) — 'na' to cast to color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_color).*

### Returns
The value of the argument after casting to color.

---

## color.b()

Retrieves the value of the color's blue component.

### Syntax

```pine
color.b(color) → series float
```

### Arguments

- `color` (*series color*) — Color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_color.b).*

### Returns
The value (0 to 255) of the color's blue component.

### Code Example
```pine
//@version=6
indicator("color.b", overlay=true)
plot(color.b(color.blue))
```

---

## color.from_gradient()

Based on the relative position of value in the bottom_value to top_value range, the function returns a color from the gradient defined by bottom_color to top_color.

### Syntax

```pine
color.from_gradient(value, bottom_value, top_value, bottom_color, top_color) → series color
```

### Arguments

- `value` (*series int|float*) — Value to calculate the position-dependent color.
- `bottom_value` (*series int|float*) — Bottom position value corresponding to bottom_color.
- `top_value` (*series int|float*) — Top position value corresponding to top_color.
- `bottom_color` (*series color*) — Bottom position color.
- `top_color` (*series color*) — Top position color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_color.from_gradient).*

### Returns
A color calculated from the linear gradient between bottom_color to top_color.

### Remarks
Using this function will have an impact on the colors displayed in the script's "Settings/Style" tab. See the User Manual for more information.

### Code Example
```pine
//@version=6
indicator("color.from_gradient", overlay=true)
color1 = color.from_gradient(close, low, high, color.yellow, color.lime)
color2 = color.from_gradient(ta.rsi(close, 7), 0, 100, color.rgb(255, 0, 0), color.rgb(0, 255, 0, 50))
plot(close, color=color1)
plot(ta.rsi(close,7), color=color2)
```

---

## color.g()

Retrieves the value of the color's green component.

### Syntax

```pine
color.g(color) → series float
```

### Arguments

- `color` (*series color*) — Color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_color.g).*

### Returns
The value (0 to 255) of the color's green component.

### Code Example
```pine
//@version=6
indicator("color.g", overlay=true)
plot(color.g(color.green))
```

---

## color.new()

Function color applies the specified transparency to the given color.

### Syntax

```pine
color.new(color, transp) → series color
```

### Arguments

- `color` (*series color*) — Color to apply transparency to.
- `transp` (*series int|float*) — Possible values are from 0 (not transparent) to 100 (invisible).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_color.new).*

### Returns
Color with specified transparency.

### Remarks
Using arguments that are not constants (e.g., 'simple', 'input' or 'series') will have an impact on the colors displayed in the script's "Settings/Style" tab. See the User Manual for more information.

### Code Example
```pine
//@version=6
indicator("color.new", overlay=true)
plot(close, color=color.new(color.red, 50))
```

---

## color.r()

Retrieves the value of the color's red component.

### Syntax

```pine
color.r(color) → series float
```

### Arguments

- `color` (*series color*) — Color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_color.r).*

### Returns
The value (0 to 255) of the color's red component.

### Code Example
```pine
//@version=6
indicator("color.r", overlay=true)
plot(color.r(color.red))
```

---

## color.rgb()

Creates a new color with transparency using the RGB color model.

### Syntax

```pine
color.rgb(red, green, blue, transp) → series color
```

### Arguments

- `red` (*series int|float*) — Red color component. Possible values are from 0 to 255.
- `green` (*series int|float*) — Green color component. Possible values are from 0 to 255.
- `blue` (*series int|float*) — Blue color component. Possible values are from 0 to 255.
- `transp` (*series int|float*, optional, default `0`) — Optional. Color transparency. Possible values are from 0 (opaque) to 100 (invisible). Default value is 0.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_color.rgb).*

### Returns
Color with specified transparency.

### Remarks
Using arguments that are not constants (e.g., 'simple', 'input' or 'series') will have an impact on the colors displayed in the script's "Settings/Style" tab. See the User Manual for more information.

### Code Example
```pine
//@version=6
indicator("color.rgb", overlay=true)
plot(close, color=color.rgb(255, 0, 0, 50))
```

---

## color.t()

Retrieves the color's transparency.

### Syntax

```pine
color.t(color) → series float
```

### Arguments

- `color` (*series color*) — Color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_color.t).*

### Returns
The value (0-100) of the color's transparency.

### Code Example
```pine
//@version=6
indicator("color.t", overlay=true)
plot(color.t(color.new(color.red, 50)))
```

---

## dayofmonth()

### Syntax

```pine
dayofmonth(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_dayofmonth).*

### Returns
Day of month (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970. Note that this function returns the day based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00 UTC-4) this value can be lower by 1 than the day of the trading day.

---

## dayofweek()

### Syntax

```pine
dayofweek(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_dayofweek).*

### Returns
Day of week (in exchange timezone) for provided UNIX time.

### Remarks
Note that this function returns the day based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the day of the trading day. UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

---

## fill()

Fills background between two plots or hlines with a given color.

### Syntax

```pine
fill(plot1, plot2, color, title, editable, show_last, fillgaps) → void
fill(hline1, hline2, color, title, editable, fillgaps) → void
```

### Arguments

- `hline1` (*hline*) — The first hline object. Required argument.
- `hline2` (*hline*) — The second hline object. Required argument.
- `plot1` (*plot*) — The first plot object. Required argument.
- `plot2` (*plot*) — The second plot object. Required argument.
- `color` (*series color*, optional) — Color of the background fill. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `title` (*const string*, optional) — Title of the created fill object. Optional argument.
- `editable` (*const bool*, optional, default `true`) — If true then fill style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of bars (from the last bar back to the past) to fill on chart.
- `fillgaps` (*const bool*, optional, default `false`) — Controls continuing fills on gaps, i.e., when one of the plot() calls returns an na value. When true, the last fill will continue on gaps. The default is false.
- `display` (*input plot_simple_display*, optional, default `display.all`) — Controls where the fill is displayed. Possible values are: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).
- `top_value` (*series int|float*) — Value where the gradient uses the `top_color`.
- `bottom_value` (*series int|float*) — Value where the gradient uses the `bottom_color`.
- `top_color` (*series color*) — Color of the gradient at the topmost value.
- `bottom_color` (*series color*) — Color of the gradient at the bottommost value.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_fill).*

### Code Example
```pine
//@version=6
indicator("Fill between hlines", overlay = false)
h1 = hline(20)
h2 = hline(10)
fill(h1, h2, color = color.new(color.blue, 90))

//@version=6
indicator("Fill between plots", overlay = true)
p1 = plot(open)
p2 = plot(close)
fill(p1, p2, color = color.new(color.green, 90))

//@version=6
indicator("Gradient Fill between hlines", overlay = false)
topVal = input.int(100)
botVal = input.int(0)
topCol = input.color(color.red)
botCol = input.color(color.blue)
topLine = hline(100, color = topCol, linestyle = hline.style_solid)
botLine = hline(0,   color = botCol, linestyle = hline.style_solid)
fill(topLine, botLine, topVal, botVal, topCol, botCol)
```

---

## fixnan()

For a given series replaces NaN values with previous nearest non-NaN value.

### Syntax

```pine
fixnan(source) → series float|int|bool|color
```

### Arguments

- `source` (*series int|float|bool|color*) — Source used for the calculation.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_fixnan).*

### Returns
Series without na gaps.

---

## float()

Casts na to float

### Syntax

```pine
float
float(x) → series float
```

### Arguments

- `x` (*series float*) — 'na' to cast to float.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_float).*

### Returns
The value of the argument after casting to float.

---

## hline()

Renders a horizontal line at a given fixed price level.

### Syntax

```pine
hline(price, title, color, linestyle, linewidth, editable, display) → hline
```

### Arguments

- `price` (*input int|float*) — Price value at which the object will be rendered. Required argument.
- `title` (*const string*) — Title of the object.
- `color` (*input color*, optional) — Color of the rendered line. Must be a constant value (not an expression). Optional argument.
- `linestyle` (*input hline_style*, optional, default `hline.style_solid`) — Style of the rendered line. Possible values are: [hline.style_solid](https://www.tradingview.com/pine-script-reference/v6/#var_hline.style_solid), [hline.style_dotted](https://www.tradingview.com/pine-script-reference/v6/#var_hline.style_dotted), [hline.style_dashed](https://www.tradingview.com/pine-script-reference/v6/#var_hline.style_dashed). Optional argument.
- `linewidth` (*input int*, optional, default `1`) — Width of the rendered line. Default value is 1.
- `editable` (*const bool*, optional, default `true`) — If true then hline style will be editable in Format dialog. Default is true.
- `display` (*input plot_simple_display*, optional, default `display.all`) — Controls where the hline is displayed. Possible values are: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_hline).*

### Returns
An hline object, that can be used in fill

### Code Example
```pine
//@version=6
indicator("input.hline", overlay=true)
hline(3.14, title='Pi', color=color.blue, linestyle=hline.style_dotted, linewidth=2)

// You may fill the background between any two hlines with a fill() function:
h1 = hline(20)
h2 = hline(10)
fill(h1, h2, color=color.new(color.green, 90))
```

---

## hour()

### Syntax

```pine
hour(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_hour).*

### Returns
Hour (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

---

## indicator()

This declaration statement designates the script as an indicator and sets a number of indicator-related properties.

### Syntax

```pine
indicator(title, shorttitle, overlay, format, precision, scale, max_bars_back, timeframe, timeframe_gaps, explicit_plot_zorder, max_lines_count, max_labels_count, max_boxes_count, calc_bars_count, max_polylines_count, dynamic_requests, behind_chart) → void
```

### Arguments

- `title` (*const string*) — The title of the script. It is displayed on the chart when no `shorttitle` argument is used, and becomes the publication’s default title when publishing the script.
- `shorttitle` (*const string*, optional) — The script’s display name on charts. If specified, it will replace the `title` argument in most chart-related windows. Optional. The default is the argument used for `title`.
- `overlay` (*const bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the indicator will be displayed over the chart. If [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), it will be added in a separate pane. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `format` (*const string*, optional, default `format.inherit`) — Specifies the formatting of the script’s displayed values. Possible values: [format.inherit](https://www.tradingview.com/pine-script-reference/v6/#var_format.inherit), [format.price](https://www.tradingview.com/pine-script-reference/v6/#var_format.price), [format.volume](https://www.tradingview.com/pine-script-reference/v6/#var_format.volume), [format.percent](https://www.tradingview.com/pine-script-reference/v6/#var_format.percent). Optional. The default is [format.inherit](https://www.tradingview.com/pine-script-reference/v6/#var_format.inherit).
- `precision` (*const int*, optional, default `syminfo.pricescale`) — Specifies the number of digits after the floating point of the script’s displayed values. Must be a non-negative integer no greater than 16. If `format` is set to [format.inherit](https://www.tradingview.com/pine-script-reference/v6/#var_format.inherit) and `precision` is specified, the format will instead be set to [format.price](https://www.tradingview.com/pine-script-reference/v6/#var_format.price). Optional. The default is inherited from the precision of the chart’s symbol.
- `scale` (*const scale_type*, optional, default `scale.right`) — The price scale used. Possible values: [scale.right](https://www.tradingview.com/pine-script-reference/v6/#var_scale.right), [scale.left](https://www.tradingview.com/pine-script-reference/v6/#var_scale.left), [scale.none](https://www.tradingview.com/pine-script-reference/v6/#var_scale.none). The [scale.none](https://www.tradingview.com/pine-script-reference/v6/#var_scale.none) value can only be applied in combination with `overlay = true`. Optional. By default, the script uses the same scale as the chart.
- `max_bars_back` (*const int*, optional, default `0`) — The length of the historical buffer the script keeps for every variable and function, which determines how many past values can be referenced using the `[]` history-referencing operator. The required buffer size is automatically detected by the Pine Script™ runtime. Using this parameter is only necessary when a runtime error occurs because automatic detection fails. More information on the underlying mechanics of the historical buffer can be found [in our Help Center](https://www.tradingview.com/chart/?solution=43000587849). Optional. The default is 0.
- `timeframe` (*const string*, optional, default `timeframe.period`) — Adds multi-timeframe functionality to simple scripts. When used, a "Timeframe" field will be added to the script’s "Settings/Inputs" tab. The field’s default value will be the argument supplied, whose format must conform to [timeframe string specifications](https://www.tradingview.com/pine-script-docs/en/v5/concepts/Timeframes.html#timeframe-string-specifications). To specify the chart’s timeframe, use an empty string or the [timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period) variable. The parameter cannot be used with scripts using Pine Script™ drawings. Optional. The default is [timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period).
- `timeframe_gaps` (*const bool*, optional, default `true`) — Specifies how the indicator’s values are displayed on chart bars when the `timeframe` is higher than the chart’s. If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), a value only appears on a chart bar when the higher `timeframe` value becomes available, otherwise [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) is returned (thus a "gap" occurs). With [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), what would otherwise be gaps are filled with the latest known value returned, avoiding [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values. When used, a "Gaps" checkbox will appear in the indicator’s "Settings/Inputs" tab. Optional. The default is [true](https://www.tradingview.com/pine-script-reference/v6/#op_true).
- `explicit_plot_zorder` (*const bool*, optional, default `false`) — Specifies the order in which the script’s plots, fills, and hlines are rendered. If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), plots are drawn in the order in which they appear in the script’s code, each newer plot being drawn above the previous ones. This only applies to `plot*()` functions, [fill](https://www.tradingview.com/pine-script-reference/v6/#fun_fill), and [hline](https://www.tradingview.com/pine-script-reference/v6/#fun_hline). Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `max_lines_count` (*const int*, optional, default `50`) — The number of last [line](https://www.tradingview.com/pine-script-reference/v6/#op_line) drawings displayed. Possible values: 1-500. The count is approximate; more drawings than the specified count may be displayed. Optional. The default is 50.
- `max_labels_count` (*const int*, optional, default `50`) — The number of last [label](https://www.tradingview.com/pine-script-reference/v6/#op_label) drawings displayed. Possible values: 1-500. The count is approximate; more drawings than the specified count may be displayed. Optional. The default is 50.
- `max_boxes_count` (*const int*, optional, default `50`) — The number of last [box](https://www.tradingview.com/pine-script-reference/v6/#op_box) drawings displayed. Possible values: 1-500. The count is approximate; more drawings than the specified count may be displayed. Optional. The default is 50.
- `max_polylines_count` (*const int*, optional, default `50`) — The number of last [polyline](https://www.tradingview.com/pine-script-reference/v6/#op_polyline) drawings displayed. Possible values: 1-100. The count is approximate; more drawings than the specified count may be displayed. Optional. The default is 50.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_indicator).*

### Remarks
Every indicator script must have one indicator call.

### Code Example
```pine
//@version=6
indicator("My script", shorttitle="Script")
plot(close)
```

---

## input()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function automatically detects the type of the argument used for 'defval' and uses the corresponding input widget.

### Syntax

```pine
input(defval, title, tooltip, inline, group, display, active) → input int/float/bool/color/string | series float
```

### Arguments

- `defval` (*const int|float|bool|string|color|<open|high|low|close|hl2|hlc3|ohlc4|hlcc4>*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where script users can change it. Source-type built-ins are built-in series float variables that specify the source of the calculation: `close`, `hlc3`, etc.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `display` (*const plot_display*, optional, default `display.none`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default depends on the type of the value passed to `defval`: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none) for [bool](https://www.tradingview.com/pine-script-reference/v6/#op_bool) and [color](https://www.tradingview.com/pine-script-reference/v6/#op_color) values, [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all) for everything else.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input).*

### Returns
Value of input variable.

### Remarks
Result of input function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input", overlay=true)
i_switch = input(true, "On/Off")
plot(i_switch ? open : na)

i_len = input(7, "Length")
i_src = input(close, "Source")
plot(ta.sma(i_src, i_len))

i_border = input(142.50, "Price Border")
hline(i_border)
bgcolor(close > i_border ? color.green : color.red)

i_col = input(color.red, "Plot Color")
plot(close, color=i_col)

i_text = input("Hello!", "Message")
l = label.new(bar_index, high, text=i_text)
label.delete(l[1])
```

---

## input.bool()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a checkmark to the script's inputs.

### Syntax

```pine
input.bool(defval, title, tooltip, inline, group, confirm, display) → input bool
```

### Arguments

- `defval` (*const bool*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.none`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.bool).*

### Returns
Value of input variable.

### Remarks
Result of input.bool function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.bool", overlay=true)
i_switch = input.bool(true, "On/Off")
plot(i_switch ? open : na)
```

---

## input.color()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a color picker that allows the user to select a color and transparency, either from a palette or a hex value.

### Syntax

```pine
input.color(defval, title, tooltip, inline, group, confirm, display) → input color
```

### Arguments

- `defval` (*const color*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.none`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.color).*

### Returns
Value of input variable.

### Remarks
Result of input.color function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.color", overlay=true)
i_col = input.color(color.red, "Plot Color")
plot(close, color=i_col)
```

---

## input.enum()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a dropdown with options based on the enum fields passed to its defval and options parameters.

### Returns
Value of input variable.

### Remarks
All fields included in the defval and options arguments must belong to the same enum.

### Code Example
```pine
//@version=6
indicator("Session highlight", overlay = true)

//@enum        Contains fields with popular timezones as titles.
//@field exch  Has an empty string as the title to represent the chart timezone.
enum tz
    utc  = "UTC"
    exch = ""
    ny   = "America/New_York"
    chi  = "America/Chicago"
    lon  = "Europe/London"
    tok  = "Asia/Tokyo"

//@variable The session string.
selectedSession = input.session("1200-1500", "Session")
//@variable The selected timezone. The input's dropdown contains the fields in the `tz` enum.
selectedTimezone = input.enum(tz.utc, "Session Timezone")

//@variable Is `true` if the current bar's time is in the specified session.
bool inSession = false
if not na(time("", selectedSession, str.tostring(selectedTimezone)))
    inSession := true

// Highlight the background when `inSession` is `true`.
bgcolor(inSession ? color.new(color.green, 90) : na, title = "Active session highlight")
```

---

## input.float()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a float input to the script's inputs.

### Syntax

```pine
input.float(defval, title, minval, maxval, step, tooltip, inline, group, confirm, display, active) → input int
input.float(defval, title, options, tooltip, inline, group, confirm, display, active) → input int
```

### Arguments

- `defval` (*const int|float*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where script users can change it. When a list of values is used with the `options` parameter, the value must be one of them.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `minval` (*const int|float*, optional) — Minimal possible value of the input variable. Optional.
- `maxval` (*const int|float*, optional) — Maximum possible value of the input variable. Optional.
- `step` (*const int|float*, optional, default `1.0`) — Step value used for incrementing/decrementing the input. Optional. The default is 1.
- `options` (*const int|float [val1, val2, ...]*) — A list of options to choose from a dropdown menu, separated by commas and enclosed in square brackets: [val1, val2, ...]. When using this parameter, the `minval`, `maxval` and `step` parameters cannot be used.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.all`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.float).*

### Returns
Value of input variable.

### Remarks
Result of input.float function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.float", overlay=true)
i_angle1 = input.float(0.5, "Sin Angle", minval=-3.14, maxval=3.14, step=0.02)
plot(math.sin(i_angle1) > 0 ? close : open, "sin", color=color.green)

i_angle2 = input.float(0, "Cos Angle", options=[-3.14, -1.57, 0, 1.57, 3.14])
plot(math.cos(i_angle2) > 0 ? close : open, "cos", color=color.red)
```

---

## input.int()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for an integer input to the script's inputs.

### Syntax

```pine
input.int(defval, title, minval, maxval, step, tooltip, inline, group, confirm, display, active) → input int
input.int(defval, title, options, tooltip, inline, group, confirm, display, active) → input int
```

### Arguments

- `defval` (*const int*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where script users can change it. When a list of values is used with the `options` parameter, the value must be one of them.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `minval` (*const int*, optional) — Minimal possible value of the input variable. Optional.
- `maxval` (*const int*, optional) — Maximum possible value of the input variable. Optional.
- `step` (*const int*, optional, default `1.0`) — Step value used for incrementing/decrementing the input. Optional. The default is 1.
- `options` (*const int [val1, val2, ...]*) — A list of options to choose from a dropdown menu, separated by commas and enclosed in square brackets: [val1, val2, ...]. When using this parameter, the `minval`, `maxval` and `step` parameters cannot be used.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.all`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.int).*

### Returns
Value of input variable.

### Remarks
Result of input.int function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.int", overlay=true)
i_len1 = input.int(10, "Length 1", minval=5, maxval=21, step=1)
plot(ta.sma(close, i_len1))

i_len2 = input.int(10, "Length 2", options=[5, 10, 21])
plot(ta.sma(close, i_len2))
```

---

## input.price()

Adds a price input to the script's "Settings/Inputs" tab. Using confirm = true activates the interactive input mode where a price is selected by clicking on the chart.

### Syntax

```pine
input.price(defval, title, tooltip, inline, group, confirm, display) → input float
```

### Arguments

- `defval` (*const int|float*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, the interactive input mode is enabled and the selection is done by clicking on the chart when the indicator is added to the chart, or by selecting the indicator and moving the selection after that. Optional. The default is false.
- `display` (*const plot_display*, optional, default `display.all`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.price).*

### Returns
Value of input variable.

### Remarks
When using interactive mode, a time input can be combined with a price input if both function calls use the same argument for their inline parameter.

### Code Example
```pine
//@version=6
indicator("input.price", overlay=true)
price1 = input.price(title="Date", defval=42)
plot(price1)

price2 = input.price(54, title="Date")
plot(price2)
```

---

## input.session()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds two dropdowns that allow the user to specify the beginning and the end of a session using the session selector and returns the result as a string.

### Syntax

```pine
input.session(defval, title, options, tooltip, inline, group, confirm, display) → input string
```

### Arguments

- `defval` (*const string*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the `options` parameter, the value must be one of them.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*const string [val1, val2, ...]*, optional) — A list of options to choose from.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.all`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.session).*

### Returns
Value of input variable.

### Remarks
Result of input.session function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.session", overlay=true)
i_sess = input.session("1300-1700", "Session", options=["0930-1600", "1300-1700", "1700-2100"])
t = time(timeframe.period, i_sess)
bgcolor(time == t ? color.green : na)
```

---

## input.source()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a dropdown that allows the user to select a source for the calculation, e.g. close, hl2, etc. The user can also select an output from another indicator on their chart as the source.

### Syntax

```pine
input.source(defval, title, tooltip, inline, group, display) → series float
```

### Arguments

- `defval` (*<open|high|low|close|hl2|hlc3|ohlc4|hlcc4>*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `display` (*const plot_display*, optional, default `display.all`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.source).*

### Returns
Value of input variable.

### Remarks
Result of input.source function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.source", overlay=true)
i_src = input.source(close, "Source")
plot(i_src)
```

---

## input.string()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a string input to the script's inputs.

### Syntax

```pine
input.string(defval, title, options, tooltip, inline, group, confirm, display) → input string
```

### Arguments

- `defval` (*const string*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the `options` parameter, the value must be one of them.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*const string [val1, val2, ...]*, optional) — A list of options to choose from.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.all`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.string).*

### Returns
Value of input variable.

### Remarks
Result of input.string function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.string", overlay=true)
i_text = input.string("Hello!", "Message")
l = label.new(bar_index, high, i_text)
label.delete(l[1])
```

---

## input.symbol()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field that allows the user to select a specific symbol using the symbol search and returns that symbol, paired with its exchange prefix, as a string.

### Syntax

```pine
input.symbol(defval, title, tooltip, inline, group, confirm, display) → input string
```

### Arguments

- `defval` (*const string*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.all`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.symbol).*

### Returns
Value of input variable.

### Remarks
Result of input.symbol function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.symbol", overlay=true)
i_sym = input.symbol("DELL", "Symbol")
s = request.security(i_sym, 'D', close)
plot(s)
```

---

## input.text_area()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a multiline text input.

### Syntax

```pine
input.text_area(defval, title, tooltip, group, confirm, display) → input string
```

### Arguments

- `defval` (*const string*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.none`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.text_area).*

### Returns
Value of input variable.

### Remarks
Result of input.text_area function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.text_area")
i_text = input.text_area(defval = "Hello \nWorld!", title = "Message")
plot(close)
```

---

## input.time()

Adds a time input to the script's "Settings/Inputs" tab. This function adds two input widgets on the same line: one for the date and one for the time. The function returns a date/time value in UNIX format. Using confirm = true activates the interactive input mode where a point in time is selected by clicking on the chart.

### Syntax

```pine
input.time(defval, title, tooltip, inline, group, confirm, display) → input int
```

### Arguments

- `defval` (*const int*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it. The value can be a [timestamp](https://www.tradingview.com/pine-script-reference/v6/#fun_timestamp) function, but only if it uses a date argument in const string format.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, the interactive input mode is enabled and the selection is done by clicking on the chart when the indicator is added to the chart, or by selecting the indicator and moving the selection after that. Optional. The default is false.
- `display` (*const plot_display*, optional, default `display.none`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.time).*

### Returns
Value of input variable.

### Remarks
When using interactive mode, a price input can be combined with a time input if both function calls use the same argument for their inline parameter.

### Code Example
```pine
//@version=6
indicator("input.time", overlay=true)
i_date = input.time(timestamp("20 Jul 2021 00:00 +0300"), "Date")
l = label.new(i_date, high, "Date", xloc=xloc.bar_time)
label.delete(l[1])
```

---

## input.timeframe()

Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a dropdown that allows the user to select a specific timeframe via the timeframe selector and returns it as a string. The selector includes the custom timeframes a user may have added using the chart's Timeframe dropdown.

### Syntax

```pine
input.timeframe(defval, title, options, tooltip, inline, group, confirm, display) → input string
```

### Arguments

- `defval` (*const string*) — Determines the default value of the input variable proposed in the script’s "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the `options` parameter, the value must be one of them.
- `title` (*const string*, optional, default `'variable_name'`) — Title of the input. If not specified, the variable name is used as the input’s title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*const string [val1, val2, ...]*, optional) — A list of options to choose from.
- `tooltip` (*const string*, optional) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*, optional) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*, optional) — Creates a header above all inputs using the same group argument string. The string is also used as the header’s text.
- `confirm` (*const bool*, optional, default `false`) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*, optional, default `display.all`) — Controls where the script will display the input’s information, aside from within the script’s settings. This option allows one to remove a specific input from the script’s status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_input.timeframe).*

### Returns
Value of input variable.

### Remarks
Result of input.timeframe function always should be assigned to a variable, see examples above.

### Code Example
```pine
//@version=6
indicator("input.timeframe", overlay=true)
i_res = input.timeframe('D', "Resolution", options=['D', 'W', 'M'])
s = request.security("AAPL", i_res, close)
plot(s)
```

---

## int()

Casts na or truncates float value to int

### Syntax

```pine
int
int(x) → series int
```

### Arguments

- `x` (*series int*) — 'na' to cast to int.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_int).*

### Returns
The value of the argument after casting to int.

---

## label()

Casts na to label

### Syntax

```pine
label
label(x) → series label
```

### Arguments

- `x` (*series label*) — 'na' to cast to label..

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label).*

### Returns
The value of the argument after casting to label.

---

## label.copy()

Clones the label object.

### Syntax

```pine
label.copy(id) → void
```

### Arguments

- `id` (*series label*) — Label object.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.copy).*

### Returns
New label ID object which may be passed to label.setXXX and label.getXXX functions.

### Code Example
```pine
//@version=6
indicator('Last 100 bars highest/lowest', overlay = true)
LOOKBACK = 100
highest = ta.highest(LOOKBACK)
highestBars = ta.highestbars(LOOKBACK)
lowest = ta.lowest(LOOKBACK)
lowestBars = ta.lowestbars(LOOKBACK)
if barstate.islastconfirmedhistory
    var labelHigh = label.new(bar_index + highestBars, highest, str.tostring(highest), color = color.green)
    var labelLow = label.copy(labelHigh)
    label.set_xy(labelLow, bar_index + lowestBars, lowest)
    label.set_text(labelLow, str.tostring(lowest))
    label.set_color(labelLow, color.red)
    label.set_style(labelLow, label.style_label_up)
```

---

## label.delete()

Deletes the specified label object. If it has already been deleted, does nothing.

---

### Syntax

```pine
label.delete(id) → void
```

### Arguments

- `id` (*series label*) — Label object to delete.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.delete).*

## label.get_text()

Returns the text of this label object.

### Syntax

```pine
label.get_text(id) → series string
```

### Arguments

- `id` (*series label*) — Label object.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.get_text).*

### Returns
String object containing the text of this label.

### Code Example
```pine
//@version=6
indicator("label.get_text")
my_label = label.new(time, open, text="Open bar text", xloc=xloc.bar_time)
a = label.get_text(my_label)
label.new(time, close, text = a + " new", xloc=xloc.bar_time)
```

---

## label.get_x()

Returns UNIX time or bar index (depending on the last xloc value set) of this label's position.

### Syntax

```pine
label.get_x(id) → series int
```

### Arguments

- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.get_x).*

### Returns
UNIX timestamp (in milliseconds) or bar index.

### Code Example
```pine
//@version=6
indicator("label.get_x")
my_label = label.new(time, open, text="Open bar text", xloc=xloc.bar_time)
a = label.get_x(my_label)
plot(time - label.get_x(my_label)) //draws zero plot
```

---

## label.get_y()

Returns price of this label's position.

### Syntax

```pine
label.get_y(id) → series float
```

### Arguments

- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.get_y).*

### Returns
Floating point value representing price.

---

## label.new()

Creates new label object.

### Syntax

```pine
label.new(point, text, xloc, yloc, color, style, textcolor, size, textalign, tooltip, text_font_family, force_overlay, text_formatting) → series label
label.new(x, y, text, xloc, yloc, color, style, textcolor, size, textalign, tooltip, text_font_family, force_overlay, text_formatting) → series label
```

### Arguments

- `x` (*series int*) — Bar index (if xloc = [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index)) or bar UNIX time (if xloc = [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time)) of the label position. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `y` (*series int|float*) — Price of the label position. It is taken into account only if yloc=[yloc.price](https://www.tradingview.com/pine-script-reference/v6/#var_yloc.price).
- `text` (*series string*, optional, default `""`) — Label text. Default is empty string.
- `xloc` (*series string*, optional, default `xloc.bar_index`) — See description of **x** argument. Possible values: [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) and [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time). Default is [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index).
- `yloc` (*series string*, optional, default `yloc.price`) — Possible values are [yloc.price](https://www.tradingview.com/pine-script-reference/v6/#var_yloc.price), [yloc.abovebar](https://www.tradingview.com/pine-script-reference/v6/#var_yloc.abovebar), [yloc.belowbar](https://www.tradingview.com/pine-script-reference/v6/#var_yloc.belowbar). If yloc=[yloc.price](https://www.tradingview.com/pine-script-reference/v6/#var_yloc.price), **y** argument specifies the price of the label position. If yloc=[yloc.abovebar](https://www.tradingview.com/pine-script-reference/v6/#var_yloc.abovebar), label is located above bar. If yloc=[yloc.belowbar](https://www.tradingview.com/pine-script-reference/v6/#var_yloc.belowbar), label is located below bar. Default is [yloc.price](https://www.tradingview.com/pine-script-reference/v6/#var_yloc.price).
- `color` (*series color*, optional, default `color.blue`) — Color of the label border and arrow
- `style` (*series string*, optional, default `label.style_label_down`) — Label style. Possible values: [label.style_none](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_none), [label.style_xcross](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_xcross), [label.style_cross](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_cross), [label.style_triangleup](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_triangleup), [label.style_triangledown](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_triangledown), [label.style_flag](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_flag), [label.style_circle](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_circle), [label.style_arrowup](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_arrowup), [label.style_arrowdown](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_arrowdown), [label.style_label_up](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_up), [label.style_label_down](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_down), [label.style_label_left](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_left), [label.style_label_right](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_right), [label.style_label_lower_left](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_lower_left), [label.style_label_lower_right](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_lower_right), [label.style_label_upper_left](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_upper_left), [label.style_label_upper_right](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_upper_right), [label.style_label_center](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_center), [label.style_square](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_square), [label.style_diamond](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_diamond), [label.style_text_outline](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_text_outline). Default is [label.style_label_down](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_down).
- `textcolor` (*series color*, optional, default `color.white`) — Text color.
- `size` (*series string*, optional, default `size.normal`) — Label size. Possible values: [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v6/#var_size.tiny), [size.small](https://www.tradingview.com/pine-script-reference/v6/#var_size.small), [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal), [size.large](https://www.tradingview.com/pine-script-reference/v6/#var_size.large), [size.huge](https://www.tradingview.com/pine-script-reference/v6/#var_size.huge). Default value is [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal).
- `textalign` (*series string*, optional, default `text.align_center`) — Label text alignment. Possible values: [text.align_left](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_left), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_right](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_right). Default value is [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center).
- `tooltip` (*series string*, optional, default `na`) — Hover to see tooltip label.
- `text_font_family` (*series string*, optional, default `font.family_default`) — The font family of the text. Optional. The default value is [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default). Possible values: [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default), [font.family_monospace](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_monospace).
- `point` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object that specifies the label’s location.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.new).*

### Returns
Label ID object which may be passed to label.setXXX and label.getXXX functions.

### Code Example
```pine
//@version=6
indicator("label.new")
var label1 = label.new(bar_index, low, text="Hello, world!", style=label.style_circle)
label.set_x(label1, 0)
label.set_xloc(label1, time, xloc.bar_time)
label.set_color(label1, color.red)
label.set_size(label1, size.large)
```

---

## label.set_color()

Sets label border and arrow color.

---

### Syntax

```pine
label.set_color(id, color) → void
```

### Arguments

- `color` (*series color*) — New label bgcolor
- `id` (*series label*) — Label object.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_color).*

## label.set_point()

Sets the location of the id label to point.

---

### Syntax

```pine
label.set_point(id, point) → void
```

### Arguments

- `point` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object.
- `id` (*series label*) — A [label](https://www.tradingview.com/pine-script-reference/v6/#op_label) object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_point).*

## label.set_size()

Sets arrow and text size of the specified label object.

---

### Syntax

```pine
label.set_size(id, size) → void
```

### Arguments

- `size` (*series string*, default `size.auto`) — Possible values: [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v6/#var_size.tiny), [size.small](https://www.tradingview.com/pine-script-reference/v6/#var_size.small), [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal), [size.large](https://www.tradingview.com/pine-script-reference/v6/#var_size.large), [size.huge](https://www.tradingview.com/pine-script-reference/v6/#var_size.huge). Default value is [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto).
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_size).*

## label.set_style()

Sets label style.

---

### Syntax

```pine
label.set_style(id, style) → void
```

### Arguments

- `style` (*series string*) — New label style. Possible values: [label.style_none](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_none), [label.style_xcross](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_xcross), [label.style_cross](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_cross), [label.style_triangleup](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_triangleup), [label.style_triangledown](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_triangledown), [label.style_flag](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_flag), [label.style_circle](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_circle), [label.style_arrowup](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_arrowup), [label.style_arrowdown](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_arrowdown), [label.style_label_up](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_up), [label.style_label_down](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_down), [label.style_label_left](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_left), [label.style_label_right](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_right), [label.style_label_lower_left](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_lower_left), [label.style_label_lower_right](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_lower_right), [label.style_label_upper_left](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_upper_left), [label.style_label_upper_right](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_upper_right), [label.style_label_center](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_label_center), [label.style_square](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_square), [label.style_diamond](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_diamond), [label.style_text_outline](https://www.tradingview.com/pine-script-reference/v6/#var_label.style_text_outline).
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_style).*

## label.set_text()

Sets label text

---

### Syntax

```pine
label.set_text(id, text) → void
```

### Arguments

- `text` (*series string*) — New label text.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_text).*

## label.set_text_font_family()

The function sets the font family of the text inside the label.

### Syntax

```pine
label.set_text_font_family(id, text_font_family) → void
```

### Arguments

- `text_font_family` (*series string*, default `font.family_default`) — The font family of the text. Possible values: [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default), [font.family_monospace](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_monospace).
- `id` (*series label*) — A label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_text_font_family).*

### Code Example
```pine
//@version=6
indicator("Example of setting the label font")
if barstate.islastconfirmedhistory
    l = label.new(bar_index, 0, "monospace", yloc=yloc.abovebar)
    label.set_text_font_family(l, font.family_monospace)
```

---

## label.set_text_formatting()

Sets the formatting attributes the drawing applies to displayed text.

---

## label.set_textalign()

Sets the alignment for the label text.

---

### Syntax

```pine
label.set_textalign(id, textalign) → void
```

### Arguments

- `textalign` (*series string*) — Label text alignment. Possible values: [text.align_left](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_left), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_right](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_right).
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_textalign).*

## label.set_textcolor()

Sets color of the label text.

---

### Syntax

```pine
label.set_textcolor(id, textcolor) → void
```

### Arguments

- `textcolor` (*series color*) — New text color.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_textcolor).*

## label.set_tooltip()

Sets the tooltip text.

---

### Syntax

```pine
label.set_tooltip(id, tooltip) → void
```

### Arguments

- `tooltip` (*series string*) — Tooltip text.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_tooltip).*

## label.set_x()

Sets bar index or bar time (depending on the xloc) of the label position.

---

### Syntax

```pine
label.set_x(id, x) → void
```

### Arguments

- `x` (*series int*) — New bar index or bar time of the label position. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_x).*

## label.set_xloc()

Sets x-location and new bar index/time value.

---

### Syntax

```pine
label.set_xloc(id, x, xloc) → void
```

### Arguments

- `x` (*series int*) — New bar index or bar time of the label position.
- `xloc` (*series string*) — New x-location value.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_xloc).*

## label.set_xy()

Sets bar index/time and price of the label position.

---

### Syntax

```pine
label.set_xy(id, x, y) → void
```

### Arguments

- `x` (*series int*) — New bar index or bar time of the label position. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `y` (*series int|float*) — New price of the label position.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_xy).*

## label.set_y()

Sets price of the label position

---

### Syntax

```pine
label.set_y(id, y) → void
```

### Arguments

- `y` (*series int|float*) — New price of the label position.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_y).*

## label.set_yloc()

Sets new y-location calculation algorithm.

---

### Syntax

```pine
label.set_yloc(id, yloc) → void
```

### Arguments

- `yloc` (*series string*) — New y-location value.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_yloc).*

## library()

Declaration statement identifying a script as a library.

### Syntax

```pine
library(title, overlay, dynamic_requests) → void
```

### Arguments

- `title` (*const string*) — The title of the library and its identifier. It cannot contain spaces, special characters or begin with a digit. It is used as the publication’s default title, and to uniquely identify the library in the [import](https://www.tradingview.com/pine-script-reference/v6/#op_import) statement, when another script uses it. It is also used as the script’s name on the chart.
- `overlay` (*const bool*, optional, default `false`) — If true, the library will be added over the chart. If false, it will be added in a separate pane. Optional. The default is false.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_library).*

### Code Example
```pine
//@version=6
// @description Math library
library("num_methods", overlay = true)
// Calculate "sinh()" from the float parameter `x`
export sinh(float x) =>
    (math.exp(x) - math.exp(-x)) / 2.0
plot(sinh(0))
```

---

## line()

Casts na to line

### Syntax

```pine
line
line(x) → series line
```

### Arguments

- `x` (*series line*) — 'na' to cast to line..

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line).*

### Returns
The value of the argument after casting to line.

---

## line.copy()

Clones the line object.

### Syntax

```pine
line.copy(id) → series line
```

### Arguments

- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.copy).*

### Returns
New line ID object which may be passed to line.setXXX and line.getXXX functions.

### Code Example
```pine
//@version=6
indicator('Last 100 bars price range', overlay = true)
LOOKBACK = 100
highest = ta.highest(LOOKBACK)
lowest = ta.lowest(LOOKBACK)
if barstate.islastconfirmedhistory
    var lineTop = line.new(bar_index[LOOKBACK], highest, bar_index, highest, color = color.green)
    var lineBottom = line.copy(lineTop)
    line.set_y1(lineBottom, lowest)
    line.set_y2(lineBottom, lowest)
    line.set_color(lineBottom, color.red)
```

---

## line.delete()

Deletes the specified line object. If it has already been deleted, does nothing.

---

### Syntax

```pine
line.delete(id) → void
```

### Arguments

- `id` (*series line*) — Line object to delete.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.delete).*

## line.get_price()

Returns the price level of a line at a given bar index.

### Syntax

```pine
line.get_price(id, x) → series float
```

### Arguments

- `x` (*series int*) — Bar index for which price is required.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.get_price).*

### Returns
Price value of line 'id' at bar index 'x'.

### Remarks
The line is considered to have been created using 'extend=extend.both'. This function can only be called for lines created using 'xloc.bar_index'. If you try to call it for a line created with 'xloc.bar_time', it will generate an error.

### Code Example
```pine
//@version=6
indicator("GetPrice", overlay=true)
var line l = na
if bar_index == 10
    l := line.new(0, high[5], bar_index, high)
plot(line.get_price(l, bar_index), color=color.green)
```

---

## line.get_x1()

Returns UNIX time or bar index (depending on the last xloc value set) of the first point of the line.

### Syntax

```pine
line.get_x1(id) → series int
```

### Arguments

- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.get_x1).*

### Returns
UNIX timestamp (in milliseconds) or bar index.

### Code Example
```pine
//@version=6
indicator("line.get_x1")
my_line = line.new(time, open, time + 60 * 60 * 24, close, xloc=xloc.bar_time)
a = line.get_x1(my_line)
plot(time - line.get_x1(my_line)) //draws zero plot
```

---

## line.get_x2()

Returns UNIX time or bar index (depending on the last xloc value set) of the second point of the line.

### Syntax

```pine
line.get_x2(id) → series int
```

### Arguments

- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.get_x2).*

### Returns
UNIX timestamp (in milliseconds) or bar index.

---

## line.get_y1()

Returns price of the first point of the line.

### Syntax

```pine
line.get_y1(id) → series float
```

### Arguments

- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.get_y1).*

### Returns
Price value.

---

## line.get_y2()

Returns price of the second point of the line.

### Syntax

```pine
line.get_y2(id) → series float
```

### Arguments

- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.get_y2).*

### Returns
Price value.

---

## line.new()

Creates new line object.

### Syntax

```pine
line.new(first_point, second_point, xloc, extend, color, style, width, force_overlay) → series line
line.new(x1, y1, x2, y2, xloc, extend, color, style, width, force_overlay) → series line
```

### Arguments

- `x1` (*series int*) — Bar index (if xloc = [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index)) or bar UNIX time (if xloc = [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time)) of the first point of the line. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `y1` (*series int|float*) — Price of the first point of the line.
- `x2` (*series int*) — Bar index (if xloc = [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index)) or bar UNIX time (if xloc = [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time)) of the second point of the line. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `y2` (*series int|float*) — Price of the second point of the line.
- `xloc` (*series string*, optional, default `xloc.bar_index`) — See description of **x1** argument. Possible values: [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) and [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time). Default is [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index).
- `extend` (*series string*, optional, default `extend.none`) — If extend=[extend.none](https://www.tradingview.com/pine-script-reference/v6/#var_extend.none), draws segment starting at point (x1, y1) and ending at point (x2, y2). If extend is equal to [extend.right](https://www.tradingview.com/pine-script-reference/v6/#var_extend.right) or [extend.left](https://www.tradingview.com/pine-script-reference/v6/#var_extend.left), draws a ray starting at point (x1, y1) or (x2, y2), respectively. If extend=[extend.both](https://www.tradingview.com/pine-script-reference/v6/#var_extend.both), draws a straight line that goes through these points. Default value is [extend.none](https://www.tradingview.com/pine-script-reference/v6/#var_extend.none).
- `color` (*series color*, optional, default `color.blue`) — Line color.
- `width` (*series int*, optional, default `1`) — Line width in pixels.
- `style` (*series string*, optional, default `line.style_solid`) — Line style. Possible values: [line.style_solid](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_solid), [line.style_dotted](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_dotted), [line.style_dashed](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_dashed), [line.style_arrow_left](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_arrow_left), [line.style_arrow_right](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_arrow_right), [line.style_arrow_both](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_arrow_both).
- `first_point` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object that specifies the line’s starting coordinate.
- `second_point` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object that specifies the line’s ending coordinate.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.new).*

### Returns
Line ID object which may be passed to line.setXXX and line.getXXX functions.

### Code Example
```pine
//@version=6
indicator("line.new")
var line1 = line.new(0, low, bar_index, high, extend=extend.right)
var line2 = line.new(time, open, time + 60 * 60 * 24, close, xloc=xloc.bar_time, style=line.style_dashed)
line.set_x2(line1, 0)
line.set_xloc(line1, time, time + 60 * 60 * 24, xloc.bar_time)
line.set_color(line2, color.green)
line.set_width(line2, 5)
```

---

## line.set_color()

Sets the line color

---

### Syntax

```pine
line.set_color(id, color) → void
```

### Arguments

- `color` (*series color*) — New line color
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_color).*

## line.set_extend()

Sets extending type of this line object. If extend=extend.none, draws segment starting at point (x1, y1) and ending at point (x2, y2). If extend is equal to extend.right or extend.left, draws a ray starting at point (x1, y1) or (x2, y2), respectively. If extend=extend.both, draws a straight line that goes through these points.

---

### Syntax

```pine
line.set_extend(id, extend) → void
```

### Arguments

- `extend` (*series string*) — New extending type.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_extend).*

## line.set_first_point()

Sets the first point of the id line to point.

---

### Syntax

```pine
line.set_first_point(id, point) → void
```

### Arguments

- `point` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object.
- `id` (*series line*) — A [line](https://www.tradingview.com/pine-script-reference/v6/#op_line) object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_first_point).*

## line.set_second_point()

Sets the second point of the id line to point.

---

### Syntax

```pine
line.set_second_point(id, point) → void
```

### Arguments

- `point` (*chart.point*) — A [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) object.
- `id` (*series line*) — A [line](https://www.tradingview.com/pine-script-reference/v6/#op_line) object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_second_point).*

## line.set_style()

Sets the line style

---

### Syntax

```pine
line.set_style(id, style) → void
```

### Arguments

- `style` (*series string*) — New line style.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_style).*

## line.set_width()

Sets the line width.

---

### Syntax

```pine
line.set_width(id, width) → void
```

### Arguments

- `width` (*series int*) — New line width in pixels.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_width).*

## line.set_x1()

Sets bar index or bar time (depending on the xloc) of the first point.

---

### Syntax

```pine
line.set_x1(id, x) → void
```

### Arguments

- `x` (*series int*) — Bar index or bar time. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_x1).*

## line.set_x2()

Sets bar index or bar time (depending on the xloc) of the second point.

---

### Syntax

```pine
line.set_x2(id, x) → void
```

### Arguments

- `x` (*series int*) — Bar index or bar time. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_x2).*

## line.set_xloc()

Sets x-location and new bar index/time values.

---

### Syntax

```pine
line.set_xloc(id, x1, x2, xloc) → void
```

### Arguments

- `x1` (*series int*) — Bar index or bar time of the first point.
- `x2` (*series int*) — Bar index or bar time of the second point.
- `xloc` (*series string*) — New x-location value.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_xloc).*

## line.set_xy1()

Sets bar index/time and price of the first point.

---

### Syntax

```pine
line.set_xy1(id, x, y) → void
```

### Arguments

- `x` (*series int*) — Bar index or bar time. Note that objects positioned using [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index) cannot be drawn further than 500 bars into the future.
- `y` (*series int|float*) — Price.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_xy1).*

## line.set_xy2()

Sets bar index/time and price of the second point

---

### Syntax

```pine
line.set_xy2(id, x, y) → void
```

### Arguments

- `x` (*series int*) — Bar index or bar time.
- `y` (*series int|float*) — Price.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_xy2).*

## line.set_y1()

Sets price of the first point

---

### Syntax

```pine
line.set_y1(id, y) → void
```

### Arguments

- `y` (*series int|float*) — Price.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_y1).*

## line.set_y2()

Sets price of the second point.

---

### Syntax

```pine
line.set_y2(id, y) → void
```

### Arguments

- `y` (*series int|float*) — Price.
- `id` (*series line*) — Line object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_line.set_y2).*

## linefill()

Casts na to linefill.

### Syntax

```pine
linefill
linefill(x) → series linefill
```

### Arguments

- `x` (*series linefill*) — 'na' to cast to linefill.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill).*

### Returns
The value of the argument after casting to linefill.

---

## linefill.delete()

Deletes the specified linefill object. If it has already been deleted, does nothing.

---

### Syntax

```pine
linefill.delete(id) → void
```

### Arguments

- `id` (*series linefill*) — A linefill object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.delete).*

## linefill.get_line1()

Returns the ID of the first line used in the id linefill.

---

### Syntax

```pine
linefill.get_line1(id) → series line
```

### Arguments

- `id` (*series linefill*) — A linefill object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.get_line1).*

## linefill.get_line2()

Returns the ID of the second line used in the id linefill.

---

### Syntax

```pine
linefill.get_line2(id) → series line
```

### Arguments

- `id` (*series linefill*) — A linefill object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.get_line2).*

## linefill.new()

Creates a new linefill object and displays it on the chart, filling the space between line1 and line2 with the color specified in color.

### Syntax

```pine
linefill.new(line1, line2, color) → series linefill
```

### Arguments

- `line1` (*series line*) — First line object.
- `line2` (*series line*) — Second line object.
- `color` (*series color*) — The color used to fill the space between the lines.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.new).*

### Returns
The ID of a linefill object that can be passed to other linefill.*() functions.

### Remarks
If any line of the two is deleted, the linefill object is also deleted. If the lines are moved (e.g. via line.set_xy functions), the linefill object is also moved. If both lines are extended in the same direction relative to the lines themselves (e.g. both have extend.right as the value of their extend= parameter), the space between line extensions will also be filled.

---

## linefill.set_color()

The function sets the color of the linefill object passed to it.

---

### Syntax

```pine
linefill.set_color(id, color) → void
```

### Arguments

- `color` (*series color*) — The color of the linefill object.
- `id` (*series linefill*) — A linefill object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.set_color).*

## log.error()

Converts the formatting string and value(s) into a formatted string, and sends the result to the "Pine logs" menu tagged with the "error" debug level.

### Syntax

```pine
log.error(message) → void
log.error(formatString, arg0, arg1, ...) → void
```

### Arguments

- `formatString` (*series string*) — Format string.
- `message` (*series string*) — Log message.
- `arg0, arg1, ...` (*series int|float|bool|string|array<int|float|bool|string>|na*) — Values to format.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_log.error).*

### Returns
The formatted string.

### Remarks
Any curly braces within an unquoted pattern must be balanced. For example, "ab {0} de" and "ab '}' de" are valid patterns, but "ab {0'}' de", "ab } de" and "''{''" are not.  The function can apply additional formatting to some values inside of the {}. The list of additional formatting options can be found in the EXAMPLE section of the str.format article.  The string used as the formatString argument can contain single quote characters ('). However, one must pair all single quotes in that string to avoid unexpected formatting results.  The "Pine logs..." button is accessible from the "More" dropdown in the Pine Editor and from the "More" dropdown in the status line of any script that uses log.*() functions.

### Code Example
```pine
//@version=6
strategy("My strategy", overlay = true, process_orders_on_close = true)
bracketTickSizeInput = input.int(1000, "Stoploss/Take-Profit distance (in ticks)")

longCondition = ta.crossover(ta.sma(close, 14), ta.sma(close, 28))
if (longCondition)
    limitLevel = close * 1.01
    log.info("Long limit order has been placed at {0}", limitLevel)
    strategy.order("My Long Entry Id", strategy.long, limit = limitLevel)

    log.info("Exit orders have been placed: Take-profit at {0}, Stop-loss at {1}", close, limitLevel)
    strategy.exit("Exit", "My Long Entry Id", profit = bracketTickSizeInput, loss = bracketTickSizeInput)

if strategy.opentrades > 10
    log.warning("{0} positions opened in the same direction in a row. Try adjusting `bracketTickSizeInput`", strategy.opentrades)

last10Perc = strategy.initial_capital / 10 > strategy.equity
if (last10Perc and not last10Perc[1])
    log.error("The strategy has lost 90% of the initial capital!")
```

---

## log.info()

Converts the formatting string and value(s) into a formatted string, and sends the result to the "Pine logs" menu tagged with the "info" debug level.

### Syntax

```pine
log.info(message) → void
log.info(formatString, arg0, arg1, ...) → void
```

### Arguments

- `formatString` (*series string*) — Format string.
- `message` (*series string*) — Log message.
- `arg0, arg1, ...` (*series int|float|bool|string|array<int|float|bool|string>|na*) — Values to format.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_log.info).*

### Returns
The formatted string.

### Remarks
Any curly braces within an unquoted pattern must be balanced. For example, "ab {0} de" and "ab '}' de" are valid patterns, but "ab {0'}' de", "ab } de" and "''{''" are not.  The function can apply additional formatting to some values inside of the {}. The list of additional formatting options can be found in the EXAMPLE section of the str.format article.  The string used as the formatString argument can contain single quote characters ('). However, one must pair all single quotes in that string to avoid unexpected formatting results.  The "Pine logs..." button is accessible from the "More" dropdown in the Pine Editor and from the "More" dropdown in the status line of any script that uses log.*() functions.

### Code Example
```pine
//@version=6
strategy("My strategy", overlay = true, process_orders_on_close = true)
bracketTickSizeInput = input.int(1000, "Stoploss/Take-Profit distance (in ticks)")

longCondition = ta.crossover(ta.sma(close, 14), ta.sma(close, 28))
if (longCondition)
    limitLevel = close * 1.01
    log.info("Long limit order has been placed at {0}", limitLevel)
    strategy.order("My Long Entry Id", strategy.long, limit = limitLevel)

    log.info("Exit orders have been placed: Take-profit at {0}, Stop-loss at {1}", close, limitLevel)
    strategy.exit("Exit", "My Long Entry Id", profit = bracketTickSizeInput, loss = bracketTickSizeInput)

if strategy.opentrades > 10
    log.warning("{0} positions opened in the same direction in a row. Try adjusting `bracketTickSizeInput`", strategy.opentrades)

last10Perc = strategy.initial_capital / 10 > strategy.equity
if (last10Perc and not last10Perc[1])
    log.error("The strategy has lost 90% of the initial capital!")
```

---

## log.warning()

Converts the formatting string and value(s) into a formatted string, and sends the result to the "Pine logs" menu tagged with the "warning" debug level.

### Syntax

```pine
log.warning(message) → void
log.warning(formatString, arg0, arg1, ...) → void
```

### Arguments

- `formatString` (*series string*) — Format string.
- `message` (*series string*) — Log message.
- `arg0, arg1, ...` (*series int|float|bool|string|array<int|float|bool|string>|na*) — Values to format.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_log.warning).*

### Returns
The formatted string.

### Remarks
Any curly braces within an unquoted pattern must be balanced. For example, "ab {0} de" and "ab '}' de" are valid patterns, but "ab {0'}' de", "ab } de" and "''{''" are not.  The function can apply additional formatting to some values inside of the {}. The list of additional formatting options can be found in the EXAMPLE section of the str.format article.  The string used as the formatString argument can contain single quote characters ('). However, one must pair all single quotes in that string to avoid unexpected formatting results.  The "Pine logs..." button is accessible from the "More" dropdown in the Pine Editor and from the "More" dropdown in the status line of any script that uses log.*() functions.

### Code Example
```pine
//@version=6
strategy("My strategy", overlay = true, process_orders_on_close = true)
bracketTickSizeInput = input.int(1000, "Stoploss/Take-Profit distance (in ticks)")

longCondition = ta.crossover(ta.sma(close, 14), ta.sma(close, 28))
if (longCondition)
    limitLevel = close * 1.01
    log.info("Long limit order has been placed at {0}", limitLevel)
    strategy.order("My Long Entry Id", strategy.long, limit = limitLevel)

    log.info("Exit orders have been placed: Take-profit at {0}, Stop-loss at {1}", close, limitLevel)
    strategy.exit("Exit", "My Long Entry Id", profit = bracketTickSizeInput, loss = bracketTickSizeInput)

if strategy.opentrades > 10
    log.warning("{0} positions opened in the same direction in a row. Try adjusting `bracketTickSizeInput`", strategy.opentrades)

last10Perc = strategy.initial_capital / 10 > strategy.equity
if (last10Perc and not last10Perc[1])
    log.error("The strategy has lost 90% of the initial capital!")
```

---

## map.clear()

Clears the map, removing all key-value pairs from it.

### Syntax

```pine
map.clear(id) → void
```

### Arguments

- `id` (*map<type>*) — A map object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.clear).*

### Code Example
```pine
//@version=6
indicator("map.clear example")
oddMap = map.new<int, bool>()
oddMap.put(1, true)
oddMap.put(2, false)
oddMap.put(3, true)
map.clear(oddMap)
plot(oddMap.size())
```

---

## map.contains()

Returns true if the key was found in the id map, false otherwise.

### Syntax

```pine
map.contains(id, key) → series bool
```

### Arguments

- `key` (*map<type>*) — The key to search in the map.
- `id` (*map<type>*) — A map object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.contains).*

### Code Example
```pine
//@version=6
indicator("map.includes example")
a = map.new<string, float>()
a.put("open", open)
p = close
if map.contains(a, "open")
    p := a.get("open")
plot(p)
```

---

## map.copy()

Creates a copy of an existing map.

### Syntax

```pine
map.copy(id) → map<keyType, valueType>
```

### Arguments

- `id` (*map<type>*) — A map object to copy.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.copy).*

### Returns
A copy of the id map.

### Code Example
```pine
//@version=6
indicator("map.copy example")
a = map.new<string, int>()
a.put("example", 1)
b = map.copy(a)
a := map.new<string, int>()
a.put("example", 2)
plot(a.get("example"))
plot(b.get("example"))
```

---

## map.get()

Returns the value associated with the specified key in the id map.

### Syntax

```pine
map.get(id, key) → series valueType
```

### Arguments

- `key` (*map< *keyType* ,valueType>*) — The key of the value to retrieve.
- `id` (*map<type>*) — A map object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.get).*

### Code Example
```pine
//@version=6
indicator("map.get example")
a = map.new<int, int>()
size = 10
for i = 0 to size
    a.put(i, size-i)
plot(map.get(a, 1))
```

---

## map.keys()

Returns an array of all the keys in the id map. The resulting array is a copy and any changes to it are not reflected in the original map.

### Syntax

```pine
map.keys(id) → type[]
```

### Arguments

- `id` (*map<type>*) — A map object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.keys).*

### Remarks
Maps maintain insertion order. The elements within the array returned by this function will also be in the insertion order.

### Code Example
```pine
//@version=6
indicator("map.keys example")
a = map.new<string, float>()
a.put("open", open)
a.put("high", high)
a.put("low", low)
a.put("close", close)
keys = map.keys(a)
ohlc = 0.0
for key in keys
    ohlc += a.get(key)
plot(ohlc/4)
```

---

## map.new<type,type>()

Creates a new map object: a collection that consists of key-value pairs, where all keys are of the keyType, and all values are of the valueType.

### Syntax

```pine
map.new<keyType, valueType>() → map<keyType, valueType>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.new<type,type>).*

### Returns
The ID of a map object which may be used in other map.*() functions.

### Remarks
Each key is unique and can only appear once. When adding a new value with a key that the map already contains, that value replaces the old value associated with the key. Maps maintain insertion order. Note that the order does not change when inserting a pair with a key that's already in the map. The new pair replaces the existing pair with the key in such cases.

### Code Example
```pine
//@version=6
indicator("map.new<string, int> example")
a = map.new<string, int>()
a.put("example", 1)
label.new(bar_index, close, str.tostring(a.get("example")))
```

---

## map.put()

Puts a new key-value pair into the id map.

### Syntax

```pine
map.put(id, key, value) → series valueType
```

### Arguments

- `key` (*map<type>*) — The key to put into the map.
- `value` (*map<type>*) — The key value to put into the map.
- `id` (*map<type>*) — A map object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.put).*

### Returns
The previous value associated with key if the key was already present in the map, or na if the key is new.

### Remarks
Maps maintain insertion order. Note that the order does not change when inserting a pair with a key that's already in the map. The new pair replaces the existing pair with the key in such cases.

### Code Example
```pine
//@version=6
indicator("map.put example")
a = map.new<string, float>()
map.put(a, "first", 10)
map.put(a, "second", 15)
prevFirst = map.put(a, "first", 20)
currFirst = a.get("first")
plot(prevFirst)
plot(currFirst)
```

---

## map.put_all()

Puts all key-value pairs from the id2 map into the id map.

### Syntax

```pine
map.put_all(id, id2) → void
```

### Arguments

- `id2` (*map<type>*) — A map object to be appended.
- `id` (*map<type>*) — A map object to append to.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.put_all).*

### Code Example
```pine
//@version=6
indicator("map.put_all example")
a = map.new<string, float>()
b = map.new<string, float>()
a.put("first", 10)
a.put("second", 15)
b.put("third", 20)
map.put_all(a, b)
plot(a.get("third"))
```

---

## map.remove()

Removes a key-value pair from the id map.

### Syntax

```pine
map.remove(id, key) → series valueType
```

### Arguments

- `key` (*map<type>*) — The key of the pair to remove from the map.
- `id` (*map<type>*) — A map object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.remove).*

### Returns
The previous value associated with key if the key was present in the map, or na if there was no such key.

### Code Example
```pine
//@version=6
indicator("map.remove example")
a = map.new<string, color>()
a.put("firstColor", color.green)
oldColorValue = map.remove(a, "firstColor")
plot(close, color = oldColorValue)
```

---

## map.size()

Returns the number of key-value pairs in the id map.

### Syntax

```pine
map.size(id) → series int
```

### Arguments

- `id` (*map<type>*) — A map object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.size).*

### Code Example
```pine
//@version=6
indicator("map.size example")
a = map.new<int, int>()
size = 10
for i = 0 to size
    a.put(i, size-i)
plot(map.size(a))
```

---

## map.values()

Returns an array of all the values in the id map. The resulting array is a copy and any changes to it are not reflected in the original map.

### Syntax

```pine
map.values(id) → type[]
```

### Arguments

- `id` (*map<type>*) — A map object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_map.values).*

### Remarks
Maps maintain insertion order. The elements within the array returned by this function will also be in the insertion order.

### Code Example
```pine
//@version=6
indicator("map.values example")
a = map.new<string, float>()
a.put("open", open)
a.put("high", high)
a.put("low", low)
a.put("close", close)
values = map.values(a)
ohlc = 0.0
for value in values
    ohlc += value
plot(ohlc/4)
```

---

## math.abs()

Absolute value of number is number if number >= 0, or -number otherwise.

### Syntax

```pine
math.abs(number) → series float
```

### Arguments

- `number` (*series int|float*) — The number to find absolute value for.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.abs).*

### Returns
The absolute value of number.

---

## math.acos()

The acos function returns the arccosine (in radians) of number such that cos(acos(y)) = y for y in range [-1, 1].

### Syntax

```pine
math.acos(angle) → series float
```

### Arguments

- `angle` (*series int|float*) — Angle, in radians.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.acos).*

### Returns
The arc cosine of a value; the returned angle is in the range [0, Pi], or na if y is outside of range [-1, 1].

---

## math.asin()

The asin function returns the arcsine (in radians) of number such that sin(asin(y)) = y for y in range [-1, 1].

### Syntax

```pine
math.asin(angle) → series float
```

### Arguments

- `angle` (*series int|float*) — Angle, in radians.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.asin).*

### Returns
The arcsine of a value; the returned angle is in the range [-Pi/2, Pi/2], or na if y is outside of range [-1, 1].

---

## math.atan()

The atan function returns the arctangent (in radians) of number such that tan(atan(y)) = y for any y.

### Syntax

```pine
math.atan(angle) → series float
```

### Arguments

- `angle` (*series int|float*) — Angle, in radians.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.atan).*

### Returns
The arc tangent of a value; the returned angle is in the range [-Pi/2, Pi/2].

---

## math.avg()

Calculates average of all given series (elementwise).

### Syntax

```pine
math.avg(number0, number1, ...) → series float
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.avg).*

### Returns
Average.

---

## math.ceil()

Rounds the specified number up to the smallest whole number ("int" value) that is greater than or equal to it.

### Syntax

```pine
math.ceil(number) → int
```

### Arguments

- `number` (*series int|float*) — Number to calculate the smallest integer greater than or equal to the argument.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.ceil).*

### Returns
The smallest "int" value that is greater than or equal to the number.

---

## math.cos()

The cos function returns the trigonometric cosine of an angle.

### Syntax

```pine
math.cos(angle) → series float
```

### Arguments

- `angle` (*series int|float*) — Angle, in radians.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.cos).*

### Returns
The trigonometric cosine of an angle.

---

## math.exp()

The exp function of number is e raised to the power of number, where e is Euler's number.

### Syntax

```pine
math.exp(number) → series float
```

### Arguments

- `number` (*series int|float*) — Number to calculate the exponent of.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.exp).*

### Returns
A value representing e raised to the power of number.

---

## math.floor()

Rounds the specified number down to the largest whole number ("int" value) that is less than or equal to it.

### Syntax

```pine
math.floor(number) → series int
```

### Arguments

- `number` (*series int|float*) — Number to calculate the largest integer less than or equal to the argument.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.floor).*

### Returns
The largest "int" value that is less than or equal to the number.

---

## math.log()

Natural logarithm of any number > 0 is the unique y such that e^y = number.

### Syntax

```pine
math.log(number) → series float
```

### Arguments

- `number` (*series int|float*) — The number to use in the calculation.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.log).*

### Returns
The natural logarithm of number.

---

## math.log10()

The common (or base 10) logarithm of number is the power to which 10 must be raised to obtain the number. 10^y = number.

### Syntax

```pine
math.log10(number) → series float
```

### Arguments

- `number` (*series int|float*) — The number to find the `log 10 or base 10` for.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.log10).*

### Returns
The base 10 logarithm of number.

---

## math.max()

Returns the greatest of multiple values.

### Syntax

```pine
math.max(number0, number1, ...) → series int|float
```

### Arguments

- `arg0, arg1, ...` (*series int|float*) — One of x numbers to find the `max` or `greatest` of the group.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.max).*

### Returns
The greatest of multiple given values.

### Code Example
```pine
//@version=6
indicator("math.max", overlay=true)
plot(math.max(close, open))
plot(math.max(close, math.max(open, 42)))
```

---

## math.min()

Returns the smallest of multiple values.

### Syntax

```pine
math.min(number0, number1, ...) → series int|float
```

### Arguments

- `arg0, arg1, ...` (*series int|float*) — One of x numbers to find the `min` or `smallest` of the group.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.min).*

### Returns
The smallest of multiple given values.

### Code Example
```pine
//@version=6
indicator("math.min", overlay=true)
plot(math.min(close, open))
plot(math.min(close, math.min(open, 42)))
```

---

## math.pow()

Mathematical power function.

### Syntax

```pine
math.pow(base, exponent) → series float
```

### Arguments

- `base` (*series int|float*) — Specify the base to use.
- `exponent` (*series int|float*) — Specifies the exponent.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.pow).*

### Returns
base raised to the power of exponent. If base is a series, it is calculated elementwise.

### Code Example
```pine
//@version=6
indicator("math.pow", overlay=true)
plot(math.pow(close, 2))
```

---

## math.random()

Returns a pseudo-random value. The function will generate a different sequence of values for each script execution. Using the same value for the optional seed argument will produce a repeatable sequence.

### Syntax

```pine
math.random(min, max, seed) → series float
```

### Arguments

- `min` (*series int|float*, optional, default `0`) — The lower bound of the range of random values. The value is not included in the range. The default is 0.
- `max` (*series int|float*, optional, default `1`) — The upper bound of the range of random values. The value is not included in the range. The default is 1.
- `seed` (*series int*, optional) — Optional argument. When the same seed is used, allows successive calls to the function to produce a repeatable set of values.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.random).*

### Returns
A random value.

---

## math.round()

Returns the value of number rounded to the nearest integer, with ties rounding up. If the precision parameter is used, returns a float value rounded to that amount of decimal places.

### Syntax

```pine
math.round(number, precision) → series float
```

### Arguments

- `number` (*series int|float*) — The value to be rounded.
- `precision` (*series int*, optional) — Optional argument. Decimal places to which `number` will be rounded. When no argument is supplied, rounding is to the nearest integer.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.round).*

### Returns
The value of number rounded to the nearest integer, or according to precision.

### Remarks
Note that for 'na' values function returns 'na'.

---

## math.round_to_mintick()

Returns the value rounded to the symbol's mintick, i.e. the nearest value that can be divided by syminfo.mintick, without the remainder, with ties rounding up.

### Syntax

```pine
math.round_to_mintick(number) → series float
```

### Arguments

- `number` (*series int|float*) — The value to be rounded.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.round_to_mintick).*

### Returns
The number rounded to tick precision.

### Remarks
Note that for 'na' values function returns 'na'.

---

## math.sign()

Sign (signum) of number is zero if number is zero, 1.0 if number is greater than zero, -1.0 if number is less than zero.

### Syntax

```pine
math.sign(number) → series float
```

### Arguments

- `number` (*series int|float*) — Number to calculate the sign of.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.sign).*

### Returns
The sign of the argument.

---

## math.sin()

The sin function returns the trigonometric sine of an angle.

### Syntax

```pine
math.sin(angle) → series float
```

### Arguments

- `angle` (*series int|float*) — Angle, in radians.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.sin).*

### Returns
The trigonometric sine of an angle.

---

## math.sqrt()

Square root of any number >= 0 is the unique y >= 0 such that y^2 = number.

### Syntax

```pine
math.sqrt(number) → series float
```

### Arguments

- `number` (*series int|float*) — The number to find the Square root of.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.sqrt).*

### Returns
The square root of number.

---

## math.sum()

The sum function returns the sliding sum of last y values of x.

### Syntax

```pine
math.sum(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.sum).*

### Returns
Sum of source for length bars back.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

---

## math.tan()

The tan function returns the trigonometric tangent of an angle.

### Syntax

```pine
math.tan(angle) → series float
```

### Arguments

- `angle` (*series int|float*) — Angle, in radians.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.tan).*

### Returns
The trigonometric tangent of an angle.

---

## math.todegrees()

Returns an approximately equivalent angle in degrees from an angle measured in radians.

### Syntax

```pine
math.todegrees(radians) → series float
```

### Arguments

- `radians` (*series int|float*) — Angle in radians.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.todegrees).*

### Returns
The angle value in degrees.

---

## math.toradians()

Returns an approximately equivalent angle in radians from an angle measured in degrees.

### Syntax

```pine
math.toradians(degrees) → series float
```

### Arguments

- `degrees` (*series int|float*) — Angle in degrees.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.toradians).*

### Returns
The angle value in radians.

---

## matrix.add_col()

The function adds a column at the column index of the id matrix. The column can consist of na values, or an array can be used to provide values.

### Syntax

```pine
matrix.add_col(id, column) → void
matrix.add_col(id, column, array_id) → void
matrix.add_col(id, column, array_id) → void
```

### Arguments

- `column` (*series int*, optional, default `matrix.columns()`) — The index of the column after which the new column will be inserted. Optional. The default value is [matrix.columns](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.columns).
- `array_id` (*any[]*) — An array to be inserted. Optional.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.add_col).*

### Remarks
Rather than add columns to an empty matrix, it is far more efficient to declare a matrix with explicit dimensions and fill it with values. Adding a column is also much slower than adding a row with the matrix.add_row function.

### Code Example
```pine
//@version=6
indicator("`matrix.add_col()` Example 1")

// Create a 2x3 "int" matrix containing values `0`.
m = matrix.new<int>(2, 3, 0)

// Add a column with `na` values to the matrix.
matrix.add_col(m)

// Display matrix elements.
if barstate.islastconfirmedhistory
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix elements:")
    table.cell(t, 0, 1, str.tostring(m))

//@version=6
indicator("`matrix.add_col()` Example 2")

if barstate.islastconfirmedhistory
    // Create an empty matrix object. 
    var m = matrix.new<int>()
    
    // Create an array with values `1` and `3`.
    var a = array.from(1, 3)
    
    // Add the `a` array as the first column of the empty matrix.
    matrix.add_col(m, 0, a)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix elements:")
    table.cell(t, 0, 1, str.tostring(m))
```

---

## matrix.add_row()

The function adds a row at the row index of the id matrix. The row can consist of na values, or an array can be used to provide values.

### Syntax

```pine
matrix.add_row(id, row, array_id) → void
```

### Arguments

- `row` (*series int*, optional, default `matrix.rows()`) — The index of the row after which the new row will be inserted. Optional. The default value is [matrix.rows](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.rows).
- `array_id` (*any[]*) — An array to be inserted. Optional.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.add_row).*

### Remarks
Indexing of rows and columns starts at zero. Rather than add rows to an empty matrix, it is far more efficient to declare a matrix with explicit dimensions and fill it with values.

### Code Example
```pine
//@version=6
indicator("`matrix.add_row()` Example 1")

// Create a 2x3 "int" matrix containing values `0`.
m = matrix.new<int>(2, 3, 0)

// Add a row with `na` values to the matrix.
matrix.add_row(m)

// Display matrix elements.
if barstate.islastconfirmedhistory
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix elements:")
    table.cell(t, 0, 1, str.tostring(m))

//@version=6
indicator("`matrix.add_row()` Example 2")

if barstate.islastconfirmedhistory
    // Create an empty matrix object. 
    var m = matrix.new<int>()
    
    // Create an array with values `1` and `2`.
    var a = array.from(1, 2)
    
    // Add the `a` array as the first row of the empty matrix.
    matrix.add_row(m, 0, a)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix elements:")
    table.cell(t, 0, 1, str.tostring(m))
```

---

## matrix.avg()

The function calculates the average of all elements in the matrix.

### Syntax

```pine
matrix.avg(id) → series float|int
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.avg).*

### Returns
The average value from the id matrix.

### Code Example
```pine
//@version=6
indicator("`matrix.avg()` Example")

// Create a 2x2 matrix.
var m = matrix.new<int>(2, 2, na)
// Fill the matrix with values.
matrix.set(m, 0, 0, 1)
matrix.set(m, 0, 1, 2)
matrix.set(m, 1, 0, 3)
matrix.set(m, 1, 1, 4)

// Get the average value of the matrix.
var x = matrix.avg(m)

plot(x, 'Matrix average value')
```

---

## matrix.col()

The function creates a one-dimensional array from the elements of a matrix column.

### Syntax

```pine
matrix.col(id, column) → type[]
```

### Arguments

- `column` (*series int*) — Index of the required column.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.col).*

### Returns
An array ID containing the column values of the id matrix.

### Remarks
Indexing of rows starts at 0.

### Code Example
```pine
//@version=6
indicator("`matrix.col()` Example", "", true)

// Create a 2x3 "float" matrix from `hlc3` values.
m = matrix.new<float>(2, 3, hlc3)

// Return an array with the values of the first column of matrix `m`.
a = matrix.col(m, 0)

// Plot the first value from the array `a`.
plot(array.get(a, 0))
```

---

## matrix.columns()

The function returns the number of columns in the matrix.

### Syntax

```pine
matrix.columns(id) → series int
```

### Arguments

- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.columns).*

### Returns
The number of columns in the matrix id.

### Code Example
```pine
//@version=6
indicator("`matrix.columns()` Example")

// Create a 2x6 matrix with values `0`.
var m = matrix.new<int>(2, 6, 0)

// Get the quantity of columns in matrix `m`.
var x = matrix.columns(m)

// Display using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, "Columns: " + str.tostring(x) + "\n" + str.tostring(m))
```

---

## matrix.concat()

The function appends the m2 matrix to the m1 matrix.

### Syntax

```pine
matrix.concat(id1, id2) → matrix<type>
```

### Arguments

- `id2` (*matrix<any>*) — Matrix object whose elements will be appended to `id1`.
- `id1` (*matrix<any>*) — Matrix object to concatenate into.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.concat).*

### Returns
Returns the id1 matrix concatenated with the id2 matrix.

### Remarks
The number of columns in both matrices must be identical.

### Code Example
```pine
//@version=6
indicator("`matrix.concat()` Example")

// Create a 2x4 "int" matrix containing values `0`.
m1 = matrix.new<int>(2, 4, 0)
// Create a 2x4 "int" matrix containing values `1`.
m2 = matrix.new<int>(2, 4, 1)

// Append matrix `m2` to `m1`.
matrix.concat(m1, m2)

// Display matrix elements.
if barstate.islastconfirmedhistory
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix Elements:")
    table.cell(t, 0, 1, str.tostring(m1))
```

---

## matrix.copy()

The function creates a new matrix which is a copy of the original.

### Syntax

```pine
matrix.copy(id) → matrix<type>
```

### Arguments

- `id` (*matrix<any>*) — A matrix object to copy.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.copy).*

### Returns
A new matrix object of the copied id matrix.

### Code Example
```pine
//@version=6
indicator("`matrix.copy()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 "float" matrix with `1` values.
    var m1 = matrix.new<float>(2, 3, 1)
    
    // Copy the matrix to a new one.
    // Note that unlike what `matrix.copy()` does, 
    // the simple assignment operation `m2 = m1`
    // would NOT create a new copy of the `m1` matrix.
    // It would merely create a copy of its ID referencing the same matrix.
    var m2 = matrix.copy(m1)
    
    // Display using a table.
    var t = table.new(position.top_right, 5, 2, color.green)
    table.cell(t, 0, 0, "Original Matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Matrix Copy:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.det()

The function returns the determinant of a square matrix.

### Syntax

```pine
matrix.det(id) → series float|int
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.det).*

### Returns
The determinant value of the id matrix.

### Remarks
Function calculation based on the LU decomposition algorithm.

### Code Example
```pine
//@version=6
indicator("`matrix.det` Example")

// Create a 2x2 matrix.
var m = matrix.new<float>(2, 2, na)
// Fill the matrix with values.
matrix.set(m, 0, 0,  3)
matrix.set(m, 0, 1,  7)
matrix.set(m, 1, 0,  1)
matrix.set(m, 1, 1, -4)

// Get the determinant of the matrix. 
var x = matrix.det(m)

plot(x, 'Matrix determinant')
```

---

## matrix.diff()

The function returns a new matrix resulting from the subtraction between matrices id1 and id2, or of matrix id1 and an id2 scalar (a numerical value).

### Syntax

```pine
matrix.diff(id1, id2) → matrix<int|float>
```

### Arguments

- `id2` (*series int|float|matrix<int|float>*) — Matrix object or a scalar value to be subtracted.
- `id1` (*matrix<int|float>*) — Matrix to subtract from.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.diff).*

### Returns
A new matrix object containing the difference between id2 and id1.

### Code Example
```pine
//@version=6
indicator("`matrix.diff()` Example 1")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 matrix containing values `5`.
    var m1 = matrix.new<float>(2, 3, 5) 
    // Create a 2x3 matrix containing values `4`.
    var m2 = matrix.new<float>(2, 3, 4) 
    // Create a new matrix containing the difference between matrices `m1` and `m2`.
    var m3 = matrix.diff(m1, m2) 
    
    // Display using a table.
    var t = table.new(position.top_right, 1, 2, color.green)
    table.cell(t, 0, 0, "Difference between two matrices:")
    table.cell(t, 0, 1, str.tostring(m3))

//@version=6
indicator("`matrix.diff()` Example 2")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 matrix with values `4`.
    var m1 = matrix.new<float>(2, 3, 4)
    
    // Create a new matrix containing the difference between the `m1` matrix and the "int" value `1`.
    var m2 = matrix.diff(m1, 1)
    
    // Display using a table.
    var t = table.new(position.top_right, 1, 2, color.green)
    table.cell(t, 0, 0, "Difference between a matrix and a scalar:")
    table.cell(t, 0, 1, str.tostring(m2))
```

---

## matrix.eigenvalues()

The function returns an array containing the eigenvalues of a square matrix.

### Syntax

```pine
matrix.eigenvalues(id) → array<float|int>
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.eigenvalues).*

### Returns
An array containing the eigenvalues of the id matrix.

### Remarks
The function is calculated using "The Implicit QL Algorithm".

### Code Example
```pine
//@version=6
indicator("`matrix.eigenvalues()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix. 
    var m1 = matrix.new<int>(2, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 2)
    matrix.set(m1, 0, 1, 4)
    matrix.set(m1, 1, 0, 6)
    matrix.set(m1, 1, 1, 8)
    
    // Get the eigenvalues of the matrix.
    tr = matrix.eigenvalues(m1)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix elements:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Array of Eigenvalues:")
    table.cell(t, 1, 1, str.tostring(tr))
```

---

## matrix.eigenvectors()

Returns a matrix of eigenvectors, in which each column is an eigenvector of the id matrix.

### Syntax

```pine
matrix.eigenvectors(id) → matrix<float|int>
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.eigenvectors).*

### Returns
A new matrix containing the eigenvectors of the id matrix.

### Remarks
The function is calculated using "The Implicit QL Algorithm".

### Code Example
```pine
//@version=6
indicator("`matrix.eigenvectors()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix 
    var m1 = matrix.new<int>(2, 2, 1)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 2)
    matrix.set(m1, 0, 1, 4)
    matrix.set(m1, 1, 0, 6)
    matrix.set(m1, 1, 1, 8)
    
    // Get the eigenvectors of the matrix.
    m2 = matrix.eigenvectors(m1)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix Elements:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Matrix Eigenvectors:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.elements_count()

The function returns the total number of all matrix elements.

---

### Syntax

```pine
matrix.elements_count(id) → series int
```

### Arguments

- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.elements_count).*

## matrix.fill()

The function fills a rectangular area of the id matrix defined by the indices from_column to to_column (not including it) and from_row to to_row(not including it) with the value.

### Syntax

```pine
matrix.fill(id, value, from_row, to_row, from_column, to_column) → void
```

### Arguments

- `value` (*any*) — The value to fill with.
- `from_row` (*series int*, optional, default `0`) — Row index from which the fill will begin (inclusive). Optional. The default value is 0.
- `to_row` (*series int*, optional, default `matrix.rows()`) — Row index where the fill will end (not inclusive). Optional. The default value is [matrix.rows](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.rows).
- `from_column` (*series int*, optional, default `0`) — Column index from which the fill will begin (inclusive). Optional. The default value is 0.
- `to_column` (*series int*, optional, default `matrix.columns()`) — Column index where the fill will end (non inclusive). Optional. The default value is [matrix.columns](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.columns).
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.fill).*

### Code Example
```pine
//@version=6
indicator("`matrix.fill()` Example")

// Create a 4x5 "int" matrix containing values `0`.
m = matrix.new<float>(4, 5, 0)

// Fill the intersection of rows 1 to 2 and columns 2 to 3 of the matrix with `hl2` values.
matrix.fill(m, hl2, 0, 2, 1, 3)

// Display using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(m))
```

---

## matrix.get()

The function returns the element with the specified index of the matrix.

### Syntax

```pine
matrix.get(id, row, column) → <matrix_type>
```

### Arguments

- `row` (*series int*) — Index of the required row.
- `column` (*series int*) — Index of the required column.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.get).*

### Returns
The value of the element at the row and column index of the id matrix.

### Remarks
Indexing of the rows and columns starts at zero.

### Code Example
```pine
//@version=6
indicator("`matrix.get()` Example", "", true)

// Create a 2x3 "float" matrix from the `hl2` values.
m = matrix.new<float>(2, 3, hl2)

// Return the value of the element at index [0, 0] of matrix `m`.
x = matrix.get(m, 0, 0)

plot(x)
```

---

## matrix.inv()

The function returns the inverse of a square matrix.

### Syntax

```pine
matrix.inv(id) → matrix<float|int>
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.inv).*

### Returns
A new matrix, which is the inverse of the id matrix.

### Remarks
The function is calculated using the LU decomposition algorithm.

### Code Example
```pine
//@version=6
indicator("`matrix.inv()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix. 
    var m1 = matrix.new<int>(2, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 1, 0, 3)
    matrix.set(m1, 1, 1, 4)
    
    // Inverse of the matrix.
    var m2 = matrix.inv(m1)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original Matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Inverse matrix:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.is_antidiagonal()

The function determines if the matrix is anti-diagonal (all elements outside the secondary diagonal are zero).

### Syntax

```pine
matrix.is_antidiagonal(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_antidiagonal).*

### Returns
Returns true if the id matrix is ​​anti-diagonal, false otherwise.

### Remarks
Returns false with non-square matrices.

---

## matrix.is_antisymmetric()

The function determines if a matrix is antisymmetric (its transpose equals its negative).

### Syntax

```pine
matrix.is_antisymmetric(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_antisymmetric).*

### Returns
Returns true, if the id matrix is antisymmetric, false otherwise.

### Remarks
Returns false with non-square matrices.

---

## matrix.is_binary()

The function determines if the matrix is binary (when all elements of the matrix are 0 or 1).

### Syntax

```pine
matrix.is_binary(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_binary).*

### Returns
Returns true if the id matrix is binary, false otherwise.

---

## matrix.is_diagonal()

The function determines if the matrix is diagonal (all elements outside the main diagonal are zero).

### Syntax

```pine
matrix.is_diagonal(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_diagonal).*

### Returns
Returns true if the id matrix is diagonal, false otherwise.

### Remarks
Returns false with non-square matrices.

---

## matrix.is_identity()

The function determines if a matrix is an identity matrix (elements with ones on the main diagonal and zeros elsewhere).

### Syntax

```pine
matrix.is_identity(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_identity).*

### Returns
Returns true if id is an identity matrix, false otherwise.

### Remarks
Returns false with non-square matrices.

---

## matrix.is_square()

The function determines if the matrix is square (it has the same number of rows and columns).

### Syntax

```pine
matrix.is_square(id) → series bool
```

### Arguments

- `id` (*matrix<any>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_square).*

### Returns
Returns true if the id matrix is square, false otherwise.

---

## matrix.is_stochastic()

The function determines if the matrix is stochastic.

### Syntax

```pine
matrix.is_stochastic(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_stochastic).*

### Returns
Returns true if the id matrix is stochastic, false otherwise.

---

## matrix.is_symmetric()

The function determines if a square matrix is symmetric (elements are symmetric with respect to the main diagonal).

### Syntax

```pine
matrix.is_symmetric(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_symmetric).*

### Returns
Returns true if the id matrix is symmetric, false otherwise.

### Remarks
Returns false with non-square matrices.

---

## matrix.is_triangular()

The function determines if the matrix is triangular (if all elements above or below the main diagonal are zero).

### Syntax

```pine
matrix.is_triangular(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to test.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_triangular).*

### Returns
Returns true if the id matrix is triangular, false otherwise.

### Remarks
Returns false with non-square matrices.

---

## matrix.is_zero()

The function determines if all elements of the matrix are zero.

### Syntax

```pine
matrix.is_zero(id) → series bool
```

### Arguments

- `id` (*matrix<float|int>*) — Matrix object to check.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.is_zero).*

### Returns
Returns true if all elements of the id matrix are zero, false otherwise.

---

## matrix.kron()

The function returns the Kronecker product for the id1 and id2 matrices.

### Syntax

```pine
matrix.kron(id1, id2) → matrix<float|int>
```

### Arguments

- `id2` (*matrix<float|int>*) — Second matrix object.
- `id1` (*matrix<float|int>*) — First matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.kron).*

### Returns
A new matrix containing the Kronecker product of id1 and id2.

### Code Example
```pine
//@version=6
indicator("`matrix.kron()` Example")

// Display using a table.
if barstate.islastconfirmedhistory
    // Create two matrices with default values `1` and `2`. 
    var m1 = matrix.new<float>(2, 2, 1) 
    var m2 = matrix.new<float>(2, 2, 2) 
    
    // Calculate the Kronecker product of the matrices.
    var m3 = matrix.kron(m1, m2) 
    
    // Display matrix elements.
    var t = table.new(position.top_right, 5, 2, color.green)
    table.cell(t, 0, 0, "Matrix 1:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 1, "⊗")
    table.cell(t, 2, 0, "Matrix 2:")
    table.cell(t, 2, 1, str.tostring(m2))
    table.cell(t, 3, 1, "=")
    table.cell(t, 4, 0, "Kronecker product:")
    table.cell(t, 4, 1, str.tostring(m3))
```

---

## matrix.max()

The function returns the largest value from the matrix elements.

### Syntax

```pine
matrix.max(id) → series float|int
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.max).*

### Returns
The maximum value from the id matrix.

### Code Example
```pine
//@version=6
indicator("`matrix.max()` Example")

// Create a 2x2 matrix.
var m = matrix.new<int>(2, 2, na)
// Fill the matrix with values.
matrix.set(m, 0, 0, 1)
matrix.set(m, 0, 1, 2)
matrix.set(m, 1, 0, 3)
matrix.set(m, 1, 1, 4)

// Get the maximum value in the matrix.
var x = matrix.max(m)

plot(x, 'Matrix maximum value')
```

---

## matrix.median()

The function calculates the median ("the middle" value) of matrix elements.

### Syntax

```pine
matrix.median(id) → series float|int
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.median).*

### Remarks
Note that na elements of the matrix are not considered when calculating the median.

### Code Example
```pine
//@version=6
indicator("`matrix.median()` Example")

// Create a 2x2 matrix.
m = matrix.new<int>(2, 2, na)
// Fill the matrix with values.
matrix.set(m, 0, 0, 1)
matrix.set(m, 0, 1, 2)
matrix.set(m, 1, 0, 3)
matrix.set(m, 1, 1, 4)

// Get the median of the matrix.
x = matrix.median(m)

plot(x, 'Median of the matrix')
```

---

## matrix.min()

The function returns the smallest value from the matrix elements.

### Syntax

```pine
matrix.min(id) → series float|int
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.min).*

### Returns
The smallest value from the id matrix.

### Code Example
```pine
//@version=6
indicator("`matrix.min()` Example")

// Create a 2x2 matrix.
var m = matrix.new<int>(2, 2, na)
// Fill the matrix with values.
matrix.set(m, 0, 0, 1)
matrix.set(m, 0, 1, 2)
matrix.set(m, 1, 0, 3)
matrix.set(m, 1, 1, 4)

// Get the minimum value from the matrix.
var x = matrix.min(m)

plot(x, 'Matrix minimum value')
```

---

## matrix.mode()

The function calculates the mode of the matrix, which is the most frequently occurring value from the matrix elements. When there are multiple values occurring equally frequently, the function returns the smallest of those values.

### Syntax

```pine
matrix.mode(id) → series float|int
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.mode).*

### Returns
The most frequently occurring value from the id matrix. If none exists, returns the smallest value instead.

### Remarks
Note that na elements of the matrix are not considered when calculating the mode.

### Code Example
```pine
//@version=6
indicator("`matrix.mode()` Example")

// Create a 2x2 matrix.
var m = matrix.new<int>(2, 2, na)
// Fill the matrix with values.
matrix.set(m, 0, 0, 0)
matrix.set(m, 0, 1, 0)
matrix.set(m, 1, 0, 1)
matrix.set(m, 1, 1, 1)

// Get the mode of the matrix.
var x = matrix.mode(m)

plot(x, 'Mode of the matrix')
```

---

## matrix.mult()

The function returns a new matrix resulting from the product between the matrices id1 and id2, or between an id1 matrix and an id2 scalar (a numerical value), or between an id1 matrix and an id2 vector (an array of values).

### Syntax

```pine
matrix.mult(id1, id2) → matrix<int|float>
matrix.mult(id1, id2) → array<int|float>
matrix.mult(id1, id2) → array|matrix<int|float>
```

### Arguments

- `id2` (*series int|float|matrix<int|float>|array<int|float>*) — Second matrix object, value or array.
- `id1` (*matrix<int|float>*) — First matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.mult).*

### Returns
A new matrix object containing the product of id2 and id1.

### Code Example
```pine
//@version=6
indicator("`matrix.mult()` Example 1")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 6x2 matrix containing values `5`.
    var m1 = matrix.new<float>(6, 2, 5) 
    // Create a 2x3 matrix containing values `4`.
    // Note that it must have the same quantity of rows as there are columns in the first matrix.
    var m2 = matrix.new<float>(2, 3, 4) 
    // Create a new matrix from the multiplication of the two matrices.
    var m3 = matrix.mult(m1, m2) 
    
    // Display using a table.
    var t = table.new(position.top_right, 1, 2, color.green)
    table.cell(t, 0, 0, "Product of two matrices:")
    table.cell(t, 0, 1, str.tostring(m3))

//@version=6
indicator("`matrix.mult()` Example 2")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 matrix containing values `4`.
    var m1 = matrix.new<float>(2, 3, 4) 
    
    // Create a new matrix from the product of the two matrices.
    scalar = 5
    var m2 = matrix.mult(m1, scalar) 
    
    // Display using a table.
    var t = table.new(position.top_right, 5, 2, color.green)
    table.cell(t, 0, 0, "Matrix 1:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 1, "x")
    table.cell(t, 2, 0, "Scalar:")
    table.cell(t, 2, 1, str.tostring(scalar))
    table.cell(t, 3, 1, "=")
    table.cell(t, 4, 0, "Matrix 2:")
    table.cell(t, 4, 1, str.tostring(m2))

//@version=6
indicator("`matrix.mult()` Example 3")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 matrix containing values `4`.
    var m1 = matrix.new<int>(2, 3, 4)
    
    // Create an array of three elements.
    var int[] a = array.from(1, 1, 1)
    
    // Create a new matrix containing the product of the `m1` matrix and the `a` array.
    var m3 = matrix.mult(m1, a) 
    
    // Display using a table.
    var t = table.new(position.top_right, 5, 2, color.green)
    table.cell(t, 0, 0, "Matrix 1:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 1, "x")
    table.cell(t, 2, 0, "Value:")
    table.cell(t, 2, 1, str.tostring(a, " "))
    table.cell(t, 3, 1, "=")
    table.cell(t, 4, 0, "Matrix 3:")
    table.cell(t, 4, 1, str.tostring(m3))
```

---

## matrix.new<type>()

The function creates a new matrix object. A matrix is a two-dimensional data structure containing rows and columns. All elements in the matrix must be of the type specified in the type template ("<type>").

### Syntax

```pine
matrix.new<type>(rows, columns, initial_value) → matrix<type>
```

### Arguments

- `rows` (*series int*, optional, default `0`) — Initial row count of the matrix. Optional. The default value is 0.
- `columns` (*series int*, optional, default `0`) — Initial column count of the matrix. Optional. The default value is 0.
- `initial_value` (*matrix<type>*, optional, default `na`) — Initial value of all matrix elements. Optional. The default is 'na'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.new<type>).*

### Returns
The ID of the new matrix object.

### Code Example
```pine
//@version=6
indicator("`matrix.new<type>()` Example 1")

// Create a 2x3 (2 rows x 3 columns) "int" matrix with values zero.
var m = matrix.new<int>(2, 3, 0)

// Display using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(m))

//@version=6
indicator("`matrix.new<type>()` Example 2")

// Function to create a matrix whose rows are filled with array values.
matrixFromArray(int rows, int columns, array<float> data) =>
    m = matrix.new<float>(rows, columns)
    for i = 0 to rows <= 0 ? na : rows - 1
        for j = 0 to columns <= 0 ? na : columns - 1
            matrix.set(m, i, j, array.get(data, i * columns + j))
    m
    
// Create a 3x3 matrix from an array of values.
var m1 = matrixFromArray(3, 3, array.from(1, 2, 3, 4, 5, 6, 7, 8, 9))
// Display using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(m1))

//@version=6
indicator("`matrix.new<type>()` Example 3")

// Function to create a matrix from a text string.
// Values in a row must be separated by a space. Each line is one row.
matrixFromInputArea(stringOfValues) =>
    var rowsArray = str.split(stringOfValues, "\n")
    var rows = array.size(rowsArray)
    var cols = array.size(str.split(array.get(rowsArray, 0), " "))
    var matrix = matrix.new<float>(rows, cols, na) 
    row = 0
    for rowString in rowsArray
        col = 0
        values = str.split(rowString, " ")
        for val in values
            matrix.set(matrix, row, col, str.tonumber(val))
            col += 1
        row += 1
    matrix

stringInput = input.text_area("1 2 3\n4 5 6\n7 8 9")
var m = matrixFromInputArea(stringInput)    

// Display using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(m))

//@version=6
indicator("`matrix.new<type>()` Example 4")

// Function to create a matrix with random values (0.0 to 1.0).
matrixRandom(int rows, int columns)=>
    result = matrix.new<float>(rows, columns)
    for i = 0 to rows - 1
        for j = 0 to columns - 1
            matrix.set(result, i, j, math.random())
    result

// Create a 2x3 matrix with random values.
var m = matrixRandom(2, 3)

// Display using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(m))
```

---

## matrix.pinv()

The function returns the pseudoinverse of a matrix.

### Syntax

```pine
matrix.pinv(id) → matrix<float|int>
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.pinv).*

### Returns
A new matrix containing the pseudoinverse of the id matrix.

### Remarks
The function is calculated using a Moore–Penrose inverse formula based on singular-value decomposition of a matrix. For non-singular square matrices this function returns the result of matrix.inv.

### Code Example
```pine
//@version=6
indicator("`matrix.pinv()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix. 
    var m1 = matrix.new<int>(2, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 1, 0, 3)
    matrix.set(m1, 1, 1, 4)
    
    // Pseudoinverse of the matrix.
    var m2 = matrix.pinv(m1)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original Matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Pseudoinverse matrix:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.pow()

The function calculates the product of the matrix by itself power times.

### Syntax

```pine
matrix.pow(id, power) → matrix<float|int>
```

### Arguments

- `power` (*series int*) — The number of times the matrix will be multiplied by itself.
- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.pow).*

### Returns
The product of the id matrix by itself power times.

### Code Example
```pine
//@version=6
indicator("`matrix.pow()` Example")

// Display using a table.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix. 
    var m1 = matrix.new<int>(2, 2, 2)
    // Calculate the power of three of the matrix.
    var m2 = matrix.pow(m1, 3)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original Matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Matrix³:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.rank()

The function calculates the rank of the matrix.

### Syntax

```pine
matrix.rank(id) → series int
```

### Arguments

- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.rank).*

### Returns
The rank of the id matrix.

### Code Example
```pine
//@version=6
indicator("`matrix.rank()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix. 
    var m1 = matrix.new<int>(2, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 1, 0, 3)
    matrix.set(m1, 1, 1, 4)
    
    // Get the rank of the matrix. 
    r = matrix.rank(m1)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix elements:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Rank of the matrix:")
    table.cell(t, 1, 1, str.tostring(r))
```

---

## matrix.remove_col()

The function removes the column at column index of the id matrix and returns an array containing the removed column's values.

### Syntax

```pine
matrix.remove_col(id, column) → type[]
```

### Arguments

- `column` (*series int*, optional, default `matrix.columns()`) — The index of the column to be removed. Optional. The default value is [matrix.columns](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.columns).
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.remove_col).*

### Returns
An array containing the elements of the column removed from the id matrix.

### Remarks
Indexing of rows and columns starts at zero. It is far more efficient to declare matrices with explicit dimensions than to build them by adding or removing columns. Deleting a column is also much slower than deleting a row with the matrix.remove_row function.

### Code Example
```pine
//@version=6
indicator("matrix_remove_col", overlay = true)

// Create a 2x2 matrix with ones.
var matrixOrig = matrix.new<int>(2, 2, 1)

// Set values to the 'matrixOrig' matrix.
matrix.set(matrixOrig, 0, 1, 2)
matrix.set(matrixOrig, 1, 0, 3)
matrix.set(matrixOrig, 1, 1, 4)

// Create a copy of the 'matrixOrig' matrix.
matrixCopy = matrix.copy(matrixOrig)

// Remove the first column from the `matrixCopy` matrix.
arr = matrix.remove_col(matrixCopy, 0)

// Display matrix elements.
if barstate.islastconfirmedhistory
    var t = table.new(position.top_right, 3, 2, color.green)
    table.cell(t, 0, 0, "Original Matrix:")
    table.cell(t, 0, 1, str.tostring(matrixOrig))
    table.cell(t, 1, 0, "Removed Elements:")
    table.cell(t, 1, 1, str.tostring(arr))
    table.cell(t, 2, 0, "Result Matrix:")
    table.cell(t, 2, 1, str.tostring(matrixCopy))
```

---

## matrix.remove_row()

The function removes the row at row index of the id matrix and returns an array containing the removed row's values.

### Syntax

```pine
matrix.remove_row(id, row) → type[]
```

### Arguments

- `row` (*series int*, optional, default `matrix.rows()`) — The index of the row to be deleted. Optional. The default value is [matrix.rows](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.rows).
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.remove_row).*

### Returns
An array containing the elements of the row removed from the id matrix.

### Remarks
Indexing of rows and columns starts at zero. It is far more efficient to declare matrices with explicit dimensions than to build them by adding or removing rows.

### Code Example
```pine
//@version=6
indicator("matrix_remove_row", overlay = true)

// Create a 2x2 "int" matrix containing values `1`.
var matrixOrig = matrix.new<int>(2, 2, 1)

// Set values to the 'matrixOrig' matrix.
matrix.set(matrixOrig, 0, 1, 2)
matrix.set(matrixOrig, 1, 0, 3)
matrix.set(matrixOrig, 1, 1, 4)

// Create a copy of the 'matrixOrig' matrix.
matrixCopy = matrix.copy(matrixOrig)

// Remove the first row from the matrix `matrixCopy`.
arr = matrix.remove_row(matrixCopy, 0)

// Display matrix elements.
if barstate.islastconfirmedhistory
    var t = table.new(position.top_right, 3, 2, color.green)
    table.cell(t, 0, 0, "Original Matrix:")
    table.cell(t, 0, 1, str.tostring(matrixOrig))
    table.cell(t, 1, 0, "Removed Elements:")
    table.cell(t, 1, 1, str.tostring(arr))
    table.cell(t, 2, 0, "Result Matrix:")
    table.cell(t, 2, 1, str.tostring(matrixCopy))
```

---

## matrix.reshape()

The function rebuilds the id matrix to rows x cols dimensions.

### Syntax

```pine
matrix.reshape(id, rows, columns) → void
```

### Arguments

- `rows` (*series int*) — The number of rows of the reshaped matrix.
- `columns` (*series int*) — The of columns of the reshaped matrix.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.reshape).*

### Code Example
```pine
//@version=6
indicator("`matrix.reshape()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 matrix.
    var m1 = matrix.new<float>(2, 3)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 0, 2, 3)
    matrix.set(m1, 1, 0, 4)
    matrix.set(m1, 1, 1, 5)
    matrix.set(m1, 1, 2, 6)
    
    // Copy the matrix to a new one.
    var m2 = matrix.copy(m1)
    
    // Reshape the copy to a 3x2.
    matrix.reshape(m2, 3, 2)
    
    // Display using a table.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Reshaped matrix:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.reverse()

The function reverses the order of rows and columns in the matrix id. The first row and first column become the last, and the last become the first.

### Syntax

```pine
matrix.reverse(id) → void
```

### Arguments

- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.reverse).*

### Code Example
```pine
//@version=6
indicator("`matrix.reverse()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Copy the matrix to a new one.
    var m1 = matrix.new<int>(2, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 1, 0, 3)
    matrix.set(m1, 1, 1, 4)
    
    // Copy matrix elements to a new matrix.
    var m2 = matrix.copy(m1)
    
    // Reverse the `m2` copy of the original matrix. 
    matrix.reverse(m2)
    
    // Display using a table.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Reversed matrix:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.row()

The function creates a one-dimensional array from the elements of a matrix row.

### Syntax

```pine
matrix.row(id, row) → type[]
```

### Arguments

- `row` (*series int*) — Index of the required row.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.row).*

### Returns
An array ID containing the row values of the id matrix.

### Remarks
Indexing of rows starts at 0.

### Code Example
```pine
//@version=6
indicator("`matrix.row()` Example", "", true)

// Create a 2x3 "float" matrix from `hlc3` values.
m = matrix.new<float>(2, 3, hlc3)

// Return an array with the values of the first row of the matrix.
a = matrix.row(m, 0)

// Plot the first value from the array `a`.
plot(array.get(a, 0))
```

---

## matrix.rows()

The function returns the number of rows in the matrix.

### Syntax

```pine
matrix.rows(id) → series int
```

### Arguments

- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.rows).*

### Returns
The number of rows in the matrix id.

### Code Example
```pine
//@version=6
indicator("`matrix.rows()` Example")

// Create a 2x6 matrix with values `0`.
var m = matrix.new<int>(2, 6, 0)

// Get the quantity of rows in the matrix.
var x = matrix.rows(m)

// Display using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, "Rows: " + str.tostring(x) + "\n" + str.tostring(m))
```

---

## matrix.set()

The function assigns value to the element at the row and column of the id matrix.

### Syntax

```pine
matrix.set(id, row, column, value) → void
```

### Arguments

- `row` (*series int*) — The row index of the element to be modified.
- `column` (*series int*) — The column index of the element to be modified.
- `value` (*any*) — The new value to be set.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.set).*

### Code Example
```pine
//@version=6
indicator("`matrix.set()` Example")

// Create a 2x3 "int" matrix containing values `4`.
m = matrix.new<int>(2, 3, 4)

// Replace the value of element at row 1 and column 2 with value `3`.
matrix.set(m, 0, 1, 3)

// Display using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(m))
```

---

## matrix.sort()

The function rearranges the rows in the id matrix following the sorted order of the values in the column.

### Syntax

```pine
matrix.sort(id, column, order) → void
```

### Arguments

- `column` (*series int*, optional, default `0`) — Index of the column whose sorted values determine the new order of rows. Optional. The default value is 0.
- `order` (*simple sort_order*, optional, default `order.ascending`) — The sort order. Possible values: [order.ascending](https://www.tradingview.com/pine-script-reference/v6/#var_order.ascending) (default), [order.descending](https://www.tradingview.com/pine-script-reference/v6/#var_order.descending).
- `id` (*matrix<int|float|string>*) — A matrix object to be sorted.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.sort).*

### Code Example
```pine
//@version=6
indicator("`matrix.sort()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix. 
    var m1 = matrix.new<float>(2, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 3)
    matrix.set(m1, 0, 1, 4)
    matrix.set(m1, 1, 0, 1)
    matrix.set(m1, 1, 1, 2)
    
    // Copy the matrix to a new one.
    var m2 = matrix.copy(m1)
    // Sort the rows of `m2` using the default arguments (first column and ascending order).
    matrix.sort(m2)
    
    // Display using a table.
    if barstate.islastconfirmedhistory
        var t = table.new(position.top_right, 2, 2, color.green)
        table.cell(t, 0, 0, "Original matrix:")
        table.cell(t, 0, 1, str.tostring(m1))
        table.cell(t, 1, 0, "Sorted matrix:")
        table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.submatrix()

The function extracts a submatrix of the id matrix within the specified indices.

### Syntax

```pine
matrix.submatrix(id, from_row, to_row, from_column, to_column) → matrix<type>
```

### Arguments

- `from_row` (*series int*, optional, default `0`) — Index of the row from which the extraction will begin (inclusive). Optional. The default value is 0.
- `to_row` (*series int*, optional, default `matrix.rows()`) — Index of the row where the extraction will end (non inclusive). Optional. The default value is [matrix.rows](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.rows).
- `from_column` (*series int*, optional, default `0`) — Index of the column from which the extraction will begin (inclusive). Optional. The default value is 0.
- `to_column` (*series int*, optional, default `matrix.columns()`) — Index of the column where the extraction will end (non inclusive). Optional. The default value is [matrix.columns](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.columns).
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.submatrix).*

### Returns
A new matrix object containing the submatrix of the id matrix defined by the from_row, to_row, from_column and to_column indices.

### Remarks
Indexing of the rows and columns starts at zero.

### Code Example
```pine
//@version=6
indicator("`matrix.submatrix()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 matrix matrix with values `0`.
    var m1 = matrix.new<int>(2, 3, 0)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 0, 2, 3)
    matrix.set(m1, 1, 0, 4)
    matrix.set(m1, 1, 1, 5)
    matrix.set(m1, 1, 2, 6)
    
    // Create a 2x2 submatrix of the `m1` matrix.
    var m2 = matrix.submatrix(m1, 0, 2, 1, 3)
    
    // Display using a table.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original Matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Submatrix:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.sum()

The function returns a new matrix resulting from the sum of two matrices id1 and id2, or of an id1 matrix and an id2 scalar (a numerical value).

### Syntax

```pine
matrix.sum(id1, id2) → matrix<int|float>
```

### Arguments

- `id2` (*series int|float|matrix<int|float>*) — Second matrix object, or scalar value.
- `id1` (*matrix<int|float>*) — First matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.sum).*

### Returns
A new matrix object containing the sum of id2 and id1.

### Code Example
```pine
//@version=6
indicator("`matrix.sum()` Example 1")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 matrix containing values `5`.
    var m1 = matrix.new<float>(2, 3, 5) 
    // Create a 2x3 matrix containing values `4`.
    var m2 = matrix.new<float>(2, 3, 4) 
    // Create a new matrix that sums matrices `m1` and `m2`.
    var m3 = matrix.sum(m1, m2) 
    
    // Display using a table.
    var t = table.new(position.top_right, 1, 2, color.green)
    table.cell(t, 0, 0, "Sum of two matrices:")
    table.cell(t, 0, 1, str.tostring(m3))

//@version=6
indicator("`matrix.sum()` Example 2")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x3 matrix with values `4`.
    var m1 = matrix.new<float>(2, 3, 4)
    
    // Create a new matrix containing the sum of the `m1` matrix with the "int" value `1`.
    var m2 = matrix.sum(m1, 1)
    
    // Display using a table.
    var t = table.new(position.top_right, 1, 2, color.green)
    table.cell(t, 0, 0, "Sum of a matrix and a scalar:")
    table.cell(t, 0, 1, str.tostring(m2))
```

---

## matrix.swap_columns()

The function swaps the columns at the index column1 and column2 in the id matrix.

### Syntax

```pine
matrix.swap_columns(id, column1, column2) → void
```

### Arguments

- `column1` (*series int*) — Index of the first column to be swapped.
- `column2` (*series int*) — Index of the second column to be swapped.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.swap_columns).*

### Remarks
Indexing of the rows and columns starts at zero.

### Code Example
```pine
//@version=6
indicator("`matrix.swap_columns()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix with ‘na’ values.
    var m1 = matrix.new<int>(2, 2, na)    
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 1, 0, 3)
    matrix.set(m1, 1, 1, 4)
    
    // Copy the matrix to a new one.
    var m2 = matrix.copy(m1)
    
    // Swap the first and second columns of the matrix copy.
    matrix.swap_columns(m2, 0, 1)

    // Display using a table.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Swapped columns in copy:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.swap_rows()

The function swaps the rows at the index row1 and row2 in the id matrix.

### Syntax

```pine
matrix.swap_rows(id, row1, row2) → void
```

### Arguments

- `row1` (*series int*) — Index of the first row to be swapped.
- `row2` (*series int*) — Index of the second row to be swapped.
- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.swap_rows).*

### Remarks
Indexing of the rows and columns starts at zero.

### Code Example
```pine
//@version=6
indicator("`matrix.swap_rows()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 3x2 matrix with ‘na’ values.
    var m1 = matrix.new<int>(3, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 1, 0, 3)
    matrix.set(m1, 1, 1, 4)
    matrix.set(m1, 2, 0, 5)
    matrix.set(m1, 2, 1, 6)
    
    // Copy the matrix to a new one.
    var m2 = matrix.copy(m1)
    
    // Swap the first and second rows of the matrix copy.
    matrix.swap_rows(m2, 0, 1)
    
    // Display using a table.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Swapped rows in copy:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## matrix.trace()

The function calculates the trace of a matrix (the sum of the main diagonal's elements).

### Syntax

```pine
matrix.trace(id) → series float|int
```

### Arguments

- `id` (*matrix<float|int>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.trace).*

### Returns
The trace of the id matrix.

### Code Example
```pine
//@version=6
indicator("`matrix.trace()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix. 
    var m1 = matrix.new<int>(2, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 1, 0, 3)
    matrix.set(m1, 1, 1, 4)
    
    // Get the trace of the matrix.
    tr = matrix.trace(m1)
    
    // Display matrix elements.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Matrix elements:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Trace of the matrix:")
    table.cell(t, 1, 1, str.tostring(tr))
```

---

## matrix.transpose()

The function creates a new, transposed version of the id. This interchanges the row and column index of each element.

### Syntax

```pine
matrix.transpose(id) → matrix<type>
```

### Arguments

- `id` (*matrix<any>*) — A matrix object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_matrix.transpose).*

### Returns
A new matrix containing the transposed version of the id matrix.

### Code Example
```pine
//@version=6
indicator("`matrix.transpose()` Example")

// For efficiency, execute this code only once.
if barstate.islastconfirmedhistory
    // Create a 2x2 matrix. 
    var m1 = matrix.new<float>(2, 2, na)
    // Fill the matrix with values.
    matrix.set(m1, 0, 0, 1)
    matrix.set(m1, 0, 1, 2)
    matrix.set(m1, 1, 0, 3)
    matrix.set(m1, 1, 1, 4)
    
    // Create a transpose of the matrix.
    var m2 = matrix.transpose(m1)
    
    // Display using a table.
    var t = table.new(position.top_right, 2, 2, color.green)
    table.cell(t, 0, 0, "Original matrix:")
    table.cell(t, 0, 1, str.tostring(m1))
    table.cell(t, 1, 0, "Transposed matrix:")
    table.cell(t, 1, 1, str.tostring(m2))
```

---

## max_bars_back()

Function sets the maximum number of bars that is available for historical reference of a given built-in or user variable. When operator '[]' is applied to a variable - it is a reference to a historical value of that variable.

### Syntax

```pine
max_bars_back(var, num) → void
```

### Arguments

- `var` (*series int|float|bool|color|label|line*) — Series variable identifier for which history buffer should be resized. Possible values are: 'open', 'high', 'low', 'close', 'volume', 'time', or any user defined variable id.
- `num` (*const int*) — History buffer size which is the number of bars that could be referenced for variable 'var'.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_max_bars_back).*

### Returns
void

### Remarks
At the moment 'max_bars_back' cannot be applied to built-ins like 'hl2', 'hlc3', 'ohlc4'. Please use multiple 'max_bars_back' calls as workaround here (e.g. instead of a single ‘max_bars_back(hl2, 100)’ call you should call the function twice: ‘max_bars_back(high, 100), max_bars_back(low, 100)’).  If the indicator or strategy 'max_bars_back' parameter is used, all variables in the indicator are affected. This may result in excessive memory usage and cause runtime problems. When possible (i.e. when the cause is a variable rather than a function), please use the max_bars_back function instead.

### Code Example
```pine
//@version=6
indicator("max_bars_back")
close_() => close
depth() => 400
d = depth()
v = close_()
max_bars_back(v, 500)
out = if bar_index > 0
    v[d]
else
    v
plot(out)
```

---

## minute()

### Syntax

```pine
minute(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_minute).*

### Returns
Minute (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

---

## month()

### Syntax

```pine
month(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_month).*

### Returns
Month (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970. Note that this function returns the month based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00 UTC-4) this value can be lower by 1 than the month of the trading day.

---

## na()

Tests if x is na.

### Syntax

```pine
na(x) → series bool
```

### Arguments

- `x` (*series any*) — Value to be tested.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_na).*

### Returns
Returns true if x is na, false otherwise.

### Code Example
```pine
//@version=6
indicator("na")
// Use the `na()` function to test for `na`.
plot(na(close[1]) ? close : close[1])
// ALTERNATIVE
// `nz()` also tests `close[1]` for `na`. It returns `close[1]` if it is not `na`, and `close` if it is.
plot(nz(close[1], close))
```

---

## nz()

Replaces NaN values with zeros (or given value) in a series.

### Syntax

```pine
nz(source, replacement) → series type
nz(source) → series type
```

### Arguments

- `source` (*series int|float|bool|color*) — Series of values to process.
- `replacement` (*series int|float|bool|color*) — Value that will replace all ‘na’ values in the `source` series.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_nz).*

### Returns
The value of source if it is not na. If the value of source is na, returns zero, or the replacement argument when one is used.

### Code Example
```pine
//@version=6
indicator("nz", overlay=true)
plot(nz(ta.sma(close, 100)))
```

---

## plot()

Plots a series of data on the chart.

### Syntax

```pine
plot(series, title, color, linewidth, style, trackprice, histbase, offset, join, editable, show_last, display, format, precision, force_overlay, linestyle) → plot
```

### Arguments

- `series` (*series int|float*) — Series of data to be plotted. Required argument.
- `title` (*const string*) — Title of the plot.
- `color` (*series color*, optional, default `color.black`) — Color of the plot. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `linewidth` (*input int*, optional, default `1`) — Width of the plotted line. Default value is 1. Not applicable to every style.
- `style` (*input plot_style*, optional, default `plot.style_line`) — Type of plot. Possible values are: [plot.style_line](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_line), [plot.style_stepline](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_stepline), [plot.style_stepline_diamond](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_stepline_diamond), [plot.style_histogram](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_histogram), [plot.style_cross](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_cross), [plot.style_area](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_area), [plot.style_columns](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_columns), [plot.style_circles](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_circles), [plot.style_linebr](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_linebr), [plot.style_areabr](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_areabr), [plot.style_steplinebr](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_steplinebr). Default value is [plot.style_line](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_line).
- `trackprice` (*input bool*, optional, default `false`) — If true then a horizontal price line will be shown at the level of the last indicator value. Default is false.
- `histbase` (*input int|float*, optional, default `0.0`) — The price value used as the reference level when rendering plot with [plot.style_histogram](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_histogram), [plot.style_columns](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_columns) or [plot.style_area](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_area) style. Default is 0.0.
- `offset` (*series int*, optional, default `0`) — Shifts the plot to the left or to the right on the given number of bars. Default is 0.
- `join` (*input bool*, optional, default `false`) — If true then plot points will be joined with line, applicable only to [plot.style_cross](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_cross) and [plot.style_circles](https://www.tradingview.com/pine-script-reference/v6/#var_plot.style_circles) styles. Default is false.
- `editable` (*const bool*, optional, default `true`) — If true then plot style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of bars (from the last bar back to the past) to plot on chart.
- `display` (*input plot_display*, optional, default `display.all`) — Controls where the plot’s information is displayed. Display options support addition and subtraction, meaning that using `display.all - display.status_line` will display the plot’s information everywhere except in the script’s status line. `display.price_scale + display.status_line` will display the plot only in the price scale and status line. When `display` arguments such as `display.price_scale` have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.pane](https://www.tradingview.com/pine-script-reference/v6/#var_display.pane), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.price_scale](https://www.tradingview.com/pine-script-reference/v6/#var_display.price_scale), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_plot).*

### Returns
A plot object, that can be used in fill

### Code Example
```pine
//@version=6
indicator("plot")
plot(high+low, title='Title', color=color.new(#00ffaa, 70), linewidth=2, style=plot.style_area, offset=15, trackprice=true)

// You may fill the background between any two plots with a fill() function:
p1 = plot(open)
p2 = plot(close)
fill(p1, p2, color=color.new(color.green, 90))
```

---

## plotarrow()

Plots up and down arrows on the chart. Up arrow is drawn at every indicator positive value, down arrow is drawn at every negative value. If indicator returns na then no arrow is drawn. Arrows has different height, the more absolute indicator value the longer arrow is drawn.

### Syntax

```pine
plotarrow(series, title, colorup, colordown, offset, minheight, maxheight, editable, show_last, display, format, precision, force_overlay) → void
```

### Arguments

- `series` (*series int|float*) — Series of data to be plotted as arrows. Required argument.
- `title` (*const string*) — Title of the plot.
- `colorup` (*series color*, optional, default `color.black`) — Color of the up arrows.
- `colordown` (*series color*, optional, default `color.black`) — Color of the down arrows. Optional argument.
- `offset` (*series int*, optional, default `0`) — Shifts arrows to the left or to the right on the given number of bars. Default is 0.
- `minheight` (*input int*, optional, default `5`) — Minimal possible arrow height in pixels. Default is 5.
- `maxheight` (*input int*, optional, default `100`) — Maximum possible arrow height in pixels. Default is 100.
- `editable` (*const bool*, optional, default `true`) — If true then plotarrow style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of arrows (from the last bar back to the past) to plot on chart.
- `display` (*input plot_display*, optional, default `display.all`) — Controls where the plot’s information is displayed. Display options support addition and subtraction, meaning that using `display.all - display.status_line` will display the plot’s information everywhere except in the script’s status line. `display.price_scale + display.status_line` will display the plot only in the price scale and status line. When `display` arguments such as `display.price_scale` have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.pane](https://www.tradingview.com/pine-script-reference/v6/#var_display.pane), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.price_scale](https://www.tradingview.com/pine-script-reference/v6/#var_display.price_scale), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_plotarrow).*

### Remarks
Use plotarrow function in conjunction with 'overlay=true' indicator parameter!

### Code Example
```pine
//@version=6
indicator("plotarrow example", overlay=true)
codiff = close - open
plotarrow(codiff, colorup=color.new(color.teal,40), colordown=color.new(color.orange, 40))
```

---

## plotbar()

Plots ohlc bars on the chart.

### Syntax

```pine
plotbar(open, high, low, close, title, color, editable, show_last, display, force_overlay) → void
```

### Arguments

- `open` (*series int|float*) — Open series of data to be used as open values of bars. Required argument.
- `high` (*series int|float*) — High series of data to be used as high values of bars. Required argument.
- `low` (*series int|float*) — Low series of data to be used as low values of bars. Required argument.
- `close` (*series int|float*) — Close series of data to be used as close values of bars. Required argument.
- `title` (*const string*, optional) — Title of the plotbar. Optional argument.
- `color` (*series color*, optional, default `color.blue`) — Color of the ohlc bars. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `editable` (*const bool*, optional, default `true`) — If true then plotbar style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of bars (from the last bar back to the past) to plot on chart.
- `display` (*input plot_display*, optional, default `display.all`) — Controls where the plot’s information is displayed. Display options support addition and subtraction, meaning that using `display.all - display.status_line` will display the plot’s information everywhere except in the script’s status line. `display.price_scale + display.status_line` will display the plot only in the price scale and status line. When `display` arguments such as `display.price_scale` have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.pane](https://www.tradingview.com/pine-script-reference/v6/#var_display.pane), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.price_scale](https://www.tradingview.com/pine-script-reference/v6/#var_display.price_scale), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_plotbar).*

### Remarks
Even if one value of open, high, low or close equal NaN then bar no draw. The maximal value of open, high, low or close will be set as 'high', and the minimal value will be set as 'low'.

### Code Example
```pine
//@version=6
indicator("plotbar example", overlay=true)
plotbar(open, high, low, close, title='Title', color = open < close ? color.green : color.red)
```

---

## plotcandle()

Plots candles on the chart.

### Syntax

```pine
plotcandle(open, high, low, close, title, color, wickcolor, editable, show_last, bordercolor, display) → void
```

### Arguments

- `open` (*series int|float*) — Open series of data to be used as open values of candles. Required argument.
- `high` (*series int|float*) — High series of data to be used as high values of candles. Required argument.
- `low` (*series int|float*) — Low series of data to be used as low values of candles. Required argument.
- `close` (*series int|float*) — Close series of data to be used as close values of candles. Required argument.
- `title` (*const string*, optional) — Title of the plotcandles. Optional argument.
- `color` (*series color*, optional, default `color.blue`) — Color of the candles. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `wickcolor` (*series color*, optional, default `color.silver`) — The color of the wick of candles. An optional argument.
- `editable` (*const bool*, optional, default `true`) — If true then plotcandle style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of candles (from the last bar back to the past) to plot on chart.
- `bordercolor` (*series color*, optional, default `color.black`) — The border color of candles. An optional argument.
- `display` (*input plot_display*, optional, default `display.all`) — Controls where the plot’s information is displayed. Display options support addition and subtraction, meaning that using `display.all - display.status_line` will display the plot’s information everywhere except in the script’s status line. `display.price_scale + display.status_line` will display the plot only in the price scale and status line. When `display` arguments such as `display.price_scale` have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.pane](https://www.tradingview.com/pine-script-reference/v6/#var_display.pane), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.price_scale](https://www.tradingview.com/pine-script-reference/v6/#var_display.price_scale), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_plotcandle).*

### Remarks
Even if one value of open, high, low or close equal NaN then bar no draw. The maximal value of open, high, low or close will be set as 'high', and the minimal value will be set as 'low'.

### Code Example
```pine
//@version=6
indicator("plotcandle example", overlay=true)
plotcandle(open, high, low, close, title='Title', color = open < close ? color.green : color.red, wickcolor=color.black)
```

---

## plotchar()

Plots visual shapes using any given one Unicode character on the chart.

### Syntax

```pine
plotchar(series, title, char, location, color, offset, text, textcolor, editable, size, show_last, display, format, precision, force_overlay) → void
```

### Arguments

- `series` (*series bool*) — Series of data to be plotted as shapes. Series is treated as a series of boolean values for all location values except [location.absolute](https://www.tradingview.com/pine-script-reference/v6/#var_location.absolute). Required argument.
- `title` (*const string*) — Title of the plot.
- `char` (*input string*) — Character to use as a visual shape.
- `location` (*input string*, optional, default `location.abovebar`) — Location of shapes on the chart. Possible values are: [location.abovebar](https://www.tradingview.com/pine-script-reference/v6/#var_location.abovebar), [location.belowbar](https://www.tradingview.com/pine-script-reference/v6/#var_location.belowbar), [location.top](https://www.tradingview.com/pine-script-reference/v6/#var_location.top), [location.bottom](https://www.tradingview.com/pine-script-reference/v6/#var_location.bottom), [location.absolute](https://www.tradingview.com/pine-script-reference/v6/#var_location.absolute). Default value is [location.abovebar](https://www.tradingview.com/pine-script-reference/v6/#var_location.abovebar).
- `color` (*series color*, optional, default `color.black`) — Color of the shapes. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `offset` (*series int*, optional, default `0`) — Shifts shapes to the left or to the right on the given number of bars. Default is 0.
- `text` (*const string*) — Text to display with the shape. You can use multiline text, to separate lines use '\n' escape sequence. Example: 'line one\nline two'.
- `textcolor` (*series color*, optional, default `color.black`) — Color of the text. You can use constants like 'textcolor=color.red' or 'textcolor=#ff001a' as well as complex expressions like 'textcolor = close >= open ? color.green : color.red'. Optional argument.
- `editable` (*const bool*, optional, default `true`) — If true then plotchar style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of chars (from the last bar back to the past) to plot on chart.
- `size` (*const string*, optional, default `size.auto`) — Size of characters on the chart. Possible values are: [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v6/#var_size.tiny), [size.small](https://www.tradingview.com/pine-script-reference/v6/#var_size.small), [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal), [size.large](https://www.tradingview.com/pine-script-reference/v6/#var_size.large), [size.huge](https://www.tradingview.com/pine-script-reference/v6/#var_size.huge). Default is [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto).
- `display` (*input plot_display*, optional, default `display.all`) — Controls where the plot’s information is displayed. Display options support addition and subtraction, meaning that using `display.all - display.status_line` will display the plot’s information everywhere except in the script’s status line. `display.price_scale + display.status_line` will display the plot only in the price scale and status line. When `display` arguments such as `display.price_scale` have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.pane](https://www.tradingview.com/pine-script-reference/v6/#var_display.pane), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.price_scale](https://www.tradingview.com/pine-script-reference/v6/#var_display.price_scale), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_plotchar).*

### Remarks
Use plotchar function in conjunction with 'overlay=true' indicator parameter!

### Code Example
```pine
//@version=6
indicator("plotchar example", overlay=true)
data = close >= open
plotchar(data, char='❄')
```

---

## plotshape()

Plots visual shapes on the chart.

### Syntax

```pine
plotshape(series, title, style, location, color, offset, text, textcolor, editable, size, show_last, display, format, precision, force_overlay) → void
```

### Arguments

- `series` (*series bool*) — Series of data to be plotted as shapes. Series is treated as a series of boolean values for all location values except [location.absolute](https://www.tradingview.com/pine-script-reference/v6/#var_location.absolute). Required argument.
- `title` (*const string*) — Title of the plot.
- `style` (*input string*, optional, default `shape.xcross`) — Type of plot. Possible values are: [shape.xcross](https://www.tradingview.com/pine-script-reference/v6/#var_shape.xcross), [shape.cross](https://www.tradingview.com/pine-script-reference/v6/#var_shape.cross), [shape.triangleup](https://www.tradingview.com/pine-script-reference/v6/#var_shape.triangleup), [shape.triangledown](https://www.tradingview.com/pine-script-reference/v6/#var_shape.triangledown), [shape.flag](https://www.tradingview.com/pine-script-reference/v6/#var_shape.flag), [shape.circle](https://www.tradingview.com/pine-script-reference/v6/#var_shape.circle), [shape.arrowup](https://www.tradingview.com/pine-script-reference/v6/#var_shape.arrowup), [shape.arrowdown](https://www.tradingview.com/pine-script-reference/v6/#var_shape.arrowdown), [shape.labelup](https://www.tradingview.com/pine-script-reference/v6/#var_shape.labelup), [shape.labeldown](https://www.tradingview.com/pine-script-reference/v6/#var_shape.labeldown), [shape.square](https://www.tradingview.com/pine-script-reference/v6/#var_shape.square), [shape.diamond](https://www.tradingview.com/pine-script-reference/v6/#var_shape.diamond). Default value is [shape.xcross](https://www.tradingview.com/pine-script-reference/v6/#var_shape.xcross).
- `location` (*input string*, default `location.abovebar`) — Location of shapes on the chart. Possible values are: [location.abovebar](https://www.tradingview.com/pine-script-reference/v6/#var_location.abovebar), [location.belowbar](https://www.tradingview.com/pine-script-reference/v6/#var_location.belowbar), [location.top](https://www.tradingview.com/pine-script-reference/v6/#var_location.top), [location.bottom](https://www.tradingview.com/pine-script-reference/v6/#var_location.bottom), [location.absolute](https://www.tradingview.com/pine-script-reference/v6/#var_location.absolute). Default value is [location.abovebar](https://www.tradingview.com/pine-script-reference/v6/#var_location.abovebar).
- `color` (*series color*, optional, default `color.black`) — Color of the shapes. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `offset` (*series int*, optional, default `0`) — Shifts shapes to the left or to the right on the given number of bars. Default is 0.
- `text` (*const string*) — Text to display with the shape. You can use multiline text, to separate lines use '\n' escape sequence. Example: 'line one\nline two'.
- `textcolor` (*series color*, optional, default `color.black`) — Color of the text. You can use constants like 'textcolor=color.red' or 'textcolor=#ff001a' as well as complex expressions like 'textcolor = close >= open ? color.green : color.red'. Optional argument.
- `editable` (*const bool*, optional, default `true`) — If true then plotshape style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — If set, defines the number of shapes (from the last bar back to the past) to plot on chart.
- `size` (*const string*, optional, default `size.auto`) — Size of shapes on the chart. Possible values are: [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v6/#var_size.tiny), [size.small](https://www.tradingview.com/pine-script-reference/v6/#var_size.small), [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal), [size.large](https://www.tradingview.com/pine-script-reference/v6/#var_size.large), [size.huge](https://www.tradingview.com/pine-script-reference/v6/#var_size.huge). Default is [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto).
- `display` (*input plot_display*, optional, default `display.all`) — Controls where the plot’s information is displayed. Display options support addition and subtraction, meaning that using `display.all - display.status_line` will display the plot’s information everywhere except in the script’s status line. `display.price_scale + display.status_line` will display the plot only in the price scale and status line. When `display` arguments such as `display.price_scale` have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: [display.none](https://www.tradingview.com/pine-script-reference/v6/#var_display.none), [display.pane](https://www.tradingview.com/pine-script-reference/v6/#var_display.pane), [display.data_window](https://www.tradingview.com/pine-script-reference/v6/#var_display.data_window), [display.price_scale](https://www.tradingview.com/pine-script-reference/v6/#var_display.price_scale), [display.status_line](https://www.tradingview.com/pine-script-reference/v6/#var_display.status_line), [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all). Optional. The default is [display.all](https://www.tradingview.com/pine-script-reference/v6/#var_display.all).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_plotshape).*

### Remarks
Use plotshape function in conjunction with 'overlay=true' indicator parameter!

### Code Example
```pine
//@version=6
indicator("plotshape example 1", overlay=true)
data = close >= open
plotshape(data, style=shape.xcross)
```

---

## polyline.delete()

Deletes the specified polyline object. It has no effect if the id doesn't exist.

---

### Syntax

```pine
polyline.delete(id) → void
```

### Arguments

- `id` (*series polyline*) — The polyline ID to delete.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_polyline.delete).*

## polyline.new()

Creates a new polyline instance and displays it on the chart, sequentially connecting all of the points in the points array with line segments. The segments in the drawing can be straight or curved depending on the curved parameter.

### Syntax

```pine
polyline.new(points, curved, closed, xloc, line_color, fill_color, line_style, line_width, force_overlay) → series polyline
```

### Arguments

- `points` (*chart.point[]*) — An array of [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) objects for the drawing to sequentially connect.
- `curved` (*series bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the drawing will connect all points from the `points` array using curved line segments. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `closed` (*series bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the drawing will also connect the first point to the last point from the `points` array, resulting in a closed polyline. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `xloc` (*series string*, optional, default `xloc.bar_index`) — Determines the field of the [chart.point](https://www.tradingview.com/pine-script-reference/v6/#op_chart.point) objects in the `points` array that the polyline will use for its x-coordinates. If [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index), the polyline will use the `index` field from each point. If [xloc.bar_time](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_time), it will use the `time` field. Optional. The default is [xloc.bar_index](https://www.tradingview.com/pine-script-reference/v6/#var_xloc.bar_index).
- `line_color` (*series color*, optional, default `color.blue`) — The color of the line segments. Optional. The default is [color.blue](https://www.tradingview.com/pine-script-reference/v6/#var_color.blue).
- `fill_color` (*series color*, optional, default `na`) — The fill color of the polyline. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `line_style` (*series string*, optional, default `line.style_solid`) — The style of the polyline. Possible values: [line.style_solid](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_solid), [line.style_dotted](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_dotted), [line.style_dashed](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_dashed), [line.style_arrow_left](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_arrow_left), [line.style_arrow_right](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_arrow_right), [line.style_arrow_both](https://www.tradingview.com/pine-script-reference/v6/#var_line.style_arrow_both). Optional. The default is {mdInternalRef1}.
- `line_width` (*series int*, optional, default `1`) — The width of the line segments, expressed in pixels. Optional. The default is 1.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_polyline.new).*

### Returns
The ID of a new polyline object that a script can use in other polyline.*() functions.

### Code Example
```pine
//@version=6
indicator("Polylines example", overlay = true)

//@variable If `true`, connects all points in the polyline with curved line segments. 
bool curvedInput = input.bool(false, "Curve Polyline")
//@variable If `true`, connects the first point in the polyline to the last point.
bool closedInput = input.bool(true, "Close Polyline")
//@variable The color of the space filled by the polyline.
color fillcolor = input.color(color.new(color.blue, 90), "Fill Color")

// Time and price inputs for the polyline's points. 
p1x = input.time(0,  "p1", confirm = true, inline = "p1")
p1y = input.price(0, "  ", confirm = true, inline = "p1")
p2x = input.time(0,  "p2", confirm = true, inline = "p2")
p2y = input.price(0, "  ", confirm = true, inline = "p2")
p3x = input.time(0,  "p3", confirm = true, inline = "p3")
p3y = input.price(0, "  ", confirm = true, inline = "p3")
p4x = input.time(0,  "p4", confirm = true, inline = "p4")
p4y = input.price(0, "  ", confirm = true, inline = "p4")
p5x = input.time(0,  "p5", confirm = true, inline = "p5")
p5y = input.price(0, "  ", confirm = true, inline = "p5")

if barstate.islastconfirmedhistory
    //@variable An array of `chart.point` objects for the new polyline.
    var points = array.new<chart.point>()
    // Push new `chart.point` instances into the `points` array.
    points.push(chart.point.from_time(p1x, p1y))
    points.push(chart.point.from_time(p2x, p2y))
    points.push(chart.point.from_time(p3x, p3y))
    points.push(chart.point.from_time(p4x, p4y))
    points.push(chart.point.from_time(p5x, p5y))
    // Add labels for each `chart.point` in `points`.
    l1p1 = label.new(points.get(0), text = "p1", xloc = xloc.bar_time, color = na)
    l1p2 = label.new(points.get(1), text = "p2", xloc = xloc.bar_time, color = na)
    l2p1 = label.new(points.get(2), text = "p3", xloc = xloc.bar_time, color = na)
    l2p2 = label.new(points.get(3), text = "p4", xloc = xloc.bar_time, color = na)
    // Create a new polyline that connects each `chart.point` in the `points` array, starting from the first.
    polyline.new(points, curved = curvedInput, closed = closedInput, fill_color = fillcolor, xloc = xloc.bar_time)
```

---

## request.currency_rate()

Provides a daily rate that can be used to convert a value expressed in the from currency to another in the to currency.

### Syntax

```pine
request.currency_rate(from, to, ignore_invalid_currency) → series float
```

### Arguments

- `from` (*simple string*) — The currency in which the value to be converted is expressed. Possible values: a three-letter string with the [currency code in the ISO 4217 format](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) (e.g. "USD"), or one of the built-in variables that return currency codes, like [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency) or [currency.USD](https://www.tradingview.com/pine-script-reference/v6/#var_currency.USD).
- `to` (*simple string*) — The currency in which the value is to be converted. Possible values: a three-letter string with the [currency code in the ISO 4217 format](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) (e.g. "USD"), or one of the built-in variables that return currency codes, like [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency) or [currency.USD](https://www.tradingview.com/pine-script-reference/v6/#var_currency.USD).
- `ignore_invalid_currency` (*simple bool*, optional, default `false`) — Determines the behavior of the function if a conversion rate between the two currencies cannot be calculated: if [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), the script will halt and return a runtime error; if [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the function will return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) and execution will continue. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.currency_rate).*

### Remarks
If from and to arguments are equal, function returns 1. Please note that using this variable/function can cause indicator repainting.

### Code Example
```pine
//@version=6
indicator("Close in British Pounds")
rate = request.currency_rate(syminfo.currency, "GBP")
plot(close * rate)
```

---

## request.dividends()

Requests dividends data for the specified symbol.

### Syntax

```pine
request.dividends(ticker, field, gaps, lookahead, ignore_invalid_symbol, currency) → series float
```

### Arguments

- `ticker` (*simple string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL". Using [syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker) will cause an error. Use [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid) instead.
- `field` (*simple string*, optional, default `dividends.gross`) — Input string. Possible values include: [dividends.net](https://www.tradingview.com/pine-script-reference/v6/#var_dividends.net), [dividends.gross](https://www.tradingview.com/pine-script-reference/v6/#var_dividends.gross). Default value is [dividends.gross](https://www.tradingview.com/pine-script-reference/v6/#var_dividends.gross).
- `gaps` (*simple barmerge_gaps*, default `barmerge.gaps_off`) — Merge strategy for the requested data (requested data automatically merges with the main series OHLC data). Possible values: [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on), [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off). [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on) - requested data is merged with possible gaps ([na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values). [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off) - requested data is merged continuously without gaps, all the gaps are filled with the previous nearest existing values. Default value is [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off).
- `lookahead` (*simple barmerge_lookahead*, optional, default `barmerge.lookahead_off`) — Merge strategy for the requested data position. Possible values: [barmerge.lookahead_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_on), [barmerge.lookahead_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_off). Default value is [barmerge.lookahead_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_off) starting from version 3. Note that behavour is the same on real-time, and differs only on history.
- `ignore_invalid_symbol` (*input bool*, optional, default `false`) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.
- `currency` (*simple string*, optional, default `syminfo.currency`) — Currency into which the symbol’s currency-related dividends values (e.g. [dividends.gross](https://www.tradingview.com/pine-script-reference/v6/#var_dividends.gross)) are to be converted. The conversion rates used are based on the FX_IDC pairs' daily rates of the previous day (relative to the bar where the calculation is done). Optional. The default is [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency). Possible values: a three-letter string with the [currency code in the ISO 4217 format](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) (e.g. "USD") or one of the constants in the currency.* namespace, e.g. [currency.USD](https://www.tradingview.com/pine-script-reference/v6/#var_currency.USD).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.dividends).*

### Returns
Requested series, or n/a if there is no dividends data for the specified symbol.

### Code Example
```pine
//@version=6
indicator("request.dividends")
s1 = request.dividends("NASDAQ:BELFA")
plot(s1)
s2 = request.dividends("NASDAQ:BELFA", dividends.net, gaps=barmerge.gaps_on, lookahead=barmerge.lookahead_on)
plot(s2)
```

---

## request.earnings()

Requests earnings data for the specified symbol.

### Syntax

```pine
request.earnings(ticker, field, gaps, lookahead, ignore_invalid_symbol, currency) → series float
```

### Arguments

- `ticker` (*simple string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL". Using [syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker) will cause an error. Use [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid) instead.
- `field` (*simple string*, default `earnings.actual`) — Input string. Possible values include: [earnings.actual](https://www.tradingview.com/pine-script-reference/v6/#var_earnings.actual), [earnings.estimate](https://www.tradingview.com/pine-script-reference/v6/#var_earnings.estimate), [earnings.standardized](https://www.tradingview.com/pine-script-reference/v6/#var_earnings.standardized). Default value is [earnings.actual](https://www.tradingview.com/pine-script-reference/v6/#var_earnings.actual).
- `gaps` (*simple barmerge_gaps*, default `barmerge.gaps_off`) — Merge strategy for the requested data (requested data automatically merges with the main series OHLC data). Possible values: [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on), [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off). [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on) - requested data is merged with possible gaps ([na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values). [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off) - requested data is merged continuously without gaps, all the gaps are filled with the previous nearest existing values. Default value is [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off).
- `lookahead` (*simple barmerge_lookahead*, default `barmerge.lookahead_off`) — Merge strategy for the requested data position. Possible values: [barmerge.lookahead_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_on), [barmerge.lookahead_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_off). Default value is [barmerge.lookahead_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_off) starting from version 3. Note that behavour is the same on real-time, and differs only on history.
- `ignore_invalid_symbol` (*input bool*, optional, default `false`) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.
- `currency` (*simple string*, optional, default `syminfo.currency`) — Currency into which the symbol’s currency-related earnings values (e.g. [earnings.actual](https://www.tradingview.com/pine-script-reference/v6/#var_earnings.actual)) are to be converted. The conversion rates used are based on the FX_IDC pairs' daily rates of the previous day (relative to the bar where the calculation is done). Optional. The default is [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency). Possible values: a three-letter string with the [currency code in the ISO 4217 format](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) (e.g. "USD") or one of the constants in the currency.* namespace, e.g. [currency.USD](https://www.tradingview.com/pine-script-reference/v6/#var_currency.USD).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.earnings).*

### Returns
Requested series, or n/a if there is no earnings data for the specified symbol.

### Code Example
```pine
//@version=6
indicator("request.earnings")
s1 = request.earnings("NASDAQ:BELFA")
plot(s1)
s2 = request.earnings("NASDAQ:BELFA", earnings.actual, gaps=barmerge.gaps_on, lookahead=barmerge.lookahead_on)
plot(s2)
```

---

## request.economic()

Requests economic data for a symbol. Economic data includes information such as the state of a country's economy (GDP, inflation rate, etc.) or of a particular industry (steel production, ICU beds, etc.).

### Syntax

```pine
request.economic(country_code, field, gaps, ignore_invalid_symbol) → series float
```

### Arguments

- `country_code` (*simple string*) — The code of the country (e.g. "US") or the region (e.g. "EU") for which the economic data is requested. The [Help Center article](https://www.tradingview.com/chart/?solution=43000665359) lists the countries and their codes. The countries for which information is available vary with metrics. The [Help Center article for each metric](https://www.tradingview.com/support/folders/43000581956-list-of-available-economic-indicators/) lists the countries for which the metric is available.
- `field` (*simple string*) — The code of the requested economic metric (e.g., "GDP"). The [Help Center article](https://www.tradingview.com/chart/?solution=43000665359) lists the metrics and their codes.
- `gaps` (*simple barmerge_gaps*, optional, default `barmerge.gaps_off`) — Specifies how the returned values are merged on chart bars. Possible values: [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off), [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on). With [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on), a value only appears on the current chart bar when it first becomes available from the function’s context, otherwise [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) is returned (thus a "gap" occurs). With [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off), what would otherwise be gaps are filled with the latest known value returned, avoiding [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values. Optional. The default is [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off).
- `ignore_invalid_symbol` (*input bool*, optional, default `false`) — Determines the behavior of the function if the specified symbol is not found: if [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), the script will halt and return a runtime error; if [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the function will return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) and execution will continue. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.economic).*

### Returns
Requested series.

### Remarks
Economic data can also be accessed from charts, just like a regular symbol. Use "ECONOMIC" as the exchange name and {country_code}{field} as the ticker. The name of US GDP data is thus "ECONOMIC:USGDP".

### Code Example
```pine
//@version=6
indicator("US GDP")
e = request.economic("US", "GDP")
plot(e)
```

---

## request.financial()

Requests financial series for symbol.

### Syntax

```pine
request.financial(symbol, financial_id, period, gaps, ignore_invalid_symbol, currency) → series float
```

### Arguments

- `symbol` (*simple string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL".
- `financial_id` (*simple string*) — Financial identifier. You can find the list of available ids via our [Help Center](https://www.tradingview.com/?solution=43000564727).
- `period` (*simple string*) — Reporting period. Possible values are "TTM", "FY", "FQ".
- `gaps` (*simple barmerge_gaps*, default `barmerge.gaps_off`) — Merge strategy for the requested data (requested data automatically merges with the main series: OHLC data). Possible values include: [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on), [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off). [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on) - requested data is merged with possible gaps ([na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values). [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off) - requested data is merged continuously without gaps, all the gaps are filled with the previous, nearest existing values. Default value is [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off).
- `ignore_invalid_symbol` (*input bool*, optional, default `false`) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.
- `currency` (*simple string*, optional, default `syminfo.currency`) — Currency into which the symbol’s financial metrics (e.g. Net Income) are to be converted. The conversion rates used are based on the FX_IDC pairs' daily rates of the previous day (relative to the bar where the calculation is done). Optional. The default is [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency). Possible values: a three-letter string with the [currency code in the ISO 4217 format](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) (e.g. "USD") or one of the constants in the currency.* namespace, e.g. [currency.USD](https://www.tradingview.com/pine-script-reference/v6/#var_currency.USD).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.financial).*

### Returns
Requested series.

### Code Example
```pine
//@version=6
indicator("request.financial")
f = request.financial("NASDAQ:MSFT", "ACCOUNTS_PAYABLE", "FY")
plot(f)
```

---

## request.quandl()

Note: This function has been deprecated due to the API change from NASDAQ Data Link. Requests for "QUANDL" symbols are no longer valid and requests for them return a runtime error.

### Syntax

```pine
request.quandl(ticker, gaps, index, ignore_invalid_symbol) → series float
```

### Arguments

- `ticker` (*simple string*) — Symbol. Note that the name of a time series and Quandl data feed should be divided by a forward slash. For example: "CFTC/SB_FO_ALL".
- `gaps` (*simple barmerge_gaps*, default `barmerge.gaps_off`) — Merge strategy for the requested data (requested data automatically merges with the main series: OHLC data). Possible values include: [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on), [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off). [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on) - requested data is merged with possible gaps ([na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values). [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off) - requested data is merged continuously without gaps, all the gaps are filled with the previous, nearest existing values. Default value is [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off).
- `index` (*simple int*) — A Quandl time-series column index.
- `ignore_invalid_symbol` (*input bool*, optional, default `false`) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.quandl).*

### Returns
Requested series.

### Code Example
```pine
//@version=6
indicator("request.quandl")
f = request.quandl("CFTC/SB_FO_ALL", barmerge.gaps_off, 0)
plot(f)
```

---

## request.security()

Requests the result of an expression from a specified context (symbol and timeframe).

### Syntax

```pine
request.security(symbol, timeframe, expression, gaps, lookahead, ignore_invalid_symbol, currency, calc_bars_count) → series <type>
```

### Arguments

- `symbol` (*simple string*) — Symbol to request the data from. Use [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid) to request data from the chart’s symbol. To request data with additional parameters (extended sessions, dividend adjustments, or a non-standard chart type like Heikin Ashi or Renko), a custom ticker identifier must first be created using functions in the `ticker.*` namespace.
- `timeframe` (*simple string*) — Timeframe of the requested data. To use the chart’s timeframe, use an empty string or the [timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period) variable. Valid timeframe strings are documented in the User Manual’s [Timeframes](https://www.tradingview.com/pine-script-docs/en/v5/concepts/Timeframes.html#timeframe-string-specifications) page.
- `expression` (*<variable>|<object>|<function>|array|matrix|int|float|bool|string|color|tuple[...]*) — An expression to be calculated and returned from the [request.security](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security) call’s context. It can be a built-in variable like [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), an expression such as `ta.sma(close, 100)`, a non-mutable user-defined variable previously calculated in the script, a function call that does not use PineScript™ drawings, an array, a matrix, or a tuple. Mutable variables are not allowed, unless they are enclosed in the body of a function used in the expression.
- `gaps` (*simple barmerge_gaps*, optional, default `barmerge.gaps_off`) — Specifies how the returned values are merged on chart bars. Possible values: [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on), [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off). With [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on) a value only appears on the current chart bar when it first becomes available from the function’s context, otherwise [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) is returned (thus a "gap" occurs). With [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off) what would otherwise be gaps are filled with the latest known value returned, avoiding [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values. Optional. The default is [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off).
- `lookahead` (*simple barmerge_lookahead*, optional, default `barmerge.lookahead_off`) — On historical bars only, returns data from the timeframe before it elapses. Possible values: [barmerge.lookahead_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_on), [barmerge.lookahead_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_off). Has no effect on realtime values. Optional. The default is [barmerge.lookahead_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_off) starting from Pine Script™ v3. The default is [barmerge.lookahead_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_on) in v1 and v2. WARNING: Using [barmerge.lookahead_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_on) at timeframes higher than the chart’s without offsetting the `expression` argument like in `close[1]` will introduce future leak in scripts, as the function will then return the `close` price before it is actually known in the current context. As is explained in the User Manual’s page on [Repainting](https://www.tradingview.com/pine-script-docs/en/v5/concepts/Repainting.html#future-leak-with-request-security) this will produce misleading results.
- `ignore_invalid_symbol` (*input bool*, optional, default `false`) — Determines the behavior of the function if the specified symbol is not found: if [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), the script will halt and throw a runtime error; if [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the function will return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) and execution will continue. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `currency` (*simple string*, optional, default `syminfo.currency`) — Currency into which values expressed in currency units ([open](https://www.tradingview.com/pine-script-reference/v6/#var_open), [high](https://www.tradingview.com/pine-script-reference/v6/#var_high), [low](https://www.tradingview.com/pine-script-reference/v6/#var_low), [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), etc.) or expressions using such values are to be converted. The conversion rates used are based on the FX_IDC pairs' daily rates of the previous day (relative to the bar where the calculation is done). Possible values: a three-letter string with the [currency code in the ISO 4217 format](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) (e.g. "USD") or one of the constants in the currency.* namespace, e.g. [currency.USD](https://www.tradingview.com/pine-script-reference/v6/#var_currency.USD). Note that literal values such as `200` are not converted. Optional. The default is [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security).*

### Returns
A result determined by expression.

### Remarks
Scripts using this function might calculate differently on historical and realtime bars, leading to repainting. A single script can contain no more than 40 unique request.*() function calls. A call is unique only if it does not call the same function with the same arguments. When using two calls to a request.*() function to evaluate the same expression from the same context with different calc_bars_count values, the second call requests the same number of historical bars as the first. For example, if a script calls request.security("AAPL", "", close, calc_bars_count = 3) after it calls request.security("AAPL", "", close, calc_bars_count = 5), the second call also uses five bars of historical data, not three. The symbol of a request.() call can be inherited if it is not specified precisely, i.e., if the symbol argument is an empty string or syminfo.tickerid. Similarly, the timeframe of a request.() call can be inherited if the timeframe argument is an empty string or timeframe.period. These values are normally taken from the chart on which the script is running. However, if request.*() function A is called from within the expression of request.*() function B, then function A can inherit the values from function B. See here for more information.

### Code Example
```pine
//@version=6
indicator("Simple `request.security()` calls")
// Returns 1D close of the current symbol.
dailyClose = request.security(syminfo.tickerid, "1D", close)
plot(dailyClose)

// Returns the close of "AAPL" from the same timeframe as currently open on the chart.
aaplClose = request.security("AAPL", timeframe.period, close)
plot(aaplClose)

//@version=6
indicator("Advanced `request.security()` calls")
// This calculates a 10-period moving average on the active chart.
sma = ta.sma(close, 10)
// This sends the `sma` calculation for execution in the context of the "AAPL" symbol at a "240" (4 hours) timeframe.
aaplSma = request.security("AAPL", "240", sma)
plot(aaplSma)

// To avoid differences on historical and realtime bars, you can use this technique, which only returns a value from the higher timeframe on the bar after it completes:
indexHighTF = barstate.isrealtime ? 1 : 0
indexCurrTF = barstate.isrealtime ? 0 : 1
nonRepaintingClose = request.security(syminfo.tickerid, "1D", close[indexHighTF])[indexCurrTF]
plot(nonRepaintingClose, "Non-repainting close")

// Returns the 1H close of "AAPL", extended session included. The value is dividend-adjusted.
extendedTicker = ticker.modify("NASDAQ:AAPL", session = session.extended, adjustment = adjustment.dividends)
aaplExtAdj = request.security(extendedTicker, "60", close)
plot(aaplExtAdj)

// Returns the result of a user-defined function.
// The `max` variable is mutable, but we can pass it to `request.security()` because it is wrapped in a function.
allTimeHigh(source) =>
    var max = source
    max := math.max(max, source)
allTimeHigh1D = request.security(syminfo.tickerid, "1D", allTimeHigh(high))

// By using a tuple `expression`, we obtain several values with only one `request.security()` call.
[open1D, high1D, low1D, close1D, ema1D] = request.security(syminfo.tickerid, "1D", [open, high, low, close, ta.ema(close, 10)])
plotcandle(open1D, high1D, low1D, close1D)
plot(ema1D)

// Returns an array containing the OHLC values of the chart's symbol from the 1D timeframe.
ohlcArray = request.security(syminfo.tickerid, "1D", array.from(open, high, low, close))
plotcandle(array.get(ohlcArray, 0), array.get(ohlcArray, 1), array.get(ohlcArray, 2), array.get(ohlcArray, 3))
```

---

## request.security_lower_tf()

Requests the results of an expression from a specified symbol on a timeframe lower than or equal to the chart's timeframe. It returns an array containing one element for each lower-timeframe bar within the chart bar. On a 5-minute chart, requesting data using a timeframe argument of "1" typically returns an array with five elements representing the value of the expression on each 1-minute bar, ordered by time with the earliest value first.

### Syntax

```pine
request.security_lower_tf(symbol, timeframe, expression, ignore_invalid_symbol, currency, ignore_invalid_timeframe, calc_bars_count) → array<type>
```

### Arguments

- `symbol` (*simple string*) — Symbol to request the data from. Use [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid) to request data from the chart’s symbol. To request data with additional parameters (extended sessions, dividend adjustments, or a non-standard chart type like Heikin Ashi or Renko), a custom ticker identifier must first be created using functions in the `ticker.*` namespace.
- `timeframe` (*simple string*) — Timeframe of the requested data. To use the chart’s timeframe, use an empty string or the [timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period) variable. Valid timeframe strings are documented in the User Manual’s [Timeframes](https://www.tradingview.com/pine-script-docs/en/v5/concepts/Timeframes.html#timeframe-string-specifications) page.
- `expression` (*<variable>|<object>|<function>|array|matrix|int|float|bool|string|color|tuple[...]*) — An expression to be calculated and returned from the function call’s context. It can be a built-in variable like [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), an expression such as `ta.sma(close, 100)`, a non-mutable user-defined variable previously calculated in the script, a function call that does not use PineScript™ drawings, arrays or matrices, or a tuple. Mutable variables are not allowed, unless they are enclosed in the body of a function used in the expression.
- `ignore_invalid_symbol` (*const bool*, optional, default `false`) — Determines the behavior of the function if the specified symbol is not found: if [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), the script will halt and throw a runtime error; if [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the function will return [na](https://www.tradingview.com/pine-script-reference/v6/#var_na) and execution will continue. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `currency` (*simple string*, optional, default `syminfo.currency`) — Currency into which values expressed in currency units ([open](https://www.tradingview.com/pine-script-reference/v6/#var_open), [high](https://www.tradingview.com/pine-script-reference/v6/#var_high), [low](https://www.tradingview.com/pine-script-reference/v6/#var_low), [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), etc.) or expressions using such values are to be converted. The conversion rates used are based on the FX_IDC pairs' daily rates of the previous day (relative to the bar where the calculation is done). Possible values: a three-letter string with the [currency code in the ISO 4217 format](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) (e.g. "USD") or one of the constants in the currency.* namespace, e.g. [currency.USD](https://www.tradingview.com/pine-script-reference/v6/#var_currency.USD). Note that literal values such as `200` are not converted. Optional. The default is [syminfo.currency](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.currency).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.security_lower_tf).*

### Returns
An array of a type determined by expression, or a tuple of these.

### Remarks
Scripts using this function might calculate differently on historical and realtime bars, leading to repainting. Please note that spreads (e.g., "AAPL+MSFT*TSLA") do not always return reliable data with this function. A single script can contain no more than 40 unique request.*() function calls. A call is unique only if it does not call the same function with the same arguments. When using two calls to a request.*() function to evaluate the same expression from the same context with different calc_bars_count values, the second call requests the same number of historical bars as the first. For example, if a script calls request.security("AAPL", "", close, calc_bars_count = 3) after it calls request.security("AAPL", "", close, calc_bars_count = 5), the second call also uses five bars of historical data, not three. The symbol of a request.() call can be inherited if it is not specified precisely, i.e., if the symbol argument is an empty string or syminfo.tickerid. Similarly, the timeframe of a request.() call can be inherited if the timeframe argument is an empty string or timeframe.period. These values are normally taken from the chart that the script is running on. However, if request.*() function A is called from within the expression of request.*() function B, then function A can inherit the values from function B. See here for more information.

### Code Example
```pine
//@version=6
indicator("`request.security_lower_tf()` Example", overlay = true)

// If the current chart timeframe is set to 120 minutes, then the `arrayClose` array will contain two 'close' values from the 60 minute timeframe for each bar.
arrClose = request.security_lower_tf(syminfo.tickerid, "60", close)

if bar_index == last_bar_index - 1
    label.new(bar_index, high, str.tostring(arrClose))
```

---

## request.seed()

Requests data from a user-maintained GitHub repository and returns it as a series. An in-depth tutorial on how to add new data can be found here.

### Syntax

```pine
request.seed(source, symbol, expression, ignore_invalid_symbol, calc_bars_count) → series <type>
```

### Arguments

- `source` (*simple string*) — Name of the GitHub repository.
- `symbol` (*simple string*) — Name of the file in the GitHub repository containing the data. The ".csv" file extension must not be included.
- `expression` (*<type>*) — An expression to be calculated and returned from the requested symbol’s context. It can be a built-in variable like [close](https://www.tradingview.com/pine-script-reference/v6/#var_close), an expression such as `ta.sma(close, 100)`, a non-mutable variable previously calculated in the script, a function call that does not use Pine Script™ drawings, an array, a matrix, or a tuple. Mutable variables are not allowed, unless they are enclosed in the body of a function used in the expression.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.seed).*

### Returns
Requested series or tuple of series, which may include array/matrix IDs.

### Code Example
```pine
//@version=6
indicator("BTC Development Activity")

[devAct, devActSMA] = request.seed("seed_crypto_santiment", "BTC_DEV_ACTIVITY", [close, ta.sma(close, 10)])

plot(devAct, "BTC Development Activity")
plot(devActSMA, "BTC Development Activity SMA10", color = color.yellow)
```

---

## request.splits()

Requests splits data for the specified symbol.

### Syntax

```pine
request.splits(ticker, field, gaps, lookahead, ignore_invalid_symbol) → series float
```

### Arguments

- `ticker` (*simple string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL". Using [syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker) will cause an error. Use [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid) instead.
- `field` (*simple string*) — Input string. Possible values include: [splits.denominator](https://www.tradingview.com/pine-script-reference/v6/#var_splits.denominator), [splits.numerator](https://www.tradingview.com/pine-script-reference/v6/#var_splits.numerator).
- `gaps` (*simple barmerge_gaps*, default `barmerge.gaps_off`) — Merge strategy for the requested data (requested data automatically merges with the main series OHLC data). Possible values: [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on), [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off). [barmerge.gaps_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_on) - requested data is merged with possible gaps ([na](https://www.tradingview.com/pine-script-reference/v6/#var_na) values). [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off) - requested data is merged continuously without gaps, all the gaps are filled with the previous nearest existing values. Default value is [barmerge.gaps_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.gaps_off).
- `lookahead` (*simple barmerge_lookahead*, default `barmerge.lookahead_off`) — Merge strategy for the requested data position. Possible values: [barmerge.lookahead_on](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_on), [barmerge.lookahead_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_off). Default value is [barmerge.lookahead_off](https://www.tradingview.com/pine-script-reference/v6/#var_barmerge.lookahead_off) starting from version 3. Note that behavour is the same on real-time, and differs only on history.
- `ignore_invalid_symbol` (*input bool*, optional, default `false`) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_request.splits).*

### Returns
Requested series, or n/a if there is no splits data for the specified symbol.

### Code Example
```pine
//@version=6
indicator("request.splits")
s1 = request.splits("NASDAQ:BELFA", splits.denominator)
plot(s1)
s2 = request.splits("NASDAQ:BELFA", splits.denominator, gaps=barmerge.gaps_on, lookahead=barmerge.lookahead_on)
plot(s2)
```

---

## runtime.error()

When called, causes a runtime error with the error message specified in the message argument.

---

### Syntax

```pine
runtime.error(message) → void
```

### Arguments

- `message` (*series string*) — Error message.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_runtime.error).*

## second()

### Syntax

```pine
second(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_second).*

### Returns
Second (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

---

## str.contains()

Returns true if the source string contains the str substring, false otherwise.

### Syntax

```pine
str.contains(source, str) → bool
```

### Arguments

- `source` (*series string*) — Source string.
- `str` (*series string*) — The substring to search for.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.contains).*

### Returns
True if the str was found in the source string, false otherwise.

### Code Example
```pine
//@version=6
indicator("str.contains")
// If the current chart is a continuous futures chart, e.g “BTC1!”, then the function will return true, false otherwise.
var isFutures = str.contains(syminfo.tickerid, "!")
plot(isFutures ? 1 : 0)
```

---

## str.endswith()

Returns true if the source string ends with the substring specified in str, false otherwise.

### Syntax

```pine
str.endswith(source, str) → bool
```

### Arguments

- `source` (*series string*) — Source string.
- `str` (*series string*) — The substring to search for.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.endswith).*

### Returns
True if the source string ends with the substring specified in str, false otherwise.

---

## str.format()

Converts the formatting string and value(s) into a formatted string. The formatting string can contain literal text and one placeholder in curly braces {} for each value to be formatted. Each placeholder consists of the index of the required argument (beginning at 0) that will replace it, and an optional format specifier. The index represents the position of that argument in the str.format argument list.

### Syntax

```pine
str.format(formatString, arg0, arg1, ...) → string
```

### Arguments

- `formatString` (*series string*) — Format string.
- `arg0, arg1, ...` (*array<[int|float|bool|string]>|na *) — Values to format.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.format).*

### Returns
The formatted string.

### Remarks
By default, formatted numbers will display up to three decimals with no trailing zeros. The string used as the formatString argument can contain single quote characters ('). However, one must pair all single quotes in that string to avoid unexpected formatting results. Any curly braces within an unquoted pattern must be balanced. For example, "ab {0} de" and "ab '}' de" are valid patterns, but "ab {0'}' de", "ab } de" and "''{''" are not.

### Code Example
```pine
//@version=6
indicator("str.format", overlay=true)
// The format specifier inside the curly braces accepts certain modifiers:
// - Specify the number of decimals to display:
s1 = str.format("{0,number,#.#}", 1.34) // returns: 1.3
label.new(bar_index, close, text=s1)
// - Round a float value to an integer:
s2 = str.format("{0,number,integer}", 1.34) // returns: 1
label.new(bar_index - 1, close, text=s2)
// - Display a number in currency:
s3 = str.format("{0,number,currency}", 1.34) // returns: $1.34
label.new(bar_index - 2, close, text=s3)
// - Display a number as a percentage:
s4 = str.format("{0,number,percent}", 0.5) // returns: 50%
label.new(bar_index - 3, close, text=s4)
// EXAMPLES WITH SEVERAL ARGUMENTS
// returns: Number 1 is not equal to 4
s5 = str.format("Number {0} is not {1} to {2}", 1, "equal", 4)
label.new(bar_index - 4, close, text=s5)
// returns: 1.34 != 1.3
s6 = str.format("{0} != {0, number, #.#}", 1.34)
label.new(bar_index - 5, close, text=s6)
// returns: 1 is equal to 1, but 2 is equal to 2
s7 = str.format("{0, number, integer} is equal to 1, but {1, number, integer} is equal to 2", 1.34, 1.52)
label.new(bar_index - 6, close, text=s7)
// returns: The cash turnover amounted to $1,340,000.00
s8 = str.format("The cash turnover amounted to {0, number, currency}", 1340000)
label.new(bar_index - 7, close, text=s8)
// returns: Expected return is 10% - 20%
s9 = str.format("Expected return is {0, number, percent} - {1, number, percent}", 0.1, 0.2)
label.new(bar_index - 8, close, text=s9)
```

---

## str.format_time()

Converts the time timestamp into a string formatted according to format and timezone.

### Syntax

```pine
str.format_time(time, format, timezone) → series string
```

### Arguments

- `time` (*series int*) — UNIX time, in milliseconds.
- `format` (*series string*, default `"yyyy-MM-dd'T'HH:mm:ssZ"`) — A format string specifying the date/time representation of the `time` in the returned string. All letters used in the string, except those escaped by single quotation marks `'`, are considered formatting tokens and will be used as a formatting instruction. Refer to the Remarks section for a list of the most useful tokens. Optional. The default is "yyyy-MM-dd'T'HH:mm:ssZ", which represents the ISO 8601 standard.
- `timezone` (*series string*, optional, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an [IANA time zone database name](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.format_time).*

### Returns
The formatted string.

### Remarks
The M, d, h, H, m and s tokens can all be doubled to generate leading zeros. For example, the month of January will display as 1 with M, or 01 with MM.  The most frequently used formatting tokens are:  y - Year. Use yy to output the last two digits of the year or yyyy to output all four. Year 2000 will be 00 with yy or 2000 with yyyy. M - Month. Not to be confused with lowercase m, which stands for minute. d - Day of the month. a - AM/PM postfix. h - Hour in the 12-hour format. The last hour of the day will be 11 in this format. H - Hour in the 24-hour format. The last hour of the day will be 23 in this format. m - Minute. s - Second. S - Fractions of a second. Z - Timezone, the HHmm offset from UTC, preceded by either + or -.

### Code Example
```pine
//@version=6
indicator("str.format_time")
if timeframe.change("1D")
    formattedTime = str.format_time(time, "yyyy-MM-dd HH:mm", syminfo.timezone)
    label.new(bar_index, high, formattedTime)
```

---

## str.length()

Returns an integer corresponding to the amount of chars in that string.

### Syntax

```pine
str.length(string) → int
```

### Arguments

- `string` (*series string*) — Source string.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.length).*

### Returns
The number of chars in source string.

---

## str.lower()

Returns a new string with all letters converted to lowercase.

### Syntax

```pine
str.lower(source) → string
```

### Arguments

- `source` (*series string*) — String to be converted.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.lower).*

### Returns
A new string with all letters converted to lowercase.

---

## str.match()

Returns the new substring of the source string if it matches a regex regular expression, an empty string otherwise.

### Syntax

```pine
str.match(source, regex) → string
```

### Arguments

- `source` (*series string*) — Source string.
- `regex` (*series string*) — The regular expression to which this string is to be matched.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.match).*

### Returns
The new substring of the source string if it matches a regex regular expression, an empty string otherwise.

### Remarks
Function returns first occurrence of the regular expression in the source string. The backslash "\" symbol in theregex string needs to be escaped with additional backslash, e.g. "\\d" stands for regular expression "\d".

### Code Example
```pine
//@version=6
indicator("str.match")

s = input.string("It's time to sell some NASDAQ:AAPL!")

// finding first substring that matches regular expression "[\w]+:[\w]+"
var string tickerid = str.match(s, "[\\w]+:[\\w]+")

if barstate.islastconfirmedhistory
    label.new(bar_index, high, text = tickerid) // "NASDAQ:AAPL"
```

---

## str.pos()

Returns the position of the first occurrence of the str string in the source string, 'na' otherwise.

### Syntax

```pine
str.pos(source, str) → int
```

### Arguments

- `source` (*series string*) — Source string.
- `str` (*series string*) — The substring to search for.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.pos).*

### Returns
Position of the str string in the source string.

### Remarks
Strings indexing starts at 0.

---

## str.repeat()

Constructs a new string containing the source string repeated repeat times with the separator injected between each repeated instance.

### Syntax

```pine
str.repeat(source, repeat, separator) → string
```

*Signature from the official v6 User Manual. Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.repeat).*

### Remarks
Returns na if the source is na.

### Code Example
```pine
//@version=6
indicator("str.repeat")
repeat = str.repeat("?", 3, ",") // Returns "?,?,?"
label.new(bar_index,close,repeat)
```

---

## str.replace()

Returns a new string with the Nth occurrence of the target string replaced by the replacement string, where N is specified in occurrence.

### Syntax

```pine
str.replace(source, target, replacement, occurrence) → string
```

### Arguments

- `source` (*series string*) — Source string.
- `target` (*series string*) — String to be replaced.
- `replacement` (*series string*) — String to be inserted instead of the target string.
- `occurrence` (*series int*, optional, default `0`) — N-th occurrence of the target string to replace. Indexing starts at 0 for the first match. Optional. Default value is 0.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.replace).*

### Returns
Processed string.

### Code Example
```pine
//@version=6
indicator("str.replace")
var source = "FTX:BTCUSD / FTX:BTCEUR"

// Replace first occurrence of "FTX" with "BINANCE" replacement string
var newSource = str.replace(source, "FTX", "BINANCE", 0)

if barstate.islastconfirmedhistory
    // Display "BINANCE:BTCUSD / FTX:BTCEUR"
    label.new(bar_index, high, text = newSource)
```

---

## str.replace_all()

Replaces each occurrence of the target string in the source string with the replacement string.

### Syntax

```pine
str.replace_all(source, target, replacement) → string
```

### Arguments

- `source` (*series string*) — Source string.
- `target` (*series string*) — String to be replaced.
- `replacement` (*series string*) — String to be substituted for each occurrence of target string.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.replace_all).*

### Returns
Processed string.

---

## str.split()

Divides a string into an array of substrings and returns its array id.

### Syntax

```pine
str.split(string, separator) → array<string>
```

### Arguments

- `string` (*series string*) — Source string.
- `separator` (*series string*) — The string separating each substring.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.split).*

### Returns
The id of an array of strings.

---

## str.startswith()

Returns true if the source string starts with the substring specified in str, false otherwise.

### Syntax

```pine
str.startswith(source, str) → bool
```

### Arguments

- `source` (*series string*) — Source string.
- `str` (*series string*) — The substring to search for.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.startswith).*

### Returns
True if the source string starts with the substring specified in str, false otherwise.

---

## str.substring()

Returns a new string that is a substring of the source string. The substring begins with the character at the index specified by begin_pos and extends to 'end_pos - 1' of the source string.

### Syntax

```pine
str.substring(source, begin_pos) → string
str.substring(source, begin_pos, end_pos) → string
```

### Arguments

- `source` (*series string*) — Source string from which to extract the substring.
- `begin_pos` (*series int*) — The beginning position of the extracted substring. It is inclusive (the extracted substring includes the character at that position).
- `end_pos` (*series int*, optional, default `str.length(source)`) — The ending position. It is exclusive (the extracted string does NOT include that position’s character). Optional. The default is the length of the `source` string.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.substring).*

### Returns
The substring extracted from the source string.

### Remarks
Strings indexing starts from 0. If begin_pos is equal to end_pos, the function returns an empty string.

### Code Example
```pine
//@version=6
indicator("str.substring", overlay = true)
sym= input.symbol("NASDAQ:AAPL")
pos = str.pos(sym, ":") // Get position of ":" character
tkr= str.substring(sym, pos+1) // "AAPL"
if barstate.islastconfirmedhistory
    label.new(bar_index, high, text = tkr)
```

---

## str.tonumber()

Converts a value represented in string to its "float" equivalent.

### Syntax

```pine
str.tonumber(string) → series float
```

### Arguments

- `string` (*series string*) — String containing the representation of an integer or floating point value.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tonumber).*

### Returns
A "float" equivalent of the value in string. If the value is not a properly formed integer or floating point value, the function returns na.

---

## str.tostring()

### Syntax

```pine
str.tostring(value) → string
str.tostring(value, format) → string
```

### Arguments

- `value` (*series matrix|array<int|float|bool|string>*) — Value or array ID whose elements are converted to a string.
- `format` (*series string*, default `'#.##########'`) — Format string. Accepts these format.* constants: [format.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_format.mintick), [format.percent](https://www.tradingview.com/pine-script-reference/v6/#var_format.percent), [format.volume](https://www.tradingview.com/pine-script-reference/v6/#var_format.volume). Optional. The default value is '#.##########'.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.tostring).*

### Returns
The string representation of the value argument.

### Remarks
The formatting of float values will also round those values when necessary, e.g. str.tostring(3.99, '#') will return "4". To display trailing zeros, use '0' instead of '#'. For example, '#.000'. When using format.mintick, the value will be rounded to the nearest number that can be divided by syminfo.mintick without the remainder. The string is returned with trailing zeros. If the x argument is a string, the same string value will be returned. Bool type arguments return "true" or "false". When x is na, the function returns "NaN".

---

## str.trim()

Constructs a new string with all consecutive whitespaces and other control characters (e.g., “\n”, “\t”, etc.) removed from the left and right of the source.

### Syntax

```pine
str.trim(source) → string
```

*Signature from the official v6 User Manual. Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.trim).*

### Remarks
Returns an empty string ("") if the result is empty after the trim or if the source is na.

### Code Example
```pine
//@version=6
indicator("str.trim")
trim = str.trim("    abc    ") // Returns "abc"
label.new(bar_index,close,trim)
```

---

## str.upper()

Returns a new string with all letters converted to uppercase.

### Syntax

```pine
str.upper(source) → string
```

### Arguments

- `source` (*series string*) — String to be converted.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_str.upper).*

### Returns
A new string with all letters converted to uppercase.

---

## strategy()

This declaration statement designates the script as a strategy and sets a number of strategy-related properties.

### Syntax

```pine
strategy(title, shorttitle, overlay, format, precision, scale, pyramiding, calc_on_order_fills, calc_on_every_tick, max_bars_back, backtest_fill_limits_assumption, default_qty_type, default_qty_value, initial_capital, currency, slippage, commission_type, commission_value, process_orders_on_close, close_entries_rule, margin_long, margin_short, explicit_plot_zorder, max_lines_count, max_labels_count, max_boxes_count, calc_bars_count, risk_free_rate, use_bar_magnifier, fill_orders_on_standard_ohlc, max_polylines_count, dynamic_requests, behind_chart, calc_on_every_history_tick) → void
```

### Arguments

- `title` (*const string*) — The title of the script. It is displayed on the chart when no `shorttitle` argument is used, and becomes the publication’s default title when publishing the script.
- `shorttitle` (*const string*, optional, default `'title'`) — The script’s display name on charts. If specified, it will replace the `title` argument in most chart-related windows. Optional. The default is the argument used for `title`.
- `overlay` (*const bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the strategy will be displayed over the chart. If [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), it will be added in a separate pane. Strategy-specific labels that display entries and exits will be displayed over the main chart regardless of this setting. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `format` (*const string*, optional, default `format.inherit`) — Specifies the formatting of the script’s displayed values. Possible values: [format.inherit](https://www.tradingview.com/pine-script-reference/v6/#var_format.inherit), [format.price](https://www.tradingview.com/pine-script-reference/v6/#var_format.price), [format.volume](https://www.tradingview.com/pine-script-reference/v6/#var_format.volume), [format.percent](https://www.tradingview.com/pine-script-reference/v6/#var_format.percent). Optional. The default is [format.inherit](https://www.tradingview.com/pine-script-reference/v6/#var_format.inherit).
- `precision` (*const int*, optional, default `syminfo.pricescale`) — Specifies the number of digits after the floating point of the script’s displayed values. Must be a non-negative integer no greater than 16. If `format` is set to [format.inherit](https://www.tradingview.com/pine-script-reference/v6/#var_format.inherit) and `precision` is specified, the format will instead be set to [format.price](https://www.tradingview.com/pine-script-reference/v6/#var_format.price). Optional. The default is inherited from the precision of the chart’s symbol.
- `scale` (*const scale_type*, optional, default `scale.right`) — The price scale used. Possible values: [scale.right](https://www.tradingview.com/pine-script-reference/v6/#var_scale.right), [scale.left](https://www.tradingview.com/pine-script-reference/v6/#var_scale.left), [scale.none](https://www.tradingview.com/pine-script-reference/v6/#var_scale.none). The [scale.none](https://www.tradingview.com/pine-script-reference/v6/#var_scale.none) value can only be applied in combination with `overlay = true`. Optional. By default, the script uses the same scale as the chart.
- `pyramiding` (*const int*, optional, default `0`) — The maximum number of entries allowed in the same direction. If the value is 0, only one entry order in the same direction can be opened, and additional entry orders are rejected. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is 0.
- `calc_on_order_fills` (*const bool*, optional, default `false`) — Specifies whether the strategy should be recalculated after an order is filled. If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the strategy recalculates after an order is filled, as opposed to recalculating only when the bar closes. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `calc_on_every_tick` (*const bool*, optional, default `false`) — Specifies whether the strategy should be recalculated on each realtime tick. If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), when the strategy is running on a realtime bar, it will recalculate on each chart update. If [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), the strategy only calculates when the realtime bar closes. The argument used does not affect strategy calculation on historical data. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `max_bars_back` (*const int*, optional, default `0`) — The length of the historical buffer the script keeps for every variable and function, which determines how many past values can be referenced using the `[]` history-referencing operator. The required buffer size is automatically detected by the Pine Script™ runtime. Using this parameter is only necessary when a runtime error occurs because automatic detection fails. More information on the underlying mechanics of the historical buffer can be found [in our Help Center](https://www.tradingview.com/chart/?solution=43000587849). Optional. The default is 0.
- `backtest_fill_limits_assumption` (*const int*, optional, default `0`) — Limit order execution threshold in ticks. When it is used, limit orders are only filled if the market price exceeds the order’s limit level by the specified number of ticks. Optional. The default is 0.
- `default_qty_type` (*const string*, optional, default `strategy.fixed`) — Specifies the units used for `default_qty_value`. Possible values are: [strategy.fixed](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.fixed) for contracts/shares/lots, [strategy.cash](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.cash) for currency amounts, or [strategy.percent_of_equity](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.percent_of_equity) for a percentage of available equity. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is [strategy.fixed](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.fixed).
- `default_qty_value` (*const int|float*, optional, default `1`) — The default quantity to trade, in units determined by the argument used with the `default_qty_type` parameter. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is 1.
- `initial_capital` (*const int|float*, optional, default `1000000`) — The amount of funds initially available for the strategy to trade, in units of `currency`. Optional. The default is 1000000.
- `currency` (*const string*, optional, default `syminfo.currency`) — Currency used by the strategy in currency-related calculations. Market positions are still opened by converting `currency` into the chart symbol’s currency. The conversion rates used are based on the FX_IDC pairs' daily rates of the previous day (relative to the bar where the calculation is done). This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is [currency.NONE](https://www.tradingview.com/pine-script-reference/v6/#var_currency.NONE), in which case the chart’s currency is used. Possible values: one of the constants in the `currency.*` namespace, e.g. [currency.USD](https://www.tradingview.com/pine-script-reference/v6/#var_currency.USD).
- `slippage` (*const int*, optional, default `0`) — Slippage expressed in ticks. This value is added to or subtracted from the fill price of market/stop orders to make the fill price less favorable for the strategy. E.g., if [syminfo.mintick](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.mintick) is 0.01 and `slippage` is set to 5, a long market order will enter at 5 * 0.01 = 0.05 points above the actual price. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is 0.
- `commission_type` (*const string*, optional, default `strategy.commission.percent`) — Determines what the number passed to the `commission_value` expresses: [strategy.commission.percent](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.commission.percent) for a percentage of the cash volume of the order, [strategy.commission.cash_per_contract](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.commission.cash_per_contract) for currency per contract, [strategy.commission.cash_per_order](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.commission.cash_per_order) for currency per order. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is [strategy.commission.percent](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.commission.percent).
- `commission_value` (*const int|float*, optional, default `0`) — Commission applied to the strategy’s orders in units determined by the argument passed to the `commission_type` parameter. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is 0.
- `process_orders_on_close` (*const bool*, optional, default `false`) — When set to [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), generates an additional attempt to execute orders after a bar closes and strategy calculations are completed. If the orders are market orders, the broker emulator executes them before the next bar’s open. If the orders are price-dependent, they will only be filled if the price conditions are met. This option is useful if you wish to close positions on the current bar. This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `close_entries_rule` (*const string*, optional, default `"FIFO"`) — Determines the order in which trades are closed. Possible values are: "FIFO" (First-In, First-Out) if the earliest exit order must close the earliest entry order, or "ANY" if the orders are closed based on the `from_entry` parameter of the [strategy.exit](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.exit) function. "FIFO" can only be used with stocks, futures and US forex (NFA Compliance Rule 2-43b), while "ANY" is allowed in non-US forex. Optional. The default is "FIFO".
- `margin_long` (*const int|float*, optional, default `0`) — Margin long is the percentage of the purchase price of a security that must be covered by cash or collateral for long positions. Must be a non-negative number. The logic used to simulate margin calls is explained in the [Help Center](https://www.tradingview.com/chart/?solution=43000628599). This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is 0, in which case the strategy does not enforce any limits on position size.
- `margin_short` (*const int|float*, optional, default `0`) — Margin short is the percentage of the purchase price of a security that must be covered by cash or collateral for short positions. Must be a non-negative number. The logic used to simulate margin calls is explained in the [Help Center](https://www.tradingview.com/chart/?solution=43000628599). This setting can also be changed in the strategy’s "Settings/Properties" tab. Optional. The default is 0, in which case the strategy does not enforce any limits on position size.
- `explicit_plot_zorder` (*const bool*, optional, default `false`) — Specifies the order in which the script’s plots, fills, and hlines are rendered. If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), plots are drawn in the order in which they appear in the script’s code, each newer plot being drawn above the previous ones. This only applies to `plot*()` functions, [fill](https://www.tradingview.com/pine-script-reference/v6/#fun_fill), and [hline](https://www.tradingview.com/pine-script-reference/v6/#fun_hline). Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `max_lines_count` (*const int*, optional, default `50`) — The number of last [line](https://www.tradingview.com/pine-script-reference/v6/#op_line) drawings displayed. Possible values: 1-500. Optional. The default is 50.
- `max_labels_count` (*const int*, optional, default `50`) — The number of last [label](https://www.tradingview.com/pine-script-reference/v6/#op_label) drawings displayed. Possible values: 1-500. Optional. The default is 50.
- `max_boxes_count` (*const int*, optional, default `50`) — The number of last [box](https://www.tradingview.com/pine-script-reference/v6/#op_box) drawings displayed. Possible values: 1-500. Optional. The default is 50.
- `risk_free_rate` (*const int|float*, optional, default `2`) — The risk-free rate of return is the annual percentage change in the value of an investment with minimal or zero risk. It is used to calculate the [Sharpe and Sortino ratios](https://www.tradingview.com/chart/?solution=43000561856). Optional. The default is 2.
- `use_bar_magnifier` (*const bool*, optional, default `false`) — When true, the [Broker Emulator](https://www.tradingview.com/pine-script-docs/en/v5/concepts/Strategies.html#broker-emulator) uses lower timeframe data during history backtesting to achieve more realistic results. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false). Only [Premium](https://www.tradingview.com/gopro/) accounts have access to this feature.
- `fill_orders_on_standard_ohlc` (optional, default `false`) — When true, forces the strategy to fill orders on Heikin Ashi charts using actual OHLC values. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `max_polylines_count` (*const int*, optional, default `50`) — The number of last [polyline](https://www.tradingview.com/pine-script-reference/v6/#op_polyline) drawings displayed. Possible values: 1-100. The count is approximate; more drawings than the specified count may be displayed. Optional. The default is 50.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy).*

### Remarks
You can learn more about strategies in our User Manual. Every strategy script must have one strategy call. Strategies using calc_on_every_tick = true parameter may calculate differently on historical and realtime bars, which causes repainting. Strategies always use the chart's prices to enter and exit positions. Using them on non-standard chart types (Heikin Ashi, Renko, etc.) will produce misleading results, as their prices are synthetic. Backtesting on non-standard charts is thus not recommended. The maximum number of orders a strategy can open, unless it uses Deep Backtesting mode, is 9000. If the strategy exceeds this limit, it removes the oldest order's information when a new entry appears in the "List of Trades" tab. The strategy.closedtrades.*() functions return na for trades opened or closed by removed orders. To retrieve the index of the oldest available closed trade, use the strategy.closedtrades.first_index variable.

### Code Example
```pine
//@version=6
strategy("My strategy", overlay = true)

// Enter long by market if current open is greater than previous high.
if open > high[1]
    strategy.entry("Long", strategy.long, 1)
// Generate a full exit bracket (profit 10 points, loss 5 points per contract) from the entry named "Long".
strategy.exit("Exit", "Long", profit = 10, loss = 5)
```

---

## strategy.cancel()

Cancels a pending or unfilled order with a specific identifier. If multiple unfilled orders share the same ID, calling this command with that ID as the id argument cancels all of them. If a script calls this command with an id representing the ID of a filled order, it has no effect.

### Syntax

```pine
strategy.cancel(id) → void
```

### Arguments

- `id` (*series string*) — A required parameter. The order identifier. It is possible to cancel an order by referencing its identifier.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.cancel).*

### Code Example
```pine
//@version=6
strategy(title = "Order cancellation demo")

conditionForBuy = open > high[1]
if conditionForBuy
    strategy.entry("Long", strategy.long, 1, limit = low) // Enter long using limit order at low price of current bar if `conditionForBuy` is `true`.
if not conditionForBuy
    strategy.cancel("Long") // Cancel the entry order with name "Long" if `conditionForBuy` is `false`.
```

---

## strategy.cancel_all()

Cancels all pending or unfilled orders, regardless of their identifiers.

### Syntax

```pine
strategy.cancel_all() → void
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.cancel_all).*

### Code Example
```pine
//@version=6
strategy(title = "Cancel all orders demo")
conditionForBuy1 = open > high[1]
if conditionForBuy1
    strategy.entry("Long entry 1", strategy.long, 1, limit = low) // Enter long using a limit order if `conditionForBuy1` is `true`.
conditionForBuy2 = conditionForBuy1 and open[1] > high[2]
float lowest2 = ta.lowest(low, 2)
if conditionForBuy2
    strategy.entry("Long entry 2", strategy.long, 1, limit = lowest2) // Enter long using a limit order if `conditionForBuy2` is `true`.
conditionForStopTrading = open < lowest2
if conditionForStopTrading
    strategy.cancel_all() // Cancel both limit orders if `conditionForStopTrading` is `true`.
```

---

## strategy.close()

Creates an order to exit from the part of a position opened by entry orders with a specific identifier. If multiple entries in the position share the same ID, the orders from this command apply to all those entries, starting from the first open trade, when its calls use that ID as the id argument.

### Syntax

```pine
strategy.close(id, comment, qty, qty_percent, alert_message, immediately) → void
```

### Arguments

- `id` (*series string*) — A required parameter. The order identifier. It is possible to close an order by referencing its identifier.
- `comment` (*series string*, optional) — An optional parameter. Additional notes on the order.
- `qty` (*series int|float*, optional, default `na`) — An optional parameter. Number of contracts/shares/lots/units to exit a trade with. The default value is 'NaN'.
- `qty_percent` (*series int|float*, optional, default `100`) — Defines the percentage (0-100) of the position to close. Its priority is lower than that of the 'qty' parameter. Optional. The default is 100.
- `alert_message` (*series string*, optional) — An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box’s "Message" field.
- `immediately` (*series bool*, optional, default `false`) — An optional parameter. If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the closing order will be executed on the tick where it has been placed, ignoring the strategy parameters that restrict the order execution to the open of the next bar. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `disable_alert` (*series bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true) when the function creates an order, the strategy alert will not fire upon the execution of that order. The parameter accepts a 'series bool' argument, allowing users to control which orders will trigger alerts when they fill. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.close).*

### Remarks
When a position consists of several open trades and the close_entries_rule in the strategy declaration statement is "FIFO" (default), a strategy.close call exits from the position starting with the first open trade. This behavior applies even if the id value is the entry ID of different open trades. However, in that case, the maximum exit order size still depends on the trades opened by orders with the id identifier. For more information, see this section of our User Manual.

### Code Example
```pine
//@version=6
strategy("Partial close strategy")

// Calculate a 14-bar and 28-bar moving average of `close` prices.
float sma14 = ta.sma(close, 14)
float sma28 = ta.sma(close, 28)

// Place a market order to enter a long position when `sma14` crosses over `sma28`.
if ta.crossover(sma14, sma28)
    strategy.entry("My Long Entry ID", strategy.long)

// Place a market order to close the long trade when `sma14` crosses under `sma28`. 
if ta.crossunder(sma14, sma28)
    strategy.close("My Long Entry ID", "50% market close", qty_percent = 50)

// Plot the position size.
plot(strategy.position_size)
```

---

## strategy.close_all()

Creates an order to close an open position completely, regardless of the identifiers of the entry orders that opened or added to it.

### Syntax

```pine
strategy.close_all(comment, alert_message, immediately) → void
```

### Arguments

- `comment` (*series string*, optional) — An optional parameter. Additional notes on the order.
- `alert_message` (*series string*, optional) — An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box’s "Message" field.
- `immediately` (*series bool*, optional, default `false`) — An optional parameter. If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the closing order will be executed on the tick where it has been placed, ignoring the strategy parameters that restrict the order execution to the open of the next bar. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).
- `disable_alert` (*series bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true) when the function creates an order, the strategy alert will not fire upon the execution of that order. The parameter accepts a 'series bool' argument, allowing users to control which orders will trigger alerts when they fill. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.close_all).*

### Code Example
```pine
//@version=6
strategy("Multi-entry close strategy")

// Calculate a 14-bar and 28-bar moving average of `close` prices.
float sma14 = ta.sma(close, 14)
float sma28 = ta.sma(close, 28)

// Place a market order to enter a long trade every time `sma14` crosses over `sma28`.
if ta.crossover(sma14, sma28)
    strategy.order("My Long Entry ID " + str.tostring(strategy.opentrades), strategy.long)

// Place a market order to close the entire position every 500 bars. 
if bar_index % 500 == 0
    strategy.close_all()

// Plot the position size.
plot(strategy.position_size)
```

---

## strategy.closedtrades.commission()

Returns the sum of entry and exit fees paid in the closed trade, expressed in strategy.account_currency.

### Syntax

```pine
strategy.closedtrades.commission(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.commission).*

### Code Example
```pine
//@version=6
strategy("`strategy.closedtrades.commission` Example", commission_type = strategy.commission.percent, commission_value = 0.1)

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Plot total fees for the latest closed trade.
plot(strategy.closedtrades.commission(strategy.closedtrades - 1))
```

---

## strategy.closedtrades.entry_bar_index()

Returns the bar_index of the closed trade's entry.

### Syntax

```pine
strategy.closedtrades.entry_bar_index(trade_num) → series int
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.entry_bar_index).*

### Code Example
```pine
//@version=6
strategy("strategy.closedtrades.entry_bar_index Example")
// Enter long trades on three rising bars; exit on two falling bars.
if ta.rising(close, 3)
    strategy.entry("Long", strategy.long)
if ta.falling(close, 2)
    strategy.close("Long")
// Function that calculates the average amount of bars in a trade.
avgBarsPerTrade() =>
    sumBarsPerTrade = 0
    for tradeNo = 0 to strategy.closedtrades - 1
        // Loop through all closed trades, starting with the oldest.
        sumBarsPerTrade += strategy.closedtrades.exit_bar_index(tradeNo) - strategy.closedtrades.entry_bar_index(tradeNo) + 1
    result = nz(sumBarsPerTrade / strategy.closedtrades)
plot(avgBarsPerTrade())
```

---

## strategy.closedtrades.entry_comment()

Returns the comment message of the closed trade's entry, or na
if there is no entry with this trade_num.

### Syntax

```pine
strategy.closedtrades.entry_comment(trade_num) → series string
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.entry_comment).*

### Code Example
```pine
//@version=6
strategy("`strategy.closedtrades.entry_comment()` Example", overlay = true)

stopPrice = open * 1.01

longCondition = ta.crossover(ta.sma(close, 14), ta.sma(close, 28))

if (longCondition)
    strategy.entry("Long", strategy.long, stop = stopPrice, comment = str.tostring(stopPrice, "#.####"))
    strategy.exit("EXIT", trail_points = 1000, trail_offset = 0)

var testTable = table.new(position.top_right, 1, 3, color.orange, border_width = 1)

if barstate.islastconfirmedhistory or barstate.isrealtime
    table.cell(testTable, 0, 0, 'Last closed trade:')
    table.cell(testTable, 0, 1, "Order stop price value: " + strategy.closedtrades.entry_comment(strategy.closedtrades - 1))
    table.cell(testTable, 0, 2, "Actual Entry Price: " + str.tostring(strategy.closedtrades.entry_price(strategy.closedtrades - 1)))
```

---

## strategy.closedtrades.entry_id()

Returns the id of the closed trade's entry.

### Syntax

```pine
strategy.closedtrades.entry_id(trade_num) → series string
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.entry_id).*

### Returns
Returns the id of the closed trade's entry.

### Remarks
The function returns na if trade_num is not in the range: 0 to strategy.closedtrades-1.

### Code Example
```pine
//@version=6
strategy("strategy.closedtrades.entry_id Example", overlay = true)

// Enter a short position and close at the previous to last bar.
if bar_index == 1
    strategy.entry("Short at bar #" + str.tostring(bar_index), strategy.short)
if bar_index == last_bar_index - 2
    strategy.close_all()
    
// Display ID of the last entry position.
if barstate.islastconfirmedhistory
    label.new(last_bar_index, high, "Last Entry ID is: " + strategy.closedtrades.entry_id(strategy.closedtrades - 1))
```

---

## strategy.closedtrades.entry_price()

Returns the price of the closed trade's entry.

### Syntax

```pine
strategy.closedtrades.entry_price(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.entry_price).*

### Code Example
```pine
//@version=6
strategy("strategy.closedtrades.entry_price Example 1")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Return the entry price for the latest entry.
entryPrice = strategy.closedtrades.entry_price(strategy.closedtrades - 1)

plot(entryPrice, "Long entry price")

// Calculates the average profit percentage for all closed trades.
//@version=6
strategy("strategy.closedtrades.entry_price Example 2")

// Strategy calls to create single short and long trades
if bar_index == last_bar_index - 15
    strategy.entry("Long Entry", strategy.long)
else if bar_index == last_bar_index - 10
    strategy.close("Long Entry")
    strategy.entry("Short", strategy.short)
else if bar_index == last_bar_index - 5
    strategy.close("Short")

// Calculate profit for both closed trades.
profitPct = 0.0
for tradeNo = 0 to strategy.closedtrades - 1
    entryP = strategy.closedtrades.entry_price(tradeNo)
    exitP = strategy.closedtrades.exit_price(tradeNo)
    profitPct += (exitP - entryP) / entryP * strategy.closedtrades.size(tradeNo) * 100
    
// Calculate average profit percent for both closed trades.
avgProfitPct = nz(profitPct / strategy.closedtrades)

plot(avgProfitPct)
```

---

## strategy.closedtrades.entry_time()

Returns the UNIX time of the closed trade's entry, expressed in milliseconds..

### Syntax

```pine
strategy.closedtrades.entry_time(trade_num) → series int
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.entry_time).*

### Code Example
```pine
//@version=6
strategy("strategy.closedtrades.entry_time Example", overlay = true)

// Enter long trades on three rising bars; exit on two falling bars.
if ta.rising(close, 3)
    strategy.entry("Long", strategy.long)
if ta.falling(close, 2)
    strategy.close("Long")

// Calculate the average trade duration 
avgTradeDuration() =>
    sumTradeDuration = 0
    for i = 0 to strategy.closedtrades - 1
        sumTradeDuration += strategy.closedtrades.exit_time(i) - strategy.closedtrades.entry_time(i)
    result = nz(sumTradeDuration / strategy.closedtrades)

// Display average duration converted to seconds and formatted using 2 decimal points
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(avgTradeDuration() / 1000, "#.##") + " seconds")
```

---

## strategy.closedtrades.exit_bar_index()

Returns the bar_index of the closed trade's exit.

### Syntax

```pine
strategy.closedtrades.exit_bar_index(trade_num) → series int
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.exit_bar_index).*

### Code Example
```pine
//@version=6
strategy("strategy.closedtrades.exit_bar_index Example 1")

// Strategy calls to place a single short trade. We enter the trade at the first bar and exit the trade at 10 bars before the last chart bar.
if bar_index == 0
    strategy.entry("Short", strategy.short)
if bar_index == last_bar_index - 10
    strategy.close("Short")

// Calculate the amount of bars since the last closed trade.
barsSinceClosed = strategy.closedtrades > 0 ? bar_index - strategy.closedtrades.exit_bar_index(strategy.closedtrades - 1) : na

plot(barsSinceClosed, "Bars since last closed trade")

// Calculates the average amount of bars per trade.
//@version=6
strategy("strategy.closedtrades.exit_bar_index Example 2")

// Enter long trades on three rising bars; exit on two falling bars.
if ta.rising(close, 3)
    strategy.entry("Long", strategy.long)
if ta.falling(close, 2)
    strategy.close("Long")

// Function that calculates the average amount of bars per trade.
avgBarsPerTrade() =>
    sumBarsPerTrade = 0
    for tradeNo = 0 to strategy.closedtrades - 1
        // Loop through all closed trades, starting with the oldest.
        sumBarsPerTrade += strategy.closedtrades.exit_bar_index(tradeNo) - strategy.closedtrades.entry_bar_index(tradeNo) + 1
    result = nz(sumBarsPerTrade / strategy.closedtrades)

plot(avgBarsPerTrade())
```

---

## strategy.closedtrades.exit_comment()

Returns the comment message of the closed trade's exit, or
na if there is no entry with this trade_num.

### Syntax

```pine
strategy.closedtrades.exit_comment(trade_num) → series string
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.exit_comment).*

### Code Example
```pine
//@version=6
strategy("`strategy.closedtrades.exit_comment()` Example", overlay = true)

longCondition = ta.crossover(ta.sma(close, 14), ta.sma(close, 28))
if (longCondition)
    strategy.entry("Long", strategy.long)
    strategy.exit("Exit", stop = open * 0.95, limit = close * 1.05, trail_points = 100, trail_offset = 0, comment_profit = "TP", comment_loss = "SL", comment_trailing = "TRAIL")

exitStats() =>
    int slCount = 0
    int tpCount = 0
    int trailCount = 0
    
    if strategy.closedtrades > 0
        for i = 0 to strategy.closedtrades - 1
            switch strategy.closedtrades.exit_comment(i)
                "TP"    => tpCount    += 1
                "SL"    => slCount    += 1
                "TRAIL" => trailCount += 1
    [slCount, tpCount, trailCount]

var testTable = table.new(position.top_right, 1, 4, color.orange, border_width = 1)

if barstate.islastconfirmedhistory
    [slCount, tpCount, trailCount] = exitStats()
    table.cell(testTable, 0, 0, "Closed trades (" + str.tostring(strategy.closedtrades) +") stats:")
    table.cell(testTable, 0, 1, "Stop Loss: " + str.tostring(slCount))
    table.cell(testTable, 0, 2, "Take Profit: " + str.tostring(tpCount))
    table.cell(testTable, 0, 3, "Trailing Stop: " + str.tostring(trailCount))
```

---

## strategy.closedtrades.exit_id()

Returns the id of the closed trade's exit.

### Syntax

```pine
strategy.closedtrades.exit_id(trade_num) → series string
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.exit_id).*

### Returns
Returns the id of the closed trade's exit.

### Remarks
The function returns na if trade_num is not in the range: 0 to strategy.closedtrades-1.

### Code Example
```pine
//@version=6
strategy("strategy.closedtrades.exit_id Example", overlay = true)

// Strategy calls to create single short and long trades
if bar_index == last_bar_index - 15
    strategy.entry("Long Entry", strategy.long)
else if bar_index == last_bar_index - 10
    strategy.entry("Short Entry", strategy.short)
    
// When a new open trade is detected then we create the exit strategy corresponding with the matching entry id
// We detect the correct entry id by determining if a position is long or short based on the position quantity
if ta.change(strategy.opentrades) != 0
    posSign = strategy.opentrades.size(strategy.opentrades - 1)
    strategy.exit(posSign > 0 ? "SL Long Exit" : "SL Short Exit", strategy.opentrades.entry_id(strategy.opentrades - 1), stop = posSign > 0 ? high - ta.tr : low + ta.tr)

// When a new closed trade is detected then we place a label above the bar with the exit info
if ta.change(strategy.closedtrades) != 0
    msg = "Trade closed by: " + strategy.closedtrades.exit_id(strategy.closedtrades - 1)
    label.new(bar_index, high + (3 * ta.tr), msg)
```

---

## strategy.closedtrades.exit_price()

Returns the price of the closed trade's exit.

### Syntax

```pine
strategy.closedtrades.exit_price(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.exit_price).*

### Code Example
```pine
//@version=6
strategy("strategy.closedtrades.exit_price Example 1")

// We are creating a long trade every 5 bars
if bar_index % 5 == 0
    strategy.entry("Long", strategy.long)
strategy.close("Long")

// Return the exit price from the latest closed trade.
exitPrice = strategy.closedtrades.exit_price(strategy.closedtrades - 1)

plot(exitPrice, "Long exit price")

// Calculates the average profit percentage for all closed trades.
//@version=6
strategy("strategy.closedtrades.exit_price Example 2")

// Strategy calls to create single short and long trades.
if bar_index == last_bar_index - 15
    strategy.entry("Long Entry", strategy.long)
else if bar_index == last_bar_index - 10
    strategy.close("Long Entry")
    strategy.entry("Short", strategy.short)
else if bar_index == last_bar_index - 5
    strategy.close("Short")

// Calculate profit for both closed trades.
profitPct = 0.0
for tradeNo = 0 to strategy.closedtrades - 1
    entryP = strategy.closedtrades.entry_price(tradeNo)
    exitP = strategy.closedtrades.exit_price(tradeNo)
    profitPct += (exitP - entryP) / entryP * strategy.closedtrades.size(tradeNo) * 100
    
// Calculate average profit percent for both closed trades.
avgProfitPct = nz(profitPct / strategy.closedtrades)

plot(avgProfitPct)
```

---

## strategy.closedtrades.exit_time()

Returns the UNIX time of the closed trade's exit, expressed in milliseconds.

### Syntax

```pine
strategy.closedtrades.exit_time(trade_num) → series int
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.exit_time).*

### Code Example
```pine
//@version=6
strategy("strategy.closedtrades.exit_time Example 1")

// Enter long trades on three rising bars; exit on two falling bars.
if ta.rising(close, 3)
    strategy.entry("Long", strategy.long)
if ta.falling(close, 2)
    strategy.close("Long")

// Calculate the average trade duration. 
avgTradeDuration() =>
    sumTradeDuration = 0
    for i = 0 to strategy.closedtrades - 1
        sumTradeDuration += strategy.closedtrades.exit_time(i) - strategy.closedtrades.entry_time(i)
    result = nz(sumTradeDuration / strategy.closedtrades)

// Display average duration converted to seconds and formatted using 2 decimal points.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(avgTradeDuration() / 1000, "#.##") + " seconds")

// Reopens a closed trade after X seconds.
//@version=6
strategy("strategy.closedtrades.exit_time Example 2")

// Strategy calls to emulate a single long trade at the first bar.
if bar_index == 0
    strategy.entry("Long", strategy.long)

reopenPositionAfter(timeSec) =>
    if strategy.closedtrades > 0
        if time - strategy.closedtrades.exit_time(strategy.closedtrades - 1) >= timeSec * 1000
            strategy.entry("Long", strategy.long)

// Reopen last closed position after 120 sec.                
reopenPositionAfter(120)

if ta.change(strategy.opentrades) != 0
    strategy.exit("Long", stop = low * 0.9, profit = high * 2.5)
```

---

## strategy.closedtrades.max_drawdown()

Returns the maximum drawdown of the closed trade, i.e., the maximum possible loss during the trade, expressed in strategy.account_currency.

### Syntax

```pine
strategy.closedtrades.max_drawdown(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.max_drawdown).*

### Remarks
The function returns na if trade_num is not in the range: 0 to strategy.closedtrades - 1.

### Code Example
```pine
//@version=6
strategy("`strategy.closedtrades.max_drawdown` Example")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Get the biggest max trade drawdown value from all of the closed trades.
maxTradeDrawDown() =>
    maxDrawdown = 0.0
    for tradeNo = 0 to strategy.closedtrades - 1
        maxDrawdown := math.max(maxDrawdown, strategy.closedtrades.max_drawdown(tradeNo))
    result = maxDrawdown

plot(maxTradeDrawDown(), "Biggest max drawdown")
```

---

## strategy.closedtrades.max_drawdown_percent()

Returns the maximum drawdown of the closed trade, i.e., the maximum possible loss during the trade, expressed as a percentage and calculated by formula: Lowest Value During Trade / (Entry Price x Quantity) * 100.

---

### Syntax

```pine
strategy.closedtrades.max_drawdown_percent(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.max_drawdown_percent).*

## strategy.closedtrades.max_runup()

Returns the maximum run up of the closed trade, i.e., the maximum possible profit during the trade, expressed in strategy.account_currency.

### Syntax

```pine
strategy.closedtrades.max_runup(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.max_runup).*

### Code Example
```pine
//@version=6
strategy("`strategy.closedtrades.max_runup` Example")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Get the biggest max trade runup value from all of the closed trades.
maxTradeRunUp() =>
    maxRunup = 0.0
    for tradeNo = 0 to strategy.closedtrades - 1
        maxRunup := math.max(maxRunup, strategy.closedtrades.max_runup(tradeNo))
    result = maxRunup

plot(maxTradeRunUp(), "Max trade runup")
```

---

## strategy.closedtrades.max_runup_percent()

Returns the maximum run-up of the closed trade, i.e., the maximum possible profit during the trade, expressed as a percentage and calculated by formula: Highest Value During Trade / (Entry Price x Quantity) * 100.

---

### Syntax

```pine
strategy.closedtrades.max_runup_percent(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.max_runup_percent).*

## strategy.closedtrades.profit()

Returns the profit/loss of the closed trade, expressed in strategy.account_currency. Losses are expressed as negative values.

### Syntax

```pine
strategy.closedtrades.profit(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.profit).*

### Code Example
```pine
//@version=6
strategy("`strategy.closedtrades.profit` Example")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Calculate average gross profit by adding the difference between gross profit and commission.
avgGrossProfit() =>
    sumGrossProfit = 0.0
    for tradeNo = 0 to strategy.closedtrades - 1
        sumGrossProfit += strategy.closedtrades.profit(tradeNo) - strategy.closedtrades.commission(tradeNo)
    result = nz(sumGrossProfit / strategy.closedtrades)
    
plot(avgGrossProfit(), "Average gross profit")
```

---

## strategy.closedtrades.profit_percent()

Returns the profit/loss value of the closed trade, expressed as a percentage. Losses are expressed as negative values.

---

### Syntax

```pine
strategy.closedtrades.profit_percent(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.profit_percent).*

## strategy.closedtrades.size()

Returns the direction and the number of contracts traded in the closed trade. If the value is > 0, the market position was long. If the value is < 0, the market position was short.

### Syntax

```pine
strategy.closedtrades.size(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.closedtrades.size).*

### Code Example
```pine
//@version=6
strategy("`strategy.closedtrades.size` Example 1")

// We calculate the max amt of shares we can buy.
amtShares = math.floor(strategy.equity / close)
// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long, qty = amtShares)
if bar_index % 20 == 0
    strategy.close("Long")

// Plot the number of contracts traded in the last closed trade.     
plot(strategy.closedtrades.size(strategy.closedtrades - 1), "Number of contracts traded")

// Calculates the average profit percentage for all closed trades.
//@version=6
strategy("`strategy.closedtrades.size` Example 2")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Calculate profit for both closed trades.
profitPct = 0.0
for tradeNo = 0 to strategy.closedtrades - 1
    entryP = strategy.closedtrades.entry_price(tradeNo)
    exitP = strategy.closedtrades.exit_price(tradeNo)
    profitPct += (exitP - entryP) / entryP * strategy.closedtrades.size(tradeNo) * 100
    
// Calculate average profit percent for both closed trades.
avgProfitPct = nz(profitPct / strategy.closedtrades)

plot(avgProfitPct)
```

---

## strategy.convert_to_account()

Converts the value from the currency that the symbol on the chart is traded in (syminfo.currency) to the currency used by the strategy (strategy.account_currency).

### Syntax

```pine
strategy.convert_to_account(value) → series float
```

### Arguments

- `value` (*series int|float*) — The value to be converted.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.convert_to_account).*

### Code Example
```pine
//@version=6
strategy("`strategy.convert_to_account` Example 1", currency = currency.EUR)

plot(close, "Close price using default currency")
plot(strategy.convert_to_account(close), "Close price converted to strategy currency")

// Calculates the "Buy and hold return" using your account's currency.
//@version=6
strategy("`strategy.convert_to_account` Example 2", currency = currency.EUR)

dateInput = input.time(timestamp("20 Jul 2021 00:00 +0300"), "From Date", confirm = true)

buyAndHoldReturnPct(fromDate) =>
    if time >= fromDate
        money = close * syminfo.pointvalue
        var initialBal = strategy.convert_to_account(money)
        (strategy.convert_to_account(money) - initialBal) / initialBal * 100
        
plot(buyAndHoldReturnPct(dateInput))
```

---

## strategy.convert_to_symbol()

Converts the value from the currency used by the strategy (strategy.account_currency) to the currency that the symbol on the chart is traded in (syminfo.currency).

### Syntax

```pine
strategy.convert_to_symbol(value) → series float
```

### Arguments

- `value` (*series int|float*) — The value to be converted.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.convert_to_symbol).*

### Code Example
```pine
//@version=6
strategy("`strategy.convert_to_symbol` Example", currency = currency.EUR)

// Calculate the max qty we can buy using current chart's currency.
calcContracts(accountMoney) =>
    math.floor(strategy.convert_to_symbol(accountMoney) / syminfo.pointvalue / close)

// Return max qty we can buy using 300 euros
qt = calcContracts(300)

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars using our custom qty.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long, qty = qt)
if bar_index % 20 == 0
    strategy.close("Long")
```

---

## strategy.default_entry_qty()

Calculates the default quantity, in units, of an entry order from strategy.entry or strategy.order if it were to fill at the specified fill_price value. The calculation depends on several strategy properties, including default_qty_type, default_qty_value, currency, and other parameters in the strategy function and their representation in the "Properties" tab of the strategy's settings.

### Syntax

```pine
strategy.default_entry_qty(fill_price) → series float
```

### Arguments

- `fill_price` (*series int/float*) — The fill price for which to calculate the default order quantity.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.default_entry_qty).*

### Remarks
This function does not consider open positions simulated by a strategy. For example, if a strategy script has an open position from a long order with a qty of 10 units, using the strategy.entry function to simulate a short order with a qty of 5 will prompt the script to sell 15 units to reverse the position. This function will still return 5 in such a case since it doesn't consider an open trade. This value represents the default calculated quantity of an order. Order placement commands can override the default value by explicitly passing a new qty value in the function call.

### Code Example
```pine
//@version=6
strategy("Supertrend Strategy", overlay = true, default_qty_type = strategy.percent_of_equity, default_qty_value = 15)

//@variable The length of the ATR calculation.
atrPeriod = input(10, "ATR Length")
//@variable The ATR multiplier.
factor = input.float(3.0, "Factor", step = 0.01)
//@variable The tick offset of the stop order.
stopOffsetInput = input.int(100, "Tick offset for entry stop")

// Get the direction of the SuperTrend.
[_, direction] = ta.supertrend(factor, atrPeriod)

if ta.change(direction) < 0
    //@variable The stop price of the entry order.
    stopPrice = close + syminfo.mintick * stopOffsetInput
    //@variable The expected default fill quantity at the `stopPrice`. This value may not reflect actual qty of the filled order, because fill price may be different.
    calculatedQty = strategy.default_entry_qty(stopPrice)
    strategy.entry("My Long Entry Id", strategy.long, stop = stopPrice)
    label.new(bar_index, stopPrice, str.format("Stop set at {0}\nExpected qty at {0}: {1}", math.round_to_mintick(stopPrice), calculatedQty))

if ta.change(direction) > 0
    strategy.close_all()
```

---

## strategy.entry()

Creates a new order to open or add to a position. If an unfilled order with the same id exists, a call to this command modifies that order.

### Syntax

```pine
strategy.entry(id, direction, qty, limit, stop, oca_name, oca_type, comment, alert_message, disable_alert) → void
```

### Arguments

- `id` (*series string*) — A required parameter. The order identifier. It is possible to cancel or modify an order by referencing its identifier.
- `direction` (*series strategy_direction*) — A required parameter. Market position direction: 'strategy.long' is for long, 'strategy.short' is for short.
- `qty` (*series int|float*, optional, default `na`) — An optional parameter. Number of contracts/shares/lots/units to trade. The default value is 'NaN'.
- `limit` (*series int|float*, optional, default `1`) — An optional parameter. Limit price of the order. If it is specified, the order type is either 'limit', or 'stop-limit'. 'NaN' should be specified for any other order type.
- `stop` (*series int|float*, optional, default `na`) — An optional parameter. Stop price of the order. If it is specified, the order type is either 'stop', or 'stop-limit'. 'NaN' should be specified for any other order type.
- `oca_name` (*series string*, optional, default `""`) — An optional parameter. Name of the OCA group the order belongs to. If the order should not belong to any particular OCA group, there should be an empty string.
- `oca_type` (*input string*, optional) — An optional parameter. Type of the OCA group. The allowed values are: [strategy.oca.none](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.oca.none) - the order should not belong to any particular OCA group; [strategy.oca.cancel](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.oca.cancel) - the order should belong to an OCA group, where as soon as an order is filled, all other orders of the same group are cancelled; [strategy.oca.reduce](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.oca.reduce) - the order should belong to an OCA group, where if X number of contracts of an order is filled, number of contracts for each other order of the same OCA group is decreased by X.
- `comment` (*series string*, optional) — An optional parameter. Additional notes on the order.
- `alert_message` (*series string*, optional) — An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box’s "Message" field.
- `disable_alert` (*series bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true) when the function creates an order, the strategy alert will not fire upon the execution of that order. The parameter accepts a 'series bool' argument, allowing users to control which orders will trigger alerts when they fill. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.entry).*

### Code Example
```pine
//@version=6
strategy("Market order strategy", overlay = true)

// Calculate a 14-bar and 28-bar moving average of `close` prices.
float sma14 = ta.sma(close, 14)
float sma28 = ta.sma(close, 28)

// Place a market order to close the short trade and enter a long position when `sma14` crosses over `sma28`.
if ta.crossover(sma14, sma28)
    strategy.entry("My Long Entry ID", strategy.long)

// Place a market order to close the long trade and enter a short position when `sma14` crosses under `sma28`.
if ta.crossunder(sma14, sma28)
    strategy.entry("My Short Entry ID", strategy.short)

//@version=6
strategy("Limit order strategy", overlay=true, margin_long=100, margin_short=100)

//@variable The distance from the `close` price for each limit order.
float limitOffsetInput = input.int(100, "Limit offset, in ticks", 1) * syminfo.mintick

//@function Draws a label and line at the specified `price` to visualize a limit order's level. 
drawLimit(float price, bool isLong) =>
    color col = isLong ? color.blue : color.red
    label.new(
         bar_index, price, (isLong ? "Long" : "Short") + " limit order created", 
         style = label.style_label_right, color = col, textcolor = color.white
     )
    line.new(bar_index, price, bar_index + 1, price, extend = extend.right, style = line.style_dashed, color = col)

//@function Stops the `l` line from extending further.
method stopExtend(line l) =>
    l.set_x2(bar_index)
    l.set_extend(extend.none)

// Initialize two `line` variables to reference limit line IDs.
var line longLimit  = na
var line shortLimit = na

// Calculate a 14-bar and 28-bar moving average of `close` prices.
float sma14 = ta.sma(close, 14)
float sma28 = ta.sma(close, 28)

if ta.crossover(sma14, sma28)
    // Cancel any unfilled sell orders with the specified ID.
    strategy.cancel("My Short Entry ID")
    //@variable The limit price level. Its value is `limitOffsetInput` ticks below the current `close`.
    float limitLevel = close - limitOffsetInput
    // Place a long limit order to close the short trade and enter a long position at the `limitLevel`.
    strategy.entry("My Long Entry ID", strategy.long, limit = limitLevel)
    // Make new drawings for the long limit and stop extending the `shortLimit` line.
    longLimit := drawLimit(limitLevel, isLong = true)
    shortLimit.stopExtend()
    
if ta.crossunder(sma14, sma28)
    // Cancel any unfilled buy orders with the specified ID.
    strategy.cancel("My Long Entry ID")
    //@variable The limit price level. Its value is `limitOffsetInput` ticks above the current `close`.
    float limitLevel = close + limitOffsetInput
    // Place a short limit order to close the long trade and enter a short position at the `limitLevel`.
    strategy.entry("My Short Entry ID", strategy.short, limit = limitLevel)
    // Make new drawings for the short limit and stop extending the `shortLimit` line.
    shortLimit := drawLimit(limitLevel, isLong = false)
    longLimit.stopExtend()
```

---

## strategy.exit()

Creates price-based orders to exit from an open position. If unfilled exit orders with the same id exist, calls to this command modify those orders. This command can generate more than one type of exit order, depending on the specified parameters. However, it does not create market orders. To exit from a position with a market order, use strategy.close or strategy.close_all.

### Syntax

```pine
strategy.exit(id, from_entry, qty, qty_percent, profit, limit, loss, stop, trail_price, trail_points, trail_offset, oca_name, comment, comment_profit, comment_loss, comment_trailing, alert_message, alert_profit, alert_loss, alert_trailing, disable_alert) → void
```

### Arguments

- `id` (*series string*) — A required parameter. The order identifier. It is possible to cancel or modify an order by referencing its identifier.
- `from_entry` (*series string*, optional) — An optional parameter. The identifier of a specific entry order to exit from it. To exit all entries an empty string should be used. The default values is empty string.
- `qty` (*series int|float*, optional) — An optional parameter. Number of contracts/shares/lots/units to exit a trade with. The default value is 'NaN'.
- `qty_percent` (*series int|float*, optional, default `100`) — Defines the percentage of (0-100) the position to close. Its priority is lower than that of the 'qty' parameter. Optional. The default is 100.
- `profit` (*series int|float*, optional) — An optional parameter. Profit target (specified in ticks). If it is specified, a limit order is placed to exit market position when the specified amount of profit (in ticks) is reached. The default value is 'NaN'.
- `limit` (*series int|float*, optional, default `na`) — An optional parameter. Profit target (requires a specific price). If it is specified, a limit order is placed to exit market position at the specified price (or better). Priority of the parameter 'limit' is higher than priority of the parameter 'profit' ('limit' is used instead of 'profit', if its value is not 'NaN'). The default value is 'NaN'.
- `loss` (*series int|float*, optional, default `na`) — An optional parameter. Stop loss (specified in ticks). If it is specified, a stop order is placed to exit market position when the specified amount of loss (in ticks) is reached. The default value is 'NaN'.
- `stop` (*series int|float*, optional, default `na`) — An optional parameter. Stop loss (requires a specific price). If it is specified, a stop order is placed to exit market position at the specified price (or worse). Priority of the parameter 'stop' is higher than priority of the parameter 'loss' ('stop' is used instead of 'loss', if its value is not 'NaN'). The default value is 'NaN'.
- `trail_price` (*series int|float*, optional, default `na`) — An optional parameter. Trailing stop activation level (requires a specific price). If it is specified, a trailing stop order will be placed when the specified price level is reached. The offset (in ticks) to determine initial price of the trailing stop order is specified in the 'trail_offset' parameter: X ticks lower than activation level to exit long position; X ticks higher than activation level to exit short position. The default value is 'NaN'.
- `trail_points` (*series int|float*, optional, default `na`) — An optional parameter. Trailing stop activation level (profit specified in ticks). If it is specified, a trailing stop order will be placed when the calculated price level (specified amount of profit) is reached. The offset (in ticks) to determine initial price of the trailing stop order is specified in the 'trail_offset' parameter: X ticks lower than activation level to exit long position; X ticks higher than activation level to exit short position. The default value is 'NaN'.
- `trail_offset` (*series int|float*, optional, default `na`) — An optional parameter. Trailing stop price (specified in ticks). The offset in ticks to determine initial price of the trailing stop order: X ticks lower than 'trail_price' or 'trail_points' to exit long position; X ticks higher than 'trail_price' or 'trail_points' to exit short position. The default value is 'NaN'.
- `oca_name` (*series string*, optional) — An optional parameter. Name of the OCA group (oca_type = [strategy.oca.reduce](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.oca.reduce)) the profit target, the stop loss / the trailing stop orders belong to. If the name is not specified, it will be generated automatically.
- `comment` (*series string*, optional, default `na`) — Additional notes on the order. If specified, displays near the order marker on the chart. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `comment_profit` (*series string*, optional, default `na`) — Additional notes on the order if the exit was triggered by crossing `profit` or `limit` specifically. If specified, supercedes the `comment` parameter and displays near the order marker on the chart. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `comment_loss` (*series string*, optional, default `na`) — Additional notes on the order if the exit was triggered by crossing `stop` or `loss` specifically. If specified, supercedes the `comment` parameter and displays near the order marker on the chart. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `comment_trailing` (*series string*, optional, default `na`) — Additional notes on the order if the exit was triggered by crossing `trail_offset` specifically. If specified, supercedes the `comment` parameter and displays near the order marker on the chart. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `alert_message` (*series string*, optional, default `na`) — Text that will replace the '{{strategy.order.alert_message}}' placeholder when one is used in the "Message" field of the "Create Alert" dialog. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `alert_profit` (*series string*, optional, default `na`) — Text that will replace the '{{strategy.order.alert_message}}' placeholder when one is used in the "Message" field of the "Create Alert" dialog. Only replaces the text if the exit was triggered by crossing `profit` or `limit` specifically. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `alert_loss` (*series string*, optional, default `na`) — Text that will replace the '{{strategy.order.alert_message}}' placeholder when one is used in the "Message" field of the "Create Alert" dialog. Only replaces the text if the exit was triggered by crossing `stop` or `loss` specifically. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `alert_trailing` (*series string*, optional, default `na`) — Text that will replace the '{{strategy.order.alert_message}}' placeholder when one is used in the "Message" field of the "Create Alert" dialog. Only replaces the text if the exit was triggered by crossing `trail_offset` specifically. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na).
- `disable_alert` (*series bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true) when the function creates an order, the strategy alert will not fire upon the execution of that order. The parameter accepts a 'series bool' argument, allowing users to control which orders will trigger alerts when they fill. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.exit).*

### Remarks
A single call to the strategy.exit command can generate exit orders for several entries in an open position, depending on the call's from_entry value. If the call does not include a from_entry argument, it creates exit orders for all open trades, even the ones opened after the call, until the position closes. See this section of our User Manual to learn more. When a position consists of several open trades, and the close_entries_rule in the strategy declaration statement is "FIFO" (default), the orders from a strategy.exit call exit from the position starting with the first open trade. This behavior applies even if the from_entry value is the entry ID of different open trades. However, in that case, the maximum size of the exit orders still depends on the trades opened by orders with the from_entry ID. For more information, see this section of our User Manual. If a strategy.exit call includes arguments for creating stop-loss and trailing stop orders, the command places only the order that is supposed to fill first, because both orders are of the "stop" type.

### Code Example
```pine
//@version=6
strategy("Exit bracket strategy", overlay = true)

// Inputs that define the profit and loss amount of each trade as a tick distance from the entry price.
int profitDistanceInput = input.int(100, "Profit distance, in ticks", 1)
int lossDistanceInput   = input.int(100, "Loss distance, in ticks", 1)

// Variables to track the take-profit and stop-loss price. 
var float takeProfit = na
var float stopLoss   = na

// Calculate a 14-bar and 28-bar moving average of `close` prices.
float sma14 = ta.sma(close, 14)
float sma28 = ta.sma(close, 28)

if ta.crossover(sma14, sma28) and strategy.opentrades == 0
    // Place a market order to enter a long position.
    strategy.entry("My Long Entry ID", strategy.long)
    // Place a take-profit and stop-loss order when the entry order fills. 
    strategy.exit("My Long Exit ID", "My Long Entry ID", profit = profitDistanceInput, loss = lossDistanceInput)

if ta.change(strategy.opentrades) == 1
    //@variable The long entry price.
    float entryPrice = strategy.opentrades.entry_price(0)
    // Update the `takeProfit` and `stopLoss` values.
    takeProfit := entryPrice + profitDistanceInput * syminfo.mintick
    stopLoss   := entryPrice - lossDistanceInput * syminfo.mintick

if ta.change(strategy.closedtrades) == 1
    // Reset the `takeProfit` and `stopLoss`.
    takeProfit := na
    stopLoss   := na

// Plot the `takeProfit` and `stopLoss`.
plot(takeProfit, "Take-profit level", color.green, 2, plot.style_linebr)
plot(stopLoss, "Stop-loss level", color.red, 2, plot.style_linebr)

//@version=6
strategy("Trailing stop strategy", overlay = true)

//@variable The distance required to activate the trailing stop.
float activationDistanceInput = input.int(100, "Trail activation distance, in ticks") * syminfo.mintick 
//@variable The number of ticks the trailing stop follows behind the price as it reaches new peaks. 
int trailDistanceInput = input.int(100, "Trail distance, in ticks")

//@function Draws a label and line at the specified `price` to visualize a trailing stop order's activation level. 
drawActivation(float price) =>
    label.new(
         bar_index, price, "Activation level", style = label.style_label_right, 
         color = color.gray, textcolor = color.white
     )
    line.new(
         bar_index, price, bar_index + 1, price, extend = extend.right, style = line.style_dashed, color = color.gray
     )

//@function Stops the `l` line from extending further.
method stopExtend(line l) =>
    l.set_x2(bar_index)
    l.set_extend(extend.none)

// The activation line, active trailing stop price, and active trailing stop flag. 
var line activationLine     = na
var float trailingStopPrice = na
var bool isActive           = false

if bar_index % 100 == 0 and strategy.opentrades == 0
    trailingStopPrice := na
    isActive          := false
    // Place a market order to enter a long position.
    strategy.entry("My Long Entry ID", strategy.long)
    //@variable The activation level's price. 
    float activationPrice = close + activationDistanceInput
    // Create a trailing stop order that activates the defined number of ticks above the entry price.
    strategy.exit(
         "My Long Exit ID", "My Long Entry ID", trail_price = activationPrice, trail_offset = trailDistanceInput,
         oca_name = "Exit"
     )
    // Create new drawings at the `activationPrice`.
    activationLine := drawActivation(activationPrice)

// Logic for trailing stop visualization. 
if strategy.opentrades == 1
    // Stop extending the `activationLine` when the stop activates.
    if not isActive and high > activationLine.get_price(bar_index)
        isActive := true
        activationLine.stopExtend()
    // Update the `trailingStopPrice` while the trailing stop is active. 
    if isActive
        float offsetPrice = high - trailDistanceInput * syminfo.mintick
        trailingStopPrice := math.max(nz(trailingStopPrice, offsetPrice), offsetPrice)

// Close the trade with a market order if the trailing stop does not activate before the next 300th bar. 
if not isActive and bar_index % 300 == 0
    strategy.close_all("Market close")

// Reset the `trailingStopPrice` and `isActive` flags when the trade closes, and stop extending the `activationLine`.
if ta.change(strategy.closedtrades) > 0
    if not isActive
        activationLine.stopExtend()
    trailingStopPrice := na
    isActive          := false

// Plot the `trailingStopPrice`.
plot(trailingStopPrice, "Trailing stop", color.red, 3, plot.style_linebr)
```

---

## strategy.opentrades.commission()

Returns the sum of entry and exit fees paid in the open trade, expressed in strategy.account_currency.

### Syntax

```pine
strategy.opentrades.commission(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.commission).*

### Code Example
```pine
// Calculates the gross profit or loss for the current open position.
//@version=6
strategy("`strategy.opentrades.commission` Example", commission_type = strategy.commission.percent, commission_value = 0.1)

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Calculate gross profit or loss for open positions only.
tradeOpenGrossPL() =>
    sumOpenGrossPL = 0.0
    for tradeNo = 0 to strategy.opentrades - 1
        sumOpenGrossPL += strategy.opentrades.profit(tradeNo) - strategy.opentrades.commission(tradeNo)
    result = sumOpenGrossPL
    
plot(tradeOpenGrossPL())
```

---

## strategy.opentrades.entry_bar_index()

Returns the bar_index of the open trade's entry.

### Syntax

```pine
strategy.opentrades.entry_bar_index(trade_num) → series int
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.entry_bar_index).*

### Code Example
```pine
// Wait 10 bars and then close the position.
//@version=6
strategy("`strategy.opentrades.entry_bar_index` Example")

barsSinceLastEntry() =>
    strategy.opentrades > 0 ? bar_index - strategy.opentrades.entry_bar_index(strategy.opentrades - 1) : na

// Enter a long position if there are no open positions.
if strategy.opentrades == 0
    strategy.entry("Long", strategy.long)

// Close the long position after 10 bars. 
if barsSinceLastEntry() >= 10
    strategy.close("Long")
```

---

## strategy.opentrades.entry_comment()

Returns the comment message of the open trade's entry, or
na if there is no entry with this trade_num.

### Syntax

```pine
strategy.opentrades.entry_comment(trade_num) → series string
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.entry_comment).*

### Code Example
```pine
//@version=6
strategy("`strategy.opentrades.entry_comment()` Example", overlay = true)

stopPrice = open * 1.01

longCondition = ta.crossover(ta.sma(close, 14), ta.sma(close, 28))

if (longCondition)
    strategy.entry("Long", strategy.long, stop = stopPrice, comment = str.tostring(stopPrice, "#.####"))

var testTable = table.new(position.top_right, 1, 3, color.orange, border_width = 1)

if barstate.islastconfirmedhistory or barstate.isrealtime
    table.cell(testTable, 0, 0, 'Last entry stats')
    table.cell(testTable, 0, 1, "Order stop price value: " + strategy.opentrades.entry_comment(strategy.opentrades - 1))
    table.cell(testTable, 0, 2, "Actual Entry Price: " + str.tostring(strategy.opentrades.entry_price(strategy.opentrades - 1)))
```

---

## strategy.opentrades.entry_id()

Returns the id of the open trade's entry.

### Syntax

```pine
strategy.opentrades.entry_id(trade_num) → series string
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.entry_id).*

### Returns
Returns the id of the open trade's entry.

### Remarks
The function returns na if trade_num is not in the range: 0 to strategy.opentrades-1.

### Code Example
```pine
//@version=6
strategy("`strategy.opentrades.entry_id` Example", overlay = true)

// We enter a long position when 14 period sma crosses over 28 period sma.
// We enter a short position when 14 period sma crosses under 28 period sma.
longCondition = ta.crossover(ta.sma(close, 14), ta.sma(close, 28))
shortCondition = ta.crossunder(ta.sma(close, 14), ta.sma(close, 28))

// Strategy calls to enter a long or short position when the corresponding condition is met.
if longCondition
    strategy.entry("Long entry at bar #" + str.tostring(bar_index), strategy.long)
if shortCondition
    strategy.entry("Short entry at bar #" + str.tostring(bar_index), strategy.short)

// Display ID of the latest open position.
if barstate.islastconfirmedhistory
    label.new(bar_index, high + (2 * ta.tr), "Last opened position is \n " + strategy.opentrades.entry_id(strategy.opentrades - 1))
```

---

## strategy.opentrades.entry_price()

Returns the price of the open trade's entry.

### Syntax

```pine
strategy.opentrades.entry_price(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.entry_price).*

### Code Example
```pine
//@version=6
strategy("strategy.opentrades.entry_price Example 1", overlay = true)

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if ta.crossover(close, ta.sma(close, 14))
    strategy.entry("Long", strategy.long)

// Return the entry price for the latest closed trade.
currEntryPrice = strategy.opentrades.entry_price(strategy.opentrades - 1)
currExitPrice = currEntryPrice * 1.05

if high >= currExitPrice
    strategy.close("Long")

plot(currEntryPrice, "Long entry price", style = plot.style_linebr)
plot(currExitPrice, "Long exit price", color.green, style = plot.style_linebr)

// Calculates the average price for the open position.
//@version=6
strategy("strategy.opentrades.entry_price Example 2", pyramiding = 2)

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Calculates the average price for the open position.
avgOpenPositionPrice() =>
    sumOpenPositionPrice = 0.0
    for tradeNo = 0 to strategy.opentrades - 1
        sumOpenPositionPrice += strategy.opentrades.entry_price(tradeNo) * strategy.opentrades.size(tradeNo) / strategy.position_size
    result = nz(sumOpenPositionPrice / strategy.opentrades)

plot(avgOpenPositionPrice())
```

---

## strategy.opentrades.entry_time()

Returns the UNIX time of the open trade's entry, expressed in milliseconds.

### Syntax

```pine
strategy.opentrades.entry_time(trade_num) → series int
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.entry_time).*

### Code Example
```pine
//@version=6
strategy("strategy.opentrades.entry_time Example")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Calculates duration in milliseconds since the last position was opened.
timeSinceLastEntry()=>
    strategy.opentrades > 0 ? (time - strategy.opentrades.entry_time(strategy.opentrades - 1)) : na

plot(timeSinceLastEntry() / 1000 * 60 * 60 * 24, "Days since last entry")
```

---

## strategy.opentrades.max_drawdown()

Returns the maximum drawdown of the open trade, i.e., the maximum possible loss during the trade, expressed in strategy.account_currency.

### Syntax

```pine
strategy.opentrades.max_drawdown(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.max_drawdown).*

### Remarks
The function returns na if trade_num is not in the range: 0 to strategy.closedtrades - 1.

### Code Example
```pine
//@version=6
strategy("strategy.opentrades.max_drawdown Example 1")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Plot the max drawdown of the latest open trade.
plot(strategy.opentrades.max_drawdown(strategy.opentrades - 1), "Max drawdown of the latest open trade")

// Calculates the max trade drawdown value for all open trades.
//@version=6
strategy("`strategy.opentrades.max_drawdown` Example 2", pyramiding = 100)

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Get the biggest max trade drawdown value from all of the open trades.
maxTradeDrawDown() =>
    maxDrawdown = 0.0
    for tradeNo = 0 to strategy.opentrades - 1
        maxDrawdown := math.max(maxDrawdown, strategy.opentrades.max_drawdown(tradeNo))
    result = maxDrawdown

plot(maxTradeDrawDown(), "Biggest max drawdown")
```

---

## strategy.opentrades.max_drawdown_percent()

Returns the maximum drawdown of the open trade, i.e., the maximum possible loss during the trade, expressed as a percentage and calculated by formula: Lowest Value During Trade / (Entry Price x Quantity) * 100.

---

### Syntax

```pine
strategy.opentrades.max_drawdown_percent(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.max_drawdown_percent).*

## strategy.opentrades.max_runup()

Returns the maximum run up of the open trade, i.e., the maximum possible profit during the trade, expressed in strategy.account_currency.

### Syntax

```pine
strategy.opentrades.max_runup(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.max_runup).*

### Code Example
```pine
//@version=6
strategy("strategy.opentrades.max_runup Example 1")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Plot the max runup of the latest open trade.
plot(strategy.opentrades.max_runup(strategy.opentrades - 1), "Max runup of the latest open trade")

// Calculates the max trade runup value for all open trades.
//@version=6
strategy("strategy.opentrades.max_runup Example 2", pyramiding = 100)

// Enter a long position every 30 bars.
if bar_index % 30 == 0
    strategy.entry("Long", strategy.long)

// Calculate biggest max trade runup value from all of the open trades.
maxOpenTradeRunUp() =>
    maxRunup = 0.0
    for tradeNo = 0 to strategy.opentrades - 1
        maxRunup := math.max(maxRunup, strategy.opentrades.max_runup(tradeNo))
    result = maxRunup

plot(maxOpenTradeRunUp(), "Biggest max runup of all open trades")
```

---

## strategy.opentrades.max_runup_percent()

Returns the maximum run-up of the open trade, i.e., the maximum possible profit during the trade, expressed as a percentage and calculated by formula: Highest Value During Trade / (Entry Price x Quantity) * 100.

---

### Syntax

```pine
strategy.opentrades.max_runup_percent(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.max_runup_percent).*

## strategy.opentrades.profit()

Returns the profit/loss of the open trade, expressed in strategy.account_currency. Losses are expressed as negative values.

### Syntax

```pine
strategy.opentrades.profit(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.profit).*

### Code Example
```pine
// Returns the profit of the last open trade.
//@version=6
strategy("`strategy.opentrades.profit` Example 1", commission_type = strategy.commission.percent, commission_value = 0.1)

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

plot(strategy.opentrades.profit(strategy.opentrades - 1), "Profit of the latest open trade")

// Calculates the profit for all open trades.
//@version=6
strategy("`strategy.opentrades.profit` Example 2", pyramiding = 5)

// Strategy calls to enter 5 long positions every 2 bars.
if bar_index % 2 == 0
    strategy.entry("Long", strategy.long, qty = 5)

// Calculate open profit or loss for the open positions.
tradeOpenPL() =>
    sumProfit = 0.0
    for tradeNo = 0 to strategy.opentrades - 1
        sumProfit += strategy.opentrades.profit(tradeNo)
    result = sumProfit
    
plot(tradeOpenPL(), "Profit of all open trades")
```

---

## strategy.opentrades.profit_percent()

Returns the profit/loss of the open trade, expressed as a percentage. Losses are expressed as negative values.

---

### Syntax

```pine
strategy.opentrades.profit_percent(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the closed trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.profit_percent).*

## strategy.opentrades.size()

Returns the direction and the number of contracts traded in the open trade. If the value is > 0, the market position was long. If the value is < 0, the market position was short.

### Syntax

```pine
strategy.opentrades.size(trade_num) → series float
```

### Arguments

- `trade_num` (*series int*) — The trade number of the open trade. The number of the first trade is zero.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.opentrades.size).*

### Code Example
```pine
//@version=6
strategy("`strategy.opentrades.size` Example 1")

// We calculate the max amt of shares we can buy.
amtShares = math.floor(strategy.equity / close)
// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long, qty = amtShares)
if bar_index % 20 == 0
    strategy.close("Long")

// Plot the number of contracts in the latest open trade.
plot(strategy.opentrades.size(strategy.opentrades - 1), "Amount of contracts in latest open trade")

// Calculates the average profit percentage for all open trades.
//@version=6
strategy("`strategy.opentrades.size` Example 2")

// Strategy calls to enter long trades every 15 bars and exit long trades every 20 bars.
if bar_index % 15 == 0
    strategy.entry("Long", strategy.long)
if bar_index % 20 == 0
    strategy.close("Long")

// Calculate profit for all open trades.
profitPct = 0.0
for tradeNo = 0 to strategy.opentrades - 1
    entryP = strategy.opentrades.entry_price(tradeNo)
    exitP = close
    profitPct += (exitP - entryP) / entryP * strategy.opentrades.size(tradeNo) * 100
    
// Calculate average profit percent for all open trades.
avgProfitPct = nz(profitPct / strategy.opentrades)
plot(avgProfitPct)
```

---

## strategy.order()

Creates a new order to open, add to, or exit from a position. If an unfilled order with the same id exists, a call to this command modifies that order.

### Syntax

```pine
strategy.order(id, direction, qty, limit, stop, oca_name, oca_type, comment, alert_message, disable_alert) → void
```

### Arguments

- `id` (*series string*) — A required parameter. The order identifier. It is possible to cancel or modify an order by referencing its identifier.
- `direction` (*series strategy_direction*) — A required parameter. Order direction: 'strategy.long' is for buy, 'strategy.short' is for sell.
- `qty` (*series int|float*, optional, default `1`) — An optional parameter. Number of contracts/shares/lots/units to trade. The default value is 'NaN'.
- `limit` (*series int|float*, optional) — An optional parameter. Limit price of the order. If it is specified, the order type is either 'limit', or 'stop-limit'. 'NaN' should be specified for any other order type.
- `stop` (*series int|float*, optional) — An optional parameter. Stop price of the order. If it is specified, the order type is either 'stop', or 'stop-limit'. 'NaN' should be specified for any other order type.
- `oca_name` (*series string*, optional) — An optional parameter. Name of the OCA group the order belongs to. If the order should not belong to any particular OCA group, there should be an empty string.
- `oca_type` (*input string*, optional) — An optional parameter. Type of the OCA group. The allowed values are: [strategy.oca.none](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.oca.none) - the order should not belong to any particular OCA group; [strategy.oca.cancel](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.oca.cancel) - the order should belong to an OCA group, where as soon as an order is filled, all other orders of the same group are cancelled; [strategy.oca.reduce](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.oca.reduce) - the order should belong to an OCA group, where if X number of contracts of an order is filled, number of contracts for each other order of the same OCA group is decreased by X.
- `comment` (*series string*, optional) — An optional parameter. Additional notes on the order.
- `alert_message` (*series string*, optional) — An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box’s "Message" field.
- `disable_alert` (*series bool*, optional, default `false`) — If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true) when the function creates an order, the strategy alert will not fire upon the execution of that order. The parameter accepts a 'series bool' argument, allowing users to control which orders will trigger alerts when they fill. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.order).*

### Code Example
```pine
//@version=6
strategy("Market order strategy", overlay = true)

// Calculate a 14-bar and 28-bar moving average of `close` prices.
float sma14 = ta.sma(close, 14)
float sma28 = ta.sma(close, 28)

// Place a market order to enter a long position when `sma14` crosses over `sma28`.
if ta.crossover(sma14, sma28) and strategy.position_size == 0
    strategy.order("My Long Entry ID", strategy.long)

// Place a market order to sell the same quantity as the long trade when `sma14` crosses under `sma28`, 
// effectively closing the long position.
if ta.crossunder(sma14, sma28) and strategy.position_size > 0
    strategy.order("My Long Exit ID", strategy.short)

//@version=6
strategy("Limit and stop exit strategy", overlay = true)

//@variable The distance from the long entry price for each short limit order.
float shortOffsetInput = input.int(200, "Sell limit/stop offset, in ticks", 1) * syminfo.mintick

//@function Draws a label and line at the specified `price` to visualize a limit order's level. 
drawLimit(float price, bool isLong, bool isStop = false) =>
    color col = isLong ? color.blue : color.red
    label.new(
         bar_index, price, (isLong ? "Long " : "Short ") + (isStop ? "stop" : "limit") + " order created", 
         style = label.style_label_right, color = col, textcolor = color.white
     )
    line.new(bar_index, price, bar_index + 1, price, extend = extend.right, style = line.style_dashed, color = col)

//@function Stops the `l` line from extending further.
method stopExtend(line l) =>
    l.set_x2(bar_index)
    l.set_extend(extend.none)

// Initialize two `line` variables to reference limit and stop line IDs.
var line profitLimit = na
var line lossStop    = na

// Calculate a 14-bar and 28-bar moving average of `close` prices.
float sma14 = ta.sma(close, 14)
float sma28 = ta.sma(close, 28)

if ta.crossover(sma14, sma28) and strategy.position_size == 0
    // Place a market order to enter a long position.
    strategy.order("My Long Entry ID", strategy.long)
    
if strategy.position_size > 0 and strategy.position_size[1] == 0
    //@variable The entry price of the long trade. 
    float entryPrice = strategy.opentrades.entry_price(0)
    // Calculate short limit and stop levels above and below the `entryPrice`.
    float profitLevel = entryPrice + shortOffsetInput
    float lossLevel   = entryPrice - shortOffsetInput
    // Place short limit and stop orders at the `profitLevel` and `lossLevel`. 
    strategy.order("Profit", strategy.short, limit = profitLevel, oca_name = "Bracket", oca_type = strategy.oca.cancel)
    strategy.order("Loss", strategy.short, stop = lossLevel, oca_name = "Bracket", oca_type = strategy.oca.cancel)
    // Make new drawings for the `profitLimit` and `lossStop` lines.
    profitLimit := drawLimit(profitLevel, isLong = false)
    lossStop    := drawLimit(lossLevel, isLong = false, isStop = true)

if ta.change(strategy.closedtrades) > 0
    // Stop extending the `profitLimit` and `lossStop` lines.
    profitLimit.stopExtend()
    lossStop.stopExtend()
```

---

## strategy.risk.allow_entry_in()

This function can be used to specify in which market direction the strategy.entry function is allowed to open positions.

### Syntax

```pine
strategy.risk.allow_entry_in(value) → void
```

### Arguments

- `value` (*simple string*) — The allowed direction. Possible values: [strategy.direction.all](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.direction.all), [strategy.direction.long](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.direction.long), [strategy.direction.short](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.direction.short)

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.risk.allow_entry_in).*

### Code Example
```pine
//@version=6
strategy("strategy.risk.allow_entry_in")

strategy.risk.allow_entry_in(strategy.direction.long)
if open > close
    strategy.entry("Long", strategy.long)
// Instead of opening a short position with 10 contracts, this command will close long entries.
if open < close
    strategy.entry("Short", strategy.short, qty = 10)
```

---

## strategy.risk.max_cons_loss_days()

The purpose of this rule is to cancel all pending orders, close all open positions and stop placing orders after a specified number of consecutive days with losses. The rule affects the whole strategy.

### Syntax

```pine
strategy.risk.max_cons_loss_days(count, alert_message) → void
```

### Arguments

- `count` (*simple int*) — A required parameter. The allowed number of consecutive days with losses.
- `alert_message` (*simple string*, optional) — An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box’s "Message" field.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.risk.max_cons_loss_days).*

### Code Example
```pine
//@version=6
strategy("risk.max_cons_loss_days Demo 1")
strategy.risk.max_cons_loss_days(3) // No orders will be placed after 3 days, if each day is with loss.
plot(strategy.position_size)
```

---

## strategy.risk.max_drawdown()

The purpose of this rule is to determine maximum drawdown. The rule affects the whole strategy. Once the maximum drawdown value is reached, all pending orders are cancelled, all open positions are closed and no new orders can be placed.

### Syntax

```pine
strategy.risk.max_drawdown(value, type, alert_message) → void
```

### Arguments

- `value` (*simple int|float*) — A required parameter. The maximum drawdown value. It is specified either in money (base currency), or in percentage of maximum equity. For % of equity the range of allowed values is from 0 to 100.
- `displayType` (*simple string*) — A required parameter. The type of the value. Please specify one of the following values: [strategy.percent_of_equity](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.percent_of_equity) or [strategy.cash](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.cash). Note: if equity drops down to zero or to a negative and the 'strategy.percent_of_equity' is specified, all pending orders are cancelled, all open positions are closed and no new orders can be placed for good.
- `alert_message` (*simple string*, optional) — An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box’s "Message" field.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.risk.max_drawdown).*

### Code Example
```pine
//@version=6
strategy("risk.max_drawdown Demo 1")
strategy.risk.max_drawdown(50, strategy.percent_of_equity) // set maximum drawdown to 50% of maximum equity
plot(strategy.position_size)

//@version=6
strategy("risk.max_drawdown Demo 2", currency = "EUR")
strategy.risk.max_drawdown(2000, strategy.cash) // set maximum drawdown to 2000 EUR from maximum equity
plot(strategy.position_size)
```

---

## strategy.risk.max_intraday_filled_orders()

The purpose of this rule is to determine maximum number of filled orders per 1 day (per 1 bar, if chart resolution is higher than 1 day). The rule affects the whole strategy. Once the maximum number of filled orders is reached, all pending orders are cancelled, all open positions are closed and no new orders can be placed till the end of the current trading session.

### Syntax

```pine
strategy.risk.max_intraday_filled_orders(count, alert_message) → void
```

### Arguments

- `count` (*simple int*) — A required parameter. The maximum number of filled orders per 1 day.
- `alert_message` (*simple string*, optional) — An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box’s "Message" field.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.risk.max_intraday_filled_orders).*

### Code Example
```pine
//@version=6
strategy("risk.max_intraday_filled_orders Demo")
strategy.risk.max_intraday_filled_orders(10) // After 10 orders are filled, no more strategy orders will be placed (except for a market order to exit current open market position, if there is any).
if open > close
    strategy.entry("buy", strategy.long)
if open < close
    strategy.entry("sell", strategy.short)
```

---

## strategy.risk.max_intraday_loss()

The maximum loss value allowed during a day. It is specified either in money (base currency), or in percentage of maximum intraday equity (0 -100).

### Syntax

```pine
strategy.risk.max_intraday_loss(value, type, alert_message) → void
```

### Arguments

- `value` (*simple int|float*) — A required parameter. The maximum loss value. It is specified either in money (base currency), or in percentage of maximum intraday equity. For % of equity the range of allowed values is from 0 to 100.
- `displayType` (*simple string*) — A required parameter. The type of the value. Please specify one of the following values: [strategy.percent_of_equity](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.percent_of_equity) or [strategy.cash](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.cash). Note: if equity drops down to zero or to a negative and the [strategy.percent_of_equity](https://www.tradingview.com/pine-script-reference/v6/#var_strategy.percent_of_equity) is specified, all pending orders are cancelled, all open positions are closed and no new orders can be placed for good.
- `alert_message` (*simple string*, optional) — An optional parameter which replaces the {{strategy.order.alert_message}} placeholder when it is used in the "Create Alert" dialog box’s "Message" field.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.risk.max_intraday_loss).*

### Code Example
```pine
// Sets the maximum intraday loss using the strategy's equity value.
//@version=6
strategy("strategy.risk.max_intraday_loss Example 1", overlay = false, default_qty_type = strategy.percent_of_equity, default_qty_value = 100)

// Input for maximum intraday loss %. 
lossPct = input.float(10)

// Set maximum intraday loss to our lossPct input
strategy.risk.max_intraday_loss(lossPct, strategy.percent_of_equity)

// Enter Short at bar_index zero.
if bar_index == 0
    strategy.entry("Short", strategy.short)

// Store equity value from the beginning of the day
eqFromDayStart = ta.valuewhen(ta.change(dayofweek) > 0, strategy.equity, 0)

// Calculate change of the current equity from the beginning of the current day.
eqChgPct = 100 * ((strategy.equity - eqFromDayStart) / strategy.equity)

// Plot it
plot(eqChgPct) 
hline(-lossPct)

// Sets the maximum intraday loss using the strategy's cash value.
//@version=6
strategy("strategy.risk.max_intraday_loss Example 2", overlay = false)

// Input for maximum intraday loss in absolute cash value of the symbol. 
absCashLoss = input.float(5)

// Set maximum intraday loss to `absCashLoss` in account currency.
strategy.risk.max_intraday_loss(absCashLoss, strategy.cash)

// Enter Short at bar_index zero.
if bar_index == 0
    strategy.entry("Short", strategy.short)

// Store the open price value from the beginning of the day.
beginPrice = ta.valuewhen(ta.change(dayofweek) > 0, open, 0)

// Calculate the absolute price change for the current period.
priceChg = (close - beginPrice)

hline(absCashLoss)
plot(priceChg)
```

---

## strategy.risk.max_position_size()

The purpose of this rule is to determine maximum size of a market position. The rule affects the following function: strategy.entry. The 'entry' quantity can be reduced (if needed) to such number of contracts/shares/lots/units, so the total position size doesn't exceed the value specified in 'strategy.risk.max_position_size'. If minimum possible quantity still violates the rule, the order will not be placed.

### Syntax

```pine
strategy.risk.max_position_size(contracts) → void
```

### Arguments

- `contracts` (*simple int|float*) — A required parameter. Maximum number of contracts/shares/lots/units in a position.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_strategy.risk.max_position_size).*

### Code Example
```pine
//@version=6
strategy("risk.max_position_size Demo", default_qty_value = 100)
strategy.risk.max_position_size(10)
if open > close
    strategy.entry("buy", strategy.long)
plot(strategy.position_size) // max plot value will be 10
```

---

## string()

Casts na to string

### Syntax

```pine
string
string(x) → series string
```

### Arguments

- `x` (*series color*) — 'na' to cast to string.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_string).*

### Returns
The value of the argument after casting to string.

---

## syminfo.prefix()

Returns exchange prefix of the symbol, e.g. "NASDAQ".

### Syntax

```pine
syminfo.prefix(symbol) → series string
```

### Arguments

- `symbol` (*series string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL".

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_syminfo.prefix).*

### Returns
Returns exchange prefix of the symbol, e.g. "NASDAQ".

### Remarks
The result of the function is used in the ticker.new/ticker.modify and request.security.

### Code Example
```pine
//@version=6
indicator("syminfo.prefix fun", overlay=true)
i_sym = input.symbol("NASDAQ:AAPL")
pref = syminfo.prefix(i_sym)
tick = syminfo.ticker(i_sym)
t = ticker.new(pref, tick, session.extended)
s = request.security(t, "1D", close)
plot(s)
```

---

## syminfo.ticker()

Returns symbol name without exchange prefix, e.g. "AAPL".

### Syntax

```pine
syminfo.ticker(symbol) → series string
```

### Arguments

- `symbol` (*series string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL".

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_syminfo.ticker).*

### Returns
Returns symbol name without exchange prefix, e.g. "AAPL".

### Remarks
The result of the function is used in the ticker.new/ticker.modify and request.security.

### Code Example
```pine
//@version=6
indicator("syminfo.ticker fun", overlay=true) 
i_sym = input.symbol("NASDAQ:AAPL")
pref = syminfo.prefix(i_sym)
tick = syminfo.ticker(i_sym)
t = ticker.new(pref, tick, session.extended)
s = request.security(t, "1D", close)
plot(s)
```

---

## ta.alma()

Arnaud Legoux Moving Average. It uses Gaussian distribution as weights for moving average.

### Syntax

```pine
ta.alma(series, length, offset, sigma, floor) → series float
```

### Arguments

- `series` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).
- `offset` (*simple int|float*) — Controls tradeoff between smoothness (closer to 1) and responsiveness (closer to 0).
- `sigma` (*simple int|float*) — Changes the smoothness of ALMA. The larger sigma the smoother ALMA.
- `floor` (*simple bool*, default `false`) — An optional parameter. Specifies whether the offset calculation is floored before ALMA is calculated. Default value is false.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.alma).*

### Returns
Arnaud Legoux Moving Average.

### Remarks
na values in the source series are included in calculations and will produce an na result.

### Code Example
```pine
//@version=6
indicator("ta.alma", overlay=true) 
plot(ta.alma(close, 9, 0.85, 6))

// same on pine, but much less efficient
pine_alma(series, windowsize, offset, sigma) =>
    m = offset * (windowsize - 1)
    //m = math.floor(offset * (windowsize - 1)) // Used as m when math.floor=true
    s = windowsize / sigma
    norm = 0.0
    sum = 0.0
    for i = 0 to windowsize - 1
        weight = math.exp(-1 * math.pow(i - m, 2) / (2 * math.pow(s, 2)))
        norm := norm + weight
        sum := sum + series[windowsize - i - 1] * weight
    sum / norm
plot(pine_alma(close, 9, 0.85, 6))
```

---

## ta.atr()

Function atr (average true range) returns the RMA of true range. True range is max(high - low, abs(high - close[1]), abs(low - close[1])).

### Syntax

```pine
ta.atr(length) → series float
```

### Arguments

- `length` (*simple int*) — Length (number of bars back).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.atr).*

### Returns
Average true range.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.atr")
plot(ta.atr(14))

//the same on pine
pine_atr(length) =>
    trueRange = na(high[1])? high-low : math.max(math.max(high - low, math.abs(high - close[1])), math.abs(low - close[1]))
    //true range can be also calculated with ta.tr(true)
    ta.rma(trueRange, length)

plot(pine_atr(14))
```

---

## ta.barssince()

Counts the number of bars since the last time the condition was true.

### Syntax

```pine
ta.barssince(condition) → series int
```

### Arguments

- `condition` (*series bool*) — The condition to search for.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.barssince).*

### Returns
Number of bars since condition was true.

### Remarks
If the condition has never been met prior to the current bar, the function returns na. Please note that using this variable/function can cause indicator repainting.

### Code Example
```pine
//@version=6
indicator("ta.barssince")
// get number of bars since last color.green bar
plot(ta.barssince(close >= open))
```

---

## ta.bb()

Bollinger Bands. A Bollinger Band is a technical analysis tool defined by a set of lines plotted two standard deviations (positively and negatively) away from a simple moving average (SMA) of the security's price, but can be adjusted to user preferences.

### Syntax

```pine
ta.bb(series, length, mult) → [series float, series float, series float]
```

### Arguments

- `series` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).
- `mult` (*simple int|float*) — Standard deviation factor.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.bb).*

### Returns
Bollinger Bands.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.bb")

[middle, upper, lower] = ta.bb(close, 5, 4)
plot(middle, color=color.yellow)
plot(upper, color=color.yellow)
plot(lower, color=color.yellow)

// the same on pine
f_bb(src, length, mult) =>
    float basis = ta.sma(src, length)
    float dev = mult * ta.stdev(src, length)
    [basis, basis + dev, basis - dev]

[pineMiddle, pineUpper, pineLower] = f_bb(close, 5, 4)

plot(pineMiddle)
plot(pineUpper)
plot(pineLower)
```

---

## ta.bbw()

Bollinger Bands Width. The Bollinger Band Width is the difference between the upper and the lower Bollinger Bands divided by the middle band.

### Syntax

```pine
ta.bbw(series, length, mult) → series float
```

### Arguments

- `series` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).
- `mult` (*simple int|float*) — Standard deviation factor.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.bbw).*

### Returns
Bollinger Bands Width.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.bbw")

plot(ta.bbw(close, 5, 4), color=color.yellow)

// the same on pine
f_bbw(src, length, mult) =>
    float basis = ta.sma(src, length)
    float dev = mult * ta.stdev(src, length)
    (((basis + dev) - (basis - dev)) / basis) * 100

plot(f_bbw(close, 5, 4))
```

---

## ta.cci()

The CCI (commodity channel index) is calculated as the difference between the typical price of a commodity and its simple moving average, divided by the mean absolute deviation of the typical price. The index is scaled by an inverse factor of 0.015 to provide more readable numbers.

### Syntax

```pine
ta.cci(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.cci).*

### Returns
Commodity channel index of source for length bars back.

### Remarks
na values in the source series are ignored.

---

## ta.change()

Compares the current source value to its value length bars ago and returns the difference.

### Syntax

```pine
ta.change(source) → float|bool|int|float
ta.change(source, length) → bool|int
```

### Arguments

- `source` (*series int|float|bool*) — Source series.
- `length` (*series int*, default `1`) — How far the past `source` value is offset from the current one, in bars. Optional. The default is 1.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.change).*

### Returns
The difference between the values when they are numerical. When a 'bool' source is used, returns true when the current source is different from the previous source.

### Remarks
na values in the source series are included in calculations and will produce an na result.

### Code Example
```pine
//@version=6
indicator('Day and Direction Change', overlay = true)
dailyBarTime = time('1D')
isNewDay = ta.change(dailyBarTime) != 0
bgcolor(isNewDay ? color.new(color.green, 80) : na)

isGreenBar = close >= open
colorChange = ta.change(isGreenBar)
plotshape(colorChange, 'Direction Change')
```

---

## ta.cmo()

Chande Momentum Oscillator. Calculates the difference between the sum of recent gains and the sum of recent losses and then divides the result by the sum of all price movement over the same period.

### Syntax

```pine
ta.cmo(series, length) → series float
```

### Arguments

- `series` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.cmo).*

### Returns
Chande Momentum Oscillator.

### Remarks
na values in the source series are ignored.

### Code Example
```pine
//@version=6
indicator("ta.cmo")
plot(ta.cmo(close, 5), color=color.yellow)

// the same on pine
f_cmo(src, length) =>
    float mom = ta.change(src)
    float sm1 = math.sum((mom >= 0) ? mom : 0.0, length)
    float sm2 = math.sum((mom >= 0) ? 0.0 : -mom, length)
    100 * (sm1 - sm2) / (sm1 + sm2)

plot(f_cmo(close, 5))
```

---

## ta.cog()

The cog (center of gravity) is an indicator based on statistics and the Fibonacci golden ratio.

### Syntax

```pine
ta.cog(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.cog).*

### Returns
Center of Gravity.

### Remarks
na values in the source series are ignored.

### Code Example
```pine
//@version=6
indicator("ta.cog", overlay=true) 
plot(ta.cog(close, 10))

// the same on pine
pine_cog(source, length) =>
    sum = math.sum(source, length)
    num = 0.0
    for i = 0 to length - 1
        price = source[i]
        num := num + price * (i + 1)
    -num / sum

plot(pine_cog(close, 10))
```

---

## ta.correlation()

Correlation coefficient. Describes the degree to which two series tend to deviate from their ta.sma values.

### Syntax

```pine
ta.correlation(source1, source2, length) → series float
```

### Arguments

- `source1` (*series int|float*) — Source series.
- `source2` (*series int|float*) — Target series.
- `length` (*series int*) — Length (number of bars back).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.correlation).*

### Returns
Correlation coefficient.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

---

## ta.cross()

### Syntax

```pine
ta.cross(source1, source2) → series bool
```

### Arguments

- `source1` (*series int|float*) — First data series.
- `source2` (*series int|float*) — Second data series.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.cross).*

### Returns
true if two series have crossed each other, otherwise false.

---

## ta.crossover()

The source1-series is defined as having crossed over source2-series if, on the current bar, the value of source1 is greater than the value of source2, and on the previous bar, the value of source1 was less than or equal to the value of source2.

### Syntax

```pine
ta.crossover(source1, source2) → series bool
```

### Arguments

- `source1` (*series int|float*) — First data series.
- `source2` (*series int|float*) — Second data series.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.crossover).*

### Returns
true if source1 crossed over source2 otherwise false.

---

## ta.crossunder()

The source1-series is defined as having crossed under source2-series if, on the current bar, the value of source1 is less than the value of source2, and on the previous bar, the value of source1 was greater than or equal to the value of source2.

### Syntax

```pine
ta.crossunder(source1, source2) → series bool
```

### Arguments

- `source1` (*series int|float*) — First data series.
- `source2` (*series int|float*) — Second data series.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.crossunder).*

### Returns
true if source1 crossed under source2 otherwise false.

---

## ta.cum()

Cumulative (total) sum of source. In other words it's a sum of all elements of source.

### Syntax

```pine
ta.cum(source) → series float
```

### Arguments

- `source` (*series int|float*) — Source used for the calculation.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.cum).*

### Returns
Total sum series.

---

## ta.dev()

Measure of difference between the series and it's ta.sma

### Syntax

```pine
ta.dev(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.dev).*

### Returns
Deviation of source for length bars back.

### Remarks
na values in the source series are ignored.

### Code Example
```pine
//@version=6
indicator("ta.dev")
plot(ta.dev(close, 10))

// the same on pine
pine_dev(source, length) =>
    mean = ta.sma(source, length)
    sum = 0.0
    for i = 0 to length - 1
        val = source[i]
        sum := sum + math.abs(val - mean)
    dev = sum/length
plot(pine_dev(close, 10))
```

---

## ta.dmi()

The dmi function returns the directional movement index.

### Syntax

```pine
ta.dmi(diLength, adxSmoothing) → [series float, series float, series float]
```

### Arguments

- `diLength` (*simple int*) — DI Period.
- `adxSmoothing` (*simple int*) — ADX Smoothing Period.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.dmi).*

### Returns
Tuple of three DMI series: Positive Directional Movement (+DI), Negative Directional Movement (-DI) and Average Directional Movement Index (ADX).

### Code Example
```pine
//@version=6
indicator(title="Directional Movement Index", shorttitle="DMI", format=format.price, precision=4)
len = input.int(17, minval=1, title="DI Length")
lensig = input.int(14, title="ADX Smoothing", minval=1)
[diplus, diminus, adx] = ta.dmi(len, lensig)
plot(adx, color=color.red, title="ADX")
plot(diplus, color=color.blue, title="+DI")
plot(diminus, color=color.orange, title="-DI")
```

---

## ta.ema()

The ema function returns the exponentially weighted moving average. In ema weighting factors decrease exponentially. It calculates by using a formula: EMA = alpha * source + (1 - alpha) * EMA[1], where alpha = 2 / (length + 1).

### Syntax

```pine
ta.ema(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*simple int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.ema).*

### Returns
Exponential moving average of source with alpha = 2 / (length + 1).

### Remarks
Please note that using this variable/function can cause indicator repainting. na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.ema")
plot(ta.ema(close, 15))

//the same on pine
pine_ema(src, length) =>
    alpha = 2 / (length + 1)
    sum = 0.0
    sum := na(sum[1]) ? src : alpha * src + (1 - alpha) * nz(sum[1])
plot(pine_ema(close,15))
```

---

## ta.falling()

Test if the source series is now falling for length bars long.

### Syntax

```pine
ta.falling(source, length) → series bool
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.falling).*

### Returns
true if current source value is less than any previous source value for length bars back, false otherwise.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

---

## ta.highest()

Highest value for a given number of bars back.

### Syntax

```pine
ta.highest(source, length) → series float
```

### Arguments

- `source` (*series int|float*, default `high`) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.highest).*

### Returns
Highest value in the series.

### Remarks
Two args version: source is a series and length is the number of bars back. One arg version: length is the number of bars back. Algorithm uses high as a source series. na values in the source series are ignored.

---

## ta.highestbars()

Highest value offset for a given number of bars back.

### Syntax

```pine
ta.highestbars(source, length) → series int
ta.highestbars(length) → series int
```

### Arguments

- `source` (*series int|float*, default `high`) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.highestbars).*

### Returns
Offset to the highest bar.

### Remarks
Two args version: source is a series and length is the number of bars back. One arg version: length is the number of bars back. Algorithm uses high as a source series. na values in the source series are ignored.

---

## ta.hma()

The hma function returns the Hull Moving Average.

### Syntax

```pine
ta.hma(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*simple int*) — Number of bars.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.hma).*

### Returns
Hull moving average of 'source' for 'length' bars back.

### Remarks
na values in the source series are ignored.

### Code Example
```pine
//@version=6
indicator("Hull Moving Average")
src = input(defval=close, title="Source")
length = input(defval=9, title="Length")
hmaBuildIn = ta.hma(src, length)
plot(hmaBuildIn, title="Hull MA", color=#674EA7)
```

---

## ta.kc()

Keltner Channels. Keltner channel is a technical analysis indicator showing a central moving average line plus channel lines at a distance above and below.

### Syntax

```pine
ta.kc(series, length, mult, useTrueRange) → [series float, series float, series float]
```

### Arguments

- `series` (*series int|float*) — Series of values to process.
- `length` (*simple int*) — Number of bars (length).
- `mult` (*simple int|float*) — Standard deviation factor.
- `useTrueRange` (*simple bool*, default `true`) — An optional parameter. Specifies if True Range is used; default is true. If the value is false, the range will be calculated with the expression (high - low).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.kc).*

### Returns
Keltner Channels.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.kc")

[middle, upper, lower] = ta.kc(close, 5, 4)
plot(middle, color=color.yellow)
plot(upper, color=color.yellow)
plot(lower, color=color.yellow)

// the same on pine
f_kc(src, length, mult, useTrueRange) =>
    float basis = ta.ema(src, length)
    float span = (useTrueRange) ? ta.tr : (high - low)
    float rangeEma = ta.ema(span, length)
    [basis, basis + rangeEma * mult, basis - rangeEma * mult]
    
[pineMiddle, pineUpper, pineLower] = f_kc(close, 5, 4, true)

plot(pineMiddle)
plot(pineUpper)
plot(pineLower)
```

---

## ta.kcw()

Keltner Channels Width. The Keltner Channels Width is the difference between the upper and the lower Keltner Channels divided by the middle channel.

### Syntax

```pine
ta.kcw(series, length, mult, useTrueRange) → series float
```

### Arguments

- `series` (*series int|float*) — Series of values to process.
- `length` (*simple int*) — Number of bars (length).
- `mult` (*simple int|float*) — Standard deviation factor.
- `useTrueRange` (*simple bool*, default `false`) — An optional parameter. Specifies if True Range is used; default is true. If the value is false, the range will be calculated with the expression (high - low).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.kcw).*

### Returns
Keltner Channels Width.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.kcw")

plot(ta.kcw(close, 5, 4), color=color.yellow)

// the same on pine
f_kcw(src, length, mult, useTrueRange) =>
    float basis = ta.ema(src, length)
    float span = (useTrueRange) ? ta.tr : (high - low)
    float rangeEma = ta.ema(span, length)
    
    ((basis + rangeEma * mult) - (basis - rangeEma * mult)) / basis

plot(f_kcw(close, 5, 4, true))
```

---

## ta.linreg()

Linear regression curve. A line that best fits the prices specified over a user-defined time period. It is calculated using the least squares method. The result of this function is calculated using the formula: linreg = intercept + slope * (length - 1 - offset), where intercept and slope are the values calculated with the least squares method on source series.

### Syntax

```pine
ta.linreg(source, length, offset) → series float
```

### Arguments

- `source` (*series int|float*) — Source series.
- `length` (*series int*) — Number of bars (length).
- `offset` (*simple int*) — Offset.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.linreg).*

### Returns
Linear regression curve.

### Remarks
na values in the source series are included in calculations and will produce an na result.

---

## ta.lowest()

Lowest value for a given number of bars back.

### Syntax

```pine
ta.lowest(source, length) → series float
ta.lowest(length) → series float
```

### Arguments

- `source` (*series int|float*, default `low`) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.lowest).*

### Returns
Lowest value in the series.

### Remarks
Two args version: source is a series and length is the number of bars back. One arg version: length is the number of bars back. Algorithm uses low as a source series. na values in the source series are ignored.

---

## ta.lowestbars()

Lowest value offset for a given number of bars back.

### Syntax

```pine
ta.lowestbars(source, length) → series int
ta.lowestbars(length) → series int
```

### Arguments

- `source` (*series int|float*, default `low`) — Series of values to process.
- `length` (*series int*) — Number of bars back.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.lowestbars).*

### Returns
Offset to the lowest bar.

### Remarks
Two args version: source is a series and length is the number of bars back. One arg version: length is the number of bars back. Algorithm uses low as a source series. na values in the source series are ignored.

---

## ta.macd()

MACD (moving average convergence/divergence). It is supposed to reveal changes in the strength, direction, momentum, and duration of a trend in a stock's price.

### Syntax

```pine
ta.macd(source, fastlen, slowlen, siglen) → [series float, series float, series float]
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `fastlen` (*simple int*) — Fast Length parameter.
- `slowlen` (*simple int*) — Slow Length parameter.
- `siglen` (*simple int*) — Signal Length parameter.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.macd).*

### Returns
Tuple of three MACD series: MACD line, signal line and histogram line.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("MACD")
[macdLine, signalLine, histLine] = ta.macd(close, 12, 26, 9)
plot(macdLine, color=color.blue)
plot(signalLine, color=color.orange)
plot(histLine, color=color.red, style=plot.style_histogram)

//@version=6
indicator("MACD")
[_, signalLine, _] = ta.macd(close, 12, 26, 9)
plot(signalLine, color=color.orange)
```

---

## ta.max()

Returns the all-time high value of source from the beginning of the chart up to the current bar.

### Syntax

```pine
ta.max(source) → series float
```

### Arguments

- `source` (*series int|float*) — Source used for the calculation.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.max).*

### Remarks
na occurrences of source are ignored.

---

## ta.median()

Returns the median of the series.

### Syntax

```pine
ta.median(source, length) → series float|int
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.median).*

### Returns
The median of the series.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

---

## ta.mfi()

Money Flow Index. The Money Flow Index (MFI) is a technical oscillator that uses price and volume for identifying overbought or oversold conditions in an asset.

### Syntax

```pine
ta.mfi(series, length) → series float
```

### Arguments

- `series` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.mfi).*

### Returns
Money Flow Index.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("Money Flow Index")

plot(ta.mfi(hlc3, 14), color=color.yellow)

// the same on pine
pine_mfi(src, length) =>
    float upper = math.sum(volume * (ta.change(src) <= 0.0 ? 0.0 : src), length)
    float lower = math.sum(volume * (ta.change(src) >= 0.0 ? 0.0 : src), length)
    mfi = 100.0 - (100.0 / (1.0 + upper / lower))
    mfi

plot(pine_mfi(hlc3, 14))
```

---

## ta.min()

Returns the all-time low value of source from the beginning of the chart up to the current bar.

### Syntax

```pine
ta.min(source) → series float
```

### Arguments

- `source` (*series int|float*) — Source used for the calculation.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.min).*

### Remarks
na occurrences of source are ignored.

---

## ta.mode()

Returns the mode of the series. If there are several values with the same frequency, it returns the smallest value.

### Syntax

```pine
ta.mode(source, length) → series float|int
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.mode).*

### Returns
The most frequently occurring value from the source. If none exists, returns the smallest value instead.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

---

## ta.mom()

Momentum of source price and source price length bars ago. This is simply a difference: source - source[length].

### Syntax

```pine
ta.mom(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Offset from the current bar to the previous bar.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.mom).*

### Returns
Momentum of source price and source price length bars ago.

### Remarks
na values in the source series are included in calculations and will produce an na result.

---

## ta.percentile_linear_interpolation()

Calculates percentile using method of linear interpolation between the two nearest ranks.

### Syntax

```pine
ta.percentile_linear_interpolation(source, length, percentage) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process (source).
- `length` (*series int*) — Number of bars back (length).
- `percentage` (*simple int|float*) — Percentage, a number from range 0..100.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.percentile_linear_interpolation).*

### Returns
P-th percentile of source series for length bars back.

### Remarks
Note that a percentile calculated using this method will NOT always be a member of the input data set. na values in the source series are included in calculations and will produce an na result.

---

## ta.percentile_nearest_rank()

Calculates percentile using method of Nearest Rank.

### Syntax

```pine
ta.percentile_nearest_rank(source, length, percentage) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process (source).
- `length` (*series int*) — Number of bars back (length).
- `percentage` (*simple int|float*) — Percentage, a number from range 0..100.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.percentile_nearest_rank).*

### Returns
P-th percentile of source series for length bars back.

### Remarks
Using the Nearest Rank method on lengths less than 100 bars back can result in the same number being used for more than one percentile. A percentile calculated using the Nearest Rank method will always be a member of the input data set. The 100th percentile is defined to be the largest value in the input data set. na values in the source series are ignored.

---

## ta.percentrank()

Percent rank is the percents of how many previous values was less than or equal to the current value of given series.

### Syntax

```pine
ta.percentrank(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.percentrank).*

### Returns
Percent rank of source for length bars back.

### Remarks
na values in the source series are included in calculations and will produce an na result.

---

## ta.pivot_point_levels()

Calculates the pivot point levels using the specified type and anchor.

### Syntax

```pine
ta.pivot_point_levels(type, anchor, developing) → array<float>
```

### Arguments

- `displayType` (*series string*) — The type of pivot point levels. Possible values: "Traditional", "Fibonacci", "Woodie", "Classic", "DM", "Camarilla".
- `anchor` (*series bool*) — The condition that triggers the reset of the pivot point calculations. When [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), calculations reset; when [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), results calculated at the last reset persist.
- `developing` (*series bool*, optional, default `false`) — If [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), the values are those calculated the last time the anchor condition was [true](https://www.tradingview.com/pine-script-reference/v6/#op_true). They remain constant until the anchor condition becomes [true](https://www.tradingview.com/pine-script-reference/v6/#op_true) again. If [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), the pivots are developing, i.e., they constantly recalculate on the data developing between the point of the last anchor (or bar zero if the anchor condition was never [true](https://www.tradingview.com/pine-script-reference/v6/#op_true)) and the current bar. Optional. The default is [false](https://www.tradingview.com/pine-script-reference/v6/#op_false).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.pivot_point_levels).*

### Returns
An array<float> with numerical values representing 11 pivot point levels: [P, R1, S1, R2, S2, R3, S3, R4, S4, R5, S5]. Levels absent from the specified type return na values (e.g., "DM" only calculates P, R1, and S1).

### Remarks
The developing parameter cannot be true when type is set to "Woodie", because the Woodie calculation for a period depends on that period's open, which means that the pivot value is either available or unavailable, but never developing. If used together, the indicator will return a runtime error.

### Code Example
```pine
//@version=6
indicator("Weekly Pivots", max_lines_count=500, overlay=true)
timeframe = "1W"
typeInput = input.string("Traditional", "Type", options=["Traditional", "Fibonacci", "Woodie", "Classic", "DM", "Camarilla"])
weekChange = timeframe.change(timeframe)
pivotPointsArray = ta.pivot_point_levels(typeInput, weekChange)
if weekChange
    for pivotLevel in pivotPointsArray
        line.new(time, pivotLevel, time + timeframe.in_seconds(timeframe) * 1000, pivotLevel, xloc=xloc.bar_time)
```

---

## ta.pivothigh()

This function returns price of the pivot high point. It returns 'NaN', if there was no pivot high point.

### Syntax

```pine
ta.pivothigh(source, leftbars, rightbars) → series float
ta.pivothigh(leftbars, rightbars) → series float
```

### Arguments

- `source` (*series int|float*, default `High`) — An optional parameter. Data series to calculate the value. 'High' by default.
- `leftbars` (*series int|float*) — Left strength.
- `rightbars` (*series int|float*) — Right strength.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.pivothigh).*

### Returns
Price of the point or 'NaN'.

### Remarks
If parameters 'leftbars' or 'rightbars' are series you should use max_bars_back function for the 'source' variable.

### Code Example
```pine
//@version=6
indicator("PivotHigh", overlay=true)
leftBars = input(2)
rightBars=input(2)
ph = ta.pivothigh(leftBars, rightBars)
plot(ph, style=plot.style_cross, linewidth=3, color= color.red, offset=-rightBars)
```

---

## ta.pivotlow()

This function returns price of the pivot low point. It returns 'NaN', if there was no pivot low point.

### Syntax

```pine
ta.pivotlow(source, leftbars, rightbars) → series float
ta.pivotlow(leftbars, rightbars) → series float
```

### Arguments

- `source` (*series int|float*, default `low`) — An optional parameter. Data series to calculate the value. 'Low' by default.
- `leftbars` (*series int|float*) — Left strength.
- `rightbars` (*series int|float*) — Right strength.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.pivotlow).*

### Returns
Price of the point or 'NaN'.

### Remarks
If parameters 'leftbars' or 'rightbars' are series you should use max_bars_back function for the 'source' variable.

### Code Example
```pine
//@version=6
indicator("PivotLow", overlay=true)
leftBars = input(2)
rightBars=input(2)
pl = ta.pivotlow(close, leftBars, rightBars)
plot(pl, style=plot.style_cross, linewidth=3, color= color.blue, offset=-rightBars)
```

---

## ta.range()

Returns the difference between the min and max values in a series.

### Syntax

```pine
ta.range(source, length) → series float|int
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.range).*

### Returns
The difference between the min and max values in the series.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

---

## ta.rci()

Calculates the Rank Correlation Index (RCI), which measures the directional consistency of price movements. It evaluates the monotonic relationship between a source series and the bar index over length bars using Spearman's rank correlation coefficient. The resulting value is scaled to a range of -100 to 100, where 100 indicates the source consistently increased over the period, and -100 indicates it consistently decreased. Values between -100 and 100 reflect varying degrees of upward or downward consistency.

### Returns
The Rank Correlation Index, a value between -100 to 100.

---

## ta.rising()

Test if the source series is now rising for length bars long.

### Syntax

```pine
ta.rising(source, length) → series bool
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.rising).*

### Returns
true if current source is greater than any previous source for length bars back, false otherwise.

### Remarks
na values in the source series are ignored.

---

## ta.rma()

Moving average used in RSI. It is the exponentially weighted moving average with alpha = 1 / length.

### Syntax

```pine
ta.rma(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*simple int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.rma).*

### Returns
Exponential moving average of source with alpha = 1 / length.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.rma")
plot(ta.rma(close, 15))

//the same on pine
pine_rma(src, length) =>
    alpha = 1/length
    sum = 0.0
    sum := na(sum[1]) ? ta.sma(src, length) : alpha * src + (1 - alpha) * nz(sum[1])
plot(pine_rma(close, 15))
```

---

## ta.roc()

Calculates the percentage of change (rate of change) between the current value of source and its value length bars ago.

### Syntax

```pine
ta.roc(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.roc).*

### Returns
The rate of change of source for length bars back.

### Remarks
na values in the source series are included in calculations and will produce an na result.

---

## ta.rsi()

Relative strength index. It is calculated using the ta.rma() of upward and downward changes of source over the last length bars.

### Syntax

```pine
ta.rsi(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*simple int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.rsi).*

### Returns
Relative strength index.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.rsi")
plot(ta.rsi(close, 7))

// same on pine, but less efficient
pine_rsi(x, y) => 
    u = math.max(x - x[1], 0) // upward ta.change
    d = math.max(x[1] - x, 0) // downward ta.change
    rs = ta.rma(u, y) / ta.rma(d, y)
    res = 100 - 100 / (1 + rs)
    res

plot(pine_rsi(close, 7))
```

---

## ta.sar()

Parabolic SAR (parabolic stop and reverse) is a method devised by J. Welles Wilder, Jr., to find potential reversals in the market price direction of traded goods.

### Syntax

```pine
ta.sar(start, inc, max) → series float
```

### Arguments

- `start` (*simple int|float*) — Start.
- `inc` (*simple int|float*) — Increment.
- `max` (*simple int|float*) — Maximum.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.sar).*

### Returns
Parabolic SAR.

### Code Example
```pine
//@version=6
indicator("ta.sar")
plot(ta.sar(0.02, 0.02, 0.2), style=plot.style_cross, linewidth=3)

// The same on Pine Script®
pine_sar(start, inc, max) =>
    var float result = na
    var float maxMin = na
    var float acceleration = na
    var bool isBelow = false
    bool isFirstTrendBar = false
    
    if bar_index == 1
        if close > close[1]
            isBelow := true
            maxMin := high
            result := low[1]
        else
            isBelow := false
            maxMin := low
            result := high[1]
        isFirstTrendBar := true
        acceleration := start
    
    result := result + acceleration * (maxMin - result)
    
    if isBelow
        if result > low
            isFirstTrendBar := true
            isBelow := false
            result := math.max(high, maxMin)
            maxMin := low
            acceleration := start
    else
        if result < high
            isFirstTrendBar := true
            isBelow := true
            result := math.min(low, maxMin)
            maxMin := high
            acceleration := start
            
    if not isFirstTrendBar
        if isBelow
            if high > maxMin
                maxMin := high
                acceleration := math.min(acceleration + inc, max)
        else
            if low < maxMin
                maxMin := low
                acceleration := math.min(acceleration + inc, max)
    
    if isBelow
        result := math.min(result, low[1])
        if bar_index > 1
            result := math.min(result, low[2])
        
    else
        result := math.max(result, high[1])
        if bar_index > 1
            result := math.max(result, high[2])
    
    result
    
plot(pine_sar(0.02, 0.02, 0.2), style=plot.style_cross, linewidth=3)
```

---

## ta.sma()

The sma function returns the moving average, that is the sum of last y values of x, divided by y.

### Syntax

```pine
ta.sma(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.sma).*

### Returns
Simple moving average of source for length bars back.

### Remarks
na values in the source series are ignored.

### Code Example
```pine
//@version=6
indicator("ta.sma")
plot(ta.sma(close, 15))

// same on pine, but much less efficient
pine_sma(x, y) =>
    sum = 0.0
    for i = 0 to y - 1
        sum := sum + x[i] / y
    sum
plot(pine_sma(close, 15))
```

---

## ta.stdev()

### Syntax

```pine
ta.stdev(source, length, biased) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).
- `biased` (*series bool*, optional, default `true`) — Determines which estimate should be used. Optional. The default is true.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.stdev).*

### Returns
Standard deviation.

### Remarks
If biased is true, function will calculate using a biased estimate of the entire population, if false - unbiased estimate of a sample. na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### Code Example
```pine
//@version=6
indicator("ta.stdev")
plot(ta.stdev(close, 5))

//the same on pine
isZero(val, eps) => math.abs(val) <= eps

SUM(fst, snd) =>
    EPS = 1e-10
    res = fst + snd
    if isZero(res, EPS)
        res := 0
    else
        if not isZero(res, 1e-4)
            res := res
        else
            15

pine_stdev(src, length) =>
    avg = ta.sma(src, length)
    sumOfSquareDeviations = 0.0
    for i = 0 to length - 1
        sum = SUM(src[i], -avg)
        sumOfSquareDeviations := sumOfSquareDeviations + sum * sum

    stdev = math.sqrt(sumOfSquareDeviations / length)
plot(pine_stdev(close, 5))
```

---

## ta.stoch()

Stochastic. It is calculated by a formula: 100 * (close - lowest(low, length)) / (highest(high, length) - lowest(low, length)).

### Syntax

```pine
ta.stoch(source, high, low, length) → series float
```

### Arguments

- `source` (*series int|float*) — Source series.
- `high` (*series int|float*) — Series of high.
- `low` (*series int|float*) — Series of low.
- `length` (*series int*) — Length (number of bars back).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.stoch).*

### Returns
Stochastic.

### Remarks
na values in the source series are ignored.

---

## ta.supertrend()

The Supertrend Indicator. The Supertrend is a trend following indicator.

### Syntax

```pine
ta.supertrend(factor, atrPeriod) → [series float, series float]
```

### Arguments

- `factor` (*series int|float*) — The multiplier by which the ATR will get multiplied.
- `atrPeriod` (*simple int*) — Length of ATR.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.supertrend).*

### Returns
Tuple of two supertrend series: supertrend line and direction of trend. Possible values are 1 (down direction) and -1 (up direction).

### Code Example
```pine
//@version=6
indicator("Pine Script® Supertrend")

[supertrend, direction] = ta.supertrend(3, 10)
plot(direction < 0 ? supertrend : na, "Up direction", color = color.green, style=plot.style_linebr)
plot(direction > 0 ? supertrend : na, "Down direction", color = color.red, style=plot.style_linebr)

// The same on Pine Script®
pine_supertrend(factor, atrPeriod) =>
    src = hl2
    atr = ta.atr(atrPeriod)
    upperBand = src + factor * atr
    lowerBand = src - factor * atr
    prevLowerBand = nz(lowerBand[1])
    prevUpperBand = nz(upperBand[1])

    lowerBand := lowerBand > prevLowerBand or close[1] < prevLowerBand ? lowerBand : prevLowerBand
    upperBand := upperBand < prevUpperBand or close[1] > prevUpperBand ? upperBand : prevUpperBand
    int _direction = na
    float superTrend = na
    prevSuperTrend = superTrend[1]
    if na(atr[1])
        _direction := 1
    else if prevSuperTrend == prevUpperBand
        _direction := close > upperBand ? -1 : 1
    else
        _direction := close < lowerBand ? 1 : -1
    superTrend := _direction == -1 ? lowerBand : upperBand
    [superTrend, _direction]

[Pine_Supertrend, pineDirection] = pine_supertrend(3, 10)
plot(pineDirection < 0 ? Pine_Supertrend : na, "Up direction", color = color.green, style=plot.style_linebr)
plot(pineDirection > 0 ? Pine_Supertrend : na, "Down direction", color = color.red, style=plot.style_linebr)
```

---

## ta.swma()

Symmetrically weighted moving average with fixed length: 4. Weights: [1/6, 2/6, 2/6, 1/6].

### Syntax

```pine
ta.swma(source) → series float
```

### Arguments

- `source` (*series int|float*) — Source series.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.swma).*

### Returns
Symmetrically weighted moving average.

### Remarks
na values in the source series are included in calculations and will produce an na result.

### Code Example
```pine
//@version=6
indicator("ta.swma")
plot(ta.swma(close))

// same on pine, but less efficient
pine_swma(x) =>
    x[3] * 1 / 6 + x[2] * 2 / 6 + x[1] * 2 / 6 + x[0] * 1 / 6
plot(pine_swma(close))
```

---

## ta.tr()

Calculates the current bar's true range. Unlike a bar's actual range (high - low), true range accounts for potential gaps by taking the maximum of the current bar's actual range and the absolute distances from the previous bar's close to the current bar's high and low. The formula is: math.max(high - low, math.abs(high - close[1]), math.abs(low - close[1]))

### Syntax

```pine
ta.tr(handle_na) → series float
```

### Arguments

- `handle_na` (*simple bool*) — How NaN values are handled. if true, and previous day’s close is NaN then tr would be calculated as current day high-low. Otherwise (if false) tr would return NaN in such cases. Also note, that [ta.atr](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.atr) uses ta.tr(true).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.tr).*

### Returns
True range. It is math.max(high - low, math.abs(high - close[1]), math.abs(low - close[1])).

### Remarks
ta.tr(false) is exactly the same as ta.tr.

---

## ta.tsi()

True strength index. It uses moving averages of the underlying momentum of a financial instrument.

### Syntax

```pine
ta.tsi(source, short_length, long_length) → series float
```

### Arguments

- `source` (*series int|float*) — Source series.
- `short_length` (*simple int*) — Short length.
- `long_length` (*simple int*) — Long length.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.tsi).*

### Returns
True strength index. A value in range [-1, 1].

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

---

## ta.valuewhen()

Returns the value of the source series on the bar where the condition was true on the nth most recent occurrence.

### Syntax

```pine
ta.valuewhen(condition, source, occurrence) → series float|int|bool|color
```

### Arguments

- `condition` (*series bool*) — The condition to search for.
- `source` (*series int|float|bool|color*) — The value to be returned from the bar where the condition is met.
- `occurrence` (*simple int*) — The occurrence of the condition. The numbering starts from 0 and goes back in time, so '0' is the most recent occurrence of `condition`, '1' is the second most recent and so forth. Must be an integer >= 0.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.valuewhen).*

### Remarks
This function requires execution on every bar. It is not recommended to use it inside a for or while loop structure, where its behavior can be unexpected. Please note that using this function can cause indicator repainting.

### Code Example
```pine
//@version=6
indicator("ta.valuewhen")
slow = ta.sma(close, 7)
fast = ta.sma(close, 14)
// Get value of `close` on second most recent cross
plot(ta.valuewhen(ta.cross(slow, fast), close, 1))
```

---

## ta.variance()

Variance is the expectation of the squared deviation of a series from its mean (ta.sma), and it informally measures how far a set of numbers are spread out from their mean.

### Syntax

```pine
ta.variance(source, length, biased) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).
- `biased` (*series bool*, optional, default `true`) — Determines which estimate should be used. Optional. The default is true.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.variance).*

### Returns
Variance of source for length bars back.

### Remarks
If biased is true, function will calculate using a biased estimate of the entire population, if false - unbiased estimate of a sample. na values in the source series are ignored; the function calculates on the length quantity of non-na values.

---

## ta.vwap()

Volume weighted average price.

### Syntax

```pine
ta.vwap(source, anchor) → series float
ta.vwap(source, anchor, stdev_mult) → [series float, series float, series float]
```

### Arguments

- `source` (*series int|float*) — Source used for the VWAP calculation.
- `anchor` (*series bool*, default `1D`) — The condition that triggers the reset of VWAP calculations. When [true](https://www.tradingview.com/pine-script-reference/v6/#op_true), calculations reset; when [false](https://www.tradingview.com/pine-script-reference/v6/#op_false), calculations proceed using the values accumulated since the previous reset. Optional. The default is equivalent to passing [timeframe.change](https://www.tradingview.com/pine-script-reference/v6/#fun_timeframe.change) with "1D" as its argument.
- `stdev_mult` (*series int|float*, default `na`) — If specified, the function will calculate the standard deviation bands based on the main VWAP series and return a [vwap, upper_band, lower_band] tuple. The `upper_band`/`lower_band` values are calculated using the VWAP to which the standard deviation multiplied by this argument is added/subtracted. Optional. The default is [na](https://www.tradingview.com/pine-script-reference/v6/#var_na), in which case the function returns a single value, not a tuple.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.vwap).*

### Returns
A VWAP series, or a tuple [vwap, upper_band, lower_band] if stdev_mult is specified.

### Remarks
Calculations only begin the first time the anchor condition becomes true. Until then, the function returns na.

### Code Example
```pine
//@version=6
indicator("Simple VWAP")
vwap = ta.vwap(open)
plot(vwap)

//@version=6
indicator("Advanced VWAP")
vwapAnchorInput = input.string("Daily", "Anchor", options = ["Daily", "Weekly", "Monthly"])
stdevMultiplierInput = input.float(1.0, "Standard Deviation Multiplier")
anchorTimeframe = switch vwapAnchorInput
    "Daily"   => "1D"
    "Weekly"  => "1W"
    "Monthly" => "1M"
anchor = timeframe.change(anchorTimeframe)
[vwap, upper, lower] = ta.vwap(open, anchor, stdevMultiplierInput)
plot(vwap)
plot(upper, color = color.green)
plot(lower, color = color.green)
```

---

## ta.vwma()

The vwma function returns volume-weighted moving average of source for length bars back. It is the same as: sma(source * volume, length) / sma(volume, length).

### Syntax

```pine
ta.vwma(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.vwma).*

### Returns
Volume-weighted moving average of source for length bars back.

### Remarks
na values in the source series are ignored.

### Code Example
```pine
//@version=6
indicator("ta.vwma")
plot(ta.vwma(close, 15))

// same on pine, but less efficient
pine_vwma(x, y) =>
    ta.sma(x * volume, y) / ta.sma(volume, y)
plot(pine_vwma(close, 15))
```

---

## ta.wma()

The wma function returns weighted moving average of source for length bars back. In wma weighting factors decrease in arithmetical progression.

### Syntax

```pine
ta.wma(source, length) → series float
```

### Arguments

- `source` (*series int|float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.wma).*

### Returns
Weighted moving average of source for length bars back.

### Remarks
na values in the source series are ignored.

### Code Example
```pine
//@version=6
indicator("ta.wma")
plot(ta.wma(close, 15))

// same on pine, but much less efficient
pine_wma(x, y) =>
    norm = 0.0
    sum = 0.0
    for i = 0 to y - 1
        weight = (y - i) * y
        norm := norm + weight
        sum := sum + x[i] * weight
    sum / norm
plot(pine_wma(close, 15))
```

---

## ta.wpr()

Williams %R. The oscillator shows the current closing price in relation to the high and low of the past 'length' bars.

### Syntax

```pine
ta.wpr(length) → series float
```

### Arguments

- `length` (*series int*) — Number of bars.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ta.wpr).*

### Returns
Williams %R.

### Remarks
na values in the source series are ignored.

### Code Example
```pine
//@version=6
indicator("Williams %R", shorttitle="%R", format=format.price, precision=2)
plot(ta.wpr(14), title="%R", color=color.new(#ff6d00, 0))
```

---

## table()

Casts na to table

### Syntax

```pine
table
table(x) → series table
```

### Arguments

- `x` (*series table*) — 'na' to cast to table.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table).*

### Returns
The value of the argument after casting to table.

---

## table.cell()

The function defines a cell in the table and sets its attributes.

### Syntax

```pine
table.cell(table_id, column, row, text, width, height, text_color, text_halign, text_valign, text_size, bgcolor, tooltip, text_font_family) → void
```

### Arguments

- `column` (*series int*) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell’s row. Numbering starts at 0.
- `text` (*series string*, optional, default `""`) — The text to be displayed inside the cell. Optional. The default is empty string.
- `text_font_family` (*series string*, optional, default `font.family_default`) — The font family of the text. Optional. The default value is [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default). Possible values: [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default), [font.family_monospace](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_monospace).
- `width` (*series int|float*, optional, default `0`) — The width of the cell as a % of the indicator’s visual space. Optional. By default, auto-adjusts the width based on the text inside the cell. Value 0 has the same effect.
- `height` (*series int|float*, optional, default `0`) — The height of the cell as a % of the indicator’s visual space. Optional. By default, auto-adjusts the height based on the text inside of the cell. Value 0 has the same effect.
- `text_color` (*series color*, optional, default `color.black`) — The color of the text. Optional. The default is [color.black](https://www.tradingview.com/pine-script-reference/v6/#var_color.black).
- `text_halign` (*series string*, optional, default `text.align_center`) — The horizontal alignment of the cell’s text. Optional. The default value is [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center). Possible values: [text.align_left](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_left), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_right](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_right).
- `text_valign` (*series string*, optional, default `text.align_center`) — The vertical alignment of the cell’s text. Optional. The default value is [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center). Possible values: [text.align_top](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_top), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_bottom](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_bottom).
- `text_size` (*series string*, optional, default `size.normal`) — The size of the text. An optional parameter, the default value is [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal). Possible values: [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v6/#var_size.tiny), [size.small](https://www.tradingview.com/pine-script-reference/v6/#var_size.small), [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal), [size.large](https://www.tradingview.com/pine-script-reference/v6/#var_size.large), [size.huge](https://www.tradingview.com/pine-script-reference/v6/#var_size.huge).
- `bgcolor` (*series color*, optional, default `na`) — The background color of the text. Optional. The default is no color.
- `tooltip` (*series string*, optional) — The tooltip to be displayed inside the cell. Optional.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell).*

### Remarks
This function does not create the table itself, but defines the table’s cells. To use it, you first need to create a table object with table.new. Each table.cell call overwrites all previously defined properties of a cell. If you call table.cell twice in a row, e.g., the first time with text='Test Text', and the second time with text_color=color.red but without a new text argument, the default value of the 'text' being an empty string, it will overwrite 'Test Text', and your cell will display an empty string. If you want, instead, to modify any of the cell's properties, use the table.cell_set_*() functions. A single script can only display one table in each of the possible locations. If table.cell is used on several bars to change the same attribute of a cell (e.g. change the background color of the cell to red on the first bar, then to yellow on the second bar), only the last change will be reflected in the table, i.e., the cell’s background will be yellow. Avoid unnecessary setting of cell properties by enclosing function calls in an if barstate.islast block whenever possible, to restrict their execution to the last bar of the series.

---

## table.cell_set_bgcolor()

The function sets the background color of the cell.

---

### Syntax

```pine
table.cell_set_bgcolor(table_id, column, row, bgcolor) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `bgcolor` (*series color*, optional) — The background color of the cell.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_bgcolor).*

## table.cell_set_height()

The function sets the height of cell.

---

### Syntax

```pine
table.cell_set_height(table_id, column, row, height) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `height` (*series int|float*, optional, default `0`) — The height of the cell as a % of the chart window. Passing 0 auto-adjusts the height based on the text inside of the cell.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_height).*

## table.cell_set_text()

The function sets the text in the specified cell.

### Syntax

```pine
table.cell_set_text(table_id, column, row, text) → void
```

### Arguments

- `column` (*series int*) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `text` (*series string*) — The text to be displayed inside the cell.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_text).*

### Code Example
```pine
//@version=6
indicator("TABLE example")
var tLog = table.new(position = position.top_left, rows = 1, columns = 2, bgcolor = color.yellow, border_width=1)
table.cell(tLog, row = 0, column = 0, text = "sometext", text_color = color.blue)
table.cell_set_text(tLog, row = 0, column = 0, text = "sometext")
```

---

## table.cell_set_text_color()

The function sets the color of the text inside the cell.

---

### Syntax

```pine
table.cell_set_text_color(table_id, column, row, text_color) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `text_color` (*series color*) — The color of the text.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_text_color).*

## table.cell_set_text_font_family()

The function sets the font family of the text inside the cell.

### Syntax

```pine
table.cell_set_text_font_family(table_id, column, row, text_font_family) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `text_font_family` (*series string*, default `font.family_default`) — The font family of the text. Possible values: [font.family_default](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_default), [font.family_monospace](https://www.tradingview.com/pine-script-reference/v6/#var_font.family_monospace).
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_text_font_family).*

### Code Example
```pine
//@version=6
indicator("Example of setting the table cell font")
var t = table.new(position.top_left, rows = 1, columns = 1)
table.cell(t, 0, 0, "monospace", text_color = color.blue)
table.cell_set_text_font_family(t, 0, 0, font.family_monospace)
```

---

## table.cell_set_text_formatting()

Sets the formatting attributes the drawing applies to displayed text.

---

## table.cell_set_text_halign()

The function sets the horizontal alignment of the cell's text.

---

### Syntax

```pine
table.cell_set_text_halign(table_id, column, row, text_halign) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `text_halign` (*series string*, default `text.align_left`) — The horizontal alignment of a cell’s text. Possible values: [text.align_left](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_left), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_right](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_right).
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_text_halign).*

## table.cell_set_text_size()

The function sets the size of the cell's text.

---

### Syntax

```pine
table.cell_set_text_size(table_id, column, row, text_size) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `text_size` (*series string*, optional, default `size.auto`) — The size of the text. Possible values: [size.auto](https://www.tradingview.com/pine-script-reference/v6/#var_size.auto), [size.tiny](https://www.tradingview.com/pine-script-reference/v6/#var_size.tiny), [size.small](https://www.tradingview.com/pine-script-reference/v6/#var_size.small), [size.normal](https://www.tradingview.com/pine-script-reference/v6/#var_size.normal), [size.large](https://www.tradingview.com/pine-script-reference/v6/#var_size.large), [size.huge](https://www.tradingview.com/pine-script-reference/v6/#var_size.huge).
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_text_size).*

## table.cell_set_text_valign()

The function sets the vertical alignment of a cell's text.

---

### Syntax

```pine
table.cell_set_text_valign(table_id, column, row, text_valign) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `text_valign` (*series string*, default `text.align_center`) — The vertical alignment of the cell’s text. Possible values: [text.align_top](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_top), [text.align_center](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_center), [text.align_bottom](https://www.tradingview.com/pine-script-reference/v6/#var_text.align_bottom).
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_text_valign).*

## table.cell_set_tooltip()

The function sets the tooltip in the specified cell.

### Syntax

```pine
table.cell_set_tooltip(table_id, column, row, tooltip) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `tooltip` (*series string*) — The tooltip to be displayed inside the cell.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_tooltip).*

### Code Example
```pine
//@version=6
indicator("TABLE example")
var tLog = table.new(position = position.top_left, rows = 1, columns = 2, bgcolor = color.yellow, border_width=1)
table.cell(tLog, row = 0, column = 0, text = "sometext", text_color = color.blue)
table.cell_set_tooltip(tLog, row = 0, column = 0, tooltip = "sometext")
```

---

## table.cell_set_width()

The function sets the width of the cell.

---

### Syntax

```pine
table.cell_set_width(table_id, column, row, width) → void
```

### Arguments

- `column` (*series int*, default `0`) — The index of the cell’s column. Numbering starts at 0.
- `row` (*series int*, default `0`) — The index of the cell’s row. Numbering starts at 0.
- `width` (*series int|float*, optional, default `0`) — The width of the cell as a % of the chart window. Passing 0 auto-adjusts the width based on the text inside of the cell.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.cell_set_width).*

## table.clear()

The function removes a cell or a sequence of cells from the table. The cells are removed in a rectangle shape where the start_column and start_row specify the top-left corner, and end_column and end_row specify the bottom-right corner.

### Syntax

```pine
table.clear(table_id, start_column, start_row, end_column, end_row) → void
```

### Arguments

- `start_column` (*series int*) — The index of the column of the first cell to delete. Numbering starts at 0.
- `start_row` (*series int*) — The index of the row of the first cell to delete. Numbering starts at 0.
- `end_column` (*series int*, optional, default `'start_column'`) — The index of the column of the last cell to delete. Optional. The default is the argument used for start_column. Numbering starts at 0.
- `end_row` (*series int*, optional, default `'start_row'`) — The index of the row of the last cell to delete. Optional. The default is the argument used for start_row. Numbering starts at 0.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.clear).*

### Code Example
```pine
//@version=6
indicator("A donut", overlay=true)
if barstate.islast
    colNum = 8, rowNum = 8
    padding = "◯"
    donutTable = table.new(position.middle_right, colNum, rowNum)
    for c = 0 to colNum - 1
        for r = 0 to rowNum - 1
            table.cell(donutTable, c, r, text=padding, bgcolor=#face6e, text_color=color.new(color.black, 100))
    table.clear(donutTable, 2, 2, 5, 5)
```

---

## table.delete()

The function deletes a table.

### Syntax

```pine
table.delete(table_id) → void
```

### Arguments

- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.delete).*

### Code Example
```pine
//@version=6
indicator("table.delete example")
var testTable = table.new(position = position.top_right, columns = 2, rows = 1, bgcolor = color.yellow, border_width = 1)
if barstate.islast
    table.cell(table_id = testTable, column = 0, row = 0, text = "Open is " + str.tostring(open))
    table.cell(table_id = testTable, column = 1, row = 0, text = "Close is " + str.tostring(close), bgcolor=color.teal)
if barstate.isrealtime
    table.delete(testTable)
```

---

## table.merge_cells()

The function merges a sequence of cells in the table into one cell. The cells are merged in a rectangle shape where the start_column and start_row specify the top-left corner, and end_column and end_row specify the bottom-right corner.

### Syntax

```pine
table.merge_cells(table_id, start_column, start_row, end_column, end_row) → void
```

### Arguments

- `start_column` (*series int*) — The index of the column of the first cell to merge. Numbering starts at 0.
- `start_row` (*series int*) — The index of the row of the first cell to merge. Numbering starts at 0.
- `end_column` (*series int*) — The index of the column of the last cell to merge. Numbering starts at 0.
- `end_row` (*series int*) — The index of the row of the last cell to merge. Numbering starts at 0.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.merge_cells).*

### Remarks
This function will merge cells, even if their properties are not yet defined with table.cell. The resulting merged cell inherits all of its values from the cell located at start_column:start_row, except width and height. The width and height of the resulting merged cell are based on the width/height of other cells in the neighboring columns/rows and cannot be set manually. To modify the merged cell with any of the table.cell_set_* functions, target the cell at the start_column:start_row coordinates. An attempt to merge a cell that has already been merged will result in an error.

### Code Example
```pine
//@version=6
indicator("table.merge_cells example")
SMA50  = ta.sma(close, 50)
SMA100 = ta.sma(close, 100)
SMA200 = ta.sma(close, 200)
if barstate.islast
    maTable = table.new(position.bottom_right, 3, 3, bgcolor = color.gray, border_width = 1, border_color = color.black)
    // Header
    table.cell(maTable, 0, 0, text = "SMA Table")
    table.merge_cells(maTable, 0, 0, 2, 0)
    // Cell Titles
    table.cell(maTable, 0, 1, text = "SMA 50")
    table.cell(maTable, 1, 1, text = "SMA 100")
    table.cell(maTable, 2, 1, text = "SMA 200")
    // Values
    table.cell(maTable, 0, 2, bgcolor = color.white, text = str.tostring(SMA50))
    table.cell(maTable, 1, 2, bgcolor = color.white, text = str.tostring(SMA100))
    table.cell(maTable, 2, 2, bgcolor = color.white, text = str.tostring(SMA200))
```

---

## table.new()

The function creates a new table.

### Syntax

```pine
table.new(position, columns, rows, bgcolor, frame_color, frame_width, border_color, border_width) → series table
```

### Arguments

- `position` (*series string*) — Position of the table. Possible values are: [position.top_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_left), [position.top_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_center), [position.top_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_right), [position.middle_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_left), [position.middle_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_center), [position.middle_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_right), [position.bottom_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_left), [position.bottom_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_center), [position.bottom_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_right).
- `columns` (*series int*) — The number of columns in the table.
- `rows` (*series int*) — The number of rows in the table.
- `bgcolor` (*series color*, optional, default `na`) — The background color of the table. Optional. The default is no color.
- `frame_color` (*series color*, optional, default `na`) — The color of the outer frame of the table. Optional. The default is no color.
- `frame_width` (*series int*, optional, default `0`) — The width of the outer frame of the table. Optional. The default is 0.
- `border_color` (*series color*, optional, default `na`) — The color of the borders of the cells (excluding the outer frame). Optional. The default is no color.
- `border_width` (*series int*, optional, default `0`) — The width of the borders of the cells (excluding the outer frame). Optional. The default is 0.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.new).*

### Returns
The ID of a table object that can be passed to other table.*() functions.

### Remarks
This function creates the table object itself, but the table will not be displayed until its cells are populated. To define a cell and change its contents or attributes, use table.cell and other table.cell_*() functions. One table.new call can only display one table (the last one drawn), but the function itself will be recalculated on each bar it is used on. For performance reasons, it is wise to use table.new in conjunction with either the var keyword (so the table object is only created on the first bar) or in an if barstate.islast block (so the table object is only created on the last bar).

### Code Example
```pine
//@version=6
indicator("table.new example")
var testTable = table.new(position = position.top_right, columns = 2, rows = 1, bgcolor = color.yellow, border_width = 1)
if barstate.islast
    table.cell(table_id = testTable, column = 0, row = 0, text = "Open is " + str.tostring(open))
    table.cell(table_id = testTable, column = 1, row = 0, text = "Close is " + str.tostring(close), bgcolor=color.teal)
```

---

## table.set_bgcolor()

The function sets the background color of a table.

---

### Syntax

```pine
table.set_bgcolor(table_id, bgcolor) → void
```

### Arguments

- `bgcolor` (*series color*, optional) — The background color of the table
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.set_bgcolor).*

## table.set_border_color()

The function sets the color of the borders (excluding the outer frame) of the table's cells.

---

### Syntax

```pine
table.set_border_color(table_id, border_color) → void
```

### Arguments

- `border_color` (*series color*, optional) — The color of the borders.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.set_border_color).*

## table.set_border_width()

The function sets the width of the borders (excluding the outer frame) of the table's cells.

---

### Syntax

```pine
table.set_border_width(table_id, border_width) → void
```

### Arguments

- `border_width` (*series int*, optional, default `0`) — The width of the borders. Optional. The default is 0.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.set_border_width).*

## table.set_frame_color()

The function sets the color of the outer frame of a table.

---

### Syntax

```pine
table.set_frame_color(table_id, frame_color) → void
```

### Arguments

- `frame_color` (*series color*, optional) — The color of the frame of the table. Optional.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.set_frame_color).*

## table.set_frame_width()

The function set the width of the outer frame of a table.

---

### Syntax

```pine
table.set_frame_width(table_id, frame_width) → void
```

### Arguments

- `frame_width` (*series int*, optional, default `0`) — The width of the outer frame of the table. Optional. The default is 0.
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.set_frame_width).*

## table.set_position()

The function sets the position of a table.

---

### Syntax

```pine
table.set_position(table_id, position) → void
```

### Arguments

- `position` (*series string*) — Position of the table. Possible values are: [position.top_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_left), [position.top_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_center), [position.top_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_right), [position.middle_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_left), [position.middle_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_center), [position.middle_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_right), [position.bottom_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_left), [position.bottom_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_center), [position.bottom_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_right).
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.set_position).*

## ticker.heikinashi()

Creates a ticker identifier for requesting Heikin Ashi bar values.

### Syntax

```pine
ticker.heikinashi(symbol) → simple string
```

### Arguments

- `symbol` (*simple string*) — Symbol ticker identifier.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.heikinashi).*

### Returns
String value of ticker id, that can be supplied to request.security function.

### Code Example
```pine
//@version=6
indicator("ticker.heikinashi", overlay=true) 
heikinashi_close = request.security(ticker.heikinashi(syminfo.tickerid), timeframe.period, close)

heikinashi_aapl_60_close = request.security(ticker.heikinashi("AAPL"), "60", close)
plot(heikinashi_close)
plot(heikinashi_aapl_60_close)
```

---

## ticker.inherit()

Constructs a ticker ID for the specified symbol with additional parameters inherited from the ticker ID passed into the function call, allowing the script to request a symbol's data using the same modifiers that the from_tickerid has, including extended session, dividend adjustment, currency conversion, non-standard chart types, back-adjustment, settlement-as-close, etc.

### Syntax

```pine
ticker.inherit(from_tickerid, symbol) → simple string
```

### Arguments

- `from_tickerid` (*simple string*) — The ticker ID to inherit modifiers from.
- `symbol` (*simple string*) — The symbol to construct the new ticker ID for.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.inherit).*

### Remarks
If the constructed ticker ID inherits a modifier that doesn't apply to the symbol (e.g., if the from_tickerid has Extended Hours enabled, but no such option is available for the symbol), the script will ignore the modifier when requesting data using the ID.

### Code Example
```pine
//@version=6
indicator("ticker.inherit")

//@variable A "NASDAQ:AAPL" ticker ID with Extender Hours enabled.
tickerExtHours = ticker.new("NASDAQ", "AAPL", session.extended)
//@variable A Heikin Ashi ticker ID for "NASDAQ:AAPL" with Extended Hours enabled.
HAtickerExtHours = ticker.heikinashi(tickerExtHours)
//@variable The "NASDAQ:MSFT" symbol with no modifiers.
testSymbol = "NASDAQ:MSFT"
//@variable A ticker ID for "NASDAQ:MSFT" with inherited Heikin Ashi and Extended Hours modifiers.
testSymbolHAtickerExtHours = ticker.inherit(HAtickerExtHours, testSymbol)

//@variable The `close` price requested using "NASDAQ:MSFT" with inherited modifiers. 
secData = request.security(testSymbolHAtickerExtHours, "60", close, ignore_invalid_symbol = true)
//@variable The `close` price requested using "NASDAQ:MSFT" without modifiers. 
compareData = request.security(testSymbol, "60", close, ignore_invalid_symbol = true)

plot(secData, color = color.green)
plot(compareData)
```

---

## ticker.kagi()

Creates a ticker identifier for requesting Kagi values.

### Syntax

```pine
ticker.kagi(symbol, reversal) → simple string
```

### Arguments

- `symbol` (*simple string*) — Symbol ticker identifier.
- `reversal` (*simple int|float*) — Reversal amount (absolute price value).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.kagi).*

### Returns
String value of ticker id, that can be supplied to request.security function.

### Code Example
```pine
//@version=6
indicator("ticker.kagi", overlay=true) 
kagi_tickerid = ticker.kagi(syminfo.tickerid, 3)
kagi_close = request.security(kagi_tickerid, timeframe.period, close)
plot(kagi_close)
```

---

## ticker.linebreak()

Creates a ticker identifier for requesting Line Break values.

### Syntax

```pine
ticker.linebreak(symbol, number_of_lines) → simple string
```

### Arguments

- `symbol` (*simple string*) — Symbol ticker identifier.
- `number_of_lines` (*simple int*) — Number of line.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.linebreak).*

### Returns
String value of ticker id, that can be supplied to request.security function.

### Code Example
```pine
//@version=6
indicator("ticker.linebreak", overlay=true) 
linebreak_tickerid = ticker.linebreak(syminfo.tickerid, 3)
linebreak_close = request.security(linebreak_tickerid, timeframe.period, close)
plot(linebreak_close)
```

---

## ticker.modify()

Creates a ticker identifier for requesting additional data for the script.

### Syntax

```pine
ticker.modify(tickerid, session, adjustment) → simple string
```

### Arguments

- `tickerid` (*simple string*) — Symbol name with exchange prefix, e.g. 'BATS:MSFT', 'NASDAQ:MSFT' or tickerid with session and adjustment from the [ticker.new](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.new) function.
- `session` (*simple string*, optional, default `syminfo.session`) — Session type. Optional argument. Possible values: [session.regular](https://www.tradingview.com/pine-script-reference/v6/#const_session.regular), [session.extended](https://www.tradingview.com/pine-script-reference/v6/#const_session.extended). Session type of the current chart is [syminfo.session](https://www.tradingview.com/pine-script-reference/v6/#const_syminfo.session). If session is not given, then [syminfo.session](https://www.tradingview.com/pine-script-reference/v6/#const_syminfo.session) value is used.
- `adjustment` (*simple string*, optional, default `adjustment.none`) — Adjustment type. Optional argument. Possible values: [adjustment.none](https://www.tradingview.com/pine-script-reference/v6/#var_adjustment.none), [adjustment.splits](https://www.tradingview.com/pine-script-reference/v6/#var_adjustment.splits), [adjustment.dividends](https://www.tradingview.com/pine-script-reference/v6/#var_adjustment.dividends). If adjustment is not given, then default adjustment value is used (can be different depending on particular instrument).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.modify).*

### Returns
String value of ticker id, that can be supplied to request.security function.

### Code Example
```pine
//@version=6
indicator("ticker_modify", overlay=true)
t1 = ticker.new(syminfo.prefix, syminfo.ticker, session.regular, adjustment.splits)
c1 = request.security(t1, "D", close)
t2 = ticker.modify(t1, session.extended)
c2 = request.security(t2, "2D", close)
plot(c1)
plot(c2)
```

---

## ticker.new()

Creates a ticker identifier for requesting additional data for the script.

### Syntax

```pine
ticker.new(prefix, ticker, session, adjustment) → simple string
```

### Arguments

- `prefix` (*simple string*) — Exchange prefix. For example: 'BATS', 'NYSE', 'NASDAQ'. Exchange prefix of main series is [syminfo.prefix](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.prefix).
- `ticker` (*simple string*) — Ticker name. For example 'AAPL', 'MSFT', 'EURUSD'. Ticker name of the main series is [syminfo.ticker](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.ticker).
- `session` (*simple string*, optional, default `syminfo.session`) — Session type. Optional argument. Possible values: [session.regular](https://www.tradingview.com/pine-script-reference/v6/#const_session.regular), [session.extended](https://www.tradingview.com/pine-script-reference/v6/#const_session.extended). Session type of the current chart is [syminfo.session](https://www.tradingview.com/pine-script-reference/v6/#const_syminfo.session). If session is not given, then [syminfo.session](https://www.tradingview.com/pine-script-reference/v6/#const_syminfo.session) value is used.
- `adjustment` (*simple string*, optional, default `adjustment.none`) — Adjustment type. Optional argument. Possible values: [adjustment.none](https://www.tradingview.com/pine-script-reference/v6/#var_adjustment.none), [adjustment.splits](https://www.tradingview.com/pine-script-reference/v6/#var_adjustment.splits), [adjustment.dividends](https://www.tradingview.com/pine-script-reference/v6/#var_adjustment.dividends). If adjustment is not given, then default adjustment value is used (can be different depending on particular instrument).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.new).*

### Returns
String value of ticker id, that can be supplied to request.security function.

### Remarks
You may use return value of ticker.new function as input argument for ticker.heikinashi, ticker.renko, ticker.linebreak, ticker.kagi, ticker.pointfigure functions.

### Code Example
```pine
//@version=6
indicator("ticker.new", overlay=true) 
t = ticker.new(syminfo.prefix, syminfo.ticker, session.regular, adjustment.splits)
t2 = ticker.heikinashi(t)
c = request.security(t2, timeframe.period, low, barmerge.gaps_on)
plot(c, style=plot.style_linebr)
```

---

## ticker.pointfigure()

Creates a ticker identifier for requesting Point & Figure values.

### Syntax

```pine
ticker.pointfigure(symbol, source, style, param, reversal) → simple string
```

### Arguments

- `symbol` (*simple string*) — Symbol ticker identifier.
- `source` (*simple string*) — The source for calculating Point & Figure. Possible values are: 'hl', 'close'.
- `style` (*simple string*) — Box Size Assignment Method: 'ATR', 'Traditional'.
- `param` (*simple int|float*) — ATR Length if `style` is equal to 'ATR', or Box Size if `style` is equal to 'Traditional'.
- `reversal` (*simple int*) — Reversal amount.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.pointfigure).*

### Returns
String value of ticker id, that can be supplied to request.security function.

### Code Example
```pine
//@version=6
indicator("ticker.pointfigure", overlay=true) 
pnf_tickerid = ticker.pointfigure(syminfo.tickerid, "hl", "Traditional", 1, 3)
pnf_close = request.security(pnf_tickerid, timeframe.period, close)
plot(pnf_close)
```

---

## ticker.renko()

Creates a ticker identifier for requesting Renko values.

### Syntax

```pine
ticker.renko(symbol, style, param, request_wicks, source) → simple string
```

### Arguments

- `symbol` (*simple string*) — Symbol ticker identifier.
- `style` (*simple string*) — Box Size Assignment Method: 'ATR', 'Traditional'.
- `param` (*simple int|float*) — ATR Length if `style` is equal to 'ATR', or Box Size if `style` is equal to 'Traditional'.
- `request_wicks` (*simple bool*, optional, default `false`) — Specifies if wick values are returned for Renko bricks. When " + addInternalLineNotTr("op", "true", "true") + ", " + addInternalLineNotTr("var", "high", "high") + " and " + addInternalLineNotTr("var", "low", "low") + " values requested from a symbol using the ticker formed by this function will include wick values when they are present. When " + addInternalLineNotTr("op", "false", "false") + ", " + addInternalLineNotTr("var", "high", "high") + " and " + addInternalLineNotTr("var", "low", "low") + " will always be equal to either " + addInternalLineNotTr("var", "open", "open") + " or " + addInternalLineNotTr("var", "close", "close") + ". Optional. The default is " + addInternalLineNotTr("op", "false", "false") + ". A detailed explanation of how Renko wicks are calculated can be found in our [Help Center](https://www.tradingview.com/support/solutions/43000481040-what-do-renko-wicks-mean/).
- `source` (*simple string*, optional, default `Close`) — The source used to calculate bricks. Optional. Possible values: "Close", "OHLC". The default is "Close".

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.renko).*

### Returns
String value of ticker id, that can be supplied to request.security function.

### Code Example
```pine
//@version=6
indicator("ticker.renko", overlay=true) 
renko_tickerid = ticker.renko(syminfo.tickerid, "ATR", 10)
renko_close = request.security(renko_tickerid, timeframe.period, close)
plot(renko_close)

//@version=6
indicator("Renko candles", overlay=false)
renko_tickerid = ticker.renko(syminfo.tickerid, "ATR", 10)
[renko_open, renko_high, renko_low, renko_close] = request.security(renko_tickerid, timeframe.period, [open, high, low, close])
plotcandle(renko_open, renko_high, renko_low, renko_close, color = renko_close > renko_open ? color.green : color.red)
```

---

## ticker.standard()

Creates a ticker to request data from a standard chart that is unaffected by modifiers like extended session, dividend adjustment, currency conversion, and the calculations of non-standard chart types: Heikin Ashi, Renko, etc. Among other things, this makes it possible to retrieve standard chart values when the script is running on a non-standard chart.

### Syntax

```pine
ticker.standard(symbol) → simple string
```

### Arguments

- `symbol` (*simple string*, optional, default `syminfo.tickerid`) — A ticker ID to be converted into its standard form. Optional. The default is [syminfo.tickerid](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.tickerid).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_ticker.standard).*

### Returns
A string representing the ticker of a standard chart in the "prefix:ticker" format. If the symbol argument does not contain the prefix and ticker information, the function returns the supplied argument as is.

### Code Example
```pine
//@version=6
indicator("ticker.standard", overlay = true)
// This script should be run on a non-standard chart such as HA, Renko...

// Requests data from the chart type the script is running on.
chartTypeValue = request.security(syminfo.tickerid, "1D", close)

// Request data from the standard chart type, regardless of the chart type the script is running on.
standardChartValue = request.security(ticker.standard(syminfo.tickerid), "1D", close)

// This will not use a standard ticker ID because the `symbol` argument contains only the ticker — not the prefix (exchange).
standardChartValue2 = request.security(ticker.standard(syminfo.ticker), "1D", close)

plot(chartTypeValue)
plot(standardChartValue, color = color.green)
```

---

## time()

The time function returns the UNIX time of the current bar for the specified timeframe and session or NaN if the time point is out of session.

### Syntax

```pine
time(timeframe, session, timezone) → series int
```

### Arguments

- `timeframe` (*series string*) — Timeframe. An empty string is interpreted as the current timeframe of the chart.
- `session` (*series string*, default `""`) — Session specification. Optional argument, session of the symbol is used by default. An empty string is interpreted as the session of the symbol.
- `timezone` (*series string*, default `syminfo.timezone`) — Timezone of the `session` argument. Can only be used when a `session` is specified. Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone). Can be specified in GMT notation (e.g. "GMT-5") or as an [IANA time zone database name](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (e.g. "America/New_York").

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_time).*

### Returns
UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### Code Example
```pine
//@version=6
indicator("Time", overlay=true)
// Try this on chart AAPL,1
timeinrange(res, sess) => not na(time(res, sess, "America/New_York")) ? 1 : 0
plot(timeinrange("1", "1300-1400"), color=color.red)

// This plots 1.0 at every start of 10 minute bar on a 1 minute chart:
newbar(res) => ta.change(time(res)) == 0 ? 0 : 1
plot(newbar("10"))

//@version=6
indicator("Time", overlay=true)
t1 = time(timeframe.period, "0000-0000:23456")
bgcolor(not na(t1) ? color.new(color.blue, 90) : na)

//@version=6
indicator("Time", overlay=true)
t1 = time(timeframe.period, "1000-1100,1400-1500:23456")
bgcolor(not na(t1) ? color.new(color.blue, 90) : na)
```

---

## time_close()

Returns the UNIX time of the current bar's close for the specified timeframe and session, or na if the time point is outside the session. On tick charts and price-based charts such as Renko, line break, Kagi, point & figure, and range, this function returns an na timestamp for the latest realtime bar (because the future closing time is unpredictable), but a valid timestamp for any previous bar.

### Syntax

```pine
time_close(timeframe, session, timezone) → series int
```

### Arguments

- `timeframe` (*series string*) — Resolution. An empty string is interpreted as the current resolution of the chart.
- `session` (*series string*, default `""`) — Session specification. Optional argument, session of the symbol is used by default. An empty string is interpreted as the session of the symbol.
- `timezone` (*series string*, default `syminfo.timezone`) — Timezone of the `session` argument. Can only be used when a `session` is specified. Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone). Can be specified in GMT notation (e.g. "GMT-5") or as an [IANA time zone database name](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) (e.g. "America/New_York").

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_time_close).*

### Returns
UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### Code Example
```pine
//@version=6
indicator("Time", overlay=true)
t1 = time_close(timeframe.period, "1200-1300", "America/New_York")
bgcolor(not na(t1) ? color.new(color.blue, 90) : na)
```

---

## timeframe.change()

Detects changes in the specified timeframe.

### Syntax

```pine
timeframe.change(timeframe) → series bool
```

### Arguments

- `timeframe` (*series string*) — String formatted according to the [User manual’s timeframe string specifications](https://www.tradingview.com/pine-script-docs/en/v5/concepts/Timeframes.html#timeframe-string-specifications).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_timeframe.change).*

### Returns
Returns true on the first bar of a new timeframe, false otherwise.

### Code Example
```pine
//@version=6
// Run this script on an intraday chart.
indicator("New day started", overlay = true)
// Highlights the first bar of the new day.
isNewDay = timeframe.change("1D")
bgcolor(isNewDay ? color.new(color.green, 80) : na)
```

---

## timeframe.from_seconds()

Converts a number of seconds into a valid timeframe string.

### Syntax

```pine
timeframe.from_seconds(seconds) → series string
```

### Arguments

- `seconds` (*series int*) — The number of seconds in the timeframe.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_timeframe.from_seconds).*

### Returns
A timeframe string compliant with timeframe string specifications.

### Remarks
If no valid timeframe exists for the quantity of seconds supplied, the next higher valid timeframe will be returned. Accordingly, one second or less will return "1S", 2-5 seconds will return "5S", and 604,799 seconds (one second less than 7 days) will return "7D". If the seconds exactly represent two or more valid timeframes, the one with the larger base unit will be used. Thus 604,800 seconds (7 days) returns "1W", not "7D". All values above 31,622,400 (366 days) return "12M".

### Code Example
```pine
//@version=6
indicator("HTF Close", "", true)
int chartTf = timeframe.in_seconds()
string tfTimes5 = timeframe.from_seconds(chartTf * 5)
float htfClose = request.security(syminfo.tickerid, tfTimes5, close)
plot(htfClose)
```

---

## timeframe.in_seconds()

Converts a timeframe string into seconds.

### Syntax

```pine
timeframe.in_seconds(timeframe) → series int
```

### Arguments

- `timeframe` (*series string*, optional, default `timeframe.period`) — Timeframe. Optional. The default is [timeframe.period](https://www.tradingview.com/pine-script-reference/v6/#var_timeframe.period).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_timeframe.in_seconds).*

### Returns
The "int" representation of the number of seconds in the timeframe string.

### Remarks
When the timeframe is "1M" or more, calculations use 2628003 as the number of seconds in one month, which represents 30.4167 (365/12) days.

### Code Example
```pine
//@version=6
indicator("`timeframe_in_seconds()`")

// Get a user-selected timeframe.
tfInput = input.timeframe("1D")

// Convert it into an "int" number of seconds.
secondsInTf = timeframe.in_seconds(tfInput)

plot(secondsInTf)
```

---

## timestamp()

Function timestamp returns UNIX time of specified date and time.

### Syntax

```pine
timestamp(year, month, day, hour, minute, second) → simple/series int
timestamp(timezone, year, month, day, hour, minute, second) → simple/series int
timestamp(dateString) → const int
```

### Arguments

- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).
- `year` (*series int*) — Year.
- `month` (*series int*) — Month.
- `day` (*series int*) — Day.
- `hour` (*series int*, optional, default `0`) — (Optional argument) Hour. Default is 0.
- `minute` (*series int*, optional, default `0`) — (Optional argument) Minute. Default is 0.
- `second` (*series int*, optional, default `0`) — (Optional argument) Second. Default is 0.
- `dateString` (*const string*) — A string containing the date and, optionally, the time and time zone. Its format must comply with either the [IETF RFC 2822](https://tools.ietf.org/html/rfc2822#section-3.3) or [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) standards ("DD MMM YYYY hh:mm:ss ±hhmm" or "YYYY-MM-DDThh:mm:ss±hh:mm", so "20 Feb 2020" or "2020-02-20"). If no time is supplied, "00:00" is used. If no time zone is supplied, GMT+0 will be used. Note that this diverges from the usual behavior of the function where it returns time in the exchange’s timezone.

*Signature from the official v6 User Manual. Arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_timestamp).*

### Returns
UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### Code Example
```pine
//@version=6
indicator("timestamp")
plot(timestamp(2016, 01, 19, 09, 30), linewidth=3, color=color.green)
plot(timestamp(syminfo.timezone, 2016, 01, 19, 09, 30), color=color.blue)
plot(timestamp(2016, 01, 19, 09, 30), color=color.yellow)
plot(timestamp("GMT+6", 2016, 01, 19, 09, 30))
plot(timestamp(2019, 06, 19, 09, 30, 15), color=color.lime)
plot(timestamp("GMT+3", 2019, 06, 19, 09, 30, 15), color=color.fuchsia)
plot(timestamp("Feb 01 2020 22:10:05"))
plot(timestamp("2011-10-10T14:48:00"))
plot(timestamp("04 Dec 1995 00:12:00 GMT+5"))
```

---

## weekofyear()

### Syntax

```pine
weekofyear(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_weekofyear).*

### Returns
Week of year (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970. Note that this function returns the week based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00) this value can be lower by 1 than the week of the trading day.

---

## year()

### Syntax

```pine
year(time, timezone) → series int
```

### Arguments

- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*, default `syminfo.timezone`) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is [syminfo.timezone](https://www.tradingview.com/pine-script-reference/v6/#var_syminfo.timezone).

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_year).*

### Returns
Year (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970. Note that this function returns the year based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00 UTC-4) this value can be lower by 1 than the year of the trading day.

---

# Keywords

## and

Logical AND. Applicable to boolean expressions.

### Syntax

```pine
<booleanExpression1> and <booleanExpression2>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

### Remarks
If expr1 evaluates to false, the and operator returns false without evaluating expr2.

---

## enum

This keyword allows the creation of an enumeration, enum for short. Enums are unique constructs that hold groups of predefined constants.

### Syntax

```pine
enum EnumName
    field_name1
    field_name2 = "Display Title"
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("Session highlight", overlay = true)

//@enum       Contains fields with popular timezones as titles.
//@field exch Has an empty string as the title to represent the chart timezone.
enum tz
    utc  = "UTC"
    exch = ""
    ny   = "America/New_York"
    chi  = "America/Chicago"
    lon  = "Europe/London"
    tok  = "Asia/Tokyo"

//@variable The session string.
selectedSession = input.session("1200-1500", "Session")
//@variable The selected timezone. The input's dropdown contains the fields in the `tz` enum.
selectedTimezone = input.enum(tz.utc, "Session Timezone")

//@variable Is `true` if the current bar's time is in the specified session.
bool inSession = false
if not na(time("", selectedSession, str.tostring(selectedTimezone)))
    inSession := true

// Highlight the background when `inSession` is `true`.
bgcolor(inSession ? color.new(color.green, 90) : na, title = "Active session highlight")

//@version=6
indicator("Map with enum keys")

//@enum        Contains fields with titles representing ticker IDs.
//@field aapl  Has an Apple ticker ID as its title.
//@field tsla  Has a Tesla ticker ID as its title.
//@field amzn  Has an Amazon ticker ID as its title.
enum symbols
    aapl = "NASDAQ:AAPL"
    tsla = "NASDAQ:TSLA"
    amzn = "NASDAQ:AMZN"

//@variable A map that accepts fields from the `symbols` enum as keys and "float" values.
map<symbols, float> data = map.new<symbols, float>()
// Put key-value pairs into the `data` map.
data.put(symbols.aapl, request.security(str.tostring(symbols.aapl), timeframe.period, close))
data.put(symbols.tsla, request.security(str.tostring(symbols.tsla), timeframe.period, close))
data.put(symbols.amzn, request.security(str.tostring(symbols.amzn), timeframe.period, close))
// Plot the value from the `data` map accessed by the `symbols.aapl` key.
plot(data.get(symbols.aapl))
```

---

## export

Used in libraries to prefix the declaration of functions or user-defined type definitions that will be available from other scripts importing the library.

### Syntax

```pine
export [method] <functionName>(<paramType> <paramName> [= <defaultValue>], …) =>
    <functionBlock>

export <type> <typeName>
    <propertyType> <propertyName> [= <value>]
    …
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Each library must have at least one exported function or user-defined type (UDT). Exported functions cannot use variables from the global scope if they are arrays, mutable variables (reassigned with :=), or variables of 'input' form. Exported functions cannot use request.*() functions. Exported functions must explicitly declare each parameter's type and all parameters must be used in the function's body. By default, all arguments passed to exported functions are of the series form, unless they are explicitly specified as simple in the function's signature. The @description, @function, @param, @type, @field, and @returns compiler annotations are used to automatically generate the library's description and release notes, and in the Pine Script® Editor's tooltips.

### Code Example
```pine
//@version=6
//@description Library of debugging functions.
library("Debugging_library", overlay = true)
//@function Displays a string as a table cell for debugging purposes.
//@param txt String to display.
//@returns Void.
export print(string txt) => 
    var table t = table.new(position.middle_right, 1, 1)
    table.cell(t, 0, 0, txt, bgcolor = color.yellow)
// Using the function from inside the library to show an example on the published chart.
// This has no impact on scripts using the library.
print("Library Test")
```

---

## for

Creates a count-controlled loop, which uses a counter variable to manage the iterative executions of its local code block. The loop continues new iterations until the counter reaches a specified final value.

### Syntax

```pine
[var_declaration =] for counter = from_num to to_num [by step_num]
    statements | continue | break
    return_expression
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Modifying a loop's to_num value during an iteration does not change the direction of the loop's counter. For a loop that counts upward, setting the to_num to a value less than the from_num value on an iteration stops the loop immediately after that iteration ends. Likewise, a loop that counts downward stops after an iteration where the to_num value becomes greater than the from_num value.

### Code Example
```pine
//@version=6
indicator("Basic `for` loop")

//@function Calculates the number of bars in the last `length` bars that have their `close` above the current `close`.
//@param length The number of bars used in the calculation.
greaterCloseCount(length) =>
    int result = 0
    for i = 1 to length
        if close[i] > close
            result += 1
    result

plot(greaterCloseCount(14))

//@version=6
indicator("`for` loop with a step")

a = array.from(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
sum = 0.0

for i = 0 to 9 by 5
    // Because the step is set to 5, we are adding only the first (0) and the sixth (5) value from the array `a`.
    sum += array.get(a, i)

plot(sum)
```

---

## for...in

The for...in structure allows the repeated execution of a number of statements for each element in an array. It can be used with either one argument: array_element, or with two: [index, array_element]. The second form doesn't affect the functionality of the loop. It tracks the current iteration's index in the tuple's first variable.

### Syntax

```pine
[var_declaration =] for array_element in array_id
    statements | continue | break
    return_expression

[var_declaration =] for [index, array_element] in array_id
    statements | continue | break
    return_expression
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("for...in")
// Here we determine on each bar how many of the bar's OHLC values are greater than the SMA of 'close' values
float[] ohlcValues = array.from(open, high, low, close)
qtyGreaterThan(value, array) =>
    int result = 0
    for currentElement in array
        if currentElement > value
            result += 1
        result
plot(qtyGreaterThan(ta.sma(close, 20), ohlcValues))

//@version=6
indicator("for...in")
var valuesArray = array.from(4, -8, 11, 78, -16, 34, 7, 99, 0, 55)
var isPos = array.new_bool(10, false)

for [index, value] in valuesArray
    if value > 0
        array.set(isPos, index, true)

if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(isPos))

//@version=6
indicator("`for ... in` matrix Example")

// Create a 2x3 matrix with values `4`.
matrix1 = matrix.new<int>(2, 3, 4)

sum = 0.0
// Loop through every row of the matrix.
for rowArray in matrix1
    // Sum values of the every row 
    sum += array.sum(rowArray)

plot(sum)
```

---

## if

If statement defines what block of statements must be executed when conditions of the expression are satisfied.

### Syntax

```pine
[variable_declaration = ] if boolean_expression
        …
    [else if boolean_expression
        … ]
    [else
        …
        return_expression]
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("if")
// This code compiles
x = if close > open
    close
else
    open

// This code doesn’t compile
// y = if close > open
//     close
// else
//     "open"
plot(x)

//@version=6
indicator("if")
x = if close > open
    close
// If current close > current open, then x = close.
// Otherwise the x = na.
plot(x)

//@version=6
indicator("if")
x = if open > close
    5
else if high > low
    close
else
    open
plot(x)

//@version=6
strategy("if")
if (ta.crossover(high, low))
    strategy.entry("BBandLE", strategy.long, stop=low, oca_name="BollingerBands", oca_type=strategy.oca.cancel, comment="BBandLE")
else
    strategy.cancel(id="BBandLE")

//@version=6
indicator("if")
float x = na
if close > open
    if close > close[1]
        x := close
    else
        x := close[1]
else
    x := open
plot(x)
```

---

## import

Used to load an external library into a script and bind its functions to a namespace. The importing script can be an indicator, a strategy, or another library. A library must be published (privately or publicly) before it can be imported.

### Syntax

```pine
import {username}/{libraryName}/{libraryVersion} as {alias}
```

### Arguments

- `username` (*literal string*) — User name of the library’s author.
- `libraryName` (*literal string*) — Name of the imported library, which corresponds to the `title` argument used by the author in his library script.
- `libraryVersion` (*literal int*) — Version number of the imported library.
- `alias` (*literal string*, optional, default `'libraryname'`) — Namespace used to refer to the library’s functions. Optional. The default is the libraryName string.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Using an alias that replaces a built-in namespace such as math.* or strategy.* is allowed, but if the library contains function names that shadow Pine Script®'s built-in functions, the built-ins will become unavailable. The same version of a library can only be imported once. Aliases must be distinct for each imported library. When calling library functions, casting their arguments to types other than their declared type is not allowed. An import statement cannot use 'as' or 'import' as username, libraryName, or alias identifiers.

### Code Example
```pine
//@version=6
indicator("num_methods import")
// Import the first version of the username’s "num_methods" library and assign it to the "m" namespace",
import username/num_methods/1 as m
// Call the “sinh()” function from the imported library
y = m.sinh(3.14)
// Plot value returned by the "sinh()" function",
plot(y)
```

---

## method

This keyword is used to prefix a function declaration, indicating it can then be invoked using dot notation by appending its name to a variable of the type of its first parameter and omitting that first parameter. Alternatively, functions declared as methods can also be invoked like normal user-defined functions. In that case, an argument must be supplied for its first parameter.

### Syntax

```pine
[export] method <functionName>(<paramType> <paramName> [= <defaultValue>], …) =>
    <functionBlock>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("")

var prices = array.new<float>()

//@function Pushes a new value into the array and removes the first one if the resulting array is greater than `maxSize`. Can be used as a method.
method maintainArray(array<float> id, maxSize, value) =>
    id.push(value)
    if id.size() > maxSize
        id.shift()

prices.maintainArray(50, close)
// The method can also be called like a function, without using dot notation.
// In this case an argument must be supplied for its first parameter.
// maintainArray(prices, 50, close)

// This calls the `array.avg()` built-in using dot notation with the `prices` array.
// It is possible because built-in functions belonging to some namespaces that are a special Pine type
// can be invoked with method notation when the function's first parameter is an ID of that type.
// Those namespaces are: `array`, `matrix`, `line`, `linefill`, `label`, `box`, and `table`.
plot(prices.avg())
```

---

## not

Logical negation (NOT). Applicable to boolean expressions.

### Syntax

```pine
not <booleanExpression>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

---

## or

Logical OR. Applicable to boolean expressions.

### Syntax

```pine
<booleanExpression1> or <booleanExpression2>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

### Remarks
If expr1 evaluates to true, the or operator returns true without evaluating expr2.

---

## switch

The switch operator transfers control to one of the several statements, depending on the values of a condition and expressions.

### Syntax

```pine
[variable_declaration = ] switch expression
    value1 => local_block
    value2 => local_block
    …
    => default_local_block

[variable_declaration = ] switch
    boolean_expression1 => local_block
    boolean_expression2 => local_block
    …
    => default_local_block
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
The value of the last expression in the local block of statements that is executed.

### Remarks
Only one of the local_block instances or the default_local_block can be executed. The default_local_block is introduced with the => token alone and is only executed when none of the preceding blocks are executed. If the result of the switch statement is assigned to a variable and a default_local_block is not specified, the statement returns na if no local_block is executed. When assigning the result of the switch statement to a variable, all local_block instances must return the same type of value.

### Code Example
```pine
//@version=6
indicator("Switch using an expression")

string i_maType = input.string("EMA", "MA type", options = ["EMA", "SMA", "RMA", "WMA"])

float ma = switch i_maType
    "EMA" => ta.ema(close, 10)
    "SMA" => ta.sma(close, 10)
    "RMA" => ta.rma(close, 10)
    // Default used when the three first cases do not match.
    => ta.wma(close, 10)

plot(ma)

//@version=6
strategy("Switch without an expression", overlay = true)

bool longCondition  = ta.crossover( ta.sma(close, 14), ta.sma(close, 28))
bool shortCondition = ta.crossunder(ta.sma(close, 14), ta.sma(close, 28))

switch
    longCondition  => strategy.entry("Long ID", strategy.long)
    shortCondition => strategy.entry("Short ID", strategy.short)
```

---

## type

This keyword allows the declaration of user-defined types (UDT) from which scripts can instantiate objects. UDTs are composite types that contain an arbitrary number of fields of any built-in or user-defined type, including the defined UDT itself. The syntax to define a UDT is:

### Syntax

```pine
[export ]type <UDT_identifier>
    [varip ]<field_type> <field_name> [= <value>]
    …
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("Multi Time Period Chart", overlay = true)

timeframeInput = input.timeframe("1D")

type bar
    float o = open
    float h = high
    float l = low
    float c = close
    int   t = time

drawBox(bar b, right) =>
    bar s = bar.new()
    color boxColor = b.c >= b.o ? color.green : color.red
    box.new(b.t, b.h, right, b.l, boxColor, xloc = xloc.bar_time, bgcolor = color.new(boxColor, 90))

updateBox(box boxId, bar b) =>
    color boxColor = b.c >= b.o ? color.green : color.red
    box.set_border_color(boxId, boxColor)
    box.set_bgcolor(boxId, color.new(boxColor, 90))
    box.set_top(boxId, b.h)
    box.set_bottom(boxId, b.l)
    box.set_right(boxId, time)

secBar = request.security(syminfo.tickerid, timeframeInput, bar.new())

if not na(secBar)
    // To avoid a runtime error, only process data when an object exists.
    if not barstate.islast
        if timeframe.change(timeframeInput)
            // On historical bars, draw a new box in the past when the HTF closes.
            drawBox(secBar, time[1])
    else
        var box lastBox = na
        if na(lastBox) or timeframe.change(timeframeInput)
            // On the last bar, only draw a new current box the first time we get there or when HTF changes.
            lastBox := drawBox(secBar, time)
        else
            // On other chart updates, use setters to modify the current box.
            updateBox(lastBox, secBar)
```

---

## var

var is the keyword used for assigning and one-time initializing of the variable.

### Syntax

```pine
var variable_name = expression
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("Var keyword example")
var a = close
var b = 0.0
var c = 0.0
var green_bars_count = 0
if close > open
    var x = close
    b := x
    green_bars_count := green_bars_count + 1
    if green_bars_count >= 10
        var y = close
        c := y
plot(a)
plot(b)
plot(c)
```

---

## varip

varip (var intrabar persist) is the keyword used for the assignment and one-time initialization of a variable or a field of a user-defined type. It’s similar to the var keyword, but variables and fields declared with varip retain their values between executions of the script on the same bar.

### Syntax

```pine
varip [<variable_type> ]<variable_name> = <expression>

[export ]type <UDT_identifier>
    varip <field_type> <field_name> [= <value>]
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
When using varip to declare variables in strategies that may execute more than once per historical chart bar, the values of such variables are preserved across successive iterations of the script on the same bar. The effect of varip eliminates the rollback of variables before each successive execution of a script on the same bar.

### Code Example
```pine
//@version=6
indicator("varip")
varip int v = -1
v := v + 1
plot(v)

//@version=6
indicator("varip with types")
type barData
    int index = -1
    varip int ticks = -1

var currBar = barData.new()
currBar.index += 1
currBar.ticks += 1

// Will be equal to bar_index on all bars
plot(currBar.index)
// In real time, will increment per every tick on the chart
plot(currBar.ticks)
```

---

## while

The while statement allows the conditional iteration of a local code block.

### Syntax

```pine
variable_declaration = while boolean_expression
    …
    continue
    …
    break
    …
    return_expression
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
The local code block after the initial while line must be indented with four spaces or a tab. For the while loop to terminate, the boolean expression following while must eventually become false, or a break must be executed.

### Code Example
```pine
//@version=6
indicator("while")
// This is a simple example of calculating a factorial using a while loop.
int i_n = input.int(10, "Factorial Size", minval=0)
int counter   = i_n
int factorial = 1
while counter > 0
    factorial := factorial * counter
    counter   := counter - 1

plot(factorial)
```

---

# Types

## array

Keyword used to explicitly declare the "array" type of a variable or a parameter. Array objects (or IDs) can be created with the array.new<type>, array.from function.

### Remarks
Array objects are always of "series" form.

### Code Example
```pine
//@version=6
indicator("array", overlay=true)
array<float> a = na
a := array.new<float>(1, close)
plot(array.get(a, 0))
```

---

## bool

Keyword used to explicitly declare the "bool" (boolean) type of a variable or a parameter. "Bool" variables can have values true or false.

### Syntax

```pine
bool
bool(x) → series bool
```

### Arguments

- `x` (*series color*) — 'na' to cast to color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Explicitly mentioning the type in a variable declaration is optional. Learn more about Pine Script® types in the User Manual page on the Type System.

### Code Example
```pine
//@version=6
indicator("bool")
bool b = true    // Same as `b = true`
plot(b ? open : close)
```

---

## box

Keyword used to explicitly declare the "box" type of a variable or a parameter. Box objects (or IDs) can be created with the box.new function.

### Syntax

```pine
box
box(x) → series box
```

### Arguments

- `x` (*series box*) — 'na' to cast to box.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Box objects are always of "series" form.

### Code Example
```pine
//@version=6
indicator("box")
// Empty `box1` box ID.
var box box1 = na
// `box` type is unnecessary because `box.new()` returns a "box" type.
var box2 = box.new(na, na, na, na)
box3 = box.new(time, open, time + 60 * 60 * 24, close, xloc=xloc.bar_time)
```

---

## chart.point

Keyword to explicitly declare the type of a variable or parameter as chart.point. Scripts can produce chart.point instances using the chart.point.from_time, chart.point.from_index, chart.point.now, and chart.point.new functions.

---

### Syntax

```pine
chart.point
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

## color

Keyword used to explicitly declare the "color" type of a variable or a parameter.

### Syntax

```pine
color
color(x) → series color
```

### Arguments

- `x` (*series color*) — 'na' to cast to color.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Color literals have the following format: #RRGGBB or #RRGGBBAA. The letter pairs represent 00 to FF hexadecimal values (0 to 255 in decimal) where RR, GG and BB pairs are the values for the color's red, green and blue components. AA is an optional value for the color's transparency (or alpha component) where 00 is invisible and FF opaque. When no AA pair is supplied, FF is used. The hexadecimal letters can be upper or lower case. Explicitly mentioning the type in a variable declaration is optional, except when it is initialized with na. Learn more about Pine Script® types in the User Manual page on the Type System.

### Code Example
```pine
//@version=6
indicator("color", overlay = true)

color textColor = color.green
color labelColor = #FF000080 // Red color (FF0000) with 50% transparency (80 which is half of FF).
if barstate.islastconfirmedhistory
    label.new(bar_index, high, text = "Label", color = labelColor, textcolor = textColor)

// When declaring variables with color literals, built-in constants(color.green) or functions (color.new(), color.rgb()), the "color" keyword for the type can be omitted.
c = color.rgb(0,255,0,0)
plot(close, color = c)
```

---

## const

The const keyword explicitly assigns the "const" type qualifier to variables and the parameters of non-exported functions. Variables and parameters with the "const" qualifier reference values established at compile time that never change in the script's execution.

### Remarks
To learn more, see our User Manual's section on type qualifiers.

### Code Example
```pine
//@version=6
indicator("custom plot title")

//@function Concatenates two "const string" values.
concatStrings(const string x, const string y) =>
    const string result = x + y

//@variable The title of the plot.
const string myTitle = concatStrings("My ", "Plot")

plot(close, myTitle)

//@version=6
indicator("can't assign input to const")

//@variable A variable declared as "const float" that attempts to assign the result of `input.float()` as its value.
//          This declaration causes an error. The "input float" qualified type is stronger than "const float".
const float myVar = input.float(2.0)

plot(myVar)
```

---

## float

Keyword used to explicitly declare the "float" (floating point) type of a variable or a parameter.

### Syntax

```pine
float
float(x) → series float
```

### Arguments

- `x` (*series float*) — 'na' to cast to float.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Explicitly mentioning the type in a variable declaration is optional, except when it is initialized with na. Learn more about Pine Script® types in the User Manual page on the Type System.

### Code Example
```pine
//@version=6
indicator("float")
float f = 3.14    // Same as `f = 3.14`
f := na
plot(f)
```

---

## int

Keyword used to explicitly declare the "int" (integer) type of a variable or a parameter.

### Syntax

```pine
int
int(x) → series int
```

### Arguments

- `x` (*series int*) — 'na' to cast to int.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Explicitly mentioning the type in a variable declaration is optional, except when it is initialized with na. Learn more about Pine Script® types in the User Manual page on the Type System.

### Code Example
```pine
//@version=6
indicator("int")
int i = 14    // Same as `i = 14`
i := na
plot(i)
```

---

## label

Keyword used to explicitly declare the "label" type of a variable or a parameter. Label objects (or IDs) can be created with the label.new function.

### Syntax

```pine
label
label(x) → series label
```

### Arguments

- `x` (*series label*) — 'na' to cast to label..

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Label objects are always of "series" form.

### Code Example
```pine
//@version=6
indicator("label")
// Empty `label1` label ID.
var label label1 = na
// `label` type is unnecessary because `label.new()` returns "label" type.
var label2 = label.new(na, na, na)
if barstate.islastconfirmedhistory
    label3 = label.new(bar_index, high, text = "label3 text")
```

---

## line

Keyword used to explicitly declare the "line" type of a variable or a parameter. Line objects (or IDs) can be created with the line.new function.

### Syntax

```pine
line
line(x) → series line
```

### Arguments

- `x` (*series line*) — 'na' to cast to line..

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Line objects are always of "series" form.

### Code Example
```pine
//@version=6
indicator("line")
// Empty `line1` line ID.
var line line1 = na
// `line` type is unnecessary because `line.new()` returns "line" type.
var line2 = line.new(na, na, na, na)
line3 = line.new(bar_index - 1, high, bar_index, high, extend = extend.right)
```

---

## linefill

Keyword used to explicitly declare the "linefill" type of a variable or a parameter. Linefill objects (or IDs) can be created with the linefill.new function.

### Syntax

```pine
linefill
linefill(x) → series linefill
```

### Arguments

- `x` (*series linefill*) — 'na' to cast to linefill.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Linefill objects are always of "series" form.

### Code Example
```pine
//@version=6
indicator("linefill", overlay=true)
// Empty `linefill1` line ID.
var linefill linefill1 = na
// `linefill` type is unnecessary because `linefill.new()` returns "linefill" type.
var linefill2 = linefill.new(na, na, na)

if barstate.islastconfirmedhistory
    line1 = line.new(bar_index - 10, high+1, bar_index, high+1, extend = extend.right)
    line2 = line.new(bar_index - 10, low+1, bar_index, low+1, extend = extend.right)
    linefill3 = linefill.new(line1, line2, color = color.new(color.green, 80))
```

---

## map

Keyword used to explicitly declare the "map" type of a variable or a parameter. Map objects (or IDs) can be created with the map.new<type,type> function.

### Remarks
Map objects are always of series form.

### Code Example
```pine
//@version=6
indicator("map", overlay=true)
map<int, float> a = na
a := map.new<int, float>()
a.put(bar_index, close)
label.new(bar_index, a.get(bar_index), "Current close")
```

---

## matrix

Keyword used to explicitly declare the "matrix" type of a variable or a parameter. Matrix objects (or IDs) can be created with the matrix.new<type> function.

### Remarks
Matrix objects are always of "series" form.

### Code Example
```pine
//@version=6
indicator("matrix example")

// Create `m1` matrix of `int` type.
matrix<int> m1 = matrix.new<int>(2, 3, 0)

// `matrix<int>` is unnecessary because the `matrix.new<int>()` function returns an `int` type matrix object.
m2 = matrix.new<int>(2, 3, 0)

// Display matrix using a label.
if barstate.islastconfirmedhistory
    label.new(bar_index, high, str.tostring(m2))
```

---

## polyline

Keyword to explicitly declare the type of a variable or parameter as polyline. Scripts can produce polyline instances using the polyline.new function.

---

## series

The series keyword explicitly assigns the "series" type qualifier to variables and function parameters. Variables and parameters that use the "series" qualifier can reference values that change throughout a script's execution.

### Syntax

```pine
[series] <type> <variable_name> = <value>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
To learn more, see our User Manual's section on type qualifiers.

### Code Example
```pine
//@version=6
//@description A library with custom functions.
library("CustomFunctions", overlay = true)

//@function Finds the highest `source` value over `length` bars, filtered by the `cond` condition.
export conditionalHighest(series float source, series bool cond, series int length) =>
    //@variable The highest `source` value from when the `cond` was `true` over `length` bars.
    series float result = na
    // Loop to find the highest value.
    for i = 0 to length - 1
        if cond[i]
            value   = source[i]
            result := math.max(nz(result, value), value)
    // Return the `result`.
    result

//@variable Is `true` once every five bars.
series bool condition = bar_index % 5 == 0

//@variable The highest `close` value from every fifth bar over the last 100 bars.
series float hiValue = conditionalHighest(close, condition, 100)

plot(hiValue)
bgcolor(condition ? color.new(color.teal, 80) : na)

//@version=6
indicator("series variable not allowed")

//@variable A variable declared as "series int" with a value of 5.
series int myVar = 5

// This call causes an error.
// The `histbase` accepts "input int/float". It can't accept the stronger "series int" qualified type.
plot(close, style = plot.style_histogram, histbase = myVar)
```

---

## simple

The simple keyword explicitly assigns the "simple" type qualifier to variables and function parameters. Variables and parameters that use the "simple" qualifier can reference values established at the beginning of a script's execution that do not change later.

### Syntax

```pine
[simple] <type> <variable_name> = <value>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
To learn more, see our User Manual's section on type qualifiers.

### Code Example
```pine
//@version=6
//@description A library with custom functions.
library("CustomFunctions", overlay = true)

//@function         Calculates the length values for a ribbon of four EMAs by multiplying the `baseLength`.
//@param baseLength The initial EMA length. Requires "simple int" because you can't use "series int" in `ta.ema()`.
//@returns          A tuple of length values.
export ribbonLengths(simple int baseLength) =>
    simple int length1 = baseLength
    simple int length2 = baseLength * 2
    simple int length3 = baseLength * 3
    simple int length4 = baseLength * 4
    [length1, length2, length3, length4]

// Get a tuple of "simple int" length values.
[len1, len2, len3, len4] = ribbonLengths(14)

// Plot four EMAs using the values from the tuple.
plot(ta.ema(close, len1), "EMA 1", color = color.red)
plot(ta.ema(close, len2), "EMA 1", color = color.orange)
plot(ta.ema(close, len3), "EMA 1", color = color.green)
plot(ta.ema(close, len4), "EMA 1", color = color.blue)

//@version=6
indicator("can't change simple to series")

//@variable A variable declared as "simple float" with a value of 5.0.
simple float myVar = 5.0

// This reassignment causes an error.
// The `close` variable returns a "series float" value. Since `myVar` is restricted to "simple" values, it cannot
// change its qualifier to "series".
myVar := close

plot(myVar)
```

---

## string

Keyword used to explicitly declare the "string" type of a variable or a parameter.

### Syntax

```pine
string
string(x) → series string
```

### Arguments

- `x` (*series color*) — 'na' to cast to string.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
Explicitly mentioning the type in a variable declaration is optional, except when it is initialized with na. Learn more about Pine Script® types in the User Manual page on the Type System.

### Code Example
```pine
//@version=6
indicator("string")
string s = "Hello World!"    // Same as `s = "Hello world!"`
// string s = na // same as "" 
plot(na, title=s)
```

---

## table

Keyword used to explicitly declare the "table" type of a variable or a parameter. Table objects (or IDs) can be created with the table.new function.

### Syntax

```pine
table
table(x) → series table
```

### Arguments

- `x` (*series table*) — 'na' to cast to table.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("table")
// Empty `table1` table ID.
var table table1 = na
// `table` type is unnecessary because `table.new()` returns "table" type.
var table2 = table.new(position.top_left, na, na)

if barstate.islastconfirmedhistory
    var table3 = table.new(position = position.top_right, columns = 1, rows = 1, bgcolor = color.yellow, border_width = 1)
    table.cell(table_id = table3, column = 0, row = 0, text = "table3 text")
```

### Remarks
Table objects are always of "series" form.

# Operators

---

## -

Subtraction or unary minus. Applicable to numerical expressions.

### Syntax

```pine
expr1 - expr2
- expr
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Returns integer or float value, or series of values:

### Remarks
You may use arithmetic operators with numbers as well as with series variables. In case of usage with series the operators are applied elementwise.

---

## -=

Subtraction assignment. Applicable to numerical expressions.

### Syntax

```pine
expr1 -= expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Integer or float value, or series of values.

### Code Example
```pine
//@version=6
indicator("-=")
// Equals to expr1 = expr1 - expr2.
a = 2
b = 3
a -= b
// Result: a = -1.
plot(a)
```

---

## :=

Reassignment operator. It is used to assign a new value to a previously declared variable.

### Syntax

```pine
<var_name> := <new_value>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("My script")

myVar = 10

if close > open
    // Modifies the existing global scope `myVar` variable by changing its value from 10 to 20.
    myVar := 20
    // Creates a new `myVar` variable local to the `if` condition and unreachable from the global scope.
    // Does not affect the `myVar` declared in global scope.
    myVar = 30

plot(myVar)
```

---

## !=

Not equal to. Applicable to expressions of any type.

### Syntax

```pine
expr1 != expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

---

## ?:

Ternary conditional operator.

### Syntax

```pine
expr1 ? expr2 : expr3
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
expr2 if expr1 is evaluated to true, expr3 otherwise. Zero value (0 and also NaN, +Infinity, -Infinity) is considered to be false, any other value is true.

### Remarks
Use na for 'else' branch if you do not need it. You can combine two or more ?: operators to achieve the equivalent of a 'switch'-like statement (see examples above). You may use arithmetic operators with numbers as well as with series variables. In case of usage with series the operators are applied elementwise.

### Code Example
```pine
//@version=6
indicator("?:")
// Draw circles at the bars where open crosses close
s2 = ta.cross(open, close) ? math.avg(open,close) : na
plot(s2, style=plot.style_circles, linewidth=2, color=color.red)

// Combination of ?: operators for 'switch'-like logic
c = timeframe.isintraday ? color.red : timeframe.isdaily ? color.green : timeframe.isweekly ? color.blue : color.gray
plot(hl2, color=c)
```

---

## []

Series subscript. Provides access to previous values of series expr1. expr2 is the number of bars back, and must be numerical. Floats will be rounded down.

### Syntax

```pine
expr1[expr2]
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
A series of values.

### Code Example
```pine
//@version=6
indicator("[]")
// [] can be used to "save" variable value between bars
a = 0.0 // declare `a`
a := a[1] // immediately set current value to the same as previous. `na` in the beginning of history
if high == low // if some condition - change `a` value to another
    a := low
plot(a)
```

---

## *

Multiplication. Applicable to numerical expressions.

### Syntax

```pine
expr1 * expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Integer or float value, or series of values.

---

## *=

Multiplication assignment. Applicable to numerical expressions.

### Syntax

```pine
expr1 *= expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Integer or float value, or series of values.

### Code Example
```pine
//@version=6
indicator("*=")
// Equals to expr1 = expr1 * expr2.
a = 2
b = 3
a *= b
// Result: a = 6.
plot(a)
```

---

## /

Division. Applicable to numerical expressions.

### Syntax

```pine
expr1 / expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Integer or float value, or series of values.

---

## /=

Division assignment. Applicable to numerical expressions.

### Syntax

```pine
expr1 /= expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Integer or float value, or series of values.

### Code Example
```pine
//@version=6
indicator("/=")
// Equals to expr1 = expr1 / expr2.
float a = 3.0
b = 3
a /= b
// Result: a = 1.
plot(a)
```

---

## %

Modulo (integer remainder). Applicable to numerical expressions.

### Syntax

```pine
expr1 % expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Integer or float value, or series of values.

### Remarks
In Pine Script®, when the integer remainder is calculated, the quotient is truncated, i.e. rounded towards the lowest absolute value. The resulting value will have the same sign as the dividend. Example: -1 % 9 = -1 - 9 * int(-1/9) = -1 - 9 * int(-0.111) = -1 - 9 * 0 = -1.

---

## %=

Modulo assignment. Applicable to numerical expressions.

### Syntax

```pine
expr1 %= expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Integer or float value, or series of values.

### Code Example
```pine
//@version=6
indicator("%=")
// Equals to expr1 = expr1 % expr2.
a = 3
b = 3
a %= b
// Result: a = 0.
plot(a)
```

---

## +

Addition or unary plus. Applicable to numerical expressions or strings.

### Syntax

```pine
expr1 + expr2
+ expr
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Binary + for strings returns concatenation of expr1 and expr2

### Remarks
You may use arithmetic operators with numbers as well as with series variables. In case of usage with series the operators are applied elementwise.

---

## +=

Addition assignment. Applicable to numerical expressions or strings.

### Syntax

```pine
expr1 += expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
For strings returns concatenation of expr1 and expr2. For numbers returns integer or float value, or series of values.

### Remarks
You may use arithmetic operators with numbers as well as with series variables. In case of usage with series the operators are applied elementwise.

### Code Example
```pine
//@version=6
indicator("+=")
// Equals to expr1 = expr1 + expr2.
a = 2
b = 3
a += b
// Result: a = 5.
plot(a)
```

---

## <

Less than. Applicable to numerical expressions.

### Syntax

```pine
expr1 < expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

---

## <=

Less than or equal to. Applicable to numerical expressions.

### Syntax

```pine
expr1 <= expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

---

## ==

Equal to. Applicable to expressions of any type.

### Syntax

```pine
expr1 == expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

---

## =>

The '=>' operator is used in user-defined function declarations and in switch statements.

### Syntax

```pine
<identifier>([<parameter_name>[=<default_value>]], ...) =>
    <local_block>
    <function_result>
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Remarks
You can learn more about user-defined functions in the User Manual's pages on Declaring functions and Libraries.

### Code Example
```pine
//@version=6
indicator("=>")
// single-line function
f1(x, y) => x + y
// multi-line function
f2(x, y) => 
    sum = x + y
    sumChange = ta.change(sum, 10)
    // Function automatically returns the last expression used in it
plot(f1(30, 8) + f2(1, 3))
```

---

## >

Greater than. Applicable to numerical expressions.

### Syntax

```pine
expr1 > expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

---

## >=

Greater than or equal to. Applicable to numerical expressions.

### Syntax

```pine
expr1 >= expr2
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Returns
Boolean value, or series of boolean values.

---
# Annotations

## @description

Sets a custom description for scripts that use the library declaration statement. The text provided with this annotation will be used to pre-fill the "Description" field in the publication dialogue.

### Code Example
```pine
//@version=6
// @description Provides a tool to quickly output a label on the chart.
library("MyLibrary")

// @function Outputs a label with `labelText` on the bar's high.
// @param labelText (series string) The text to display on the label.
// @returns Drawn label.
export drawLabel(string labelText) =>
    label.new(bar_index, high, text = labelText)
```

---

## @enum

If placed above an enum declaration, it adds a custom description for the enum. The Pine Editor's autosuggest uses this description and displays it when a user hovers over the enum name. When used in library scripts, the descriptions of all enums using the export keyword will pre-fill the "Description" field in the publication dialogue.

### Syntax

```pine
//@enum EnumName
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/).*

### Code Example
```pine
//@version=6
indicator("Session highlight", overlay = true)

//@enum       Contains fields with popular timezones as titles.
//@field exch Has an empty string as the title to represent the chart timezone.
enum tz
    utc  = "UTC"
    exch = ""
    ny   = "America/New_York"
    chi  = "America/Chicago"
    lon  = "Europe/London"
    tok  = "Asia/Tokyo"

//@variable The session string.
selectedSession = input.session("1200-1500", "Session")
//@variable The selected timezone. The input's dropdown contains the fields in the `tz` enum.
selectedTimezone = input.enum(tz.utc, "Session Timezone")

//@variable Is `true` if the current bar's time is in the specified session.
bool inSession = false
if not na(time("", selectedSession, str.tostring(selectedTimezone)))
    inSession := true

// Highlight the background when `inSession` is `true`.
bgcolor(inSession ? color.new(color.green, 90) : na, title = "Active session highlight")
```

---

## @field

If placed above a type or enum declaration, it adds a custom description for a field of the type/enum. After the annotation, users should specify the field name, followed by its description.

### Code Example
```pine
//@version=6
indicator("New high over the last 20 bars", overlay = true)

//@type A point on a chart.
//@field index The index of the bar where the point is located, i.e., its `x` coordinate.
//@field price The price where the point is located, i.e., its `y` coordinate.
type Point
    int index
    float price

//@variable If the current `high` is the highest over the last 20 bars, returns a new `Point` instance, `na` otherwise.
Point highest = na

if ta.highestbars(high, 20) == 0
    highest := Point.new(bar_index, high)
    label.new(highest.index, highest.price, str.tostring(highest.price))
```

---

## @function

If placed above a function declaration, it adds a custom description for the function.

### Code Example
```pine
//@version=6
// @description Provides a tool to quickly output a label on the chart.
library("MyLibrary")

// @function Outputs a label with `labelText` on the bar's high.
// @param labelText (series string) The text to display on the label.
// @returns Drawn label.
export drawLabel(string labelText) =>
    label.new(bar_index, high, text = labelText)
```

---

## @param

If placed above a function declaration, it adds a custom description for a function parameter. After the annotation, users should specify the parameter name, then its description.

### Code Example
```pine
//@version=6
// @description Provides a tool to quickly output a label on the chart.
library("MyLibrary")

// @function Outputs a label with `labelText` on the bar's high.
// @param labelText (series string) The text to display on the label.
// @returns Drawn label.
export drawLabel(string labelText) =>
    label.new(bar_index, high, text = labelText)
```

---

## @returns

If placed above a function declaration, it adds a custom description for what that function returns.

### Code Example
```pine
//@version=6
// @description Provides a tool to quickly output a label on the chart.
library("MyLibrary")

// @function Outputs a label with `labelText` on the bar's high.
// @param labelText (series string) The text to display on the label.
// @returns Drawn label.
export drawLabel(string labelText) =>
    label.new(bar_index, high, text = labelText)
```

---

## @strategy_alert_message

If used within a strategy script, it provides a default message to pre-fill the "Message" field in the alert creation dialogue.

### Code Example
```pine
//@version=6
strategy("My strategy", overlay=true, margin_long=100, margin_short=100)
//@strategy_alert_message Strategy alert on symbol {{ticker}}

longCondition = ta.crossover(ta.sma(close, 14), ta.sma(close, 28))
if (longCondition)
    strategy.entry("My Long Entry Id", strategy.long)
strategy.exit("Exit", "My Long Entry Id", profit = 10 / syminfo.mintick, loss = 10 / syminfo.mintick)
```

---

## @type

If placed above a type declaration, it adds a custom description for the type.

### Code Example
```pine
//@version=6
indicator("New high over the last 20 bars", overlay = true)

//@type A point on a chart.
//@field index The index of the bar where the point is located, i.e., its `x` coordinate.
//@field price The price where the point is located, i.e., its `y` coordinate.
type Point
    int index
    float price

//@variable If the current `high` is the highest over the last 20 bars, returns a new `Point` instance, `na` otherwise.
Point highest = na

if ta.highestbars(high, 20) == 0
    highest := Point.new(bar_index, high)
    label.new(highest.index, highest.price, str.tostring(highest.price))
```

---

## @variable

If placed above a variable declaration, it adds a custom description for the variable.

### Code Example
```pine
//@version=6
indicator("New high over the last 20 bars", overlay = true)

//@type A point on a chart.
//@field index The index of the bar where the point is located, i.e., its `x` coordinate.
//@field price The price where the point is located, i.e., its `y` coordinate.
type Point
    int index
    float price

//@variable If the current `high` is the highest over the last 20 bars, returns a new `Point` instance, `na` otherwise.
Point highest = na

if ta.highestbars(high, 20) == 0
    highest := Point.new(bar_index, high)
    label.new(highest.index, highest.price, str.tostring(highest.price))
```

---

## @version=

Specifies the Pine Script® version that the script will use. The number in this annotation should not be confused with the script's version number, which updates on every saved change to the code.

### Remarks
The version should always be specified. Otherwise, for compatibility reasons, the script will be compiled using Pine Script® v1, which lacks most of the newer features and is bound to confuse. This annotation can be anywhere within a script, but we recommend placing it at the top of the code for readability.

### Code Example
```pine
//@version=6
indicator("Pine v6 Indicator")
plot(close)

//This indicator has no version annotation, so it will try to use v1.
//Pine Script® v1 has no function named `indicator()`, so the script will not compile.
indicator("Pine v1 Indicator")
plot(close)
```

---
