# Strings in C

## Introduction
C does not have an explicit string type. Instead, strings are represented as character arrays terminated with a null byte (`\0`). All character arrays may not be considered strings, but any contiguous and null-terminated buffer of characters behaves like a string.

## Initialization
Strings in C can be declared and initialized in various ways:

1. Using a char pointer to point to a string literal in read-only memory:
    ```c
    char* s = "CS@UIUC";
    ```

2. Initializing a char array on the stack using a string literal:
    ```c
    char s2[8] = "CS@UIUC";
    ```

3. Initializing a char array on the stack using an array literal:
    ```c
    char s3[8] = {'C','S','@','U','I','U','C','\0'};
    ```

4. Dynamically allocating memory for a string and then writing a string literal:
    ```c
    char* s4 = malloc(8);
    strcpy(s4, "CS@UIUC");
    ```

5. Using `strdup` to create a duplicate of a string:
    ```c
    char* s5 = strdup("CS@UIUC");
    ```

## String Representation in Memory
Regardless of how a string is initialized, its representation in memory involves a sequence of characters terminated by a null byte.

## String Functions in `string.h`

### Comparison and Length
- `strcmp`: String comparison function, returns 0 if equal, 1 if the first string is greater, and -1 if the second string is greater.
    ```c
    int c1 = strcmp("A", "A");
    int c2 = strcmp("AB", "BA");
    int c3 = strcmp("BA", "AB");
    ```

- `strncmp`: Compares the first n bytes of two strings.

- `strlen`: Returns the length of a string.

### Concatenation
- `strcat`: Concatenates two strings.
    ```c
    char c[24] = "I love ";
    strcat(c, "systems!");
    ```

- `strncat`: Concatenates the first n bytes of two strings.

### Search Functions
- `strchr`: Finds the first instance of a character in a string.
    ```c
    char s[8] = "ABCDEFG";
    char* c = strchr(s, 'B');
    ```

- `strrchr`: Finds the last instance of a character in a string.

- `strstr`: Finds the first occurrence of a substring in a string.

### Copying and Allocating Strings
- `strcpy`: Copies the contents of one string to another.
    ```c
    char* dest = malloc(4);
    strcpy(dest, "ABC");
    ```

- `strncpy`: Copies the first n characters of one string to another.

- `strdup`: Creates a duplicate of a string and allocates memory for it.

### Tokenization
- `strtok`: Tokenizes a string using a delimiter.

## Common Pitfalls
- Forgetting the null byte can lead to undefined behavior.
- Buffer overflows can occur if functions like `strcpy` are misused.
- Changing read-only memory can result in segmentation faults.
