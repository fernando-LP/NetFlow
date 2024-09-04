# Mitigação eficiente de DDoS

## FASTNETMON
> Utilizaremos o fastnetmon para estudo.

Fastnetmon é uma ferramenta para deteção, prevenção e mitigação de DDOs rápidas, confiaveis e automatizadas.
FastNetMon tem capacidade de detectar um ataque DDoS em 30 segundos para Netflow 5/9 e IPFIX, em sFlow a detecção ocorre em 2 segundos.
Com detecção de 30 ou 2 segundos, o FastNetMon responde ataques a medida em que recebe informações de fluxo de seu equipamento de rede (roteadores, switches, servidores, CGNAT, radio enlace etc).

O FastNetMin é uma ferramenta versátil de detecção de DDoS, sensível a uma variedade de tipos de ataque DoS/DDoS:
* Ataques de inundação via UDP, TCP, ICMP
* Ataques do protocolo TCP via inundações SYN, SYN-ACK e FIN
* Ataques multivetoriais usando uma combinação de técnicas
* Ataques de protocolo IP por meio de pacotes fragmentados
* Ataques de aplificação via NTP, SNMP, SSDP, DNS, GRE, cobranças e mais
Ele suporta uma variedade de protocolos de telemetria de tráfego e analise de fluxo, como NetFlow, IPFIX, sFlow e SPAN/Port mirror, como Amazon e Google VPC Flow Logs.


### Porque usar FastNetMon?
* Na versão FREE é possivel!
   * deteção instantanea de ataque 30 e/ou 2 segundos
   * Escalabilidade ilimitada
   * Amigável ao desenvolvedor API
   * 100% Adequado para engenheiros de rede
   * Automação BGP BlackHole
   * Visibilidade do tráfego
   * Flowspec Mitigação DDoS (Versão Advancend Edition $$)
FastNetMon pode ajudar a resolver seus desafios de visibilidade de tráfego de rede e proteger sua infraestrutura.

Adminsitradores de rede precisam dividir seus esforços entre o "jogo que está lento - iptv que esta travando" e a criação de contramedidas para situações de crise, oque torna as empresas geralmente incapazes de lidar com grandes ataques.

Com a analise de fluxo, podemos **identificar e prevenir** a nossa rede de uma enorme quantidade de problemas que poderiam trazer grandes prejuízos financeiros.
Como analisar o fluxo?
 O sistema automatizado ira analisar o tráfego recebido nos roteadores e, baseado nas thresholds que definimos, ele desencadeará o processo de mitigação:
 * Mitigar ataques DDoS é um jogo de xadrez, mas de forma muito resumida envolve basicamente 4 estágios:
 *   Detecção;
 *   Desvio;
 *   Filtragem;
 *   Análise.
_Se há um provérbio que define o ataque DDoS é esse:_
> O prudente percebe o perigo e busca refúgio; o inexperiente segue adiante e sofre as consequências.


## Niveis de mitigação

### Nivel 1
* RTBH - BlackHole
Estão atacando meu bloco /27, então coloco esse meu bloco em blcakhole.

### Nivel 2
* Flow SPec
Vai bloquear o vetor

### Nivel 3
* Clean Housf Local
Filtragem de trafego localmente até o nivel maximo de banda que você conseguir mitigar

### Nivel 4
* Nuvem
Empresas de mitigação
