**Sumário**
	**Tags**: #Linux #Windows #Computador 
	**Conteúdo:** 
			youtube.com/watch?v=6FW3L-NePUI - Explicação.
			medium.com/@habbema/desvendando-o-wsl-2-no-windows-11-c7649545026d - Escrito sobre.
			
----

Emulando o [[Kernel]] do Linux via virtualização, o Windows consegue nativamente rodar programas do Linux em seu sistema, para desenvolvedores e programadores isso facilita muito as coisas pois assim não precisar fazer uma maquina virtual, ou instalar mais de um sistema operacional sem seu computador para realizarem suas atividades. Existem duas versões dessa ferramenta no Windows, sendo cada uma delas limitadas as capacidades da maquina. 

É possível escolher diversas distribuições na Microsoft Store, ou também usando o comando `wsl --install -d` (tanto no powershell quanto no cmd) e em seguida o nome da distribuição desejada. Para verificar quais imagens estão disponíveis existe o comando `wsl --list --online` que gera uma lista com as que podem ser usadas. E para usar o sistema operacional basta simplesmente digitar `wsl -d` e o nome da distro instalada.

