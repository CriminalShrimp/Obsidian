# Objetivos

Parte 1: Use um algoritmo de criptografia clássico

Parte 2: Use um algoritmo de criptografia simétrica moderna

Parte 3: Use um algoritmo de criptografia assimétrica moderna

# Histórico/Cenário

A criptografia moderna baseia-se principalmente na teoria matemática e na prática da ciência da computação. Os algoritmos criptográficos são projetados em torno de suposições de complexidade computacional, tornando-as difíceis, se não impossíveis, de serem quebradas por um agente de ameaças. JCrypTool é uma ferramenta de software de código aberto, independente de plataforma, e faz parte do projeto de código aberto CrypTool. O JCrypTool é uma plataforma de e-learning extensível que apresenta criptografia, análise de criptografia e segurança de TI de uma forma moderna e fácil de usar. Este laboratório usará o JCrypTool para apresentar algoritmos criptográficos clássicos, modernos, simétricas e assimétricas.

# Recursos necessários

PC com o **CSE-LABVM** instalado no VirtualBox

# Instruções

## Parte 1: Use um algoritmo de criptografia clássica

Na criptografia, uma cifra é um algoritmo utilizado para realizar a criptografia ou descriptografia. Uma cifra é um conjunto de etapas (um algoritmo) para executar uma criptografia e a descriptografia correspondente. As primeiras cifras de criptografia foram projetadas para permitir que a criptografia e a descriptografia ocorram manualmente, enquanto as que são desenvolvidas e usadas hoje em dia só são possíveis com computadores. Os algoritmos clássicos são aqueles inventados até os anos 50.

Uma cifra de César, também conhecida como cifra de deslocamento, é uma das técnicas de criptografia mais simples e amplamente conhecidas. O método tem o nome de Júlio César, que o usou em sua correspondência privada. A cifra de César é um tipo de cifra de substituição na qual cada letra é substituída por outra letra que é correspondente a um número que define quantas posições irão pular no alfabeto. Por exemplo, com um turno à esquerda de 3, D seria substituído por A, E se tornaria B e assim por diante.

### Etapa 1: Inicie o CSE-LABVM.

### Etapa 2: Abrir e explorar o JCrypTool.

a.     Clique duas vezes no ícone **JCrypTool** na área de trabalho. O diretório **JCrypTool** é aberto.

b.     Clique duas vezes no ícone **JCrypTool**.

A ferramenta tem quatro janelas:

=   **Explorador de arquivos** - É usado para localizar, abrir e salvar arquivos.

=   **Ajuda** - É usado para localizar arquivos de ajuda e tutoriais.

=   **Arquivo aberto atualmente** - Contém arquivos para serem operados com ferramentas de criptografia. O arquivo **unsaved001.txt** deve estar aberto.

=   **Crypto Explorador** - Fornece acesso a ferramentas de criptografia. Por padrão, o Crypto Explorador não é exibido. Para abri-lo, clique em **Janela**> **Mostrar vistas**> **Crypto Explorador**.

### Etapa 3: Use o algoritmo de César para criptografar uma mensagem de texto.

a.    Para começar, você precisará preencher o arquivo aberto no momento com a mensagem que deseja criptografar. Destaque todo o texto no arquivo ***unsaved001.txt** e substitua-o pela seguinte mensagem:

**CRIPTOGRAFIA É DIVERTIDO VOCÊ PODE LER ESTA MENSAGEM SECRETA?**

b.     No **Crypto Explorador,**clique em **Clássico** se não for expandido e clique duas vezes em **César**.

c.     Na seção **Operação**, selecione **Criptografar**, se ainda não estiver selecionada.

d.    Na seção **Alfabeto**, verifique se as opções **Selecionar alfabeto** e **Latim (AZ)** estão selecionadas. Caso contrário, selecione-os agora.

e.    Na seção **Chave**, vá para **Entrar usando um caractere** e mude para **K**. Deixe todas as outras opções como padrão.

f.     Clique em **Concluir** para salvar as opções e criptografar os dados.

g.    Um novo arquivo chamado ***out001.txt** é aberto com a mensagem criptografada.

### Etapa 4: Descriptografar o texto criptografado com o algoritmo de César.

a.     Mova o arquivo ***out001.txt** para a janela do Explorador de arquivos, se necessário. Isso garante que o **Crypto Explorador** use esse arquivo como o arquivo ativo. Você também pode fechar o arquivo ***unsaved001.txt**.

b.      Na guia **Crypto Explorador**, clique duas vezes no algoritmo de **César** novamente.

c.     Na seção **Operação**, selecione **Descriptografar**.

d.     Selecione as mesmas configurações para descriptografar o texto cifrado atual no arquivo de saída ***out001.txt**.

e.     Clique em **Concluir** para salvar as opções e descriptografar os dados.

f.     Feche todos os arquivos no **Explorador de Arquivos**. Não há necessidade de salvá-los.

### Etapa 5: Alterar as configurações do algoritmo de César.

a.     Crie um novo arquivo de texto de entrada selecionando **Arquivo**> **Novo**> **Arquivo vazio no Editor de texto**.

