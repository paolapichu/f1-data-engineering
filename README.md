# 🏎️ F1 Data Engineering Project

Projeto de Engenharia de Dados desenvolvido no Azure Databricks, utilizando dados históricos da Fórmula 1 para construir a camada Bronze de um Data Lakehouse.

## 📌 Sobre o projeto

O projeto implementa um pipeline de ingestão de dados utilizando PySpark e Delta Lake, aplicando tipagem rígida, padronização de colunas e rastreabilidade da carga.

Os dados utilizados pertencem ao dataset público **Formula 1 World Championship (1950–Atual)**, disponibilizado no Kaggle.

## 🎯 Objetivo

Construir a primeira etapa de uma arquitetura Lakehouse, realizando a ingestão de arquivos CSV na camada Bronze sem utilizar inferência automática de schema.

## 🗂️ Dados utilizados

Foram utilizados os seguintes arquivos:

- `drivers.csv`: informações sobre os pilotos;
- `races.csv`: informações sobre as corridas;
- `lap_times.csv`: tempos de volta registrados nas corridas.

> Os arquivos CSV não estão incluídos neste repositório. Eles podem ser obtidos diretamente no Kaggle.

## 🛠️ Tecnologias

- Azure Databricks
- Apache Spark
- PySpark
- Delta Lake
- Python
- Git e GitHub

## ⚙️ Etapas realizadas

1. Upload dos arquivos CSV para um Volume no Databricks;
2. Leitura dos arquivos utilizando PySpark;
3. Definição manual dos schemas com `StructType` e `StructField`;
4. Tratamento de valores nulos representados por `\N`;
5. Padronização dos nomes das colunas para `snake_case`;
6. Adição da coluna de auditoria `ingestion_timestamp`;
7. Gravação dos DataFrames no formato Delta Lake;
8. Validação dos dados gravados na camada Bronze.

## 🏗️ Arquitetura

O fluxo de ingestão implementado foi:

```text
Arquivos CSV
     ↓
Volume Raw
     ↓
Processamento com PySpark
     ↓
Camada Bronze em Delta Lake
```

A camada raw preserva os arquivos originais, enquanto a camada Bronze armazena os dados tipados, padronizados e acompanhados do timestamp de ingestão.

📁 Estrutura do repositório

formula1-lakehouse-databricks/

├── notebooks/
│   └── 01_ingestion_bronze.ipynb

├── images/
│   └── bronze-validation.png

├── .gitignore
└── README.md

✅ Resultado

Foram criados três conjuntos de dados no formato Delta:

bronze_f1/

├── drivers/

├── races/

└── lap_times/

Cada conjunto possui schema definido manualmente, colunas padronizadas e informações de auditoria sobre o momento da ingestão.

💡 Principais aprendizados
Processamento distribuído com Apache Spark;
Criação de schemas rígidos no PySpark;
Organização das zonas Raw e Bronze;
Aplicação da arquitetura Medallion;
Gravação e leitura de dados em Delta Lake;
Inclusão de metadados para rastreabilidade;
Organização de um projeto de Engenharia de Dados.

🚀 Próximas etapas
Arquitetura Medalhão e Cruzamentos (Camadas Prata e Ouro)
Objetivo: Transformar dados brutos em tabelas relacionais limpas (Prata) e, em seguida, consolidar métricas de alto valor para o negócio (Ouro), orquestrando o fluxo de ponta a ponta.
