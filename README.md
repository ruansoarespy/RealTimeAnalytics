# Real Time Analytics - Engenharia de Dados

Projeto de **Engenharia de Dados em tempo real** utilizando serviços da AWS, desenvolvido para análise e processamento de dados em tempo real.

<img width="703" height="452" alt="conceitualaws" src="https://github.com/user-attachments/assets/04b62903-e1a8-4f88-8427-49dc4ed4951f" />

---

## Tecnologias e serviços utilizados

- **AWS Lambda**: Processamento de dados em tempo real.  
- **Amazon Kinesis**: Ingestão e transporte de dados em tempo real.  
- **SNS**: Alertas em tempo real por e-mail e SMS.  
- **S3**: Armazenamento de dados brutos (`raw`) e transformados (`gold`).  
- **Glue**: ETL, catálogo e crawlers para organização e transformação de dados.  
- **Athena**: Consultas ad-hoc sobre dados armazenados no S3.  
- **CloudWatch**: Monitoramento de logs e métricas.  
- **IAM**: Controle de permissões e segurança.

---

## Arquitetura do projeto

O pipeline de dados segue o fluxo abaixo:

1. **MapIn → Producer Lambda**
   - Recebe dados de uma API externa.
   - Role IAM e monitoramento via CloudWatch.
   - Envia dados para **Kinesis Stream**.

2. **Kinesis Stream**
   - Canal de ingestão de dados em tempo real.
   - Consumido por múltiplas Lambdas simultaneamente.

3. **Consumer Lambda RealTime**
   - Processa dados em tempo real.
   - Envia alertas críticos via **SNS** (e-mail e SMS).
   - Role IAM própria.

4. **Consumer Lambda Batch**
   - Processa dados do Kinesis em lote.
   - Armazena dados brutos no **S3 Raw**.
   - Role IAM própria.

5. **S3 Raw / Gold**
   - **Raw:** Dados brutos do ConsumerBatch.  
   - **Gold:** Dados transformados pelo Glue ETL.

6. **Glue ETL (Glue)**
   - Lê dados do S3 Raw, transforma e envia para S3 Gold.
   - Crawlers atualizam o catálogo de dados automaticamente.
   - Role IAM dedicada.

7. **Crawler Gold → Gold Database**
   - Atualiza o catálogo para consultas via Athena.

8. **Athena**
   - Consultas SQL ad-hoc sobre os dados transformados.
   - Ideal para análise rápida e exploração de dados.

9. **CloudWatch**
   - Monitora todas as Lambdas, Kinesis, Glue e SNS.
   - Identifica erros e métricas críticas em tempo real.

---


## Estrutura do projeto


Estrutura do projeto:
```
RealTimeAnalytics/
    lambda_functions.py/       - Funções Lambda
    consumer_realtime/        - Scripts de ingestão ou configuração
    jobglue.py/              - Scripts ETL e catálogos
    consumer_batch/         -consumo de dados em batch
    s3/                - Estrutura raw/gold

    README.txt
```
---

## Aprendizados e objetivos

- Construir **pipelines de dados em tempo real** com AWS.  
- Implementar alertas críticos automáticos via SNS.  
- Armazenar dados de forma organizada e escalável no S3.  
- Automatizar ETL e catalogação com Glue e Crawlers.  
- Realizar consultas rápidas e flexíveis com Athena.  
- Monitorar todo o pipeline com CloudWatch.  
- Aplicar boas práticas de **segurança e controle de acesso** via IAM.

---

## Requisitos

- Conhecimentos básicos em **Python**.  
- Conta AWS com permissões para Lambda, Kinesis, SNS, S3, Glue, Athena e CloudWatch.  

---

## Como usar

1. Configure **variáveis de ambiente** e **roles IAM**.  
2. Execute as **funções Lambda** e scripts ETL.  
3. Consulte os dados transformados via **Athena**.  
4. Monitore logs e métricas no **CloudWatch**.  
