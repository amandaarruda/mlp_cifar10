# Mini-Projeto: Aplicação de MLPs ao CIFAR-10
Este repositório apresenta a análise do desempenho de diferentes configurações de redes neurais Perceptron Multicamadas (MLPs) aplicadas à classificação de imagens do conjunto CIFAR-10.

## Objetivo
Investigar o impacto de variações arquiteturais e de hiperparâmetros no desempenho das MLPs sobre um conjunto de dados de imagens naturais, visando avaliar sua capacidade de generalização em tarefas de classificação supervisionada.

## Dataset
CIFAR-10 é um conjunto composto por 60.000 imagens coloridas de 32x32 pixels, distribuídas igualmente entre 10 classes.

## Experimentos
Foram realizados 8 experimentos variando arquitetura, função de ativação, otimizadores, dropout, regularização L2, taxa de aprendizado, data augmentation e número de épocas.

## Tabela Resumo dos Resultados
| # | Arquitetura (Camadas/Neurônios)            | Função de Ativação | Batch Size | Learning Rate | Otimizador    | Dropout | Weight Decay (L2) | Data Augmentation | Épocas Treinadas | Acurácia Teste | Precisão | Recall | F1-Score |
|---|---------------------------------------------|---------------------|-------------|----------------|----------------|---------|--------------------|--------------------|------------------|----------------|----------|--------|----------|
| 1 | 3072 → 1024 → 512 → 10                      | ReLU                | 128         | 0.001          | Adam           | 30%     | N/A                | Não                | 20               | 0.55           | 0.56     | 0.55   | 0.55     |
| 2 | 3072 → 2048 → 1024 → 512 → 10               | ReLU                | 128         | 0.001          | Adam           | 30%     | 0.0001             | Não                | 40               | 0.58           | 0.59     | 0.58   | 0.58     |
| 3 | 3072 → 1024 → 512 → 256 → 128 → 10          | LeakyReLU           | 64          | 0.0005         | RMSprop        | N/A     | 0.00001            | Sim                | 100              | 0.54           | 0.54     | 0.54   | 0.54     |
| 4 | 3071 → 170 → 155 → 155 → 10                 | LeakyReLU           | 16          | 0.00034        | AdamW          | 15%     | 0.0001             | Sim                | 50               | 0.56           | 0.55     | 0.56   | 0.55     |
| 5 | 3072 → 128 → 256 → 128 → 10                 | LeakyReLU           | 64          | 0.001          | Adam           | N/A     | 0.00001            | Sim                | 100              | 0.54           | 0.58     | 0.54   | 0.54     |
| 6 | 3072 → 128 → 256 → 128 → 10                 | LeakyReLU           | 64          | 0.001          | SGD            | N/A     | N/A                | Sim                | 100              | 0.51           | 0.51     | 0.51   | 0.50     |
| 7 | 3072 → 128 → 64 → 10                        | ReLU                | 64          | 0.001          | Adam           | 30%     | 0.0001             | Não                | 20               | 0.52           | 0.52     | 0.52   | 0.52     |
| 8 | 3072 → 256 → 128 → 64 → 10                  | Tanh                | 128         | 0.0005         | SGD (momentum) | 20%     | 0.001              | Sim                | 20               | 0.36           | 0.36     | 0.36   | 0.34     |

## Análises e Conclusões
O melhor desempenho foi obtido pelo experimento 2 (58% de acurácia), com arquitetura profunda, ReLU, dropout e regularização L2.

A função de ativação Tanh (experimento 8) resultou no pior desempenho.

Otimizadores Adam e AdamW demonstraram maior estabilidade e generalização.

Data augmentation contribuiu positivamente em modelos com menor capacidade.

A regularização (dropout e L2) foi essencial para mitigar overfitting em modelos mais complexos.

## Autoria
Trabalho desenvolvido por:

Amanda Arruda Melo Silva

Lucas Vinícius da Silva

Luís Felipe Oliveira Costa

Michel Leonidas Aleixo da Silva

Severino Carlos da Silva Junior
