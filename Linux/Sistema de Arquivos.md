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

Os arquivos são armazenados usando um sistema chamado **F**ilesystem **H**ierarchy **S**tandard ou <span style="color:rgb(255, 255, 0)">FHS</span>, [aqui](https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.pdf) tem um arquivo que contem informações mais detalhadas sobre. Linux usa a "/" diferente do Windows que utiliza "\\\", e também não usa letras para denominar partições. Além disso os arquivos também são [[Case Sensitive|Case Sensitive]].

<figure style="text-align: center;">
  <img src="FHS.webp" style="margin: 0 auto;">
  <figcaption>Explicação do FHS.</figcaption>
</figure>


## Caminho Absoluto e Caminho Relativo

**Caminhos absolutos** sempre começam com o diretório Root (/), como por exemplo `cd /usr/bin`, já os **Caminhos Relativos** começam do caminho onde esta sendo trabalhado, por exemplo `cd ../../usr/bin`. O uso de cada um desses métodos varia de acordo com o momento.

<figure style="text-align: center;">
  <img src="ArvorePastasLinux.webp" style="margin: 0 auto;">
  <figcaption>Visualização Root Tree.</figcaption>
</figure>

