# Desafio das Séries

Utilizamos os inteiros $a$, $b$ e $n$ para criar a seguinte série:

$$(a + 2^0 \cdot b), (a + 2^0 \cdot b + 2^1 \cdot b), \ldots, (a + 2^0 \cdot b + 2^1 \cdot b + \ldots + 2^{n-1} \cdot b)$$

## Formato de Entrada

A primeira linha contém um inteiro, $q$, denotando o número de seŕies.  
Cada linha $i$ das $q$ linhas subsequentes contém três inteiros separados por espaço que descrevem os respectivos valores de $a_i$, $b_i$ e $n_i$ para aquela consulta.

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