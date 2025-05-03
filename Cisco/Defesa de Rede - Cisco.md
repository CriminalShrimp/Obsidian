Exercícios [[Exercicios|aqui]].
#Redes #Firewall #Segurança #Ferramentas #RedTeam
# Modulo 1: Compreendendo a Defesa
## Defesa em profundidade
Objetivo: Explicar como a estratégia de Defesa de profundidade é usada para proteger as redes.

Analistas de segurança devem ser capazes de identificar qual tipo de ataque esta ocorrendo e se preparar para como reagir, um dos passos é identificar na empresa quais são os <span style="color:rgb(255, 255, 0)">Ativos</span> que seriam qualquer coisa de valor para uma organização e que deve ser protegida, incluindo servidores, dispositivos de infraestrutura, dispositivos finais e o maior ativo, dados. <span style="color:rgb(65, 105, 255)">Vulnerabilidades</span> no sistema ou no design que pode ser explorada por um agente de ameaça. E as <span style="color:rgb(206, 0, 86)">Ameaças</span> que são qualquer perigo em potencial para um ativo.

### Identificando os Ativos
Os ativos são todas as superfícies de ataques que um atacante pode atingir, a coleta de todos e quaisquer dados seriam os ativos das empresas, esses ativos podem ter importâncias e níveis de segurança diferentes entre eles. A identificação e categorização podem ser feitas em 4 etapas sendo elas.

Etapa 1: Determinar a categoria de identificação de ativos adequada que podem ser Ativos de informações, Ativos de software, Ativos físicos e Ativos de Serviços.

Etapa 2: Estabeleça a responsabilização, identificando o proprietário de todos os ativos de informações e de softwares de aplicativos.

Etapa 3: Determinar os critérios de classificação que podem ser: Confidencialidade, Valor, Tempo Direitos de Acesso e  Destruição.

Etapa 4: Implemente um esquema de classificação, adotando uma maneira uniforme de identificação de informações para assegurar a proteção uniforme.

Assim como na vida os ativos tem um ciclo de vida, o primeiro é a <span style="color:rgb(255, 255, 0)">Aquisição</span>, empresa compra os ativos de acordo com as necessidades identificadas nos dados coletados para justificar a compra. <span style="color:rgb(255, 255, 0)">Implantação</span>, o ativo é montado e inspecionado para verificar se há falhas ou outros problemas, a equipe realiza testes e instala tags ou códigos de barras para fins de rastreamento. <span style="color:rgb(255, 255, 0)">Utilização</span>, essa é a fase mais longa do ciclo, o desempenho do ativo é verificado continuamente, atualizações, correções de patches, compras de novas licenças e auditorias de conformidade fazem parte do estágio de utilização. A <span style="color:rgb(255, 255, 0)">Manutenção</span> ajuda a prolongar a vida produtiva de um ativo, os funcionários podem modificar ou atualizar o recurso. E ao final da vida produtiva do ativo, ele deve ser descartado, todos os dados devem ser apagados do recurso, o descarte pode incluir a desmontagem de um ativo para peças, finalizando assim o ciclo com a <span style="color:rgb(255, 255, 0)">Eliminação</span>.
### Identificando as Vulnerabilidades
Identificar as possíveis ameaças para cada ambiente fornece uma lista de ataques mais prováveis de ocorrerem. A varias perguntas  que podem ser feitas para descobrir essas vulnerabilidades como: Quem pode explorar as vulnerabilidades? Quais são elas? O que sistemas parecidos sofreram e sofrem de ataques? O que ocorrera quando/se os ativos forem perdidos e as vulnerabilidades do sistema exploradas? 
Vamos exemplificar usando como exemplo um e-banking 
![[e-banking.webp]]
A identificação da ameaça para um sistema de banca electrónica incluiria:
• Compromisso interno do sistema - O atacante usa os servidores de e-banking expostos para invadir um sistema bancário interno.
• Dados roubados - Um atacante rouba os dados pessoais e financeiros dos clientes bancários do banco de dados do cliente.
• Transações falsas de um servidor externo - Um invasor altera o código do aplicativo de e-banking e faz transações personificando um usuário legítimo.
• Transações falsas - Um invasor rouba a identidade de um cliente e conclui transações mal-intencionadas da conta comprometida.
• Ataque insider no sistema - Um funcionário do banco encontra uma falha no sistema a partir disso realiza um ataque.
• Erros de entrada de dados - Um usuário insere dados incorretos ou faz solicitações de transação incorretas.
• Destruição do data center - Um evento cataclísmico danifica gravemente ou destrói o data center.
É importante na hora de identificar as vulnerabilidades entender usa regra de negocio e seu meio para ter uma ideia do que pode acontecer com sua empresa.
### Identificando as Ameaças
Usar a abordagem de defesa profunda para identificar ameaças e proteger ativos vulneráveis. Essa abordagem usa várias camadas de segurança, uma analogia muito comum é falar de "segurança cebola" mais popularmente conhecida como <span style="color:rgb(255, 255, 0)">onion security</span>, um ator de ameaça teria que descascar as defesas de uma rede camada por camada de uma maneira semelhante a descascar uma cebola, somente depois de penetrar cada camada, o ator da ameaça alcançaria os dados ou o sistema de destino.

