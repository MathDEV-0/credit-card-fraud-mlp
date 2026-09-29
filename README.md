# Detecção de Fraude em Transações de Cartão (Problema 2)

## 📌 O Contexto do Cliente
Uma fintech em rápido crescimento processa milhares de transações por hora e precisa modernizar sua segurança. Atualmente, o sistema de checagem é baseado em regras fixas, que os fraudadores já aprenderam a contornar. O desafio de negócio é equilibrar uma balança delicada:
* **Falso Positivo:** Bloquear uma compra legítima gera atrito, reclamação e cancelamento de conta.
* **Falso Negativo:** Liberar uma fraude gera prejuízo financeiro direto.

O objetivo é desenvolver uma arquitetura **MLP (Perceptron de Múltiplas Camadas)** sobre dados tabulares para tomar essa decisão de forma mais inteligente.

## 📊 Os Dados
O projeto utiliza uma base de [transações de cartões europeus no Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud).
* **Volume total:** 284.807 transações.
* **Fraudes:** 492 transações (apenas 0,172% do total).
* **Privacidade:** As variáveis foram anonimizadas utilizando a técnica de PCA (Análise de Componentes Principais), resultando em componentes numéricos (V1, V2, etc.).

## 🎯 Principais Desafios do Projeto

1. **A Ilusão da Acurácia:** Devido ao extremo desbalanceamento dos dados, um modelo ingênuo que simplesmente responda "não é fraude" para tudo terá 99,8% de acurácia, mas será completamente inútil. O foco deve estar em métricas como **Precisão, Revocação (Recall), Curva Precisão-Revocação** e na calibração do **Limiar de Decisão (Threshold)**.
2. **Custo Assimétrico dos Erros:** A decisão de onde colocar a linha de corte (limiar) deve passar por uma discussão de negócio para entender qual erro é mais custoso para a fintech no momento.
3. **Explicabilidade (XAI):** Como as variáveis passaram por PCA e perderam seu significado interpretável original, surge um grande desafio prático: como o time de atendimento vai justificar para o cliente o motivo pelo qual sua compra legítima foi bloqueada?

---

## 🚀 Como Executar o Projeto

> **💡 Recomendação Principal: Google Colab**  
> A forma mais fácil e rápida de rodar este projeto é utilizando o **Google Colab**. Além de não exigir nenhuma configuração complexa de ambiente, você pode ativar a aceleração por **GPU** de forma gratuita (em *Ambiente de execução > Alterar o tipo de ambiente de execução*), o que acelera drasticamente o treinamento das redes neurais (TensorFlow/Keras). Você só precisará colar o código ou importar o notebook e rodar!

### Opção Alternativa: Execução Local

Caso prefira rodar o projeto na sua própria máquina, siga os passos abaixo para preparar o ambiente:

#### 1. Preparando o Ambiente
É altamente recomendável criar um ambiente virtual (venv ou conda) para evitar conflitos de versão.

```bash
# Crie um ambiente virtual
python -m venv venv

# Ative o ambiente virtual
# No Windows:
venv\Scripts\activate
# No Linux/Mac:
source venv/bin/activate
```

#### 2. Instalando as Dependências
Com o ambiente ativado, instale as bibliotecas necessárias utilizando o arquivo `requirements.txt`:

```bash
pip install -r requirements.txt
```

#### 3. Download do Dataset
Os dados não estão inclusos diretamente no repositório devido ao tamanho. O código utiliza a biblioteca `kagglehub` para baixar o dataset diretamente durante a execução. Certifique-se de estar conectado à internet na primeira vez que rodar o projeto.

#### 4. Rodando o Modelo
Execute o script principal ou abra o Jupyter Notebook para treinar e avaliar a rede neural MLP:

```bash
# Se for um script Python
python main.py

# Se estiver usando um notebook (requer jupyter instalado)
jupyter notebook
```