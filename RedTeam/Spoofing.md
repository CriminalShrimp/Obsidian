**Sumário**
	**Tags:** #RedTeam 
	**Conteúdo:**
		kaspersky.com.br/resource-center/definitions/spoofing - Spoofing Geral
		cloudflare.com/pt-br/learning/ddos/glossary/ip-spoofing/ - Spoofing IP
		

----

Spoofing é quando um atacante fingem ser uma entidade confiável, como pessoas, empresas, ou máquinas para obter a confiança da vítima. A ação visa roubar ou obter dados, informações pessoais ou transferência de dinheiro, além de poder ser usado para disseminar [[malware]]. 

- **[[Protocolos#Address Resolution Protocol (ARP)|ARP]] Spoofing:** Quando o atacante consegue ter acesso a rede ele pode utilizar ferramentas como o [[Ettercap]] para descobrir o [[Abreviações#MAC = **M**edia **A**ccess **C**ontrol diz respeito ao endereço físico que cada dispositivo tem gravado em sua placa de rede, é como se fosse o CPF de um dispositivo. O. Ele é representado por 6 pares de caracteres hexadecimais (até 16),os primeiros 6 dígitos (3 bytes) indicam o fabricante, e Os últimos 6 dígitos (3 bytes) são atribuídos pelo fabricante para identificar a placa de rede específica ex 00 1A 2B 3C 4D 5E.|MAC]] e o IP dos dispositivos, após isso ele envia mensagem de resposta ARP (**ARP Replay**) forjadas se passando como um desportivo legitimo na rede, assim adicionando seu desportivo na tabela ARP das máquinas na rede. A Partir desse ponto a rede passa a confiar na máquina, fazendo com que o atacante possa interceptar o trafico da rede, resultando em um **ARP Poisoning**.
 ^5b9ca3
- **Spoofing de IP:** É a criação de pacotes de IP com endereços de origem modificados para ocultar a identidade do remetente, fingindo ser outro sistema de computador. É uma técnica usada com frequência por atacantes para fazer ataques [[Denial of Service (DDoS)|DDoS]]. Se o pacote tiver sido falsificado o endereço de origem também será falso, uma analogia seria alguém enviar um pacote a com o endereço de devolução errado. Com frequência, os ataques de DDoS usam a falsificação com o objetivo de sobrecarregar o alvo e ao mesmo tempo, mascarar a real origem do atacante.

- **Spoofing de [[Protocolos#Domain Name System (DNS)|DNS]]:** Também chamado de envenenamento cache de DNS, é um ataque no qual registros de DNS são alterados fazendo com que a vítima seja levada para outro site. Os atacantes fazem isso substituindo os endereços IPs armazenados no servidor de DNS pelos endereços que desejam.

- **Spoofing de e-mail:** Ocorre quando o atacante passa por uma empresa ou alguém em um e-mail com o intuito de fazer a vítima cai em um golpe, seja roubar dados, fazer uma transferência, ou baixar um anexo que possa conter um [[Malware]]. A taxa de sucesso aumenta com a capacidade de convencer a vítima a acreditar que o que ela está vendo é legítimo, fazendo com que ela abra um anexo, transfira dinheiro, etc.

- **Spoofing de telefone:** Podem ser feitas por spoofing de ligações ou por mensagem de textos se passando por uma empresa ou alguém próximo com o objetivo de adquirir alguma informação, dinheiro ou infectar a vitima com algum arquivo malicioso.

- **[[Abreviações#URL = **U**niform **R**esource **L**ocator é o endereço único e específico de um recurso na internet, como um site, imagem ou arquivo, funcionando como um "CEP digital".|URL]] Spoofing:** Atacantes criam sites ou URls falsos para fazer as vitimas caírem em golpes, serem infectadas ou revelarem dados sensíveis. Isso é feito usando caracteres parecidos como **O** e **0**, usando caracteres de diferentes alfabetos com o "а" do alfabeto Cyrillic que tem seu valor na tabela [[Abreviações#ASCII = **A**merican **S**tandard **C**ode for **I**nformation **I**nterchange é um sistema de representação de letras, algarismos e sinais de pontuação e de controle, através de um sinal codificado em forma de código binário.|ASCII]] de U+0430, e o "a" do alfabeto Latino cujo seu valor é de U+0061.


