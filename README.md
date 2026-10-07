# Linux Memory Mapped File Management System

## Team Details

**Section:** 10
**Team:** 21

### Team Members

| **Roll Number** | **Name**        |
| --------------- | --------------- |
| 2520090122      | Savulla Rithesh |
| 2520090149      | Sai Snehith     |
| 2520090114      | Harshith        |

### Supervisor

**[Supervisor Name]**

---

## Project Overview

This project demonstrates Linux memory-mapped file management using the `mmap()` system call.

The system provides an efficient method for accessing and modifying file contents by mapping a file directly into the process's virtual memory space.

Instead of repeatedly using traditional `read()` and `write()` system calls, the application maps the file into memory and allows the program to access the file contents through memory addresses.

The project demonstrates:

1. File creation and opening
2. File size management
3. Memory mapping using `mmap()`
4. Reading data through mapped memory
5. Modifying file contents through mapped memory
6. Synchronizing mapped data with the file
7. Unmapping memory using `munmap()`
8. Proper file descriptor management

The project helps demonstrate the relationship between **virtual memory, file management, system calls, and memory-mapped files** in Linux.

---

## Main Operating System Concepts

The project demonstrates the following Operating Systems concepts:

* Virtual Memory
* Memory-Mapped Files
* File Management
* File Descriptors
* Process Address Space
* Memory Mapping
* Page-Based Memory Management
* System Calls
* File I/O
* Shared Memory Concepts
* Memory Synchronization
* File Permissions
* Kernel and User Space
* `mmap()` System Call
* `munmap()` System Call

---

## Linux System Calls Used

The memory-mapped file management system uses Linux system calls and library functions such as:

* `open()`
* `close()`
* `read()`
* `write()`
* `lseek()`
* `ftruncate()`
* `mmap()`
* `munmap()`
* `msync()`
* `stat()`

These functions allow the application to create, access, map, modify, synchronize, and close files.

---

## Memory Mapping

The central concept of the project is the Linux `mmap()` system call.

The general mapping operation is:

```c
mmap(NULL, file_size, PROT_READ | PROT_WRITE, MAP_SHARED, fd, 0);
```

This creates a mapping between the file and the process's virtual address space.

The application can then access the mapped file using a pointer.

For example:

```c
char *mapped_data;

mapped_data = mmap(
    NULL,
    file_size,
    PROT_READ | PROT_WRITE,
    MAP_SHARED,
    fd,
    0
);
```

After mapping, the file contents can be accessed like normal memory:

```c
printf("%s", mapped_data);
```

Changes made through the mapped memory can be synchronized back to the file.

---

## Project Execution Flow

```text
Linux Terminal
      |
      | ./memory_manager
      v
Linux Memory Mapped File Management System
      |
      +--> 1. Create/Open File
      |
      +--> 2. Set File Size
      |
      +--> 3. Map File into Memory
      |
      +--> 4. Read File Through Memory
      |
      +--> 5. Modify Mapped Memory
      |
      +--> 6. Synchronize Changes
      |
      +--> 7. Unmap Memory
      |
      +--> 8. Close File
```

---

## Memory-Mapped File Operation

The project follows the following sequence:

### Step 1 — Open the File

The file is opened using:

```c
open()
```

A file descriptor is returned by the operating system.

Example:

```text
File
 |
 v
open()
 |
 v
File Descriptor
```

---

### Step 2 — Determine File Size

The application determines the size of the file before mapping it.

The file size can be obtained using:

```c
stat()
```

or:

```c
lseek()
```

The size is required because the mapping length must be specified when calling `mmap()`.

---

### Step 3 — Map the File

The file is mapped into the process's virtual address space using:

```c
mmap()
```

The mapping provides the process with a memory address corresponding to the file contents.

```text
Disk File
   |
   | mmap()
   v
Virtual Memory
   |
   v
Mapped Address
```

---

### Step 4 — Read the File

After mapping, the program can access the file contents through the mapped memory.

For example:

```c
printf("%s", mapped_data);
```

No separate `read()` operation is required to access the mapped region.

---

### Step 5 — Modify the File Through Memory

The program can modify the mapped memory directly.

Example:

``
