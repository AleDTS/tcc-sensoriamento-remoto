# Insights - 28/08

- Selecionei inicialmente imagem de 2017 da região da cidade de Bauru do satélite Landsat 8
  - Para posterior validação com o mapbiomas
  - O 'quadrado' do landsat cobre bauru por completo (não precisei 'juntar' imagens e fazer correções)
- Onde vou selecionar dados para treinamento?
  - classes do mapbiomas para toda região do cerrado (bauru é predominantemente cerrado, artigo prof de bio)
- Objetivos do tcc
  - Testar e comparar algoritmos de aprendizado de máquina
    - Discussão de parâmetros, restrições do problema, análise de acurácia
  - Trabalhar com dados abertos e software livre

# Ideias 26/10

### Aprendizado estatístico

- Métodos de aprendizado estatístico como uma poderosa ferramenta para usos acadêmicos e não acadêmicos

  - Uso de softwares amplamente desenvolvidos e apoiados por comunidades facilitam a acessibilidade

    





- 
- 



- ## Observacao da terra

  ​	A área da Observação da Terra (EO) está mudando rapidamente com os avanços nas tecnologias digitais e de sensoriamento. A computação e armazenamento em nuvem levaram a grandes mudanças na coleta, distribuição e análise de dados remotos. Há uma grande disponibilidade desses dados sobre o estado do nosso planeta e as suas mudanças, possibilitando monitoramento em escala global. 

  ​	Além disso, a crescente mercantilização e comercialização do espaço - e também a queda dos custos de construção, lançamento e processamento de pequenos satélites - levou a entrada de novos atores na área, como startups e as grandes empresas de tecnologia. Com isso, temos hoje dados com maiores resoluções espaciais e temporais, levando a uma ainda maior compreensão do nosso planeta, com sensores inteligentes e interconectados.

  ​	Tal fluxo de dados oferece novas oportunidades tanto para cientistas entenderem melhor o Sistema Terrestre, como para empreendedores tranformarem *big data* em serviços de informação, trazendo novos desafios para áreas como analise de dados.

# [Make Earth observations open access](https://www.nature.com/news/satellites-make-earth-observations-open-access-1.15804)



Boa parte dos dados de satélite têm compatibilidade limitada, porque são controlados pelos objetivos diversos dos programas espaciais nacionais. Em alguns casos, os dados são restritos ou cobrados. 

 	Os programas *Landsat* do *United States Geological Survey* (USGS) e da NASA desde 2008, bem como o *Copernicus* (com destaque para os satélites da série *Sentinel*) desde 2013, liberaram para acesso aberto o catálogo de imagens, abrindo uma nova era da Oberservação da Terra.

​	Avanços na computação em nuvem distribuida, como o *NASA Earth Exchange*  (NEX) e o *Google Earth Engine* que podem lidar com alto volume de dados geoespaciais e de sensoriamento remoto, trazem facilidades para o usuário desenvolver seu algorítmo enquanto minimiza o problema de dados duplicados. 

​		Governos e a comunidade de sensoriamento remoto tem a tarefa fundamental de desenvolver uma estratégia unificada para o monitoramento da terra.

## Meio ambiente e Geotecnologias

​	As mudanças na ocupação do solo afetam o clima global, tornando assim essencial um devido monitoramento do uso e ocupação do solo, em escala global. Governos e a comunidade de SR têm um papel fundamental no desenvolvimento de uma estratégia unificada para o monitoramento da Terra.

- Observação da terra (OE): coleta e interpretação de informações sobre os recursos e comportamento do planeta



## Disponibilidade

- Computação e armazenamento em nuvem 
  
  - Coleta, distribuição e análise de dados remotos
- Aumento da disponibilidade dos dados possibilita monitoramento em escala global.

- Crescente mercantilização de dados espaciais mais a queda de custos de pequenos satélites levaram a entrada de novos atores (startups, grandes empresas de tecnologia ) e dados com maiores resoluções temporais e espaciais.

- 

- nuvem

  - Google Earth Engine e Google Cloud; Amazon aws; NASA earth exchange
  - Facilidade para usuários finais 
  - Minimiza problema de dados duplicados.

- Grande disponibilidade de dados remotos sobre o estado do nosso planeta e as suas mudanças, possibilitando monitoramento em escala global.

- Dados de satélites de diversos programas espaciais, empresas que muitas vezes são restritos

- Estratégias unificadas entre comunidade e governos são fundamentais.

- Landsat e Copernicus com acesso aberto: passo importante para a observação da terra

  

- Sistemas de informações geográficas (SIG): sistemas integrados para captura, armazenamento, manipulação, analise, representação de dados geográficos.

  - Evolução: processamento isolado -> formatos de arquivos -> bibliotecas -> cloud
  - Cloud tenta resolver problema de analise eficiente, mas é novamente isolado -> problemas de reprodutibilidade

## Reprodutibilidade

Reprodução -> acesso facilitado a recursos de hardware capazes de executar tarefas de geocomputação aliado ao acesso de bases públicas de dados (geocompr)



Em sensoriamento remoto, algoritmos preditivos focam em classificações de cobertura da terra  (WASKE, Bjorn et al, 2009), provendo importantes informações de entrada em diversos sistemas de monitoramento ambientais. Nesse contexto o algoritmo aprende a diferenciar diferentes tipos de padrões, no caso, classes de cobertura da terra.