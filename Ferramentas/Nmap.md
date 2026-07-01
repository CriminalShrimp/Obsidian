**Sumário**
	**Tags:** #Redes #Ferramentas #RedTeam
	**Conteúdo:**
		http://scanme.nmap.org - Teste de Scann.
		medium.com/@angelinasalim_/an-introduction-to-port-scanning-for-beginners-using-nmap-67c0e02c5dc7 - Explicação de como o Scann funciona.
		
	
----

Usado para identificar dispositivos, portas e serviços na redes, além de descobrir vulnerabilidades da mesma, o Nmap (abreviação de Network Mapper) é usado para para realizar o mapeamento de redes de forma simples e rápida, ou de forma complexa e detalhada. Ela esta disponível para diversos sistemas operacionais, possui uma interface para seu uso chamada de **ZenMap**, porém o seu uso via [[Abreviações#CLI = **C**ommand **L**ine **I**nterface é onde são realizados os comandos do sistema.|cli]] é mais preferido e utilizado por quem usa a ferramenta.

<figure style="text-align: center;">
  <img src="Nmap Interface.png" style="margin: 0 auto;">
  <figcaption>ZenMap</figcaption>
</figure>

Usando o comando `nmap` sem nenhuma opção adicional, e logo depois colocar o endereço do scan (pode ser o nome do domínio ou o ip), será feita uma varredura das 1000 portas mais comuns usadas em serviços. Também é possível fazer o scan de diversos alvos, separando os endereços com um espaço, e também redes usando a sua notação [[Abreviações#CIDR = **C**lassless **I**nter **D**omain **R**outing é usado para representar o endereço IP e sua mascara de rede, representado por sua uma / após o endereço.|CIDR]], e caso haja vários alvos destintos o comando `-iL` seguido de um arquivo .txt com os alvos, ira fazer o scan de cada alvo.

O resultado ao concluir um scan aparece da seguinte forma: **porta**/**protocolo**, o estado que pode ser <span style="color:rgb(0, 176, 80)">open</span>, <span style="color:rgb(206, 0, 86)">close</span> ou <span style="color:rgb(65, 105, 255)">filtered</span>, e o no final o **serviço** que esta rodando, outros resultados podem aparecer dependendo das opções passadas na hora de realizar o reconhecimento. O estado <span style="color:rgb(0, 176, 80)">open</span> significa que a porta esta aceitado conexões, <span style="color:rgb(206, 0, 86)">close</span> é quando ela responde as pacotes Nmap, mas não tem nenhuma aplicação rodando nela, e <span style="color:rgb(65, 105, 255)">filtered</span> ocorre normalmente quando existe um firewall na rede. Com o comando `-oN` arquivo.txt (ou `-oX` arquivo.xml), o resultado é escrito no arquivo, facilitando assim a leitura ou exportação.

As opções podem ser somadas e combinadas, fazendo assim scans específicos para cada cenário, ou também complexos e letos, mas que funcionam em grande parte dos cenários. Os  mais usados são `-p` para especificar portas, `-O` para identificar sistemas operacionais, `-sn` para fazer scan usando o ping, o `-Pn` que trata todos os hosts como ativos (útil contra firewalls), `-sT` para protocolo TCP, e `-sU` para o UDP, `-sV` detecta a versão do que esta rodando na porta, e um dos mais populares o `-sS` que realiza um scan de forma furtiva, vale mencionar também o `-T` que permite colocar tempo entre os envios de pacotes para que não fique tão obvio que esta ocorrendo um recolhimento da rede. Para algo mais customizado e bem trabalhado temos o **N**map **S**cripting **E**ngine (**NSE**), diversos scripts estão presente nativamente no Nmap, mas também há como criar seus próprios scripts.

## Scanns Avançados

nmap -sV -T5 --min-rate 5000 --max-retries 1 -F <target> - Reconhecimento Rápido de Infraestrutura.
	O -sV identifica as versões, o T5 faz realizar a varredura de forma rápida junto com o min-rate que faz que com envie um valor mínimo de pacotes, para não existir em portas inúteis o max-retries e o -F usa as 100 portas mais comuns.

nmap -sS -sV -O -p 21,22,23,25,80,139,443,445,3389 --script=vuln,aut <target> - Varredura, Versão e Scripts de Vulnerabilidade
	Usando o -O para descobrir Sistema Operacional, -p  com as portas mais comunsm e por fim o
	--script=vuln,auth que executa seus respectivos scripts.

nmap -sS -p- -T4 -f --data-length 32 -D RND:5 --randomize-hosts <target>
	Realiza o reconhecimento de forma silenciosa com o -sS, define as todas a portas com -p-, para se mesclar com trafego é usado -f, --data-length, --randomize-hosts, e -D RND:5 que cria 5 endereços IP falsos (iscas) para mascarar o IP real.

