# Projeto de Análise de Dados — Acidentes de Trânsito nas Rodovias Federais

## Sobre o projeto

Os acidentes de trânsito representam um problema relevante de segurança pública, gerando impactos sociais e econômicos. A análise de dados pode contribuir para a identificação de padrões e características associadas à ocorrência e à gravidade dos acidentes.

Este projeto analisa dados públicos da **Polícia Rodoviária Federal (PRF)** referentes aos acidentes registrados em rodovias federais brasileiras entre **2023 e 2025**.

O objetivo é identificar padrões relacionados ao volume, localização, causas e gravidade dos acidentes, utilizando Python para o tratamento e a análise exploratória dos dados e o Looker Studio para a apresentação dos resultados.

---

# 1. Coleta de dados

## Fonte dos dados

Os dados utilizados são provenientes da base de **Dados Abertos da Polícia Rodoviária Federal (PRF)**.

Foram utilizados os arquivos referentes aos anos de:

- 2023
- 2024
- 2025

Os dados foram disponibilizados em arquivos **CSV**, contendo informações sobre os acidentes registrados nas rodovias federais brasileiras.

Entre as variáveis disponíveis estão:

- Data e horário da ocorrência
- Unidade Federativa (UF)
- Município
- Causa do acidente
- Tipo de acidente
- Classificação do acidente
- Condição meteorológica
- Tipo de pista
- Traçado da via
- Número de pessoas envolvidas
- Número de mortos
- Número de feridos
- Número de veículos
- Latitude e longitude
- Quilômetro da rodovia

## Tecnologias utilizadas

- Python
- Pandas
- Google Colab
- Looker Studio
- GitHub

Os arquivos CSV foram importados no Google Colab utilizando a biblioteca Pandas, considerando o separador `;` e a codificação `latin-1`.

---

# 2. Modelagem e tratamento dos dados

Após a coleta, foi realizada uma análise exploratória da estrutura e da qualidade dos dados.

## Conhecimento e validação das bases

Inicialmente foram verificadas:

- Quantidade de registros;
- Quantidade de variáveis;
- Nomes das colunas;
- Tipos de dados;
- Valores ausentes;
- Registros duplicados;
- Identificadores duplicados;
- Consistência entre variáveis quantitativas.

As bases apresentaram:

| Ano | Registros |
|---|---:|
| 2023 | 67.766 |
| 2024 | 73.156 |
| 2025 | 72.529 |
| **Total** | **213.451** |

As três bases possuem estrutura compatível, permitindo sua consolidação.

## Tratamento dos dados

Foram realizadas as seguintes etapas:

### Valores ausentes

Foram identificados poucos registros com valores ausentes, principalmente em variáveis administrativas como `regional`, `delegacia` e `uop`.

Como a quantidade de registros afetados representa uma parcela muito pequena das bases, os registros não foram excluídos. Os valores ausentes foram preservados e considerados conforme a necessidade de cada análise.

### Duplicidades

Não foram encontrados registros completamente duplicados.

Também não foram identificados valores duplicados na variável `id` dentro de cada ano.

### Padronização das variáveis

Foram realizadas correções de formato nas principais variáveis utilizadas nas análises:

- `id`
- `latitude`
- `longitude`
- `km`
- `data_inversa`

A variável `id` foi padronizada para formato inteiro.

Latitude e longitude foram convertidas para formato numérico, realizando a substituição da vírgula pelo ponto quando necessário.

A variável `km` também foi convertida para formato numérico.

A variável `data_inversa` foi convertida para o formato `datetime`, permitindo a realização de análises temporais.

### Verificação de consistência

Foram verificadas as relações entre variáveis quantitativas.

A variável `feridos` apresentou consistência em todos os registros, correspondendo à soma de `feridos_leves` e `feridos_graves`.

Também foi investigada a relação entre `pessoas` e as categorias de pessoas envolvidas. As diferenças encontradas foram analisadas e não foram realizadas alterações nos valores originais, evitando modificar os dados sem uma justificativa baseada na definição da fonte.

## Consolidação

