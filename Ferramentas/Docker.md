**Sumário**
	**Tags:** #Ferramentas 
	**Conteúdo:**
		**Docker:**
			youtube.com/watch?v=ntbpIfS44Gw - Conteúdo Básico em Vídeo.
			github.com/iam-veeramalla/Docker-Zero-to-Hero - Passo a Passo.
			medium.com/@viveksachdev1121/docker-from-zero-to-hero-663bdd337c1a - Referencia.
			[docs.docker.com](https://docs.docker.com/) - Documentação.
			kubernetes.io/docs/home/ - Documentação Kubernetes.
		**Kubernetes:**
			kubernetes.io/docs/home/ - Documentação.
			youtube.com/watch?v=z3hOWY46OMQ - Vídeo Explicativo.
			
----

Imagine que você fez um sistema no seu computador para a sua empresa, e na hora de colocar em outra maquina não funciona, nesse cenário surgiu uma das falas da informática, *na minha maquina funciona*. Foi ai que o Docker entrou para ajudar e mudar esse cenário, criando um ambiente isolado em sua máquina, que contem todas as dependências necessárias para o funcionamento da sua aplicação, e que pode empacotar elas para funcionar em qualquer outra máquina que for colocado. Esse ambiente feito pelo Docker é chamado de <span style="color:rgb(255, 255, 0)">contêiner</span>. Quando pensamos em contêiner podemos  imaginar algo como um ambiente isolado, leve e padronizado. E é na plataforma do Docker que conseguimos usar os contêineres a partir de suas <span style="color:rgb(255, 255, 0)">imagens</span>, que funcionam como uma receita de bolo para criar um contêiner, a criação da imagem é chamada de **Docker Build**. 

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

**Docker x Maquina Virtual** - A grande diferença entre esses dois é seu uso de recursos, em poucas palavras e de forma simples, uma maquina virtual instala todo um sistema operacional para ser usado, em quando o Docker compartilha o [[Kernel]] da maquina e virtualiza somente o espaço do usuário, usando menos recurso computacional quando comparado com uma maquina virtual.
## Parte Avançada

### Docker File

Cada linha em um Docker File representa uma instrução no processo da criação de uma imagem. Os principais componentes crucias em um arquivo docker seriam composto por uma <span style="color:rgb(0, 176, 80)">imagem base</span> que é a base do que esta sendo feito, por exemplo se esta fazendo uma aplicação em Python, a base seria `python:3.9`. <span style="color:rgb(0, 176, 80)">Código</span> e <span style="color:rgb(0, 176, 80)">dependências</span> que garante que tudo rode de forma constante e correta. E as <span style="color:rgb(0, 176, 80)">configurações</span> e <span style="color:rgb(0, 176, 80)">comandos</span> vão garantir que os comandos sejam executados, as variáveis sejam setadas corretamente, entre outras configurações necessárias.

O Docker File contem instruções simples, e cada uma dessas instruções performa uma ação específica, a sintaxe em geral é **`INTRUÇÃO argumentos`**, ela se repete ao longos das outras instruções.

```
ADD # Adiciona arquivos ou diretorios ao contêiner.
ARG	# Usado para passar variáveis na hora de criar o build-time contêiner.
COPY # Copia os arquivos ou pastas do sistema para o contêiner.
CMD # Comando padrão que sera rodado toda vez que o contêiner iniciar.
ENTRYPOINT # Define um comando que fará com que o seu contêiner rode como um executável.
ENV	# Cria variáveis de ambiente.
EXPOSE # Porta que o contêiner estará "funcionando".
FROM # Imagem base.
HEALTHCHECK	# Mostra como verificar se o contêiner está funcionando via teste.
LABEL # Usado para adicionar metadados a imagem.
MAINTAINER # Cria um campo com a informação do autor da imagem.
ONBUILD	# Permite criar instruções especificas na hora da criação do contêiner.
RUN # Executa comandos, aqui atualiza e instala o nmap.
SHELL # Permite alterar o terminal, no Windows como exemplo de cmd para shellpower.
STOPSIGNAL	# Específica um sinal para que o contêiner encerre.
USER # Determina um usuário na etapa desejada.
VOLUME	# Criar um volume de disco no contêiner.
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

# Kubernetes

Para automação de implantação, escalonamento e gerenciamento de aplicações em contêineres. Quando se tem apenas um contêiner para gerenciar é fácil, mas em um cenário onde existam vários se tornar muito difícil cuidar de todos, é ai que o **Kubernetes** ou **K8s** (do grego piloto ou timoneiro) entra, ele é uma plataforma de código aberto que orquestra os contêineres, em outras palavras, ele realiza mudanças e melhorias em suas aplicações, se algo da errado durante isso ele mesmo volta a versão e reinicia contêineres que falharam, entre outras coisas que facilitam a vida de quem gerência contêineres. Ele realiza esse gerenciamento através de <span style="color:rgb(255, 255, 0)"><b>Pods</b></span>, e nesse pode é onde temos o contêiner, sendo possível colocar mais que um contêiner em um Pod (mas é um uso especifico). A criação de Pods é feita em YAML assim como o DockFile, mas não criamos isso de formar manual, ao invés disso usamos os <span style="color:rgb(255, 255, 0)">Workloads</span> (ou **Cargas de Trabalho**), que é uma aplicação do Kubernetes, e usando os **Recursos de Worklaod**, e com esses recursos como `replicaSet`, `deployment`, 

## Parte Avançada

### Comandos 

A sintaxe dos comandos segue um padrão do Docker com o serviço sendo usado, e o comando. 

<p style="text-align:center;">kubectl {<span style="color:rgb(65, 105, 255)">command</span>} {<span style="color:rgb(0, 176, 80)">TYPE</span>} {<span style="color:rgb(206, 0, 86)">NAME</span>} {<span style="color:rgb(112, 48, 160)">flags</span>} </p>

<span style="color:rgb(65, 105, 255)">Command </span>específica a operação que será feita, como `create`<span style="color:rgb(65, 105, 255)">,</span> `get`<span style="color:rgb(65, 105, 255)">,</span> `delete`<span style="color:rgb(65, 105, 255)">.</span> O <span style="color:rgb(0, 176, 80)">TYPE</span> é um recurso do comando que pode ser usado. o <span style="color:rgb(206, 0, 86)">NAME</span> é usado para especificar/identificar por exemplo um arquivo que será usado junto de um comando. E por fim as <span style="color:rgb(112, 48, 160)">flags</span> são opcionais, podem especificar um servidor ou ate mudar a saída de um comando. 

[^1]: É um formato de codificação de dados feito para ser lido por humanos, ele é usado em arquivos de configurações, em Dockers e também em arquivos de data.
