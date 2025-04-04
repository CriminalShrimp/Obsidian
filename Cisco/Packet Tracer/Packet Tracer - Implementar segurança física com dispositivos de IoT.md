
# Objetivos

Parte 1, Conexão dos dispositivos de IoT à rede

Parte 2: Adicionar dispositivos de IoT ao servidor de registro

Parte 3: Explore a funcionalidade dos dispositivos de segurança da IoT

# Histórico/Cenário

Na tentativa de aumentar a segurança física da sua casa, você decidiu instalar alguns dispositivos da Internet das Coisas (IoT) para permitir que você monitore sua casa remotamente enquanto estiver ausente. Nesta atividade do Packet Tracer, você instalará um dispositivo de IoT para melhorar a segurança em casa. Em seguida, você configurará todos os dispositivos de IoT para se conectarem à rede sem fio e se comunicarem com um servidor de registro de IoT remoto.

# Instruções

## Parte 1: Conexão de dispositivos de IoT à rede

Nesta parte, você conectará dispositivos de IoT à rede sem fio e implementará a filtragem de endereço MAC.

### Etapa 1: Conectar a sirene à porta

a. Clique em **Home** (Lar) e localize Home_Siren and Home Door (Portas do lar e sirenes) na sala de estar.

b. Na barra de ferramentas na parte inferior, clique em **Conexões**> **Cabo personalizado da IoT**, que é a penúltima opção.

c. Clique em Home_Siren> Interface **DO** e clique em Portas residenciais> Interface **DO**.

d. Mantenha a tecla **ALT** pressionada e clique na porta para abrir e fechá-la. Observe que abrir a porta ativará a sirene.

### Etapa 2: Associar todos os dispositivos de IoT à rede sem fio HomeNet.

O **Roteador sem fio doméstico** é pré-configurado para usar a filtragem de endereço WPA2-PSK e MAC para controlar quem pode se associar à rede e quais dispositivos podem usar a rede para transferir tráfego. Todos os novos dispositivos devem estar em conformidade com a configuração atual.

a. Localize os quatro dispositivos sem fio da IoT:

o Home_Siren

o Portas residenciais

o Home_Motion_Sensor (janelas do home office)

o Home_Webcam (estante do home office)

b. Clique em Home_Siren e, em seguida, na guia **Config** > **Wireless0**.

c. Configure o **SSID** e o modo de **autenticação**

o SSID: HomeNet

o Autenticação: **WPA2-PSK**

o Senha: ciscorocks

d. Em **Configuração de IP**, clique em **DHCP**. Verifique se o dispositivo recebeu um endereço IP da rede 192.168.0.0/24.

**Observação**: pode ser necessário alternar entre **estático** e **DHCP** para forçar o Packet Tracer a convergir em suas configurações.

e. Registre o endereço MAC do dispositivo de IoT. Formate os endereços com dois pontos entre cada dois números hexadecimais em vez de um período entre cada quatro números hexadecimais. Esse formato é necessário para a próxima etapa, quando você aplicará a filtragem de endereço MAC.

#### Perguntas:

o Home_Siren

Área de Resposta

Mostrar resposta

o Portas residenciais

Área de Resposta

Mostrar resposta

o Home_Motion_Sensor

Área de Resposta

Mostrar resposta

o Home_Webcam

Área de Resposta

Mostrar resposta

f. Repita essas etapas para cada dispositivo de IoT.

### Etapa 3: Configurar a filtragem de endereço MAC para permitir os dispositivos de IoT.

a. Clique home office PC > **aba Desktop** > **Navegador da Web**.

b. Faça login no Roteador sem fio doméstico em 192.168.0.1. Use **admin** como nome de usuário e senha.

c. Clique em Roteador sem fio doméstico> **guia GUI**.

d. Clique em **Wireless** e, em seguida, **Wireless MAC Filter**.

