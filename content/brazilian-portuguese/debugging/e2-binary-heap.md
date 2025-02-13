---
title: "Exercício 2 - Implementação de Heap Binário"
difficulty: "Intermediário"
weight: 100
draft: false
---

Um heap binário é uma estrutura de dados importante usada com mais frequência para implementar um tipo de dados chamado fila de prioridade. Também é usado conceitualmente no algoritmo de ordenação chamado heapsort. Sua característica distintiva é a consulta `O(1)` para o maior ou menor valor dentro de seu conteúdo, dependendo de que tipo de heap estamos falando.

## A Teoria

O heap binário é conceitualmente uma árvore binária completa. Isso significa que os nós são adicionados à árvore em ordem de nível, e a profundidade da árvore aumenta apenas quando não há espaço no nível mais profundo da árvore.

Além dessa restrição estrutural, ela segue a propriedade de ordenação do heap: os filhos de um nó devem ter um valor maior ou menor que o próprio nó. Em um **min-heap**, os filhos devem ser maiores. Em um **max-heap**, os filhos devem ser menores. Efetivamente, isso significa que a raiz deve conter o maior elemento na pilha.

Veja a seguir um exemplo de heap binário máximo, que é o tipo de heap no qual vamos nos concentrar neste exercício.

![Exemplo de heap binário](../resources/e2-01.png)

Você pode ver que cada nó tem 2 ou nenhum filho, exceto o nó mais à direita. Os nós são preenchidos da esquerda para a direita antes de iniciar uma nova linha. Todos os filhos são menores que seus pais.

{{% notice note %}}
Duplicatas são facilmente tratadas neste esquema. Precisamos sustentar que todos os filhos são realmente menores que *ou iguais* a seus pais.
{{% /notice %}}

Podemos usar um array para representar essa estrutura de dados. Um nó i pode ser acessado por seu índice, i. Para acessar o filho esquerdo, multiplique por 2. Para acessar o filho direito, multiplique por 2 e some 1. O diagrama a seguir ilustra isso:

![Matriz de pilha binária](../resources/e2-02.png)

### Adicionando a um heap binário

Para adicionar um elemento, primeiro o adicionamos ao próximo local disponível. Em seguida, “consertamos” retroativamente quaisquer problemas causados por isso, deslizando-o para cima e trocando os nós até atingir uma posição estável, ou seja, seu pai é maior ou igual a si mesmo.

O diagrama abaixo ilustra este processo para adicionar `34` ao heap binário de exemplo.
1. Nós inserimos `34` no último slot provisoriamente (círculo verde, passo 1).
2. Em seguida, comparamos com seu pai (seta azul) e descobrimos que `34 > 19`. Assim, trocamos os dois nós.
3. Na etapa 2, comparamos com `85` e descobrimos que `34 < 85`, o que indica que terminamos.

![Adição de pilha binária](../resources/e2-03.png)

### Removendo o Max do Heap

Um heap binário máximo também precisa suportar `removeMax`, que remove o maior elemento do heap. Felizmente, o maior elemento é simplesmente a raiz; no entanto, precisamos consertar os problemas causados por esse novo buraco que fizemos.

Para preencher esse buraco, pegamos o último elemento e o preenchemos até o topo. Como antes, “consertamos” retroativamente quaisquer problemas que isso cause. Realizamos repetidamente trocas para baixo com o filho menor até que ele atinja uma posição estável na pilha.

O diagrama abaixo mostra como ocorre uma remoção máxima.
1. A raiz é removida e colocada com o elemento mais à direita na linha inferior.
2. No passo 1, comparamos `19` e `42`. Como `42` é o maior dos 2, comparamos `12` e `42` (seta azul) e encontramos `12 < 42`. Assim, trocamos `12` por `42`.
3. Repetimos o processo para a etapa 2. Descobrimos que `28` é o maior dos 2 filhos e, como `12 < 28`, trocamos novamente.
4. Finalmente alcançamos uma posição estável para o passo 3.

![Remoção de pilha binária](../resources/e2-04.png)

## A implementação

Em nossa implementação, começamos a indexação de `1` para economizar um pouco de computação. Portanto, a raiz do heap binário está localizada em `heap.__arr[1]` em vez de `heap.__arr[0]`. Todas as funções possuem comentários sobre sua função em `binary_heap.h`.

A implementação **será** testada contra duplicatas, portanto, certifique-se de lidar com elas. Além disso, enquanto o tamanho do heap é fixo, os dados são armazenados no heap. Certifique-se de que os dados estejam `livres`'!

{{% notice tip %}}
As funções `createHeap` e `heapPrint` já foram testadas e seu funcionamento foi verificado.
{{% /notice %}}

Seu objetivo é executar `make test` e não ter erros. Use qualquer ferramenta, como `gdb`, `valgrind`, etc. a seu favor. Boa sorte!

<a class="my-2 mx-4 btn btn-info" href="https://replit.com/@nuevofoundation/Debugging-Exercise-2" target="_blank">Executar Replit</a>