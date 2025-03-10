# Type Conversions

Most of the time, operators and functions automatically convert the values given to them to the right type. <br>

For example, `alert` automatically converts any value to a string to show it. Mathematical operations convert values to numbers. <br>

There are also cases when we need explicitly covert a value to the expected type. <br>

**Not talking about objects yet**

In this chaper, we won't cover objects. For now, we'll just be talking about primitives. <br>
Later, after we learn about objects, in the chapter **Object to primitive conversion** we'll soon see how objects fit in. <br>

## String Coversion

String coversion happens when we need the string form of a value. <br>

For example, `alert(value)` does it to show the value. <br>

We can also call the `String(value)` function to covert a value to a string: <br>

```
let value = true;
alert(typeof value); // Boolean

value = String(value); // now value is a string "true"
alert(typeof value); // string
```

String coversion is mostly obvious. A `false` becomes `"false"`, `null` becomes `"null"`, etc.

## Numberic Conversion

Numeric conversion in mathematical functions and expressions happens automatically. <br>

For example, when division `/` is applied to non-numbers: <br>

`alert("6" / "2"); // 3, strings are converted to numbers`

We can use the `Number(value)` function to explicitly convert a `value` to a number:

```
let str = "123";
alert(typeof str); // string

let num = Number(str); // becomes a number 123
alert(typeof num); // number
```

Explicit conversion is usually required when we read a value from a string-based source like a text form but expect a number to be entered. <br>

If the string is not a valid number, the sult of such a coversion is `NaN`. For instance:

```
let age = Number("an arbitrary string instead of a number");
alert(age); // NaN, coversion failed
```

Numeric conversion rules: <br>

| Value              | Becomes...                                                                                                                                                                                                                   |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `undefined`        | `NaN`                                                                                                                                                                                                                        |
| `null`             | `0`                                                                                                                                                                                                                          |
| `true` and `false` | `1` and `0`                                                                                                                                                                                                                  |
| `string`           | Whitespaces (includes spaces, tabs `\t`, newlines `\n` etc.) from the start and end are removed. If the remaining string is empty, the result is `0`. Otherwise, the number is “read” from the string. An error gives `NaN`. |

Examples:

```
alert(Number("   123   ")); // 123
alert(Number("123z")); // NaN (error reading a number at "z")
alert(Number(true)); // 1
alert(Number(false)); // 0
```

Please note that `null` and `undefined` behave differently here: `null` becomes zero while `undefined` becomes `NaN`. <br>

Most mathematical operators also perform such coversions, we'll see that in the next chapter. <br>

## Boolean Conversion

Boolean conversion is the simplest one. <br>

It happens in logical operations (later we'll meet condition tests and other similar things) but can also be performed explicitly with a call to `Boolean(value)`. <br>

The conversion rule:

-   Values that are intuitively "empty", like `0`, or empty string, `null`, `undefined`, and `NaN`, become `false`.
-   Other values become `true`.

For instance:

```
alert(Boolean(1)); // true
alert(Boolean(0)); // false

alert(Boolean("hello")); // true
alert(Boolean("")); // false
```

**Please note: the string with zero `"0"` is `true`**

Some languages (namely PHP) treat `"0"` as `false`. But in JavaScript, a non-empty string is always `true`.

```
alert( Boolean("0") ); // true
alert( Boolean(" ") ); // spaces, also true (any non-empty string is true)
```

# Summary

The three most widely used type conversions are to string, to number, and to boolean.

**String Conversion** – Occurs when we output something. Can be performed with `String(value)`. The conversion to string is usually obvious for primitive values.

**Numeric Conversion** – Occurs in math operations. Can be performed with `Number(value)`.

Scrimba course progress 50%
