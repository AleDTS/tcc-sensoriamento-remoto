# Fundamentação teórica

# Geotecnologias

> As  geotecnologias  são  o  conjunto  de  tecnologias  para  coleta,  processamento,  análise  e  oferta  de  informação  com  referência  geográfica. ([ROSA, 2005](http://www.revistas.usp.br/rdg/article/view/47288/51024))

​	Podem ser caracterizadas geotecnologias: Sistemas de Informação Geográfica (SIG), cartografia digital, Sensoriamento Remoto (SR), sistema de posicionamento global (GPS) e a topografia. Geoprocessamento, por sua vez, é um conceito mais abrangente e representa qualquer tipo de processamento de dados georreferenciados (ROSA, 2005). Um SIG,

> é um conjunto de ferramentas computacionais composto de equipamentos e programas que, por meio de técnicas, integra dados, pessoas e instituições, de forma a tornar possível a coleta, o armazenamento, o processamento, a análise e a oferta de informação georreferenciada produzida por meio de aplicações disponíveis, que visam maior facilidade, segurança e agilidade nas atividades humanas referentes ao monitoramento, planejamento e tomada de decisão relativas ao espaço geográfico. (ROSA, 2005)

​	Os SIGs se desenvolveram consideravelmente durante as últimas décadas. Inicialmente, nos anos 80, cada sistema tinha um banco de dados próprio e o processamento era feito isoladamente, em softwares de código fechado. Nos anos 90, formatos de arquivos surgiram, o que facilitou a intercâmbialidade entre os programas disponíveis. A partir de 2000, surgiu a biblioteca GDAL (*Geospatial Data Abstraction Layer*), feita para ler e escrever dados geoespaciais. De 2010 até hoje em dia, os ambientes de computação em núvem surgiram a fim de resolverem o problema de análise, mas novamente de maneira isolada, gerando problemas de reprodutibilidade. (OPENEO)

## Dados geoespaciais

​	São considerados dados geoespaciais, dados georreferenciados, ou ainda dados espaciais, os dados que possuem uma localização definida. Computacionalmente, são representados por: pontos, que interligados podem formar linhas e polígonos que representam um objeto geográfico e são chamados de **dados vetoriais**; por matrizes de pontos, divididas em células de tamanhos iguais, que são os *pixels* de uma imagem, denominados como **dados *raster***; ou ainda com metadados, que são textos, números e símbolos armazenados em tabelas e vinculados aos dados que possuem referência espacial. Todo dado espacial é composto por um Sistema de Referência de Coordenadas (SRC), que pode ser geográfico (esférico ou geodésico, ou seja, no formato da Terra) ou projetado (em duas dimensões). (GEOCOMPR, CAP 2, [IBGE](https://biblioteca.ibge.gov.br/visualizacao/livros/liv101675.pdf))

# Sensoriamento Remoto

​	De maneira objetiva, sensoriamento remoto (SR) pode ser definido como:

> "(...)  uma   ciência   que   visa   o   desenvolvimento  da  obtenção  de  imagens  da  superfície  terrestre  por  meio  da  detecção  e  medição  quantitativa  das  respostas  das  interações  da  radiação  eletromagnética  com  os  materiais terrestres" (MENESES, 2012)

​	Por essa definição, tem-se um sistema onde um **alvo** localizado na superfície da terra interage com a **energia** proveniente de uma **fonte** (como a luz solar) gerando uma resposta que é captada por um sensor (geralmente um satélite) e que por sua vez é processada e traduzida como uma **imagem**.

## Energia

​	A Radiação Eletromagnética (REM) é caracterizada pela dualidade de comportamento na natureza: é ao mesmo tempo uma forma de onda e uma forma de energia que se propaga pelo espaço vazio. Segundo o modelo ondulatório, a radiação é definida como uma forma de onda propagada a partir da perturbação dos campos elétrico e magnético, gerados por uma partícula eletricamente carregada. As características das imagens de SR são definidas pela intensidade com que um objeto reflete a REM em razão da textura de sua superfície e do comprimento de onda; essa interação é denominada **interação macroscópica**. Já o modelo corpuscular, define a REM como uma forma dinâmica de energia que se manifesta por suas interações com a matéria. As trocas de energia ocorrerão somente se a quantidade de energia da REM for igual à necessária para promover uma mudança nos níveis de energia dos átomos ou moléculas, caracterizando a **interação microscópica**. (MENESES)

​	A partir desses modelos, define-se a energia transportada $E$, o comprimento de onda $\lambda$ relacionados pela equação:
$$
E = \frac{hc}{\lambda}
$$
Onde $h$ é constante de Planck ($6,624\times10^{-34}$ Joules.seg) e $c$ a velocidade da luz de aproximadamente $300.000$ km/s

### Interferências Atmosféricas

​	O nosso sistema solar tem como o próprio Sol a maior fonte de energia que chega até a Terra, que por sinal também emite REM, em menor quantidade mas que pode ser detectada por sensores. No caso do SR orbital (ou seja, via satélite), a atmosfera é opaca à radiação para vários intervalos de comprimentos de onda. Isso ocorre devido aos efeitos de **absorção** e **espalhamento** causados pela interferência da interação entre a REM e as partículas e moléculas presentes na atmosfera terrestre. (MENESES)

### Espectro Eletromagnético

​	O espectro eletromagnético representa a distribuição da REM por regiões espectrais conhecidas pelo homem. Da luz visível, por exemplo, cada cor tem seu comprimento de onda, portanto as imagens de SR são definidas em intervalos (ou **bandas**). Lembrando que a cor "real" dos alvos não é a mesma capturados pelos sensores, devido às interferências explicadas logo acima. (MENESES)

TABELA COMPRIMENTO DE ONDA E CORES

​	Os objetos (ou **alvos**) presentes na superfície terrestre refletem, absorvem e transmitem radiação de acordo com a característica de seu material de composição. As variações da energia refletida podem ser representadas através de curvas, que distinguem os alvos. A representação destes nas imagens vão variar, para cada banda, do branco (ou seja, refletem mais energia) ao preto (refletem pouca energia). 

## Sensores

​	O sensor é responsável por captar e converter para valores digitais a intensidade da radiância, ou seja, o fluxo radiante refletido pelo elemento da superfície. As imagens são capturadas e posteriormente pré processadas, e nesse processo geralmente são convertidos os valores da radiância para a reflectância, obtida pela divisão entre a radiância e a irradiância, que por sua vez representa a densidade do fluxo radiante solar incidente por área da superfície. O tipo mais comum de sensor, é o multiespectral. São sensores capazes de obter múltiplas imagens simultâneas da superfície em diversos comprimentos de ondas diferentes. (MENESES)

### Resolução

​	As características de uma imagem obtida por sensoriamento remoto podem ser resumidas em quatro resoluções: espacial (ou geométrica), temporal, espectral e radiométrica. A **resolução espacial**, dada em metros, é a área representada por um pixel na imagem final, ou seja, se é de 30 metros, significa que a largura de um pixel representa um espaço de 30 metros na superfície. A **resolução espectral** é definida por três características: o número de bandas, a largura do comprimento de onda de cada banda, e onde cada uma está posicionada no espectro. A largura da banda, vai definir por exemplo as feições de absorção de cada material, para aquela região do espectro. A intensidade da radiância da área de cada pixel é medida pela **resolução radiométrica**. O sinal que o sensor recebe é quantizado em valores digitais (*bits*), ou seja, essa resolução definirá quantos tons de cinza uma imagem consegue representar. Por último, a **resolução temporal** refere-se a frequência que um sensor revisita uma área, gerando imagens periódicas muito importantes para análises temporais. (MENESES)

# Aprendizado de Máquina

​	Aprendizado de máquina (AM) é uma área da inteligência artificial que se refere ao desenvolvimento de métodos que otimizam sua performance iterativamente aprendendo com dados. (TOM MITCHELL, 1998) define como:

> Um programa de computador é orientado a aprender da experiência $E$, com a uma tarefa $T$ e uma medida de performance $P$, se sua performance em $T$, medida por $P$, melhora com a experiência $E$.

​	Os diversos métodos de AM podem ser categorizados em diversos critérios. Se no problema em questão é apresentado um conjunto de dados em que se sabe o resultado correto das predições, é chamado de **aprendizado supervisionado**. Caso não se tenha informações sobre os resultados, temos um método de **aprendizado não supervisionado**.

​	Dado um conjunto de testes, o objetivo de um problema de aprendizado supervisionado é aprender uma função $h \rarr XY$, sendo $h(x)$, chamada de hipótese, um "bom" preditor do valor correspondente de $y$.

​	Dentro dos classificadores supervisionados, podemos dividir em regressão e classificação. Em um **problema de regressão**, temos a previsão de um resultado dentro de uma saída contínua, ou seja, é necessário mapear as variáveis de entrada em uma função contínua. No caso do **problema de classificação**, o objetivo é a previsão de um resultado em uma saída discreta, ou seja, mapeiam-se variáveis de entrada em categorias. (COURSERA)

​	O foco deste trabalho é o estudo de métodos classificadores supervisionados, a fim de predizer classes espectrais que representam diferentes alvos de uso e cobertura da terra. Portanto, segue uma explicação das principais técnicas utilizadas segundo a literatura, bem como as que foram implementadas.

## Aprendizado supervisionado

​	No caso em que assumimos que $p(x|y)$ segue uma distribuição específica (gauss por exemplo), o método é chamado de **paramétrico**, pois é preciso estimar os parâmetros do modelo preditor. No caso dos métodos **não paramétricos**, não se utilizam parâmetros estatísticos para a modelagem da função. (WASKE, Bjorn et al, 2009)

### Alto e baixo viés

​	Quando há muitas variáveis na função hipótese $h_\theta$, corre-se o risco do modelo se ajustar bem aos exemplos de treinamento, porém, não é um bom preditor de novos exemplos, diz-se que é um problema de **alto viés**. O oposto também é problemático, se temos poucas variáveis, .corre-se o risco de acontecer **baixo-viés**. (COURSERA)

### Validação Cruzada

​	Validação cruzada é um método de reamostragem onde dividi-se o conjunto de dados repetidamente em conjuntos de treinamento, usados para ajustar o modelo, e conjuntos de teste, usados para verificar o desempenho das predições. A validação é feita utilizando medidas de análise de precisão, e o resultado é um modelo preditor com viés reduzido, ou seja, tem maior capacidade de generalizar novos dados (GEOCOMPR, JAMES).

## Aprendizado de Máquina e Sensoriamento remoto

​	Em sensoriamento remoto, algoritmos preditivos focam em classificações de cobertura da terra. Nesse contexto o algoritmo aprende a diferenciar diferentes tipos de padrões complexos, no caso, classes de cobertura da terra.  (WASKE, Bjorn et al, 2009).

​	Classificadores não paramétricos aceitam diversos tipos de dados de treinamento de entrada, além de não fazerem suposições sobre a distribuição dos dados, que são características desejáveis para o problema. (MAXWELL, 2018) 

​	Quando se fala em classificação de imagens e reconhecimento de padrões, podemos acrescentar mais um critério de divisão dos métodos. Se utilizarmos as informações espectrais de cada *pixel* de treinamento para encontrar regiões homogêneas, estamos descrevendo um classificador **pixel a pixel**. Outro caso, é quando se realiza um agrupamento de *pixels* por métodos de segmentação de imagens em grupos que serão unidades a serem classificadas, então é um classificador **por região**, também conhecido como OBIA, ou quando se fala em dados geográficos, GEOBIA. (MENESES, LU&WENG)

## Algoritmos

​	Dois algoritmos de classificação foram utilizados e testado neste trabalho: Máquina de Vetores de Suporte (MVS), ou *Support Vector Machine* e Floresta Aleatória (FA), ou *Random Forest*.

### Máquina de Vetores Suporte

​	Na classificação paramétrica, o objetivo é definir um espaço de características para cada classe. No caso da MVS (não paramétrica), o foco está apenas nos exemplos de treinamento que estão próximos do **limite de decisão** (*decision boundary*) ótimo que separa as classes. Estes exemplos definem os **vetores de suporte**.

​	O objetivo é achar o limite de decisão ótimo entre duas classes, maximizando a margem entre os vetores de suporte. Originalmente, a MVS foi feita para identificar um limite de decisão linear (definindo um *hyperplano*), porém, essa limitação foi resolvida projetando o espaço de características para uma dimensão maior. Essa projeção é feita com uma função denominada de **núcleo** (ou *kernel*). Em sensoriamento remoto, as funções de núcleo mais utilizadas são *Radial Basis Function* e também a polinomial.

### Florestas Aleatórias

​	O método de FA é baseado em Árvore de Decisão (AD). Uma AD é definida como cortes recursivos nos dados de entrada. As divisões são feitas repetidamente, criando novas ramificações (como um tronco de uma árvore), sendo que ao chegar em uma "ponta" (ou folhas), é definida uma classe. Uma AD é um conceito simples de se entender e visualizar, e também podem ser boas preditoras, porém, correm o risco de se ajustarem bem demais para um conjunto de treinamento, caindo no problema do alto viés.

​	As Florestas Aleatórias utilizam em conjunto um número definido de AD's. Uma classe será definida a partir do "voto" da maioria das árvores presentes na floresta. Essa abordagem supera o problema de alto viés de uma única AD, chegando assim mais perto de uma solução global.

​	Esse conceito é ainda ampliado: cada árvore é treinada com um único subconjunto de teste e variáveis, gerados aleatoriamente. Essa combinação significa que uma única árvore será menos precisa, porém, também estará menos correlacionada com todas as outras, tornando o conjunto mais confiável.

(MAXWELL)	

## Avaliação de Desempenho

​	Para verificar a acurácia após realizada a classificação, um método comumente empregado em sensoriamento remoto é o cálculo da matriz de erro (WENG), utilizada para comparação entre os dados de referência e os dados classificados. Alguns fatores que podem influenciar na acurácia podem ser: a complexidade do terreno; o algoritmo utilizado; número de classes; conjunto de dados que representa a verdade (MENESES), que podem ser obtidos por exemplo através de outras classificações ou validação em campo.

​	A partir da matriz de erro são calculados índices de validação. Um deles é a avaliação geral, calculado a partir da divisão entre a soma dos elementos da diagonal principal (elementos classificados corretamente) e a soma do total de pontos. Outro índice muito utilizado é o *kappa*, proposto por (LANDIS E KOCH, 1977) que varia de 0 até 1, onde: 0 – 0,2 = ruim; 0,2 – 0,4 = razoável; 0,4 – 0,6 = boa; 0,6 – 0,8 = muito boa; e 0,8 –1,0 = excelente (MENESES).

