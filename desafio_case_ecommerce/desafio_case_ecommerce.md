## Desafio Case Ecommerce

- Descrição:
    - Para simular um mundo real de ingestão de dados foi criado um Cloudformation para ingerir dados que serão processados e analisados.
    - O processo se inicia com funções AWS Lambda que geram dados aleatórios que são enviados ao Kinesis Streams.
    - O Kinesis Streams é consumido por três consumidores diferentes: Kinesis Firehose, Kinesis Data Analytics e uma Lambda Function. Então temos três destinados para cada registro.
    - O Kinesis Data Analytics realiza agregação nos dados em near real time. 
    - O Kinesis Firehose grava os dados brutos (raw) para um bucket S3 para ser analisado posteriormente.
    - Também há outra função Lambda que pode enviar dados para o ElasticSearch e na sequencia visualizá-los no Kibana.

- Fluxo de dados criado pelo Cloudformation:

![alt text](https://github.com/schmidt-samuel/fia_batalha_de_dados1/blob/master/desafio_case_ecommerce/imagens/fluxo_de_dados.png)


- Realizar deploy do Cloudformation template:
    - Apos logar na sua conta da AWS criada recentemente, clique neste link para iniciar o deploy do cloudformation:
    ```
    https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?&templateURL=https:%2F%2Fs3.amazonaws.com%2Fhhug-demo-data%2Fkinesis-demo%2Fecommerce%2Fstreaming-ecommerce-es.template
    ```
    
- Preencher o conteúdo dos parâmetros solicitados de forma semelhante ao seguinte exemplo:
obs 1: Lembre-se que o nome do S3 bucket (Bucket Name) tem que possuir um prefixo unico em nível global.
obs 2: Lembre-se de fazer deploy na region da N. Virgina.

![alt text](https://github.com/schmidt-samuel/fia_batalha_de_dados1/blob/master/desafio_case_ecommerce/imagens/cloudformation_passo1.png)

- Verifique o status da evolução do cloudformation ecommerce:
    - Para verificar a evolução clique no link:
    ```
    https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks
    ```

![alt text](https://github.com/schmidt-samuel/fia_batalha_de_dados1/blob/master/desafio_case_ecommerce/imagens/cloudformation_passo2.png)

- Aguarde, entre 12 e 20 minutos, para o deploy fique com o status de completo (CREATE_COMPLETE):
  
![alt text](https://github.com/schmidt-samuel/fia_batalha_de_dados1/blob/master/desafio_case_ecommerce/imagens/cloudformation_passo3.png)

- Valide os recursos criados:

![alt text](https://github.com/schmidt-samuel/fia_batalha_de_dados1/blob/master/desafio_case_ecommerce/imagens/cloudformation_passo4.png)
