# 🚲 Seoul Bike Sharing Demand — Previsão de Procura (Regressão)

Projeto de Aprendizagem Automática desenvolvido no âmbito da unidade curricular de **Inteligência Artificial** (ESTGA — Universidade de Aveiro). O objetivo é prever o número de bicicletas alugadas por hora (`Rented Bike Count`) em Seul com base em condições meteorológicas e dados temporais.

## 👥 Autoras

- **Jéssica Pereira**
- **Nadia Bento**

---

## 📋 Visão Geral do Projeto

O dataset utilizado (`SeoulBikeData.csv`) contém **8.760 registos horários** (1 ano completo, de dezembro de 2017 a novembro de 2018) com 14 variáveis meteorológicas e de calendário .

### Estrutura do Notebook

O trabalho encontra-se dividido em quatro partes principais:

| Parte                                        | Secções | Conteúdo                                                                                                                                   |
| :------------------------------------------- | :------ | :----------------------------------------------------------------------------------------------------------------------------------------- |
| **I — Dados, preparação e baselines**        | 1 a 7   | Carregamento, limpeza, engenharia de _features_, split temporal, função de avaliação e _baselines_ (`DummyRegressor` e Regressão Linear) . |
| **II — Exploração e modelos lineares**       | 8 a 12  | Análise Exploratória de Dados (EDA), Regressão Polinomial, Ridge, Lasso, codificação categórica da hora e otimização com `GridSearchCV` .  |
| **III — Modelos não lineares e diagnóstico** | 13 a 17 | Árvores de Decisão, Random Forest, otimização de hiperparâmetros, importância das variáveis e análise de resíduos .                        |
| **IV — Síntese comparativa**                 | 18      | Tabela comparativa geral de desempenho e discussão crítica dos resultados .                                                                |

---

## ⚙️ Metodologia e Boas Práticas

- **Limpeza de Dados:** Remoção de 295 registos correspondentes a dias em que o sistema esteve encerrado (`Functioning Day = No`), ficando **8.465 horas** válidas .
- **Engenharia de Variáveis (_Features_):**
  - Extração de `month`, `dayofweek` e `is_weekend` a partir da data .
  - Transformação cíclica da hora (`hour_sin`, `hour_cos`) para modelos lineares, mantendo `hour` para modelos baseados em árvores .
  - Codificação _One-Hot_ para as estações do ano (`season`) e binarização de `holiday` .
- **Validação Temporal (Prevenção de _Data Leakage_):**
  - Divisão cronológica estrita: **80% treino** (6.772 horas) e **20% teste** (1.693 horas) .
  - Validação cruzada com `TimeSeriesSplit` (5 _folds_) aplicada exclusivamente ao conjunto de treino .
  - Normalização (`StandardScaler`) encapsulada em `Pipeline` apenas sobre variáveis numéricas contínuas .
- **Métricas de Avaliação:** `MAE` (Mean Absolute Error), `RMSE` (Root Mean Squared Error) e $R^2$ (Coeficiente de Determinação)

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

- **Python 3**
- `pandas` & `numpy` (manipulação e processamento de dados)
- `matplotlib` & `seaborn` (visualização e EDA)
- `scikit-learn` (pré-processamento, validação cruzada, modelos lineares e de ensemble)
- `ipykernel` / `jupyter` (execução do notebook interativo)

---

## 🚀 Como Executar

1. **Clonar o repositório:**
   ```bash
   git clone <url-do-repositorio>
   cd <nome-do-repositorio>
   ```
