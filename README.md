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
Cada despesa possui um respectivo número contábil, que foi utilizado para criar colunas no DataFrame, onde cada coluna representa uma categoria de despesa específica. Além disso, foram adicionadas colunas para representar os anos e meses, permitindo uma organização temporal dos dados e facilitando a análise e a modelagem preditiva. Foram realizadas análises detalhadas nessas colunas para identificar relações entre as variáveis e estudar a base de dados com o objetivo de compreender melhor os padrões presentes, bem como avaliar possíveis outliers e tendências ao longo do tempo. Essas análises foram fundamentais para orientar as etapas subsequentes de preparação dos dados e construção do modelo preditivo.
<br><br>
![image](https://github.com/user-attachments/assets/867dd620-5461-44f5-bbde-90a9714b83c9)
<br><br>O mapa de calor apresentado exibe a correlação entre a coluna "Total Mês" e as demais colunas que representam diferentes categorias de despesas, identificadas pelos números contábeis. A análise do gráfico sugere:
- Altas Correlações (Próximas de 1): As colunas que aparecem em vermelho na parte superior têm uma forte correlação positiva com a coluna "Total Mês". Isso indica que as variações nos valores dessas despesas    estão diretamente relacionadas ao aumento ou diminuição do total mensal.
- Baixas Correlações (Próximas de 0): As colunas que aparecem em tons de azul claro possuem uma baixa correlação com "Total Mês". Isso sugere que essas despesas têm pouca ou nenhuma influência direta no total mensal.
- Correlação Negativa: Não há tons de azul escuro que indiquem correlações negativas significativas (próximas de -1), o que indica que nenhuma das despesas está inversamente relacionada ao "Total Mês".
- Distribuição das Correlações: Observa-se que a maioria das colunas tem correlação baixa ou moderada, enquanto poucas possuem correlação muito alta. Isso sugere que apenas um subconjunto de despesas contribui significativamente para o total mensal.
<br><br>
![image](https://github.com/user-attachments/assets/9fbd4c4e-c5d9-424e-8a84-ae7da17ac0be)
<br><br>
Usando um modelo de RandomForest para identificar a importância das variáveis.
O gráfico apresenta a evolução ao longo do tempo de cinco colunas selecionadas, representando diferentes categorias de despesas contábeis. A análise do gráfico sugere os seguintes pontos:
- Tendências Gerais:
Algumas despesas, como as representadas pelas colunas 311110107 e 362110101, mostram um crescimento acentuado nos últimos meses, indicando picos de gastos significativos.
Outras categorias, como 332210105, apresentam flutuações mais sutis ao longo do período, mas ainda mostram variações pontuais.

- Picos e Anomalias:
Há aumentos repentinos em algumas colunas, como no caso de 362110101 e 311110107, especialmente nos meses finais. Esses picos podem ser indicativos de eventos extraordinários ou despesas atípicas que impactaram o total.

- Estabilidade em Algumas Categorias:
Despesas como as representadas por 313110114 permanecem relativamente constantes ao longo do tempo, sugerindo que essas categorias têm um comportamento mais previsível.
- Comparação Entre Categorias:
Algumas categorias possuem valores muito mais altos em comparação a outras, indicando que essas despesas têm maior peso no total geral.
<br><br>
![image](https://github.com/user-attachments/assets/9fa16376-6a12-4634-8e45-e99b45cf5fdb)
<br><br>
O gráfico gráfico de barras horizontais apresenta a importância das variáveis (features) utilizadas no treinamento de um modelo de regressão com Random Forest para prever o "Total Mês". A análise dos resultados mostra os seguintes pontos:

- Principais Features:
 As variáveis 312110103 e 331110106 possuem os maiores valores de importância, indicando que contribuem significativamente para a previsão do "Total Mês".
 Esses dados sugerem que essas despesas têm uma forte relação com o total mensal e desempenham um papel crucial no modelo.
 
- Importância Moderada:
 Variáveis como 331110102 e 3322101AB também apresentam uma relevância considerável, embora sejam menos importantes que as principais features.
 Esse grupo de variáveis pode indicar padrões secundários que impactam a previsão do total mensal.
 
- Menores Importâncias:
 Features como 332110132 e 332210177 possuem valores mais baixos de importância, sugerindo que têm pouca influência na variável alvo.
 Essas variáveis podem ser consideradas para redução de dimensionalidade, caso necessário.
- Diversidade de Impactos:
 A diferença nas importâncias mostra que apenas algumas variáveis têm um impacto expressivo na previsão, enquanto outras contribuem de forma marginal.
<br><br>
![image](https://github.com/user-attachments/assets/c4843516-b7ba-44cd-b6c4-68d305253228)
<br><br>
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
