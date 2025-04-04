
# Objetivos

**Parte 1: Configurar e usar credenciais de autenticação AAA**

**Parte 2: Configurar e Verificar Serviços de E-mail**

**Parte 3: Configurar e usar serviços de FTP**

# Histórico/Cenário

Autenticação e autorização são processos de segurança distintos no mundo do gerenciamento de identidade e acesso (IAM). A autenticação usa senhas e outros métodos de identificação para confirmar que os usuários são quem eles dizem ser. Por outro lado, a autorização atribui permissões de usuário aos recursos aos quais o usuário tem permissão. Nesta atividade do Packet Tracer (PT), você configurará a autenticação e a autorização para serviços de rede, incluindo acesso à rede sem fio, e-mail e serviços de FTP.

**Nota**: Esta atividade é aberta no modo **Físico**. No entanto, você pode concluí-la no modo **Lógico**.

**Observação**: a maioria das tarefas nesta atividade é classificada. Clique em **Verificar resultados** a qualquer momento para ver os **Itens de avaliação** corretos e incorretos.

# Instruções

## Parte 1: Configurar e usar credenciais de autenticação AAA

### Etapa 1: Configurar contas de usuário no servidor AAA.

a.     Navegue até a Sede e clique no **Gabinete de Fiação**, que é o chassi do servidor preto e alto no canto inferior esquerdo.

b.     No **Rack** do lado direito, clique em **AAA-RADIUS** server > **guia Serviços** e depois em **AAA** debaixo de **SERVICES**.

c.     Ative o serviço AAA.

d.     Em **Configuração do usuário**, adicione os seguintes nomes de **usuário** / **senhas**.

o    user1 / PASSuser1!

o    user2 / PASSuser2!

### Etapa 2: Configurar a autenticação sem fio no HQ-Laptop-1.

a.     Volte para HQ e clique em HQ-Laptop-1. Ele está localizado em duas salas à direita do **Wiring Closet**.

b.     Clique na guia **Config** e, depois, clique na **INTERFACE** **Wireless0**.

c.     Na caixa **SSID**, digite HQ-INT.

d.     Na área **Autenticação**, clique em **WPA2**.

e.     Na caixa **ID de usuário**, insira user1; e digite PASSuser1! na caixa **Senha**.

f.     Na seção de **Configuração de IP**, clique em **DHCP**. Que minutos o DHCP oferece para ser aceito. Verifique o endereço IP recebido pelo HQ-Laptop-1 e tenha um endereço na rede 192.168.50.0/24.

**Observação**: pode ser necessário alternar entre **estático** e **DHCP** para forçar o Packet Tracer a convergir em suas configurações. Além disso, clique em **Verificar resultados** para verificar se configurou corretamente o servidor AAA e as configurações sem fio no laptop. Clicar em **Verificar resultados** também pode forçar o Packet Tracer a convergir. Se tudo estiver configurado corretamente, prossiga para a configuração do HQ-Laptop-2 e, em seguida, retorne para HQ-Laptop-1 e verifique sua configuração de IP. Esse problema normalmente é resolvido.

### Etapa 3: Configurar a autenticação sem fio no HQ-Laptop-2.

a.     Clique em HQ-Laptop-2, localizado no canto superior direito da HQ.

b.     Repita as etapas anteriores para definir as configurações sem fio para HQ-Laptop-2, usando as credenciais de usuário2.

c.     Verifique o endereço IP recebido pelo HQ-Laptop-2 e receba um endereço na rede 192.168.50.0/24.

## Parte 2: Configurar e usar serviços de e-mail

### Etapa 1: Ativar serviços de e-mail e configurar contas de usuário de e-mail.

a.     Navegue para o **armário de fiação**.

b.     No lado direito do **Rack**, clique em Servidor de **e-mail** > guia **Serviços** e depois **EMAIL** em **SERVIÇOS**.

c.     Ative os serviços **SMTP** e **POP3**.

d.     Defina o domínio como mail.cyberhq.com.

e.     Em **Configuração do usuário**, digite os seguintes **nomes de usuário** / **senhas**. Clique no sinal de adição (**+**) para adicionar cada par.

o     HQuser1 / Cisco123!

o     HQuser2 / Cisco123~

o     BRuser1 / Cisco123-

o     BRuser2 / Cisco123 +

### Passo 2: Configure os clientes de e-mail

a.     Volte para a sede e clique no PC 1-1, que fica no canto inferior.

b.     Clique na guia **Desktop** > **Email**. As **configurações de caixa de correio** são abertas.

c.     Insira as informações a seguir:

o    Seu nome: Suk-Yi

o    Endereço de e-mail: HQuser1@mail.cyberhq.com

o    Servidor de e-mail de entrada e saída: email.cyberhq.com

o    Nome do usuário: HQuser1

o    Senha: Cisco123!

Clique em **Salvar**.

