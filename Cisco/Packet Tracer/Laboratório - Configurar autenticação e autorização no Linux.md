
# Objetivos

Parte 1: Adicionar um novo grupo para usuários

Parte 2: Adicionar usuários ao novo grupo

Parte 3: Alternar usuários e modificar permissões

Parte 4: Modificar permissões no modo absoluto

# Histórico/Cenário

Neste laboratório, você usará a linha de comando do Linux para criar um grupo para novos usuários e adicionar usuários ao grupo. Cada usuário receberá uma senha para autenticação no login. Em seguida, você modificará as permissões para autorizar os privilégios de leitura, gravação e execução para usuários e grupos.

# Recursos necessários

PC com o **CSE-LABVM** instalado no VirtualBox

# Instruções

## Parte 1: Adicionar um novo grupo para usuários

Nesta parte, você adicionará um novo grupo de usuários à máquina virtual.

### Etapa 1: Abrir uma janela de terminal no CSE-LABVM.

a.   Inicie o **CSE-LABVM.**

b.   Clique duas vezes no ícone **Terminal** para abrir um terminal.

### Etapa 2: Escalar privilégios para o nível raiz.

Digite o comando **sudo su** e entre com a senha **password** quando a senha for solicitada.

cisco@labvm:~$**sudo su**

[sudo]senha para cisco:

root@labvm:/home/cisco#

### Etapa 3: Adicionar um novo grupo chamado RH.

Insira o comando **groupadd**RH.

root@ubuntu:/home/cisco#**groupadd HR**

### Etapa 4: Verifique se o novo grupo foi adicionado.

Insira o comando **cat /etc/group** para verificar se RH foi adicionado.

root@ubuntu:/home/cisco#**cat /etc/group**

root:x:0:

daemon:x:1:

bin:x:2:

sys:x:3:

<output omitted>

Alice:x:1000:

Bob:x:1001:

Véspera:x:1002:

Eric:x:1003:

Xnobody:x:1004:

RH:x:1005:

O novo grupo RH será adicionado na parte inferior do arquivo /etc/group com o ID de grupo 1005.

## Parte 2: Adicionar usuários ao novo grupo

Nesta parte, você adicionará contas de usuário de Jenny e Joe ao grupo de RH.

### Etapa 1: adicionar Jenny como um novo usuário e movê-la para o grupo de RH.

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

### Etapa 2: adicionar Joe como um novo usuário e movê-lo para o grupo de RH.

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

### Etapa 3: Verifique os usuários recém-criados no arquivo passwd .

Insira o comando **cat / etc / passwd** para verificar os novos usuários no arquivo passwd.

root@ubuntu:/home/cisco# **cat /etc/passwd**

root:x:0:0:root:/root:/bin/bash

daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin

bin:x:2:2:bin:/bin:/usr/sbin/nologin

sys:x:3:3:sys:/dev:/usr/sbin/nologin

<output omitted>

Xnobody:x:1004:1004::/home/Xnobody:/bin/sh

jenny:x:1005:1006:Jenny,,,:/home/jenny:/bin/bash

joe:x:1006:1007:Joe,,,:/home/joe:/bin/bash

### Etapa 4: Visualize os usuários criados no arquivo shadow .

Insira o comando **cat /etc/shadow** para verificar os novos usuários no arquivo shadow.

root@labvm:/home/cisco# **cat /etc/shadow**

root:!:18704:0:99999:7:::

daemon:*:18704:0:99999:7:::

bin:*:18704:0:99999:7:::

sys:*:18704:0:99999:7:::

<output omitted>

Xnobody:!:18704:0:99999:7:::

jenny:$6$VmEFD7wi6zHV8VH5$m2K8U2wpONkvTXzf9uSxSHitbcwAQMEmNiYg8ICnBpdct9dxqr3Hh8EGvxaIasa9fUw.mtB4GGkQYvoZHAFSa/:18705:0:99999:7:::

joe:$6$Ga2C7801c2vb7ias$G9OdK91gnLCnq.5vgpUJjn0/KyWKkXmRemqoGJgBFH0QejpmRYZxQhmS42eZG0SBApc1Z2Q/gsfwuD6oLUh.W.:18705:0:99999:7:::

## Parte 3: Alternar usuários e modificar permissões

Nesta parte, você vai fazer login como jenny, explorar diretórios e alterar permissões.

### Etapa 1: Alternar usuário de root para jenny.

a.  Para alternar para a área de trabalho de Jenny, clique em **Menu** na parte inferior esquerda da área de trabalho e clique em **Logout**.

b.   Clique em **Switch User (Alternar usuário)** na caixa de diálogo.

c.   Clique em **Jenny** na lista de usuários disponíveis e digite a senha **jenPass**.

