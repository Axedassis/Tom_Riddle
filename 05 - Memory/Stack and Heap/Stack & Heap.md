Quando iniciamos um programa o mesmo tem processos que o computador aloca um espaço da memoria para que o mesmo possa trabalhar. o layout de memória padrão do C se baseia na seguinte disposição

### Memory layout in C language

![[Pasted image 20240921224155.png]]


Here is the translation of the text into English:

---

**Stack** (FILO)  
The stack is a memory space that holds the program's functions. Each segmentation in this stack is called a **Stack Frame**. Every new function creates a new Stack Frame in this stack. Each Stack Frame can also hold variables, and when the Stack Frame ends—such as when a function finishes—the entire Stack Frame is destroyed.

#### Stack parts

- **Stack Pointer**  
    Indicates the address of the free memory space, which is located at the top of the last Stack Frame created.

It's interesting to know that adding a Stack Frame to a Stack is extremely `fast` and `efficient` because all the processor does is move the **Stack Pointer** to a smaller position (since the stack frames grow inversely).

- **Heap**  
    In short, the heap is a larger memory space that holds everything that occurs during the code's execution—what is generated and loaded. To use this part of memory, `malloc` and `free` are frequently used.
    
- **Uninitialized Data**  
    These are basically variables declared without any value, stored in this memory address.
    
- **Data**  
    These are variables and constant strings that already have their values initialized at the beginning of the process.
    
- **Text Code**  
    This is where our written code is literally loaded, usually in its form transpiled into Assembly.


---
.bss -> Block starting symbol = is the portion of an object file, executable, or assembly language code that contains statically allocated variables that are declared but have not been assigned a value yet. It is often referred to as the "bss section" or "bss segment". [[Book - compiling processes]]

A alocação de memória utilizando malloc é na heap isso se reflete nas questões de variáveis de escopo e globais e possibilidade de externalizalas

### Stack Frame Structure
![[Pasted image 20240921232243.png]]

Variáveis locais e parâmetros de função se autoexplicam.

**Antigo topo da pilha** -> também chamado de ==Frame Pointer== indica onde é o topo da última Stack Frame

Temos então que para cada função chamada empilhamos um stack frame no topo da pilha de funções. O topo dessa pilha sempre contém o menor endereço de memória. Dessa forma se o topo da pilha for o endereço X, qualquer endereço menor do que X é inválido e qualquer endereço maior do que X é um stack frame válido.


Heap desaloca memória no momento 

Os espaços de memória utilizados pela _Stack_ são eficientes e não fragmentados. O _Heap_ por sua vez, fragmenta muito a memória, o que pode levar a um mal aproveitamento do espaço de endereçamento como consequência.

Stack possui um tamanho limitado, funções recursivas podem faćilmente estourar esse limite, resultado em erros como "Stack overflow",  já a Heap pode crescer e diminuir dinamicamente de acordo com o programa. por padrão as heap vem com um tamanho de memória, porem quando o limite é atingido o programa faz uma solicitação (System Call) para o processador e solicita que mais memória seja disponibilizada

---

Heap Corruption: Refere-se a alterações indesejadas na memória do heap que podem causar falhas ou comportamento errático.

Memory Leak: Quando a memória alocada no heap não é liberada, resultando em um uso crescente de memória ao longo do tempo.

Heap Overflow: Embora menos comum, refere-se a um buffer overflow que ocorre no heap.

Allocation Failure: Um termo que descreve a falha na alocação de memória no heap.