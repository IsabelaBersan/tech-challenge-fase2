# data/

# 🍷 Wine Quality Classification

## Classificação da Qualidade de Vinhos com Machine Learning

### 📊 Sobre o Projeto

Este projeto foi desenvolvido como parte do Tech Challenge – Fase 2 da Pós-Graduação em Data Analytics da FIAP.

O objetivo é analisar características físico-químicas de vinhos tintos e desenvolver modelos de Machine Learning capazes de classificar sua qualidade em duas categorias:

- **Baixa/Média Qualidade:** nota de qualidade < 6
- **Alta Qualidade:** nota de qualidade ≥ 6

A partir da Análise Exploratória de Dados (EDA), foram investigadas as distribuições das variáveis, correlações, possíveis outliers e o balanceamento das classes.

Na etapa de modelagem, foram testados os algoritmos **K-Nearest Neighbors (KNN)** e **Support Vector Machine (SVM)**, utilizando inicialmente as variáveis preditoras disponíveis e, posteriormente, um conjunto reduzido de quatro variáveis selecionadas a partir dos resultados da análise exploratória.

O projeto também utilizou **Random Forest** como análise complementar para avaliar a relevância das variáveis na classificação.

---

## 🎯 Objetivos

- Explorar e compreender as características presentes no conjunto de dados;
- Verificar a existência de valores ausentes, duplicidades e possíveis outliers;
- Analisar a relação entre as características físico-químicas e a qualidade dos vinhos;
- Transformar a variável `quality` em uma classificação binária;
- Realizar o pré-processamento dos dados para utilização nos modelos;
- Comparar o desempenho dos modelos KNN e SVM;
- Avaliar os modelos utilizando métricas como acurácia, AUC e F1-score;
- Identificar as variáveis com maior relevância para a classificação;
- Avaliar possíveis aplicações dos modelos no apoio ao controle de qualidade.

---

## 🍷 Base de Dados

Foi utilizado o **Wine Quality Dataset**, disponibilizado publicamente no Kaggle.

A base utilizada no projeto possui **1.143 registros e 13 colunas**, contendo características físico-químicas dos vinhos e sua respectiva avaliação de qualidade.

Entre as variáveis disponíveis estão:

- `fixed acidity` – acidez fixa
- `volatile acidity` – acidez volátil
- `citric acid` – ácido cítrico
- `residual sugar` – açúcar residual
- `chlorides` – cloretos
- `free sulfur dioxide` – dióxido de enxofre livre
- `total sulfur dioxide` – dióxido de enxofre total
- `density` – densidade
- `pH`
- `sulphates` – sulfatos
- `alcohol` – teor alcoólico
- `quality` – nota de qualidade
- `Id` – identificador da amostra

### Variável-alvo

A variável `quality` foi transformada em uma classificação binária:

| Nota | Classificação |
|---|---|
| `< 6` | Baixa/Média Qualidade |
| `>= 6` | Alta Qualidade |