Após a padronização e validação, as bases de 2023, 2024 e 2025 foram consolidadas em uma única base.

A base final contém:

**213.451 registros e 30 variáveis.**

Essa consolidação permitiu realizar análises comparativas entre os anos e investigar padrões no período completo.

---

# 3. Conclusões

A análise exploratória permitiu identificar diferentes padrões relacionados aos acidentes registrados nas rodovias federais brasileiras entre 2023 e 2025.

## Principais resultados

Foram registrados **213.451 acidentes** no período analisado.

Desses:

- **15.290 foram acidentes fatais**;
- **17.830 mortes** foram registradas;
- **246.539 feridos** foram registrados;
- Os acidentes fatais representaram **7,16%** do total.

### Evolução anual

2024 apresentou o maior número de acidentes, com **73.156 ocorrências**.

Em 2025 houve uma pequena redução, com **72.529 acidentes**.

Apesar da variação no número total de ocorrências, a proporção de acidentes fatais permaneceu bastante estável nos três anos, próxima de **7,1%**.

### Distribuição por estado

A quantidade absoluta de acidentes não apresentou o mesmo comportamento observado na proporção de acidentes fatais.

**Minas Gerais** apresentou o maior número de acidentes, com **27.873 ocorrências**.

Por outro lado, considerando a proporção de acidentes fatais:

- **Maranhão:** 19,59%
- **Pará:** 18,92%
- **Bahia:** 11,61%

Esse resultado demonstra a importância de analisar não apenas o volume de acidentes, mas também sua gravidade proporcional.

### Principais causas

Entre as causas mais frequentes estão:

- Reação tardia ou ineficiente do condutor;
- Ausência de reação do condutor;
- Acessar a via sem observar a presença dos outros veículos;
- Condutor deixou de manter distância do veículo da frente;
- Velocidade incompatível.

Entretanto, frequência e gravidade não apresentaram necessariamente o mesmo comportamento.

Entre as dez causas mais frequentes analisadas, **"Transitar na contramão"** apresentou a maior proporção de acidentes fatais, com **28,96%**.

Também se destacaram:

- Velocidade incompatível: **8,95%**
- Condutor dormindo: **7,22%**

Esses resultados mostram que as causas mais frequentes não são necessariamente aquelas associadas às maiores proporções de acidentes fatais.

> Os resultados identificam associações presentes nos dados e não permitem afirmar, isoladamente, que determinada causa seja responsável pela ocorrência de mortes.

---

# Visualização dos resultados

Os principais resultados da análise foram apresentados em um dashboard desenvolvido no **Looker Studio**.

O dashboard permite explorar visualmente informações relacionadas a:

- Distribuição dos acidentes por UF;
- Proporção de acidentes fatais;
- Principais causas dos acidentes;
- Comparações entre diferentes categorias;
- Indicadores gerais do período analisado.

### Dashboard

**[Acessar o Dashboard no Looker Studio](https://datastudio.google.com/reporting/0a51b1b4-4c5e-45ff-a4e9-47a9d459690e)**

---

# Notebook da análise

O processo completo de tratamento, validação, consolidação e análise exploratória dos dados está disponível no notebook desenvolvido em Python.

**Arquivo:** `projeto_acidentes_prf[.ipynb`

O notebook contém todo o processo de análise, desde a importação dos arquivos originais até a geração dos principais insights utilizados no dashboard.

---

# Considerações finais

A análise demonstrou que a utilização de dados públicos permite identificar padrões relevantes sobre os acidentes ocorridos nas rodovias federais brasileiras.

Os resultados também evidenciam a importância de combinar diferentes indicadores. A análise apenas do número de ocorrências poderia levar a conclusões diferentes daquela obtida quando a gravidade dos acidentes é considerada.

Dessa forma, a análise de dados pode apoiar a identificação de padrões e contribuir para o direcionamento de ações de prevenção e segurança no trânsito.

---

## Autor

**Meysa Souza**

Projeto desenvolvido como parte do projeto Semantix em parceria com EBAC no curso de análise de dados.
