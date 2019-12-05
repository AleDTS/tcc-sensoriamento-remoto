# Metodologia

# Ferramentas e Dados

## Linguagem R

​	R é uma linguagem e ambiente multiplataforma para análise estatística com ferramentas gráficas avançadas. A linguagem implementa o paradigma da programação funcional, bem como o da orientação a objetos. O projeto R é distribuído sob a Licença Pública Geral (GPL) do projeto GNU (SITE R). O GNU foi criado como uma reação aos *softwares* proprietários e de código fonte fechado, marcando o início do movimento do *software* livre, ou seja, programas de computador com código fonte aberto e que está disponível para que qualquer um o estude, copie, modifique e o redistribua. (TORRES, 2014). 

### Ambiente R

​		O desenvolvimento e crescimento da comunidade em torno do R se deu pela sua capacidade de integração com outros *softwares*, facilitando assim, por exemplo, a integração com diversas bibliotecas SIG. O uso da linguagem torna-se mais amigável com o Ambiente de Desenvolvimento Integrado (*IDE*) chamado *Rstudio*, que possui recursos como painéis de visualização interativos, acesso a documentação dos pacotes diretamente pela linha de comando ou painel, criação e manutenção de projetos, entre outros. (GEOCOMPR, EFFICIENT R) 

​	Através da linha de comando, é muito simples instalar um pacote ou então acessar sua documentação, que é um dos pontos fortes do R. Todos os pacotes estão armazenados em uma rede de servidores chamada CRAN, ou *Comprehensive R Archive Network*, onde a comunidade desenvolvedora mantém um padrão de documentação muito bem organizado. Para que um pacote esteja disponível no CRAN, é necessário por exemplo um manual com referências teóricas para cada método implementado, e geralmente possuem exemplos simples e intuitivos, que também podem ser acessados com facilidade pela linha de comando.

### Rmarkdown

​	*Markdown* é uma linguagem marcação simples cujo texto é convertido para o HTML (Linguagem de Marcação de Hipertexto). O *RMarkdown* é uma adaptação do *markdown* para o R que em conjunto com outros pacotes, pode ser facilmente convertida para formatos como PDF (*Portable Document Format*), arquivos de texto, HTML, apresentação de slides, entre outros. Sua importância está na divulgação de resultados de análises que poderão ser facilmente reproduzidas por outras pessoas.

​	Com o *RMarkdown* é possível escrever texto no formato LaTeX, adicionar trechos de código (*chunks*) que por sua vez imprimirão seu resultado, seja ele um gráfico, uma tabela ou texto. De maneira integrada ao RStudio, os *chunks* também possuem suporte a outras linguagens como Python.	

### Bibliotecas

​	Para a realização deste trabalho, foram utilizadas, dentro do ambiente de desenvolvimento RStudio, bibliotecas quem fazem a *interface* com a GDAL (*Geospatial Data Abstraction Layer*), uma biblioteca tradutora para dados geoespaciais *raster* e vetoriais que é utilizada por muitos *software* de SIG.

## Google Earth Engine

​	O *Google Earth Engine* (GEE) é uma plataforma de processamento geoespacial baseada em nuvem, feito principalmente para análises de dados ambientais em escala planetária. O acesso a plataforma foi utilizado para a obtenção e processamento de dados de treinamento.

## Iniciativas

### Mapbiomas

> O Projeto de Mapeamento Anual da Cobertura e Uso do Solo do Brasil é uma iniciativa que envolve uma rede colaborativa com especialistas nos biomas, usos da terra, sensoriamento remoto, SIG e ciência da computação que utiliza processamento em nuvem e classificadores automatizados desenvolvidos e operados a partir da plataforma Google Earth Engine para gerar uma série histórica de mapas anuais de cobertura e uso da terra 
> do Brasil.

​	O Mapbiomas é uma plataforma aberta e colaborativa com uma metodologia de baixo custo que pode ser aplicada em diversos contextos. Grande parte deste trabalho teve essa iniciativa como referência, e também, parte dos dados que foram utilizados no modelo de classificação foram obtidos da Coleção 3.1 do projeto, através do próprio *site* e também pela plataforma do GEE. Os detalhes estão explicados no próximo capítulo.

​	Além do mapeamento anual dos biomas brasileiros, também a outras iniciativas como o Mapbiomas Alerta:

> MapBiomas Alerta é um sistema de validação e refinamento de alertas de desmatamento, degradação e regeneração de vegetação nativa com imagens de alta resolução. Esta versão atual é dedicada exclusivamente ao tema de desmatamento em todos os biomas brasileiros e se expandirá para os demais temas ao longo dos próximos dois anos.

### Outras iniciativas

