#Redes #Firewall #Segurança #Ferramentas 
# Modulo 1: Compreendendo a Defesa.
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
Outra coisa importante de se ter para analisar são os pacotes de rede, quando se ter ferramentas para capturar esses pacotes e analisa-los é possível saber fazer uma análise de problemas de rede, detecção de uso indevido da rede, tentativas de invasão da rede, etc. Existem vários desses analisadores como [[Ferramentas#Wireshark = O [WireShark](https //www.wireshark.org/) (anteriormente conhecido como Ethereal) é um programa que analisa o tráfego de rede, e o organiza por protocolos. As funcionalidades do Wireshark são parecidas com o tcpdump mas com uma interface gráfica, com mais informação e com a possibilidade da utilização de filtros.|WireShark]], [[Ferramentas#TCPDump = O comando [tcpdump](https //www.ibm.com/docs/pt-br/aix/7.3?topic=t-tcpdump-command) imprime os cabeçalhos de pacotes em uma interface de rede que combinam com a expressão booleana. Você pode executar o comando com o sinalizador -w para salvar os dados do pacote em um arquivo para análise adicional.|TCPDump]], Ettercap, Kismet, Ngrep, Ntop, Etherape, entre outras.
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
Barreiras físicas dizem respeito a meios de limitar a entrada de indevidos não autorizados ou indevidos a certos locais/áreas, normalmente elas são cerceamentos ou barreiras físicas , áreas de alta segurança geralmente requerem uma “proteção superior”, como arame farpado ou fio de arame farpado. Os guardas superiores atuam como um impedimento adicional e podem atrasar o invasor, causando ferimentos graves.
## Segurança de Aplicações
## Fortalecimento da Rede 
## Blindagem de Rede
## Resiliência de Cyber Segurança
## Sistema Embarcados
# Modulo 3: Controle de Acesso.
## Modulo 4: Lista de Controle de Acesso.
## Modulo 5: Tecnologias de Firewall.
## Modulo 6: Firewalls de Politica com base de zona.
## Modulo 7: Segurança da Nuvem.
## Modulo 8: Criptografia.
## Modulo 9: Tecnologias e Protocolos.
## Modulo 10: Dados de Segurança Do Rede.
## Modulo 11: Avaliação de Alertas.
