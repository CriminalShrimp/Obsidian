**Sumário**
	**Tags:** #Redes #Protocolos 
	**Arquivos Relacionados:** [[Descoberta de Rede (HUB)]]
	**Conteúdo:**
		www.youtube.com/watch?v=4I2AZ1by_sY - Vídeo sobre protocolos.
		iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml
		**ARP:**
			https://ccna.network/arp/.
			youtube.com/watch?v=t2klOZcXZqc.
			geeksforgeeks.org/computer-networks/arp-protocol-packet-format/.
		**BGP:**
			cloudflare.com/pt-br/learning/security/glossary/what-is-bgp/ - Material de leitura.
			fortinet.com/br/resources/cyberglossary/bgp-border-gateway-protocol.
			youtube.com/watch?v=ivlSUuMF99M - Vídeo Br.
		**DNS:**
			youtube.com/watch?v=shEoRtaB6dE - Vídeo Br.
			youtube.com/watch?v=NiQTs9DbtW4 - Vídeo avançado.
			youtube.com/watch?v=mpQZVYPuDGU - Animação da requisição do pacote DNS.
			cloudflare.com/learning/dns/what-is-dns/ - Material de leitura.
			computernetworkingnotes.com/linux-tutorials/types-of-resources-records-in-zone-files.html - Sobre DNS Zone Files.
	
----


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

Já pensou em ao invés de digitar <span style="color:rgb(206, 0, 86)">studio.youtube.com</span> ter que digitar <span style="color:rgb(0, 176, 80)">142.251.135.238</span>, graças ao DNS podemos escrever os endereços de sites com seu <span style="color:rgb(206, 0, 86)">nome</span> ao invés do seu <span style="color:rgb(0, 176, 80)">endereço IP</span>. Um bom comparativo seria com sua lista de contados, digitamos o nome de Bob por que é mais fácil do que decorar seu numero de telefone. Então para resumir em uma frase, o DNS converte da linguagem humana para a linguagem de computador.

