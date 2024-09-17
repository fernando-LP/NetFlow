# BGP FLOWSPEC

## Oque e o Flowspec
Ele e uma extensao da familia do protocolo BGP, que permite fazer filtragens de trafego BGP, sao com ose fossem regras de firewall, mas distribuidas via BGP.
Com ele e permitido criar regras especificas, como para origem, destino, portas e protocolos de rede, assim sendo muito mais inteligente a regra de mitigacao. Essas regras sao dado a origem dos propios roteadores
de borda de um ISP por exemplo, onde esta rodando o BGP, dessa forma permite a criacao de regras em tempo real e mais precisa contra ameacas

![Imagem ilustrativa](/Imagens-NetFlow/flowspec1.png)


### Flowspec vc Blackhole (RTBH)
Quando aplicamos uma regra de Blackhole, ela descarta todo trafego com destino ao um IP ou bloco de IP, sendo uma medida muito
drastica, por conta de bloquear servicos importantes da rede.
Essa regra e interessante quando o ataque e voltado para alguns ips da rede ou os enderecos sao pouco importantes. Porem quando
o ataque e feito em carpet bombing ou para enderecos importantes, aplicar essa regra apenas aumenta o problema.
Por exemplo quando e feito um blackhole de dns, onde todos os seus usuarios consultam esse ip dns, ou seja todos iram ficar
sem acesso a internet quando bloquear esse servidor DNS.

Ja o **flowspec** e bastante especifico e e capaz de descartar o tipo de trafego especifico do ataque, sem ferir o resto do trafego da rede. Num ataque de NTP por exemplo, e possivel descartar todo o NTP da rede, mas manter todo o resto do trafego
funcionando

### Limitacoes do Flowspec
O Flowspec e semelhante a regras de firewall de camada 4. Ou seja, ele e capas de dar match nos criterios estabelecidos. Caso a regra nao seja capaz de destinguir o trafego legitimo do ataque, ambos serao descartados. Tambem nao e capaz de dar match no payload do pacote. Existem trabalho em andamento para isso.

### Exemplos de regras
SRC: 2001:DB8:FACA::1 <br>
DST-PORT: 53 <br>
Protocol: 17 (udp) <br>
Action: Deny <br>
<br><br>
DST: 2001:DB8:DEAD::2<br>
DST-PORT: 22<br>
Protocol: 6 (tcp)<br>
Action: Rate-limit<br>
<br><br>

```bash
Proto: UDP
DST: 192.0.2.0/24
SRC-PORT: 53
Action: rate-limit em 50 Mbps
```
> Mitiga ataques de reflexao de DNS. Porem limita o trafego DNS em IPv4. entretanto IPv6 nao sera afetado.
<br><br>
```bash
Proto: TCP
DST: 192.0.2.0/24
DST-PORT: 80
Action: Discard
```
> Descarta todo o trafego de HTTP para a rede em questao, mas tem o efeito de deixar o HTTP da rede indisponivel. Mas se utilizar ipv6, vaio continuar funcionando
<br><br>
```bash
Proto: TCP
DST: 192.0.2.0/24
SRC-PORT: 443
TCP Flags: SYN and ACK
Action: Discard
```
> Mitiga ataques SYN e ACK para rede, porem nenhuma nova conexao IPv4 podera mais ser estabelecida. Cuidado com essa regra, pois pode gerar um impacto tao alto como o proprio ataque em si.



## Possibilidades do Flowspec
Referencia: https://datatracker.ietf.org/doc/html/rfc8955

* Uma regra de Flowspec e composta por matchers + acoes.
 *  Podendo ser varios matchers, varias acoes agrupadas na mesma regra.

### Matchers
1. Destination Prefix
2. Source Prefix
3. IP Protocol
4. Port
5. Destination Port
6. Source Port
7. ICMP Type
8. ICMP Code
9. TCP Flags
10. Packet Lenght
11. DSCP (Diffserv Code Point)
12. Fragment

### Principais acoes
1. Accept
2. Discard
3. Redirect
 a. Next-Hob
 b. VRF
4. Rate Limit

### Principais operadores
1. "==" (equal)
2. ">" (greater than)<br>
   a. Portas maiores que 1000<br>
   b. Rate limit em cima das portas 1024 <br>
3. ">=" (greater than or equal)
4. "<" (less than)
5. "<=" (less than or equal)
6. "!=" (not equal value)



