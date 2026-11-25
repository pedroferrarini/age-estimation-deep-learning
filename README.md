# Estimativa de Idade por Imagens com Deep Learning

## Sobre o Projeto

Este projeto tem como objetivo desenvolver um modelo de Deep Learning capaz de estimar a idade de pessoas a partir de fotografias, utilizando técnicas de Visão Computacional e Transfer Learning.

O projeto faz parte do curso de Ciência de Dados da TripleTen e simula um cenário em que uma rede de supermercados deseja utilizar câmeras para auxiliar na verificação da idade de clientes durante a compra de bebidas alcoólicas.

## Objetivos

- Realizar uma análise exploratória das imagens e das idades disponíveis.
- Preparar os dados para o treinamento do modelo.
- Desenvolver um modelo de estimativa de idade utilizando a arquitetura ResNet50.
- Avaliar o desempenho do modelo por meio da métrica MAE (Mean Absolute Error).

## Conjunto de Dados

O conjunto de dados contém **7.591 imagens de rostos**, acompanhadas de suas respectivas idades.

Os arquivos estão organizados da seguinte forma:

- `final_files/`: diretório contendo as imagens.
- `labels.csv`: arquivo com os nomes das imagens (`file_name`) e as idades reais (`real_age`).

### Análise Exploratória dos Dados (EDA)

Durante a análise exploratória, foram identificadas as seguintes características:

- Total de imagens: 7.591.
- Idade mínima: 1 ano.
- Idade máxima: 100 anos.
- Idade média: aproximadamente 31,2 anos.
- Idade mediana: 29 anos.
- Valores ausentes: nenhum identificado nas colunas analisadas.

Também foi elaborado um histograma para visualizar a distribuição das idades e foram exibidas 15 imagens do conjunto de dados para observar a variedade de rostos e faixas etárias.

## Desenvolvimento do Projeto

### 1. Preparação dos Dados

- Carregamento dos rótulos utilizando Pandas.
- Utilização do `ImageDataGenerator` para carregar as imagens em lotes.
- Redimensionamento das imagens para 224 × 224 pixels.
- Definição do tamanho dos lotes (`batch_size`) em 32.
- Separação dos dados em conjuntos de treinamento (75%) e validação (25%).

### 2. Construção do Modelo

Foi utilizada a arquitetura **ResNet50**, com pesos pré-treinados no ImageNet, aplicando a técnica de Transfer Learning.

A arquitetura foi configurada com:

- ResNet50 com pesos pré-treinados no ImageNet.
- Camada convolucional congelada (`backbone.trainable = False`).
- `GlobalAveragePooling2D` para redução das dimensões das características extraídas.
- `Dense(1, activation='relu')` para realizar a previsão da idade.

### 3. Treinamento

As configurações utilizadas foram:

- Otimizador: Adam.
- Taxa de aprendizado: 0.0001.
- Função de perda: Mean Squared Error (MSE).
- Métrica de avaliação: Mean Absolute Error (MAE).
- Número de épocas: 5.

## Resultados e Avaliação

Ao final do treinamento, o modelo alcançou um **MAE de aproximadamente 13,48 anos no conjunto de validação**.

O resultado demonstra que o modelo conseguiu aprender padrões visuais relevantes para estimar a idade, apresentando redução dos erros ao longo das épocas.

Entretanto, o desempenho ficou acima da referência de 8 anos esperada para o projeto, indicando oportunidades de melhoria na precisão das previsões.

### Conclusão

O desenvolvimento do projeto permitiu aplicar conceitos de análise exploratória, pré-processamento de imagens, Redes Neurais Convolucionais e Transfer Learning.

Embora o modelo tenha apresentado evolução durante o treinamento, o erro médio de 13,48 anos limita sua utilização em situações que exigem uma verificação confiável da idade, como a compra de bebidas alcoólicas.

Como possibilidades de melhoria, podem ser explorados o ajuste das camadas da ResNet50, o aumento do número de épocas e o aprimoramento das estratégias de treinamento.

## Tecnologias e Bibliotecas

- Python
- Pandas
- Matplotlib
- Seaborn
- TensorFlow
- Keras
- ResNet50
- Jupyter Notebook

## Competências Desenvolvidas

- Análise Exploratória de Dados (EDA).
- Manipulação e preparação de dados.
- Pré-processamento de imagens.
- Visão Computacional.
- Redes Neurais Convolucionais (CNN).
- Transfer Learning.
- Treinamento e avaliação de modelos de Deep Learning.
- Avaliação de modelos utilizando MAE.
