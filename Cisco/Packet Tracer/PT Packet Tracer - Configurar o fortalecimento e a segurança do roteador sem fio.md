
# Objetivos

Parte 1: Configuração das definições básicas em um roteador sem fio

Parte 2: Configurar a segurança de rede do roteador sem fio

Parte 3: Configurar a segurança de rede de clientes sem fio

Parte 4: Verificar as configurações de conectividade e segurança

# Histórico/Cenário

Nesta atividade do Packet Tracer, você configurará segurança um roteador sem fio. Durante a instalação do roteador, ele foi parcialmente configurado, mas tem alguns problemas de segurança que precisam ser resolvidos. Você também protegerá o roteador para ajudar a mitigar possíveis ataques. Após a conclusão da configuração de segurança, você verificará as configurações de conectividade e segurança.

**Observação**: a maioria das tarefas nesta atividade é classificada. Clique em **Verificar resultados** a qualquer momento para ver os **Itens de avaliação** corretos e incorretos.

**Observação**: a mudança para o modo **lógico** está desativada nesta atividade. Além disso, os **data centers** e locais de **ISP / Telco** estão bloqueados.

# Instruções

## Parte 1: Configuração das definições básicas em um roteador sem fio

As configurações iniciais de um roteador sem fio doméstico podem representar um risco à segurança. Por exemplo, se os agentes de ameaças conhecem o seu endereço IP público, eles podem pesquisar na Internet as credenciais de login padrão do roteador e acessar remotamente o roteador. Nesta parte, você vai alterar a senha do roteador e desativar o login remoto.

### Etapa 1: A primeira etapa é alterar a senha padrão do roteador .

É importante definir uma senha muito forte ou uma frase longa para impedir que usuários não autorizados alterem as configurações do roteador.

a. Clique em Home Office PC> aba Desktop > **Navegador da Web** .

b. Faça login no Roteador sem fio doméstico em **192.168.0.1**.

c. Use **admin** para nome do usuário e senha.

d. Clique na guia **Administração** e insira cisconetacadrocks! para os dois campos de senha.

e. Role até a parte inferior e clique em **Salvar configurações**.

f.  O roteador solicita que você autentique novamente. Faça login novamente com o nome de usuário **admin** e a nova senha e clique em **Continuar**.

### Etapa 2 Desativar gerenciamento remoto.

Roteadores sem fio domésticos normalmente são enviados com a configuração remota ativada. Isso permite que os técnicos da operadora acessem o dispositivo para ajudar a configurar a rede doméstica ou solucionar problemas. No entanto, isso pode ser um risco à segurança, porque uma porta deve estar aberta e em escuta para que o técnico se conecte ao roteador. Muitas vezes, é possível alterar a porta e permitir apenas o acesso HTTPS, mas isso não oferece nenhuma medida real de segurança porque um agente de ameaça pode detectar portas abertas e iniciar um ataque de senha contra o roteador. Se o gerenciamento remoto for realmente necessário, seria muito mais seguro configurar uma solução VPN. O Roteador sem fio doméstico nessa atividade do Packet Tracer não é compatível com VPN. Portanto, você desativará o gerenciamento remoto.

a. Na guia **Administração**, clique em **Desativado** ao lado de **Gerenciamento remoto** **.**

b. Clique em **Salvar configurações**.

**Observação**: essa alteração fará com que o roteador sem fio doméstico seja redefinido. Feche o **navegador da Web** e clique **em Fast Forward** (Alt + D). Retorne ao **PC do Home Office** e clique em **Configuração de IP** para verificar se o endereçamento IP foi reatribuído. Se necessário, alterne entre **DHCP** e **Estático** até que o **PC do Home Office** receba o endereçamento IP da rede 192.168.0.1/24. Feche a janela **IP Configuration(Configuração de IP** ) eentão clique em **Web Browser (Navegador Web)**. Navegue até **192.168.0.1** e faça a nova autenticação novamente, preparando-se para a próxima parte da atividade.

## Parte 2: Configurar a segurança de rede do roteador sem fio

No momento, qualquer pessoa que tenha um dispositivo sem fio ao alcance do Roteador sem fio doméstico pode se conectar facilmente e, possivelmente, acessar dispositivos na rede. Para evitar que isso aconteça, nesta parte, você protegerá as redes sem fio para que apenas os dispositivos com a configuração correta consigam se conectar às redes.

### Etapa 1: Configurar e transmitir o HomeNet SSID.

Atualmente, o roteador não está transmitindo o SSID das redes configuradas. Essa não é uma medida de segurança geralmente aceita, principalmente porque, se um agente de ameaças estivesse procurando uma rede para atacar, ainda veria a rede sem nome. Há ferramentas disponíveis para detectar o tráfego para determinar o SSID. Na verdade, a prática de desativar a transmissão SSID pode potencialmente tornar a rede um alvo mais alto para o ataque, porque o administrador está tentando ocultá-la.

a. Clique na guia **Sem fio** e, em cada uma das três redes, clique em **Habilitado** para **transmissão SSID**.

b. Para cada uma das três redes, altere o SSID do **padrão** para HomeNet.

c. Clique em **Salvar configurações**.

### Etapa 2: Configurar a segurança para as redes sem fio HomeNet.

