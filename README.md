# Get_Next_Line

**A robust C implementation for reading lines from file descriptors with dynamic memory management.**

---

## Overview

Get_Next_Line is a low-level file I/O utility designed to read successive lines from a file descriptor one at a time, regardless of line length or buffer constraints. The project demonstrates advanced C programming techniques including memory management, buffer handling, and robust error management.

## Key Features

### Core Functionality
- **Sequential Line Reading**: Reads complete lines from file descriptors, returning one line per function call
- **Dynamic Buffer Management**: Adapts to arbitrary line lengths and configurable `BUFFER_SIZE` constants
- **Robust Error Handling**: Gracefully manages invalid file descriptors, memory allocation failures, and edge cases
- **Memory Efficiency**: Implements careful memory allocation and deallocation with zero memory leaks

### Implementation Highlights

| Feature | Details |
|---------|---------|
| **Memory Optimization** | Efficient buffer allocation and state management across multiple calls |
| **Edge Case Handling** | Correctly handles files without trailing newlines, empty files, and extremely long lines |
| **Modularity** | Clean separation of concerns with dedicated helper functions for buffer operations |
| **Configurable Performance** | Supports flexible `BUFFER_SIZE` values (tested from 1 to 10,000,000 bytes) |

## Technical Approach

### Development Highlights
- **Flexible Buffer Testing**: Validated across multiple `BUFFER_SIZE` configurations for reliability and performance
- **Comprehensive Edge Case Coverage**: 
  - Files ending without newline characters
  - Empty file handling
  - Extended line length support
  - Multiple file descriptor management
- **Rigorous Testing**: Custom test cases covering valid and invalid file descriptor scenarios

## Project Structure

```
├── get_next_line.h           # Function declarations and macros
├── get_next_line.c           # Main implementation
├── get_next_line_utils.c     # Helper functions and utilities
├── main.c                    # Test and usage examples
└── README.md                 # This file
```

## Usage Example

```c
#include "get_next_line.h"

int main(void)
{
    int fd = open("file.txt", O_RDONLY);
    char *line;
    
    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s\n", line);
        free(line);
    }
    close(fd);
    return (0);
}
```

## Requirements

- GCC or compatible C compiler
- POSIX-compliant system (Linux/macOS/Unix)
- C99 or later standard

## Building

Compile with the standard C library:
```bash
gcc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c main.c -o get_next_line
```

## Key Learnings

This project reinforces essential low-level programming competencies:
- **Efficient memory management** through careful allocation and cleanup
- **Systematic problem decomposition** for handling complex I/O challenges
- **Robust error handling** for production-quality code
- **Performance optimization** through buffer design and system-level thinking

---

**Status**: Complete | **Language**: C | **Difficulty**: Intermediate to Advanced
