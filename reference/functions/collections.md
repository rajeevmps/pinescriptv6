<!--
Source: https://www.tradingview.com/pine-script-reference/v6/
Pine Script v6 — official TradingView language reference manual
Retrieved: 2026-08-20
-->

# Collection functions (arrays, matrices, maps)

The three reference-type collections and every method that operates on them.

**115 functions** · Source: [Pine Script® v6 Reference Manual](https://www.tradingview.com/pine-script-reference/v6/)

## Index

- [`array.abs()`](#arrayabs)
- [`array.avg()`](#arrayavg)
- [`array.binary_search()`](#arraybinarysearch)
- [`array.binary_search_leftmost()`](#arraybinarysearchleftmost)
- [`array.binary_search_rightmost()`](#arraybinarysearchrightmost)
- [`array.clear()`](#arrayclear)
- [`array.concat()`](#arrayconcat)
- [`array.copy()`](#arraycopy)
- [`array.covariance()`](#arraycovariance)
- [`array.every()`](#arrayevery)
- [`array.fill()`](#arrayfill)
- [`array.first()`](#arrayfirst)
- [`array.from()`](#arrayfrom)
- [`array.get()`](#arrayget)
- [`array.includes()`](#arrayincludes)
- [`array.indexof()`](#arrayindexof)
- [`array.insert()`](#arrayinsert)
- [`array.join()`](#arrayjoin)
- [`array.last()`](#arraylast)
- [`array.lastindexof()`](#arraylastindexof)
- [`array.max()`](#arraymax)
- [`array.median()`](#arraymedian)
- [`array.min()`](#arraymin)
- [`array.mode()`](#arraymode)
- [`array.new_bool()`](#arraynewbool)
- [`array.new_box()`](#arraynewbox)
- [`array.new_color()`](#arraynewcolor)
- [`array.new_float()`](#arraynewfloat)
- [`array.new_int()`](#arraynewint)
- [`array.new_label()`](#arraynewlabel)
- [`array.new_line()`](#arraynewline)
- [`array.new_linefill()`](#arraynewlinefill)
- [`array.new_string()`](#arraynewstring)
- [`array.new_table()`](#arraynewtable)
- [`array.new<type>()`](#arraynewtype)
- [`array.percentile_linear_interpolation()`](#arraypercentilelinearinterpolation)
- [`array.percentile_nearest_rank()`](#arraypercentilenearestrank)
- [`array.percentrank()`](#arraypercentrank)
- [`array.pop()`](#arraypop)
- [`array.push()`](#arraypush)
- [`array.range()`](#arrayrange)
- [`array.remove()`](#arrayremove)
- [`array.reverse()`](#arrayreverse)
- [`array.set()`](#arrayset)
- [`array.shift()`](#arrayshift)
- [`array.size()`](#arraysize)
- [`array.slice()`](#arrayslice)
- [`array.some()`](#arraysome)
- [`array.sort()`](#arraysort)
- [`array.sort_indices()`](#arraysortindices)
- [`array.standardize()`](#arraystandardize)
- [`array.stdev()`](#arraystdev)
- [`array.sum()`](#arraysum)
- [`array.unshift()`](#arrayunshift)
- [`array.variance()`](#arrayvariance)
- [`map.clear()`](#mapclear)
- [`map.contains()`](#mapcontains)
- [`map.copy()`](#mapcopy)
- [`map.get()`](#mapget)
- [`map.keys()`](#mapkeys)
- [`map.new<type,type>()`](#mapnewtypetype)
- [`map.put()`](#mapput)
- [`map.put_all()`](#mapputall)
- [`map.remove()`](#mapremove)
- [`map.size()`](#mapsize)
- [`map.values()`](#mapvalues)
- [`matrix.add_col()`](#matrixaddcol)
- [`matrix.add_row()`](#matrixaddrow)
- [`matrix.avg()`](#matrixavg)
- [`matrix.col()`](#matrixcol)
- [`matrix.columns()`](#matrixcolumns)
- [`matrix.concat()`](#matrixconcat)
- [`matrix.copy()`](#matrixcopy)
- [`matrix.det()`](#matrixdet)
- [`matrix.diff()`](#matrixdiff)
- [`matrix.eigenvalues()`](#matrixeigenvalues)
- [`matrix.eigenvectors()`](#matrixeigenvectors)
- [`matrix.elements_count()`](#matrixelementscount)
- [`matrix.fill()`](#matrixfill)
- [`matrix.get()`](#matrixget)
- [`matrix.inv()`](#matrixinv)
- [`matrix.is_antidiagonal()`](#matrixisantidiagonal)
- [`matrix.is_antisymmetric()`](#matrixisantisymmetric)
- [`matrix.is_binary()`](#matrixisbinary)
- [`matrix.is_diagonal()`](#matrixisdiagonal)
- [`matrix.is_identity()`](#matrixisidentity)
- [`matrix.is_square()`](#matrixissquare)
- [`matrix.is_stochastic()`](#matrixisstochastic)
- [`matrix.is_symmetric()`](#matrixissymmetric)
- [`matrix.is_triangular()`](#matrixistriangular)
- [`matrix.is_zero()`](#matrixiszero)
- [`matrix.kron()`](#matrixkron)
- [`matrix.max()`](#matrixmax)
- [`matrix.median()`](#matrixmedian)
- [`matrix.min()`](#matrixmin)
- [`matrix.mode()`](#matrixmode)
- [`matrix.mult()`](#matrixmult)
- [`matrix.new<type>()`](#matrixnewtype)
- [`matrix.pinv()`](#matrixpinv)
- [`matrix.pow()`](#matrixpow)
- [`matrix.rank()`](#matrixrank)
- [`matrix.remove_col()`](#matrixremovecol)
- [`matrix.remove_row()`](#matrixremoverow)
- [`matrix.reshape()`](#matrixreshape)
- [`matrix.reverse()`](#matrixreverse)
- [`matrix.row()`](#matrixrow)
- [`matrix.rows()`](#matrixrows)
- [`matrix.set()`](#matrixset)
- [`matrix.sort()`](#matrixsort)
- [`matrix.submatrix()`](#matrixsubmatrix)
- [`matrix.sum()`](#matrixsum)
- [`matrix.swap_columns()`](#matrixswapcolumns)
- [`matrix.swap_rows()`](#matrixswaprows)
- [`matrix.trace()`](#matrixtrace)
- [`matrix.transpose()`](#matrixtranspose)

---

## array.abs()

Returns an array containing the absolute value of each element in the original array.
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

## matrix.elements_count()

The function returns the total number of all matrix elements.
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