Talvez a medida de segurança mais importante fora da alteração da senha do roteador seja a criptografia do tráfego entre o roteador e os clientes sem fio. Sem criptografia, um agente de ameaça pode usar ferramentas fáceis de obter e muitas vezes gratuitas para interceptar comunicações com muito pouco esforço. Isso pode gerar mais ataques à medida que o agente de ameaças obtém conhecimento sobre você e suas redes.

a. Guia **Rede sem fio** - **Segurança da rede sem fio**

b. Para cada uma das três redes, configure o seguinte:

o Security Mode: **WPA2 Personal**

o Encryption: **AES**

o Passphrase: **ciscorocks**

c. Clique em **Salvar configurações**.

### Etapa 3: Configurar a segurança para a rede sem fio GuestNet.

Esse roteador permite que duas redes sem fio independentes sejam configuradas para cada rádio. Isso pode ser útil quando você deseja manter o tráfego de convidados separado do tráfego nas outras redes.

a. Na guia **Sem fio**, clique em **Rede Guest.**

b. Para cada uma das três redes, clique em **Habilitar perfil do convidado** e, em seguida, configure o seguinte:

o SSID: GuestNet

o Broadcast SSID: **Enabled**

o Security Mode: **WPA2 Personal**

o Encryption: **AES**

o Passphrase: guestpass

c. Clique em **Salvar configurações**.

## Parte 3: Configurar a segurança de rede de clientes sem fio

O roteador sem fio doméstico foi reforçado e a segurança sem fio foi configurada. Nesta parte, você conectará com segurança clientes sem fio à rede.

### Etapa 1: Configurar a conectividade sem fio para os laptops.

a. Clique em Laptop doméstico 1 localizado na sala de estar e clique na guia **Desktop**> **PC Wireless**.

b. Clique na guia **Connect**.

c. Clique na primeira entrada da HomeNet e clique em **Conectar**.

d. A segurança já está definida como **WPA2-Personal**. Digite Cisco123! No campo **chave pré-compartilhada** e clique em **Connect**.

e. Clique na guia **Link Information**. Você verá uma mensagem que confirma que você se conectou com sucesso ao ponto de acesso. Se você ainda não estiver conectado, verifique a configuração do Roteador sem fio doméstico e tente novamente.

f.  Feche **PC Wireless** window and click **IP Configuration**. Se o laptop ainda tiver um endereço da rede "169", alterne entre **DHCP** e Estático até receber o endereçamento IP da rede 192.168.0.0/24.

g. Repita esta etapa para o Laptop doméstico 2 no home office, mas use a primeira entrada para GuestNet. escreva **guestpass** como pre **-shared key**.

### Etapa 2: Configurar a conectividade sem fio para dispositivos IOT.

a. No home office, na prateleira superior da estante, clique em Home_Webcam

b. Clique **Config** > **Wireless0**.

c. Insira a HomeNet como **SSID**.

d. Escolha **WPA2-PSK** para **Autenticação** e digite ciscorocks para a senha **PSK**.

e. Em **Configuração de IP**, clique em **DHCP** e verifique se o dispositivo recebeu endereçamento IP da rede 192.168.0.0/24. Alterne entre **DHCP** e **Estático**, se necessário.

f.  Repita esta etapa para o Home_Siren, localizado na sala de estar acima da estante, e o **Home Door**.

## Parte 4: Verificar as configurações de conectividade e segurança

Nesta parte, você testará suas configurações e segurança para garantir que os dispositivos estejam se comunicando entre si e que consigam acessar a Internet.

### Etapa 1: Testar a conectividade da Internet para notebooks sem fio.

a. Clique Home Laptop 1 > **Desktop** tab > **Web Browser**.

b. Acesse www.ptsecurity.com. O Packet Tracer pode levar alguns segundos para convergir. Você pode clicar em **Fast Forward** para acelerar o processo até a **página pública do Data Center** carregar.

c. Repita esta etapa para o Laptop doméstico 2.

### Etapa 2: Configurar a segurança para a interconectividade GuestNet e HomeNet.

Normalmente, a **GuestNet** e a HomeNet não devem conseguir se conectar ou compartilhar recursos. Lembre-se de que o laptop doméstico 2 está configurado para a rede de convidado e normalmente não deve ter acesso aos dispositivos na rede doméstica.

a. Use o método que você deseja determinar para o endereço IP do laptop doméstico 1.

b. Clique em Home Laptop na guia Desktop > **Command** Prompt( **Prompt de comando).**

c. Insira o comando **ping** seguido pelo endereço IP do laptop doméstico 1.

O laptop doméstico 1 responde aos pings, indicando que o laptop doméstico 2 pode acessar dispositivos na rede doméstica. Você precisará configurar o roteador para impedir que hosts em redes diferentes se comuniquem entre si.

d. Do **PC Home Office**, se necessário, faça login novamente na página da Web de configuração do Roteador sem fio doméstico em 192.168.0.1.

e. Clique na guia **Sem fio** e, em seguida, no submenu **Rede de convidados**.

f.  Desmarque a caixa ao lado de **Permitir que os convidados se encontrem e acessem a rede local** e clique em **Salvar configurações**.

g. Do Laptop doméstico 2, tente executar ping no Laptop doméstico 1 novamente. O ping devem falhar. Isso indica que os hosts não têm permissão para se comunicar entre as duas redes.