A criptografia é a ciência de criar e quebrar códigos.

Ao armazenar e transmitir dados criptografados, apenas o destinatário pretendido pode lê-los ou processá-los e somente se eles tiverem o conhecimento adequado do segredo usado no algoritmo de criptografia.

A encriptação é o processo de embaralhamento de dados para impedir que uma pessoa não autorizada leia os dados com facilidade.

Ao habilitar a encriptação, os dados legíveis são chamados de texto simples ou texto claro, enquanto a versão criptografada é chamada de texto criptografado ou texto cifrado. A criptografia converte a mensagem legível de texto claro em texto codificado, que é a mensagem ilegível disfarçada. A descriptografia reverte o processo.

A encriptação também precisa de uma chave, que desempenha um papel crítico para criptografar e descriptografar uma mensagem. A pessoa que possui a chave pode descriptografar o texto codificado para texto claro.

Há duas classes de algoritmos de criptografia:

- Os algoritmos simétricos usam a mesma chave pré-compartilhada para criptografar e descriptografar dados, um método também conhecido como criptografia com chave privada. O Advanced Encryption Standard (AES) é um algoritmo de criptografia simétrica que possui um tamanho de bloco fixo de 128 bits com um tamanho de chave de 128, 192 ou 256 bits. O governo norte-americano usa o AES para proteger as informações confidenciais.
- A criptografia assimétrica, também chamada de criptografia de chave pública, utiliza uma chave de criptografia que é diferente da chave usada para descriptografia. Os algoritmos de criptografia assimétrica incluem Rivest-Shamir-Adleman (RSA), Diffie-Hellman, EIGamal e Elliptic Curve Cryptography (ECC).

# Criptografia Simétrica
Os algoritmos simétricos usam a mesma chave pré-compartilhada para criptografar e descriptografar dados. Uma chave pré-compartilhada, também chamada de chave secreta, é conhecida pelo remetente e pelo receptor antes que qualquer comunicação criptografada possa ocorrer.

Para ajudar a ilustrar como a criptografia simétrica funciona, considere um exemplo em que Alice e Bob moram em locais diferentes e desejam trocar mensagens secretas entre si por meio do sistema de correio. Alice deseja enviar uma mensagem secreta para Bob.

Na figura, Alice e Bob têm chaves idênticas para um único cadeado. A troca de chaves aconteceu antes de enviar quaisquer mensagens secretas. Alice escreve uma mensagem secreta e a coloca em uma pequena caixa trancada com o cadeado. Ela manda a caixa para Bob. A mensagem está segura e trancada dentro da caixa, à medida que a caixa segue seu caminho através do sistema de correios. Quando Bob recebe a caixa, ele usa a chave para destrancar o cadeado e recuperar a mensagem. Bob pode usar a mesma caixa e cadeado para enviar uma resposta secreta para Alice.
![[Criptografia Simétrica.png]]

Hoje, algoritmos de criptografia simétrica são comumente usados com o tráfego VPN. Isso ocorre porque os algoritmos simétricos usam menos recursos da CPU do que os algoritmos de criptografia assimétrica. Isso permite que a criptografia e a descriptografia de dados sejam rápidas ao usar uma VPN. Ao usar algoritmos de criptografia simétrica, como qualquer outro tipo de criptografia, quanto maior a chave, mais tempo levará para alguém descobrir a chave. A maioria das chaves de criptografia tem entre 112 e 256 bits. Para garantir que a criptografia é segura, um comprimento mínimo de chave de 128 bits deve ser usado. Use uma chave mais longa para comunicações mais seguras .Alguns algoritmos de criptografia são:

Data Encryption Standard (DES) - Este é um algoritmo de criptografia simétrica legado. Ele usa um comprimento de chave curto que o torna inseguro para a maioria dos usos atuais. 
3DES (Triple DES) - O substituto do DES e repete o processo do algoritmo DES três vezes. Deve ser evitado, se possível, uma vez que está programado para ser aposentado em 2023. Se implementado, use durações de chave muito curtas. 
Advanced Encryption Standard (AES) - É um algoritmo de criptografia simétrica popular e recomendado. Ele oferece combinações de chaves de 128, 192 ou 256 bits para criptografar blocos de dados de 128, 192 ou 256 bits. 
Software-Optimized Encryption Algorithm (SEAL) - É um algoritmo de criptografia simétrica alternativo mais rápido ao AES. SEAL é uma cifra de fluxo que usa uma chave de criptografia de 160 bits e tem um impacto menor na CPU em comparação com outros algoritmos baseados em software. 
Algoritmos da série Rivest ciphers (RC) - Este algoritmo foi desenvolvido por Ron Rivest. Diversas variações foram desenvolvidas, mas o RC4 foi o mais prevalente em uso. RC4 é uma cifra de fluxo usada para proteger o tráfego da web. Verificou-se que tem múltiplas vulnerabilidades que o tornaram inseguro. O RC4 não deve ser utilizado.

