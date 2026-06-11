# logistics-data-pipeline

Logistics data pipeline built with Python and PostgreSQL for automated ingestion and historical data storage.

📌 Visão Geral

Este projeto foi desenvolvido para resolver um problema real de processamento e armazenamento de dados logísticos.

O processo original dependia da extração diária de relatórios em Excel, conversão para CSV, consolidação através do Power Query e análise por meio de Tabelas Dinâmicas. Com o aumento do volume de dados, o Excel passou a apresentar limitações de desempenho e capacidade.

A solução foi a criação de uma pipeline automatizada utilizando Python e PostgreSQL para centralizar, armazenar e gerenciar o histórico completo dos pedidos.

🎯 Problema de Negócio

Os relatórios operacionais gerados pelo sistema da empresa frequentemente ultrapassavam o limite prático de manipulação no Excel.

Principais desafios:
Grande volume de registros diários;
Necessidade de exportar múltiplos arquivos para um único dia;
Consolidação manual dos arquivos;
Crescimento contínuo do histórico;
Risco de duplicidade de registros;
Dificuldade para realizar análises históricas.
🚀 Solução Desenvolvida

Foi criada uma pipeline de ingestão de dados capaz de:

Ler arquivos CSV e XLSX;
Processar múltiplos arquivos automaticamente;
Carregar os dados para o PostgreSQL;
Impedir a inserção de pedidos duplicados;
Registrar o histórico de arquivos processados;
Manter uma base histórica centralizada;
Organizar automaticamente os arquivos processados.


🛠️ Tecnologias Utilizadas
Python
Pandas
PostgreSQL
Psycopg2
SQL
OpenPyXL


📊 Fluxo da Solução

Sistema Operacional
        │
        ▼
 Arquivos CSV/XLSX
        │
        ▼
 Pipeline em Python
        │
        ▼
 Validação e Tratamento
        │
        ▼
 PostgreSQL
        │
        ▼
 Base Histórica Centralizada

 
⚙️ Funcionalidades
Importação Automática

Processa automaticamente todos os arquivos presentes na pasta de entrada.

Suporte a Múltiplos Formatos

Compatível com:

CSV
XLSX
Controle de Arquivos Processados

Evita reprocessamento através de uma tabela de controle.

Deduplicação

Utiliza o campo Número de Pedido JMS como identificador único para impedir registros duplicados.

Tratamento de Erros

Arquivos com falhas são direcionados automaticamente para uma pasta específica para análise.

🗄️ Estrutura do Banco de Dados

Schema RAW

Tabela principal:
raw.firstfranqueados_raw
Responsável por armazenar todos os dados importados sem transformações de negócio.

Tabela de controle:
raw.arquivos_processados
Responsável por registrar:

Nome do arquivo;
Data de processamento;
Quantidade de registros importados;
Status do processamento;
Mensagens de erro.


📈 Resultados Obtidos
Centralização de milhões de registros logísticos;
Eliminação das limitações do Excel para armazenamento histórico;
Redução do trabalho manual de consolidação de arquivos;
Controle de duplicidades;
Base preparada para futuras análises em SQL e ferramentas de BI.


🔮 Próximos Passos
Implementação de camada tratada para análise;
Criação de views analíticas;
Integração com Power BI;
Agendamento automático das cargas;
Monitoramento por logs.


👨‍💻 Autor

Jefferson Novaes

Projeto desenvolvido como iniciativa de estudo e aplicação prática de Engenharia e Análise de Dados, utilizando dados operacionais do setor de logística para construção de uma solução de armazenamento histórico e processamento automatizado.
