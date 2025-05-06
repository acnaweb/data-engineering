
# 📘 Roadmap Completo: Engenharia de Dados com GCP

---

## 🎯 Escala de Conhecimento por Nível

| Nível        | Descrição Geral                                                                 |
|--------------|----------------------------------------------------------------------------------|
| **Júnior**   | Conhece os fundamentos, executa tarefas com supervisão, entende o básico da nuvem e dados |
| **Pleno**    | Executa com autonomia, compreende arquitetura e boas práticas, contribui com soluções |
| **Sênior**   | Lidera iniciativas, propõe melhorias, domina arquitetura e pipelines fim a fim  |
| **Especialista** | Define padrões, mentora outros, projeta soluções complexas, representa a área em decisões técnicas |

---

## 🧭 Roadmap de Estudo – Engenharia de Dados com GCP

| Fase    | Tópico a Estudar                  | Exemplos                                           | Entregáveis                                                                 | Cronograma     |
|---------|----------------------------------|----------------------------------------------------|------------------------------------------------------------------------------|----------------|
| Fase 1  | Comandos básicos de Linux        | ls, cd, grep, find, chmod, crontab                 | Scripts bash versionados                                                    | Semanas 1–4    |
| Fase 1  | Shell scripting                   | scripts para backup, parsing de logs              | Scripts de automação com shell                                              | Semanas 1–4    |
| Fase 1  | Fundamentos de Redes              | HTTP vs HTTPS, ping, traceroute, NAT              | Documentação de rede VPC simulada                                           | Semanas 1–4    |
| Fase 1  | Git básico e avançado             | git clone, merge, rebase, GitFlow                 | Repositório Git com branches e PRs                                          | Semanas 1–4    |
| Fase 1  | Python básico                     | funções, classes, módulos, pandas                 | Scripts ETL simples com pandas                                              | Semanas 1–4    |
| Fase 1  | SQL avançado                      | JOINs, CTEs, índices, window functions            | Queries otimizadas e versionadas                                            | Semanas 1–4    |
| Fase 2  | Modelagem de dados OLTP e OLAP    | 3NF, Star Schema, Snowflake Schema                | Modelos conceituais no dbdiagram.io                                         | Semanas 5–10   |
| Fase 2  | BigQuery avançado                 | partitioning, clustering, materialized views      | Tabelas otimizadas e consultas complexas                                    | Semanas 5–10   |
| Fase 2  | Cloud Storage e IAM               | criação de buckets, roles, uniform access         | Configuração de buckets versionados                                         | Semanas 5–10   |
| Fase 2  | Dataflow / Apache Beam            | PCollection, ParDo, janela de tempo               | Pipeline simples com templates parametrizados                               | Semanas 5–10   |
| Fase 2  | Pub/Sub                           | pub/sub topics, dead-letter topics                | Configuração de tópico + subscrição com DLQ                                 | Semanas 5–10   |
| Fase 2  | Apache Airflow (Composer)         | DAGs, Operators, XCom                             | DAG com múltiplas dependências e paralelismo                                | Semanas 5–10   |
| Fase 2  | Dataform / dbt                    | incremental models, testes de schema              | Tabelas incrementais com testes e documentação                              | Semanas 5–10   |
| Fase 3  | Arquitetura GCP                   | VPC, subnets, NAT gateway, Cloud Run              | Diagrama C4 e plano de arquitetura GCP                                      | Semanas 11–16  |
| Fase 3  | Design Patterns para dados        | pipeline, event-driven, CQRS                      | Documentação com padrões aplicados                                          | Semanas 11–16  |
| Fase 3  | CI/CD e DataOps                   | GitHub Actions, Terraform tfvars                  | Pipelines com múltiplos ambientes e tfvars                                  | Semanas 11–16  |
| Fase 3  | Testes em pipelines de dados      | Great Expectations, Pytest                        | Testes automatizados com assertions e CI                                    | Semanas 11–16  |
| Fase 3  | Observabilidade e qualidade       | Stackdriver, Prometheus, Data Catalog             | Painel de métricas e alertas configurados                                   | Semanas 11–16  |
| Fase 3  | Governança e Segurança            | DLP, políticas de masking, RBAC                   | Policies, roles e criptografia de dados sensíveis                           | Semanas 11–16  |
| Fase 4  | ML com Vertex AI                  | Feature Store, treinamento e deploy de modelos    | Pipeline completo com treinamento e serving                                 | Semanas 17–24  |
| Fase 4  | Data Contracts                    | jsonschema, Pydantic, OpenAPI                     | YAMLs versionados e validados via CLI                                       | Semanas 17–24  |
| Fase 4  | Streaming com Kafka e Flink       | event time, watermarks                            | Pipeline com Flink integrado a Pub/Sub                                      | Semanas 17–24  |
| Fase 4  | Data Mesh                         | domínios, produtos de dados                       | PoC com 2 domínios e contratos independentes                                | Semanas 17–24  |
| Fase 4  | Projeto Final                     | pipeline batch+stream+ML                          | Projeto público com documentação e CI/CD                                    | Semanas 17–24  |

