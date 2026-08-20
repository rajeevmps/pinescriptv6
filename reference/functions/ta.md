<!--
Source: https://www.tradingview.com/pine-script-reference/v6/
Pine Script v6 — official TradingView language reference manual
Retrieved: 2026-08-20
-->

# Technical analysis functions

Moving averages, oscillators, pivots, and every other `ta.*` study built into Pine Script v6.

**59 functions** · Source: [Pine Script® v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/)

## Index

- [`ta.alma()`](#taalma)
- [`ta.atr()`](#taatr)
- [`ta.barssince()`](#tabarssince)
- [`ta.bb()`](#tabb)
- [`ta.bbw()`](#tabbw)
- [`ta.cci()`](#tacci)
- [`ta.change()`](#tachange)
- [`ta.cmo()`](#tacmo)
- [`ta.cog()`](#tacog)
- [`ta.correlation()`](#tacorrelation)
- [`ta.cross()`](#tacross)
- [`ta.crossover()`](#tacrossover)
- [`ta.crossunder()`](#tacrossunder)
- [`ta.cum()`](#tacum)
- [`ta.dev()`](#tadev)
- [`ta.dmi()`](#tadmi)
- [`ta.ema()`](#taema)
- [`ta.falling()`](#tafalling)
- [`ta.highest()`](#tahighest)
- [`ta.highestbars()`](#tahighestbars)
- [`ta.hma()`](#tahma)
- [`ta.kc()`](#takc)
- [`ta.kcw()`](#takcw)
- [`ta.linreg()`](#talinreg)
- [`ta.lowest()`](#talowest)
- [`ta.lowestbars()`](#talowestbars)
- [`ta.macd()`](#tamacd)
- [`ta.max()`](#tamax)
- [`ta.median()`](#tamedian)
- [`ta.mfi()`](#tamfi)
- [`ta.min()`](#tamin)
- [`ta.mode()`](#tamode)
- [`ta.mom()`](#tamom)
- [`ta.percentile_linear_interpolation()`](#tapercentilelinearinterpolation)
- [`ta.percentile_nearest_rank()`](#tapercentilenearestrank)
- [`ta.percentrank()`](#tapercentrank)
- [`ta.pivot_point_levels()`](#tapivotpointlevels)
- [`ta.pivothigh()`](#tapivothigh)
- [`ta.pivotlow()`](#tapivotlow)
- [`ta.range()`](#tarange)
- [`ta.rci()`](#tarci)
- [`ta.rising()`](#tarising)
- [`ta.rma()`](#tarma)
- [`ta.roc()`](#taroc)
- [`ta.rsi()`](#tarsi)
- [`ta.sar()`](#tasar)
- [`ta.sma()`](#tasma)
- [`ta.stdev()`](#tastdev)
- [`ta.stoch()`](#tastoch)
- [`ta.supertrend()`](#tasupertrend)
- [`ta.swma()`](#taswma)
- [`ta.tr()`](#tatr)
- [`ta.tsi()`](#tatsi)
- [`ta.valuewhen()`](#tavaluewhen)
- [`ta.variance()`](#tavariance)
- [`ta.vwap()`](#tavwap)
- [`ta.vwma()`](#tavwma)
- [`ta.wma()`](#tawma)
- [`ta.wpr()`](#tawpr)

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

## ta.rci()

Calculates the Rank Correlation Index (RCI), which measures the directional consistency of price movements. It evaluates the monotonic relationship between a source series and the bar index over length bars using Spearman's rank correlation coefficient. The resulting value is scaled to a range of -100 to 100, where 100 indicates the source consistently increased over the period, and -100 indicates it consistently decreased. Values between -100 and 100 reflect varying degrees of upward or downward consistency.

### Returns
The Rank Correlation Index, a value between -100 to 100.

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
