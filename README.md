# C 06 - Command Line Arguments

![42 Badge](https://img.shields.io/badge/42-C_Piscine-brightgreen)
![C Badge](https://img.shields.io/badge/Language-C-blue)
![Status Badge](https://img.shields.io/badge/Status-Completed-success)

## What I Learned

Through this C Piscine module, I developed essential skills in command-line argument handling and program execution:

- **Command-line argument parsing** - Mastered the use of `argc` and `argv` parameters in main function
- **Program name retrieval** - Learned how the operating system passes the program name to the executable
- **Array iteration techniques** - Implemented forward and reverse iteration through argument arrays
- **String comparison algorithms** - Built custom string comparison functions for sorting operations
- **Sorting algorithms** - Implemented bubble sort for string arrays using ASCII comparison
- **Pointer manipulation** - Used double pointers to swap string references efficiently
- **Memory-safe programming** - Handled edge cases like zero arguments without crashes
- **System-level I/O** - Used only the `write` system call for all output operations
- **Modular function design** - Created reusable helper functions for common operations
- **Algorithm optimization** - Balanced simplicity with efficiency in sorting implementations

This module reinforced my understanding of how programs interact with the operating system and handle user input, essential skills for any systems programmer.

## About the Project

C 06 focuses on command-line argument manipulation in C programs. This module teaches fundamental concepts about how programs receive and process arguments from the command line, covering everything from basic argument display to advanced sorting operations.

## Implementation Details

The project consists of 4 exercises demonstrating progressive complexity in argument handling:

### Exercise 00: ft_print_program_name
**Objective**: Display the program's own name

```c
// Usage example:
$> ./a.out
./a.out
```

**Key Concepts**:
- Understanding `argv[0]` contains the program name
- Basic string output using only `write` function
- Handling the case where `argc` might be 0

**Implementation Highlights**:
- Uses helper functions `ft_putchar` and `ft_putstr` for modular output
- Includes safety check for `argc > 0` before accessing `argv[0]`
- Demonstrates proper newline handling

### Exercise 01: ft_print_params  
**Objective**: Display all command-line arguments (except program name)

```c
// Usage example:
$> ./a.out test1 test2 test3
test1
test2
test3
```

**Key Concepts**:
- Iterating through `argv` array starting from index 1
- Understanding the relationship between `argc` and `argv` length
- Sequential argument processing

**Implementation Highlights**:
- Simple forward loop from `argv[1]` to `argv[argc-1]`
- Each argument printed on a separate line
- Clean separation between argument processing and output

### Exercise 02: ft_rev_params
**Objective**: Display command-line arguments in reverse order

```c
// Usage example:
$> ./a.out first second third
third
second
first
```

**Key Concepts**:
- Reverse iteration through arrays
- Understanding array indexing from end to beginning
- Maintaining proper bounds checking

**Implementation Highlights**:
- Starts from `argc - 1` and decrements to 1
- Preserves original argument order in memory while changing display order
- Efficient single-pass reverse iteration

### Exercise 03: ft_sort_params
**Objective**: Display arguments sorted in ASCII order

```c
// Usage example:
$> ./a.out zebra apple banana
apple
banana
zebra
```

**Key Concepts**:
- String comparison algorithms
- Sorting algorithms (bubble sort implementation)
- Pointer swapping for array manipulation
- ASCII value-based comparison

**Implementation Highlights**:
- **Custom string comparison**: `ft_strcmp` function implementing lexicographic ordering
- **Efficient swapping**: `ft_swap` function using double pointers for string reference swapping
- **Bubble sort algorithm**: Simple O(n²) sorting with nested loops
- **Modular design**: Separate functions for sorting, printing, and comparison operations

#### Technical Deep Dive - Sorting Implementation:

```c
void ft_sort(int ac, char **av)
{
    int i = 1;
    int j;
    
    while (i < ac - 1)
    {
        j = i + 1;
        while (j < ac)
        {
            if (ft_strcmp(av[i], av[j]) > 0)
                ft_swap(&av[i], &av[j]);
            j++;
        }
        i++;
    }
}
```

This implementation:
- Compares each argument with all subsequent arguments
- Swaps arguments when they are out of ASCII order
- Modifies the original `argv` array in place
- Ensures stable sorting behavior

## Usage

Each exercise produces a standalone executable:

```bash
# Compile any exercise
cc -Wall -Wextra -Werror ft_print_program_name.c -o program_name
cc -Wall -Wextra -Werror ft_print_params.c -o print_params
cc -Wall -Wextra -Werror ft_rev_params.c -o rev_params
cc -Wall -Wextra -Werror ft_sort_params.c -o sort_params

# Run examples
./program_name
./print_params hello world 42
./rev_params first second third
./sort_params zebra apple banana charlie
```

## Technical Challenges Overcome

- **Pointer arithmetic mastery** - Working with `char **argv` required understanding double pointer manipulation
- **Memory safety** - Ensuring no buffer overflows when accessing argument arrays
- **Edge case handling** - Managing programs called with zero arguments or empty strings
- **Efficient algorithms** - Implementing sorting without using standard library functions
- **System call limitations** - Building all functionality using only the `write` system call
- **String manipulation** - Creating robust string comparison without `strcmp` library function
- **Code modularity** - Designing reusable helper functions for common operations

## Key Programming Concepts Demonstrated

| Concept | Exercise | Implementation |
|---------|----------|----------------|
| Basic I/O | ex00 | Program name display |
| Array iteration | ex01 | Forward parameter traversal |
| Reverse iteration | ex02 | Backward parameter display |
| Sorting algorithms | ex03 | Bubble sort with string comparison |
| Pointer manipulation | ex03 | Double pointer swapping |
| String comparison | ex03 | Custom lexicographic ordering |

## File Structure

```
C06/
├── ex00/
│   └── ft_print_program_name.c
├── ex01/
│   └── ft_print_params.c
├── ex02/
│   └── ft_rev_params.c
└── ex03/
    └── ft_sort_params.c
```

## Constraints and Requirements

- **Allowed functions**: Only `write` system call permitted
- **Compilation flags**: `-Wall -Wextra -Werror` with `gcc`
- **Norminette compliance**: All code follows 42 School coding standards
- **No standard library**: Custom implementation of all string and I/O operations
- **Memory safety**: No memory allocation required, working with provided arguments
- **Error handling**: Robust handling of edge cases and invalid inputs

---

*This project was completed as part of the 42 School C Piscine, demonstrating proficiency in command-line argument handling, basic algorithms, and systems programming fundamentals.*

---

## License

This project is licensed under the [MIT License](./LICENSE).
