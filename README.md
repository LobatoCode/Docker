# Docker

Site oficial do Docker:

https://www.docker.com/

As versões mais recentes do docker pedem o windows 10 pro pra cima. Mas existe o docker toolbox para versões anteriores:

https://github.com/docker-archive/toolbox/blob/master/docs/toolbox_install_windows.md

Comando no cmd para baixar o docker. Através do Winget (windows packge manager):

winget install -e --id Docker.DockerDesktop

Vídeo ensinando a instalar o docker:

https://www.youtube.com/watch?v=ZyBBv1JmnWQ

Documentação:

https://docs.docker.com/desktop/setup/install/windows-install/

Guia para rodar natural adabas em Containers:

[AN+Community+Edition+Guide.pdf](https://github.com/user-attachments/files/19146284/AN%2BCommunity%2BEdition%2BGuide.pdf)

## Criação de um Container para testes:

Abra o cmd e digite:

docker run -d -p 8080:80 docker/welcome-to-docker

No navegador digite localhost/8080

## Comandos básicos do Docker

docker ps: lista os containers em execução.<br>
docker ps -a: lista todos os containers (inclusive os parados).<br>
docker network create nome_network: cria uma network.<br>
docker network ls: lista as networks criadas.<br>
docker images: lista todas as imagens.<br>
docker stop <id ou nome do container>: para um container em execução.<br>
docker start <id ou nome do container>: inicia um container parado.<br>
docker rm <id ou nome do container>: remove um container.<br>
docker rmi nome_da_imagem: remove uma imagem.

## Comandos para criar network, imagens e containers que serão usados no Natural Adabas. Execute na ordem.

docker network create adabas_natural

docker run -d -e ACCEPT_EULA=Y -e ADABAS_DBID=12 -e "ADABAS_DB_CREATION=demodb" --network adabas_natural --name ADABAS-DB softwareag/adabas-ce:7.3.0

docker run -d -p 2700:2700 --network adabas_natural -e ACCEPT_EULA=Y --name natural-ce softwareag/natural-ce:9.3.2
