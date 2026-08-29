**Sumário**
	**Tags:** #Linux 
	**Conteúdo:** Introduction to Linux (LFS101)
	
----

No Linux, tudo é tratado como um arquivo. Seja lidando com documentos ou com dispositivos (como uma impressora), os comandos de entrada e saída utilizados são os mesmos. Assim como separamos livros e musicas por categorias, ou organizar por gênero, tipo, etc. O mesmo ocorre com os arquivos de sistemas. Dos diferentes tipos de arquivos de sistema que o [[Linux Courses|Linux]] suporta estão:

- Arquivos convencionais de sistema: **ext3**, **ext4**, **XFS**, **Btrfs**, **JFS**, **NTFS**, **vfat**, **exfat**, etc.
- Arquivos de armazenamento Flash: **ubifs**, **jffs2**, **yaffs**, etc.
- Arquivos de "Bando de Dados" 
- Arquivos especiais: **procfs**, **sysfs**, **tmpfs**, **squashfs**, **debugfs**, **fuse**, etc.

Comparação do sistema de arquivos do Windows e do Linux.

<figure style="text-align: center;">
  <img src="LinuxVSWindos.webp" style="margin: 0 auto;">
  <figcaption>Sistema de arquivos Windows x Linux.</figcaption>
</figure>

Diferente do Windows que separa os [[Computador#Dispositivo de Armazenamento|dispositivos de armazenamento]] por disco C: ou D:, o Linux junta todos esses dispositivos em um só lugar, o  **MountPoint**, onde o sistema (disco C:) é o **root** (/), e ao invés de existir um disco D:, usamos outro MountPoint, onde usaremos o outro disco de  armazenamento como uma pasta. Os arquivos são armazenados usando um sistema chamado **F**ilesystem **H**ierarchy **S**tandard ou <span style="color:rgb(255, 255, 0)">FHS</span>, [aqui](https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.pdf) tem um arquivo que contem informações mais detalhadas sobre. Linux usa a "/" diferente do Windows que utiliza "\\\", além disso os arquivos também são [[Case Sensitive|Case Sensitive]].
**Caminhos absolutos** sempre começam com o diretório **Root** (/), como por exemplo `cd /usr/bin`, aqui vamos direto para a raiz do sistema (**root**), não importa aonde estamos no sistema. Já os **Caminhos Relativos** começam do caminho onde esta sendo trabalhado, por exemplo `cd ../../usr/bin`, aqui usamos o `..` para voltar pastas, e de lá procurar a pasta `usr`. O uso de cada um desses métodos varia de acordo com o momento.

<figure style="text-align: center;">
  <img src="ArvorePastasLinux.webp" style="margin: 0 auto;">
  <figcaption>Visualização Root Tree.</figcaption>
</figure>

## Diretórios

No <span style="color:rgb(67, 44, 37)">/home</span> é onde ficam os usuários do sistema, e também é possível criar subpastas para nelas criar grupos, como por exemplo `/home/estudantes`, `/home/professores` e `/home/diretoria`. No <span style="color:rgb(1, 73, 109)">/bin</span> existem os comandos usados no sistema como o **cat**, **mv**, **rm**, e no <span style="color:rgb(29, 64, 56)">/sbin</span> temos os binários essências para o funcionamento do sistema, como o **ip** e o **fsck** (File System Check). Dentro do <span style="color:rgb(32, 72, 75)">/proc</span> existem arquivos virtuais ou temporários que são deletados ao reinício do sistema, esses arquivos possuem informações do sistema como interrupções, informações de **memória** e [[Computador#Central Processing Unit (CPU)|CPU]], etc.

<figure style="text-align: center;">
  <img src="FHS.webp" style="margin: 0 auto;">
  <figcaption>Explicação do FHS.</figcaption>
</figure>
