## 1. Bitwise Boolean Operators
- Bitwise Boolean operators are fundamental operations used to manipulate individual bits within integers in programming languages. These operators treat integers as sequences of bits and perform operations on corresponding bits.

| Operator | Meaning             | Example                         |
| -------- | ------------------- | ------------------------------- |
| ~        | Bitwise NOT         | ```~ 1100``` → ```0011```       |
| \|       | Bitwise OR          | ```1100 \| 0110``` → ```1110``` |
| &        | Bitwise AND         | ```1100 & 0110``` → ```0100```  |
| ^        | Bitwise XOR         | ```1100 ^ 0110``` → ```1010```  |
| >>       | Bitwise right shift | ```1100 >> 2``` → ```0011```    |
| <<       | Bitwise left shift  | ```1100 << 2``` → ```110000```  |

- When shifting, bits that no longer fit within the number are dropped, and new bits are added to maintain the number of bits. For left shifts, new bits are always zeros. For right shifts, it depends on the language and datatype, with some languages performing sign-extending shifts for signed integers and zero-extending shifts for unsigned integers.

### Example in C:
```c
#include <stdio.h>

int main() {
    // char is an 8-bit integer datatype
    signed char x = 0b10100101;
    unsigned char y = 0b10100101;
    
    printf("Signed char right shift result: %d\n", x >> 2);
    printf("Unsigned char right shift result: %d\n", y >> 2);

    return 0;
}
```

Output:
```
Signed char right shift result: -23
Unsigned char right shift result: 37
```

- In this example, the right shift operation is performed on both signed and unsigned char variables in C, demonstrating the difference in behavior based on data type.

## 2. Masks
- A bit mask, often represented as a hexadecimal value, is used to select specific bits from another value. Bit masks are commonly used in conjunction with bitwise AND (&) operations to extract particular bits from a value.

- Bit mask constants are typically written in hexadecimal notation, with sequential bits set to 1 and all others set to 0.

### Example:
- Consider a bit mask `0x3ffe0`, which selects 13 bits, ranging from the 5th least significant bit to the 17th.

```plaintext
Binary:    0011 1111 1111 1110 0000
```

- Bit mask values can also be computed using shifts and negations to create masks of desired lengths and positions.

## 3. Bit Terminology
- When discussing sequences of bits, several terms are commonly used:
    - **Bit Vector**: A fixed-length sequence of bits, manipulated primarily by bitwise operations.
    - **Clear**: To set a bit to 0, or a noun indicating the absence of 1s.
    - **ith bit**: The bit position, usually counting from least to most significant starting at 0.
    - **Set**: To set a bit to 1, or an adjective indicating the presence of a 1.
    - **Zero**: The opposite of 1 in a single bit or a bit vector of all 0 bits.

## 4. Flags and Bitvectors as Sets
- Bit manipulation is often used to represent sets of Boolean values efficiently. Each possible element in the set is assigned a unique bit within a number, and bitwise OR operations are used to represent sets containing multiple elements.

- Single-set-bit values are called flags, and a set represented by the bitwise OR of flags is referred to as the flags.

### Set Operations Using Bitwise Operators:
- Membership: `a ∈ x` can be checked using `(A & x) != 0`.
- Union: `{a} ∪ x` is achieved with the bitwise OR operation, `A | x`.
- Set Difference: `x ∖ {a}` can be computed as `x & ~A`.

## 5. Bit-fiddling
- Bit-fiddling refers to the practice of using sequences of bitwise operations to achieve various bit-level transformations of values. While often considered low-level and sometimes confusing, bit-fiddling can offer significant memory or speed benefits in specific situations.

- Example: Computing the parity of a 32-bit vector `x` using bitwise XOR operations.

```c
unsigned int parity = 0;
for (int i = 0; i < 32; i++) {
    parity ^= (x & 1);
    x >>= 1;
}
```

- More efficient method:
```c
x ^= (x >> 16);
x ^= (x >> 8);
x ^= (x >> 4);
x ^= (x >> 2);
x ^= (x >> 1);
unsigned int parity = x & 1;
```

- Bit-fiddling often involves finding shortcuts and tricks to optimize operations, although it may not always be favored by software engineers due to its complexity and potential for errors.

Now, let's consider the code `x ^= y; y ^= x; x ^= y;`.