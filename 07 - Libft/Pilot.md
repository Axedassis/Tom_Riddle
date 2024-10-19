
#### Retorno de funções como ft_is@somehting
- ==0== quando não é 
- ==1== qualquer outro número quando é valido

### Patterns to Head Guards in 42SP

```libft.h
#ifndef LIBFT_H
# define LIBFT_H

....

#endif 
```

### ASCII table diffrence 

7 bits = 126 char
8 bits = 255 char
[[[ASCII tables difference]]]

#### Unsigned char

é importante quando vamos fazer comparações na tabela ascii efetuar o casting dos valores para (unsigned char) para evitar a procura de valores além do sistema de 8 bits


#### const pointers

Em C, quando você tem um parâmetro `const void *s`, o modificador `const` significa que você não pode alterar o valor para o qual o ponteiro aponta, ou seja, o conteúdo da memória que o ponteiro está referenciando é "constante" e não pode ser modificado.

importancia do casting do pointer

```c
void *ft_memchr(const void *s, int c, size_t n)
{
	int i = 0;
	while(i <= n)
	{
		if(*(unsigned char *)s == c)
			return (s);
		s++;
		i++;
	}
	return ((void *)0);
}

```

---
#### casting time difference

A diferença entre `((unsigned char *)dest)[i]` e `(unsigned char *)dest[i]` está na forma como o compilador interpreta as expressões, influenciada pela precedência dos operadores de ponteiros e arrays.

### 1. `((unsigned char *)dest)[i]`

Nesta expressão, o ponteiro `dest` é primeiramente **convertido** para um ponteiro do tipo `unsigned char *`. Em seguida, a notação de array `[i]` é usada para acessar o **i-ésimo elemento** do array de `unsigned char`.

Passos:

1. `(unsigned char *)dest` transforma `dest` em um ponteiro para `unsigned char`.
2. `((unsigned char *)dest)[i]` acessa o elemento na posição `i` de um array de `unsigned char`.

Isso é útil quando você tem um ponteiro genérico (como `void *`) ou um ponteiro de um tipo diferente e deseja tratá-lo como uma sequência de bytes (`unsigned char`).

### 2. `(unsigned char *)dest[i]`

Aqui, a interpretação é diferente por causa da precedência dos operadores. A expressão `dest[i]` é avaliada primeiro. Ou seja:

- **Primeiro** o índice `i` é aplicado a `dest`, ou seja, a expressão acessa o **i-ésimo elemento de `dest`**, e **depois** este elemento é **convertido** para um ponteiro de `unsigned char`.

Passos:

1. `dest[i]` acessa o elemento `i` de `dest`.
2. `(unsigned char *)` converte o resultado de `dest[i]` para um ponteiro de `unsigned char`.

### Diferença Prática

- **`((unsigned char *)dest)[i]`**: Você está acessando o **i-ésimo byte** de uma sequência de `unsigned char` apontada por `dest`.
- **`(unsigned char *)dest[i]`**: Aqui, o programa acessa o **i-ésimo elemento** de `dest` (que pode ser um array de qualquer tipo), e depois tenta **converter** esse elemento para um ponteiro de `unsigned char`.
---

![[Pasted image 20241017012905.png]]

----

gemini para interpretar e sumarizar para o formado que o mermaid precisa e utilizar o mermaid para fazer grafo

---


****INFORMATIONS****
ft_strlen -> return the string size of an pointer char *s

******COPY AND CONCATENET******
ft_strlcpy -> copia para dst, "size" characters de src
ft_strlcat -> append the "src" string into "dst", but only "size" characters 
ft_strdup -> duplica uma string para outro ponteiro
ft_strjoin -> junta a str1 com str2
ft_substr -> a partir da string str1 na posição start copia len caracteres e retorna um ponteiro para nova string


****SEARCH FUNCTINS****
ft_strchr -> search for the first occurrence of a char in a string and return the pointer for it
ft_strrchr -> search for the ==last== occurrence of a char in a string and return the pointer for it
ft_strncmp -> compare n string from str1 and str2
ft_strnstr -> search for "n" bytes in "haystack" by the "niddle" and return the pointer into it if find 

****TREATMENT****
ft_strtrim -> remove "neddles" from a haystack "like remove all spaces from a string"