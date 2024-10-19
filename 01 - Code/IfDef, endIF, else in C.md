é um condicional que traduzida informa "se definido"  e basicamente inclui ou excluir partes de código.

verifica se tem uma constante definida, se tiver ela executa um bloco de código

```c
#include <stdio.h>
#define MACRO 10
int main(void)
{
#ifdef MACRO
	printf("the macro >MACRO< exists");
#else
	printf("the marcro >MACRO< doesn't exist");
#endif
}
```

para acabar o bloco de código caso uma macro exista utilizamos ==#endif===, podemos também caso não exista aquela macro defina ter uma tratativa para continuar.

caso queiramos "desdefinir" uma macro podemos utilizar o ==#undef== para retirar sua definição.
mas caso queiramos fazer a verificar se um macro está desfeinida podemos utilizar ==#ifndef==

```c
#include <stdio.h>
#define MACRO 10
#undef MACRO
int main(void)
{
	#ifndef MACRO
		printf("the macro >MACRO< is undef");
	#else
		printf("the macro >MACRO< is def");
	#endif  
}
```

basicamente é o ==if== com a lógica inversa ==!==, `if(!MACRO)`.