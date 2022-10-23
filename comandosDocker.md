Como iniciar um container QUE AINDA NAO EXISTE

CRIAR/INICIAR UM CONTAINER (NOME SELECIONADO PELO DOCKER)
 docker run docker/getting-starteddocker run docker/getting-started

CRIAR/INICIAR UM CONTAINER COM NOME
 docker run --name hello-world docker/getting-started

 docker run --name hello-world -p 80:80  docker/getting-started
 
 docker run --name hello-world -p 80:80 -p 8000:80 docker/getting-started

 EXECUTAR COMANDOS DENTRO DE UM CONTAINER O CONTAINER TEM QUE ESTAR EM EXECUCAO
  docker exec -it hello-world /bin/bash
  docker exec -it hello-worldpwd
   /bin/sh   (ESTE COMANDO NO POWER SHELLLS
  )


PARA VER OS CONTAINER QUE ESTAO RODANDO
 docker ps

 PARA PARAR UM CONTAINER
   docker stop (nome do container)
   docker stop suspicious_stonebraker

PARA INICIA UM  QUE JA EXISTE
   docker start (nome do container)
   docker start suspicious_stonebraker   

PARA REMOVER UM CONTAINER (ELE DEVE ESTAR PARADO)
   docker rm (nome do container)
   docker rm suspicious_stonebraker 


https://github.com/ffborelli/curso-brq-java-2022-09-05

https://github.com/ffborelli/curso-brq-java-2022-09-05/blob/docker/comandos-docker.md


caso tenha problema com git 
rm .git/index.lock

comandos linux
ls  - lista diretorio
cp - copia arquivo
cd - entrar numa pasta diretoro
pwd - mostrar diretorio
cd .. - volta um diretorio
cd /usr/share/nginx/html
cd \ volta para o rais
mkdir - cria uma pasta
touch nome.arq - cria um arquivo
exit - sai do linux e volta para usa maquina

# dentro do container, iremos criar uma pasta

```
    mkdir pasta1
```

Para sair do container, digite:         exit

# Removendo o container para verificar o que acontece com o seu conteúdo

```
    docker stop hello-word
    docker rm hello-word
```

# Subindo um novo container da mesma imagem

```
    docker run --name hello-world -p 80:80 -p 8000:80  docker/getting-started
    docker exec -it hello-world /bin/sh
```

# Como podemos fazer para ao deletar um container, não perdermos dados do mesmo?

Resp: usando o conceito de volume

```
    docker run -v PASTA_DO_HOSPEDEIRO:PASTA_DO_CONTAINER

    docker rm hello-world
    
    docker run --name hello-world -p 80:80 -p 8000:80 -v ${PWD}/meu-volume:/meu-volume-container docker/getting-started

     docker run --name hello-wilton -p 81:80 -p 8001:80 -v ${PWD}/meu-volwil:/meu-volwil-container docker/getting-started
```

docker run -d --name=mysql-java3 -p 3307:3306 --env="MYSQL_ROOT_PASSWORD=root" -v ${PWD}/mysql-datadir:/var/lib/mysql    mysql

entrar no sql via terminal
docker exec -it mysql-java3 /bin/sh


Logar no DB
mysql -uroot -proot

 create database dbcorrentista;
 create database dbwilton;
 use dbcorrentista;

create table cuentas ( cd_contas int primary key auto_increment, 
nombre varchar(40) );

insert into cuentas (nombre) VALUES ('JUAN');

use dbwilton;
create table usuario (usuid int primary key auto_increment, 
                      usunome varchar(40),
                      usuemail varchar(30));
insert into usuario (usunome, usuemail ) VALUES ('Wilton', 'wil@gmail.com');
insert into usuario (usunome, usuemail ) VALUES ('Angela', 'ang@gmail.com');
create table professor (proid int primary key auto_increment, 
                      pronome varchar(40),
                      proemail varchar(30));


para sair do termnal SQL quit

dockerfile... sao as parametrização para levantar uma imagem docker
no geral quando criamos nossa imagem partimos de uma outra padrao.
subindo 
docker run --name nginx -p 80:80 nginx:latest

para listar as images disponiveis
docker images 

subir uma image criada por nos
docker run --name brq-nginx-container -p 90:80 brq-nginx:latest

conectar ao db2 dbwever
docker run -d --name=mysql-java2 -p 3306:3307 --env="MYSQL_ROOT_PASSWORD=root"  mysql
server host: localhost:3306?allowPublicKeyRetrieval=true&useSSL=False

localhost:3306?allowPublicKeyRetrieval=true&useSSL=False

Docker fica olhando a pasta user.. criar a pasta dentro usuario
Na pasta de projeto criar arquivos:
- www - (nesta pasta criar dados projeto)
- dockerfile
Configuracoes.
Criar arquivo dockerfile (sem extensao)
dockerfile:
FROM php:7.4.apache (imagem a ser copiada)
RUN docker-php-ext-install pdo pdo-mysql (extensoes necessadrias)
COPY WWW/ /var/www/html

Cria arquivo:
docker-compose.yml
version: "3"

services:
    www:
        build: .
        restart: always
        ports:
            - '8000':80
        volumes:
            - ./www:/var/www/htm
        networks:
            - default
    db: 
        image: mysql:5.7
        restart: always
        ports:
            - '3306:3306'
        environment: 
            MYSQL_DATABASE: meudb
            MYSQL_USER: wilton
            MYSQL_PASSWORD: 1234
            MYSQL_ROOT_PASSWORD: root
        volumes:
            -db_data:/var/lib/mysql
        networks:
            - default
volumes:
    db_data:


para rodar o projeto
docker-compose up -d (sob e libera o terminal para uso)
docker machine ip (para ver os ip dos )
docker container ls (ver o que está rodando)
docker-compose stop
docker-compose down (deleta o container deixando os dados)
docker-compose down --volume  (deleta tudo incluindo os dados)