# modelo_previsao_cotacao_ibovespa
Modelo de Previsão Direcional do IBOVESPA

Este repositório contém um projeto de Machine Learning aplicado a séries temporais financeiras, com foco na previsão direcional de movimentos relevantes do IBOVESPA (D+1).

O objetivo não é prever o mercado de forma contínua e irrestrita, mas identificar oportunidades em janelas curtas e regimes específicos, utilizando técnicas robustas e interpretáveis.

🎯 Objetivo do Projeto

  Desenvolver um modelo de apoio à decisão para identificar movimentos direcionais relevantes do IBOVESPA no dia seguinte.

  Reduzir o impacto de ruído diário por meio de uma definição criteriosa de target.

  Avaliar diferentes modelos de ML sob uma perspectiva realista e corporativa.

  ⚠️ Importante: este projeto não tem como objetivo criar um sistema autônomo de trading, mas sim uma ferramenta analítica de suporte à tomada de decisão.



📊 Aquisição e Exploração dos Dados

  Fonte: Série histórica diária do IBOVESPA

  Granularidade: Diário

  Período analisado: ~600 dias úteis

  Principais características observadas:

  Forte dependência temporal

  Não estacionariedade

  Presença de múltiplos regimes de mercado

  Baixa volatilidade

  Alta volatilidade

  Movimentos laterais

  Essas características motivaram a adoção de janelas temporais curtas e a rejeição de validações aleatórias.

🔧 Engenharia de Atributos

  Foram utilizadas features simples, interpretáveis e financeiramente justificáveis, com o objetivo de reduzir overfitting.

  Atributos criados:

  Tendência

  Média móvel de 5 dias (MM5)

  Média móvel de 10 dias (MM10)

  Média móvel de 20 dias (MM20)

  Retorno
  
  Retorno diário (D0)

  Volatilidade

  Volatilidade histórica de 5 dias (VOL_5)

  Volatilidade histórica de 10 dias (VOL_10)

  Posicionamento do preço

  Distância do fechamento em relação à MM20

🎯 Definição do Target

  O target foi definido com foco em movimentos relevantes, descartando pequenas variações consideradas ruído.

  Regra utilizada:
  Alta (1): retorno D+1 > +0,3%
  Queda (0): retorno D+1 < -0,3%
  Zona neutra: removida do dataset
  Justificativa:

  Pequenas oscilações diárias possuem baixo poder preditivo

  A exclusão da zona neutra aumenta a separabilidade das classes

⏱️ Estratégia Temporal

  Ordenação rigorosa dos dados por data

  Separação treino/teste sem vazamento temporal

  Avaliação em janelas curtas (30 dias)

  O uso de validações rolling extensas mostrou queda significativa de performance, evidenciando forte dependência de regime.

🧠 Modelos Avaliados

  Regressão Logística

  Random Forest

  Gradient Boosting

  Modelo escolhido: Gradient Boosting

Motivos:

  Captura relações não lineares

  Bom desempenho em dados tabulares

  Equilíbrio entre viés e variância

  Maior estabilidade em janelas curtas

  Modelos mais complexos (ex: LSTM) foram evitados devido ao alto risco de overfitting e baixa interpretabilidade.

📈 Resultados
  Melhor cenário observado (janela de 30 dias):

  Acurácia: 75%

  Precision (classe Alta): 85%

  Recall (classe Alta): 85%

  Observações importantes:

  Resultados dependem fortemente do regime de mercado

  Performance não se sustenta em validações rolling longas

⚠️ Limitações

  Amostra reduzida em janelas curtas

  Sensibilidade a mudanças estruturais do mercado

  Não generaliza bem para períodos longos

  Essas limitações são esperadas em séries financeiras reais e foram explicitamente documentadas.

✅ Conclusão

  Este projeto demonstra que:

  É possível obter sinais de alta qualidade em janelas curtas

  A engenharia de atributos baseada em volatilidade é fundamental

  Modelos financeiros devem ser avaliados sob a ótica de regime



👤 Autor

Projeto desenvolvido por Mateus Moraes



