<!--
Source: https://www.tradingview.com/pine-script-reference/v6/
Pine Script v6 — official TradingView language reference manual
Retrieved: 2026-08-20
-->

# Data request functions

Pulling data from other symbols, timeframes, financials, and non-standard tickers, plus the volume-footprint accessors.

**39 functions** · Source: [Pine Script® v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/)

## Index

- [`footprint.buy_volume()`](#footprintbuyvolume)
- [`footprint.delta()`](#footprintdelta)
- [`footprint.get_row_by_price()`](#footprintgetrowbyprice)
- [`footprint.poc()`](#footprintpoc)
- [`footprint.rows()`](#footprintrows)
- [`footprint.sell_volume()`](#footprintsellvolume)
- [`footprint.total_volume()`](#footprinttotalvolume)
- [`footprint.vah()`](#footprintvah)
- [`footprint.val()`](#footprintval)
- [`request.currency_rate()`](#requestcurrencyrate)
- [`request.dividends()`](#requestdividends)
- [`request.earnings()`](#requestearnings)
- [`request.economic()`](#requesteconomic)
- [`request.financial()`](#requestfinancial)
- [`request.footprint()`](#requestfootprint)
- [`request.quandl()`](#requestquandl)
- [`request.security()`](#requestsecurity)
- [`request.security_lower_tf()`](#requestsecuritylowertf)
- [`request.seed()`](#requestseed)
- [`request.splits()`](#requestsplits)
- [`syminfo.prefix()`](#syminfoprefix)
- [`syminfo.ticker()`](#syminfoticker)
- [`ticker.heikinashi()`](#tickerheikinashi)
- [`ticker.inherit()`](#tickerinherit)
- [`ticker.kagi()`](#tickerkagi)
- [`ticker.linebreak()`](#tickerlinebreak)
- [`ticker.modify()`](#tickermodify)
- [`ticker.new()`](#tickernew)
- [`ticker.pointfigure()`](#tickerpointfigure)
- [`ticker.renko()`](#tickerrenko)
- [`ticker.standard()`](#tickerstandard)
- [`volume_row.buy_volume()`](#volumerowbuyvolume)
- [`volume_row.delta()`](#volumerowdelta)
- [`volume_row.down_price()`](#volumerowdownprice)
- [`volume_row.has_buy_imbalance()`](#volumerowhasbuyimbalance)
- [`volume_row.has_sell_imbalance()`](#volumerowhassellimbalance)
- [`volume_row.sell_volume()`](#volumerowsellvolume)
- [`volume_row.total_volume()`](#volumerowtotalvolume)
- [`volume_row.up_price()`](#volumerowupprice)

---

## footprint.buy_volume()
Calculates the total "buy" volume for the volume footprint represented by a footprint object.

### Syntax
```pine
footprint.buy_volume(id) → series float
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.

### Returns
The total "buy" volume measured by the footprint.

## footprint.delta()
Calculates the overall volume delta for the volume footprint represented by a footprint object. The value represents the difference between the footprint's total "buy" volume and "sell" volume. A positive value indicates that the total "buy" volume in the footprint exceeds the total "sell" volume, and a negative value indicates the opposite.

### Syntax
```pine
footprint.delta(id) → series float
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.

### Returns
The overall volume delta for the footprint.

## footprint.get_row_by_price()
Analyzes the volume footprint represented by a footprint object to find the row whose price range includes the specified price level. If the price belongs to one of the rows, the function returns the ID of the volume_row object that contains the data for that row. Otherwise, it returns na.

### Syntax
```pine
footprint.get_row_by_price(id, price) → volume_row
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.
- `price` (*series int/float*) — The price value for which to find the corresponding footprint row.

### Returns
The ID of a volume_row object representing the footprint row that contains the specified price, or na if the price is outside the footprint's price range.

## footprint.poc()
Finds the Point of Control (POC) row for the volume footprint represented by a footprint object, then returns the ID of a volume_row object containing the data for that row.

### Syntax
```pine
footprint.poc(id) → volume_row
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.

### Returns
The ID of a volume_row object representing the footprint's POC row.

## footprint.rows()
Creates an array containing all volume_row IDs from a footprint object. Each volume_row object referenced in the array contains data for one row in the calculated volume footprint, where the first object represents the lowest row and the last one represents the highest row.

### Syntax
```pine
footprint.rows(id) → array<volume_row>
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.

### Returns
The ID of an array containing a volume_row ID for each row in the footprint.

## footprint.sell_volume()
Calculates the total "sell" volume for the volume footprint represented by a footprint object.

### Syntax
```pine
footprint.sell_volume(id) → series float
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.

### Returns
The total "sell" volume measured by the footprint.

## footprint.total_volume()
Calculates the sum of the total "buy" volume and "sell" volume for the volume footprint represented by a footprint object.

### Syntax
```pine
footprint.total_volume(id) → series float
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.

### Returns
The total volume measured by the footprint.

## footprint.vah()
Finds the Value Area High (VAH) row for the volume footprint represented by a footprint object, then returns the ID of a volume_row object containing the data for that row.

### Syntax
```pine
footprint.vah(id) → volume_row
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.

### Returns
The ID of a volume_row object representing the footprint's VAH row.

## footprint.val()
Finds the Value Area Low (VAL) row for the volume footprint represented by a footprint object, then returns the ID of a volume_row object containing the data for that row.

### Syntax
```pine
footprint.val(id) → volume_row
```

### Arguments
- `id` (*footprint*) — The reference (ID) of the footprint object to analyze.

### Returns
The ID of a volume_row object representing the footprint's VAL row.

## request.currency_rate()
Provides a daily rate that can be used to convert a value expressed in the from currency to another in the to currency.

### Syntax
```pine
request.currency_rate(from, to, ignore_invalid_currency) → series float
```

### Arguments
- `from` (*series string*) — The currency in which the value to be converted is expressed. Possible values: a three-letter string with the currency code in the ISO 4217 format (e.g. "USD"), or one of the built-in variables that return currency codes, like syminfo.currency or currency.USD.
- `to` (*series string*) — The currency in which the value is to be converted. Possible values: a three-letter string with the currency code in the ISO 4217 format (e.g. "USD"), or one of the built-in variables that return currency codes, like syminfo.currency or currency.USD.
- `ignore_invalid_currency` (*series bool*) — Determines the behavior of the function if a conversion rate between the two currencies cannot be calculated: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. Optional. The default is false.

### Example
```pine
//@version=6
indicator("Close in British Pounds")
rate = request.currency_rate(syminfo.currency, "GBP")
plot(close * rate)
```

### Remarks
If from and to arguments are equal, function returns 1. Please note that using this variable/function can cause indicator repainting.

## request.dividends()
Requests dividends data for the specified symbol.

### Syntax
```pine
request.dividends(ticker, field, gaps, lookahead, ignore_invalid_symbol, currency) → series float
```

### Arguments
- `ticker` (*series string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL". Using syminfo.ticker will cause an error. Use syminfo.tickerid instead.
- `field` (*series string*) — Input string. Possible values include: dividends.net, dividends.gross. Default value is dividends.gross.
- `gaps` (*simple barmerge_gaps*) — Merge strategy for the requested data (requested data automatically merges with the main series OHLC data). Possible values: barmerge.gaps_on, barmerge.gaps_off. barmerge.gaps_on - requested data is merged with possible gaps (na values). barmerge.gaps_off - requested data is merged continuously without gaps, all the gaps are filled with the previous nearest existing values. Default value is barmerge.gaps_off.
- `lookahead` (*simple barmerge_lookahead*) — Merge strategy for the requested data position. Possible values: barmerge.lookahead_on, barmerge.lookahead_off. Default value is barmerge.lookahead_off starting from version 3. Note that behavour is the same on real-time, and differs only on history.
- `ignore_invalid_symbol` (*input bool*) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.
- `currency` (*series string*) — Currency into which the symbol's currency-related dividends values (e.g. dividends.gross) are to be converted. The conversion rate depends on the previous daily value of a corresponding currency pair from the most popular exchange. A spread symbol is used if no exchange provides the rate directly. Possible values: a "string" representing a valid currency code (e.g., "USD" or "USDT") or a constant from the currency.* namespace (e.g., currency.USD or currency.USDT). The default is syminfo.currency.

### Example
```pine
//@version=6
indicator("request.dividends")
s1 = request.dividends("NASDAQ:BELFA")
plot(s1)
s2 = request.dividends("NASDAQ:BELFA", dividends.net, gaps=barmerge.gaps_on, lookahead=barmerge.lookahead_on)
plot(s2)
```

### Returns
Requested series, or n/a if there is no dividends data for the specified symbol.

### See also
`request.earnings()`, `request.splits()`, `request.security()`, `syminfo.tickerid`

## request.earnings()
Requests earnings data for the specified symbol.

### Syntax
```pine
request.earnings(ticker, field, gaps, lookahead, ignore_invalid_symbol, currency) → series float
```

### Arguments
- `ticker` (*series string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL". Using syminfo.ticker will cause an error. Use syminfo.tickerid instead.
- `field` (*series string*) — Input string. Possible values include: earnings.actual, earnings.estimate, earnings.standardized. Default value is earnings.actual.
- `gaps` (*simple barmerge_gaps*) — Merge strategy for the requested data (requested data automatically merges with the main series OHLC data). Possible values: barmerge.gaps_on, barmerge.gaps_off. barmerge.gaps_on - requested data is merged with possible gaps (na values). barmerge.gaps_off - requested data is merged continuously without gaps, all the gaps are filled with the previous nearest existing values. Default value is barmerge.gaps_off.
- `lookahead` (*simple barmerge_lookahead*) — Merge strategy for the requested data position. Possible values: barmerge.lookahead_on, barmerge.lookahead_off. Default value is barmerge.lookahead_off starting from version 3. Note that behavour is the same on real-time, and differs only on history.
- `ignore_invalid_symbol` (*input bool*) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.
- `currency` (*series string*) — Currency into which the symbol's currency-related earnings values (e.g. earnings.actual) are to be converted. The conversion rate depends on the previous daily value of a corresponding currency pair from the most popular exchange. A spread symbol is used if no exchange provides the rate directly. Possible values: a "string" representing a valid currency code (e.g., "USD" or "USDT") or a constant from the currency.* namespace (e.g., currency.USD or currency.USDT). The default is syminfo.currency.

### Example
```pine
//@version=6
indicator("request.earnings")
s1 = request.earnings("NASDAQ:BELFA")
plot(s1)
s2 = request.earnings("NASDAQ:BELFA", earnings.actual, gaps=barmerge.gaps_on, lookahead=barmerge.lookahead_on)
plot(s2)
```

### Returns
Requested series, or n/a if there is no earnings data for the specified symbol.

### See also
`request.dividends()`, `request.splits()`, `request.security()`, `syminfo.tickerid`

## request.economic()
Requests economic data for a symbol. Economic data includes information such as the state of a country's economy (GDP, inflation rate, etc.) or of a particular industry (steel production, ICU beds, etc.).

### Syntax
```pine
request.economic(country_code, field, gaps, ignore_invalid_symbol) → series float
```

### Arguments
- `country_code` (*series string*) — The code of the country (e.g. "US") or the region (e.g. "EU") for which the economic data is requested. The Help Center article lists the countries and their codes. The countries for which information is available vary with metrics. The Help Center article for each metric lists the countries for which the metric is available.
- `field` (*series string*) — The code of the requested economic metric (e.g., "GDP"). The Help Center article lists the metrics and their codes.
- `gaps` (*simple barmerge_gaps*) — Specifies how the returned values are merged on chart bars. Possible values: barmerge.gaps_off, barmerge.gaps_on. With barmerge.gaps_on, a value only appears on the current chart bar when it first becomes available from the function's context, otherwise na is returned (thus a "gap" occurs). With barmerge.gaps_off, what would otherwise be gaps are filled with the latest known value returned, avoiding na values. Optional. The default is barmerge.gaps_off.
- `ignore_invalid_symbol` (*input bool*) — Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. Optional. The default is false.

### Example
```pine
//@version=6
indicator("US GDP")
e = request.economic("US", "GDP")
plot(e)
```

### Returns
Requested series.

### Remarks
Economic data can also be accessed from charts, just like a regular symbol. Use "ECONOMIC" as the exchange name and {country_code}{field} as the ticker. The name of US GDP data is thus "ECONOMIC:USGDP".

### See also
`request.financial()`

## request.financial()
Requests financial series for symbol.

### Syntax
```pine
request.financial(symbol, financial_id, period, gaps, ignore_invalid_symbol, currency) → series float
```

### Arguments
- `symbol` (*series string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL".
- `financial_id` (*series string*) — Financial identifier. You can find the list of available ids via our Help Center.
- `period` (*series string*) — Reporting period. Possible values are "TTM", "FY", "FQ", "FH", "D".
- `gaps` (*simple barmerge_gaps*) — Merge strategy for the requested data (requested data automatically merges with the main series: OHLC data). Possible values include: barmerge.gaps_on, barmerge.gaps_off. barmerge.gaps_on - requested data is merged with possible gaps (na values). barmerge.gaps_off - requested data is merged continuously without gaps, all the gaps are filled with the previous, nearest existing values. Default value is barmerge.gaps_off.
- `ignore_invalid_symbol` (*input bool*) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.
- `currency` (*series string*) — Optional. Currency into which the symbol's financial metrics (e.g. Net Income) are to be converted. The conversion rate depends on the previous daily value of a corresponding currency pair from the most popular exchange. A spread symbol is used if no exchange provides the rate directly. Possible values: a "string" representing a valid currency code (e.g., "USD" or "USDT") or a constant from the currency.* namespace (e.g., currency.USD or currency.USDT). The default is syminfo.currency.

### Example
```pine
//@version=6
indicator("request.financial")
f = request.financial("NASDAQ:MSFT", "ACCOUNTS_PAYABLE", "FY")
plot(f)
```

### Returns
Requested series.

### See also
`request.security()`, `syminfo.tickerid`

## request.footprint()
Requests the ID of a footprint object that contains data for calculating volume footprint information for the current chart bar. Scripts can use the returned ID in calls to the footprint.*() functions to retrieve footprint data, including footprint rows, categorized volume sums, and volume delta.

### Syntax
```pine
request.footprint(ticks_per_row, va_percent, imbalance_percent) → footprint
```

### Arguments
- `ticks_per_row` (*simple int*) — The price range of each footprint row, expressed in ticks.
- `va_percent` (*simple int/float*) — Optional. The percentage of each footprint's total volume to use for calculating the value area (VA). The default is 70.
- `imbalance_percent` (*simple int/float*) — Optional. The percentage difference in volume for detecting row imbalances. Scripts can use volume_row IDs retrieved from the returned footprint object in calls to volume_row.has_buy_imbalance() and volume_row.has_sell_imbalance() to identify imbalanced rows. A row is imbalanced if its "buy" volume exceeds the "sell" volume of the row below it by the specified percentage, or if its "sell" volume exceeds the "buy" volume of the row above it by the percentage. The default is 300.

### Returns
The ID of a footprint object containing volume footprint data for the current bar, or na if no data is available.

### Remarks
Only accounts with Premium or Ultimate plans can use scripts that call this function.
A single script cannot include more than one request.footprint() call.

## request.quandl()
Note: This function has been deprecated due to the API change from NASDAQ Data Link. Requests for "QUANDL" symbols are no longer valid and requests for them return a runtime error.
Some of the data previously provided by this function is available on TradingView through other feeds, such as "BCHAIN" or "FRED". Use Symbol Search to look for such data based on its description. Commitment of Traders (COT) data can be requested using the official LibraryCOT library.
Requests Nasdaq Data Link (formerly Quandl) data for a symbol.

### Syntax
```pine
request.quandl(ticker, gaps, index, ignore_invalid_symbol) → series float
```

### Arguments
- `ticker` (*series string*) — Symbol. Note that the name of a time series and Quandl data feed should be divided by a forward slash. For example: "CFTC/SB_FO_ALL".
- `gaps` (*simple barmerge_gaps*) — Merge strategy for the requested data (requested data automatically merges with the main series: OHLC data). Possible values include: barmerge.gaps_on, barmerge.gaps_off. barmerge.gaps_on - requested data is merged with possible gaps (na values). barmerge.gaps_off - requested data is merged continuously without gaps, all the gaps are filled with the previous, nearest existing values. Default value is barmerge.gaps_off.
- `index` (*series int*) — A Quandl time-series column index.
- `ignore_invalid_symbol` (*input bool*) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.

### Example
```pine
//@version=6
indicator("request.quandl")
f = request.quandl("CFTC/SB_FO_ALL", barmerge.gaps_off, 0)
plot(f)
```

### Returns
Requested series.

### See also
`request.security()`, `syminfo.tickerid`

## request.security()
Requests the result of an expression from a specified context (symbol and timeframe).

### Syntax
```pine
request.security(symbol, timeframe, expression, gaps, lookahead, ignore_invalid_symbol, currency, calc_bars_count) → series <type>
```

### Arguments
- `symbol` (*series string*) — Symbol or ticker identifier of the requested data. Use an empty string or syminfo.tickerid to request data using the chart's symbol. To retrieve data with additional modifiers (extended sessions, dividend adjustments, non-standard chart types like Heikin Ashi and Renko, etc.), create a custom ticker ID for the request using the functions in the ticker.* namespace.
- `timeframe` (*series string*) — Timeframe of the requested data. Use an empty string or timeframe.period to request data from the chart's timeframe or the timeframe specified in the indicator() function. To request data from a different timeframe, supply a valid timeframe string. See here to learn about specifying timeframe strings.
- `expression` (*variable, function, object, array, matrix, or map of series int/float/bool/string/color/enum, or a tuple of these*) — The expression to calculate and return from the requested context. It can accept a built-in variable like close, a user-defined variable, an expression such as ta.change(close) / (high - low), a function call that does not use Pine Script® drawings, an object, a collection, or a tuple of expressions.
- `gaps` (*simple barmerge_gaps*) — Specifies how the returned values are merged on chart bars. Possible values: barmerge.gaps_on, barmerge.gaps_off. With barmerge.gaps_on a value only appears on the current chart bar when it first becomes available from the function's context, otherwise na is returned (thus a "gap" occurs). With barmerge.gaps_off what would otherwise be gaps are filled with the latest known value returned, avoiding na values. Optional. The default is barmerge.gaps_off.
- `lookahead` (*simple barmerge_lookahead*) — On historical bars only, returns data from the timeframe before it elapses. Possible values: barmerge.lookahead_on, barmerge.lookahead_off. Has no effect on realtime values. Optional. The default is barmerge.lookahead_off starting from Pine Script® v3. The default is barmerge.lookahead_on in v1 and v2. WARNING: Using barmerge.lookahead_on at timeframes higher than the chart's without offsetting the expression argument like in close[1] will introduce future leak in scripts, as the function will then return the close price before it is actually known in the current context. As is explained in the User Manual's page on Repainting this will produce misleading results.
- `ignore_invalid_symbol` (*input bool*) — Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and throw a runtime error; if true, the function will return na and execution will continue. Optional. The default is false.
- `currency` (*series string*) — Optional. Specifies the target currency for converting values expressed in currency units (e.g., open, high, low, close) or expressions involving such values. Literal values such as 200 are not converted. The conversion rate for monetary values depends on the previous daily value of a corresponding currency pair from the most popular exchange. A spread symbol is used if no exchange provides the rate directly. Possible values: a "string" representing a valid currency code (e.g., "USD" or "USDT") or a constant from the currency.* namespace (e.g., currency.USD or currency.USDT). The default is syminfo.currency.
- `calc_bars_count` (*simple int*) — Optional. Determines the maximum number of recent historical bars that the function can request. If specified, the function evaluates the expression argument starting from that number of bars behind the last historical bar in the requested dataset, treating those bars as the only available data. Limiting the number of historical bars in a request can help improve calculation efficiency in some cases. The default is the same as the number of chart bars available for the symbol and timeframe. The maximum number of bars that the function can attempt to retrieve depends on the intrabar limit of the user's plan. However, the request cannot retrieve more bars than are available in the dataset.

### Example
```pine
//@version=6
indicator("Simple `request.security()` calls")
// Returns 1D close of the current symbol.
dailyClose = request.security(syminfo.tickerid, "1D", close)
plot(dailyClose)

// Returns the close of "AAPL" from the same timeframe as currently open on the chart.
aaplClose = request.security("AAPL", timeframe.period, close)
plot(aaplClose)
```

### Example
```pine
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

### Returns
A result determined by expression.

### Remarks
Scripts using this function might calculate differently on historical and realtime bars, leading to repainting.
A single script can contain no more than 40 unique request.*() function calls. A call is unique only if it does not call the same function with the same arguments.
When using two calls to a request.*() function to evaluate the same expression from the same context with different calc_bars_count values, the second call requests the same number of historical bars as the first. For example, if a script calls request.security("AAPL", "", close, calc_bars_count = 3) after it calls request.security("AAPL", "", close, calc_bars_count = 5), the second call also uses five bars of historical data, not three.
The symbol of a request.() call can be inherited if it is not specified precisely, i.e., if the symbol argument is an empty string or syminfo.tickerid. Similarly, the timeframe of a request.() call can be inherited if the timeframe argument is an empty string or timeframe.period. These values are normally taken from the chart on which the script is running. However, if request.*() function A is called from within the expression of request.*() function B, then function A can inherit the values from function B. See here for more information.

### See also
`syminfo.ticker`, `syminfo.tickerid`, `timeframe.period`, `ticker.new()`, `ticker.modify()`, `request.security_lower_tf()`, `request.dividends()`, `request.earnings()`, `request.splits()`, `request.financial()`

## request.security_lower_tf()
Requests the results of an expression from a specified symbol on a timeframe lower than or equal to the chart's timeframe. It returns an array containing one element for each lower-timeframe bar within the chart bar. On a 5-minute chart, requesting data using a timeframe argument of "1" typically returns an array with five elements representing the value of the expression on each 1-minute bar, ordered by time with the earliest value first.

### Syntax
```pine
request.security_lower_tf(symbol, timeframe, expression, ignore_invalid_symbol, currency, ignore_invalid_timeframe, calc_bars_count) → array<type>
```

### Arguments
- `symbol` (*series string*) — Symbol or ticker identifier of the requested data. Use an empty string or syminfo.tickerid to request data using the chart's symbol. To retrieve data with additional modifiers (extended sessions, dividend adjustments, non-standard chart types like Heikin Ashi and Renko, etc.), create a custom ticker ID for the request using the functions in the ticker.* namespace.
- `timeframe` (*series string*) — Timeframe of the requested data. Use an empty string or timeframe.period to request data from the chart's timeframe or the timeframe specified in the indicator() function. To request data from a different timeframe, supply a valid timeframe string. See here to learn about specifying timeframe strings.
- `expression` (*variable, object or function of series int/float/bool/string/color/enum, or a tuple of these*) — The expression to calculate and return from the requested context. It can accept a built-in variable like close, a user-defined variable, an expression such as ta.change(close) / (high - low), a function call that does not use Pine Script® drawings, an object, or a tuple of expressions. Collections are not allowed unless they are within the fields of an object
- `ignore_invalid_symbol` (*series bool*) — Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and throw a runtime error; if true, the function will return na and execution will continue. Optional. The default is false.
- `currency` (*series string*) — Optional. Specifies the target currency for converting values expressed in currency units (e.g., open, high, low, close) or expressions involving such values. Literal values such as 200 are not converted. The conversion rate for monetary values depends on the previous daily value of a corresponding currency pair from the most popular exchange. A spread symbol is used if no exchange provides the rate directly. Possible values: a "string" representing a valid currency code (e.g., "USD" or "USDT") or a constant from the currency.* namespace (e.g., currency.USD or currency.USDT). The default is syminfo.currency.
- `ignore_invalid_timeframe` (*series bool*) — Determines the behavior of the function when the chart's timeframe is smaller than the timeframe used in the function call. If false, the script will halt and throw a runtime error. If true, the function will return na and execution will continue. Optional. The default is false.
- `calc_bars_count` (*simple int*) — Optional. Determines the maximum number of recent historical bars that the function can request. If specified, the function evaluates the expression argument starting from that number of bars behind the last historical bar in the requested dataset, treating those bars as the only available data. Limiting the number of historical bars in a request can help improve calculation efficiency in some cases. The default is the same as the number of chart bars available for the symbol and timeframe. The maximum number of bars that the function can attempt to retrieve depends on the intrabar limit of the user's plan. However, the request cannot retrieve more bars than are available in the dataset.

### Example
```pine
//@version=6
indicator("`request.security_lower_tf()` Example", overlay = true)

// If the current chart timeframe is set to 120 minutes, then the `arrayClose` array will contain two 'close' values from the 60 minute timeframe for each bar.
arrClose = request.security_lower_tf(syminfo.tickerid, "60", close)

if bar_index == last_bar_index - 1
    label.new(bar_index, high, str.tostring(arrClose))
```

### Returns
An array of a type determined by expression, or a tuple of these.

### Remarks
Scripts using this function might calculate differently on historical and realtime bars, leading to repainting.
Please note that spreads (e.g., "AAPL+MSFT*TSLA") do not always return reliable data with this function.
A single script can contain no more than 40 unique request.*() function calls. A call is unique only if it does not call the same function with the same arguments.
When using two calls to a request.*() function to evaluate the same expression from the same context with different calc_bars_count values, the second call requests the same number of historical bars as the first. For example, if a script calls request.security("AAPL", "", close, calc_bars_count = 3) after it calls request.security("AAPL", "", close, calc_bars_count = 5), the second call also uses five bars of historical data, not three.
The symbol of a request.() call can be inherited if it is not specified precisely, i.e., if the symbol argument is an empty string or syminfo.tickerid. Similarly, the timeframe of a request.() call can be inherited if the timeframe argument is an empty string or timeframe.period. These values are normally taken from the chart that the script is running on. However, if request.*() function A is called from within the expression of request.*() function B, then function A can inherit the values from function B. See here for more information.

### See also
`request.security()`, `syminfo.ticker`, `syminfo.tickerid`, `timeframe.period`, `ticker.new()`, `request.dividends()`, `request.earnings()`, `request.splits()`, `request.financial()`

## request.seed()
Requests the result of an expression evaluated on data from a user-maintained GitHub repository. **Note:**The creation of new Pine Seeds repositories is suspended; only existing repositories are currently supported. See the Pine Seeds documentation on GitHub to learn more.

### Syntax
```pine
request.seed(source, symbol, expression, ignore_invalid_symbol, calc_bars_count) → series <type>
```

### Arguments
- `source` (*series string*) — Name of the GitHub repository.
- `symbol` (*series string*) — Name of the file in the GitHub repository containing the data. The ".csv" file extension must not be included.
- `expression` (*<arg_expr_type>*) — An expression to be calculated and returned from the requested symbol's context. It can be a built-in variable like close, an expression such as ta.sma(close, 100), a non-mutable variable previously calculated in the script, a function call that does not use Pine Script® drawings, an array, a matrix, or a tuple. Mutable variables are not allowed, unless they are enclosed in the body of a function used in the expression.
- `ignore_invalid_symbol` (*input bool*) — Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and throw a runtime error; if true, the function will return na and execution will continue. Optional. The default is false.
- `calc_bars_count` (*simple int*) — Optional. If specified, the function requests only this number of values from the end of the symbol's history and calculates expression as if these values are the only available data, which might improve calculation speed in some cases. The default is the same as the number of chart bars available for the symbol and timeframe. The maximum number of bars that the function can attempt to retrieve depends on the intrabar limit of the user's plan. However, the request cannot retrieve more bars than are available in the dataset.

### Example
```pine
//@version=6
indicator("BTC Development Activity")

[devAct, devActSMA] = request.seed("seed_crypto_santiment", "BTC_DEV_ACTIVITY", [close, ta.sma(close, 10)])

plot(devAct, "BTC Development Activity")
plot(devActSMA, "BTC Development Activity SMA10", color = color.yellow)
```

### Returns
Requested series or tuple of series, which may include array/matrix IDs.

## request.splits()
Requests splits data for the specified symbol.

### Syntax
```pine
request.splits(ticker, field, gaps, lookahead, ignore_invalid_symbol) → series float
```

### Arguments
- `ticker` (*series string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL". Using syminfo.ticker will cause an error. Use syminfo.tickerid instead.
- `field` (*series string*) — Input string. Possible values include: splits.denominator, splits.numerator.
- `gaps` (*simple barmerge_gaps*) — Merge strategy for the requested data (requested data automatically merges with the main series OHLC data). Possible values: barmerge.gaps_on, barmerge.gaps_off. barmerge.gaps_on - requested data is merged with possible gaps (na values). barmerge.gaps_off - requested data is merged continuously without gaps, all the gaps are filled with the previous nearest existing values. Default value is barmerge.gaps_off.
- `lookahead` (*simple barmerge_lookahead*) — Merge strategy for the requested data position. Possible values: barmerge.lookahead_on, barmerge.lookahead_off. Default value is barmerge.lookahead_off starting from version 3. Note that behavour is the same on real-time, and differs only on history.
- `ignore_invalid_symbol` (*input bool*) — An optional parameter. Determines the behavior of the function if the specified symbol is not found: if false, the script will halt and return a runtime error; if true, the function will return na and execution will continue. The default value is false.

### Example
```pine
//@version=6
indicator("request.splits")
s1 = request.splits("NASDAQ:BELFA", splits.denominator)
plot(s1)
s2 = request.splits("NASDAQ:BELFA", splits.denominator, gaps=barmerge.gaps_on, lookahead=barmerge.lookahead_on)
plot(s2)
```

### Returns
Requested series, or n/a if there is no splits data for the specified symbol.

### See also
`request.earnings()`, `request.dividends()`, `request.security()`, `syminfo.tickerid`

## syminfo.prefix()
Returns exchange prefix of the symbol, e.g. "NASDAQ".

### Syntax & Overloads
```pine
syminfo.prefix(symbol) → simple string
```
```pine
syminfo.prefix(symbol) → series string
```

### Arguments
- `symbol` (*simple string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL".

### Example
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

### Returns
Returns exchange prefix of the symbol, e.g. "NASDAQ".

### Remarks
The result of the function is used in the ticker.new()/ticker.modify() and request.security().

### See also
`syminfo.tickerid`, `syminfo.ticker`, `syminfo.prefix`, `syminfo.ticker()`, `ticker.new()`

## syminfo.ticker()
Returns symbol name without exchange prefix, e.g. "AAPL".

### Syntax & Overloads
```pine
syminfo.ticker(symbol) → simple string
```
```pine
syminfo.ticker(symbol) → series string
```

### Arguments
- `symbol` (*simple string*) — Symbol. Note that the symbol should be passed with a prefix. For example: "NASDAQ:AAPL" instead of "AAPL".

### Example
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

### Returns
Returns symbol name without exchange prefix, e.g. "AAPL".

### Remarks
The result of the function is used in the ticker.new()/ticker.modify() and request.security().

### See also
`syminfo.tickerid`, `syminfo.ticker`, `syminfo.prefix`, `syminfo.prefix()`, `ticker.new()`

## ticker.heikinashi()
Creates a ticker identifier for requesting Heikin Ashi bar values.

### Syntax & Overloads
```pine
ticker.heikinashi(symbol) → simple string
```
```pine
ticker.heikinashi(symbol) → series string
```

### Arguments
- `symbol` (*simple string*) — Symbol ticker identifier.

### Example
```pine
//@version=6
indicator("ticker.heikinashi", overlay=true)
heikinashi_close = request.security(ticker.heikinashi(syminfo.tickerid), timeframe.period, close)

heikinashi_aapl_60_close = request.security(ticker.heikinashi("AAPL"), "60", close)
plot(heikinashi_close)
plot(heikinashi_aapl_60_close)
```

### Returns
String value of ticker id, that can be supplied to request.security() function.

### See also
`syminfo.tickerid`, `syminfo.ticker`, `request.security()`, `ticker.renko()`, `ticker.linebreak()`, `ticker.kagi()`, `ticker.pointfigure()`

## ticker.inherit()
Constructs a ticker ID for the specified symbol with additional parameters inherited from the ticker ID passed into the function call, allowing the script to request a symbol's data using the same modifiers that the from_tickerid has, including extended session, dividend adjustment, currency conversion, non-standard chart types, back-adjustment, settlement-as-close, etc.

### Syntax & Overloads
```pine
ticker.inherit(from_tickerid, symbol) → simple string
```
```pine
ticker.inherit(from_tickerid, symbol) → series string
```

### Arguments
- `from_tickerid` (*simple string*) — The ticker ID to inherit modifiers from.
- `symbol` (*simple string*) — The symbol to construct the new ticker ID for.

### Example
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

### Remarks
If the constructed ticker ID inherits a modifier that doesn't apply to the symbol (e.g., if the from_tickerid has Extended Hours enabled, but no such option is available for the symbol), the script will ignore the modifier when requesting data using the ID.

## ticker.kagi()
Creates a ticker identifier for requesting Kagi values.

### Syntax & Overloads
```pine
ticker.kagi(symbol, reversal) → simple string
```
```pine
ticker.kagi(symbol, reversal) → series string
```
```pine
ticker.kagi(symbol, param, style) → simple string
```
```pine
ticker.kagi(symbol, param, style) → series string
```

### Arguments
- `symbol` (*simple string*) — Symbol ticker identifier.
- `reversal` (*simple int/float*) — Reversal amount (absolute price value).

### Example
```pine
//@version=6
indicator("ticker.kagi", overlay=true)
kagi_tickerid = ticker.kagi(syminfo.tickerid, 3)
kagi_close = request.security(kagi_tickerid, timeframe.period, close)
plot(kagi_close)
```

### Returns
String value of ticker id, that can be supplied to request.security() function.

### See also
`syminfo.tickerid`, `syminfo.ticker`, `request.security()`, `ticker.heikinashi()`, `ticker.renko()`, `ticker.linebreak()`, `ticker.pointfigure()`

## ticker.linebreak()
Creates a ticker identifier for requesting Line Break values.

### Syntax & Overloads
```pine
ticker.linebreak(symbol, number_of_lines) → simple string
```
```pine
ticker.linebreak(symbol, number_of_lines) → series string
```

### Arguments
- `symbol` (*simple string*) — Symbol ticker identifier.
- `number_of_lines` (*simple int*) — Number of line.

### Example
```pine
//@version=6
indicator("ticker.linebreak", overlay=true)
linebreak_tickerid = ticker.linebreak(syminfo.tickerid, 3)
linebreak_close = request.security(linebreak_tickerid, timeframe.period, close)
plot(linebreak_close)
```

### Returns
String value of ticker id, that can be supplied to request.security() function.

### See also
`syminfo.tickerid`, `syminfo.ticker`, `request.security()`, `ticker.heikinashi()`, `ticker.renko()`, `ticker.kagi()`, `ticker.pointfigure()`

## ticker.modify()
Creates a ticker identifier for requesting additional data for the script.

### Syntax & Overloads
```pine
ticker.modify(tickerid, session, adjustment, backadjustment, settlement_as_close) → simple string
```
```pine
ticker.modify(tickerid, session, adjustment, backadjustment, settlement_as_close) → series string
```

### Arguments
- `tickerid` (*simple string*) — Symbol name with exchange prefix, e.g. 'BATS:MSFT', 'NASDAQ:MSFT' or tickerid with session and adjustment from the ticker.new() function.
- `session` (*simple string*) — Session type. Optional argument. Possible values: session.regular, session.extended. Session type of the current chart is syminfo.session. If session is not given, then syminfo.session value is used.
- `adjustment` (*simple string*) — Adjustment type. Optional argument. Possible values: adjustment.none, adjustment.splits, adjustment.dividends. If adjustment is not given, then default adjustment value is used (can be different depending on particular instrument).
- `backadjustment` (*simple backadjustment*) — Specifies whether past contract data on continuous futures symbols is back-adjusted. This setting only affects the data from symbols with this option available on their charts. Optional. The default is backadjustment.inherit, meaning that the modified ticker ID inherits the setting from the ticker ID passed to the tickerid parameter, or it inherits the symbol's default if the tickerid does not specify this setting. Possible values: backadjustment.inherit, backadjustment.on, backadjustment.off.
- `settlement_as_close` (*simple settlement*) — Specifies whether a futures symbol's close value represents the actual closing price or the settlement price on "1D" and higher timeframes. This setting only affects the data from symbols with this option available on their charts. Optional. The default is settlement_as_close.inherit, meaning that the modified ticker ID inherits the setting from the tickerid passed into the function, or it inherits the chart symbol's default if the tickerid does not specify this setting. Possible values: settlement_as_close.inherit, settlement_as_close.on, settlement_as_close.off.

### Example
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

### Returns
String value of ticker id, that can be supplied to request.security() function.

### See also
`syminfo.tickerid`, `syminfo.ticker`, `syminfo.session`, `session.extended`, `session.regular`, `ticker.heikinashi()`, `adjustment.none`, `adjustment.splits`, `adjustment.dividends`, `backadjustment.inherit`, `backadjustment.on`, `backadjustment.off`, `settlement_as_close.inherit`, `settlement_as_close.on`, `settlement_as_close.off`

## ticker.new()
Creates a ticker identifier for requesting additional data for the script.

### Syntax & Overloads
```pine
ticker.new(prefix, ticker, session, adjustment, backadjustment, settlement_as_close) → simple string
```
```pine
ticker.new(prefix, ticker, session, adjustment, backadjustment, settlement_as_close) → series string
```

### Arguments
- `prefix` (*simple string*) — Exchange prefix. For example: 'BATS', 'NYSE', 'NASDAQ'. Exchange prefix of main series is syminfo.prefix.
- `ticker` (*simple string*) — Ticker name. For example 'AAPL', 'MSFT', 'EURUSD'. Ticker name of the main series is syminfo.ticker.
- `session` (*simple string*) — Session type. Optional argument. Possible values: session.regular, session.extended. Session type of the current chart is syminfo.session. If session is not given, then syminfo.session value is used.
- `adjustment` (*simple string*) — Adjustment type. Optional argument. Possible values: adjustment.none, adjustment.splits, adjustment.dividends. If adjustment is not given, then default adjustment value is used (can be different depending on particular instrument).
- `backadjustment` (*simple backadjustment*) — Specifies whether past contract data on continuous futures symbols is back-adjusted. This setting only affects the data from symbols with this option available on their charts. Optional. The default is backadjustment.inherit, meaning that the new ticker ID inherits the symbol's default setting. Possible values: backadjustment.inherit, backadjustment.on, backadjustment.off.
- `settlement_as_close` (*simple settlement*) — Specifies whether a futures symbol's close value represents the actual closing price or the settlement price on "1D" and higher timeframes. This setting only affects the data from symbols with this option available on their charts. Optional. The default is settlement_as_close.inherit, meaning that the new ticker ID inherits the chart symbol's default setting. Possible values: settlement_as_close.inherit, settlement_as_close.on, settlement_as_close.off.

### Example
```pine
//@version=6
indicator("ticker.new", overlay=true)
t = ticker.new(syminfo.prefix, syminfo.ticker, session.regular, adjustment.splits)
t2 = ticker.heikinashi(t)
c = request.security(t2, timeframe.period, low, barmerge.gaps_on)
plot(c, style=plot.style_linebr)
```

### Returns
String value of ticker id, that can be supplied to request.security() function.

### Remarks
You may use return value of ticker.new() function as input argument for ticker.heikinashi(), ticker.renko(), ticker.linebreak(), ticker.kagi(), ticker.pointfigure() functions.

### See also
`syminfo.tickerid`, `syminfo.ticker`, `syminfo.session`, `session.extended`, `session.regular`, `ticker.heikinashi()`, `adjustment.none`, `adjustment.splits`, `adjustment.dividends`, `backadjustment.inherit`, `backadjustment.on`, `backadjustment.off`, `settlement_as_close.inherit`, `settlement_as_close.on`, `settlement_as_close.off`

## ticker.pointfigure()
Creates a ticker identifier for requesting Point & Figure values.

### Syntax & Overloads
```pine
ticker.pointfigure(symbol, source, style, param, reversal) → simple string
```
```pine
ticker.pointfigure(symbol, source, style, param, reversal) → series string
```

### Arguments
- `symbol` (*simple string*) — Symbol ticker identifier.
- `source` (*simple string*) — The source for calculating Point & Figure. Possible values are: 'hl', 'close'.
- `style` (*simple string*) — Specifies the ticker's box size assignment method. Possible values: "ATR" for Average True Range sizing, "Traditional" to use a fixed size, or "PercentageLTP" to use a percentage of the last trading price.
- `param` (*simple int/float*) — Represents the ticker's "ATR length" value if the style value is "ATR", "Box size" value if the style is "Traditional", or "Percentage" value if the style is "PercentageLTP".
- `reversal` (*simple int*) — Reversal amount.

### Example
```pine
//@version=6
indicator("ticker.pointfigure", overlay=true)
pnf_tickerid = ticker.pointfigure(syminfo.tickerid, "hl", "Traditional", 1, 3)
pnf_close = request.security(pnf_tickerid, timeframe.period, close)
plot(pnf_close)
```

### Returns
String value of ticker id, that can be supplied to request.security() function.

### See also
`syminfo.tickerid`, `syminfo.ticker`, `request.security()`, `ticker.heikinashi()`, `ticker.renko()`, `ticker.linebreak()`, `ticker.kagi()`

## ticker.renko()
Creates a ticker identifier for requesting Renko values.

### Syntax & Overloads
```pine
ticker.renko(symbol, style, param, request_wicks, source) → simple string
```
```pine
ticker.renko(symbol, style, param, request_wicks, source) → series string
```

### Arguments
- `symbol` (*simple string*) — Symbol ticker identifier.
- `style` (*simple string*) — Specifies the ticker's box size assignment method. Possible values: "ATR" for Average True Range sizing, "Traditional" to use a fixed size, or "PercentageLTP" to use a percentage of the last trading price.
- `param` (*simple int/float*) — Represents the ticker's "ATR length" value if the style value is "ATR", "Box size" value if the style is "Traditional", or "Percentage" value if the style is "PercentageLTP".
- `request_wicks` (*simple bool*) — Specifies if wick values are returned for Renko bricks. When true, high and low values requested from a symbol using the ticker formed by this function will include wick values when they are present. When false, high and low will always be equal to either open or close. Optional. The default is false. A detailed explanation of how Renko wicks are calculated can be found in our Help Center.
- `source` (*simple string*) — The source used to calculate bricks. Optional. Possible values: "Close", "OHLC". The default is "Close".

### Example
```pine
//@version=6
indicator("ticker.renko", overlay=true)
renko_tickerid = ticker.renko(syminfo.tickerid, "ATR", 10)
renko_close = request.security(renko_tickerid, timeframe.period, close)
plot(renko_close)
```

### Example
```pine
//@version=6
indicator("Renko candles", overlay=false)
renko_tickerid = ticker.renko(syminfo.tickerid, "ATR", 10)
[renko_open, renko_high, renko_low, renko_close] = request.security(renko_tickerid, timeframe.period, [open, high, low, close])
plotcandle(renko_open, renko_high, renko_low, renko_close, color = renko_close > renko_open ? color.green : color.red)
```

### Returns
String value of ticker id, that can be supplied to request.security() function.

### See also
`syminfo.tickerid`, `syminfo.ticker`, `request.security()`, `ticker.heikinashi()`, `ticker.linebreak()`, `ticker.kagi()`, `ticker.pointfigure()`

## ticker.standard()
Creates a ticker to request data from a standard chart that is unaffected by modifiers like extended session, dividend adjustment, currency conversion, and the calculations of non-standard chart types: Heikin Ashi, Renko, etc. Among other things, this makes it possible to retrieve standard chart values when the script is running on a non-standard chart.

### Syntax & Overloads
```pine
ticker.standard(symbol) → simple string
```
```pine
ticker.standard(symbol) → series string
```

### Arguments
- `symbol` (*simple string*) — A ticker ID to be converted into its standard form. Optional. The default is syminfo.tickerid.

### Example
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

### Returns
A string representing the ticker of a standard chart in the "prefix:ticker" format. If the symbol argument does not contain the prefix and ticker information, the function returns the supplied argument as is.

### See also
`request.security()`

## volume_row.buy_volume()
Calculates the total "buy" volume for the volume footprint row represented by a volume_row object.

### Syntax
```pine
volume_row.buy_volume(id) → series float
```

### Arguments
- `id` (*volume_row*) — The reference (ID) of the volume_row object to analyze.

### Returns
The total "buy" volume for the footprint row.

## volume_row.delta()
Calculates the volume delta for the volume footprint row represented by a volume_row object. The value represents the difference between the row's "buy" volume and "sell" volume. A positive value indicates that the "buy" volume for the row exceeds the "sell" volume, and a negative value indicates the opposite.

### Syntax
```pine
volume_row.delta(id) → series float
```

### Arguments
- `id` (*volume_row*) — The reference (ID) of the volume_row object to analyze.

### Returns
The volume delta for the footprint row.

## volume_row.down_price()
Retrieves the lower price level of the volume footprint row represented by a volume_row object.

### Syntax
```pine
volume_row.down_price(id) → series float
```

### Arguments
- `id` (*volume_row*) — The reference (ID) of the volume_row object to analyze.

### Returns
The lower boundary of the footprint row's price range.

## volume_row.has_buy_imbalance()
Checks whether the volume footprint row represented by a volume_row object has a "buy" imbalance, based on the imbalance_percent argument of the request.footprint() call that the object depends on. Returns true if the row's "buy" volume exceeds the "sell" volume of the row below it in the footprint by the specified percentage, and false otherwise.

### Syntax
```pine
volume_row.has_buy_imbalance(id) → series bool
```

### Arguments
- `id` (*volume_row*) — The reference (ID) of the volume_row object to analyze.

### Returns
A value of true if the footprint row has a detected buy imbalance, and false otherwise.

## volume_row.has_sell_imbalance()
Checks whether the volume footprint row represented by a volume_row object has a sell imbalance, based on the imbalance_percent argument of the request.footprint() call that the object depends on. Returns true if the row's "sell" volume exceeds the "buy" volume of the row above it in the footprint by the specified percentage, and false otherwise.

### Syntax
```pine
volume_row.has_sell_imbalance(id) → series bool
```

### Arguments
- `id` (*volume_row*) — The reference (ID) of the volume_row object to analyze.

### Returns
A value of true if the footprint row has a detected sell imbalance, and false otherwise.

## volume_row.sell_volume()
Calculates the total "sell" volume for the volume footprint row represented by a volume_row object.

### Syntax
```pine
volume_row.sell_volume(id) → series float
```

### Arguments
- `id` (*volume_row*) — The reference (ID) of the volume_row object to analyze.

### Returns
The total "sell" volume for the footprint row.

## volume_row.total_volume()
Calculates the sum of the "buy" and "sell" volume for the volume footprint row represented by a volume_row object.

### Syntax
```pine
volume_row.total_volume(id) → series float
```

### Arguments
- `id` (*volume_row*) — The reference (ID) of the volume_row object to analyze.

### Returns
The total volume for the footprint row.

## volume_row.up_price()
Retrieves the upper price level of the volume footprint row represented by a volume_row object.

### Syntax
```pine
volume_row.up_price(id) → series float
```

### Arguments
- `id` (*volume_row*) — The reference (ID) of the volume_row object to analyze.

### Returns
The upper boundary of the footprint row's price range.
