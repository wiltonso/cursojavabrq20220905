Como iniciar um container QUE AINDA NAO EXISTE

CRIAR/INICIAR UM CONTAINER (NOME SELECIONADO PELO DOCKER)
 docker run docker/getting-starteddocker run docker/getting-started

CRIAR/INICIAR UM CONTAINER COM NOME
 docker run --name hello-world docker/getting-started

 docker run --name hello-wilton -p 80:80  docker/getting-started

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



