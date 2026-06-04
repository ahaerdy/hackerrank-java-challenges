# Bem-vindo ao Java!

Bem-vindo ao mundo do Java! Neste desafio, praticamos a impressão no `stdout`.

Os stubs de código em seu editor declaram uma classe `Solution` e um método `main`. Complete o método `main` copiando as duas linhas de código abaixo e colando-as dentro do corpo do seu método `main`.

```java
System.out.println("Hello, World.");
System.out.println("Hello, Java.");

```

## Formato de Entrada

Não existe entrada para este desafio.

## Formato de Saída

Você deve imprimir duas linhas de saída:

1. Imprima `Hello, World.` na primeira linha.
2. Imprima `Hello, Java.` na segunda linha.

## Exemplo de Saída

```text
Hello, World.
Hello, Java.
```

---

## Template Inicial do Desafio

```java
public class Solution {

    public static void main(String[] args) {
        /* Enter your code here. Print output to STDOUT. Your class should be named Solution. */

    }
}
```

--- 

## ✅ Solução

```java
public class Solution {

    public static void main(String[] args) {
        /* Enter your code here. Print output to STDOUT. Your class should be named Solution. */
        System.out.println("Hello, World.");
        System.out.println("Hello, Java.");
    }
}
```

### Saída no Console

<p align="center">
  <img src="000-Midia_e_Anexos/2026-06-04-14-07-38.png" alt="" width="100%">
</p>

---

### Observação: O Conceito de "Delimitador" no Scanner

Por padrão, a classe `Scanner` utiliza uma expressão regular que representa **qualquer espaço em branco** como separador (*delimitador*) para dividir a entrada em partes (chamadas de *tokens*).

Na linguagem Java, "espaço em branco" (whitespace) engloba vários caracteres, incluindo:

* O espaço simples (` `)
* A quebra de linha (`\n` ou `\r\n`, gerada pelo `<Enter>`)
* O tabulador (`\t`)

Portanto, para o método `nextInt()`, não importa se o próximo número está do lado ou na linha de baixo; ele simplesmente ignora todos os espaços em branco anteriores, lê o número e para assim que encontra o próximo espaço em branco.

---

#### Os dois cenários de execução

##### Cenário 1: Separados por Espaço

Se você digitar na console:
`42 100 125[Enter]`

O `Scanner` enxerga um único fluxo de texto.

1. O primeiro `nextInt()` consome `42` e para no espaço.
2. O segundo `nextInt()` pula o espaço, consome `100` e para no próximo espaço.
3. O terceiro `nextInt()` pula o espaço, consome `125` e para na quebra de linha.

##### Cenário 2: Separados por Enter

Se você digitar na console:
`42[Enter]`
`100[Enter]`
`125[Enter]`

O comportamento do código é idêntico:

1. O primeiro `nextInt()` consome `42` e para na quebra de linha.
2. O segundo `nextInt()` ignora a quebra de linha, consome `100` e para na próxima quebra.
3. O terceiro faz o mesmo com o `125`.

---

#### De onde vem essa confusão comum?

Essa percepção de que "deve ser na mesma linha" geralmente acontece por dois motivos:

1. **Uso misto com `nextLine()`:** Se o seu código tivesse um `scan.nextLine()` logo após um `nextInt()`, o comportamento quebraria ao usar o `<Enter>`. Isso ocorre porque o `nextInt()` consome o número mas **deixa a quebra de linha (`\n`) para trás no buffer**. O `nextLine()` subsequente capturaria essa quebra de linha vazia imediatamente, parecendo que o programa "pulou" uma leitura. Como o seu código só usa `nextInt()`, esse problema não acontece.
2. **Plataformas de Desafios (como HackerRank ou Beecrowd):** Muitas vezes os exemplos de entrada de dados (*Input Format*) desses sites são ilustrados em uma única linha de texto para economizar espaço na tela, induzindo o desenvolvedor a achar que o código só funciona daquela forma estrita.

Em resumo: seu código está robusto e pronto para tratar os números de ambas as formas!

---

