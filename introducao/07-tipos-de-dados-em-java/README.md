# Tipos Primitivos em Java

Em Java, existem 8 tipos primitivos: `char`, `boolean`, `byte`, `short`, `int`, `long`, `float` e `double`.  
Neste desafio, vamos focar nos tipos que armazenam números inteiros: `byte`, `short`, `int` e `long`.

- Um `byte` é um inteiro com sinal de 8 bits.  
- Um `short` é um inteiro com sinal de 16 bits.  
- Um `int` é um inteiro com sinal de 32 bits.  
- Um `long` é um inteiro com sinal de 64 bits.  

Sua tarefa é determinar quais desses tipos primitivos podem armazenar corretamente um número inteiro fornecido.

Mais detalhes podem ser encontrados na documentação oficial da Oracle [(docs.oracle.com)](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html).

## Formato de Entrada

- A primeira linha deve receber um inteiro `t`, representando o número de casos de teste.  
- Cada caso de teste consiste em uma única linha contendo um inteiro `n`, que pode ser arbitrariamente grande ou pequeno.

## Formato de Saída

Para cada número de entrada `n`, você deve determinar se os tipos primitivos são capazes de armazená-lo.  
Se sim, imprima o seguinte:

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

## Explicação

- O número `-150` pode ser armazenado em um `short`, em um `int` ou em um `long`.  
- O número `2133333333333333333333333333333333333333` é extremamente grande e está fora do intervalo permitido para os tipos primitivos discutidos neste problema.  
- Já o número `-100000000000000` cabe dentro de um `long`, mas não em `int`, `short` ou `byte`.

Essa análise mostra como diferentes tipos primitivos em Java possuem limites distintos de armazenamento, e por isso é necessário verificar cuidadosamente em qual intervalo cada número se encaixa.

## Template Inicial do Desafio

```java
import java.util.*;
import java.io.*;

class Solution{
    public static void main(String []argh)
    {
        Scanner sc = new Scanner(System.in);
        int t=sc.nextInt();

        for(int i=0;i<t;i++)
        {
            try
            {
                long x=sc.nextLong();
                System.out.println(x+" can be fitted in:");
                if(x>=-128 && x<=127)System.out.println("* byte");
                //Complete the code
            }
            catch(Exception e)
            {
                System.out.println(sc.next()+" can't be fitted anywhere.");
            }

        }
    }
}
```

## Solução

```java
import java.util.*;
import java.io.*;

class Solution {
    public static void main(String []argh) {
        // Inicializa o Scanner para ler a entrada padrão (teclado/arquivo de teste)
        Scanner sc = new Scanner(System.in);
        
        // Lê a quantidade de casos de teste (t)
        int t = sc.nextInt();

        // Loop para processar cada caso de teste individualmente
        for (int i = 0; i < t; i++) {
            try {
                // Tenta ler o próximo número diretamente como um tipo 'long' (64 bits).
                // Se o número for maior que o limite de um long (ou menor), 
                // o Scanner lançará uma exceção 'InputMismatchException', disparando o bloco catch.
                long x = sc.nextLong();
                
                // Se chegou aqui, o número cabe pelo menos em um 'long'
                System.out.println(x + " can be fitted in:");
                
                // Verifica os limites do tipo 'byte' (8 bits: -128 a 127)
                if (x >= Byte.MIN_VALUE && x <= Byte.MAX_VALUE) {
                    System.out.println("* byte");
                }
                
                // Verifica os limites do tipo 'short' (16 bits: -32.768 a 32.767)
                if (x >= Short.MIN_VALUE && x <= Short.MAX_VALUE) {
                    System.out.println("* short");
                }
                
                // Verifica os limites do tipo 'int' (32 bits: -2.147.483.648 a 2.147.483.647)
                if (x >= Integer.MIN_VALUE && x <= Integer.MAX_VALUE) {
                    System.out.println("* int");
                }
                
                // Como o sc.nextLong() não estourou, o número com certeza cabe em um 'long' (64 bits)
                if (x >= Long.MIN_VALUE && x <= Long.MAX_VALUE) {
                    System.out.println("* long");
                }
                
            } catch (Exception e) {
                // Se o número digitado ultrapassou os limites do tipo 'long' (estouro de bits),
                // sc.nextLong() falha. Capturamos o token inválido usando sc.next() para exibi-lo.
                System.out.println(sc.next() + " can't be fitted anywhere.");
            }
        }
        
        sc.close(); // Boa prática: fecha o scanner após o uso
    }
}
```

## Explicação Detalhada do Código

O desafio central deste exercício é lidar com **estouro de capacidade (overflow/underflow)** e entender como a arquitetura do Java gerencia os tipos inteiros primitivos.

### 1. A Estratégia de Captura com `try-catch`

A maior armadilha desse problema está nos números que não cabem nem mesmo no maior tipo primitivo inteiro disponível (`long`).

* Se tentássemos ler a entrada como uma string simples ou um `BigInteger` para fazer todas as validações manualmente, gastaríamos mais processamento e linhas de código.
* Em vez disso, usamos o próprio comportamento do `Scanner`. O método `sc.nextLong()` tenta converter a entrada em um inteiro de 64 bits. Se o número for absurdamente grande (como `213333333333333333333333333333333333`), a leitura falha imediatamente e o fluxo é desviado para o bloco `catch`.
* No `catch`, usamos `sc.next()` para recuperar o "token" (o texto do número gigante) que o `nextLong()` rejeitou e imprimimos a mensagem padrão de erro.

### 2. Uso das Classes Wrapper (`Byte`, `Short`, `Integer`, `Long`)

No template inicial do desafio, o exemplo trazia valores fixos literais: `if(x>=-128 && x<=127)`. Embora correto para o `byte`, decorar ou digitar manualmente os valores máximos e mínimos de `int` e `long` é propenso a erros de digitação.

Para tornar o código limpo, profissional e legível, utilizamos as **Constantes Embutidas** das classes utilitárias do Java:

* `Byte.MIN_VALUE` (-128) e `Byte.MAX_VALUE` (127)
* `Short.MIN_VALUE` (-32768) e `Short.MAX_VALUE` (32767)
* `Integer.MIN_VALUE` ($-2^{31}$) e `Integer.MAX_VALUE` ($2^{31} - 1$)
* `Long.MIN_VALUE` ($-2^{63}$) e `Long.MAX_VALUE` ($2^{63} - 1$)

### 3. Estrutura de Condicionais Independentes

Note que **não** utilizamos `else if`. Como o enunciado exige que listemos *todos* os tipos nos quais o número se encaixa, em ordem crescente de tamanho, precisamos testar cada limite de forma independente.

Se um número for `-150`:

* Não entra no `if` do `byte`.
* Entra no `if` do `short` $\rightarrow$ Imprime `* short`
* Entra no `if` do `int` $\rightarrow$ Imprime `* int`
* Entra no `if` do `long` $\rightarrow$ Imprime `* long`

O fluxo garante a ordenação e a precisão exigidas pela saída do problema.