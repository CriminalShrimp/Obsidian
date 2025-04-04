# Objetivos

Parte 1: Snort de pesquisa e IDs de CVE

Parte 2: Classificar alertas em um ambiente Windows

Parte 3: Classificar alertas em um ambiente Unix / Linux

# Histórico/Cenário

Neste laboratório, você classificará alertas de dois ambientes diferentes: Windows e Linux. Você é responsável por determinar se um alerta detectado é um positivo positivo ou um falso positivo. Você é responsável por classificar se os alertas são gerados pelo SIEM ou de realizar verificações de vulnerabilidade. Haverá dois ambientes diferentes aos quais você pode aplicar os alertas gerados.

# Recursos necessários

= Acesso à Internet

# Instruções

## Parte 1: Snort da pesquisa e IDs do CVE

Use sites como mitre.org, snort.org, virustotal.com e sites de fornecedores para pesquisar informações sobre as seguintes IDs de snort (CID) e IDs de CVE. Para cada alerta, forneça as seguintes informações:

=    A lista cruzada entre IDs do snort e números CVE quando disponível.

=    A pontuação do CVSS que indica a gravidade de cada uma das seguintes IDs.

=    Uma breve descrição do alerta.

Você classificará esses alertas nas partes 2 e 3.

#### Perguntas:

1.     Sid 1-54630

Área de Resposta

CVE-2020-8617 - CVSS Pontuação 7.5 High - Usando uma mensagem especialmente criada, um invasor pode fazer com que um servidor BIND alcance um estado inconsistente se o invasor souber (ou adivinharcom êxito) o nome de uma chave TSIG usada pelo servidor.

Ocultar resposta

2.     CVE-2021-3438

Área de Resposta

Um potencial estouro de buffer nos drivers de software de determinados produtos HP LaserJet e impressoras de produtos Samsung pode levar a uma escalada de privilégios.

Ocultar resposta

3.     CVE-2020-5723

Área de Resposta

O UCM6200 series 1.0.20.22 e abaixo armazena senhas de usuário não criptografadas em um banco de dados SQLite. Isso pode permitir que um invasor recupere todas as senhas e obtenha privilégios elevados.

Ocultar resposta

4.     Sid1-46597

Área de Resposta

CVE-2018-8165 - CVSS Pontuação 6.9 Alta - Existe uma vulnerabilidade de elevação de privilégio quando o driver do DirectX Graphics Kernel (DXGKRNL) manipula indevidamente objetos na memória, também conhecido como "Vulnerabilidade de elevação de privilégio do kernel do DirectX Graphics." Isso afeta os servidores Windows Server 2016, Windows 10 e Windows 10.

Ocultar resposta

5.    CVE-2020-28374

Área de Resposta

CVSS Pontuação 8.1 Alta - Em drivers / target / target_core_xcopy.c no kernel do Linux anterior à versão 5.10.7, a verificação de identificador insuficiente no código de destino LIO SCSI pode ser usada por invasores remotos para ler ou gravar arquivos através de diretório transversal em uma solicitação XCOPY, também conhecido como CID-2896c93811e3. Por exemplo, um ataque pode ocorrer através de uma rede se o invasor tiver acesso a um LUN iSCSI. O invasor obtém o controle sobre o acesso a arquivos porque as operações de I / O são enviadas por proxy através de um backstore selecionado pelo invasor.

Ocultar resposta

6.     Sid1-31814

Área de Resposta

Essa atividade é indicativa da atividade de malware em um host. Nesse caso, o sinal de keepalive de saída MALWARE-CNC Win.Trojan.Darkcomet enviado foi detectado. Relatórios do Total de vírus: 50 fornecedores de segurança sinalizaram este arquivo como mal-intencionado.

Ocultar resposta

7.     Sid1-50089

Área de Resposta

CVE-2019-0885 - Pontuação CVSS 5.9 Alta - Existe uma vulnerabilidade de execução remota de código quando o OLE do Microsoft Windows falha ao validar corretamente a entrada do usuário, também conhecida como “Vulnerabilidade de execução remota de código do Windows OLE”.

Ocultar resposta

8.     Sid1-50190

Área de Resposta

CVE-2019-3462 - Pontuação CVSS 8.1 Alta - O saneamento incorreto do campo de redirecionamento 302 no método de transporte HTTP das versões 1.4.8 e anteriores do apt pode levar à injeção de conteúdo por um invasor MITM, possivelmente levando à execução remota de código na máquina de destino . Vários servidores Linux são listados como possíveis alvos.

Ocultar resposta

9.     Sid1-49188

Área de Resposta

Esse evento é gerado quando o SpeakUp linux trojan trisolicita scripts mal-intencionados dos servidores C2. Relatórios do Total de vírus: 30 fornecedores de segurança sinalizaram este arquivo como mal-intencionado. Perl

Ocultar resposta

10.     Sid1-46991

Área de Resposta

