# ann-lego-sets

# Previsão de Preços de LEGO Sets com Redes Neurais Artificiais (ANN)

## 🚀 Título do Projeto
Inteligência Artificial - ML com Scikit-learn: Previsão de Preços de LEGO Sets usando Redes Neurais Artificiais

## 🎯 Objetivo
O principal objetivo deste projeto é explorar e aplicar modelos de Redes Neurais Artificiais (ANN) utilizando a biblioteca Scikit-Learn em Python para o dataset de LEGO Sets. A tarefa central é preencher os valores de preço ausentes (`US_retailPrice`) nos conjuntos de LEGO através da modelagem e previsão, garantindo que todos os itens tenham um preço estimado.

## 📊 Dados
O dataset utilizado, "LEGO Sets", contém informações sobre conjuntos de LEGO lançados entre 1970 e 2022. Inclui detalhes como tema do set, número de peças, minifiguras, faixa etária recomendada, preço de varejo nos EUA e URLs de imagens.

Fonte: [Maven Analytics - LEGO Sets](https://mavenanalytics.io/data-playground/lego-sets)

## 📝 Estrutura do Notebook
O notebook está organizado nas seguintes seções:

1.  **Download e Descompactação dos Dados**: Baixa e extrai o arquivo `LEGO+Sets.zip`.
2.  **Importação de Bibliotecas**: Carrega as bibliotecas necessárias para Análise Exploratória de Dados (EDA) e Machine Learning.
3.  **Carregamento e Visualização Inicial**: Carrega `lego_sets.csv` em um DataFrame Pandas e exibe as primeiras linhas.
4.  **Análise de Dados Faltantes**: Utiliza `lego_df.isnull().sum()` e a biblioteca `missingno` (com `msno.matrix`, `msno.bar`, `msno.heatmap`) para identificar e visualizar a distribuição dos valores ausentes.
5.  **Preparação de Dados para ANN**: Define as features numéricas (`pieces`, `minifigs`, `agerange_min`, `year`) e categóricas (`themeGroup`, `category`) e o target (`US_retailPrice`).
    -   Cria um DataFrame de treino com apenas os preços válidos e aplica uma transformação logarítmica ao target.
6.  **Pipeline de Pré-processamento**: Configura pipelines para:
    -   **Features Numéricas**: Imputação de medianas e escalonamento (`StandardScaler`).
    -   **Features Categóricas**: Imputação da moda e codificação one-hot (`OneHotEncoder`).
7.  **Treinamento da ANN**: Implementa um `MLPRegressor` com camadas ocultas (64, 32) e o treina dentro de um pipeline que inclui o pré-processamento.
    -   Avalia o modelo em um conjunto de validação, reportando MAE e R² Score.
8.  **Preenchimento de Preços Faltantes**: Utiliza o modelo treinado para prever os preços dos sets sem `US_retailPrice` e os atribui a uma nova coluna `price`.
9.  **Validação Final**: Verifica se a coluna `price` possui valores nulos após a imputação e exibe uma amostra dos resultados.
10. **Colunas Importantes para Prever o Preço**: Lista e descreve as features consideradas mais relevantes para a previsão de preços dos LEGO sets.

## 🛠️ Instruções de Uso
1.  **Abrir no Google Colab**: Clique em "Open in Colab" (ou clone o repositório e abra o `.ipynb` localmente).
2.  **Executar Células**: Execute as células do notebook sequencialmente. Certifique-se de que todas as dependências estejam instaladas (o Colab geralmente lida com isso automaticamente).
3.  **Observar Saídas**: Acompanhe as saídas para ver o download dos dados, as visualizações de dados faltantes, as métricas de avaliação do modelo e a imputação final dos preços.

## 📈 Resultados
Após o treinamento e avaliação, o modelo ANN alcançou as seguintes métricas no conjunto de validação:
-   **MAE (Erro Médio Absoluto)**: $9.46
-   **R² Score**: 0.8665

Isso indica que o modelo é capaz de prever os preços com uma precisão razoável, com um erro médio de aproximadamente $9.46 e explicando cerca de 86.65% da variância nos preços.

## ✅ Colunas Importantes para Prever o Preço
As seguintes colunas foram identificadas como cruciais para a previsão do preço dos conjuntos de LEGO:

-   **pieces**: O número de peças é um fator direto no custo de produção e, consequentemente, no preço final.
-   **minifigs**: A quantidade de minifiguras, muitas vezes colecionáveis, pode aumentar significativamente o valor percebido de um set.
-   **agerange_min**: A idade mínima recomendada pode indicar a complexidade e o público-alvo do set, com Legos para adultos frequentemente sendo mais caros.
-   **themeGroup**: A afiliação a um `themeGroup` (e.g., colaborações com franquias famosas) pode encarecer o produto devido a licenciamento e popularidade.
-   **category**: Distingue conjuntos normais de itens especiais ou exclusivos, que geralmente possuem um preço premium.
-   **year**: O ano de lançamento pode refletir a conjuntura econômica, a inflação e a raridade do set, influenciando o preço de varejo e seu valor ao longo do tempo.
