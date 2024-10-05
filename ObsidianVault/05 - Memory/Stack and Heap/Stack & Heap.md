Quando iniciamos um programa o mesmo tem processos que o computador aloca um espaço da memoria para que o mesmo possa trabalhar. o layout de memória padrão do C se baseia na seguinte disposição

### Memory layout in C language

![[Pasted image 20240921224155.png]]


**Stack** (FILO)
é um espaço em memoria que comporta as funções do programa. cada segmentação nesse pilha é demonimada  ==_Stack Frame_== . toda nova função cria uma nova Stack Frame nessa stack. Toda Stack Frame também tem a capacidade de comportar variáveis. e quando a Stack Frame é finalizada, como por exemplo um função terminou, todo a Stack Frame é destruida.

#### Stack parts

- Stack Pointer
	indica o endereço do espaço de memória que está livre, ficando localizada no top da última stack frame criada.

É interessante saber que a operação de adicionar uma Stack Frame a uma Stack é extremamente `rápida` e `eficiente` pois a única coisa que o processador faz é mover o ==Stack pointer== para um posição menor (pois a stack frame crescem inveramente).

- **Heap**
	De forma resumida é um espaço maior em memoria que vai comportar tudo aquilo que ocorre durante o código, o que é gerado e carregado. e para utilizarmos essa parte é frequentamente usado ==malooc e freee==.


- **Unitialize Data**
	Basicamente são variaiveis declaradas sem nenhum valor que são armazenadas nesse endereço de memoria. 

- **Data**
	Basicamente são variáveis e string constantes que já tem seu valor inicializado no começo do processo

- **Text Code**
	É onde literalmente nosso código digitado vai ser carregado, normalmente a forma dele transpilada em Assembly


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