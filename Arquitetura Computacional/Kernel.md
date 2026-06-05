**Sumário**
	**Tags:** #Computador #Linux  #Dica 
	**Conteudo:** github.com/xiyuan1avery/-MIT-6.S081-Operating-System-Engineering?tab=readme-ov-file
	
----

Kernel é a parte principal de um sistema operacional, podemos comparar ele como o **cérebro** ou o **coração** de um computador, ele tem a função de ligar a parte que o usuário chuta do computar (**Hardware**), e a parte que o usuário xinga (**Software**). Além disso ele tem a função de fazer o gerenciamento de recursos do sistema, como a [[Computador#Central Processing Unit (CPU)|CPU]], conectar dispositivos, memória, rodar programas, acessar arquivos e garantir de que tudo esta funcione corretamente. Em poucas palavras, **tudo e qualquer coisa feita no computador e por ele**, passa pelo <span style="color:rgb(65, 105, 255)">Kernel</span>.

- **Modo Kernel:** Tem acesso total e direto aos recursos da máquina (hardware), normalmente é nesse modo que kernel opera. 

- **Modo Usuário:** Já aqui os recursos e privilégios já são limitadas, onde para ter acesso a um recurso é necessário fazer uma solicitação para o sistema, o chamado "system call".

# Tipos de Kernel

Existem diversos modelos de Kernel, porém esses três são os mais usados comumente. 
### Kernel Monolítico

Aqui todos os serviços essenciais do sistema são realizados em um único espaço de memória, e rodam no modo Kernel. Ele tem um <span style="color:rgb(65, 105, 255)">desempenho alto</span> e <span style="color:rgb(65, 105, 255)">baixo tempo de resposta</span>, porém ele é <span style="color:rgb(206, 0, 86)">complexo</span> e <span style="color:rgb(206, 0, 86)">grande</span> (com muito código), devido a isso falhas podem afetar todo o sistema operacional. Sistemas que usam esse tipo de Kernel são: **Linux**, **FreeBSD**, entre outros.

**OBS:** O Linux também é modular, onde é possível inserir módulos (drives) sem precisar reiniciar o sistema.

<figure style="text-align: center;">
  <img src="Kernel Monolitico.png" style="margin: 0 auto;">
  <figcaption>Kernel Monolitico</figcaption>
</figure>
##### Interessante

Uma representação visual de como um Kernel de Linux funciona.

<iframe src="https://makelinux.github.io/kernel/map/" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>

### Microkernel

Somente o que é essencial opera no modo Kernel, já os demais serviços operam em modo usuário, não sendo necessário fazer uma chamada de sistema para realizar certas ações. Pelos seus serviços essências serem rodados de forma mais isolado, ele acabada sendo <span style="color:rgb(0, 176, 80)">mais seguro</span> e com <span style="color:rgb(0, 176, 80)">falhas mais isoladas</span>, isso também o torna <span style="color:rgb(255, 255, 0)">mais complexo</span> e <span style="color:rgb(206, 0, 86)">sobrecarregado</span>. Alguns sistemas que usam esse tipo de Kernel são: Mach, Minix 3, BlackBerry, entre outros.

<figure style="text-align: center;">
  <img src="Microkernel.png" style="margin: 0 auto;">
  <figcaption>Microkernel</figcaption>
</figure>

### Kernel Híbrido

Tentando aproveitar o melhor do **Microkernel** e do **Kernel Monolítico**, o Kernel Hibrido mistura pontos entre os dois, como executar alguns serviços do sistema no espeço do usuário para obter uma performasse melhor, e outros são executados no espaço do usuário. Sistemas que usam esse tipo de arquitetura são: **Windows**, **NetWare**, entre outros. 

<figure style="text-align: center;">
  <img src="Kernel Hibrido.png" style="margin: 0 auto;">
  <figcaption>Kernel Hibrido</figcaption>
</figure>

## Comparação entre os modelos 

Tabela com as principais pontos entre cada modelo.

| Tipo de Kernel  | Descrição                                                                                                      | Vantagens                                                 | Desvantagens                                                                | Exemplos                                 |
| --------------- | -------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------------------------- | ---------------------------------------- |
| **Monolítico**  | Todo o sistema operacional roda no espaço do núcleo ( drivers, sistemas de arquivos, etc.).                    | Alta performance e acesso eficiente ao hardware.          | Se um componente falha, todo o sistema pode parar; código menos organizado. | Linux, Unix, MS-DOS.                     |
| **Microkernel** | Apenas serviços essenciais (gerenciamento básico) rodam no núcleo. Serviços extras rodam no espaço do usuário. | Mais robusto, seguro e modular. Fácil de estender.        | Performance inferior devido à maior comunicação entre componentes.          | Minix, QNX, L4.                          |
| **Híbrido**     | Combina a performance do monolítico com a estrutura modular do microkernel.                                    | Flexibilidade e melhor desempenho que microkernels puros. | Pode se tornar complexo e propenso a bugs como monolíticos.                 | Windows NT (10/11), macOS (Darwin), iOS. |

Representação visual de como cada modelo se comporta.

<figure style="text-align: center;">
  <img src="Tipos de Kernel.png" style="margin: 0 auto;">
  <figcaption>Tipos de Kernel</figcaption>
</figure>

