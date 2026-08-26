**Sumário**
	**Tags:** #Linux #Dica #Comandos
	**Conteúdo:** Introduction to Linux (LFS101)
	
----
# Introdução

CLI esta presente em praticamente todos software, e nele é possível fazer coisas de formar mais eficaz que por interface gráfica. Um site que com vir a ser útil é o [explainshell.com](https://explainshell.com/), ele oferece uma explicação detalhada sobre cada parte do comando que esta sendo realizado. 
<span style="color:rgb(255, 255, 0)">Adendo</span>: **sudo systemctl stop/start gdm**  **sudo telinit 3** para stop e **sudo telinit 5** para o start) para ativar a interface (GUI).

Comumente a CLI vai apresentar a seguinte composição de elementos:

<p style="text-align:center;">[<span style="color:rgb(255, 0, 0)"> usuario</span>@<span style="color:rgb(0, 176, 240)">sistema</span> <span style="color:rgb(255, 192, 0)"><span style="color:rgb(255, 192, 0)"><span style="color:rgb(0, 176, 80)">~</span></span></span>] <span style="color:rgb(255, 192, 0)">$</span></p>
<span style="color:rgb(255, 0, 0)">Se refere ao nome do usuário em que esta logado.</span>

<span style="color:rgb(0, 176, 240)">Sistema em que esta logado.</span>

<span style="color:rgb(0, 176, 80)">Já esse campo representa o diretório em que esta sendo acessado, o símbolo ~ se refere a o home do usuário.</span>

<span style="color:rgb(255, 192, 0)">Esse campo pode mudar entre $ e #, sendo que quando aparece o símbolo # significa que o usuário esta com privilégios, já o $ significa que é um usuário "padrão".</span>

Na hora de realizar comandos na CLI a seguinte sintaxe deve ser seguida:

<p style="text-align:center;"><span style="color:rgb(255, 0, 0)"> comando</span> [<span style="color:rgb(0, 176, 240)">opções</span>] [<span style="color:rgb(0, 176, 80)">argumentos</span>]</p>

<span style="color:rgb(255, 0, 0)">O comando pode ter ou não os campos opção e argumentos, isso varia conforme a o resultado desejado.</span> 

<span style="color:rgb(0, 176, 240)">Logo em seguida vem as opções que podem ser mais que uma, quando vamos usar uma opção ela vem antecedida com um - ou dois --, quando usado com somente um - significa que estamos usando a abreviação de um palavra, já quando contem dois -- tudo é tratado como uma palavra.</span> 

# Comandos 

Parâmetros de buscas 

|?| Procurar qualquer caráter.
| * | Procurar por todas as possiblidades de texto.
|[set]| Procura por qualquer caráter colocado na combinação, por exemplo [ g - v].
|[!set]| Ao contrario por tudo que não contem o que há no campo.

## Básicos

#### locate - Procura em todo o sistema pelo texto que foi inserido na busca. 

#### cd - **C**hange **D**irectory movimenta-se pelo sistema.
**cd ..** - Volta para a **Home**
**cd -**  - Volta para o diretório anterior.
#### ls - Usado para listar arquivos.
ls  <span style="color:rgb(0, 176, 240)">opções </span>  <span style="color:rgb(0, 176, 80)">Arquivo/diretorio</span>

#### pwd - **P**rint **W**orking **D**irectory mostra o<span style="color:rgb(255, 255, 0)"> caminho de pastas</span> ate chegar onde o usuário esta trabalhando.
#### touch - Usado para criar um arquivo.
**touch -t** {tempo} - com essa opção é possível coloca a data de criação do arquivo 
#### cat - Usado para ver o conteúdo do arquivo.
#### tac - A mesma coisa do cat, só que começa da ultima linha .
#### tail - Mostras as 10 ultimas linhas do arquivo, podendo alterar o valor usando -n e o valor desejado.
#### head - A mesma coisa do tail, só que começa da primeira linha. 
#### mkdir - Cria uma pasta com o nome desejado.
#### mv - Muda o nome do arquivo.
#### rm - Remove um arquivo.
**rm -f** - Força o arquivo a ser removido.
**rm -rf** - Força o diretório. 
#### tree - 
#### find  - Usado comumente para<span style="color:rgb(255, 255, 0)"> procurar arquivos no sistema.</span>

**-type d - name**
	Procura por diretórios com o nome inserido.
**-type f - name**
	Procura por arquivos com o nome inserido.
**-exec** <span style="color:rgb(0, 176, 80)">comando</span>
	É possível executar comandos como <span style="color:rgb(255, 255, 0)">rm</span>, <span style="color:rgb(255, 255, 0)">cp</span> entre outros com o find também.
-**/ -(<span style="color:rgb(255, 255, 0)">x</span>)time**
	Serve para procurar para arquivos passeados em seu tempo, trocando o <span style="color:rgb(255, 255, 0)">x</span> é possível pesquisar pelo seu último acesso, data de criação entre outras opções.
-**/ -size**
	Procura pelo tamanho dos arquivos.

#### which  - Procura por programas com o nome colocado na pesquisa e mostra sua localização.
#### whereis  - Além de procurar por programas também procura por arquivos com o nome na pesquisa.
#### timedatectl - 

