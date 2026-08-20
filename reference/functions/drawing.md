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
- `color` (*series color*) — Color of bars. You can use constants like 'red' or '#ff001a' as well as complex expressions like 'close >= open ? color.green : color.red'. Required argument.
- `offset` (*simple int*) — Shifts the color series to the left or to the right on the given number of bars. Default is 0.
- `editable` (*input bool*) — If true then barcolor style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — Optional. The number of bars, counting backwards from the most recent bar, on which the function can draw.
- `title` (*const string*) — Title of the barcolor. Optional argument.
- `display` (*input plot_simple_display*) — Controls where the barcolor is displayed. Possible values are: display.none, display.all. Default is display.all.

### Example
```pine
//@version=6
indicator("barcolor example", overlay=true)
barcolor(close < open ? color.black : color.white)
```

### See also
`bgcolor()`, `plot()`, `fill()`

## bgcolor()
Fill background of bars with specified color.

### Syntax
```pine
bgcolor(color, offset, editable, show_last, title, display, force_overlay) → void
```

### Arguments
- `color` (*series color*) — Color of the filled background. You can use constants like 'red' or '#ff001a' as well as complex expressions like 'close >= open ? color.green : color.red'. Required argument.
- `offset` (*simple int*) — Shifts the color series to the left or to the right on the given number of bars. Default is 0.
- `editable` (*input bool*) — If true then bgcolor style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — Optional. The number of bars, counting backwards from the most recent bar, on which the function can draw.
- `title` (*const string*) — Title of the bgcolor. Optional argument.
- `display` (*input plot_simple_display*) — Controls where the bgcolor is displayed. Possible values are: display.none, display.all. Default is display.all.
- `force_overlay` (*const bool*) — If true, the plotted results will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
```pine
//@version=6
indicator("bgcolor example", overlay=true)
bgcolor(close < open ? color.new(color.red,70) : color.new(color.green, 70))
```

### See also
`barcolor()`, `plot()`, `fill()`

## box()
Casts na to box.

### Syntax
```pine
box(x) → series box
```