CVE-2018-4243 - Pontuação CVSS 5.9 Alta - Um problema foi descoberto emdeterminados produtos da Apple. O iOS anterior à 11.4 é afetado. o macOS anterior à versão 10.13.5 seja afetado. O tvOS anterior à 11.4 é afetado. O watchOS anterior à versão 4.3.1 é afetado. A questão envolve o componente "Kernel". Um estouro de buffer no getvolattrlist permite que os invasores executem código arbitrário em um contexto privilegiado por meio de um aplicativo criado.

Ocultar resposta

## Parte 2: Classificar alertas em um ambiente Windows

Nesse cenário, você está trabalhando principalmente em um ambiente Windows que consiste em PCs com Windows 10, servidores Windows 2016, impressoras HP LaserJet, sistema telefônico IP Grandstream UCM 6200 series e vários softwares.

Use as informações coletadas na Parte 1 para determinar se o alerta deve ser classificado como positivo verdadeiro, falso positivo ou precisando de mais informações sobre o ambiente.

#### Perguntas:

1.     Sid 1-54630

Área de Resposta

Falso positivo nesse ambiente, o BIND está sendo executado em um servidor Linux

Ocultar resposta

2.     CVE-2021-3438

Área de Resposta

Verdadeiro positivo - Como esse ambiente inclui impressoras HP, é muito provável que este alerta

Ocultar resposta

3.     CVE-2020-5723

Área de Resposta

Verdadeiro positivo - O sistema de telefonia IP UCM 6200 series está listado especificamente.

Ocultar resposta

4.     Sid1-46597

Área de Resposta

Verdadeiro positivo - Esse alerta afeta os servidores Windows 10 e Windows 2016.

Ocultar resposta

5.    CVE-2020-28374

Área de Resposta

Falso positivo - O alerta refere-se a sistemas Unix / Linux.

Ocultar resposta

6.     Sid1-31814

Área de Resposta

Verdadeiro positivo - Malware aplicável a sistemas baseados em Windows.

Ocultar resposta

7.     Sid1-50089

Área de Resposta

Verdadeiro positivo - Possibilidade de execução remota para sistemas Windows.

Ocultar resposta

8.     Sid1-50190

Área de Resposta

Falso positivo - O alerta é aplicável a várias distribuições de Linux.

Ocultar resposta

9.     Sid1-49188

Área de Resposta

Falso positivo - Cavalo de Troia Linux, principalmente usando um executável perl.

Ocultar resposta

10.     Sid1-46991

Área de Resposta

Provavelmente falso-positivo, precisa de mais investigação - afeta o MacOS e outros sistemas operacionais Apple. É possível que um usuário tenha trazido seu próprio dispositivo e conectado à rede.

Ocultar resposta

## Parte 3: Classificar alertas em um ambiente Linux

Nesse cenário, você está trabalhando em um ambiente principalmente Linux, que consiste em servidores Linux que fornecem DNS, serviços da Web e e-mail. O ambiente também inclui estações de trabalho Linux, um sistema de telefonia IP da Cisco, impressoras Epson e vários aplicativos de software.

Use as informações coletadas na Parte 1 para determinar se o alerta deve ser classificado como positivo verdadeiro, falso positivo ou precisando de mais informações sobre o ambiente.

#### Perguntas:

1.    Sid 1-54630

Área de Resposta

Verdadeiro positivo nesse ambiente, o BIND está sendo executado em um servidor Linux

Ocultar resposta

2.     CVE-2021-3438

Área de Resposta

mySecretKey

Ocultar resposta

3.     CVE-2020-5723

Área de Resposta

Falso positivo - O sistema de telefone IP em uso é um sistema daCisco.

Ocultar resposta

4.     Sid1-46597

Área de Resposta

Verdadeiro positivo - Esse alerta afeta os servidores Windows 10 e Windows 2016. Esse ambiente está usando estações de trabalho Linux.

Ocultar resposta

5.    CVE-2020-28374

Área de Resposta

Verdadeiro positivo - O alerta refere -se a uma vulnerabilidadedo kernel em sistemas Linux.

Ocultar resposta

6.     Sid1-31814

Área de Resposta

Falso positivo - Malware aplicável a sistemas baseados em Windows. Esse ambiente está usando estações de trabalho Linux.

Ocultar resposta

7.     Sid1-50089

Área de Resposta

Falso positivo - Possibilidade de execução remota parasistemas Windows. Esse ambiente está usando estações de trabalho Linux.

Ocultar resposta

8.     Sid1-50190

Área de Resposta

Verdadeiro positivo - O alerta é aplicável a várias distribuições de Linux.

Ocultar resposta

9.     Sid1-49188

Área de Resposta

Verdadeiro positivo - Cavalo de troia Linux, usando principalmente um executável perl.

Ocultar resposta

10.     Sid1-46991

Área de Resposta

Provavelmente falso-positivo, precisa de mais investigação - afeta o MacOS e outros sistemas operacionais Apple. É possível que um usuário tenha trazido seu próprio dispositivo e conectado à rede.

Ocultar resposta