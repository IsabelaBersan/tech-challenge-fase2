# 🍷 Wine Quality Classification

## Classificação da Qualidade de Vinhos com Machine Learning

Projeto desenvolvido para o **Tech Challenge — Fase 2 da Pós-Graduação em Data Analytics da FIAP**, com o objetivo de analisar características físico-químicas de vinhos tintos e desenvolver modelos de Machine Learning capazes de classificar sua qualidade.

---

## 📊 Sobre o Projeto

A qualidade de um vinho está relacionada a diferentes características físico-químicas, como acidez, açúcar residual, cloretos, dióxido de enxofre, densidade, pH, sulfatos e teor alcoólico.

Neste projeto, foi utilizado o **Wine Quality Dataset**, contendo informações físico-químicas de amostras de vinhos tintos e uma avaliação de qualidade atribuída por avaliadores.

O objetivo foi investigar quais características apresentam maior relação com a qualidade e verificar se modelos de Machine Learning conseguem classificar os vinhos em duas categorias:

- **Regular/Ruim:** qualidade < 6
- **Bom:** qualidade ≥ 6

A análise foi desenvolvida em Python, contemplando Análise Exploratória de Dados (EDA), pré-processamento, modelagem e avaliação dos resultados.

---

## 🎯 Objetivos

### Objetivo geral

Analisar as características físico-químicas de vinhos tintos e desenvolver modelos de Machine Learning capazes de classificar as amostras de acordo com sua qualidade.

### Objetivos específicos

- Explorar e compreender as características presentes no conjunto de dados;
- Verificar valores ausentes, duplicidades e possíveis outliers;
- Analisar a distribuição da variável `quality`;
- Investigar a relação entre as características físico-químicas e a qualidade;
- Transformar a variável `quality` em uma classificação binária;
- Realizar o pré-processamento dos dados;
- Comparar os modelos KNN e SVM;
- Avaliar os modelos utilizando métricas de desempenho;
- Identificar as variáveis com maior importância para a previsão da qualidade;
- Analisar possíveis aplicações dos resultados no controle de qualidade dos vinhos.

---

## 🍷 Base de Dados

O projeto utiliza o **Wine Quality Dataset**, disponibilizado no Kaggle.

A base analisada possui:

- **1.143 registros**
- **13 colunas**
- 11 características físico-químicas
- 1 variável de qualidade (`quality`)
- 1 identificador (`Id`)

Entre as características analisadas estão:

- `fixed acidity`
- `volatile acidity`
- `citric acid`
- `residual sugar`
- `chlorides`
- `free sulfur dioxide`
- `total sulfur dioxide`
- `density`
- `pH`
- `sulphates`
- `alcohol`

A variável original `quality` possui notas entre 3 e 8 no conjunto analisado. :contentReference[oaicite:2]{index=2}

### Fonte

Wine Quality Dataset — Kaggle:

https://www.kaggle.com/datasets/yasserh/wine-quality-dataset

---

## 🔎 Análise Exploratória de Dados

A Análise Exploratória de Dados foi realizada com o objetivo de compreender a distribuição das variáveis e identificar possíveis relações entre as características físico-químicas e a qualidade dos vinhos.

Foram realizadas análises como:

- Distribuição da variável `quality`;
- Análise da distribuição das classes;
- Matriz de correlação de Pearson;
- Identificação de possíveis outliers;
- Boxplots das principais características por classe de qualidade.

A análise de correlação indicou que:

- `alcohol` apresentou a maior correlação positiva com a qualidade, aproximadamente **0,48**;
- `volatile acidity` apresentou uma das principais correlações negativas, aproximadamente **-0,41**.

Esses resultados foram posteriormente comparados com a importância das variáveis obtida através do Random Forest. :contentReference[oaicite:3]{index=3}

---

## 🧪 Pré-processamento

Antes da aplicação dos modelos, foram realizadas as seguintes etapas:

### Remoção da variável `Id`

A coluna `Id` foi removida por representar apenas um identificador das amostras, sem relação direta com as características físico-químicas. :contentReference[oaicite:4]{index=4}

### Criação da variável-alvo

A variável `quality` foi transformada em uma variável binária denominada `quality_binary`.

| Qualidade | Classificação |
|---|---|
| < 6 | Regular/Ruim |
| ≥ 6 | Bom |

:contentReference[oaicite:5]{index=5}

### Separação treino e teste

Os dados foram divididos em:

- **80% para treinamento**
- **20% para teste**

Foi utilizado `stratify` para preservar uma proporção semelhante das classes nos conjuntos de treinamento e teste. :contentReference[oaicite:6]{index=6}

### Padronização

As variáveis foram padronizadas antes da aplicação dos modelos.

Essa etapa foi especialmente importante para KNN e SVM, pois ambos podem ser influenciados pela escala das variáveis. A transformação foi ajustada utilizando apenas os dados de treinamento e posteriormente aplicada ao conjunto de teste. :contentReference[oaicite:7]{index=7}

---

## 🤖 Modelagem