---

## 🏗️ Arquiteturas de Referência

| Arquitetura | Definição | Quando Usar | Aplicação na GCP |
|-------------|-----------|-------------|------------------|
| **Lambda**  | Combina batch e streaming com camadas distintas | Sistemas legados que precisam evoluir para streaming | Pub/Sub, Dataflow, BigQuery, Composer |
| **Kappa**   | Trata todo o fluxo como streaming               | Sistemas orientados a eventos em tempo real           | Pub/Sub, Dataflow (stream), BigQuery, Looker |
| **Medallion** | Organiza dados em Bronze, Silver, Gold         | Governança e rastreabilidade no Data Lake             | GCS, Dataflow, BigQuery, Dataform, Data Catalog |

---

## 💡 Desafios por Arquitetura

### 🔹 Lambda Architecture – Detecção de Fraude Bancária
- **Problema**: Detectar transações suspeitas em tempo real e manter dados históricos.
- **Objetivo**: Pipeline híbrido com batch e streaming.
- **Entradas**: Pub/Sub (real-time) + CSVs diários no Cloud Storage.
- **Componentes GCP**: Pub/Sub, Dataflow, BigQuery, Composer.
- **Entregáveis**:
  - DAG Composer com ingestão híbrida
  - Pipeline com Dataflow (batch e stream)
  - Views analíticas cruzando dados

### 🔹 Kappa Architecture – Telemetria IoT em Tempo Real
- **Problema**: Detectar anomalias em sensores industriais via stream.
- **Objetivo**: Pipeline 100% streaming com alerta e painel.
- **Entradas**: Eventos JSON via Pub/Sub.
- **Componentes GCP**: Pub/Sub, Dataflow, BigQuery, Looker, Cloud Functions.
- **Entregáveis**:
  - Pipeline com Watermarks
  - Alertas automáticos
  - Dashboard analítico

### 🔹 Medallion Architecture – Análise de Vendas com Governança
- **Problema**: Integrar dados de ERP, e-commerce e CRM com governança.
- **Objetivo**: Implementar arquitetura Medallion com camadas bronze, silver e gold.
- **Entradas**: JSON e CSV no Cloud Storage.
- **Componentes GCP**: GCS, Dataflow, BigQuery, Dataform, Data Catalog.
- **Entregáveis**:
  - Buckets organizados por camada
  - Modelos incrementais e testes no Dataform
  - Metadados e lineage no Data Catalog

---

## 📊 Matriz de Avaliação por Tema e Nível

