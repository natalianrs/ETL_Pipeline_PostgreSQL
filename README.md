<div align=right>
<a href="/README_pt.md"><img src="https://custom-icon-badges.herokuapp.com/badge/-ReadMe em Português BR-plum?style=for-the-badge&logo=comment-discussion&logoColor=black"/></a></div>

# Data Modeling and Data Pipeline in a Songs Streaming App 🎼


This case simulates activities from a songs streaming app. <br>
The final objective is to understand `which songs the users are listening and their habits of using the app`<br>
It was necessary to build a `otimized database` focused in facilite the SQL analysis process for the app data analytics team. <br>

Portanto, era preciso construir um `banco de dados otimizado` com foco em facilitar o processo de análise dos dados em SQL <br>  
## 🛠 Project Structure:
1. Modelagem dos dados relacionais;  
2. Coleta de dados das músicas e os logs de atividades dos usuários no app; 
3. Carregamento dos dados em um Data Warehouse em PostgreSQL;

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







