<!--
Source: https://www.tradingview.com/pine-script-reference/v6/
Pine Script v6 — official TradingView language reference manual
Retrieved: 2026-08-20
-->

# General functions (math, strings, inputs, time, alerts)

Math, string handling, user inputs, time conversion, alerts, logging, and the script declaration statements.

**94 functions** · Source: [Pine Script® v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/)

## Index

- [`alert()`](#alert)
- [`alertcondition()`](#alertcondition)
- [`bool()`](#bool)
- [`color()`](#color)
- [`color.b()`](#colorb)
- [`color.from_gradient()`](#colorfromgradient)
- [`color.g()`](#colorg)
- [`color.new()`](#colornew)
- [`color.r()`](#colorr)
- [`color.rgb()`](#colorrgb)
- [`color.t()`](#colort)
- [`dayofmonth()`](#dayofmonth)
- [`dayofweek()`](#dayofweek)
- [`fixnan()`](#fixnan)
- [`float()`](#float)
- [`hour()`](#hour)
- [`indicator()`](#indicator)
- [`input()`](#input)
- [`input.bool()`](#inputbool)
- [`input.color()`](#inputcolor)
- [`input.enum()`](#inputenum)
- [`input.float()`](#inputfloat)
- [`input.int()`](#inputint)
- [`input.price()`](#inputprice)
- [`input.session()`](#inputsession)
- [`input.source()`](#inputsource)
- [`input.string()`](#inputstring)
- [`input.symbol()`](#inputsymbol)
- [`input.text_area()`](#inputtextarea)
- [`input.time()`](#inputtime)
- [`input.timeframe()`](#inputtimeframe)
- [`int()`](#int)
- [`library()`](#library)
- [`log.error()`](#logerror)
- [`log.info()`](#loginfo)
- [`log.warning()`](#logwarning)
- [`math.abs()`](#mathabs)
- [`math.acos()`](#mathacos)
- [`math.asin()`](#mathasin)
- [`math.atan()`](#mathatan)
- [`math.avg()`](#mathavg)
- [`math.ceil()`](#mathceil)
- [`math.cos()`](#mathcos)
- [`math.exp()`](#mathexp)
- [`math.floor()`](#mathfloor)
- [`math.log()`](#mathlog)
- [`math.log10()`](#mathlog10)
- [`math.max()`](#mathmax)
- [`math.min()`](#mathmin)
- [`math.pow()`](#mathpow)
- [`math.random()`](#mathrandom)
- [`math.round()`](#mathround)
- [`math.round_to_mintick()`](#mathroundtomintick)
- [`math.sign()`](#mathsign)
- [`math.sin()`](#mathsin)
- [`math.sqrt()`](#mathsqrt)
- [`math.sum()`](#mathsum)
- [`math.tan()`](#mathtan)
- [`math.todegrees()`](#mathtodegrees)
- [`math.toradians()`](#mathtoradians)
- [`max_bars_back()`](#maxbarsback)
- [`minute()`](#minute)
- [`month()`](#month)
- [`na()`](#na)
- [`nz()`](#nz)
- [`runtime.error()`](#runtimeerror)
- [`second()`](#second)
- [`str.contains()`](#strcontains)
- [`str.endswith()`](#strendswith)
- [`str.format()`](#strformat)
- [`str.format_time()`](#strformattime)
- [`str.length()`](#strlength)
- [`str.lower()`](#strlower)
- [`str.match()`](#strmatch)
- [`str.pos()`](#strpos)
- [`str.repeat()`](#strrepeat)
- [`str.replace()`](#strreplace)
- [`str.replace_all()`](#strreplaceall)
- [`str.split()`](#strsplit)
- [`str.startswith()`](#strstartswith)
- [`str.substring()`](#strsubstring)
- [`str.tonumber()`](#strtonumber)
- [`str.tostring()`](#strtostring)
- [`str.trim()`](#strtrim)
- [`str.upper()`](#strupper)
- [`string()`](#string)
- [`time()`](#time)
- [`time_close()`](#timeclose)
- [`timeframe.change()`](#timeframechange)
- [`timeframe.from_seconds()`](#timeframefromseconds)
- [`timeframe.in_seconds()`](#timeframeinseconds)
- [`timestamp()`](#timestamp)
- [`weekofyear()`](#weekofyear)
- [`year()`](#year)

---

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

## math.avg()

Calculates average of all given series (elementwise).

### Syntax

```pine
math.avg(number0, number1, ...) → series float
```

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_math.avg).*

### Returns
Average.

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

## runtime.error()

When called, causes a runtime error with the error message specified in the message argument.
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
