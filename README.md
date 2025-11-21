# Process Management & Compilation Lab

[![Language](https://img.shields.io/badge/language-C-blue.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![OS](https://img.shields.io/badge/os-Linux-green.svg)](https://www.linux.org/)

## Overview

Educational project demonstrating fundamental OS concepts through practical C implementations.

## Structure

```
assignment2_OS_mo/
├── process_creation.c    # Exercise 1: fork() system call
├── file1.c              # Exercise 5: Linker demo (part 1)
├── file2.c              # Exercise 5: Linker demo (part 2)
├── simple_program.c     # Exercise 6: Loader demo
├── Makefile            # Build automation
└── README.md
```

## Build Instructions

```bash
# Build all executables
make all

# Build specific target
make process_creation
make output_program
make simple_program

# Execute all programs
make run

# Clean build artifacts
make clean
```

## Implementation Details

### 1. Process Creation (`process_creation.c`)

Demonstrates `fork()` system call behavior:
- Parent process continues execution
- Child process is created with separate PID
- Both processes run concurrently

**Key Functions**: `fork()`, `getpid()`

### 2. Linker Example (`file1.c` + `file2.c`)

Shows linking phase of compilation:
- Separate compilation units
- Symbol resolution across files
- External function references

**Compilation Steps**:
```bash
gcc -c file1.c -o file1.o
gcc -c file2.c -o file2.o
gcc file1.o file2.o -o output_program
```

### 3. Loader Example (`simple_program.c`)

Illustrates program loading mechanism:
- Dynamic library dependencies
- Memory mapping
- Execution initialization

**Inspect loaded libraries**:
```bash
ldd ./simple_program
```

## Technical Notes

### Linker vs Loader

| Aspect | Linker | Loader |
|--------|--------|--------|
| **Phase** | Compile-time | Run-time |
| **Input** | Object files | Executable |
| **Output** | Executable | Process in memory |
| **Task** | Resolve symbols | Load & execute |

## Environment

- **Compiler**: GCC (GNU Compiler Collection)
- **OS**: Linux/Unix with POSIX support
- **Standard**: C99 or later

## Author

Lab 5 Assignment - Operating Systems Course

## License

MIT License - Educational Use
```
