# Lidando com os itens da fila

Neste exemplo, o código Python é usado para enviar e receber mensagens.O código usa o SDK AWS para Python para enviar e receber mensagens usando esses métodos da classe de cliente AWS.SQS:

- [send_message](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html#SQS.Client.send_message).
- [receive_message](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html#SQS.Client.receive_message).
- [delete_message](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/sqs.html#SQS.Client.delete_message).

Para obter mais informações sobre as mensagens do Amazon SQS, consulte Enviando uma mensagem para uma fila da Amazon SQS e recebendo e excluindo uma mensagem de uma fila Amazon SQS no Guia de Desenvolvedor de Serviços da Amazon Simple File.


Para configurar e executar este exemplo, você deve primeiro concluir essas tarefas:

- Crie uma fila utilizando o boto3


## Enviar uma mensagem para a fila


Crie um script chamado enviando-mensagens-fila.py com o comando `c9 open enviando-mensagens-fila.py` e adicione o seguinte conteúdo:
```python
import boto3

# Crie o cliente SQS.
sqs = boto3.client('sqs')

queue_url = ""

# Enviando mensagem para a fila SQS
response = sqs.send_message(
    QueueUrl=queue_url,
    DelaySeconds=10,
    MessageAttributes={
        'Title': {
            'DataType': 'String',
            'StringValue': 'The Whistler'
        },
        'Author': {
            'DataType': 'String',
            'StringValue': 'John Grisham'
        },
        'WeeksOn': {
            'DataType': 'Number',
            'StringValue': '6'
        }
    },
    MessageBody=(
        'Information about current NY Times fiction bestseller for '
        'week of 12/11/2016.'
    )
)

print(response['MessageId'])
```

Execute o script criado.

## Recebendo e deletando mensagens de uma fila

Crie um script chamado lendo-deletando-mensagens.py com o comando `c9 open lendo-deletando-mensagens.py` e adicione o seguinte conteúdo:

```python
import boto3

# Crie o cliente SQS.
sqs = boto3.client('sqs')

queue_url = ''

# Receba mensagem de sqs fila
response = sqs.receive_message(
    QueueUrl=queue_url,
    AttributeNames=[
        'SentTimestamp'
    ],
    MaxNumberOfMessages=1,
    MessageAttributeNames=[
        'All'
    ],
    VisibilityTimeout=0,
    WaitTimeSeconds=0
)

message = response['Messages'][0]
receipt_handle = message['ReceiptHandle']

# Excluir mensagem recebida da fila
sqs.delete_message(
    QueueUrl=queue_url,
    ReceiptHandle=receipt_handle
)
print('Received and deleted message: %s' % message)
```