Foram utilizados dois algoritmos de classificação:

- **K-Nearest Neighbors (KNN)**
- **Support Vector Machine (SVM)**

Os dois modelos foram avaliados em dois cenários:

1. Utilizando as **11 variáveis físico-químicas**;
2. Utilizando apenas **4 variáveis selecionadas**:

   - `alcohol`
   - `volatile acidity`
   - `sulphates`
   - `citric acid`

A seleção das quatro variáveis foi baseada nos resultados observados durante a análise exploratória. :contentReference[oaicite:8]{index=8}

Para otimização dos modelos foi utilizado **GridSearchCV** com validação cruzada de 5 folds.

No SVM foi utilizado o **kernel RBF**, avaliando diferentes combinações dos hiperparâmetros `C` e `gamma`. :contentReference[oaicite:9]{index=9}

---

## 📈 Resultados

| Modelo | Variáveis | Acurácia | AUC | F1-Score |
|---|---:|---:|---:|---:|
| KNN | 11 | 78,6% | 0,857 | — |
| **KNN** | **4** | **80,3%** | **0,873** | **0,825** |
| SVM | 11 | 78,6% | 0,842 | — |
| SVM | 4 | 77,7% | 0,838 | — |

O melhor resultado obtido foi o **KNN utilizando quatro variáveis**, alcançando:

- **Acurácia:** 80,3%
- **AUC:** 0,873
- **F1-Score:** 0,825

O KNN com quatro variáveis também apresentou melhora em relação à utilização das 11 variáveis, passando de 78,6% para 80,3% de acurácia e de 0,857 para 0,873 de AUC. :contentReference[oaicite:10]{index=10}

Já no SVM, a redução para quatro variáveis apresentou uma pequena perda de desempenho: a acurácia passou de 78,6% para 77,7% e o AUC de 0,842 para 0,838. :contentReference[oaicite:11]{index=11}

### ⚠️ Interpretação dos resultados

Apesar de o KNN com quatro variáveis ter apresentado o melhor resultado, a diferença entre os modelos foi relativamente pequena.

A diferença entre a maior e a menor acurácia foi de apenas **2,6 pontos percentuais**, considerando o conjunto de teste com 229 amostras.

Além disso, o experimento utilizou uma única divisão entre treinamento e teste. Dessa forma, os resultados não devem ser interpretados como evidência definitiva de superioridade de um algoritmo sobre o outro. :contentReference[oaicite:12]{index=12}

---

## 🌳 Importância das Variáveis

Como análise complementar, foi utilizado um modelo **Random Forest** para avaliar a importância relativa das 11 características físico-químicas.

O Random Forest indicou como principais variáveis:

1. `alcohol`
2. `sulphates`
3. `total sulfur dioxide`
4. `volatile acidity`

O teor alcoólico apresentou a maior importância, com valor próximo de 0,20. :contentReference[oaicite:13]{index=13}

A análise também reforçou os resultados observados na matriz de correlação, principalmente em relação ao `alcohol` e à `volatile acidity`.

É importante destacar que a importância de uma variável no modelo representa sua contribuição para a previsão e **não significa necessariamente uma relação de causa e efeito** com a qualidade do vinho. :contentReference[oaicite:14]{index=14}

---

## 🍇 Possíveis Aplicações

Os resultados indicam que modelos de Machine Learning podem ser utilizados como uma ferramenta complementar no processo de análise da qualidade dos vinhos.

Uma aplicação possível seria utilizar as características físico-químicas disponíveis para identificar amostras com maior ou menor probabilidade de pertencer à categoria de boa qualidade.

Entretanto, o modelo não deve substituir a avaliação de especialistas. Os resultados representam associações encontradas nos dados e capacidade de classificação, não permitindo afirmar que alterações isoladas em determinada característica necessariamente aumentarão a qualidade do vinho. :contentReference[oaicite:15]{index=15}

---

## 🏆 Modelo Selecionado

Considerando os resultados obtidos neste experimento, o modelo selecionado foi o:

### KNN com 4 variáveis

**Variáveis utilizadas:**

- `alcohol`
- `volatile acidity`
- `sulphates`
- `citric acid`

**Resultados:**

> **Acurácia: 80,3% | AUC: 0,873 | F1-Score: 0,825**

A redução das variáveis não prejudicou o desempenho do KNN. Pelo contrário, apresentou uma pequena melhora nas métricas em relação ao modelo utilizando as 11 variáveis. :contentReference[oaicite:16]{index=16}

---

## 🛠️ Tecnologias Utilizadas

- Python
- Pandas
- NumPy
- Scikit-learn
  - KNeighborsClassifier
  - SVC
  - RandomForestClassifier
  - GridSearchCV
  - métricas de avaliação
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## 📁 Estrutura do Repositório

```text
wine-quality-classification/
│
├── data/
│   └── WineQT.csv
│
├── notebooks/
│   └── análise e modelagem
│
├── results/
│   └── gráficos e resultados
│
├── TechChallenge_2.docx
├── requirements.txt
└── README.md
