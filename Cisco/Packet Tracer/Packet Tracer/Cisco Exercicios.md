
# Laboratório - Armazenamento de Autoridade de Certificação
## Objetivos

Parte 1: Certificados Confiáveis pelo Seu Navegador

Parte 2: Verificando o Man-In-Middle

## Histórico/Cenário

Conforme a web evoluiu, também cresceu a necessidade de segurança. HTTPS (onde o 'S' significa segurança) junto com o conceito de Autoridade de Certificação foi introduzido pela Netscape em 1994 e ainda é usado hoje. Neste laboratório, você irá:

Liste todos os certificados confiáveis por seu navegador (preenchidos em seu computador)

Use hashes para detectar se sua conexão com a Internet estiver sendo interceptada (concluída na máquina virtual da estação de trabalho de segurança)

## Recursos necessários

Máquina virtual Security Workstation.

Acesso à Internet

### Parte 1: Certificados Confiáveis pelo Seu Navegador

HTTPS depende de uma entidade de terceiros para validação. Conhecida como Autoridade de Certificação (CA), essa entidade de terceira parte verifica se um nome de domínio realmente pertence à organização que reivindica sua propriedade. Se a verificação for marcada, a CA cria um certificado assinado digitalmente contendo informações sobre a organização, incluindo sua chave pública.

Todo o sistema é baseado no fato de que os navegadores da web e os sistemas operacionais são fornecidos com uma lista de CAs em que confiam. Todos os certificados assinados por qualquer uma das CAs na lista serão vistos pelo navegador como legítimos e automaticamente confiáveis. Para tornar o sistema mais seguro e escalável, as CAs frequentemente distribuem a tarefa de criar e assinar certificados entre muitas CAs filhas. O CA pai é conhecido como CA raiz. Se um navegador confiar em uma CA raiz, ele também confiará em todas as CAs filhas.

**Nota**: Embora os armazenamentos de certificados sejam semelhantes entre os navegadores, este laboratório se concentra em **Chrome 81** e **Firefox 75** . O menu e os gráficos podem ser diferentes para outras versões do navegador da web.

Siga as etapas para exibir a loja da CA em seu navegador:

#### Etapa 1: Exibir os certificados raiz no Chrome.

Você pode fazer este passo na sua máquina local ou usar o Firefox na VM de Workstation de segurança. Se você usa o Firefox, prossiga para a Etapa 2. Se você usa um navegador diferente do Chrome ou Firefox, pesquise na Internet as etapas para exibir seus certificados raiz.

**Nota**: O menu e os gráficos podem ser diferentes para outras versões do navegador Chrome.

a.  Abra o navegador Chrome em seu PC.

b.  Clique no ícone de três pontos na extremidade direita da barra de endereço para exibir as opções do Chrome. Clique em **Configurações**.