Algoritmos de criptografia simétrica às vezes são classificados como uma cifra de bloco ou uma cifra de fluxo.
## Cifra de Bloco
As cifras de bloco transformam um bloco de texto simples de comprimento fixo em um bloco comum de texto cifrado de 64 ou 128 bits. As cifras de bloco comuns incluem DES com um tamanho de bloco de 64 bits e AES com um tamanho de bloco de 128 bits.
![[Cifra de Bloco.webp]]
## Cifra de Fluxo
**As cifras de fluxo** criptografam o texto simples um byte ou um bit de cada vez. As cifras de fluxo são basicamente uma cifra de bloco com um tamanho de bloco de um byte ou bit. As cifras de fluxo geralmente são mais rápidas do que as cifras de bloco porque os dados são criptografados continuamente. Exemplos de cifras de fluxo incluem RC4 e A5, que é usado para criptografar comunicações de telefone celular GSM.![[Cifra de Fluxo.webp]]
# Criptografia Assimétrica
Os algoritmos assimétricos, também chamados algoritmos de chave pública, são projetados para que a chave usada para criptografia seja diferente da chave usada para descriptografia, conforme mostrado na figura. A chave de descriptografia não pode, em uma quantidade razoável de tempo, ser calculada a partir da chave de criptografia e vice-versa.![[Criptografia Assimetrica.webp]]
Algoritmos assimétricos usam uma chave pública e uma chave privada. Ambas as chaves são capazes do processo de criptografia, mas a chave emparelhada complementar é necessária para descriptografia. O processo também é reversível. Os dados criptografados com a chave pública requerem a chave privada para descriptografar. Algoritmos assimétricos alcançam confidencialidade e autenticidade usando este processo.
Como nenhuma das partes possui um segredo compartilhado, é necessário usar comprimentos de chave muito longos. A criptografia  assimétrica pode usar comprimentos de chave entre 512 e 4.096 bits. Comprimentos de chave maiores ou iguais a 2.048 bits podem ser confiáveis, enquanto comprimentos de chave de 1.024 ou menores são considerados insuficientes.
Exemplos de protocolos que usam algoritmos de chave assimétrica incluem:

• Internet Key Exchange (IKE) - Este é um componente fundamental das VPNs IPsec.
• Secure Socket Layer (SSL) - Agora isso é implementado como TLS (Transport Layer Security) padrão da IETF.
• Secure Shell (SSH) - Este protocolo fornece uma conexão segura de acesso remoto a dispositivos de rede.
• Pretty Good Privacy (PGP) - Este programa de computador fornece privacidade e autenticação criptográficas. É frequentemente usado para aumentar a segurança das comunicações por email.

Os algoritmos assimétricos são substancialmente mais lentos que os algoritmos simétricos. Seu design é baseado em problemas computacionais, como fatorar números extremamente grandes ou calcular logaritmos discretos de números extremamente grandes.
Por serem lentos, algoritmos assimétricos geralmente são usados em mecanismos criptográficos de baixo volume, como assinaturas digitais e troca de chaves. No entanto, o gerenciamento de chaves de algoritmos assimétricos tende a ser mais simples que os algoritmos simetricos, porque geralmente uma das chaves de criptografia ou de descriptografia pode se tornar publica ou privada. Alguns dos algoritmos de descriptografia assimétricos são:

