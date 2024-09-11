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

