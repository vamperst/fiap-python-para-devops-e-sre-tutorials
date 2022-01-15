# [Dictionaries](https://docs.python.org/3/library/stdtypes.html#dict) 
Collections of `key`-`value` pairs. 


```python
my_empty_dict = {}  # alternativa: my_empty_dict = dict()
print('dict: {}, type: {}'.format(my_empty_dict, type(my_empty_dict)))
```

## Inicialização


```python
dict1 = {'value1': 1.6, 'value2': 10, 'name': 'John Doe'}
dict2 = dict(value1=1.6, value2=10, name='John Doe')

print(dict1)
print(dict2)

print('equal: {}'.format(dict1 == dict2))
print('length: {}'.format(len(dict1)))
```

## `dict.keys(), dict.values(), dict.items()`


```python
print('keys: {}'.format(dict1.keys()))
print('values: {}'.format(dict1.values()))
print('items: {}'.format(dict1.items()))
```

## Acessando e configurando valores


```python
my_dict = {}
my_dict['key1'] = 'value1'
my_dict['key2'] = 99
my_dict['key1'] = 'new value'  # overriding existing value
print(my_dict)
print('value of key1: {}'.format(my_dict['key1']))
```

Acessar uma chave inexistente irá gerar `KeyError` (veja [`dict.get()`](#dict_get) para solução alternativa):


```python
# print(my_dict['nope'])
```

## Deletando


```python
my_dict = {'key1': 'value1', 'key2': 99, 'keyX': 'valueX'}
del my_dict['keyX']
print(my_dict)

# Geralmente é melhor ter certeza de que a chave existe (veja também pop() e popitem())
key_to_delete = 'my_key'
if key_to_delete in my_dict:
    del my_dict[key_to_delete]
else:
    print('{key} is not in {dictionary}'.format(key=key_to_delete, dictionary=my_dict))
```

## Os dicionários são mutáveis


```python
my_dict = {'ham': 'good', 'carrot': 'semi good'}
my_other_dict = my_dict
my_other_dict['carrot'] = 'super tasty'
my_other_dict['sausage'] = 'best ever'
print('my_dict: {}\nother: {}'.format(my_dict, my_other_dict))
print('equal: {}'.format(my_dict == my_other_dict))
```

Crie um novo `dict` se quiser ter uma cópia:


```python
my_dict = {'ham': 'good', 'carrot': 'semi good'}
my_other_dict = dict(my_dict)
my_other_dict['beer'] = 'decent'
print('my_dict: {}\nother: {}'.format(my_dict, my_other_dict))
print('equal: {}'.format(my_dict == my_other_dict))
```

<a id='dict_get'></a>
## `dict.get()`
Retorna `None` se `key` não estiver em `dict`. No entanto, você também pode especificar o valor de retorno `default` que será retornado se `key` não estiver presente no `dict`. 


```python
my_dict = {'a': 1, 'b': 2, 'c': 3}
d = my_dict.get('d')
print('d: {}'.format(d))

d = my_dict.get('d', 'my default value')
print('d: {}'.format(d))
```

## `dict.pop()`


```python
my_dict = dict(food='ham', drink='beer', sport='football')
print('dict before pops: {}'.format(my_dict))

food = my_dict.pop('food')
print('food: {}'.format(food))
print('dict after popping food: {}'.format(my_dict))

food_again = my_dict.pop('food', 'default value for food')
print('food again: {}'.format(food_again))
print('dict after popping food again: {}'.format(my_dict))

```

## `dict.setdefault()`
Retorna o `value` de `key` definido como primeiro parâmetro. Se a `key` não estiver presente no dict, adiciona `key` com o valor padrão (segundo parâmetro).


```python
my_dict = {'a': 1, 'b': 2, 'c': 3}
a = my_dict.setdefault('a', 'my default value')
d = my_dict.setdefault('d', 'my default value')
print('a: {}\nd: {}\nmy_dict: {}'.format(a, d, my_dict))
```

## `dict.update()`
Mesclar dois `dict`s


```python
dict1 = {'a': 1, 'b': 2}
dict2 = {'c': 3}
dict1.update(dict2)
print(dict1)

# Se eles tiverem as mesmas chaves:
dict1.update({'c': 4})
print(dict1)
```

## As chaves de um `dict` devem ser imutáveis

Assim, você não pode usar, por exemplo, uma `list` ou um `dict` como chave porque são tipos mutáveis:


```python
# bad_dict = {['my_list'], 'value'}  # Raises TypeError
```

Os valores podem ser mutáveis


```python
good_dict = {'my key': ['Python', 'is', 'still', 'cool']}
print(good_dict)
```
