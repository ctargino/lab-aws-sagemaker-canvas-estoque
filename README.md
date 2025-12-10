
# 📦 Sistema No-Code de Previsão de Estoque na AWS
Implementação de um pipeline completo de Machine Learning (ML) No-Code utilizando o **Amazon SageMaker Canvas**, parte do desafio da Digital Innovation One (DIO).

---

## 🎯 Escopo do Projeto
Este repositório tem como propósito detalhar a construção de um modelo de **projeção de inventário** (previsão de estoque). O processo, conforme ditado pelo desafio da DIO, foi integralmente realizado através da interface visual do SageMaker Canvas, documentando as seguintes fases:

* Preparação e curadoria do conjunto de dados.
* Carregamento (Upload) da base de dados no SageMaker Canvas.
* Definição e mapeamento das variáveis do modelo.
* Treinamento e otimização do algoritmo.
* Análise crítica das métricas de desempenho.
* Simulação e geração de projeções.
* Descoberta de pontos de atenção (insights).
---

## 🗂️ Estrutura do Repositório

```
lab-aws-sagemaker-canvas-estoque/
├── README.md
├── dataset/
│   └── estoque_exemplo.csv
└── imagens/
    └── exemplo_treinamento.png
```

## 1️⃣ Base de Dados Utilizada

O modelo foi alimentado com um conjunto de dados simulado, refletindo o histórico de vendas e gestão de inventário. As colunas principais são:

* `data`: Período da observação.
* `produto`: Identificador do item.
* `estoque_atual`: Quantidade disponível no momento.
* `vendas_dia`: Volume de saídas diárias.
* `dias_para_reposicao`: Tempo estimado para reabastecimento.
* `estoque_futuro` (**Variável Preditiva**): A métrica que o modelo deve estimar.

O arquivo pode ser encontrado em **dataset/estoque_exemplo.csv**.

---

## 2️⃣ Desenvolvimento e Otimização do Modelo

A criação do modelo ocorreu totalmente dentro do ambiente **Amazon SageMaker Canvas**, com os seguintes passos:

### ✔️ Ingestão de Dados
O arquivo CSV foi transferido diretamente para o Canvas.

### ✔️ Mapeamento de Atributos (Features)
* **Variável Alvo (Target)**: `estoque_futuro` (o que queremos prever).
* **Variáveis Explicativas (Features)**:
    * `estoque_atual`
    * `vendas_dia`
    * `dias_para_reposicao`
    * `produto` (O Canvas lida automaticamente com sua natureza categórica).

### ✔️ Classificação da Tarefa
O Canvas reconheceu a tarefa como um problema de **Regressão**, visto que o objetivo é prever um valor numérico contínuo.

### ✔️ Treinamento
Foi escolhida a opção **Standard Build**, que garante maior precisão e uma análise mais aprofundada dos dados.

---

## 3️⃣ Avaliação de Performance

Após a conclusão do treinamento, o Canvas forneceu uma visão detalhada da performance do modelo:

### 📊 Métricas Chave
* **RMSE (Root Mean Square Error)**: Analisado para garantir que o erro esteja em um nível aceitável.
* **R² (Coeficiente de Determinação)**: Satisfatório, indicando que o modelo captura bem a variação da variável alvo.
* **Correlação**: Apresentou a interdependência entre os atributos.

### 💡 Relevância das Variáveis
A análise de importância destacou os fatores mais influentes na previsão:

1.  `vendas_dia` (Mais crítico)
2.  `estoque_atual`
3.  `dias_para_reposicao`

---

## 4️⃣ Execução de Previsões

O modelo treinado foi imediatamente empregado para simular cenários:

* Projeção do nível de estoque em datas futuras.
* Identificação proativa de **rupturas de estoque** (falta de produtos).
* Priorização de itens com alto risco de esgotamento antes do próximo reabastecimento.

Os resultados das previsões foram exportados em formato `.csv` para posteriores decisões operacionais.

---

## 📈 Conclusões e Potenciais Expansões

* Produtos de alta rotatividade demonstraram uma forte correlação entre a previsão e a variável `vendas_dia`.
* O modelo comprovou ser eficaz na sinalização de **gargalos críticos de inventário**.
* **Próximos passos**: A precisão pode ser aprimorada pela inclusão de dados adicionais, como:
    * Impacto de ações promocionais.
    * Variações sazonais de demanda.
    * Lead time real e variado dos fornecedores.

---

## 🔗 Referência Original
Este projeto foi desenvolvido em cumprimento ao desafio da DIO:
https://github.com/digitalinnovationone/lab-aws-sagemaker-canvas-estoque

---

## ✅ Resumo

Este repositório documenta a conclusão bem-sucedida do desafio da DIO, demonstrando a implementação de um fluxo completo de ML preditivo usando o **SageMaker Canvas**. O resultado é um modelo robusto, pronto para otimizar decisões logísticas e de reposição de estoque em qualquer contexto empresarial.
