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

#### Este projeto foi dividido em 10 passos: 

1 - Análise de descrição de dados: Padronização dos nomes das colunas no dataset, verificação e substituição de dados faltantes, adequação dos tipos de dados. Estudo estatístico dos dados.

2 - Feature Engineering: Criação de Hipóteses para o negócio, criação de novas variáveis de tempo.

3 - Filtragem de Variáveis: Seleção de variáveis numéricas e categóricas.

4 - Análise Exploratória dos dados: Respostas das Hipóteses criadas na Feature Engineering e estudo do comportamento dos dados.

5 - Rescala dos dados para melhor adequação dos dados ao modelo de Machine Learning: Foi utilizado o Robust Scaler e o MinMaxScaler para rescalar os dados numéricos que apresentavam altos valores de intervalo e outliers. Para as variáveis categóricas foram utilizados o LabelEncoder para dados com relação de ordem, One Hot Encoding para diferenciar dias com feriado e não feriado utilizando 0 e 1. 

6 - Seleção de Features: Foi utilizado o Boruta para selecionar as features com maior relevância para o modelo de Machine Learning.

7 - Aplicação de Algoritmos de Machine Learning: Foram testados 5 modelos de Machine Learning: Linear Regression, Linear Regression - Lasso, Average Model, XGBoost Regressor e o Random Forest Regressor juntamente com cross validation K-fold para verificar se os dados sofrem overfitting. Foi escolhido o XGBosty por apresentar um boa performance,  quase 90%.

8 - Hyperparameter Fine Tuning: Foi implementado o Fine Tuning para encontrar um melhor parâmetro que maximize o resultado do modelo.

9 - Tradução e Interpretação do Erro: Através dos índices MAE foram previstos através do modelo de Machine Learning os melhores e piores cenários de vendas para cada loja da rede nas próximas 6 semanas.

10 - Deploy do Modelo: Implantação com o objetivo de disponibilizar a previsão do modelo para qualquer usuário. O usuário pode ser: uma pessoa, smartphone, aplicativo, site, planilhas do google, excel ou qualquer software conectado na internet que possa executar uma solicitação de API. A solicitação de previsão pode ser feita por qualquer um dos usuários. A interface entre o usuário e o modelo é feita por meio da API. Posteriormente, tanto a API quanto o modelo serão carregados em um servidor nuvem (heroku) para que possam trabalhar com as solicitações enviadas pela internet. Neste caso foi criado um bot no telegrama para o projeto, de forma que a solicitação de previsão de vendas seja feita de forma rápida e fácil. A previsão pode ser acessada a qualquer momento e em qualquer lugar que tenha acesso a internet somente digitando o número da loja como entrada.

