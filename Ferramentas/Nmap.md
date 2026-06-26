**Sumário**
	**Tags:** #Redes #Ferramentas #RedTeam
	**Conteúdo:**
		http://scanme.nmap.org - Teste de Scann.
		medium.com/@angelinasalim_/an-introduction-to-port-scanning-for-beginners-using-nmap-67c0e02c5dc7 - Explicação de como o Scann funciona.
		
	
----

Usado para identificar dispositivos, portas e serviços na redes, além de descobrir vulnerabilidades da mesma, o Nmap é usado para para realizar o mapeamento de redes de forma simples e rápida, ou de forma complexa e detalhada. Ela esta disponível para diversos sistemas operacionais, possui uma interface para seu uso chamada de **ZenMap**, porém o seu uso via [[Abreviações#CLI = **C**ommand **L**ine **I**nterface é onde são realizados os comandos do sistema.|cli]] é mais preferido e utilizado por quem usa a ferramenta.

<figure style="text-align: center;">
  <img src="Nmap Interface.png" style="margin: 0 auto;">
  <figcaption>ZenMap</figcaption>
</figure>

Usando o comando `nmap` sem nenhuma opção adicional, e logo depois colocar o endereço do scan (pode ser o nome do domínio ou o ip), será feita uma varredura das 1000 portas mais comuns usadas em serviços. Também é possível fazer o scan de diversos alvos, separando os endereços com um espaço, e também redes usando a sua notação [[Abreviações#CIDR = **C**lassless **I**nter **D**omain **R**outing é usado para representar o endereço IP e sua mascara de rede, representado por sua uma / após o endereço.|CIDR]], e caso haja vários alvos destintos o comando `-iL` seguido de um arquivo .txt com os alvos, ira fazer o scan de cada alvo.

O resultado ao concluir um scan aparece da seguinte forma: **porta**/**protocolo**, o estado que pode ser <span style="color:rgb(0, 176, 80)">open</span>, <span style="color:rgb(206, 0, 86)">close</span> ou <span style="color:rgb(65, 105, 255)">filtered</span>, e o no final o **serviço** que esta rodando, outros resultados podem aparecer dependendo das opções passadas na hora de realizar o reconhecimento. O estado <span style="color:rgb(0, 176, 80)">open</span> significa que a porta esta aceitado conexões, <span style="color:rgb(206, 0, 86)">close</span> é quando ela responde as pacotes Nmap, mas não tem nenhuma aplicação rodando nela, e <span style="color:rgb(65, 105, 255)">filtered</span> ocorre normalmente quando existe um firewall na rede. Com o comando `-oN` arquivo.txt (ou `-oX` arquivo.xml), o resultado é escrito no arquivo, facilitando assim a leitura ou exportação.

As opções podem ser somadas e combinadas, fazendo assim scans específicos para cada cenário, ou também complexos e letos, mas que funcionam em grande parte dos cenários. Os  mais usados são `-p` para especificar portas, 

#### Scanns Avançados

