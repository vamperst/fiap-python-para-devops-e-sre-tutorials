# [`for` loops](https://docs.python.org/3/tutorial/controlflow.html#for-statements)

## Iterando listas


```python
my_list = [1, 2, 3, 4, 'Python', 'is', 'neat']
for item in my_list:
    print(item)
```

### `break`
Pare a execução do loop.


```python
for item in my_list:
    if item == 'Python':
        break
    print(item)
```

### `continue`
Continue para o próximo item sem executar as linhas que ocorrem após `continue` dentro do loop.


```python
for item in my_list:
    if item == 1:
        continue
    print(item)
```

### `enumerate()`
Caso você precise conhecer também o índice:


```python
for idx, val in enumerate(my_list):
    print('idx: {}, value: {}'.format(idx, val))
```

## Iterando dicionários


```python
my_dict = {'hacker': True, 'age': 72, 'name': 'John Doe'}
for val in my_dict:
    print(val)
```


```python
for key, val in my_dict.items():
    print('{}={}'.format(key, val))
```

## `range()`


```python
for number in range(5):
    print(number)
```


```python
for number in range(2, 5):
    print(number)
```


```python
for number in range(0, 10, 2):
    print(number)
```
