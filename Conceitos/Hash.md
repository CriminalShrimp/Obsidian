**Sumário**
	**Tags:** #Segurança 
	**Conteúdo:** Maratona de Ciber Segurança Gratuita da Cisco.
	
----
O  hash é usado como uma ferramenta que "garante" a integridade dos dados ao considerar dados binários (por exemplo, uma mensagem) e produzir uma representação de comprimento fixo chamada de valor de hash. Além disso ela também pode ser em autenticações, usando uma função de hash criptográfico para substituir senhas de texto simples ou chaves de criptografia.

Uma função hash criptográfica tem as seguintes propriedades:

- A entrada pode ser de qualquer comprimento.

- A saída tem um comprimento fixo.

- A função hash é unidirecional e não é reversível.

- Dois valores de entrada diferentes quase nunca resultarão no mesmo hash.

O Instituto **N**acional de **P**adrões e **T**ecnologia (**NIST**) dos EUA desenvolveu o SHA, o algoritmo especificado no padrão hash seguro (SHS).

**Observação:** o Message Digest 5 (MD5) foi outro algoritmo de hash popular que não é mais considerado seguro.

Após algum tempo surgiu o SHA-2, que substituiu o SHA-1 com quatro funções hash adicionais para formar a família de SHA:

- SHA-224 (224 bits)

- SHA-256 (256 bits)

- SHA-384 (384 bits)

- SHA-512 (512 bits)

O hash é baseado em uma função matemática unilateral que é relativamente fácil de calcular, mas significativamente mais difícil de reverter. A moagem de café é uma boa analogia de função unidirecional. É fácil moer grãos de café, mas é quase impossível unir novamente todos os pedaços para reconstruir os grãos originais.

![[Hash.webp|Hash]]


Como mostrado na figura a, uma função hash leva um bloco variável de dados binários, e produz uma representação condensada de comprimento fixo, chamado hash.

Com funções hash, é computacionalmente inviável que dois conjuntos diferentes de dados apresentem a mesma saída hash. Cada vez que os d**ados são modificados** ou alterados, o valor de **hash também muda**. Por isso, muitas vezes esses valor são **chamados de impressões digitais**. Eles podem ser usados para detectar arquivos de dados duplicados, alterações de versão de arquivo e aplicativos semelhantes, esses valores são usados para proteger contra uma alteração acidental ou intencional dos dados, ou corrupção acidental dos dados. E também em **computação forense** para garantir a não alteração dos dados durante a investigação.

Os algoritmos hash transformam qualquer quantidade de dados em um hash digital ou impressão digital de tamanho fixo. Ninguém pode reverter um hash digital para descobrir a entrada original. Se a entrada mudar completamente, o resultado do hash sera diferente. Isso funciona para proteger as senhas por exemplo. Um sistema precisa armazenar uma senha de modo a protegê-la, mas que ainda possa verificar se a senha do usuário está correta. Para decifrar um hash, um invasor deve adivinhar a senha.

![[Hash Senha.webp]]

## Operação de Criptografia

Matematicamente, a equação **_h = H (x)_** é usada para explicar como um algoritmo de hash opera. Como mostrado na figura, uma função hash **H** leva uma entrada **x** e retorna um valor hash string de tamanho fixo **h**.

![[Operação Hash.webp]]

Uma função hash criptográfica deve ter as seguintes propriedades:

- A entrada pode ser de qualquer comprimento.

- A saída tem um comprimento fixo.

- H é relativamente fácil de calcular para qualquer x.

- h para X é um caminho e não reversível.

- h é livre de colisões, o que significa que dois valores de entrada diferentes resultarão em valores de hash diferentes.

Se uma função hash é difícil de inverter, ela é considerada um hash unidirecional. Difícil de inverter significa que, dado um valor de hash de _h, é computacionalmente inviável encontrar uma entrada para x tal que_ _H=h (x)._

## MD5 e SHA

As funções de hash são usadas para garantir a integridade de uma mensagem. Eles garantem que os dados não foram alterados acidentalmente ou intencionalmente. Na figura, o remetente está enviando uma transferência de dinheiro de US $ 100 para Alex. O remetente deseja garantir que a mensagem não seja alterada acidentalmente no caminho para o destinatário. Alterações deliberadas que são feitas por um ator ameaça ainda são possíveis.

![[md5 e sha.webp]]

Existem quatro funções hash bem conhecidas:

- **MD5 de 128 bits:** Desenvolvido por Ron Rivest e usado em uma variedade de aplicações de internet, MD5 é uma função unidirecional que produz uma mensagem hash de 128 bits. MD5 é considerado um algoritmo legado e deve ser evitado.

- **SHA-1:** Desenvolvido pela Agência de Segurança Nacional dos EUA (NSA) em 1995. É muito semelhante às funções hash MD5. O SHA-1 cria uma mensagem de 160 bits e é um pouco mais lento que o MD5. O SHA-1 possui falhas conhecidas e é um algoritmo antigo e por conta disso não é mais usado.

