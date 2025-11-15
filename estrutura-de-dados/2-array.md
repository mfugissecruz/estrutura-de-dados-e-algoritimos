# Arrays Primitivos: Entendendo a Base da Computação

## Teoria Simplificada

### O que é um array primitivo?

Um array primitivo é simplesmente uma **fileira de gavetas** coladas uma na outra na memória do computador. Cada gaveta tem exatamente o mesmo tamanho e guarda um valor.

```
Gaveta 0 | Gaveta 1 | Gaveta 2 | Gaveta 3
   [5]   |   [10]   |   [15]   |   [20]
```

### Memória contígua

A palavra "contíguo" significa que as gavetas estão **grudadas**, sem espaço entre elas:

```
Endereço 1000: [5]
Endereço 1004: [10]  ← logo depois
Endereço 1008: [15]  ← logo depois
Endereço 1012: [20]  ← logo depois
```

### Por que é tão rápido?

Para achar qualquer elemento, o computador faz apenas uma conta:

```
Posição do arr[2] = endereço_inicial + (índice × tamanho_elemento)
Posição do arr[2] = 1000 + (2 × 4) = 1008
```

Uma única multiplicação e soma. Isso é **O(1)** - tempo constante, não importa o tamanho do array.

### Características fundamentais

1. **Tamanho fixo** - definido na criação, não muda
2. **Tipo fixo** - todos os elementos têm o mesmo tamanho
3. **Sem metadados** - apenas os dados brutos, nada mais
4. **Sem proteções** - não verifica se você acessou posição inválida

## Utilização Prática

### Declarando e usando arrays em C

```c
#include <stdio.h>

int main() {
    // Declara um array de 5 inteiros
    int numeros[5];

    // Preenche o array
    numeros[0] = 10;
    numeros[1] = 20;
    numeros[2] = 30;
    numeros[3] = 40;
    numeros[4] = 50;

    // Lê valores do array
    printf("Primeiro elemento: %d\n", numeros[0]);
    printf("Terceiro elemento: %d\n", numeros[2]);

    // Percorre o array
    for(int i = 0; i < 5; i++) {
        printf("numeros[%d] = %d\n", i, numeros[i]);
    }

    return 0;
}
```

### Exemplo com loop de preenchimento

```c
#include <stdio.h>

int main() {
    int valores[10];

    // Preenche com múltiplos de 5
    for(int i = 0; i < 10; i++) {
        valores[i] = (i + 1) * 5;
    }

    // Exibe os valores
    for(int i = 0; i < 10; i++) {
        printf("%d ", valores[i]);
    }
    // Saída: 5 10 15 20 25 30 35 40 45 50

    return 0;
}
```

### Cuidados importantes

```c
int arr[3];

// ✅ CORRETO
arr[0] = 1;
arr[1] = 2;
arr[2] = 3;

// ❌ PERIGO! Acessa memória inválida
arr[5] = 99;  // Comportamento indefinido
arr[-1] = 10; // Também é perigoso
```

O compilador C **não verifica** se você está acessando posições válidas. Isso pode causar:

- Crashes do programa
- Corrupção de dados
- Bugs difíceis de rastrear

## Desafio

### Desafio 1: Soma de elementos

Crie um programa que:

1. Declare um array de 8 inteiros
2. Preencha com os valores: 2, 4, 6, 8, 10, 12, 14, 16
3. Calcule e exiba a soma de todos os elementos

**Resultado esperado:** `72`

### Desafio 2: Encontrar o maior valor

Escreva um programa que:

1. Declare um array com os valores: 45, 12, 78, 23, 91, 34, 67
2. Encontre e exiba o maior valor do array
3. Exiba também a posição (índice) onde ele está

**Resultado esperado:** `Maior valor: 91 na posição 4`

### Desafio 3: Inverter array

Crie um programa que:

1. Declare um array: [1, 2, 3, 4, 5]
2. Inverta a ordem dos elementos **no próprio array** (sem criar outro)
3. Exiba o array invertido

**Resultado esperado:** `[5, 4, 3, 2, 1]`

**Dica:** Use uma variável temporária para trocar os valores de posição.

---

**Próximo passo:** Tente resolver os desafios sem olhar soluções prontas. A prática com arrays primitivos é fundamental para entender estruturas de dados mais complexas!
