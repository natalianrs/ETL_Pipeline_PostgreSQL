<div align=left>
<a href="/README_pt.md"><img src="https://custom-icon-badges.herokuapp.com/badge/-ReadMe em Português BR-plum?style=for-the-badge&logo=comment-discussion&logoColor=black"/></a></div>

# Data Modeling and Data Pipeline in a Songs Streaming App 🎼 
- In a music streaming app, the data analytics team `analyzes data collected to understand the users habits and interests` 
in order to identify opportunities for improvement in the services, targeting business growth and optimization. 
- The data that needs to be analyzed contains song's informations and user's informations/logs, and they are stored in different places.
- In order to achieve a simpler way to analyze the data, an otimized datawarehouse was build to stored all the data together, in a strutured aggregated way using dimensions.   
- This method simplified the data analytics team way of doing queries and provide an easy and faster results for the business strategy . 

## 🛠 Project Structure:
1. Dimensional Data Modeling;  
2. Data extraction and collection;
3. Loading data into a Data Warehouse based in PostgreSQL;

![main](etl-pipeline.png)
### Estrutura do repositório 📂

    ├── data                   # .JSON files 
    |    ├── song_data         # Sub-dataset de "Milion Song Dataset" contendo metadata de músicas 
    │    └── log_data          # Logs de atividades de usuários gerado em'Event Data Simulator'
    ├── create_tables.py       # Python script contém rotinas para conectar ao BD, criar e dropar tabelas; Usado durante o desenvolvimento/testes do pipeline;
    ├── sql_queries.py         # Python script contendo SQL queries (CREATE/DROP/INSERT/DELETE statements e Joins);
    ├── elt.py                 # ETL script em Python; Extrai os dados da fonte e carrega no banco de dados PostgreSQL. 
    ├── test.ipynb             # Jupyter notebook contendo consultas SQL para testar a criação das tabelas e carregamento dos dados; 
    └── README.md



## Dados 💾
Foram usadas duas fontes de dados distintas. <br>
A 1a fonte é um sub-dataset do ["Milion Song Dataset"](http://millionsongdataset.com/) que contém `metadata de milhões de músicas`. <br> 
A 2a fonte de dados consiste em `logs de atividades` que foram geradas usando o ['Eventsim'](https://github.com/Interana/eventsim) para simular usuários reais do app.
> Todos os dados estão estruturados em arquivos .json

### Modelagem de Dados
Os dados foram modelados com o objetivo final de otimizar o processo de consultas SQL. <br>
Foi criado um esquema estrela desnormalizado, com a tabela de fatos "songplays" que nos fornece a info da música ouvida em determinado log de atividade. E as tabelas dimensionais que nos fornecem características adicionais dos fatos. 
![main](data_model_postgre.png)

## Pipeline de Dados ⚙
`sql_queries.py` é um modulo, a ser importado em ETL.py, que contem rotinas de DROP / CREATE / INSERT,  consultas SELECT com JOINS.<br>
`create_tables.py` é um script para criar novas tabelas, e deletar tabelas existentes (caso existam!) <br> 
`ETL.py` é script escrito em python com funções para conectar com o banco de dados, processar os dados na fonte, e carregar os dados nas tabelas já existentes. 
 
#### Como executar o pipeline de dados
1. Execute `$ python create_tables.py` para criar novas tabelas, e resetar as existentes (caso existam);
2. Execute `$ python etl.py` para iniciar a coleta e carregamento de dados;