- **SHA-2:** Inclui SHA-224 (224 bits), SHA-256 (256 bits), SHA-384 (384 bits) e SHA-512 (512 bits). Se você estiver usando SHA-2, então os algoritmos SHA-256, SHA-384 e SHA-512 devem ser usados sempre que possível.

- **SHA-3**- SHA-3 é o mais novo algoritmo de hash e foi introduzido pelo NIST como uma alternativa e eventual substituição para a família SHA-2 de algoritmos de hash. SHA-3 inclui SHA3-224 (224 bits), SHA3-256 (256 bits), SHA3-384 (384 bits) e SHA3-512 (512 bits). A família SHA-3 são algoritmos de última geração e devem ser usados sempre que possível.

Embora o hashing possa ser usado para detectar alterações acidentais, ele não pode ser usado para proteger contra alterações deliberadas feitas por um agente de ameaça. Não há informações de identificação única do remetente no procedimento de hash. Isso significa que qualquer pessoa pode processar um hash para quaisquer dados, desde que tenha a função hash correta. Por exemplo, quando a mensagem atravessa a rede, um invasor em potencial pode interceptar a mensagem, alterá-la, recalcular o hash e anexá-lo à mensagem. O dispositivo receptor só validará contra o hash que estiver anexado. Em outra palavras em certo nível ele é vulnerável a um ataque [[Man-in-the-Middle (MITM)]]. Para adicionar autenticação de origem e garantia de integridade, use um o  método MAC (Message Authentication Code). Com destaque para o HMAC, que é usado em muitos sistemas, incluindo SSL, IPsec e SSH.

## Hash Message Authentication Code (HMAC)

Um Algoritmo HMAC é calculado usando qualquer algoritmo criptográfico que combina uma função hash criptográfica com uma chave secreta. Somente o remetente e o destinatário têm conhecimento da chave secreta e agora a saída da função hash depende dos dados de entrada e da chave secreta. Apenas as partes que têm acesso a essa chave secreta podem calcular o resultado de uma função HMAC. Isso derrota os ataques man-in-the-middle e fornece autenticação da origem dos dados. Se duas partes compartilharem uma chave secreta e usarem as funções HMAC para autenticação, uma mensagem HMAC adequadamente construída, a parte recebeu indica que a outra parte foi a originadora da mensagem. Isso ocorre porque a outra parte possui a chave secreta.

![[Algoritmo HMAC.webp]]

### Criação do valor HMAC

Usando a figura para ajudar a entender como o HMAC funciona, o dispositivo de envio insere dados (como o pagamento de Terry Smith de US $ 100 e a chave secreta) no algoritmo de hash e calcula o HMAC Digest (resultado) de comprimento fixo. Esse resultado é anexado à mensagem e enviado ao destinatário.

![[Criaçã HMAC.webp]]

### Verificação valor HMAC

Na figura, o dispositivo receptor remove o Digest (resultado) da mensagem e usa a mensagem de texto sem formatação com sua chave secreta como entrada na mesma função de hash. Se o Digest calculado pelo dispositivo receptor for igual ao resumo enviado, a mensagem não foi alterada. Adicionalmente, a origem da mensagem é autenticada porque apenas o remetente possui uma cópia da chave secreta compartilhada.

![[Verificalçao HMAC.webp]]

# SALT

O salting server para torna o hash de senhas ainda mais seguro. Se dois usuários têm a mesma senha, eles também terão os mesmos hashes de senha. Um SALT, que é uma cadeia de caracteres aleatória, é uma entrada adicional à senha antes de ser feito o hash. Isso cria um resultado de hash diferente para as duas senhas, conforme mostrado na figura. Um banco de dados armazena o hash e o SALT.

![[SALT.webp]]

Um **C**ryptographically **S**ecure **P**seudo-**R**andom **N**umber **G**enerator (**CSPRNG**) ou em português Gerador Numérico Pseudo Randômico de Criptografia Segura é a melhor opção para gerar o salt. Eles geram um número aleatório com um alto nível de aleatoriedade e é completamente imprevisível, portanto, é criptograficamente confiável. As recomendações a seguir ajudarão a garantir a implementação bem-sucedida da salt:

- O salt deve ser exclusivo para cada senha de usuário.

- Nunca reutilize um salt.

- O tamanho do sal deve corresponder ao tamanho da saída da função hash.

- Sempre execute o hash no servidor em um aplicativo da Web.

O uso de uma técnica chamada **alongamento de chave (key stretching)** também ajudará a proteger contra ataques. O alongamento de chaves faz com que as tentativas de descobrir senhas trabalhem muito lentamente. Isso impede torna um hardware de ponta que poderia calcular bilhões de hashes por segundo menos eficaz.