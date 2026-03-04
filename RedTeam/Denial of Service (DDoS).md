**Sumário**
	**Tags:** #Redes #RedTeam 
	**Conteúdo:**
		cloudflare.com/pt-br/learning/ddos/what-is-a-ddos-attack/
		fortinet.com/uk/resources/cyberglossary/dos-vs-ddos
		
----

Ataques de **D**istributed **D**enial **o**f **S**ervice **(DDoS)** e **D**enial **o**f **S**ervice (**DoS**) tem como intuito fazer com que um serviço fique indisponível ou ao menos tenha seu desempenho drasticamente afetado, a única diferença entre esses dois ataques é que o DDoS usa várias máquinas (botnets) para realizar esse ataque, enquanto o DoS usa somente uma máquina para realizar o ataque.

<figure style="text-align: center;">
  <img src="DoS vs DDoS.png" style="margin: 0 auto;">
  <figcaption>DoS x DDoS</figcaption>
</figure>

Existem vários jeitos de realizar esse ataque para sobrecarregar os equipamentos do alvo, no DDoS antes é necessário conseguir uma botnet para realiza-lo. Os tipos de ataques que ocorrem com mais frequência são os **Ataques Volumétricos** que usam as botnets para mandar várias solicitações para o alvo, como o servidor precisa responder muitas solicitações ele começa a apresentar lentidão e pode cair eventualmente, **Ataque à camada de aplicação** que visa fazer o serviço responder solicitações HTTP, que são pesadas para o servidor pois envolve carregar diversos arquivos para entregar a respostar a quem solicitou, **Ataques de protocolo** que visam consumir recursos dos equipamentos como firewalls, **Inundação SYN** que explora o handshake TCP para realizar o ataque, onde ele prepara um pacote e fica esperando a confirmação para entregá-lo, essa confirmação que nunca chega e ao mesmo tempo mais pacotes assim ficam chegando, existem diversos outros tipos de ataques "D"DoS.