**Sumário**
	**Tags:** #Redes #RedTeam
	**Conteúdo:**
		https://medium.com/@laurent.mandine/c2-role-in-cyber-attack-dde4710f2037 - Explicação.
		paloaltonetworks.com/cyberpedia/command-and-control-explained - Explicação.
		youtube.com/watch?v=ql0ijCvO7q8 - Demonstração de ataque.
	
----

Uma das ações após um atacante conseguir infectar/comprometer uma maquina é criar um canal de comunicação para poder usar a maquina com bem entender, usando um servidor para mandar comandos (C2 Server) e assim obter controle sobre a maquina ou rede. O uso mais comum desse ataque é para a criação de **Botnets**, onde se tem diversas maquinas infectadas para realizar um ataque [[Denial of Service (DDoS)|DDoS]], além disso é possível roubar dados das maquinas, instalar [[Malware]] ou comprometer a disponibilidade de serviços. Mascarar esse trafego para não ser detectado e manter as maquinas "zombies" sobre comando é a parte mais difícil depois de infecta-las, é possível mascarar o tráfego usando fragmentação e ofuscação de pacotes, e criptografando o trafego.

Existem diferentes modelos de ataques, a diferença entre eles normalmente é sua complexidade, estrutura e o quão difícil é identificá-los. 

- **Arquitetura Centralizada**: Essa é o modelo mais comum usado nos ataques, funciona como uma comunicação normal de cliente e servidor. Quando um computador é infectado, ele se junta a botnet iniciando o comunicação com o servidor C2, e fica esperando os comandos do **botmanster** que é quem controla a rede de bots. Esse modelo pode ser facilmente detectado e bloqueado, mas também existem técnicas para tornar essa identificação mais difícil como utilizar [[Proxy]], [[Balanceador de Carga]] e redirecionadores.

	<figure style="text-align: center;">
	  <img src="C2 Centralizado.png" style="margin: 0 auto;">
	  <figcaption>C2 Centralizado</figcaption>
	</figure>

- **Peer-2-Peer (P2P)**: Um modelo que não é centralizando, ele usa pontos da arquitetura para mandar os comandos, e com isso tornando mais difícil de ser detectado, e mesmo quando é possível identificar só é possível derrubar alguns pontos, mas a rede continua em funcionado com os outros pontos.

	<figure style="text-align: center;">
	  <img src="C2 P2P.png" style="margin: 0 auto;">
	  <figcaption>C2 P2P</figcaption>
	</figure>

- **Arquitetura Aleatória**: Usa de diversos meios de comunicações confiáveis para esconder os traços de seus ataques.

	<figure style="text-align: center;">
	  <img src="C2 Aleatoria.png" style="margin: 0 auto;">
	  <figcaption>C2 Aleatoria</figcaption>
	</figure>