# Java If-Else

Neste desafio, testamos seu conhecimento no uso de estruturas condicionais `if-else` para automatizar processos de tomada de decisão. Uma condicional `if-else` possui o seguinte fluxo lógico:

<p align="center">
  <img src="000-Midia_e_Anexos/2026-06-04-15-14-18.png" alt="" width="480">
</p>

## Tarefa

Dado um número inteiro $n$, realize as seguintes ações condicionais:

* Se $n$ for ímpar, imprima `Weird`
* Se $n$ for par e estiver no intervalo inclusivo de 2 a 5, imprima `Not Weird`
* Se $n$ for par e estiver no intervalo inclusivo de 6 a 20, imprima `Weird`
* Se $n$ for par e maior que 20, imprima `Not Weird`

Complete o stub de código fornecido em seu editor para imprimir se $n$ é ou não `weird`.

## Formato de Entrada

Uma única linha contendo um número inteiro positivo, $n$.

## Restrições

* $1 \le n \le 100$

## Formato de Saída

Imprima `Weird` se o número for *weird*; caso contrário, imprima `Not Weird`.

## Exemplo de Entrada 0

```text
3

```

## Exemplo de Saída 0

```text
Weird

```

## Exemplo de Entrada 1

```text
24

```

## Exemplo de Saída 1

```text
Not Weird

```

## Explicação

**Caso de Exemplo 0:** $n = 3$ é ímpar e números ímpares são considerados *weird*, portanto imprimimos `Weird`.

**Caso de Exemplo 1:** $n = 24$, sendo $n > 20$ e par, logo ele não é *weird*. Portanto, imprimimos `Not Weird`.

---

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



    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int N = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        scanner.close();
    }
}
```

---

## Solução

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int N = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        if (N % 2 != 0) {
            System.out.println("Weird");
        } else {
            if (N >= 2 && N <= 5) {
                System.out.println("Not Weird");
            } else if (N >= 6 && N <= 20) {
                System.out.println("Weird");
            } else if (N > 20) {
                System.out.println("Not Weird");
            }
        }

        scanner.close();
    }
}
```

### Saídas no Console

#### 🔹n = 3

<p align="center">
  <img src="000-Midia_e_Anexos/2026-06-04-15-23-33.png" alt="" width="100%">
</p>

#### 🔹n = 24

<p align="center">
  <img src="000-Midia_e_Anexos/2026-06-04-15-24-20.png" alt="" width="100%">
</p>

