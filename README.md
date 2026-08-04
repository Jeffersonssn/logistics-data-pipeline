# 📦 Pipeline de Dados Logísticos

Pipeline de ETL automatizada desenvolvida com **Python** e **PostgreSQL** para ingestão, validação e armazenamento de dados logísticos provenientes de arquivos Excel e CSV em uma base histórica centralizada.

---

# 📌 Visão Geral

Este projeto foi desenvolvido para solucionar um problema real de processamento e armazenamento de dados logísticos.

O processo original dependia da exportação diária de relatórios, consolidação manual de diversos arquivos em Excel e análises realizadas por meio de Tabelas Dinâmicas. Com o crescimento contínuo da base histórica, o Excel passou a apresentar limitações de desempenho, capacidade e manutenção.

Como solução, foi desenvolvida uma pipeline automatizada utilizando Python e PostgreSQL, capaz de centralizar os dados, validar informações e construir uma base histórica escalável para futuras análises.

---

> **<img width="1774" height="887" alt="image" src="https://github.com/user-attachments/assets/f516067b-b4a6-45ca-af9b-ce588ced2bd4" />
** Fluxo completo da pipeline.

---

# 🎯 Problema de Negócio

A operação logística gerava diversos relatórios diariamente, que precisavam ser consolidados manualmente antes de qualquer análise.

Esse processo apresentava diversos problemas:

* Consolidação manual de vários arquivos
* Grande volume de registros
* Limitações de desempenho do Excel
* Risco de registros duplicados
* Alto tempo de processamento
* Dificuldade para consultas históricas
* Processo totalmente dependente de intervenção manual

O objetivo era automatizar toda essa etapa e criar uma base histórica confiável para consultas em SQL e ferramentas de Business Intelligence.

---

# 🚀 Solução Desenvolvida

Foi criada uma pipeline de ETL responsável por:

* Ler arquivos CSV e XLSX automaticamente
* Processar múltiplos arquivos em lote
* Validar regras de negócio
* Evitar registros duplicados
* Carregar os dados para o PostgreSQL
* Controlar arquivos já processados
* Centralizar o histórico dos pedidos
* Isolar automaticamente arquivos com erro

---

# 🛠️ Tecnologias Utilizadas

* Python
* Pandas
* PostgreSQL
* SQL
* Psycopg2
* OpenPyXL

---

# 📊 Arquitetura da Solução

```text
Arquivos CSV / XLSX
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
Consultas SQL / Power BI
```

> **📷 Inserir imagem:** Fluxograma da arquitetura.

---

# ⚙️ Principais Funcionalidades

## 📂 Importação Automática

Processa automaticamente todos os arquivos encontrados na pasta de entrada.

---

## 📄 Suporte a Múltiplos Formatos

Arquivos suportados:

* CSV
* XLSX

---

## ✅ Validação dos Dados

Antes da carga no banco, os registros passam por validações para garantir a integridade das informações e o cumprimento das regras de negócio.

---

## 🔄 Controle de Duplicidades

Cada registro é validado antes da inserção, impedindo pedidos duplicados e preservando o histórico da operação.

---

## 🚨 Tratamento de Erros

Arquivos que apresentam inconsistências são automaticamente separados em uma pasta específica para análise.

---

## 🗃️ Base Histórica

Todos os registros são armazenados em uma base PostgreSQL, permitindo consultas históricas e integração com ferramentas analíticas.

---

# 🗄️ Estrutura do Banco de Dados

## Schema

```text
raw
```

### Tabela Principal

```text
raw.firstfranqueados_raw
```

Responsável pelo armazenamento dos dados exatamente como são recebidos do sistema operacional (camada RAW).

---

### Tabela de Controle

```text
raw.arquivos_processados
```

Responsável por registrar:

* Nome do arquivo
* Data do processamento
* Quantidade de registros importados
* Status da execução
* Mensagens de erro

---

> **📷 Inserir print:** Estrutura das tabelas no PostgreSQL.

---

# 📁 Estrutura do Projeto

```text
projeto/

│

├── input/

├── processed/

├── error/

├── logs/

├── src/

│   ├── main.py

│   ├── database.py

│   ├── importer.py

│   ├── validator.py

│   └── utils.py

│

├── requirements.txt

├── README.md

└── .gitignore
```

> **📷 Inserir print:** Estrutura do projeto no VS Code.

---

# ▶️ Como Executar

Clone o repositório

```bash
git clone https://github.com/seu-usuario/logistics-data-pipeline.git
```

Instale as dependências

```bash
pip install -r requirements.txt
```

Execute a pipeline

```bash
python main.py
```

---

# 💻 Exemplo de Execução

```text
Procurando arquivos...

3 arquivos encontrados.

Lendo arquivos...

Validando registros...

45.821 linhas importadas.

0 registros duplicados.

Processamento concluído com sucesso.
```

> **📷 Inserir print:** Terminal executando a pipeline.

---

# 📈 Resultados Obtidos

Após a implementação da solução foi possível:

* Centralizar milhões de registros logísticos em um único banco de dados
* Eliminar a necessidade de consolidação manual em Excel
* Automatizar o processo de ingestão de dados
* Evitar registros duplicados
* Criar uma base histórica preparada para consultas SQL
* Disponibilizar os dados para integração com Power BI
* Construir uma solução escalável para futuras evoluções

---

# 🔮 Próximos Passos

* Implementação da camada tratada (Trusted)
* Criação de Views Analíticas
* Integração completa com Power BI
* Agendamento automático das cargas
* Monitoramento por logs
* Containerização com Docker
* Migração para ambiente em nuvem

---

# 👨‍💻 Autor

**Jefferson Novaes**

Projeto desenvolvido como aplicação prática de Engenharia de Dados para automatizar o processamento de dados logísticos, substituir processos manuais baseados em Excel e construir uma base histórica centralizada utilizando Python e PostgreSQL.
