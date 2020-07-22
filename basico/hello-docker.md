#### Criando uma imagem docker.

```docker create hello-world```

O ID do nosso contêiner sera criado em forma de cadeia de caracteres parecida 
com:

>6699a0df2edd725f6ebb48703dab494704540aa07433d5e2aa4cce7d048b750b

#### Iniciando nosso Contêiner.

Não se preocupe, para executar nosso contêiner não ha nescessidade de informar
 todos estes digitos. Os Primeiros caracteres são mais que suficiente.

```docker start 6699a0df2edd```

Nesse ponto oce deve estar pensando. Nada aconteceu !!

fique calmo, vamos descobrir que seu conteier na esta executando. Digite o seguinte comando para fazer essa conulta:

```docker ps -a```

Uma saida semelhante a esta deve surgir em seu terminal.

~~~
[adoniasvitorio@localhost basico]$ docker ps -a
CONTAINER ID        IMAGE                    COMMAND                  CREATED             STATUS                      PORTS               NAMES
6699a0df2edd        hello-world              "/hello"                 9 minutes ago       Exited (0) 27 seconds ago                       friendly_boyd
~~~

Agora sim, seu primeiro contêiner foi criado e, esta funcionando muito bem.


Espera ! algo continua errado. Voce deve estar se perguntando,  Quando executei o
comando  ```docker run hello-world``` anteriormente as informações que 
 o terminal apresentou estavam diferentes. Parabéns !

Observou muito bem ! Vamos entender o que aconteceu.

Acontece que ao executar ```docker start 6699a0df2edd``` não estamos conectando
 nosso terminal ao fluxo de saida do contêiner.
 
Para não fugir do topico deste estudo vou deixar este
 [link](https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-i-o-redirection) pra que 
voce consulte este assunto com mais calma. 

Por hora vamos executar o comando novamente corrigindo esse ponto.

```docker start -a 6699a0df2edd```

```-a``` ou ```-attach``` neste caso serve para conectar nosso terminal ao fluxo de saida
 do contêiner.

Agora sim, se tudo correr bem devemos receber a mesma mensagem de anteriormente.

~~~
[adoniasvitorio@localhost basico]$ docker start -a 6699a0df2edd

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

[adoniasvitorio@localhost basico]$ 
~~~

#### Ponto de atenção.

Sempre que quisermos executar um contêiner que ainda não esteja em execução, podemos usar 
o comando ```start```. O comando ```run``` sempre ira criar um novo contêiner.

