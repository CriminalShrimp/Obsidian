### Snort - Falar sbre
As regras de Snort consistem em duas seções, o cabeçalho da regra e as opções da regra. O cabeçalho da regra contém a ação, o protocolo, os endereços IP de origem e destino e as máscaras de rede e as informações da porta de origem e destino. A seção Opções de regra contém mensagens de alerta e informações sobre quais partes do pacote devem ser inspecionadas para determinar se a ação da regra deve ser executada.

**Estrutura da regra Snort**

alert ip any any -> any any (msg:"GPL ATTACK_RESPONSE id check returned root"; content:"uid=0|28|root|29|"; fast_pattern:only; classtype:bad-unknown; sid:2100498; rev:8;)
/nsm/server_data/securityonion/rules/seconion-eth1-1/downloaded.rules:Line 692

| Componente         | Exemplo (abreviado...)                               | Explicação                                                                                                                                                               |
| ------------------ | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| cabeçalho da regra | alert ip any any -> any any                          | Contém a ação a ser tomada, endereços e porta de origem e destino e a direção do fluxo de tráfego                                                                        |
| opções de regra    | (msg:”GPL ATTACK_RESPONSE ID CHECK RETURNED ROOT”;…) | Inclui a mensagem a ser exibida, detalhes do conteúdo do pacote, tipo de alerta, ID de origem e detalhes adicionais, como uma referência para a regra ou vulnerabilidade |
| local da regra     | /nsm/server_data/securityonion/rules/…               | Adicionado pelo Sguil para indicar a localização da regra na estrutura do arquivo Cebola Segurança e no arquivo de regra especificado                                    |

**O cabeçalho da regra**

O cabeçalho da regra contém a ação, o protocolo, o endereçamento e as informações da porta. Além disso, a direção do fluxo que acionou o alerta é indicada, a estrutura da parte do cabeçalho é consistente entre as regras de alerta Snort.
O Snort pode ser configurado para usar variáveis para representar endereços IP internos e externos. Essas variáveis, $HOME_NET e $EXTERNAL_NET, servem para simplificam a criação de regras, eliminando a necessidade de especificar endereços e máscaras específicos para cada regra, também permite que endereços IP individuais, blocos de endereços ou listas de ambos sejam especificados. Os intervalos de portas podem ser especificados separando os valores superior e inferior do intervalo com dois pontos.

**Estrutura do cabeçalho da regra Snort**

alert ip any any -> any any (msg:"GPL ATTACK_RESPONSE id check returned root"; content:"uid=0|28|root|29|"; fast_pattern:only; classtype:bad-unknown; sid:2100498; rev:8;)/nsm/server_data/securityonion/rules/seconion-eth1-1/downloaded.rules:Line 692

|Componente|Explicação|
|---|---|
|alerta|a ação a ser tomada é emitir um alerta, outras ações são registradas e passadas|
|ip|o protocolo|
|any any|a fonte especificada é qualquer endereço IP e qualquer porta da Camada 4|
|->|a direção do fluxo é da origem para o destino|
|any any|o destino especificado é qualquer endereço IP e qualquer porta da Camada 4|

**As Opções de Regra**

A estrutura da seção de opções da regra é variável, contém a mensagem de texto que identifica o alerta, metadados sobre o alerta, como um URL que fornece informações de referência para o alerta,  informações como o tipo de regra e um identificador numérico exclusivo podem ser incluídos. O manual de usuários do Snort, que pode ser encontrado na internet, fornece detalhes sobre regras e como criá-las.
Mensagens de regra de "snifar" podem incluir a origem da regra. Três fontes comuns para as regras do Snort são:

- **GPL** - Regras mais antigas do Snort que foram criadas pelo Sourcefire e distribuídas sob uma GPLv2. Inclui Snort SIDs 3464 e abaixo. O conjunto de regras GPL pode ser baixado do site do Snort e está incluído no Onion Security.
- **ET**- Regras Snort de ameaças emergentes. Emerging Threats é um ponto de coleta para regras Snort de várias fontes. As regras ET são de código aberto sob uma licença BSD. O conjunto de regras ET contém regras de várias categorias. Um conjunto de regras ET está incluído com Cebola Segurança. Emerging Threats é uma divisão da Proofpoint, Inc.
- **VRT** - Essas regras estão imediatamente disponíveis para assinantes e são liberadas para usuários registrados 30 dias após sua criação, com algumas limitações. Eles agora são criados e mantidos pelo Cisco Talos.

Alertas que não são gerados pelas regras do Snort são identificados pelas tags OSSEC ou PADS, entre outras. Além disso, regras locais personalizadas podem ser criadas.

**Estrutura de Opções de Regras Snort**
alert ip any any -> any any (msg:"GPL ATTACK_RESPONSE id check returned root"; content:"uid=0|28|root|29|"; fast_pattern:only; classtype:bad-unknown; sid:2100498; rev:8;
/nsm/server_data/securityonion/rules/seconion-eth1-1/downloaded.rules:Line 692

|Componente|Explicação|
|---|---|
|msg:|Texto que descreve o alerta.|
|content:|Refere-se ao conteúdo do pacote. Neste caso, um alerta será enviado se o texto literal "uid=O(root)" aparecer em qualquer lugar nos dados do pacote. Valores especificando a localização do texto na carga de dados podem ser fornecidos.|
|reference:|Isso não é mostrado na figura. Muitas vezes, é um link para uma URL que fornece mais informações sobre a regra. Nesse caso, o sid é hipervinculado à origem da regra na Internet.|
|classtype:|Uma categoria para o ataque. O Snort inclui um conjunto de categorias padrão que têm um dos quatro valores de prioridade.|
|sid:|Um identificador numérico exclusivo para a regra.|
|rev:|A revisão da regra que é representada pelo sid.|

### Suricata - falar sobre