b.     Digite a seguinte mensagem: **Criptografia é divertido. Você consegue ler esta mensagem secreta?**

c.     Na guia **Crypto Explorador**, clique duas vezes no algoritmo de **César** novamente.

d.     **Criptografar** já deve estar selecionada. Para **Selecionar alfabeto**, defina o valor como **Latim maiúsculo e minúsculo (AZ, az).** Para a quantidade de turnos ("shifts") ao longo do alfabeto, defina o valor como **13**.

e.     Clique em **Concluir** para salvar as opções e criptografar os dados.

f.     Feche todos os arquivos no **Explorador de Arquivos**. Não há necessidade de salvá-lo.

Explorações adicionais

Experimente sozinho o César e outros algoritmos de criptografia clássicos para ver como eles funcionam.

## Parte 2: Use um algoritmo de criptografia simétrica moderna

Nesta parte, você usará um algoritmo de criptografia simétrica moderna. Uma das versões mais populares de um algoritmo criptográfico moderno é o Advanced Encryption Standard (AES). O AES é uma cifra criptográfica simétrica em software e hardware que é usada em todo o mundo para criptografar dados confidenciais. A criptografia AES requer uma chave de criptografia para controlar o processo de criptografia e descriptografia. Esse algoritmo é considerado um protocolo criptográfico forte com base em sua complexidade e comprimento de chave de 128 bits.

### Etapa 1: Usar criptografia AES para criptografar uma mensagem de texto.

a.     Crie um novo arquivo de texto de entrada selecionando **Arquivo**> **Novo**> **Arquivo vazio no Editor de texto**.

b.     Digite a seguinte mensagem: **Criptografia é divertido. Você consegue ler esta mensagem secreta?**

c.     Na guia **Crypto Explorador**, clique em **Simétrico** para expandi-lo, se necessário, e clique duas vezes em **AES**.

d.     Use as seguintes configurações.

·         Operação: **criptografar**

·         Origem da chave: **Chave personalizada**

·         Tamanho da chave: **128**

·         Chave (hex): **AA 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FF**

·         Modo: **Manual de códigos eletrônico (codebook) (BCE)**

·         Espaçamento: **PKCS # 5 Espaçamento**

e.     Clique em **Concluir.** Um arquivo de saída com extensão a.bin é aberto. Você verá quatro linhas com 16 valores hexadecimais em cada linha. O texto cifrado é exibido à direita de cada linha.

### Etapa 2: Use AES para descriptografar a mensagem.

a.     Clique duas vezes em **AES** novamente.

b.     Altere a **Operação** para **Descriptografar** e, em seguida, use as configurações da Etapa 1 para descriptografar o texto cifrado.

c.     Clique em **Concluir** para salvar as opções e descriptografar os dados. Um arquivo de saída com extensão .bin é aberto com o texto descriptografado.

d.     Feche todos os arquivos.

## Parte 3: Use um algoritmo de criptografia assimétrica moderna

Nesta parte, você usará um algoritmo de criptografia assimétrica moderno. Ao contrário da criptografia simétrica, a criptografia assimétrica criptografa e descriptografa os dados usando duas chaves criptográficas separadas matematicamente conectadas. Essas chaves são conhecidas como “Chave pública” e “Chave privada”. Para que uma pessoa envie uma mensagem criptografada para outra pessoa usando criptografia assimétrica, ela solicita uma chave pública e depois a usa para criptografar uma mensagem com um algoritmo combinado. A outra pessoa descriptografa a mensagem usando sua chave privada. A mensagem não pode ser descriptografada usando a chave pública.

### Etapa 1: Use a criptografia assimétrica do RSA para criptografar um arquivo de texto.

a.     Crie um novo arquivo de texto de entrada selecionando **Arquivo**> **Novo**> **Arquivo vazio no Editor de texto**.

b.     Digite a seguinte mensagem: **Criptografia é divertido. Você consegue ler esta mensagem secreta?**

c.     No Crypto Explorador, clique em **Assimétrico** para expandi-lo e clique duas vezes em **RSA** para abrir as configurações do algoritmo.

d.     Use as seguintes configurações:

·         Operação: **Criptografar**

·         Keystore: clique em **Criar um novo par no keystore**.

·         Na caixa de diálogo **Novo par de chaves**, insira o seguinte:

o    Nome de contato: **John Smith**

o    Senha: **Segredo**

o    Deixe todas as outras entradas como padrão.

e.     Clique em **Concluir.**

f.      Clique em **Concluir** na caixa de diálogo **RSA - criptografia** para criptografar os dados. Um arquivo de saída com extensão .bin é aberto com o texto criptografado.

### Etapa 2: Use a criptografia assimétrica RSA para descriptografar um arquivo de texto.

a.     Clique duas vezes em **RSA**.

b.     Selecione **Descriptografar** para a operação.

c.     Chave de seleção = **"John Smith" - chave pública - 1024**

d.     Clique em **Concluir** para descriptografar o texto cifrado.

e.     Insira a senha **Segredo**. Clique em **OK**.

Fim do documento
