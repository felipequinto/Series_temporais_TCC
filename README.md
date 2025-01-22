<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Análise Séries Temporais - Previsão de Despesas

#### Aluno: [Felipe Ribeiro Quinto](https://github.com/felipequinto)
#### Orientador: [Felipe Borges](https://github.com/FelipeBorgesC).

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

<!-- para os links a seguir, caso os arquivos estejam no mesmo repositório que este README, não há necessidade de incluir o link completo: basta incluir o nome do arquivo, com extensão, que o GitHub completa o link corretamente -->
- [Link para o código](https://github.com/link_do_repositorio). <!-- caso não aplicável, remover esta linha -->
- [Link para o código](Exploration_database.ipynb).
  
---

### Resumo

<!-- trocar o texto abaixo pelo resumo do trabalho, em português -->

Introdução

Este projeto tem como base os dados de despesas de uma empresa sem fins lucrativos, abrangendo os anos de 2018, 2019 e o período de janeiro a março de 2020. A base de dados original contém informações organizadas nas colunas: lote, sequência, tipo, estabelecimento, conta contábil, fornecedor, documento, item, data de lançamento, mês, valor de lançamento contábil e valor do documento.

O principal objetivo deste trabalho foi desenvolver um modelo de machine learning capaz de prever as despesas futuras da empresa, utilizando como referência os dados históricos disponíveis. Além disso, buscou-se avaliar o desempenho desses modelos em um cenário caracterizado pela escassez de dados — limitado a 27 meses — e pela presença de valores outliers. Esses desafios foram cruciais para compreender as limitações e potencialidades dos algoritmos preditivos em situações similares.

Por meio deste estudo, espera-se contribuir para o entendimento das melhores práticas na aplicação de modelos de machine learning em contextos com restrições de dados e padrões atípicos, oferecendo insights relevantes tanto para organizações sem fins lucrativos quanto para o campo da ciência de dados.

Modelo de Previsão de Despesas

Este projeto implementa modelos de machine learning para previsão de despesas utilizando séries temporais. São exploradas duas abordagens diferentes: uma focada apenas no total mensal (Step 1) e outra considerando múltiplas categorias de despesas (Step 2).

Estrutura do Projeto

O projeto está organizado em dois principais scripts de análise:

- **AnalysisStep1.ipynb**: Implementa modelos para previsão do total mensal de despesas.
- **AnalysisStep2.ipynb**: Expande a análise para incluir previsões de categorias específicas de despesas.

### Abstract <!-- Opcional! Caso não aplicável, remover esta seção -->

<!-- trocar o texto abaixo pelo resumo do trabalho, em inglês -->

Introduction

This project is based on the expense data of a non-profit company, covering the years 2018, 2019 and the period from January to March 2020. The original database contains information organized in the following columns: batch, sequence, type, establishment, accounting account, supplier, document, item, release date, month, accounting entry value and document value.

The main objective of this work was to develop a machine learning model capable of predicting the company's future expenses, using the available historical data as a reference. In addition, we sought to evaluate the performance of these models in a scenario characterized by data scarcity — limited to 27 months — and the presence of outliers. These challenges were crucial to understanding the limitations and potential of predictive algorithms in similar situations.

Through this study, we hope to contribute to the understanding of best practices in the application of machine learning models in contexts with data restrictions and atypical patterns, offering relevant insights for both nonprofit organizations and the field of data science.

Expense Forecasting Model

This project implements machine learning models for expense forecasting using time series. Two different approaches are explored: one focused only on the monthly total (Step 1) and another considering multiple expense categories (Step 2).

Project Structure

The project is organized into two main analysis scripts:

- **AnalysisStep1.ipynb**: Implements models for forecasting the monthly total of expenses.

- **AnalysisStep2.ipynb**: Expands the analysis to include forecasts of specific expense categories.

### 1. Introdução

**Introdução**

Este projeto tem como base os dados de despesas de uma empresa sem fins lucrativos, abrangendo os anos de 2018, 2019 e o período de janeiro a março de 2020. A base de dados original contém informações organizadas nas colunas: lote, sequência, tipo, estabelecimento, conta contábil, fornecedor, documento, item, data de lançamento, mês, valor de lançamento contábil e valor do documento.

O principal objetivo deste trabalho foi desenvolver um modelo de machine learning capaz de prever as despesas futuras da empresa, utilizando como referência os dados históricos disponíveis. Além disso, buscou-se avaliar o desempenho desses modelos em um cenário caracterizado pela escassez de dados — limitado a 27 meses — e pela presença de valores outliers. Esses desafios foram cruciais para compreender as limitações e potencialidades dos algoritmos preditivos em situações similares.

Por meio deste estudo, espera-se contribuir para o entendimento das melhores práticas na aplicação de modelos de machine learning em contextos com restrições de dados e padrões atípicos, oferecendo insights relevantes tanto para organizações sem fins lucrativos quanto para o campo da ciência de dados.

### 2. Modelagem
Para o projeto de previsão de despesas, foram utilizados dois modelos principais: Random Forest Regressor e uma Rede Neural Recorrente com LSTM (Long Short-Term Memory). Os passos adotados foram os seguintes:

Pré-processamento dos Dados

Utilização de janela deslizante (window size = 5) para criar sequências de entrada.

Normalização dos dados utilizando MinMaxScaler.

Divisão dos dados em treino e teste na proporção 70/30.

Modelos Implementados.

Step 1: Previsão do Total Mensal

Random Forest Regressor

Otimização de hiperparâmetros realizada com RandomizedSearchCV.

Principais hiperparâmetros testados:

Número de árvores: [100, 500, 1000].

Profundidade máxima: [10, 50, None].

Amostras mínimas para divisão: [2, 10].

Features por nó: ['sqrt', 'log2', None].

Rede Neural (LSTM + CNN).

Arquitetura:

LSTM (2 unidades) com retorno de sequências.

Normalização em lote (BatchNormalization).

Camada convolucional 1D (1 filtro, kernel size = 4).

Camada densa para a saída.

Treinamento com callbacks:

EarlyStopping (paciência = 15).

ReduceLROnPlateau (fator = 0.1, paciência = 5).

Step 2: Previsão Multicategoria

Modelo neural com arquitetura similar ao Step 1, adaptado para entrada multidimensional:

Entrada: 5 timesteps com 4 features em cada timestep.

LSTM bidirecional seguido de camada convolucional 1D (CNN).

Camadas densas (Dense layers) para redução de dimensionalidade.

### 3. Resultados

Step 1: Previsão do Total Mensal
Random Forest:

RMSE: Demonstrou boa capacidade de generalização.
R²: Mostrou forte correlação entre valores previstos e reais.
MAPE: Indicou erro percentual aceitável para aplicação prática.

Rede Neural:

Convergência estável conforme evidenciado pela curva de loss.
Boa performance na previsão de tendências.
Capacidade de capturar padrões sazonais.

Step 2: Previsão Multicategoria
O modelo demonstrou capacidade de:

Aprender relações entre diferentes categorias de despesas.
Capturar tendências específicas por categoria.
Manter consistência nas previsões agregadas.

Visualizações
O projeto inclui visualizações importantes:

Gráficos de dispersão (valores reais vs. previstos).
Curvas de aprendizado (loss vs. epochs).
Séries temporais comparando valores reais e previstos.

Reprodutibilidade
O código inclui:

Fixação de seeds para reprodutibilidade.
Padronização de pré-processamento.
Documentação das configurações de treinamento.

Tecnologias Utilizadas

Python 3.x
TensorFlow/Keras
Scikit-learn
Pandas
NumPy
Matplotlib
Seaborn
### 4. Conclusões

O projeto demonstra a viabilidade de prever despesas tanto de forma agregada quanto por categoria, com resultados promissores em ambas as abordagens. A combinação de modelos tradicionais (Random Forest) e deep learning (LSTM+CNN) oferece insights complementares sobre o comportamento das despesas ao longo do tempo.

A abordagem em dois steps permite uma análise mais completa, onde o Step 1 fornece uma visão macro das despesas totais, enquanto o Step 2 possibilita um entendimento mais granular por categoria.

Resultados Step 1:

Random Forest

![image](https://github.com/user-attachments/assets/006e6d20-fa67-4a60-b112-6c5b58322e46)

Rede Neural

![image](https://github.com/user-attachments/assets/4343cf53-0152-4386-b370-95cec2a27cf2)

Resultado melhor modelo Step 2:

Rede Neural

![image](https://github.com/user-attachments/assets/aaedfb99-95f9-4d69-8c28-84fd5dd0c618)

---

Matrícula: 222.100.15

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
