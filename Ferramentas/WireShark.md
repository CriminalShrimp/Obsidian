**Sumário**
	**Tags:** #Redes #BlueTeam #RedTeam #Ferramentas 
	**Arquivos Relacionados:** [[Descoberta de Rede (HUB)]]
	**Conteúdo:**
		https://www.wireshark.org/ - Site oficial.
		https://medium.com/@cyberengage.org/master-wireshark-tool-like-a-pro-the-ultimate-packet-analysis-guide-for-real-world-analysts-981fb9024e7d - Configuração de interface e uso.
		https://www.youtube.com/watch?v=w6kIER4SFhQ - exemplo de captura de pacotes.
	
----

O WireShark (anteriormente conhecido como Ethereal) é um analisador de pacotes que é usado para capturar captura, observar e inspecionar trafego passando por uma rede de computador. Ele é usado para descobrir problemas na rede como lentidão, latência e perda de pacotes, e também para alisar possíveis ameaças, como malwares e trafego/comunicação foram do comum dentro da rede. 

<figure style="text-align: center;">
  <img src="WireShark.png" style="margin: 0 auto;">
  <figcaption>WireShark</figcaption>
</figure>

A principal parte e que também vai ser mais vista e usada durante o uso e sua interface, nela temos de tudo, dados, menu, atalhos, pacotes e diversas outras coisas. 

Agora falando das principais funções de cada opção na  barra de menus logo no começo temos o **File**, nela é possível salvar, abrir, exportar e juntar capturas de pacotes. Depois temos a opção **Edit** que contem um localizador de pacotes, gerenciamento de perfis e também as configurações de preferencias para o uso do programa. Para modificar qualquer aspecto visual basta acessar o menu **View** e alterar o que for de seu agrado. A opção **Go** server para navegar entre os pacotes capturados. Para começar, parar ou filtrar uma captura de pacotes basta acessar a aba **Capture**. 
No **Analyze** da para usar filtros, macros, seguir pacotes e conversas, adicionar colunas e protocolos. Já em **Statistics** existe diversas ferramentas uteis para visualizar e compreender melhor sobre a captura realizada, um menu que é muito útil e deve ser usado. E para terminar os menus de de **Telephone**, **Wireless**, **Tools** e **Help** são usados em determinadas situações e seus usos são bem específicas.

A **Barra de Ferramentas** é a **principal** do WireShark, as funções que estão aqui são as que tem seu uso mais frequente, como **iniciar**, pausar, **reiniciar**, abrir, fechar, **recomeçar** a captura de arquivos e de pacotes, e também podemos navegar entre os pacotes e mudar alguns aspectos da visualização. A baixo dela temos a Barra de Filtro, que contam com botões para ver filtros salvos, mudar a aparência, ver filtros recentes, adicionar mais filtros, e limpar o campo onde colocamos as expressões que realizam o filtro desejado, é possível ver mais sobre esses filtros mais adiante em **Parte Avançada -> Filtros**.

O que mais chama atenção, e ocupa maior parte da tela, é a **Lista de Pacotes**, tem varias colunas que podem ser adicionadas, as que vem por padrão, e que também são as principais mostram **origem**, **destino**, **protocolo**, tempo, e informações sobre o pacote. Abaixo da lista de pacotes no lado esquerdo temos os **Detalhes do Pacote**, e na direita os **Bytes do Pacote**, mostrando mais informações do que esta ocorrendo no pacote analisado.

<figure style="text-align: center;">
  <img src="WireShark Interface.png" style="margin: 0 auto;">
  <figcaption>Interface do WireShark</figcaption>
</figure>

## Parte Avançada


### Filtros

Para usar saber qual filtro usar para achar o que procura, é necessário ter um certo conhecimento de **redes**.

`tcp.analysis.retransmission` - Procura por pacotes retransmitimos.

`tcp.flags.syn == 1 and tcp.flags.ack == 0` - Mostra pacotes usados para começar uma conexão.

`dns.qry.name contains "domain"` - Procura por requisições de pacotes para um domínio especifico.