# Objetivos

=   Use OpenSSL para gerar uma assinatura digital.

=   Assina um documento com a assinatura digital.

=   Verifique se um documento assinado foi alterado.

# Histórico/Cenário

Uma assinatura digital é uma técnica matemática usada para validar a autenticidade e a integridade de uma mensagem digital. A finalidade de uma assinatura digital é evitar a adulteração das mensagens e a falsificação de identidade na comunicação digital. Em muitos países, incluindo os Estados Unidos, as assinaturas digitais têm o mesmo valor legal que as formas tradicionais de documentos assinados. O governo dos Estados Unidos publica, agora, versões eletrônicas de orçamentos, leis e projetos de leis do congresso com assinaturas digitais.

Um algoritmo de assinatura digital consiste em um processo de criação e verificação de assinatura. O usuário A gera a assinatura digital e o usuário B verifica a assinatura usando o processo de verificação. Tanto o assinante quanto o verificador têm uma chave pública e privada que eles usam para concluir cada processo.

Neste laboratório, você usará o kit de ferramentas OpenSSL para gerar uma assinatura digital. Você, então, vai gerar um documento, assiná-lo com a assinatura digital e validar a autenticidade e a integridade do documento. Por fim, você alterará o documento e validará se o documento não é mais autêntico porque sua integridade foi comprometida.

# Recursos necessários

PC com o **CSE-LABVM** instalado no VirtualBox

# Instruções

## Parte 1: Abra uma janela de terminal no CSE-LABVM.

a.﻿ ﻿Inicie o **CSE-LABVM**.

b. Clique duas vezes no ícone **Terminal** para abrir um terminal.

## Parte 2: Gerar e exibir uma chave privada.

a. Para gerar uma chave privada, use o comando **OpenSL genpkey**. O comando gera uma chave privada usando o algoritmo RSA e a envia para um arquivo chamado **private_key.pem**.

cisco@labvm:~$ **openssl genpkey -algorithm RSA -out private_key.pem**

........................ +++++

... +++++

cisco@labvm:~$

b. Use o comando **cat** para visualizar o arquivo **private_key.pem**.

cisco@labvm:~$ **cat private_key.pem**

----- COMECE A CHAVE PRIVADA -----

MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQC1db50XOYeDTAy

GnQLRwGusr7us0Mi44hfFUmai3QHzelqRBxO06ujv9fFwQ8e5QsaQWbph + RVTQBu

<output omitted>

R7TLUOrewnIlkMuVLk8II2EQAXTMmvvZOICCiTSvm8gflx / FRJmUEiTf0I0MVUai

X6O9rDJOjnoHBbi67+fgN0sn

-----END PRIVATE KEY-----

cisco@labvm:~$

## Parte 3: Gerar e exibir uma chave pública.

a. Para gerar uma chave pública, use o comando **OpenSL pkey**. O comando leva seu **private_key.pem** como uma entrada e, em seguida, gera uma chave pública **(-pubout -out)** para um arquivo chamado **public_key.pem**.

cisco@labvm:~$ **openssl pkey -in private_key.pem -pubout -out public_key.pem**

cisco@labvm:~$

b. Use o comando **cat** para visualizar **public_key.pem**.

cisco@labvm:~$ **cat public_key.pem**

----- COMECE A CHAVE PÚBLICA -----

MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtXW + dFzmHg0wMhp0C0cB

rrK+7rNDIuOIXxVJmot0B83pakQcTtOro7/XxcEPHuULGkFm6YfkVU0Abq/1ccub

SFZFb1kKobMutMhxvfBQjQr3jo1j6aG12yMvrQudvSlaxHTvuDpMlhPY3IrBjkMz

2Lx0SjjOC9uD3CzaMwu6JWnhRt0svH7n6cZNXDfIlsYpcjLg9JqKrWEO3Ooq05q1

e2JEAuDOXte+M2O0ZC7cjSyxCiOfD2IEXkBq41H7xgIKTq2WJ8f+/RXEdC5Mx6Xx

fu7pQXN9gT9LbUPlLJfUG7vTCs2d2AA6TBUyUuzH2mS61KwWcT8VRAWtWdr/sPSK

AQIDAQAB

-----END PUBLIC KEY-----

cisco@labvm:~$

## Parte 4: Crie um novo documento que será assinado digitalmente.

a. Use o comando **echo** para criar um arquivo de texto chamado **Contract.txt**.

cisco@labvm:~$ **echo Please transfer 2,000,000 US Dollars to Mr. Jester by 6pm today! > Contract.txt**

cisco@labvm:~$

b. Use o comando **cat** para exibir o conteúdo do arquivocontacts.txt**.**

**

cisco@labvm:~$ **cat contract.txt**

Transfira 2.000.000 dólares para o Mr. Jester hoje às 18h!

## Parte 5: use a chave privada para assinar digitalmente o novo documento.

a. Para assinar o documento, use o comando **OpenSL dgst**. O comando **dgst** pode receber qualquer número de valores de resumo da mensagem. Neste exemplo, você usará SHA 256 e, em seguida, **private_key.pem** para gerar uma **assinatura** para o documento **contrat.txt**.

cisco@labvm:~$ **openssl dgst -sha256 -sign private_key.pem -out signature contract.txt**

cisco@labvm:~$

**

**b. Use o comando **cat** para exibir o conteúdo do** arquivo**. O arquivo é um arquivo binário. Pressione **Enter**para obter um prompt de comando.**

**

cisco@labvm:~$ **cat signature**

H�&/J�c�M�$R�xpA��*t�>�ѣmr�C      jw��q]t'�#ot"%_B�X���~�k��p3����-���̣

<output omitted>

ROˤ    ��D?Nz�����f�<�H�~�P5nJ���hqG�&28Jcisco@labvm:~$

## Parte 6: Verificar a autenticidade e a integridade do documento.

A tecnologia de assinatura digital permite que o destinatário verifique a autenticidade e a integridade do arquivo. O processo de verificação de assinatura digital é garantir que uma determinada mensagem tenha sido assinada pela chave privada que corresponde a uma determinada chave pública.

Para verificar se o documento é autêntico e não foi violado, use o comando **OpenSL dgst** com a opção de **verificação** e **public_key.pem**.

cisco@labvm:~$ **openssl dgst -sha256 -verify public_key.pem -signature signature contract.txt**

Verificado

## Parte 7: Simule um agente de ameaça alterando o destinatário especificado no arquivo Contract.txt.

a. Use **gedit** para abrir o arquivo **Contract.txt**.

cisco@labvm:~$ **gedit contract.txt**

b. Mude **o Sr. Jester** para o **Sr. Viper.**

c. Clique em **Arquivo**> **Sair** e, em seguida, clique em **Salvar** na caixa de diálogo.

## Parte 8: Verifique se a integridade do documento foi comprometida.

Reutilize o comando **opensl dgst** com a opção de **verificação** para validar que a verificação do documento agora falha.

cisco@labvm:~$ **openssl dgst -sha256 -verify public_key.pem -signature signature contract.txt**

Falha na verificação

cisco@labvm:~$

**