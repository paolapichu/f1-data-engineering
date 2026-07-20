# F1 Data Engineering Project (Azure Databricks)

## Descrição
Projeto de engenharia de dados utilizando Azure Databricks com foco em ingestão e transformação de dados.

## Objetivo
Construir pipeline de ingestão (camada Bronze) com boas práticas de dados.

## Tecnologias
- Azure Databricks
- PySpark
- Delta Lake

## Etapas do Projeto
- Leitura de arquivos CSV
- Definição de schema com StructType
- Padronização de colunas (snake_case)
- Adição de metadata (ingestion_timestamp)
- Escrita em formato Delta (camada Bronze)

## Estrutura

formula1-lakehouse-databricks/
├── notebooks/
│   └── 01_ingestion_bronze.ipynb
├── images/
│   └── bronze-validation.png
├── .gitignore
└── README.md

## 💡 Aprendizados
- Uso de Spark para processamento de dados
- Boas práticas de ingestão
- Arquitetura Medallion (Bronze)