|Algoritmo|Tamanho da Chave (bits)|Descrição|
|---|---|---|
|**Diffie-Hellman (DH)**|512, 1024, 2048, 3072, 4096|Permite que duas partes concordem com uma chave compartilhada para criptografia. Sua segurança baseia-se na dificuldade de calcular o expoente a partir de uma potência modular.|
|**Digital Signature Standard (DSS) / Digital Signature Algorithm (DSA)**|512 - 1024|Utilizado para assinaturas digitais, baseado no esquema de assinatura ElGamal. A criação da assinatura tem velocidade semelhante ao RSA, mas a verificação é mais lenta.|
|**Rivest-Shamir-Adleman (RSA)**|512 até 2048|Algoritmo de chave pública baseado na dificuldade de fatoração de números grandes. Amplamente utilizado em comércio eletrônico e considerado seguro com chaves suficientemente longas.|
|**El Gamal**|512 - 1024|Baseado no contrato de chave Diffie-Hellman. Uma desvantagem é que a mensagem criptografada se torna muito grande, sendo usada principalmente para pequenas mensagens, como chaves secretas.|
|**Técnicas de Curva Elíptica**|224 ou superior|Pode ser aplicada a diversos algoritmos, como Diffie-Hellman e ElGamal. Sua principal vantagem é a possibilidade de usar chaves menores sem comprometer a segurança.|
## Confidencialidade 
Algoritmos assimétricos são usados para fornecer confidencialidade sem pré-compartilhar uma senha. O objetivo de confidencialidade dos algoritmos assimétricos é iniciado quando o processo de criptografia é iniciado com a chave pública.
O processo pode ser resumido usando a fórmula:

**Chave pública (criptografar) + chave privada (descriptografar) = confidencialidade**

Quando a chave pública é usada para criptografar os dados, a chave privada deve ser usada para descriptografar os dados. Apenas um host tem a chave privada; portanto, a confidencialidade é alcançada. Se a chave privada estiver comprometida, outro par de chaves deve ser gerado para substituir a chave comprometida. Seguindo a historia de Alice e Bob para nossa explicação 
<p style="text-align:center;"> Alice solicita e obtém a chave pública de Bob.</p>

![[Alice solicita e obtém a chave pública de Bob..png]]
<p style="text-align:center;">Alice usa a chave pública de Bob para criptografar uma mensagem usando um algoritmo acordado. Alice envia a mensagem criptografada para Bob.</p>
![[Alice usa a chave pública criptografar mensagem.png|center]]
<p style="text-align:center;">Bob então usa sua chave privada para descriptografar a mensagem. Como Bob é o único com a chave privada, a mensagem de Alice só pode ser descriptografada por Bob e, portanto, a confidencialidade é alcançada.</p>
![[Bob Descriptografa.webp|center]]
## Autenticação
 O objetivo de autenticação de algoritmos assimétricos é iniciado quando o processo de criptografia é iniciado com a chave privada. O processo pode ser resumido usando a fórmula:
 
**Chave privada (criptografar) + chave pública (descriptografar) = autenticação**

Quando a chave privada é usada para criptografar os dados, a chave pública correspondente deve ser usada para descriptografar os dados. Como apenas um host tem a chave privada, somente esse host poderia ter criptografado a mensagem, fornecendo autenticação do remetente. Normalmente, nenhuma tentativa é feita para preservar o sigilo da chave pública, portanto, qualquer número de hosts pode descriptografar a mensagem. Quando um host descriptografa uma mensagem com êxito usando uma chave pública, é confiável que a chave privada criptografou a mensagem, o que verifica quem é o remetente. Esta é uma forma de autenticação.
<p style="text-align:center;">Alice criptografa uma mensagem usando sua chave privada. Alice envia a mensagem criptografada para Bob. Bob precisa autenticar que a mensagem realmente veio de Alice.</p>
![[Alice usa chave privada.webp.webp|center]]

<p style="text-align:center;">Para autenticar a mensagem, Bob solicita a chave pública de Alice.</p>![[Bob usa chave.png]]
<p style="text-align:center;">Bob usa a chave pública de Alice para descriptografar a mensagem.</p>
![[bob descriptografa chave public.webp|center]]
## Integridade
Combinar os dois processos de criptografia assimétrica fornece confidencialidade, autenticação e integridade da mensagem.

O exemplo a seguir será usado para ilustrar esse processo. Neste exemplo, uma mensagem será cifrada usando a chave pública de Bob e um hash cifrado será criptografado usando a chave privada de Alice para fornecer confidencialidade, autenticidade e integridade.

