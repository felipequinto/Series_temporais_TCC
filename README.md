<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Análise Séries Temporais

#### Aluno: [Felipe Ribeiro Quinto](https://github.com/felipequinto)
#### Orientador: [Felipe Borges](https://github.com/FelipeBorgesC).

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

<!-- para os links a seguir, caso os arquivos estejam no mesmo repositório que este README, não há necessidade de incluir o link completo: basta incluir o nome do arquivo, com extensão, que o GitHub completa o link corretamente -->
- [Link para o código](https://github.com/link_do_repositorio). <!-- caso não aplicável, remover esta linha -->

---

### Resumo

<!-- trocar o texto abaixo pelo resumo do trabalho, em português -->

Este projeto teve como objetivo principal analisar e desenvolver um modelo de machine learning para prever despesas de uma empresa. O conjunto de dados utilizado contém 27 meses de despesas, apresentando um desafio adicional devido ao seu pequeno volume e à presença de outliers.

O estudo explorou as etapas fundamentais de preparação dos dados, seleção de features e avaliação de modelos, com foco em entender como técnicas de machine learning se comportam em cenários com limitações de dados históricos e irregularidades.

Os resultados do modelo foram analisados considerando métricas preditivas e a capacidade de lidar com padrões atípicos nos dados, contribuindo para o entendimento das possibilidades e limitações da aplicação de algoritmos preditivos em contextos semelhantes.

Este repositório contém o código desenvolvido, os insights obtidos e as visualizações utilizadas para interpretação dos resultados..

### Abstract <!-- Opcional! Caso não aplicável, remover esta seção -->

<!-- trocar o texto abaixo pelo resumo do trabalho, em inglês -->

The main objective of this project was to analyze and develop a machine learning model to predict a company's expenses. The dataset used contains 27 months of expenses, presenting an additional challenge due to its small volume and the presence of outliers.

The study explored the fundamental steps of data preparation, feature selection, and model evaluation, with a focus on understanding how machine learning techniques behave in scenarios with historical data limitations and irregularities.

The model's results were analyzed considering predictive metrics and the ability to deal with atypical patterns in the data, contributing to the understanding of the possibilities and limitations of applying predictive algorithms in similar contexts.
This repository contains the code developed, the insights obtained, and the visualizations used to interpret the results.

### 1. Introdução

**Introdução**

Este projeto tem como base os dados de despesas de uma empresa sem fins lucrativos, abrangendo os anos de 2018, 2019 e o período de janeiro a março de 2020. A base de dados original contém informações organizadas nas colunas: lote, sequência, tipo, estabelecimento, conta contábil, fornecedor, documento, item, data de lançamento, mês, valor de lançamento contábil e valor do documento.

O principal objetivo deste trabalho foi desenvolver um modelo de machine learning capaz de prever as despesas futuras da empresa, utilizando como referência os dados históricos disponíveis. Além disso, buscou-se avaliar o desempenho desses modelos em um cenário caracterizado pela escassez de dados — limitado a 27 meses — e pela presença de valores outliers. Esses desafios foram cruciais para compreender as limitações e potencialidades dos algoritmos preditivos em situações similares.

Por meio deste estudo, espera-se contribuir para o entendimento das melhores práticas na aplicação de modelos de machine learning em contextos com restrições de dados e padrões atípicos, oferecendo insights relevantes tanto para organizações sem fins lucrativos quanto para o campo da ciência de dados.

### 2. Modelagem
Para o projeto de previsão de despesas, foram utilizados dois modelos principais: Random Forest Regressor e uma Rede Neural Recorrente com LSTM (Long Short-Term Memory). Os passos adotados foram:

1. Tratamento e Organização dos Dados
Fonte dos Dados: Um arquivo Excel com colunas relevantes como Ano, Mês, Total Mês, e outras categorias.
Normalização: Os dados foram escalados utilizando MinMaxScaler para normalizar os valores numéricos em um intervalo [0, 1], melhorando o desempenho dos algoritmos.
Criação de Janelas Temporais: Foi aplicada uma técnica de janela deslizante com tamanho 5 para criar entradas sequenciais para os modelos.
Divisão do Conjunto de Dados: Os dados foram divididos em 70% para treino e 30% para teste, com um random_state fixo para reprodutibilidade.
2. Modelos Utilizados
2.1 Random Forest Regressor
Utilizado como primeiro modelo para avaliar a capacidade preditiva com hiperparâmetros ajustados usando RandomizedSearchCV.
Hiperparâmetros testados:
Número de estimadores (n_estimators): 100, 500, 1000.
Profundidade máxima (max_depth): 10, 50, ou sem limite.
Número mínimo de amostras para divisão e folhas (min_samples_split, min_samples_leaf).
Máximo de variáveis por nó (max_features): sqrt, log2, ou todas.
Métrica de Avaliação: mean_squared_error (erro quadrático médio) foi utilizada durante a validação cruzada (5 folds).
O melhor modelo foi ajustado e avaliado no conjunto de teste.
2.2 Rede Neural com LSTM
Arquitetura composta por:
Uma camada LSTM com 2 unidades.
Uma camada de convolução (Conv1D) para captar padrões locais nas sequências.
Uma camada Flatten para achatar os dados após a convolução.
Camadas densas para realizar a predição final.
Hiperparâmetros do Modelo:
Otimizador: adam.
Função de perda: mean_squared_error.
Épocas: 200.
Tamanho do lote (batch_size): 2.
Regularização e Callbacks:
Dropout para evitar overfitting.
EarlyStopping com paciência de 15 épocas para interromper o treinamento caso não haja melhoria.
ReduceLROnPlateau para reduzir a taxa de aprendizado dinamicamente.
Visualização do Modelo: Foi utilizado o método summary() para detalhar a arquitetura e as dimensões de entrada e saída.

### 3. Resultados

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula.

Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam.

### 4. Conclusões

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula.

Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam.

---

Matrícula: 222.100.15

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