d.   A área de trabalho de Jenny é carregada. Aqui, você pode clicar com o botão direito do mouse na área de trabalho e escolher **Abrir no Terminal**.

jenny@labvm: ~/Desktop$

### Etapa 2: explorar o ambiente da Jenny.

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

### Etapa 3: Faça login como root.

Joe pode não querer que Jenny leia o conteúdo do diretório. O acesso raiz (root) ou outro superusuário pode alterar as permissões de diretório para negar o acesso de leitura de Jenny, ou qualquer outro usuário ou grupo, ao diretório inicial de Joe.

a.   Faça login como usuário **cisco** com a senha como a **password**. Use o comando **su cisco**.

jenny@labvm:/home$ **su cisco**

Senha:

b.  Insira o comando **sudo -i** para alternar para root e digite a senha como a **password**.

cisco@labvm:~$ **sudo -i**

[sudo] password for cisco: **password**

### Etapa 4: Modificar as permissões para o diretório pessoal de Joe.

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

### Etapa 5: Verificar se Jenny não consegue mais acessar o diretório de Joe.

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

## Parte 4: Modificar permissões no modo absoluto

Na parte anterior, você alterou as permissões no modo simbólico. No modo simbólico, o administrador usa o comando **chmod** com uma combinação de letras e símbolos para adicionar ou remover permissões. Nesta parte, você usará o comando **chmod** e os valores octal para definir permissões para cada tripleto de permissões (rwx) para usuário, grupo e outro.

### Etapa 1: Alternar usuário de jenny para joe.

a.  Para alternar para a área de trabalho de Joe, clique em **Menu** na parte superior esquerda da área de trabalho. Na parte inferior do menu suspenso, clique no botão com a ponta da ferramenta **Finalizar a sessão atual**.

b.   Clique em **Switch User (Alternar usuário)** na caixa de diálogo.

c.  Clique em **Joe** na lista de usuários disponíveis e digite a senha **joePass**.

d.   A área de trabalho de Joe é carregada. Aqui, você pode clicar com o botão direito do mouse na área de trabalho e escolher **Abrir no Terminal**.

joe@labvm:~/Desktop$

### Etapa 2: Explorar o ambiente de Joe.

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

### Etapa 3: Use o modo absoluto para modificar e, em seguida, verifique as permissões para o diretório de Joe.

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

### Etapa 4: criar um arquivo no diretório joe.

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

### Etapa 5: Alternar usuário de joe para jenny.

a.   Para alternar para a área de trabalho de Jenny, clique em **Menu** na parte superior esquerda da área de trabalho. Na parte inferior do menu, clique no botão com a ponta da ferramenta **Finalizar a sessão atual**.

b.   Clique em **Switch User (Alternar usuário)** na caixa de diálogo.

c.   Clique em **Jenny** na lista de usuários disponíveis e digite a senha **jenPass**.

d.   A área de trabalho de Jenny é carregada. Aqui, você pode clicar com o botão direito do mouse na área de trabalho e escolher **Abrir no Terminal**.

jenny@labvm:~/Desktop$

### Etapa 6: Mude para o diretório inicial e liste seu conteúdo.

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

### Etapa 7: Mude para o diretório /home/joe e indique o conteúdo do diretório.

Observe que o usuário jenny, como um membro de "outros", tem acesso de leitura ao diretório joe e também tem acesso de leitura para o arquivo "test.txt".

jenny@labvm:/home$ **cd joe**

jenny@labvm:/home/joe$ **ls -l**

total 12

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Desktop

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Documents

drwxr-xr-x 2 joe joe 4096 Mar 20 15:00 Downloads

-rw-rw-r-- 1 joe joe    0 Mar 22 14:33 test.txt

jenny@labvm:/home/joe$

### Etapa 8: Tente criar um arquivo no diretório joe.

Observe como o usuário Jenny não tem permissão para gravar no diretório joe.

jenny@ubuntu:/home/joe$ **touch jenny.txt**

touch: cannot touch '/mnt/myNewFile.txt': Permission denied (permissão negada)

jenny@labvm:/home/joe$

### Etapa 9: Alternar usuário de Jenny para Cisco e fechar a VM (máquina virtual).

a.  Clique em **Menu** na parte superior esquerda da área de trabalho. Na parte inferior do menu suspenso, clique no botão com a ponta da ferramenta **Finalizar a sessão atual**.

b.   Clique em **Switch User (Alternar usuário)** na caixa de diálogo.

c.  Clique em **Cybersecurity Analyst (analista de cibersegurança)**na lista de usuários disponíveis e digite a senha como a **password**.

d.  Clique em **Arquivo**> **Fechar**, escolha **Salvar o estado da máquina** e clique em **OK**.

Fim do documento

  

---

© 2017 - 2022 Cisco and/or its affiliates. All rights reserved. Cisco Public