# 🧠 Machine Learning: Previsão de Intenção de Compra de Clientes

Projeto desenvolvido como parte do Módulo PCA - Redução de Dimensionalidade do curso de Cientista de Dados da EBAC, com foco na construção de modelos de Machine Learning para prever a intenção de compra online de clientes de uma empresa de varejo.

A partir de dados de perfil, comportamento de compra e interação com os canais digitais, foram realizadas etapas de tratamento, análise exploratória, pré-processamento, modelagem e avaliação comparativa entre Regressão Logística e Random Forest Classifier.

## 🎯 Objetivo do Projeto

O objetivo é desenvolver um modelo preditivo capaz de identificar clientes com maior propensão a realizar compras pela web, utilizando informações históricas de comportamento e características dos consumidores.

A análise busca responder:

    Quais características e comportamentos estão associados à intenção de compra online dos clientes?

Os resultados podem apoiar estratégias de:

- segmentação de clientes;
- campanhas de marketing;
- personalização de ofertas;
- direcionamento de ações comerciais;
- aumento da conversão no canal digital.

## 🗂️ Base de Dados

A base contém informações relacionadas a características demográficas, financeiras e comportamentais dos clientes, incluindo:

- Ano de nascimento;
- Escolaridade;
- Estado civil;
- Renda;
- Quantidade de filhos em casa;
- Recência da última compra;
- Gastos por categoria de produto;
- Compras realizadas em loja física;
- Compras realizadas pela web;
- Visitas ao site;
- Reclamações;
- Entre outras variáveis relacionadas ao comportamento de consumo.

A variável `Num_Compras_Web` foi definida como variável dependente (y) para o desenvolvimento dos modelos de classificação.

## 🧩 ETAPA 1 — Preparação dos Dados

### A) Exploração e limpeza

Inicialmente foram avaliados:

- tipos de dados;
- valores nulos;
- estatísticas descritivas;
- valores discrepantes;
- possíveis outliers;
- consistência das variáveis.

Durante a análise foram identificadas inconsistências principalmente nas variáveis `Income` e `Year_Birth`.

Na variável `Income`, foi identificado um valor extremo de 666.666, considerado uma anomalia de preenchimento. O registro foi substituído por `NaN` e posteriormente preenchido utilizando a mediana da variável.

Na variável `Year_Birth`, foram identificados anos incompatíveis com o perfil esperado da base. Esses registros foram tratados e substituídos pela mediana.

Após o tratamento, foram realizadas novas verificações para confirmar a consistência dos dados.

### 📊 ETAPA 2 — Análise exploratória

A EDA buscou compreender o comportamento dos clientes e identificar padrões relacionados às compras realizadas nos canais físico e digital.

Foram analisados:

**👥 Perfil dos clientes**

Foram avaliadas relações entre:

- escolaridade;
- estado civil;
- quantidade de filhos;
- renda;
- compras pela web;
- compras em lojas físicas.

Os resultados indicaram maior concentração de compras entre clientes com maior nível de escolaridade, especialmente nos grupos de graduação, mestrado e doutorado.

**🛒 Comportamento de compra**

Também foram analisadas:

- visitas ao site;
- compras pela web;
- compras em lojas físicas;
- reclamações;
- gastos por categoria de produto.

A análise permitiu observar diferenças entre os canais e identificar padrões de preferência dos consumidores.

**🌐 Integração entre canais**

Foi criada uma variável de perfil de canal, classificando os clientes conforme sua preferência entre compras online e físicas.

Essa abordagem permitiu analisar de maneira mais estruturada o comportamento multicanal dos consumidores.

### ⚙️ ETAPA 3 — Pré-processamento

Após a EDA, foi realizado o preparo da base para utilização nos algoritmos de Machine Learning.

**🔎 Análise de correlação**

Foi construída uma matriz de correlação para identificar:

- relações entre as variáveis;
- possíveis redundâncias;
- multicolinearidade;
- variáveis com baixa contribuição para o modelo.

Com base nessa análise, algumas variáveis foram removidas da modelagem, como:

- `Reclamacao`;
- `Recencia`;
- `Num_Visitas_Web_Mes`.

Essa etapa teve como objetivo simplificar a estrutura do modelo e reduzir informações pouco relevantes para a previsão.

**🔤 Codificação das variáveis categóricas**

