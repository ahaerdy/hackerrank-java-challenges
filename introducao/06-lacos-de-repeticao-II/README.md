# Desafio das Séries

Utilizamos os inteiros $a$, $b$ e $n$ para criar a seguinte série:

$$(a + 2^0 \cdot b), (a + 2^0 \cdot b + 2^1 \cdot b), \ldots, (a + 2^0 \cdot b + 2^1 \cdot b + \ldots + 2^{n-1} \cdot b)$$

## Formato de Entrada

A primeira linha deverá informar um inteiro, $q$, denotando o número de séries.  
Cada linha $i$ das $q$ linhas subsequentes contém três inteiros separados por espaço que descrevem os respectivos valores de $a_i$, $b_i$ e $n_i$ para aquela série.

## Restrições

* $0 \le q \le 500$
* $0 \le a, b \le 50$
* $1 \le n \le 15$

## Formato de Saída

Para cada consulta, imprima a série correspondente em uma nova linha. Cada série deve ser impressa em ordem como uma única linha de $n$ inteiros separados por espaço.

## Exemplo de Entrada

```text
2
0 2 10
5 3 5

```

## Exemplo de Saída

```text
2 6 14 30 62 126 254 510 1022 2046
8 14 26 50 98

```

## Explicação

Temos duas consultas:

1. Usamos $a = 0$, $b = 2$ e $n = 10$ para produzir a série $s_0, s_1, \ldots, s_{n-1}$:
* $s_0 = 0 + 1 \cdot 2 = 2$
* $s_1 = 0 + 1 \cdot 2 + 2 \cdot 2 = 6$
* $s_2 = 0 + 1 \cdot 2 + 2 \cdot 2 + 4 \cdot 2 = 14$
* ... e assim por diante.

Ao atingirmos $n = 10$, imprimimos os primeiros dez termos como uma única linha de inteiros separados por espaço.


2. Usamos $a = 5$, $b = 3$ e $n = 5$ para produzir a série $s_0, s_1, \ldots, s_{n-1}$:
* $s_0 = 5 + 1 \cdot 3 = 8$
* $s_1 = 5 + 1 \cdot 3 + 2 \cdot 3 = 14$
* $s_2 = 5 + 1 \cdot 3 + 2 \cdot 3 + 4 \cdot 3 = 26$
* $s_3 = 5 + 1 \cdot 3 + 2 \cdot 3 + 4 \cdot 3 + 8 \cdot 3 = 50$
* $s_4 = 5 + 1 \cdot 3 + 2 \cdot 3 + 4 \cdot 3 + 8 \cdot 3 + 16 \cdot 3 = 98$

Em seguida, imprimimos cada elemento da nossa série como uma única linha de valores separados por espaço.

## Template Inicial do Desafio

```java
import java.util.*;
import java.io.*;

class Solution{
    public static void main(String []argh){
        Scanner in = new Scanner(System.in);
        int t=in.nextInt();
        for(int i=0;i<t;i++){
            int a = in.nextInt();
            int b = in.nextInt();
            int n = in.nextInt();
        }
        in.close();
    }
}
```

## Solução

```java
import java.util.*;
import java.io.*;

class Solution {
    public static void main(String []argh) {
        Scanner in = new Scanner(System.in);
        int t = in.nextInt(); // Lê a quantidade total de consultas (queries)
        
        for (int i = 0; i < t; i++) {
            int a = in.nextInt(); // Lê o valor de 'a' para a consulta atual
            int b = in.nextInt(); // Lê o valor de 'b' para a consulta atual
            int n = in.nextInt(); // Lê o número de termos 'n' a serem gerados
            
            // Esta variável vai acumular o valor do termo atual da série.
            // Ela começa com o valor de 'a' porque todos os termos têm 'a' na fórmula.
            int termoAtual = a;
            
            // Loop para gerar cada um dos 'n' termos da série (de 0 até n-1)
            for (int j = 0; j < n; j++) {
                // A fórmula do termo j adiciona (2^j * b) ao acumulador.
                // Em Java, (1 << j) é uma forma muito eficiente de calcular 2 elevado a j.
                termoAtual += (1 << j) * b;
                
                // Imprime o termo atual seguido de um espaço, mantendo na mesma linha
                System.out.print(termoAtual + " ");
            }
            
            // Após imprimir todos os 'n' termos da consulta atual, pula para a próxima linha
            System.out.println();
        }
        in.close(); // Fecha o scanner para liberar os recursos
    }
}

```

## O que foi feito na solução?

### 1. Entendendo a Lógica da Série Matemática

Se olharmos atentamente para a fórmula da série na imagem, percebemos que cada termo é construído em cima do termo anterior:

* Primeiro termo ($s_0$): $a + 2^0 \cdot b$
* Segundo termo ($s_1$): $(a + 2^0 \cdot b) + 2^1 \cdot b \implies s_0 + 2^1 \cdot b$
* Terceiro termo ($s_2$): $(a + 2^0 \cdot b + 2^1 \cdot b) + 2^2 \cdot b \implies s_1 + 2^2 \cdot b$

Reparou no padrão? O termo atual é sempre o **termo anterior somado a $2^j \cdot b$**, onde $j$ é o índice atual do elemento (começando em $0$ e indo até $n-1$).

### 2. Otimização com o Acumulador (`termoAtual`)

Em vez de recalcular potências complexas do zero a cada iteração, nós inicializamos a variável `termoAtual` com o valor de `a`.

Dentro do loop interno (`j`), nós apenas calculamos a parte do passo atual ($2^j \cdot b$) e somamos ao que já tínhamos guardado ali. Isso torna o algoritmo muito mais rápido e limpo.

### 3. O Truque do *Bitwise Shift* (`1 << j`)

Para calcular $2^j$ de forma extremamente rápida, usamos a operação de deslocamento de bits para a esquerda: `1 << j`.

* Quando `j = 0`: `1 << 0` resulta em $1$ ($2^0$).
* Quando `j = 1`: `1 << 1` resulta em $2$ ($2^1$).
* Quando `j = 2`: `1 << 2` resulta em $4$ ($2^2$).

Isso evita que precisemos usar métodos mais pesados como `Math.pow(2, j)`, que trabalham com números de ponto flutuante (`double`) e exigiriam conversões de tipo (*casting*).

### 4. Formatação da Saída

* Utilizamos o `System.out.print(...)` (sem o "ln") dentro do loop dos termos para garantir que todos os resultados daquela linha de consulta fiquem lado a lado, separados por um espaço em branco.
* Quando o loop interno termina de processar todos os $n$ termos, chamamos um `System.out.println()` vazio apenas para quebrar a linha e preparar o console para a próxima query do loop principal.



## Console