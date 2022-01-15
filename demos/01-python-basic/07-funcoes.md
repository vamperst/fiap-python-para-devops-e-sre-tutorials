# Funções


```python
def my_first_function():
    print('Hello world!')

print('type: {}'.format(my_first_function))

my_first_function()  # Chamando uma função
```

### Argumentos.


```python
def greet_us(name1, name2):
    print('Hello {} and {}!'.format(name1, name2))

greet_us('John Doe', 'Superman')
```


```python
# Função com valor de retorno
def strip_and_lowercase(original):
    modified = original.strip().lower()
    return modified

uggly_string = '  MixED CaSe '
pretty = strip_and_lowercase(uggly_string)
print('pretty: {}'.format(pretty))
```

### Argumentos da palavra-chave.


```python
def my_fancy_calculation(first, second, third):
    return first + second - third 

print(my_fancy_calculation(3, 2, 1))

print(my_fancy_calculation(first=3, second=2, third=1))

# Com argumentos de palavra-chave você pode misturar o pedido
print(my_fancy_calculation(third=1, first=3, second=2))

# Você pode misturar argumentos e argumentos de palavra-chave, mas você tem que começar com argumentos
print(my_fancy_calculation(3, third=1, second=2))  
```

### Argumentos padrão


```python
def create_person_info(name, age, job=None, salary=300):
    info = {'name': name, 'age': age, 'salary': salary}
    
    # Adicione a chave 'Job' somente se for fornecida como parâmetro
    if job:  
        info.update(dict(job=job))
        
    return info

person1 = create_person_info('John Doe', 82)  # Use valores padrão para trabalho e salário
person2 = create_person_info('Lisa Doe', 22, 'hacker', 10000)
print(person1)
print(person2)
```

**Não use objetos mutáveis como argumentos padrão!**


```python
def append_if_multiple_of_five(number, magical_list=[]):
    if number % 5 == 0:
        magical_list.append(number)
    return magical_list

print(append_if_multiple_of_five(100))
print(append_if_multiple_of_five(105))
print(append_if_multiple_of_five(123))
print(append_if_multiple_of_five(123, []))
print(append_if_multiple_of_five(123))
```

Veja como você pode alcançar o comportamento desejado:

```python
def append_if_multiple_of_five(number, magical_list=None):
    if not magical_list:
        magical_list = []
    if number % 5 == 0:
        magical_list.append(number)
    return magical_list

print(append_if_multiple_of_five(100))
print(append_if_multiple_of_five(105))
print(append_if_multiple_of_five(123))
print(append_if_multiple_of_five(123, []))
print(append_if_multiple_of_five(123))
```

### Docstrings
Strings para documentar suas funções, métodos, módulos e variáveis.


```python
def print_sum(val1, val2):
    """Função que imprime a soma de argumentos dados."""
    print('sum: {}'.format(val1 + val2))

print(help(print_sum))
```


```python
def calculate_sum(val1, val2):
    """Este é um DocString mais longo, definindo também os args e o valor de retorno. 

    Args:
        val1: The first parameter.
        val2: The second parameter.

    Returns:
        The sum of val1 and val2.
        
    """
    return val1 + val2

print(help(calculate_sum))
```

### [`pass`](https://docs.python.org/3/reference/simple_stmts.html#the-pass-statement) declaração
`pass` é uma instrução que não faz nada quando é executada. Pode ser usado e. a como espaço reservado para tornar o código sintaticamente correto ao esboçar as funções e/ou classes de seu aplicativo. Por exemplo, o seguinte é Python válido.


```python
def my_function(some_argument):
    pass

def my_other_function():
    pass
```
