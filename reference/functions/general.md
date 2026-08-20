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
- `message` (*series string*) — The message to send when the alert occurs.
- `freq` (*input string*) — Optional. Determines the allowed frequency of the alert trigger. Possible values are: alert.freq_all (allows an alert on any realtime update), alert.freq_once_per_bar (allows an alert only on the first execution for each realtime bar), or alert.freq_once_per_bar_close (allows an alert only when a realtime bar closes). The default is alert.freq_once_per_bar.

### Example
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

### Remarks
The alert() function does not display information on the chart.
In contrast to alertcondition(), calls to this function do not count toward a script's plot count. Additionally, alert() calls are allowed in local scopes, including the scopes of exported library functions.
See this article in our Help Center to learn more about activating alerts from alert() calls.

### See also
`alertcondition()`

## alertcondition()
Creates alert condition, that is available in Create Alert dialog. Please note, that alertcondition() does NOT create an alert, it just gives you more options in Create Alert dialog. Also, alertcondition() effect is invisible on chart.

### Syntax
```pine
alertcondition(condition, title, message) → void
```

### Arguments
- `condition` (*series bool*) — Series of boolean values that is used for alert. True values mean alert fire, false - no alert. Required argument.
- `title` (*const string*) — Title of the alert condition. Optional argument.
- `message` (*const string*) — Message to display when alert fires. Optional argument.

### Example
```pine
//@version=6
indicator("alertcondition", overlay=true)
alertcondition(close >= open, title='Alert on Green Bar', message='Green Bar!')
```

### Remarks
Please note that an alertcondition call generates an additional plot. All such calls are taken into account when we calculate the number of the output series per script.

### See also
`alert()`

## bool()
Converts the x value to a bool value. Returns false if x is na, false, or an int/float value equal to 0. Returns true for all other possible values.

### Syntax & Overloads
```pine
bool(x) → const bool
```
```pine
bool(x) → input bool
```
```pine
bool(x) → simple bool
```
```pine
bool(x) → series bool
```

