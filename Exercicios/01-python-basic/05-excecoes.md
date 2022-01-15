```python
# Execute isso primeiro!

import os

# Constantes para os exercícios:
WORKING_DIR = os.getcwd()
DATA_DIR = os.path.join(os.path.dirname(WORKING_DIR), 'data')
```

# 1. Números de soma listados em um arquivo
Preencha ____ partes do código abaixo. A função `sum_numbers_in_file` recebe um caminho de arquivo de entrada como argumento, lê os números listados no arquivo de entrada e retorna a soma desses números. Você pode supor que cada linha contém exatamente um valor numérico.


```python
def sum_numbers_in_file(input_file):
    sum_ = 0  # Uma maneira comum de usar nomes variáveis que colidem com palavras internas / palavras-chave é adicionar sublinhado
    with ____(input_file, ____) as ____:
        for line in ____:
            ____ = line.strip()  # Remover potencial espaço em branco
            ____ += float(____)
    return ____
```


```python
in_file = os.path.join(DATA_DIR, 'numbers.txt')
assert sum_numbers_in_file(in_file) == 189.5
```

# 2. Lendo a primeira palavra de cada linha de um arquivo
Implemente a função `find_first_words` que recebe um caminho de arquivo de entrada como argumento. A função deve encontrar a primeira palavra de cada linha no arquivo e retornar essas palavras como uma lista. Se uma linha estiver vazia, a lista retornada deverá conter uma string vazia para essa linha.


```python
# Sua implementação vai aqui
```


```python
in_file1 = os.path.join(DATA_DIR, 'simple_file.txt')
in_file2 = os.path.join(DATA_DIR, 'simple_file_with_empty_lines.txt')

expected_file_1 = ['First', 'Second', 'Third', 'And']
assert find_first_words(in_file1) == expected_file_1

expected_file_2 = ['The', '', 'First', 'nonsense', '', 'Then']
assert find_first_words(in_file2) == expected_file_2
```
