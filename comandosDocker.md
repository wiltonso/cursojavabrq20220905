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

docker run -d --name=mysql-java -p 3306:3306 --env="MYSQL_ROOT_PASSWORD=root" -v ${PWD}/mysql-datadir:/var/lib/mysql    mysql

entrar no sql via terminal
docker exec -it mysql-java /bin/sh

Logar no DB
mysql -uroot -proot

 create database dbcorrentista;
 use dbcorrentista;

create table cuentas ( cd_contas int primary key auto_increment, nombre varchar(40) );

insert into cuentas (nombre) VALUES ('JUAN');

para sair do termnal SQL quit

dockerfile... sao as parametrização para levantar uma imagem docker
no geral quando criamos nossa imagem partimos de uma outra padrao.
subindo 
docker run --name nginx -p 80:80 nginx:latest

para listar as images disponiveis
docker images 
