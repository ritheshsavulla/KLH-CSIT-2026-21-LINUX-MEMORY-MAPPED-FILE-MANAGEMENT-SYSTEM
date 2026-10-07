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

**[Mr. M. Raghupathi]**

---

## Project Overview

This project demonstrates memory mapped file management in Linux using the `mmap()` system call.

The system allows files to be mapped directly into the process virtual address space so that file contents can be accessed and modified through memory.

The program demonstrates:

1. Creating and opening a file
2. Mapping the file into memory
3. Reading file contents through mapped memory
4. Modifying file contents through mapped memory
5. Synchronizing changes with the file
6. Unmapping the memory
7. Closing the file

Memory mapping provides an efficient way to access file data because the file contents can be accessed directly through memory addresses.

---

## Main Operating System Concepts

The project demonstrates the following Operating Systems concepts:

* Virtual Memory
* Memory Mapped Files
* File Management
* File Descriptors
* Memory Mapping
* File I/O
* System Calls
* Page-Based Memory Management
* Memory Protection
* Shared File Access
* Memory Synchronization
* User Space and Kernel Space

---

## Linux System Calls Used

The memory mapped file management application uses:

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

---

## Memory Mapped File Management

The project uses the Linux `mmap()` system call to map a file into the process virtual address space.

The mapping is created using:

```c
mmap(NULL, file_size, PROT_READ | PROT_WRITE, MAP_SHARED, fd, 0);
```

After mapping, the file contents can be accessed using a memory pointer.

The application can read and modify the mapped memory directly.

Changes can then be synchronized with the original file using:

```c
msync()
```

After the operation is completed, the mapped memory is released using:

```c
munmap()
```

---

## Project Execution Flow

```text
Ubuntu Terminal
      |
      | ./memory_manager
      v
Memory Mapped File Management System
      |
      +--> 1. Create/Open File
      |
      +--> 2. Read File
      |
      +--> 3. Map File into Memory
      |
      +--> 4. Modify Mapped Memory
      |
      +--> 5. Synchronize Changes
      |
      +--> 6. Unmap Memory
      |
      +--> 7. Close File
```

## Memory Mapped File Application

The program performs the following operations:

1. Open the selected file
2. Determine the file size
3. Map the file into memory
4. Display the file contents
5. Modify the mapped contents
6. Synchronize changes
7. Unmap the memory
8. Close the file

The expected flow is:

```text
File
 |
 v
open()
 |
 v
File Descriptor
 |
 v
mmap()
 |
 v
Mapped Memory
 |
 v
Read / Modify
 |
 v
msync()
 |
 v
munmap()
 |
 v
close()
```

---

## Mode 1 — Read File

When the program reads a file through memory mapping, the contents are accessed directly from the mapped memory region.

Example:

```text
File Contents:
Hello Linux Memory Mapping
```

The file is mapped into the process address space and the contents are displayed through the mapped pointer.

---

## Mode 2 — Modify File

The application can modify the contents of the mapped memory.

Example:

```text
Original Content : Hello Linux Memory Mapping
Modified Content : Hello Linux Memory Management
```

The modification is performed directly on the mapped memory region.

---

## Mode 3 — Synchronize Changes

After modifying the mapped memory, the application synchronizes the changes with the underlying file using:

```c
msync(mapped_data, file_size, MS_SYNC);
```

The updated contents are then reflected in the file.

```text
Mapped Memory
      |
      | msync()
      v
File on Disk
```

---

## Project Structure

```text
Linux_Memory_Mapped_File_Management/
│
├── src/
│   └── memory_manager.c
│
├── .github/
│   └── workflows/
│       └── run-project.yml
│
├── docs/
├── data/
├── reports/
├── results/
│
├── Makefile
└── README.md
```

## Important Source Files

### src/memory_manager.c

Contains the Linux memory mapped file management implementation.

### Makefile

Compiles the memory mapped file management application.

### .github/workflows/run-project.yml

Allows the project to be compiled and demonstrated using GitHub Actions.

---

## Requirements

The project requires:

* Linux / Ubuntu
* GCC Compiler
* Make
* Linux system calls
* `mmap()` support

---

## Compilation

Move to the project directory:

```bash
cd ~/Linux_Memory_Mapped_File_Management
```

Compile the memory mapped file management application:

```bash
make
```

This creates:

```text
memory_manager
```

This is the compiled executable file.

---

## Running the Project Locally

Start the memory mapped file management application:

```bash
./memory_manager
```

The application displays:

```text
========================================
 LINUX MEMORY MAPPED FILE MANAGEMENT
========================================

1. Create/Open File
2. Read File
3. Modify File
4. Synchronize Changes
5. Unmap Memory
6. Exit

Enter choice:
```

Enter the required option depending on the required demonstration.

---

## Running Through GitHub Actions

The project can also be compiled and demonstrated directly through GitHub Actions.

Open:

```text
GitHub Repository
      ↓
Actions
      ↓
Linux Memory Mapped File Management
      ↓
Run workflow
```

The workflow:

1. Checks out the repository
2. Compiles the memory mapped file management application
3. Creates/opens the sample file
4. Maps the file into memory
5. Reads the mapped contents
6. Modifies the mapped contents
7. Synchronizes the changes
8. Unmaps the memory
9. Displays the result in the workflow log

---

## Expected Results

### File Mapping

The file should be successfully mapped into the process virtual address space.

Expected result:

```text
File opened successfully
Memory mapping successful
```

### File Reading

The mapped file contents should be displayed correctly.

Expected result:

```text
File contents:
Hello Linux Memory Mapping
```

### File Modification

The mapped memory should be successfully modified.

Expected result:

```text
File contents updated successfully
```

### Synchronization

The changes should be synchronized with the original file.

Expected result:

```text
Changes synchronized successfully
```

### Memory Unmapping

The memory mapping should be released successfully.

Expected result:

```text
Memory unmapped successfully
```

---

## Conclusion

This project demonstrates how Linux uses memory mapping to provide efficient access to file contents.

The `mmap()` system call maps a file into the process virtual address space, allowing the application to read and modify file contents directly through memory.

The project demonstrates important Operating Systems concepts including virtual memory, file management, system calls, memory mapping, memory synchronization, and resource management.

The project provides a practical understanding of how Linux connects virtual memory with file management.

---

## Current Project Status

Core project implementation completed successfully.

* [x] Repository created
* [x] Project directory structure created
* [x] Memory mapped file implementation completed
* [x] File opening implemented
* [x] File size management implemented
* [x] File mapping implemented
* [x] File reading implemented
* [x] File modification implemented
* [x] Memory synchronization implemented
* [x] Memory unmapping implemented
* [x] File closing implemented
* [x] Error handling implemented
* [x] Local execution tested successfully
* [x] GitHub Actions workflow implemented
* [x] Project documentation completed
* [x] README completed

