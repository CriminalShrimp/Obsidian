Sumario
	#Computador 
	
----

Kernel é a parte principal de um sistema operacional, podemos comparar ele como o **cérebro** ou o **coração** de um computador, ele tem a função de ligar a parte que o usuário chuta do computar (**Hardware**), e a parte que o usuário xinga (**Software**). Além disso ele tem a função de fazer o gerenciamento de recursos do sistema, como a [[Central Processing Unit (CPU)|CPU]], conectar dispositivos, memoria, rodar programas, acessar arquivos e garantir de que tudo esta funcione corretamente. Em poucas palavras, **tudo e qualquer coisa feita no computador e por ele**, passa pelo <span style="color:rgb(65, 105, 255)">Kernel</span>.

- **Modo Kernel:** Tem acesso total e direto aos recursos da maquina, normalmente é nesse modo que kernel opera. 

- **Modo Usuário:** Já aqui os recursos e privilégios já são limitadas, onde para ter acesso a um recurso é necessário fazer uma solicitação para o sistema, o chamado "system call".

Uma representação visual de como um Kernel de Linux funciona.

<iframe src="https://makelinux.github.io/kernel/map/" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>

Kernel Monolítico



Microkernel



Kernel Híbrido