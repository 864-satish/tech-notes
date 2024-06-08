# 📖 Bit manipulation

#### All explanation are on 4-bit representation [N = 4]


## 🚀 Common Bitwise operations

1. `AND (&)`: AND on each bits; Example: `1101 & 1011 = 1001`.

2. `OR (|)`: OR on each bits; Example: `1101 | 1011 = 1111`.

3. `XOR (^)`: XOR (Odd one detector) on each bits. Example:` 1101 ^ 1011 = 0110`.

4. `NOT (~)`: Inverts each bits; Example: `~1101 = 0010`.

5. `NAND`: AND then Negates the result; Example: `1101 & 1011 = 1001, then ~1001 = 0110`.


## 🚀 Understanding the operations manually with examples

1. `0110 + 0110 = 0110 * 2 => 1100` equivalent to shifting left by 1 (`num << 1`)
2. `0100 * 0011 = 4 * 0011 => 1100` equivalent to shifting left by 2 (`num << 2`)
3. `1101 ^ (~1101) = 1111` XOR a bit with it's own negated value will always get 1 (`num ^ (~num) = 1111`) 
4. `1011 & (~0 << 2) = 1000` ~0  negating series of zeros = 1111 and then left shift by 2 and performing AND will clear the last 2 bits.


## 🚀 Bit Facts and Tricks [performing operation on a]

```bash
a ^ 0s = a          a & 0s = 0          a | 0s = a
a ^ 1s = ~a         a & 1s = a          a | 1s = 1s
a ^ a = 0           a & a = a           a | a = a
```
## 🚀 Two's compliment and Negative numbers
- 2's compliment of a = 2<sup>N</sup> - a
- Most significatn bit represent sign of number [1 = negative, 0 = positive]
- -a can be represented as concat(1, 2<sup>N</sup> - a)

## 🚀 Arithmetic `[>>]` and Logical `[>>>]` right shift
1. Arithmetic right shifts the value but put the SIGN bit at most significant plac
   It has rougly the value devided by 2.
   Example:  -75 >> 1 = -38

2. Logical right shifts the value and puts the ZERO at most significant place.
    Example -75 >>> 1 = 90

## 🚀 Common Bit tasks | Getting, Setting bit from a number num

- **Get** i<sup>th</sup> bit = `num & (1 << i) != 0`
- **Set** i<sup>th</sup> bit = `num | (1 << i)`
- **Clear** 
    - i<sup>th</sup> bit `mask = ~(1 << i), return num & mask` 
    - clear all bits from most significant to i<sup>th</sup> inclusive
    `mask = (1 << i - 1) [sequence of 1s], return num & mask` 
    - clear all bits from i<sup>th</sup> to 0 inclusive
    `mask = -1 << (i + 1), return num & mask` 
     -1 [is sequence of 1s] left shift by i+1, give last i bits zeros
    
- **Update** i<sup>th</sup> bit to a value b = ` num & ~(1 << i) | (v << i)`
    1. Clear the ith bit `num = num & ~(1 << i)` and then
    2. Put v to the ith bit `num | (v << i)`




Ref: Cracking the Coding Interview