<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Análise Séries Temporais - Previsão de Despesas

#### Aluno: [Felipe Ribeiro Quinto](https://github.com/felipequinto)
#### Orientador: [Felipe Borges](https://github.com/FelipeBorgesC).

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

<!-- para os links a seguir, caso os arquivos estejam no mesmo repositório que este README, não há necessidade de incluir o link completo: basta incluir o nome do arquivo, com extensão, que o GitHub completa o link corretamente -->
- [Exploration_database.ipynb](Exploration_database.ipynb). <!-- caso não aplicável, remover esta linha -->
- [Treatment_database.ipynb](Treatment_database.ipynb)
- [AnalysisStep1.ipynb](AnalysisStep1.ipynb)
- [AnalysisStep2.ipynb](AnalysisStep2.ipynb)
  
---

### Resumo
Este projeto emprega dados de despesas de uma empresa sem fins lucrativos, referentes a 2018, 2019 e ao período de janeiro a março de 2020, para prever gastos futuros. O foco recai em desenvolver e avaliar modelos de machine learning em um cenário marcado pela escassez de dados (apenas 27 meses) e pela presença de valores atípicos, visando aprimorar o planejamento financeiro. A proposta contempla duas abordagens de previsão em série temporal: uma para o total de despesas mensais e outra segmentada em categorias específicas de gastos. Assim, busca-se 
<!-- trocar o texto abaixo pelo resumo do trabalho, em português -->

### Abstract <!-- Opcional! Caso não aplicável, remover esta seção -->

<!-- trocar o texto abaixo pelo resumo do trabalho, em inglês -->
This project uses expense data from a non-profit company for 2018, 2019, and the period from January to March 2020 to forecast future expenses. The focus is on developing and evaluating machine learning models in a scenario marked by scarcity of data (only 27 months) and the presence of outliers, aiming to improve financial planning. The proposal includes two time series forecasting approaches: one for total monthly expenses and another segmented into specific expense categories. Thus, the aim is to


### 1. Introdução
A base original inclui informações como lote, sequência, tipo, estabelecimento, conta contábil, fornecedor, documento, item, data de lançamento, mês e valores contábeis. Dada a necessidade de antever despesas para otimizar o fluxo financeiro, a empresa enfrentou o desafio de trabalhar com registros reduzidos e dados outliers, que impactam a confiabilidade de modelos preditivos. Para contornar essas limitações, foram testados algoritmos distintos de machine learning, tanto para analisar o montante total de despesas quanto para prever categorias de gastos específicas. O objetivo final é evidenciar as boas práticas aplicadas na modelagem de séries temporais em ambientes com restrição de dados e cenários atípicos, contribuindo para a eficiência de organizações sem fins lucrativos e para a evolução das técnicas de ciência de dados.


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
