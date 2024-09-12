# BGP FLOWSPEC

## Oque e o Flowspec
Ele e uma extensao da familia do protocolo BGP, que permite fazer filtragens de trafego BGP, sao com ose fossem regras de firewall, mas distribuidas via BGP.
Com ele e permitido criar regras especificas, como para origem, destino, portas e protocolos de rede, assim sendo muito mais inteligente a regra de mitigacao. Essas regras sao dado a origem dos propios roteadores
de borda de um ISP por exemplo, onde esta rodando o BGP, dessa forma permite a criacao de regras em tempo real e mais precisa contra ameacas

![Imagem ilustrativa](/Imagens-NetFlow/flowspec1.png)


### Flowspec vc Blackhole (RTBH)
