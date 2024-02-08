# UTF-8

## 1. Unicode
- **Unicode** is an international standard mapping characters to non-negative integers called **code points**.
- Characters are represented as U+ followed by a hexadecimal code point.
- Unicode supports code points ranging from U+0000 to U+10FFFF.

### Note:
- Unicode encompasses various character categorizations and normalization algorithms.
- Detailed information can be found in the Unicode standard documentation.

## 2. Splitting bits
- **UTF-8** divides code points into 1–4 bit groups based on the number of bits required for representation.
- Groups are arranged in big-endian order.

## 3. Padding bits
- Each bit group is padded to form a full byte.
- The first byte's padding depends on the number of groups, while subsequent bytes use a common padding scheme.
- Padding ensures clear byte separation and character identification within UTF-8 encoded streams.

### Example:
```c
// Function to encode a Unicode code point to UTF-8
void encodeToUTF8(uint32_t codePoint, uint8_t *utf8Bytes) {
    if (codePoint <= 0x7F) {
        utf8Bytes[0] = (uint8_t)codePoint;
    } else if (codePoint <= 0x7FF) {
        utf8Bytes[0] = (uint8_t)(0xC0 | (codePoint >> 6));
        utf8Bytes[1] = (uint8_t)(0x80 | (codePoint & 0x3F));
    } else if (codePoint <= 0xFFFF) {
        utf8Bytes[0] = (uint8_t)(0xE0 | (codePoint >> 12));
        utf8Bytes[1] = (uint8_t)(0x80 | ((codePoint >> 6) & 0x3F));
        utf8Bytes[2] = (uint8_t)(0x80 | (codePoint & 0x3F));
    } else {
        utf8Bytes[0] = (uint8_t)(0xF0 | (codePoint >> 18));
        utf8Bytes[1] = (uint8_t)(0x80 | ((codePoint >> 12) & 0x3F));
        utf8Bytes[2] = (uint8_t)(0x80 | ((codePoint >> 6) & 0x3F));
        utf8Bytes[3] = (uint8_t)(0x80 | (codePoint & 0x3F));
    }
}
```

## 4. Combined examples
- Encoding examples illustrate the process of converting code points to UTF-8 byte sequences.
- Each example involves:
  - Writing the code point in binary.
  - Determining the number of bytes required based on the bits.
  - Splitting the bits into groups and padding them accordingly.

### Examples:
1. Encoding U+0041 (capital A)
   ```c
   uint32_t codePoint = 0x0041;
   uint8_t utf8Bytes[4];
   encodeToUTF8(codePoint, utf8Bytes);
   ```

2. Encoding U+06CD (Arabic yeh with tail, ۍ)
   ```c
   uint32_t codePoint = 0x06CD;
   uint8_t utf8Bytes[4];
   encodeToUTF8(codePoint, utf8Bytes);
   ```

3. Encoding U+2331 (dimensional origin symbol, ⌱)
   ```c
   uint32_t codePoint = 0x2331;
   uint8_t utf8Bytes[4];
   encodeToUTF8(codePoint, utf8Bytes);
   ```

4. Encoding U+12500 (cuneiform sign LAK-608, 𒔀)
   ```c
   uint32_t codePoint = 0x12500;
   uint8_t utf8Bytes[4];
   encodeToUTF8(codePoint, utf8Bytes);
   ```

### Decoding Example:
- Decoding UTF-8 byte sequences involves identifying the byte's structure and extracting the data bits to reconstruct the original code point.

### Example:
- Decoding the UTF-8 byte sequence F8 93 EA 80 B2 5C 00 to retrieve the first UTF-8 character.
