#Linux 
### O Básico
A primeira coisa, obviamente, é energia para poder ligar o computador. Após isso é iniciado o sistema o Basic Input/Output System mais conhecido como <span style="color:rgb(255, 255, 0)">BIOS</span>, iniciando o hardware, teclado, telas e testando a memoria principal, esse processo é chamado de <span style="color:rgb(255, 255, 0)">POST</span> (Power On Self Test).
![[Inicialização de um Computador-20250828060442458.webp|center]]
O sistema da BIOS fica armazenado na memoria <span style="color:rgb(255, 255, 0)">ROM</span> (Read-Only Memory), localizado na placa mãe, após isso o processo de inicialização é passado para o boot loader, que fica localizado em algum dos discos de armazenamento do computado como [[Dispositivo de Armazenamento#SSD|SSD]] ou [[Dispositivo de Armazenamento#HD|HD]], que estão armazenados no setor de boot ou no [[Abreviações#EFI/UEFI = (Unified) Extensible Firmware Interface é um padrão moderno de firmware(software embutido em dispositivos de hardware) que substitui o antigo BIOS.|EFI/UEFI]] no caso do boot UEFI , e por fim retirando os paramentos da [[Dispositivo de Armazenamento#CMOS|CMOS]], e após isso o computador acessa a tela inicial do [[Abreviações#OS = Operating System, é o sistema operacional|OS]].
![[Processo de Inicialização(Boot)-20251021045442507.webp]] 

### Boot Loader na Pratica
#kernel
Para os sistemas que utilizam o método de <span style="color:rgb(255, 255, 0)">BIOS</span>, o boot loader fica localizado na primeira seção do disco, conhecido como MBR (**M**aster **B**oot **R**ecord) que ocupa somente 512 bytes de espaço no disco. 