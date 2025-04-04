

# Tabela de endereçamento

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

# Objetivos

= Configurar a autenticação AAA baseada no servidor usando o TACACS+.

= Verifique a autenticação AAA baseada em servidor do cliente PC-B.

= Configurar a autenticação AAA baseada no servidor usando o RADIUS.

= Verifique a autenticação AAA baseada em servidor do cliente PC-B .

# Histórico/Cenário

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

## Parte 1: Configurar a autenticação AAA baseada em servidor usando o TACACS+ no R2

### Etapa 1: Testar Conectividade

= Ping do PC-A para PC-B.

= Ping do PC-A para PC-C.

= Ping do PC-B para PC-C.

### Etapa 2: Configurar uma entrada de banco de dados local de backup chamada Admin.

Para fins de backup, configure um nome de usuário local de Admin2 e uma senha secreta de admin2pa55.

### Etapa 3: Verifique a configuraçãodo servidor TACACS+.

Clique o server TACACS+. Na aba Serviços, clique em **AAA**. Observe que há uma entrada de configuração de rede para o R2 e uma entrada da instalação do usuário para Admin2.

### Etapa 4: Configurar os detalhes do servidor TACACS+ no R2 .

Configurar o endereço IP e a chave secreta do servidor AAA TACACS no R2.

**Nota**: Os comandos **tacacs-server host** e a **tacacs-server key** são obsoletas Atualmente, o Packet Tracer não suporta o novo comando **tacacs server** .

R2(config)# **tacacs-server host 192.168.2.2**

R2(config)# **tacacs-server key tacacspa55**

### Etapa 5: Configurar a autenticação de login AAA para o acesso de console no R2.

Ative o AAA no R2 e configure todos os logins para autenticar usando o servidor AAA TACACS+. Se não estiver disponível, use o banco de dados local.

### Etapa 6: Configurar as linhas vty para usar o método de autenticação AAA definido.

Configurar a autenticação AAA para que o login do console use o método de autenticação AAA padrão.

### Etapa 7: Verifique o método de autenticação AAA.

Verifique o login EXEC do usuário usando o servidor AAA TACACS+.

## Parte 2: Configure a Autenticação baseada em servidor AAA usando RADIUS no R3

### Etapa 1: Configure uma base de dados de backup local chamada Admin.

Para fins de backup, configure um nome de usuário local de **Admin3** e uma senha secreta **admin3pa55**.

### Etapa 2: Verifique a configuração do servidor Radius.

Clique o servidor Radius. Na aba Serviços, clique em **AAA**. Observe que há uma entrada de configuração de rede para o R3 e uma entrada de instalação do usuário para Admin3.

### Etapa 3: Configurar os detalhes do servidor Radius no R2 .

Configurar o endereço IP e a chave secreta do servidor AAA Radius no R3.

**Nota**: Os comandos **radius-server host** e a **radius-server key** são obsoletas Atualmente, o Packet Tracer não suporta o novo comando **radius server** .

R3(config)# **radius-server host 192.168.3.2**

R3(config)# **radius-server key radiuspa55**

### Etapa 4: Configurar a autenticação de login AAA para o acesso de console no R2.

Ative o AAA no R3 e configure todos os logins para autenticar usando o servidor AAA Radius. Se não estiver disponível, use o banco de dados local.

### Etapa 5: Configurar as linhas vty para usar o método de autenticação AAA definido.

Configurar a autenticação AAA para que o login do console use o método de autenticação AAA padrão.

### Etapa 6: Verifique o método de autenticação AAA.

Verifique o início de uma sessão EXEC do usuário usando o servidor RADIUS AAA.

### Etapa 7:Verifique os resultados.

O percentual de conclusão deve ser 100%. Clique em **Check Results** para ver o feedback e a verificação de quais componentes necessários foram concluídos.
