most of projects in c follow an structure to organize the files and folders. the basic folder structure that we can had is:
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

- ==src== -> basically `src` come from `source` that is the folders with all source code, every typing coding. in the example we had `file1.c`, `file2.c` and `main.c`

- ==include== -> the `include` is store all our headers file, is important to remember the most part of the `.h` as their own `.c` corresponding. 

- ==lib== -> in this folder the external lib are stored in two type of files `.a` and `.so`. the difference between this file is `.a` is a `external static libray` and this type of lib in the `compile processes`is incorporated into executable binary. however the `.so(shared object)` is a type of `externa libray` it's not incorporated in the code in `compile processes`. their are loaded in the `time runing`.

- ==bin== -> is the final state of a program, is the place where the binaries are stored before the `compling processes`

- ==build== -> is a temporally directory where the `.o` (object file) and other types files are stored to be used later.