![Captura de tela do navegador Chrome destacando o ícone de três pontos à extrema direita da barra de endereço.](https://www.netacad.com/content/nad/1.0/courses/content/m8/pt-BR/assets/8.6.8-1.jpg)

c. Role para baixo para **privacidade e segurança** e clique em **segurança**.

d. Selecione **Gerenciar certificados**.

e. Na janela Certificado, selecione a guia **Trusted Root Certification Authorities** para mostrar todos os certificados e autoridades de certificação confiáveis para o Chrome.

![Captura de tela da janela Certificados com a guia Autoridades de certificação raiz confiáveis selecionadas.](https://www.netacad.com/content/nad/1.0/courses/content/m8/pt-BR/assets/8.6.8-2.jpg)

#### Etapa 2: Exibir os certificados no armazenamento da CA no Firefox.

**Nota**: O menu e os gráficos podem ser diferentes para outras versões do navegador Firefox e entre diferentes sistemas operacionais. O **Firefox 94** na CyberOps Workstation VM é mostrado nesta etapa.

a. Abra o Firefox e clique no ícone Menu. O **ícone** Menu está localizado na extremidade direita da janela do Firefox, próximo à barra de endereço. Clique em **Configurações**.

**![Captura de tela do navegador Firefox mostrando o ícone de menu na extrema direita da janela.](https://www.netacad.com/content/nad/1.0/courses/content/m8/pt-BR/assets/8.6.8-3.jpg)**

b. Clique **em Privacy & Security** no painel esquerdo.

**c.** Role para baixo até a seção Segurança e clique em **View Certificates**.

d. É aberta uma janela que mostra os certificados e autoridades de certificação confiáveis para o Firefox.

![Captura de tela da janela do Gerenciador de certificados com a guia Autoridades selecionada.](https://www.netacad.com/content/nad/1.0/courses/content/m8/pt-BR/assets/8.6.8-4.jpg)

### Parte 2: Verificando o Man-In-Middle

Esta parte é concluída usando a VM de estação de trabalho de segurança.

Um uso comum de hashes é verificar a integridade dos dados, mas eles também podem ser usados para detectar ataques man-in-the-middle HTTPS.

Para proteger os dados do usuário, cada vez mais sites estão migrando para o tráfego criptografado. Conhecidos como HTTPS, os sites usam protocolos como TLS / SSL para criptografar o tráfego do usuário de ponta a ponta. Depois que o tráfego é criptografado corretamente, é muito difícil para qualquer outra parte, exceto o usuário e o site em questão, ver o conteúdo da mensagem criptografada. Isso é bom para os usuários, mas cria um problema para as organizações que desejam analisar esse tráfego. As empresas e organizações geralmente optam por espiar o tráfego gerado por funcionários para fins de monitoramento. Eles precisavam ser capazes de examinar o tráfego criptografado por TLS / SSL. Isso é feito usando um proxy HTTPS.

Os navegadores da web confiam na identidade de um site visitado se o certificado apresentado por esse site for assinado por uma das CAs instaladas no armazenamento de certificados do navegador. Para poder espiar o tráfego criptografado por TLS / SSL de seus usuários, uma empresa ou organização simplesmente adiciona outra CA à lista de CA instalada do navegador do usuário.

Considere o seguinte cenário: A empresa X contrata um novo funcionário e fornece a ele um novo laptop da empresa. Antes de entregar o laptop, o departamento de TI da empresa instala todos os softwares necessários para o trabalho. Entre o software e os pacotes instalados, o departamento de TI também inclui uma CA extra na lista de CAs confiáveis. Essa CA extra aponta para um computador controlado pela empresa conhecido como proxy HTTPS. Como a empresa controla os padrões de tráfego, o proxy HTTPS pode ser colocado no meio de qualquer conexão. Funciona assim:

1. O usuário tenta estabelecer uma conexão segura com o site HTTPS H, hospedado na Internet. H pode ser qualquer site HTTPS: um banco, loja online, servidor de e-mail, etc.

2. Como a empresa controla os padrões de tráfego, ela faz com que todo o tráfego do usuário atravesse o proxy HTTPS. O proxy HTTPS então _personifica_ o site H e apresenta um certificado autoassinado para provar que é H. O proxy HTTPS basicamente diz “Olá, sou o site HTTPS H. Aqui está meu certificado. Foi assinado por ... eu mesmo. ”

3. Como o certificado apresentado é assinado por um dos CAs incluídos no armazenamento de CA do laptop (lembre-se, ele foi adicionado por TI), o navegador da web acredita erroneamente que está realmente se comunicando com H. Observe que, se o CA extra não tivesse sido adicionado a o armazenamento da CA, o laptop não confiaria no certificado e perceberia imediatamente que outra pessoa estava tentando _se passar por_ H.

4. O laptop confia na conexão e estabelece um canal seguro com o proxy HTTPS, acreditando erroneamente que está se comunicando com segurança com H.

5. O proxy HTTPS agora estabelece uma segunda conexão segura com H, o site que o usuário estava tentando acessar desde o início.

6. O proxy HTTPS é agora o ponto final de duas conexões seguras separadas; um estabelecido com o usuário e outro estabelecido com H. Como o HTTPS é o ponto final de ambas as conexões, ele agora pode descriptografar o tráfego de ambas as conexões.

7. O proxy HTTPS agora pode receber tráfego de usuário criptografado por TLS/SSL destinado a H, descriptografá-lo, inspecioná-lo, criptografá-lo novamente usando TLS/SSL e enviá-lo para H. Quando H responde, o proxy HTTPS reverte o processo antes de encaminhar o tráfego para o usuário.

Observe que o processo é mais transparente para o usuário, que vê a conexão como criptografada por TLS/SSL (marcas verdes no navegador). Embora a conexão seja segura (criptografada por TLS / SSL), ela foi estabelecida com um site espúrio.

Mesmo que sua presença seja mais transparente para o usuário, os proxies TLS podem ser facilmente detectados com a ajuda de hashes. Considerando o exemplo acima, como o proxy HTTPS não tem acesso às chaves privadas do site H, o certificado que ele apresenta ao usuário é diferente do certificado apresentado por H. Incluído em cada certificado está um valor conhecido como _impressão digital._ Essencialmente, um hash calculado e assinado pelo emissor do certificado, a impressão digital atua como um resumo exclusivo de todo o conteúdo do certificado. Se uma letra do certificado for modificada, a impressão digital produzirá um valor completamente diferente quando calculada. Por causa dessa propriedade, as impressões digitais são usadas para comparar certificados rapidamente. Voltando ao exemplo acima, o usuário pode solicitar o certificado de H e comparar a impressão digital incluída nele com a fornecida quando a conexão com o site H foi estabelecida. Se as impressões digitais corresponderem, a conexão foi realmente estabelecida com H. Se as impressões digitais não corresponderem, a conexão foi estabelecida com algum outro ponto de extremidade.

Siga as etapas abaixo para avaliar se há um proxy HTTPS em sua conexão.

#### Etapa 1: Coletando a impressão digital correta e não modificada do certificado.

A primeira etapa é coletar algumas impressões digitais do site. Isso é importante porque eles serão usados para comparação posteriormente. A tabela abaixo contém algumas impressões digitais de certificado de site de sites populares.

**Observação**: as impressões digitais SHA-1 mostradas na Tabela 1 podem não ser mais válidas, pois as organizações renovam regularmente seus certificados. Uma impressão digital também é chamada de impressão digital em máquinas com Windows.

**Tabela** **1** **- Sites populares e suas impressões digitais de certificado SHA-1**

|Local|Domínios Cobertos por Certificado|Impressão Digital do Certificado SHA-1  <br>( a partir de maio 2020)|
|---|---|---|
|[www.cisco.com](http://www.cisco.com/)|[www.cisco.com](http://www.cisco.com/)|E2:BD:0B:58:C6:B4:FF:91:D6:23:AB:44:0D:8F:64:76:29:4E:30:0B|
|[www.facebook.com](http://www.facebook.com/)|*.facebook.com|BB:E7:A0:97:C7:92:B2:2D:00:38:12:69:E4:64:E9:04:96:4B:C7:41|
|[www.wikipedia.org](http://www.wikipedia.org/)|*.wikipedia.org|A8:F9:F7:79:BE:DB:3E:EB:59:F0:1D:A6:34:08:A1:64:5D:28:48:44|
|[twitter.com](http://www.twitter.com/)|twitter.com|73:33:BB:96:1D:DB:9C:0C:4F:E5:1C:FF:68:26:CF:5E:3F:50:AB:96|
|[www.linkedin.com](http://www.linkedin.com/)|[www.linkedin.com](http://www.linkedin.com/)|04:BC:C5:09:DD:AE:99:40:7E:99:A5:65:32:68:EC:5D:2D:D7:5A:19|

##### Perguntas:

Quais são as impressões digitais? Por que eles são importantes?



Mostrar resposta

Quem calcula as impressões digitais? Como encontrá-los?



Mostrar resposta

#### Etapa 2: Reúna a impressão digital do certificado em uso pela CyberOps Workstation VM.

Agora que temos as impressões digitais reais, é hora de obter as impressões digitais de um host local e comparar os valores. Se as impressões digitais não corresponderem, o certificado em uso NÃO pertence ao site HTTPS sendo verificado, o que significa que há um proxy HTTPS entre o computador host e o site HTTPS sendo verificado. A correspondência de impressões digitais significa que nenhum proxy HTTPS está instalado.

a. Use os três comandos canalizados abaixo para buscar a impressão digital para Cisco.com. A linha abaixo usa OpenSSL para se conectar a cisco.com na porta 443 (HTTPS), solicitar o certificado e armazená-lo em um arquivo de texto chamado **cisco.pem**. A saída também é mostrada para contexto.

[analyst@secOps ~]$ **echo -n | openssl s_client -connect cisco.com:443 | sed 
-ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > ./cisco.pem**

depth=2 C = BM, O = QuoVadis Limited, CN = QuoVadis Root CA 2

verify return:1

depth=1 C = US, O = HydrantID (Avalanche Cloud Corporation), CN = HydrantID SSL ICA G2

verify return:1

depth=0 C = US, ST = CA, L = San Jose, O = "Cisco Systems, Inc.", CN = www.cisco.com

verify return:1

DONE

b. Opcionalmente, use o comando **cat** para listar o conteúdo do certificado obtido e armazenado no arquivo de texto **cisco.pem** :

[analyst@secOps ~]$ **cat cisco.pem**

-----BEGIN CERTIFICATE-----

MIIG1zCCBL+gAwIBAgIUKBO9xTQoMemc9zFHNkdMW+SgFO4wDQYJKoZIhvcNAQEL

BQAwXjELMAkGA1UEBhMCVVMxMDAuBgNVBAoTJ0h5ZHJhbnRJRCAoQXZhbGFuY2hl

IENsb3VkIENvcnBvcmF0aW9uKTEdMBsGA1UEAxMUSHlkcmFudElEIFNTTCBJQ0Eg

RzIwHhcNMTcxMjA3MjIxODU1WhcNMTkxMjA3MjIyODAwWjBjMQswCQYDVQQGEwJV

UzELMAkGA1UECAwCQ0ExETAPBgNVBAcMCFNhbiBKb3NlMRwwGgYDVQQKDBNDaXNj

byBTeXN0ZW1zLCBJbmMuMRYwFAYDVQQDDA13d3cuY2lzY28uY29tMIIBIjANBgkq

yvo6dWpJdSircYy8HG0nz4+936+2waIVf1BBQXZUjNVuws74Z/eLIpl2c6tANmE0

q1i7fiWgItjDQ8rfjeX0oto6rvp8AXPjPY6X7PT1ulfhkLYnxqXHPETRwr8l5COO

MDEh95cRxATXNAlWAwLcBT7lDmrGron6rW6hDtuUPPG/rjZeZbNww5p/nT3EXX2L

Rh+m0R4j/tuvy/77YRWyp/VZhmSLrvZEYiVjM2MgCXBvqR+aQ9zWJkw+CAm5Z414

Eiv5RLctegYuBUMGTH1al9r5cuzfwEg2mNkxl4I/mtDro2kDAv7bcTm8T1LsZAO/

1bWvudsrTA8jksw+1WGAEd9bHi3ZpJPYedlL

-----END CERTIFICATE-----

[analyst@secOps ~]$

c. Agora que o certificado está salvo no arquivo de texto **cisco.pem** , use o comando abaixo para extrair e exibir sua impressão digital:

[analyst@secOps ~]$ **openssl x509 -noout -in cisco.pem -fingerprint -sha1**

SHA1 Fingerprint=64:19:CA:40:E2:1B:3F:92:29:21:A9:CE:60:7D:C9:0C:39:B5:71:3E

[analyst@secOps ~]$

**Nota**: O valor da sua impressão digital pode ser diferente por dois motivos. Primeiro, você pode estar usando um sistema operacional diferente da VM de estação de trabalho de segurança. Em segundo lugar, os certificados são atualizados regularmente, alterando o valor da impressão digital.

#### Perguntas:

Qual algoritmo hash foi usado pelo OpenSSL para calcular a impressão digital?



Mostrar resposta

Por que esse algoritmo específico foi escolhido? Isso importa?



Mostrar resposta

#### Etapa 3: Compare as impressões digitais

Use a Tabela 1 para comparar a impressão digital do certificado adquirida diretamente do site Cisco HTTPS com aquela adquirida de sua rede. Lembre-se de que as impressões digitais podem mudar com o tempo.

##### Perguntas:

As impressões digitais são iguais?



Mostrar resposta

O que isso significa?



Mostrar resposta

Este método é 100% infalível?



Mostrar resposta

### Parte 3: Desafios (opcional)

a. Verifique as impressões digitais dos sites mostrados na Tabela 1, mas usando a GUI do seu navegador da web.

**Dicas**: Encontre uma maneira de exibir a impressão digital por meio da GUI do navegador. Lembre-se: o Google é útil neste exercício, e o Windows costuma se referir à impressão digital como **Thumbprint** .

b. Use o OpenSSL (Parte 2, Etapas 1 a 3) para verificar todas as impressões digitais listadas na Tabela 1
##### Perguntas para reflexão

O que seria necessário para o proxy HTTPS funcionar?



A máquina local teria que confiar cegamente no proxy HTTPS. Empresas e organizações que desejam monitorar o tráfego HTTPS obtêm essa confiança instalando o certificado do proxy HTTPS no armazenamento de certificados raiz da máquina local. Nesse cenário, as máquinas locais confiarão no proxy HTTPS, permitindo que ele descriptografe o tráfego sem nenhum aviso.


# Laboratório - Calculando Hashes
## Objetivos

Parte 1: Hash de um arquivo de texto com OpenSSL

Parte 2: Verificando Hashhes

## Histórico/Cenário

Funções de hash são algoritmos matemáticos projetados para tomar dados como entrada e gerar uma cadeia de caracteres única de tamanho fixo, também conhecido como o hash. Projetado para ser rápido, as funções de hash são muito difíceis de reverter; é muito difícil recuperar os dados que criaram qualquer hash determinado, com base apenas no hash. Outra propriedade importante da função hash é que mesmo a menor alteração feita para os dados de entrada produz um hash completamente diferente.

Embora o OpenSSL possa ser usado para gerar e comparar hashes, outras ferramentas estão disponíveis. Algumas dessas ferramentas também estão incluídas neste laboratório.

## Recursos necessários

Máquina virtual de estação de trabalho de segurança

## Instruções

### Parte 1: Hash de um arquivo de texto com OpenSSL

OpenSSL pode ser usado como uma ferramenta autônoma para hash. Para criar um hash de um arquivo de texto, siga as etapas abaixo:

a. Na máquina virtual de estação de trabalho de segurança, abra uma janela de terminal.

b. Como o arquivo de texto a ser criptografado está no diretório /home/analyst/lab.support.files/, mude para esse diretório:

[analyst@secOps ~]$ **cd /home/analyst/lab.support.files/**

c. Digite o comando abaixo para listar o conteúdo do arquivo de texto letter_to_grandma.txt na tela:

[analyst@secOps lab.support.files]$ **cat letter_to_grandma.txt**

Hi Grandma,

I am writing this letter to thank you for the chocolate chip cookies you sent me. I got them this morning and I have already eaten half of the box! They are absolutely delicious!

I wish you all the best. Love,

Your cookie-eater grandchild.

d. Na mesma janela de terminal, execute o comando abaixo para criptografar o arquivo de texto. O comando usará SHA-2-256 como o algoritmo de hash para gerar um hash do arquivo de texto. O hash será exibido na tela depois que o OpenSSL o calculou.

[analyst@secOps lab.support.files]$ **openssl sha256 letter_to_grandma.txt**

SHA256 (letter_to_grandma.txt) = deff9c9bbece44866796ff6cf21f2612fbb77aa1b2515a900bafb29be118080b

Observe o formato da saída. O OpenSSL exibe o algoritmo de hash usado, SHA-256, seguido pelo nome do arquivo usado como dados de entrada. O hash SHA-256 em si é exibido após o sinal de igual ('=').

e. Funções de hash são úteis para verificar a integridade dos dados, independentemente de se tratar de uma imagem, uma música ou um arquivo de texto simples. A menor alteração resulta em um hash completamente diferente. Os hashes podem ser calculados antes e depois da transmissão, e depois comparados. Se os hashes não corresponderem, os dados foram modificados durante a transmissão.

Vamos modificar o arquivo de texto letter_to_grandma.txt e recalcular o hash MD5. Execute o comando abaixo para abrir **o nano,** um editor de texto de linha de comando.

[analyst@secOps lab.support.files]$ **nano letter_to_grandma.txt**
Usando nano, altere a primeira frase de 'Hi Grandma' para 'Hi Grandpa'. Observe que estamos mudando apenas um caractere, 'm' para 'p'. Após a alteração ter sido feita, pressione as teclas <CONTROL+X> para salvar o arquivo modificado. Pressione 'Y' para confirmar o nome e salvar o arquivo. Pressione a **Enter** tecla e você sairá de nano para continuar na próxima etapa.


f. Agora que o arquivo foi modificado e salvo, execute o mesmo comando novamente para gerar um hash SHA-2-256 do arquivo.

[analyst@secOps lab.support.files]$ **openssl sha256 letter_to_grandma.txt**

SHA256 (letter_to_grandma.txt) = 43302c4500b7c4b8e574ba27a59d83267812493c029fd054c9242f3ac73100bc

#### Pergunta:

O novo hash é diferente do hash calculado no item (d)? Quão diferente?


g. Um algoritmo de hash com comprimento de bits mais longo, como SHA-2-512, também pode ser usado. Para gerar um hash SHA-2-512 do arquivo letter_to_grandma.txt, use o comando abaixo:

[analyst@secOps lab.support.files]$ **openssl sha512 letter_to_grandma.txt**

SHA512 (letter_to_grandma.txt) = 7c35db79a06aa30ae0f6de33f2322fd419560ee9af9cedeb6e251f2f1c4e99e0bbe5d2fc32ce501468891150e3be7e288e3e568450812980c9f8e3a31d3

[analyst@secOps lab.support.files]$

h. Use **sha256sum** e **sha512sum** para Generatesha-2-256 e SHA-2-512 hash do arquivo letter_to_grandma.txt:

[analyst@secOps lab.support.files]$ **sha256sum letter_to_grandma.txt**

43302c4500b7c4b8e574ba27a59d83267812493c029fd054c9242f3ac73100bc  letter_to_grandma.txt

[analyst@secOps lab.support.files]$ **sha512sum letter_to_grandma.txt**

7c35db79a06aa30ae0f6de33f2322fd419560ee9af9cedeb6e251f2f1c4e99e0bbe5d2fc32ce501468891150e3be7e288e3e568450812980c9f8288e3103a1d3  letter_to_grandma.txt

#### Pergunta:

Os hashes gerados com **sha256sum** e **sha512sum** combinam os hashes gerados em itens (f) e (g), respectivamente? Explique.



Mostrar resposta

**Nota**: SHA-2 é o padrão recomendado para hash. Embora o SHA-2 ainda não tenha sido efetivamente comprometido, os computadores estão se tornando cada vez mais poderosos. Espera-se que esta evolução natural em breve torne possível que os atacantes quebrem SHA-2.

SHA-3 é o mais novo algoritmo de hash e, eventualmente, ser o substituto para a família SHA-2 de hashes.

**Nota**: A VM de estação de trabalho de segurança inclui apenas suporte para SHA-2-224, SHA-2-256, e SHA-2-512 (**sha224sum**, **sha256sum**, e **sha512sum**, respectivamente).

### Parte 2: Verificando Hashhes

Como mencionado anteriormente, um uso comum para hashes é verificar a integridade do arquivo. Siga as etapas abaixo para usar hashes SHA-2-256 para verificar a integridade de sample.img, um arquivo baixado da Internet.

a. Junto com sample.img, Sample.img_sha256.sig também foi baixado. Sample.img_sha256.sig é um arquivo contendo o hash SHA-2-256 que foi computado pelo site. Primeiro, use o comando cat para exibir o conteúdo do arquivo Sample.img_sha256.sig:

[analyst@secOps lab.support.files]$ **cat sample.img_SHA256.sig**

c56c4724c26eb0157963c0d62b76422116be31804a39c82fd44ddf0ca5013e6a

b. Use SHA256Sum para calcular o hash SHA-2-256 do arquivo exemplo.img:

[analyst@secOps lab.support.files]$ **sha256sum sample.img**

c56c4724c26eb0157963c0d62b76422116be31804a39c82fd44ddf0ca5013e6a  sample.img

#### Pergunta:

O sample.img foi baixado sem erros? Explique.

**Observação**: Embora a comparação de hashes seja um método relativamente robusto para detectar erros de transmissão, há maneiras melhores de garantir que o arquivo não tenha sido adulterado. Ferramentas, como o **gpg** , fornecem um método muito melhor para garantir que o arquivo baixado não foi modificado por terceiros e é de fato o arquivo que o editor pretendia publicar.

# Laboratório - Classificar alertas

## Objetivos

Parte 1: Snort de pesquisa e IDs de CVE

Parte 2: Classificar alertas em um ambiente Windows

Parte 3: Classificar alertas em um ambiente Unix / Linux

## Histórico/Cenário

Neste laboratório, você classificará alertas de dois ambientes diferentes: Windows e Linux. Você é responsável por determinar se um alerta detectado é um positivo positivo ou um falso positivo. Você é responsável por classificar se os alertas são gerados pelo SIEM ou de realizar verificações de vulnerabilidade. Haverá dois ambientes diferentes aos quais você pode aplicar os alertas gerados.

## Instruções

### Parte 1: Snort da pesquisa e IDs do CVE

Use sites como mitre.org, snort.org, virustotal.com e sites de fornecedores para pesquisar informações sobre as seguintes IDs de snort (CID) e IDs de CVE. Para cada alerta, forneça as seguintes informações:

A lista cruzada entre IDs do snort e números CVE quando disponível.

A pontuação do CVSS que indica a gravidade de cada uma das seguintes IDs.

Uma breve descrição do alerta.

Você classificará esses alertas nas partes 2 e 3.

##### Perguntas:

1. Sid 1-54630


CVE-2020-8617 - CVSS Pontuação 7.5 High - Usando uma mensagem especialmente criada, um invasor pode fazer com que um servidor BIND alcance um estado inconsistente se o invasor souber (ou adivinharcom êxito) o nome de uma chave TSIG usada pelo servidor.


2. CVE-2021-3438


Um potencial estouro de buffer nos drivers de software de determinados produtos HP LaserJet e impressoras de produtos Samsung pode levar a uma escalada de privilégios.


3. CVE-2020-5723


O UCM6200 series 1.0.20.22 e abaixo armazena senhas de usuário não criptografadas em um banco de dados SQLite. Isso pode permitir que um invasor recupere todas as senhas e obtenha privilégios elevados.


4. Sid1-46597


CVE-2018-8165 - CVSS Pontuação 6.9 Alta - Existe uma vulnerabilidade de elevação de privilégio quando o driver do DirectX Graphics Kernel (DXGKRNL) manipula indevidamente objetos na memória, também conhecido como "Vulnerabilidade de elevação de privilégio do kernel do DirectX Graphics." Isso afeta os servidores Windows Server 2016, Windows 10 e Windows 10.


5.    CVE-2020-28374


CVSS Pontuação 8.1 Alta - Em drivers / target / target_core_xcopy.c no kernel do Linux anterior à versão 5.10.7, a verificação de identificador insuficiente no código de destino LIO SCSI pode ser usada por invasores remotos para ler ou gravar arquivos através de diretório transversal em uma solicitação XCOPY, também conhecido como CID-2896c93811e3. Por exemplo, um ataque pode ocorrer através de uma rede se o invasor tiver acesso a um LUN iSCSI. O invasor obtém o controle sobre o acesso a arquivos porque as operações de I / O são enviadas por proxy através de um backstore selecionado pelo invasor.


6. Sid1-31814


Essa atividade é indicativa da atividade de malware em um host. Nesse caso, o sinal de keepalive de saída MALWARE-CNC Win.Trojan.Darkcomet enviado foi detectado. Relatórios do Total de vírus: 50 fornecedores de segurança sinalizaram este arquivo como mal-intencionado.


7. Sid1-50089


CVE-2019-0885 - Pontuação CVSS 5.9 Alta - Existe uma vulnerabilidade de execução remota de código quando o OLE do Microsoft Windows falha ao validar corretamente a entrada do usuário, também conhecida como “Vulnerabilidade de execução remota de código do Windows OLE”.


8. Sid1-50190


CVE-2019-3462 - Pontuação CVSS 8.1 Alta - O saneamento incorreto do campo de redirecionamento 302 no método de transporte HTTP das versões 1.4.8 e anteriores do apt pode levar à injeção de conteúdo por um invasor MITM, possivelmente levando à execução remota de código na máquina de destino . Vários servidores Linux são listados como possíveis alvos.


9. Sid1-49188


Esse evento é gerado quando o SpeakUp linux trojan trisolicita scripts mal-intencionados dos servidores C2. Relatórios do Total de vírus: 30 fornecedores de segurança sinalizaram este arquivo como mal-intencionado. Perl


10. Sid1-46991


CVE-2018-4243 - Pontuação CVSS 5.9 Alta - Um problema foi descoberto emdeterminados produtos da Apple. O iOS anterior à 11.4 é afetado. o macOS anterior à versão 10.13.5 seja afetado. O tvOS anterior à 11.4 é afetado. O watchOS anterior à versão 4.3.1 é afetado. A questão envolve o componente "Kernel". Um estouro de buffer no getvolattrlist permite que os invasores executem código arbitrário em um contexto privilegiado por meio de um aplicativo criado.


### Parte 2: Classificar alertas em um ambiente Windows

Nesse cenário, você está trabalhando principalmente em um ambiente Windows que consiste em PCs com Windows 10, servidores Windows 2016, impressoras HP LaserJet, sistema telefônico IP Grandstream UCM 6200 series e vários softwares.

Use as informações coletadas na Parte 1 para determinar se o alerta deve ser classificado como positivo verdadeiro, falso positivo ou precisando de mais informações sobre o ambiente.

##### Perguntas:

1. Sid 1-54630


Falso positivo nesse ambiente, o BIND está sendo executado em um servidor Linux


2. CVE-2021-3438


Verdadeiro positivo - Como esse ambiente inclui impressoras HP, é muito provável que este alerta


3. CVE-2020-5723


Verdadeiro positivo - O sistema de telefonia IP UCM 6200 series está listado especificamente.


4. Sid1-46597


Verdadeiro positivo - Esse alerta afeta os servidores Windows 10 e Windows 2016.


5.    CVE-2020-28374


Falso positivo - O alerta refere-se a sistemas Unix / Linux.


6. Sid1-31814


Verdadeiro positivo - Malware aplicável a sistemas baseados em Windows.


7. Sid1-50089


Verdadeiro positivo - Possibilidade de execução remota para sistemas Windows.


8. Sid1-50190


Falso positivo - O alerta é aplicável a várias distribuições de Linux.


9. Sid1-49188


Falso positivo - Cavalo de Troia Linux, principalmente usando um executável perl.


10. Sid1-46991

Provavelmente falso-positivo, precisa de mais investigação - afeta o MacOS e outros sistemas operacionais Apple. É possível que um usuário tenha trazido seu próprio dispositivo e conectado à rede.


### Parte 3: Classificar alertas em um ambiente Linux

Nesse cenário, você está trabalhando em um ambiente principalmente Linux, que consiste em servidores Linux que fornecem DNS, serviços da Web e e-mail. O ambiente também inclui estações de trabalho Linux, um sistema de telefonia IP da Cisco, impressoras Epson e vários aplicativos de software.

Use as informações coletadas na Parte 1 para determinar se o alerta deve ser classificado como positivo verdadeiro, falso positivo ou precisando de mais informações sobre o ambiente.

##### Perguntas:

1.    Sid 1-54630


Verdadeiro positivo nesse ambiente, o BIND está sendo executado em um servidor Linux


2. CVE-2021-3438


mySecretKey


3. CVE-2020-5723


Falso positivo - O sistema de telefone IP em uso é um sistema daCisco.


4. Sid1-46597


Verdadeiro positivo - Esse alerta afeta os servidores Windows 10 e Windows 2016. Esse ambiente está usando estações de trabalho Linux.


5.    CVE-2020-28374


Verdadeiro positivo - O alerta refere -se a uma vulnerabilidadedo kernel em sistemas Linux.


6. Sid1-31814


Falso positivo - Malware aplicável a sistemas baseados em Windows. Esse ambiente está usando estações de trabalho Linux.


7. Sid1-50089


Falso positivo - Possibilidade de execução remota parasistemas Windows. Esse ambiente está usando estações de trabalho Linux.


8. Sid1-50190


Verdadeiro positivo - O alerta é aplicável a várias distribuições de Linux.



9. Sid1-49188


Verdadeiro positivo - Cavalo de troia Linux, usando principalmente um executável perl.


10. Sid1-46991


Provavelmente falso-positivo, precisa de mais investigação - afeta o MacOS e outros sistemas operacionais Apple. É possível que um usuário tenha trazido seu próprio dispositivo e conectado à rede.

# Laboratório - Configurar autenticação e autorização no Linux

## Objetivos

Parte 1: Adicionar um novo grupo para usuários

Parte 2: Adicionar usuários ao novo grupo

Parte 3: Alternar usuários e modificar permissões

Parte 4: Modificar permissões no modo absoluto

## Histórico/Cenário

Neste laboratório, você usará a linha de comando do Linux para criar um grupo para novos usuários e adicionar usuários ao grupo. Cada usuário receberá uma senha para autenticação no login. Em seguida, você modificará as permissões para autorizar os privilégios de leitura, gravação e execução para usuários e grupos.

## Recursos necessários

PC com o **CSE-LABVM** instalado no VirtualBox

## Instruções

### Parte 1: Adicionar um novo grupo para usuários

Nesta parte, você adicionará um novo grupo de usuários à máquina virtual.

#### Etapa 1: Abrir uma janela de terminal no CSE-LABVM.

a.   Inicie o **CSE-LABVM.**

b.   Clique duas vezes no ícone **Terminal** para abrir um terminal.

#### Etapa 2: Escalar privilégios para o nível raiz.

Digite o comando **sudo su** e entre com a senha **password** quando a senha for solicitada.

cisco@labvm:~$**sudo su**

[sudo]senha para cisco:

root@labvm:/home/cisco#

#### Etapa 3: Adicionar um novo grupo chamado RH.

Insira o comando **groupadd**RH.

root@ubuntu:/home/cisco#**groupadd HR**

#### Etapa 4: Verifique se o novo grupo foi adicionado.

Insira o comando **cat /etc/group** para verificar se RH foi adicionado.

root@ubuntu:/home/cisco#**cat /etc/group**

root:x:0:

daemon:x:1:

bin:x:2:

sys:x:3:

output omitted

Alice:x:1000:

Bob:x:1001:

Véspera:x:1002:

Eric:x:1003:

Xnobody:x:1004:

RH:x:1005:

O novo grupo RH será adicionado na parte inferior do arquivo /etc/group com o ID de grupo 1005.

### Parte 2: Adicionar usuários ao novo grupo

Nesta parte, você adicionará contas de usuário de Jenny e Joe ao grupo de RH.

#### Etapa 1: adicionar Jenny como um novo usuário e movê-la para o grupo de RH.

a.  Preencha o seguinte para adicionar Jenny como usuário:

1)    Insira o **comando adduser jenny** e pressione **Enter.**

2)    Insira **jenPass** como a senha e pressione **Enter.**

3)    Digite novamente a nova senha e pressione **Enter.**

4)    Insira **Jenny** para Nome completo e pressione **Enter.**

5)    No restante da configuração, pressione **Enter**.

6)    Insira**Y** para verificar se as informações estão corretas e pressione **Enter.**

root@labvm:/home/cisco# **adduser jenny**

Adicionando usuário `jenny '...

Adicionando novo grupo `jenny '(1006) ...

Adicionando o novo usuário `jenny '(1005) com o grupo` jenny' ...

Criando o diretório inicial `/ home / jenny '...

Copiando arquivos de `/ etc / skel '...

Nova senha: **jenPass**

Redigitar nova senha: **jenPass**

passwd: senha atualizada com êxito

Alterando as informações de usuário de jenny

Insira o novo valor ou pressione ENTER para o padrão

  Nome completo []: **Jenny**

   Número da sala []:

   Telefone de trabalho []:

   Telefone residencial []:

   Outro []:

As informações estão corretas? [Y/n] **Y**

root@labvm:/home/cisco#

b.   Mova **jenny** para o grupo de RH. Insira o comando **usermod -G HR jenny** para mover o **jenny** para o grupo de RH.

root@ubuntu:/home/cisco# **usermod –G HR jenny**

#### Etapa 2: adicionar Joe como um novo usuário e movê-lo para o grupo de RH.

a.   Insira o comando **adduser joe** e siga as etapas para atribuir ao usuário **joe** a senha **joePass** e o nome completo **Joe**.

root@labvm:/home/cisco# **adduser jenny**

Adicionando usuário `joe'...

Adicionando novo grupo `joe '(1007) ...

Adicionando novo usuário `joe '(1006) com o grupo` joe' ...

Criando o diretório inicial `/ home / joe '...

Copiando arquivos de `/ etc / skel '...

Nova senha: **joePass**

Redigitar nova senha: **jenPass**

passwd: senha atualizada com êxito

Alterando as informações de usuário para joe

Insira o novo valor ou pressione ENTER para o padrão

   Nome completo []: **Joe**

   Número da sala []:

   Telefone de trabalho []:

   Telefone residencial []:

   Outro []:

As informações estão corretas? [Y/n] **Y**

b.   Coloque o usuário **joe** no grupo de HR .

root@ubuntu:/home/cisco# **usermod –G HR joe**

#### Etapa 3: Verifique os usuários recém-criados no arquivo passwd .

Insira o comando **cat / etc / passwd** para verificar os novos usuários no arquivo passwd.

root@ubuntu:/home/cisco# **cat /etc/passwd**

root:x:0:0:root:/root:/bin/bash

daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin

bin:x:2:2:bin:/bin:/usr/sbin/nologin

sys:x:3:3:sys:/dev:/usr/sbin/nologin

output omitted

Xnobody:x:1004:1004::/home/Xnobody:/bin/sh

jenny:x:1005:1006:Jenny,,,:/home/jenny:/bin/bash

joe:x:1006:1007:Joe,,,:/home/joe:/bin/bash

#### Etapa 4: Visualize os usuários criados no arquivo shadow .

Insira o comando **cat /etc/shadow** para verificar os novos usuários no arquivo shadow.

root@labvm:/home/cisco# **cat /etc/shadow**

root:!:18704:0:99999:7:::

daemon:*:18704:0:99999:7:::

bin:*:18704:0:99999:7:::

sys:*:18704:0:99999:7:::

output omitted

Xnobody:!:18704:0:99999:7:::

jenny:$6$VmEFD7wi6zHV8VH5$m2K8U2wpONkvTXzf9uSxSHitbcwAQMEmNiYg8ICnBpdct9dxqr3Hh8EGvxaIasa9fUw.mtB4GGkQYvoZHAFSa/:18705:0:99999:7:::

joe:$6$Ga2C7801c2vb7ias$G9OdK91gnLCnq.5vgpUJjn0/KyWKkXmRemqoGJgBFH0QejpmRYZxQhmS42eZG0SBApc1Z2Q/gsfwuD6oLUh.W.:18705:0:99999:7:::

### Parte 3: Alternar usuários e modificar permissões

Nesta parte, você vai fazer login como jenny, explorar diretórios e alterar permissões.

#### Etapa 1: Alternar usuário de root para jenny.

a.  Para alternar para a área de trabalho de Jenny, clique em **Menu** na parte inferior esquerda da área de trabalho e clique em **Logout**.

b.   Clique em **Switch User (Alternar usuário)** na caixa de diálogo.

c.   Clique em **Jenny** na lista de usuários disponíveis e digite a senha **jenPass**.

d.   A área de trabalho de Jenny é carregada. Aqui, você pode clicar com o botão direito do mouse na área de trabalho e escolher **Abrir no Terminal**.

jenny@labvm: ~/Desktop$

#### Etapa 2: explorar o ambiente da Jenny.

a.  Insira o comando **pwd** para imprimir o diretório atual e, em seguida, navegue até o diretório **/home** com o comando **cd ../ ..**

jenny@labvm:~/Desktop$ **pwd**

/home/jenny/Desktop

jenny@labvm:~/Desktop$ **cd ../..**

jenny@labvm:/home$

b.   Insira o comando **ls -l** para listar todos os diretórios em **/home**, suas permissões e usuários.

jenny@labvm:/home$ **ls -l**

total 28

drwxr-xr-x  2 Alice Alice 4096 Mar 18 21:58 Alice

drwxr-xr-x  2 Bob   Bob   4096 Mar 18 21:58 Bob

drwxr-xr-x 12 cisco cisco 4096 Mar 19 20:02 cisco

drwxr-xr-x  2 Eric  Eric  4096 Mar 18 21:58 Eric

drwxr-xr-x  2 Eve   Eve   4096 Mar 18 21:58 Eve

drwxr-xr-x  9 jenny jenny 4096 Mar 19 19:58 jenny

drwxr-xr-x  2 joe   joe   4096 Mar 19 19:44 joe

O sistema operacional Linux tem um total de 10 letras ou traços nos campos de permissões: Por exemplo, esses diretórios pessoais têm as seguintes permissões: drwxr-xr-x.

o   A **d** no primeiro campo indica que este é um diretório. Um traço (**-**) significa que é um arquivo.

o    O próximo conjunto de três caracteres corresponde a permissão dos usuários (**rwx**). Por exemplo, o usuário, **jenny**, é proprietário do diretório e pode **ler**, **escrever** e **executar o arquivo**.

o    O segundo conjunto de caracteres é para permissões de grupo (**rw-**). O grupo é **jenny**, o que significa que nenhum grupo, além de jenny, pode gravar neste diretório.

o    O terceiro conjunto de caracteres é para quaisquer outras permissões de usuário ou grupo (**r-x**). Qualquer outro usuário ou grupo no computador pode ler ou executar, mas não pode gravar no diretório.

c.  Como Jenny, digite o comando **cd joe** para entrar no diretório de Joe. Observe que somos capazes de navegar até o diretório de Joe porque a permissão para outros é **r-x**. O x permite que qualquer pessoa entre no diretório.

jenny@labvm:/home$ **cd joe**

jenny@labvm:/home/joe$

d.  Enquanto estiver no diretório de Joe, digite o comando **touch new.txt** para criar um arquivo. Você foi negado porque o usuário **jenny** não tem permissão para gravar no diretório de Joe.

jenny@labvm:/home/joe$ **touch new.txt**

touch: cannot touch 'new.txt': Permission denied

jenny@labvm:/home/joe$

e.   Insira o comando **cd ..** para sair do diretório inicial de Joe.

jenny@labvm:/home/joe$ **cd ..**

jenny@labvm:/home$

#### Etapa 3: Faça login como root.

Joe pode não querer que Jenny leia o conteúdo do diretório. O acesso raiz (root) ou outro superusuário pode alterar as permissões de diretório para negar o acesso de leitura de Jenny, ou qualquer outro usuário ou grupo, ao diretório inicial de Joe.

a.   Faça login como usuário **cisco** com a senha como a **password**. Use o comando **su cisco**.

jenny@labvm:/home$ **su cisco**

Senha:

b.  Insira o comando **sudo -i** para alternar para root e digite a senha como a **password**.

cisco@labvm:~$ **sudo -i**

[sudo] password for cisco: **password**

#### Etapa 4: Modificar as permissões para o diretório pessoal de Joe.

Navegue até o diretório inicial e digite o comando **chmod o-x joe** para alterar a permissão no diretório inicial de Joe para não executável para outros usuários e grupos.

root@labvm:~# **cd /home**

root@labvm:/home# **chmod o-x joe**

root@labvm:/home# **ls -1**

total 28

drwxr-xr-x  2 Alice Alice  4096 Mar 18 21:58

drwxr-xr-x  2 Bob   Bob    4096 Mar 18 21:58

drwxr-xr-x 12 cisco cisco  4096 Mar 19 20:02

drwxr-xr-x  2 Eric  Eric   4096 Mar 18 21:58

drwxr-xr-x  2 Eve   Eve    4096 Mar 18 21:58

drwxr-xr-x  9 jenny jenny  4096 Mar 20 14:02

drwxr-xr--  2 joe   joe    4096 Mar 19 19:44

#### Etapa 5: Verificar se Jenny não consegue mais acessar o diretório de Joe.

a.  Deslogue (logout) como **root** e o usuário **cisco**.

root@labvm:/home# **exit**

logout

cisco@labvm:~$ **exit**

logout

jenny@labvm:/home$

b.   Insira o comando **cd joe** para tentar navegar até o diretório de Joe. Observe que a permissão é negada.

jenny@labvm:/home$ **cd joe**

bash: cd: joe: Permission denied

jenny@labvm:/home$

O gráfico abaixo mostra exemplos de outras maneiras de usar o comando **chmod**:

|chmod command|Resultados.|
|---|---|
|**chmod u+rwx**|Adiciona permissões de leitura, edição e execução para o usuário|
|**chmod u+rw**|Adiciona permissões de leitura e edição para o usuário|
|**chmod o+r**|Adiciona permissão de leitura para outros|
|**chmod g-rwx**|Remove permissões de leitura, edição e execução para o grupo|

Linha em branco, sem informações adicionais

### Parte 4: Modificar permissões no modo absoluto

Na parte anterior, você alterou as permissões no modo simbólico. No modo simbólico, o administrador usa o comando **chmod** com uma combinação de letras e símbolos para adicionar ou remover permissões. Nesta parte, você usará o comando **chmod** e os valores octal para definir permissões para cada tripleto de permissões (rwx) para usuário, grupo e outro.

#### Etapa 1: Alternar usuário de jenny para joe.

a.  Para alternar para a área de trabalho de Joe, clique em **Menu** na parte superior esquerda da área de trabalho. Na parte inferior do menu suspenso, clique no botão com a ponta da ferramenta **Finalizar a sessão atual**.

b.   Clique em **Switch User (Alternar usuário)** na caixa de diálogo.

c.  Clique em **Joe** na lista de usuários disponíveis e digite a senha **joePass**.

d.   A área de trabalho de Joe é carregada. Aqui, você pode clicar com o botão direito do mouse na área de trabalho e escolher **Abrir no Terminal**.

joe@labvm:~/Desktop$

#### Etapa 2: Explorar o ambiente de Joe.

a.  Insira o comando **pwd** para imprimir o diretório atual e, em seguida, navegue até o diretório **/home** com o comando **cd ../ ..**

joe@labvm:~/Desktop$ **pwd**

/home/joe/Desktop

joe@labvm:~/Desktop$ **cd ../..**

joe@labvm:/home$

b.   Insira o comando **ls -l** para listar todos os diretórios em **/home**, suas permissões e usuários. Observe que a pasta do Joe está configurada para que “others” não possam acessam a pasta.

joe@labvm:/home$ **ls -l**

total 28

drwxr-xr-x  2 Alice Alice 4096 Mar 18 21:58 Alice

drwxr-xr-x  2 Bob   Bob   4096 Mar 18 21:58 Bob

drwxr-xr-x 12 cisco cisco 4096 Mar 19 20:02 cisco

drwxr-xr-x  2 Eric  Eric  4096 Mar 18 21:58 Eric

drwxr-xr-x  2 Eve   Eve   4096 Mar 18 21:58 Eve

drwxr-xr-x  9 jenny jenny 4096 Mar 20 14:02 jenny

drwxr-xr--  9 joe   joe   4096 Mar 20 15:01 joe

#### Etapa 3: Use o modo absoluto para modificar e, em seguida, verifique as permissões para o diretório de Joe.

A outra forma de atribuir permissões, além de usar permissões simbólicas, é o uso de permissões absolutas. As permissões absolutas usam um número octal de três dígitos para representar as permissões para o responsável, grupo e outros.

A tabela abaixo define cada valor absoluto e as permissões correspondentes:

|Número|Permissões|
|---|---|
|7|Leitura, edição e execução|
|6|Leitura e Escrita|
|5|Ler e Executar|
|4|Leitura|
|3|Edição e execução|
|2|Escrever|
|1|Executar|
|0|None|

Linha em branco, sem informações adicionais

Ao digitar o comando **chmod 764 examplefile**, o "examplefile" será atribuído às seguintes permissões:

|Dígito|Equivalente Binário|Permissão|
|---|---|---|
|7 (user)|111|1-Read<br><br>1-Escrever<br><br>1-Execute|
|6 (group)|110|1-Read<br><br>1-Escrever<br><br>0-Não Executar|
|4 (others)|100|1-Read<br><br>0-Não Escrever<br><br>0-Não Executar|

Linha em branco, sem informações adicionais

a.   Modifique o campo “others” na pasta do Joe de modo que outros possam ler e executar, mas não possam editar e, ao mesmo tempo, mantenha o campo “user” para leitura, edição e execução.

joe@labvm:/home$ **chmod 705 joe**

b.  Liste as permissões de arquivo do diretório atual, para ver se as mudanças absolutas foram efetuadas.

joe@labvm:/home$ **ls -l**

total 28

drwxr-xr-x  2 Alice Alice 4096 Mar 18 21:58 Alice

drwxr-xr-x  2 Bob   Bob   4096 Mar 18 21:58 Bob

drwxr-xr-x 12 cisco cisco 4096 Mar 19 20:02 cisco

drwxr-xr-x  2 Eric  Eric  4096 Mar 18 21:58 Eric

drwxr-xr-x  2 Eve   Eve   4096 Mar 18 21:58 Eve

drwxr-xr-x  9 jenny jenny 4096 Mar 20 14:02 jenny

drwx---r-x  9 joe   joe   4096 Mar 20 15:01 joe

joe@labvm:/home$

#### Etapa 4: criar um arquivo no diretório joe.

Alterne para o diretório joe, use o comando **touch test.txt** para criar um arquivo e, em seguida, liste o conteúdo do diretório.

joe@labvm:/home$ **cd joe**

joe@labvm:~$ **touch test.txt**

joe @ labvm: ~ $ **ls -l**

total 12

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Desktop

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Documents

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Downloads

-rw-rw-r-- 1 joe joe    0 Mar 20 15:33 test.txt

joe@labvm:~$

#### Etapa 5: Alternar usuário de joe para jenny.

a.   Para alternar para a área de trabalho de Jenny, clique em **Menu** na parte superior esquerda da área de trabalho. Na parte inferior do menu, clique no botão com a ponta da ferramenta **Finalizar a sessão atual**.

b.   Clique em **Switch User (Alternar usuário)** na caixa de diálogo.

c.   Clique em **Jenny** na lista de usuários disponíveis e digite a senha **jenPass**.

d.   A área de trabalho de Jenny é carregada. Aqui, você pode clicar com o botão direito do mouse na área de trabalho e escolher **Abrir no Terminal**.

jenny@labvm:~/Desktop$

#### Etapa 6: Mude para o diretório inicial e liste seu conteúdo.

jenny@labvm:~/Desktop$ **cd ../..**

jenny@labvm:/home$ **ls -l**

total 28

drwxr-xr-x  2 Alice Alice 4096 Mar 18 21:58 Alice

drwxr-xr-x  2 Bob   Bob   4096 Mar 18 21:58 Bob

drwxr-xr-x 12 cisco cisco 4096 Mar 19 20:02 cisco

drwxr-xr-x  2 Eric  Eric  4096 Mar 18 21:58 Eric

drwxr-xr-x  2 Eve   Eve   4096 Mar 18 21:58 Eve

drwxr-xr-x  9 jenny jenny 4096 Mar 20 14:02 jenny

drwx---r-x  9 joe   joe   4096 Mar 20 15:01 joe

jenny@labvm:/home$

#### Etapa 7: Mude para o diretório /home/joe e indique o conteúdo do diretório.

Observe que o usuário jenny, como um membro de "outros", tem acesso de leitura ao diretório joe e também tem acesso de leitura para o arquivo "test.txt".

jenny@labvm:/home$ **cd joe**

jenny@labvm:/home/joe$ **ls -l**

total 12

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Desktop

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Documents

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Downloads

-rw-rw-r-- 1 joe joe    0 Mar 22 14:33 test.txt

jenny@labvm:/home/joe$

#### Etapa 8: Tente criar um arquivo no diretório joe.

Observe como o usuário Jenny não tem permissão para gravar no diretório joe.

jenny@ubuntu:/home/joe$ **touch jenny.txt**

touch: cannot touch '/mnt/myNewFile.txt': Permission denied (permissão negada)

jenny@labvm:/home/joe$

#### Etapa 9: Alternar usuário de Jenny para Cisco e fechar a VM (máquina virtual).

a.  Clique em **Menu** na parte superior esquerda da área de trabalho. Na parte inferior do menu suspenso, clique no botão com a ponta da ferramenta **Finalizar a sessão atual**.

b.   Clique em **Switch User (Alternar usuário)** na caixa de diálogo.

c.  Clique em **Cybersecurity Analyst (analista de cibersegurança)**na lista de usuários disponíveis e digite a senha como a **password**.

d.  Clique em **Arquivo**> **Fechar**, escolha **Salvar o estado da máquina** e clique em **OK**.


# Laboratório - Criptografando e descriptografando dados usando OpenSSL

## Objetivos

Parte 1: Criptografando mensagens com OpenSSL

Parte 2: Descriptografando mensagens com OpenSSL

## Histórico/Cenário

O OpenSSL é um projeto de código aberto que fornece um kit de ferramentas robusto, de nível comercial e completo para os protocolos TLS (Transport Layer Security) e Secure Sockets Layer (SSL). É também uma biblioteca de criptografia de uso geral. Neste laboratório, você usará o OpenSSL para criptografar e descriptografar mensagens de texto.

**Observação**: Embora o OpenSSL seja a biblioteca de criptografia de fato hoje, o uso apresentado neste laboratório NÃO é recomendado para proteção robusta. Abaixo estão dois problemas de segurança com este laboratório:

1) O método descrito neste laboratório usa uma função de derivação de chave fraca. A ÚNICA segurança é introduzida por uma senha muito forte.

2) O método descrito neste laboratório não garante a integridade do arquivo de texto.

Este laboratório deve ser usado apenas para fins de instrução. Os métodos aqui apresentados NÃO devem ser usados para proteger dados verdadeiramente sensíveis.

## Recursos necessários

Máquina virtual Security Workstation.
## Instruções

### Parte 1: Criptografando mensagens com OpenSSL

OpenSSL pode ser usado como uma ferramenta autônoma para criptografia. Embora muitos algoritmos de criptografia possam ser usados, esse laboratório se concentra no AES. Para usar o AES para criptografar um arquivo de texto diretamente da linha de comando usando o OpenSSL, siga as etapas abaixo:

#### Etapa 1: Criptografando um arquivo de texto

a. Log into CyberOPS Workstation VM.

b. Abra uma janela de terminal.

c. Como o arquivo de texto a ser criptografado está no diretório /home/analyst/lab.support.files/, mude para esse diretório:

[analyst@secOps ~]$ **cd ./lab.support.files/**

[analyst@secOps lab.support.files]$

d. Digite o comando abaixo para listar o conteúdo do arquivo de texto **letter_to_grandma.txt** na tela:

[analyst@secOps lab.support.files]$ **cat letter_to_grandma.txt**

Hi Grandma,

I am writing this letter to thank you for the chocolate chip cookies you sent me. I got them this morning and I have already eaten half of the box! They are absolutely delicious!

I wish you all the best. Love,

Your cookie-eater grandchild.

[analyst@secOps lab.support.files]$

e. Na mesma janela de terminal, execute o comando abaixo para criptografar o arquivo de texto. O comando usará AES-256 para criptografar o arquivo de texto e salvar a versão criptografada como **message.enc**. O OpenSSL pedirá uma senha e confirmação de senha. Forneça a senha conforme solicitado e lembre-se da senha.

[analyst@secOps lab.support.files]$ **openssl aes-256-cbc -in letter_to_grandma.txt -out message.enc**

enter aes-256-cbc encryption password:

Verifying - enter aes-256-cbc encryption password:

[analyst@secOps lab.support.files]$

##### Pergunta:

Documente a senha.



Mostrar resposta

f. Quando o processo for concluído, use o comando **cat** novamente para exibir o conteúdo do arquivo **message.enc** .

[analyst@secOps lab.support.files]$ **cat message.enc**

##### Pergunta:

O conteúdo do arquivo **message.enc** foi exibido corretamente? O que é que se parece? Explique.



Mostrar resposta

g. Para tornar o arquivo legível, execute o comando OpenSSL novamente, mas desta vez adicione a **opção -a** . A opção **-a** diz ao OpenSSL para codificar a mensagem criptografada usando um método de codificação diferente do Base64 antes de armazenar os resultados em um arquivo.

**Nota**: Base64 é um grupo de esquemas de codificação binária a texto semelhantes usados para representar dados binários em um formato de string ASCII.

[analyst@secOps lab.support.files]$ **openssl aes-256-cbc -a -in letter_to_grandma.txt -out message.enc**

enter aes-256-cbc encryption password:

Verifying - enter aes-256-cbc encryption password:

h. Mais uma vez, use o comando **cat** para exibir o conteúdo do arquivo message.enc , agora regerado:

**Nota**: O conteúdo de **message.enc** irá variar.

[analyst@secOps lab.support.files]$ **cat message.enc**

U2FsdGVkX19ApWyrn8RD5zNp0RPCuMGZ98wDc26u/vmj1zyDXobGQhm/dDRZasG7

rfnth5Q8NHValEw8vipKGM66dNFyyr9/hJUzCoqhFpRHgNn+Xs5+TOtz/QCPN1bi

08LGTSzOpfkg76XDCk8uPy1hl/+Ng92sM5rgMzLXfEXtaYe5UgwOD42U/U6q73pj

a1ksQrTWsv5mtN7y6mh02Wobo3A1ooHrM7niOwK1a3YKrSp+ZhYzVTrtksWDl6Ci

XMufkv+FOGn+SoEEuh7l4fk0LIPEfGsExVFB4TGdTiZQApRw74rTAZaE/dopaJn0

sJmR3+3C+dmgzZIKEHWsJ2pgLvj2Sme79J/XxwQVNpw=

[analyst@secOps lab.support.files]$

##### Perguntas:

**Message.enc** é exibido corretamente agora? Explique.



Mostrar resposta

Você pode pensar em um benefício de ter **message.enc** codificado Base64?



Mostrar resposta

### Parte 2: Descriptografando mensagens com OpenSSL

Com um comando OpenSSL semelhante, é possível descriptografar **message.enc**.

a. Use o comando abaixo para descriptografar message.enc:

[analyst@secOps lab.support.files]$ **openssl aes-256-cbc –a -d -in message.enc -out decrypted_letter.txt**

b. O OpenSSL pedirá a senha usada para criptografar o arquivo. Enter the same password again.

c. Quando o OpenSSL terminar de descriptografar o arquivo **message.enc** , ele salva a mensagem descriptografada em um arquivo de texto chamado d**ecrypted_letter.txt**. Use o **cat** exibir o conteúdo de **decrypted_letter.txt**:

[analyst@secOps lab.support.files]$ **cat decrypted_letter.txt**

##### Perguntas:

A carta foi descriptografada corretamente?

O comando usado para descriptografar também contém uma opção. Você pode explicar?

# Laboratório - Criptografar e descriptografar dados usando uma ferramenta de hacker

## Objetivos

Parte 1: Criar e criptografar arquivos

Parte 2: Recuperar senhas de arquivo zip criptografado

## Histórico/Cenário

E se você trabalhar para uma grande empresa que tinha uma política corporativa sobre mídia removível? Especificamente, ele afirma que apenas documentos compactados criptografados podem ser copiados para unidades flash USB portáteis.

Nesse cenário, o Diretor Financeiro (CFO) está fora da cidade em negócios e entrou em contato com você em pânico com um pedido de ajuda de emergência. Enquanto estava fora da cidade em negócios, ele tentou descompactar documentos importantes de um arquivo zip criptografado em uma unidade USB. No entanto, a senha fornecida para abrir o arquivo zip é inválida. O diretor financeiro contatou você para ver se havia algo que pudesse fazer.

**Nota**: O cenário fornecido é simples e serve apenas como exemplo.

Pode haver algumas ferramentas disponíveis para recuperar senhas perdidas. Isto é especialmente verdadeiro em situações como esta em que o analista de segurança cibernética poderia adquirir informações pertinentes do CFO. A informação pertinente pode ser o tamanho da senha e uma idéia do que poderia ser. Conhecer informações pertinentes ajuda drasticamente ao tentar recuperar senhas.

Exemplos de utilitários e programas de recuperação de senha incluem hashcat, John the Ripper, Lopttcrack e outros. Em nosso cenário, usaremos **fcrackzip** que é um utilitário simples Linux para recuperar as senhas de arquivos zip criptografados.

Considere que essas mesmas ferramentas podem ser usadas por cibercriminosos para descobrir senhas desconhecidas. Embora eles não tenham acesso a algumas informações pertinentes, com o tempo, é possível descobrir senhas para abrir arquivos zip criptografados. O tempo necessário depende da força da senha e do comprimento da senha. Senhas mais longas e mais complexas (mistura de diferentes tipos de caracteres) são mais seguras.

Neste laboratório, você irá:

·   Criar e criptografar arquivos de texto de exemplo.

·   Descriptografar o arquivo zip criptografado.

**Nota**: Este laboratório deve ser usado apenas para fins instrutivos. Os métodos aqui apresentados NÃO devem ser usados para proteger dados verdadeiramente sensíveis.

## Recursos necessários

Máquina virtual Security Workstation.

## Instruções

### Parte 1: Criar e criptografar arquivos

Nesta parte, você criará alguns arquivos de texto que serão usados para criar arquivos zip criptografados na próxima etapa.

#### Etapa 1: Crie um arquivo de texto

a. Inicie a VM da estação de trabalho de segurança.

b. Abra uma janela de terminal. Verifique se você está no diretório home do analyst. Caso contrário, digite **cd ~** no prompt do terminal.

c. Crie uma nova pasta chamada Zip Files usando o comando **mkdir Zip-Files** .

d. Mover para esse diretório usando o comando **cd Zip-Files**.

e. Digite o seguinte para criar três arquivos de texto.

[analyst@secOps Zip-Files]$ **echo This is a sample text file > sample-1.txt**

[analyst@secOps Zip-Files]$ **echo This is a sample text file > sample-2.txt**

[analyst@secOps Zip-Files]$ **echo This is a sample text file > sample-3.txt**

f. Verifique se os arquivos foram criados usando o comando **ls** .

[analyst@secOps Zip-Files]$ **ls -l**

total 12

-rw-r—r— 1 analyst de 27 de maio de 13 10:58 sample-1.txt

-rw-r—r— 1 analyst de 27 de maio de 13 10:58 sample-2.txt

-rw-r—r— 1 analyst de 27 de maio de 13 10:58 sample-3.txt

#### Etapa 2: Zipar e criptografar os arquivos de texto.

Em seguida, criaremos vários arquivos compactados criptografados usando comprimentos de senha variados. Para fazer isso, todos os três arquivos de texto serão criptografados usando o utilitário zip.

a. Crie um arquivo zip criptografado chamado **file-1.zip** contendo os três arquivos de texto usando o seguinte comando:

[analyst@secOps Zip-Files]$ **zip –e file-1.zip sample***

b. Quando for solicitada uma senha, insira uma senha de um caractere de sua escolha. No exemplo, a letra **B** foi inserida. Digite a mesma letra quando solicitado a verificar.

[analyst@secOps Zip-Files]$ **zip -e file-1.zip sample-***

Enter password:

Verify password:

  adding: sample-1.txt (stored 0%)

  adding: sample-2.txt (stored 0%)

  adding: sample-3.txt (stored 0%)

c. Repita o procedimento para criar os seguintes 4 outros arquivos

o **file-2.zip** usando uma senha de 2 caracteres de sua escolha. No nosso exemplo, usamos **R2**.

o **file-3.zip** usando uma senha de 3 caracteres de sua escolha. No nosso exemplo, usamos **0B1**.

o **file-4.zip** usando uma senha de 2 caracteres de sua escolha. No nosso exemplo, usamos **Y0Da**.

o **file-5.zip** usando uma senha de 5 caracteres de sua escolha. No nosso exemplo, usamos **C-3P0**.

d. Verifique se os arquivos foram criados usando o comando **ls** .

[analyst@secOps Zip-Files]$ **ls -l f***

-rw-r—r— 1 analyst 643 Maio 13 11:01 file-1.zip

-rw-r—r— 1 analyst analyst 643 13 de maio 11:02 file-2.zip

-rw-r—r— 1analyst analyst 643 13 de maio 11:03 file-3.zip

-rw-r—r— 1 analyst analyst 643 13 de maio 11:03 file-4.zip

-rw-r—r— 1 analyst analyst 643 13 de maio 11:03 file-5.zip

e.Tente abrir um zip usando uma senha incorreta, conforme mostrado.

[analyst@secOps Zip-Files]$ **unzip file-1.zip**

Archive:  file-1.zip

[file-1.zip] sample-1.txt password:

password incorrect--reenter:

password incorrect--reenter:

   skipping: sample-1.txt    incorrect password

[file-1.zip] sample-2.txt password:

password incorrect--reenter:

password incorrect--reenter:

   skipping: sample-2.txt    incorrect password

[file-1.zip] sample-3.txt password:

password incorrect--reenter:

password incorrect--reenter:

   skipping: sample-3.txt    incorrect password

### Parte 2: Recuperar senhas de arquivo zip criptografado

Nesta parte, você usará o utilitário **fcrackzip** para recuperar senhas perdidas de arquivos compactados criptografados. O Fcrackzip procura cada arquivo zip fornecido para arquivos criptografados e tenta adivinhar a senha usando métodos de força bruta.

A razão pela qual criamos arquivos zip com diferentes comprimentos de senha foi para ver se o comprimento da senha influencia o tempo necessário para descobrir uma senha.

#### Etapa 1: Introdução ao fcrackzip

Na janela do terminal, digite o comando **fcrackzip -h** para ver as opções de comando associadas.

Em nossos exemplos, usaremos as opções de comando **-v**, **-u**, e **-l** . A opção -l será listada por último porque especifica o comprimento da senha possível. Sinta-se livre para experimentar outras opções.

#### Etapa 2: Recuperando senhas usando fcrackzip

  

a. Agora tente recuperar a senha do arquivo **file-1.zip** . Lembre-se de que uma senha de um caractere foi usada para criptografar o arquivo.Portanto, use o seguinte comando **fcrackzip** :

[analyst@secOps Zip-Files]$ **fcrackzip -vul 1-4 file-1.zip**

found file 'sample-1.txt', (size cp/uc 39/    27, flags 9, chk 5754)

found file 'sample-2.txt', (size cp/uc 39/    27, flags 9, chk 5756)

found file 'sample-3.txt', (size cp/uc 39/    27, flags 9, chk 5757)

PASSWORD FOUND!!!!: pw == B

**Observação**: o comprimento da senha pode ter sido definido para menos de 1 a 4 caracteres.

##### Pergunta:

Quanto tempo leva para descobrir a senha?


Leva menos de um segundo.


b. Agora tente recuperar a senha do arquivo **file-2.zip** . Lembre-se de que uma senha de dois caracteres foi usada para criptografar o arquivo.Portanto, use o seguinte comando **fcrackzip** :

[analyst@secOps Zip-Files]$ **fcrackzip –vul 1-4 file-2.zip**

found file 'sample-1.txt', (size cp/uc 39/    27, flags 9, chk 5754)

found file 'sample-2.txt', (size cp/uc 39/    27, flags 9, chk 5756)

found file 'sample-3.txt', (size cp/uc 39/    27, flags 9, chk 5757)

PASSWORD FOUND!!!!: pw == R2

##### Pergunta:

Quanto tempo leva para descobrir a senha?


Deve demorar cerca de um segundo.


c. Repita o procedimento e recupere a senha do arquivo **file-3.zip** . Lembre-se de que uma senha de três caracteres foi usada para criptografar o arquivo. Tempo para ver quanto tempo leva para descobrir uma senha de 3 letras. Use o seguinte comando **fcrackzip** :

[analyst@secOps Zip-Files]$ **fcrackzip –vul 1-4 file-3.zip**

found file 'sample-1.txt', (size cp/uc 39/    27, flags 9, chk 5754)

found file 'sample-2.txt', (size cp/uc 39/    27, flags 9, chk 5756)

found file 'sample-3.txt', (size cp/uc 39/    27, flags 9, chk 5757)

PASSWORD FOUND!!!!: pw == 0B1

##### Pergunta:

Quanto tempo leva para descobrir a senha?


As respostas variam dependendo da plataforma e senha real usada, mas deve cerca de um segundo ou dois.


d. Quanto tempo demora para decifrar uma senha de quatro caracteres? Repita o procedimento e recupere a senha do arquivo **file-4.zip** . Tempo para ver quanto tempo leva para descobrir a senha usando o seguinte comando **fcrackzip** :

[analyst@secOps Zip-Files]$ **fcrackzip –vul 1-4 file-4.zip**

found file 'sample-1.txt', (size cp/uc 39/    27, flags 9, chk 5754)

found file 'sample-2.txt', (size cp/uc 39/    27, flags 9, chk 5756)

found file 'sample-3.txt', (size cp/uc 39/    27, flags 9, chk 5757)

checking pw X9M~    

PASSWORD FOUND!!!!: pw == Y0Da

##### Pergunta:

Quanto tempo leva para descobrir a senha?


As respostas variam de acordo com a plataforma e a senha real usada, mas deve demorar alguns segundos.


e. Quanto tempo demora para decifrar uma senha de cinco caracteres? Repita o procedimento e recupere a senha do arquivo **file-5.zip** . O comprimento da senha é de cinco caracteres, então precisamos definir a opção de comando **-l para** **1- 5**. Novamente, tempo para ver quanto tempo leva para descobrir a senha usando o seguinte comando **fcrackzip** :

[analyst@secOps Zip-Files]$ **fcrackzip –vul 1-5 file-5.zip**

found file 'sample-1.txt', (size cp/uc 39/    27, flags 9, chk 5754)

found file 'sample-2.txt', (size cp/uc 39/    27, flags 9, chk 5756)

found file 'sample-3.txt', (size cp/uc 39/    27, flags 9, chk 5757)

checking pw C-H*~    

PASSWORD FOUND!!!!: pw == C-3P0

##### Pergunta:

Quanto tempo leva para descobrir a senha?


As respostas variam de acordo com a plataforma e a senha real usada, mas deve levar cerca de dois minutos.

f. Recuperar uma senha de 6 caracteres usando fcrackzip.

Parece que senhas mais longas levam mais tempo para serem descobertas e, portanto, elas são mais seguras. No entanto, uma senha de 6 caracteres não dissuadiria um criminoso cibernético.

##### Pergunta:

Quanto tempo você acha que o fcrackzip levaria para descobrir uma senha de 6 caracteres?


As respostas variam.


Para responder a essa pergunta, crie um arquivo chamado **file-6.zip** usando uma senha de 6 caracteres de sua escolha. No nosso exemplo, usamos **JarJar**.

[analyst@secOps Zip-Files]$ **zip –e file-6.zip sample***

g. Repita o procedimento para recuperar a senha do arquivo **file-6.zip** usando o seguinte comando **fcrackzip** :

[analyst@secOps Zip-Files]$ **fcrackzip –vul 1-6 file-6.zip**

##### Pergunta:

Quanto tempo demora o fcrackzip para descobrir a senha?


As respostas variam dependendo da plataforma e da senha real usada, mas levará muito mais tempo (horas).


A verdade simples é que senhas mais longas são mais seguras porque demoram mais tempo para serem descobertas.

##### Pergunta:

Por quanto tempo você recomendaria uma senha para que ela seja segura?

As respostas variam.

# Laboratório - Determinar o algoritmo de criptografia a ser usado

## Objetivos

Parte 1: Proteção de dados pessoais

Parte 2: Proteger dados sem fio

Parte 3: Proteção de dados corporativos entre locais

## Histórico/Cenário

A Internet é usada por vários motivos, incluindo trabalho, diversão, entretenimento e muito mais. Existem vários protocolos, algoritmos e métodos disponíveis para proteger o acesso on-line.

Este laboratório inclui três cenários. Em cada cenário, você concluirá algumas etapas e fará uma pesquisa na Internet para responder a perguntas, inclusive qual é o melhor algoritmo de criptografia para cada cenário.

## Recursos necessários

Um PC Windows com acesso à Internet

## Instruções

### Parte 1: Proteção de dados pessoais

Nesse cenário, você é um aluno usando um computador compartilhado. Você gostaria de salvar algumas informações confidenciais neste computador, mas não deseja que outras pessoas acessem esses dados.

#### Etapa 1: Crie um arquivo de texto

a. Abra **o File Explorer** procurando-o ou usando a combinação de teclas **Windows + E** do teclado.

b. Navegue até um local de trabalho e crie uma nova pasta com o nome de sua escolha.

**Observação**: para exibir extensões de arquivo, clique em **Exibir**> **Opções**. Na janela **Opções de pasta**, clique na guia **Exibir** e desmarque **Ocultar extensões para tipos de arquivos conhecidos**.

c. Dentro da pasta, clique com o botão direito do mouse no espaço vazio e clique em **Novo**> **Documento de texto**.

d. Altere o nome para **File-1.txt** e clique duas vezes nele para abrir o arquivo.

e. Insira algum texto, como "Este é um teste." E salve e feche o arquivo.

#### Etapa 2: Discutir como você pode proteger esse arquivo.

Suponha que você deva proteger esse arquivo de forma a ser lido, roubado ou alterado.

##### Perguntas:

Como você pode fazer isso?

Você pode usar um programa para proteger o arquivo por senha. Programas de compactação, como o 7-Zip, oferecem a opção de compactar e criptografar arquivos.

Qual algoritmo de criptografia (ou seja, DES, 3DES ou AES) você deve usar se conseguir criptografar o arquivo? Por quê?

O AES oferece a criptografia mais forte em comparação ao DES e 3DES. Ele deve ser usado para garantir que o arquivo esteja protegido com segurança.

#### Etapa 3: Baixar e instalar o 7-Zip.

a. Pesquise na Internet "download do 7-Zip" e baixe este programa de compactação de código aberto gratuito.

b. Instale o 7-Zip.

#### Etapa 4: Inspecionar os formatos de arquivo e os métodos de criptografia 7-Zip.

a. Na janela do **File Explorer**, **clique com** o botão direito em **File-1.txt** e selecione **7-Zip** > **Add to archive…**

b. No menu suspenso ao lado de Formato de arquivo morto :, escolha o formato zip.

c. O 7 - Zip oferece dois métodos de criptografia para o formato **zip**. O **ZipCrypto** é um método.

##### Perguntas:

Qual é o outro método?

O outro método de criptografia é o AES-256

Quais são as diferenças entre cada método?

O 7-Zip pode compactar um arquivo usando o formato 7z ou ZIP. O formato 7z é compatível apenas com AES-256, enquanto o formato ZIP é compatível com ZipCrypto ou AES-256. Use o ZipCrypto se quiser obter um arquivo compatível com a maioria dos arquivadores ZIP.

Qual método você deve usar se quiser ter a criptografia mais robusta?

O AES-256 oferece criptografia mais eficiente, mas não é tão amplamente suportado.

#### Etapa 5: Compactar e criptografar o arquivo 1.

a. Com a janela **Adicionar ao arquivo** ainda aberta, digite a senha de sua preferência no campo **Inserir senha** .

b. Clique em **OK** para compactar e criptografar o arquivo. Isso cria um novo arquivo arquivado chamado **File-1.zip**.

c. Para excluir permanentemente o arquivo original, clique nele e pressione **Shift-Excluir**. Você será solicitado a excluir o arquivo permanentemente. Clique em **Sim**.

#### Etapa 6: Descriptografar o File-1.zip criptografado e compactado.

a. Com o **File Explorer** ainda aberto, clique com o botão direito do mouse em **File-1.zip** e escolha **7-Zip** > **Extrair aqui**.

b. A janela **Inserir senha** é exibida. Digite sua senha para descriptografar **File-1.txt** e, em seguida, clique em OK.

c. Abra o **File1.txt** para verificar se a mensagem original está lá.

### Parte 2: Proteger dados sem fio

Nesse cenário, você tem uma pequena empresa que fornece suporte de TI a cidadãos locais. Um novo cliente solicitou que você os configurasse com o melhor acesso sem fio. Especificamente, eles:

·  Uma grande casa de três andares com 5.000 pés quadrados.

·  Vários dispositivos pessoais mais novos e antigos, incluindo smartphones, tablets, computadores, televisores inteligentes, Oculus 2, impressoras e muito mais.

·  Quatro dispositivos Wi-Fi 6 mais recentes (802.11ax).

Após algumas pesquisas, você decide recomendar o Linksys Atlas Pro 6, sistema Dual-Band Mesh Wi-Fi 6 System de 3 pacotes. Esse sistema deve ser compatível com os dispositivos listados e oferecer a segurança sem fio necessária.

Os roteadores Wi-Fi normalmente oferecem várias opções de segurança para criptografar dados sem fio. Qual opção de criptografia você deve usar neste cenário?

#### Etapa 1: Pesquisar o roteador Linksys Wireless

a. Pesquise na Internet pelo "Linksys Atlas Pro 6, sistema Wi-Fi 6 de malha de banda dupla". Sua pesquisa fornecerá muitos links possíveis. No entanto, escolha o link fornecido por **linksys.com**.

b. Analise os recursos do roteador para ver se ele atende às especificações necessárias.

#### Etapa 2: Pesquisar as opções de segurança

O sistema Linksys Atlas oferece três recursos de segurança.

##### Perguntas:

Quais são os recursos de segurança disponíveis com este sistema?

Os recursos de segurança disponíveis são:  
  
 •   WPA2 / WPA3 pessoal misto  
 •   WPA2 pessoal  
 •   WPA3 pessoal

Qual opção de segurança esses clientes devem usar?

WPA2 / WPA3 misto pessoal: recomendado apenas para uso doméstico se todos os nós estiverem atualizados com o firmware compatível com o modo misto WPA2 / WPA3.Ele usa WPA3 com criptografia AES quando possível, WPA2 com criptografia AES para dispositivos mais antigos.Alguns dispositivos podem não conseguir se conectar.  
  
WPA3 Pessoal: os dispositivos mais antigos não poderão se conectar.  
  
WPA2 Pessoal: recomendado para uso doméstico.Os usuários se conectam usando uma senha e criptografia AES.

### Parte 3: Proteção de dados corporativos entre locais

Nesse cenário, você está trabalhando para uma pequena empresa de vários locais interconectada na Internet pública. É fundamental que os dados corporativos entre os locais sejam protegidos enquanto trafegam pela Internet.

As redes virtuais privadas (VPNs) são comumente usadas entre filiais e locais centrais para proteger dados e garantir a autenticação de origem. A empresa está usando roteadores Cisco Integrated Series (ISRs) para oferecer suporte a VPNs IPsec de site para site entre sites. O Internet Protocol Security ou IPsec é uma estrutura que permite especificar qual mecanismo de criptografia, autenticação e integridade usar.

Nesta parte, você está encarregado de recomendar os melhores algoritmos de criptografia e autenticação para implementar no Cisco ISR 4321 usando o IOS XE 17. Para fazer isso, você pesquisará vários protocolos compatíveis com VPNs IPsec.

#### Etapa 1: Pesquisar algoritmos de criptografia IPsec

a. Faça uma pesquisa na Internet em “Security for VPNs with IPsec Configuration Guide, Cisco IOS XE 17”.

b. Escolha o primeiro link em **cisco.com** para abrir o **Índice**.

c. Clique no **link Configuração de segurança para VPNs com IPsec** .

d. Role para baixo até os **Padrões compatíveis** para responder às seguintes perguntas.

##### Pergunta:

Quais algoritmos de criptografia criptográfica são compatíveis com as VPNs IPsec?


Os algoritmos de criptografia compatíveis com as VPNs IPsec incluem:  
  
 •   Padrão de criptografia avançado (AES)  
 •   Algoritmo DES  
 •   Algoritmo DES triplo (3DES)


#### Etapa 2: Pesquisar a algoritmo

##### de integridade e autenticação de IPsec Pergunta:

Na seção **Padrões compatíveis**, quais algoritmos de hash são usados para autenticar dados e verificar a integridade?



Os algoritmos de criptografia compatíveis com as VPNs IPsec incluem:  
  
 •   Algoritmo seguro de hash (SHA-2) e SHA-1  
 •  Algoritmo de resumo de mensagens 5 (MD5)


#### Etapa 3: Recomendar uma pergunta sobre o algoritmo

##### De criptografia e autenticação:

Para satisfazer as necessidades da empresa, qual algoritmo de criptografia e algoritmo de hash você deve recomendar para garantir a proteção adequada para os dados que atravessam a Internet?



As VPNs IPsec de site para site normalmente exigiriam:  
  
 •   Criptografia: AES ou suas variantes (ou seja, AES-128, AES-192 ou AES-256)  
 •   Autenticação e integridade: SHA-2 ou suas variantes (ou seja, SHA-256 , SHA-384 ou SHA-512)

# Laboratório - Examinando Telnet e SSH com o Wireshark

## Objetivos

Parte 1: Examinar uma Sessão Telnet com o Wireshark

Parte 2: Examinar uma Sessão SSH com o Wireshark

## Histórico/Cenário

Neste laboratório, você configurará um roteador para aceitar a conectividade SSH e usará o Wireshark para capturar e visualizar sessões Telnet e SSH. Isso demonstrará a importância da criptografia com o SSH.

## Recursos necessários

Máquina virtual de estação de trabalho de segurança

## Instruções

### Parte 1: Examinando uma sessão Telnet com Wireshark

Você usará o Wireshark para capturar e visualizar os dados transmitidos de uma sessão Telnet.

#### Etapa 1: Capturar dados.

a. Inicie a VM Security Workstation e faça login com o nome de usuário **analyst** e a senha **cyberops**.

b. Abra uma janela de terminal e inicie o Wireshark.

[analyst@secOps ~]$ **wireshark &**

c. Inicie uma captura do Wireshark na interface **Loopback: lo**.

d. Abra outra janela do terminal. Inicie uma sessão Telnet para o localhost. Digite o nome de usuário **analyst** e a senha **cyberops** quando solicitado. Observe que pode levar vários minutos para que o prompt “conectado ao localhost” e login apareça.

[analyst@secOps ~]$ **telnet localhost**

Trying ::1...

Connected to localhost.

Escape character is '^]'.

Linux 4.10.10-1-ARCH (unallocated.barefruit.co.uk) (pts/12)

secOps login: **analyst**

Password:

Last login: Fri Apr 28 10:50:52 from localhost.localdomain

[analyst@secOps ~]$

e. Pare a captura Wireshark depois de ter fornecido as credenciais do usuário.

#### Etapa 2: Examine a sessão Telnet.

a. Aplique um filtro que exiba apenas o tráfego relacionado ao Telnet. Digite **telnet** no campo de filtro e clique em **Apply** (Aplicar).

b. Clique com o botão direito do mouse em uma das linhas **Telnet** na seção **Packet list** do Wireshark e, na lista suspensa, selecione **Follow** > **TCP Stream**.

c. A janela Follow TCP Stream exibe os dados de sua sessão Telnet com a VM da estação de trabalho de segurança. A sessão inteira é exibida em texto simples, incluindo sua senha. Observe que o nome de usuário que você inseriu é exibido com caracteres duplicados. Isso é causado pela configuração de eco no Telnet para permitir que você visualize os caracteres digitados na tela.

d. Depois de revisar sua sessão Telnet na janela **Follow TCP Stream** (Acompanhar Transmissão TCP), clique em **Close** (Fechar).

e. Digite **exit** no terminal para sair da sessão **Telnet**.

[analyst@secOps ~]$ **exit**

### Parte 2: Examinar uma Sessão SSH com o Wireshark

Na Parte 2, você estabelecerá uma sessão SSH com o localhost. O Wireshark será usado para capturar e exibir os dados da sessão SSH.

a. Inicie outra captura Wireshark usando a interface **Loopback: lo**.

b. Você estabelecerá uma sessão SSH com o localhost. No prompt do terminal, digite **ssh localhost**. Digite **yes** (sim) para continuar se conectando. Entre com **cyberops** quando solicitado.

[analyst@secOps ~]$ **ssh localhost**

The authenticity of host 'localhost (::1)' can't be established.

ECDSA key fingerprint is SHA256:1xZuV8NMeVsNQPRrzVf9nXHzdUP+EtgVouZVbWH80XA.

Are you sure you want to continue connecting (yes/no/[fingerprint])? **yes**

Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.

analyst@localhost's password:

Last login: Sat May 23 10:18:47 2020Stop the Wireshark capture.

c. Aplique um filtro SSH nos dados de captura do Wireshark. Digite **ssh** no campo de filtro e clique em **Apply** (Aplicar).

d. Clique com o botão direito em uma das linhas **SSHv2** na seção **Packet list** do Wireshark e, na lista suspensa, selecione **Follow > TCP Stream**.

e. Examine a janela **Follow TCP Stream** (Acompanhar Transmissão TCP) da sessão SSH. Os dados foram criptografados e estão ilegíveis. Compare os dados da sessão SSH com os dados da sessão Telnet.

f. Após analisar sua sessão SSH, clique em **Close** (Fechar).

g. Feche o Wireshark.

## Perguntas para reflexão

Por que o SSH tem preferência sobre o Telnet para conexões remotas?

# Laboratório - Gerar e usar uma Assinatura Digital 

## Objetivos

Use OpenSSL para gerar uma assinatura digital.

Assina um documento com a assinatura digital.

Verifique se um documento assinado foi alterado.

## Histórico/Cenário

Uma assinatura digital é uma técnica matemática usada para validar a autenticidade e a integridade de uma mensagem digital. A finalidade de uma assinatura digital é evitar a adulteração das mensagens e a falsificação de identidade na comunicação digital. Em muitos países, incluindo os Estados Unidos, as assinaturas digitais têm o mesmo valor legal que as formas tradicionais de documentos assinados. O governo dos Estados Unidos publica, agora, versões eletrônicas de orçamentos, leis e projetos de leis do congresso com assinaturas digitais.

Um algoritmo de assinatura digital consiste em um processo de criação e verificação de assinatura. O usuário A gera a assinatura digital e o usuário B verifica a assinatura usando o processo de verificação. Tanto o assinante quanto o verificador têm uma chave pública e privada que eles usam para concluir cada processo.

Neste laboratório, você usará o kit de ferramentas OpenSSL para gerar uma assinatura digital. Você, então, vai gerar um documento, assiná-lo com a assinatura digital e validar a autenticidade e a integridade do documento. Por fim, você alterará o documento e validará se o documento não é mais autêntico porque sua integridade foi comprometida.

## Recursos necessários

PC com o **CSE-LABVM** instalado no VirtualBox

## Instruções

### Parte 1: Abra uma janela de terminal no CSE-LABVM.

a.﻿ ﻿Inicie o **CSE-LABVM**.

b. Clique duas vezes no ícone **Terminal** para abrir um terminal.

### Parte 2: Gerar e exibir uma chave privada.

a. Para gerar uma chave privada, use o comando **OpenSL genpkey**. O comando gera uma chave privada usando o algoritmo RSA e a envia para um arquivo chamado **private_key.pem**.

cisco@labvm:~$ **openssl genpkey -algorithm RSA -out private_key.pem**

........................ +++++

... +++++

cisco@labvm:~$

b. Use o comando **cat** para visualizar o arquivo **private_key.pem**.

cisco@labvm:~$ **cat private_key.pem**

----- COMECE A CHAVE PRIVADA -----

MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQC1db50XOYeDTAy

GnQLRwGusr7us0Mi44hfFUmai3QHzelqRBxO06ujv9fFwQ8e5QsaQWbph + RVTQBu

output omitted

R7TLUOrewnIlkMuVLk8II2EQAXTMmvvZOICCiTSvm8gflx / FRJmUEiTf0I0MVUai

X6O9rDJOjnoHBbi67+fgN0sn

-----END PRIVATE KEY-----

cisco@labvm:~$

### Parte 3: Gerar e exibir uma chave pública.

a. Para gerar uma chave pública, use o comando **OpenSL pkey**. O comando leva seu **private_key.pem** como uma entrada e, em seguida, gera uma chave pública **(-pubout -out)** para um arquivo chamado **public_key.pem**.

cisco@labvm:~$ **openssl pkey -in private_key.pem -pubout -out public_key.pem**

cisco@labvm:~$

b. Use o comando **cat** para visualizar **public_key.pem**.

cisco@labvm:~$ **cat public_key.pem**

----- COMECE A CHAVE PÚBLICA -----

MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtXW + dFzmHg0wMhp0C0cB

rrK+7rNDIuOIXxVJmot0B83pakQcTtOro7/XxcEPHuULGkFm6YfkVU0Abq/1ccub

SFZFb1kKobMutMhxvfBQjQr3jo1j6aG12yMvrQudvSlaxHTvuDpMlhPY3IrBjkMz

2Lx0SjjOC9uD3CzaMwu6JWnhRt0svH7n6cZNXDfIlsYpcjLg9JqKrWEO3Ooq05q1

e2JEAuDOXte+M2O0ZC7cjSyxCiOfD2IEXkBq41H7xgIKTq2WJ8f+/RXEdC5Mx6Xx

fu7pQXN9gT9LbUPlLJfUG7vTCs2d2AA6TBUyUuzH2mS61KwWcT8VRAWtWdr/sPSK

AQIDAQAB

-----END PUBLIC KEY-----

cisco@labvm:~$

### Parte 4: Crie um novo documento que será assinado digitalmente.

a. Use o comando **echo** para criar um arquivo de texto chamado **Contract.txt**.

cisco@labvm:~$ **echo Please transfer 2,000,000 US Dollars to Mr. Jester by 6pm today! > Contract.txt**

cisco@labvm:~$

b. Use o comando **cat** para exibir o conteúdo do arquivocontacts.txt**.**

cisco@labvm:~$ **cat contract.txt**

Transfira 2.000.000 dólares para o Mr. Jester hoje às 18h!

### Parte 5: use a chave privada para assinar digitalmente o novo documento.

a. Para assinar o documento, use o comando **OpenSL dgst**. O comando **dgst** pode receber qualquer número de valores de resumo da mensagem. Neste exemplo, você usará SHA 256 e, em seguida, **private_key.pem** para gerar uma **assinatura** para o documento **contrat.txt**.

cisco@labvm:~$ **openssl dgst -sha256 -sign private_key.pem -out signature contract.txt**

cisco@labvm:~$

**b. Use o comando **cat** para exibir o conteúdo do** arquivo**. O arquivo é um arquivo binário. Pressione **Enter**para obter um prompt de comando.**

cisco@labvm:~$ **cat signature**

H�&/J�c�M�$R�xpA��*t��ѣmr�C  jw��q]t'�#ot"%_B�X���~�k��p3����-���̣

output omitted

ROˤ    ��D?Nz�����f��H�~�P5nJ���hqG�&28Jcisco@labvm:~$

### Parte 6: Verificar a autenticidade e a integridade do documento.

A tecnologia de assinatura digital permite que o destinatário verifique a autenticidade e a integridade do arquivo. O processo de verificação de assinatura digital é garantir que uma determinada mensagem tenha sido assinada pela chave privada que corresponde a uma determinada chave pública.

Para verificar se o documento é autêntico e não foi violado, use o comando **OpenSL dgst** com a opção de **verificação** e **public_key.pem**.

cisco@labvm:~$ **openssl dgst -sha256 -verify public_key.pem -signature signature contract.txt**

Verificado

### Parte 7: Simule um agente de ameaça alterando o destinatário especificado no arquivo Contract.txt.

a. Use **gedit** para abrir o arquivo **Contract.txt**.

cisco@labvm:~$ **gedit contract.txt**

b. Mude **o Sr. Jester** para o **Sr. Viper.**

c. Clique em **Arquivo**> **Sair** e, em seguida, clique em **Salvar** na caixa de diálogo.

### Parte 8: Verifique se a integridade do documento foi comprometida.

Reutilize o comando **opensl dgst** com a opção de **verificação** para validar que a verificação do documento agora falha.

cisco@labvm:~$ **openssl dgst -sha256 -verify public_key.pem -signature signature contract.txt**

Falha na verificação

cisco@labvm:~$




# Laboratório - Regras de Snort e Firewall 

## Topologia

![|672x420](https://www.netacad.com/content/nad/1.0/courses/content/m11/pt-BR/assets/11.1.7-1.png)

## Objetivos

Parte 1: Preparando o Ambiente Virtual

Parte 2: Firewall e logs IDS

Parte 3: Encerrar e Limpar o Processo Mininet

## Histórico/Cenário

Em uma rede de produção segura, os alertas de rede são gerados por vários tipos de dispositivos, como dispositivos de segurança, firewalls, dispositivos IPS, roteadores, switches, servidores e muito mais. O problema é que nem todos os alertas são criados igualmente. Por exemplo, alertas gerados por um servidor e alertas gerados por um firewall serão diferentes e variam em conteúdo e formato.

Neste laboratório, para se familiarizar com regras de firewall e assinaturas IDS.

## Recursos necessários

Máquina virtual Security Workstation.

Conexão com a Internet

**Observação**: Neste laboratório, a VM CyberOps Workstation é um contêiner para armazenar o ambiente Mininet mostrado na Topologia. Se um erro de memória for recebido em uma tentativa de executar qualquer comando, saia da etapa, vá para as configurações da VM e aumente a memória. O padrão é 1 GB; tente 2 GB.

## Instruções

### Parte 1: Preparando o Ambiente Virtual

a. Inicie o **Oracle VirtualBox** e altereo **CyberOps Workstation** para o modo Bridged, se necessário. Selecione **Machine > Settings > Network**. Em **Attached To**, selecione **Bridged Adapter** (ou, se estiver usando WiFi com um proxy, talvez seja necessário um **NATadapter**) e clique em **OK**.

b. Inicie a **VM CyberOps Workstation**, abra um terminal e configure sua rede executando o **script configure_as_dhcp.sh** .

Como o script requer privilégios de superusuário, forneça a senha para o usuário **analyst**

[analyst @secOps ~] $ **sudo./lab.support.files/scripts/configure_as_dhcp.sh**

[sudo] password for analyst:

[analyst @secOps ~] $

c. Use o comando **ifconfig** para verificar se a **VM CyberOps Workstation** agora tem um endereço IP em sua rede local. Você também pode testar a conectividade com um servidor público da Web fazendo ping em www.cisco.com. Use **Ctrl+C** para parar os pings.

[analyst @secOps ~] $ **ping www.cisco.com**

PING e2867.dsca.akamaiedge.net (23.204.15.199) 56(84) bytes of data.

64 bytes from a23-204-15-199.deploy.static.akamaitechnologies.com (23.204.15.199): icmp_seq=1 ttl=54 time=28.4 ms

64 bytes from a23-204-15-199.deploy.static.akamaitechnologies.com (23.204.15.199): icmp_seq=2 ttl=54 time=35.5 ms

^C

--- e2867.dsca.akamaiedge.net ping statistics ---

2 packets transmitted, 2 received, 0% packet loss, time 1002ms

rtt min/avg/máx/mdev = 28.446/32.020/35,595/3.578 ms

### Parte 2: Firewall e logs IDS

Firewalls e sistemas de detecção de intrusões (IDS) são frequentemente implantados para automatizar parcialmente a tarefa de monitoramento de tráfego. Ambos os firewalls e IDSs correspondem ao tráfego de entrada em relação às regras administrativas. Os firewalls costumam comparar o cabeçalho do pacote com um conjunto de regras, enquanto os IDSs costumam usar a carga do pacote para comparação do conjunto de regras. Como firewalls e IDSs aplicam as regras predefinidas a diferentes partes do pacote IP, IDS e regras de firewall têm estruturas diferentes.

Embora haja uma diferença na estrutura de regras, algumas semelhanças entre os componentes das regras permanecem. Por exemplo, as regras de firewall e IDS contêm componentes correspondentes e componentes de ação. As ações são tomadas após uma correspondência ser encontrada.

**Componente de correspondência** - especifica os elementos de pacote de interesse, como: origem do pacote; destino do pacote; portas e protocolos da camada de transporte; e dados incluídos na carga útil do pacote.

**Componente de ação** - especifica o que deve ser feito com esse pacote que corresponde a um componente, como: aceitar e encaminhar o pacote; descartar o pacote; ou enviar o pacote para um conjunto de regras secundário para inspeção adicional.

Um design de firewall comum é descartar pacotes por padrão enquanto especifica manualmente qual tráfego deve ser permitido. Conhecido como dropping-by-default, este design tem a vantagem de proteger a rede contra protocolos e ataques desconhecidos. Como parte desse design, é comum registrar os eventos de pacotes descartados, uma vez que estes são pacotes que não foram explicitamente permitidos e, portanto, infringem as políticas da organização. Tais eventos devem ser registados para análise futura.

#### Monitoramento os logs IDS em tempo real

a. Na VM **CyberOps Workstation**,execute o script para iniciar **o mininet**.

[analyst @secOps ~] $ **sudo./lab.support.files/scripts/cyberops_extended_topo_no_fw.py**

[sudo] password for analyst:

*** Adding controller

*** Add switches

*** Add hosts

*** Add links

*** Starting network

*** Configuring hosts

R1 R4 H1 H2 H3 H4 H5 H6 H7 H8 H9 H10 H11

*** Starting controllers

*** Starting switches

*** Add routes

*** Post configure switches and hosts

*** Starting CLI:

mininete>

O prompt do **mininet** deve ser exibido, indicando que o **mininet** está pronto para comandos.

b.No prompt do **mininet**, abra um shell no **R1** usando o comando abaixo:

mininet > **xterm R1**

mininet>

##### Pergunta:

O shell **R1** abre em uma janela de terminal com texto preto e fundo branco. Qual usuário está logado nesse shell? Qual é o indicador disso?

O usuário root. Isso é indicado pelo sinal # após o prompt.

c.No shell do **R1**, inicie o IDS baseado em Linux, Snort.

[root@secOps analyst]#**./lab.support.files/scripts/start_snort.sh**

Running in IDS mode

--== Initializing Snort ==--

Initializing Output Plugins!

Initializing Preprocessors!

Initializing Plug-ins!

Parsing Rules file "/etc/snort/snort.conf"

output omitted

**Observação**: Você não verá um prompt, pois o Snort está sendo executado nesta janela. Se, por algum motivo, o Snort parar de funcionar e o prompt **[root @secOps analist] #** for exibido, execute novamente o script para iniciar o Snort. Snort deve estar executando para capturar alertas mais tarde no laboratório.

d. No prompt do **mininet da** **VMCyberOps Workstation**, abra shells para hosts **H5** e **H10**.

mininet> **xterm H5**

mininet> **xterm H10**

mininet>

e. **O H10** simulará um servidor na Internet que hospeda malware. Em **H10**, execute o **script mal_server_start.sh** para iniciar o servidor.

[root @secOps analyst] #.**/lab.support.files/scripts/mal_server_start.sh**

[root@secOps analyst]#

f. No **H10**, use **netstat** com as **opções -tunpa** para verificar se o servidor web está sendo executado. Quando usado como mostrado abaixo, **netstat** lista todas as portas atualmente atribuídas aos serviços:

[root @secOps analyst] # **netstat -tunpa**

Active Internet connections (servers and established)

Proto Recv-Q Send-Q Local Address   Foreign Address  State   PID/Program name   

tcp    0  0 0.0.0.0:6666    0.0.0.0:*   LISTEN  1839/nginx: master 

[root@secOps analyst]#

Como visto pela saída acima, o servidor web leve **nginx** está sendo executado e ouvindo conexões na porta TCP 6666.

g. Na janela do terminal **R1** , uma instância do Snort está em execução. Para inserir mais comandos no **R1**, abra outro terminal **R1** inserindo o **xterm R1** novamente na janela do terminal da **VM CyberOps Workstation**. Você também pode querer organizar as janelas do terminal para que você possa ver e interagir com cada dispositivo.

h. Na nova guia do terminal **R1**, execute o comando **tail** com a opção **-f** para monitorar o arquivo **/var/log/snort/alert** em tempo real. Este arquivo é onde o snort está configurado para registrar alertas.

[root @sec0ps analyst] # **tail -f /var/log/snort/alert**

Como nenhum alerta ainda foi registrado, o log deve estar vazio. No entanto, se você tiver executado este laboratório antes, as entradas de alerta antigas podem ser mostradas. Em ambos os casos, você não receberá um prompt depois de digitar este comando. Esta janela exibirá alertas à medida que eles acontecem.

i. Em **H5**, use o comando **wget** para baixar um arquivo chamado **W32.Nimda.amm.exe**. Projetado para baixar conteúdo via HTTP, **wget** é uma ótima ferramenta para baixar arquivos de servidores web diretamente da linha de comando.

[root @secOps analyst] # **wget 209.165.202. 133:6666 /W32.Nimda.amm.exe**

--2017-04-28 17:00:04--  http://209.165.202.133:6666/W32.Nimda.Amm.exe

Connecting to 209.165.202.133:6666... connected.

HTTP request sent, awaiting response... 200 OK

Length: 345088 (337K) [application/octet-stream]

Saving to: 'W32.Nimda.Amm.exe'

W32.Nimda.Amm.exe   100%[==========================================>] 337.00K  --.-KB/s    in 0.02s  

2017-04-28 17:00:04 (16.4 MB/s) - 'W32.Nimda.Amm.exe' saved [345088/345088]

[root@secOps analyst]#

##### Pergunta:

Qual porta é usada ao se comunicar com o servidor web de malware? Qual é o indicador?

Porta 6666. A porta foi especificada na URL, após o separador:.

O arquivo foi completamente baixado?

Sim

O IDS gerou algum alerta relacionado ao download do arquivo?

Sim

j. Como o arquivo malicioso estava transitando **R1**, o IDS, Snort, foi capaz de inspecionar sua carga útil. A carga correspondeu a pelo menos uma das assinaturas configuradas no Snort e disparou um alerta na segunda janela do terminal **R1** (a guia onde o **tail -f** está sendo executado). A entrada de alerta é mostrada abaixo. Seu carimbo de data/hora será diferente:

04/28-17:00:04.092153  [**] [1:1000003:0] Malicious Server Hit! [**] [Priority: 0] {TCP} 209.165.200.235:34484 -> 209.165.202.133:6666

##### Perguntas:

Com base no alerta mostrado acima, quais foram os endereços IPv4 de origem e destino usados na transação?

[**] [Priority: 0] {TCP} 209.165.200.235:34484 -> 209.165.202.133:6666

Com base no alerta mostrado acima, quais foram as portas de origem e destino usadas na transação?

origem: 34484; Porta de destino: 6666. (Nota: a porta de origem irá variar).

Com base no alerta mostrado acima, quando o download ocorreu?

Com base no alerta mostrado acima, qual foi a mensagem registrada pela assinatura IDS?

“Malicious Server Hit!”

Em **H5**, use o comando **tcpdump** para capturar o evento e baixar o arquivo de malware novamente para que você possa capturar a transação. Execute o seguinte comando abaixo iniciar a captura de pacotes:

[root @secOps analyst] # **tcpdump —i H5-eth0 —w nimda.download.pcap &**

[1] 5633

[root@secOps analyst]# tcpdump: listening on H5-eth0, link-type EN10MB (Ethernet), capture size 262144 bytes

O comando acima instrui o tcpdump para capturar pacotes na interface **H5-eth0** e salvar a captura em um arquivo chamado **nimda.download.pcap**.

O **&** símbolo no final diz ao shell para executar o **tcpdump** em segundo plano. Sem este símbolo, o **tcpdump** tornaria o terminal inutilizável enquanto ele estava em execução. Observe o **[1] 5633**; ele indica que um processo foi enviado para segundo plano e seu ID de processo (PID) é 5366. Seu PID provavelmente será diferente.

k. Pressione **ENTER** algumas vezes para recuperar o controle do shell enquanto **o tcpdump** é executado em segundo plano.

l. Agora que o **tcpdump** está capturando pacotes, baixe o malware novamente. Em **H5**, execute novamente o comando ou use a seta para cima para recuperá-lo do recurso de histórico de comandos.

[root @secOps analyst] # **wget 209.165.202. 133:6666 /W32.Nimda.amm.exe**

- --2017-05-02 10: 26: 50--  http: //209.165.202.133: 6666 / W32.Nimda.Amm.exe

Connecting to 209.165.202.133:6666... connected.

HTTP request sent, awaiting response... 200 OK

Length: 345088 (337K) [application/octet-stream]

Saving to: 'W32.Nimda.Amm.exe'

W32.Nimda.Amm.exe   100%[===================>] 337.00K  --.-KB/s    in 0.003s 

2017-05-02 10:26:50 (105 MB/s) - 'W32.Nimda.Amm.exe' saved [345088/345088]

m. Pare a captura trazendo **tcpdump** para primeiro plano com o comando **fg**. Como **tcpdump** foi o único processo enviado para segundo plano, não há necessidade de especificar o PID. Pare o processo **tcpdump** com **Ctrl+C**. O processo **tcpdump** para e exibe um resumo da captura. O número de pacotes pode ser diferente para sua captura.

[root @secOps analyst] # **fg**

tcpdump -i h5-eth0 -w nimda.download.pcap

^C316 packets captured

316 packets received by filter

0 packets dropped by kernel

[root@secOps analyst]#

n. Em **H5**, use o **comando ls** para verificar se o arquivo pcap foi, de fato, salvo no disco e tem tamanho maior que zero:

[root @secOps analyst] # **ls -l**

total 1400

drwxr-xr-x 2 analyst analyst   4096 Sep 26  2014 Desktop

drwx------ 3 analyst analyst   4096 Jul 14 11:28 Downloads

drwxr-xr-x 8 analyst analyst   4096 Jul 25 16:27 lab.support.files

-rw-r--r-- 1 root    root    371784 Aug 17 14:48 nimda.download.pcap

drwxr-xr-x 2 analyst analyst   4096 Mar  3 15:56 second_drive

-rw-r--r-- 1 root    root    345088 Apr 14 15:17 W32.Nimda.Amm.exe

-rw-r--r-- 1 root    root    345088 Apr 14 15:17 W32.Nimda.Amm.exe.1

 [root@secOps analyst]#

**Observação**: Sua lista de diretórios pode ter uma combinação diferente de arquivos, mas você ainda deve ver o arquivo **nimda.download.pcap**.

##### Pergunta:

Como esse arquivo PCAP pode ser útil para o analista de segurança?

Os arquivos PCAP contêm os pacotes relacionados ao tráfego visto pela NIC de captura. Dessa forma, o PCAP é muito útil para refazer eventos de rede, como comunicação para pontos finais mal-intencionados. Ferramentas como Wireshark podem ser usadas parafacilitar a análise PCAP.

**Nota**: A análise do arquivo PCAP será realizada em outro laboratório.

#### Ajustar regras de firewall com base em alertas IDS

Na Etapa 1, você iniciou um servidor mal-intencionado baseado na Internet. Para impedir que outros usuários acessem esse servidor, é recomendável bloqueá-lo no firewall de borda.

Na topologia deste laboratório, o **R1** não está apenas executando um IDS, mas também um firewall baseado em Linux muito popular chamado **iptables**. Nesta etapa, você bloqueará o tráfego para o servidor mal-intencionado identificado na Etapa 1 editando as regras de firewall atualmente presentes no **R1**.

**Nota**: Embora um estudo abrangente de **iptables** esteja além do escopo deste curso, a lógica básica **iptables** e a estrutura de regras são bastante simples.

O firewall **iptables** usa os conceitos de _chains_ (cadeias) e _regras_ para filtrar o tráfego.

O tráfego que entra no firewall e destinado ao próprio dispositivo de firewall é tratado pela chain **INPUT**. Exemplos desse tráfego são pacotes de ping provenientes de qualquer outro dispositivo em qualquer rede e enviados para qualquer uma das interfaces do firewall.

O tráfego originado no próprio dispositivo de firewall e destinado a outro lugar é tratado pela chain **OUTPUT**. Exemplos desse tráfego são respostas de ping geradas pelo próprio dispositivo de firewall.

O tráfego originou-se em outro lugar e a passagem pelo dispositivo de firewall é manipulada pela chain **FORWARD**. Exemplos desse tráfego são pacotes sendo roteados pelo firewall.

Cada chain pode ter seu próprio conjunto de regras independentes especificando como o tráfego deve ser filtrado para essa chain. Uma chain pode ter praticamente qualquer número de regras, incluindo nenhuma regra.

As regras são criadas para verificar características específicas dos pacotes, permitindo que os administradores criem filtros muito abrangentes. Se um pacote não corresponder a uma regra, o firewall passa para a próxima regra e verifica novamente. Se uma correspondência for encontrada, o firewall executará a ação definida na regra de correspondência. Se todas as regras em uma chain tiverem sido verificadas e ainda nenhuma correspondência foi encontrada, o firewall executará a ação especificada na política da chain, geralmente permite que o pacote flua ou negue.

a. Na VM **CyberOps Workstation**,inicie uma terceira janela de terminal R1.

mininet > **xterm R1**

b. Na nova janela do terminal **R1** , use o comando **iptables** para listar as chain e suas regras atualmente em uso:

[root@secOps~] # **iptables -L -v**

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)

 pkts bytes target prot opt in out source   destination    

Chain FORWARD (policy ACCEPT 6 packets, 504 bytes)

 pkts bytes target prot opt in out source   destination    

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)

 pkts bytes target prot opt in out source   destination    

[root @secOps ~] #

##### Pergunta:

Quais chain estão atualmente em uso pelo **R1**?

INPUT, OUTPUT and FORWARD

c. Conexões com o servidor mal-intencionado geram pacotes que devem transverter o firewall **iptables** no **R1**. Os pacotes que atravessam o firewall são tratados pela regra FORWARD e, portanto, essa é a chain que receberá a regra de bloqueio. Para impedir que os computadores do usuário se conectem ao servidor mal-intencionado identificado na Etapa 1, adicione a seguinte regra à chain FORWARD no **R1**:

[root@secOps ~]# **iptables -I FORWARD -p tcp -d 209.165.202.133 --dport 6666 -j DROP**

[root @secOps ~] #

Onde:

- **-I FORWARD**: insere uma nova regra na chain FORWARD.

- **-p tcp**: especifica o protocolo TCP.

- **-d 209.165.202.133**: especifica o destino do pacote

- -dport 6666**: especifica a porta de destino

- **-j DROP**: define a ação para soltar.

d. Use o comando **iptables** novamente para garantir que a regra foi adicionada à chain FORWARD. A VM CyberOps Workstation pode levar alguns segundos para gerar a saída:

[root@secOps analyst]# **iptables -L -v**

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)

 pkts bytes target prot opt in out source   destination    

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)

 pkts bytes target prot opt in out source   destination    

    0 0 DROP   tcp  --  any    any anywhere  209.165.202.133  tcp dpt:6666

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)

 pkts bytes target prot opt in out source   destination    

[root@secOps analyst]#

e. No **H5**, tente baixar o arquivo novamente:

[root @secOps analyst] # **wget 209.165.202. 133:6666 /W32.Nimda.amm.exe**

- --2017-05-01 14: 42: 37--  http: //209.165.202.133: 6666 / W32.Nimda.Amm.exe

Connecting to 209.165.202.133:6666... failed: Connection timed out.

Retrying.

--2017-05-01 14:44:47--  (try: 2)  http://209.165.202.133:6666/W32.Nimda.Amm.exe

Connecting to 209.165.202.133:6666... failed: Connection timed out.

Retrying.

Digite **Ctrl+C** para cancelar o download, se necessário.

##### Perguntas:

O download foi bem sucedido desta vez? Explique.

Não. O firewall está bloqueando conexões com o servidor de hospedagem de malware.

O que seria uma abordagem mais agressiva, mas também válida, ao bloquear o servidor ofensivo?

Em vez de especificar IP, protocolo e porta, uma regra poderia simplesmente bloquear o endereço IP do servidor. Isso cortaria completamente o acesso a esse servidor a partir da rede interna.


### Parte 3: Encerrar e Limpar o Processo Mininet

a. Navegue até o terminal usado para iniciar Mininet. Encerre o Mininet inserindo **quit** na janela principal do terminal da VM security workstation.

b. Depois de sair da Mininet, limpe os processos iniciados pela Mininet. Entre a senha **cyberops** quando solicitado

[analyst@secOps scripts]$ **sudo mn –c**

[sudo] password for analyst:

# Laboratório - Use algoritmos de criptografia clássica e moderna

## Objetivos

Parte 1: Use um algoritmo de criptografia clássico

Parte 2: Use um algoritmo de criptografia simétrica moderna

Parte 3: Use um algoritmo de criptografia assimétrica moderna

## Histórico/Cenário

A criptografia moderna baseia-se principalmente na teoria matemática e na prática da ciência da computação. Os algoritmos criptográficos são projetados em torno de suposições de complexidade computacional, tornando-as difíceis, se não impossíveis, de serem quebradas por um agente de ameaças. JCrypTool é uma ferramenta de software de código aberto, independente de plataforma, e faz parte do projeto de código aberto CrypTool. O JCrypTool é uma plataforma de e-learning extensível que apresenta criptografia, análise de criptografia e segurança de TI de uma forma moderna e fácil de usar. Este laboratório usará o JCrypTool para apresentar algoritmos criptográficos clássicos, modernos, simétricas e assimétricas.

## Recursos necessários

PC com o **CSE-LABVM** instalado no VirtualBox

## Instruções

### Parte 1: Use um algoritmo de criptografia clássica

Na criptografia, uma cifra é um algoritmo utilizado para realizar a criptografia ou descriptografia. Uma cifra é um conjunto de etapas (um algoritmo) para executar uma criptografia e a descriptografia correspondente. As primeiras cifras de criptografia foram projetadas para permitir que a criptografia e a descriptografia ocorram manualmente, enquanto as que são desenvolvidas e usadas hoje em dia só são possíveis com computadores. Os algoritmos clássicos são aqueles inventados até os anos 50.

Uma cifra de César, também conhecida como cifra de deslocamento, é uma das técnicas de criptografia mais simples e amplamente conhecidas. O método tem o nome de Júlio César, que o usou em sua correspondência privada. A cifra de César é um tipo de cifra de substituição na qual cada letra é substituída por outra letra que é correspondente a um número que define quantas posições irão pular no alfabeto. Por exemplo, com um turno à esquerda de 3, D seria substituído por A, E se tornaria B e assim por diante.

#### Etapa 1: Inicie o CSE-LABVM.

#### Etapa 2: Abrir e explorar o JCrypTool.

a.  Clique duas vezes no ícone **JCrypTool** na área de trabalho. O diretório **JCrypTool** é aberto.

b.  Clique duas vezes no ícone **JCrypTool**.

A ferramenta tem quatro janelas:

**Explorador de arquivos** - É usado para localizar, abrir e salvar arquivos.

**Ajuda** - É usado para localizar arquivos de ajuda e tutoriais.

**Arquivo aberto atualmente** - Contém arquivos para serem operados com ferramentas de criptografia. O arquivo **unsaved001.txt** deve estar aberto.

**Crypto Explorador** - Fornece acesso a ferramentas de criptografia. Por padrão, o Crypto Explorador não é exibido. Para abri-lo, clique em **Janela**> **Mostrar vistas**> **Crypto Explorador**.

#### Etapa 3: Use o algoritmo de César para criptografar uma mensagem de texto.

a.    Para começar, você precisará preencher o arquivo aberto no momento com a mensagem que deseja criptografar. Destaque todo o texto no arquivo ***unsaved001.txt** e substitua-o pela seguinte mensagem:

**CRIPTOGRAFIA É DIVERTIDO VOCÊ PODE LER ESTA MENSAGEM SECRETA?**

b.  No **Crypto Explorador,**clique em **Clássico** se não for expandido e clique duas vezes em **César**.

c.  Na seção **Operação**, selecione **Criptografar**, se ainda não estiver selecionada.

d.    Na seção **Alfabeto**, verifique se as opções **Selecionar alfabeto** e **Latim (AZ)** estão selecionadas. Caso contrário, selecione-os agora.

e.    Na seção **Chave**, vá para **Entrar usando um caractere** e mude para **K**. Deixe todas as outras opções como padrão.

f.  Clique em **Concluir** para salvar as opções e criptografar os dados.

g.    Um novo arquivo chamado ***out001.txt** é aberto com a mensagem criptografada.

#### Etapa 4: Descriptografar o texto criptografado com o algoritmo de César.

a.  Mova o arquivo ***out001.txt** para a janela do Explorador de arquivos, se necessário. Isso garante que o **Crypto Explorador** use esse arquivo como o arquivo ativo. Você também pode fechar o arquivo ***unsaved001.txt**.

b.   Na guia **Crypto Explorador**, clique duas vezes no algoritmo de **César** novamente.

c.  Na seção **Operação**, selecione **Descriptografar**.

d.  Selecione as mesmas configurações para descriptografar o texto cifrado atual no arquivo de saída ***out001.txt**.

e.  Clique em **Concluir** para salvar as opções e descriptografar os dados.

f.  Feche todos os arquivos no **Explorador de Arquivos**. Não há necessidade de salvá-los.

#### Etapa 5: Alterar as configurações do algoritmo de César.

a.  Crie um novo arquivo de texto de entrada selecionando **Arquivo**> **Novo**> **Arquivo vazio no Editor de texto**.

b.  Digite a seguinte mensagem: **Criptografia é divertido. Você consegue ler esta mensagem secreta?**

c.  Na guia **Crypto Explorador**, clique duas vezes no algoritmo de **César** novamente.

d.  **Criptografar** já deve estar selecionada. Para **Selecionar alfabeto**, defina o valor como **Latim maiúsculo e minúsculo (AZ, az).** Para a quantidade de turnos ("shifts") ao longo do alfabeto, defina o valor como **13**.

e.  Clique em **Concluir** para salvar as opções e criptografar os dados.

f.  Feche todos os arquivos no **Explorador de Arquivos**. Não há necessidade de salvá-lo.

Explorações adicionais

Experimente sozinho o César e outros algoritmos de criptografia clássicos para ver como eles funcionam.

### Parte 2: Use um algoritmo de criptografia simétrica moderna

Nesta parte, você usará um algoritmo de criptografia simétrica moderna. Uma das versões mais populares de um algoritmo criptográfico moderno é o Advanced Encryption Standard (AES). O AES é uma cifra criptográfica simétrica em software e hardware que é usada em todo o mundo para criptografar dados confidenciais. A criptografia AES requer uma chave de criptografia para controlar o processo de criptografia e descriptografia. Esse algoritmo é considerado um protocolo criptográfico forte com base em sua complexidade e comprimento de chave de 128 bits.

#### Etapa 1: Usar criptografia AES para criptografar uma mensagem de texto.

a.  Crie um novo arquivo de texto de entrada selecionando **Arquivo**> **Novo**> **Arquivo vazio no Editor de texto**.

b.  Digite a seguinte mensagem: **Criptografia é divertido. Você consegue ler esta mensagem secreta?**

c.  Na guia **Crypto Explorador**, clique em **Simétrico** para expandi-lo, se necessário, e clique duas vezes em **AES**.

d.  Use as seguintes configurações.

·      Operação: **criptografar**

·      Origem da chave: **Chave personalizada**

·      Tamanho da chave: **128**

·      Chave (hex): **AA 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FF**

·      Modo: **Manual de códigos eletrônico (codebook) (BCE)**

·      Espaçamento: **PKCS ## 5 Espaçamento**

e.  Clique em **Concluir.** Um arquivo de saída com extensão a.bin é aberto. Você verá quatro linhas com 16 valores hexadecimais em cada linha. O texto cifrado é exibido à direita de cada linha.

#### Etapa 2: Use AES para descriptografar a mensagem.

a.  Clique duas vezes em **AES** novamente.

b.  Altere a **Operação** para **Descriptografar** e, em seguida, use as configurações da Etapa 1 para descriptografar o texto cifrado.

c.  Clique em **Concluir** para salvar as opções e descriptografar os dados. Um arquivo de saída com extensão .bin é aberto com o texto descriptografado.

d.  Feche todos os arquivos.

### Parte 3: Use um algoritmo de criptografia assimétrica moderna

Nesta parte, você usará um algoritmo de criptografia assimétrica moderno. Ao contrário da criptografia simétrica, a criptografia assimétrica criptografa e descriptografa os dados usando duas chaves criptográficas separadas matematicamente conectadas. Essas chaves são conhecidas como “Chave pública” e “Chave privada”. Para que uma pessoa envie uma mensagem criptografada para outra pessoa usando criptografia assimétrica, ela solicita uma chave pública e depois a usa para criptografar uma mensagem com um algoritmo combinado. A outra pessoa descriptografa a mensagem usando sua chave privada. A mensagem não pode ser descriptografada usando a chave pública.

#### Etapa 1: Use a criptografia assimétrica do RSA para criptografar um arquivo de texto.

a.  Crie um novo arquivo de texto de entrada selecionando **Arquivo**> **Novo**> **Arquivo vazio no Editor de texto**.

b.  Digite a seguinte mensagem: **Criptografia é divertido. Você consegue ler esta mensagem secreta?**

c.  No Crypto Explorador, clique em **Assimétrico** para expandi-lo e clique duas vezes em **RSA** para abrir as configurações do algoritmo.

d.  Use as seguintes configurações:

·      Operação: **Criptografar**

·      Keystore: clique em **Criar um novo par no keystore**.

·      Na caixa de diálogo **Novo par de chaves**, insira o seguinte:

o    Nome de contato: **John Smith**

o    Senha: **Segredo**

o    Deixe todas as outras entradas como padrão.

e.  Clique em **Concluir.**

f.   Clique em **Concluir** na caixa de diálogo **RSA - criptografia** para criptografar os dados. Um arquivo de saída com extensão .bin é aberto com o texto criptografado.

#### Etapa 2: Use a criptografia assimétrica RSA para descriptografar um arquivo de texto.

a.  Clique duas vezes em **RSA**.

b.  Selecione **Descriptografar** para a operação.

c.  Chave de seleção = **"John Smith" - chave pública - 1024**

d. Clique em **Concluir** para descriptografar o texto cifrado.

e. Insira a senha **Segredo**. Clique em **OK**.

# Packet Tracer para exibir dados de rede gerados pelo syslog, AAA e NetFlow

## Objetivos

**Parte 1: Usar syslog para capturar arquivos de log de vários dispositivos de rede**

**Parte 2: Observe o registro de acesso do usuário AAA**

**Parte 3: Observar as informações do NetFlow**

## Histórico/Cenário

Nesta atividade, você usará o Rastreador de Pacotes para exibir dados de rede gerados pelo syslog, AAA e NetFlow.

## Instruções

### Parte 1: Exibir entradas de log com Syslog

#### Etapa 1: O servidor syslog

O Syslog é um sistema de mensagens projetado para suportar o registro remoto. Os clientes Syslog enviam entradas de log para um servidor syslog. O servidor syslog concentra e armazena entradas de log. O Packet Tracer suporta operações básicas de syslog e pode ser usado para demonstração. A rede inclui um servidor syslog e clientes syslog. R1, R2, Core Switch e o Firewall são clientes syslog. Esses dispositivos são configurados para enviar suas entradas de log para o servidor syslog. O servidor syslog coleta as entradas de log e permite que elas sejam lidas.

As entradas de log são categorizadas por sete níveis de gravidade. Níveis mais baixos representam eventos mais graves. Os níveis são: emergências (0), alertas (1), críticos (2), erros (3), avisos (4), notificações (5), informativos (6) e depuração (7). Os clientes Syslog podem ser configurados para enviar entradas de log para servidores syslog com base no nível de gravidade.

a. Clique no **Syslog Server** para abrir sua janela.

b. Selecione a guia de **Services** ﻿﻿ e selecione **SYSLOG** na lista de serviços mostrada à esquerda.

c. ﻿Clique em **On** para ativar o serviço Syslog.

d. As entradas de syslog provenientes de clientes syslog serão mostradas na janela à direita. Atualmente, não há entradas.

e. Mantenha esta janela aberta e visível e vá para o **Passo 2**.

#### Etapa 2: Habilitar o Syslog.

Os dispositivos já estão configurados para enviar mensagens de log para o servidor syslog, mas o Rastreador de Pacotes suporta somente o log para o nível de gravidade de depuração com syslog. Devido a isso, devemos gerar mensagens de nível de depuração (nível 7) para que possam ser enviadas para o servidor syslog.

a. Clique na guia **R1** **> CLI**.

b. Pressione Enter para obter um prompt de comando e digite o comando **enable**.

c. Entre o comando **debug eigrp packets** para habilitar a depuração EIGRP. O console de linha de comando irá preencher imediatamente com mensagens de depuração.

d. Retorne para a janela **Syslog Server** Verifique se as entradas de log aparecem no servidor syslog.

e. Depois que algumas mensagens forem registradas, clique no botão de rádio para ativar o serviço syslog **Off**.

##### Pergunta:

Quais são algumas das informações incluídas nas mensagens do syslog que estão sendo exibidas pelo Servidor Syslog?

EIGRP: Sending HELLO on GigabitEthernet0/0 AS 1, Flags 0x0, Seq 10/0 idbQ 0/0 iidbQ un/rely 0/0 Algumas das informações são tipo de pacote EIGRP (HELLO), a interface que recebeu os pacotes, o sistema autônomo do EIGRP, data e hora e a origem da mensagem. Os detalhes variam.

f.  Feche a janela do dispositivo R1

#### Etapa 3: Logar Acesso de Usuário

Outro tipo importante de log está relacionado ao acesso do usuário. Ter registros de logins de usuários é crucial para solução de problemas e análise de tráfego. O Cisco IOS suporta autenticação, autorização e contabilidade (AAA). Com o AAA, é possível não apenas delegar a tarefa de validação do usuário a um servidor externo, mas também registrar atividades.

TACACS+ é um protocolo projetado para permitir autenticação remota através de um servidor centralizado.

O Packet Tracer oferece suporte básico AAA e TACACS+. R2 também é configurado como um servidor TACACS+. R2 perguntará ao servidor se esse usuário é válido verificando nome de usuário e senha, e concederá ou negará acesso com base na resposta. O servidor armazena as credenciais do usuário e também é capaz de registrar transações de login do usuário. Siga as etapas abaixo para fazer login no R2 e exibir as entradas de log relacionadas a esse login:

a. Clique no **Syslog Server** para abrir sua janela.

b. Selecione a guia **Desktop** e selecione **AAA Accounting**. Deixe essa janela aberta.

c. Clique em **R2 > CLI**.

d. Pressione Enter para obter um prompt de comando. **R2** irá pedir nome de usuário e senha antes de conceder acesso ao seu CLI. Insira as seguintes credenciais de usuário: **analyst** e **cyberops** como nome de usuário e senha, respectivamente.

e. Retorne à janela de registros de contabilidade AAA do servidor Syslog.

##### Pergunta:

Quais informações estão na entrada de log?

A entrada de log vai mostrar : DATE= 09:56:31 UTC Apr 05 2017 ,Username= analyst ,Caller Id= ,Flag= Start ,NAS IP= 192.168.12.2 ,NAS Port= con0 A entrada contém a estampa de hora de quando o evento aconteceu, o usuario e a senha usados, endereço IP de R2 (o dispositivo usado para a tentativa de login) e uma flag de Inicio Start. O sinalizador Iniciar indica que o usuário analista efetuou login no momento mostrado.

f.  On R2, insira o comando **logout**.

##### Pergunta:

O que aconteceu na janela de contabilidade da AAA?

Uma nova entrada foi adicionada, no entanto, desta vez o sinalizador Stop indica que o usuário desconectou.

## Parte 2: NetFlow e Visualização

Na topologia, o servidor Syslog também é um NetFlow collector. O firewall é configurado como um NetFlow exporter.

a. Clique no **Syslog Server** para abrir sua janela. Feche a janela Registros Contábeis AAA.

b. Da guia **Desktop** , selecione **Netflow Collector**. Os serviços do NetFlow collector devem ser ativados.

c. De qualquer PC, execute ping no Corp Web Server em 209.165.200.194. Após um breve atraso, o gráfico de pizza será atualizado para mostrar o novo fluxo de tráfego.

**Nota**: Os gráficos de pizza exibidos variam de acordo com o tráfego na rede. Outros fluxos de pacotes, como tráfego relacionado ao EIGRP, estão sendo enviados entre dispositivos. O NetFlow está capturando esses pacotes e exportando estatísticas para o NetFlow Collector. Quanto mais tempo o NetFlow tiver permissão para ser executado em uma rede, mais estatísticas de tráfego serão capturadas.

## Reflexão

Embora as ferramentas apresentadas nesta atividade sejam úteis, cada uma tem seu próprio serviço e pode precisar rodar em dispositivos totalmente diferentes. Uma maneira melhor, explorada mais tarde no curso, é que todas as informações de registro sejam concentradas em uma única ferramenta, permitindo fácil referência cruzada e recursos poderosos de pesquisa. As plataformas SIEM (Security Information and Event Management, gerenciamento de eventos e informações de segurança) podem coletar arquivos de log e outras informações de diversas fontes e integrar as informações para acesso por uma única ferramenta.

# Packet Tracer - Configurar a autenticação baseada em servidor com TACACS+ e RADIUS



## Tabela de endereçamento

|Dispositivo|Interface|Endereço IP|Máscara de Sub-Rede|Gateway padrão|Porta do Switch|
|---|---|---|---|---|---|
|R1|G0/1|192.168.1.1|255.255.255.0|N/D|S1 F0/1|
|R1|S0/0/0 (DCE)|10.1.1.2|255.255.255.252|N/D|N/D|
|R2|G0/0|192.168.2.1|255.255.255.0|N/D|S2 F0/2|
|R2|S0/0/0|10.1.1.1|255.255.255.252|N/D|N/D|
|R2|S0/0/1 (DCE)|10.2.2.1|255.255.255.252|N/D|N/D|
|R3|G0/1|192.168.3.1|255.255.255.0|N/D|S3 F0/5|
|R3|S0/0/1|10.2.2.2|255.255.255.252|N/D|N/D|
|Servidor TACACS+|Placa de rede|192.168.2.2|255.255.255.0|192.168.2.1|S2 F0/6|
|Servidor RADIUS|Placa de rede|192.168.3.2|255.255.255.0|192.168.3.1|S3 F0/1|
|PC-A|NIC|192.168.1.3|255.255.255.0|192.168.1.1|S1 F0/2|
|PC-B|NIC|192.168.2.3|255.255.255.0|192.168.2.1|S2 F0/1|
|PC-C|NIC|192.168.3.3|255.255.255.0|192.168.3.1|S3 F0/18|

Linha em branco, sem informações adicionais

## Objetivos

Configurar a autenticação AAA baseada no servidor usando o TACACS+.

Verifique a autenticação AAA baseada em servidor do cliente PC-B.

Configurar a autenticação AAA baseada no servidor usando o RADIUS.

Verifique a autenticação AAA baseada em servidor do cliente PC-B .

## Histórico/Cenário

A topologia de rede mostra os roteadores R1, R2 e R3. Atualmente, toda a segurança administrativa é baseada no conhecimento da senha secreta de habilitação. Sua tarefa é configurar e testar soluções AAA locais e baseadas em servidor.

Você configurará o roteador R2 para apoiar a autenticação baseada no servidor usando o protocolo TACACS+. O servidor TACACS+ foi pré-configurado com o seguinte:

o Cliente: R2 usando a palavra -chavetacacspa55

o Conta de usuário: Admin2 e senha admin2pa55

Finalmente, você configurará o roteador R3 para apoiar a autenticação baseada no servidor usando o protocolo RADIUS. O servidor Radius foi pré-configurado com o seguinte:

o Cliente: R3 usando a palavra-chave radiuspa55

o Conta de usuário: Admin3 e senha admin3pa55

Os roteadores também foram pré-configurados com o seguinte:

o Habilitar senha secreta: ciscoenpa55

o Protocolo de roteamento OSPF com autenticação MD5 usando senha: MD5pa55

Nota: O console e as linhas vty não foram pré-configuradas.

**Nota**: As imagens IOS mais novas usam o algoritmo de hashing de criptografia mais seguro; contudo, a versão IOS apoiada atualmente no Packet Tracer usa MD5. Use sempre a opção mais segura disponível no seu equipamento físico.

### Parte 1: Configurar a autenticação AAA baseada em servidor usando o TACACS+ no R2

#### Etapa 1: Testar Conectividade

Ping do PC-A para PC-B.

Ping do PC-A para PC-C.

Ping do PC-B para PC-C.

#### Etapa 2: Configurar uma entrada de banco de dados local de backup chamada Admin.

Para fins de backup, configure um nome de usuário local de Admin2 e uma senha secreta de admin2pa55.

#### Etapa 3: Verifique a configuraçãodo servidor TACACS+.

Clique o server TACACS+. Na aba Serviços, clique em **AAA**. Observe que há uma entrada de configuração de rede para o R2 e uma entrada da instalação do usuário para Admin2.

#### Etapa 4: Configurar os detalhes do servidor TACACS+ no R2 .

Configurar o endereço IP e a chave secreta do servidor AAA TACACS no R2.

**Nota**: Os comandos **tacacs-server host** e a **tacacs-server key** são obsoletas Atualmente, o Packet Tracer não suporta o novo comando **tacacs server** .

R2(config)# **tacacs-server host 192.168.2.2**

R2(config)# **tacacs-server key tacacspa55**

#### Etapa 5: Configurar a autenticação de login AAA para o acesso de console no R2.

Ative o AAA no R2 e configure todos os logins para autenticar usando o servidor AAA TACACS+. Se não estiver disponível, use o banco de dados local.

#### Etapa 6: Configurar as linhas vty para usar o método de autenticação AAA definido.

Configurar a autenticação AAA para que o login do console use o método de autenticação AAA padrão.

#### Etapa 7: Verifique o método de autenticação AAA.

Verifique o login EXEC do usuário usando o servidor AAA TACACS+.

### Parte 2: Configure a Autenticação baseada em servidor AAA usando RADIUS no R3

#### Etapa 1: Configure uma base de dados de backup local chamada Admin.

Para fins de backup, configure um nome de usuário local de **Admin3** e uma senha secreta **admin3pa55**.

#### Etapa 2: Verifique a configuração do servidor Radius.

Clique o servidor Radius. Na aba Serviços, clique em **AAA**. Observe que há uma entrada de configuração de rede para o R3 e uma entrada de instalação do usuário para Admin3.

#### Etapa 3: Configurar os detalhes do servidor Radius no R2 .

Configurar o endereço IP e a chave secreta do servidor AAA Radius no R3.

**Nota**: Os comandos **radius-server host** e a **radius-server key** são obsoletas Atualmente, o Packet Tracer não suporta o novo comando **radius server** .

R3(config)# **radius-server host 192.168.3.2**

R3(config)# **radius-server key radiuspa55**

#### Etapa 4: Configurar a autenticação de login AAA para o acesso de console no R2.

Ative o AAA no R3 e configure todos os logins para autenticar usando o servidor AAA Radius. Se não estiver disponível, use o banco de dados local.

#### Etapa 5: Configurar as linhas vty para usar o método de autenticação AAA definido.

Configurar a autenticação AAA para que o login do console use o método de autenticação AAA padrão.

#### Etapa 6: Verifique o método de autenticação AAA.

Verifique o início de uma sessão EXEC do usuário usando o servidor RADIUS AAA.

#### Etapa 7:Verifique os resultados.

O percentual de conclusão deve ser 100%. Clique em **Check Results** para ver o feedback e a verificação de quais componentes necessários foram concluídos.


# Packet Tracer - Configure o Controle de Acesso


## Objetivos

**Parte 1: Configurar e usar credenciais de autenticação AAA**

**Parte 2: Configurar e Verificar Serviços de E-mail**

**Parte 3: Configurar e usar serviços de FTP**

## Histórico/Cenário

Autenticação e autorização são processos de segurança distintos no mundo do gerenciamento de identidade e acesso (IAM). A autenticação usa senhas e outros métodos de identificação para confirmar que os usuários são quem eles dizem ser. Por outro lado, a autorização atribui permissões de usuário aos recursos aos quais o usuário tem permissão. Nesta atividade do Packet Tracer (PT), você configurará a autenticação e a autorização para serviços de rede, incluindo acesso à rede sem fio, e-mail e serviços de FTP.

**Nota**: Esta atividade é aberta no modo **Físico**. No entanto, você pode concluí-la no modo **Lógico**.

**Observação**: a maioria das tarefas nesta atividade é classificada. Clique em **Verificar resultados** a qualquer momento para ver os **Itens de avaliação** corretos e incorretos.

## Instruções

### Parte 1: Configurar e usar credenciais de autenticação AAA

#### Etapa 1: Configurar contas de usuário no servidor AAA.

a. Navegue até a Sede e clique no **Gabinete de Fiação**, que é o chassi do servidor preto e alto no canto inferior esquerdo.

b. No **Rack** do lado direito, clique em **AAA-RADIUS** server > **guia Serviços** e depois em **AAA** debaixo de **SERVICES**.

c. Ative o serviço AAA.

d. Em **Configuração do usuário**, adicione os seguintes nomes de **usuário** / **senhas**.

- user1 / PASSuser1!

- user2 / PASSuser2!

#### Etapa 2: Configurar a autenticação sem fio no HQ-Laptop-1.

a. Volte para HQ e clique em HQ-Laptop-1. Ele está localizado em duas salas à direita do **Wiring Closet**.

b. Clique na guia **Config** e, depois, clique na **INTERFACE** **Wireless0**.

c. Na caixa **SSID**, digite HQ-INT.

d. Na área **Autenticação**, clique em **WPA2**.

e. Na caixa **ID de usuário**, insira user1; e digite PASSuser1! na caixa **Senha**.

f. Na seção de **Configuração de IP**, clique em **DHCP**. Que minutos o DHCP oferece para ser aceito. Verifique o endereço IP recebido pelo HQ-Laptop-1 e tenha um endereço na rede 192.168.50.0/24.

**Observação**: pode ser necessário alternar entre **estático** e **DHCP** para forçar o Packet Tracer a convergir em suas configurações. Além disso, clique em **Verificar resultados** para verificar se configurou corretamente o servidor AAA e as configurações sem fio no laptop. Clicar em **Verificar resultados** também pode forçar o Packet Tracer a convergir. Se tudo estiver configurado corretamente, prossiga para a configuração do HQ-Laptop-2 e, em seguida, retorne para HQ-Laptop-1 e verifique sua configuração de IP. Esse problema normalmente é resolvido.

#### Etapa 3: Configurar a autenticação sem fio no HQ-Laptop-2.

a. Clique em HQ-Laptop-2, localizado no canto superior direito da HQ.

b. Repita as etapas anteriores para definir as configurações sem fio para HQ-Laptop-2, usando as credenciais de usuário2.

c. Verifique o endereço IP recebido pelo HQ-Laptop-2 e receba um endereço na rede 192.168.50.0/24.

### Parte 2: Configurar e usar serviços de e-mail

#### Etapa 1: Ativar serviços de e-mail e configurar contas de usuário de e-mail.

a. Navegue para o **armário de fiação**.

b. No lado direito do **Rack**, clique em Servidor de **e-mail** > guia **Serviços** e depois **EMAIL** em **SERVIÇOS**.

c. Ative os serviços **SMTP** e **POP3**.

d. Defina o domínio como mail.cyberhq.com.

e. Em **Configuração do usuário**, digite os seguintes **nomes de usuário** / **senhas**. Clique no sinal de adição (**+**) para adicionar cada par.

o HQuser1 / Cisco123!

o HQuser2 / Cisco123~

o BRuser1 / Cisco123-

o BRuser2 / Cisco123 +

#### Passo 2: Configure os clientes de e-mail

a. Volte para a sede e clique no PC 1-1, que fica no canto inferior.

b. Clique na guia **Desktop** > **Email**. As **configurações de caixa de correio** são abertas.

c. Insira as informações a seguir:

o    Seu nome: Suk-Yi

o    Endereço de e-mail: HQuser1@mail.cyberhq.com

o    Servidor de e-mail de entrada e saída: email.cyberhq.com

o    Nome do usuário: HQuser1

o    Senha: Cisco123!

Clique em **Salvar**.

d. Use as informações da tabela para definir as configurações de e-mail para 2-3, HQ-Laptop-1 e Net-Admin. O PC 2-3 está no escritório abaixo da sala de conferência. O PC Net-Admin está no **armário de conexões**.

|PC / Laptop|Seu nome|Endereço de e-mail|Nome de Usuário|Senha|
|---|---|---|---|---|
|2-3|Ajulo|BRuser1 @ mail.cyberhq.com|BRuser1|Cisco123-|
|HQ-Laptop-1|Malia|BRuser2 @ mail.cyberhq.com|BRuser2|Cisco123 +|
|NetAdmin|Cisco|HQuser2@mail.cyberhq.com|HQuser2|Cisco123~|

Linha em branco, sem informações adicionais

#### Etapa 3: Enviar um e-mail como Suk-Yi.

a. No PC 1-1, clique em **Escrever**.

b. Escreva um e-mail para o Ajulo em BRuser1@mail.cyberhq.com. Insira um assunto e uma mensagem de e-mail de sua escolha. Clique em **Enviar** quando terminar.

**Observação**: o Packet Tracer pode levar vários segundos para convergir antes de você ver uma mensagem de **envio de sucesso** na parte inferior da janela.

**Observção**: o packet tracer não classifica esta etapa. Verifique se você concluiu corretamente esta etapa ao receber o e-mail enviado por Suk-Yi no PC 2-3 do Ajulo.

c. Navegue até o PC 2-3 do Ajulo. Se necessário, clique na guia **Desktop** > **E-mail**.

d. Clique em **Receber** e leia o e-mail de Suk-Yi.

### Parte 3: Configurar e usar serviços de FTP

#### Etapa 1: Ative o serviço de FTP.

a. Navegue para o **armário de fiação**.

b. No lado direito do **rack**, clique em Servidor **FTP** > guia **Serviços** e depois em **FTP** em **SERVIÇOS**.

c. Ative o serviço **FTP** .

#### Etapa 2: Criar as contas de usuário de FTP.

a. Em **Configuração do usuário**, insira os seguintes nomes de usuário, senhas e privilégios. Clique em **Adicionar** para adicionar cada usuário.

**Observação**: certifique-se de que o nome de usuário malia não inclua a opção **Excluir** como um dos privilégios de usuário.

|Nome de usuário|Senha|Privilégio de usuário|
|---|---|---|
|sukyi|cisco123|RWDNL (escrever, ler, excluir, renomear, lista)|
|ajulo|cisco321|RWDNL (escrever, ler, excluir, renomear, lista)|
|malia|cisco123|RWNL (gravação, leitura, renomeação, lista)|

Linha em branco, sem informações adicionais

b. Verifique se cada usuário foi criado corretamente e feche o servidor.

#### Etapa 3: Transferir arquivos entre o Net-Admin e o servidor FTP.

a. Clique em Net-Admin PC e então clique em **Área de Trabalho** > **Prompt de Comando**.

b. Insira o comando **ftp 192.168.75.2** para fazer login no servidor FTP e, em seguida, autentique com o nome de usuário sukyi e a senha cisco123.

c. Insira o comando **dir** para listar os arquivos no servidor FTP.

d. Use o comando **get** para baixar aMessage.txt.

e. Saia da sessão de FTP.

f. Feche o **prompt de comando**, clique em **Editor de texto** e em **Arquivo** > **Abrir**. Abra o arquivo baixado aMessage.txt.

##### Pergunta:

Qual é a mensagem no arquivo?

g. Clique em **Arquivo > Novo**. Digite uma mensagem de texto de sua escolha.

h. Clique em **Arquivo** > **Salvar** e salve o novo arquivo como aMessage_new.txt. Feche o **Text Editor** (Editor de Texto) quando terminar.

i.  Clique em **Prompt de comando** e faça o login novamente no servidor FTP como usuário sukyi.

j.  Use o comando **put** para carregar aMessage_new.txt.

k. Saia da sessão de FTP.

#### Etapa 4: Verificar se os privilégios de usuário do FTP estão funcionando conforme configurado.

a. Volte para HQ e clique em HQ-Laptop-1, guia **Desktop** > **Prompt de comando**.

b. Faça login no servidor FTP em 192.168.75.2 com o nome de usuário malia e a senha **cisco123**.

c. Use o comando **delete** para tentar remover o arquivo recém-carregado aMessage_new.txt.

##### Pergunta:

Você conseguiu excluir o arquivo do servidor FTP? Explique.

d. Use o comando **rename** para tentar alterar o nome de aMessage_new.txt para aMessage_rename.txt.

ftp> **rename aMessage_new.txt aMessage_rename.txt**

##### Pergunta:

Você conseguiu renomear o arquivo do servidor FTP?

e. Saia da sessão de FTP e feche a janela HQ-Laptop-1.

# Packet Tracer - Explore uma implementação NetFlow

## Objetivos

Parte 1: Observar registros de fluxo NetFlow - Uma direção

Parte 2: Observe os registros NetFlow para uma sessão que entra e sai do coletor

## Histórico/Cenário

Nesta atividade, você usará o Packet Tracer para criar tráfego de rede e observar os registros de fluxo NetFlow correspondentes em um coletor NetFlow. O Packet Tracer oferece uma simulação básica da funcionalidade NetFlow. Não é um substituto para aprender NetFlow em equipamentos físicos. Algumas diferenças podem existir entre registros de fluxo NetFlow gerados pelo Packet Tracer e por registros criados por equipamentos de rede completos.

## Instruções

### Parte 1: Observar registros de fluxo de NetFlow - One Direction

#### Etapa 1: Abra o NetFlow collector.

a. No NetFlow collector, clique na guia **Desktop** . Clique no icone **Netflow Collector** .

b. Clique no botão de opção **On** para ativar o coletor conforme necessário. Posicione e dimensione a janela de forma que seja visível na janela de topologia do Packet Tracer.

#### Etapa 2: Ping no gateway padrão do PC-1.

a. CliquePC-1.

b. Abra a guia **Desktop** e clique no icone **Command Prompt** .

c. Entre o comando **ping** para testar a conectividade com o gateway padrão em 10.0.0.1.

C:\> **ping 10.0.0.1**

d. Após um breve atraso, a tela do NetFlow collector exibirá um gráfico de pizza.

**Nota**: O primeiro conjunto de pings pode não ser enviado ao NetFlow collector porque o processo ARP deve primeiro resolver os endereços IP e MAC. Se após 30 segundos, um gráfico de pizza não aparecer, execute ping no gateway padrão novamente.

e. Clique no gráfico de pizza ou na entrada da legenda para exibir os detalhes do registro de fluxo.

f.  O registro de fluxo terá entradas semelhantes às da tabela abaixo. Seus carimbos de data / hora serão diferentes.

|Entrada|Valor|Explicação|
|---|---|---|
|Contribuição do tráfego|100% (1/1)|Esta é a proporção de todo o tráfego representado por esse fluxo.|
|IPV4 SOURCE ADDRESS|10.0.0.10|Este é o endereço IP de origem dos pacotes de fluxo.|
|IPV4 DESTINATION ADDRESS|10.0.0.1|Este é o endereço IP de destino dos pacotes de fluxo.|
|TRNS SOURCE PORT|0|Esta é a porta de origem da camada de transporte. O valor é 0 porque este é um fluxo ICMP.|
|TRNS DESTINATION PORT|0|Esta é a porta de destino da camada de transporte. O valor é 0 porque este é um fluxo ICMP.|
|PROTOCOLO IP|1|Isso identifica o serviço da Camada 4, normalmente 1 para ICMP, 6 para TCP e 17 para UDP.|
|timestamp primeiro|00:47:49.593|Este é o carimbo de data/hora para o início do fluxo.|
|carimbo de data/hora|00:47:52.598|Este é o carimbo de data/hora do último pacote no fluxo.|
|flags TCP|0x00|Este é o valor do flag TCP. Nesse caso, nenhuma sessão TCP foi envolvida porque o protocolo é ICMP.|
|contador de bytes|512|Este é o número de bytes no fluxo.|
|contador de pacotes|4|Este é o número de pacotes no fluxo.|
|entrada da interface|Gig0/0|Esta é a interface do Flow exporter que coletou o fluxo na direção de entrada (na interface do dispositivo de monitoramento).|
|saída da interface|Null|Esta é a interface do Flow exporter que coletou o fluxo na direção de saída (fora da interface do dispositivo de monitoramento). O valor é “Nulo” porque este era um ping para a interface de entrada.|

Linha em branco, sem informações adicionais

Nesse caso, o fluxo representa o ping ICMP do host 10.0.0.10 para 10.0.0.1. Quatro pacotes de ping estavam no fluxo. Os pacotes inseridos na interface G0/0 do exportador.

**Nota**: Nesta atividade, o roteador Edge foi configurado como um flow exporter do NetFlow. A interface LAN é configurada para monitorar fluxos que entram na rede local. A interface serial foi configurada para coletar fluxos que entram na internet. Isso foi feito para simplificar esta atividade.

Para ver o tráfego que corresponde a uma sessão bidirecional completa, o NetFlow Flow exporter precisaria ser configurado para coletar fluxos que entram e saem de uma rede.

#### Etapa 3: Criar tráfego adicional.

a. Clique **PC-2 > Desktop**.

b. Abra um prompt de comando e **ping** o default gateway 10.0.0.1.

##### Pergunta:

O que você espera ver nos registros de fluxo do NetFlow collector? As estatísticas do registro de fluxo existente serão alteradas ou um novo fluxo aparecerá no gráfico de pizza?

Um fluxo é definido como um fluxo unidirecional de pacotes que compartilham os mesmos endereços IP de origem e destino e números de porta, bem como o mesmo protocolo IP. Como esse tráfego terá um endereço IP de origem diferente, ele criará um novo registro de fluxo representado por uma nova parte codificada por cores do gráfico de pizza.

c. Retorne ao PC-1 e repita o ping para o gateway.

##### Pergunta:

Como esse tráfego será representado? Como um novo segmento no gráfico de pizza ou ele modificará os valores no registro de fluxo existente?

 
Os detalhes do fluxo original permanecem os mesmos, no entanto, a proporção de tráfego representada pelo fluxo duplicou.

d. Emita pings de PC-3 e PC-4 para o endereço de gateway padrão.

O que deve acontecer com a tela no coletor de fluxo?
 
Um novo registro deve aparecer para cada fluxo.

### Parte 2: Observe os registros do NetFlow para uma sessão que entra e sai do coletor

O NetFlow exporter foi configurado para coletar fluxos que saem da LAN e entram no roteador da Internet.

#### Etapa 1: Acessar o servidor Web por endereço IP.

Antes de continuar, desligue e ligue o NetFlow collector para limpar os fluxos.

a. Clique na guia **NetFlow Collector > Physical** .

b. Clique no botão de energia vermelho para desligar o servidor. Em seguida, clique nele novamente para ligar o servidor novamente. (**Nota**: Pode ser necessário rolar ou diminuir o zoom.)

c. No NetFlow Collector, clique na guia **Desktop** .

d. Clique no ícone Netflow Collector. Clique no botão de opção “On” para ativar o coletor. Feche a janela NetFlow Collector.

e. Antes de acessar um servidor web do PC-1, preveja quantos fluxos haverá no gráfico de pizza? Explique.

Como os fluxos que saem da LAN e entram no roteador de borda de fora serão coletados, haverá dois fluxos, um para os pacotes de solicitação enviados ao servidor e um para os dados retornados do servidor.

A partir do seu conhecimento de protocolos de rede e NetFlow, preveja os valores para as solicitações de página da Web que saem da LAN.

|Campo de registro|Valor|Diretrizes|
|---|---|---|
|Endereço IP de origem| |N/D|
|Endereço IP de destino| |N/D|
|Porta de origem|1025—5000 (padrão do MS Windows, que é o que o PT usa.|Este é um valor aproximado que é criado dinamicamente.|
|Porta de destino| |N/D|
|Interface de entrada| |N/D|
|Interface de saída| |N/D|

Linha em branco, sem informações adicionais

Clique em **Mostrar resposta** em uma tabela de respostas de amostra.

|Campo de registro|Valor|Diretrizes|
|---|---|---|
|Endereço IP de origem|10.0.0.10|N/D|
|Endereço IP de destino|192.0.2.100|N/D|
|Porta de origem|1025—5000 (padrão do MS Windows, que é o que o PT usa.|Este é um valor aproximado que é criado dinamicamente.|
|Porta de destino|80|N/D|
|Interface de entrada|Gig0/0|N/D|
|Interface de saída|Se0/0/1|N/D|

 

Linha em branco, sem informações adicionais

Preveja os valores para a resposta da página da Web que entra no roteador do exportador NetFlow a partir da Internet.

|Campo de registro|Valor|Diretrizes|
|---|---|---|
|Endereço IP de origem| |N/D|
|Endereço IP de destino| |N/D|
|Porta de origem| |N/D|
|Porta de destino|1025-5000|Este é o valor que foi atribuído aleatoriamente a partir do intervalo de portas efêmeras.|
|Interface de entrada| |N/D|
|Interface de saída| |N/D|

Linha em branco, sem informações adicionais

Clique em **Mostrar resposta** em uma tabela de respostas de amostra.

|Campo de registro|Valor|Diretrizes|
|---|---|---|
|Endereço IP de origem|192.0.2.100|N/D|
|Endereço IP de destino|10.0.0.10|N/D|
|Porta de origem|80|N/D|
|Porta de destino|1025-5000|Este é o valor que foi atribuído aleatoriamente a partir do intervalo de portas efêmeras.|
|Interface de entrada|Se0/0/1|N/D|
|Interface de saída|Gig0/0|N/D|


Linha em branco, sem informações adicionais

f. Clique **PC-1 > Desktop**. Feche a janela do prompt de comando, se necessário. Clique no ícone do navegador da web.

g. No navegador da Web para PC-1, digite 192.0.2.100 e clique em**Go**. A página da Web do site de exemplo será exibida.

h. Após um breve atraso, um novo gráfico de pizza aparecerá no coletor NetFlow. Você verá pelo menos dois segmentos de pizza para a solicitação HTTP e resposta. Talvez você veja um terceiro segmento se o cache ARP para PC-1 expirou.

i. Clique em cada segmento de pizza HTTP para exibir o registro e verificar suas previsões.

j. Clique no link para a página de direitos autorais.

##### Perguntas:

O que aconteceu? Explique. (Dica: compare o número da porta no host para os fluxos.

Como o host abriu uma nova porta de origem para a nova solicitação para o servidor Web, dois novos fluxos foram criados.

Compare os fluxos. Além do carimbo de data/hora óbvio, endereço IP de origem e destino, porta e interfaces, diferenças, o que mais é diferente entre os fluxos de solicitação e resposta?

Os flags TCP são diferentes. Os flags para os fluxos de solicitação são 0x02 e os sinalizadores de resposta são 0x12. Direcione os alunos a procurar esses valores fazendo uma pesquisa no Google em termos como “valores para os flags tcp”. Está além do escopo deste laboratório explicar como os valores são determinados, mas o significado de 0x02 será SYN (decimal 2) para o fluxo de solicitação e será SYN-ACK (decimal 18) para os fluxos de resposta.

#### Etapa 2: Acessar o servidor Web por URL.

a. Desligue e ligue o NetFlow collector para limpar os fluxos.

b. Ative o serviço Netflow Collector.

c. Antes de acessar o servidor Web por seu URL.

##### Pergunta:

O que você acha que verá na exibição do NetFlow collector?

Você verá quatro fluxos. Como o site é acessado por URL, uma consulta DNS deve ocorrer. Dois fluxos representam a consulta DNS e a resposta. Os outros dois fluxos representam a solicitação HTTP e a resposta.

d. No PC-1, entre **www.example.com** no campo URL e pressione **Go**.

e. Depois que os fluxos forem exibidos, inspecione cada registro de fluxo.

##### Pergunta:

Quais valores você vê para o campo de protocolo IP do registro de fluxo? O que significam esses valores?

Os campos de protocolo IP foram discutidos na tabela na Parte 1, Passo 1 deste laboratório. O valor 6 é para TCP e é usado para o tráfego HTTP na porta TCP 80. O valor 17 é para tráfego UDP e é usado pelos fluxos de consulta e resposta DNS.

# Packet Tracer - Implementar segurança física com dispositivos de IoT


## Objetivos

Parte 1, Conexão dos dispositivos de IoT à rede

Parte 2: Adicionar dispositivos de IoT ao servidor de registro

Parte 3: Explore a funcionalidade dos dispositivos de segurança da IoT

## Histórico/Cenário

Na tentativa de aumentar a segurança física da sua casa, você decidiu instalar alguns dispositivos da Internet das Coisas (IoT) para permitir que você monitore sua casa remotamente enquanto estiver ausente. Nesta atividade do Packet Tracer, você instalará um dispositivo de IoT para melhorar a segurança em casa. Em seguida, você configurará todos os dispositivos de IoT para se conectarem à rede sem fio e se comunicarem com um servidor de registro de IoT remoto.

## Instruções

### Parte 1: Conexão de dispositivos de IoT à rede

Nesta parte, você conectará dispositivos de IoT à rede sem fio e implementará a filtragem de endereço MAC.

#### Etapa 1: Conectar a sirene à porta

a. Clique em **Home** (Lar) e localize Home_Siren and Home Door (Portas do lar e sirenes) na sala de estar.

b. Na barra de ferramentas na parte inferior, clique em **Conexões**> **Cabo personalizado da IoT**, que é a penúltima opção.

c. Clique em Home_Siren> Interface **DO** e clique em Portas residenciais> Interface **DO**.

d. Mantenha a tecla **ALT** pressionada e clique na porta para abrir e fechá-la. Observe que abrir a porta ativará a sirene.

#### Etapa 2: Associar todos os dispositivos de IoT à rede sem fio HomeNet.

O **Roteador sem fio doméstico** é pré-configurado para usar a filtragem de endereço WPA2-PSK e MAC para controlar quem pode se associar à rede e quais dispositivos podem usar a rede para transferir tráfego. Todos os novos dispositivos devem estar em conformidade com a configuração atual.

a. Localize os quatro dispositivos sem fio da IoT:

- Home_Siren

- Portas residenciais

- Home_Motion_Sensor (janelas do home office)

- Home_Webcam (estante do home office)

b. Clique em Home_Siren e, em seguida, na guia **Config** > **Wireless0**.

c. Configure o **SSID** e o modo de **autenticação**

- SSID: HomeNet

- Autenticação: **WPA2-PSK**

- Senha: ciscorocks

d. Em **Configuração de IP**, clique em **DHCP**. Verifique se o dispositivo recebeu um endereço IP da rede 192.168.0.0/24.

**Observação**: pode ser necessário alternar entre **estático** e **DHCP** para forçar o Packet Tracer a convergir em suas configurações.

e. Registre o endereço MAC do dispositivo de IoT. Formate os endereços com dois pontos entre cada dois números hexadecimais em vez de um período entre cada quatro números hexadecimais. Esse formato é necessário para a próxima etapa, quando você aplicará a filtragem de endereço MAC.

##### Perguntas:

Home_Siren


Portas residenciais


Home_Motion_Sensor


Home_Webcam


f. Repita essas etapas para cada dispositivo de IoT.

#### Etapa 3: Configurar a filtragem de endereço MAC para permitir os dispositivos de IoT.

a. Clique home office PC > **aba Desktop** > **Navegador da Web**.

b. Faça login no Roteador sem fio doméstico em 192.168.0.1. Use **admin** como nome de usuário e senha.

c. Clique em Roteador sem fio doméstico> **guia GUI**.

d. Clique em **Wireless** e, em seguida, **Wireless MAC Filter**.

e. Verifique se o filtro está habilitado para a porta sem fio de 2,4 GHz e se está definido para permitir que computadores acessem a rede sem fio.

f. Adicione os quatro endereços MAC do dispositivo de IoT à tabela.

g. Role até a parte inferior e clique em **Salvar configurações**.

h. O Roteador sem fio doméstico será reiniciado. Feche o **navegador da Web** e clique em **Configuração de IP**. Se necessário, alterne os botões **DHCP** e **Estático** para renovar a configuração IP para que o Home Office PC tenha um endereço IP da rede 192.168.0.0/24.

### Parte 2: Adicionar dispositivos de IoT ao servidor de registro

Nesta parte, você se inscreverá em uma conta com um serviço de monitoramento remoto de IoT. Em seguida, você registrará os dispositivos de IoT para se comunicar com o serviço. Isso permitirá que você monitore remotamente os dispositivos de IoT por meio de um portal da Web.

#### Etapa 1: Criar uma conta no ISP IoT Registration Server.

a. No Home Office PC, feche a **Configuração de IP** e clique em **Navegador da Web**.

b. Navegue até **http://10.3.0.125**.

c. Clique em **Inscreva-se agora** e crie uma nova conta com o nome de usuário HomeUser e a senha Pa$$w0rd.

### Etapa 2: Registrar cada dispositivo de IoT no servidor de registro

Cada um dos quatro dispositivos de IoT deve ser registrado com um servidor de registro para monitorar e gerenciar o dispositivo remotamente. Repita as etapas a seguir para cada dispositivo de IoT.

a. Clique na guia Dispositivo> **Configuração** > **Configurações** em **GLOBAL**.

b. Role até a **seção IoT** na parte inferior da página e insira as seguintes informações:

o Selecione **Servidor remoto**

o Endereço do servidor: **10.3.0.125**

o Nome do usuário: HomeUser

o Senha: Pa$$w0rd

c. Clique no botão **Conectar**. O botão mudará para **Conectando** e depois para A**tualizar** em alguns segundos. O dispositivo de IoT agora está registrado com o servidor.

**Observação**: caso não seja alterado para **Atualizar**, é possível que as informações estejam incorretas. Portanto, insira novamente as informações e repita esta etapa.

d. Repita as etapas acima para registrar todos os dispositivos de IoT.

#### Etapa 3: Verificar se todos os dispositivos estão registrados.

a. Volte para o **Navegador da Web** no PC do Home Office. Se necessário, navegue até 10.3.0.125 e faça login com o nome de usuário HomeUser e a senha Pa$word

b. Verifique se todos os quatro dispositivos de IoT estão registrados no servidor.

Abrir a janela de configuração

### Parte 3: Explore a funcionalidade dos dispositivos de segurança da IoT

Nesta parte, você vai explorar a funcionalidade dos dispositivos de IoT e monitorar seus estados no servidor de registro de IoT.

#### Etapa 1: Observar e controlar os dispositivos de IoT no servidor de registro.

a. No **Navegador da Web** no PC do Home Office, clique em cada seção de cada dispositivo de IoT para exibir os detalhes do dispositivo.

##### Pergunta:

Qual é o status de cada dispositivo?





b. Clique no retângulo vermelho em Home Doors para ativá-lo.

##### Pergunta:

O que aconteceu?



c. Clique no retângulo da porta novamente para desativar o dispositivo.

##### Pergunta:

O que aconteceu?

d. Clique no retângulo verde da Home_Webcam.

##### Pergunta:

O que aconteceu?

e. Clique no retângulo verde novamente para ligar a Home_Webcam.

f. Clique no círculo vermelho de Home_Motion_Sensor. Nada vai acontecer porque o sensor de movimento só envia informações para o servidor de registro. Este é um exemplo de dispositivo que pode ser monitorado apenas.

#### Etapa 2: Interagir com os sensores em casa.

No Packet Tracer, os dispositivos de IoT normalmente podem ser ativados mantendo a tecla ALT pressionada e clicando no dispositivo (clique ALT). O sensor de movimento é ativado pressionando a tecla ALT e movendo o mouse sobre o sensor. Tenha a tela do servidor de registro de IoT visível para essas ações.

a. ATL-clique na porta.

##### Pergunta:

O que aconteceu?


b. ALT-Clique na webcam.

##### Pergunta:

O que aconteceu?

c. Pressione a tecla ALT e mova o mouse sobre o sensor de movimento.

##### Pergunta:

O que aconteceu?

## Questões para Reflexão

1. Quais vantagens os dispositivos habilitados para IoT oferecem para segurança em casa?


2. Qual é a vantagem de usar um servidor de registro para dispositivos habilitados para IoT?


3. Pesquisar na Internet para descobrir que tipos de dispositivos habilitados para IoT são usados para segurança em casa?



# Packet Tracer - Configurar o fortalecimento e a segurança do roteador sem fio


## Objetivos

Parte 1: Configuração das definições básicas em um roteador sem fio

Parte 2: Configurar a segurança de rede do roteador sem fio

Parte 3: Configurar a segurança de rede de clientes sem fio

Parte 4: Verificar as configurações de conectividade e segurança

## Histórico/Cenário

Nesta atividade do Packet Tracer, você configurará segurança um roteador sem fio. Durante a instalação do roteador, ele foi parcialmente configurado, mas tem alguns problemas de segurança que precisam ser resolvidos. Você também protegerá o roteador para ajudar a mitigar possíveis ataques. Após a conclusão da configuração de segurança, você verificará as configurações de conectividade e segurança.

**Observação**: a maioria das tarefas nesta atividade é classificada. Clique em **Verificar resultados** a qualquer momento para ver os **Itens de avaliação** corretos e incorretos.

**Observação**: a mudança para o modo **lógico** está desativada nesta atividade. Além disso, os **data centers** e locais de **ISP / Telco** estão bloqueados.

## Instruções

### Parte 1: Configuração das definições básicas em um roteador sem fio

As configurações iniciais de um roteador sem fio doméstico podem representar um risco à segurança. Por exemplo, se os agentes de ameaças conhecem o seu endereço IP público, eles podem pesquisar na Internet as credenciais de login padrão do roteador e acessar remotamente o roteador. Nesta parte, você vai alterar a senha do roteador e desativar o login remoto.

#### Etapa 1: A primeira etapa é alterar a senha padrão do roteador .

É importante definir uma senha muito forte ou uma frase longa para impedir que usuários não autorizados alterem as configurações do roteador.

a. Clique em Home Office PC> aba Desktop > **Navegador da Web** .

b. Faça login no Roteador sem fio doméstico em **192.168.0.1**.

c. Use **admin** para nome do usuário e senha.

d. Clique na guia **Administração** e insira cisconetacadrocks! para os dois campos de senha.

e. Role até a parte inferior e clique em **Salvar configurações**.

f.  O roteador solicita que você autentique novamente. Faça login novamente com o nome de usuário **admin** e a nova senha e clique em **Continuar**.

#### Etapa 2 Desativar gerenciamento remoto.

Roteadores sem fio domésticos normalmente são enviados com a configuração remota ativada. Isso permite que os técnicos da operadora acessem o dispositivo para ajudar a configurar a rede doméstica ou solucionar problemas. No entanto, isso pode ser um risco à segurança, porque uma porta deve estar aberta e em escuta para que o técnico se conecte ao roteador. Muitas vezes, é possível alterar a porta e permitir apenas o acesso HTTPS, mas isso não oferece nenhuma medida real de segurança porque um agente de ameaça pode detectar portas abertas e iniciar um ataque de senha contra o roteador. Se o gerenciamento remoto for realmente necessário, seria muito mais seguro configurar uma solução VPN. O Roteador sem fio doméstico nessa atividade do Packet Tracer não é compatível com VPN. Portanto, você desativará o gerenciamento remoto.

a. Na guia **Administração**, clique em **Desativado** ao lado de **Gerenciamento remoto** **.**

b. Clique em **Salvar configurações**.

**Observação**: essa alteração fará com que o roteador sem fio doméstico seja redefinido. Feche o **navegador da Web** e clique **em Fast Forward** (Alt + D). Retorne ao **PC do Home Office** e clique em **Configuração de IP** para verificar se o endereçamento IP foi reatribuído. Se necessário, alterne entre **DHCP** e **Estático** até que o **PC do Home Office** receba o endereçamento IP da rede 192.168.0.1/24. Feche a janela **IP Configuration(Configuração de IP** ) eentão clique em **Web Browser (Navegador Web)**. Navegue até **192.168.0.1** e faça a nova autenticação novamente, preparando-se para a próxima parte da atividade.

### Parte 2: Configurar a segurança de rede do roteador sem fio

No momento, qualquer pessoa que tenha um dispositivo sem fio ao alcance do Roteador sem fio doméstico pode se conectar facilmente e, possivelmente, acessar dispositivos na rede. Para evitar que isso aconteça, nesta parte, você protegerá as redes sem fio para que apenas os dispositivos com a configuração correta consigam se conectar às redes.

#### Etapa 1: Configurar e transmitir o HomeNet SSID.

Atualmente, o roteador não está transmitindo o SSID das redes configuradas. Essa não é uma medida de segurança geralmente aceita, principalmente porque, se um agente de ameaças estivesse procurando uma rede para atacar, ainda veria a rede sem nome. Há ferramentas disponíveis para detectar o tráfego para determinar o SSID. Na verdade, a prática de desativar a transmissão SSID pode potencialmente tornar a rede um alvo mais alto para o ataque, porque o administrador está tentando ocultá-la.

a. Clique na guia **Sem fio** e, em cada uma das três redes, clique em **Habilitado** para **transmissão SSID**.

b. Para cada uma das três redes, altere o SSID do **padrão** para HomeNet.

c. Clique em **Salvar configurações**.

#### Etapa 2: Configurar a segurança para as redes sem fio HomeNet.

Talvez a medida de segurança mais importante fora da alteração da senha do roteador seja a criptografia do tráfego entre o roteador e os clientes sem fio. Sem criptografia, um agente de ameaça pode usar ferramentas fáceis de obter e muitas vezes gratuitas para interceptar comunicações com muito pouco esforço. Isso pode gerar mais ataques à medida que o agente de ameaças obtém conhecimento sobre você e suas redes.

a. Guia **Rede sem fio** - **Segurança da rede sem fio**

b. Para cada uma das três redes, configure o seguinte:

o Security Mode: **WPA2 Personal**

o Encryption: **AES**

o Passphrase: **ciscorocks**

c. Clique em **Salvar configurações**.

#### Etapa 3: Configurar a segurança para a rede sem fio GuestNet.

Esse roteador permite que duas redes sem fio independentes sejam configuradas para cada rádio. Isso pode ser útil quando você deseja manter o tráfego de convidados separado do tráfego nas outras redes.

a. Na guia **Sem fio**, clique em **Rede Guest.**

b. Para cada uma das três redes, clique em **Habilitar perfil do convidado** e, em seguida, configure o seguinte:

o SSID: GuestNet

o Broadcast SSID: **Enabled**

o Security Mode: **WPA2 Personal**

o Encryption: **AES**

o Passphrase: guestpass

c. Clique em **Salvar configurações**.

### Parte 3: Configurar a segurança de rede de clientes sem fio

O roteador sem fio doméstico foi reforçado e a segurança sem fio foi configurada. Nesta parte, você conectará com segurança clientes sem fio à rede.

#### Etapa 1: Configurar a conectividade sem fio para os laptops.

a. Clique em Laptop doméstico 1 localizado na sala de estar e clique na guia **Desktop**> **PC Wireless**.

b. Clique na guia **Connect**.

c. Clique na primeira entrada da HomeNet e clique em **Conectar**.

d. A segurança já está definida como **WPA2-Personal**. Digite Cisco123! No campo **chave pré-compartilhada** e clique em **Connect**.

e. Clique na guia **Link Information**. Você verá uma mensagem que confirma que você se conectou com sucesso ao ponto de acesso. Se você ainda não estiver conectado, verifique a configuração do Roteador sem fio doméstico e tente novamente.

f.  Feche **PC Wireless** window and click **IP Configuration**. Se o laptop ainda tiver um endereço da rede "169", alterne entre **DHCP** e Estático até receber o endereçamento IP da rede 192.168.0.0/24.

g. Repita esta etapa para o Laptop doméstico 2 no home office, mas use a primeira entrada para GuestNet. escreva **guestpass** como pre **-shared key**.

#### Etapa 2: Configurar a conectividade sem fio para dispositivos IOT.

a. No home office, na prateleira superior da estante, clique em Home_Webcam

b. Clique **Config** > **Wireless0**.

c. Insira a HomeNet como **SSID**.

d. Escolha **WPA2-PSK** para **Autenticação** e digite ciscorocks para a senha **PSK**.

e. Em **Configuração de IP**, clique em **DHCP** e verifique se o dispositivo recebeu endereçamento IP da rede 192.168.0.0/24. Alterne entre **DHCP** e **Estático**, se necessário.

f.  Repita esta etapa para o Home_Siren, localizado na sala de estar acima da estante, e o **Home Door**.

### Parte 4: Verificar as configurações de conectividade e segurança

Nesta parte, você testará suas configurações e segurança para garantir que os dispositivos estejam se comunicando entre si e que consigam acessar a Internet.

#### Etapa 1: Testar a conectividade da Internet para notebooks sem fio.

a. Clique Home Laptop 1 > **Desktop** tab > **Web Browser**.

b. Acesse www.ptsecurity.com. O Packet Tracer pode levar alguns segundos para convergir. Você pode clicar em **Fast Forward** para acelerar o processo até a **página pública do Data Center** carregar.

c. Repita esta etapa para o Laptop doméstico 2.

#### Etapa 2: Configurar a segurança para a interconectividade GuestNet e HomeNet.

Normalmente, a **GuestNet** e a HomeNet não devem conseguir se conectar ou compartilhar recursos. Lembre-se de que o laptop doméstico 2 está configurado para a rede de convidado e normalmente não deve ter acesso aos dispositivos na rede doméstica.

a. Use o método que você deseja determinar para o endereço IP do laptop doméstico 1.

b. Clique em Home Laptop na guia Desktop > **Command** Prompt( **Prompt de comando).**

c. Insira o comando **ping** seguido pelo endereço IP do laptop doméstico 1.

O laptop doméstico 1 responde aos pings, indicando que o laptop doméstico 2 pode acessar dispositivos na rede doméstica. Você precisará configurar o roteador para impedir que hosts em redes diferentes se comuniquem entre si.

d. Do **PC Home Office**, se necessário, faça login novamente na página da Web de configuração do Roteador sem fio doméstico em 192.168.0.1.

e. Clique na guia **Sem fio** e, em seguida, no submenu **Rede de convidados**.

f.  Desmarque a caixa ao lado de **Permitir que os convidados se encontrem e acessem a rede local** e clique em **Salvar configurações**.

g. Do Laptop doméstico 2, tente executar ping no Laptop doméstico 1 novamente. O ping devem falhar. Isso indica que os hosts não têm permissão para se comunicar entre as duas redes.