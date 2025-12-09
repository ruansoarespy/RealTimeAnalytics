# Real Time Analytics - Engenharia de Dados

Projeto de **Engenharia de Dados em tempo real** utilizando serviços da AWS, desenvolvido para análise e processamento de dados em tempo real.

<img width="703" height="452" alt="conceitualaws" src="https://github.com/user-attachments/assets/04b62903-e1a8-4f88-8427-49dc4ed4951f" />


## Tecnologias e serviços utilizados
- AWS Lambda (processamento de dados em tempo real)
- Amazon Kinesis (ingestão de dados)
- SNS (alertas em tempo real)
- S3 (armazenamento raw e gold)
- Glue (ETL, catálogos e crawlers)
- Athena (consultas ad-hoc)
- CloudWatch (monitoramento e logs)
- IAM (roles e permissões)

## Arquitetura do projeto
1. Dados são consumidos de uma API externa.
2. Lambda processa os dados em tempo real e envia para Kinesis.
3. SNS envia alertas para eventos críticos.
4. Dados brutos são armazenados em S3 (raw) e transformados em S3 (gold) via Glue ETL.
5. Athena permite consultas rápidas nos dados transformados.
6. CloudWatch monitora logs e métricas do pipeline.

## Aprendizados
- Integração de serviços AWS para soluções escaláveis.
- Desenvolvimento de pipelines em tempo real.
- Automação de ETL e organização de dados.
- Criação de alertas e monitoramento proativo.
- Boas práticas de segurança e controle de acesso via IAM.

## Estrutura do projeto


Estrutura do projeto:
```
RealTimeAnalytics/
    lambda/            - Funções Lambda
    kinesis/           - Scripts de ingestão ou configuração
    glue/              - Scripts ETL e catálogos
    s3/                - Estrutura raw/gold
    athena_queries/    - Queries de análise
    cloudwatch/        - Dashboards ou logs de exemplo
    docs/              - Prints, diagramas, explicações
    README.txt
```
Como usar:
- Configurar variáveis de ambiente e roles IAM.
- Executar funções Lambda e scripts ETL.
- Consultar dados via Athena.
- Monitorar via CloudWatch.