### Arguments
- `x` (*series box*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to box.

### See also
`float()`, `int()`, `bool()`, `color()`, `string()`, `line()`, `label()`

## box.copy()
Clones the box object.

### Syntax
```pine
box.copy(id) → series box
```

### Arguments
- `id` (*series box*) — Box object.

### Example
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

### See also
`box.new()`, `box.delete()`

## box.delete()
Deletes the specified box object. If it has already been deleted, does nothing.

### Syntax
```pine
box.delete(id) → void
```

### Arguments
- `id` (*series box*) — A box object to delete.

### See also
`box.new()`

## box.get_bottom()
Returns the price value of the bottom border of the box.

### Syntax
```pine
box.get_bottom(id) → series float
```

### Arguments
- `id` (*series box*) — A box object.

### Returns
The price value.

### See also
`box.new()`, `box.set_bottom()`

## box.get_left()
Returns the bar index or the UNIX time (depending on the last value used for 'xloc') of the left border of the box.

### Syntax
```pine
box.get_left(id) → series int
```

### Arguments
- `id` (*series box*) — A box object.

### Returns
A bar index or a UNIX timestamp (in milliseconds).

### See also
`box.new()`, `box.set_left()`

## box.get_right()
Returns the bar index or the UNIX time (depending on the last value used for 'xloc') of the right border of the box.

### Syntax
```pine
box.get_right(id) → series int
```

### Arguments
- `id` (*series box*) — A box object.

### Returns
A bar index or a UNIX timestamp (in milliseconds).

### See also
`box.new()`, `box.set_right()`

## box.get_top()
Returns the price value of the top border of the box.

### Syntax
```pine
box.get_top(id) → series float
```

### Arguments
- `id` (*series box*) — A box object.

### Returns
The price value.

### See also
`box.new()`, `box.set_top()`

## box.new()
Creates a new box object.

### Syntax & Overloads
```pine
box.new(top_left, bottom_right, border_color, border_width, border_style, extend, xloc, bgcolor, text, text_size, text_color, text_halign, text_valign, text_wrap, text_font_family, force_overlay, text_formatting) → series box
```
```pine
box.new(left, top, right, bottom, border_color, border_width, border_style, extend, xloc, bgcolor, text, text_size, text_color, text_halign, text_valign, text_wrap, text_font_family, force_overlay, text_formatting) → series box
```

### Arguments
- `top_left` (*chart.point*) — A chart.point object that specifies the top-left corner location of the box.
- `bottom_right` (*chart.point*) — A chart.point object that specifies the bottom-right corner location of the box.
- `border_color` (*series color*) — Color of the four borders. Optional. The default is color.blue.
- `border_width` (*series int*) — Width of the four borders, in pixels. Optional. The default is 1 pixel.
- `border_style` (*series string*) — Style of the four borders. Possible values: line.style_solid, line.style_dotted, line.style_dashed. Optional. The default value is line.style_solid.
- `extend` (*series string*) — When extend.none is used, the horizontal borders start at the left border and end at the right border. With extend.left or extend.right, the horizontal borders are extended indefinitely to the left or right of the box, respectively. With extend.both, the horizontal borders are extended on both sides. Optional. The default value is extend.none.
- `xloc` (*series string*) — Determines whether the arguments to 'left' and 'right' are a bar index or a time value. If xloc = xloc.bar_index, the arguments must be a bar index. If xloc = xloc.bar_time, the arguments must be a UNIX time. Possible values: xloc.bar_index and xloc.bar_time. Optional. The default is xloc.bar_index.
- `bgcolor` (*series color*) — Background color of the box. Optional. The default is color.blue.
- `text` (*series string*) — The text to be displayed inside the box. Optional. The default is empty string.
- `text_size` (*series int/string*) — Optional. Size of the box's text. The size can be any positive integer, or one of the size.* built-in constant strings. The constant strings and their equivalent integer values are: size.auto (0), size.tiny (8), size.small (10), size.normal (14), size.large (20), size.huge (36). The default value is size.auto or 0.
- `text_color` (*series color*) — The color of the text. Optional. The default is color.black.
- `text_halign` (*series string*) — The horizontal alignment of the box's text. Optional. The default value is text.align_center. Possible values: text.align_left, text.align_center, text.align_right.
- `text_valign` (*series string*) — The vertical alignment of the box's text. Optional. The default value is text.align_center. Possible values: text.align_top, text.align_center, text.align_bottom.
- `text_wrap` (*series string*) — Optional. Whether to wrap text. Wrapped text starts a new line when it reaches the side of the box. Wrapped text lower than the bottom of the box is not displayed. Unwrapped text stays on a single line and is displayed past the width of the box if it is too long. If the text_size is 0 or text.wrap_auto, this setting has no effect. The default value is text.wrap_none. Possible values: text.wrap_none, text.wrap_auto.
- `text_font_family` (*series string*) — The font family of the text. Optional. The default value is font.family_default. Possible values: font.family_default, font.family_monospace.
- `force_overlay` (*const bool*) — If true, the drawing will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.
- `text_formatting` (*series text_format*) — The formatting of the displayed text. Formatting options support addition. For example, text.format_bold + text.format_italic will make the text both bold and italicized. Possible values: text.format_none, text.format_bold, text.format_italic. Optional. The default is text.format_none.

### Example
```pine
//@version=6
indicator("box.new")
var b = box.new(time, open, time + 60 * 60 * 24, close, xloc=xloc.bar_time, border_style=line.style_dashed)
box.set_lefttop(b, time, 100)
box.set_rightbottom(b, time + 60 * 60 * 24, 500)
box.set_bgcolor(b, color.green)
```

### Returns
The ID of a box object which may be used in box.set_*() and box.get_*() functions.

### See also
`box.delete()`, `box.get_left()`, `box.get_top()`, `box.get_right()`, `box.get_bottom()`, `box.set_top_left_point()`, `box.set_left()`, `box.set_top()`, `box.set_bottom_right_point()`, `box.set_right()`, `box.set_bottom()`, `box.set_border_color()`, `box.set_bgcolor()`, `box.set_border_width()`, `box.set_border_style()`, `box.set_extend()`, `box.set_text()`, `box.set_text_formatting()`, `box.set_xloc()`

## box.set_bgcolor()
Sets the background color of the box.

### Syntax
```pine
box.set_bgcolor(id, color) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `color` (*series color*) — New background color.

### See also
`box.new()`

## box.set_border_color()
Sets the border color of the box.

### Syntax
```pine
box.set_border_color(id, color) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `color` (*series color*) — New border color.

### See also
`box.new()`

## box.set_border_style()
Sets the border style of the box.

### Syntax
```pine
box.set_border_style(id, style) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `style` (*series string*) — New border style.

### See also
`box.new()`, `line.style_solid`, `line.style_dotted`, `line.style_dashed`

## box.set_border_width()
Sets the border width of the box.

### Syntax
```pine
box.set_border_width(id, width) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `width` (*series int*) — Width of the four borders, in pixels.

### See also
`box.new()`

## box.set_bottom()
Sets the bottom coordinate of the box.

### Syntax
```pine
box.set_bottom(id, bottom) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `bottom` (*series int/float*) — Price value of the bottom border.

### See also
`box.new()`, `box.get_bottom()`

## box.set_bottom_right_point()
Sets the bottom-right corner location of the id box to point.

### Syntax
```pine
box.set_bottom_right_point(id, point) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `point` (*chart.point*) — A chart.point object.

## box.set_extend()
Sets extending type of the border of this box object. When extend.none is used, the horizontal borders start at the left border and end at the right border. With extend.left or extend.right, the horizontal borders are extended indefinitely to the left or right of the box, respectively. With extend.both, the horizontal borders are extended on both sides.

### Syntax
```pine
box.set_extend(id, extend) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `extend` (*series string*) — New extending type.

### See also
`box.new()`, `extend.none`, `extend.right`, `extend.left`, `extend.both`

## box.set_left()
Sets the left coordinate of the box.

### Syntax
```pine
box.set_left(id, left) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `left` (*series int*) — Bar index or bar time of the left border. Note that objects positioned using xloc.bar_index cannot be drawn further than 500 bars into the future.

### See also
`box.new()`, `box.get_left()`

## box.set_lefttop()
Sets the left and top coordinates of the box.

### Syntax
```pine
box.set_lefttop(id, left, top) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `left` (*series int*) — Bar index or bar time of the left border.
- `top` (*series int/float*) — Price value of the top border.

### See also
`box.new()`, `box.get_left()`, `box.get_top()`

## box.set_right()
Sets the right coordinate of the box.

### Syntax
```pine
box.set_right(id, right) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `right` (*series int*) — Bar index or bar time of the right border. Note that objects positioned using xloc.bar_index cannot be drawn further than 500 bars into the future.

### See also
`box.new()`, `box.get_right()`

## box.set_rightbottom()
Sets the right and bottom coordinates of the box.

### Syntax
```pine
box.set_rightbottom(id, right, bottom) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `right` (*series int*) — Bar index or bar time of the right border.
- `bottom` (*series int/float*) — Price value of the bottom border.

### See also
`box.new()`, `box.get_right()`, `box.get_bottom()`

## box.set_text()
The function sets the text in the box.

### Syntax
```pine
box.set_text(id, text) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `text` (*series string*) — The text to be displayed inside the box.

### See also
`box.set_text_color()`, `box.set_text_size()`, `box.set_text_valign()`, `box.set_text_halign()`, `box.set_text_formatting()`

## box.set_text_color()
The function sets the color of the text inside the box.

### Syntax
```pine
box.set_text_color(id, text_color) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `text_color` (*series color*) — The color of the text.

### See also
`box.set_text()`, `box.set_text_size()`, `box.set_text_valign()`, `box.set_text_halign()`

## box.set_text_font_family()
The function sets the font family of the text inside the box.

### Syntax
```pine
box.set_text_font_family(id, text_font_family) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `text_font_family` (*series string*) — The font family of the text. Possible values: font.family_default, font.family_monospace.

### Example
```pine
//@version=6
indicator("Example of setting the box font")
if barstate.islastconfirmedhistory
    b = box.new(bar_index, open-ta.tr, bar_index-50, open-ta.tr*5, text="monospace")
    box.set_text_font_family(b, font.family_monospace)
```

### See also
`box.new()`, `font.family_default`, `font.family_monospace`

## box.set_text_formatting()
Sets the formatting attributes the drawing applies to displayed text.

### Syntax
```pine
box.set_text_formatting(id, text_formatting) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `text_formatting` (*series text_format*) — The formatting of the displayed text. Formatting options support addition. For example, text.format_bold + text.format_italic will make the text both bold and italicized. Possible values: text.format_none, text.format_bold, text.format_italic. Optional. The default is text.format_none.

### See also
`box.set_text_color()`, `box.set_text_size()`, `box.set_text_valign()`, `box.set_text_halign()`, `box.set_text()`

## box.set_text_halign()
The function sets the horizontal alignment of the box's text.

### Syntax
```pine
box.set_text_halign(id, text_halign) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `text_halign` (*series string*) — The horizontal alignment of a box's text. Possible values: text.align_left, text.align_center, text.align_right.

### See also
`box.set_text()`, `box.set_text_size()`, `box.set_text_valign()`, `box.set_text_color()`

## box.set_text_size()
The function sets the size of the box's text.

### Syntax
```pine
box.set_text_size(id, text_size) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `text_size` (*series int/string*) — Size of the box's text. The size can be any positive integer, or one of the size.* built-in constant strings. The constant strings and their equivalent integer values are: size.auto (0), size.tiny (8), size.small (10), size.normal (14), size.large (20), size.huge (36).

### See also
`box.set_text()`, `box.set_text_color()`, `box.set_text_valign()`, `box.set_text_halign()`

## box.set_text_valign()
The function sets the vertical alignment of a box's text.

### Syntax
```pine
box.set_text_valign(id, text_valign) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `text_valign` (*series string*) — The vertical alignment of the box's text. Possible values: text.align_top, text.align_center, text.align_bottom.

### See also
`box.set_text()`, `box.set_text_size()`, `box.set_text_color()`, `box.set_text_halign()`

## box.set_text_wrap()
The function sets the mode of wrapping of the text inside the box.

### Syntax
```pine
box.set_text_wrap(id, text_wrap) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `text_wrap` (*series string*) — Whether to wrap text. Wrapped text starts a new line when it reaches the side of the box. Wrapped text lower than the bottom of the box is not displayed. Unwrapped text stays on a single line and is displayed past the width of the box if it is too long. If the text_size is 0 or text.wrap_auto, this setting has no effect. Possible values: text.wrap_none, text.wrap_auto.

### See also
`box.set_text()`, `box.set_text_size()`, `box.set_text_valign()`, `box.set_text_halign()`, `box.set_text_color()`

## box.set_top()
Sets the top coordinate of the box.

### Syntax
```pine
box.set_top(id, top) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `top` (*series int/float*) — Price value of the top border.

### See also
`box.new()`, `box.get_top()`

## box.set_top_left_point()
Sets the top-left corner location of the id box to point.

### Syntax
```pine
box.set_top_left_point(id, point) → void
```

### Arguments
- `id` (*series box*) — A box object.
- `point` (*chart.point*) — A chart.point object.

## box.set_xloc()
Sets the left and right borders of a box and updates its xloc property.

### Syntax
```pine
box.set_xloc(id, left, right, xloc) → void
```

### Arguments
- `id` (*series box*) — The ID of the box object to update.
- `left` (*series int*) — The bar index or timestamp for the left border of the box.
- `right` (*series int*) — The bar index or timestamp for the right border of the box.
- `xloc` (*series string*) — Determines whether the box treats the left and right arguments as bar indices or timestamps. Possible values: xloc.bar_index and xloc.bar_time. If the value is xloc.bar_index, the arguments represent bar indices. If xloc.bar_time, the arguments represent UNIX timestamps.

### See also
`box.new()`, `xloc.bar_index`, `xloc.bar_time`

## chart.point.copy()
Creates a copy of a chart.point object with the specified id.

### Syntax
```pine
chart.point.copy(id) → chart.point
```

### Arguments
- `id` (*chart.point*) — A chart.point object.

## chart.point.from_index()
Returns a chart.point object with index as its x-coordinate and price as its y-coordinate.

### Syntax
```pine
chart.point.from_index(index, price) → chart.point
```

### Arguments
- `index` (*series int*) — The x-coordinate of the point, expressed as a bar index value.
- `price` (*series int/float*) — The y-coordinate of the point.

### Remarks
The time field values of chart.point instances returned from this function will be na, meaning drawing objects with xloc values set to xloc.bar_time will not work with them.

## chart.point.from_time()
Returns a chart.point object with time as its x-coordinate and price as its y-coordinate.

### Syntax
```pine
chart.point.from_time(time, price) → chart.point
```

### Arguments
- `time` (*series int*) — The x-coordinate of the point, expressed as a UNIX time value, in milliseconds.
- `price` (*series int/float*) — The y-coordinate of the point.

### Remarks
The index field values of chart.point instances returned from this function will be na, meaning drawing objects with xloc values set to xloc.bar_index will not work with them.

## chart.point.new()
Creates a new chart.point object with the specified time, index, and price.

### Syntax
```pine
chart.point.new(time, index, price) → chart.point
```

### Arguments
- `time` (*series int*) — The x-coordinate of the point, expressed as a UNIX time value, in milliseconds.
- `index` (*series int*) — The x-coordinate of the point, expressed as a bar index value.
- `price` (*series int/float*) — The y-coordinate of the point.

### Remarks
Whether a drawing object uses a point's time or index field as an x-coordinate depends on the xloc type used in the function call that returned the drawing.
It's important to note that this function does not verify that the time and index values refer to the same bar.

### See also
`polyline.new()`

## chart.point.now()
Returns a chart.point object with price as the y-coordinate

### Syntax
```pine
chart.point.now(price) → chart.point
```

### Arguments
- `price` (*series int/float*) — The y-coordinate of the point. Optional. The default is close.

### Remarks
The chart.point instance returned from this function records values for its index and time fields on the bar it executed on, making it suitable for use with drawing objects of any xloc type.

## fill()
Fills background between two plots or hlines with a given color.

### Syntax & Overloads
```pine
fill(hline1, hline2, color, title, editable, fillgaps, display) → void
```
```pine
fill(plot1, plot2, color, title, editable, show_last, fillgaps, display) → void
```
```pine
fill(plot1, plot2, top_value, bottom_value, top_color, bottom_color, title, display, fillgaps, editable) → void
```

### Arguments
- `hline1` (*hline*) — The first hline object. Required argument.
- `hline2` (*hline*) — The second hline object. Required argument.
- `color` (*series color*) — Color of the background fill. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `title` (*const string*) — Title of the created fill object. Optional argument.
- `editable` (*input bool*) — If true then fill style will be editable in Format dialog. Default is true.
- `fillgaps` (*const bool*) — Controls continuing fills on gaps, i.e., when one of the plot() calls returns an na value. When true, the last fill will continue on gaps. The default is false.
- `display` (*input plot_simple_display*) — Controls where the fill is displayed. Possible values are: display.none, display.all. Default is display.all.
- Fill between two horizontal lines

### Example
```pine
//@version=6
indicator("Fill between hlines", overlay = false)
h1 = hline(20)
h2 = hline(10)
fill(h1, h2, color = color.new(color.blue, 90))
```
Fill between two plots

### Example
```pine
//@version=6
indicator("Fill between plots", overlay = true)
p1 = plot(open)
p2 = plot(close)
fill(p1, p2, color = color.new(color.green, 90))
```
Gradient fill between two horizontal lines

### Example
```pine
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

### See also
`plot()`, `barcolor()`, `bgcolor()`, `hline()`, `color.new()`

## hline()
Renders a horizontal line at a given fixed price level.

### Syntax
```pine
hline(price, title, color, linestyle, linewidth, editable, display) → hline
```

### Arguments
- `price` (*input int/float*) — Price value at which the object will be rendered. Required argument.
- `title` (*const string*) — Title of the object.
- `color` (*input color*) — Color of the rendered line. Must be a constant value (not an expression). Optional argument.
- `linestyle` (*input hline_style*) — Style of the rendered line. Possible values are: hline.style_solid, hline.style_dotted, hline.style_dashed. Optional argument.
- `linewidth` (*input int*) — Width of the rendered line. Default value is 1.
- `editable` (*input bool*) — If true then hline style will be editable in Format dialog. Default is true.
- `display` (*input plot_simple_display*) — Controls where the hline is displayed. Possible values are: display.none, display.all. Default is display.all.

### Example
```pine
//@version=6
indicator("input.hline", overlay=true)
hline(3.14, title='Pi', color=color.blue, linestyle=hline.style_dotted, linewidth=2)

// You may fill the background between any two hlines with a fill() function:
h1 = hline(20)
h2 = hline(10)
fill(h1, h2, color=color.new(color.green, 90))
```

### Returns
An hline object, that can be used in fill()

### See also
`fill()`

## label()
Casts na to label

### Syntax
```pine
label(x) → series label
```

### Arguments
- `x` (*series label*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to label.

### See also
`float()`, `int()`, `bool()`, `color()`, `string()`, `line()`

## label.copy()
Clones the label object.

### Syntax
```pine
label.copy(id) → series label
```

### Arguments
- `id` (*series label*) — Label object.

### Example
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

### Returns
New label ID object which may be passed to label.setXXX and label.getXXX functions.

### See also
`label.new()`, `label.delete()`

## label.delete()
Deletes the specified label object. If it has already been deleted, does nothing.

### Syntax
```pine
label.delete(id) → void
```

### Arguments
- `id` (*series label*) — Label object to delete.

### See also
`label.new()`

## label.get_text()
Returns the text of this label object.

### Syntax
```pine
label.get_text(id) → series string
```

### Arguments
- `id` (*series label*) — Label object.

### Example
```pine
//@version=6
indicator("label.get_text")
my_label = label.new(time, open, text="Open bar text", xloc=xloc.bar_time)
a = label.get_text(my_label)
label.new(time, close, text = a + " new", xloc=xloc.bar_time)
```

### Returns
String object containing the text of this label.

### See also
`label.new()`

## label.get_x()
Returns UNIX time or bar index (depending on the last xloc value set) of this label's position.

### Syntax
```pine
label.get_x(id) → series int
```

### Arguments
- `id` (*series label*) — Label object.

### Example
```pine
//@version=6
indicator("label.get_x")
my_label = label.new(time, open, text="Open bar text", xloc=xloc.bar_time)
a = label.get_x(my_label)
plot(time - label.get_x(my_label)) //draws zero plot
```

### Returns
UNIX timestamp (in milliseconds) or bar index.

### See also
`label.new()`

## label.get_y()
Returns price of this label's position.

### Syntax
```pine
label.get_y(id) → series float
```

### Arguments
- `id` (*series label*) — Label object.

### Returns
Floating point value representing price.

### See also
`label.new()`

## label.new()
Creates new label object.

### Syntax & Overloads
```pine
label.new(point, text, xloc, yloc, color, style, textcolor, size, textalign, tooltip, text_font_family, force_overlay, text_formatting) → series label
```
```pine
label.new(x, y, text, xloc, yloc, color, style, textcolor, size, textalign, tooltip, text_font_family, force_overlay, text_formatting) → series label
```

### Arguments
- `point` (*chart.point*) — A chart.point object that specifies the label's location.
- `text` (*series string*) — Label text. Default is empty string.
- `xloc` (*series string*) — See description of x argument. Possible values: xloc.bar_index and xloc.bar_time. Default is xloc.bar_index.
- `yloc` (*series string*) — Possible values are yloc.price, yloc.abovebar, yloc.belowbar. If yloc=yloc.price, y argument specifies the price of the label position. If yloc=yloc.abovebar, label is located above bar. If yloc=yloc.belowbar, label is located below bar. Default is yloc.price.
- `color` (*series color*) — Color of the label border and arrow
- `style` (*series string*) — Label style. Possible values: label.style_none, label.style_xcross, label.style_cross, label.style_triangleup, label.style_triangledown, label.style_flag, label.style_circle, label.style_arrowup, label.style_arrowdown, label.style_label_up, label.style_label_down, label.style_label_left, label.style_label_right, label.style_label_lower_left, label.style_label_lower_right, label.style_label_upper_left, label.style_label_upper_right, label.style_label_center, label.style_square, label.style_diamond, label.style_text_outline. Default is label.style_label_down.
- `textcolor` (*series color*) — Text color.
- `size` (*series int/string*) — Optional. Size of the label. Accepts a positive int value or one of the built-in size.* constants. The constants and their equivalent numeric sizes are: size.auto (0), size.tiny (~7), size.small (~10), size.normal (12), size.large (18), size.huge (24). The default value is size.normal, which represents the numeric size of 12.
- `textalign` (*series string*) — Label text alignment. Possible values: text.align_left, text.align_center, text.align_right. Default value is text.align_center.
- `tooltip` (*series string*) — Hover to see tooltip label.
- `text_font_family` (*series string*) — The font family of the text. Optional. The default value is font.family_default. Possible values: font.family_default, font.family_monospace.
- `force_overlay` (*const bool*) — If true, the drawing will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.
- `text_formatting` (*series text_format*) — The formatting of the displayed text. Formatting options support addition. For example, text.format_bold + text.format_italic will make the text both bold and italicized. Possible values: text.format_none, text.format_bold, text.format_italic. Optional. The default is text.format_none.

### Example
```pine
//@version=6
indicator("label.new")
var label1 = label.new(bar_index, low, text="Hello, world!", style=label.style_circle)
label.set_x(label1, 0)
label.set_xloc(label1, time, xloc.bar_time)
label.set_color(label1, color.red)
label.set_size(label1, size.large)
```

### Returns
Label ID object which may be passed to label.setXXX and label.getXXX functions.

### See also
`label.delete()`, `label.set_x()`, `label.set_y()`, `label.set_xy()`, `label.set_xloc()`, `label.set_yloc()`, `label.set_color()`, `label.set_textcolor()`, `label.set_style()`, `label.set_size()`, `label.set_textalign()`, `label.set_tooltip()`, `label.set_text()`, `label.set_text_formatting()`

## label.set_color()
Sets label border and arrow color.

### Syntax
```pine
label.set_color(id, color) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `color` (*series color*) — New label border and arrow color.

### See also
`label.new()`

## label.set_point()
Sets the location of the id label to point.

### Syntax
```pine
label.set_point(id, point) → void
```

### Arguments
- `id` (*series label*) — A label object.
- `point` (*chart.point*) — A chart.point object.

## label.set_size()
Sets arrow and text size of the specified label object.

### Syntax
```pine
label.set_size(id, size) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `size` (*series int/string*) — Size of the label. Accepts a positive int value or one of the built-in size.* constants. The constants and their equivalent numeric sizes are: size.auto (0), size.tiny (~7), size.small (~10), size.normal (12), size.large (18), size.huge (24). The default value is size.normal, which represents the numeric size of 12.

### See also
`size.auto`, `size.tiny`, `size.small`, `size.normal`, `size.large`, `size.huge`, `label.new()`

## label.set_style()
Sets label style.

### Syntax
```pine
label.set_style(id, style) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `style` (*series string*) — New label style. Possible values: label.style_none, label.style_xcross, label.style_cross, label.style_triangleup, label.style_triangledown, label.style_flag, label.style_circle, label.style_arrowup, label.style_arrowdown, label.style_label_up, label.style_label_down, label.style_label_left, label.style_label_right, label.style_label_lower_left, label.style_label_lower_right, label.style_label_upper_left, label.style_label_upper_right, label.style_label_center, label.style_square, label.style_diamond, label.style_text_outline.

### See also
`label.new()`

## label.set_text()
Sets label text

### Syntax
```pine
label.set_text(id, text) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `text` (*series string*) — New label text.

### See also
`label.new()`, `label.set_text_formatting()`

## label.set_text_font_family()
The function sets the font family of the text inside the label.

### Syntax
```pine
label.set_text_font_family(id, text_font_family) → void
```

### Arguments
- `id` (*series label*) — A label object.
- `text_font_family` (*series string*) — The font family of the text. Possible values: font.family_default, font.family_monospace.

### Example
```pine
//@version=6
indicator("Example of setting the label font")
if barstate.islastconfirmedhistory
    l = label.new(bar_index, 0, "monospace", yloc=yloc.abovebar)
    label.set_text_font_family(l, font.family_monospace)
```

### See also
`label.new()`, `font.family_default`, `font.family_monospace`

## label.set_text_formatting()
Sets the formatting attributes the drawing applies to displayed text.

### Syntax
```pine
label.set_text_formatting(id, text_formatting) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `text_formatting` (*series text_format*) — The formatting of the displayed text. Formatting options support addition. For example, text.format_bold + text.format_italic will make the text both bold and italicized. Possible values: text.format_none, text.format_bold, text.format_italic. Optional. The default is text.format_none.

### See also
`label.new()`, `label.set_text()`

## label.set_textalign()
Sets the alignment for the label text.

### Syntax
```pine
label.set_textalign(id, textalign) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `textalign` (*series string*) — Label text alignment. Possible values: text.align_left, text.align_center, text.align_right.

### See also
`text.align_left`, `text.align_center`, `text.align_right`, `label.new()`

## label.set_textcolor()
Sets color of the label text.

### Syntax
```pine
label.set_textcolor(id, textcolor) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `textcolor` (*series color*) — New text color.

### See also
`label.new()`

## label.set_tooltip()
Sets the tooltip text.

### Syntax
```pine
label.set_tooltip(id, tooltip) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `tooltip` (*series string*) — Tooltip text.

### See also
`label.new()`

## label.set_x()
Sets bar index or bar time (depending on the xloc) of the label position.

### Syntax
```pine
label.set_x(id, x) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `x` (*series int*) — New bar index or bar time of the label position. Note that objects positioned using xloc.bar_index cannot be drawn further than 500 bars into the future.

### See also
`label.new()`

## label.set_xloc()
Sets x-location and new bar index/time value.

### Syntax
```pine
label.set_xloc(id, x, xloc) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `x` (*series int*) — New bar index or bar time of the label position.
- `xloc` (*series string*) — New x-location value.

### See also
`xloc.bar_index`, `xloc.bar_time`, `label.new()`

## label.set_xy()
Sets bar index/time and price of the label position.

### Syntax
```pine
label.set_xy(id, x, y) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `x` (*series int*) — New bar index or bar time of the label position. Note that objects positioned using xloc.bar_index cannot be drawn further than 500 bars into the future.
- `y` (*series int/float*) — New price of the label position.

### See also
`label.new()`

## label.set_y()
Sets price of the label position

### Syntax
```pine
label.set_y(id, y) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `y` (*series int/float*) — New price of the label position.

### See also
`label.new()`

## label.set_yloc()
Sets new y-location calculation algorithm.

### Syntax
```pine
label.set_yloc(id, yloc) → void
```

### Arguments
- `id` (*series label*) — Label object.
- `yloc` (*series string*) — New y-location value.

### See also
`yloc.price`, `yloc.abovebar`, `yloc.belowbar`, `label.new()`

## line()
Casts na to line

### Syntax
```pine
line(x) → series line
```

### Arguments
- `x` (*series line*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to line.

### See also
`float()`, `int()`, `bool()`, `color()`, `string()`, `label()`

## line.copy()
Clones the line object.

### Syntax
```pine
line.copy(id) → series line
```

### Arguments
- `id` (*series line*) — Line object.

### Example
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

### Returns
New line ID object which may be passed to line.setXXX and line.getXXX functions.

### See also
`line.new()`, `line.delete()`

## line.delete()
Deletes the specified line object. If it has already been deleted, does nothing.

### Syntax
```pine
line.delete(id) → void
```

### Arguments
- `id` (*series line*) — Line object to delete.

### See also
`line.new()`

## line.get_price()
Returns the price level of a line at a given bar index.

### Syntax
```pine
line.get_price(id, x) → series float
```

### Arguments
- `id` (*series line*) — Line object.
- `x` (*series int*) — Bar index for which price is required.

### Example
```pine
//@version=6
indicator("GetPrice", overlay=true)
var line l = na
if bar_index == 10
    l := line.new(0, high[5], bar_index, high)
plot(line.get_price(l, bar_index), color=color.green)
```

### Returns
Price value of line 'id' at bar index 'x'.

### Remarks
The line is considered to have been created using 'extend=extend.both'.
This function can only be called for lines created using 'xloc.bar_index'. If you try to call it for a line created with 'xloc.bar_time', it will generate an error.

### See also
`line.new()`

## line.get_x1()
Returns UNIX time or bar index (depending on the last xloc value set) of the first point of the line.

### Syntax
```pine
line.get_x1(id) → series int
```

### Arguments
- `id` (*series line*) — Line object.

### Example
```pine
//@version=6
indicator("line.get_x1")
my_line = line.new(time, open, time + 60 * 60 * 24, close, xloc=xloc.bar_time)
a = line.get_x1(my_line)
plot(time - line.get_x1(my_line)) //draws zero plot
```

### Returns
UNIX timestamp (in milliseconds) or bar index.

### See also
`line.new()`

## line.get_x2()
Returns UNIX time or bar index (depending on the last xloc value set) of the second point of the line.

### Syntax
```pine
line.get_x2(id) → series int
```

### Arguments
- `id` (*series line*) — Line object.

### Returns
UNIX timestamp (in milliseconds) or bar index.

### See also
`line.new()`

## line.get_y1()
Returns price of the first point of the line.

### Syntax
```pine
line.get_y1(id) → series float
```

### Arguments
- `id` (*series line*) — Line object.

### Returns
Price value.

### See also
`line.new()`

## line.get_y2()
Returns price of the second point of the line.

### Syntax
```pine
line.get_y2(id) → series float
```

### Arguments
- `id` (*series line*) — Line object.

### Returns
Price value.

### See also
`line.new()`

## line.new()
Creates new line object.

### Syntax & Overloads
```pine
line.new(first_point, second_point, xloc, extend, color, style, width, force_overlay) → series line
```
```pine
line.new(x1, y1, x2, y2, xloc, extend, color, style, width, force_overlay) → series line
```

### Arguments
- `first_point` (*chart.point*) — A chart.point object that specifies the line's starting coordinate.
- `second_point` (*chart.point*) — A chart.point object that specifies the line's ending coordinate.
- `xloc` (*series string*) — See description of x1 argument. Possible values: xloc.bar_index and xloc.bar_time. Default is xloc.bar_index.
- `extend` (*series string*) — If extend=extend.none, draws segment starting at point (x1, y1) and ending at point (x2, y2). If extend is equal to extend.right or extend.left, draws a ray starting at point (x1, y1) or (x2, y2), respectively. If extend=extend.both, draws a straight line that goes through these points. Default value is extend.none.
- `color` (*series color*) — Line color.
- `style` (*series string*) — Line style. Possible values: line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both.
- `width` (*series int*) — Line width in pixels.
- `force_overlay` (*const bool*) — If true, the drawing will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
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

### Returns
Line ID object which may be passed to line.setXXX and line.getXXX functions.

### See also
`line.delete()`, `line.set_x1()`, `line.set_y1()`, `line.set_xy1()`, `line.set_x2()`, `line.set_y2()`, `line.set_xy2()`, `line.set_xloc()`, `line.set_color()`, `line.set_extend()`, `line.set_style()`, `line.set_width()`

## line.set_color()
Sets the line color

### Syntax
```pine
line.set_color(id, color) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `color` (*series color*) — New line color

### See also
`line.new()`

## line.set_extend()
Sets extending type of this line object. If extend=extend.none, draws segment starting at point (x1, y1) and ending at point (x2, y2). If extend is equal to extend.right or extend.left, draws a ray starting at point (x1, y1) or (x2, y2), respectively. If extend=extend.both, draws a straight line that goes through these points.

### Syntax
```pine
line.set_extend(id, extend) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `extend` (*series string*) — New extending type.

### See also
`extend.none`, `extend.right`, `extend.left`, `extend.both`, `line.new()`

## line.set_first_point()
Sets the first point of the id line to point.

### Syntax
```pine
line.set_first_point(id, point) → void
```

### Arguments
- `id` (*series line*) — A line object.
- `point` (*chart.point*) — A chart.point object.

## line.set_second_point()
Sets the second point of the id line to point.

### Syntax
```pine
line.set_second_point(id, point) → void
```

### Arguments
- `id` (*series line*) — A line object.
- `point` (*chart.point*) — A chart.point object.

## line.set_style()
Sets the line style

### Syntax
```pine
line.set_style(id, style) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `style` (*series string*) — New line style.

### See also
`line.style_solid`, `line.style_dotted`, `line.style_dashed`, `line.style_arrow_left`, `line.style_arrow_right`, `line.style_arrow_both`, `line.new()`

## line.set_width()
Sets the line width.

### Syntax
```pine
line.set_width(id, width) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `width` (*series int*) — New line width in pixels.

### See also
`line.new()`

## line.set_x1()
Sets bar index or bar time (depending on the xloc) of the first point.

### Syntax
```pine
line.set_x1(id, x) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `x` (*series int*) — Bar index or bar time. Note that objects positioned using xloc.bar_index cannot be drawn further than 500 bars into the future.

### See also
`line.new()`

## line.set_x2()
Sets bar index or bar time (depending on the xloc) of the second point.

### Syntax
```pine
line.set_x2(id, x) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `x` (*series int*) — Bar index or bar time. Note that objects positioned using xloc.bar_index cannot be drawn further than 500 bars into the future.

### See also
`line.new()`

## line.set_xloc()
Sets x-location and new bar index/time values.

### Syntax
```pine
line.set_xloc(id, x1, x2, xloc) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `x1` (*series int*) — Bar index or bar time of the first point.
- `x2` (*series int*) — Bar index or bar time of the second point.
- `xloc` (*series string*) — New x-location value.

### See also
`xloc.bar_index`, `xloc.bar_time`, `line.new()`

## line.set_xy1()
Sets bar index/time and price of the first point.

### Syntax
```pine
line.set_xy1(id, x, y) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `x` (*series int*) — Bar index or bar time. Note that objects positioned using xloc.bar_index cannot be drawn further than 500 bars into the future.
- `y` (*series int/float*) — Price.

### See also
`line.new()`

## line.set_xy2()
Sets bar index/time and price of the second point

### Syntax
```pine
line.set_xy2(id, x, y) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `x` (*series int*) — Bar index or bar time.
- `y` (*series int/float*) — Price.

### See also
`line.new()`

## line.set_y1()
Sets price of the first point

### Syntax
```pine
line.set_y1(id, y) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `y` (*series int/float*) — Price.

### See also
`line.new()`

## line.set_y2()
Sets price of the second point.

### Syntax
```pine
line.set_y2(id, y) → void
```

### Arguments
- `id` (*series line*) — Line object.
- `y` (*series int/float*) — Price.

### See also
`line.new()`

## linefill()
Casts na to linefill.

### Syntax
```pine
linefill(x) → series linefill
```

### Arguments
- `x` (*series linefill*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to linefill.

### See also
`float()`, `int()`, `bool()`, `color()`, `string()`, `line()`, `label()`

## linefill.delete()
Deletes the specified linefill object. If it has already been deleted, does nothing.

### Syntax
```pine
linefill.delete(id) → void
```

### Arguments
- `id` (*series linefill*) — A linefill object.

## linefill.get_line1()
Returns the ID of the first line used in the id linefill.

### Syntax
```pine
linefill.get_line1(id) → series line
```

### Arguments
- `id` (*series linefill*) — A linefill object.

## linefill.get_line2()
Returns the ID of the second line used in the id linefill.

### Syntax
```pine
linefill.get_line2(id) → series line
```

### Arguments
- `id` (*series linefill*) — A linefill object.

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

### Returns
The ID of a linefill object that can be passed to other linefill.*() functions.

### Remarks
If any line of the two is deleted, the linefill object is also deleted. If the lines are moved (e.g. via line.set_xy() functions), the linefill object is also moved.
If both lines are extended in the same direction relative to the lines themselves (e.g. both have extend.right as the value of their extend= parameter), the space between line extensions will also be filled.

## linefill.set_color()
The function sets the color of the linefill object passed to it.

### Syntax
```pine
linefill.set_color(id, color) → void
```

### Arguments
- `id` (*series linefill*) — A linefill object.
- `color` (*series color*) — The color of the linefill object.

## plot()
Plots a series of data on the chart.

### Syntax
```pine
plot(series, title, color, linewidth, style, trackprice, histbase, offset, join, editable, show_last, display, format, precision, force_overlay, linestyle) → plot
```

### Arguments
- `series` (*series int/float*) — Series of data to be plotted. Required argument.
- `title` (*const string*) — Title of the plot.
- `color` (*series color*) — Color of the plot. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `linewidth` (*input int*) — Width of the plotted line. Default value is 1. Not applicable to every style.
- `style` (*input plot_style*) — Type of plot. Possible values are: plot.style_line, plot.style_stepline, plot.style_stepline_diamond, plot.style_histogram, plot.style_cross, plot.style_area, plot.style_columns, plot.style_circles, plot.style_linebr, plot.style_areabr, plot.style_steplinebr. Default value is plot.style_line.
- `trackprice` (*input bool*) — If true then a horizontal price line will be shown at the level of the last indicator value. Default is false.
- `histbase` (*input int/float*) — The price value used as the reference level when rendering plot with plot.style_histogram, plot.style_columns or plot.style_area style. Default is 0.0.
- `offset` (*simple int*) — Shifts the plot to the left or to the right on the given number of bars. Default is 0.
- `join` (*input bool*) — If true then plot points will be joined with line, applicable only to plot.style_cross and plot.style_circles styles. Default is false.
- `editable` (*input bool*) — If true then plot style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — Optional. The number of bars, counting backwards from the most recent bar, on which the function can draw.
- `display` (*input plot_display*) — Controls where the plot's information is displayed. Display options support addition and subtraction, meaning that using display.all - display.status_line will display the plot's information everywhere except in the script's status line. display.price_scale + display.status_line will display the plot only in the price scale and status line. When display arguments such as display.price_scale have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: display.none, display.pane, display.data_window, display.price_scale, display.status_line, display.all. Optional. The default is display.all.
- `format` (*input string*) — Determines whether the script formats the plot's values as prices, percentages, or volume values. The argument passed to this parameter supersedes the format parameter of the indicator(), and strategy() functions. Optional. The default is the format value used by the indicator()/strategy() function. Possible values: format.price, format.percent, format.volume.
- `precision` (*input int*) — The number of digits after the decimal point the plot's values show on the chart pane's y-axis, the script's status line, and the Data Window. Accepts a non-negative integer less than or equal to 16. The argument passed to this parameter supersedes the precision parameter of the indicator() and strategy() functions. When the function's format parameter uses format.volume, the precision parameter will not affect the result, as the decimal precision rules defined by format.volume supersede other precision settings. Optional. The default is the precision value used by the indicator()/strategy() function.
- `force_overlay` (*const bool*) — If true, the plotted results will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.
- `linestyle` (*input plot_line_style*) — Optional. A modifier for plot styles that display lines. It specifies whether the plotted line is solid (plot.linestyle_solid), dashed (plot.linestyle_dashed), or dotted (plot.linestyle_dotted). The modifier applies only when the function uses one of the following style arguments: plot.style_line, plot.style_linebr, plot.style_stepline, plot.style_stepline_diamond, and plot.style_area. The default is plot.linestyle_solid.

### Example
```pine
//@version=6
indicator("plot")
plot(high+low, title='Title', color=color.new(#00ffaa, 70), linewidth=2, style=plot.style_area, offset=15, trackprice=true)

// You may fill the background between any two plots with a fill() function:
p1 = plot(open)
p2 = plot(close)
fill(p1, p2, color=color.new(color.green, 90))
```

### Returns
A plot object, that can be used in fill()

### See also
`plotshape()`, `plotchar()`, `plotarrow()`, `barcolor()`, `bgcolor()`, `fill()`

## plotarrow()
Plots up and down arrows on the chart. Up arrow is drawn at every indicator positive value, down arrow is drawn at every negative value. If indicator returns na then no arrow is drawn. Arrows has different height, the more absolute indicator value the longer arrow is drawn.

### Syntax
```pine
plotarrow(series, title, colorup, colordown, offset, minheight, maxheight, editable, show_last, display, format, precision, force_overlay) → void
```

### Arguments
- `series` (*series int/float*) — Series of data to be plotted as arrows. Required argument.
- `title` (*const string*) — Title of the plot.
- `colorup` (*series color*) — Color of the up arrows. Optional argument.
- `colordown` (*series color*) — Color of the down arrows. Optional argument.
- `offset` (*simple int*) — Shifts arrows to the left or to the right on the given number of bars. Default is 0.
- `minheight` (*input int*) — Minimal possible arrow height in pixels. Default is 5.
- `maxheight` (*input int*) — Maximum possible arrow height in pixels. Default is 100.
- `editable` (*input bool*) — If true then plotarrow style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — Optional. The number of bars, counting backwards from the most recent bar, on which the function can draw.
- `display` (*input plot_display*) — Controls where the plot's information is displayed. Display options support addition and subtraction, meaning that using display.all - display.status_line will display the plot's information everywhere except in the script's status line. display.price_scale + display.status_line will display the plot only in the price scale and status line. When display arguments such as display.price_scale have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: display.none, display.pane, display.data_window, display.price_scale, display.status_line, display.all. Optional. The default is display.all.
- `format` (*input string*) — Determines whether the script formats the plot's values as prices, percentages, or volume values. The argument passed to this parameter supersedes the format parameter of the indicator(), and strategy() functions. Optional. The default is the format value used by the indicator()/strategy() function. Possible values: format.price, format.percent, format.volume.
- `precision` (*input int*) — The number of digits after the decimal point the plot's values show on the chart pane's y-axis, the script's status line, and the Data Window. Accepts a non-negative integer less than or equal to 16. The argument passed to this parameter supersedes the precision parameter of the indicator() and strategy() functions. When the function's format parameter uses format.volume, the precision parameter will not affect the result, as the decimal precision rules defined by format.volume supersede other precision settings. Optional. The default is the precision value used by the indicator()/strategy() function.
- `force_overlay` (*const bool*) — If true, the plotted results will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
```pine
//@version=6
indicator("plotarrow example", overlay=true)
codiff = close - open
plotarrow(codiff, colorup=color.new(color.teal,40), colordown=color.new(color.orange, 40))
```

### Remarks
Use plotarrow() function in conjunction with 'overlay=true' indicator() parameter!

### See also
`plot()`, `plotshape()`, `plotchar()`, `barcolor()`, `bgcolor()`

## plotbar()
Plots ohlc bars on the chart.

### Syntax
```pine
plotbar(open, high, low, close, title, color, editable, show_last, display, format, precision, force_overlay) → void
```

### Arguments
- `open` (*series int/float*) — Open series of data to be used as open values of bars. Required argument.
- `high` (*series int/float*) — High series of data to be used as high values of bars. Required argument.
- `low` (*series int/float*) — Low series of data to be used as low values of bars. Required argument.
- `close` (*series int/float*) — Close series of data to be used as close values of bars. Required argument.
- `title` (*const string*) — Title of the plotbar. Optional argument.
- `color` (*series color*) — Color of the ohlc bars. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `editable` (*input bool*) — If true then plotbar style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — Optional. The number of bars, counting backwards from the most recent bar, on which the function can draw.
- `display` (*input plot_display*) — Controls where the plot's information is displayed. Display options support addition and subtraction, meaning that using display.all - display.status_line will display the plot's information everywhere except in the script's status line. display.price_scale + display.status_line will display the plot only in the price scale and status line. When display arguments such as display.price_scale have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: display.none, display.pane, display.data_window, display.price_scale, display.status_line, display.all. Optional. The default is display.all.
- `format` (*input string*) — Determines whether the script formats the plot's values as prices, percentages, or volume values. The argument passed to this parameter supersedes the format parameter of the indicator(), and strategy() functions. Optional. The default is the format value used by the indicator()/strategy() function. Possible values: format.price, format.percent, format.volume.
- `precision` (*input int*) — The number of digits after the decimal point the plot's values show on the chart pane's y-axis, the script's status line, and the Data Window. Accepts a non-negative integer less than or equal to 16. The argument passed to this parameter supersedes the precision parameter of the indicator() and strategy() functions. When the function's format parameter uses format.volume, the precision parameter will not affect the result, as the decimal precision rules defined by format.volume supersede other precision settings. Optional. The default is the precision value used by the indicator()/strategy() function.
- `force_overlay` (*const bool*) — If true, the plotted results will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
```pine
//@version=6
indicator("plotbar example", overlay=true)
plotbar(open, high, low, close, title='Title', color = open < close ? color.green : color.red)
```

### Remarks
Even if one value of open, high, low or close equal NaN then bar no draw.
The maximal value of open, high, low or close will be set as 'high', and the minimal value will be set as 'low'.

### See also
`plotcandle()`

## plotcandle()
Plots candles on the chart.

### Syntax
```pine
plotcandle(open, high, low, close, title, color, wickcolor, editable, show_last, bordercolor, display, format, precision, force_overlay) → void
```

### Arguments
- `open` (*series int/float*) — Open series of data to be used as open values of candles. Required argument.
- `high` (*series int/float*) — High series of data to be used as high values of candles. Required argument.
- `low` (*series int/float*) — Low series of data to be used as low values of candles. Required argument.
- `close` (*series int/float*) — Close series of data to be used as close values of candles. Required argument.
- `title` (*const string*) — Title of the plotcandles. Optional argument.
- `color` (*series color*) — Color of the candles. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `wickcolor` (*series color*) — The color of the wick of candles. An optional argument.
- `editable` (*input bool*) — If true then plotcandle style will be editable in Format dialog. Default is true.
- `show_last` (*input int*) — Optional. The number of bars, counting backwards from the most recent bar, on which the function can draw.
- `bordercolor` (*series color*) — The border color of candles. An optional argument.
- `display` (*input plot_display*) — Controls where the plot's information is displayed. Display options support addition and subtraction, meaning that using display.all - display.status_line will display the plot's information everywhere except in the script's status line. display.price_scale + display.status_line will display the plot only in the price scale and status line. When display arguments such as display.price_scale have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: display.none, display.pane, display.data_window, display.price_scale, display.status_line, display.all. Optional. The default is display.all.
- `format` (*input string*) — Determines whether the script formats the plot's values as prices, percentages, or volume values. The argument passed to this parameter supersedes the format parameter of the indicator(), and strategy() functions. Optional. The default is the format value used by the indicator()/strategy() function. Possible values: format.price, format.percent, format.volume.
- `precision` (*input int*) — The number of digits after the decimal point the plot's values show on the chart pane's y-axis, the script's status line, and the Data Window. Accepts a non-negative integer less than or equal to 16. The argument passed to this parameter supersedes the precision parameter of the indicator() and strategy() functions. When the function's format parameter uses format.volume, the precision parameter will not affect the result, as the decimal precision rules defined by format.volume supersede other precision settings. Optional. The default is the precision value used by the indicator()/strategy() function.
- `force_overlay` (*const bool*) — If true, the plotted results will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
```pine
//@version=6
indicator("plotcandle example", overlay=true)
plotcandle(open, high, low, close, title='Title', color = open < close ? color.green : color.red, wickcolor=color.black)
```

### Remarks
Even if one value of open, high, low or close equal NaN then bar no draw.
The maximal value of open, high, low or close will be set as 'high', and the minimal value will be set as 'low'.

### See also
`plotbar()`

## plotchar()
Plots visual shapes using any given one Unicode character on the chart.

### Syntax
```pine
plotchar(series, title, char, location, color, offset, text, textcolor, editable, size, show_last, display, format, precision, force_overlay) → void
```

### Arguments
- `series` (*series int/float/bool*) — Series of data to be plotted as shapes. Series is treated as a series of boolean values for all location values except location.absolute. Required argument.
- `title` (*const string*) — Title of the plot.
- `char` (*input string*) — Character to use as a visual shape.
- `location` (*input string*) — Location of shapes on the chart. Possible values are: location.abovebar, location.belowbar, location.top, location.bottom, location.absolute. Default value is location.abovebar.
- `color` (*series color*) — Color of the shapes. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `offset` (*simple int*) — Shifts shapes to the left or to the right on the given number of bars. Default is 0.
- `text` (*const string*) — Text to display with the shape. You can use multiline text, to separate lines use '\n' escape sequence. Example: 'line one\nline two'.
- `textcolor` (*series color*) — Color of the text. You can use constants like 'textcolor=color.red' or 'textcolor=#ff001a' as well as complex expressions like 'textcolor = close >= open ? color.green : color.red'. Optional argument.
- `editable` (*input bool*) — If true then plotchar style will be editable in Format dialog. Default is true.
- `size` (*const string*) — Size of characters on the chart. Possible values are: size.auto, size.tiny, size.small, size.normal, size.large, size.huge. Default is size.auto.
- `show_last` (*input int*) — Optional. The number of bars, counting backwards from the most recent bar, on which the function can draw.
- `display` (*input plot_display*) — Controls where the plot's information is displayed. Display options support addition and subtraction, meaning that using display.all - display.status_line will display the plot's information everywhere except in the script's status line. display.price_scale + display.status_line will display the plot only in the price scale and status line. When display arguments such as display.price_scale have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: display.none, display.pane, display.data_window, display.price_scale, display.status_line, display.all. Optional. The default is display.all.
- `format` (*input string*) — Determines whether the script formats the plot's values as prices, percentages, or volume values. The argument passed to this parameter supersedes the format parameter of the indicator(), and strategy() functions. Optional. The default is the format value used by the indicator()/strategy() function. Possible values: format.price, format.percent, format.volume.
- `precision` (*input int*) — The number of digits after the decimal point the plot's values show on the chart pane's y-axis, the script's status line, and the Data Window. Accepts a non-negative integer less than or equal to 16. The argument passed to this parameter supersedes the precision parameter of the indicator() and strategy() functions. When the function's format parameter uses format.volume, the precision parameter will not affect the result, as the decimal precision rules defined by format.volume supersede other precision settings. Optional. The default is the precision value used by the indicator()/strategy() function.
- `force_overlay` (*const bool*) — If true, the plotted results will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
```pine
//@version=6
indicator("plotchar example", overlay=true)
data = close >= open
plotchar(data, char='❄')
```

### Remarks
Use plotchar() function in conjunction with 'overlay=true' indicator() parameter!

### See also
`plot()`, `plotshape()`, `plotarrow()`, `barcolor()`, `bgcolor()`

## plotshape()
Plots visual shapes on the chart.

### Syntax
```pine
plotshape(series, title, style, location, color, offset, text, textcolor, editable, size, show_last, display, format, precision, force_overlay) → void
```

### Arguments
- `series` (*series int/float/bool*) — Series of data to be plotted as shapes. Series is treated as a series of boolean values for all location values except location.absolute. Required argument.
- `title` (*const string*) — Title of the plot.
- `style` (*input string*) — Type of plot. Possible values are: shape.xcross, shape.cross, shape.triangleup, shape.triangledown, shape.flag, shape.circle, shape.arrowup, shape.arrowdown, shape.labelup, shape.labeldown, shape.square, shape.diamond. Default value is shape.xcross.
- `location` (*input string*) — Location of shapes on the chart. Possible values are: location.abovebar, location.belowbar, location.top, location.bottom, location.absolute. Default value is location.abovebar.
- `color` (*series color*) — Color of the shapes. You can use constants like 'color=color.red' or 'color=#ff001a' as well as complex expressions like 'color = close >= open ? color.green : color.red'. Optional argument.
- `offset` (*simple int*) — Shifts shapes to the left or to the right on the given number of bars. Default is 0.
- `text` (*const string*) — Text to display with the shape. You can use multiline text, to separate lines use '\n' escape sequence. Example: 'line one\nline two'.
- `textcolor` (*series color*) — Color of the text. You can use constants like 'textcolor=color.red' or 'textcolor=#ff001a' as well as complex expressions like 'textcolor = close >= open ? color.green : color.red'. Optional argument.
- `editable` (*input bool*) — If true then plotshape style will be editable in Format dialog. Default is true.
- `size` (*const string*) — Size of shapes on the chart. Possible values are: size.auto, size.tiny, size.small, size.normal, size.large, size.huge. Default is size.auto.
- `show_last` (*input int*) — Optional. The number of bars, counting backwards from the most recent bar, on which the function can draw.
- `display` (*input plot_display*) — Controls where the plot's information is displayed. Display options support addition and subtraction, meaning that using display.all - display.status_line will display the plot's information everywhere except in the script's status line. display.price_scale + display.status_line will display the plot only in the price scale and status line. When display arguments such as display.price_scale have user-controlled chart settings equivalents, the relevant plot information will only appear when all settings allow for it. Possible values: display.none, display.pane, display.data_window, display.price_scale, display.status_line, display.all. Optional. The default is display.all.
- `format` (*input string*) — Determines whether the script formats the plot's values as prices, percentages, or volume values. The argument passed to this parameter supersedes the format parameter of the indicator(), and strategy() functions. Optional. The default is the format value used by the indicator()/strategy() function. Possible values: format.price, format.percent, format.volume.
- `precision` (*input int*) — The number of digits after the decimal point the plot's values show on the chart pane's y-axis, the script's status line, and the Data Window. Accepts a non-negative integer less than or equal to 16. The argument passed to this parameter supersedes the precision parameter of the indicator() and strategy() functions. When the function's format parameter uses format.volume, the precision parameter will not affect the result, as the decimal precision rules defined by format.volume supersede other precision settings. Optional. The default is the precision value used by the indicator()/strategy() function.
- `force_overlay` (*const bool*) — If true, the plotted results will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
```pine
//@version=6
indicator("plotshape example 1", overlay=true)
data = close >= open
plotshape(data, style=shape.xcross)
```

### Remarks
Use plotshape() function in conjunction with 'overlay=true' indicator() parameter!

### See also
`plot()`, `plotchar()`, `plotarrow()`, `barcolor()`, `bgcolor()`

## polyline.delete()
Deletes the specified polyline object. It has no effect if the id doesn't exist.

### Syntax
```pine
polyline.delete(id) → void
```

### Arguments
- `id` (*series polyline*) — The polyline ID to delete.

## polyline.new()
Creates a new polyline instance and displays it on the chart, sequentially connecting all of the points in the points array with line segments. The segments in the drawing can be straight or curved depending on the curved parameter.

### Syntax
```pine
polyline.new(points, curved, closed, xloc, line_color, fill_color, line_style, line_width, force_overlay) → series polyline
```

### Arguments
- `points` (*array<chart.point>*) — An array of chart.point objects for the drawing to sequentially connect.
- `curved` (*series bool*) — If true, the drawing will connect all points from the points array using curved line segments. Optional. The default is false.
- `closed` (*series bool*) — If true, the drawing will also connect the first point to the last point from the points array, resulting in a closed polyline. Optional. The default is false.
- `xloc` (*series string*) — Determines the field of the chart.point objects in the points array that the polyline will use for its x-coordinates. If xloc.bar_index, the polyline will use the index field from each point. If xloc.bar_time, it will use the time field. Optional. The default is xloc.bar_index.
- `line_color` (*series color*) — The color of the line segments. Optional. The default is color.blue.
- `fill_color` (*series color*) — The fill color of the polyline. Optional. The default is na.
- `line_style` (*series string*) — The style of the polyline. Possible values: line.style_solid, line.style_dotted, line.style_dashed, line.style_arrow_left, line.style_arrow_right, line.style_arrow_both. Optional. The default is line.style_solid.
- `line_width` (*series int*) — The width of the line segments, expressed in pixels. Optional. The default is 1.
- `force_overlay` (*const bool*) — If true, the drawing will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
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

### Returns
The ID of a new polyline object that a script can use in other polyline.*() functions.

### See also
`chart.point.new()`

## table()
Casts na to table

### Syntax
```pine
table(x) → series table
```

### Arguments
- `x` (*series table*) — The value to convert to the specified type, usually na.

### Returns
The value of the argument after casting to table.

### See also
`float()`, `int()`, `bool()`, `color()`, `string()`, `line()`, `label()`

## table.cell()
The function defines a cell in the table and sets its attributes.

### Syntax
```pine
table.cell(table_id, column, row, text, width, height, text_color, text_halign, text_valign, text_size, bgcolor, tooltip, text_font_family, text_formatting) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `text` (*series string*) — The text to be displayed inside the cell. Optional. The default is empty string.
- `width` (*series int/float*) — The width of the cell as a % of the indicator's visual space. Optional. By default, auto-adjusts the width based on the text inside the cell. Value 0 has the same effect.
- `height` (*series int/float*) — The height of the cell as a % of the indicator's visual space. Optional. By default, auto-adjusts the height based on the text inside of the cell. Value 0 has the same effect.
- `text_color` (*series color*) — The color of the text. Optional. The default is color.black.
- `text_halign` (*series string*) — The horizontal alignment of the cell's text. Optional. The default value is text.align_center. Possible values: text.align_left, text.align_center, text.align_right.
- `text_valign` (*series string*) — The vertical alignment of the cell's text. Optional. The default value is text.align_center. Possible values: text.align_top, text.align_center, text.align_bottom.
- `text_size` (*series int/string*) — Size of the object. The size can be any positive integer, or one of the size.* built-in constant strings. The constant strings and their equivalent integer values are: size.auto (0), size.tiny (8), size.small (10), size.normal (14), size.large (20), size.huge (36). The default value is size.normal or 14.
- `bgcolor` (*series color*) — The background color of the text. Optional. The default is no color.
- `tooltip` (*series string*) — The tooltip to be displayed inside the cell. Optional.
- `text_font_family` (*series string*) — The font family of the text. Optional. The default value is font.family_default. Possible values: font.family_default, font.family_monospace.
- `text_formatting` (*series text_format*) — The formatting of the displayed text. Formatting options support addition. For example, text.format_bold + text.format_italic will make the text both bold and italicized. Possible values: text.format_none, text.format_bold, text.format_italic. Optional. The default is text.format_none.

### Remarks
This function does not create the table itself, but defines the table’s cells. To use it, you first need to create a table object with table.new().
Each table.cell() call overwrites all previously defined properties of a cell. If you call table.cell() twice in a row, e.g., the first time with text='Test Text', and the second time with text_color=color.red but without a new text argument, the default value of the 'text' being an empty string, it will overwrite 'Test Text', and your cell will display an empty string. If you want, instead, to modify any of the cell's properties, use the table.cell_set_*() functions.
A single script can only display one table in each of the possible locations. If table.cell() is used on several bars to change the same attribute of a cell (e.g. change the background color of the cell to red on the first bar, then to yellow on the second bar), only the last change will be reflected in the table, i.e., the cell’s background will be yellow. Avoid unnecessary setting of cell properties by enclosing function calls in an if barstate.islast block whenever possible, to restrict their execution to the last bar of the series.

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text()`, `table.cell_set_text_formatting()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_tooltip()`

## table.cell_set_bgcolor()
The function sets the background color of the cell.

### Syntax
```pine
table.cell_set_bgcolor(table_id, column, row, bgcolor) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `bgcolor` (*series color*) — The background color of the cell.

### See also
`table.cell_set_height()`, `table.cell_set_text()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_tooltip()`

## table.cell_set_height()
The function sets the height of cell.

### Syntax
```pine
table.cell_set_height(table_id, column, row, height) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `height` (*series int/float*) — The height of the cell as a % of the chart window. Passing 0 auto-adjusts the height based on the text inside of the cell.

### See also
`table.cell_set_bgcolor()`, `table.cell_set_text()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_tooltip()`

## table.cell_set_text()
The function sets the text in the specified cell.

### Syntax
```pine
table.cell_set_text(table_id, column, row, text) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `text` (*series string*) — The text to be displayed inside the cell.

### Example
```pine
//@version=6
indicator("TABLE example")
var tLog = table.new(position = position.top_left, rows = 1, columns = 2, bgcolor = color.yellow, border_width=1)
table.cell(tLog, row = 0, column = 0, text = "sometext", text_color = color.blue)
table.cell_set_text(tLog, row = 0, column = 0, text = "sometext")
```

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_tooltip()`, `table.cell_set_text_formatting()`

## table.cell_set_text_color()
The function sets the color of the text inside the cell.

### Syntax
```pine
table.cell_set_text_color(table_id, column, row, text_color) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `text_color` (*series color*) — The color of the text.

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_tooltip()`

## table.cell_set_text_font_family()
The function sets the font family of the text inside the cell.

### Syntax
```pine
table.cell_set_text_font_family(table_id, column, row, text_font_family) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `text_font_family` (*series string*) — The font family of the text. Possible values: font.family_default, font.family_monospace.

### Example
```pine
//@version=6
indicator("Example of setting the table cell font")
var t = table.new(position.top_left, rows = 1, columns = 1)
table.cell(t, 0, 0, "monospace", text_color = color.blue)
table.cell_set_text_font_family(t, 0, 0, font.family_monospace)
```

### See also
`table.new()`, `font.family_default`, `font.family_monospace`

## table.cell_set_text_formatting()
Sets the formatting attributes the drawing applies to displayed text.

### Syntax
```pine
table.cell_set_text_formatting(table_id, column, row, text_formatting) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `text_formatting` (*series text_format*) — The formatting of the displayed text. Formatting options support addition. For example, text.format_bold + text.format_italic will make the text both bold and italicized. Possible values: text.format_none, text.format_bold, text.format_italic. Optional. The default is text.format_none.

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_tooltip()`, `table.cell_set_text()`

## table.cell_set_text_halign()
The function sets the horizontal alignment of the cell's text.

### Syntax
```pine
table.cell_set_text_halign(table_id, column, row, text_halign) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `text_halign` (*series string*) — The horizontal alignment of a cell's text. Possible values: text.align_left, text.align_center, text.align_right.

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text()`, `table.cell_set_text_color()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_tooltip()`

## table.cell_set_text_size()
The function sets the size of the cell's text.

### Syntax
```pine
table.cell_set_text_size(table_id, column, row, text_size) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `text_size` (*series int/string*) — Size of the object. The size can be any positive integer, or one of the size.* built-in constant strings. The constant strings and their equivalent integer values are: size.auto (0), size.tiny (8), size.small (10), size.normal (14), size.large (20), size.huge (36). The default value is size.normal or 14.

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_tooltip()`

## table.cell_set_text_valign()
The function sets the vertical alignment of a cell's text.

### Syntax
```pine
table.cell_set_text_valign(table_id, column, row, text_valign) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `text_valign` (*series string*) — The vertical alignment of the cell's text. Possible values: text.align_top, text.align_center, text.align_bottom.

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_width()`, `table.cell_set_tooltip()`

## table.cell_set_tooltip()
The function sets the tooltip in the specified cell.

### Syntax
```pine
table.cell_set_tooltip(table_id, column, row, tooltip) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `tooltip` (*series string*) — The tooltip to be displayed inside the cell.

### Example
```pine
//@version=6
indicator("TABLE example")
var tLog = table.new(position = position.top_left, rows = 1, columns = 2, bgcolor = color.yellow, border_width=1)
table.cell(tLog, row = 0, column = 0, text = "sometext", text_color = color.blue)
table.cell_set_tooltip(tLog, row = 0, column = 0, tooltip = "sometext")
```

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_width()`, `table.cell_set_text()`

## table.cell_set_width()
The function sets the width of the cell.

### Syntax
```pine
table.cell_set_width(table_id, column, row, width) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `column` (*series int*) — The index of the cell's column. Numbering starts at 0.
- `row` (*series int*) — The index of the cell's row. Numbering starts at 0.
- `width` (*series int/float*) — The width of the cell as a % of the chart window. Passing 0 auto-adjusts the width based on the text inside of the cell.

### See also
`table.cell_set_bgcolor()`, `table.cell_set_height()`, `table.cell_set_text()`, `table.cell_set_text_color()`, `table.cell_set_text_halign()`, `table.cell_set_text_size()`, `table.cell_set_text_valign()`, `table.cell_set_tooltip()`

## table.clear()
The function removes a cell or a sequence of cells from the table. The cells are removed in a rectangle shape where the start_column and start_row specify the top-left corner, and end_column and end_row specify the bottom-right corner.

### Syntax
```pine
table.clear(table_id, start_column, start_row, end_column, end_row) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `start_column` (*series int*) — The index of the column of the first cell to delete. Numbering starts at 0.
- `start_row` (*series int*) — The index of the row of the first cell to delete. Numbering starts at 0.
- `end_column` (*series int*) — The index of the column of the last cell to delete. Optional. The default is the argument used for start_column. Numbering starts at 0.
- `end_row` (*series int*) — The index of the row of the last cell to delete. Optional. The default is the argument used for start_row. Numbering starts at 0.

### Example
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

### See also
`table.delete()`, `table.new()`

## table.delete()
The function deletes a table.

### Syntax
```pine
table.delete(table_id) → void
```

### Arguments
- `table_id` (*series table*) — A table object.

### Example
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

### See also
`table.new()`, `table.clear()`

## table.merge_cells()
The function merges a sequence of cells in the table into one cell. The cells are merged in a rectangle shape where the start_column and start_row specify the top-left corner, and end_column and end_row specify the bottom-right corner.

### Syntax
```pine
table.merge_cells(table_id, start_column, start_row, end_column, end_row) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `start_column` (*series int*) — The index of the column of the first cell to merge. Numbering starts at 0.
- `start_row` (*series int*) — The index of the row of the first cell to merge. Numbering starts at 0.
- `end_column` (*series int*) — The index of the column of the last cell to merge. Numbering starts at 0.
- `end_row` (*series int*) — The index of the row of the last cell to merge. Numbering starts at 0.

### Example
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

### Remarks
This function will merge cells, even if their properties are not yet defined with table.cell().
The resulting merged cell inherits all of its values from the cell located at start_column:start_row, except width and height. The width and height of the resulting merged cell are based on the width/height of other cells in the neighboring columns/rows and cannot be set manually.
To modify the merged cell with any of the table.cell_set_* functions, target the cell at the start_column:start_row coordinates.
An attempt to merge a cell that has already been merged will result in an error.

### See also
`table.delete()`, `table.new()`

## table.new()
The function creates a new table.

### Syntax
```pine
table.new(position, columns, rows, bgcolor, frame_color, frame_width, border_color, border_width, force_overlay) → series table
```

### Arguments
- `position` (*series string*) — Position of the table. Possible values are: position.top_left, position.top_center, position.top_right, position.middle_left, position.middle_center, position.middle_right, position.bottom_left, position.bottom_center, position.bottom_right.
- `columns` (*series int*) — The number of columns in the table.
- `rows` (*series int*) — The number of rows in the table.
- `bgcolor` (*series color*) — The background color of the table. Optional. The default is no color.
- `frame_color` (*series color*) — The color of the outer frame of the table. Optional. The default is no color.
- `frame_width` (*series int*) — The width of the outer frame of the table. Optional. The default is 0.
- `border_color` (*series color*) — The color of the borders of the cells (excluding the outer frame). Optional. The default is no color.
- `border_width` (*series int*) — The width of the borders of the cells (excluding the outer frame). Optional. The default is 0.
- `force_overlay` (*const bool*) — If true, the drawing will display on the main chart pane, even when the script occupies a separate pane. Optional. The default is false.

### Example
```pine
//@version=6
indicator("table.new example")
var testTable = table.new(position = position.top_right, columns = 2, rows = 1, bgcolor = color.yellow, border_width = 1)
if barstate.islast
    table.cell(table_id = testTable, column = 0, row = 0, text = "Open is " + str.tostring(open))
    table.cell(table_id = testTable, column = 1, row = 0, text = "Close is " + str.tostring(close), bgcolor=color.teal)
```

### Returns
The ID of a table object that can be passed to other table.*() functions.

### Remarks
This function creates the table object itself, but the table will not be displayed until its cells are populated. To define a cell and change its contents or attributes, use table.cell() and other table.cell_*() functions.
One table.new() call can only display one table (the last one drawn), but the function itself will be recalculated on each bar it is used on. For performance reasons, it is wise to use table.new() in conjunction with either the var keyword (so the table object is only created on the first bar) or in an if barstate.islast block (so the table object is only created on the last bar).

### See also
`table.cell()`, `table.clear()`, `table.delete()`, `table.set_bgcolor()`, `table.set_border_color()`, `table.set_border_width()`, `table.set_frame_color()`, `table.set_frame_width()`, `table.set_position()`

## table.set_bgcolor()
The function sets the background color of a table.

### Syntax
```pine
table.set_bgcolor(table_id, bgcolor) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `bgcolor` (*series color*) — The background color of the table. Optional. The default is no color.

### See also
`table.clear()`, `table.delete()`, `table.new()`, `table.set_border_color()`, `table.set_border_width()`, `table.set_frame_color()`, `table.set_frame_width()`, `table.set_position()`

## table.set_border_color()
The function sets the color of the borders (excluding the outer frame) of the table's cells.

### Syntax
```pine
table.set_border_color(table_id, border_color) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `border_color` (*series color*) — The color of the borders. Optional. The default is no color.

### See also
`table.clear()`, `table.delete()`, `table.new()`, `table.set_frame_color()`, `table.set_border_width()`, `table.set_bgcolor()`, `table.set_frame_width()`, `table.set_position()`

## table.set_border_width()
The function sets the width of the borders (excluding the outer frame) of the table's cells.

### Syntax
```pine
table.set_border_width(table_id, border_width) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `border_width` (*series int*) — The width of the borders. Optional. The default is 0.

### See also
`table.clear()`, `table.delete()`, `table.new()`, `table.set_frame_color()`, `table.set_frame_width()`, `table.set_bgcolor()`, `table.set_border_color()`, `table.set_position()`

## table.set_frame_color()
The function sets the color of the outer frame of a table.

### Syntax
```pine
table.set_frame_color(table_id, frame_color) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `frame_color` (*series color*) — The color of the frame of the table. Optional. The default is no color.

### See also
`table.clear()`, `table.delete()`, `table.new()`, `table.set_border_color()`, `table.set_border_width()`, `table.set_bgcolor()`, `table.set_frame_width()`, `table.set_position()`

## table.set_frame_width()
The function set the width of the outer frame of a table.

### Syntax
```pine
table.set_frame_width(table_id, frame_width) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `frame_width` (*series int*) — The width of the outer frame of the table. Optional. The default is 0.

### See also
`table.clear()`, `table.delete()`, `table.new()`, `table.set_frame_color()`, `table.set_border_width()`, `table.set_bgcolor()`, `table.set_border_color()`, `table.set_position()`

## table.set_position()
The function sets the position of a table.

### Syntax
```pine
table.set_position(table_id, position) → void
```

### Arguments
- `table_id` (*series table*) — A table object.
- `position` (*series string*) — Position of the table. Possible values are: position.top_left, position.top_center, position.top_right, position.middle_left, position.middle_center, position.middle_right, position.bottom_left, position.bottom_center, position.bottom_right.

### See also
`table.clear()`, `table.delete()`, `table.new()`, `table.set_bgcolor()`, `table.set_border_color()`, `table.set_border_width()`, `table.set_frame_color()`, `table.set_frame_width()`
