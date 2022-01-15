# 1. `if-elif-else`
Preencha as partes faltantes (`____`) do código a seguir de forma que as impressões façam sentido.

```python
name = 'John Doe'
```


```python
if ____:
    print('Name "{}" is more than 20 chars long'.format(name))
    length_description = 'long'
elif ____:
    print('Name "{}" is more than 15 chars long'.format(name))
    length_description = 'semi long'
elif ____:
    print('Name "{}" is more than 10 chars long'.format(name))
    length_description = 'semi long'
elif ____:
    print('Name "{}" is 8, 9 or 10 chars long'.format(name))
    length_description = 'semi short'
else:
    print('Name "{}" is a short name'.format(name))
    length_description = 'short'
```


```python
if length_description == 'semi short':
    print("DONE!!")
```