#### cat - Usado para criar arquivos.
#### cp - Copia o arquivo.
#### man - É a abreviação de manual, esse comando mostra dados e informações sobre o que deseja.
-**man -a** - Ira mostrar todas as paginas uma por uma.
-**man -f** - Gera uma breve descrição das paginas e capítulos.
-**man -k** - Mostra todas as paginas que contem a palavra usada.
#### info - Traz as informações sobre o que foi procurado

## Processos

Antes de vermos os comandos é sobre processos é importante entender alguns conceitos sobre <span style="color:rgb(65, 105, 255)">Processos</span>, <span style="color:rgb(0, 176, 80)">Threads</span> e <span style="color:rgb(206, 0, 86)">Tasks</span>.

De forma simples <span style="color:rgb(65, 105, 255)">processos</span> são os programas ou comandos que estão em execução, e esses por sua vez são a execução de uma ou mais *thread*. Cada processo necessita de uma certa quantidade de recursos da máquina, esses recursos são alocados pelo kernel, um exemplo de processo seria o **Download**. Existem diferentes tipos de processos. Já a <span style="color:rgb(0, 176, 80)">thread</span> é o responsável por executar o trabalho. Como por exemplo existe o processo do **Download**, e dentro dele a thread responsável por baixar o arquivo. Existem também as <span style="color:rgb(0, 176, 80)">Multithreads</span> ou "Multitarefas" que seriam várias threads dentro de um processo realizando **vários downloads**, ou fazendo diversas coisas. E por fim temos as <span style="color:rgb(206, 0, 86)">tasks</span> é o que deve ser feito, usando como exemplo seria a missão de **fazer o download**.

Fazendo uma analogia para entender e **resumir**, o <span style="color:rgb(65, 105, 255)">processo</span> é uma <span style="color:rgb(65, 105, 255)">fabrica</span> que disponibiliza recursos e ferramentas, <span style="color:rgb(0, 176, 80)">thread</span> é o <span style="color:rgb(0, 176, 80)">operário</span> que realizara o serviço, e <span style="color:rgb(206, 0, 86)">task</span> é o <span style="color:rgb(206, 0, 86)">serviço a para ser feito</span>.

##### top - Lista os processos ativos.

Esse é um comando onde transforma o seu terminal em um sistema de monitoramento em tempo real, ele é dividido em duas partes principais, no começo temos as estatísticas com dados como usuários, tempo ligado, estado das *Tasks*, dados da [[Computador#Central Processing Unit (CPU)|CPU]], e abaixo delas temos dados de [[Computador#Memória RAM|Memória RAM]] e de [[Computador#Dispositivo de Armazenamento|Armazenamento]]. E ate o final da tela temos as tabelas com os processos, contendo informações relacionadas aos processos a qual usuário ela pertence, comando usado, consumo de recursos, tempo ativa, etc.

> Vale a pena usar o btop, uma versão com mais detalhes e mais fácil de ser compreendida, e também o atop para mais dados de recursos sendo usados.

Para ver as opções e interações com a tabela basta usar **?** ou **h**, mostrara comandos interativos com o comando. Para mudar como a tabela esta sendo listada usando a tecla `shift + {tecla}`, alguma das combinações mais importantes são:

**p**
	Lista processos por uso de CPU.
**m**
	Listar processos por uso de memória.
**k**
	Encerrar um processo. Não precisa usar o shift, basta fornecer o id do processo para encerrá-lo.
##### ps - Gera uma "print" de processos rodando.

##### ef - Mostra todos os processos detalhadamente.

#### Processos programados

Comandos que são usados para realizar tarefas em períodos específicos ou cotidianamente, o mais relevante deles é o `cron`, usado juntamente com o `sleep`.
##### at - Roda uma tarefa uma vez.
##### cron - Serviço de rotinas e tarefas.
##### crontab - Arquivo e comando usado para gerenciar as rotinas do cron.

O crontab tem 6 colunas, que da esquerda para a direita representam **Minutos** pode ir de **0** a **59**, **Horas** **0** a **23**, **Dias** **1** a **31**, **Messes** **1** a **12** ou de **jan** a **dez**, **Dias da Semana** **0** a **6** ou de **sun** a **sat**, e por último o **Comandos** que pode ser também um **script**. Caso aparece na coluna apareça o símbolo `*` ele simboliza do primeiro até o último valor do campo.

##### anacron - 
##### sleep - 
## Sistema
#### shutdown - Faz o processo de desligamento padrão, executando rotinas, finalizando serviços e processos e desligando a máquina. 

<span style="color:rgb(65, 105, 255)">now</span>
	Desliga a maquina imediatamente
**<span style="color:rgb(65, 105, 255)">-r</span>, --reboot**
	Reinicia o sistema
**<span style="color:rgb(65, 105, 255)">-h</span>,** <span style="color:rgb(0, 176, 80)">TIME</span>
	 Colocando `now` faz com que o sistema seja desligado na hora. Também da para colocar tempo específico para desligar o sistema

Ex: `shutdown -h 10:00 "Shutting down for scheduled maintenance."`
#### halt - Para o sistema operacional porém ainda deixa a máquina ligada.
#### poweroff - Parecido com shutdown porém funciona de uma forma mais "bruta", cortando a energia do sistema, não rodando scripts e rotinas antes de desligar.