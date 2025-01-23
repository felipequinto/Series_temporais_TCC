<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Análise Séries Temporais - Previsão de Despesas

#### Aluno: [Felipe Ribeiro Quinto](https://github.com/felipequinto)
#### Orientador: [Felipe Borges](https://github.com/FelipeBorgesC)

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

<!-- para os links a seguir, caso os arquivos estejam no mesmo repositório que este README, não há necessidade de incluir o link completo: basta incluir o nome do arquivo, com extensão, que o GitHub completa o link corretamente -->
- [Exploration_database.ipynb](Exploration_database.ipynb). <!-- caso não aplicável, remover esta linha -->
- [Treatment_database.ipynb](Treatment_database.ipynb)
- [AnalysisStep1.ipynb](AnalysisStep1.ipynb)
- [AnalysisStep2.ipynb](AnalysisStep2.ipynb)
  
---

### Resumo
Este projeto emprega dados de despesas de uma empresa sem fins lucrativos, referentes a 2018, 2019 e ao período de janeiro a março de 2020, para prever gastos futuros. O foco recai em desenvolver e avaliar modelos de machine learning em um cenário marcado pela escassez de dados (apenas 27 meses) e pela presença de valores atípicos, visando aprimorar o planejamento financeiro. A proposta contempla duas abordagens de previsão em série temporal: uma para o total de despesas mensais e outra segmentada em categorias específicas de gastos. Assim, busca-se Assim, busca-se oferecer uma ferramenta mais robusta para a tomada de decisão em contextos de recursos limitados.
<!-- trocar o texto abaixo pelo resumo do trabalho, em português -->

### Abstract <!-- Opcional! Caso não aplicável, remover esta seção -->

<!-- trocar o texto abaixo pelo resumo do trabalho, em inglês -->
This project uses expense data from a non-profit organization for 2018, 2019, and the period from January to March 2020 to forecast future expenses. The focus is on developing and evaluating machine learning models in a scenario marked by scarce data (only 27 months) and the presence of outliers, aiming to improve financial planning. The proposal includes two time-series forecasting approaches: one for total monthly expenses and another segmented into specific expense categories. Thus, the aim is to offer a more robust tool for decision-making in contexts of limited resources.


### 1. Introdução
A base original inclui informações como lote, sequência, tipo, estabelecimento, conta contábil, fornecedor, documento, item, data de lançamento, mês e valores contábeis. Dada a necessidade de antever despesas para otimizar o fluxo financeiro, a empresa enfrentou o desafio de trabalhar com registros reduzidos e dados outliers, que impactam a confiabilidade de modelos preditivos. Para contornar essas limitações, foram testados algoritmos distintos de machine learning, tanto para analisar o montante total de despesas quanto para prever categorias de gastos específicas. O objetivo final é evidenciar as boas práticas aplicadas na modelagem de séries temporais em ambientes com restrição de dados e cenários atípicos, contribuindo para a eficiência de organizações sem fins lucrativos e para a evolução das técnicas de ciência de dados.

### 2. Modelagem
Foram desenvolvidas três abordagens, todas utilizando scikit-learn e TensorFlow/Keras, com janela deslizante (window size = 5), normalização (MinMaxScaler) e divisão de dados em 70/30. A Abordagem RF (clássica) emprega o RandomForestRegressor para prever o total mensal, otimizando hiperparâmetros via RandomizedSearchCV. Já a Abordagem RN (rede recorrente com input único) utiliza uma rede LSTM + CNN 1D para série temporal univariada (apenas o valor das despesas). Por fim, a Abordagem RN 2 (rede recorrente com múltiplas entradas) adota uma arquitetura semelhante, porém com várias variáveis por timestep, permitindo estimar múltiplas categorias de despesas simultaneamente.

Tecnologias Utilizadas

- Python 3.x
- TensorFlow/Keras
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- Seaborn

### 3. Resultados

Step 1 (Previsão do Total Mensal) avaliou Random Forest (RMSE, R², MAPE) com boa capacidade de generalização e Rede Neural, que demonstrou convergência estável e boa previsão de tendências sazonais. Step 2 (Previsão Multicategoria) evidenciou aprendizagem de relações entre diversas categorias, captura de tendências específicas e previsões agregadas consistentes. As visualizações incluem gráficos de dispersão (valores reais vs. previstos), curvas de aprendizado (loss vs. epochs) e comparações de séries temporais. Já a reprodutibilidade foi garantida por meio de seeds fixas, padronização de pré-processamento e documentação das configurações de treinamento.

Resultados Step 1:

Random Forest

![image](https://github.com/user-attachments/assets/66a60a2f-9f94-4641-8066-79d2cbca2e87)

Rede Neural

![image](https://github.com/user-attachments/assets/c525b0f7-eef9-4eae-ad43-5a26c43c57cf)

Resultado melhor modelo Step 2:

Rede Neural

![image](https://github.com/user-attachments/assets/eac69ce0-d361-41f0-babd-e29173c25153)

### 4. Conclusões

O projeto demonstra a viabilidade de prever despesas tanto de forma agregada quanto por categoria, com resultados promissores em ambas as abordagens. A combinação de modelos tradicionais (Random Forest) e deep learning (LSTM+CNN) oferece insights complementares sobre o comportamento das despesas ao longo do tempo.
A abordagem em dois steps permite uma análise mais completa, onde o Step 1 fornece uma visão macro das despesas totais, enquanto o Step 2 possibilita um entendimento mais granular por categoria.

---

Matrícula: 222.100.15

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