![[security onion.webp]]
Porem esse conceito vem mudando com o tempo e agora é usado o "alcachofra de segurança" no inglês <span style="color:rgb(255, 255, 0)">security artichoke</span>, onde não se precisa mais ir camadas por camadas para chegar no objetivo e sim ir tirando as "folhas" e obtendo dados/informações para conseguir realizar suas ações maliciosas, por exemplo, é mais fácil para um agente de ameaça comprometer um dispositivo móvel do que comprometer um computador ou servidor interno protegido por camadas de defesa. Cada dispositivo móvel é uma folha, e folha após folha, tudo leva o hacker a mais dados. O coração da alcachofra é onde os dados mais confidenciais são encontrados. Cada folha fornece uma camada de proteção enquanto fornece simultaneamente um caminho para o ataque, nem todas as folhas precisam ser removidas para chegar ao coração da alcachofra.
![[alcachofra.webp]]
## Gerenciamento de operações de segurança cibernética
As configurações realizadas no ambiente são fundamentais para no futuro serem fitas mudanças, auditorias, controle e identificação no sistema. Configurar os arquivos de [[Abreviações#Log = Abreviação de logfile (arquivo de registro) ou logging (processo de registro de eventos|LOG]] é importante para quando for realizado uma auditoria de quando ouve um ataque ou uma defesa bem sucedida, ou também para controle de atividades dos usuários, claro que quando maior a empresa mais logs são gerados então devem entrar um trabalho de gerenciamento dos mesmos.
Outra coisa importante de se ter para analisar são os pacotes de rede, quando se ter ferramentas para capturar esses pacotes e analisa-los é possível saber fazer uma análise de problemas de rede, detecção de uso indevido da rede, tentativas de invasão da rede, etc. Existem vários desses analisadores como [[Ferramentas/Ferramentas#Wireshark = O [WireShark](https //www.wireshark.org/) (anteriormente conhecido como Ethereal) é um programa que analisa o tráfego de rede, e o organiza por protocolos. As funcionalidades do Wireshark são parecidas com o tcpdump mas com uma interface gráfica, com mais informação e com a possibilidade da utilização de filtros.|WireShark]], [[Ferramentas/Ferramentas#TCPDump = O comando [tcpdump](https //www.ibm.com/docs/pt-br/aix/7.3?topic=t-tcpdump-command) imprime os cabeçalhos de pacotes em uma interface de rede que combinam com a expressão booleana. Você pode executar o comando com o sinalizador -w para salvar os dados do pacote em um arquivo para análise adicional.|TCPDump]], Ettercap, Kismet, Ngrep, Ntop, Etherape, entre outras.
## Políticas, regulamentos e padrões de segurança
#baboseira
Políticas de negócios são as diretrizes que são desenvolvidas por uma organização para governar suas ações. As políticas definem padrões de comportamento correto para a empresa e seus funcionários, na rede as políticas definem as atividades permitidas na rede. Se um comportamento que viola a política de negócios for detectado na rede, é possível que tenha ocorrido uma violação de segurança. Uma organização pode ter várias diretivas orientadoras como <span style="color:rgb(255, 255, 0)">Politica da Empresa</span> que definem as responsabilidades dos trabalhadores e suas condutas como vestimenta, privacidade, assim também como proteger seus direitos e interesses. Também existem as <span style="color:rgb(255, 255, 0)">Politicas de Funcionários  </span>que são criadas e mantidas pelos Recursos Humanos para identificar, benefícios, salários, feiras, etc. E por fim as <span style="color:rgb(255, 255, 0)">Politicas de Segurança</span> que especificam requisitos do sistema, regras e comportamento dos usuários, esse conjunto de regras e requisitos garantem a segurança dos sistemas e redes de computador de uma empresa.
### Politica de Segurança 
Uma política de segurança abrangente estabelece diretrizes para proteger os ativos tecnológicos e informacionais de uma organização. Seus benefícios incluem demonstrar compromisso com a segurança, definir regras de comportamento, garantir consistência nas operações, estabelecer consequências para violações e oferecer suporte da gestão ao setor de segurança. Além disso, informa usuários, funcionários e gestores sobre os requisitos de segurança, especifica mecanismos de proteção e serve como referência para aquisição, configuração e auditoria de sistemas e redes.
As políticas de segurança abrangem diversas diretrizes essenciais como quem pode acessar a rede e os procedimentos de verificação de identidade, estabelece requisitos mínimos e a necessidade de alteração periódica das senhas, determina os aplicativos e usos permitidos na rede, além das consequências por violações, regula como e o que os usuários remotos podem acessar, define procedimentos para atualização de sistemas e aplicativos e especifica a resposta a incidentes de segurança.
### Políticas de BYOD
Hoje em dia é comum ver empresas com a cultura do [[Abreviações#BYOD = Bring Your Own Device, levar os próprios dispositivos para o trabalho|BYOD]], pois essa positiva traz vários benefícios para empresa como redução de custos com equipamentos para empresa, aumento na produtividade pois os colaboradores se sentem mais confortáveis usando seus dispositivos, porém para aderir essa politica é preciso também preparar o ambiente e funcionários para isso, como usar senhas exclusivas para cada dispositivo e conta, conecte-se apenas a redes confiáveis, mantenha sempre o sistema operacional do dispositivo e outros softwares atualizados, ativar o backup do dispositivo para evitar perda de dados em caso de roubo ou extravio, utilizar serviço de rastreamento de dispositivos que permita localização e apagamento remoto dos dados, utilizar antivírus.
# Modulo 2 : Defesa do Sistema e da Rede
## Segurança Física
Barreiras físicas dizem respeito a meios de limitar a entrada de indevidos não autorizados ou indevidos a certos locais/áreas, normalmente elas são cerceamentos ou barreiras físicas , áreas de alta segurança geralmente requerem uma “proteção superior”, como arame farpado ou fio de arame farpado, cerca elétrica, guardas atuam como um impedimento adicional e podem atrasar o invasor, causando ferimentos graves. Uma das mais comum para autenticação e confirmação de acesso de uma pessoa são as seguranças por biometria, sistemas de autenticação de biometria incluem medições da face, impressão digital, geometria da mão, íris, retina, assinatura e voz. Outra forma de autenticação comum e identificação nas áreas de trabalho é o crachá, que é feito com o auxílio de um leitor de cartão, quanto mais etapas de identificação melhor será a segurança física do local.
## Segurança de Aplicações
Durante a criação de um sistema o software deve ser desenvolvido e atualizado em um ambiente de desenvolvimentos, pois esse é um ambiente seguro para o sistema poder conter falhas de código pois. Depois do o sistema segue para o ambiente de preparo que simula o real ambiente onde o código ira funcionar, neste ambiente os desenvolvedores podem verificar se o código esta sendo executando corretamente e com os padrões de segurança necessário, e também podem realizar de alguns testes.
Técnicas como ofuscação e camuflagem são usadas para proteger o software contra engenharia reversa. A ofuscação oculta dados originais com caracteres ou informações aleatórias, enquanto a camuflagem substitui dados confidenciais por versões fictícias realistas. A reutilização de código permite economizar tempo e custos ao usar software existente para criar novos programas, mas deve ser feita com cuidado para evitar vulnerabilidades. Os SDKs e bibliotecas de terceiros aceleram o desenvolvimento ao fornecer código pronto para uso, porém, qualquer falha de segurança nesses componentes pode afetar múltiplos aplicativos.
## Fortalecimento da Rede 
Criminosos exploram serviços de rede vulneráveis para ataques, incluindo scanners de porta para identificar acessos desprotegidos. Para mitigar riscos, é essencial fechar portas desnecessárias e proteger serviços como DHCP, DNS, ICMP, RIP e NTP. Adoção de firewalls, monitoramento, atualizações e autenticação são medidas essenciais para garantir a segurança da rede.

**[[Abreviações#DHCP = Dynamic Host Configuration Protocol é um protocolo de rede que atribui automaticamente endereços IP a dispositivos.|DHCP]]**: Pode ser explorado para negar acesso à rede. Medidas de segurança incluem rastreamento de DHCP e proteção do servidor.

**[[Abreviações#DNS = Domain Name System é o que traduz IPs em nomes de domínio.|DNS]]**: Alvo de ataques para redirecionamento de tráfego e negação de acesso. Adoção de [[Abreviações#DNSSEC = Domain Name System Security Extensions é um conjunto de extensões que adiciona segurança ao protocolo DNS.|DNSSEC]] e autenticação entre servidores aumenta a segurança.

**[[Abreviações#ICMP = Internet Control Message Protocol faz parte do protocolo IP e é usado para comunicar informações de nível de rede.|ICMP]]**: Usado para testes de conectividade, mas pode ser explorado para ataques [[Abreviações#DoS = DenialofService é um ataque que visa tornar um serviço ou dispositivo indisponível para os usuário.|DoS]], fazer a filtragem de ICMP reduz riscos.

**[[Abreviações#RIP = Protocolo de Informação de Roteamento permite que roteadores troquem informações sobre rotas em uma rede,|RIP]]**: Protocolo de roteamento vulnerável a ataques que afetam desempenho e disponibilidade. 

[[Abreviações#NTP = Network Time Protocol sincroniza os relógios de computadores em uma rede.|NTP]]: Fundamental para a sincronização de tempo e segurança digital, e também autenticação protege contra manipulações maliciosas.
## Blindagem de Rede
### VLans
 VLANs são baseadas em conexões lógicas, enquanto LANs são baseadas em conexões físicas. Portas individuais de um switch podem ser atribuídas a uma VLAN específica. Outras portas podem ser usadas para interconectar fisicamente os switches e permitir o tráfego de várias VLANs entre os switches. Essas portas são chamadas <span style="color:rgb(255, 255, 0)">Trunks</span>.  As VLANs fornecem uma forma de agrupar dispositivos em uma LAN e em switches individuais, além disso os administradores usam VLANs para segmentar redes com base em fatores como função, equipe ou aplicativo. Os dispositivos em uma VLAN atuam como se estivessem em sua própria rede independente, mesmo que compartilhem uma infraestrutura comum com outras VLANs. Uma VLAN pode separar grupos que têm dados confidenciais do resto da rede, diminuindo as chances de violações de informações confidenciais Os hackers podem atacar também a disponibilidade e o desempenho da VLAN. Para proteger a VLAN, monitorar seu desempenho, usar configurações avançadas e instalar regularmente patches e atualizações.
### DMZ 
DMZ ou zona desmilitarizada é uma pequena rede entre uma rede privada confiável e a Internet, servidores Web e de e-mail geralmente são colocados na DMZ para permitir que os usuários acessem uma rede não confiável, como a Internet, sem comprometer a rede interna.
A maioria das redes tem de duas a quatro zonas de risco: a LAN privada confiável, a DMZ, a Internet e uma extranet. Na zona de LAN, o nível de risco é baixo e o nível de confiança é alto. Na zona da extranet, o nível de risco é médio-baixo e o nível de confiança médio-alto. Na DMZ, o nível de risco é médio-alto e o nível de confiança é médio-baixo. Na zona da Internet, o nível de risco é alto e o nível de confiança é baixo. 
## Resiliência de Cyber Segurança
O [[Abreviações#WAP = Wi-Fi Protected Access é um padrão de segurança para dispositivos|WAP]] foi a resposta do setor de computadores para enfraquecer a utilização do padrão WEP. A configuração mais comum de WPA é WPA-PSK (Pre-Shared Key). O WPA3 adicionou mais recursos ao WPA2, como a manutenção de algoritmos criptográficos robustos e a melhoria da troca de chaves.
Dispositivos móveis e sem fio se tornaram o tipo predominante de dispositivos na maioria das redes modernas. Eles oferecem mobilidade e conveniência, mas estão vulneráveis a diversos problemas de segurança digital. Essas vulnerabilidades incluem roubo, invasão e acesso remoto não autorizado, PSK é a sigla para "Pre-Shared Key" (chave pré-compartilhada). É um mecanismo de segurança que permite estabelecer uma conexão segura entre um dispositivo e um ponto de acesso Wi-Fi, [[Snaffing]], ataques [[Man-in-the-Middle]] e DoS.
A melhor forma de proteger uma rede sem fio é usar autenticação e criptografia. O padrão 801.11, introduziu dois tipos de autenticação, a de sistema aberto onde qualquer dispositivo pode se conectar à rede sem fio que é usado quando segurança não é um preocupação, e a de chave compartilhada que fornecer mecanismos para autenticações e criptografia dos dados trafegados.

## Disponibilidade do sistema
O termo alta disponibilidade descreve sistemas concebidos para evitar períodos de inatividade. A disponibilidade contínua de sistemas de informação é imprescindível, não só para as empresas, mas para a vida moderna, já que todos nós usamos e dependemos de computadores e sistemas de informação mais do que nunca. Dentre as práticas mais populares de alta disponibilidade estão os cinco noves. Ela recebe esse nome do objetivo de atingir uma taxa de disponibilidade de 99,999%, ou seja, cinco noves em seguida. Isso significa que o período de inatividade é menos de 5,26 minutos por ano.
A redundância N+1 garante a disponibilidade do sistema, no caso de falha de um componente. Os componentes (N) precisam ter, no mínimo, um componente de backup (+1). Uma boa maneira de pensar sobre isso é que, no caso de um piso plano, um carro tem quatro pneus (N) e um sobressalente (+1) no porta-malas. Embora um sistema N + 1 contenha equipamento redundante, não é um sistema totalmente redundante.

### RAID
O RAID obtém os dados normalmente armazenados em um único disco e os espalha entre várias unidades. Se qualquer disco único RAID0 for perdido, o usuário poderá recuperar os dados de outros discos que também hospedam os dados. Também pode aumentar a velocidade da recuperação de dados, já que várias unidades recuperarão os dados solicitados mais rapidamente do que um disco fazendo o mesmo.
![[RAID.webp]]

### Spanning Tree 
A redundância aumenta a disponibilidade da infraestrutura da rede, protegendo-a de um ponto único de falha, como um cabo ou um switch com falha na rede.
Quando os designers projetam a redundância física em uma rede, pode haver loops e quadros duplicados. Os loops e quadros duplicados têm consequências graves para uma rede comutada.
O [[Abreviações#STP = Spanning Tree Protocol previne loops em uma rede quando os switches se interconectarem por vários caminhos|STP]] soluciona esses problemas. A função básica do STP é prevenir loops em uma rede, quando os switches se interconectarem por vários caminhos. O STP garante que os links físicos redundantes estejam livres de loop e que apenas um caminho lógico seja executado entre todos os destinos na rede. O STP bloqueia intencionalmente os caminhos redundantes que poderiam provocar um loop.
Bloquear os caminhos redundantes é fundamental para evitar loops na rede. Os caminhos físicos ainda existirão para fornecer redundância, mas o STP desativa esses caminhos para evitar que ocorram loops. Se um cabo ou switch da rede falhar, o STP recalculará os caminhos e desbloqueará as portas necessárias, para permitir que o caminho redundante se torne ativo.
## Sistema Embarcados 
Ao longo da última década, ataques como o **Stuxnet** demonstraram o potencial destrutivo de ameaças cibernéticas contra infraestruturas críticas. Para proteger sistemas industriais, recomenda-se **separar as redes internas e externas**, isolando redes SCADA da LAN corporativa.
A **Internet das Coisas (IoT)** conecta diversos dispositivos à Internet, geralmente por tecnologia sem fio, e muitos utilizam **sistemas operacionais em tempo real (RTOS)**. Essa expansão de dispositivos gerou o fenômeno do **Big Data**, impulsionado por **sistemas integrados** que capturam e processam grandes volumes de dados. No entanto, esses sistemas são vulneráveis a **ataques de tempo**, em que invasores analisam o tempo de resposta para descobrir falhas.
Em aeronaves, sistemas integrados como controle de voo e comunicação enfrentam riscos devido a **credenciais fracas, protocolos inseguros e backdoors**. **Drones (UAVs)**, usados em diversas áreas, são vulneráveis a **sequestros, spoofing de GPS, ataques Wi-Fi e falhas de autenticação**.
Para reforçar a segurança, empresas usam **técnicas de dissimulação**, como **honeypots** — sistemas falsos criados para atrair e monitorar invasores — e **honeynets**, que são conjuntos de honeypots. Um **sinkhole DNS** é outra medida eficaz, usada para bloquear a resolução de domínios maliciosos e redirecionar usuários para locais seguros.

# Modulo 3: Controle de Acesso

## Físico
Controles de acesso físico são barreiras reais implantadas para evitar o contato direto com os sistemas. A meta é prevenir que usuários não autorizados acessem fisicamente as instalações, equipamentos e outros ativos organizacionais. Alguns exemplos seriam cartões de acesso, alarme de intrusão, portas trancadas, detectores de movimento, etc.
## Logico
Controles de acesso lógico são as soluções de hardware e software usadas para gerenciar o acesso aos recursos e sistemas. Essas soluções baseadas em tecnologia incluem ferramentas e protocolos que os sistemas de computador usam para identificação, autenticação, autorização e auditoria, como firewalls, criptografia, senhas, etc. .

## Controles de Acesso Administrativos
O conceito de controles de acesso administrativo envolve três serviços de segurança: autenticação, autorização e contabilidade (AAA).Esses serviços fornecem a estrutura principal para controlar o acesso, impedindo o acesso não autorizado a um computador, rede, banco de dados ou outro recurso de dados. O primeiro A no AAA representa a <span style="color:rgb(255, 255, 0)">Autenticação</span>, ela verifica a identidade de um usuário para evitar o acesso não autorizado. Os usuários provam sua identidade com um nome de usuário ou um ID. Serviços de <span style="color:rgb(255, 255, 0)">Autorização</span> determinam quais recursos os usuários podem acessar, juntamente com as operações que os usuários podem realizar.
Alguns sistemas fazem isso usando uma lista de controle de acesso, porem não é porque você pode se autenticar na rede corporativa que tenha permissão para usar a impressora colorida de alta velocidade. A contabilidade (<span style="color:rgb(255, 255, 0)">Accounting</span>) em AAA acompanha o que os usuários fazem – incluindo o que eles acessam, a quantidade de tempo que acessam os recursos e quaisquer alterações que fazem.

## Autenticação multifator

Como abordamos anteriormente, a autenticação multifatorial usa pelo menos dois métodos de verificação - como uma senha e algo que você tem, por exemplo, um chaveiro de segurança. Isso pode ser levado um passo adiante adicionando algo que você é, como uma verificação de impressão digital. A autenticação multifator pode reduzir a incidência de roubo de identidade online porque significa que saber uma senha não dará aos cibe criminosos acesso à conta de um usuário. Retirar dinheiro de um caixa eletrônico é um exemplo simples de autenticação multifatorial, pois o usuário deve ter o cartão do banco e saber o PIN antes de o caixa eletrônico distribuir dinheiro.

# Modulo 4: Lista de Controle de Acesso
falando a verdade achei ruim entao so ta o resumo aqui
As ACLs (Access Control Lists) são listas de regras utilizadas para filtrar pacotes em redes. Elas analisam o tráfego que passa por interfaces de roteadores e aplicam regras sequenciais de permissão ou negação. Existem diferentes tipos de ACLs: as padrão, que utilizam os números de 1 a 99 ou 1300 a 1999, e as estendidas, que vão de 100 a 199 ou de 2000 a 2699. Além disso, há as ACLs nomeadas, que facilitam o gerenciamento, pois permitem identificar seu propósito através do nome atribuído.

Para determinar quais partes do endereço devem ser analisadas, as ACLs IPv4 utilizam máscaras curingas de 32 bits. Essas máscaras diferem das máscaras de sub-rede, pois utilizam lógica inversa na correspondência de bits. O Cisco IOS oferece palavras-chave como **host** e **any**, que simplificam o uso das máscaras curingas, tornando a configuração mais intuitiva.

A configuração e aplicação das ACLs exigem planejamento, sendo recomendável que sejam criadas previamente em um editor de texto antes de serem inseridas nos dispositivos. ACLs padrão e estendidas possuem comandos distintos para sua configuração e aplicação em interfaces. Enquanto as ACLs padrão filtram apenas pelo endereço de origem, as ACLs estendidas oferecem maior controle, permitindo filtrar pacotes com base em protocolos e portas. Além disso, ACLs estendidas podem ser usadas para funções básicas de firewall stateful, como permitir tráfego de saída e autorizar automaticamente o tráfego de resposta.

Ao configurar ACLs, é essencial seguir diretrizes para garantir sua eficácia. A localização da ACL na rede influencia seu desempenho: ACLs padrão devem ser aplicadas o mais próximo possível do destino, enquanto ACLs estendidas devem ficar o mais próximo possível da origem do tráfego. A ordem das regras dentro da ACL é crucial, pois assim que um pacote atende a uma regra, o processamento é interrompido. Além disso, apenas uma ACL pode ser aplicada por interface, protocolo e direção. Para evitar falhas na segurança, a última regra de uma ACL deve ser uma negação implícita (**deny any** ou **deny ip any any**).

ACLs também são úteis para mitigar ataques, como spoofing de endereços IP e ataques de negação de serviço (DoS). Um método eficaz para proteção é permitir explicitamente apenas determinados tipos de tráfego e bloquear mensagens indesejadas, como **ICMP Echo** e **Redirect**. Se o protocolo SNMP for necessário, seu uso deve ser restringido para evitar exploração de vulnerabilidades.

No contexto do IPv6, as ACLs possuem funcionamento semelhante ao do IPv4, mas sem a existência de ACLs padrão. Todas as ACLs IPv6 devem ser nomeadas e podem filtrar tráfego com base em endereços de origem e destino, bem como em cabeçalhos opcionais e protocolos de camada superior. A segurança no IPv6 também depende da filtragem adequada na borda da rede, protegendo infraestruturas contra ataques furtivos, exploração de hosts dual-stack e técnicas de tunelamento maliciosas.
# Modulo 5: Tecnologias de Firewall
#Redes #Firewall #Redes 
## Proteger redes com firewalls
Um firewall é um sistema ou grupo de sistemas que aplica uma política de controle de acesso na rede, eles são resistente a ataques, reforçam a politica de controle de acesso, exposição de hosts, recursos e aplicações sensíveis a usuários não confiáveis, e bloqueia dados maliciosos.
Existem tipos de firewalls com tecnologias e funções diferentes
### Firewall de filtragem de pacotes (sem estado)

Os firewalls de filtragem de pacotes geralmente fazem parte de um firewall de roteador, que permite ou nega tráfego com base nas informações da Camada 3 e da Camada 4. Eles são firewalls sem estado que usam uma simples pesquisa de tabela de políticas que filtra o tráfego com base em critérios específicos. Por exemplo, os servidores SMTP escutam a porta 25 por padrão. Um administrador pode configurar o firewall de filtragem de pacotes para bloquear a porta 25 de uma estação de trabalho específica para evitar que ela transmita um vírus de e-mail.
![[Firewall de filtragem de pacotes (sem estado).webp]]

### Firewall de filtragem de pacotes de estado
Firewalls com estado são as tecnologias de firewall mais versáteis e mais comuns em uso. Os firewalls stateful fornecem filtragem de pacotes stateful usando informações de conexão mantidas em uma tabela de estado. Filtragem com estado é uma arquitetura de firewall classificada na camada de rede. Ele também analisa o tráfego na camada 4 da OSI e na camada 5.![[Firewall de filtragem de pacotes de estado.webp]]
### Firewall de gateway de aplicativo
Um firewall de gateway de aplicação (firewall proxy), conforme mostrado na figura, filtra as informações nas camadas 3, 4, 5 e 7 do modelo de referência OSI. A maior parte do controle e filtragem do firewall é feita em software. Quando um cliente precisa acessar um servidor remoto, ele se conecta a um servidor proxy. O servidor proxy se conecta ao servidor remoto em nome do cliente. Portanto, o servidor só vê uma conexão do servidor proxy.
![[Firewall de gateway de aplicativo.webp]]
### Firewall de última geração
Os firewalls de última geração (NGFW) vão além dos firewalls de estado, fornecendo prevenção de intrusão integrada, reconhecimento e controle de aplicativos para ver e bloquear aplicativos arriscados, caminhos de atualização para incluir futuros feeds de informações e técnicas para lidar com ameaças de segurança em evolução.

## Arquitetura de Segurança
Existe diversos tipos de arquitetura como a <span style="color:rgb(255, 255, 0)">publica e a privada </span>onde a privada é considerada uma rede confiável, sendo esta normalmente toda a rede da empresa e a parte publica à não confiável ou não segura. Também existe a<span style="color:rgb(255, 255, 0)"> Zona Desmilitarizada</span> ou [[Abreviações#DMZ = Demilitarized Zone é uma subrede que isola serviços externos de uma organização de uma rede interna mais segura, permitindo acesso controlado à internet.|DMZ]]  é um projeto de firewall onde normalmente há uma interface interna conectada à rede privada, uma interface externa conectada à rede pública e uma interface DMZ. O tráfego proveniente da rede privada é inspecionado ao se dirigir para a rede pública ou DMZ, sendo geralmente permitido sem grandes restrições. O tráfego de retorno dessas redes para a privada também é autorizado. Já o tráfego que se origina na DMZ e tenta acessar a rede privada costuma ser bloqueado, enquanto aquele que vai para a rede pública é permitido seletivamente conforme as necessidades do serviço. O tráfego vindo da rede pública para a DMZ é inspecionado e permitido apenas para serviços específicos, como email, DNS, HTTP e HTTPS, com o retorno da DMZ para a rede pública sendo dinamicamente liberado. No entanto, qualquer tráfego originado na rede pública em direção à rede privada é bloqueado por questões de segurança. E por final a por <span style="color:rgb(255, 255, 0)">política baseados em zona</span> ou [[Abreviações#ZPF = Zone-Based Policy Firewalls refere-se a um sistema que divide a rede em zonas de segurança distintas aplicando políticas de segurança específicas|ZPFs]] usam o conceito de zonas para fornecer flexibilidade adicional. Uma zona é um grupo de uma ou mais interfaces que têm funções ou recursos semelhantes, as zonas ajudam a especificar onde uma regra ou política de firewall. Por padrão, o tráfego entre interfaces na mesma zona não está sujeito a nenhuma política e passa livremente. No entanto, todo o tráfego de zona para zona está bloqueado. Para permitir o tráfego entre as zonas, uma política que permite ou inspeciona o tráfego deve ser configurada.
# Modulo 6: Firewalls ZPFs
#Firewall 
Para criação desse projeto primeiro o administrador se concentra na separação da rede em zonas. Zonas estabelecem as fronteiras de segurança de uma rede, onde o tráfego é submetido a restrições políticas à medida que cruza para outra região da rede. Por exemplo, a rede pública seria uma zona e a rede interna seria outra zona. Após isso , deve ser projetado a infraestrutura física, levando em conta os requisitos de segurança e disponibilidade ao projetar a infraestrutura física. Isso inclui ditar o número de dispositivos entre zonas mais seguras e menos seguras e determinar dispositivos redundantes. Alguns exemplos que podem ser achados na internet são
Lan-to-internet, Firewall-with-public-servers-1, Firewall-with-public-servers-2, Firewalls redundantes e os mais complexos.

# Modulo 7: Segurança da Nuvem
## Virtualização e Computação em Nuvem
A virtualização retira a quantidade de maquinas e também o custo do espaço que elas ocupam existem vários tipos de virtualização
### Máquinas virtuais
Um hypervisor é um programa de software ou hardware que permite executar vários sistemas o
peracionais independentes em um sistema físico. Ele é um componente chave da virtualização. Existem dois métodos de virtualização:

Virtualização de hardware - O sistema operacional convidado é executado diretamente em uma plataforma de hardware, sob o controle do sistema host. 
Virtualização hospedada - Um aplicativo em execução na máquina host é usado para criar máquinas virtuais que consistem totalmente em software e não contêm componentes de hardware.
Os ambientes de máquinas virtuais usam um sistema operacional, portanto, eles precisam ser corrigidos. As máquinas virtuais compartilham hardware e são executadas com privilégios muito altos. 
### Contêineres
Ao contrário de uma máquina virtual, um contêiner consiste apenas no aplicativo e suas dependências. Um contêiner usa um mecanismo para emulação de sistema operacional. O Docker é uma plataforma aberta que usa a virtualização no SO para distribuir software em pacotes (contêineres). Você pode facilmente mover contêineres e o aplicativo será executado. Um software especializado como o Kubernetes permite gerenciar seus contêineres.
### Infraestrutura de Desktops Virtuais
Os ambientes de desktop do usuário podem ser armazenados remotamente em um servidor usando thin client ou desktops virtuais. Isso torna muito fácil criar, excluir, copiar, arquivar ou baixar configurações com rapidez em uma rede. A virtualização de desktop requer alta disponibilidade e capacidade de armazenamento.
## Tecnologia na Nuvem
As tecnologias baseadas em nuvem permitem que empresas acessem computadores, armazenamento, software e servidores pela Internet. Ele move o componente de tecnologia da organização para o provedor de nuvem.
[[Abreviações#SaaS - Software as a Service modelo de computação em nuvem que permite o uso de aplicativos por meio da internet.|SaaS]] - Permite que os usuários acessem software de aplicativos e bancos de dados. Os provedores de nuvem gerenciam a infraestrutura enquanto os usuários armazenam dados nos servidores do provedor de nuvem.
[[Abreviações#PaaS - Platform as a Serviço modelo de computação em nuvem que permite criar, implantar, executar e gerir aplicações.|PaaS]] - Permite que uma organização acesse remotamente as ferramentas e serviços de desenvolvimento usados para entregar tais aplicativos, por assinatura.
[[Abreviações#IaaS - Infrastructure as a Service modelo de computação em nuvem que fornece recursos conforme a demanda e o uso.|IaaS]] - Fornece recursos de computação virtualizados pela Internet. O provedor hospeda o hardware, software, servidores e componentes de armazenamento, e o usuário paga por uma assinatura desses recursos.
Esse tipo de serviço envolve os dois lados cliente e provedor, assim ambos tem uma responsabilidade compartilhada como pode ver a seguir
![[Tabela Cliente Nuvem.webp]]
## Segurança de dados na nuvem
Em relação aos dados do cliente eles podem ser protegidos de formas diferentes,  <span style="color:rgb(255, 255, 0)">Dados em Repouso</span> (*date at rest*) que é quando nenhum usuário ou processo os acessa, solicita ou altera, esses podem ser armazenados em dispositivos locais, como um disco rígido em um computador ou uma rede centralizada, como um servidor da empresa. Na computação em nuvem, os dados inativos podem ser armazenados em uma nuvem e podem ser acessados em qualquer computador conectado à Internet, geralmente com assinatura.  <span style="color:rgb(255, 255, 0)">Dados em Transito</span> (*data in transit*) que refere-se aos que não estão inativos nem estão sendo processados. A transmissão pode ocorrer em um único servidor ao longo das linhas de barramento da placa-mãe, entre dispositivos em uma única rede ou entre redes e, possivelmente, através da Internet. E por fim os <span style="color:rgb(255, 255, 0)">Dados em Processo</span> (*date in process*) que se refere aos dados durante a entrada inicial, a modificação, o cálculo ou a saída. Todos esses dados devem ser protegidos via [[Criptografia]] e/ou [[Hash]].

# Modulo 8: Criptografia
Acessar o arquivo [[Criptografia]] para ver sobre o conteúdo.

## Ofuscação de Dados
O mascaramento de dados protege informações sensíveis substituindo-as por versões não confidenciais que mantêm a aparência e funcionalidade dos dados originais. Essa tecnologia permite o uso seguro de dados em testes e análises sem comprometer informações críticas. Os dados podem ser mascarados  quando uma solicitação for considerada arriscada ou em ambientes não produtivos para maior segurança. Entre as principais técnicas estão: <span style="color:rgb(255, 255, 0)">substituição</span>, que troca os dados por valores realistas, <span style="color:rgb(255, 255, 0)">em baralhamento</span> que reorganiza os valores dentro da mesma coluna para preservar a coerência, e <span style="color:rgb(255, 255, 0)">anulação</span>, que aplica valores nulos para ocultar completamente as informações.
### Esteganografia
A estenografia esconde dados em outro arquivo, como um gráfico, áudio ou outro arquivo de texto. A vantagem da estenografia em relação à criptografia é que a mensagem secreta não atrai atenção especial, ao visualizar o arquivo ninguém saberá que existe uma mensagem secreta. Há vários componentes envolvidos na ocultação de dados. Primeiro, existem os dados integrados que compõem a mensagem secreta. O texto de capa (imagem ou áudio) oculta os dados integrados, produzindo o estego-arquivo.

A abordagem usada para integrar dados em uma imagem de capa é o uso de [[Abreviações#LSB = Least Significant Bit é o bit mais à direita e menos significativo em um número binário.|LSB]]. Esse método usa os bits de cada pixel na imagem.
- Um pixel é a unidade básica de cor programável em uma imagem de computador.
- A cor específica de um pixel é uma mistura de três cores - vermelho, verde e azul (RGB).
- Três bytes de dados especificam a cor de um pixel (um byte para cada cor). Um sistema de cores de 24 bits usa todos os três bytes.
- O LSB usa um pouco de cada um dos componentes das cores vermelho, verde e azul. Cada pixel pode armazenar 3 bits.
## Comunicações Seguras
As organizações devem fornecer suporte para proteger os dados à medida que eles viajam pelos links. Isso pode incluir tráfego interno, mas é mais importante proteger os dados que viajam para fora da organização para as filiais, locais de trabalho remoto, e parceiros. Estes são os quatro elementos das comunicações seguras:

- **Integridade de dados** - Garante que a mensagem não foi alterada. Quaisquer alterações nos dados em trânsito serão detectadas. A integridade é garantida pela implementação de um dos algoritmos Secure Hash (SHA-2 ou SHA-3).
- **Autenticação de origem** - Garante que a mensagem não é uma falsificação e realmente vem de quem é declarada. Muitas redes modernas garantem autenticação com algoritmos como código de autenticação de mensagem baseado em hash (HMAC).
- **Confidencialidade dos dados** - Garante que apenas usuários autorizados possam ler a mensagem. Se a mensagem for interceptada, ela não poderá ser decifrada dentro de um razoável período de tempo. A confidencialidade dos dados é implementada usando algoritmos de criptografia simétrica e assimétrica.
- **Não Repúdio de Dados** - Garante que o remetente não pode repudiar ou refutar a validade de uma mensagem enviada. O não repúdio depende do fato de que apenas o remetente possui as características ou a assinatura exclusivas de como essa mensagem é tratada.
## Hash

Olhar o arquivo [[Hash]] para ver sobre.
# Modulo 9: Tecnologias e Protocolos
## Monitorando protocolos comuns
### Syslog
Diversos protocolos utilizados em redes possuem características que os tornam fundamentais para o monitoramento de segurança. Entre eles, o **syslog** e o **Network Time Protocol (NTP)** desempenham um papel essencial no trabalho dos analistas de segurança cibernética.
O **syslog** é um padrão amplamente adotado para registrar eventos de dispositivos de rede e endpoints. Ele permite a transmissão, armazenamento e análise de mensagens de forma neutra e padronizada. Graças a essa flexibilidade, dispositivos de diferentes fabricantes podem enviar logs para servidores centrais que executam um daemon syslog. Essa centralização facilita o monitoramento de segurança, tornando-o mais eficiente. Normalmente, os servidores syslog escutam na porta **UDP 514**.

Devido à sua importância na segurança, os servidores syslog são alvos potenciais de ataques cibernéticos. Atores mal-intencionados podem explorar esses servidores para ocultar atividades suspeitas, como a **exfiltração de dados**, que muitas vezes ocorre de maneira lenta e discreta. Os invasores podem tentar interromper a transferência de logs, corromper ou destruir dados e comprometer o software responsável pelo envio das mensagens.

Para mitigar essas ameaças, foi desenvolvida a **próxima geração do syslog**, conhecida como **syslog-ng**. Essa versão aprimorada oferece recursos adicionais que aumentam a segurança e a integridade dos registros, dificultando ataques e manipulações maliciosas.
![[Syslog.webp|center]]
### NTP
As mensagens do Syslog geralmente incluem carimbos de data e hora, permitindo a organização cronológica de registros provenientes de diferentes fontes. Isso proporciona uma visão clara dos processos de comunicação da rede. Como esses registros podem vir de diversos dispositivos, é essencial que todos compartilhem um relógio sincronizado. Para isso, os dispositivos podem utilizar o **Network Time Protocol (NTP)**, que emprega uma hierarquia de fontes de tempo autoritativas para distribuir informações temporais na rede. Dessa forma, mensagens de dispositivos sincronizados podem ser enviadas para o servidor Syslog com precisão. O NTP opera na porta **UDP 123**.
Os carimbos de data e hora são fundamentais para a detecção de ameaças, pois permitem rastrear eventos registrados em vários dispositivos ao longo do caminho até o sistema de destino. Atores maliciosos podem tentar comprometer a infraestrutura do **NTP** para manipular informações de tempo, dificultando a correlação de eventos e ocultando rastros de atividades maliciosas. Além disso, criminosos cibernéticos já exploraram vulnerabilidades em clientes e servidores **NTP** para lançar ataques **DDoS**. Embora esses ataques não corrompam necessariamente os dados de monitoramento de segurança, podem afetar a disponibilidade da rede.
![[NTP.webp|center]]
### DNS
O **Serviço de Nome de Domínio (DNS)** é amplamente utilizado diariamente, mas muitas organizações adotam políticas de segurança menos rigorosas contra ameaças baseadas em DNS em comparação com outras explorações cibernéticas. Cientes dessa vulnerabilidade, invasores frequentemente encapsulam diferentes protocolos de rede dentro do **DNS** para contornar dispositivos de segurança. Atualmente, o DNS é um vetor comum para diversos tipos de malware, sendo utilizado para comunicação com **servidores de comando e controle (CNC)** e para exfiltração de dados, mascarando essas transmissões como consultas DNS legítimas. Técnicas de codificação, como **Base64, binário de 8 bits e hexadecimal**, são empregadas para ocultar os dados e driblar medidas básicas de prevenção de perda de dados (**DLP**).

Um exemplo dessa técnica envolve o malware codificando informações roubadas na parte do subdomínio de uma consulta DNS direcionada a um domínio controlado pelo invasor. Por exemplo, uma solicitação para **"long-string-of-exfiltrated-data.example.com"** seria enviada ao servidor de nomes de **example.com**, permitindo que o atacante extraísse os dados e retornasse uma resposta codificada ao malware. Com isso, o invasor poderia recuperar e reconstruir informações sensíveis, como um banco de dados de credenciais de usuários e senhas.

Uma característica marcante desse tipo de ataque é que as consultas DNS utilizadas são significativamente mais longas do que o normal. **Analistas cibernéticos** podem modelar a distribuição do tamanho dos subdomínios para definir um padrão de comportamento esperado e, assim, detectar anomalias. Por exemplo, a consulta **"AW4GCGXHy2UGDG8GCHJVDGVJDC.example.com"** geraria suspeitas se um host interno da rede começasse a enviar múltiplas requisições desse tipo.

Consultas DNS com nomes de domínio gerados aleatoriamente ou subdomínios anormalmente longos devem ser consideradas suspeitas, principalmente se houver um aumento repentino dessas solicitações na rede. Logs de proxy **DNS** podem ser analisados para identificar essas atividades maliciosas. Alternativamente, serviços como o **Cisco Umbrella** podem ser empregados para bloquear consultas a servidores CNC suspeitos e domínios associados a ameaças cibernéticas.
![[DNS.webp|center]]
### HTTP/HTTPS
O **Hypertext Transfer Protocol (HTTP)** é a espinha dorsal da World Wide Web, mas todas as informações transmitidas por ele viajam em **texto simples**, sem qualquer proteção contra interceptação ou alteração por agentes mal-intencionados. Essa vulnerabilidade representa um risco significativo para a privacidade, a identidade e a segurança das informações, tornando todas as atividades de navegação potencialmente expostas a ameaças.

Uma exploração comum no HTTP é a **injeção de iFrame (quadro inline)**. Muitas ameaças baseadas na web envolvem scripts maliciosos inseridos em servidores comprometidos, que redirecionam os navegadores para sites infectados por meio de **iFrames ocultos**. Nesse tipo de ataque, um invasor compromete um servidor legítimo e insere um código malicioso que cria um iFrame invisível em uma página popular. Quando a página é carregada, o iFrame baixa e executa **malware**, frequentemente hospedado em um URL diferente do site original. Para mitigar esse tipo de ataque, **soluções de segurança de rede**, como a **filtragem Cisco Web Reputation**, podem identificar e bloquear tentativas de carregamento de conteúdo suspeito provenientes de fontes não confiáveis, mesmo quando essas solicitações são feitas por meio de um iFrame oculto.
![[Exploração de injeção iFrame de HTTP.webp]]
Para lidar com a alteração ou interceptação de dados confidenciais, muitas organizações comerciais adotaram HTTPS ou implementaram políticas somente HTTPS para proteger os visitantes de seus sites e serviços.

HTTPS adiciona uma camada de criptografia ao protocolo HTTP usando Secure Socket Layer (SSL), como mostrado na figura. Isso torna os dados HTTP ilegíveis, pois deixam o computador de origem até chegar ao servidor. Observe que HTTPS não é um mecanismo para a segurança do servidor Web. Ele só protege o tráfego de protocolo HTTP enquanto está em trânsito.
![[Diagrama de protocolo HTTPS.webp|center]]
Infelizmente, o tráfego HTTPS criptografado complica o monitoramento de segurança de rede. Alguns dispositivos de segurança incluem descriptografia e inspeção SSL; no entanto, isso pode apresentar problemas de processamento e privacidade. Além disso, o HTTPS adiciona complexidade às capturas de pacotes devido às mensagens adicionais envolvidas no estabelecimento da conexão criptografada. Esse processo é resumido na figura e representa sobrecarga adicional sobre HTTP.
![[Transações HTTPS.webp|center]]
### Email
Protocolos de e-mail como SMTP, POP3 e IMAP podem ser usados por atores de ameaças para espalhar malware, exfiltrar dados ou fornecer canais para servidores CNC de malware, como mostrado na figura.

SMTP envia dados de um host para um servidor de email e entre servidores de email. Como DNS e HTTP, é um protocolo comum para ver sair da rede. Como há muito tráfego SMTP, ele nem sempre é monitorado. No entanto, o SMTP foi usado no passado por malware para exfiltrar dados da rede. No 2014 hack da Sony Pictures, uma das explorações usou SMTP para exfiltrar detalhes do usuário de hosts comprometidos para servidores CNC. Essas informações podem ter sido usadas para ajudar a desenvolver explorações de recursos protegidos na rede Sony Pictures. O monitoramento de segurança pode revelar esse tipo de tráfego com base nos recursos da mensagem de email.

IMAP e POP3 são usados para baixar mensagens de email de um servidor de email para o computador host. Por esse motivo, eles são os protocolos de aplicativos que são responsáveis por trazer malware para o host. O monitoramento de segurança pode identificar quando um anexo de malware entrou na rede e qual host ele infectou pela primeira vez. A análise retrospectiva pode então rastrear o comportamento do malware a partir desse ponto em diante. Desta forma, o comportamento do malware pode ser melhor compreendido e a ameaça identificada. As ferramentas de monitoramento de segurança também podem permitir a recuperação de anexos de arquivos infectados para envio a caixas de proteção de malware para análise.
![[Ameaças de protocolo de email.webp]]
### ICMP
ICMP tem muitos usos legítimos, no entanto, a funcionalidade ICMP também tem sido usada para criar vários tipos de explorações. O ICMP pode ser usado para identificar hosts em uma rede, a estrutura de uma rede e determinar os sistemas operacionais em uso na rede. Ele também pode ser usado como um veículo para vários tipos de ataques DoS.

ICMP também pode ser usado para exfiltração de dados. Devido à preocupação de que o ICMP possa ser usado para vigiar ou negar o serviço de fora da rede, o tráfego ICMP de dentro da rede às vezes é ignorado. No entanto, algumas variedades de malware usam pacotes ICMP criados para transferir arquivos de hosts infectados para agentes ameaçadores usando esse método, conhecido como tunelamento ICMP.
**Observação:** um ou todos os sites disponíveis na pesquisa podem estar bloqueados pelo firewall da sua instituição.
Existem várias ferramentas para a criação de túneis. Procure na internet por Ping Tunnel para explorar uma dessas ferramentas.
## Tecnologias de segurança
### ACL
Muitas tecnologias e protocolos podem ter impacto no monitoramento de segurança. Listas de Controle de Acesso (ACLs) estão entre essas tecnologias. As ACLs podem dar uma falsa sensação de segurança se forem excessivamente confiadas. As ACLs e a filtragem de pacotes em geral são tecnologias que contribuem para um conjunto em evolução de proteções de segurança de rede.

A figura ilustra o uso de ACLs para permitir apenas tipos específicos de tráfego ICMP (Internet Control Message Protocol). O servidor em 192.168.1.10 faz parte da rede interna e tem permissão para enviar solicitações de ping para o host externo em 209.165.201.3. O tráfego ICMP de retorno do host externo é permitido se for uma resposta ICMP, extinção de origem (informa a origem para reduzir o ritmo do tráfego) ou qualquer mensagem ICMP inacessível. Todos os outros tipos de tráfego ICMP são negados. Por exemplo, o host externo não pode iniciar uma solicitação de ping para o host interno. A ACL de saída está permitindo mensagens ICMP que relatam vários problemas. Isso permitirá túneis ICMP e exfiltração de dados.

Os invasores podem determinar quais endereços IP, protocolos e portas são permitidos pelas ACLs. Isso pode ser feito por varredura de portas, testes de penetração ou através de outras formas de reconhecimento. Os atacantes podem criar pacotes que usam endereços IP de origem falsificados. Os aplicativos podem estabelecer conexões em portas arbitrárias. Outros recursos do tráfego de protocolo também podem ser manipulados, como o sinalizador estabelecido em segmentos TCP. As regras não podem ser antecipadas e configuradas para todas as técnicas de manipulação de pacotes emergentes.

Para detectar e reagir à manipulação de pacotes, comportamentos mais sofisticados e medidas baseadas em contexto precisam ser tomadas. Os firewalls de próxima geração da Cisco, o AMP (Advanced Malware Protection) e os appliances de conteúdo de e-mail e Web são capazes de resolver as deficiências das medidas de segurança baseadas em regras.
![[Atenuante o abuso de ICMP.webp|center]]
### NAT/PAT
Conversão de Endereços de Rede (NAT) e Tradução de Endereço de Porta (PAT) podem complicar o monitoramento de segurança. Vários endereços IP são mapeados para um ou mais endereços públicos visíveis na Internet, ocultando os endereços IP individuais que estão dentro da rede (endereços internos).

A figura ilustra a relação entre endereços internos e externos que são usados como endereços de origem (SA) e endereços de destino (DA). Esses endereços internos e externos estão em uma rede que está usando NAT para se comunicar com um destino na Internet. Se o PAT estiver em vigor e todos os endereços IP que saem da rede usarem o endereço global 209.165.200.226 interno para tráfego na Internet, pode ser difícil registrar o dispositivo interno específico que está solicitando e recebendo o tráfego quando ele entra na rede.

Esse problema pode ser especialmente relevante com dados NetFlow. Os fluxos de NetFlow são unidirecionais e são definidos pelos endereços e portas que eles compartilham. O NAT basicamente quebrará um fluxo que passa por um gateway NAT, tornando as informações de fluxo além desse ponto indisponíveis. A Cisco oferece produtos de segurança que irão “costurar” fluir juntos mesmo que os endereços IP tenham sido substituídos pelo NAT.
O NetFlow é discutido com mais detalhes posteriormente no módulo.
![[Network Address Translation.webp|center]]
### peer-2-peer (P2P)
Na rede ponto a ponto (P2P), mostrada na figura, os hosts podem operar em funções de cliente e servidor. Existem três tipos de aplicativos P2P: compartilhamento de arquivos, compartilhamento de processadores e mensagens instantâneas. No compartilhamento de arquivos P2P, os arquivos em uma máquina participante são compartilhados com membros da rede P2P. Exemplos disso são os outrora populares Napster e Gnutella. Bitcoin é uma operação P2P que envolve o compartilhamento de um banco de dados distribuído, ou razão, que registra saldos e transações Bitcoin. BitTorrent é uma rede de compartilhamento de arquivos P2P.
Sempre que os usuários desconhecidos recebem acesso aos recursos de rede, a segurança é uma preocupação. Aplicativos P2P de compartilhamento de arquivos não devem ser permitidos em redes corporativas. A atividade da rede P2P pode contornar as proteções de firewall e é um vetor comum para a propagação de malware. P2P é inerentemente dinâmico. Ele pode operar conectando-se a vários endereços IP de destino e também pode usar numeração dinâmica de portas. Arquivos compartilhados são frequentemente infectados com malware, e os atores de ameaças podem posicionar seu malware em clientes P2P para distribuição a outros usuários.
As redes P2P de compartilhamento de processadores doam ciclos de processador para tarefas computacionais distribuídas. Pesquisa de câncer, pesquisa de extraterrestres, e pesquisa científica usam ciclos de processador doados para distribuir tarefas computacionais.

Mensagens instantâneas (IM) também é considerado um aplicativo P2P. IM tem valor legítimo dentro de organizações que têm equipes de projeto distribuídas geograficamente. Nesse caso, aplicativos de IM especializados estão disponíveis, como a plataforma Webex Teams, que são mais seguras do que as mensagens instantâneas que usam servidores públicos.
![[p2p.webp|center]]
#### TOR
Tor é uma plataforma de software e rede de hosts P2P que funcionam como roteadores de internet na rede Tor. A rede Tor permite que os usuários naveguem na internet anonimamente. Os usuários acessam a rede Tor usando um navegador especial. Quando uma sessão de navegação é iniciada, o navegador constrói um caminho de ponta a ponta em camadas na rede do servidor Tor que é criptografado, como mostrado na figura. Cada camada criptografada é “removida” como as camadas de uma cebola (portanto, “onion routing”) à medida que o tráfego atravessa um retransmissor do Tor. As camadas contêm informações criptografadas do próximo salto que só podem ser lidas pelo roteador que precisa ler as informações. Dessa forma, nenhum dispositivo único conhece todo o caminho para o destino e as informações de roteamento só podem ser lidas pelo dispositivo que as requer. Finalmente, no final do caminho do Tor, o tráfego atinge seu destino na internet. Quando o tráfego é retornado à origem, um caminho criptografado em camadas é construído novamente.

Tor apresenta uma série de desafios aos analistas de segurança cibernética. Primeiro, o Tor é amplamente utilizado por organizações criminosas na “Dark Net”. Além disso, Tor tem sido usado como um canal de comunicação para malware CNC. Como o endereço IP de destino do tráfego Tor é ofuscado pela criptografia, com apenas o nó Tor de próximo salto conhecido, o tráfego Tor evita listas negras configuradas em dispositivos de segurança.
![[TOR.webp|center]]
## Balanceador de Carga
O balanceamento de carga envolve a distribuição do tráfego entre dispositivos ou caminhos de rede para evitar recursos de rede sobrecarregados com muito tráfego. Se existirem recursos redundantes, um algoritmo ou dispositivo de balanceamento de carga funcionará para distribuir o tráfego entre esses recursos, conforme mostrado na figura.

Uma maneira de fazer isso na internet é através de várias técnicas que usam DNS para enviar tráfego para recursos que têm o mesmo nome de domínio, mas vários endereços IP. Em alguns casos, a distribuição pode ser para servidores que são distribuídos geograficamente. Isso pode resultar em uma única transação de Internet sendo representada por vários endereços IP nos pacotes de entrada. Isso pode fazer com que recursos suspeitos apareçam em capturas de pacotes. Além disso, alguns dispositivos do gerenciador de balanceamento de carga (LBM) usam testes para testar o desempenho de diferentes caminhos e a integridade de diferentes dispositivos. Por exemplo, um LBM pode enviar testes para os diferentes servidores para os quais ele está balanceando o tráfego de carga, a fim de detectar que os servidores estão operando. Isso é feito para evitar o envio de tráfego para um recurso que não está disponível. Esses testes podem parecer tráfego suspeito se o analista de segurança cibernética não estiver ciente de que esse tráfego faz parte da operação do LBM.
![[Balanceamento de carga com delegação DNS.webp]]
# Modulo 10: Dados de Segurança Do Rede
## Tipos de dados
### Dados de alerta
Os dados de alerta consistem em mensagens geradas por sistemas de prevenção de intrusões (IPSs) ou sistemas de detecção de intrusões (IDSs) em resposta ao tráfego que viola uma regra ou corresponde à assinatura de uma exploração conhecida. Um IDS de rede (NIDS), como o Snort, vem configurado com regras para explorações conhecidas. Os alertas são gerados pelo Snort e são legíveis e pesquisáveis pelos aplicativos Sguil e Squert, que fazem parte do conjunto Security Onion de ferramentas NSM.

Um site de teste que é usado para determinar se o Snort está funcionando é o site tesmyids. Procure por ele na internet. Consiste em uma única página da Web que exibe apenas o seguinte texto **uid=0(root) gid=0(root) groups=0(root)**. Se o Snort estiver funcionando corretamente e um host visitar este site, uma assinatura será correspondida e um alerta será acionado. Esta é uma maneira fácil e inofensiva de verificar se o NIDS está em execução.

A regra Snort que é acionada é:

```
alert ip any any -> any any (msg:"GPL ATTACK\_RESPONSE id check returned root"; content:"uid=0|28|root|29|"; fast\_pattern:only; classtype:bad-unknown; sid:2100498; rev:8;)
```

Esta regra gera um alerta se **qualquer endereço IP** na rede receber dados de uma fonte externa que contenha conteúdo com texto correspondente ao padrão de **uid=0 (root)**. O alerta contém a mensagem **GPL ATTACK_RESPONSE id check retornou root**. O ID da regra Snort que foi acionada é **2100498**.

A linha destacada na figura exibe um alerta Sguil que foi gerado visitando o site testmyids. A regra Snort e os dados do pacote para o conteúdo recebido da página da Web testmyvids são exibidos na área inferior direita da interface Sguil.
![[Console Sguil mostrando o alerta de teste do Snort IDS.webp|center]]
### Dados de Sessão e Transação
1. **ts**: carimbo de data e hora
2. **uid**: ID de sessão única
3. **id.orig_h**: Endereço IP do host que originou a sessão (endereço de origem)
4. **id.orig_p**: porta de protocolo para o host de origem (porta de origem)
5. **id.resp_h**: Endereço IP do host que responde ao host de origem (endereço de destino)
6. **id.resp_p**: protocolo de host respondente (porta de destino)
7. **proto**: protocolo de camada de transporte para sessão
8. **service**: protocolo de camada de aplicativo
9. **duration**: duração da sessão
10. **orig_bytes**: bytes do host de origem
11. **resp_bytes**: bytes do host respondente
12. **orig_packets**: pacotes do host de origem
13. **resp_packets**:pacotes do host respondente

Os dados de sessão são um registro de uma conversa entre dois pontos de extremidade de rede, que geralmente são um cliente e um servidor. O servidor pode estar dentro da rede corporativa ou em um local acessado pela Internet. Dados de sessão são dados sobre a sessão, não os dados recuperados e usados pelo cliente. Os dados da sessão incluirão informações de identificação, como **as cinco tuplas** de endereços IP de origem e destino, números de porta de origem e destino, e o código IP do protocolo em uso. Os dados sobre a sessão geralmente incluem um ID de sessão, a quantidade de dados transferidos por origem e destino e informações relacionadas à duração da sessão.

Zeek, anteriormente Bro, é uma ferramenta de monitoramento de segurança de rede que você usará em laboratórios mais tarde no curso. A figura mostra uma saída parcial para três sessões HTTP a partir de um log de conexão Zeek. As explicações dos campos são mostradas abaixo da figura.
![[Dados de Sessão Zeek - Conteúdo Parcial.webp]]
Os dados de transação consistem nas mensagens que são trocadas durante sessões de rede. Essas transações podem ser exibidas em transcrições de captura de pacotes. Os logs de dispositivos mantidos por servidores também contêm informações sobre as transações que ocorrem entre clientes e servidores. Por exemplo, uma sessão pode incluir o download de conteúdo de um servidor web, como mostrado na figura. As transações que representam as solicitações e respostas seriam registradas em um log de acesso no servidor ou por um NIDS como Zeek. A sessão é todo o tráfego envolvido na elaboração da solicitação, a transação é a própria solicitação.
![[Dados de transação.webp|center]]
### Dados Estáticos
Como dados de sessão, dados estatísticos são sobre tráfego de rede. Os dados estatísticos são criados através da análise de outras formas de dados de rede. Podem ser feitas conclusões que descrevem ou predizem o comportamento da rede a partir dessas análises. As características estatísticas do comportamento normal da rede podem ser comparadas ao tráfego de rede atual em um esforço para detectar anomalias. As estatísticas podem ser usadas para caracterizar quantidades normais de variação nos padrões de tráfego de rede, a fim de identificar condições de rede que estão significativamente fora desses intervalos. Diferenças estatisticamente significativas devem gerar alarmes e investigação imediata.

A NBA (Network Behavior Analysis) e a Network Behavior Anomaly Detection (NBAD) são abordagens para monitoramento de segurança de rede que usam técnicas analíticas avançadas para analisar dados de telemetria de rede NetFlow ou IPFIX (Internet Protocol Flow Information Export). Técnicas como análise preditiva e inteligência artificial realizam análises avançadas de dados de sessão detalhados para detectar possíveis incidentes de segurança.

**Observação**: IPFIX é a versão padrão IETF do Cisco NetFlow versão 9.
## Logs de dispositivos
### Logs de Host
Conforme discutido anteriormente, os sistemas de detecção de intrusão baseados em host (HIDS) são executados em hosts individuais. HIDS não só detecta intrusões, mas na forma de firewalls baseados em host, também pode impedir intrusões. Este software cria logs e os armazena no host. Isso pode dificultar a visão do que está acontecendo em hosts na empresa, pois muitas proteções baseadas em host têm uma maneira de enviar logs para servidores centralizados de gerenciamento de logs. Dessa forma, os logs podem ser pesquisados a partir de um local central usando as ferramentas NSM.

Os sistemas HIDS podem usar agentes para enviar logs para servidores de gerenciamento. O OSSEC, um HIDS de código aberto popular, inclui uma funcionalidade robusta de coleta e análise de logs. Pesquise OSSEC na internet para saber mais. O Microsoft Windows inclui vários métodos para coleta e análise automatizadas de logs de host. Tripwire oferece um HIDS para Linux que inclui funcionalidade semelhante. Todos podem ser dimensionados para grandes empresas.

Os logs de host do Microsoft Windows são visíveis localmente pelo Visualizador de Eventos. O Visualizador de Eventos mantém cinco tipos de logs:

- **Logs de aplicativos** — Eles contêm eventos registrados por vários aplicativos.
- **Registros do sistema** — Isso inclui eventos relacionados à operação de drivers, processos e hardware.
- **Registros de instalação** — Estes registram informações sobre a instalação de software, incluindo atualizações do Windows.
- **Registros de segurança** — Esses eventos registram relacionados à segurança, como tentativas de logon e operações relacionadas ao gerenciamento e acesso de arquivos ou objetos.
- **Logs da linha de comando** - Os invasores que obtiveram acesso a um sistema e alguns tipos de malware executam comandos da interface de linha de comando (CLI) em vez de uma GUI. A execução da linha de comando em log fornecerá visibilidade para esse tipo de incidente.

Vários logs podem ter diferentes tipos de eventos. Os logs de segurança consistem apenas em mensagens de falha ou êxito de auditoria. Em computadores Windows, o log de segurança é realizado pelo Local Security Authority Subsystem Service (LSASS), que também é responsável por impor diretivas de segurança em um host Windows. O LSASS é executado como lsass.exe. Ele é frequentemente falsificado por malware. Ele deve estar sendo executado a partir do diretório System32 do Windows. Se um arquivo com esse nome, ou um nome camuflado, como 1sass.exe, estiver em execução ou em execução a partir de outro diretório, ele pode ser malware.

Os Eventos do Windows são identificados por números de ID e descrições breves. Uma enciclopédia de IDs de eventos de segurança, algumas com detalhes adicionais, está disponível no Ultimate Windows Security na Web.

A tabela explica o significado dos cinco tipos de eventos de log de host do Windows.

|Tipo de evento|Descrição|
|---|---|
|Erro|Um erro é um evento que indica um problema significativo, como perda de dados ou perda de funcionalidade. Por exemplo, se um serviço falhar ao carregar durante a inicialização, um evento de erro será registrado.|
|Aviso|Um aviso é um evento que não é necessariamente significativo, mas pode indicar um possível problema futuro. Por exemplo, quando o espaço em disco é baixo, um evento de aviso é registrado. Se um aplicativo pode se recuperar de um evento sem perda de funcionalidade ou dados, ele geralmente pode classificar o evento como um evento de aviso.|
|Informações|Um evento informativo descreve a operação bem-sucedida de um aplicativo, driver ou serviço. Por exemplo, quando um driver de rede é carregado com êxito, pode ser apropriado registrar um evento de informações. Observe que geralmente é inapropriado para um aplicativo de área de trabalho registrar um evento cada vez que ele é iniciado.|
|Sucesso na Auditoria|Uma auditoria bem-sucedida é um evento que registra uma tentativa de acesso de segurança auditada com êxito. For example, a user's successful attempt to log on to the system is logged as a success audit event.|
|Falha ne Auditoria|Uma auditoria de falha é um evento que registra uma tentativa de acesso de segurança auditada que falha. Por exemplo, se um usuário tentar acessar uma unidade de rede e falhar, a tentativa é registrada como um evento de auditoria de falha.|
### Syslog
O Syslog inclui especificações para formatos de mensagem, uma estrutura de aplicativos cliente-servidor e protocolo de rede. Muitos tipos diferentes de dispositivos de rede podem ser configurados para usar o padrão syslog para registrar eventos em servidores syslog centralizados.

Syslog é um protocolo cliente / servidor. O Syslog foi definido dentro do grupo de trabalho Syslog do IETF (RFC 5424) e é suportado por uma grande variedade de dispositivos e receptores em várias plataformas.

O remetente do Syslog envia uma pequena mensagem de texto (menos de 1 KB) para o receptor do Syslog. O receptor Syslog é comumente chamado de “syslogd”, “Syslog daemon” ou “Syslog server.“ As mensagens do Syslog podem ser enviadas via UDP (porta 514) e/ou TCP (normalmente, porta 5000). Embora existam algumas exceções, como wrappers SSL, esses dados são normalmente enviados em texto simples pela rede.

O formato completo de uma mensagem Syslog que é visto na rede tem três partes distintas, como mostrado na figura.

- PRI (prioridade)
- HEADER
- MSG (texto da mensagem)

O PRI consiste em dois elementos, a Facilidade e a Gravidade da mensagem, que são ambos valores inteiros. O recurso consiste em amplas categorias de fontes que geraram a mensagem, como o sistema, o processo ou a aplicação. O valor Facility pode ser usado por servidores de log para direcionar a mensagem para o arquivo de log apropriado. A gravidade é um valor de 0 a 7 que define a gravidade da mensagem.

| Valor | Severidade                                                                                                                  |
| ----- | --------------------------------------------------------------------------------------------------------------------------- |
| 0     | **Emergência**: sistema está inutilizável                                                                                   |
| 1     | **Alerta**: a ação deve ser tomada imediatamente                                                                            |
| 2     | **Crítico**: condições críticas que devem ser corrigidas imediatamente e indica falha em um sistema                         |
| 3     | **Erro**: uma falha que não é urgente, deve ser resolvida dentro de um determinado tempo                                    |
| 4     | **Aviso**: um erro não existe atualmente; no entanto, um erro ocorrerá no futuro se a condição não for resolvida            |
| 5     | **Aviso**: Qual ferramenta está incluída no Security Onion que é usada pelo Snort para baixar automaticamente novas regras? |
| 6     | **Informativo**: mensagens emitidas relativas ao funcionamento normal                                                       |
| 7     | **Depuração**: mensagens de interesse para desenvolvedores                                                                  |
### Logs do servidor
Os logs do servidor são uma fonte essencial de dados para o monitoramento da segurança da rede. Os servidores de aplicativos de rede, como servidores de e-mail e Web, mantêm registros de acesso e erros. Os logs do servidor proxy DNS que documentam todas as consultas DNS e respostas que ocorrem na rede são especialmente importantes. Os logs de proxy DNS são úteis para identificar hosts que possam ter visitado sites perigosos e para identificar a exfiltração de dados DNS e conexões a servidores de comando e controle de malware. Muitos servidores UNIX e Linux usam syslog. Outros podem usar o registro proprietário. O conteúdo dos eventos do arquivo de log depende do tipo de servidor.
## Logs de rede

### NetFlow (cisco)
NetFlow é um protocolo desenvolvido pela Cisco como uma ferramenta para solução de problemas de rede e contabilidade baseada em sessão. O NetFlow fornece com eficiência um importante conjunto de serviços para aplicativos IP, incluindo contabilidade de tráfego de rede, faturamento de rede com base no uso, planejamento de rede, segurança, recursos de monitoramento de negação de serviço e monitoramento de rede. O NetFlow fornece informações valiosas sobre usuários e aplicativos de rede, tempos de uso de pico e roteamento de tráfego.

O NetFlow não faz uma captura completa de pacote ou captura o conteúdo real no pacote. O NetFlow registra informações sobre o fluxo de pacotes, incluindo metadados. A Cisco desenvolveu o NetFlow e, em seguida, permitiu que ele fosse usado como base para um padrão IETF chamado IPFIX. O IPFIX é baseado no Cisco NetFlow Versão 9.
### Registros de Proxy

Os servidores proxy, como os usados para solicitações Web e DNS, contêm logs valiosos que são uma fonte primária de dados para monitoramento de segurança de rede.

Servidores proxy são dispositivos que atuam como intermediários para clientes de rede. Por exemplo, uma empresa pode configurar um proxy da Web para lidar com solicitações da Web em nome de clientes. Em vez de solicitações de recursos da Web serem enviadas diretamente para o servidor do cliente, a solicitação é enviada primeiro para um servidor proxy. O servidor proxy solicita os recursos e os retorna ao cliente. O servidor proxy gera logs de todas as solicitações e respostas. Esses logs podem ser analisados para determinar quais hosts estão fazendo as solicitações, se os destinos são seguros ou potencialmente maliciosos, e também para obter insights sobre o tipo de recursos que foram baixados.

Proxies da Web fornecem dados que ajudam a determinar se as respostas da Web foram geradas em resposta a solicitações legítimas ou foram manipuladas para parecer respostas, mas são, de fato, explorações. Também é possível usar proxies da web para inspecionar o tráfego de saída como meio de prevenção de perda de dados (DLP). O DLP envolve a varredura do tráfego de saída para detectar se os dados que estão saindo da Web contêm informações confidenciais, confidenciais ou secretas. Exemplos de proxies populares da Web são Squid, CCProxy, Apache Traffic Server e WinGate.

Um exemplo de um log de proxy da web do Squid na forma nativa do Squid aparece abaixo. Explicações dos valores de campo aparecem na tabela abaixo da entrada de log.

**Exemplo de log de proxy DNS**

```
1265939281.764 19478 172.16.167.228 TCP_MISS/200 864GEThttp://www.example.com//images/home.png - NONE/- image/png
```

|Valor de log de proxy|Explicação|
|---|---|
|1265939281.764|**Tempo** - Timestamp em milliseconds no formato Unix epoch|
|19478|**Duração** - o tempo decorrido para a solicitação e resposta do Squid|
|172.16.167.228|**cliente** Endereço IP do|
|TCP_MISS/200|**Resultado** - Códigos de resultado do Squid e código de status HTTP separados por uma barra|
|864|**Tamanho** - os bytes de dados entregues|
|GET|**Solicitação** - solicitação HTTP feita pelo client|
|http://www.example.com//images/home.png|**URI/URL** - endereço do recurso que foi solicitado|
|-|**Identidade do cliente** - valor RFC 1413 para o cliente que fez a solicitação. Não usado por padrão.|
|NONE/-|**Código de peering/Host de peer** - Consulta ao servidor de cache vizinho|
|image/png|**Tipo** - tipo de conteúdo MIME do valor Content-Type no cabeçalho de resposta HTTP|

**Observação**: Proxies da Web abertos, que são proxies que estão disponíveis para qualquer usuário da Internet, podem ser usados para ofuscar endereços IP de atores de ameaças. Endereços de proxy abertos podem ser usados na lista negra do tráfego da Internet.
# Modulo 11: Avaliação de Alertas
#redes #BlueTeam 
## Cebola Segurança
O Security Onion é um pacote de código aberto de ferramentas de Monitoramento de Segurança de Rede que é executado em uma distribuição Ubuntu Linux. A ferramenta fornece três funções principais para o analista de segurança cibernética: captura completa de pacotes , sistemas de detecção de intrusão e ferramentas de analistas de alerta.
## Regras e Alertas
Os alertas podem vir de várias fontes:
- **[[Abreviações#NIDS = Network Intrusion Detection System são tecnologias que monitoram a rede em busca de atividades maliciosas|NIDS]]** - [[FerramentasBlueTeam#Snort - Falar sbre|Snort]], [[FerramentasBlueTeam#Suricata - falar sobre|Suricata]] e [[FerramentasBlueTeam#Zeek - falar sobre|Zeek]].
- **[[Abreviações#HIDS = Host Intrusion Detection System segurança são tecnologias que monitoram um host especifico em busca de atividades maliciosas|HIDS]]** - OSSEC, Wazuh.
- **Gerenciamento e monitoramento de ativos** - Sistema de detecção de ativos passivos (PADS).
- **Transações HTTP, DNS e TCP** - Registradas pelo Zeek e pcaps.
- **Mensagens do Syslog** - Várias fontes.

## Visão Geral de Alertas 
### Avaliando Alertas 
Os incidentes de segurança são classificados usando um esquema de diagnósticos médicos, esse esquema de classificação é usado para orientar ações e avaliar procedimentos de diagnóstico. Por exemplo, quando um paciente visita um médico para um exame de rotina, uma das tarefas do médico é determinar se o paciente está doente. Um dos resultados pode ser uma determinação correta de que a doença está presente e o paciente está doente. Outro resultado pode ser que não há doença e o paciente é saudável. A preocupação é que o diagnóstico pode ser preciso, ou verdadeiro, ou impreciso, ou falso. Por exemplo, o médico pode perder os sinais de doença e fazer a determinação incorreta de que o paciente está bem quando está de fato doente. Outro erro possível é decidir que um paciente está doente quando esse paciente é de fato saudável. Os falsos diagnósticos são caros ou perigosos.

Na análise de segurança de rede, o analista de segurança cibernética é apresentado com um alerta. Isso é semelhante a um paciente indo ao médico e dizendo: “Estou doente”. O analista de segurança cibernética, como o médico, precisa determinar se esse diagnóstico é verdadeiro. O analista de segurança cibernética pergunta: “O sistema diz que ocorreu uma exploração. Isso é verdade?”. Os alertas podem ser classificados da seguinte forma:

<span style="color:rgb(255, 255, 0)">Verdadeiro Positivo</span>: o alerta foi verificado como um incidente de segurança real.

<span style="color:rgb(255, 255, 0)">Falso Positivo</span>: O alerta não indica um incidente de segurança real. A atividade benigna que resulta em um falso positivo é às vezes referida como um gatilho benigno.

Uma situação alternativa é que um alerta não foi gerado. A ausência de um alerta pode ser classificada como:

<span style="color:rgb(255, 255, 0)">Verdadeiro Negativo</span>: Nenhum incidente de segurança ocorreu. A atividade é benigna.

<span style="color:rgb(255, 255, 0)">Falso Negativo</span>: Ocorreu um incidente não detectado.

| **Quando um alerta é emitido, ele receberá uma das quatro classificações possíveis.** | True                                                              | False                    |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | ------------------------ |
| **Positivo (Alerta existe)**                                                          | Ocorreu um incidente                                              | Nenhum incidente ocorreu |
| **Negativo (Nenhum alerta existe)**                                                   | Retrieving data. Wait a few seconds and try to cut or copy again. | Ocorreu um incidente     |

**Nota:** eventos “verdadeiros” são desejáveis. Eventos “falsos” são indesejáveis ​​e potencialmente perigosos.

**<span style="color:rgb(255, 255, 0)">Verdadeiros positivos</span>** são o tipo de alerta desejado. Eles significam que as regras que geram alertas funcionaram.

**<span style="color:rgb(255, 255, 0)">Falsos positivos</span>** não são desejáveis, não é preciso investigar alarmes falsos.

**<span style="color:rgb(255, 255, 0)">Verdadeiros negativos</span>** são desejáveis. Eles indicam que o tráfego normal benigno é corretamente ignorado e alertas errôneos não estão sendo emitidos.

**<span style="color:rgb(255, 255, 0)">Falsos negativos</span>** são perigosos. Eles indicam que as explorações não estão sendo detectadas pelos sistemas de segurança que estão em vigor.

Quando os verdadeiros positivos são suspeitos, um analista de segurança cibernética às vezes é obrigado a escalar o alerta para um nível mais alto. Essas informações serão usadas por mais funcionários de segurança sênior que trabalharão para isolar os danos, solucionar vulnerabilidades, mitigar a ameaça e lidar com os requisitos de relatórios. Um analista de segurança cibernética também pode ser responsável por informar o pessoal de segurança de que falsos positivos estão ocorrendo na medida em que o tempo do analista de segurança cibernética é seriamente afetado. Esta situação indica que os sistemas de monitoramento de segurança precisam ser ajustados para se tornarem mais eficientes. Falsos negativos podem ser descobertos bem depois de uma exploração ter ocorrido.
### Análise Determinística e Análise Probabilística
Técnicas estatísticas podem ser usadas para avaliar o risco de que as explorações serão bem-sucedidas em uma determinada rede. Duas abordagens gerais utilizadas para isso são a análise determinística e probabilística, a análise determinística avalia o risco com base no que é conhecido sobre uma vulnerabilidade, nessa abordagem para que a exploração seja bem-sucedida, todas as etapas anteriores do processo de exploração também devem ser.

A análise probabilística estima o sucesso potencial de uma exploração, estimando a probabilidade de que, se uma etapa de uma exploração tiver sido concluída com sucesso, a próxima etapa também será bem-sucedida. A análise probabilística é especialmente útil na análise de segurança de rede em tempo real. As técnicas estatísticas que são projetadas para estimar a probabilidade de que um evento ocorrerá com base na probabilidade de ocorrerem eventos anteriores. Usando esse tipo de análise, os caminhos mais prováveis que uma exploração tomará podem ser estimados e a atenção do pessoal de segurança pode ser focada nesses pontos.

Em uma análise determinística, toda a informação para realizar uma exploração é assumida como sendo conhecida. As características da exploração, como o uso de números de porta específicos, são conhecidas de outras instâncias da exploração ou porque portas padronizadas estão em uso. Na análise probabilística, presume-se que os números de porta que serão utilizados só podem ser previstos com algum grau de confiança. Nessa situação, uma exploração que usa números de porta dinâmicos, por exemplo, não pode ser analisada deterministicamente. Tais explorações foram otimizadas para evitar a detecção por firewalls que usam regras estáticas.

As duas abordagens são resumidas a seguir.

- **Análise Determinística** - Para que uma exploração seja bem-sucedida, todas as etapas anteriores da exploração também devem ser bem-sucedidas. O analista de segurança cibernética conhece as etapas para uma exploração bem-sucedida.
- **Análise Probabilística** - Técnicas estatísticas são usadas para determinar a probabilidade de que uma exploração bem-sucedida ocorrerá com base na probabilidade de que cada etapa da exploração seja bem-sucedida.