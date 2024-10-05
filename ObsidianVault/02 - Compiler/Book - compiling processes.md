Compile time = perfomed the code into memory/execute
Load time = when the source code is translate

`bother = incomodar`
`baffling = desconcenrtante`

static linking -> dynamic linking of shared libraries at load time ->  dynamic linking of shared libraries at run time

ELF or Standard ELF Object File Format -> mean Executable and Linkable format. is a kind of "organize Box" that improve the executable processes store the data and code.

---
#### Compiler Drivers

main.c -> preprocessor -> main.i -> compiler -> main.s -> assembler -> main.o -> linking -> main.out

main.c -> C language 
main.i -> .i mean `intermediate`, that a intermediate file
main.s -> .s is assembly 
main.o / main.obj -> .o mean `object file` begin a binary file | `Relocatable object files`
main.out / main.exe -> .out 


The shell invokes a function in the operating system called the ==loader==, which copies the code and data in the executable file into memory, and then transfers control to the beginning of the program.

---
#### Gears to be in the processes 

**Preprocessor**
	==ccp==(C Preprocessor) handle with #include and #define, and conditional compilation instructions. It handles macro expansion and file inclusions before the actual compilation step.
		The preprocessor is often bundled with compilers like `gcc` or `clang`.

**Compiler**
	- ==gcc==(GNU Compiler collection) One of the most popular and widely used C compilers.
	- ==clang== Another popular compiler, known for its modularity and error diagnostics. It is part of the [[LLVM project]]
	-==cc== In many Unix-like systems, `cc` is a reference to the system's default C compiler (which is often `gcc` or `clang`).

**Linker**
	-==ld==(GNU Linker ) Commonly used to link object files and libraries into a single executable. It is used in the final stage of compilation after the code has been compiled into object files.
	-==collect2== In some cases, `gcc` uses `collect2`, which is a wrapper around `ld` for handling some special cases (like constructors and destructors in C++).
	-==gold== A faster alternative to the GNU `ld` linker, designed for high performance.
	

---
### Translation Unit

Is the result of compiling a single source file. This processes happens before the linking stage. the compiling of a `translation unit` produces an **object file**(`.o` or `.obj` file) with contains the compiled machine code and some metadata

he terms are closely related because an object file is essentially the binary representation of the translation unit.

----

### Object Files

**Relocatable object file**
	Contains binary code and data in a form that can be combined with other relocatable object files at compile time to create an executable object file.

**Executable object file**
	Contains binary code and data in a form that can be copied directly into memory and executed.

**Shared object file**
	A special type of relocatable object file that can be _loaded into memory and linked dynamically_, at either load time or run time.

`COFF = Common object file format(COFF)`
`ELF = Executable and Linkable Format (ELF).`


##### Relocatable Object Files

A typical ELF relocatable object file starts with an ELF header. The header begins with a 16-byte sequence that specifies the system's word size and byte order that generated the file. The rest of the header contains key details for the linker to read and interpret the file. These include the ELF header size, object file type (such as relocatable, executable, or shared), machine type (e.g., IA32), the location of the section header table, and the size and number of entries in this table. The section header table provides the locations and sizes of the file’s sections, with one fixed-size entry per section.
![[Pasted image 20240926212529.png]]
ELF relocatable object file contains the following sections:

**.text**
	The machine code of the compiled program.

**.rodata**
	Read-only data such as the format strings in printf statements, and jump tables for switch statements
	

**.data**
	The .data segment of an ELF (Executable and Linkable Format) file contains global and static variables that are initialized in the program's source code. Unlike .bss segments, which store uninitialized variables, .data stores data that already has a value defined before the program runs.

.**bss**
	Uninitialized global C variables. This section occupies no actual space in the object file; it is merely a place holder.

**.Symtab**
	A symbol table with information about **functions and global variables** that are defined and referenced in the program.

**.rel.text**
	A list of locations in the .text section that will need to be modified when the **linker combines this object file with others**. In general, any instruction that calls an external function or references a global variable will need to be modified. On the other hand, instructions that call local functions do not need to be modified. Note that relocation information is not needed in executable object files, and is usually omitted unless the user explicitly instructs the linker to include it.

**.rel.data**
	Relocation information for any global variables that are referenced or defined by the module. In general, any initialized global variable whose initial value is the address of a global variable or externally defined function will need to be modified.

.debug
	A debugging symbol table with entries for local variables and typedefs defined in the program, global variables defined and referenced in the program, and the original C source file. **It is only present if the compiler driver is invoked with the -g option.**

.line
	A mapping between line numbers in the original C source program and machine code instructions in the .text section. It is only present if the compiler driver is invoked with the -g option.

**.strtab:**
	 A string table for the symbol tables in the .symtab and .debug sections, and for the section names in the section headers. A string table is a sequence of null-terminated character strings