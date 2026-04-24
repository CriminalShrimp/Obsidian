**Sumário**
	**Tags:** #Ferramentas 
	**Conteúdo:**
		youtube.com/watch?v=ntbpIfS44Gw - Conteúdo Básico em Vídeo.
		github.com/iam-veeramalla/Docker-Zero-to-Hero - Passo a Passo.
		medium.com/@viveksachdev1121/docker-from-zero-to-hero-663bdd337c1a - Referencia.
		[docs.docker.com](https://docs.docker.com/) - Documentação 

----

Imagine que você fez um sistema no seu computador para a sua empresa, e na hora de colocar em outra maquina não funciona, nesse cenário surgiu uma das falas da informática, *na minha maquina funciona*. Foi ai que o Docker entrou para ajudar e mudar esse cenário, criando um ambiente isolado em sua máquina, que contem todas as dependências necessárias para o funcionamento da sua aplicação, e que pode empacotar elas para funcionar em qualquer outra máquina que for colocado. Esse ambiente feito pelo Docker é chamado de <span style="color:rgb(255, 255, 0)">contêiner</span>. E é na plataforma do Docker que conseguimos usar os contêineres a partir de suas <span style="color:rgb(255, 255, 0)">imagens</span>, que funcionam como uma receita de bolo para criar um contêiner, a criação da imagem é chamada de **Docker Build**.

<figure style="text-align: center;">
  <img src="ProcessoDocker.png" style="margin: 0 auto;">
  <figcaption>Ciclo de um Docker</figcaption>
</figure>

Aqui vão algumas terminologias usadas com frequência quando estamos lidando com Docker:

- **Docker Daemon:** Também chamado de **dockerd**, é um serviço que faz o gerenciamento de imagens, contêineres, rede e volumes. Ele funciona como se fosse um servidor.

- **Docker Client:** É como os usuários de Docker interagem com o `dockerd`, isso ocorre via [[Abreviações#CLI = **C**ommand **L**ine **I**nterface é onde são realizados os comandos do sistema.|CLI]], mas também é possível fazer isso via interface gráfica usando o **Docker Desktop**.

- **Docker Registries:** Funciona como uma **biblioteca de imagens** de contêineres, e além disso ele é usado para gerenciar, armazenar e distribuir as imagens.

- **Docker Hub:** É um tipo de **mercado comunitário**, nele as pessoas postam imagens pré-montadas.

- **DockerFile:** Arquivo que contem o **passo a passo de como construir a imagem** do Docker.

- **Docker Compose:** Ferramenta para gerenciar e roda múltiplos contêiner a partir de um único arquivo [^1]YAML.

## Parte Avançada

### Docker File

Cada linha em um Docker File representa uma instrução no processo da criação de uma imagem. Os principais componentes crucias em um arquivo docker seriam composto por uma <span style="color:rgb(0, 176, 80)">imagem base</span> que é a base do que esta sendo feito, por exemplo se esta fazendo uma aplicação em Python, a base seria `python:3.9`. <span style="color:rgb(0, 176, 80)">Código</span> e <span style="color:rgb(0, 176, 80)">dependências</span> que garante que tudo rode de forma constante e correta. E as <span style="color:rgb(0, 176, 80)">configurações</span> e <span style="color:rgb(0, 176, 80)">comandos</span> vão garantir que os comandos sejam executados, as variáveis sejam setadas corretamente, entre outras configurações necessárias.

O Docker File contem instruções simples, e cada uma dessas instruções performa uma ação específica, a sintaxe em geral é a mostrada na primeira linha, e se repete ao longos das outras instruções:

```
INSTRUÇÃO argumentos

ADD # Adiciona arquivos ou diretorios ao contêiner.
ARG	# Usado para passar variáveis na hora de criar o build-time contêiner.
COPY # Copia os arquivos ou pastas do sistema para o contêiner.
CMD # Comando padrão que sera rodado toda vez que o contêiner iniciar.
ENTRYPOINT # Define um comando que fara com que o seu contêiner rode como um executável.
ENV	# Cria variáveis de ambiente.
EXPOSE # Porta que o contêiner estará "funcionando".
FROM # Imagem base.
HEALTHCHECK	# Check a container's health on startup.
LABEL	Add metadata to an image.
MAINTAINER	Specify the author of an image.
ONBUILD	Specify instructions for when the image is used in a build.
SHELL	Set the default shell of an image.
STOPSIGNAL	Specify the system call signal for exiting a container.
USER	Set user and group ID.
VOLUME	Create volume mounts.
RUN # Executa comandos, aqui atualiza e instala o nmap.
WORKDIR # Específica o diretório que o contêiner que será usado.

```

A seguir tem como exemplo de DockerFile com as explicações da ação de cada instrução.

```
# Imagem feita para fazer o reconhecimento de uma rede.

FROM ubuntu # Imagem base.
RUN apt-get update && apt-get install nmap -y # Executa comandos, aqui atualiza e instala o nmap.
ENTRYPOINT ["nmap"] #
CMD ["-h"] # Comando padrão que sera rodado toda vez que o contêiner iniciar.

```


### Comandos 

Aqui tem os comandos e seus parâmetros mais úteis.

docker ps <span style="color:rgb(65, 105, 255)">OPÇÕES</span> <span style="color:rgb(0, 176, 80)">PARAMETRO</span> - Lista os contêineres.
	<span style="color:rgb(65, 105, 255)">-a</span>, --all
		Mostra todos os contêineres rodando, roda padrão no comando.
	<span style="color:rgb(65, 105, 255)">-f</span>, --filter <span style="color:rgb(0, 176, 80)">PARAMETRO</span>
		Faz uma busca nos dockers por um campo específico, os <span style="color:rgb(0, 176, 80)">parâmetros</span> mais comum usados são `id`, `name`, `label`, `status`, `volume`, `network`, `publish/expose`.
	<span style="color:rgb(65, 105, 255)">--format</span> {{.CAMPO}}
		Realiza prints dos contêineres e dos campos que foram passados em um modelo "GO", é possível usar mais que um campo na hora de realizar a captura dos dados. Os campos mais úteis para usar com esse comando são **ID**, **Labels**, **Image**, **Names**, **Status**, **Ports**.
	<span style="color:rgb(65, 105, 255)">-s</span>, --size
		Mostra o espaço de disco usado pelos contêineres.

docker run <span style="color:rgb(65, 105, 255)">OPÇÕES</span> {IMAGE} <span style="color:rgb(0, 176, 80)">PARAMETRO</span> - Cria e roda contêineres.
	<span style="color:rgb(65, 105, 255)">-d</span>, --detach:
		Roda o contêiner em segundo plano e imprime o ID do mesmo.
	<span style="color:rgb(65, 105, 255)">-p</span>, --publish {PortaHost}:{PortaContainer} {IMAGE}: 
		Usado para mapear portas entre o host e os contêiners.
	<span style="color:rgb(65, 105, 255)">--name</span>: 
		Nomeia um contêiner.
	<span style="color:rgb(65, 105, 255)">--mount</span> {TYPE} {SOURCE} {DESTINATION}:
		Usado na criação e na manipulação de arquivos.
			TYPE: Normalmente variam entre `bind` que servem para pastas no computador, e `volume` para volumes gerenciados pelo Docker.
			SOURCE: Onde estão localizados os dados.
			DESTINATION: Local onde os dados irão ficar no contêiner.
	<span style="color:rgb(65, 105, 255)">-e</span>, --env: 
		Seta as variáveis de ambiente.
	<span style="color:rgb(65, 105, 255)">-it</span> -i, --interactive e -t, --tty: 
		Cria uma espécie de terminal para usar o contêiner.
	<span style="color:rgb(65, 105, 255)">--rm</span>: 
		Automaticamente remove o contêiner.
	<span style="color:rgb(65, 105, 255)">--network</span> {REDE} {IMAGEM}:
		Conecta o contêiner a uma rede.
	<span style="color:rgb(65, 105, 255)">-m</span>, --memory: 
		Define um limite de uso da [[Computador#Memória RAM|Memória RAM]].
	<span style="color:rgb(65, 105, 255)">--restart</span> <span style="color:rgb(0, 176, 80)">PARAMETRO</span>: 
		Política para realizar (ou não) o <span style="color:rgb(65, 105, 255)">reinício</span> do contêiner quando ele "sair". 
			Os parâmetros mais usados são <span style="color:rgb(0, 176, 80)">always</span> que reinicia sempre que o contêiner, e o <span style="color:rgb(0, 176, 80)">unless-stopped</span> que somente não reinicia quando o contêiner é parado de forma manual ou outra forma.

docker pull {IMAGE} - Realiza o download de uma imagem.

docker start {CONTAINER} - Inicializa um ou mais contêineres.

docker stop {CONTAINER}- Para um ou mais contêineres.

[^1]: É um formato de codificação de dados feito para ser lido por humanos, ele é usado em arquivos de configurações, em Dockers e também em arquivos de data.
