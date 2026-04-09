**Sumário**
	**Tags:** #Ferramentas 
	**Conteúdo:**
		youtube.com/watch?v=ntbpIfS44Gw - Conteúdo Básico em Vídeo.
		github.com/iam-veeramalla/Docker-Zero-to-Hero - Passo a Passo.
		medium.com/@viveksachdev1121/docker-from-zero-to-hero-663bdd337c1a - Referencia.
		[docs.docker.com](https://docs.docker.com/) - Documentação 

----

Imagine que você fez um sistema no seu computador para a sua empresa, e na hora de colocar em outra maquina não funciona, nesse cenário surgiu uma das falas da informática, *na minha maquina funciona*. Foi ai que o Docker entrou para ajudar e mudar esse cenário, criando um ambiente isolado em sua máquina, que contem todas as dependências necessárias para o funcionamento da sua aplicação, e que pode empacotar elas para funcionar em qualquer outra máquina que for colocado. Esse ambiente feito pelo Docker é chamado de **contêiner**. E é na plataforma do Docker que conseguimos usar os contêineres a partir de suas **imagens**, que funcionam como uma receita de bolo para criar um contêiner, a criação da imagem é chamada de **docker build**.

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



[^1]: É um formato de codificação de dados feito para ser lido por humanos, ele é usado em arquivos de configurações, em Dockers e também em arquivos de data.