d.     Use as informações da tabela para definir as configurações de e-mail para 2-3, HQ-Laptop-1 e Net-Admin. O PC 2-3 está no escritório abaixo da sala de conferência. O PC Net-Admin está no **armário de conexões**.

|PC / Laptop|Seu nome|Endereço de e-mail|Nome de Usuário|Senha|
|---|---|---|---|---|
|2-3|Ajulo|BRuser1 @ mail.cyberhq.com|BRuser1|Cisco123-|
|HQ-Laptop-1|Malia|BRuser2 @ mail.cyberhq.com|BRuser2|Cisco123 +|
|NetAdmin|Cisco|HQuser2@mail.cyberhq.com|HQuser2|Cisco123~|

Linha em branco, sem informações adicionais

### Etapa 3: Enviar um e-mail como Suk-Yi.

a.     No PC 1-1, clique em **Escrever**.

b.     Escreva um e-mail para o Ajulo em BRuser1@mail.cyberhq.com. Insira um assunto e uma mensagem de e-mail de sua escolha. Clique em **Enviar** quando terminar.

**Observação**: o Packet Tracer pode levar vários segundos para convergir antes de você ver uma mensagem de **envio de sucesso** na parte inferior da janela.

**Observção**: o packet tracer não classifica esta etapa. Verifique se você concluiu corretamente esta etapa ao receber o e-mail enviado por Suk-Yi no PC 2-3 do Ajulo.

c.     Navegue até o PC 2-3 do Ajulo. Se necessário, clique na guia **Desktop** > **E-mail**.

d.     Clique em **Receber** e leia o e-mail de Suk-Yi.

## Parte 3: Configurar e usar serviços de FTP

### Etapa 1: Ative o serviço de FTP.

a.     Navegue para o **armário de fiação**.

b.     No lado direito do **rack**, clique em Servidor **FTP** > guia **Serviços** e depois em **FTP** em **SERVIÇOS**.

c.     Ative o serviço **FTP** .

### Etapa 2: Criar as contas de usuário de FTP.

a.     Em **Configuração do usuário**, insira os seguintes nomes de usuário, senhas e privilégios. Clique em **Adicionar** para adicionar cada usuário.

**Observação**: certifique-se de que o nome de usuário malia não inclua a opção **Excluir** como um dos privilégios de usuário.

|Nome de usuário|Senha|Privilégio de usuário|
|---|---|---|
|sukyi|cisco123|RWDNL (escrever, ler, excluir, renomear, lista)|
|ajulo|cisco321|RWDNL (escrever, ler, excluir, renomear, lista)|
|malia|cisco123|RWNL (gravação, leitura, renomeação, lista)|

Linha em branco, sem informações adicionais

b.     Verifique se cada usuário foi criado corretamente e feche o servidor.

### Etapa 3: Transferir arquivos entre o Net-Admin e o servidor FTP.

a.     Clique em Net-Admin PC e então clique em **Área de Trabalho** > **Prompt de Comando**.

b.     Insira o comando **ftp 192.168.75.2** para fazer login no servidor FTP e, em seguida, autentique com o nome de usuário sukyi e a senha cisco123.

c.     Insira o comando **dir** para listar os arquivos no servidor FTP.

d.     Use o comando **get** para baixar aMessage.txt.

e.     Saia da sessão de FTP.

f.     Feche o **prompt de comando**, clique em **Editor de texto** e em **Arquivo** > **Abrir**. Abra o arquivo baixado aMessage.txt.

#### Pergunta:

Qual é a mensagem no arquivo?

Área de Resposta

Mostrar resposta

g.     Clique em **Arquivo > Novo**. Digite uma mensagem de texto de sua escolha.

h.     Clique em **Arquivo** > **Salvar** e salve o novo arquivo como aMessage_new.txt. Feche o **Text Editor** (Editor de Texto) quando terminar.

i.      Clique em **Prompt de comando** e faça o login novamente no servidor FTP como usuário sukyi.

j.      Use o comando **put** para carregar aMessage_new.txt.

k.     Saia da sessão de FTP.

### Etapa 4: Verificar se os privilégios de usuário do FTP estão funcionando conforme configurado.

a.     Volte para HQ e clique em HQ-Laptop-1, guia **Desktop** > **Prompt de comando**.

b.     Faça login no servidor FTP em 192.168.75.2 com o nome de usuário malia e a senha **cisco123**.

c.     Use o comando **delete** para tentar remover o arquivo recém-carregado aMessage_new.txt.

#### Pergunta:

Você conseguiu excluir o arquivo do servidor FTP? Explique.

Área de Resposta

Mostrar resposta

d.     Use o comando **rename** para tentar alterar o nome de aMessage_new.txt para aMessage_rename.txt.

ftp> **rename aMessage_new.txt aMessage_rename.txt**

#### Pergunta:

Você conseguiu renomear o arquivo do servidor FTP?

Área de Resposta

Mostrar resposta

e.     Saia da sessão de FTP e feche a janela HQ-Laptop-1.

