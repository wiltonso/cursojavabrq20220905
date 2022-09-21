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
```