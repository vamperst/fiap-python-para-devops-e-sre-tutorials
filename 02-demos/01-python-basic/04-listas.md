# [Listas](https://docs.python.org/3/library/stdtypes.html#lists)


```python
my_empty_list = []
print('empty list: {}, type: {}'.format(my_empty_list, type(my_empty_list)))
```


```python
list_of_ints = [1, 2, 6, 7]
list_of_misc = [0.2, 5, 'Python', 'is', 'still fun', '!']
print('lengths: {} and {}'.format(len(list_of_ints), len(list_of_misc)))
```

## Acessando valores


```python
my_list = ['Python', 'is', 'still', 'cool']
print(my_list[0])
print(my_list[3])
```


```python
coordinates = [[12.0, 13.3], [0.6, 18.0], [88.0, 1.1]]  # two dimensional
print('first coordinate: {}'.format(coordinates[0]))
print('second element of first coordinate: {}'.format(coordinates[0][1]))
```

## Atualizando valores


```python
my_list = [0, 1, 2, 3, 4, 5]
my_list[0] = 99
print(my_list)

# Remover primeiro valor
del my_list[0]
print(my_list)
```

## Verificando se determinado valor está presente na lista


```python
languages = ['Java', 'C++', 'Go', 'Python', 'JavaScript']
if 'Python' in languages:
    print('Python is there!')
```


```python
if 6 not in [1, 2, 3, 7]:
    print('number 6 is not present')
```

## A lista é mutável


```python
original = [1, 2, 3]
modified = original
modified[0] = 99
print('original: {}, modified: {}'.format(original, modified))
```

Você pode contornar isso criando uma nova `list`:


```python
original = [1, 2, 3]
modified = list(original)  # Note list() 
# Alternativamente, você pode usar o método de cópia
# modified = original.copy()
modified[0] = 99
print('original: {}, modified: {}'.format(original, modified))
```

## `list.append()`


```python
my_list = [1]
my_list.append('ham')
print(my_list)
```

## `list.remove()`


```python
my_list = ['Python', 'is', 'sometimes', 'fun']
my_list.remove('sometimes')
print(my_list)

# Se você não tiver certeza de que o valor está na lista, é melhor verificar primeiro:
if 'Java' in my_list:
    my_list.remove('Java')
else:
    print('Java is not part of this story.')
```

## `list.sort()`


```python
numbers = [8, 1, 6, 5, 10]
numbers.sort()
print('numbers: {}'.format(numbers))

numbers.sort(reverse=True)
print('numbers reversed: {}'.format(numbers))

words = ['this', 'is', 'a', 'list', 'of', 'words']
words.sort()
print('words: {}'.format(words))
```

## `sorted(list)`
While `list.sort()` sorts the list in-place, `sorted(list)` returns a new list and leaves the original untouched:


```python
numbers = [8, 1, 6, 5, 10]
sorted_numbers = sorted(numbers)
print('numbers: {}, sorted: {}'.format(numbers, sorted_numbers))
```

## `list.extend()`


```python
first_list = ['beef', 'ham']
second_list = ['potatoes',1 ,3]
first_list.extend(second_list)
print('first: {}, second: {}'.format(first_list, second_list))
```

Alternativamente, você também pode estender listas somando-as:


```python
first = [1, 2, 3]
second = [4, 5]
first += second
print('first: {}'.format(first))

# Se precisar de uma nova lista
summed = first + second
print('summed: {}'.format(summed))
```

## `list.reverse()`


```python
my_list = ['a', 'b', 'ham']
my_list.reverse()
print(my_list)
```

Exercicio de listas: [clique aqui](../../03-Exercicios/01-python-basic/02-listas.md)