As variáveis categóricas foram transformadas utilizando **One-Hot Encoding**.

Foram codificadas:

- `Escolaridade`;
- `Estado_Civil`;
- `Perfil_Canal`.

A transformação foi necessária porque os algoritmos de Machine Learning utilizados trabalham com representações numéricas.

**✂️ Separação entre treino e teste**

A variável:

    Num_Compras_Web

foi definida como variável dependente (y), enquanto as demais variáveis selecionadas compuseram as variáveis independentes (X).

A base foi dividida em:

- **80% para treinamento;**
- **20% para teste.**

Foi utilizado `stratify=y` para preservar a distribuição da variável alvo entre os conjuntos.

**📏 Padronização**

Foi aplicado o **StandardScaler** às variáveis de entrada.

A padronização transforma as variáveis para uma escala comparável, com média próxima de 0 e desvio padrão de 1.

Essa etapa é especialmente relevante para a **Regressão Logística**, evitando que variáveis com valores numericamente maiores tenham influência desproporcional.

### 🤖 ETAPA 4 — Modelagem

Foram selecionados dois algoritmos de classificação:

**Regressão Logística**

Utilizada como modelo estatístico linear, oferecendo maior interpretabilidade sobre a relação entre as variáveis e a probabilidade de compra online.

**Random Forest Classifier**

Utilizado como modelo baseado em múltiplas árvores de decisão, capaz de capturar relações não lineares e interações mais complexas entre as características dos clientes.

A utilização dos dois modelos permitiu realizar uma comparação entre uma abordagem linear e outra baseada em aprendizado por conjuntos (ensemble).

### 📈 ETAPA 5 — Avaliação dos modelos

Os modelos foram avaliados utilizando:

- **Accuracy;**
- **Precision;**
- **Recall;**
- **F1-Score;**
- **Matriz de Confusão.**

As métricas foram calculadas tanto para os dados de treinamento quanto para os dados de teste, permitindo verificar não apenas o desempenho dos modelos, mas também possíveis sinais de **overfitting**.

A matriz de confusão foi utilizada para identificar:

- Verdadeiros positivos;
- Verdadeiros negativos;
- Falsos positivos;
- Falsos negativos.

## 🏆 Resultado

A análise comparativa demonstrou que o Random Forest Classifier apresentou o melhor desempenho geral na previsão da intenção de compra online.

Enquanto a Regressão Logística apresentou comportamento mais linear e maior interpretabilidade, o Random Forest conseguiu capturar melhor os padrões presentes na base.

Dessa forma, considerando as métricas avaliadas e a capacidade de classificação observada nos dados de teste, o Random Forest foi definido como o modelo de melhor desempenho para o problema analisado.

## ⚠️ Nota Técnica

Durante o desenvolvimento foram identificadas inconsistências entre o enunciado do projeto e a base de dados disponibilizada.

Uma das divergências identificadas está relacionada à ausência de variáveis mencionadas na descrição original do exercício. Essas diferenças foram documentadas e consideradas durante o desenvolvimento, evitando a criação de informações que não estavam efetivamente disponíveis na base.

## 🛠️ Tecnologias Utilizadas

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Plotly**
- **Scikit-learn**
- **Jupyter Notebook**

## 🎯 Competências Demonstradas

- Data Cleaning;
- Data Wrangling;
- Análise Exploratória de Dados (EDA);
- Análise de correlação;
- Tratamento de outliers;
- Feature Engineering;
- One-Hot Encoding;
- StandardScaler;
- Train/Test Split;
- Regressão Logística;
- Random Forest;
- Classificação supervisionada;
- Avaliação de modelos;
- Matriz de Confusão;
- Interpretação de métricas de Machine Learning;
- Análise comparativa de modelos.

## ✅ Conclusão

O projeto apresentou um fluxo completo de Ciência de Dados e Machine Learning, desde a exploração e tratamento dos dados até a construção e avaliação de modelos preditivos.

A comparação entre Regressão Logística e Random Forest Classifier demonstrou que o Random Forest apresentou melhor desempenho geral para identificar a intenção de compra online dos clientes.

O projeto também reforçou a importância das etapas de qualidade dos dados, análise exploratória e pré-processamento, uma vez que decisões tomadas antes da modelagem influenciam diretamente a qualidade e a interpretação dos resultados obtidos.