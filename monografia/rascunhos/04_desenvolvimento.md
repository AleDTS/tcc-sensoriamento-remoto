# Desenvolvimento

# Etapas

## Aquisição dos dados

### Área de Treinamento

​	Primeiro, foi selecionado e feito *download* de um arquivo no formato *shapefile*, da malha territorial do estado de São Paulo, com divisão por município, disponibilizado pelo Instituto Brasileiro de Geografia e Estatística (IBGE). A partir desse arquivo, foi selecionado apenas o polígono que representa o município de Bauru.

​	Para a seleção das amostras de treinamento, era preciso que os dados representassem bem as classes de uso e cobertura do solo dentro do município. De acordo com o ([PLANO PRESERVACAO](http://www2.bauru.sp.gov.br/arquivos/arquivos_site/sec_meioambiente/plano_mata_atlantica.pdf)) e ([CAVASSAN](https://repositorio.unesp.br/bitstream/handle/11449/135125/ISSN1413-7461-2013-17-01-46-54.pdf?sequence=1&isAllowed=y)), as principais unidades fitogeográficas que ocorrem no município de bauru são as formações de Floresta Estacional Semidecidual e de Cerrado, apesar de a cobertura primitiva já tenha sido muito reduzida, assim como o Cerrado no estado de São Paulo, que já representou uma área maior.

### Seleção de Amostras

​	Portanto, duas decisões foram tomadas: as amostras de treinamento seriam provindas do bioma Cerrado; como a extensão o Cerrado é grande, a fim de viabilizar o processamento, apenas a região de cerrado dentro do estado de São Paulo foi selecionada. Para isso, foi feito o download de outro arquivo do site do Mapbiomas (MAPBIOMAS): um *raster* do mapa da coleção 3.1 do projeto, para o bioma Cerrado, classificado de acordo com a metologia ATBD contendo as seguintes classes:

​	Esse *raster* foi recortado para o tamanho do polígono do estado de São Paulo. Em seguida, foi feito a seleção de 200 amostras aleatórias de cada classe, e exportado para um arquivo *shapefile*. 

### Extração dos Valores das Amostras

​	A próxima etapa, foi a de extração dos valores das amostras. Cada coordenada gerada na última etapa, contém a informação da classe que ela representa, então o próximo passo foi de extrair os valores de cada banda naquele ponto, e então compor a tabela com as variáveis preditoras para a modelagem de aprendizado de máquina.

​	Nessa etapa, foi utilizado o ambiente do Google Earth Engine, onde o *shapefile* foi carregado, foi feita uma composição com imagens do satélite Sentinel-2, filtradas por baixa porcentagem de nuvens e para a região em que os pontos estão compreendidos. Em seguida, para cada ponto, foi extraído os valores das bandas e exportado para um arquivo *geojson*, que foi importado de volta ao ambiente do RStudio.

​	Em um sistema de classificação, antes da extração dos valores dos pontos das amostras, seria interessante que a imagem passasse por um processo de pré processamento. Essa etapa incluiria a aplicação de técnicas de processamento de imagens para correções atmosféricas e geométricas, eliminação de ruídos, entre outras (LU, WENG). Contudo, uma característica das imagens do Sentinel 2, é de que há uma série de etapas de pré processamento, como as mencionadas, que são realizadas antes das imagens serem disponibilizadas. 

## Extração de Características

​	A etapa da extração de características envolve a seleção das variáveis usadas no processo de classificação, que podem ser as assinaturas espectrais das bandas, índices de vegetação, informação de textura, entre outras (LU, WENG). 

### Índices de Vegetação

​	Os índices de vegetação são obtidos através de operações aritméticas entre as bandas. Possuem a característica de realçar as variações de densidade da cobertura vegetal (MENESES). O NDVI é provavelmente o mais utilizado, ou pelo menos o mais conhecido. Esse índice possui a característica de evidenciar áreas da vegetação fotossinteticamente mais ativas. O cálculo do NDVI é dado por:
$$
NDVI = \frac{NIR - RED}{NIR + RED}
$$
Onde $NIR$ é o valor para a banda na região do infravermelho próximo (a banda 8 do Sentinel 2) e $RED$ é a banda na região do vermelho (banda 4).

### Seleção de Amostras

​	Como variáveis preditoras, foram selecionadas as bandas "SWIR1", "SWIR2", "Azul", "Verde", "Vermelho", "NIR", "RE1", "RE2", "RE3", "RE4" e uma nova coluna contendo o cálculo do NDVI para cada ponto da amostra.

## Modelagem

​		O pacote *caret* (*Classification And REgression Training*) do R contém funções para otimizar o processo de treinamento de modelos para problemas de regressão e classificação (CARET). Ele funciona como um agregador de diversos pacotes que contém métodos de aprendizado estatístico, fazendo a interface entre as funções disponíveis no pacote para controle do processo de treinamento e avaliação de resultados.

### Reamostragem

​	A primeira etapa para a criação dos modelos, foi a divisão do conjunto de dados em dois subconjuntos: um de treinamento (75%) e outro de teste (25%).  Utilizando a função de validação cruzada do *caret*, na criação do modelo, o conjunto de treinamento é reparticionado em 10, e então, a partir dessa repetições no ajuste, é escolhido o conjunto de parâmetros que teve melhor resultado para aquele método.

### Treinamento

​	Na etapa do treinamento dos modelos, para a seleção dos parâmetros utilizados em cada algoritmo foi utilizada a técnica da validação cruzada *k-fold* (não é o mesmo que na última etapa), onde os dados de treinamento são subdivididos em *k* subconjuntos e então, o modelo é calculado *k* vezes, e então, o resultado é comparado para seleção do parâmetro (ou conjunto) que obteve melhor resultado, no caso, o método de comparação utilizado foi a acurácia geral a partir da matriz de confusão gerada para cada modelo.

​	O primeiro modelo foi treinado com o algoritmo MVS (*svmRadial* no *caret*), utilizado como núcleo a função de base radial dada por:
$$
K(x,y) = \exp(-\frac{\parallel x-y^{2} \parallel}{\sigma^{2}})
$$
​	Após o treinamento do modelo, foram selecionados os parâmetros C = 1 e Sigma = 1.

PARÂMETROS SELECIONADOS PARA MVS COM NÚCLEO RADIAL

​	O próximo modelo, foi MVS também, porém linear (*svmLinear3* no *caret*), ou seja, sem função de núcleo e com regularização, que significa aplicar um custo de penalização nos parâmetros $\theta$. Os parâmetros selecionados foram C = 0.03 e Loss = L2.

PARÂMETROS SELECIONADOS PARA MVS SEM NÚCLEO

​	Por último, foi computado também um modelo utilizando Florestas Aleatórias (*rf* no *caret*), com o parâmetro selecionado mtry = 3.  

PARÂMETROS SELECIONADOS PARA FA

# Resultados

## Predição

​	Para cada modelo treinado, foi realizada uma predição com a imagem selecionada anteriormente do satélite Sentinel para a região do município de Bauru, resultando em *rasters* com os valores para cada classes usadas para a criação dos modelos, demonstrados a seguir:

MAPA DO  CLASSES DE USO E COBERTURA DA TERRA OBTIDO A PARTIR PREDIÇÃO DO MODELO UTILIZANDO MÁQUINA DE VETORES SUPORTE COM NÚCLEO RADIAL

MAPA COM CLASSES DE USO E COBERTURA DA TERRA OBTIDO A PARTIR PREDIÇÃO DO MODELO UTILIZANDO MÁQUINA DE VETORES SUPORTE SEM NÚCLEO E COM REGULARIZAÇÃO

MAPA COM CLASSES DE USO E COBERTURA DA TERRA OBTIDO A PARTIR PREDIÇÃO DO MODELO UTILIZANDO FLORESTAS ALEATÓRIAS

### Avaliação de Precisão

​	Para a avaliação da qualidade das predições realizadas, foi computado a matriz de confusão de cada uma, a partir dos índices calculados a partir da matriz de erro. A matriz de erro por sua vez foi montada a partir da seleção de 100 pontos de amostras para cada classe dos *rasters* obtidos na etapa da predição, e em seguida, os valores dos pontos foram extraídos de um conjunto verdade, que é um *raster* da mesma região com a classificação realizada pela iniciativa MapBiomas e disponibilizada para download. Para comparação visual com os mapas apresentados anteriormente, o *raster* do MapBiomas está representado a seguir:

MAPA COM CLASSES DE USO E COBERTURA DA TERRA OBTIDO A PARTIR DA CLASSIFICAÇÃO  REALIZADA PELO MAPBIOMAS

​	Com destaque para os índices *kappa* e *accuracy* (acurácia geral), na tabela a seguir estão demonstrados os valores dos resultados:

TABELA DE AVALIAÇÃO DE PRECISÃO DAS PREDIÇÕES REALIZADAS

### Considerações

​	Comparando visualmente os mapas obtidos com o mapa do MapBiomas, pôde-se notar algumas classes que sofreram certa confusão, como é o caso da *formação_florestal* na predição com FA, que na verdade representariam a classe *floresta_plantada*. Levando em consideração que na metodologia do MapBiomas aplicada nos dados de treinamento são utilizadas outras variáveis de predição (como outros índices de vegetação), é provável que apenas as bandas selecionadas e o NDVI não seja suficiente para separar com precisão todas as classes utilizadas, como (WENG) apontam no artigo o qual este trabalho se baseou. Ainda no caso dessa predição, a acurácia foi prejudicada pelo fato dos *pixels* apresentarem pouca homogeneidade nos espaços vizinhos. A predição realizada com o algoritmo MVS com núcleo não linear, apesar de apresentar uma acurácia mediana, resultou em poucas classes que predominaram. A classificação que obteve melhor resultado foi a que utilizou MVS linear para criação do modelo.



