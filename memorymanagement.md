# Memory Management

## 1. Globals

- **Global memory** is allocated once when the program is **loaded** and **remains unchanged** thereafter.
- Global memory is divided into several regions:
  - **Code:** **Executable** but not directly **accessible**.
  - Read-only globals: Includes **string literals**.
  - Normal globals: **Variables declared outside of functions** and **static variables declared inside functions**.

## 2. The Stack

- Managed **automatically** by the **compiler** and linked to function calls.

- **New function activation records** (arguments, return value, return address, local variables) are pushed onto the stack upon function invocation and popped off upon return.

- Common bugs:
  - **Use after return:** Pointer to stack memory outlives the function, causing incorrect behavior. To avoid this, allocating memory to heap.
  
    ````c
    #include <stdio.h>
    
    int* create_array(int size) {
        int array[size];
        for (int i = 0; i < size; i++) {
            array[i] = i;
        }
        return array;
    }
    
    int main() {
        int* ptr = create_array(5);
        printf("First element: %d\n", ptr[0]); // Use after return here, will cause undefined behavior
        return 0;
    }
    
    ````
  
    
  
  - **Stack overflow:** Too much data or deep recursion exhausts the stack segment allocated by the OS.

## 3. Heap, level 0: sbrk

- Initially **small or empty segment** of memory storing the heap.
- The b**eginning is fixed**, while the **end** can be adjusted by the OS.
- `sbrk` is commonly used to **request changes** in **heap size** by specifying a delta in bytes.

## 4. Heap, level 1: malloc and friends

- `malloc`, `free`, `calloc`, and `realloc` use `sbrk` to request heap memory and manage their own bookkeeping.
- Common features of `malloc` implementations:
  - **Bookkeeping** data stored before pointers returned by `malloc`.
  - Preference for reusing freed memory.
  - Strategies to manage and reduce fragmentation.
- In C++, `new` and `delete` wrap `malloc` and `free` respectively, also invoking constructors and destructors.

## 5. Heap, level 2: tracking lifetimes

- Memory management with `malloc` can lead to errors such as:
  - Memory leaks
  - Use after free
  - Double free
- Techniques to avoid errors:
  - **Lifetimes:** Tracking when pointers should be freed.
  - **Reference counting:** Incrementing/decrementing counters to manage lifetimes.
  - **Ownership tracking:** Enforcing ownership rules at the language level.

## 6. Heap, level 3: garbage collection

- Garbage collectors identify and free **allocated heap memory** that will **never be used again**.
- **Unreachable memory** is a subset of garbage.
- Garbage collectors trade off **performance** and **memory** constraints for ease of use in code writing.
- Common in high-level languages like Java, Python, and JavaScript.
- Not present in languages like Rust due to ownership tracking or C/C++ unless third-party libraries are used.

**Note:** Restyle © 2024-02-06 Luther Tychonievich. This work is licensed under a Creative Commons Attribution-NonCommercial 4.0 International License.