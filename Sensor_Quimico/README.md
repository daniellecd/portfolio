## Desafio 
### Análise de dados de sensores químicos
Autora: Danielle Calazans Dondoni [\[linkedin\]](<https://www.linkedin.com/in/danielle-cd/>)


#### **1. Descrição:**

O conjunto de dados contém 9357 resultados médios de 5 sensores químicos de um dispositivo multisensor (PTXX.SX). O dispositivo estava localizado a nível da rua, dentro de uma cidade significativamente poluída. Os dados foram registrados de março de 2004 a abril de 2005 (um ano). Valores ausentes são marcados com o valor -200. A medida de outros sensores também está disponível e algumas podem ser redundantes. A variável chave a ser analisada é PT08.S1 (CO), concentração de CO na atmosfera.

##### Informação das colunas:
1.	Date (DD/MM/YYYY) 
2.	Time (HH.MM.SS) 
3.	PT08.S1 (CO) – Variável de predição
4.	Non Metanic HydroCarbons Concentration (mg/m^3)
5.	Benzene Concentration (mg/m^3) 
6.	PT08.S2 (NMHC) 
7.	NOx Concentration (ppb) 
8.	PT08.S3 (NOx) 
9.	NO2 Concentration (mg/m^3) 
10.	PT08.S4 (NO2s) 
11.	PT08.S5 (O3) 
12.	Temperature (C) 
13.	Relative Humidity (%) 
14.	AH Absolute Humidity 

#### **2. Questões para análise:**

1.	Escolha uma estratégia de tratamento de valores faltantes e *outliers*. Justifique sua escolha.
2.	Para as quartas-feiras, quais os horários de pico na cidade (de maior concentração de CO) ?
3.	Quais as variáveis mais correlacionadas com a variável de predição?
4.	Crie um modelo de regressão de PT08.S1 a partir das demais variáveis. Avalie usando as métricas que julgar pertinente para o problema.
5.	Pergunta bônus: como as estações do ano interferem nas variáveis/predição e qual sua proposta de solução? 


#### **3. Abordagem adotada:**

Inicialmente os dados foram avaliados sem nenhum tratamento prévio, apenas para conhecer o dataset e ter insights sobre as estratégias que poderiam ser adotadas. Para essa etapa foi utilizado a biblioteca pandas profillig, que gera um relatório interativo em HTML contendo uma descrição geral e informações estatíticas das observações.

Para tratamento dos dados faltantes, uma completa análise de cenários foi realizada. Foram contruídos 6 cenários, cada qual com 10 formas de preencher os dados faltantes. A escolha do método para tratamento dos dados faltantes teve como base a análise dos dados resultantes. 

Para não tornar o *notebook* principal extensivo, os códigos e resultados são apresentados em notebooks separados. Neste ponto, cabe ressaltar que não foi realizada um simplificação e otimização do código com criação de funções, por exemplo, pois estes não iriam compor o arquivo principal. Portanto, destaco que há possibilidade de melhoria nesses código, a ser realizados em momento oportuno.

Considerando as perguntas relacionadas a dias da semana e estações do ano, novas colunas foram inseridas. A definição da estação do ano teve como base o dia do ano, isto é, dias numerados de 1 a 365. Com auxílio dos recursos do *pandas datetime*  foi realizado o mapeamento dos dias da semana.

De forma complementar, considerando uma série temporal, os itens de tendência e sazonalidade foram acrescentados.

Os modelos de regressão escolhidos para este desafio foram:

* AdaBoostRegressor  
* DecisionTreeRegressor
* GradientBoostingRegressor
* KNeighborsRegressor
* LightGBM
* LinearRegression
* RandomForestRegressor
* SupportVectorRegressor
* XGBRegressor

As seguintes métricas foram calculadas: r², MAE, MSE, RMSE, MAPE e RMSLE.

Para este estudo, foi adotado o RMSE como referência para escolha do melhor modelo, sendo escolhido o XGBRegressor.

#### **4. Considerações finais:**

De forma geral o conjunto de dados é consistente, permite diversas análises e pode ser utilizado como treino para uso em aplicações reais. Para mim o mais interessante em realizar este desafio foi a adoção de um método diferente do usual para inclusão de dados faltatntes, o KNNImputer.

No entanto, para que pudesse utilizá-lo algumas 'manobras' nos dados era necessário, em virtude do tipo dos dados. A maior dificuldade foi manipular as datas sem perder informações relevantes durante o processo, isso porque dependendo da ação que eu tinha em mente necessitei recorrer a alguma estratégia inesperada para alcançar o resultado desejado.
