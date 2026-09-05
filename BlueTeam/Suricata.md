**Sumário**
	**Tags:** #Redes #Protocolos #Ferramentas 
	**Arquivos Relacionados:** [[Descoberta de Rede (HUB)]]
	**Conteúdo:**
		huntress.com/cybersecurity-101/topic/what-is-suricata - Sobre a ferramenta.
		
----

Uma ferramenta de código aberto que atua como um sistema de prevenção a intrusões (**IPS**) e também como um sistema de detecção de intrusões (**IDS**), com esse dois sistema ele pode gerar alertas sobre possíveis ameaça e também bloqueá-las, um diferencial dele é sua analise de pacotes, onde ele consegue ver o real conteúdo dos pacotes, e então usar suas regras ou assinaturas de ataque para detectar suas ameaças. E usando [^1]Multithreads ele não passa dificuldades para realizar todas essas funções. Suricata não possui [[Abreviações#GUI = **G**raphical **U**ser **I**nterface onde o usuário consegue interagir como programa por meio de botões imagens, ícones, etc.|GUI]] toda sua configuração é realizada via linha de comando.

[^1]: Treads são tarefas dentro de um processo. Como por exemplo existe o processo do Download, e dentro dele podem ter vários downloads, que seriam as tarefas. <span style="color:rgb(255, 255, 0)">Multithreads</span> ou "<span style="color:rgb(255, 255, 0)">Multitarefas</span>" seriam várias threads dentro de um processo realizando coisas diferentes.