### Arguments
- `x` (*simple int/float/bool*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to bool.

### See also
`float()`, `int()`, `color()`, `string()`, `line()`, `label()`

## color()
Casts na to color

### Syntax & Overloads
```pine
color(x) → const color
```
```pine
color(x) → input color
```
```pine
color(x) → simple color
```
```pine
color(x) → series color
```

### Arguments
- `x` (*const color*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to color.

### See also
`float()`, `int()`, `bool()`, `string()`, `line()`, `label()`

## color.b()
Retrieves the value of the color's blue component.

### Syntax & Overloads
```pine
color.b(color) → const float
```
```pine
color.b(color) → input float
```
```pine
color.b(color) → simple float
```
```pine
color.b(color) → series float
```

### Arguments
- `color` (*const color*) — Color.

### Example
```pine
//@version=6
indicator("color.b", overlay=true)
plot(color.b(color.blue))
```

### Returns
The value (0 to 255) of the color's blue component.

## color.from_gradient()
Based on the relative position of value in the bottom_value to top_value range, the function returns a color from the gradient defined by bottom_color to top_color.

### Syntax
```pine
color.from_gradient(value, bottom_value, top_value, bottom_color, top_color) → series color
```

### Arguments
- `value` (*series int/float*) — Value to calculate the position-dependent color.
- `bottom_value` (*series int/float*) — Bottom position value corresponding to bottom_color.
- `top_value` (*series int/float*) — Top position value corresponding to top_color.
- `bottom_color` (*series color*) — Bottom position color.
- `top_color` (*series color*) — Top position color.

### Example
```pine
//@version=6
indicator("color.from_gradient", overlay=true)
color1 = color.from_gradient(close, low, high, color.yellow, color.lime)
color2 = color.from_gradient(ta.rsi(close, 7), 0, 100, color.rgb(255, 0, 0), color.rgb(0, 255, 0, 50))
plot(close, color=color1)
plot(ta.rsi(close,7), color=color2)
```

### Returns
A color calculated from the linear gradient between bottom_color to top_color.

### Remarks
Using this function will have an impact on the colors displayed in the script's "Settings/Style" tab. See the User Manual for more information.

## color.g()
Retrieves the value of the color's green component.

### Syntax & Overloads
```pine
color.g(color) → const float
```
```pine
color.g(color) → input float
```
```pine
color.g(color) → simple float
```
```pine
color.g(color) → series float
```

### Arguments
- `color` (*const color*) — Color.

### Example
```pine
//@version=6
indicator("color.g", overlay=true)
plot(color.g(color.green))
```

### Returns
The value (0 to 255) of the color's green component.

## color.new()
Function color applies the specified transparency to the given color.

### Syntax & Overloads
```pine
color.new(color, transp) → const color
```
```pine
color.new(color, transp) → input color
```
```pine
color.new(color, transp) → simple color
```
```pine
color.new(color, transp) → series color
```

### Arguments
- `color` (*const color*) — Color to apply transparency to.
- `transp` (*const int/float*) — Possible values are from 0 (not transparent) to 100 (invisible).

### Example
```pine
//@version=6
indicator("color.new", overlay=true)
plot(close, color=color.new(color.red, 50))
```

### Returns
Color with specified transparency.

### Remarks
Using arguments that are not constants (e.g., 'simple', 'input' or 'series') will have an impact on the colors displayed in the script's "Settings/Style" tab. See the User Manual for more information.

## color.r()
Retrieves the value of the color's red component.

### Syntax & Overloads
```pine
color.r(color) → const float
```
```pine
color.r(color) → input float
```
```pine
color.r(color) → simple float
```
```pine
color.r(color) → series float
```

### Arguments
- `color` (*const color*) — Color.

### Example
```pine
//@version=6
indicator("color.r", overlay=true)
plot(color.r(color.red))
```

### Returns
The value (0 to 255) of the color's red component.

## color.rgb()
Creates a new color with transparency using the RGB color model.

### Syntax & Overloads
```pine
color.rgb(red, green, blue, transp) → const color
```
```pine
color.rgb(red, green, blue, transp) → input color
```
```pine
color.rgb(red, green, blue, transp) → simple color
```
```pine
color.rgb(red, green, blue, transp) → series color
```

### Arguments
- `red` (*const int/float*) — Red color component. Possible values are from 0 to 255.
- `green` (*const int/float*) — Green color component. Possible values are from 0 to 255.
- `blue` (*const int/float*) — Blue color component. Possible values are from 0 to 255.
- `transp` (*const int/float*) — Optional. Color transparency. Possible values are from 0 (opaque) to 100 (invisible). Default value is 0.

### Example
```pine
//@version=6
indicator("color.rgb", overlay=true)
plot(close, color=color.rgb(255, 0, 0, 50))
```

### Returns
Color with specified transparency.

### Remarks
Using arguments that are not constants (e.g., 'simple', 'input' or 'series') will have an impact on the colors displayed in the script's "Settings/Style" tab. See the User Manual for more information.

## color.t()
Retrieves the color's transparency.

### Syntax & Overloads
```pine
color.t(color) → const float
```
```pine
color.t(color) → input float
```
```pine
color.t(color) → simple float
```
```pine
color.t(color) → series float
```

### Arguments
- `color` (*const color*) — Color.

### Example
```pine
//@version=6
indicator("color.t", overlay=true)
plot(color.t(color.new(color.red, 50)))
```

### Returns
The value (0-100) of the color's transparency.

## dayofmonth()
Calculates the day number of the month, in a specified time zone, from a UNIX timestamp.

### Syntax
```pine
dayofmonth(time, timezone) → series int
```

### Arguments
- `time` (*series int*) — A UNIX timestamp in milliseconds.
- `timezone` (*series string*) — Optional. Specifies the time zone of the returned day number. The value can be a time zone string in UTC/GMT offset notation (e.g., "UTC-5") or IANA time zone database notation (e.g., "America/New_York"). The default is syminfo.timezone.

### Returns
The calculated day of the month, expressed in the specified time zone.

### Remarks
A UNIX timestamp represents the number of milliseconds elapsed since 00:00 UTC on 1970-01-01. The meaning of a UNIX timestamp does not change relative to any time zone.

### See also
`dayofmonth`, `dayofweek()`, `weekofyear()`, `time()`, `year()`, `month()`, `hour()`, `minute()`, `second()`

## dayofweek()
Calculates the day number of the week, in a specified time zone, from a UNIX timestamp.

### Syntax
```pine
dayofweek(time, timezone) → series int
```

### Arguments
- `time` (*series int*) — A UNIX timestamp in milliseconds.
- `timezone` (*series string*) — Optional. Specifies the time zone of the returned day number. The value can be a time zone string in UTC/GMT offset notation (e.g., "UTC-5") or IANA time zone database notation (e.g., "America/New_York"). The default is syminfo.timezone.

### Returns
The calculated day number, expressed in the specified time zone.

### Remarks
A UNIX timestamp represents the number of milliseconds elapsed since 00:00 UTC on 1970-01-01. The meaning of a UNIX timestamp does not change relative to any time zone.

### See also
`dayofweek`, `dayofmonth()`, `weekofyear()`, `time()`, `year()`, `month()`, `hour()`, `minute()`, `second()`

## fixnan()
For a given series replaces NaN values with previous nearest non-NaN value.

### Syntax & Overloads
```pine
fixnan(source) → series color
```
```pine
fixnan(source) → series int
```
```pine
fixnan(source) → series float
```

### Arguments
- `source` (*series color*) — Source used for the calculation.

### Returns
Series without na gaps.

### See also
`na()`, `na`, `nz()`

## float()
Casts na to float

### Syntax & Overloads
```pine
float(x) → const float
```
```pine
float(x) → input float
```
```pine
float(x) → simple float
```
```pine
float(x) → series float
```

### Arguments
- `x` (*const int/float*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to float.

### See also
`int()`, `bool()`, `color()`, `string()`, `line()`, `label()`

## hour()

### Syntax
```pine
hour(time, timezone) → series int
```

### Arguments
- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is syminfo.timezone.

### Returns
Hour (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### See also
`hour`, `time()`, `year()`, `month()`, `dayofmonth()`, `dayofweek()`, `minute()`, `second()`

## indicator()
A declaration statement that identifies the script as an indicator and sets specific script-wide properties.

### Syntax
```pine
indicator(title, shorttitle, overlay, format, precision, scale, max_bars_back, timeframe, timeframe_gaps, explicit_plot_zorder, max_lines_count, max_labels_count, max_boxes_count, calc_bars_count, max_polylines_count, dynamic_requests, behind_chart) → void
```

### Arguments
- `title` (*const string*) — A string representing the script's title. The script displays the string's text in all possible locations if the declaration statement does not include a shorttitle argument. Additionally, the "Publish script" window uses the text as the default title for a script publication.
- `shorttitle` (*const string*) — Optional. A string representing the script's display name on charts. If specified and not an empty string, the value's text replaces the title string in most chart locations, including the "Settings" window, the script's status line, the Data Window, and the "Create alert" dialog box. Otherwise, the title string appears as the script's title in all locations. The default is an empty string.
- `overlay` (*const bool*) — Optional. If true, the script's visuals appear on the main chart pane if the user adds it to the chart directly, or in another script's pane if the user applies it to that script. If false, the script's visuals appear in a separate pane. However, if a function call that creates visuals includes force_overlay = true, its output always appears on the main chart pane, even if the script occupies a separate pane. Changes to this argument apply only after the user adds the script to the chart again. Additionally, if the user moves the script to another pane by selecting a "Move to" option in the script's "More" menu, the script does not move back to its original pane after any updates to the source code. The default is false.
- `format` (*const string*) — Optional. Specifies the format of the script's plotted values. Possible values are format.inherit, format.price, format.volume, and format.percent. The default is format.inherit.
- `precision` (*const int*) — Optional. Specifies the number of fractional digits that the script shows for plotted numbers. The value must be an integer from 0 to 16. If specified and the format argument is format.inherit, the script uses format.price as the formatting option instead. If the format argument is {format.volume}, the script ignores the precision value, because the decimal precision rules specified by format.volume supersede other precision settings. By default, the script inherits the precision settings of the chart.
- `scale` (*const scale_type*) — Optional. Determines the location of the script's price scale and the scaling behavior of the script's visuals. Possible values are scale.right, scale.left, and scale.none. If specified and the script overlays on the main chart pane or another script's pane, the script scales its visuals independently to fit the pane's visual space. If the script occupies the same pane as the main chart or another script, scale.right or scale.left adds a separate price scale for the script to the left or right side of that pane. If the script occupies a separate pane, either argument positions the price scale for that pane on the left or right side without adding a new scale. If the argument is scale.none, which is valid only if the overlay argument is true, the script displays plotted numbers directly on the scale of the existing pane, or displays values on a new price scale if the user moves it to a new pane. Changes to the argument apply only after the user adds the script to the chart again. If not specified, the script uses the main price scale for the pane it occupies, and it does not scale its visuals separately if it overlays on an existing pane.
- `max_bars_back` (*const int*) — Optional. Sets the minimum length of all the script's historical buffers, which determine the number of bars back that the script can reference for each series using the [] operator or the functions that retrieve history internally. The value must be an integer from 0 to 5000. By default, Pine's runtime system automatically calculates appropriate historical buffer sizes for each series while loading a script. Manually setting buffer sizes is necessary only in rare cases where automatic size detection fails. See the Historical buffers section of our User Manual for advanced details.
- `timeframe` (*const string*) — Optional. A valid timeframe string that determines the main timeframe the script uses for its calculations. If specified, the script automatically adds a "Timeframe" input to the "Settings/Inputs" tab. The input's displayed default in the tab represents the same timeframe as the specified argument. If the value is an empty string or not specified, the script uses the same timeframe as the chart. An argument is allowed for this parameter only if the script does not use drawing types or alert() function calls.
- `timeframe_gaps` (*const bool*) — Optional. Controls how the script displays plotted values if the timeframe value represents a higher timeframe than the chart's timeframe. An argument for this parameter is allowed only if the call includes a timeframe argument. If specified, the script adds a "Wait for timeframe closes" input, where users can change the setting, below the generated "Timeframe" input in the "Settings/Inputs" tab. If true, the indicator displays values only on the chart bars where new higher-timeframe data is available, and na on all other bars. If false, the indicator displays the last retrieved values on all chart bars where new data is not available. The default is true.
- `explicit_plot_zorder` (*const bool*) — Optional. Specifies which rules the script uses to determine the visual order of plots from plot*() calls, levels from hline() calls, and fills from fill() calls on the chart. If true, the indicator displays these visuals in the order of their function calls in the code. If false, the script uses the default z-index rules to determine the order of the visuals. The default is false.
- `max_lines_count` (*const int*) — Optional. Determines the maximum number of line objects that remain available to the script. The system automatically deletes the oldest line objects when the number of lines exceeds the limit. The limit specified by the argument is approximate; the script might display more drawings than specified. The default is ~50 lines.
- `max_labels_count` (*const int*) — Optional. Determines the maximum number of label objects that remain available to the script. The system automatically deletes the oldest label objects when the number of labels exceeds the limit. The limit specified by the argument is approximate; the script might display more drawings than specified. The default is ~50 labels.
- `max_boxes_count` (*const int*) — Optional. Determines the maximum number of box objects that remain available to the script. The system automatically deletes the oldest box objects when the number of boxes exceeds the limit. The limit specified by the argument is approximate; the script might display more drawings than specified. The default is ~50 boxes.
- `calc_bars_count` (*const int*) — Optional. Determines how many of the most recent historical bars are available to the script. If specified, the script automatically adds a "Calculated bars" input to the "Settings/Inputs" tab. If the value is positive and less than the number of historical bars in the dataset, the script starts its calculations that number of bars before the most recent bar. If the value is 0, the script's calculations start on the dataset's first bar. The default is 0.
- `max_polylines_count` (*const int*) — Optional. Determines the maximum number of polyline objects that remain available to the script. The system automatically deletes the oldest polyline objects when the number of polylines exceeds the limit. The limit specified by the argument is approximate; the script might display more drawings than specified. The default is ~50 polylines.
- `dynamic_requests` (*const bool*) — Optional. Specifies whether the script can use dynamic request.*() function calls. Dynamic request.*() calls are allowed within the local scopes of conditional structures (e.g., if), loops (e.g., for), and exported functions. Additionally, such calls allow "series" arguments for several parameters that otherwise require values with "simple" or weaker qualifiers. See the Dynamic requests section of our User Manual for more information. The default is true.
- `behind_chart` (*const bool*) — Optional. Controls whether all plots and drawings appear behind the chart display (if true) or in front of it (if false). This parameter takes effect only when the overlay argument is true. Changes to the argument apply only after the user adds the script to the chart again. The default is true.

### Example
```pine
//@version=6
indicator("My script", shorttitle="Script")
plot(close)
```

### Remarks
Every indicator script must include exactly one indicator() statement in the code.

### See also
`strategy()`, `library()`

## input()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function automatically detects the type of the argument used for 'defval' and uses the corresponding input widget.

### Syntax & Overloads
```pine
input(defval, title, tooltip, inline, group, display, active) → input color
```
```pine
input(defval, title, tooltip, inline, group, display, active) → input string
```
```pine
input(defval, title, tooltip, inline, group, display, active) → input int
```
```pine
input(defval, title, tooltip, inline, group, display, active) → input float
```
```pine
input(defval, title, inline, group, tooltip, display, active) → series float
```
```pine
input(defval, title, tooltip, inline, group, display, active) → input bool
```

### Arguments
- `defval` (*const int/float/bool/string/color or source-type built-ins*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where script users can change it. Source-type built-ins are built-in series float variables that specify the source of the calculation: close, hlc3, etc.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default depends on the type of the value passed to defval: display.none for bool and color values, display.all for everything else.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
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

### Returns
Value of input variable.

### Remarks
Result of input() function always should be assigned to a variable, see examples above.

### See also
`input.bool()`, `input.color()`, `input.int()`, `input.float()`, `input.string()`, `input.symbol()`, `input.timeframe()`, `input.text_area()`, `input.session()`, `input.source()`, `input.time()`

## input.bool()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a checkmark to the script's inputs.

### Syntax
```pine
input.bool(defval, title, tooltip, inline, group, confirm, display, active) → input bool
```

### Arguments
- `defval` (*const bool*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.none.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.bool", overlay=true)
i_switch = input.bool(true, "On/Off")
plot(i_switch ? open : na)
```

### Returns
Value of input variable.

### Remarks
Result of input.bool() function always should be assigned to a variable, see examples above.

### See also
`input.int()`, `input.float()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## input.color()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a color picker that allows the user to select a color and transparency, either from a palette or a hex value.

### Syntax
```pine
input.color(defval, title, tooltip, inline, group, confirm, display, active) → input color
```

### Arguments
- `defval` (*const color*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.none.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.color", overlay=true)
i_col = input.color(color.red, "Plot Color")
plot(close, color=i_col)
```

### Returns
Value of input variable.

### Remarks
Result of input.color() function always should be assigned to a variable, see examples above.

### See also
`input.bool()`, `input.int()`, `input.float()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.time()`, `input()`

## input.enum()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a dropdown with options based on the enum fields passed to its defval and options parameters.
The text for each option in the resulting dropdown corresponds to the titles of the included fields. If a field's title is not specified in the enum declaration, its title is the string representation of its name.

### Syntax
```pine
input.enum(defval, title, options, tooltip, inline, group, confirm, display, active) → input enum
```

### Arguments
- `defval` (*const enum*) — Determines the default value of the input, which users can change in the script's "Settings/Inputs" tab. When the options parameter has a specified tuple of enum fields, the tuple must include the defval.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*tuple of enum fields: [enumName.field1, enumName.field2, ...]*) — A list of options to choose from. Optional. By default, the titles of all of the enum's fields are available in the dropdown. Passing a tuple as the options argument limits the list to only the included fields.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
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

### Returns
Value of input variable.

### Remarks
All fields included in the defval and options arguments must belong to the same enum.

### See also
`input.text_area()`, `input.bool()`, `input.int()`, `input.float()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## input.float()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a float input to the script's inputs.

### Syntax & Overloads
```pine
input.float(defval, title, options, tooltip, inline, group, confirm, display, active) → input float
```
```pine
input.float(defval, title, minval, maxval, step, tooltip, inline, group, confirm, display, active) → input float
```

### Arguments
- `defval` (*const int/float*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where script users can change it. When a list of values is used with the options parameter, the value must be one of them.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*tuple of const int/float values: [val1, val2, ...]*) — A list of options to choose from a dropdown menu, separated by commas and enclosed in square brackets: [val1, val2, ...]. When using this parameter, the minval, maxval and step parameters cannot be used.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.float", overlay=true)
i_angle1 = input.float(0.5, "Sin Angle", minval=-3.14, maxval=3.14, step=0.02)
plot(math.sin(i_angle1) > 0 ? close : open, "sin", color=color.green)

i_angle2 = input.float(0, "Cos Angle", options=[-3.14, -1.57, 0, 1.57, 3.14])
plot(math.cos(i_angle2) > 0 ? close : open, "cos", color=color.red)
```

### Returns
Value of input variable.

### Remarks
Result of input.float() function always should be assigned to a variable, see examples above.

### See also
`input.bool()`, `input.int()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## input.int()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for an integer input to the script's inputs.

### Syntax & Overloads
```pine
input.int(defval, title, options, tooltip, inline, group, confirm, display, active) → input int
```
```pine
input.int(defval, title, minval, maxval, step, tooltip, inline, group, confirm, display, active) → input int
```

### Arguments
- `defval` (*const int*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where script users can change it. When a list of values is used with the options parameter, the value must be one of them.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*tuple of const int values: [val1, val2, ...]*) — A list of options to choose from a dropdown menu, separated by commas and enclosed in square brackets: [val1, val2, ...]. When using this parameter, the minval, maxval and step parameters cannot be used.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.int", overlay=true)
i_len1 = input.int(10, "Length 1", minval=5, maxval=21, step=1)
plot(ta.sma(close, i_len1))

i_len2 = input.int(10, "Length 2", options=[5, 10, 21])
plot(ta.sma(close, i_len2))
```

### Returns
Value of input variable.

### Remarks
Result of input.int() function always should be assigned to a variable, see examples above.

### See also
`input.bool()`, `input.float()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## input.price()
Adds a price input to the script's "Settings/Inputs" tab. The user can change the price in the settings or by selecting the indicator and dragging the price line.

### Syntax
```pine
input.price(defval, title, tooltip, inline, group, confirm, display, active) → input float
```

### Arguments
- `defval` (*const int/float*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — Optional. If true, the script prompts the user to set the input's initial value by clicking a point on the chart. If inputs of other types require confirmation, the "Confirm inputs" dialog box also displays this input's field, allowing final adjustments to the value before the script starts to run. The default is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.price", overlay=true)
price1 = input.price(title="Date", defval=42)
plot(price1)

price2 = input.price(54, title="Date")
plot(price2)
```

### Returns
Value of input variable.

### Remarks
The user can change the input's value by specifying a new value in the "Settings/Inputs" tab, or by moving the input's marker on the chart. Alternatively, they can select "Reset points" from the script's "More" menu and set a new input value by clicking a point on the chart.
If an input.time() and input.price() function call in the script share a unique inline argument and have matching group arguments, those calls create a single interactive point marker on the chart. The user can move that marker to adjust the input time and price values simultaneously.

### See also
`input.bool()`, `input.int()`, `input.float()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.resolution()`, `input.session()`, `input.source()`, `input.color()`, `input()`

## input.session()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds two dropdowns that allow the user to specify the beginning and the end of a session using the session selector and returns the result as a string.

### Syntax
```pine
input.session(defval, title, options, tooltip, inline, group, confirm, display, active) → input string
```

### Arguments
- `defval` (*const string*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the options parameter, the value must be one of them.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*tuple of const string values: [val1, val2, ...]*) — A list of options to choose from.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.session", overlay=true)
i_sess = input.session("1300-1700", "Session", options=["0930-1600", "1300-1700", "1700-2100"])
t = time(timeframe.period, i_sess)
bgcolor(time == t ? color.green : na)
```

### Returns
Value of input variable.

### Remarks
Result of input.session() function always should be assigned to a variable, see examples above.

### See also
`input.bool()`, `input.int()`, `input.float()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.timeframe()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## input.source()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a dropdown that allows the user to select a source for the calculation, e.g. close, hl2, etc. The user can also select an output from another indicator on their chart as the source.

### Syntax
```pine
input.source(defval, title, tooltip, inline, group, display, active, confirm) → series float
```

### Arguments
- `defval` (*open/high/low/close/hl2/hlc3/ohlc4/hlcc4*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.

### Example
```pine
//@version=6
indicator("input.source", overlay=true)
i_src = input.source(close, "Source")
plot(i_src)
```

### Returns
Value of input variable.

### Remarks
Result of input.source() function always should be assigned to a variable, see examples above.

### See also
`input.bool()`, `input.int()`, `input.float()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.color()`, `input.time()`, `input()`

## input.string()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a string input to the script's inputs.

### Syntax
```pine
input.string(defval, title, options, tooltip, inline, group, confirm, display, active) → input string
```

### Arguments
- `defval` (*const string*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the options parameter, the value must be one of them.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*tuple of const string values: [val1, val2, ...]*) — A list of options to choose from.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.string", overlay=true)
i_text = input.string("Hello!", "Message")
l = label.new(bar_index, high, i_text)
label.delete(l[1])
```

### Returns
Value of input variable.

### Remarks
Result of input.string() function always should be assigned to a variable, see examples above.

### See also
`input.text_area()`, `input.bool()`, `input.int()`, `input.float()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## input.symbol()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field that allows the user to select a specific symbol using the symbol search and returns that symbol, paired with its exchange prefix, as a string.

### Syntax
```pine
input.symbol(defval, title, tooltip, inline, group, confirm, display, active) → input string
```

### Arguments
- `defval` (*const string*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.symbol", overlay=true)
i_sym = input.symbol("DELL", "Symbol")
s = request.security(i_sym, 'D', close)
plot(s)
```

### Returns
Value of input variable.

### Remarks
Result of input.symbol() function always should be assigned to a variable, see examples above.

### See also
`input.bool()`, `input.int()`, `input.float()`, `input.string()`, `input.text_area()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## input.text_area()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a field for a multiline text input.

### Syntax
```pine
input.text_area(defval, title, tooltip, group, confirm, display, active) → input string
```

### Arguments
- `defval` (*const string*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.none.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.text_area")
i_text = input.text_area(defval = "Hello \nWorld!", title = "Message")
plot(close)
```

### Returns
Value of input variable.

### Remarks
Result of input.text_area() function always should be assigned to a variable, see examples above.

### See also
`input.string()`, `input.bool()`, `input.int()`, `input.float()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## input.time()
Adds two inputs to the script's "Settings/Inputs" tab on the same line: one for the date and one for the time. The user can change the price in the settings or by selecting the indicator and dragging the price line. The function returns a date/time value in UNIX format.

### Syntax
```pine
input.time(defval, title, tooltip, inline, group, confirm, display, active) → input int
```

### Arguments
- `defval` (*const int*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it. The value can be a timestamp() function, but only if it uses a date argument in const string format.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — Optional. If true, the script prompts the user to set the input's initial value by clicking a point on the chart. If inputs of other types require confirmation, the "Confirm inputs" dialog box also displays this input's field, allowing final adjustments to the value before the script starts to run. The default is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.none.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.time", overlay=true)
i_date = input.time(timestamp("20 Jul 2021 00:00 +0300"), "Date")
l = label.new(i_date, high, "Date", xloc=xloc.bar_time)
label.delete(l[1])
```

### Returns
Value of input variable.

### Remarks
The user can change the input's value by specifying a new value in the "Settings/Inputs" tab, or by moving the input's marker on the chart. Alternatively, they can select "Reset points" from the script's "More" menu and set a new input value by clicking a point on the chart.
If an input.time() and input.price() function call in the script share a unique inline argument and have matching group arguments, those calls create a single interactive point marker on the chart. The user can move that marker to adjust the input time and price values simultaneously.

### See also
`input.bool()`, `input.int()`, `input.float()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.timeframe()`, `input.session()`, `input.source()`, `input.color()`, `input()`

## input.timeframe()
Adds an input to the Inputs tab of your script's Settings, which allows you to provide configuration options to script users. This function adds a dropdown that allows the user to select a specific timeframe via the timeframe selector and returns it as a string. The selector includes the custom timeframes a user may have added using the chart's Timeframe dropdown.

### Syntax
```pine
input.timeframe(defval, title, options, tooltip, inline, group, confirm, display, active) → input string
```

### Arguments
- `defval` (*const string*) — Determines the default value of the input variable proposed in the script's "Settings/Inputs" tab, from where the user can change it. When a list of values is used with the options parameter, the value must be one of them.
- `title` (*const string*) — Title of the input. If not specified, the variable name is used as the input's title. If the title is specified, but it is empty, the name will be an empty string.
- `options` (*tuple of const string values: [val1, val2, ...]*) — A list of options to choose from.
- `tooltip` (*const string*) — The string that will be shown to the user when hovering over the tooltip icon.
- `inline` (*const string*) — Combines all the input calls using the same argument in one line. The string used as an argument is not displayed. It is only used to identify inputs belonging to the same line.
- `group` (*const string*) — Creates a header above all inputs using the same group argument string. The string is also used as the header's text.
- `confirm` (*const bool*) — If true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
- `display` (*const plot_display*) — Controls where the script will display the input's information, aside from within the script's settings. This option allows one to remove a specific input from the script's status line or the Data Window to ensure only the most necessary inputs are displayed there. Possible values: display.none, display.data_window, display.status_line, display.all. Optional. The default is display.all.
- `active` (*input bool*) — Optional. Specifies whether users can change the value of the input in the script's "Settings/Inputs" tab. The script can use this parameter to set the state of the input based on the values of other inputs. If true, users can change the value of the input. If false, the input is grayed out, and users cannot change the value. The default is true.

### Example
```pine
//@version=6
indicator("input.timeframe", overlay=true)
i_res = input.timeframe('D', "Resolution", options=['D', 'W', 'M'])
s = request.security("AAPL", i_res, close)
plot(s)
```

### Returns
Value of input variable.

### Remarks
Result of input.timeframe() function always should be assigned to a variable, see examples above.

### See also
`input.bool()`, `input.int()`, `input.float()`, `input.string()`, `input.text_area()`, `input.symbol()`, `input.session()`, `input.source()`, `input.color()`, `input.time()`, `input()`

## int()
Casts na or truncates float value to int

### Syntax & Overloads
```pine
int(x) → const int
```
```pine
int(x) → input int
```
```pine
int(x) → simple int
```
```pine
int(x) → series int
```

### Arguments
- `x` (*const int/float*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to int.

### See also
`float()`, `bool()`, `color()`, `string()`, `line()`, `label()`

## library()
Declaration statement identifying a script as a library.

### Syntax
```pine
library(title, overlay, dynamic_requests) → void
```

### Arguments
- `title` (*const string*) — The title of the library and its identifier. It cannot contain spaces, special characters or begin with a digit. It is used as the publication's default title, and to uniquely identify the library in the import statement, when another script uses it. It is also used as the script's name on the chart.
- `overlay` (*const bool*) — If true, the script's visuals appear on the main chart pane if the user adds it to the chart directly, or in another script's pane if the user applies it to that script. If false, the script's visuals appear in a separate pane. Changes to the overlay value apply only after the user adds the script to the chart again. Additionally, if the user moves the script to another pane by selecting a "Move to" option in the script's "More" menu, it does not move back to its original pane after any updates to the source code. The default is false. Strategy-specific labels that display entries and exits will be displayed over the main chart regardless of this setting.
- `dynamic_requests` (*const bool*) — Specifies whether the script can dynamically call functions from the request.*() namespace. Dynamic request.*() calls are allowed within the local scopes of conditional structures (e.g., if), loops (e.g., for), and exported functions. Additionally, such calls allow "series" arguments for many of their parameters. Optional. The default is true. See the User Manual's Dynamic requests section for more information.

### Example
```pine
//@version=6
// @description Math library
library("num_methods", overlay = true)
// Calculate "sinh()" from the float parameter `x`
export sinh(float x) =>
    (math.exp(x) - math.exp(-x)) / 2.0
plot(sinh(0))
```

### See also
`indicator()`, `strategy()`

## log.error()
Converts the formatting string and value(s) into a formatted string, and sends the result to the "Pine logs" menu tagged with the "error" debug level.
The formatting string can contain literal text and one placeholder in curly braces {} for each value to be formatted. Each placeholder consists of the index of the required argument (beginning at 0) that will replace it, and an optional format specifier. The index represents the position of that argument in the function's argument list.

### Syntax & Overloads
```pine
log.error(message) → void
```
```pine
log.error(formatString, arg0, arg1, ...) → void
```

### Arguments
- `message` (*series string*) — Log message.

### Example
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

### Returns
The formatted string.

### Remarks
Any curly braces within an unquoted pattern must be balanced. For example, "ab {0} de" and "ab '}' de" are valid patterns, but "ab {0'}' de", "ab } de" and "''{''" are not.
The function can apply additional formatting to some values inside of the {}. The list of additional formatting options can be found in the EXAMPLE section of the str.format() article.
The string used as the formatString argument can contain single quote characters ('). However, one must pair all single quotes in that string to avoid unexpected formatting results.
The "Pine logs..." button is accessible from the "More" dropdown in the Pine Editor and from the "More" dropdown in the status line of any script that uses log.*() functions.

## log.info()
Converts the formatting string and value(s) into a formatted string, and sends the result to the "Pine logs" menu tagged with the "info" debug level.
The formatting string can contain literal text and one placeholder in curly braces {} for each value to be formatted. Each placeholder consists of the index of the required argument (beginning at 0) that will replace it, and an optional format specifier. The index represents the position of that argument in the function's argument list.

### Syntax & Overloads
```pine
log.info(message) → void
```
```pine
log.info(formatString, arg0, arg1, ...) → void
```

### Arguments
- `message` (*series string*) — Log message.

### Example
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

### Returns
The formatted string.

### Remarks
Any curly braces within an unquoted pattern must be balanced. For example, "ab {0} de" and "ab '}' de" are valid patterns, but "ab {0'}' de", "ab } de" and "''{''" are not.
The function can apply additional formatting to some values inside of the {}. The list of additional formatting options can be found in the EXAMPLE section of the str.format() article.
The string used as the formatString argument can contain single quote characters ('). However, one must pair all single quotes in that string to avoid unexpected formatting results.
The "Pine logs..." button is accessible from the "More" dropdown in the Pine Editor and from the "More" dropdown in the status line of any script that uses log.*() functions.

## log.warning()
Converts the formatting string and value(s) into a formatted string, and sends the result to the "Pine logs" menu tagged with the "warning" debug level.
The formatting string can contain literal text and one placeholder in curly braces {} for each value to be formatted. Each placeholder consists of the index of the required argument (beginning at 0) that will replace it, and an optional format specifier. The index represents the position of that argument in the function's argument list.

### Syntax & Overloads
```pine
log.warning(message) → void
```
```pine
log.warning(formatString, arg0, arg1, ...) → void
```

### Arguments
- `message` (*series string*) — Log message.

### Example
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

### Returns
The formatted string.

### Remarks
Any curly braces within an unquoted pattern must be balanced. For example, "ab {0} de" and "ab '}' de" are valid patterns, but "ab {0'}' de", "ab } de" and "''{''" are not.
The function can apply additional formatting to some values inside of the {}. The list of additional formatting options can be found in the EXAMPLE section of the str.format() article.
The string used as the formatString argument can contain single quote characters ('). However, one must pair all single quotes in that string to avoid unexpected formatting results.
The "Pine logs..." button is accessible from the "More" dropdown in the Pine Editor and from the "More" dropdown in the status line of any script that uses log.*() functions.

## math.abs()
Absolute value of number is number if number >= 0, or -number otherwise.

### Syntax & Overloads
```pine
math.abs(number) → const int
```
```pine
math.abs(number) → input int
```
```pine
math.abs(number) → const float
```
```pine
math.abs(number) → simple int
```
```pine
math.abs(number) → input float
```
```pine
math.abs(number) → series int
```
```pine
math.abs(number) → simple float
```
```pine
math.abs(number) → series float
```

### Arguments
- `number` (*const int*) — The number to use in the calculation.

### Returns
The absolute value of number.

## math.acos()
The acos function returns the arccosine (in radians) of number such that cos(acos(y)) = y for y in range [-1, 1].

### Syntax & Overloads
```pine
math.acos(angle) → const float
```
```pine
math.acos(angle) → input float
```
```pine
math.acos(angle) → simple float
```
```pine
math.acos(angle) → series float
```

### Arguments
- `angle` (*const int/float*) — The value, in radians, to use in the calculation.

### Returns
The arc cosine of a value; the returned angle is in the range [0, Pi], or na if y is outside of range [-1, 1].

## math.asin()
The asin function returns the arcsine (in radians) of number such that sin(asin(y)) = y for y in range [-1, 1].

### Syntax & Overloads
```pine
math.asin(angle) → const float
```
```pine
math.asin(angle) → input float
```
```pine
math.asin(angle) → simple float
```
```pine
math.asin(angle) → series float
```

### Arguments
- `angle` (*const int/float*) — The value, in radians, to use in the calculation.

### Returns
The arcsine of a value; the returned angle is in the range [-Pi/2, Pi/2], or na if y is outside of range [-1, 1].

## math.atan()
The atan function returns the arctangent (in radians) of number such that tan(atan(y)) = y for any y.

### Syntax & Overloads
```pine
math.atan(angle) → const float
```
```pine
math.atan(angle) → input float
```
```pine
math.atan(angle) → simple float
```
```pine
math.atan(angle) → series float
```

### Arguments
- `angle` (*const int/float*) — The value, in radians, to use in the calculation.

### Returns
The arc tangent of a value; the returned angle is in the range [-Pi/2, Pi/2].

## math.avg()
Calculates average of all given series (elementwise).

### Syntax & Overloads
```pine
math.avg(number0, number1, ...) → simple float
```
```pine
math.avg(number0, number1, ...) → series float
```

### Arguments
- number0, number1, ... (simple int/float) A sequence of numbers to use in the calculation.

### Returns
Average.

### See also
`math.sum()`, `ta.cum()`, `ta.sma()`

## math.ceil()
Rounds the specified number up to the smallest whole number ("int" value) that is greater than or equal to it.

### Syntax & Overloads
```pine
math.ceil(number) → const int
```
```pine
math.ceil(number) → input int
```
```pine
math.ceil(number) → simple int
```
```pine
math.ceil(number) → series int
```

### Arguments
- `number` (*const int/float*) — The number to round.

### Returns
The smallest "int" value that is greater than or equal to the number.

### See also
`math.floor()`, `math.round()`

## math.cos()
The cos function returns the trigonometric cosine of an angle.

### Syntax & Overloads
```pine
math.cos(angle) → const float
```
```pine
math.cos(angle) → input float
```
```pine
math.cos(angle) → simple float
```
```pine
math.cos(angle) → series float
```

### Arguments
- `angle` (*const int/float*) — Angle, in radians.

### Returns
The trigonometric cosine of an angle.

## math.exp()
The exp function of number is e raised to the power of number, where e is Euler's number.

### Syntax & Overloads
```pine
math.exp(number) → const float
```
```pine
math.exp(number) → input float
```
```pine
math.exp(number) → simple float
```
```pine
math.exp(number) → series float
```

### Arguments
- `number` (*const int/float*) — The number to use in the calculation.

### Returns
A value representing e raised to the power of number.

### See also
`math.pow()`

## math.floor()
Rounds the specified number down to the largest whole number ("int" value) that is less than or equal to it.

### Syntax & Overloads
```pine
math.floor(number) → const int
```
```pine
math.floor(number) → input int
```
```pine
math.floor(number) → simple int
```
```pine
math.floor(number) → series int
```

### Arguments
- `number` (*const int/float*) — The number to round.

### Returns
The largest "int" value that is less than or equal to the number.

### See also
`math.ceil()`, `math.round()`

## math.log()
Natural logarithm of any number > 0 is the unique y such that e^y = number.

### Syntax & Overloads
```pine
math.log(number) → const float
```
```pine
math.log(number) → input float
```
```pine
math.log(number) → simple float
```
```pine
math.log(number) → series float
```

### Arguments
- `number` (*const int/float*) — The number to use in the calculation.

### Returns
The natural logarithm of number.

### See also
`math.log10()`

## math.log10()
The common (or base 10) logarithm of number is the power to which 10 must be raised to obtain the number. 10^y = number.

### Syntax & Overloads
```pine
math.log10(number) → const float
```
```pine
math.log10(number) → input float
```
```pine
math.log10(number) → simple float
```
```pine
math.log10(number) → series float
```

### Arguments
- `number` (*const int/float*) — The number to use in the calculation.

### Returns
The base 10 logarithm of number.

### See also
`math.log()`

## math.max()
Returns the greatest of multiple values.

### Syntax & Overloads
```pine
math.max(number0, number1, ...) → const int
```
```pine
math.max(number0, number1, ...) → const float
```
```pine
math.max(number0, number1, ...) → input int
```
```pine
math.max(number0, number1, ...) → simple int
```
```pine
math.max(number0, number1, ...) → input float
```
```pine
math.max(number0, number1, ...) → series int
```
```pine
math.max(number0, number1, ...) → simple float
```
```pine
math.max(number0, number1, ...) → series float
```

### Arguments
- number0, number1, ... (const int) A sequence of numbers to use in the calculation.

### Example
```pine
//@version=6
indicator("math.max", overlay=true)
plot(math.max(close, open))
plot(math.max(close, math.max(open, 42)))
```

### Returns
The greatest of multiple given values.

### See also
`math.min()`

## math.min()
Returns the smallest of multiple values.

### Syntax & Overloads
```pine
math.min(number0, number1, ...) → const int
```
```pine
math.min(number0, number1, ...) → const float
```
```pine
math.min(number0, number1, ...) → input int
```
```pine
math.min(number0, number1, ...) → simple int
```
```pine
math.min(number0, number1, ...) → input float
```
```pine
math.min(number0, number1, ...) → series int
```
```pine
math.min(number0, number1, ...) → simple float
```
```pine
math.min(number0, number1, ...) → series float
```

### Arguments
- number0, number1, ... (const int) A sequence of numbers to use in the calculation.

### Example
```pine
//@version=6
indicator("math.min", overlay=true)
plot(math.min(close, open))
plot(math.min(close, math.min(open, 42)))
```

### Returns
The smallest of multiple given values.

### See also
`math.max()`

## math.pow()
Mathematical power function.

### Syntax & Overloads
```pine
math.pow(base, exponent) → const float
```
```pine
math.pow(base, exponent) → input float
```
```pine
math.pow(base, exponent) → simple float
```
```pine
math.pow(base, exponent) → series float
```

### Arguments
- `base` (*const int/float*) — Specify the base to use.
- `exponent` (*const int/float*) — Specifies the exponent.

### Example
```pine
//@version=6
indicator("math.pow", overlay=true)
plot(math.pow(close, 2))
```

### Returns
base raised to the power of exponent. If base is a series, it is calculated elementwise.

### See also
`math.sqrt()`, `math.exp()`

## math.random()
Returns a pseudo-random value. The function will generate a different sequence of values for each script execution. Using the same value for the optional seed argument will produce a repeatable sequence.

### Syntax
```pine
math.random(min, max, seed) → series float
```

### Arguments
- `min` (*series int/float*) — The lower bound of the range of random values. The value is not included in the range. The default is 0.
- `max` (*series int/float*) — The upper bound of the range of random values. The value is not included in the range. The default is 1.
- `seed` (*series int*) — Optional argument. When the same seed is used, allows successive calls to the function to produce a repeatable set of values.

### Returns
A random value.

## math.round()
Returns the value of number rounded to the nearest integer, with ties rounding up. If the precision parameter is used, returns a float value rounded to that amount of decimal places.

### Syntax & Overloads
```pine
math.round(number) → const int
```
```pine
math.round(number) → input int
```
```pine
math.round(number) → simple int
```
```pine
math.round(number) → series int
```
```pine
math.round(number, precision) → const float
```
```pine
math.round(number, precision) → input float
```
```pine
math.round(number, precision) → simple float
```
```pine
math.round(number, precision) → series float
```

### Arguments
- `number` (*const int/float*) — The value to be rounded.

### Returns
The value of number rounded to the nearest integer, or according to precision.

### Remarks
Note that for 'na' values function returns 'na'.

### See also
`math.ceil()`, `math.floor()`

## math.round_to_mintick()
Returns the value rounded to the symbol's mintick, i.e. the nearest value that can be divided by syminfo.mintick, without the remainder, with ties rounding up.

### Syntax & Overloads
```pine
math.round_to_mintick(number) → simple float
```
```pine
math.round_to_mintick(number) → series float
```

### Arguments
- `number` (*simple int/float*) — The value to be rounded.

### Returns
The number rounded to tick precision.

### Remarks
Note that for 'na' values function returns 'na'.

### See also
`math.ceil()`, `math.floor()`

## math.sign()
Sign (signum) of number is zero if number is zero, 1.0 if number is greater than zero, -1.0 if number is less than zero.

### Syntax & Overloads
```pine
math.sign(number) → const float
```
```pine
math.sign(number) → input float
```
```pine
math.sign(number) → simple float
```
```pine
math.sign(number) → series float
```

### Arguments
- `number` (*const int/float*) — The number to use in the calculation.

### Returns
The sign of the argument.

## math.sin()
The sin function returns the trigonometric sine of an angle.

### Syntax & Overloads
```pine
math.sin(angle) → const float
```
```pine
math.sin(angle) → input float
```
```pine
math.sin(angle) → simple float
```
```pine
math.sin(angle) → series float
```

### Arguments
- `angle` (*const int/float*) — Angle, in radians.

### Returns
The trigonometric sine of an angle.

## math.sqrt()
Square root of any number >= 0 is the unique y >= 0 such that y^2 = number.

### Syntax & Overloads
```pine
math.sqrt(number) → const float
```
```pine
math.sqrt(number) → input float
```
```pine
math.sqrt(number) → simple float
```
```pine
math.sqrt(number) → series float
```

### Arguments
- `number` (*const int/float*) — The number to use in the calculation.

### Returns
The square root of number.

### See also
`math.pow()`

## math.sum()
The sum function returns the sliding sum of last y values of x.

### Syntax
```pine
math.sum(source, length) → series float
```

### Arguments
- `source` (*series int/float*) — Series of values to process.
- `length` (*series int*) — Number of bars (length).

### Returns
Sum of source for length bars back.

### Remarks
na values in the source series are ignored; the function calculates on the length quantity of non-na values.

### See also
`ta.cum()`, `for`

## math.tan()
The tan function returns the trigonometric tangent of an angle.

### Syntax & Overloads
```pine
math.tan(angle) → const float
```
```pine
math.tan(angle) → input float
```
```pine
math.tan(angle) → simple float
```
```pine
math.tan(angle) → series float
```

### Arguments
- `angle` (*const int/float*) — Angle, in radians.

### Returns
The trigonometric tangent of an angle.

## math.todegrees()
Returns an approximately equivalent angle in degrees from an angle measured in radians.

### Syntax
```pine
math.todegrees(radians) → series float
```

### Arguments
- `radians` (*series int/float*) — Angle in radians.

### Returns
The angle value in degrees.

## math.toradians()
Returns an approximately equivalent angle in radians from an angle measured in degrees.

### Syntax
```pine
math.toradians(degrees) → series float
```

### Arguments
- `degrees` (*series int/float*) — Angle in degrees.

### Returns
The angle value in radians.

## max_bars_back()
Function sets the maximum number of bars that is available for historical reference of a given built-in or user variable. When operator '[]' is applied to a variable - it is a reference to a historical value of that variable.
If an argument of an operator '[]' is a compile time constant value (e.g. 'v[10]', 'close[500]') then there is no need to use 'max_bars_back' function for that variable. Pine Script® compiler will use that constant value as history buffer size.
If an argument of an operator '[]' is a value, calculated at runtime (e.g. 'v[i]' where 'i' - is a series variable) then Pine Script® attempts to autodetect the history buffer size at runtime. Sometimes it fails and the script crashes at runtime because it eventually refers to historical values that are out of the buffer. In that case you should use 'max_bars_back' to fix that problem manually.

### Syntax
```pine
max_bars_back(var, num) → void
```

### Arguments
- `var` (*series int/float/bool/color/label/line*) — Series variable identifier for which history buffer should be resized. Possible values are: 'open', 'high', 'low', 'close', 'volume', 'time', or any user defined variable id.
- `num` (*const int*) — History buffer size which is the number of bars that could be referenced for variable 'var'.

### Example
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

### Returns
void

### Remarks
At the moment 'max_bars_back' cannot be applied to built-ins like 'hl2', 'hlc3', 'ohlc4'. Please use multiple 'max_bars_back' calls as workaround here (e.g. instead of a single ‘max_bars_back(hl2, 100)’ call you should call the function twice: ‘max_bars_back(high, 100), max_bars_back(low, 100)’).
If the indicator() or strategy() 'max_bars_back' parameter is used, all variables in the indicator are affected. This may result in excessive memory usage and cause runtime problems. When possible (i.e. when the cause is a variable rather than a function), please use the max_bars_back() function instead.

### See also
`indicator()`

## minute()

### Syntax
```pine
minute(time, timezone) → series int
```

### Arguments
- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is syminfo.timezone.

### Returns
Minute (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### See also
`minute`, `time()`, `year()`, `month()`, `dayofmonth()`, `dayofweek()`, `hour()`, `second()`

## month()

### Syntax
```pine
month(time, timezone) → series int
```

### Arguments
- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is syminfo.timezone.

### Returns
Month (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.
Note that this function returns the month based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00 UTC-4) this value can be lower by 1 than the month of the trading day.

### See also
`month`, `time()`, `year()`, `dayofmonth()`, `dayofweek()`, `hour()`, `minute()`, `second()`

## na()
Tests if x is na.

### Syntax & Overloads
```pine
na(x) → simple bool
```
```pine
na(x) → series bool
```

### Arguments
- `x` (*simple int/float*) — Value to be tested.

### Example
```pine
//@version=6
indicator("na")
// Use the `na()` function to test for `na`.
plot(na(close[1]) ? close : close[1])
// ALTERNATIVE
// `nz()` also tests `close[1]` for `na`. It returns `close[1]` if it is not `na`, and `close` if it is.
plot(nz(close[1], close))
```

### Returns
Returns true if x is na, false otherwise.

### See also
`na`, `fixnan()`, `nz()`

## nz()
Replaces na (undefined) values with either a type-specific default value or a specified replacement.

### Syntax & Overloads
```pine
nz(source, replacement) → simple color
```
```pine
nz(source, replacement) → simple int
```
```pine
nz(source, replacement) → series color
```
```pine
nz(source, replacement) → series int
```
```pine
nz(source, replacement) → simple float
```
```pine
nz(source, replacement) → series float
```

### Arguments
- `source` (*simple color*) — The source series to process.
- `replacement` (*simple color*) — Optional. The value the function uses to replace na values in the source series. The default depends on the source type: 0 for "int", 0.0 for "float", or #00000000 for "color".

### Example
```pine
//@version=6
indicator("nz", overlay=true)
plot(nz(ta.sma(close, 100)))
```

### Returns
The value of source if it is not na. If the value of source is na, returns zero, or the replacement argument when one is used.

### See also
`na`, `na()`, `fixnan()`

## runtime.error()
When called, causes a runtime error with the error message specified in the message argument.

### Syntax
```pine
runtime.error(message) → void
```

### Arguments
- `message` (*series string*) — Error message.

## second()

### Syntax
```pine
second(time, timezone) → series int
```

### Arguments
- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is syminfo.timezone.

### Returns
Second (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### See also
`second`, `time()`, `year()`, `month()`, `dayofmonth()`, `dayofweek()`, `hour()`, `minute()`

## str.contains()
Returns true if the source string contains the str substring, false otherwise.

### Syntax & Overloads
```pine
str.contains(source, str) → const bool
```
```pine
str.contains(source, str) → simple bool
```
```pine
str.contains(source, str) → series bool
```

### Arguments
- `source` (*const string*) — Source string.
- `str` (*const string*) — The substring to search for.

### Example
```pine
//@version=6
indicator("str.contains")
// If the current chart is a continuous futures chart, e.g “BTC1!”, then the function will return true, false otherwise.
var isFutures = str.contains(syminfo.tickerid, "!")
plot(isFutures ? 1 : 0)
```

### Returns
True if the str was found in the source string, false otherwise.

### See also
`str.pos()`, `str.match()`

## str.endswith()
Returns true if the source string ends with the substring specified in str, false otherwise.

### Syntax & Overloads
```pine
str.endswith(source, str) → const bool
```
```pine
str.endswith(source, str) → simple bool
```
```pine
str.endswith(source, str) → series bool
```

### Arguments
- `source` (*const string*) — Source string.
- `str` (*const string*) — The substring to search for.

### Returns
True if the source string ends with the substring specified in str, false otherwise.

### See also
`str.startswith()`

## str.format()
Creates a formatted string using a specified formatting string (formatString) and one or more additional arguments (arg0, arg1, etc.). The formatting string defines the structure of the returned string, where all placeholders in curly brackets ({}) refer to the additional arguments. Each placeholder requires a number representing an argument's position, starting from 0. For instance, the placeholder {0} refers to the first argument after formatString (arg0), {1} refers to the second (arg1), and so on. The function replaces each placeholder with a string representation of the corresponding argument.

### Syntax & Overloads
```pine
str.format(formatString, arg0, arg1, ...) → simple string
```
```pine
str.format(formatString, arg0, arg1, ...) → series string
```

### Arguments
- `formatString` (*simple string*) — Format string.
- arg0, arg1, ... (simple int/float/bool/string) Values to format.

### Example
```pine
//@version=6
indicator("Simple `str.format()` demo")

//@variable A formatted string that includes representations of the current `bar_index` and `close` values.
//          The placeholder `{0}` refers to the first argument after the formatting string (`bar_index`), and
//          `{1}` refers to the second (`close`).
string labelText = str.format("Current bar index: {0}\nCurrent bar close: {1}", bar_index, close)

// Draw a label to display the `labelText` string at the current bar's `high` price.
label.new(bar_index, high, labelText)
```

### Example
```pine
//@version=6
indicator("Extensive `str.format()` demo", overlay=true)
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

### Returns
The formatted string.

### Remarks
The string used as the formatString argument can contain single quote characters ('). However, programmers must pair all single quotes in that string to avoid unexpected formatting results.
All non-quoted left curly brackets must have corresponding right curly brackets in the formatting string. If the string contains imbalanced left curly brackets, it causes a runtime error. For example, "ab {0} de" and "ab }{0} de" are valid formatting strings, but "ab {0'}' de", "ab }{0}{ de" and "''{''{0}" are not.
The placeholders for "int" or "float" values or arrays can include modifiers and formatting tokens to customize how the resulting string represents them.
For example, the placeholder {0,number,#.#) specifies that the result inserts characters representing the arg0 number rounded to one fractional digit.
For detailed information about placeholders and supported formats, refer to the Formatting strings section of our User Manual's Strings page.
The apostrophe (') acts as a quote character rather than a literal character inside formatting strings. If a formatting string has a sequence of characters between two apostrophes, the function's result includes those characters literally. For instance, the substring '{' adds a literal { character to the result instead of treating it as the start of a placeholder. Note that if a formatting string uses apostrophes instead of quotation marks for its enclosing characters, the string must escape any apostrophes within the character sequence using the backslash.

## str.format_time()
Converts the time timestamp into a string formatted according to format and timezone.

### Syntax
```pine
str.format_time(time, format, timezone) → series string
```

### Arguments
- `time` (*series int*) — UNIX time, in milliseconds.
- `format` (*series string*) — A format string specifying the date/time representation of the time in the returned string. All letters used in the string, except those escaped by single quotation marks ', are considered formatting tokens and will be used as a formatting instruction. Refer to the Remarks section for a list of the most useful tokens. Optional. The default is "yyyy-MM-dd'T'HH:mm:ssZ", which represents the ISO 8601 standard.
- `timezone` (*series string*) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is syminfo.timezone.

### Example
```pine
//@version=6
indicator("str.format_time")
if timeframe.change("1D")
    formattedTime = str.format_time(time, "yyyy-MM-dd HH:mm", syminfo.timezone)
    label.new(bar_index, high, formattedTime)
```

### Returns
The formatted string.

### Remarks
The M, d, h, H, m and s tokens can all be doubled to generate leading zeros. For example, the month of January will display as 1 with M, or 01 with MM.
The most frequently used formatting tokens are:
y - Year. Use yy to output the last two digits of the year or yyyy to output all four. Year 2000 will be 00 with yy or 2000 with yyyy.
M - Month. Not to be confused with lowercase m, which stands for minute.
d - Day of the month.
a - AM/PM postfix.
h - Hour in the 12-hour format. The last hour of the day will be 11 in this format.
H - Hour in the 24-hour format. The last hour of the day will be 23 in this format.
m - Minute.
s - Second.
S - Fractions of a second.
Z - Timezone, the HHmm offset from UTC, preceded by either + or -.

## str.length()
Returns an integer corresponding to the amount of chars in that string.

### Syntax & Overloads
```pine
str.length(string) → const int
```
```pine
str.length(string) → simple int
```
```pine
str.length(string) → series int
```

### Arguments
- `string` (*const string*) — Source string.

### Returns
The number of chars in source string.

## str.lower()
Returns a new string with all letters converted to lowercase.

### Syntax & Overloads
```pine
str.lower(source) → const string
```
```pine
str.lower(source) → simple string
```
```pine
str.lower(source) → series string
```

### Arguments
- `source` (*const string*) — String to be converted.

### Returns
A new string with all letters converted to lowercase.

### See also
`str.upper()`

## str.match()
Returns the new substring of the source string if it matches a regex regular expression, an empty string otherwise.

### Syntax & Overloads
```pine
str.match(source, regex) → simple string
```
```pine
str.match(source, regex) → series string
```

### Arguments
- `source` (*simple string*) — Source string.
- `regex` (*simple string*) — The regular expression to which this string is to be matched.

### Example
```pine
//@version=6
indicator("str.match")

s = input.string("It's time to sell some NASDAQ:AAPL!")

// finding first substring that matches regular expression "[\w]+:[\w]+"
var string tickerid = str.match(s, "[\\w]+:[\\w]+")

if barstate.islastconfirmedhistory
    label.new(bar_index, high, text = tickerid) // "NASDAQ:AAPL"
```

### Returns
The new substring of the source string if it matches a regex regular expression, an empty string otherwise.

### Remarks
Function returns first occurrence of the regular expression in the source string.
The backslash "\" symbol in theregex string needs to be escaped with additional backslash, e.g. "\\d" stands for regular expression "\d".

### See also
`str.contains()`, `str.substring()`

## str.pos()
Returns the position of the first occurrence of the str string in the source string, 'na' otherwise.

### Syntax & Overloads
```pine
str.pos(source, str) → const int
```
```pine
str.pos(source, str) → simple int
```
```pine
str.pos(source, str) → series int
```

### Arguments
- `source` (*const string*) — Source string.
- `str` (*const string*) — The substring to search for.

### Returns
Position of the str string in the source string.

### Remarks
Strings indexing starts at 0.

### See also
`str.contains()`, `str.match()`, `str.substring()`

## str.repeat()
Constructs a new string containing the source string repeated repeat times with the separator injected between each repeated instance.

### Syntax & Overloads
```pine
str.repeat(source, repeat, separator) → const string
```
```pine
str.repeat(source, repeat, separator) → input string
```
```pine
str.repeat(source, repeat, separator) → simple string
```
```pine
str.repeat(source, repeat, separator) → series string
```

### Arguments
- `source` (*const string*) — String to repeat.
- `repeat` (*const int*) — Number of times to repeat the source string. Must be greater than or equal to 0.
- `separator` (*const string*) — String to inject between repeated values. Optional. The default is empty string.

### Example
```pine
//@version=6
indicator("str.repeat")
repeat = str.repeat("?", 3, ",") // Returns "?,?,?"
label.new(bar_index,close,repeat)
```

### Remarks
Returns na if the source is na.

## str.replace()
Returns a new string with the Nth occurrence of the target string replaced by the replacement string, where N is specified in occurrence.

### Syntax & Overloads
```pine
str.replace(source, target, replacement, occurrence) → const string
```
```pine
str.replace(source, target, replacement, occurrence) → simple string
```
```pine
str.replace(source, target, replacement, occurrence) → series string
```

### Arguments
- `source` (*const string*) — Source string.
- `target` (*const string*) — String to be replaced.
- `replacement` (*const string*) — String to be inserted instead of the target string.
- `occurrence` (*const int*) — N-th occurrence of the target string to replace. Indexing starts at 0 for the first match. Optional. Default value is 0.

### Example
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

### Returns
Processed string.

### See also
`str.replace_all()`, `str.match()`

## str.replace_all()
Replaces each occurrence of the target string in the source string with the replacement string.

### Syntax & Overloads
```pine
str.replace_all(source, target, replacement) → simple string
```
```pine
str.replace_all(source, target, replacement) → series string
```

### Arguments
- `source` (*simple string*) — Source string.
- `target` (*simple string*) — String to be replaced.
- `replacement` (*simple string*) — String to be substituted for each occurrence of target string.

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

### Returns
The id of an array of strings.

## str.startswith()
Returns true if the source string starts with the substring specified in str, false otherwise.

### Syntax & Overloads
```pine
str.startswith(source, str) → const bool
```
```pine
str.startswith(source, str) → simple bool
```
```pine
str.startswith(source, str) → series bool
```

### Arguments
- `source` (*const string*) — Source string.
- `str` (*const string*) — The substring to search for.

### Returns
True if the source string starts with the substring specified in str, false otherwise.

### See also
`str.endswith()`

## str.substring()
Returns a new string that is a substring of the source string. The substring begins with the character at the index specified by begin_pos and extends to 'end_pos - 1' of the source string.

### Syntax & Overloads
```pine
str.substring(source, begin_pos, end_pos) → const string
```
```pine
str.substring(source, begin_pos, end_pos) → simple string
```
```pine
str.substring(source, begin_pos, end_pos) → series string
```

### Arguments
- `source` (*const string*) — Source string from which to extract the substring.
- `begin_pos` (*const int*) — The beginning position of the extracted substring. It is inclusive (the extracted substring includes the character at that position).
- `end_pos` (*const int*) — The ending position. It is exclusive (the extracted string does NOT include that position's character). Optional. The default is the length of the source string.

### Example
```pine
//@version=6
indicator("str.substring", overlay = true)
sym= input.symbol("NASDAQ:AAPL")
pos = str.pos(sym, ":") // Get position of ":" character
tkr= str.substring(sym, pos+1) // "AAPL"
if barstate.islastconfirmedhistory
    label.new(bar_index, high, text = tkr)
```

### Returns
The substring extracted from the source string.

### Remarks
Strings indexing starts from 0. If begin_pos is equal to end_pos, the function returns an empty string.

### See also
`str.contains()`, `str.pos()`, `str.match()`

## str.tonumber()
Converts a value represented in string to its "float" equivalent.

### Syntax & Overloads
```pine
str.tonumber(string) → const float
```
```pine
str.tonumber(string) → input float
```
```pine
str.tonumber(string) → simple float
```
```pine
str.tonumber(string) → series float
```

### Arguments
- `string` (*const string*) — String containing the representation of an integer or floating point value.

### Returns
A "float" equivalent of the value in string. If the value is not a properly formed integer or floating point value, the function returns na.

## str.tostring()

### Syntax & Overloads
```pine
str.tostring(value) → const string
```
```pine
str.tostring(value, format) → simple string
```
```pine
str.tostring(value, format) → series string
```
```pine
str.tostring(value) → simple string
```
```pine
str.tostring(value) → series string
```

### Arguments
- `value` (*const enum*) — Value or array ID whose elements are converted to a string.

### Returns
The string representation of the value argument.
If the value argument is a string, it is returned as is.
When the value is na, the function returns the string "NaN".

### Remarks
The formatting of float values will also round those values when necessary, e.g. str.tostring(3.99, '#') will return "4".
To display trailing zeros, use '0' instead of '#'. For example, '#.000'.
When using format.mintick, the value will be rounded to the nearest number that can be divided by syminfo.mintick without the remainder. The string is returned with trailing zeros.
If the x argument is a string, the same string value will be returned.
Bool type arguments return "true" or "false".
When x is na, the function returns "NaN".

## str.trim()
Constructs a new string with all consecutive whitespaces and other control characters (e.g., “\n”, “\t”, etc.) removed from the left and right of the source.

### Syntax & Overloads
```pine
str.trim(source) → const string
```
```pine
str.trim(source) → input string
```
```pine
str.trim(source) → simple string
```
```pine
str.trim(source) → series string
```

### Arguments
- `source` (*const string*) — String to trim.

### Example
```pine
//@version=6
indicator("str.trim")
trim = str.trim("    abc    ") // Returns "abc"
label.new(bar_index,close,trim)
```

### Remarks
Returns an empty string ("") if the result is empty after the trim or if the source is na.

## str.upper()
Returns a new string with all letters converted to uppercase.

### Syntax & Overloads
```pine
str.upper(source) → const string
```
```pine
str.upper(source) → simple string
```
```pine
str.upper(source) → series string
```

### Arguments
- `source` (*const string*) — String to be converted.

### Returns
A new string with all letters converted to uppercase.

### See also
`str.lower()`

## string()
Casts na to string

### Syntax & Overloads
```pine
string(x) → const string
```
```pine
string(x) → input string
```
```pine
string(x) → simple string
```
```pine
string(x) → series string
```

### Arguments
- `x` (*const string*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to string.

### See also
`float()`, `int()`, `bool()`, `color()`, `line()`, `label()`

## time()
Returns the opening UNIX timestamp for the specified timeframe and session, or na if the time point is outside the session.

### Syntax & Overloads
```pine
time(timeframe, session, bars_back, timeframe_bars_back) → series int
```
```pine
time(timeframe, session, timezone, bars_back, timeframe_bars_back) → series int
```

### Arguments
- `timeframe` (*series string*) — The timeframe of the timestamp calculation. If the value is an empty string, the function uses the script's main timeframe.
- `session` (*series string*) — Optional. The session string for filtering times. The function returns a timestamp if the time is in the specified session, or na if the time is outside the session. If the argument is an empty string, the function uses the default, which is the symbol's session.
- `bars_back` (*series int*) — Optional. The bar offset on the script's main timeframe. If the value is positive, the function finds the bar that is N bars before the current bar on the main timeframe, then retrieves the timestamp of the corresponding bar on the timeframe specified by the timeframe argument. If the value is a negative number from -1 to -500, the function calculates the expected timestamp of the timeframe bar corresponding to N bars after the current bar on the main timeframe. The default is 0.
- `timeframe_bars_back` (*series int*) — Optional. The additional bar offset on the timeframe specified by the timeframe argument. If the value is positive, the function retrieves the timestamp of the bar that is N timeframe bars before the one corresponding to the bars_back offset. If the value is a negative number from -1 to -500, the function calculates the expected timestamp of the timeframe bar that is N timeframe bars after the one corresponding to the bars_back offset. The default is 0.

### Example
```pine
//@version=6
indicator("Time", overlay=true)
// Try this on chart AAPL,1
timeinrange(res, sess) => not na(time(res, sess, "America/New_York")) ? 1 : 0
plot(timeinrange("1", "1300-1400"), color=color.red)

// This plots 1.0 at every start of 10 minute bar on a 1 minute chart:
newbar(res) => ta.change(time(res)) == 0 ? 0 : 1
plot(newbar("10"))
```
While setting up a session you can specify not just the hours and minutes but also the days of the week that will be included in that session.
If the days aren't specified, the session is considered to have been set from Sunday (1) to Saturday (7), i.e. "1100-2000" is the same as "1100-1200:1234567".
You can change that by specifying the days. For example, on a symbol that is traded seven days a week with the 24-hour trading session the following script will not color Saturdays and Sundays:

### Example
```pine
//@version=6
indicator("Time", overlay=true)
t1 = time(timeframe.period, "0000-0000:23456")
bgcolor(not na(t1) ? color.new(color.blue, 90) : na)
```
One session argument can include several different sessions, separated by commas. For example, the following script will highlight the bars from 10:00 to 11:00 and from 14:00 to 15:00 (workdays only):

### Example
```pine
//@version=6
indicator("Time", overlay=true)
t1 = time(timeframe.period, "1000-1100,1400-1500:23456")
bgcolor(not na(t1) ? color.new(color.blue, 90) : na)
```

### Returns
The opening UNIX timestamp.

### Remarks
UNIX time is a standardized date and time representation that measures the number of non-leap seconds elapsed since January 1, 1970 at 00:00:00 UTC. Pine Script expresses UNIX time values in milliseconds. See the UNIX timestamps section of the User Manual's Time page to learn more.

### See also
`time`

## time_close()
Returns the closing UNIX timestamp for the specified timeframe and session, or na if the time point is outside the session. On tick charts and price-based charts such as Renko, line break, Kagi, point & figure, and range, the function returns na on the latest realtime bar because the future closing time is unpredictable. However, it returns a valid timestamp for any previous bar.

### Syntax & Overloads
```pine
time_close(timeframe, session, bars_back, timeframe_bars_back) → series int
```
```pine
time_close(timeframe, session, timezone, bars_back, timeframe_bars_back) → series int
```

### Arguments
- `timeframe` (*series string*) — The timeframe of the timestamp calculation. If the value is an empty string, the function uses the script's main timeframe.
- `session` (*series string*) — Optional. The session string for filtering times. The function returns a timestamp if the time is in the specified session, or na if the time is outside the session. If the argument is an empty string, the function uses the default, which is the symbol's session.
- `bars_back` (*series int*) — Optional. The bar offset on the script's main timeframe. If the value is positive, the function finds the bar that is N bars before the current bar on the main timeframe, then retrieves the timestamp of the corresponding bar on the timeframe specified by the timeframe argument. If the value is a negative number from -1 to -500, the function calculates the expected timestamp of the timeframe bar corresponding to N bars after the current bar on the main timeframe. The default is 0.
- `timeframe_bars_back` (*series int*) — Optional. The additional bar offset on the timeframe specified by the timeframe argument. If the value is positive, the function retrieves the timestamp of the bar that is N timeframe bars before the one corresponding to the bars_back offset. If the value is a negative number from -1 to -500, the function calculates the expected timestamp of the timeframe bar that is N timeframe bars after the one corresponding to the bars_back offset. The default is 0.

### Example
```pine
//@version=6
indicator("Time", overlay=true)
t1 = time_close(timeframe.period, "1200-1300", "America/New_York")
bgcolor(not na(t1) ? color.new(color.blue, 90) : na)
```

### Returns
The closing UNIX timestamp.

### Remarks
UNIX time is a standardized date and time representation that measures the number of non-leap seconds elapsed since January 1, 1970 at 00:00:00 UTC. Pine Script expresses UNIX time values in milliseconds. See the UNIX timestamps section of the User Manual's Time page to learn more.

### See also
`time_close`

## timeframe.change()
Detects changes in the specified timeframe.

### Syntax
```pine
timeframe.change(timeframe) → series bool
```

### Arguments
- `timeframe` (*series string*) — String formatted according to the User manual's timeframe string specifications.

### Example
```pine
//@version=6
// Run this script on an intraday chart.
indicator("New day started", overlay = true)
// Highlights the first bar of the new day.
isNewDay = timeframe.change("1D")
bgcolor(isNewDay ? color.new(color.green, 80) : na)
```

### Returns
Returns true on the first bar of a new timeframe, false otherwise.

## timeframe.from_seconds()
Converts a number of seconds into a valid timeframe string.

### Syntax & Overloads
```pine
timeframe.from_seconds(seconds) → simple string
```
```pine
timeframe.from_seconds(seconds) → series string
```

### Arguments
- `seconds` (*simple int*) — The number of seconds in the timeframe.

### Example
```pine
//@version=6
indicator("HTF Close", "", true)
int chartTf = timeframe.in_seconds()
string tfTimes5 = timeframe.from_seconds(chartTf * 5)
float htfClose = request.security(syminfo.tickerid, tfTimes5, close)
plot(htfClose)
```

### Returns
A timeframe string compliant with timeframe string specifications.

### Remarks
If no valid timeframe exists for the quantity of seconds supplied, the next higher valid timeframe will be returned. Accordingly, one second or less will return "1S", 2-5 seconds will return "5S", and 604,799 seconds (one second less than 7 days) will return "7D".
If the seconds exactly represent two or more valid timeframes, the one with the larger base unit will be used. Thus 604,800 seconds (7 days) returns "1W", not "7D".
All values above 31,622,400 (366 days) return "12M".

### See also
`timeframe.in_seconds()`, `request.security`, `request.security_lower_tf`

## timeframe.in_seconds()
Converts a timeframe string into seconds.

### Syntax & Overloads
```pine
timeframe.in_seconds(timeframe) → simple int
```
```pine
timeframe.in_seconds(timeframe) → series int
```

### Arguments
- `timeframe` (*simple string*) — Timeframe string in timeframe string specifications format. Optional. The default is timeframe.period.

### Example
```pine
//@version=6
indicator("`timeframe_in_seconds()`"),

// Get a user-selected timeframe.
tfInput = input.timeframe("1D")

// Convert it into an "int" number of seconds.
secondsInTf = timeframe.in_seconds(tfInput)

plot(secondsInTf)
```

### Returns
The "int" representation of the number of seconds in the timeframe string.

### Remarks
When the timeframe is "1M" or more, calculations use 2628003 as the number of seconds in one month, which represents 30.4167 (365/12) days.

### See also
`input.timeframe()`, `timeframe.period`, `timeframe.from_seconds()`

## timestamp()
Function timestamp returns UNIX time of specified date and time.

### Syntax & Overloads
```pine
timestamp(dateString) → const int
```
```pine
timestamp(dateString) → series int
```
```pine
timestamp(year, month, day, hour, minute, second) → simple int
```
```pine
timestamp(year, month, day, hour, minute, second) → series int
```
```pine
timestamp(timezone, year, month, day, hour, minute, second) → simple int
```
```pine
timestamp(timezone, year, month, day, hour, minute, second) → series int
```

### Arguments
- `dateString` (*const string*) — A string containing the date and, optionally, the time and time zone. Its format must comply with either the IETF RFC 2822 or ISO 8601 standards ("DD MMM YYYY hh:mm:ss ±hhmm" or "YYYY-MM-DDThh:mm:ss±hh:mm", so "20 Feb 2020" or "2020-02-20"). If no time is supplied, "00:00" is used. If no time zone is supplied, GMT+0 will be used. Note that this diverges from the usual behavior of the function where it returns time in the exchange's timezone.

### Example
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

### Returns
UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.

### See also
`time()`, `time`, `timenow`, `syminfo.timezone`

## weekofyear()
Calculates the week number of the year, in a specified time zone, from a UNIX timestamp.

### Syntax
```pine
weekofyear(time, timezone) → series int
```

### Arguments
- `time` (*series int*) — A UNIX timestamp in milliseconds.
- `timezone` (*series string*) — Optional. Specifies the time zone of the returned week number. The value can be a time zone string in UTC/GMT offset notation (e.g., "UTC-5") or IANA time zone database notation (e.g., "America/New_York"). The default is syminfo.timezone.

### Returns
The calculated week number, expressed in the specified time zone.

### Remarks
A UNIX timestamp represents the number of milliseconds elapsed since 00:00 UTC on 1970-01-01. The meaning of a UNIX timestamp does not change relative to any time zone.

### See also
`weekofyear`, `dayofmonth()`, `dayofweek()`, `time()`, `year()`, `month()`, `hour()`, `minute()`, `second()`

## year()

### Syntax
```pine
year(time, timezone) → series int
```

### Arguments
- `time` (*series int*) — UNIX time in milliseconds.
- `timezone` (*series string*) — Allows adjusting the returned value to a time zone specified in either UTC/GMT notation (e.g., "UTC-5", "GMT+0530") or as an IANA time zone database name (e.g., "America/New_York"). Optional. The default is syminfo.timezone.

### Returns
Year (in exchange timezone) for provided UNIX time.

### Remarks
UNIX time is the number of milliseconds that have elapsed since 00:00:00 UTC, 1 January 1970.
Note that this function returns the year based on the time of the bar's open. For overnight sessions (e.g. EURUSD, where Monday session starts on Sunday, 17:00 UTC-4) this value can be lower by 1 than the year of the trading day.

### See also
`year`, `time()`, `month()`, `dayofmonth()`, `dayofweek()`, `hour()`, `minute()`, `second()`
