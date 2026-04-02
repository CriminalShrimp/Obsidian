**Sumário**
	**Tags:** #Redes #Protocolos #Ferramentas 
	**Arquivos Relacionados:** [[Descoberta de Rede (HUB)]]
	**Conteúdo:**
		medium.com/@ashutoshthakurofficial/deep-dive-into-zeek-a-powerful-network-security-monitoring-tool-f52ff3485035 - Explicação do Zeek.
		youtube.com/watch?v=WBid7AZ5w4A - Vídeo Demonstração.
		
----

Não é uma ferramenta, mas sim um framework que é adicionado para se adequar e melhorar a segurança da rede. Ele funciona de duas camadas, uma delas é a de **Event Engine**, onde ele analisa o trafego de rede e "destaca" eventos suspeitos, e a outra é a **Script Interpreter**, que permite criar regras especificas para quando ocorrer algum eventos uma determinada ação seja tomada. Além disso ele utiliza frameworks modulares (usados para separar pedaços específicos de sistemas) para aumentar suas capacidades, como **Logging Framework**, que gera logs como `conn.log`, `dns.log`, `http.log`, etc, **Notice Framework**, que manda gerar alertas para atividades suspeitas, e muito outros. É possível gerar mais de 50 tipos de logs, os mais usados são os já citados e `files.log`,`signatures.log`, `notice.log` e `intel.log`. Aqui tem pdf com os logs e os detalhes de cada tipo

![[ZeekLogs.pdf]]