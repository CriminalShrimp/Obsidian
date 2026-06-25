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

Usando o comando `nmap` sem nenhuma opção adicional, e logo depois colocar o endereço do scan (pode ser o nome do domínio ou o ip), será feita uma varredura das 1000 portas mais comuns usadas em serviços. É também possível fazer o scan de diversos alvos, separando os endereços com um espaço, e também redes usando a sua notação CIDR, 
#### Scanns Avançados