<p style="text-align:center;">Alice quer enviar uma mensagem para Bob assegurando que só Bob pode ler o documento. Em outras palavras, Alice quer garantir a confidencialidade da mensagem. Alice usa a chave pública de Bob para cifrar a mensagem. Só Bob será capaz de decifrá-lo usando sua chave privada.</p>
![[Alica sua cahve pub Bob.webp|center]]
<p style="text-align:center;">Alice também quer garantir a autenticação e integridade da mensagem. A autenticação garante a Bob que o documento foi enviado por Alice, e a integridade garante que ele não foi modificado Alice usa sua chave privada para cifrar um hash da mensagem. Alice envia a mensagem criptografada com seu hash criptografado para Bob.</p>
![[Alice crip hash chave privada.webp|center]]
<p style="text-align:center;">Bob usa a chave pública de Alice para verificar se a mensagem não foi modificada. O hash recebido é igual ao hash determinado localmente com base na chave pública de Alice. Além disso, isso verifica se Alice é definitivamente o remetente da mensagem porque ninguém mais tem a chave privada de Alice. </p>
![[Bob savhe publi de alice pra descrip hash.webp|center]]
<p style="text-align:center;">Bob usa sua chave privada para decifrar a mensagem.</p>
![[Bob usa sua chave privada para decifrar a mensagem.webp|center]]
# Diffie-Hellman
Diffie-Hellman (DH) é um algoritmo matemático assimétrico que permite que dois computadores gerem um segredo compartilhado idêntico sem terem se comunicado antes. A nova chave compartilhada nunca é realmente trocada entre o remetente e o destinatário. No entanto, como as duas partes o conhecem, a chave pode ser usada por um algoritmo de criptografia para criptografar o tráfego entre os dois sistemas.

Aqui estão dois exemplos de casos em que DH é comumente usado:

- Os dados são trocados usando uma VPN IPsec
- Dados SSH são trocados
![[Diffie-Hellman.webp]]As cores na figura serão usadas em vez de números longos complexos para simplificar o processo de contrato de chave DH. A troca de chaves DH começa com Alice e Bob concordando com uma cor comum arbitrária que não precisa ser mantida em segredo. A cor combinada em nosso exemplo é amarelo.

Em seguida, Alice e Bob selecionarão uma cor secreta. Alice escolheu vermelho enquanto Bob escolheu azul. Essas cores secretas nunca serão compartilhadas com ninguém. A cor secreta representa a chave privada secreta escolhida de cada parte.

Alice e Bob agora misturam a cor comum compartilhada (amarelo) com suas respectivas cores secretas para produzir uma cor pública. Portanto, Alice vai misturar o amarelo com sua cor vermelha para produzir uma cor pública de laranja. Bob irá misturar o amarelo e o azul para produzir uma cor pública de verde.

Alice envia sua cor pública (laranja) para Bob e Bob envia sua cor pública (verde) para Alice.

Alice e Bob misturam a cor que receberam com a sua própria cor secreta original (vermelho para Alice e azul para Bob). O resultado é uma mistura final de cor marrom que é idêntica à mistura de cor final do parceiro. A cor marrom representa a chave secreta compartilhada resultante entre Bob e Alice.

A segurança do DH se baseia-se no fato de que ele usa números muito grandes em seus cálculos. Por exemplo, um número DH 1024 bits é aproximadamente igual a um número decimal de 309 dígitos. Considerando que um bilhão é 10 dígitos decimais (1.000.000.000), pode-se facilmente imaginar a complexidade de trabalhar não com um, mas com vários números decimais de 309 dígitos.

Diffie-Hellman usa diferentes grupos DH para determinar a força da chave que é usada no processo de acordo de chave. Os números de grupo mais altos são mais seguros, mas exigem tempo adicional para calcular a chave. O seguinte identifica os grupos DH suportados pelo Cisco IOS Software e seu valor de número primo associado:

- Grupo DH 1:768 bits
- Grupo DH 2:1024 bits
- Grupo DH 5:1536 bits
- Grupo DH 14:2048 bits
- Grupo DH 15:3072 bits
- Grupo DH 16:4096 bits

**Nota**: Um acordo de chave DH também pode ser baseado em criptografia de curva elíptica. Os grupos DH 19, 20 e 24, que são baseados em criptografia de curva elíptica, também são suportados pelo Cisco IOS Software.

Infelizmente, os sistemas de chave assimétrica são extremamente lentos para qualquer tipo de criptografia em massa. É por isso que é comum criptografar a maior parte do tráfego usando um algoritmo simétrico, como 3DES ou AES, e usar o algoritmo DH para criar chaves que serão usadas pelo algoritmo de criptografia.