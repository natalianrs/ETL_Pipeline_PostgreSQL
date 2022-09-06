<a href="/README.md"><img src="https://custom-icon-badges.herokuapp.com/badge/-ReadMe in English-plum?style=for-the-badge&logo=comment-discussion&logoColor=black"/></a>

# Pipeline de Dados para um app de Streaming de Músicas 🎼
- Em um aplicativo de streaming de músicas, o time de data analytics `analiza os dados coletados para entender os hábitos e interesses dos usuários` com o objetivo de identificar oportunidades de melhoria nos serviços,  almejando o crescimento e a optimização do negócio.
- Os dados que precisam ser analizados contem informações das músicas disponíveis e dos usuários do app, e estão salvos em dois lugares diferentes dificultado o processo de realização de consultas.
- Objetivando uma maneira simples de analizar os dados,  um datawarehouse foi construído para salvar todos os dados em conjunto de uma forma estruturada usando tabelas dimensionais. 
- Este método simplica a maneira de realizar consultas e proporciona resultados para o business analytics com mais rapidez e facilidade.  

## 🛠 Estrutura do Projeto:
1. Modelagem dimensional dos dados relacionais;  
2. Extração e coleta de dados das músicas e os logs de atividades dos usuários no app; 
3. Carregamento dos dados em um Data Warehouse com PostgreSQL;

![main](etl-pipeline.png)
### Estrutura do repositório 📂

    ├── data                   # .JSON files 
    |    ├── song_data         # Contém informações e metadata de músicas 
    │    └── log_data          # Contém informações e logs de atividades dos usuários. 
    ├── create_tables.py       # Contém rotinas para conectar ao BD, criar e dropar tabelas;
    ├── sql_queries.py         # Contém SQL queries (CREATE/DROP/INSERT/DELETE statements e Joins);
    ├── elt.py                 # Extrai os dados da fonte e carrega no banco de dados PostgreSQL. 
    ├── test.ipynb             # Contém rotinas para testar a criação das tabelas e carregamento; 
    └── README.md

## Dados 💾
Este projeto simula as atividades de um app de streaming de músicas.
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





