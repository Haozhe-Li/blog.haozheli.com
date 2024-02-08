# File I/O in C

### Introduction
In C, file I/O (Input/Output) is facilitated through functions provided by the `stdio.h` library. Files are treated as byte streams, and operations can be performed on them using functions that manipulate these streams represented by `FILE*` types.

### Opening and Closing Files
- **fopen**: Opens a file and returns a file pointer.
  ```c
  FILE *fopen(const char *restrict pathname, const char *restrict mode);
  ```

- **fclose**: Closes a file.
  ```c
  int fclose(FILE *stream);
  ```

### Reading from Files
- **fread**: Reads data from a file.
  ```c
  size_t fread(void *restrict ptr, size_t size, size_t nmemb, FILE *restrict stream);
  ```

- **fgets**: Reads a string from a file.
  ```c
  char *fgets(char *restrict s, int n, FILE *restrict stream);
  ```

### Writing to Files
- **fwrite**: Writes data to a file.
  ```c
  size_t fwrite(const void *restrict ptr, size_t size, size_t nmemb, FILE *restrict stream);
  ```

- **fputs**: Writes a string to a file.
  ```c
  int fputs(const char *restrict s, FILE *restrict stream);
  ```

### Manipulating File Pointers
- **ftell**: Returns the current position of the file pointer.
  ```c
  long ftell(FILE *stream);
  ```

- **fseek**: Sets the file position indicator.
  ```c
  int fseek(FILE *stream, long offset, int whence);
  ```

- **rewind**: Resets the file position indicator to the beginning of the file.
  ```c
  void rewind(FILE *stream);
  ```

### Example Usage
```c
#include <stdio.h>

int main() {
    FILE *file = fopen("example.txt", "r");
    if (file == NULL) {
        perror("Error opening file");
        return -1;
    }
    
    char buffer[255];
    fgets(buffer, 255, file);
    printf("Read from file: %s\n", buffer);

    fclose(file);
    return 0;
}
```

### Further Reading
- [stdio(3) - Linux manual page](#)

This information is part of the [Systems Encyclopedia](#), a resource for foundational systems knowledge under the Creative Commons BY-NC-SA 4.0 International license.