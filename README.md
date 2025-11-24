# Benchmark de Modelos Preditivos – df_rides

Projeto autoral de Machine Learning focado em **previsão de valores de corridas** a partir do dataset `df_rides`.  
Aqui eu comparo diferentes modelos, documento o processo de análise e deixo o código pronto para ser estudado e reaproveitado.

---

## Objetivo

Responder à pergunta:

> **“Quão bem conseguimos prever o valor de uma corrida usando apenas dados históricos (tempo, distância, localização etc.)?”**

Com isso, o projeto poderia apoiar decisões como:

- Definição de políticas de preço mais consistentes;
- Identificação de corridas fora do padrão (possíveis fraudes ou erros);
- Entendimento de quais variáveis mais influenciam o valor final.

---

## Dataset

- **Nome:** `df_rides`
- **Origem:** dataset utilizado em atividades educacionais (EBAC / estudos pessoais).
- **Unidade de análise:** cada linha representa uma corrida.
- **Principais tipos de variáveis:**
  - Dados de tempo (data/hora da corrida);
  - Medidas de distância/duração;
  - Informações categóricas (ex.: tipo de corrida, região/bairro, categoria do serviço);
  - Variável alvo: **preço/valor da corrida**.

> Detalhes completos das colunas podem ser vistos diretamente no notebook.

---

## Metodologia

O fluxo segue uma abordagem inspirada no **CRISP-DM**:

1. **Entendimento do Problema**
   - Definição da pergunta de negócio e das métricas principais (MAE, RMSE, R²).
2. **Entendimento dos Dados**
   - Análise exploratória (distribuições, correlações, outliers, dados faltantes).
3. **Preparação dos Dados**
   - Tratamento de nulos;
   - Criação de variáveis derivadas (tempo, distância, etc.);
   - Codificação de variáveis categóricas;
   - Padronização/normalização de variáveis numéricas quando necessário.
4. **Modelagem**
   - Treinamento e comparação de diferentes modelos preditivos.
5. **Avaliação**
   - Avaliação com **validação cruzada (k-fold)** e conjunto de teste (holdout);
   - Comparação dos modelos com as métricas definidas.
6. **Conclusões e Próximos Passos**
   - Interpretação dos resultados e limitações;
   - Sugestões de melhorias futuras.

---

## Modelos Avaliados

Modelos de regressão testados (podem ser adaptados à sua realidade do notebook):

- **Baseline:** Dummy Regressor (referência mínima de desempenho);
- **Modelos lineares:** Regressão Linear / Regressão Ridge/Lasso;
- **Modelos baseados em árvores:** Decision Tree Regressor;
- **Ensembles:** Random Forest, Gradient Boosting / XGBoost (se usado).

Para cada modelo são comparados:

- **MAE (Mean Absolute Error)**  
- **RMSE (Root Mean Squared Error)**  
- **R² (Coeficiente de Determinação)**  

---

## Principais Insights

- Horários e/ou dias específicos apresentam valores médios de corrida significativamente diferentes;
- Corridas mais longas não aumentam o preço de forma perfeitamente linear (efeito de tarifa mínima ou descontos progressivos);
- Algumas variáveis categóricas (ex.: região ou tipo de serviço) têm forte impacto no valor, sugerindo segmentação de pricing;
- O melhor modelo obteve **MAE ≈ X** e **R² ≈ Y** no conjunto de teste, superando o baseline com folga.

---

## Estrutura do Projeto

```text
.
├── data/              # (Opcional) Amostras ou referências de dados
├── notebooks/
│   └── benchmark_df_rides.ipynb   # Notebook principal do projeto
├── src/               # (Opcional) Scripts reutilizáveis
├── README.md
└── requirements.txt   # (Opcional) Lista de dependências

 Tecnologias Utilizadas

Linguagem: Python

Ambiente: Google Colab

Principais bibliotecas:

pandas, numpy – manipulação e análise de dados

matplotlib, seaborn – visualização de dados

scikit-learn – pré-processamento, modelagem e métricas

Como Executar:
Google Colab

Acesse o notebook na pasta notebooks/.

Clique em “Open in Colab” (se você adicionar o badge/link).

Execute as células em ordem.

Caso use dados locais, ajuste o caminho dos arquivos na seção de carregamento do dataset.


