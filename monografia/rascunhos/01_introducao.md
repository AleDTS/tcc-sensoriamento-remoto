# Introdução

​	Dados gerados a partir da Observação da Terra são ricas fontes para se descobrir como a Terra está mudando. Imagens obtidas a partir de satélites que orbitam o globo possibilitam uma visão de conjunto multitemporal da superfície terrestre, o que possibilita o estudo e monitoramento dos impactos causados por fenômenos naturais e antrópicos. Portanto, o desenvolvimento de técnicas e abordagens que viabilizam a análise desses dados é essencial.

>"Sensoriamento  remoto  é  uma  técnica  de  obtenção  de  imagens  dos  objetos  da  superfície  terrestre  sem  que  haja  um  contato  físico  de  qualquer  espécie entre o sensor e o objeto." (MENESES)

​	As mudanças na ocupação do solo afetam o clima global, logo torna-se relevante o devido monitoramento do uso e ocupação do solo em escala global ([nature](https://www.nature.com/news/satellites-make-earth-observations-open-access-1.15804)). Isso é possível através da **coleta**, **distribuição** e **análise** de dados obtidos por Sensoriamento Remoto (SR). Duas definições para cobertura e uso da terra, respectivamente, são:

> "cobertura (bio)física observada na superfície da terra" (FAO, 2010)

> "arranjos, atividades e insumos que as pessoas empreendem em um certo tipo de cobertura da terra para produzir, alterar ou manter" (FAO, 2010)

​	Pesquisas na área de SR envolvendo métodos digitais de classificação de imagens chamam a atenção porque seus resultados são a base para muitas aplicações ambientais e socioeconômicas (LU, WENG 2007). Além disso, metodologias de aprendizado de máquina têm bons resultados em aplicações reais, especialmente para tarefas de classificação e regressão, uma vez que não é necessário um conhecimento a priori sobre o modelo de distribuição dos dados disponíveis nem o relacionamento entre as variáveis independentes precisam ser assumidos. Essas são propriedades desejáveis para o sucesso desses métodos para a análise de imagens de sensoriamento remoto.  (WASKE, Bjorn et al, 2009)

​	Hoje em dia, há uma alta demanda para aplicações de alta performance em geoprocessamento, num contexto onde muitos dados georreferenciados são produzidos a todo instante, a exemplo dos *smartphones* que possuem GPS e são amplamente utilizados. Além disso, SR para monitoramento é uma tarefa que exige um muito processamento e espaço em disco disponível (GEOCOMPR).

​	A solução atualmente é a computação e armazenamento em aplicações baseadas em nuvem, ou seja, serviços disponibilizados por estruturas capazes de lidar com uma grande quantidade de dados de maneira eficiente. Com isso, a coleta e distribuição de dados gerados por sensoriamento remoto se torna muito mais viável, possibilitando o monitoramento em escala global. (EARTH OBSERVATION AND OPEN SCIENCE)

## Objetivos

### Objetivos Gerais

​	Levando em consideração a importância da aplicação de métodos analíticos para monitoramento da cobertura terrestre, bem como os meios que tornam essa tarefa viável, estre trabalho teve como objetivo a aplicação e estudo de um processo de construção e comparação modelos preditivos, a fim de realizar a classificação de novos dados.

​	O desenvolvimento foi realizado a partir da coleta de dados da iniciativa MapBiomas, e também imagens do sensor *MSI* do satélite *Sentinel-2*, ambos disponíveis gratuitamente. Os ambientes utilizados foram a *IDE* *RStudio* da linguagem R, bem como plataforma do *Google Earth Engine*. A área de estudo foi a região do município de Bauru - SP. Os métodos de classificação de imagens aplicados foram: Florestas Aleatórias (ou *Random Forests*) e Máquina de Vetores Suporte (ou *Support Vector Machines*) com duas funções de núcleo diferentes, uma linear e outra radial.

### Objetivos Específicos

- Revisão teórica: organizar um estudo dos conceitos chave acerca dos temas que envolvem o trabalho, ou seja, sensoriamento remoto, aprendizado de máquina, classificação de imagens. 
- Análise e comparação: discussão dos métodos e dados a serem coletados, bem como apresentação das ferramentas utilizadas.
- Implementação: desenvolvimento do modelo e aplicação.
- Teste e validação dos resultados: realizar uma avaliação de precisão de classificação, a fim de comparar os modelos aplicados e discussão de resultados