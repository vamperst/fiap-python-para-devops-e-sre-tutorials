# [File I/O](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)
Lendo e escrevendo arquivos.

## Trabalhando com caminhos


```python
import os

current_file = os.path.realpath('file_io.ipynb')  
print('current file: {}'.format(current_file))
# Nota: em arquivos .py você pode obter o caminho do arquivo atual por __file__

current_dir = os.path.dirname(current_file)  
print('current directory: {}'.format(current_dir))
# Nota: em arquivos .py você pode obter o diretório do arquivo atual por os.path.dirname(__file__)

data_dir = os.path.join(os.path.dirname(current_dir), 'data')
print('data directory: {}'.format(data_dir))
```

### Verificando se o caminho existe


```python
print('exists: {}'.format(os.path.exists(data_dir)))
print('is file: {}'.format(os.path.isfile(data_dir)))
print('is directory: {}'.format(os.path.isdir(data_dir)))
```

## Lendo arquivos


```python
file_path = os.path.join(data_dir, 'simple_file.txt')

with open(file_path, 'r') as simple_file:
    for line in simple_file:
        print(line.strip())
```

A instrução [with](https://docs.python.org/3/reference/compound_stmts.html#the-with-statement) é para obter um [gerenciador de contexto](https://docs.python.org/3/reference/datamodel.html#with-statement-context-managers) que será usado como contexto de execução para os comandos dentro do `with`. Os gerenciadores de contexto garantem que certas operações sejam feitas ao sair do contexto. 

Neste caso, o gerenciador de contexto garante que `simple_file.close()` seja chamado implicitamente ao sair do contexto. Essa é uma maneira de facilitar a vida dos desenvolvedores: você não precisa se lembrar de fechar explicitamente o arquivo que abriu nem se preocupar com a ocorrência de uma exceção enquanto o arquivo estiver aberto. Arquivo não fechado pode ser uma fonte de vazamento de recursos. Assim, prefira usar a estrutura `with open()` sempre com I/O de arquivo.

Para ter um exemplo, o mesmo acima sem o `with`.


```python
file_path = os.path.join(data_dir, 'simple_file.txt')

# ESTA NÃO É A MANEIRA PREFERIDA
simple_file = open(file_path, 'r')
for line in simple_file:
    print(line.strip())
simple_file.close()  # Isso tem que ser chamado explicitamente
```

## Gravando arquivos


```python
new_file_path = os.path.join(data_dir, 'new_file.txt')

with open(new_file_path, 'w') as my_file:
    my_file.write('This is my first file that I wrote with Python.')
```

Agora vá e verifique se existe um new_file.txt no diretório de dados. Depois disso, você pode excluir o arquivo por:


```python
if os.path.exists(new_file_path):  # certifique-se de que está lá
    os.remove(new_file_path)
```
