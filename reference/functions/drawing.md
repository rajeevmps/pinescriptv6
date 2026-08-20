<!--
Source: https://www.tradingview.com/pine-script-reference/v6/
Pine Script v6 — official TradingView language reference manual
Retrieved: 2026-08-20
-->

# Plotting and drawing functions

Everything that puts pixels on the chart: plots, fills, lines, boxes, labels, polylines, and tables.

**120 functions** · Source: [Pine Script® v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/)

## Index

- [`barcolor()`](#barcolor)
- [`bgcolor()`](#bgcolor)
- [`box()`](#box)
- [`box.copy()`](#boxcopy)
- [`box.delete()`](#boxdelete)
- [`box.get_bottom()`](#boxgetbottom)
- [`box.get_left()`](#boxgetleft)
- [`box.get_right()`](#boxgetright)
- [`box.get_top()`](#boxgettop)
- [`box.new()`](#boxnew)
- [`box.set_bgcolor()`](#boxsetbgcolor)
- [`box.set_border_color()`](#boxsetbordercolor)
- [`box.set_border_style()`](#boxsetborderstyle)
- [`box.set_border_width()`](#boxsetborderwidth)
- [`box.set_bottom()`](#boxsetbottom)
- [`box.set_bottom_right_point()`](#boxsetbottomrightpoint)
- [`box.set_extend()`](#boxsetextend)
- [`box.set_left()`](#boxsetleft)
- [`box.set_lefttop()`](#boxsetlefttop)
- [`box.set_right()`](#boxsetright)
- [`box.set_rightbottom()`](#boxsetrightbottom)
- [`box.set_text()`](#boxsettext)
- [`box.set_text_color()`](#boxsettextcolor)
- [`box.set_text_font_family()`](#boxsettextfontfamily)
- [`box.set_text_formatting()`](#boxsettextformatting)
- [`box.set_text_halign()`](#boxsettexthalign)
- [`box.set_text_size()`](#boxsettextsize)
- [`box.set_text_valign()`](#boxsettextvalign)
- [`box.set_text_wrap()`](#boxsettextwrap)
- [`box.set_top()`](#boxsettop)
- [`box.set_top_left_point()`](#boxsettopleftpoint)
- [`box.set_xloc()`](#boxsetxloc)
- [`chart.point.copy()`](#chartpointcopy)
- [`chart.point.from_index()`](#chartpointfromindex)
- [`chart.point.from_time()`](#chartpointfromtime)
- [`chart.point.new()`](#chartpointnew)
- [`chart.point.now()`](#chartpointnow)
- [`fill()`](#fill)
- [`hline()`](#hline)
- [`label()`](#label)
- [`label.copy()`](#labelcopy)
- [`label.delete()`](#labeldelete)
- [`label.get_text()`](#labelgettext)
- [`label.get_x()`](#labelgetx)
- [`label.get_y()`](#labelgety)
- [`label.new()`](#labelnew)
- [`label.set_color()`](#labelsetcolor)
- [`label.set_point()`](#labelsetpoint)
- [`label.set_size()`](#labelsetsize)
- [`label.set_style()`](#labelsetstyle)
- [`label.set_text()`](#labelsettext)
- [`label.set_text_font_family()`](#labelsettextfontfamily)
- [`label.set_text_formatting()`](#labelsettextformatting)
- [`label.set_textalign()`](#labelsettextalign)
- [`label.set_textcolor()`](#labelsettextcolor)
- [`label.set_tooltip()`](#labelsettooltip)
- [`label.set_x()`](#labelsetx)
- [`label.set_xloc()`](#labelsetxloc)
- [`label.set_xy()`](#labelsetxy)
- [`label.set_y()`](#labelsety)
- [`label.set_yloc()`](#labelsetyloc)
- [`line()`](#line)
- [`line.copy()`](#linecopy)
- [`line.delete()`](#linedelete)
- [`line.get_price()`](#linegetprice)
- [`line.get_x1()`](#linegetx1)
- [`line.get_x2()`](#linegetx2)
- [`line.get_y1()`](#linegety1)
- [`line.get_y2()`](#linegety2)
- [`line.new()`](#linenew)
- [`line.set_color()`](#linesetcolor)
- [`line.set_extend()`](#linesetextend)
- [`line.set_first_point()`](#linesetfirstpoint)
- [`line.set_second_point()`](#linesetsecondpoint)
- [`line.set_style()`](#linesetstyle)
- [`line.set_width()`](#linesetwidth)
- [`line.set_x1()`](#linesetx1)
- [`line.set_x2()`](#linesetx2)
- [`line.set_xloc()`](#linesetxloc)
- [`line.set_xy1()`](#linesetxy1)
- [`line.set_xy2()`](#linesetxy2)
- [`line.set_y1()`](#linesety1)
- [`line.set_y2()`](#linesety2)
- [`linefill()`](#linefill)
- [`linefill.delete()`](#linefilldelete)
- [`linefill.get_line1()`](#linefillgetline1)
- [`linefill.get_line2()`](#linefillgetline2)
- [`linefill.new()`](#linefillnew)
- [`linefill.set_color()`](#linefillsetcolor)
- [`plot()`](#plot)
- [`plotarrow()`](#plotarrow)
- [`plotbar()`](#plotbar)
- [`plotcandle()`](#plotcandle)
- [`plotchar()`](#plotchar)
- [`plotshape()`](#plotshape)
- [`polyline.delete()`](#polylinedelete)
- [`polyline.new()`](#polylinenew)
- [`table()`](#table)
- [`table.cell()`](#tablecell)
- [`table.cell_set_bgcolor()`](#tablecellsetbgcolor)
- [`table.cell_set_height()`](#tablecellsetheight)
- [`table.cell_set_text()`](#tablecellsettext)
- [`table.cell_set_text_color()`](#tablecellsettextcolor)
- [`table.cell_set_text_font_family()`](#tablecellsettextfontfamily)
- [`table.cell_set_text_formatting()`](#tablecellsettextformatting)
- [`table.cell_set_text_halign()`](#tablecellsettexthalign)
- [`table.cell_set_text_size()`](#tablecellsettextsize)
- [`table.cell_set_text_valign()`](#tablecellsettextvalign)
- [`table.cell_set_tooltip()`](#tablecellsettooltip)
- [`table.cell_set_width()`](#tablecellsetwidth)
- [`table.clear()`](#tableclear)
- [`table.delete()`](#tabledelete)
- [`table.merge_cells()`](#tablemergecells)
- [`table.new()`](#tablenew)
- [`table.set_bgcolor()`](#tablesetbgcolor)
- [`table.set_border_color()`](#tablesetbordercolor)
- [`table.set_border_width()`](#tablesetborderwidth)
- [`table.set_frame_color()`](#tablesetframecolor)
- [`table.set_frame_width()`](#tablesetframewidth)
- [`table.set_position()`](#tablesetposition)

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

## box.delete()

Deletes the specified box object. If it has already been deleted, does nothing.
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

## box.set_bgcolor()

Sets the background color of the box.
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

## box.set_text_formatting()

Sets the formatting attributes the drawing applies to displayed text.

## box.set_text_halign()

The function sets the horizontal alignment of the box's text.
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

## chart.point.copy()

Creates a copy of a chart.point object with the specified id.
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

## label.delete()

Deletes the specified label object. If it has already been deleted, does nothing.
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

## label.set_color()

Sets label border and arrow color.
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

## label.set_text_formatting()

Sets the formatting attributes the drawing applies to displayed text.

## label.set_textalign()

Sets the alignment for the label text.
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
### Syntax

```pine
label.set_yloc(id, yloc) → void
```

### Arguments

- `yloc` (*series string*) — New y-location value.
- `id` (*series label*) — Label object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_label.set_yloc).*

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

## line.delete()

Deletes the specified line object. If it has already been deleted, does nothing.
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

## line.set_color()

Sets the line color
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

## linefill.delete()

Deletes the specified linefill object. If it has already been deleted, does nothing.
### Syntax

```pine
linefill.delete(id) → void
```

### Arguments

- `id` (*series linefill*) — A linefill object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.delete).*

## linefill.get_line1()

Returns the ID of the first line used in the id linefill.
### Syntax

```pine
linefill.get_line1(id) → series line
```

### Arguments

- `id` (*series linefill*) — A linefill object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.get_line1).*

## linefill.get_line2()

Returns the ID of the second line used in the id linefill.
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

## linefill.set_color()

The function sets the color of the linefill object passed to it.
### Syntax

```pine
linefill.set_color(id, color) → void
```

### Arguments

- `color` (*series color*) — The color of the linefill object.
- `id` (*series linefill*) — A linefill object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_linefill.set_color).*

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

## polyline.delete()

Deletes the specified polyline object. It has no effect if the id doesn't exist.
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

## table.cell_set_bgcolor()

The function sets the background color of the cell.
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

## table.cell_set_text_color()

The function sets the color of the text inside the cell.
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

## table.cell_set_text_formatting()

Sets the formatting attributes the drawing applies to displayed text.

## table.cell_set_text_halign()

The function sets the horizontal alignment of the cell's text.
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

## table.cell_set_width()

The function sets the width of the cell.
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

## table.set_bgcolor()

The function sets the background color of a table.
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
### Syntax

```pine
table.set_position(table_id, position) → void
```

### Arguments

- `position` (*series string*) — Position of the table. Possible values are: [position.top_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_left), [position.top_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_center), [position.top_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.top_right), [position.middle_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_left), [position.middle_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_center), [position.middle_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.middle_right), [position.bottom_left](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_left), [position.bottom_center](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_center), [position.bottom_right](https://www.tradingview.com/pine-script-reference/v6/#var_position.bottom_right).
- `table_id` (*series table*) — A table object.

*Syntax and arguments from TradingView's Pine Editor docs data (early-v6 snapshot). Verify against the [live reference manual](https://www.tradingview.com/pine-script-reference/v6/#fun_table.set_position).*