e. Verifique se o filtro está habilitado para a porta sem fio de 2,4 GHz e se está definido para permitir que computadores acessem a rede sem fio.

f. Adicione os quatro endereços MAC do dispositivo de IoT à tabela.

g. Role até a parte inferior e clique em **Salvar configurações**.

h. O Roteador sem fio doméstico será reiniciado. Feche o **navegador da Web** e clique em **Configuração de IP**. Se necessário, alterne os botões **DHCP** e **Estático** para renovar a configuração IP para que o Home Office PC tenha um endereço IP da rede 192.168.0.0/24.

## Parte 2: Adicionar dispositivos de IoT ao servidor de registro

Nesta parte, você se inscreverá em uma conta com um serviço de monitoramento remoto de IoT. Em seguida, você registrará os dispositivos de IoT para se comunicar com o serviço. Isso permitirá que você monitore remotamente os dispositivos de IoT por meio de um portal da Web.

### Etapa 1: Criar uma conta no ISP IoT Registration Server.

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

### Etapa 3: Verificar se todos os dispositivos estão registrados.

a. Volte para o **Navegador da Web** no PC do Home Office. Se necessário, navegue até 10.3.0.125 e faça login com o nome de usuário HomeUser e a senha Pa$$w0rd.

b. Verifique se todos os quatro dispositivos de IoT estão registrados no servidor.

Abrir a janela de configuração

## Parte 3: Explore a funcionalidade dos dispositivos de segurança da IoT

Nesta parte, você vai explorar a funcionalidade dos dispositivos de IoT e monitorar seus estados no servidor de registro de IoT.

### Etapa 1: Observar e controlar os dispositivos de IoT no servidor de registro.

a. No **Navegador da Web** no PC do Home Office, clique em cada seção de cada dispositivo de IoT para exibir os detalhes do dispositivo.

#### Pergunta:

Qual é o status de cada dispositivo?

Área de Resposta

Mostrar resposta

b. Clique no retângulo vermelho em Home Doors para ativá-lo.

#### Pergunta:

O que aconteceu?

Área de Resposta

Mostrar resposta

c. Clique no retângulo da porta novamente para desativar o dispositivo.

#### Pergunta:

O que aconteceu?

Área de Resposta

Mostrar resposta

d. Clique no retângulo verde da Home_Webcam.

#### Pergunta:

O que aconteceu?

Área de Resposta

Mostrar resposta

e. Clique no retângulo verde novamente para ligar a Home_Webcam.

f. Clique no círculo vermelho de Home_Motion_Sensor. Nada vai acontecer porque o sensor de movimento só envia informações para o servidor de registro. Este é um exemplo de dispositivo que pode ser monitorado apenas.

### Etapa 2: Interagir com os sensores em casa.

No Packet Tracer, os dispositivos de IoT normalmente podem ser ativados mantendo a tecla ALT pressionada e clicando no dispositivo (clique ALT). O sensor de movimento é ativado pressionando a tecla ALT e movendo o mouse sobre o sensor. Tenha a tela do servidor de registro de IoT visível para essas ações.

a. ATL-clique na porta.

#### Pergunta:

O que aconteceu?

Área de Resposta

Mostrar resposta

b. ALT-Clique na webcam.

#### Pergunta:

O que aconteceu?

Área de Resposta

Mostrar resposta

c. Pressione a tecla ALT e mova o mouse sobre o sensor de movimento.

#### Pergunta:

O que aconteceu?

Área de Resposta

Mostrar resposta

# Questões para Reflexão

1. Quais vantagens os dispositivos habilitados para IoT oferecem para segurança em casa?

Área de Resposta

Mostrar resposta

2. Qual é a vantagem de usar um servidor de registro para dispositivos habilitados para IoT?

Área de Resposta

Mostrar resposta

3. Pesquisar na Internet para descobrir que tipos de dispositivos habilitados para IoT são usados para segurança em casa?

Área de Resposta

Mostrar resposta

