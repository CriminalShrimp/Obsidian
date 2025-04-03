# Objetivos

Parte 1: Proteção de dados pessoais

Parte 2: Proteger dados sem fio

Parte 3: Proteção de dados corporativos entre locais

# Histórico/Cenário

A Internet é usada por vários motivos, incluindo trabalho, diversão, entretenimento e muito mais. Existem vários protocolos, algoritmos e métodos disponíveis para proteger o acesso on-line.

Este laboratório inclui três cenários. Em cada cenário, você concluirá algumas etapas e fará uma pesquisa na Internet para responder a perguntas, inclusive qual é o melhor algoritmo de criptografia para cada cenário.

# Recursos necessários

= Um PC Windows com acesso à Internet

# Instruções

## Parte 1: Proteção de dados pessoais

Nesse cenário, você é um aluno usando um computador compartilhado. Você gostaria de salvar algumas informações confidenciais neste computador, mas não deseja que outras pessoas acessem esses dados.

### Etapa 1: Crie um arquivo de texto

a. Abra **o File Explorer** procurando-o ou usando a combinação de teclas **Windows + E** do teclado.

b. Navegue até um local de trabalho e crie uma nova pasta com o nome de sua escolha.

**Observação**: para exibir extensões de arquivo, clique em **Exibir**> **Opções**. Na janela **Opções de pasta**, clique na guia **Exibir** e desmarque **Ocultar extensões para tipos de arquivos conhecidos**.

c. Dentro da pasta, clique com o botão direito do mouse no espaço vazio e clique em **Novo**> **Documento de texto**.

d. Altere o nome para **File-1.txt** e clique duas vezes nele para abrir o arquivo.

e. Insira algum texto, como "Este é um teste." E salve e feche o arquivo.

### Etapa 2: Discutir como você pode proteger esse arquivo.

Suponha que você deva proteger esse arquivo de forma a ser lido, roubado ou alterado.

#### Perguntas:

Como você pode fazer isso?

Área de Resposta

Você pode usar um programa para proteger o arquivo por senha. Programas de compactação, como o 7-Zip, oferecem a opção de compactar e criptografar arquivos.

Ocultar resposta

Qual algoritmo de criptografia (ou seja, DES, 3DES ou AES) você deve usar se conseguir criptografar o arquivo? Por quê?

Área de Resposta

O AES oferece a criptografia mais forte em comparação ao DES e 3DES. Ele deve ser usado para garantir que o arquivo esteja protegido com segurança.

Ocultar resposta

### Etapa 3: Baixar e instalar o 7-Zip.

a. Pesquise na Internet "download do 7-Zip" e baixe este programa de compactação de código aberto gratuito.

b. Instale o 7-Zip.

### Etapa 4: Inspecionar os formatos de arquivo e os métodos de criptografia 7-Zip.

a. Na janela do **File Explorer**, **clique com** o botão direito em **File-1.txt** e selecione **7-Zip** > **Add to archive…**

b. No menu suspenso ao lado de Formato de arquivo morto :, escolha o formato zip.

c. O 7 - Zip oferece dois métodos de criptografia para o formato **zip**. O **ZipCrypto** é um método.

#### Perguntas:

Qual é o outro método?

Área de Resposta

O outro método de criptografia é o AES-256

Ocultar resposta

Quais são as diferenças entre cada método? (**Dica**: consulte a **ajuda**).

Área de Resposta

O 7-Zip pode compactar um arquivo usando o formato 7z ou ZIP. O formato 7z é compatível apenas com AES-256, enquanto o formato ZIP é compatível com ZipCrypto ou AES-256. Use o ZipCrypto se quiser obter um arquivo compatível com a maioria dos arquivadores ZIP.

Ocultar resposta

Qual método você deve usar se quiser ter a criptografia mais robusta?

Área de Resposta

O AES-256 oferece criptografia mais eficiente, mas não é tão amplamente suportado.

Ocultar resposta

### Etapa 5: Compactar e criptografar o arquivo 1.

a. Com a janela **Adicionar ao arquivo** ainda aberta, digite a senha de sua preferência no campo **Inserir senha** .

b. Clique em **OK** para compactar e criptografar o arquivo. Isso cria um novo arquivo arquivado chamado **File-1.zip**.

c. Para excluir permanentemente o arquivo original, clique nele e pressione **Shift-Excluir**. Você será solicitado a excluir o arquivo permanentemente. Clique em **Sim**.

### Etapa 6: Descriptografar o File-1.zip criptografado e compactado.

a. Com o **File Explorer** ainda aberto, clique com o botão direito do mouse em **File-1.zip** e escolha **7-Zip** > **Extrair aqui**.

b. A janela **Inserir senha** é exibida. Digite sua senha para descriptografar **File-1.txt** e, em seguida, clique em OK.

c. Abra o **File1.txt** para verificar se a mensagem original está lá.

## Parte 2: Proteger dados sem fio

Nesse cenário, você tem uma pequena empresa que fornece suporte de TI a cidadãos locais. Um novo cliente solicitou que você os configurasse com o melhor acesso sem fio. Especificamente, eles:

·  Uma grande casa de três andares com 5.000 pés quadrados.

·  Vários dispositivos pessoais mais novos e antigos, incluindo smartphones, tablets, computadores, televisores inteligentes, Oculus 2, impressoras e muito mais.

·  Quatro dispositivos Wi-Fi 6 mais recentes (802.11ax).

Após algumas pesquisas, você decide recomendar o Linksys Atlas Pro 6, sistema Dual-Band Mesh Wi-Fi 6 System de 3 pacotes. Esse sistema deve ser compatível com os dispositivos listados e oferecer a segurança sem fio necessária.

Os roteadores Wi-Fi normalmente oferecem várias opções de segurança para criptografar dados sem fio. Qual opção de criptografia você deve usar neste cenário?

### Etapa 1: Pesquisar o roteador Linksys Wireless

a. Pesquise na Internet pelo "Linksys Atlas Pro 6, sistema Wi-Fi 6 de malha de banda dupla". Sua pesquisa fornecerá muitos links possíveis. No entanto, escolha o link fornecido por **linksys.com**.

b. Analise os recursos do roteador para ver se ele atende às especificações necessárias.

### Etapa 2: Pesquisar as opções de segurança

O sistema Linksys Atlas oferece três recursos de segurança.

#### Perguntas:

Quais são os recursos de segurança disponíveis com este sistema?

Área de Resposta

Os recursos de segurança disponíveis são:  
  
 •   WPA2 / WPA3 pessoal misto  
 •   WPA2 pessoal  
 •   WPA3 pessoal

Ocultar resposta

Qual opção de segurança esses clientes devem usar?

Área de Resposta

WPA2 / WPA3 misto pessoal: recomendado apenas para uso doméstico se todos os nós estiverem atualizados com o firmware compatível com o modo misto WPA2 / WPA3.Ele usa WPA3 com criptografia AES quando possível, WPA2 com criptografia AES para dispositivos mais antigos.Alguns dispositivos podem não conseguir se conectar.  
  
WPA3 Pessoal: os dispositivos mais antigos não poderão se conectar.  
  
WPA2 Pessoal: recomendado para uso doméstico.Os usuários se conectam usando uma senha e criptografia AES.

Ocultar resposta

## Parte 3: Proteção de dados corporativos entre locais

Nesse cenário, você está trabalhando para uma pequena empresa de vários locais interconectada na Internet pública. É fundamental que os dados corporativos entre os locais sejam protegidos enquanto trafegam pela Internet.

As redes virtuais privadas (VPNs) são comumente usadas entre filiais e locais centrais para proteger dados e garantir a autenticação de origem. A empresa está usando roteadores Cisco Integrated Series (ISRs) para oferecer suporte a VPNs IPsec de site para site entre sites. O Internet Protocol Security ou IPsec é uma estrutura que permite especificar qual mecanismo de criptografia, autenticação e integridade usar.

Nesta parte, você está encarregado de recomendar os melhores algoritmos de criptografia e autenticação para implementar no Cisco ISR 4321 usando o IOS XE 17. Para fazer isso, você pesquisará vários protocolos compatíveis com VPNs IPsec.

### Etapa 1: Pesquisar algoritmos de criptografia IPsec

a. Faça uma pesquisa na Internet em “Security for VPNs with IPsec Configuration Guide, Cisco IOS XE 17”.

b. Escolha o primeiro link em **cisco.com** para abrir o **Índice**.

c. Clique no **link Configuração de segurança para VPNs com IPsec** .

d. Role para baixo até os **Padrões compatíveis** para responder às seguintes perguntas.

#### Pergunta:

Quais algoritmos de criptografia criptográfica são compatíveis com as VPNs IPsec?

Área de Resposta

Os algoritmos de criptografia compatíveis com as VPNs IPsec incluem:  
  
 •   Padrão de criptografia avançado (AES)  
 •   Algoritmo DES  
 •   Algoritmo DES triplo (3DES)

Ocultar resposta

### Etapa 2: Pesquisar a algoritmo

#### de integridade e autenticação de IPsec Pergunta:

Na seção **Padrões compatíveis**, quais algoritmos de hash são usados para autenticar dados e verificar a integridade?

Área de Resposta

Os algoritmos de criptografia compatíveis com as VPNs IPsec incluem:  
  
 •   Algoritmo seguro de hash (SHA-2) e SHA-1  
 •  Algoritmo de resumo de mensagens 5 (MD5)

Ocultar resposta

### Etapa 3: Recomendar uma pergunta sobre o algoritmo

#### de criptografia e autenticação:

Para satisfazer as necessidades da empresa, qual algoritmo de criptografia e algoritmo de hash você deve recomendar para garantir a proteção adequada para os dados que atravessam a Internet?

Área de Resposta

As VPNs IPsec de site para site normalmente exigiriam:  
  
 •   Criptografia: AES ou suas variantes (ou seja, AES-128, AES-192 ou AES-256)  
 •   Autenticação e integridade: SHA-2 ou suas variantes (ou seja, SHA-256 , SHA-384 ou SHA-512)