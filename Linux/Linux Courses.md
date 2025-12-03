Sumario
	Tags: #CLI #Linux
	Cursos: 
		Red Hat Systems Administration (EX200) 
		Introduction to Linux (LFS101)
	Documentações:
	[Gentoo Handbook](https://www.gentoo.org/support/documentation/).
	[Ubuntu Documentation](https://help.ubuntu.com/community/CommunityHelpWiki).
	[Fedora Documentation](https://docs.fedoraproject.org/en-US/fedora/latest/).
	[Linux Pages](http://man7.org/linux/man-pages/).
	[openSUSE Documentation](https://doc.opensuse.org/)
# Introdução
Distribuições Linux são sistemas operacionais feito em cima de um [[Kernel#^b8a742|Kernel]] Linux, essas distribuições são de código aberto, o que significa que são disponibilizadas gratuitamente para todos e além disso tem os requisitos para rodar são mínimos. Dentre as distros ( uma abreviação de Distributions) seria <span style="color:rgb(161, 79, 140)">CentOS</span>, <span style="color:rgb(65, 105, 255)">Fedora</span>, <span style="color:rgb(255, 165, 0)">Ubuntu</span> e <span style="color:rgb(206, 0, 86)">Debian</span>. Distros podem possuir interface gráfica, porém todas suas funções também podem ser feitas pela [[Abreviações#CLI = Command Line Interface é onde são realizados os comandos|command line interface]] mais conhecida como [[CLI]], existem vários terminais CLI como o xterm, konsole, terminator.
 ![[LoginInterfaceGrafica.webp| center]]
<p style="text-align:center;"> Aqui por exemplo é um login feito via interface gráfica</p>

![[LoginCLI.webp| center]]
*<p style="text-align:center;"> Já aqui é um login via CLI</p>

Nos sistemas existe o usuário root que seria a conta que tem a permissão de administrador, o que seria a maior permissão possível de ter em um sistema, com ela é possível fazer qualquer modificação sem que o sistema interfira.

# Manipulação de Pastas e Arquivos
Tags: #Dica
Ver também o tópico: [[Sistema de Arquivos]] e também [[CLI#Comandos|Comandos]].
## Arquivos

Uma frase muito conhecida que se refere a Linux é "no Linux tudo é um arquivo" sejam as informações sobre o hardware do dispositivo, bem como as próprias configurações do kernel, são todas armazenadas em arquivos especiais que residem em diretórios virtuais, os código de estados  0 é o padrão de entrada , 1 é o padrão de saída  e 2 se referre a um erro. Um dos comandos para mexer em arquivos é o **cat** que um uma abreviação de *concatenate* (concatenar), para ler um arquivo bastar escrever **cat arquivo.txt**, duas <span style="color:rgb(255, 255, 0)">dica</span> muito interessante é que para passar outputs direto para um arquivo pode se usar output <span style="color:rgb(255, 255, 0)">></span> arquivo.txt, se é um arquivo que você somente queira adicionar mais linha então use o <span style="color:rgb(255, 255, 0)">>></span>, e a outra seria usar *pipelines* que seria essa barra na vertical  <span style="color:rgb(255, 255, 0)">| </span>, ela faz com que o resultado de um comando seja o *input* de outro. Um comando muito útil para achar arquivos e pastas é o [[CLI#find |find]], já para procurar palavras em textos é o <span style="color:rgb(255, 255, 0)">grep</span>.

Para criar um arquivo existe diversas maneiras um exemplo básico seria com **`touch arquivo.extensao`**.

Para realizar a copia de um arquivo usamos **`cp arquivo.extensao Pasta`**.

Para mudar um arquivo de lugar basta colocar `mv` o nome do arquivo sua extensão  e o destino **`mv arquivo.extensao Pasta`**, o comando `mv` também é usado para mudar nome de arquivos basta colocar **`mv NomeAntigo.extensao NomeNovo.extensao`**.

E para deletar arquivos usamos o **`rm`** e em seguida o nome do arquivo e sua extensão, **`rm arquivo.extensao`**.
## Arquivos Comprimidos

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
## Pastas

A criação de pastas via interface é mamão com açúcar então aqui vamos ver somente a parte de criação via linha de comando.

Para criar uma pastar o comando é **`mkdir Pasta`**.

Quando vamos copiar uma pasta com seus conteúdos precisamos usar a opção --recursive ou -r e em seguida as outras pastas que deseja copiar sem isso o conteúdo não é copiado **`cp --recursive PastaFilho PastaPai`**.

Para mudar uma pasta de lugar basta colocar `mv` pasta e a  pasta de destino **`mv Pasta1 PastaDestino`**, o comando `mv` também é usado para mudar nome da pasta basta colocar **`mv PastaNomeAntigo PastaNomeNovo`**.

E para deletar pastas usamos o **`rm`** e em seguida o nome da pasta, **`rm Pasta`**.
# Editores de Texto (Vim/Nano)
#Ferramentas 
Assim  como tudo no Linux temos os editores de texto via interface e via linha de comando, de interface temos o <span style="color:rgb(206, 0, 86)">gedit</span> que tem uma interface bem intuitiva de se mexer, já na linha de comando temos <span style="color:rgb(0, 176, 80)">nano</span> e <span style="color:rgb(0, 176, 80)">vim</span>, digamos que o nano é uma versão mais simplificada e mais fácil que o vim, que é a principal razão para ter esse tópico.

FAZER COMANDOS NANO/VIM
# Permissões 

Existem níveis de permissão para usuários (UID), grupos (GID), pastas e arquivos. O primeiro usuário criado no sistema recebe o valor de 1000 em seu [[Abreviações#UID = User identifier é uma propriedade numérica que identifica o usuário no sistema|UID]], já os que forem entre 100 a 999 são conhecidos como usuários do sistema e os valores de 0 a 99 são reservados para o Kernel. O [[Abreviações#GID = Group identifier é uma propriedade numera que identifica um grupo de usuários|GID]] funciona de forma similar ao UID, os grupos começam a partir do numero 1000 sendo este criado ao primeiro usuário, é possível que um usuário tenha acesso a vários grupos 

Adicionar permissões de arquivos  

# SUDO

A palavras sudo vem de _<span style="color:rgb(255, 255, 0)">superuser do</span>_, bem sugestivo ao seu significado ele eleva as permissões do usuário para um "super usuário" tendo permissões para mexer em privilégios de pastas, arquivos, usuários, grupos entre varias outras coisas. Para ter acesso a esse modo basta colocar na CLI `sudo` pressionar enter, e inserir a senha que é escolhida no sistema, mas normalmente é a do próprio usuário.
# Acesso Remoto (SSH)
#Comandos #CLI 

O linux usa o _Secure Shell Protocol_ popularmente chamado de SSH para fazer acesso remoto em computadores permitindo envia arquivos e comandos.  O SSH criptografa a comunicação entre os comutadores, normalmente é usado para acessar data centers e Servidores Cloud. Na linha de comando vc pode se conectar a outros computadores usando o comando `ssh`.
#### Habilitando login SSH via linha de comando

Para habilitar o login remoto via SSH usasse o comando `systemctl`, esse comando se refere aos serviços de sistema, como o SSH . Usando o comando `systemctl` com o subcomando`enable` para ativar o serviço, juntamente com a opção `--now` para fazer a mudança imediatamente e por fim o nome do serviço.

[user@host ~]$ **`sudo systemctl enable --now sshd`**

O comando `systemctl is-active` verificar se um serviço esta ativo.

[user@host ~]$ **`systemctl is-active sshd`**
active

[user@host ~]$ **`systemctl is-active lvm2`**
inactive

O comando `systemctl status` mostra os status do serviço.

[user@host ~]$ **`systemctl status sshd`**
● sshd.service - OpenSSH server daemon
     Loaded: loaded (/usr/lib/systemd/system/sshd.service; enabled; vendor pres>
     Active: active (running) since Fri 2023-11-03 15:34:30 NZDT; 1h 43min ago
[...]

#### Logando pela linha de comando

O comando SSH exige o nome do usuário e o endereço/domínio que esta sendo conectado, esses dois argumentos são adicionados com o símbolo (`@`)  separando-os
Nesse exemplo vc esta logando na maquina `servera`, com o usuário `remote` que tem a senha `RedHat123!`.

[user@host ~]$ **`ssh remote@servera`**
student@servera's password: **`RedHat123!`**

Após conseguir efetuar com sucesso o login o que mudara vai ser o usuário e o domínio na sua linha de comando.
[remote@servera ~]$

#### Transferindo arquivos via CLI

O comando `scp` copia arquivos de um computador para outro por uma criptografia na rede, ele requer dois argumentos na seguinte ordem: o arquivo a ser movido e a localização desejada.

Para copiar um arquivo local para um servidor remoto forneça o caminho do arquivo para o arquivo que deseja copiar e o server de destino junto com o caminho, esta ação precisa da senha para ser realizada.

[user@host ~]$ **`scp ~/Documents/exemplo.txt user@servera:~/Documents`**

É possivel copiar um arquivo do servidor remoto para seu computador local.

[user@host ~]$ **`scp user@servera:~/Documents/exemplo.txt ~/Documents`**

E também é possível copiar de um servidor remoto para outro servidor remoto.

[user@host ~]$ **`scp user@servera:~/Documents/exemplo.txt user@serverb:~/Documents`**

### Chaves SSH para Autenticação Remota

É possível fazer autenticações usando o conceito de [[Chaves Públicas e Privadas]]. 
#### Criando um par de chave SSH
Na linha de comando, crie uma chave usando o comando `ssh-keygen` com a opção `-t ed25519` esse numero refere-se ao algoritmo de criptografia, e para as opções seguinte aceite as padrões. É possível  gerar essa chave somente uma vez , mas o mesmo pode usar o mesmo par para diversos servidores. Uma opção adicional é usar uma "senha" na hora da criação da chave, como um camada a mais de segurança. Aqui esta um exemplo da criação da chave.

[user@host ~]$ **`ssh-keygen -t ed25519`**
$ ssh-keygen -t ed25519
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/user/.ssh/id_ed25519): **`**Enter**`**
Created directory '/home/user/.ssh'.
Enter passphrase (empty for no passphrase): **`**Enter**`**
Enter same passphrase again: **`**Enter**`**
Your identification has been saved in /home/user/.ssh/id_ed25519
Your public key has been saved in /home/user/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:y+Ue2FpKtHlTIes+5RC/VFBHohey+5iAGWRQ9J6bpJw user@host
The key's randomart image is:
+--[ED25519 256]--+
|      .+=   ..+.o|
|       o .  .+ + |
|        . o +..  |
|         =.+ +.  |
|        S Boo.   |
|       + &.=++   |
|        E @=o..  |
|       . B.oo    |
|        o o.     |
+----[SHA256]-----+

Para verificar as chaves use o comando  `ls` para verificar o conteúdo do diretório `~/.ssh`. O arquivo `id_ed25519`  é a chave privada , já o arquivo `id_ed25519.pub` é a chave publica.
#### Distribuindo a chave SSH

O comando `ssh-copy-id` copai sua chave publica para um computador remoto, basta colocar o comando seu usuário e o destino separados por um @, como no exemplo abaixo

[mhoward@host ~]$ **`ssh-copy-id developer030@servera`**
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
developer030@172.25.250.10's password: **`RedHat123!`**

Number of key(s) added: 1

Se estiver certo, quando logar não precisara digitar a senha, para testar use  `ssh usuario@destino`


# Sistema de Gerenciamento de Pacotes
Aqui é onde encontramos como instalar softwares no sistema Linux, existem dois gerenciadores de pacotes conhecidos popularmente: os baseados em sistema <span style="color:rgb(206, 0, 86)">Debian</span> e os que usam <span style="color:rgb(255, 255, 0)">RPM</span>. Ambos pacotes operam com ferramentas em níveis distintos, como em baixo nível (como a **dpkg** ou **rpm**) que se preocupa com rodas scripts, baixar e descompactar pacotes por pacotes, instalar os softwares corretamente. Enquanto as de alto nível (como **apt**, **dnf** ou **zypeer**) que baixam grupos de pacotes, e descobre as dependências. Muitas vezes os usuários trabalham com as ferramentas de alto nível, que quando necessário chamam as de baixo. 

![[Gerenciadores de Pacotes Linux.webp|center ]]
### Diferentes Gerenciadores de Pacotes
Comandos para adquirir softwares de diferentes gerenciadores muda dependendo de qual esta sendo utilizado no momento, aqui tem uma rápida comparação de alguns comandos.
![[Comandos de Gerenciadores de Pacote.webp|center]]
#### Advanced Packaging Tool (apt)
É o gerenciador de softwares baseados no sistema <span style="color:rgb(206, 0, 86)">Debian</span>.
#### dnf 
Esse é um gerenciador de pacote que tem seu código aberto usado para sistemas pertencentes a família <span style="color:rgb(206, 0, 86)">Red Hat</span>.
#### zyper
Este é o gerenciador de pacote de sistemas da família <span style="color:rgb(0, 176, 80)">SUSE</span> também baseada em RPM, sendo bem fácil de entender e utilizar, além disso ele se baseia em dnf.