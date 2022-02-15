# 1. Preencha as peças que faltam da classe `calculadora`
Preencha partes `____` da implementação `Calculadora` para passar as asserções.

```python
class Calculator:
    def __init__(self, var1, ____):
        self.____ = var1
        self.____ = _____
    
    def calculate_power(self):
        return self.____ ** ____.____
    
    def calculate_sum(____, var3):
        return ____.____ + ____.____ + var3
```


```python
calc = Calculator(2, 3)
assert calc.calculate_power() == 8
assert calc.calculate_sum(4) == 9
```

# 2. Criar classe `cães
Crie a classe `Dog` que tem a seguinte especificação:
* Os cães consomem sua energia latindo e ganham energia dormindo
* Uma nova instância `Dog` tem 10 unidades de energia
* `Dog` tem um método `sleep` que dá 2 unidades de energia
* `Dog` tem um método `bark` que consome 1 unidade de energia
* `Dog` tem um método `get_energy` que retorna a quantidade de energia restante

```python
class Dog:
    # Sua implementação vai aqui
```


```python
doge = Dog()
assert doge.get_energy() == 10

doge.bark()
doge.bark()
doge.bark()
assert doge.get_energy() == 7

doge.sleep()
assert doge.get_energy() == 9

another_doge = Dog()
assert another_doge.get_energy() == 10
```

Retorne para a próxima demo [Excecoes](../../02-demos/01-python-basic/10-excecoes.md)
