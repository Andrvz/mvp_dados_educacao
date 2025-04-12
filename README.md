# 📊 Consulta aos Dados Educacionais

Este projeto organiza, trata e analisa dados públicos da educação básica brasileira, com foco nas **taxas de rendimento escolar**, **estrutura das escolas**, **indicadores de atendimento** e **distribuição regional**. O pipeline foi desenvolvido em ambiente Databricks, com arquitetura em camadas (Bronze, Silver e Gold), e segue os princípios de reprodutibilidade e clareza analítica.

---

## 🌐 Fontes de Dados Oficiais

Os dados utilizados foram extraídos diretamente do portal do INEP:

- [Taxas de rendimento escolar](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/indicadores-educacionais/taxas-de-rendimento-escolar)
- [Censo Escolar (Microdados)](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/censo-escolar)
- [Média de alunos por turma](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/indicadores-educacionais/media-de-alunos-por-turma)
- [Média de horas-aula diária](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/indicadores-educacionais/media-de-horas-aula-diaria)

---

## 🗂️ Arquitetura de Dados

O projeto está estruturado nas seguintes camadas:

#### Bronze (Raw)
Dados brutos importados diretamente das fontes:

- Formatos: `.csv`, `.xlsx`, `.ods`
- Leitura com inferência de schema
- Nomes de tabelas: `bronze.nome_da_tabela_ano`

#### Silver (Tratado)
Dados transformados e organizados por temas e granularidade:

- Padronização de nomes e tipos
- Segmentação temática por arquivo
- Tabelas tratadas:
  - `censo_escolar__escolas`
  - `censo_escolar__infra_*` (água, esgoto, professores, acessibilidade etc.)
  - `taxa_escolar__tap`, `__tre`, `__tab`
  - `alunos_por_turma__atu`, `hora_aula_diaria__had`
  - `d_calendario`, `d_escolas`, `d_municipios`, `d_series`

#### Gold (Analítico)
Camada final com indicadores prontos para análise:

- Tabelas de fatos: `indicadores_por_segmento`, `infraestrutura_escolar`
- Views analíticas: `vw_indicadores_completos`, `vw_taxas_por_uf_segmento_dependencia`
- Métricas agregadas por ano, UF, segmento e dependência

---

## 🛠️ Tecnologias Utilizadas

- Apache Spark (Databricks)
- Delta Lake (armazenamento)
- Python + SQL
- GitHub (versionamento e entrega)

---

## 📌 Objetivos Atendidos

- Análise comparativa entre estados
- Avaliação por tipo de escola (pública ou privada)
- Medição do atendimento escolar e infraestrutura
- Priorização de políticas públicas com base em evidências educacionais

---
