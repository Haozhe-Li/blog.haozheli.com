# Concurrency Notes

## 1. Kinds of Concurrency

- **Computers**:
  - Heaviest-weight concurrency, running on separate physical computers.
  - Requires explicit message-passing protocol.

- **Processes**:
  - Run their own code, access own memory, but share OS with other processes on the same computer.
  - Communication via system calls to OS accessing shared resources.

- **Threads**:
  - Have own execution context but share memory within the same process.
  - Easy coordination but prone to accidental memory corruption due to shared memory.
  - Race conditions are common pitfalls, requiring synchronization.
  
- **Fibers**:
  - Like threads but cannot run in parallel with others.
  - Run until voluntarily relinquishing control.
  - Used in applications with frequent waiting for I/O operations.

## 2. Coding Concurrency

### 2.1 Multi-Computer Concurrency
- Applications communicate using sockets and network connections.

### 2.2 Multi-Process Concurrency
- **Fork**: Duplicates a process, creating parent and child processes.
- Communication via pipes or sockets.
- Parent process often cleans up after child process.

### 2.3 Multi-Thread Concurrency
- Parent thread spawns a child thread, giving it a function to execute.
- Threads communicate via shared memory, but synchronization is required to avoid race conditions.
- Race conditions occur when the outcome depends on the order of thread operations.
- Synchronization includes techniques like locks, condition variables, and semaphores.

### 2.4 Non-Parallel Concurrency
- **Generators**: Functions that can yield multiple values, pausing execution until next invocation.
- **Async Functions**: Run until encountering an await statement, allowing other tasks to proceed in the meantime. Managed by async schedulers.
