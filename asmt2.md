---
print_background: true
export_on_save:
    html: true
puppeteer:
    format: "Letter"
    timeout: 3000
---

# Assignment 2

## *Problem 1* (1.5 points) (Show all intermediate steps. No intermediate steps will receive 0 point)

### Convert integer -3 to 8 digit TC Binary.  (0.5 point)

First, convert $3$ to binary: $3 = 2^1 + 2^0=$ `0b 0000 0011`.

Then negate it:

```
    0b 0000 0011    (3 in binary)
    0b 1111 1100    (flip bits)
  + 0b 0000 0001    (add one)
  ---------------
    0b 1111 1101    (-3)
```

$-3$ in an 8-bit two's complement binary is `0b 1111 1101`.

### Convert decimal -1 to 8 digit TC Hex. (0.5 point)

First, convert $1$ to hexadecimal: $1 = 1(16^0) =$ `0x 0000 0001`.

Then, negate it:

```
    0x FFFF FFFF
  - 0x 0000 0001    (1 in hex)
  ---------------
    0x FFFF FFFE    (subtract from 0x FFFF FFFF)
  + 0x 0000 0001    (add one)
  ---------------
    0x FFFF FFFF    (-255)
```

$-1$ in an 8-digit two's complement hexadecimal is `0x FFFF FFFF`.

### Convert integer -255 to 8 digit Hex (Hint: You can either convert 255 to Hex then negate with TC Hex rule, or you can convert -255 to TC Bin, then convert it to Hex) (0.5 point)

I'm doing the former, so: $255 = 15(16^1) + 15(15^0) = $ `0x 0000 00FF`.

```
    0x FFFF FFFF
  - 0x 0000 00FF    (255 in hex)
  ---------------
    0x FFFF FF00    (subtract from 0x FFFF FFFF)
  + 0x 0000 0001    (add one)
  ---------------
    0x FFFF FF01    (-255)
```

$-255$ in an 8-digit two's complement hexadecimal is `0x FFFF FF01`.

## *Problem 2* Convert the 2-digit two's complement hexadecimal integer 0x6e to decimal. Show all intermediate steps clearly. (0.5 point)

First, we note that `0x6e` is a positive integer because the leading digit here is less than eight. So, we can just convert it to decimal where `E` correspond to $14$.

As such, `0x6e` $=6(16^1) + 14(16^0) = 110$.

## *Problem 3* Convert the decimal integer -61 to an 8-bit two's complement binary integer.  Show all intermediate steps clearly. (0.5 point)

First, convert $61$ into hexadecimal: $61 = 3(16^1) + 13(16^0)=$ `0x 0000 003D`.

Using a reference table, we convert `0x 0000 003D` to binary: `0b 0011 1101`.

|  Dec  |  Bin   |  Hex  |
| :---: | :----: | :---: |
|  $3$  | `0011` |  `3`  |
| $13$  | `1101` |  `D`  |


Then, negate it.

```
    0b 0011 1101    (61 in binary)
    0b 1100 0010    (flip bits)
  + 0b 0000 0001    (add one)
  ---------------
    0b 1100 0011    (-61)
```

$-61$ in an 8-bit two's complement binary is `0b 1100 0011`.

## *Problem 4* You're given two 4-digit, 2's complement hexadecimal numbers X = `0xa731` and Y = `0xe6a2`. Compute X-Y. Remember to indicate overflow if it occurs. Show all intermediate steps clearly. (1 point)

First, negate $Y$ to find $-Y$.

```
    0x FFFF
  - 0x E6A2     (Y)
  ----------
    0x 195D     (subtract from 0x FFFF)
  + 0x 0001     (add one)
  ----------
    0x 195E     (-Y)
```

Then, $X-Y = X+(-Y)$. So:

```
       1
    0x A731     (X)
  + 0x 195E     (-Y)
  ----------
    0x C08F
```

In a 4-digit two's complement hexadecimal system, $X-Y=$ `0x C08F`.

### Sanity check

|         |   $X$    |   $Y$   |  $-Y$  |  $X-Y$   |
| ------- | :------: | :-----: | :----: | :------: |
| **Hex** |  `A731`  | `E6A2`  | `195E` |  `C08F`  |
| **Dec** | $-22735$ | $-6494$ | $6494$ | $-16241$ |

$$
\begin{align*}
    X - Y &= -22735 - (-6494) \\
    &= -22735 + 6494 \\
    &= X + (-Y) \\
    &= -22735 + 6494 \\
    &= -16241
\end{align*}
$$
