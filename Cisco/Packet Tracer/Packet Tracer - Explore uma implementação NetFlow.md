# Objetivos

Parte 1: Observar registros de fluxo NetFlow - Uma direção

Parte 2: Observe os registros NetFlow para uma sessão que entra e sai do coletor

# Histórico/Cenário

Nesta atividade, você usará o Packet Tracer para criar tráfego de rede e observar os registros de fluxo NetFlow correspondentes em um coletor NetFlow. O Packet Tracer oferece uma simulação básica da funcionalidade NetFlow. Não é um substituto para aprender NetFlow em equipamentos físicos. Algumas diferenças podem existir entre registros de fluxo NetFlow gerados pelo Packet Tracer e por registros criados por equipamentos de rede completos.

# Instruções

## Parte 1: Observar registros de fluxo de NetFlow - One Direction

### Etapa 1: Abra o NetFlow collector.

a.     No NetFlow collector, clique na guia **Desktop** . Clique no icone **Netflow Collector** .

b.     Clique no botão de opção **On** para ativar o coletor conforme necessário. Posicione e dimensione a janela de forma que seja visível na janela de topologia do Packet Tracer.

### Etapa 2: Ping no gateway padrão do PC-1.

a.     CliquePC-1.

b.     Abra a guia **Desktop** e clique no icone **Command Prompt** .

c.     Entre o comando **ping** para testar a conectividade com o gateway padrão em 10.0.0.1.

C:\> **ping 10.0.0.1**

d.     Após um breve atraso, a tela do NetFlow collector exibirá um gráfico de pizza.

**Nota**: O primeiro conjunto de pings pode não ser enviado ao NetFlow collector porque o processo ARP deve primeiro resolver os endereços IP e MAC. Se após 30 segundos, um gráfico de pizza não aparecer, execute ping no gateway padrão novamente.

e.     Clique no gráfico de pizza ou na entrada da legenda para exibir os detalhes do registro de fluxo.

f.      O registro de fluxo terá entradas semelhantes às da tabela abaixo. Seus carimbos de data / hora serão diferentes.

|Entrada|Valor|Explicação|
|---|---|---|
|Contribuição do tráfego|100% (1/1)|Esta é a proporção de todo o tráfego representado por esse fluxo.|
|IPV4 SOURCE ADDRESS|10.0.0.10|Este é o endereço IP de origem dos pacotes de fluxo.|
|IPV4 DESTINATION ADDRESS|10.0.0.1|Este é o endereço IP de destino dos pacotes de fluxo.|
|TRNS SOURCE PORT|0|Esta é a porta de origem da camada de transporte. O valor é 0 porque este é um fluxo ICMP.|
|TRNS DESTINATION PORT|0|Esta é a porta de destino da camada de transporte. O valor é 0 porque este é um fluxo ICMP.|
|PROTOCOLO IP|1|Isso identifica o serviço da Camada 4, normalmente 1 para ICMP, 6 para TCP e 17 para UDP.|
|timestamp primeiro|00:47:49.593|Este é o carimbo de data/hora para o início do fluxo.|
|carimbo de data/hora|00:47:52.598|Este é o carimbo de data/hora do último pacote no fluxo.|
|flags TCP|0x00|Este é o valor do flag TCP. Nesse caso, nenhuma sessão TCP foi envolvida porque o protocolo é ICMP.|
|contador de bytes|512|Este é o número de bytes no fluxo.|
|contador de pacotes|4|Este é o número de pacotes no fluxo.|
|entrada da interface|Gig0/0|Esta é a interface do Flow exporter que coletou o fluxo na direção de entrada (na interface do dispositivo de monitoramento).|
|saída da interface|Null|Esta é a interface do Flow exporter que coletou o fluxo na direção de saída (fora da interface do dispositivo de monitoramento). O valor é “Nulo” porque este era um ping para a interface de entrada.|

Linha em branco, sem informações adicionais

Nesse caso, o fluxo representa o ping ICMP do host 10.0.0.10 para 10.0.0.1. Quatro pacotes de ping estavam no fluxo. Os pacotes inseridos na interface G0/0 do exportador.

