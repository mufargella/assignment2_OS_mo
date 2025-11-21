# OS Lab 5 - Quick Reference Guide

##  Quick Commands

```bash
# Setup
git clone https://github.com/mufargella/assignment2_OS_mo.git && cd assignment2_OS_mo

# Build & Run (all in one)
make all && make run

# Individual builds
make process_creation && ./process_creation
make output_program && ./output_program
make simple_program && ./simple_program

# Cleanup
make clean
```

##  Files Overview

```
process_creation.c  → fork() demo
file1.c + file2.c   → linker demo
simple_program.c    → loader demo
Makefile           → build automation
```

##  Key Concepts

### fork() Cheat Sheet

```c
pid_t pid = fork();

if (pid < 0) {
    // Error
} else if (pid == 0) {
    // Child process
} else {
    // Parent process (pid = child's PID)
}
```

**Result**: Creates exact copy of calling process

### Compilation Pipeline

```
.c → [Preprocessor] → .i → [Compiler] → .s → [Assembler] → .o → [Linker] → executable
```

### Linker vs Loader

| | Linker | Loader |
|---|--------|--------|
| **When** | Compile-time | Run-time |
| **Input** | `*.o` files | `executable` |
| **Output** | `executable` | Running process |
| **Job** | Combine & resolve symbols | Load into memory & start |

## 🔍 Debug Commands

```bash
# See linked libraries
ldd ./simple_program

# See system calls
strace ./simple_program

# See compiled symbols
nm ./output_program

# See file type
file ./process_creation

# See assembly
objdump -d ./simple_program
```

##  Expected Outputs

### process_creation
```
This is the parent process. PID: 1234
This is the child process. PID: 1235
```

### output_program
```
Hello from file1!
```

### simple_program
```
This is a simple program.
```

##  Troubleshooting

| Problem | Solution |
|---------|----------|
| `gcc: command not found` | `sudo apt install build-essential` |
| `Permission denied` | `chmod +x ./program_name` |
| `No such file` | Run `make all` first |
| Makefile errors | Check tabs (not spaces) |

##  Manual Compilation

```bash
# Process creation
gcc process_creation.c -o process_creation

# Linker example (step by step)
gcc -c file1.c
gcc -c file2.c
gcc file1.o file2.o -o output_program

# Simple program
gcc simple_program.c -o simple_program
```

##  Quick Definitions

**Process**: Running program instance  
**PID**: Process ID (unique number)  
**Fork**: Create child process (clone)  
**Linker**: Combines `.o` files  
**Loader**: Starts executable  
**Object File**: Compiled but not linked  
**Symbol**: Function/variable name  

##  Learning Checklist

- [ ] Understand what `fork()` returns
- [ ] Explain difference between parent and child
- [ ] Know what linker does
- [ ] Know what loader does
- [ ] Can manually compile multi-file program
- [ ] Can use `ldd` to see dependencies
- [ ] Understand Makefile basics

##  Try These

```bash
# See all processes
ps aux | grep simple_program

# Run in background
./simple_program &

# Time execution
time ./process_creation

# Watch memory usage
/usr/bin/time -v ./simple_program
```

---

** Tip**: Use `man fork` or `man gcc` for detailed documentation!
```
