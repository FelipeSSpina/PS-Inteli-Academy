# Previsão de Churn - TelecomPlus

## Descrição do Projeto
O objetivo deste desafio é desenvolver um modelo de Machine Learning supervisionado capaz de prever a rotatividade (churn) de clientes da TelecomPlus. Ao antecipar quais clientes possuem maior probabilidade de cancelar seus serviços nos próximos 3 meses, a empresa pode adotar medidas preventivas e reduzir perdas financeiras.

## Estrutura do Repositório

- **dados_clientes.csv**: Conjunto de dados de treino com informações históricas e variável alvo `churn`.
- **desafio.csv**: Conjunto de dados de teste sem rótulo de churn.
- **churn_prediction.ipynb**: Notebook Jupyter contendo todo o código e documentação do processo.
- **resultado_nome_sobrenome.csv**: Arquivo de submissão com as previsões de churn para o conjunto de teste.
- **README.md**: Documento de descrição deste projeto.

## Tecnologias e Bibliotecas Utilizadas

Foram utilizadas as seguintes ferramentas e bibliotecas em Python:

- **pandas** e **numpy** para manipulação de dados.
- **matplotlib** e **seaborn** para visualização exploratória.
- **scikit-learn** para pré-processamento, pipelines e avaliação de modelos:
  - `StratifiedKFold`, `train_test_split`, `OneHotEncoder`, `StandardScaler`, `SimpleImputer`, `Pipeline`, `ColumnTransformer`.
  - Algoritmos de classificação: `LogisticRegression`, `RandomForestClassifier`.
- **xgboost** para implementação do modelo **XGBClassifier**.

## Descrição das Etapas

1. **Exploração de Dados (EDA)**
   - Visualização da distribuição de churn e análise de correlações entre variáveis numéricas.
   - Identificação de padrões por tipo de contrato e outras categorias.

2. **Pré-processamento e Engenharia de Features**
   - Tratamento de valores ausentes (mediana para numéricos e moda para categóricos).
   - Padronização de features numéricas.
   - Codificação one-hot para variáveis categóricas.
   - Criação da variável derivada `qtde_produtos` a partir de `produtos_assinados`.

3. **Treinamento e Validação de Modelos**
   - Definição de três pipelines paralelos para **Regressão Logística**, **Random Forest** e **XGBoost**.
   - Validação cruzada estratificada (5 folds) avaliando métricas de acurácia, precisão, recall, F1 e ROC-AUC.
   - Comparação dos resultados obtidos em cada modelo.

4. **Seleção do Modelo Final**
   - Escolha do melhor modelo com base na acurácia média na validação cruzada.
   - Treinamento final com divisão 75% treino / 25% validação via `train_test_split`.
   - Cálculo de todas as métricas no conjunto de validação e plot das curvas ROC e Precision-Recall.

5. **Geração de Submissão**
   - Aplicação do pipeline final sobre `desafio.csv` para gerar as previsões.
   - Exportação do arquivo `resultado_nome_sobrenome.csv` contendo as colunas `Id` e `churn`.

## Resultados Obtidos

O modelo selecionado alcançou **X% de acurácia**, **Y% de precisão**, **Z% de recall** e **W% de ROC-AUC** no conjunto de validação. As curvas ROC e Precision-Recall demonstram a performance discriminativa do modelo em diferentes limiares.

## Como Executar este Projeto

1. Clone este repositório:

   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   ```

2. Crie um ambiente virtual e instale as dependências:

   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\\Scripts\\activate   # Windows
   pip install -r requirements.txt
   ```

3. Abra o notebook e execute as células na sequência:

   ```bash
   jupyter notebook churn_prediction.ipynb
   ```

4. Após o treinamento, o arquivo de submissão será gerado automaticamente como `resultado_nome_sobrenome.csv`.

## Conclusões e Próximos Passos

Este projeto demonstrou um pipeline completo de Machine Learning aplicado à previsão de churn, desde a exploração inicial até a geração de resultados para submissão. Como próximos passos, recomenda-se:

- Realizar ajuste de hiperparâmetros (Grid Search ou Bayesian Optimization).
- Testar outras técnicas de engenharia de features, como interação entre variáveis.
- Avaliar amostragens balanceadas (SMOTE ou undersampling) para lidar com possíveis desbalanceamentos.
- Implementar monitoramento de performance em produção e atualização periódica do modelo.

---

*Desenvolvido por [Seu Nome] em abril de 2025.*

