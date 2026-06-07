# Loops em Java I

## Objetivo

Neste desafio, vamos usar laços de repetição (*loops*) para nos ajudar a realizar algumas operações matemáticas simples.

## Tarefa

Dado um número inteiro $N$, imprima os seus primeiros 10 múltiplos. Cada múltiplo $i$ (onde $1 \le i \le 10$) deve ser impresso em uma nova linha no formato: `N x i = resultado`.

## Formato de Entrada

Um único número inteiro, $N$.

## Restrições

* $2 \le N \le 20$

## Formato de Saída

Imprima 10 linhas de saída; cada linha $i$ (onde $1 \le i \le 10$) deve conter o resultado de $N \times i$ no formato:
`N x i = resultado`.

## Exemplo de Entrada

```text
2

```

## Exemplo de Saída

```text
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
2 x 10 = 20

```

## Template Inicial do Desafio

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;



public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(bufferedReader.readLine().trim());

        bufferedReader.close();
    }
}
```

## Solução



## Console