**Nota**: Nesta atividade, o roteador Edge foi configurado como um flow exporter do NetFlow. A interface LAN é configurada para monitorar fluxos que entram na rede local. A interface serial foi configurada para coletar fluxos que entram na internet. Isso foi feito para simplificar esta atividade.

Para ver o tráfego que corresponde a uma sessão bidirecional completa, o NetFlow Flow exporter precisaria ser configurado para coletar fluxos que entram e saem de uma rede.

### Etapa 3: Criar tráfego adicional.

a.     Clique **PC-2 > Desktop**.

b.     Abra um prompt de comando e **ping** o default gateway 10.0.0.1.

#### Pergunta:

O que você espera ver nos registros de fluxo do NetFlow collector? As estatísticas do registro de fluxo existente serão alteradas ou um novo fluxo aparecerá no gráfico de pizza?

Área de Resposta

Um fluxo é definido como um fluxo unidirecional de pacotes que compartilham os mesmos endereços IP de origem e destino e números de porta, bem como o mesmo protocolo IP. Como esse tráfego terá um endereço IP de origem diferente, ele criará um novo registro de fluxo representado por uma nova parte codificada por cores do gráfico de pizza.

Ocultar resposta

c.     Retorne ao PC-1 e repita o ping para o gateway.

#### Pergunta:

Como esse tráfego será representado? Como um novo segmento no gráfico de pizza ou ele modificará os valores no registro de fluxo existente?

Área de Resposta

Os detalhes do fluxo original permanecem os mesmos, no entanto, a proporção de tráfego representada pelo fluxo duplicou.

Ocultar resposta

d.     Emita pings de PC-3 e PC-4 para o endereço de gateway padrão.

O que deve acontecer com a tela no coletor de fluxo?

Área de Resposta

Um novo registro deve aparecer para cada fluxo.

Ocultar resposta

## Parte 2: Observe os registros do NetFlow para uma sessão que entra e sai do coletor

O NetFlow exporter foi configurado para coletar fluxos que saem da LAN e entram no roteador da Internet.

### Etapa 1: Acessar o servidor Web por endereço IP.

Antes de continuar, desligue e ligue o NetFlow collector para limpar os fluxos.

a.     Clique na guia **NetFlow Collector > Physical** .

b.     Clique no botão de energia vermelho para desligar o servidor. Em seguida, clique nele novamente para ligar o servidor novamente. (**Nota**: Pode ser necessário rolar ou diminuir o zoom.)

c.     No NetFlow Collector, clique na guia **Desktop** .

d.     Clique no ícone Netflow Collector. Clique no botão de opção “On” para ativar o coletor. Feche a janela NetFlow Collector.

e.     Antes de acessar um servidor web do PC-1, preveja quantos fluxos haverá no gráfico de pizza? Explique.

Área de Resposta

Como os fluxos que saem da LAN e entram no roteador de borda de fora serão coletados, haverá dois fluxos, um para os pacotes de solicitação enviados ao servidor e um para os dados retornados do servidor.

Ocultar resposta

A partir do seu conhecimento de protocolos de rede e NetFlow, preveja os valores para as solicitações de página da Web que saem da LAN.

