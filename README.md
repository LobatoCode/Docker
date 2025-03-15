# Docker

Site oficial do Docker.<br>
Official Docker website.

https://www.docker.com/

As versões mais recentes do docker pedem o windows 10 pro pra cima. Mas existe o docker toolbox para versões anteriores.<br>
The latest versions of Docker require Windows 10 Pro or higher. However, there is Docker Toolbox for previous versions.

https://github.com/docker-archive/toolbox/blob/master/docs/toolbox_install_windows.md

Comando no cmd para baixar o docker usando Winget (windows packge manager).<br>
Command in cmd to download Docker using Winget (windows packge manager).

winget install -e --id Docker.DockerDesktop

Vídeo ensinando a instalar o docker.<br>
Video teaching how to install Docker.

https://www.youtube.com/watch?v=ZyBBv1JmnWQ

Documentação.<br>
Documentation.

https://docs.docker.com/desktop/setup/install/windows-install/

Guia para rodar natural adabas em Containers.<br>
Guide to run Natural Adabas in Containers.

[AN+Community+Edition+Guide.pdf](https://github.com/user-attachments/files/19146284/AN%2BCommunity%2BEdition%2BGuide.pdf)

## Criação de um Container para testes | Creating a Container for Testing

Abra o cmd e digite.<br>
Open cmd and type.

docker run -d -p 8080:80 docker/welcome-to-docker

No navegador, digite localhost/8080 <br>
In the browser, type localhost/8080

## Comandos básicos do Docker | Basic Docker Commands

docker ps: lista os containers em execução | lists the running containers <br>
docker ps -a: lista todos os containers (inclusive os parados) | lists all containers (including stopped ones) <br>
docker network create nome_network: cria uma network | creates a network <br>
docker network ls: lista as networks criadas | lists the created networks <br>
docker images: lista todas as imagens | lists all images <br>
docker stop <id ou nome do container>: para um container em execução | stops a running container <br>
docker start <id ou nome do container>: inicia um container parado | starts a stopped container <br>
docker rm <id ou nome do container>: remove um container | removes a container <br>
docker rmi nome_da_imagem: remove uma imagem | removes an image

## Comandos para criar network, imagens e containers que serão usados no Natural Adabas | Commands to create network, images, and containers that will be used in Natural Adabas

Execute na ordem | Execute in order

docker network create adabas_natural

docker run -d -e ACCEPT_EULA=Y -e ADABAS_DBID=12 -e "ADABAS_DB_CREATION=demodb" --network adabas_natural --name ADABAS-DB softwareag/adabas-ce:7.3.0

docker run -d -p 2700:2700 --network adabas_natural -e ACCEPT_EULA=Y --name natural-ce softwareag/natural-ce:9.3.2
