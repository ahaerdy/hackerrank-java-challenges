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
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt(); // Lê o número de casos de teste

        for (int i = 0; i < t; i++) {
            try {
                long x = sc.nextLong(); // Tenta ler o número como long
                System.out.println(x + " can be fitted in:");

                // Verifica se cabe em byte (-128 a 127)
                if (x >= -128 && x <= 127) System.out.println("* byte");

                // Verifica se cabe em short (-32768 a 32767)
                if (x >= -32768 && x <= 32767) System.out.println("* short");

                // Verifica se cabe em int (-2^31 a 2^31 - 1)
                if (x >= -2147483648 && x <= 2147483647) System.out.println("* int");

                // Verifica se cabe em long (-2^63 a 2^63 - 1)
                if (x >= -9223372036854775808L && x <= 9223372036854775807L) System.out.println("* long");

            } catch (Exception e) {
                // Caso o número seja grande demais para caber em long
                System.out.println(sc.next() + " can't be fitted anywhere.");
            }
        }
    }
}
```

### Detalhamento

1. **Leitura dos casos de teste**  
   A primeira linha da entrada contém `t`, o número de casos de teste. O programa usa um laço `for` para processar cada número.

2. **Uso de `try-catch`**  
   - Dentro do `try`, o programa tenta ler o número como `long`.  
   - Se o número for maior que o limite de `long`, ocorre uma exceção, e o `catch` imprime que o valor não pode ser armazenado em nenhum tipo primitivo.

3. **Verificação dos intervalos**  
   - Cada tipo primitivo tem um intervalo fixo:
     - `byte`: -128 a 127  
     - `short`: -32.768 a 32.767  
     - `int`: -2.147.483.648 a 2.147.483.647  
     - `long`: -9.223.372.036.854.775.808 a 9.223.372.036.854.775.807  
   - O programa compara o valor `x` com esses limites e imprime todos os tipos nos quais ele cabe.

4. **Saída formatada**  
   - Se o número cabe em algum tipo, imprime:
     ```
     n can be fitted in:
     * tipo
     ```
   - Se não cabe em nenhum, imprime:
     ```
     n can't be fitted anywhere.
     ```

---


## Console