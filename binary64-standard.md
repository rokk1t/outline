---
tags:
- ComputerScience/IEEE754
- ComputerScience/FloatingPoint
---
# IEEE-754 Standard for Floating-Point Arithmetic

Definition: Стандарт представления чисел с плавающей запятой в двоичном виде

- Using:
	- C/C++ DT
		- `float`
		- `double`
	- Java
	- Python
	- Processors
		- x86
		- ARM

## Binary interchange formats | ?

- binary16 | half
	- Total | Всего: 16 b
	- Sign | Знак: 1 b
	- Exponent | : 5 b
	- Explicit significand: 10 b
- binary32 | single
	- Total: 32 b
	- Sign: 1 b
	- Exponent: 8 b
	- Explicit significand: 23 b
	- Precision: 24 b
	- C, C++: `float`
- binary64 | double

### binary64 standard

- Total: 64 b
	- Sign (of number): 1 b
		- `0`: +
		- `1`: -
	- Exponent (base-2): 11 b
		- Values: `0b00000000000`..`0b11111111111` | 0..2047
			- Special Values
				- `0b00000000000` | 0: zero or subnormal number
				- `0b11111111111` | 2047: Infinity OR NaN (Not a Number)
			- Normal Values
				- `0b00000000001`..`0b11111111110` | 1..2046
	- Explicit Significand | Явная значащая часть (Mantissa): 52 b
	- Precision | Точность: 53 b
		- Hidden: 1 b with value = 1 for normal and 0 for subnormal numbers
- C, C++: `double` (DOUBLE precision) data type

The real exponent 0 is encoded as `0b01111111111` | 1023. This simplifies the processor logic.

- Stored Exponent - Bias = Real Exponent
	- E.g., for 2^0. 1023 - 1023 = 0
- Real Exponent + Bias = Stored Exponent
	- E.g., for 2^0. 0 + 1023 = 1023

- Bias (of exponent) | смещение = 2^(exponentbits - 1) - 1
- `double` bias = 2^(11 - 1) - 1 = 1023 | `0b01111111111`
	- exponentbits = 11

- Constants:
	- Real Exponent Min = -1022. Stored as `0b00000000001` | 1
	- Real Exponent = 0. Stored as `0b01111111111` | 1023
	- Real Exponent Max | 1023. Stored as `0b11111111110` | 2046

- Numbers for `double` are encoded as:
	- `number = Mantissa * 2^n`

- E.g., for:
	- 8 | `0b1000`
	- Encoded view: `1.0 * 2^3`
	- Sign: `0b0`. +
	- Exponent: `0b10000000010`. 1026 = 1023 + 3 = doublebias + 3
	- Mantissa: `0b(1)0000000000000000000000000000000000000000000000000000`
		- Hidden: (1)
	- Total: `0b010000000010(1)0000000000000000000000000000000000000000000000000000`

- Range controlled by exponent
- Precision controlled by mantissa

#### Integer Value

- Integer range for recording exact value:
	- `0..2^53`: range for integers divisible by `2^0`
		- $\text{Integer Value} = \frac{\text{Integer}}{2^n}$
			- where n = 0..53
	- `2^53..2^54`: range for integers divisible by `2^1`
	- `2^54..2^55`: range for integers divisible by `2^2`
	- `2^n..2^(n+1)`: range for integers divisible by `2^(n-52)`
	- `2^1022..2^1023`: range for integers divisible by `2^970`
		- For example, integer = 2, then `integer^n = 2^n, where -1022 <= n <= 1023`

`step = 2^(max(n, -1022) - 52)`, where `n = floor(log2|x|)` (Between which powers of 2 is the integer?)

- Rounding:
	- `3^40 = 12157665459056928801`
		- `0(+)_10000111110(63)_(1)0101000101110001011010001010010001010010001111111101_(00000100001)`
	- `? = 12157665459056928768`
		- `0(+)_10000111110(63)_(1)0101000101110001011010001010010001010010001111111101_(00000000000)`

Note: min 15 digits of precision are preserved

### float.exposed

- <https://float.exposed/0x4020000000000000>
	- Value: `8.0`
		- `.0` is added for create `double` dt
	- Bit Pattern: `0b0100000000100000000000000000000000000000000000000000000000000000`
	- Raw Hexadecimal Integer Value: `0x4020000000000000`
	- Raw Decimal Integer Value: `4620693217682128896`
	- Hexadecimal Form ("%a"): `0x1p+3 == 1.0 * 2^3`
		- Equivalent `1e+3 = 10^3`
	- Position within Significand–Exponent Range
	- Evaluation in Base-2 =
		`(−0b1)^0b0 * 0b​10^(0b10000000010 − 0b01111111111)​ * 0b​1.0000000000000000000000000000000000000000000000000000 =`
		`(−1)^0 * 2^(1026-1023) * 1.0 =`
		`= (-1)^Sign * 2^((bias+exponent)-bias) * 1.ExplicitSignificand`

## Other formats

`bfloat16`

## Footer

- Little Dictionary
	- Explicit significand | Mantissa: Значащая часть числа с плавающей запятой
	- Implicit Bit: Неявный бит единицы перед двоичной запятой.
	- Exponent: показатель степени
	- NaN (Not a Number)
- External Links
	- <https://float.exposed/>: Visualisator
	- <https://www.rapidtables.com/convert/number/binary-to-decimal.html>
- Internal Links
	- [[Two's complement]]