​	Pensando em monitoramento do uso e cobertura da terra, por meio de análise de imagens de satélite num contexto Brasileiro, é importante destacar outras iniciativas. 

​	O Instituto do Homem e Meio Ambiente da Amazônia (IMAZON) é um instituto que possui o programa de Monitoramento da Amazônia tem por objetivo monitorar e detectar desmatamento, a exploração madeireira e outras formas de pressão humana. (https://imazon.org.br/programas/monitoramento-da-amazonia/)

​	O Instituto Nacional de Pesquisas Espaciais (INPE) possui um papel fundamental e histórico para o uso de SR em escala nacional. Foi pioneiro no desenvolvimento e formação nas áreas de interpretação de imagens e processamento digital (MENESES). 

> O sistema PRODES do INPE fornece uma série histórica anual e ininterrupta do corte raso (áreas totalmente desmatadas) na Amazônia  desde 1988, permitindo análises comparativas. Além disso, o INPE mantém  desde 2004 o DETER, um sistema de apoio à fiscalização que produz  diariamente alertas sobre corte raso e também de áreas em processo de  degradação florestal (exploração de madeira, mineração, queimadas e  outras). Esses alertas são enviados automaticamente ao Ibama, para o  planejamento das ações de fiscalização. As informações ficam ainda  disponíveis na internet para as Secretarias Estaduais de Meio Ambiente, bem como para toda a sociedade. (http://www.inpe.br/noticias/noticia.php?Cod_Noticia=5179)

>  	Em 2018, o INPE expandiu o monitoramento para o Cerrado. Somados aos  dados produzidos para a Amazônia, o Instituto garante uma base de  informações sobre o desmatamento em áreas de vegetação natural de 73% do  território brasileiro.
>
>  A série histórica de dados orbitais sobre desmatamento norteia vários  estudos científicos e políticas públicas, produzindo informação para  toda a sociedade interessada em sustentabilidade. O INPE também monitora  queimadas e a qualidade do ar, entre outros índices importantes na área  de clima e meio ambiente. http://www.inpe.br/noticias/noticia.php?Cod_Noticia=5124

## Satélites

​	Num contexto de Obervação da Terra (OT), a fim de monitorar os recursos terrestres, há uma grande quantidade de programas de satélites que orbitam o globo com a tarefa de fazer o imageamento da superfície terrestre. O próprio INPE realiza a distribuição de imagens geradas por diversos desses programas através da sessão de Divisão de Geração de Imagens (DGI), como: o Landsat e TERRA, dos Estados Unidos; o RESOURCESAT, da Índia; o RapidEye da Alemanhã; bem como o AQUA, uma parceria entre Brasil e Japão; e ainda o CBERS, parceria entre Brasil e China que tem como objetivo o monitoramento de biomas, agricultura, crescimento urbano, gerenciamento hídrico e de desastres naturais. (http://www.dgi.inpe.br/)

​	Vale o destaque para o Landsat, programa de origem norte americana gerenciado pela Administração Nacional da Aeronáutica e Espaço (NASA) e o Serviço Geológico dos Estados Unidos (USGS), que realizou uma série de lançamentos desde a década de 1970. Em um contexto, vindo da década anterior, da corrida espacial e as primeiras imagens da Terra capturadas por satélites, a história desse programa se confunde com o desenvolvimento das técnicas de SR e interpretação de imagens digitais. Também há o programa de OT da União Europeia, o Copernicus, desenvolvido em parceria com a Agência Espacial Europeia (ESA), que possui a missão dos satélites Sentinel, com características semelhantes as do Landsat (ambos possuem resolução espacial média, por exemplo).

​	É importante destacar também o advento dos nano e microsatélites, que geralmente carregam sensores com uma resolução espacial maior e menor custo de lançamento, porém, com menor resolução radiométrica. Lembrando que cada característica dos sensores possuem diferentes fins de aplicações. 

​	Os dados dos satélites do programa *Landsat*  e *Sentinel* possuem acesso aberto desde 2008 e 2013, respectivamente. Estes são marcos importantes num contexto de Observação da Terra, gerando demanda para a computação em nuvem, que resolvem problema de processamento e armazenamento, enquanto o usuário pode focar no desenvolvimento do algoritmo. ([nature](https://www.nature.com/news/satellites-make-earth-observations-open-access-1.15804))

# Etapas

​	De acordo com (LU, WENG), o sucesso da classificação de dados de SR em um mapa temático depende de fatores como: complexidade da área de estudo, seleção dos dados, abordagens de processamento de imagens e seleção de sistema de classificação apropriado. Com base nos artigos de (LU, WENG) e (MAXWELL), foi elaborado o seguinte processo descrito no fluxograma a seguir

FLUXOGRAMA DAS ETAPAS

