**Sumário**
	**Tags:** #BlueTeam  
	**Conteúdo:**
		kaspersky.com.br/resource-center/threats/what-is-a-honeypot
		techtarget.com/searchsecurity/definition/honey-pot
		
	
----

Assim como o **rato** se sente atraído por um **queijo na ratoeira**, uma <span style="color:rgb(255, 255, 0)">abelha</span> se sente atrai por um <span style="color:rgb(255, 255, 0)">pote de mel</span>, mas qual a **relação entre essas duas coisas**? Ambas são uma **armadilha**! Essa é a ideia do Honeypot em uma rede de segurança, fazer uma isca para que as abelhas (atacantes) caiam nela.

A ideia é simples, fazer um **sistema muito parecido com o sistema real, para que os atacantes explorem a aplicação e busquem por falhas nela**, e desse ponto analisar os dados e os resultados das ações realizadas nesse ambiente e fazer melhorias e correções nos verdadeiros ambientes. Além de gerar dados de atacas reais, também ganha tempo pois os atacantes estão atacando uma aplicação falsa ao invés de atacarem a real. Existe dois tipos de Honeypot, e além disso eles também são classificados em três tipos, são eles: 

- **Honeypot de Produção:** São colocados ao lado de outros produtos servindo como isca, para tirar a atenção dos serviços reais. Essas iscas contem informações para chamar atenção dos atacantes, além disso são feitos para parecerem reais, tudo para que os atacantes gastem empenho e tempo nessas falsas aplicações.
 
- **Honeypot de Pesquisa:** Aqui já é feito um trabalho analítico, vendo quais ataques estão sendo explorados, quais pontos do sistema possuem mais tentativas de invasão, entre outras ameaças. Esses dados então usados para prevenir ataques futuros e reforçar o sistema de segurança.

- **Puro:** Esses são os mais difíceis e complexos de se manter, eles são executados em escala real e em vários servidores de produção, com dados forjados para parecem autênticos, eles possuem uma série de [^1]sensores usados para rastrear e observar a atividades suspeitas.

- **Alta Interação:** Rodam diversos serviços e imitam a atividade de um servidor de produção, tudo isso para obter a maior quantidade de dados possíveis. O objetivo aqui é entreter o atacante pelo maior tempo possível, e após eles ter acesso privilegiado no sistema, analisar sua atividade a partir desse ponto.

- **Baixa Interação:** Simulam os vulnerabilidades mais comuns, oferecem menos risco e são simples de manter, normalmente não pegam ataques complexos e sim boots, origem de ataques, [[Malware|malwares]] e dados mais rudimentares.

Além disso existem Honeypots específicos para tipos de ataques como: **Malware Honeypots** que exploram vetores de ataques malware, **Spam Honeypots** que pegam métodos de spam de e-mail, monitoram e os bloqueiam por exemplo, **Database Honeypots** que analisam ataques contra banco de dados, **Client Honeypots** são reforçados com segurança pois eles se passam por cliente em busca de servidores maliciosos, **Spider Honeypots** que são feitos para segurarem bots que buscam paginas em uma pagina, e diversos outros tipos.

Muito importante reforçar que <span style="color:rgb(206, 0, 86)">Honeypots podem ser usados pelos invasores para entrar na rede</span>, pois se o mesmo não estiver bem configurado e protegido, é possível se espalhar na rede e infectar mais maquinas, assim levando ao comprometimento de todo o sistema, servidores e serviços.

[^1]: Esses sensores seriam regras e "triggers" que alertam a equipe de segurança em caso de ameaça.
