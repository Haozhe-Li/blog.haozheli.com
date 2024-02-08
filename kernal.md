## Kernel Mode

### 1. System Calls: Explicit Requests to the Kernel

- **System Calls**: Mechanism for user mode code to request kernel mode operations.
- C standard library provides wrapper functions for system calls like `open`, `read`, `write`, and `close`.
- Each operating system has its own set of system calls, implemented using assembly's system call instruction.
- File descriptors: Numeric indices representing communication or storage interfaces, managed by the kernel.
- Blocking system calls suspend program execution until requested data is available.

### 1.1 File Descriptors

- **File Descriptors**: Non-negative integers representing communication or storage interfaces.
- Commonly used for files, terminals, network connections, etc.
- Operations include read, write, and seek, with the latter adjusting the file offset.
- Default file descriptors in C: stdin (0), stdout (1), stderr (2).
- Pipes: Utilized for connecting standard input and output of command-line programs.

### 1.2 FILE *

- **FILE ***: Recommended file handling method in C, providing buffered I/O.
- Opaque pointer containing information about the file and a buffer for efficient I/O operations.
- Standard library functions like `fopen`, `fwrite`, `fread`, etc., operate on FILE pointers.
- Buffered I/O reduces system calls, enhancing performance.

### 2. Invisible Context Switches

- **Context Switches**: Occur when code transitions between user mode and kernel mode.
- Reasons for context switches include faults (e.g., accessing unallocated memory) and interrupts (e.g., keypresses).
- Faults and interrupts are handled by the kernel, often resulting in context switches.
- Page faults occur when accessing unallocated memory pages, managed by the operating system.
- Timer interrupts occur frequently for system maintenance and task scheduling.

### Conclusion

- Kernel mode enables privileged operations inaccessible from user mode.
- System calls provide a bridge between user and kernel modes for operations like file I/O.
- Understanding context switches is crucial for efficient system programming and debugging.
