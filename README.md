# 🏀 Classificação de Posições de Jogadores da NBA

Este projeto aplica técnicas de Ciência de Dados e Machine Learning para classificar a posição de jogadores da NBA com base em suas estatísticas de jogo. O objetivo é entender se as métricas tradicionais ainda definem bem as posições em uma era de "positionless basketball".

## 📋 Visão Geral

O projeto segue um pipeline completo de Data Science:
1.  **Análise Exploratória e Limpeza**: Tratamento de valores nulos e outliers.
2.  **Engenharia de Features**: Criação de novas métricas para capturar nuances do jogo.
3.  **Modelagem**: Teste e otimização de diversos algoritmos de classificação.
4.  **Avaliação**: Análise detalhada de performance e erros.

## 🛠️ Metodologia

### 1. Dados
O dataset base é o `NBA_Player_Stats.csv`, contendo estatísticas de temporada regular.
- **Limpeza**: Remoção de colunas irrelevantes e tratamento de valores nulos.
- **Outliers**: Análise e tratamento de outliers em métricas chave.

### 2. Engenharia de Features
Foram criadas 15 novas variáveis para enriquecer o modelo, divididas em categorias:
- **Playmaking**: `assist_turnover_ratio`, `assists_per_minute`, `playmaking_score`.
- **Garrafão (Big Men)**: `rebounds_per_minute`, `blocks_per_minute`, `interior_dominance`.
- **Arremesso (Shooting)**: `three_point_rate`, `scoring_efficiency`, `perimeter_threat`.
- **Defesa**: `defensive_versatility`, `defensive_impact`, `steals_per_minute`.
- **Geral**: `points_per_minute`, `usage_rate`, `true_shooting_pct`.

### 3. Modelagem
Foram testados quatro algoritmos principais:
- **Random Forest**: Ensemble de árvores de decisão.
- **Logistic Regression**: Modelo linear base.
- **SGD Classifier**: Modelo linear com gradiente descendente estocástico.
- **SVC (Support Vector Classifier)**: Modelo baseado em vetores de suporte.

**Otimização**:
Utilizou-se `GridSearchCV` para ajustar hiperparâmetros. O **SVC** apresentou o melhor desempenho geral, com melhor generalização (menor gap entre treino e validação) em comparação ao Random Forest.

## 📊 Resultados Principais

- **Melhor Modelo**: SVC (Kernel RBF, C=1, Gamma=0.1).
- **Acurácia Geral**: ~64% (no dataset completo de jogadores únicos).
- **F1-Score Médio (CV)**: ~0.56.

### Performance por Posição
O modelo tem facilidade em distinguir posições extremas, mas confunde posições intermediárias (o que é esperado no basquete moderno):
- **Point Guards (Armadores)**: Alta precisão (~76%).
- **Centers (Pivôs)**: Alta precisão (~75%).
- **Wings (Alas/Armadores)**: Menor precisão (~42-60%), refletindo a versatilidade desses jogadores.

## 🚀 Como Executar

1.  Certifique-se de ter as dependências instaladas:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```
2.  Execute o notebook principal:
    ```bash
    jupyter notebook NBA_Posicoes_Jogadores.ipynb
    ```
3.  Os resultados finais das predições serão salvos em `nba_predictions_svc_unique_players.csv`.

## 📁 Estrutura do Projeto

- `NBA_Posicoes_Jogadores.ipynb`: Notebook principal com todo o código.
- `data/`: Diretório contendo o dataset original.
- `outputs/`: Diretório onde são salvos os modelos e resultados.
- `utils.py`: Funções auxiliares (se houver).

---

Autores: Denise Ramos Soares e Izabella Bonfim

*Desenvolvido como parte da disciplina de Introdução à Ciência de Dados, ministrada pelo professor Erneson Alves de Oliveira - Mestrado em Informática Aplicada (Unifor).*
