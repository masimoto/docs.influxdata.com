---
title: covariance() function
description: placeholder
menu:
  flux_0_7:
    name: covariance
    parent: Functions
    weight: 1
---

The `covariance()` function computes the covariance between two columns.

_**Function type:** aggregate_  
_**Output data type:** float_

```js
covariance(columns: ["column_x", "column_y"], pearsonr: false, valueDst: "_value")
```

## Parameters

### columns
A list of columns on which to operate.

_**Data type:** array of strings_

> Exactly two columns must be provided to the `columns` property.

### pearsonr
Indicates whether the result should be normalized to be the Pearson R coefficient.

_**Data type:** boolean_

### valueDst
The column into which the result will be placed. Defaults to `"_value"`.

_**Data type:** string_

## Examples
```js
from(bucket: "telegraf/autogen")
  |> range(start:-5m)
  |> covariance(columns: ["x", "y"])
```