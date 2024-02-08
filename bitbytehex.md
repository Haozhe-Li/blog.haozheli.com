# Bits, Bytes, and Composite Values

## 1. Bits
- Digital computers utilize binary digits (**bits**) with two distinguishable states: 0 and 1.
- Common representations include {0, 1} or {False, True}.
- **Binary digits** serve as the foundational unit for digital data representation and processing.

## 2. Binary integers
- Binary integers employ a base-2 number system with values {0, 1}.
- Representation involves place-value numbers.
- Negative numbers are often represented using **two's complement** notation.

### Coding Example (C):
```c
int binary = 0b101010; // Binary literal representation
```

## 3. Base 16 and Base 256
- **Base-16 (hexadecimal)** and **base-256** systems aid in compactly representing binary data.
- Hexadecimal uses digits {0-9, A-F}.
- Base-256 is commonly represented in **bytes** or **octets**.

### Coding Example (C):
```c
int hex_num = 0xA1F; // Hexadecimal literal representation
```

## 4. Power-of-1024 suffixes
- Power-of-1024 suffixes denote binary multiples such as **KiB (Kibibyte)**, **MiB (Mebibyte)**, **GiB (Gibibyte)**, etc.
- Suffixes clarify powers of 2, distinguishing them from powers of 10.

## 5. Composition through adjacency
### 5.1 Structures
- **Structures** store multiple values sequentially.
- Static structures maintain a fixed order, while **discriminant unions** may vary based on initial values.

### 5.2 Arrays
- Arrays are lists stored sequentially.
- Arrays may have **static length**, **stored length**, or **sentinel values** indicating the end.

### 5.3 Case study: UTF-8 char *
- Strings in C are stored as **char pointers** with a sentinel value (byte 0) indicating the end.
- UTF-8 encoding utilizes multi-byte structures to represent Unicode characters.

### 5.4 Multi-byte numbers and Endianness
- Numbers larger than a byte are stored in **adjacent memory** locations.
- **Endianness** determines the byte order: **big-endian** or **little-endian**.
- Different data types are stored in memory accordingly.

## 6. Composition with Pointers
- Memory and files are represented as arrays of bytes.
- **Pointers** store addresses of data in memory.
- Pointers are themselves multi-byte numbers, subject to **endianness**.

## 7. Functions
### 7.1 Serialization
- Serialization converts data into a compact byte sequence for storage or transmission.
- Objectives include efficiency, compactness, readability, and generality.

### 7.2 Compression
- **Lossless compression** reduces the size of data without loss of information.
- **Lossy compression** sacrifices some data fidelity for further compression.

### 7.3 Encryption
- Encryption transforms data into a non-readable form using a secret key.
- Common encryption functions use a secret key to encrypt and decrypt data securely.