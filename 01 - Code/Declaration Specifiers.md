### Static
the keyword `stactic` can has multiple functions depends of their context and application.


**Global Variables**
	When we had a scope `var` as example a var inside a function and we want to preserve their values in multiple calls of the same function we can use `static` to preserve their value.
```c

void contador(){
	static int count = 0;
	printf("%d",count);
}

contador(); //0
contador(); //1
contador(); //2
```

the `var` behavior is the same as we define it out of function scope. 

**Narrowing the definition to the scope**
	when we had a `global variable` and we want restrict it only in that file we can use `static`. in this case the variable can only be accessed in `definition file` begin unable to be accessed in another files even with #include.

```c
#include <stdio.h>

static int x = 0; //global variable truncate into this file

int main(void)
{
	printf("%d\n", x);
	
	return (0);
}
```

**funções**
quando utilizamos a keyword `static` em uma função ela vai ter a mesma funcionalidade que a static com a variável global, ela só podera ser chamada e utilizada naquele `translation unit`, naquele arquivo em resumo.

```c
#include <stdio.h>

static void soma()
{
	static int x = 0;
	printf("%d\n", x);
}

int main(void)
{
	soma();
	soma();
	soma();
	soma();
	return (0);
}
```

#### Extern
A keyword `extern` no C informa que definição daquela função ou variável foi feito em outro arquivo. Ela permite que diferentes arquivos de um programa compartilhem variáveis e funções, funcionando como uma espécie de "link" entre os arquivos.

**Variáveis globais**
	Nesse contexto quando pensamos em variáveis globais estamos pensando em um quesito mais amplo, não somente entre funções mas sim entre arquivos diferentes.

```c
	//Arquivo 1
#include <stdio.h>

int global_var = 10; //definição

void print_var(){
	printf("the current value of >global_var< is: %d", global_var);
}
```
em outro arquivo temos
```c
#include <stdio.h>

extern int global_var; //declaração da variável global

int main(void)
{
	printf("valor de var_global que está em outro arquivo: %d", global_var);
	return (0);
}
```

**Uso com funções**
por padrão o compartilhamento de funções entre diferente arquivos já é suportado nativamente, como se tivessemos um `extern` implicito em todas as funções.

```c
#include <stdio.h> 
void minha_funcao()  // Definição da função 
{ 
printf("Função chamada de arquivo1!\n"); 
}
```
em outro arquivos

```c
#include <stdio.h>

extern void minha_funcao();

int main(void)
{
	minha_funcao();
	return (0);
}
```

**Declaração VS Definição**
Declaração -> informa ao compilador que uma variável ou função existe em algum outro lugar não resver memória.

Defininção -> reserva memória para variável ou função.

variáveis fora de algum escopo, inclusive do main podem ser utilizadas em outro arquivo com `extern`. o header nada mais que essa chamada de funções e variáveis de outros arquivos.