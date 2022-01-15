# [Módulos e pacotes](https://docs.python.org/3/tutorial/modules.html#modules)

> Módulo é um arquivo de código-fonte Python, ou seja, um arquivo com extensão .py.

> Package é um diretório que contém o arquivo `__init__.py` e pode conter módulos python e outros pacotes.  


## Por que organizar seu código em módulos e pacotes
* Manutenibilidade
* Reutilização
* Espaçamento de nomes
* Pessoas não familiarizadas com o seu projeto podem obter uma visão geral clara apenas observando a estrutura de diretórios do seu projeto
* É fácil pesquisar determinada funcionalidade ou classe

## Como usar

Vamos usar a seguinte estrutura de diretórios como exemplo:

      
```
food_store/
    __init__.py
    
    product/
        __init__.py
        
        fruit/
            __init__.py
            apple.py
            banana.py
            
        drink/
            __init__.py
            juice.py
            milk.py
            beer.py

    cashier/
        __ini__.py
        receipt.py
        calculator.py
```


Vamos considerar que o arquivo banana.py contém:

```python

def get_available_brands():
    return ['chiquita']


class Banana:
    def __init__(self, brand='chiquita'):
        if brand not in get_available_brands():
            raise ValueError('Unkown brand: {}'.format(brand))
        self._brand = brand
     
```

### Importando

Digamos que precisamos acessar a classe `Banana` do arquivo banana.py dentro do arquivo receive.py. Podemos conseguir isso importando no início de receive.py:

```python
from food_store.product.fruit.banana import Banana

# then it's used like this
my_banana = Banana()
```



Se precisarmos acessar várias classes ou funções do arquivo banana.py:

```python
from food_store.product.fruit import banana

# then it's used like this
brands = banana.get_available_brands()
my_banana = banana.Banana()
```

Uma introdução abrangente aos módulos e pacotes pode ser encontrada [aqui](https://realpython.com/python-modules-packages/).
