So para n ficar vazio A criptografia é a ciência de criar e quebrar códigos.

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

Na figura, Alice e Bob têm chaves idênticas para um único cadeado. A troca de chaves aconteceu antes de enviar quaisquer mensagens secretas. Alice escreve uma mensagem secreta e a coloca em uma pequena caixa trancada com o cadeado. Ela manda a caixa para Bob. A mensagem está segura e trancada dentro da caixa, à medida que a caixa segue seu caminho através do sistema de correios. Quando Bob recebe a caixa, ele usa a chave para destrancar o cadeado e recuperar a mensagem. Bob pode usar a mesma caixa e cadeado para enviar uma resposta secreta para Alice.![[Criptografia Simétrica.png]]

Hoje, algoritmos de criptografia simétrica são comumente usados com o tráfego VPN. Isso ocorre porque os algoritmos simétricos usam menos recursos da CPU do que os algoritmos de criptografia assimétrica. Isso permite que a criptografia e a descriptografia de dados sejam rápidas ao usar uma VPN. Ao usar algoritmos de criptografia simétrica, como qualquer outro tipo de criptografia, quanto maior a chave, mais tempo levará para alguém descobrir a chave. A maioria das chaves de criptografia tem entre 112 e 256 bits. Para garantir que a criptografia é segura, um comprimento mínimo de chave de 128 bits deve ser usado. Use uma chave mais longa para comunicações mais seguras .Alguns algoritmos de criptografia são  
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
