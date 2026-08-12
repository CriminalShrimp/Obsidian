**Sumário**
	**Tags:** #Redes #Protocolos 
	**Arquivos Relacionados:** [[Descoberta de Rede (HUB)]]
	**Conteúdo:**
		www.youtube.com/watch?v=4I2AZ1by_sY - Vídeo sobre protocolos.
		iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml
		**ARP:**
			https://ccna.network/arp/#:~:text=Em%20ambos%20os%20casos%2C%20a,uma%20anima%C3%A7%C3%A3o%20da%20fun%C3%A7%C3%A3o%20ARP.
			youtube.com/watch?v=t2klOZcXZqc
			geeksforgeeks.org/computer-networks/arp-protocol-packet-format/
		**BGP:**
			cloudflare.com/pt-br/learning/security/glossary/what-is-bgp/
			fortinet.com/br/resources/cyberglossary/bgp-border-gateway-protocol
			youtube.com/watch?v=ivlSUuMF99M - Vídeo Br.
		**DNS:**
			youtube.com/watch?v=shEoRtaB6dE - Vídeo Br.
			
	
----

Colocar os mais utilizados 

# Principais Protocolos 
## Address Resolution Protocol (ARP)

O **P**rotocolo de **R**esolução de **E**ndereços é um protocolo que funciona na [[Modelo OSI e Modelo TCP IP#Camada 2 - Enlace|camada de enlace]], ele é o responsável por obter o endereço [[Abreviações#MAC = **M**edia **A**ccess **C**ontrol diz respeito ao endereço físico que cada dispositivo tem gravado em sua placa de rede, é como se fosse o CPF de um dispositivo. Ele é representado por 6 pares de caracteres hexadecimais (até 16), ex 00 1A 2B 3C 4D 5E.|MAC]] de um dispositivo a partir de seu endereço IP. Para obter essa informação ele usa duas mensagem, o **ARP Request** que faz a requisição de um endereço IP em um endereço físico. E o **ARP Replay** que manda a reposta a requisição contendo o endereço físico resolvido.

<figure style="text-align: center;">
  <img src="Funcao ARP.gif" style="margin: 0 auto;">
  <figcaption>ARP Request e Replay</figcaption>
</figure>

O protocolo ARP possui um cache e um tabela dentro da máquina, ele guarda o endereço dos MACs usados recentemente. Para ver essa tabela com os endereços tanto no Windows quando no Linux o comando é `arp -a`. 

### Pacote ARP

O pacote ARP vem encapsulado em um quadro (frame) da Ethernet, ele possui um tamanho fixo de **28 bytes** (224 bits), em seu cabeçalho temos os seguintes campos:  

<table style="margin: 0 auto; width: 100%; border-collapse: collapse; text-align: center;" border="1">
  <thead>
    <tr>
      <th style="text-align: center">HTYPE</th>
      <th style="text-align: center">PTYPE</th>
      <th style="text-align: center">HLEN</th>
      <th style="text-align: center">PLEN</th>
      <th style="text-align: center">OPER</th>
      <th style="text-align: center">SHA</th>
      <th style="text-align: center">SPA</th>
      <th style="text-align: center">THA</th>
      <th style="text-align: center">TPA</th>
    </tr>
  </thead>
</table>

- **Hardware Type (HTYPE):** Possuindo **16 bits** o campo **Tipo Hardware** define o tipo de protocolo de rede da camada de enlase, para a Ethernet que é o mais comum o valor é **1**.

- **Protocol Type (PTYPE):** Tendo **16 bits** nesse campo é especificado o **Tipo de Protocolo** que esta se comunicando na **camada de rede** (Modelo OSI) ou **camada de internet** (Modelo TCP/IP), geralmente é o IPv4 com o valor 0x8000.

- **Hardware Length (HLEN):** Especifica o **Tamanho do Endereço Físico** (MAC) que esta sendo usado na rede, ele tem o tamanho de 8 bits dentro do pacote, o seu valor mais comum é 6 que se refere a Ethernet

- **Protocol Length (PLEN):** Também especifica o **Tamanho do Endereço**  porém do **Protocolo**, para o protocolo **IPv4** que é o mais comum o valor é **4**, seu tamanho no pacote é de 8 bits.

- **Operation (OPER):** Define se a **Operação** que esta acontecendo é um <span style="color:rgb(65, 105, 255)">ARP Request</span> cujo o valor é <span style="color:rgb(65, 105, 255)">1</span>, e se for um <span style="color:rgb(0, 176, 80)">ARP Replay</span> o valor vai ser <span style="color:rgb(0, 176, 80)">2</span>. O valor desse campo é de 16 bits.

- **Sender Address Hardware (SHA):** É o **Endereço Físico do Remetente**, ou  seja o endereço de quem esta mandando o pacote. Quando é no <span style="color:rgb(65, 105, 255)">ARP Request</span> ele tem o endereço físico de quem mandou, e no <span style="color:rgb(0, 176, 80)">ARP Replay</span> contem o endereço físico procurado, já resolvido. Seu tamanho é de 48 bits.

- **Sender Protocol Address (SPA):** O cabeçalho do **Endereço do Remetente** contem justamente o endereço IP de quem esta mandando o pacote. Seu tamanho é de 32 bits.

- **Target Hardware Address (THA):** **Endereço De Hardware do Alvo** só tem importância no <span style="color:rgb(0, 176, 80)">ARP Replay</span>, pois é somente nele que sabemos o endereço do destino que queremos, no <span style="color:rgb(65, 105, 255)">ARP Request</span> esse valor vem com 0s. o tamanho dele no pacote é de 48 bits.

- **Target Protocol Address (TPA):** E por final o **Endereço de Protocolo do Alvo** que é o endereço IP, é a partir dele que é feita a requisição ARP, a máquina tem o endereço IP e através dele descobre o endereço MAC .O valor desse campo é de 32 bits.

#### Exemplo de Pacote ARP

Um exemplo de um pacote ARP capturado fornecido pela ferramenta e pelo site do [WireShark](https://wiki.wireshark.org/AddressResolutionProtocol).

<figure style="text-align: center;">
  <img src="WireShark ARP.png" style="margin: 0 auto;">
  <figcaption>Pacote ARP</figcaption>
</figure>


## Border Gateway Protocol (BGP)

É o responsável por escolher por qual rota o pacote de dados ira percorrer na internet ate que a mesma chegue me seu destino final, no mundo real seria o sistema de correios que decide para onde cada pacote vai ser mandado. Para entender melhor esse protocolo é necessário antes entender como a internet funciona, ela é uma rede de redes, que é dividida em redes menores, essas por sua vez são chamadas de **AS**, esses **A**utonomous **S**ystem (sistema autônomo) seriam redes que pertencem a um grupo, como ao Google, Apple, Amazon. Usando o BGP é possível declarar que essa rede existe, e por quais redes ela pode ser alcançada, e qual o melhor caminho a ser feito.

Para mantarem suas tabelas sempre atualizadas, os AS fazem **peering** com seus AS vizinhos, que consiste em se conectar com eles e trocar as informações que eles possuem, a comunicação entre eles é feita pela **porta 179**. Os BGP determina o melhor caminho para ser tomado a partir de diversos atributos, por exemplo Local Preference, que é um valor atribuído manualmente, por exemplo se existem um link de operadora com mais banda do que outro, o certo é aumentar o valor do Local Preference desse link. Para ver mais sobre os atributos é possível consultar no [RFC IANA](https://www.iana.org/assignments/bgp-parameters).
Imagine que o seu computador é o AS 1, e quer acessar a rede AS 3 (Google por exemplo), o caminho mais fácil é ir pelo AS 2 pois ele tem menos "saltos", esse caminho é determinado pelo BGP. Caso houver algum problema ele encontraria outro caminho para chegar ao seu destino.

<figure style="text-align: center;">
  <img src="BGP.png" style="margin: 0 auto;">
  <figcaption>BGP</figcaption>
</figure>

Conforme o tempo e a tecnologia foram avançando começaram a surgir problemas com esse protocolo, então foi adicionado a ele o **R**esource **P**ublic **K**ey **I**nfrastructure (**RPKI**), usando criptografia para criar assinaturas confirmando assim a legitimidade de uma rede. Fazendo isso problemas de segurança como [[Denial of Service (DDoS)|DDoS]], BGP hijacking, e [[Ataques de Engenharia Social#Phising|Phinsing]] podem ser evitados facilmente, porém uma grande parte da internet ainda não utilizam esse recurso de segurança.

## Domain Name System (DNS)

Já pensou em ao invés de digitar <span style="color:rgb(206, 0, 86)">youtube.com</span> ter que digitar <span style="color:rgb(0, 176, 80)">142.251.135.238</span>, graças ao DNS podemos escrever os endereços de sites com seu <span style="color:rgb(206, 0, 86)">nome</span> ao invés do seu <span style="color:rgb(0, 176, 80)">endereço IP</span>. Um bom comparativo seria com sua lista de contados, digitamos o nome de Bob por que é mais fácil do que decorar seu numero de telefone. Então para resumir em uma frase, o DNS converte da linguagem humana para a linguagem de computador.

Quando solicitamos um endereço web quem resolve ele para o IP é o e
## Dynamic Host Configuration Protocol (DHCP)

## File Transfer Protocol (FTP)

## Hypertext Transfer Protocol (HTTPs)

## Internet Control Message Protocol (ICMP)

## Quick UDP Internet Connections (Quic)
## Simple Mail Transfer Protocol (SMTP)

## Transmission Control Protocol (TCP/IP)

## Transport Layer Security (TLS)

O novo Secure Sockets Layer (SSL) 

## User Datagram Protocol (UDP)

## WebSocket



