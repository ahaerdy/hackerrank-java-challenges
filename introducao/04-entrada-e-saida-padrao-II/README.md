# # Entrada e Saída Padrão II

Neste desafio, você deve ler um número inteiro (`integer`), um número de ponto flutuante (`double`) e uma `String` a partir do `stdin`, e então imprimir os valores de acordo com as instruções na seção **Formato de Saída** abaixo. Para tornar o problema um pouco mais fácil, uma parte do código já é fornecida para você no editor.

*Nota: Recomendamos concluir o desafio "Java Stdin and Stdout I" antes de tentar este.*

## Formato de Entrada

Existem três linhas de entrada:

1. A primeira linha contém um inteiro (`integer`).
2. A segunda linha contém um `double`.
3. A terceira linha contém uma `String`.

## Formato de Saída

Existem três linhas de saída:

1. Na primeira linha, imprima `String:` seguido pela `String` inalterada que foi lida do `stdin`.
2. Na segunda linha, imprima `Double:` seguido pelo `double` inalterado que foi lido do `stdin`.
3. Na terceira linha, imprima `Int:` seguido pelo inteiro inalterado que foi lido do `stdin`.

*Nota: Se você usar o método `nextLine()` imediatamente após o método `nextInt()`, lembre-se de que o `nextInt()` lê apenas tokens numéricos; por causa disso, o caractere de quebra de linha (`\n`) no final daquela linha de entrada inteira ainda permanece na fila do buffer de entrada, e o próximo `nextLine()` acabará lendo o restante dessa linha (que está vazia).*

## Exemplo de Entrada

```text
42
3.1415
Welcome to HackerRank's Java tutorials!
```

## Exemplo de Saída

```text
String: Welcome to HackerRank's Java tutorials!
Double: 3.1415
Int: 42
```