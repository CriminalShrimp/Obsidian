Sumario
	[[Descoberta de Rede (HUB)]]
	**Tags:** #Redes #Protocolos 
	**Conteúdo:**
		https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml
		**ARP:**
			https://ccna.network/arp/#:~:text=Em%20ambos%20os%20casos%2C%20a,uma%20anima%C3%A7%C3%A3o%20da%20fun%C3%A7%C3%A3o%20ARP.
			https://www.youtube.com/watch?v=t2klOZcXZqc
	
----

Colocar os mais utilizados 

## Address Resolution Protocol (ARP)

O **P**rotocolo de **R**esolução de **E**ndereços é um protocolo que funciona na [[Modelo OSI#Camada 2 - Enlace|camada de enlace]], ele é o responsável por obter o endereço [[Abreviações#MAC = **M**edia **A**ccess **C**ontrol diz respeito ao endereço físico que cada dispositivo tem gravado em sua placa de rede, é como se fosse o CPF de um dispositivo. Ele é representado por 6 pares de caracteres hexadecimais (até 16), ex 00 1A 2B 3C 4D 5E.|MAC]] de um dispositivo a partir de seu endereço IP. Para obter essa informação ele usa duas mensagem, o **ARP Request** que faz a requisição de um endereço IP em um endereço físico. E o **ARP Replay** que manda a reposta a requisição contendo o endereço físico resolvido.

<figure style="text-align: center;">
  <img src="Funcao ARP.gif" style="margin: 0 auto;">
  <figcaption>ARP Request e Replay</figcaption>
</figure>

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

- **Protocol Type (PTYPE):** Tendo **16 bits** nesse campo é especificado o **tipo de protocolo** que esta se comunicando na **camada de rede** (Modelo OSI) ou **camada de internet** (Modelo TCP/IP), geralmente é o IPv4 com o valor 0x8000.

- **Hardware Length (HLEN):** Especifica o o **tamanho do endereço físico** (MAC) que esta sendo usado na rede, ele tem o tamanho de 8 bits dentro do pacote, o seu valor mais comum é 6 que se refere a Ethernet

- **Protocol Length (PLEN):** 8 bits 

- **Operation (OPER):** Define se a **operação** que esta acontecendo é um <span style="color:rgb(65, 105, 255)">ARP Request</span> cujo o valor é <span style="color:rgb(65, 105, 255)">1</span>, e se for um <span style="color:rgb(0, 176, 80)">ARP Replay</span> o valor vai ser <span style="color:rgb(0, 176, 80)">2</span>. O valor desse campo é de 16 bits.

- **Sender Address Hardware (SHA):** 48 bits

- **Sender Protocol Address (SPA):** 32 bits

- **Target Hardware Address (THA):** 48 bits

- **Target Protocol Address (TPA):** 32 bits

## Internet Control Message Protocol (ICMP)



