# [Lidando com arquivos no S3](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html)

O AWS SDK para Python fornece um par de métodos para carregar um arquivo para um bucket S3.

O método upload_File aceita um nome de arquivo, um nome de bucket e um nome de objeto.O método lida com arquivos grandes, dividindo-os em pedaços menores e carregando cada pedaço em paralelo.

Vamos baixar os arquivos a serem utilizados nos exemplos seguintes, execute os comandos no terminal do Cloud9 fora do python:

```shell
curl -o aws.png https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Amazon_Web_Services_Logo.svg/1200px-Amazon_Web_Services_Logo.svg.png
```

## Upload de arquivos 

Crie o arquivo upload-arquivos.py com o seguinte comando `c9 open upload-arquivos.py` e adicione o seguinte conteúdo:

```python
import boto3
from botocore.exceptions import ClientError
import os
import json


def upload_file(file_name, bucket, object_name=None):
    """Carregar um arquivo para um bucket S3

    :param file_name: File to upload
    :param bucket: Bucket to upload to
    :param object_name: S3 object name. If not specified then file_name is used
    :return: True if file was uploaded, else False
    """

    # If S3 object_name was not specified, use file_name
    if object_name is None:
        object_name = os.path.basename(file_name)

    # Upload the file
    s3_client = boto3.client('s3')
    try:
        response = s3_client.upload_file(file_name, bucket, object_name)
        print(f"Arquivo {object_name} criado")
    except ClientError as e:
        print(e)
        return False
    return True

if __name__ == '__main__':
    nomeDoBucket = ""
    arquivoLocal="aws.png"
    upload_file(arquivoLocal,nomeDoBucket)
    upload_file(arquivoLocal,nomeDoBucket,"aws-personalizado.png")
```

Para executar o arquivo volte a linha de comando e execute:

```shell
python upload-arquivos.py
```

O método upload_FileOBJ aceita um objeto like de arquivo legível.O objeto de arquivo deve ser aberto no modo binário, não no modo de texto.

Os métodos upload_File e upload_fileobj são fornecidos pelo cliente, bucket e classes de objetos S3. A funcionalidade do método fornecido por cada classe é idêntica. Nenhum benefício é obtido chamando o método de uma classe sobre o outro.Use qualquer classe que seja mais conveniente.

Altere o script upload-arquivos.py para alterar o método de fazer upload para mandar um objeto ao invés de um arquivo.

```python
with open(file_name, "rb") as f:
    response = s3_client.upload_fileobj(f,  bucket, object_name)
```

Execute novamente para ver o resultado.

## Download de arquivos

Crie o arquivo download-arquivos.py com o comando `c9 open download-arquivos.py` com o seguinte conteúdo:

```python
import boto3
from botocore.exceptions import ClientError
import os
import json


def download_file(object_name, bucket, file_name=None):
    """Download a file to an S3 bucket

    :param file_name: File to upload
    :param bucket: Bucket to upload to
    :param object_name: S3 object name. If not specified then file_name is used
    :return: True if file was downloades, else False
    """

    # If S3 object_name was not specified, use file_name
    if file_name is None:
        file_name = os.path.basename(object_name)

    # Upload the file
    s3 = boto3.client('s3')
    try:
        with open(file_name, 'wb') as f:
            s3.download_fileobj(bucket, object_name, f)
        print(f"Arquivo {file_name} baixado")
    except ClientError as e:
        print(e)
        return False
    return True


if __name__ == '__main__':
    nomeDoBucket = ""
    arquivoLocal="aws-baixado.png"
    objetoDoS3 = "aws.png"
    download_file(objetoDoS3,nomeDoBucket,arquivoLocal)
```

Para executar o arquivo volte a linha de comando e execute:

```shell
python download-arquivos.py
```

## [Configurando a transferencia de arquivos](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/customizations/s3.html#boto3.s3.transfer.TransferConfig)


Ao fazer o upload, download ou copiar um objeto ou S3 Object, o AWS SDK para Python gerencia automaticamente novas repetições e multiplicar e transferências não-multipartes.

As operações de gerenciamento são realizadas usando configurações padrão razoáveis que são bem adequadas para a maioria dos cenários.Para lidar com um caso especial, as configurações padrão podem ser configuradas para atender aos requisitos.

As configurações são armazenadas em um objeto Boto3.S3.Transfer.Transferconfig.O objeto é passado para um método de transferência (Upload_File, download_file, etc.) no parâmetro Config =.

As seções restantes demonstram como configurar várias operações de transferência com o objeto TransferConfig.

Vamos criar um arquivo de 1GB antes de continuar o exemplo. Esse arquivo será utilizado para rodar o próximo script.
```shell
dd if=/dev/zero of=1GB.file count=1024 bs=1M
```

Crie o arquivo upload-dividido.py com o comando `c9 open upload-dividido.py`.

## Operações concorrentes e Threads

O número máximo de operações de transferência de API S3 concorrentes pode ser ajustada para ajustar a velocidade de conexão.Defina o atributo max_concurrency para aumentar ou diminuir o uso da largura de banda.

A configuração padrão do atributo é 10. Para reduzir o uso de largura de banda, reduza o valor;Para aumentar o uso, aumente.

Transferir Operations Use threads para implementar simultaneamente. O uso das threads pode ser desativado definindo o atributo use_threads como falso.

Se o uso de thread estiver desativado, transferir simultaneidade não ocorrerá. Assim, o valor do atributo Max_Concurrency é ignorado.

Crie um arquivo chamado download-em-partes.py `c9 open upload-dividido.py` com o seguinte conteúdo:

```python
import boto3
from boto3.s3.transfer import TransferConfig

# Defina o valor do limiar de multiparício desejado (1GB)
MB = 1024 ** 2
config = TransferConfig(multipart_threshold=100*MB)

# Execute a transferência
s3 = boto3.client('s3')
nomeDoBucket = ""
arquivoLocal="1GB.file"
response=s3.upload_file(arquivoLocal, nomeDoBucket, arquivoLocal, Config=config)
print(response)
```
Execute o script criado com o comando `python upload-dividido.py`

