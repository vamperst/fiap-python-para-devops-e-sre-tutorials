# Condicionais

## Testando booleano

### `bool`


```python
print('type of True and False: {}'.format(type(True)))
```


```python
print('0: {}, 1: {}'.format(bool(0), bool(1)))
print('empty list: {}, list with values: {}'.format(bool([]), bool(['woop'])))
print('empty dict: {}, dict with values: {}'.format(bool({}), bool({'Python': 'cool'})))
```

### `==, !=, >, <, >=, <=`


```python
print('1 == 0: {}'.format(1 == 0))
print('1 != 0: {}'.format(1 != 0))
print('1 > 0: {}'.format(1 > 0))
print('1 > 1: {}'.format(1 > 1))
print('1 < 0: {}'.format(1 < 0))
print('1 < 1: {}'.format(1 < 1))
print('1 >= 0: {}'.format(1 >= 0))
print('1 >= 1: {}'.format(1 >= 1))
print('1 <= 0: {}'.format(1 <= 0))
print('1 <= 1: {}'.format(1 <= 1))
```

Você pode combinar estes:


```python
print('1 <= 2 <= 3: {}'.format(1 <= 2 <= 3))
```

### `and, or, not`


```python
python_is_cool = True
java_is_cool = False
empty_list = []
secret_value = 3.14
```


```python
print('Python and java are both cool: {}'.format(python_is_cool and java_is_cool))
print('secret_value and python_is_cool: {}'.format(secret_value and python_is_cool))
```


```python
print('Python or java is cool: {}'.format(python_is_cool or java_is_cool))
print('1 >= 1.1 or 2 < float("1.4"): {}'.format(1 >= 1.1 or 2 < float('1.4')))
```


```python
print('Java is not cool: {}'.format(not java_is_cool))
```

Você pode combinar várias instruções, a ordem de execução é da esquerda para a direita. Você pode controlar a ordem de execução usando colchetes.


```python
print(bool(not java_is_cool or secret_value and  python_is_cool or empty_list))
print(bool(not (java_is_cool or secret_value and  python_is_cool or empty_list)))
```

## `if`


```python
statement = True
if statement:
    print('statement is True')
    
if not statement:
    print('statement is not True')
```


```python
empty_list = []
# Com if e elif, a conversão para `bool` é implícita
if empty_list:
    print('empty list will not evaluate to True')  # Isso não 
```


```python
val = 3
if 0 <= val < 1 or val == 3:
    print('Value is positive and less than one or value is three')
```

## `if-else`


```python
my_dict = {}
if my_dict:
    print('there is something in my dict')
else:
    print('my dict is empty :(')
```

## `if-elif-else`


```python
val = 88
if val >= 100:
    print('value is equal or greater than 100')
elif val > 10:
    print('value is greater than 10 but less than 100')
else:
    print('value is equal or less than 10')
```

Você pode ter quantas instruções `elif` precisar. Além disso, `else` no final não é obrigatório.


```python
greeting = 'Hello fellow Pythonista!'
language = 'Italian'

if language == 'Swedish':
    greeting = 'Hejsan!'
elif language == 'Finnish':
    greeting = 'Latua perkele!'
elif language == 'Spanish':
    greeting = 'Hola!'
elif language == 'German':
    greeting = 'Guten Tag!'
    
print(greeting)
```

Para uma visão mais detalhada sobre condicionais, verifique este [tutorial Real Python](https://realpython.com/python-conditional-statements/).
