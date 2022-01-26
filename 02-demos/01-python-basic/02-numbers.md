# [Numbers](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)

## `int`


```python
my_int = 6
print('value: {}, type: {}'.format(my_int, type(my_int)))
```

## `float`


```python
my_float = float(my_int)
print('value: {}, type: {}'.format(my_float, type(my_float)))
```

Observe que a divisão de `int`s produz `float`:


```python
print(1 / 1)
print(6 / 5)
```

Esteja ciente das armadilhas de ponto flutuante binário (consulte [Decimal](#decimal) para solução alternativa):


```python
val = 0.1 + 0.1 + 0.1
print(val == 0.3)
print(val)
```

## Divisão do piso `//`, módulo `%`, potência `**`


```python
7 // 5
```


```python
7 % 5
```


```python
2 ** 3
```

<a id='decimal'></a>
## [`decimal.Decimal`](https://docs.python.org/3/library/decimal.html)


```python
from decimal import Decimal
```


```python
from_float = Decimal(0.1)
from_str = Decimal('0.1')
print('from float: {}\nfrom string: {}'.format(from_float, from_str))
```


```python
my_decimal = Decimal('0.1')
sum_of_decimals = my_decimal + my_decimal + my_decimal
print(sum_of_decimals == Decimal('0.3'))
```

## Precedência do operador nos cálculos
A precedência do operador matemático se aplica. Use colchetes se quiser alterar a ordem de execução:


```python
print(1 + 2**2 * 3 / 6) # 1 + 4 * 3 / 6 == 1 + 12 / 6 == 1 + 2
print((1 + 2**2) * 3 / 6)
```
