# Lendo da Entrada Padrão (stdin)

A maioria dos desafios do HackerRank exige que você leia a entrada a partir de `stdin` (entrada padrão) e escreva a saída em `stdout` (saída padrão).

Uma maneira popular de ler a entrada de `stdin` é usando a classe `Scanner` e especificando o fluxo de entrada como `System.in`. Por exemplo:

```java
Scanner scanner = new Scanner(System.in);
String myString = scanner.next();
int myInt = scanner.nextInt();
scanner.close();

System.out.println("myString is: " + myString);
System.out.println("myInt is: " + myInt);

```

O código acima cria um objeto `Scanner` e o utiliza para ler uma `String` e um `int`. Em seguida, ele fecha o objeto `Scanner` porque não há mais entrada a ser lida, e imprime no `stdout` usando `System.out.println(String).` Portanto, se a nossa entrada for:

```text
Hi 5

```

O nosso código irá imprimir:

```text
myString is: Hi
myInt is: 5

```

Alternativamente, você pode usar a classe `BufferedReader`.

## Tarefa

Neste desafio, você deve ler $3$ inteiros de `stdin` e, em seguida, imprimi-los em `stdout`. Cada inteiro deve ser impresso em uma nova linha. Para tornar o problema um pouco mais fácil, uma parte do código já é fornecida para você no editor abaixo.

## Formato de Entrada

Existem $3$ linhas de entrada, e cada linha contém um único inteiro.

## Exemplo de Entrada

```text
42
100
125

```

## Exemplo de Saída

```text
42
100
125

```

---

## Template Inicial do Desafio

## Solução

```java
import java.util.*;

public class Solution {

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int a = scan.nextInt();
        int b = scan.nextInt();
        int c = scan.nextInt();
        scan.close();

        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
    }
}
```

### Saída no Console

<p align="center">
  <img src="000-Midia_e_Anexos/2026-06-04-14-07-38.png" alt="" width="480">
</p>
