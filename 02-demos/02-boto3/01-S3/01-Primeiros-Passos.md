# [Boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/index.html)

Este guia detalha as etapas necessárias para instalar ou atualizar o AWS SDK para Python.

O SDK é composto por dois pacotes de teclas Python: Botocore (a biblioteca que fornece a funcionalidade de baixo nível compartilhada entre o Python SDK e o AWS CLI) e o BOTO3 (o pacote implementando o próprio Python SDK).

## Instalando `Boto3`  

Antes de instalar o Boto3, instale o Python 3.6 ou posterior;Suporte para Python 3.5 e anterior já está descontinuado.Após a data de depreciação listada para cada versão Python, novos lançamentos de Boto3 não incluirão suporte para essa versão do Python.Para detalhes, incluindo o cronograma de depreciação e como atualizar seu projeto para usar o Python 3.6.

Crie um ambiente virtual python:
```shell
sudo pip3 install virtualenv
virtualenv ~/venv 
source ~/venv/bin/activate
```

Instale a última versão Boto3 via Pip:

```shell
pip install boto3
```


## Usando `Boto3`  

Para usar o Boto3, você deve primeiro importá-lo e indicar qual serviço ou serviços você usará:

```python
import boto3

# Vamos usar Amazon S3
s3 = boto3.resource('s3')
```

Agora você tem um recurso S3, você pode fazer solicitações de envio para o serviço.O código a seguir usa a coleção Buckets para imprimir todos os nomes de bucket:

```python
# Imprime o nome de todos os buckets
for bucket in s3.buckets.all():
    print(bucket.name)
```

Vamos baixar os arquivos a serem utilizados nos exemplos seguintes, execute os comandos no terminal do Cloud9 fora do python:
```shell
curl -o aws.png https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Amazon_Web_Services_Logo.svg/1200px-Amazon_Web_Services_Logo.svg.png
```


Você também pode fazer o upload e download de dados binários.Por exemplo, o seguinte carrega um novo arquivo para S3, supondo que o Bucket já existe:
```pytohn
# Upload de um arquivo
data = open('aws.png', 'rb')
s3.Bucket('base-config-SEU RM').put_object(Key='aws.png', Body=data)
```


## Criando um bucket

A partir desse momento do curso vamos utilizar scritps em python ao invés de direto na linha de comando.

Por isso sempre vamos utilizar o comando `c9 open` para criar o arquivo e após isso vamos rodar ele na linha de comando.

O nome de um bucket da Amazon S3 deve ser único em todas as regiões da plataforma AWS.O bucket pode ser localizado em uma região específica para minimizar a latência ou para atender aos requisitos regulatórios.

Execute o comando a seguir para entrar na pasta certa e criar o arquivo em branco:
```shell

```