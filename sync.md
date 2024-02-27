# Synchronization Notes

## 1. Atomic Operations

- **Definition**:
  - Key concept in lock-free data structures.
  - Guarantees exclusive access to resources during operation.
  - Less efficient than non-atomic operations.

- **Common Atomic Operations**:
  1. **Test-and-set**:
     - Sets a bit in memory to 1 and returns if it was changed.
  2. **Compare-and-set**:
     - Modifies a value only if it had a specific previous value.
  3. **Atomic modification operations** (e.g., +=):
     - Guarantees no race conditions between loading and writing.

## 2. Synchronization Primitives

- **Properties**:
  - Pair opaque data with functions/methods operating on it.
  - Define rules for threads to block until certain conditions are met.

### 2.1 Lock

- **Definition**:
  - Two states: locked and unlocked.
  - Methods: acquire and release.

- **Usage**:
  - Implement mutual exclusion with critical sections.

### 2.2 Condition Variable

- **Definition**:
  - Temporary release mode for locks.
  - Methods: wait, notify, and notify_all.

- **Usage**:
  - Useful for waiting until complex conditions are met.

### 2.3 Reader-writer Lock

- **Definition**:
  - Supports shared (read) and exclusive (write) modes.
  - Allows multiple readers or one writer.

- **Usage**:
  - Common in file systems.
  - Implemented using condition variables and counts.

### 2.4 Semaphore

- **Definition**:
  - Allows more than one thread to lock it at a time.
  - Can implement most other synchronization primitives.

- **Usage**:
  - Rarely used outside historical or OS contexts.

### 2.5 Barrier

- **Definition**:
  - Blocks until several threads are ready to pass.
  - All threads pass through at once.

- **Usage**:
  - Helpful in handling setup phases or collecting intermediate results.
