# Projeto de Previsão de Churn com Machine Learning

## 📌 Definição de Churn

Neste projeto, consideramos que um cliente realizou churn (ou seja, foi perdido) quando **não renovou ou não realizou uma nova assinatura válida até 30 dias após o término da assinatura anterior**.

---

## 🔁 Etapas do Projeto

1. **Processamento inicial**  
   Arquivo bruto de ~30GB processado e dividido em amostras para facilitar o manuseio.

2. **Definição de regra de churn e modelagem da base**  
   Definimos o churn conforme explicado acima e modelamos as tabelas com base em regras de negócio.

3. **Validação e análise exploratória**  
   Com a base ajustada, validamos os dados e realizamos EDA para identificar padrões iniciais.

4. **Engenharia de variáveis**  
   A partir da análise, criamos variáveis relevantes para alimentar os modelos.

5. **Modelagem e deploy de campanhas**  
   Criamos modelos preditivos e desdobramos os resultados em campanhas com foco em **retenção e engajamento da base**.

---

## 🗂️ Organização das Pastas (Data Lake)

| Camada | Descrição |
|--------|-----------|
| **RAW**    | Dados brutos extraídos diretamente do Kaggle. |
| **BRONZE** | Dados processados e amostrados: `df_members`, `df_user_logs`, `df_transactions`. |
| **PRATA**  | Dados transformados com feature store e regra de churn aplicada. |
| **OURO**   | Tabela final com a **probabilidade de churn** (`df_proba`) para tomada de decisão. |

---

## 🤖 Modelagem - Pipeline de Machine Learning

1. Leitura do book de variáveis e cruzamento com a base de churn  
2. Divisão dos dados: 60% treino, 20% validação, 20% teste  
3. Normalização e codificação de variáveis categóricas  
4. Simulação de diferentes modelos  
5. Escolha do melhor modelo com análise de trade-off entre métricas de negócio

---

## 🧠 Modelo Escolhido

- **XGBoost**
- Métricas utilizadas:
  - F1-Score
  - AUC-ROC
  - AUC-PR
- Técnicas aplicadas para lidar com desbalanceamento:
  - `scale_pos_weight`
  - Uso de AUC-PR para otimizar a performance na classe minoritária

---

## 📈 Resultados

| Métrica | Validação | Teste |
|--------|-----------|-------|
| **AUC-ROC** | 0.845 | 0.846 |
| **F1-Score** | 0.53 | 0.53 |
| **Recall** | 0.56 | 0.58 |
| **Precision** | 0.50 | 0.49 |

- **Top 3 variáveis mais importantes**:
  1. `%_último_mês`
  2. `%_cancel`
  3. `actual_amount_paid`

As curvas ROC e o gráfico de importância de variáveis mostram boa capacidade preditiva e interpretabilidade do modelo.

---

## 🎯 Considerações Finais

O modelo de churn desenvolvido é eficaz para prever a saída de usuários da plataforma, permitindo ações preventivas com maior assertividade. As campanhas baseadas nas predições ajudaram a aumentar a **retenção e engajamento** da base de clientes.
