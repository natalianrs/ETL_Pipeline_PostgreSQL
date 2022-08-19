## Modelagem e Coleta de Dados em um app de Streaming de Músicas 🎼
Este case simula as atividades de um app de streaming de músicas. <br>
O objetivo final do time de data analytics do app é entender `quais músicas os usuários estão ouvindo e os seus hábitos de uso no app` <br>
Portanto, precisavámos construir um `banco de dados otimizado` com foco em facilitar o processo de análise dos dados em SQL <br>  
 🛠Para isso foi realizado: 
1. Modelagem dos dados relacionais;  
2. Coleta de dados das músicas e os logs de atividades dos usuários no app; 
3. Carregamento dos dados em um Data Warehouse em PostgreSQL;

![main](etl-pipeline.png)

## Fontes de Dados 💾
Foram usadas duas fontes de dados distintas. <br>
A 1a fonte é um sub-dataset do ["Milion Song Dataset"](http://millionsongdataset.com/) que contém `metadata de milhões de músicas`. <br> 
A 2a fonte de dados consiste em `logs de atividades` que foram geradas usando o ['Eventsim'](https://github.com/Interana/eventsim) para simular usuários reais do app.
> Todos os dados estão estruturados em arquivos .json

## Modelagem de Dados 🗃
Os dados foram modelados com o objetivo final de otimizar o processo de consultas SQL. <br>
Foi criado um esquema estrela desnormalizado, com a tabela de fatos "songplays" que nos fornece a info da música ouvida em determinado log de atividade. E as tabelas dimensionais que nos fornecem características adicionais dos fatos. 
![main](data_model_postgre.png)

## Criação do Pipeline de Dados 

## Estrutura do repositório 

    ├── data                   # .JSON files 
    |    ├── song_data         # Sub-dataset de "Milion Song Dataset" contendo metadata de músicas 
    │    └── log_data          # Logs de atividades de usuários gerado em'Event Data Simulator'
    ├── sql_queries.py         # Python script contendo SQL queries (CREATE/DROP/INSERT/DELETE statements e Joins);
    ├── elt.py                 # ETL script em Python; Extrai os dados da fonte, processa e insere no banco de dados PostgreSQL. 
    ├── etl.ipynb              # Jupyter notebook com o passo-a-passo explicativo do pipeline; 
    ├── create_tables.py       # Python script contém rotinas para conectar ao BD, criar e dropar tabelas; Usado durante o desenvolvimento/testes do pipeline;
    ├── test.ipynb             # Jupyter notebook contem rotinas para testar se as tabelas foram criadas corretamente; 
    └── README.md






