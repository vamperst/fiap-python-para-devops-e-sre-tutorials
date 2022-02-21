# [Utilizando filas SQS](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html)

Neste exemplo, o código Python é usado para trabalhar com filas.O código usa o AWS SDK para Python para usar filas usando esses métodos da classe de cliente AWS.SQS:

- list_queues.
- create_queue.
- get_queue_url.
- delete_queue.

Para obter mais informações sobre mensagens Amazon SQS, consulte [Como as filas funcionam](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-how-it-works.html) no Guia de Desenvolvedor do Amazon Simple File Service.

## Crie filas
O exemplo abaixo mostra como:

- Crie uma fila usando [create_queue](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html#SQS.Client.create_queue).

Crie um script chamado criar-fila.py com o comando `c9 open criar-fila.py` e adicione o seguinte conteúdo:

```python
import boto3

# Crie o cliente SQS.
sqs = boto3.client('sqs')
nomeDaFila=""
# Crie uma fila SQS
response = sqs.create_queue(
    QueueName=nomeDaFila,
    Attributes={
        'DelaySeconds': '60',
        'MessageRetentionPeriod': '86400'
    }
)

print(response['QueueUrl'])
```

Execute o script criado.

## Listar suas filas

O exemplo abaixo mostra como:

- Listar filas usando [list_queues](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html#SQS.Client.list_queues).


Crie um script chamado listar-filas.py com o comando `c9 open listar-filas.py` e adicione o seguinte conteúdo:

```python
import boto3

# Crie o cliente SQS.
sqs = boto3.client('sqs')

# Lista sqs filas.
response = sqs.list_queues()

print(response['QueueUrls'])
```

Execute o script criado.

## URL de uma fila

O exemplo abaixo mostra como:

- Obtenha o URL para uma fila usando [get_queue_url](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html#SQS.Client.get_queue_url).
  

Crie um script chamado pegar-URL-fila.py com o comando `c9 open pegar-URL-fila.py` e adicione o seguinte conteúdo:

```python
import boto3

# Crie o cliente SQS.
sqs = boto3.client('sqs')

nomeDaFila=""

# Obtenha URL para a fila SQS
response = sqs.get_queue_url(QueueName=nomeDaFila)

print(response['QueueUrl'])
```

## Delete a fila

O exemplo abaixo mostra como:

- Excluir uma fila usando [delete_queue](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html#SQS.Client.delete_queue).



Crie um script chamado deletar-fila.py com o comando `c9 open deletar-fila.py` e adicione o seguinte conteúdo:

```python
import boto3
import json

# Crie o cliente SQS.
sqs = boto3.client('sqs')

nomeDaFila=""

# Excluir sqs fila
response=sqs.delete_queue(QueueUrl=nomeDaFila)
print(json.dumps(response))
```