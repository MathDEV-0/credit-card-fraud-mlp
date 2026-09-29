Detecção de Fraude em Transações de Cartão (Problema 2)

📌 O Contexto do Cliente

Uma fintech em rápido crescimento processa milhares de transações por hora e precisa modernizar sua segurança. Atualmente, o sistema de checagem é baseado em regras fixas, que os fraudadores já aprenderam a contornar. O desafio de negócio é equilibrar uma balança delicada:

Falso Positivo: Bloquear uma compra legítima gera atrito, reclamação e cancelamento de conta.

Falso Negativo: Liberar uma fraude gera prejuízo financeiro direto.

O objetivo é desenvolver uma arquitetura MLP (Perceptron de Múltiplas Camadas) sobre dados tabulares para tomar essa decisão de forma mais inteligente.

📊 Os Dados

O projeto utiliza uma base de transações de cartões europeus no Kaggle.

Volume total: 284.807 transações.

Fraudes: 492 transações (apenas 0,172% do total).

Privacidade: As variáveis foram anonimizadas utilizando a técnica de PCA (Análise de Componentes Principais), resultando em componentes numéricos (V1, V2, etc.).

🎯 Principais Desafios do Projeto

1. **A Ilusão da Acurácia:** Devido ao extremo desbalanceamento dos dados, um modelo ingênuo que simplesmente responda "não é fraude" para tudo terá 99,8% de acurácia, mas será completamente inútil. O foco deve estar em métricas como **Precisão, Revocação (Recall), Curva Precisão-Revocação** e na calibração do **Limiar de Decisão (Threshold)**.
2. **Custo Assimétrico dos Erros:** A decisão de onde colocar a linha de corte (limiar) deve passar por uma discussão de negócio para entender qual erro é mais custoso para a fintech no momento.
3. **Explicabilidade (XAI):** Como as variáveis passaram por PCA e perderam seu significado interpretável original, surge um grande desafio prático: como o time de atendimento vai justificar para o cliente o motivo pelo qual sua compra legítima foi bloqueada?