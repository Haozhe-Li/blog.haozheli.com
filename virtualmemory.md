# Virtual Memory

## 1. Pretend I’m alone

- Virtual memory allows programs to operate as if they have **exclusive access to memory**.
- Each program has its own virtual address space, **isolating it from others**.
- Hardware implements memory accesses using virtual addresses, which are **translated** to physical addresses.

## 2. Hide the hardware

- Programs can use memory **without** needing to know the total system memory.
- Virtual memory provides the illusion of abundant memory by utilizing disk space as **swap space**.
- Although **slower** than main memory, this allows programs to continue execution **without crashing**.

## 3. Address translation

- Virtual memory relies on **address translation** to map virtual addresses to physical addresses.
- **Pages:** Memory is divided into pages, typically **4KiB**, with each address split into **page number** and **page offset**.
- Translation involves mapping virtual page numbers to physical page numbers.

### 3.1 Pages

- Memory is organized into pages, with each page having its own **page number** and **offset**.
- Address translation **only affects page numbers**, preserving spatial locality and reducing translation overhead.

### 3.2 Sparse arrays

- Translation utilizes a multi-level page table, a **tree-like structure** storing sparse arrays.
- Each node in the tree corresponds to a **page of memory**, with **fixed height** and **keys** represented by **virtual page numbers**.
- The structure is stored in **physical memory** with large nodes fitting one page per node.

## 4. Pages and Segments

- The **operating system** manages mapping of virtual addresses to physical addresses.
- Memory allocation occurs in three steps:
  1. **Segmentation:** Allocating **segments** for **stack, heap**, etc., to prevent memory hogging.
  2. **Initialization:** Setting up virtual memory mappings and contents during program loading.
  3. **Dynamic mapping:** Adding mappings for accessed addresses, handling segmentation violations or bus errors.
