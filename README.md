# Algoritmo de Verificação de Números Primos e Encontrar Divisores

Este é um algoritmo em C++ que verifica se um número é primo e, caso não seja, encontra todos os seus divisores.

## Funcionamento

O algoritmo é composto por três funções principais:

1. `encontrar_divisores(vector<int>& lista, int n)`: Esta função recebe um vetor por referência (`lista`) e um número inteiro (`n`). Ela é responsável por encontrar todos os divisores de `n` e adicioná-los ao vetor `lista`.

2. `verificarPrimo(int n)`: Esta função recebe um número inteiro (`n`) e verifica se ele é primo. Retorna `true` se `n` for primo e `false` caso contrário.

3. `main()`: A função principal do programa, onde a execução começa.

### Função `encontrar_divisores`

A função `encontrar_divisores` utiliza um loop para percorrer todos os números de 1 até a raiz quadrada de `n`. Para cada número `i`, ela verifica se `i` é um divisor de `n` usando a operação de módulo (`n % i == 0`). Se `i` for um divisor, ele é adicionado ao vetor `lista` usando o método `push_back()`.

Além disso, se `i` não for a raiz quadrada exata de `n`, o outro divisor correspondente (`n / i`) também é adicionado ao vetor `lista`. Isso garante que todos os divisores sejam encontrados.

### Função `verificarPrimo`

A função `verificarPrimo` verifica se um número `n` é primo. Ela começa verificando se `n` é menor ou igual a 1, pois números menores ou iguais a 1 não são considerados primos. Se `n` for menor ou igual a 1, a função retorna `false`.

Em seguida, a função utiliza um loop para percorrer todos os números de 2 até a raiz quadrada de `n`. Se algum número `i` for um divisor de `n` (ou seja, se `n % i == 0`), significa que `n` não é primo e a função retorna `false`.

Se o loop terminar sem encontrar nenhum divisor, significa que `n` é primo e a função retorna `true`.

### Função `main`

Na função `main()`, o número `n` é definido como 10 (você pode alterar esse valor para testar outros números). Um vetor vazio chamado `divisores` é criado para armazenar os divisores de `n`, caso `n` não seja primo.

Em seguida, a função `verificarPrimo` é chamada passando `n` como argumento. Se `n` for primo, a mensagem "Primo." é impressa na tela. Caso contrário, a função `encontrar_divisores` é chamada, passando o vetor `divisores` e o número `n` como argumentos, para encontrar todos os divisores de `n`.

Por fim, um loop `for` é usado para percorrer todos os elementos do vetor `divisores` e imprimi-los na tela.

## Exemplo de Uso

Ao executar o programa com `n = 10`, a saída será:

```
1 10 2 5 
```

Isso indica que 10 não é um número primo e seus divisores são 1, 10, 2 e 5.

Se você alterar o valor de `n` para um número primo, como 7, a saída será:

```
Primo.
```

Isso indica que 7 é um número primo.

## Conclusão

Este algoritmo é útil para verificar se um número é primo e encontrar seus divisores caso não seja. Ele utiliza conceitos básicos de C++, como loops, condicionais e vetores, para realizar essas tarefas de forma eficiente.

```cpp
#include<bits/stdc++.h>
using namespace std;

void encontrar_divisores(vector<int>& lista, int n){
    for(int i = 1; i * i <= n; i++){
        if(n % i == 0){
            lista.push_back(i);
            if(i * i != n){
                lista.push_back(n / i);
            }
        }
    }
}

bool verificarPrimo(int n){
    if(n <= 1) return false;
    for(int i = 2; i * i <= n; i++){
        if(n % i == 0)
            return false;
    }
    return true;
}

int main()
{
    int n = 10;
    vector<int> divisores;
    
    if(verificarPrimo(n) == true){
        cout << "Primo." << endl;
    }else{
        encontrar_divisores(divisores, n);
    }
    
    for(auto const elemento : divisores){
        cout << elemento << " ";
    }
    cout << endl;
    
    return 0;
}

```