| Tema                     | Júnior                                      | Pleno                                        | Sênior                                       | Especialista                                           |
|--------------------------|---------------------------------------------|----------------------------------------------|----------------------------------------------|--------------------------------------------------------|
| Linux e Shell            | Usa comandos básicos                        | Automatiza tarefas com shell                 | Scripts para deploy/ETL                      | Otimiza ambientes e define padrões                     |
| Redes                   | Entende HTTP/DNS                            | Soluciona problemas básicos                  | Desenha redes para pipelines                 | Planeja VPCs, NAT, firewalls e segurança               |
| Git/GitHub              | Clone e commit                              | Branching, PRs, GitFlow                      | Estratégias de versionamento                 | Integração com CI/CD                                   |
| Python                  | Scripts simples com pandas                  | Tipagem, testes, estruturação                | Bibliotecas reutilizáveis                    | SDKs, APIs, automação com GCP                          |
| SQL                     | SELECT, JOIN                                | CTEs, views, tuning                          | Modelagem dimensional                        | Arquitetura do warehouse                               |
| BigQuery                | Queries básicas                             | Partições, clustering                        | Monitoramento e automação                    | Arquitetura analítica e governança de custos           |
| Dataflow / Beam         | Pipeline simples                            | Windowing, transforms                        | Pipelines parametrizados                     | Arquitetura tempo real e otimização                    |
| Pub/Sub                 | Publica e consome mensagens                 | DLQ, ordering                                | Orquestra eventos                            | Alta performance com eventos                           |
| Composer / Airflow      | DAGs simples                                | XComs, dependências                          | Execução paralela                            | Arquitetura de orquestração                            |
| Dataform / dbt          | SQL simples                                 | Incremental, testes                          | CI/CD e ambientes                            | Padrões e modelo semântico                             |
| Testes de Dados         | Validações manuais                          | Great Expectations                           | Testes automatizados                         | Estratégia organizacional de qualidade                 |
| CI/CD e Terraform       | Entende pipeline básico                     | Terraform e revisão                          | Infraestrutura modular                       | GitOps com CLI customizado                             |
| Observabilidade         | Logs simples                                | Dashboards e alertas                         | Tracing e SLA de dados                        | Padrões operacionais completos                         |
| Segurança e Governança  | Roles básicos                               | RBAC, masking                                | Compliance                                   | Políticas automatizadas e auditoria                    |
| ML e Vertex AI          | Treinamento básico                          | Pipelines com deploy                         | MLOps com dados reais                         | Métricas, serving e automação                          |
| Data Contracts / Mesh   | Consome schema                              | Valida schema                                | Automatiza contratos                         | Arquitetura federada                                   |

---

## 🧩 Plano de Desenvolvimento Individual (PDI)

| Nível        | Critério                    | Sugestões de Desenvolvimento |
|--------------|-----------------------------|-------------------------------|
| Júnior       | Nota média entre 0.0 e 1.4  | Cursos básicos, supervisão próxima, foco em fundamentos |
| Pleno        | Nota média entre 1.5 e 2.4  | Projetos autônomos, testes, versionamento |
| Sênior       | Nota média entre 2.5 e 2.9  | Liderança técnica, CI/CD, monitoramento, mentoring |
| Especialista | Nota média entre 3.0 e 3.5  | Padrões técnicos, inovação, estratégia e governança |

---

## 📌 Plano de Ação Individual

| Nome   | Tema com Gap | Nota Atual | Meta | Ações Recomendadas                                                        | Prazo   | Responsável         | Observações             |
|--------|--------------|------------|------|---------------------------------------------------------------------------|---------|----------------------|--------------------------|
| Ana    | Dataflow     | 1          | 2    | Estudar curso GCP Dataflow, criar pipeline com template                  | 30 dias | Ana + Mentor Técnico |                          |
| Carlos | ML           | 1          | 2    | Laboratório Vertex AI com Feature Store                                  | 45 dias | Carlos               |                          |
| Ana    | Airflow      | 1          | 2    | Criar DAG com múltiplas tarefas, XCom e dependências                     | 30 dias | Ana                  | Revisar com Tech Lead    |
| João   | Data Mesh    | 2          | 3    | Ler material ThoughtWorks, simular domínio                               | 60 dias | João                 | Apresentar em tech talk  |