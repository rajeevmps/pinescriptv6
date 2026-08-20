<!--
Source: https://www.tradingview.com/pine-script-reference/v6/
Pine Script v6 — official TradingView language reference manual
Retrieved: 2026-08-20
-->

# Data request functions

Pulling data from other symbols, timeframes, financials, dividends, and non-standard chart tickers.

**21 functions** · Source: [Pine Script® v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/)

## Index

- [`request.currency_rate()`](#requestcurrencyrate)
- [`request.dividends()`](#requestdividends)
- [`request.earnings()`](#requestearnings)
- [`request.economic()`](#requesteconomic)
- [`request.financial()`](#requestfinancial)
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
