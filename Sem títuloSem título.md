
# Acesso Remoto (SSH)
#Comandos
O linux usa o _Secure Shell Protocol_ popularmente chamado de SSH para fazer acesso remoto em computadores permitindo envia arquivos e comandos.  O SSH criptografa a comunicação entre os comutadores, normalmente é usado para acessar data centers e Servidores Cloud. Na linha de comando vc pode se conectar a outros computadores usando o comando `ssh`.
#### Habilitando login SSH via linha de comando

Para habilitar o login remoto via SSH usasse o comando `systemctl`, esse comando se refere aos serviços de sistema, como o SSH . Usando o comando `systemctl` com o subcomando`enable` para ativar o serviço, juntamente com a opção `--now` para fazer a mudança imediatamente e por fim o nome do serviço.

[user@host ~]$ **`sudo systemctl enable --now sshd`**

O comando `systemctl is-active` verificar se um serviço esta ativo.

[user@host ~]$ **`systemctl is-active sshd`**
active

[user@host ~]$ **`systemctl is-active lvm2`**
inactive

O comando `systemctl status` mostra os status do serviço.

[user@host ~]$ **`systemctl status sshd`**
● sshd.service - OpenSSH server daemon
     Loaded: loaded (/usr/lib/systemd/system/sshd.service; enabled; vendor pres>
     Active: active (running) since Fri 2023-11-03 15:34:30 NZDT; 1h 43min ago
[...]

#### Logando pela linha de comando

O comando SSH exige o nome do usuário e o endereço/domínio que esta sendo conectado, esses dois argumentos são adicionados com o símbolo (`@`)  separando-os
Nesse exemplo vc esta logando na maquina `servera`, com o usuário `remote` que tem a senha `RedHat123!`.

[user@host ~]$ **`ssh remote@servera`**
student@servera's password: **`RedHat123!`**

Após conseguir efetuar com sucesso o login o que mudara vai ser o usuário e o domínio na sua linha de comando.
[remote@servera ~]$

#### Transferindo arquivos via CLI

O comando `scp` copia arquivos de um computador para outro por uma criptografia na rede, ele requer dois argumentos na seguinte ordem: o arquivo a ser movido e a localização desejada.

Para copiar um arquivo local para um servidor remoto forneça o caminho do arquivo para o arquivo que deseja copiar e o server de destino junto com o caminho, esta ação precisa da senha para ser realizada.

[user@host ~]$ **`scp ~/Documents/exemplo.txt user@servera:~/Documents`**

É possivel copiar um arquivo do servidor remoto para seu computador local.

[user@host ~]$ **`scp user@servera:~/Documents/exemplo.txt ~/Documents`**

E também é possível copiar de um servidor remoto para outro servidor remoto.

[user@host ~]$ **`scp user@servera:~/Documents/exemplo.txt user@serverb:~/Documents`**

### Chaves SSH para Autenticação Remota

É possivel fazer autenticações usando o conceito de [[Chaves Públicas e Privadas]]. 
#### Creating an SSH Key Pair

On the command line, generate an SSH key pair by using the `ssh-keygen` command with the `-t ed25519` option to choose the `ed25519` encryption algorithm, and then follow the prompts, accepting all defaults. You can generate a key pair only one time, because you can use the same key pair to log in to multiple servers.

Optionally, you can set a passphrase when creating an SSH key pair to add an additional security layer. A passphrase is a password that you configure to a key pair; you must input the passphrase every time that you use the key pair. By default, SSH key pairs do not use a passphrase.

[user@host ~]$ **`ssh-keygen -t ed25519`**
$ ssh-keygen -t ed25519
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/user/.ssh/id_ed25519): **`**Enter**`**
Created directory '/home/user/.ssh'.
Enter passphrase (empty for no passphrase): **`**Enter**`**
Enter same passphrase again: **`**Enter**`**
Your identification has been saved in /home/user/.ssh/id_ed25519
Your public key has been saved in /home/user/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:y+Ue2FpKtHlTIes+5RC/VFBHohey+5iAGWRQ9J6bpJw user@host
The key's randomart image is:
+--[ED25519 256]--+
|      .+=   ..+.o|
|       o .  .+ + |
|        . o +..  |
|         =.+ +.  |
|        S Boo.   |
|       + &.=++   |
|        E @=o..  |
|       . B.oo    |
|        o o.     |
+----[SHA256]-----+

Verify that the `id_ed25519` key pair exists by using the `ls` key to view the contents of the `~/.ssh` hidden directory. The `id_ed25519` file is the private key, and the `id_ed25519.pub` file is the public key.
#### Distributing an SSH Key Pair

The `ssh-copy-id` command copies your SSH public key to a remote computer. Use the `ssh-copy-id` command followed by your username on the remote computer, the at sign (`@`), and then the IP address of the server that you want to copy your key to.

In the following example, you copy the SSH public key of the `mhoward` user on the local computer to the `developer030` user on the `servera` machine.

[mhoward@host ~]$ **`ssh-copy-id developer030@servera`**
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
developer030@172.25.250.10's password: **`RedHat123!`**

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'developer030@172.25.250.10'"
and check to make sure that only the key(s) you wanted were added.

The next time that you log in to the remote host, whether you use the GNOME desktop or the command line, you are not prompted for a password.