**Fonte:** [Wine Quality Dataset – Kaggle](https://www.kaggle.com/datasets/yasserh/wine-quality-dataset)

---

## 🔎 Metodologia

O desenvolvimento do projeto foi dividido nas seguintes etapas:

### 1. Análise Exploratória de Dados (EDA)

Foram realizadas análises para compreender o comportamento dos dados, incluindo:

- distribuição das notas de qualidade;
- análise do balanceamento das classes;
- identificação de valores ausentes e duplicidades;
- análise de possíveis outliers;
- matriz de correlação de Pearson;
- análise da relação entre as características físico-químicas e a qualidade;
- boxplots das principais variáveis.

### 2. Pré-processamento

Foram realizadas as seguintes etapas:

- remoção da coluna `Id`, por se tratar de um identificador;
- criação da variável-alvo binária a partir de `quality`;
- separação entre variáveis preditoras e variável-alvo;
- divisão dos dados em treino e teste;
- normalização das variáveis numéricas;
- utilização de `stratify` na divisão dos dados para preservar a proporção das classes.

### 3. Modelagem

Foram avaliados dois algoritmos de classificação:

- **K-Nearest Neighbors (KNN)**
- **Support Vector Machine (SVM)**

Os modelos foram otimizados utilizando **GridSearchCV**.

Foram realizadas duas abordagens:

1. utilização das 11 variáveis preditoras;
2. utilização de um conjunto reduzido de 4 variáveis:

   - `alcohol`
   - `volatile acidity`
   - `sulphates`
   - `citric acid`

### 4. Análise da importância das variáveis

Como análise complementar, foi utilizado o algoritmo **Random Forest** para avaliar a relevância das variáveis e verificar se os resultados observados na análise exploratória eram consistentes com a importância apresentada pelo modelo.

---

## 🏆 Resultados

Os modelos apresentaram os seguintes resultados:

| Modelo | Nº de variáveis | Acurácia | AUC | F1-Score |
|---|---:|---:|---:|---:|
| KNN | 11 | 78,6% | 0,857 | — |
| **KNN** | **4** | **80,3%** | **0,873** | **0,825** |
| SVM | 11 | 78,6% | 0,842 | — |
| SVM | 4 | 77,7% | 0,838 | — |

### ⭐ Melhor modelo

O melhor desempenho geral entre os modelos avaliados foi obtido pelo **KNN utilizando apenas 4 variáveis**:

- **Acurácia:** 80,3%
- **AUC:** 0,873
- **F1-Score:** 0,825

As variáveis utilizadas foram:

`alcohol`, `volatile acidity`, `sulphates` e `citric acid`.

Um resultado relevante do projeto foi observar que a utilização de um conjunto menor de variáveis não necessariamente reduz o desempenho do modelo. Neste caso, o KNN apresentou desempenho superior utilizando quatro variáveis em comparação à abordagem com as 11 variáveis.

Esse resultado também reforça a importância da seleção de variáveis na construção de modelos de Machine Learning.

---

## 💡 Principais Insights

A análise realizada indicou que algumas características físico-químicas apresentam maior relação com a classificação da qualidade dos vinhos.

Entre as variáveis analisadas, destacaram-se:

- **Teor alcoólico (`alcohol`)**
- **Acidez volátil (`volatile acidity`)**
- **Sulfatos (`sulphates`)**
- **Ácido cítrico (`citric acid`)**

Essas quatro variáveis foram utilizadas na construção do modelo KNN que apresentou o melhor desempenho.

Os resultados indicam que características físico-químicas podem fornecer informações relevantes para apoiar a classificação da qualidade dos vinhos.

---

## 📌 Possíveis Aplicações

Um modelo desse tipo pode ser utilizado como ferramenta de apoio em processos de controle de qualidade, permitindo:

- classificação preliminar de amostras;
- identificação de padrões associados a vinhos de maior qualidade;
- apoio à análise de lotes;
- monitoramento de características físico-químicas;
- suporte à tomada de decisão durante processos produtivos.

O modelo, entretanto, deve ser utilizado como **ferramenta de apoio**, não como substituto da avaliação sensorial realizada por especialistas.

---

## ⚠️ Limitações

Algumas limitações devem ser consideradas na interpretação dos resultados:

- a transformação da variável `quality` em duas classes simplifica a avaliação original de qualidade;
- a distribuição das classes não é completamente equilibrada;
- os resultados estão condicionados às características e ao tamanho da base utilizada;
- importância de variável e correlação não devem ser interpretadas como relações de causalidade;
- os modelos foram desenvolvidos para apoio à classificação e não para substituir a avaliação sensorial de especialistas.

---

## 🛠️ Tecnologias Utilizadas

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook
- GridSearchCV
- KNeighborsClassifier
- SVC
- RandomForestClassifier

---

## 📁 Estrutura do Repositório

```text
wine-quality-classification/
│
├── data/
│   └── WineQT.csv
│
├── notebooks/
│   └── análise_modelagem.ipynb
│
├── results/
│   ├── gráficos/
│   └── métricas/
│
├── TechChallenge_2.docx
├── requirements.txt
└── README.md
