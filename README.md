# Operating Systems 2024-1 Assignments

## Assignment 01: xv6 System Call

### System Call Handling in xv6

xv6 handles system calls through traps. When a system call is triggered, the CPU executes the INT instruction to generate a trap. The `usys.S` file uses the INT instruction to handle system calls.

- **Trap and System Call Numbers**
  - Numbers for each trap are defined in `traps.h`, and numbers for system calls are defined in `syscall.h`.

- **Processing INT n Instruction**
  - Manages the values of registers eip and esp, and invokes the trap handler from the IDT.

- **Interrupt Descriptor Table (IDT)**
  - Initialized in `trap.c`, the IDT contains entries for handling traps and interrupts.

- **Vector Table**
  - Defined in `vectors.S`, system call vectors jump to `alltraps` which handles the trap.

- **Trap Frame and Trap Function**
  - `trap.c` checks the trap number and calls the `syscall` function if it matches `T_SYSCALL`.

- **syscall Function**
  - In `syscall.c`, the syscall function uses a function pointer array to call the appropriate system call functions.

### Assignment 01: Implementing a New System Call

**Implementing the `getppid` System Call:**
- Implement the `getppid` system call, which returns the PID of the parent process.
- Refer to the `getpid` system call in `sysproc.c`.

**API Definition:**
- Declare the `getppid` system call in `user.h`.
- Define the `getppid` macro in `usys.S`.
- Define the `getppid` number in `syscall.h`.
- Add the `getppid` pointer to the syscall function pointer array in `syscall.c`.
- Implement the `sys_getppid` function in `sysproc.c`.

---

## Assignment 02: xv6 File System

### xv6 File System Structure and Operation

xv6 implements a simple UNIX-like file system. Understanding its structure and operation is key.

- **Disk and File System Initialization**
  - Initialized in `fs.c`, which sets up the disk and file system.

- **File System Structure**
  - **Superblock:** Contains metadata about the file system.
  - **Inode:** Manages metadata about files and the location of data blocks.
  - **Data Blocks:** Store the actual file data.

- **File System Functions**
  - Basic file system functions (read, write, file creation, etc.) are implemented in `fs.c`.

### Assignment 02: Extending File System Features

**Adding File System Features:**
- **Directory Listing:** Implement a feature to list the contents of a directory.
- **File Size Retrieval:** Implement a system call to return the size of a file.

**API Definition and Implementation:**
- Implement new system calls in **`sysfile.c`**.
- Declare functions for user space calls in **`user.h`**.

---

## Assignment 03: xv6 Scheduling

### xv6 Scheduling Algorithms

xv6 uses a basic round-robin scheduling algorithm to manage processes. Understanding how scheduling algorithms work is essential.

- **Scheduling Algorithm Overview**
  - **Round-Robin:** Allocates CPU time to processes in a circular order to ensure fairness.

- **Scheduling Implementation**
  - Implemented in `proc.c`, which contains scheduling-related functions.

### Assignment 03: Improving Scheduling Algorithms

**Modifying the Scheduling Algorithm:**
- **Priority-Based Scheduling:** Add functionality to allocate CPU based on process priority.
- **Multilevel Queue Scheduling:** Implement a multilevel queue system to improve scheduling based on process execution history.

**API Definition and Implementation:**
- Implement priority-based and multilevel queue scheduling in **`proc.c`**.
- Declare functions for scheduling information in **`user.h`**.

