# [Exceções](https://docs.python.org/3/library/exceptions.html#concrete-exceptions)
Quando algo dá errado, uma exceção é gerada. Por exemplo, se você tentar dividir por zero, `ZeroDivisionError` será gerado ou se você tentar acessar uma chave inexistente em um dicionário, `KeyError` será gerado.




```python
empty_dict = {}
# empty_dict['key']  # Uncomment to see the traceback
```

## Estrutura `try-except`  
Se você sabe que um bloco de código pode falhar de alguma maneira, você pode usar a estrutura `try-except` para lidar com possíveis exceções da maneira desejada.


```python
# Vamos tentar abrir um arquivo que não existe
file_name = 'not_existing.txt'

try:
    with open(file_name, 'r') as my_file:
        print('File is successfully open')
        
except FileNotFoundError as e:
    print('Uups, file: {} not found'.format(file_name))
    print('Exception: {} was raised'.format(e))
```

Se você não sabe o tipo de exceção que um bloco de código pode gerar, você pode usar `Exception` que captura todas as exceções. Além disso, você pode ter várias instruções `except`.


```python
def calculate_division(var1, var2):
    result = 0
    
    try:
        result = var1 / var2
    except ZeroDivisionError as ex1:
        print("Can't divide by zero")
    except Exception as ex2:
        print('Exception: {}'.format(ex2))

    return result

result1 = calculate_division(3, 3)
print('result1: {}'.format(result1))

result2 = calculate_division(3, '3')
print('result2: {}'.format(result2))

result3 = calculate_division(3, 0)
print('result3: {}'.format(result3))
```

`try-except` também pode estar no escopo externo:


```python
def calculate_division(var1, var2):
    return var1 / var2

try:
    result = calculate_division(3, '3')
except Exception as e:
    print(e)
```

## Criando suas exceções personalizadas
Em seus próprios aplicativos, você pode usar exceções personalizadas para sinalizar aos usuários sobre erros que ocorrem durante o tempo de execução do aplicativo.  


```python
import math

# Defina sua própria exceção
class NegativeNumbersNotSupported(Exception):
    pass

# Dummy example how to use your custom exception
def secret_calculation(number1, number2):
    if number1 < 0 or number2 < 0:
        msg = 'Negative number in at least one of the parameters: {}, {}'.format(
            number1, number2)
        raise NegativeNumbersNotSupported(msg)

    return math.sqrt(number1) + math.sqrt(number2)

# Descomente para ver o traceback
# result = secret_calculation(-1, 1)
```

Exercicio de Exceções: [clique aqui](../../03-Exercicios/01-python-basic/05-excecoes.md)