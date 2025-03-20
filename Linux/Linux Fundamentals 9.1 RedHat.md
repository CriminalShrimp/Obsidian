Tags: #CLI #Linux
# Introdução
Distribuições Linux são sistemas operacionais feito em cima de um [[Kernel#^b8a742|Kernel]] Linux, essas distribuições são de código aberto, o que significa que são disponibilizadas gratuitamente para todos e além disso tem os requisitos para rodar são mínimos. Dentre as distros ( uma abreviação de Distributions) seria <span style="color:rgb(161, 79, 140)">CentOS</span>, <span style="color:rgb(65, 105, 255)">Fedora</span>, <span style="color:rgb(255, 165, 0)">Ubuntu</span> e <span style="color:rgb(206, 0, 86)">Debian</span>. Algumas dessas distros podem possuir interface gráfica, porém todas suas funções são feitas pela [[Abreviações#CLI = Command Line Interface é onde são realizados os comandos|command line interface]] mais conhecida como [[CLI]].
 ![[LoginInterfaceGrafica.webp| center]]
*<p style="text-align:center;"> Aqui por exemplo é um login feito via interface gráfica</p>

![[LoginCLI.webp| center]]
*<p style="text-align:center;"> Já aqui é um login via CLI</p>

Nos sistemas existe o usuário root que seria a conta que tem a permissão de administrador, o que seria a maior permissão possível de ter em um sistema, com ela é possível fazer qualquer modificação sem que o sistema interfira.

# Manipulação de Pastas e Arquivos
Tags: #Dica
## Arquivos

Uma frase muito conhecida que se refere a Linux é "no Linux tudo é um arquivo" sejam as informações sobre o hardware do dispositivo, bem como as próprias configurações do kernel, são todas armazenadas em arquivos especiais que residem em diretórios virtuais, os código de estados  0 é o padrão de entrada , 1 é o padrão de saída  e 2 se referre a um erro. Um dos comandos para mexer em arquivos é o **cat** que um uma abreviação de *concatenate* (concatenar), para ler um arquivo bastar escrever **cat arquivo.txt**, duas <span style="color:rgb(255, 255, 0)">dica</span> muito interessante é que para passar outputs direto para um aquivo pode se usar output <span style="color:rgb(255, 255, 0)">></span> arquivo.txt, se é um arquivo que você somente queira adicionar mais linha então use o <span style="color:rgb(255, 255, 0)">>></span>, e a outra seria usar *pipelines* que seria essa barra na vertical  <span style="color:rgb(255, 255, 0)">| </span>, ela faz com que o resultado de um comando seja o *input* de outro. Um comando muito útil para achar arquivos e pastas é o [[CLI#find |find]], já para procurar palavras em textos é o <span style="color:rgb(255, 255, 0)">grep</span>.

Para criar um arquivo existe diversas maneiras um exemplo básico seria com **`touch arquivo.extensao`**.

Para realizar a copia de um arquivo usamos **`cp arquivo.extensao Pasta`**.

Para mudar um arquivo de lugar basta colocar `mv` o nome do arquivo sua extensão  e o destino **`mv arquivo.extensao Pasta`**, o comando `mv` também é usado para mudar nome de arquivos basta colocar **`mv NomeAntigo.extensao NomeNovo.extensao`**.

E para deletar arquivos usamos o **`rm`** e em seguida o nome do arquivo e sua extensão, **`rm arquivo.extensao`**.
# Arquivos Comprimidos

Para criar um arquivo comprimido `.tar` basta usar o comando `tar`. Argumentos que podem ser passados são `--create`, `--gzip`, e `--file`.

`--create` Gera um novo arquivo.

`--gzip` Faz a compressão do arquivo. 

`--file` Especifica o nome do arquivo.

Exemplo: [user@host Downloads]$ **`tar --create --gzip --file example.tar.gz example`**


O formato `gzip` é bem comum no Linux. Também é possível usar outros formatos como `xz` ou `zstd`. O formato `xz` esta disponível para arquivos de aplicação. Na CLI use o comando `tar` coma opção  `--xz`.

#### Extraindo Arquivo via CLI

Para descompactar alguns arquivos é possível usar o mesmo comando, e as vezes ele com opções diferentes. Para alguns já existem comandos específicos para descompactar como `unzip` para extrair arquivos `.zip`.

 Exemplo: [user@host Downloads]$ **`unzip exemplo.zip`**

Para extrair arquivos `.tar`, use o comando com `--extract`, em sequencia o arquivo `--arquivo` as opções e o caminho do arquivo. Para descompactar arquivos `.gz` e `.xz`, use as opções `--gzip` e `--xz`.

[user@host Downloads]$ **`tar --extract --arquivo --gzip exemplo.tar.gz
# Pastas

A criação de pastas via interface é mamão com açúcar então aqui vamos ver somente a parte de criação via linha de comando.

Para criar uma pastar o comando é **`mkdir Pasta`**.

Quando vamos copiar uma pasta com seus conteúdos precisamos usar a opção --recursive ou -r e em seguida as outras pastas que deseja copiar sem isso o conteúdo não é copiado **`cp --recursive PastaFilho PastaPai`**.

Para mudar uma pasta de lugar basta colocar `mv` pasta e a  pasta de destino **`mv Pasta1 PastaDestino`**, o comando `mv` também é usado para mudar nome da pasta basta colocar **`mv PastaNomeAntigo PastaNomeNovo`**.

E para deletar pastas usamos o **`rm`** e em seguida o nome da pasta, **`rm Pasta`**.
# Editores de Texto (Vim)

Assim  como tudo no Linux temos os editores de texto via interface e via linha de comando, de interface temos o <span style="color:rgb(206, 0, 86)">gedit</span> que tem uma interface bem intuitiva de se mexer, já na linha de comando temos <span style="color:rgb(0, 176, 80)">nano</span> e <span style="color:rgb(0, 176, 80)">vim</span>, digamos que o nano é uma versão mais simplificada e mais fácil que o vim, que é a principal razão para ter esse tópico.

# Permissões 

Existem níveis de permissão para usuários (UID), grupos (GID), pastas e arquivos. O primeiro usuário criado no sistema recebe o valor de 1000 em seu [[Abreviações#UID = User identifier é uma propriedade numérica que identifica o usuário no sistema|UID]], já os que forem entre 100 a 999 são conhecidos como usuários do sistema e os valores de 0 a 99 são reservados para o Kernel. O [[Abreviações#GID = Group identifier é uma propriedade numera que identifica um grupo de usuários|GID]] funciona de forma similar ao UID, os grupos começam a partir do numero 1000 sendo este criado ao primeiro usuário, é possível que um usuário tenha acesso a vários grupos 

Adicionar permissões de arquivos  

# SUDO

A palavras sudo vem de _superuser_ _do_, bem sugestivo ao seu significado ele eleva as permissões do usuário para um "super usuário" tendo permissões para mexer em privilégios de pastas, arquivos, usuários, grupos entre varias outras coisas. Para ter acesso a esse modo basta colocar na cli `sudo` pressionar enter, e inserir a senha que é escolhida no sistema, mas normalmente é a do próprio usuário  