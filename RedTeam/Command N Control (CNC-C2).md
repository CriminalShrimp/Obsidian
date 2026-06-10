**Sumário**
	**Tags:** #Redes #RedTeam
	**Conteúdo:**
		medium.com/@laurent.mandine/c2-role-in-cyber-attack-dde4710f2037 - 
		paloaltonetworks.com/cyberpedia/command-and-control-explained - Explicação.
	
----

Uma das ações após um atacante conseguir infectar/comprometer uma maquina é criar um canal de comunicação para poder usar a maquina com bem entender, usando um servidor para mandar comandos (C2 Server) e assim obter controle sobre a maquina ou rede. O uso mais comum desse ataque é para a criação de **Botnets**, onde se tem diversas maquinas infectadas para realizar um ataque [[Denial of Service (DDoS)|DDoS]], além disso é possível roubar dados das maquinas, instalar [[Malware]] ou comprometer a disponibilidade de serviços. Mascarar esse trafego para não ser detectado e manter as maquinas "zombies" sobre comando é a parte mais difícil depois de infecta-las, é possível mascarar o tráfego usando fragmentação e ofuscação de pacotes, e criptografando o trafego.

Existem 3 modelos que são usados em ataques de C2, a de Arquitetura Centralizada, P2P e a Aleatoria