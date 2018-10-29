---
title: integral() function
description: placeholder
menu:
  flux_0_7:
    name: integral
    parent: Functions
    weight: 1
---

The `integral()` function computes the area under the curve per [`unit`](#unit) of time of subsequent non-null records.
The curve is defined using `_time` as the domain and record values as the range.

_**Function type:** aggregate_  
_**Output data type:** float_

```js
integral(unit: 10s, columns: ["_value"])
```

## Parameters

### unit
The time duration used when computing the integral.

_**Data type:** duration_

### columns
A list of columns on which to operate.
Defaults to `["_value"]`.

_**Data type:** array of strings_

## Examples
```js
from(bucket: "telegraf/autogen")
  |> range(start: -5m)
  |> filter(fn: (r) => r._measurement == "cpu" and r._field == "usage_system")
  |> integral(unit:10s)
```