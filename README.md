## Data Science em Produção
![This is an image](https://advancedinstitute.ai/wp-content/uploads/2019/04/regressao-1170x500.png)

### Motivação do Projeto:

A Rossmann opera mais de 3000 drogarias em 7 países europeus. O CFO da rede de drogarias solicitou aos gerentes de loja a previsão de suas vendas diárias com até seis semanas de antecedência, com o objetivo de alocar recursos para a reforma das lojas. As vendas são influenciadas por muitos fatores, incluindo promoções, competição, feriados escolares e estaduais, sazonalidade e localidade.

###  Causa Raiz do Problema:

-  O CFO precisa saber o quanto cada loja irá trazer de lucro para alocar em investimentos para reformas das lojas.

###  Stakeholder

- CFO

### Formato de Solução:

- Vendas Diárias para as próximas 6 semanas;
- Problema de Predição;
- Time Series, Regressão;
- Predições acessadas via celular 

### Este projeto foi dividido em 10 passos: 

### 1.0 - Análise de descrição de dados: 

Foi realizado a Padronização dos nomes das colunas no dataset alterando-as para o formato snakecase, utilizando a biblioteca inflection;
Para solucionar os dados faltantes foi utilizado como estratégia substituir os Na’s por dados do próprio negócio utilizando condicionais com o método isnan que vem da classe ismath que percorrer todas as linhas da coluna. 

### 2.0. Feature Engineering: 

Foi criado hipóteses para o negócio, criação de novas variáveis de tempo.

### 3.0. Filtragem de Variáveis: 

Nesse passo do projeto foram criadas variáveis para estudo durante a análise exploratória de dados.
Mapa Mental de Hipóteses: 
Foi criado um mapa mental de Hipóteses para entender qual fenômeno está sendo modelado, com o intuito de ensinar os modelos de Machine Learning a entender quais agentes atuam sobre  o fenômeno estudados. Exemplo: Clientes, quantidade de lojas, variação dos produtos e etc.
Objetivo das hipóteses:
Conseguir derivar uma lista de hipóteses para validar com os dados, assim gerando insights para o negócio.

### 4.0. Análise Exploratória dos dados: 

Hipóteses constatadas na Feature Engineering e estudo do comportamento dos dados:
competition_distance: Possui uma concentração maior em competidores com uma distância menor, os competidores estão muito próximos. 
competition_open_since_month: Mostra o comportamento de acordo com a abertura em meses do competidor, nesta análise verifica-se que nos meses 4 e 7 há um comportamento maior de vendas.
day_of_week: Não há variação de vendas durante os dias da semana 
is_promo: O volume de vendas é maior quando a loja não está em promoção.
promo2_since_year: As lojas que entraram na promoção em 2013 e 2015 possuem um maior volume de vendas.
state_holiday: Os feriados públicos possuem um número maior de vendas. Os feriados christmas e easter_holiday possuem um volume de venda menor, porém tem um pico alto de vendas.
store_type: A loja do tipo a possuí um volume bem maior comparado as outras lojas, quanto ao volume de vendas 
assortment: As lojas com o assortment basic e extended são as que vendem mais, o extra tem um volume de vendas menor, porém com uma distribuição maior, existem lojas que vendem mais com o assortment extra e outras lojas que vendem menos.  

### 5.0. Rescala dos dados:

#### Encoding

state_holiday: Por se tratar de uma variável com ideia de estado, há mudança de comportamento foi utilizado o One Hot Enconding
store_type: Não tem uma ordem, foi utilizado o Label Encoding
assortment: Por possuir uma ordem de grandeza foi utilizado o Ordinal Encoding.
Transformação da variável resposta: Foi utilizado a transformação logarítmica np.log1p para a variável sales.
###Nature Transformation
day_of_week, month, week_of_year, day: Por tratar-se de uma natureza cíclica foi utilizado o seno e cosseno

#### 6.0. Seleção de Features: 

Para a seleção das variáveis mais relevantes para o modelo foi utilizado o algoritmo Boruta. Por se tratar de um problema que envolve tempo, os dados de treino e teste não podem ser escolhidos aleatoriamente, então, para os dados de treino foi selecionado o selecionado as últimas 6 semanas de vendas.

#### 7.0. Aplicação de Algoritmos de Machine Learning: Foram testados 5 modelos de Machine Learning: Linear Regression, Linear Regression - Lasso, Average Model, XGBoost Regressor e o Random Forest Regressor.

### Contatações:

Average Model: Performou melhor que os modelos lineares;
Linear Regression e Linear Regression Regularized: A previsão de vendas das lojas Rossman possuí dados complexos, modelos lineares não funcionam muito bem para esse tipo de fenômeno.
Random Forest Regressor e XGBoost Regressor: A previsão de vendas das lojas Rossman exige modelos mais complexos, Random Forest Regressor e XGBoost Regressor funcionaram bem 
Em todos os modelos testados, exceto o Average Model, foram aplicados após o resultado o cross validation Time Series para testar a variabilidade que o fenômeno possa ter.

### 8.0. Hyperparameter Fine Tuning:

Foi implementado o Fine Tuning para encontrar um melhor parâmetro que maximize o resultado do modelo.

### 9.0. Business Performance 
 
1 – Soma das predições
Para avaliar a performance de negócio é somado todas as predições por loja 
2 – MAE e MAPE

### 10.0. Deploy do Modelo: 

Implantação com o objetivo de disponibilizar a previsão do modelo para qualquer usuário. O usuário pode ser: uma pessoa, smartphone, aplicativo, site, planilhas do google, excel ou qualquer software conectado na internet que possa executar uma solicitação de API. A solicitação de previsão pode ser feita por qualquer um dos usuários. A interface entre o usuário e o modelo é feita por meio da API. Posteriormente, tanto a API quanto o modelo serão carregados em um servidor nuvem (heroku) para que possam trabalhar com as solicitações enviadas pela internet. Neste caso foi criado um bot no telegrama para o projeto, de forma que a solicitação de previsão de vendas seja feita de forma rápida e fácil. A previsão pode ser acessada a qualquer momento e em qualquer lugar que tenha acesso a internet somente digitando o número da loja como entrada.

