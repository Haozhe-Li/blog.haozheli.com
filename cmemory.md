# Basic Memory Management in C

C provides a simple and direct interface for managing program memory during runtime. Here we'll provide a brief overview of C's memory model, the standard library's memory management functions, and common pitfalls new C programmers can run into when using these functions.

### C Runtime Memory Model

The C runtime memory model can be broken down into 3 separate pieces:

1. **Automatically Allocated Memory**: This section of memory consists of locally initialized variables (e.g., declaring `int i = 0` inside of any function) and function parameters. All memory allocated to these variables is automatically managed by C, meaning that you do not need to (and should not!) use any of the C stdlib's memory management functions on them. In most cases, your source code will consist of automatically managed variables.

2. **Dynamically Allocated Memory**: This consists of any memory that your program explicitly tells the operating system to allocate for it. In other words, if you use any of C's memory allocation functions, you will be dynamically allocating memory.

3. **Static/Global Memory**: Any variable declared with the `static` keyword or declared globally will exist in a separate space of memory. When this space is allocated, it is never freed during the execution of the program.

### Important stdlib Functions for Memory Management

C implements a number of functions in `stdlib.h` and `string.h` that are used to manipulate memory.

- **Memory Allocation and Data Size**: `malloc`, `calloc`, `realloc`, and `sizeof`
  ```c
  void *malloc(size_t size);
  void *calloc(size_t nmemb, size_t size);
  void *realloc(void *ptr, size_t size);
  size_t sizeof(type);
  ```

- **Deallocating Memory**: `free`
  ```c
  void free(void *ptr);
  ```

- **Copying and Modifying Memory**: `memcpy`, `memmove`, and `memset`
  ```c
  void *memcpy(void *restrict dest, const void *restrict src, size_t n);
  void *memmove(void *dest, const void *src, size_t n);
  void *memset(void *s, int c, size_t n);
  ```

### Common Pitfalls

- **Overusing `malloc`**: Dynamic allocation should mostly be used for pieces of data where the byte size of that data is unknown or for data whose lifespan needs to be preserved outside of the scope of the function it is contained inside.

- **Memory Leaks**: Always remember to free dynamically allocated memory when it is no longer needed.

- **Double Frees and Dangling Pointers**: Avoid deallocating memory that has already been deallocated, and set pointers to freed memory to `NULL` to avoid dangling pointers.

