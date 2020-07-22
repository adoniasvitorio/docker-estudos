#### Listando Contêineres.

Eventualmente precisamos consultar ou inspecionar um ou mais conteineres. Nesse caso,
 podemos lista-los executando o 02 comandos.

1. Listando conteineres em execução.

```docker ps```.

2. Listando todos os contêineres. Em execução ou mesmo parados.

```docker ps -a``` ou ```docker ps -all```.  

Saida no Terminal

~~~
[adoniasvitorio@localhost basico]$ docker ps -a
CONTAINER ID        IMAGE                    COMMAND                  CREATED             STATUS                      PORTS               NAMES
6699a0df2edd        hello-world              "/hello"                 50 minutes ago      Exited (0) 16 minutes ago                       friendly_boyd
~~~
