# 1. Preencha as peças que faltam da função `Count_even_numbers`
Preencha os `____` espaços da implementação de `count_even_numbers` para passar as afirmações.Você pode assumir que o argumento de "numbers" é uma lista de inteiros.


```python
____ count_even_numbers(numbers):
    count = 0
    for num in ____:
        if ____ % 2 == ____:
            count += ____
    _____ _____
```


```python
assert count_even_numbers([1, 2, 3, 4, 5, 6]) == 3
assert count_even_numbers([1, 3, 5, 7]) == 0
assert count_even_numbers([-2, 2, -10, 8]) == 4
```

# 2. Procurando por pessoas queridas
Implemente a função `find_wanted_people` que recebe uma lista de nomes (strings) como argumento. A função deve retornar uma lista de nomes que estão presentes tanto em `WANTED_PEOPLE` quanto na lista de nomes dada como argumento para a função.

```python
WANTED_PEOPLE = ['John Doe', 'Clint Eastwood', 'Chuck Norris']
```


```python
# Sua implementação vai aqui
```


```python
people_to_check1 = ['Donald Duck', 'Clint Eastwood', 'John Doe', 'Barack Obama']
wanted1 = find_wanted_people(people_to_check1)
assert len(wanted1) == 2
assert 'John Doe' in wanted1
assert 'Clint Eastwood'in wanted1

people_to_check2 = ['Donald Duck', 'Mickey Mouse', 'Zorro', 'Superman', 'Robin Hood']
wanted2 = find_wanted_people(people_to_check2)
assert wanted2 == []
```

# 3. Contando comprimento médio de palavras em uma frase
Crie uma função `average_length_of_words` que recebe uma string como argumento e retorna o comprimento médio das palavras na string. Você pode supor que há um único espaço entre cada palavra e que a entrada não possui pontuação. O resultado deve ser arredondado para uma casa decimal (dica: veja [`round`](https://docs.python.org/3/library/functions.html#round)).


```python
# Sua implementação vai aqui
```


```python
assert average_length_of_words('only four lett erwo rdss') == 4
assert average_length_of_words('one two three') == 3.7
assert average_length_of_words('one two three four') == 3.8
assert average_length_of_words('') == 0
```
