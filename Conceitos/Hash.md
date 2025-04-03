O  hash é uma ferramenta que garante a integridade dos dados ao considerar dados binários (por exemplo, uma mensagem) e produzir uma representação de comprimento fixo chamada de valor de hash (por exemplo, um message digest).

Hashes são usados para verificar e garantir a integridade dos dados. A ferramenta de hash também pode verificar a autenticação. Ele funciona usando uma função de hash criptográfico para substituir senhas de texto simples ou chaves de criptografia.

Uma função hash criptográfica tem as seguintes propriedades:

- A entrada pode ser de qualquer comprimento.
- A saída tem um comprimento fixo.
- A função hash é unidirecional e não é reversível.
- Dois valores de entrada diferentes quase nunca resultarão no mesmo hash.

O Instituto Nacional de Padrões e Tecnologia (NIST) dos EUA desenvolveu o SHA, o algoritmo especificado no padrão hash seguro (SHS). O NIST publicou o SHA-1 em 1994.

**Observação:** o Message Digest 5 (MD5) foi outro algoritmo de hash popular que não é mais considerado seguro.

O SHA-2 substituiu o SHA-1 com quatro funções hash adicionais para formar a família de SHA:

- SHA-224 (224 bits)
- SHA-256 (256 bits)
- SHA-384 (384 bits)
- SHA-512 (512 bits)

O SHA-2 é um algoritmo mais forte e está substituindo o MD5. SHA-256, SHA-384 e SHA-512 são os algoritmos de próxima geração.

===============================================================
Hashes são usados para verificar e garantir a integridade dos dados. O hash é baseado em uma função matemática unilateral que é relativamente fácil de calcular, mas significativamente mais difícil de reverter. A moagem de café é uma boa analogia de função unidirecional. É fácil moer grãos de café, mas é quase impossível unir novamente todos os pedaços para reconstruir os grãos originais. A função de hash criptográfico também pode ser usada para verificar a autenticação.![[Hash-20250403060418222.webp]]
Como mostrado na figura, uma função hash leva um bloco variável de dados binários, chamado de mensagem, e produz uma representação condensada de comprimento fixo, chamado hash. O hash resultante também é às vezes chamado de mensagem digest, digest ou impressão digital.

Com funções hash, é computacionalmente inviável que dois conjuntos diferentes de dados apresentem a mesma saída hash. Cada vez que os dados são modificados ou alterados, o valor de hash também muda. Por isso, muitas vezes os valores criptográficos de hash são chamados de impressões digitais. Eles podem ser usados para detectar arquivos de dados duplicados, alterações de versão de arquivo e aplicativos semelhantes. Esses valores são usados para proteger contra uma alteração acidental ou intencional dos dados ou corrupção acidental dos dados.

A função hash criptográfico é aplicada em muitas situações diferentes para autenticação de entidade, integridade de dados e fins de autenticidade de dados.
## Operação de hash criptográfico
Matematicamente, a equação **_h = H (x)_** é usada para explicar como um algoritmo de hash opera. Como mostrado na figura, uma função hash H leva uma entrada x e retorna um valor hash string de tamanho fixo h.![[Operação Hash.webp]]O exemplo na figura resume o processo matemático. Uma função hash criptográfica deve ter as seguintes propriedades:

- A entrada pode ser de qualquer comprimento.
- A saída tem um comprimento fixo.
- H(x) é relativamente fácil de calcular para qualquer x.
- H (x) é um caminho e não reversível.
- H(x) é livre de colisões, o que significa que dois valores de entrada diferentes resultarão em valores de hash diferentes.

Se uma função hash é difícil de inverter, ela é considerada um hash unidirecional. Difícil de inverter significa que, dado um valor de hash de _h, é computacionalmente inviável encontrar uma entrada para x tal que_ _H=h (x)._
## MD5 e SHA
As funções de hash são usadas para garantir a integridade de uma mensagem. Eles garantem que os dados não foram alterados acidentalmente ou intencionalmente. Na figura, o remetente está enviando uma transferência de dinheiro de US $ 100 para Alex. O remetente deseja garantir que a mensagem não seja alterada acidentalmente no caminho para o destinatário. Alterações deliberadas que são feitas por um ator ameaça ainda são possíveis.![[md5 e sha.webp]]
Existem quatro funções hash bem conhecidas:

- **MD5 com digest de 128 bits** - Desenvolvido por Ron Rivest e usado em uma variedade de aplicações de internet, MD5 é uma função unidirecional que produz uma mensagem hash de 128 bits. MD5 é considerado um algoritmo legado e deve ser evitado e usado apenas quando não houver alternativas melhores disponíveis. Recomenda- se que SHA-2 ou SHA-3 sejam usados em vez disso.
- **SHA-1 -** Desenvolvido pela Agência de Segurança Nacional dos EUA (NSA) em 1995. É muito semelhante às funções hash MD5. Existem várias versões. O SHA-1 cria uma mensagem de 160 bits e é um pouco mais lento que o MD5. O SHA-1 possui falhas conhecidas e é um algoritmo antigo.
- **SHA-2 –** Desenvolvido pela NSA. Inclui SHA-224 (224 bits), SHA-256 (256 bits), SHA-384 (384 bits) e SHA-512 (512 bits). Se você estiver usando SHA-2, então os algoritmos SHA-256, SHA-384 e SHA-512 devem ser usados sempre que possível.
- **SHA-3**- SHA-3 é o mais novo algoritmo de hash e foi introduzido pelo NIST como uma alternativa e eventual substituição para a família SHA-2 de algoritmos de hash. SHA-3 inclui SHA3-224 (224 bits), SHA3-256 (256 bits), SHA3-384 (384 bits) e SHA3-512 (512 bits). A família SHA-3 são algoritmos de última geração e devem ser usados sempre que possível.

Embora o hashing possa ser usado para detectar alterações acidentais, ele não pode ser usado para proteger contra alterações deliberadas feitas por um agente de ameaça. Não há informações de identificação única do remetente no procedimento de hash. Isso significa que qualquer pessoa pode processar um hash para quaisquer dados, desde que tenha a função hash correta.

Por exemplo, quando a mensagem atravessa a rede, um invasor em potencial pode interceptar a mensagem, alterá-la, recalcular o hash e anexá-lo à mensagem. O dispositivo receptor só validará contra o hash que estiver anexado.

Portanto, hash é vulnerável a ataques man in the middle e não oferece segurança aos dados transmitidos. Para fornecer autenticação de integridade e origem, é necessário algo mais.

**Observação:** Os algoritmos de hash protegem somente contra alterações acidentais e não protegem os dados contra alterações feitas deliberadamente por um ator de ameaça.

## Autenticação de Origem
Para adicionar autenticação de origem e garantia de integridade, use um código de autenticação de mensagem hash com chave (HMAC). HMACs usam uma chave secreta adicional como entrada à função hash.

**Observação:** Outros métodos MAC (Message Authentication Code) também são usados. No entanto, o HMAC é usado em muitos sistemas, incluindo SSL, IPsec e SSH.
### Algoritmo HMAC
Conforme mostrado na figura, um HMAC é calculado usando qualquer algoritmo criptográfico que combina uma função hash criptográfica com uma chave secreta. As funções de hash são a base do mecanismo de proteção dos HMACs.

Somente o remetente e o destinatário têm conhecimento da chave secreta e agora a saída da função hash depende dos dados de entrada e da chave secreta. Apenas as partes que têm acesso a essa chave secreta podem calcular o digest de uma função HMAC. Isso derrota os ataques man-in-the-middle e fornece autenticação da origem dos dados.

Se duas partes compartilharem uma chave secreta e usarem as funções HMAC para autenticação, uma mensagem HMAC adequadamente construída, a parte recebeu indica que a outra parte foi a originadora da mensagem. Isso ocorre porque a outra parte possui a chave secreta.![[Algoritmo HMAC.webp|center]]
### Criação do valor HMAC
Conforme mostrado na figura, o dispositivo de envio insere dados (como o pagamento de Terry Smith de US $ 100 e a chave secreta) no algoritmo de hash e calcula o HMAC Digest de comprimento fixo. Esse Digest autenticado é anexado à mensagem e enviado ao destinatário.
![[Criaçã HMAC.webp|center]]

### Verificação valor HMAC
Na figura, o dispositivo receptor remove o Digest da mensagem e usa a mensagem de texto sem formatação com sua chave secreta como entrada na mesma função de hash. Se o Digest calculado pelo dispositivo receptor for igual ao resumo enviado, a mensagem não foi alterada. Adicionalmente, a origem da mensagem é autenticada porque apenas o remetente possui uma cópia da chave secreta compartilhada. A função HMAC garantiu a autenticidade da mensagem.![[Verificalçao HMAC.webp|center]]
