
syntax

To create: requirements
	steps
	
CC -> compiler
CFLAGS -> compiler flagas(as -Wall -Werror -Wextra)
LDFLAGS -> stands for ==Linker Flags==

### Static Lib
`.a` vem de `archive` que são varios object files ligados(compilados) que podem ser anexado em um programa no processo de linkagem 

(.o + .o + .o + .o) = .a

Quando você usa uma biblioteca estática, o compilador copia os trechos de código necessários do arquivo `.a` diretamente para o binário final (executável) do programa.

Como o código da biblioteca está incluído diretamente no executável, o programa não depende de nenhum arquivo de biblioteca externo quando for executado.
### Common uses of ==LDFLAGS==
- -L(dir): Tells to the linker what is the path to the folder for the Libraries. For example `-L/usr/local/lib`, tells to linker the path to find the libs.
- -l(libray): Links a specific library. as example -lmylib. it lin


----
```bash
/project-root
│
├── /src            # Arquivos de código-fonte (.c)
│   ├── main.c
│   ├── file1.c
│   └── file2.c
│
├── /include        # Arquivos de cabeçalho (.h)
│   ├── file1.h
│   └── file2.h
│
├── /lib            # Bibliotecas externas ou compiladas (.a ou .so)
│   └── mylib.a
│
├── /bin            # Executáveis gerados após a compilação
│   └── myprogram
│
├── /build          # Arquivos temporários de build (gerados pela compilação)
│   └── objects
│       ├── file1.o
│       └── file2.o
│
├── /tests          # Arquivos de teste
│   └── test_file.c
│
├── Makefile        # Script para automação de build
└── README.md       # Descrição do projeto

```

`$(addprefix ./src/,$(SOURCES))`
`$(SOURCES:./src/%.c=./obj/%.o)`
### Atribuição com `:=` (Atribuição Imediata):

Quando você usa `:=`, a variável é avaliada **imediatamente** no momento em que a linha é lida. Isso significa que o valor da variável é calculado e armazenado no exato momento da atribuição.

### Wildcards
Wildcards are used to simplify the management of files allow us to select a bunch of files based on their pattern names. they are similar to the `wildcard shell unix`, used `*` (represent anything until a certain point) or `?` represent a single any char.

- ==`*`== used to combine any sequence of char. `*.c` -> any file terminated with `.c`
- ==`?`== replace a single char. as example `file?.txt` can select a sequence
- ==[...]== inside the brackets represent the allow char. as example `file[123]`


**Using Wildcards**

In the example below we are assigning all files ending in `.c` to the `source variable`
```makefile
SOURCES = $(wildcard *.c)
```

### KeyWord

`$@` represent the target to be create, as the example in below the @S mean `program`, we also can use $(PROGRAM)

`$^` represent all the dependence  of the current target, in the below example is `$(OBJECTS)`
(we also can use $(OBJECTS) however @^ is cool)
```makefile
CC = gcc
SOURCES = $(wildcard *.c)
CFLAGS = -Wall -Wextra -Werror -g3 -fsanitize=address
OBJECTS = $(SOURCES:.c=.o)
PROGRAM = myprogram

all: $(PROGRAM)

$(PROGRAM): $(OBJECTS)
	$(CC) $^ $(CFLAGS) -o $@
```

`$(CC) $(OBJECTS) $(CFLAGS) -o $(PROGRAM) = $(CC) $^ $(CFLAGS) -o $@`

- Use `%` in pattern rules to define how to compile or transform an input file into a corresponding output file.

- Use `*` when you want to refer to a set of files more broadly, such as in dependency lists or when cleaning up files.

em resumo % é utilizado para quando temos uma `regra de padão` onde o correspondente de um lado existe do outro lado também. quando utilizamod %.o : %.c

**`$<`**:
- This is a special variable in Makefiles that represents the first prerequisite of the rule, which is the source file (`%.c`) in this case. If the target is `example.o`, then `$<` would be `example.c`.
```makefile
CC = gcc
CFLAGS = -Wall -Wextra -Werror 
SOURCES = $(wildcard *.c)
OBJECTS = $(SOURCES:.c=.o)
PROGRAM = myProgram

all: $(PROGRAM)

clean: 
	rm -r $(PROGRAM)

$(PROGRAM): $(OBJECTS)
	$(CC) $(CFLAGS) -o $@ $^

%.o: %.c
		$(CC) $(CFLAGS) -c $< -o $@
```

is interesting to know the line `%.o: %.c` is execute automatically when the make note we has made modifications in `.c` archives or notice the dependence `.o` does not exist  

---
### AR RCS
the `ar rcs` command is used to create and modify an `static library` in C
- ar-> is it acronum of ==archiver==. it server to create, modify and extract files
- -r -> the `-r` is telling to ar to `replace` or `add` file to the archive If the file (typically an object file) already exists in the archive, it will be replaced with the new version. If the file doesn't exist, it will be added.
- -c -> create
- s -> request to ar create an symbol table

**FLAG RESUME**
r -> **(Replace/add)**
c -> **(Create)**
s -> **(Symbol table/index)**
**Example**
`ar rcs libfunctions_libray.a file1.o file2.o`

**Important points**
[X] by convention we always used the **prefix** ==lib== before create the library name. the prefix is automatically **hidden** when haft  to use.

**Another important flags**

- -t -> the `-t` flag is acroum to ==table content== it show all `object files` that are compressed into this `static library`

```bash
ar -t liblib_ft.a

//OUTPUT
ft_putstr.o
ft_strcmp.o
ft_strlen.o
ft_swap.o
```

-x -> another important flag is the `-x` flag it ==extract== all object files out of that `static library` 

-d -> the flag `-d` allow us delete one or more object files of an `static library`. in the example below we are removing the `file1.o` from the library

```bash
ar -d liblib_ft.a file1.o
```

-v -> this is the famous ==verbose mode==



---

