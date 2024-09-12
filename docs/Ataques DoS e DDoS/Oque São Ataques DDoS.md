# Oque são ataques DDoS?
São ataques enviados para rede de computadores de ISPs e data centers, com o objetivo de deixá-las fora do ar ou com
uma performace baixa.
Para isso acontecer o ataque é feito da seguinte forma:
* Enviam um trafego indesejado, invalido que utilize toda a banda disponivel do transito IP e IX do ISP ou Data Center.
  * Por exemplo o ISP contrata um link de 10G, se o ataque for de 15G a rede desse provedor vai parar de funcionar, pois não vai ter espaço para pacotes ligitimos trafegarem, ou se trafegarem será muito lento.
* Aumentando a utilização da CPU
 * Equipamentos de rede tem um CPU, memoria ram como um computador normal, então com essa grande carga de pacotes de redes invalidos, o processamento da maquina pode ser saturado.
* Esgotam o recurso humano
 * Como a rede fica congestionada, os usuários da aquela rede não conseguiram utilizar de forma eficiente, e o suporte da aquela rede precisara trabalhar longas horas em cima desse problema, como por exemplo uma enorme fila de chamados com lentidão e mal funcionamento da internet. Isso leva a muitos problemas, como cancelamentos de clientes, e problemas graves, como serviços publicos, Hospitais, Prefeituras, Centrais do Governo que ficaram sem internet.


## Sobre o Ataque
* O atacante **não** será identificado
  * Vamos ver a frente que o ataque DDoS ele é distribuido de varias lugares de mundo, então a Origem de IP do atacante, não é uma só, é varias, dessa forma não é possivel identificar quem é o atacante.
  * Oque acontece muito é o atacante comprar um ataque DDoS, oque é bem barato, e esse ataque tem como base varios dispositivos no mundo infectados que enviam request todos para um lugar apenas. Imagina milhões de computadores infectados pelo mundo, e com um clique você faz esses computadores começarem a enviar pacotes de rede invalida para um lugar, assim gerando todo o congestionamento e carga de CPU.

* Nem todas Operadoras fazem mitigação contra ataque.
 * Operadoras são provedores com nivel maior, onde elas atendem ISPs e Data Centers, o trafego de toda a rede do ISP passa por essa operadora antes, porém depende do contrato feito, não é de obrigatoriedade da operadora mitigar o ataque.

* Tempo de ataque
  * O tempo de ataque costuma demorar muito tempo, porque o atacante que deixar você fora do ar, então dependendo do ataque pode demorar messes. E para dificultar a localicação desses ataques, é feito em periodos curto de tempo, ou seja, mando um trafego ddos a cada 10 minutos ou a cada 1 minuto, para que eu consiga burlar os sistemas de analise de trafego de rede.

* Procurar se previnir antes do ataque
 * "Depois que você já tomou o tiro, não adianta colocar o colete!"
 * Segundo os especialistas e consultorias de ataques ddos, a implantação para mitigar ataques ddos, dura dias e não horas. Durante esse tempo o ataque vai está ocorrendo, geranto varios efeitos colaterais.

## Mitigação

Nos ataques DDoS, em vez de falar em bloqueio, usamos o termo mitigação. Embora possa parecer simples bloquear o tráfego indesejado, na prática existem muitas formas diferentes de conduzir um ataque, utilizando variados tipos de protocolos. O atacante pode tornar o tráfego indesejado o mais parecido possível com o tráfego legítimo, tornando-o quase invisível. Por essa razão, o bloqueio de ataques DDoS apenas com regras de firewall, como ACLs (listas de controle de acesso), é muitas vezes ineficaz. Portanto, usamos o termo mitigação, que significa suavizar, ou seja, tentar reduzir o impacto do ataque DDoS para que ele não afete negativamente a rede.

## Como identificar de forma automática?

A identificação automática de ataques DDoS é altamente eficiente, pois utiliza sistemas que analisam o fluxo de rede e, ao identificar uma anomalia, podem tomar ações apropriadas.

Para isso, concentradores, switches e outros equipamentos de rede geralmente oferecem suporte para protocolos de TELEMETRIA, como NetFlow, sFlow e IPFIX. Esses protocolos capturam o tráfego da rede e enviam para um servidor de logs, onde uma aplicação analisa esse tráfego.

Um *flow* é composto por: uma origem + um destino + um protocolo = flow. Quando um usuário tenta acessar um sistema, ocorre uma comunicação entre uma origem e um destino, que são endereços IP, portas de conexão e protocolos. Dentro dessa comunicação, existem tipos de comunicação TCP/IP, como SYN, ACK e SYN-ACK, que são frequentemente usados em ataques. Você entenderá melhor do que estou falando aqui se já souber como funciona a comunicação entre máquinas na internet em nível mais baixo.

Em resumo, todos os protocolos utilizados para abrir uma página ou enviar uma mensagem podem ser explorados por um atacante para criar pacotes de rede falsos. Por exemplo, quando uma conexão com um site é encerrada, é enviada uma mensagem "FIN" por padrão. Um atacante pode gerar uma enorme quantidade de pacotes "FIN", enviando-os para um destino e criando um grande volume de tráfego, resultando em um ataque DDoS.

Esses protocolos funcionam no formato de *push*, ou seja, ao configurá-los nos equipamentos de rede, o próprio protocolo envia fluxos e amostras de pacotes para o servidor externo, que então lê, analisa e toma decisões automáticas.

### Tipos de regras automáticas

* **Alarme**
  * Notifica os responsáveis sobre a ocorrência de um ataque.

* **Black hole**
  * Essa regra envia o tráfego para um "buraco negro", ou seja, o tráfego é simplesmente ignorado e não é enviado para lugar algum; ele é descartado. Normalmente, isso é feito nos roteadores de borda.

* **Desvio para caixa de mitigação**
  * Nesta regra, o tráfego é direcionado para uma caixa de mitigação, que "limpa" o tráfego e envia apenas o tráfego legítimo para a rede local. Normalmente, esse equipamento é um servidor, como um Dell 760 com alta capacidade de throughput.

* **Desvio para nuvem de mitigação**
  * O tráfego da rede é enviado para uma nuvem de mitigação, que contém servidores e serviços avançados de alta capacidade capazes de limpar o tráfego e retornar apenas o tráfego legítimo para a rede local da vítima.

* **Anúncio BGP Flowspec**

### Observações sobre as soluções que voce escolher

* **Tempo customizado para a regra de Flowspec**
  * Alguns ataques tentam burlar o sistema de detecção automática, realizando ataques no formato *hit and run* (atacam por alguns segundos e depois desaparecem). Alguns sistemas de detecção automática podem não identificar esses ataques, por isso é importante analisar o tempo durante o qual a regra deve permanecer ativa.

* **Rate-Limit suportado**
  * O objetivo principal do DDoS é utilizar toda a banda disponível da rede para interromper os serviços. Se o serviço de detecção consegue criar regras de QoS baseadas na origem e destino do ataque, é uma ferramenta muito poderosa. No entanto, nem todos os detectores fazem isso; a maioria cria um *drop*, muito semelhante ao black hole.

* **White List**
  * O bloqueio de tráfego indesejado é feito automaticamente pela ferramenta. É interessante que a ferramenta tenha a opção de incluir uma **white list**, que é uma lista de endereços que não devem ser bloqueados e devem permanecer liberados. Isso evita que a ferramenta crie um *drop* indevido em serviços cruciais da sua rede.