|Campo de registro|Valor|Diretrizes|
|---|---|---|
|Endereço IP de origem|Área de Resposta|N/D|
|Endereço IP de destino|Área de Resposta|N/D|
|Porta de origem|1025—5000 (padrão do MS Windows, que é o que o PT usa.|Este é um valor aproximado que é criado dinamicamente.|
|Porta de destino|Área de Resposta|N/D|
|Interface de entrada|Área de Resposta|N/D|
|Interface de saída|Área de Resposta|N/D|

Linha em branco, sem informações adicionais

Clique em **Mostrar resposta** em uma tabela de respostas de amostra.

|Campo de registro|Valor|Diretrizes|
|---|---|---|
|Endereço IP de origem|10.0.0.10|N/D|
|Endereço IP de destino|192.0.2.100|N/D|
|Porta de origem|1025—5000 (padrão do MS Windows, que é o que o PT usa.|Este é um valor aproximado que é criado dinamicamente.|
|Porta de destino|80|N/D|
|Interface de entrada|Gig0/0|N/D|
|Interface de saída|Se0/0/1|N/D|

Ocultar resposta

Linha em branco, sem informações adicionais

Preveja os valores para a resposta da página da Web que entra no roteador do exportador NetFlow a partir da Internet.

|Campo de registro|Valor|Diretrizes|
|---|---|---|
|Endereço IP de origem|Área de Resposta|N/D|
|Endereço IP de destino|Área de Resposta|N/D|
|Porta de origem|Área de Resposta|N/D|
|Porta de destino|1025-5000|Este é o valor que foi atribuído aleatoriamente a partir do intervalo de portas efêmeras.|
|Interface de entrada|Área de Resposta|N/D|
|Interface de saída|Área de Resposta|N/D|

Linha em branco, sem informações adicionais

Clique em **Mostrar resposta** em uma tabela de respostas de amostra.

|Campo de registro|Valor|Diretrizes|
|---|---|---|
|Endereço IP de origem|192.0.2.100|N/D|
|Endereço IP de destino|10.0.0.10|N/D|
|Porta de origem|80|N/D|
|Porta de destino|1025-5000|Este é o valor que foi atribuído aleatoriamente a partir do intervalo de portas efêmeras.|
|Interface de entrada|Se0/0/1|N/D|
|Interface de saída|Gig0/0|N/D|

Ocultar resposta

Linha em branco, sem informações adicionais

f.      Clique **PC-1 > Desktop**. Feche a janela do prompt de comando, se necessário. Clique no ícone do navegador da web.

g.     No navegador da Web para PC-1, digite 192.0.2.100 e clique em**Go**. A página da Web do site de exemplo será exibida.

h.     Após um breve atraso, um novo gráfico de pizza aparecerá no coletor NetFlow. Você verá pelo menos dois segmentos de pizza para a solicitação HTTP e resposta. Talvez você veja um terceiro segmento se o cache ARP para PC-1 expirou.

i.      Clique em cada segmento de pizza HTTP para exibir o registro e verificar suas previsões.

j.      Clique no link para a página de direitos autorais.

#### Perguntas:

O que aconteceu? Explique. (Dica: compare o número da porta no host para os fluxos.)

Área de Resposta

Como o host abriu uma nova porta de origem para a nova solicitação para o servidor Web, dois novos fluxos foram criados.

Ocultar resposta

Compare os fluxos. Além do carimbo de data/hora óbvio, endereço IP de origem e destino, porta e interfaces, diferenças, o que mais é diferente entre os fluxos de solicitação e resposta?

Área de Resposta

Os flags TCP são diferentes. Os flags para os fluxos de solicitação são 0x02 e os sinalizadores de resposta são 0x12. Direcione os alunos a procurar esses valores fazendo uma pesquisa no Google em termos como “valores para os flags tcp”. Está além do escopo deste laboratório explicar como os valores são determinados, mas o significado de 0x02 será SYN (decimal 2) para o fluxo de solicitação e será SYN-ACK (decimal 18) para os fluxos de resposta.

Ocultar resposta

### Etapa 2: Acessar o servidor Web por URL.

a.     Desligue e ligue o NetFlow collector para limpar os fluxos.

b.     Ative o serviço Netflow Collector.

c.     Antes de acessar o servidor Web por seu URL.

#### Pergunta:

O que você acha que verá na exibição do NetFlow collector?

Área de Resposta

Você verá quatro fluxos. Como o site é acessado por URL, uma consulta DNS deve ocorrer. Dois fluxos representam a consulta DNS e a resposta. Os outros dois fluxos representam a solicitação HTTP e a resposta.

Ocultar resposta

d.     No PC-1, entre **www.example.com** no campo URL e pressione **Go**.

e.     Depois que os fluxos forem exibidos, inspecione cada registro de fluxo.

#### Pergunta:

Quais valores você vê para o campo de protocolo IP do registro de fluxo? O que significam esses valores?

Área de Resposta

Os campos de protocolo IP foram discutidos na tabela na Parte 1, Passo 1 deste laboratório. O valor 6 é para TCP e é usado para o tráfego HTTP na porta TCP 80. O valor 17 é para tráfego UDP e é usado pelos fluxos de consulta e resposta DNS.