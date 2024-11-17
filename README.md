# Detecção de Phishing com Machine Learning  
### Integrantes
Eric Akio Uchiyamada                  <br/>RA: 10395287<br/><br/>
Lucas Goulart de Farias Meres         <br/>RA: 10395777<br/><br/>
Oliver Kieran Galvão McCormack        <br/>RA: 10395672<br/><br/>
Pedro Loureiro Morone Branco Volpe    <br/>RA: 10395922<br/><br/>
Renan Tagliaferro                     <br/>RA: 10395211<br/><br/>
  
# Visão Geral

Este projeto explora a utilização de algoritmos de machine learning para a detecção automatizada de sites de phishing, com base em características extraídas de URLs e conteúdo das páginas. O estudo compara os desempenhos de três algoritmos: Regressão Logística, K-Nearest Neighbors (KNN) e Random Forest, usando um dataset que contém 5.780 amostras, sendo 578 de sites phishing e 5.000 de sites legítimos. 
  
# Datasets  
Para o projeto coletamos dados do site Zenodo (Link: https://zenodo.org/records/8041387 ). Nele são apresentados diveros datasets separados em phishing e não phishing (legitimos).
Nós análisamos e selecionamos dois datasets, um com 5000 casos de phishing e outro com 5000 casos legitimos, ambos com as mesmas colunas (valores).  
Os datasets baixados foram o *not-phishing.csv* e *phishing.csv*

O tratamento dos dados está descrito no artigo.  
  
# Algoritmos Utilizados  
  
Regressão Logística: Modelo simples e interpretável para classificação binária.  
K-Nearest Neighbors (KNN): Algoritmo baseado em instâncias que classifica com base na proximidade de vizinhos.  
Random Forest: Modelo de ensemble que utiliza múltiplas árvores de decisão para melhorar a precisão.  

# Resultados  
  
KNN e Regressão Logística tiveram boa acurácia para sites legítimos, mas dificuldades em identificar phishing, com altos falsos negativos.  
Random Forest teve melhor desempenho na detecção de phishing, com menos falsos negativos, mas mais falsos positivos.  
  
# Conclusão  
   
O modelo Random Forest é o mais eficaz para detectar phishing, embora com um custo maior de falsos positivos, o que é aceitável para segurança, pois falsos negativos são mais prejudiciais.   

# Informações Adicionais 
Mais detalhes sobre o projeto estão no artigo "Detecção de Sites Phishing com Machine Learning_ Uma Abordagem Baseada em Análise de Dados de Sites Autênticos e Maliciosos".  
  
Também disponibilizamos um .ipynb, com os codigos organizados para melhor visualização das informações, sendo uma versão extra sobre os códigos presentes no Docker do projeto.  

# Executar Docker
## Opção 1: Obter imagem pelo Docker Hub
### a. Instale o Docker (se ainda não estiver instalado):
Siga as instruções de instalação para o Docker de acordo com o sistema operacional: [Docker](https://www.docker.com/products/docker-desktop/) 
### b. Faça login no Docker Hub
Abra o terminal e digite:
```bash
docker login
``` 
Insira seu nome de usuário e senha do Docker Hub. Se o contêiner for público, essa etapa pode ser opcional.
### c. Baixe a imagem do contêiner do Docker Hub:
```bash
docker pull eriaki/detect-phishing:latest
```
### d. Prepare o arquivo .csv com os dados da predição
**Atenção**: o arquivo .csv deve ter um formato específico para a predição ser executada normalmente. <br/>
O arquivo .csv deve ter as colunas: `brands`, `features.html`, `whois_domain_age`, `remote_ip_address`, `domain`, `whois_registrar_url`, `url`, `assets_downloaded` e `is_phishing`. <br/>
Recomenda-se utilizar um dataset alterado do site do Zenodo (Link: https://zenodo.org/records/8041387).
### e. Execute o contêiner
```bash
docker run -p 8501:8501 eriaki/detect-phishing
```
### f. Abra localhost no navegador
Pesquise por http://localhost:8501/ no seu navegador de preferência
### g. Insira o arquivo .csv para a previsão
Um campo para inserir arquivos estará disponível. Insira o arquivo .csv no campo. <br/>
Com isso, os modelos preverão baseado no arquivo .csv fornecido.
## Opção 2: Obter imagem pela pasta Docker
### a. Instale o Docker (se ainda não estiver instalado):
Siga as instruções de instalação para o Docker de acordo com o sistema operacional: [Docker](https://www.docker.com/products/docker-desktop/) 
### b. Baixe a pasta Docker presente neste repositório
### c. Abra o terminal dentro da pasta Docker
### d. Faça build do Docker
Antes verifique se o Docker foi isntalado com:
```bash
docker --version
```
Se ele foi instalado, a versão dele irá aparecer. <br/>
Depois, faça a build da imagem:
```bash
docker build -t streamlit-app .
```
Este processo irá demorar um tempo.
### e. Execute a imagem
```bash
docker run -p 8501:8501 streamlit-app
```
### f. Abra localhost no navegador
Pesquise por http://localhost:8501/ no seu navegador de preferência.
### g. Insira o arquivo .csv para a previsão
Um campo para inserir arquivos estará disponível. Insira o arquivo .csv no campo. <br/>
Com isso, os modelos preverão baseado no arquivo .csv fornecido.
