# Tipos Primitivos em Java

Em Java, existem 8 tipos primitivos: `char`, `boolean`, `byte`, `short`, `int`, `long`, `float` e `double`.  
Neste desafio, vamos focar nos tipos que armazenam números inteiros: `byte`, `short`, `int` e `long`.

- Um `byte` é um inteiro com sinal de 8 bits.  
- Um `short` é um inteiro com sinal de 16 bits.  
- Um `int` é um inteiro com sinal de 32 bits.  
- Um `long` é um inteiro com sinal de 64 bits.  

Sua tarefa é determinar quais desses tipos primitivos podem armazenar corretamente um número inteiro fornecido.

Mais detalhes podem ser encontrados na documentação oficial da Oracle [(docs.oracle.com in Bing)](https://www.bing.com/search?q="https%3A%2F%2Fdocs.oracle.com%2Fjavase%2Ftutorial%2Fjava%2Fnutsandbolts%2Fdatatypes.html").

## Formato de Entrada

- A primeira linha contém um inteiro `T`, representando o número de casos de teste.  
- Cada caso de teste consiste em uma única linha contendo um inteiro `n`, que pode ser arbitrariamente grande ou pequeno.

## Formato de Saída

Para cada número de entrada `n`, você deve determinar se os tipos primitivos são capazes de armazená-lo.  
Se sim, imprima:

```
n can be fitted in:
* dataType
```

Se houver mais de um tipo apropriado, imprima cada um em sua própria linha, em ordem crescente de tamanho (`byte < short < int < long`).  

Se o número não puder ser armazenado em nenhum dos quatro tipos primitivos mencionados, imprima:

```
n can't be fitted anywhere.
```

## Exemplo de Entrada

```text
5
-150
150000
1500000000
213333333333333333333333333333333333
-100000000000000
```

## Exemplo de Saída

```text
-150 can be fitted in:
* short
* int
* long
150000 can be fitted in:
* int
* long
1500000000 can be fitted in:
* int
* long
213333333333333333333333333333333333 can't be fitted anywhere.
-100000000000000 can be fitted in:
* long
```
