# 1. Populando um dicionário
Crie um dicionário usando todas as variáveis dadas.


```python
first_name = 'John'
last_name = 'Doe'
favorite_hobby = 'Python'
sports_hobby = 'gym'
age = 82
```


```python
# Sua implementação
my_dict = 
```


```python
assert my_dict == {
        'name': 'John Doe',
        'age': 82,
        'hobbies': ['Python', 'gym']
    }
```

# 2. Acessando e fundindo dicionários
2.1. Combinar `dict1`, `dict2`, e `dict3` em `my_dict`. 

2.2. Além disso, obtenha o valor de `special_key` a partir do `my_dict` em uma variável `special_value`. Note que os dicionários originais devem permanecer intocados e `special_key` deve ser removido do `my_dict`.


```python
dict1 = dict(key1='This is not that hard', key2='Python is still cool')
dict2 = {'key1': 123, 'special_key': 'secret'}
# Isso também é longe para inicializar um ditado(lista de tuplas) 
dict3 = dict([('key2', 456), ('keyX', 'X')])
```


```python
# 'Sua implementação'
my_dict = 
special_value = 
```


```python
assert my_dict == {'key1': 123, 'key2': 456, 'keyX': 'X'}
assert special_value == 'secret'

# Vamos verificar se os originais são intocados
assert dict1 == {
        'key1': 'This is not that hard',
        'key2': 'Python is still cool'
    }
assert dict2 == {'key1': 123, 'special_key': 'secret'}
assert dict3 == {'key2': 456, 'keyX': 'X'}
```

Retorne para a próxima demo [for-loops](../../02-demos/01-python-basic/06-for-loops.md)