Quando solicitamos um endereço web ele verifica na memoria cache do PC se o endereço já foi pesquisado antes (o comando `ipconfig /displaydns` mostra assa tabela), depois ele passa parra o roteador, então para o [[Abreviações#ISP = **I**nternet **S**ervice **P**rovider responsável por prover a internet ao usuario, pode ser a Vivo, Claro, Nio, etc.|ISP]], se mesmo assim nada retornar do endereço, o seu ISP repassa a requisição para a **root zone**, nela existem **"13 DNS Root servers"** que apontam diretamente ao **T**op **L**evel **D**omain (<span style="color:rgb(255, 255, 0)">TLD</span>) , responsável por exemplo pelos domínios *.com*, que indica para o **S**econd **L**evel **D**omain (<span style="color:rgb(255, 255, 0)">SLD</span>) responsável pelo *youtube* no nosso exemplo, e não saiba o endereço, por final indicara ao seu ISP o servidor que contem o site em questão o **Authoritative Servers**, que possuem um arquivo chamado de **DNS Zone File**, e em um campo dele chamado **DNS Record**, tem todas as informações relacionadas a o <span style="color:rgb(206, 0, 86)">youtube.com</span>, e também seus subdomínios como o <span style="color:rgb(206, 0, 86)">studio.youtube.com</span>, e seu IP desejado. Esse cenário é uma situação resumida e bem anormal, já que em todos esses passos existe a memoria cache que normalmente já retorna o nome resolvido para o endereço.

<figure style="text-align: center;">
  <img src="DNS Protocol.gif" style="margin: 0 auto;">
  <figcaption>Comunicação simples de um DNS</figcaption>
</figure>

A hierarquia dessas zonas DNS vão do Root, para TLD, SLD e por fim para subdomínios.

<figure style="text-align: center;">
  <img src="DNS Zone.png" style="margin: 0 auto;">
  <figcaption>DNS Zones</figcaption>
</figure>

### 13 Root DNS Servers

Não são 13 servidores físicos, mas sim 13 endereços de IP que vão de a.root-server.net até m.root-server.net, o numero 13 esta relacionado ao limite de bytes do protocolo **UDP**, esses 13 endereçõs são operados por diferentes organizações ao longo do globo. A verdade é que existe milhares de servidores DNS espalhados pelo mundo.

<figure style="text-align: center;">
  <img src="13 Root DNS Servers.png" style="margin: 0 auto;">
  <figcaption>13 Root DNS</figcaption>
</figure>

### DNS Zone File

Nesse arquivo temos as configurações e os registros relacionados aos seus dominós, esses arquivos são guardados *.txt*. Mandatoriamente esse arquivo deve ter dois campos, o [[Abreviações#TTL = **T**ime **t**o **L**ive é um campo no pacote IP, que determina quanto tempo um pacote pode viajar pela internet, pode chamar de "hops", pois ele pula de roteador a roteador. Uma informação útil é que Windows tem o TTL de 128, e Mac e Linux de 64.|TTL]] que por padrão é de 86400s ou 1 dia, e o **ORIGIN** que define um domínio [[Abreviações#FQDN = **F**ully **Q**ualified **D**omain **N**ame diz respeito ao endereço exato de um dispositivo ou recurso na internet.|FQND]](example.com.) para todo o arquivo, e ao longo do arquivo ele pode ser referenciado por um nome relativo (e-mail ou blog), um **@** ou pode ser deixado em branco. Aqui temos um exemplo de um desses arquivos. 

<figure style="text-align: center;">
  <img src="DNS Zone File.png" style="margin: 0 auto;">
  <figcaption>Exemplo de DNS Zone File</figcaption>
</figure>

#### DNS Records

Esses registros dizem respeito as características e propriedades "entidades" presentes nesse domínio. Existem vários tipos desses registros, mas **obrigatoriamente** deve sempre haver um **Start Of Authority (SOA)**.
##### Start Of Authority (SOA)

Nele configuramos certas características e parâmetros sobre o servidor, para explicar melhor vamos usar um registro como exemplo.

<span style="color:rgb(112, 48, 160)">youtube.com.</span>    60    <span style="color:rgb(206, 0, 86)">IN</span>    <span style="color:rgb(0, 176, 80)">SOA</span>    <span style="color:rgb(65, 105, 255)">ns1.google.com.</span> <span style="color:rgb(255, 255, 0)">dns-admin.google.com.</span> (
                                   611537233  ; Serial number
                                   900        ; Refresh Time
                                   900        ; Retry Time
                                   1800       ; Expire Time
                                   60         ; Next-domain-TTL
)

Sobre os campos desse registros, temos <span style="color:rgb(112, 48, 160)">domain-name</span> que tem as mesma propriedades do **ORIGIN** comentando anteriormente. O numero **60** diz respeito ao **TTL**. A <span style="color:rgb(206, 0, 86)">class</span> que pode ser <span style="color:rgb(206, 0, 86)">IN</span>, <span style="color:rgb(206, 0, 86)">CH</span>, e <span style="color:rgb(206, 0, 86)">HS</span>, mas o **IN** é o mais usado, os outros são para casos específicos. O <span style="color:rgb(0, 176, 80)">record-type</span> que nesse caso é o SOA, esse campo muda conforme o registro. No campo <span style="color:rgb(65, 105, 255)">name-server</span> definimos qual nome autorizado para esse domínio. E o <span style="color:rgb(255, 255, 0)">email-address</span> pode ser colocado qualquer e-mail valido, normalmente é colocado o do responsável pelo *host*, algo para se saber é que o primeiro (.) é substituído por um @.

O jeito que o DNS vê o SOA é da seguinte forma (convertido para minutos os tempos): 

**@ IN SOA ://google.com. ://google.com. 611537233 15m 15m 30m 1m**

Nele temos os campos que ficam no parênteses no SOA, por primeiro o **Serial Number** usado para diversas coisas, mas o uso mais comum é o de **rastrear mudanças e atualizações**, esse numero normalmente é usado como **ANO-MES-DIA** e uma sequencia de **00** ate **99**. O **Refresh Time** indica de quanto em quanto tempo ele deve **buscar por atualizações** no servidor *mestre*. No **Retry Time** indicamos o **período de tempo que ele deve ser comunicar com o servidor mestre** caso falhe a comunicação com o servidor *mestre*. O **Expire Time** indica por quanto tempo os **registros serão validos**. E por final o **Next-domain-TTL** que de forma básica, caso um ele tente resolver para um endereço que não esteja no arquivo entra retorna o erro **Name Error (NXDOMAIN)**, e entra no campo **negative-cache-TTL** (mesma coisa que Next-domain-TTL), somente depois do tempo determinado no campo ele tentara novamente para o nome do domínio que deu erro.
##### Name Server (NS)

Indica quais os servidores DNS autorizados para o domínio, sempre deve haver ao menos **dois registros** desses no arquivo, também pode ser apontando um nome de servidor externo. Um exemplo desse registro seria assim:

; The NS records.
; Primary or main NS server. Available within the domain.
    3w	IN 	NS 	ns1.example.com.
; Secondary or backup NS server. Available outside the domain.
        IN 	NS 	ns2.example.net.

##### ### Mail Exchanger (MX)

Esse é opcional, caso não tenha serviços de e-mail não precisa adiciona-lo, também pode ser apontando um nome de servidor externo. Um exemplo desse registro seria assim:
 
; The MX records
; Primary or main NS server. Available within the domain.
    3w 	IN 	MX 	10 	mail.example.com.
; Secondary or backup NS server. Available outside the domain.
        IN 	MX 	20 	mail.example.net.

##### Address (A)

Caso houver um serviço ou *host* que precisar ser publico, deve ser definido seu endereço IPv4 nesse registro, é um registro opcional. Um exemplo de desse registro seria assim:  

; The A records
ns1 		IN	 A 	172.168.1.1
mail 		IN	 A 	172.168.1.2
www 		IN 	 A 	172.168.1.3

##### Quad A (AAAA)

Igual o anterior porém para endereços IPv6. Um exemplo desse registro seria assim:  

; The AAAA
ns1 		IN	 AAAA 	2002:db7::
mail 		IN	 AAAA	2002:db8::
www 		IN 	 AAAA 	2002:db9::
##### Canonical Name (CNAME)

Caso existir um "apelido" para o seu endereço ele será redirecionado para o endereço apontado, esse campo também é opcional. Um bom exemplo é o google, que tem o domínio faltando um o, e que quando buscado redireciona para seu endereço oficial. 

; The CNAME
gogle.com 		IN	 CNAME 	google.com.
www 		    IN	 CNAME 	google.com.

##### Pointer (PTR)

Ele funciona como se fosse um <span style="color:rgb(255, 255, 0)">DNS Reverso</span>, que funciona como uma solução para manter a logica do especifico para o geral, igual é feito no domínios (lido da direita para esquerda), para fazermos isso basta pega o IP (142.251.135.238), e inverter a ordem (238.135.251.142), e no final dele adicionar o endereço in-addr.arpa (no IPv4), com isso ao digitar um **IP** ele traduz para um **nome**, também é um campo opcional. Um exemplo de registro desse seria assim: 

; The PTR
238		IN	 PTR 	youtube.com.

Nesse caso o servidor estaria previamente configurado para gerenciar essa rede, usando essa configuração:

zone "135.251.142.in-addr.arpa" { 
	type master; 
	file "/etc/bind/db.142.251.135"; # Caminho do arquivo onde vão as regras };

Mas caso não houver essa configuração é necessário colocar ele por completo,
; The PTR
238.135.251.142.in-addr.arpa.		IN	 PTR 	studio.youtube.com.
##### Server (SRV)

Quando temos um serviço que roda em uma porta especifica, precisamos usar esse registro para apontar para o **endereço** e o **numero da porta**, também é opcional. Um exemplo de registro desse seria assim:  

`_xmpp-server._://youtube.com. 3600 IN SRV 10 20 5269 ://google.com.`

Aqui o <span style="color:rgb(255, 255, 0)">xamp</span> é o <span style="color:rgb(255, 255, 0)">serviço</span> rodando, <span style="color:rgb(65, 105, 255)">://</span> diz respeito ao protocolo que é o <span style="color:rgb(65, 105, 255)">TCP</span>, <span style="color:rgb(206, 0, 86)">youtube</span> é o nossos <span style="color:rgb(206, 0, 86)">domínio</span>, 3600 o TTL, <span style="color:rgb(0, 176, 80)">10</span> é a <span style="color:rgb(0, 176, 80)">prioridade</span>, o **uso** será sempre para o servidor configurado com o **menor numero**, temos o <span style="color:rgb(112, 48, 160)">20</span> que se refere a o <span style="color:rgb(112, 48, 160)">peso</span>, que é usado para o [[Balanceador de Carga]] decidir para qual servidor mandar mais carga, porém ele é usado somente quando ambos os servidores tem a mesma prioridade, o maior valor nesse campo recebe mais carga, e finalmente o numero **5269**, é a **porta** em que o serviço esta rodando.

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



