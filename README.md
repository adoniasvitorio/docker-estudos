## Sobre o repositorio.

Este repositorio aborda conceitos e praticas de docker que adiquiri durante meus estudos com essa tecnologia.

As informações aqui escritas refletem minha didatica e entendimento do conteudo no momento dos estudos. Não significa que estão inteiramente corretas. Na verdade, fique a vontade para corrigir, alterar, sugerir ou adicionar qualquer informação que considerar relevante a este assunto.

>*Considere deixar sua contribuição para estudantes futuros*.

### Introdução ao Docker

Docker é uma plataforma de conteinerização de código aberto. Executando aplicações em um ambiente chamado de *contêiner*.

Contêiners são **parecidos** com maquinas virtuais porem, muito mais leves e que, podem executar a partir do kernel de seu Sistema Operacional. 

São considerados mais leves e dispensam a nescessidade de uma hypervisor. Com isso, ganhamos principalmente em flexibilidade e execução de varios contêineres simultaneamente. 

Cada contêiner gerado tem suas próprias Dependências e é isolado dos demais contêineres.

### Instalação 

Neste Repositorio voce encontrará um manual de instalação baseada no meu OS no momomento deste estudo (Fedora 32).

Para outros sistems Operacionais ou informações mais detalhadas sobre esta entapa, considere acompanhar a Documentação oficial.

1. Removendo Conflitos
~~~
sudo dnf remove docker-*
sudo dnf config-manager --disable docker-*
~~~
2. Ative CGroups antigos.
```
sudo grubby --update-kernel=ALL --args="systemd.unified_cgroup_hierarchy=0"
```

Interessado em saber mais sobre CGroups. [Consulte este link](https://docs.fedoraproject.org/en-US/Fedora/15/html/Resource_Management_Guide/ch01.html).

3. Permitindo acesso ao Firewall
~~~
sudo firewall-cmd --permanent --zone=trusted --add-interface=docker0
sudo firewall-cmd --permanent --zone=FedoraWorkstation --add-masquerade
~~~
4. Utilize Moby

>*Poupe-se de alguns transtornos no inicio de sua carreira com Docker (palavras minhas)*. 

[Moby](https://mobyproject.org/) é a versão de código aberto aceito pelo Docker. Está incluído no repositório principal do Fedora, o que facilita a instalação.

Isto instala o *moby-engine*, o *docker-compose*, *container* e outras bibliotecas relacionadas. 
```
sudo dnf install moby-engine docker-compose
```
Depois de instalado, você precisará habilitar o daemon em todo o sistema para executar o Docker.
```
sudo systemctl enable docker
```

5. Reinicie o computador e diga um **hello world** com Docker.
~~~
sudo systemctl reboot
sudo docker run hello-world
~~~

*Se tudo correr bem, uma imagem parecida com esta surgira em seu terminal*.

>adoniasvitorio@localhost ~]$ docker run hello-world
>
>Hello from Docker!
>This message shows that your installation appears to be working correctly.
>
>To generate this message, Docker took the following steps:
> 1. The Docker client contacted the Docker daemon.
> 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
>    (amd64)
> 3. The Docker daemon created a new container from that image which runs the
>    executable that produces the output you are currently reading.
> 4. The Docker daemon streamed that output to the Docker client, which sent it
>    to your terminal.
>
>To try something more ambitious, you can run an Ubuntu container with:
> $ docker run -it ubuntu bash
>
>Share images, automate workflows, and more with a free Docker ID:
> https://hub.docker.com/
>
>For more examples and ideas, visit:
> https://docs.docker.com/get-started/


6. Execute como Admin.
~~~
sudo groupadd docker
sudo usermod -aG docker $USER
~~~

>*Estes passos foram feitos durante a realização deste estudo*, baseado na documentação do [fedoramagazine.org](https://fedoramagazine.org/docker-and-fedora-32/)


### Um pouco sobre a arquitetura Docker

Docker utiliza arquitetura *client-server* que é separada em três componentes Principais.

 * **Docker Daemon:** Aplicativo de execução que fica em segundo plano ouvindo os comandos executados. Ele gerencia imagens, contêineres, redes e volumes.
 * **Docker Client:** Este é um CLI acessivel pelo docker. Este é responsavel por enviar os comandos executados para o *Docker Daemon*.
 * **API** API é responsavel por fazer a comunicação entre o daemon e o client, utiliza uma *API REST* sobre *UNIX Sockets* ou interfaces de rede.
 
 ### Imagens e Contêineres.
 
 **Imagens** São arquivos com instruções nescessarias para criar *contêineres*. Imagens podem ser Trocadas a partir do registro, podemos usar imagens criada por outras pessoas, e modifica-las adicionando novas instruções se assim desejar-mos.
 
 **Contêiner** são instancias executáveis de uma *imagem*. Ou seja, quando executamos a imagem *hello-world*, na verdade estamos criando um ambiente isolado para executar o programa incluído na imagem.

### Registries (Registros)
**Registries** estão para imagens Docker como o Github esta para nossos codigos. 

Um lugar publico padrão para armazenar estas imagens, podendo compartilhar fazer upload, obter copias, etc.

O [Docker Hub](https://hub.docker.com/) é o registro publico padrão para imagens Docker.


