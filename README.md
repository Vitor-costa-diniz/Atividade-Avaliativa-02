# Clusterização de Vinhos com PCA e K-Means

## Sobre o Projeto

Este projeto aborda um problema clássico de aprendizado de máquina não supervisionado: como encontrar grupos ou padrões em um conjunto de dados que não possui rótulos predefinidos. O desafio é pegar dados complexos e multidimensionais — neste caso, 13 características químicas de vinhos — e agrupá-los em categorias que façam sentido.

Para resolver isso, utilizamos uma abordagem em duas etapas:

1.  **Simplificação dos Dados (PCA):** Primeiro, aplicamos a Análise de Componentes Principais (PCA) para reduzir a complexidade dos dados de 13 dimensões para apenas 2, tornando possível visualizar a estrutura dos dados em um gráfico.
2.  **Agrupamento (K-Means):** Em seguida, usamos o algoritmo K-Means nos dados simplificados para identificar e formar os clusters (grupos) de vinhos com perfis químicos semelhantes.

O resultado final é uma clara separação dos vinhos em três grupos distintos, que se alinha de forma muito próxima com as classes originais dos produtores, validando a eficácia do método.

## Objetivo

O objetivo principal é agrupar 178 amostras de vinhos em 3 clusters distintos com base em suas características químicas, sem utilizar os rótulos originais dos produtores para o treinamento.

## Etapas do Projeto e Funcionamento dos Algoritmos

#### 1. Preparação dos Dados
Antes de qualquer análise, os dados foram padronizados usando `StandardScaler`. Este passo é crucial porque o PCA é sensível à escala das variáveis. A padronização garante que características com valores maiores (como magnésio) não dominem a análise sobre características com valores menores (como pH).

#### 2. Redução de Dimensionalidade com PCA (Análise de Componentes Principais)
O PCA é uma técnica usada para transformar um conjunto de dados com muitas variáveis em um novo conjunto com menos variáveis, chamadas de **componentes principais**.

* **O que o PCA faz?** Ele encontra novas "direções" (os componentes) no conjunto de dados que capturam o máximo de informação possível. O primeiro componente principal é a direção que explica a maior parte da **variância** (a "dispersão" dos dados). O segundo componente explica a maior parte da variância restante, e assim por diante.
* **Por que usamos?** Com 13 características, é impossível visualizar como os vinhos se relacionam. Ao reduzir para 2 componentes, podemos plotar cada vinho em um gráfico de dispersão 2D, tornando a estrutura dos dados visível. Além disso, ao focar na maior parte da variância, o PCA ajuda a filtrar ruídos e a destacar os padrões mais importantes.

#### 3. Clusterização com K-Means
Após simplificar os dados com o PCA, aplicamos o K-Means para encontrar os grupos.

* **O que o K-Means faz?** É um algoritmo que agrupa os dados em um número pré-definido de clusters (neste caso, `k=3`). Ele funciona de maneira iterativa:
    1.  **Inicialização:** Escolhe aleatoriamente 3 pontos nos dados para serem os "centroides" iniciais (o centro de cada cluster).
    2.  **Atribuição:** Atribui cada amostra de vinho ao centroide mais próximo.
    3.  **Atualização:** Recalcula a posição de cada centroide para ser a média de todas as amostras que foram atribuídas a ele.
    4.  **Repetição:** Repete os passos 2 e 3 até que os centroides não mudem mais de posição, significando que os clusters estão estáveis.
* **Por que usamos?** O K-Means é eficiente e muito eficaz para encontrar grupos esféricos e bem definidos em dados, o que é exatamente o que o PCA nos ajuda a visualizar.

#### 4. Visualização e Análise
Finalmente, criamos dois gráficos para avaliar o resultado:
* **Gráfico 1:** Mostra os clusters encontrados pelo K-Means.
* **Gráfico 2:** Mostra as classes reais (os produtores originais) dos vinhos.

A comparação visual entre os dois gráficos nos permite validar o quão bem nosso modelo não supervisionado conseguiu recriar a classificação original.

## Resultados

A análise final revela uma alta correspondência entre os clusters formados pelo K-Means e as classes reais dos vinhos.
Isso demonstra que as características químicas dos vinhos são, de fato, distintas o suficiente para separá-los em seus respectivos produtores.
O projeto confirma que a combinação de PCA para simplificação e K-Means para agrupamento é uma abordagem poderosa para extrair insights valiosos de dados complexos.
