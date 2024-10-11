this note flow is based in this PDF https://db.in.tum.de/teaching/ss19/c++praktikum/slides/lecture-02.2.pdf?lang=de.

the processes of compiling is divided into 3 back processes:
	`Preprocessor -> Compiler -> Linker`
until to be able to run.

**Preprocessor**
	Takes an input file of any programming language.
	Handles all preprocessor directives (all lines starting with ==#==) and macros
		`#include <stdio> | #define MIN_SIZ 4 | ... `
	Output the file without any preprocessor directives or macros

**Most common preprocessor directives**

- `#include`, copies the contents of a file into the current file.
- `#define`, also know as ==macro==, define a macro
- `#ifdef/#ifndef/#else/#endif` include all [[IfDef, endIF, else in C]]

**Compiler**
	Every ==translation unit== result in exactly one object file(usually .o or .obj).
	External symbol references are not resolved by the compiler, but are marked as external to be resolved later during the linking stage.

**Linker**
	Problems in code will only be found by the Linker processes, the most popular linkers are ==GNU ld, GNU gold, lld(by the LLVM project)==

### Compiler Flags
==Preprocessor and LInker== is excuted by the compiler.
The compiler flags are additional flags that can influence the preprocessor or the Linker step.

- -E  -> Only does the Preprocessor step
- -S  -> Run only preprocessor and compiler (outputs assembly as text) ==dont link==
- -g -> add debug symbols to the generated binary (`g3`)
- -l[lib] -> Link library [lib] into executable (`-lm, link the math libray`)
- -I[path] -> Also search [path] for `#include` files
- -L[path] -> Also search [path] for `libs` specified with `-l`
- -O0 -> compiled without optimazations(good to debug)

`cc main.c -g3 -O0 -Wall -Wextra -Werror -fsanitize=address -o main`


### Head Guards

Header guards are an important feature that should be included in ALL header files.  The purpose of a header guard is to prevent `macros, typedefs, enums and function `prototypes from accidentally being included in a source file ==twice==.  If these definitions do get included twice it can lead to a compiler error due to a double definition. The use of a header guard will easily solve this problem.  A header guard consists of three parts.

1) Checking whether a macro related to this file has been previously defined through the use of #ifndef

2) If the macro hasn’t been previously defined then the macro is now defined using #define

3) Closing of the #ifndef block using #endif

```c
//functions.h

#ifndef FUNCTIONS_H
	#define FUNCTIONS_H

	int is_empty(st_node *root); 
	int search_node(st_node* root, int value); 
	int length_node(st_node *root); 
	void insert_node_list(st_node **root, st_node *new_node); 
	void delete_node_list(st_node **root, int value); 
	void free_memory_node(st_node *root); 
#endif 

```

Another form to implement the header guards is using ==#pragme once==

```c
//functions.h
#pragma once
	int is_empty(st_node *root); 
	int search_node(st_node* root, int value); 
	int length_node(st_node *root); 
	void insert_node_list(st_node **root, st_node *new_node); 
	void delete_node_list(st_node **root, int value); 
	void free_memory_node(st_node *root); 
```

When you use #pragma once at the beginning of a header file, it prevents the same file from being processed more than once by the compilation, regardless of how many times it is included.

[[Book - compiling processes]] to know more.