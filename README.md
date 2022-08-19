# Pipeline de Dados ETL em PostgreSQL

![main](etl-pipeline.png)

## Estrutura do repositório 
├── data                   # .JSON files <br>
│   ├── song_data						          # Sub-dataset de "Milion Song Dataset" contendo metadata de músicas <br>

│   └── log_data           # Logs de atividades de usuários gerado por 'Event Data Simulator' (https://github.com/Interana/eventsim) 
├── sql_queries.py         # Py script contém SQL queries usadas no processo de ETL
├── elt.py                 # ETL script em Python 
├── etl.ipynb              # Jupyter notebook com o passo-a-passo explicativo de ETL.py
├── create_tables.py       # Python script contém rotinas para criar e dropar tabelas usada no desenvolvimento da ETL
├── test.ipynb             # Jupyter notebook contem rotinas para testar se o banco de dados foi criado corretamente 
└── README.md



![main](data_model_postgre.png)





