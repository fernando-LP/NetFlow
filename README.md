# NetFlow

NetFlow é uma tecnologia da Cisco usada para monitorar profundamente o fluxo de rede, analisando os dados e o tráfego coletados por roteadores e outros dispositivos de rede. NetFlow fornece uma visão detalhada da rede. Desenvolvido pela Cisco em 1996, o protocolo permite analisar o tráfego de rede, visualizando informações como protocolos de origem e destino, portas, volume de tráfego, entre outros. Com essas informações, é possível identificar padrões de tráfego na rede.

As equipes podem usar esses dados para facilitar a detecção de possíveis violações de segurança ou políticas internas. NetFlow registra apenas informações de comunicação de rede por meio de atributos úteis das camadas de rede, transporte e enlace. Esses atributos podem ajudar a entender o comportamento da rede, fornecendo insights sobre quem está usando a rede, quando ela é utilizada, o tipo de aplicativo em uso e como a largura de banda é consumida.

## Componentes Principais

As três principais componentes da topologia NetFlow são:

* **Exportador de Fluxo:** Agrupa pacotes e fluxos e exporta os registros de fluxo para um ou mais coletores de fluxo.
* **Coletor de Fluxo:** Responsável por receber, armazenar e pré-processar os dados de fluxo recebidos de um exportador de fluxo.
* **Analisador de Fluxo:** Aplicativo utilizado para analisar os dados de fluxo recebidos. A análise pode ser usada para gerar perfis de tráfego ou solucionar problemas de rede.

Os registros NetFlow geralmente são enviados via UDP e recebidos por um coletor. A porta UDP de destino e o IP do coletor devem ser especificados no NetFlow Exporter.

## Principais Perguntas que NetFlow Responde

* Quem é o fluxo?
* O que é o fluxo?
* Para onde vai o fluxo?
* Quando ocorreu o fluxo?
* Qual é a quantidade de tráfego no fluxo?

## O que é NetFlow

Os dispositivos de rede que suportam NetFlow (Flow Exporter) geram logs de fluxo e os enviam a um coletor NetFlow. O dispositivo que prepara os logs de fluxo normalmente os envia ao coletor quando determina que o fluxo está completo, seja devido ao tempo limite, à ausência de tráfego dentro de um tempo especificado, ou ao final de uma sessão TCP.

A porta UDP de destino e o IP do coletor devem ser especificados no NetFlow Exporter. Embora o RFC 3954 não defina um número específico de porta UDP para NetFlow, os valores comuns usados pela Cisco são as portas 2055, 9555, 9995, 9025 ou 9026. IPFIX recomenda as portas UDP 47 e 4740.

Quando o fluxo de tráfego chega ao Flow Collector, este armazena os dados em seus bancos de dados e o fluxo é analisado pelo Flow Analyzer. Como resultado, são gerados relatórios e alertas que mostram o comportamento do fluxo de tráfego da rede.

Esses atributos identificam pacotes IP únicos ou semelhantes. Os fluxos são temporariamente armazenados em um cache local de roteadores, chamado FlowCache. Além disso, há outros atributos úteis que descrevem detalhes sobre o tráfego, como hora de início e término, duração, sinalizadores TCP, número de pacotes e número de bytes.

## Versões do NetFlow

* **Versão 1:** A primeira versão, restrita ao IPv4.
* **Versões 2, 3, 4:** Versões usadas pela Cisco internamente e nunca lançadas.
* **Versão 5:** A versão mais comumente implantada e padrão.
* **Versão 6:** Versão que não é mais suportada pela Cisco.
* **Versão 7:** Semelhante à versão 5, mas não inclui AS, interface, sinalizadores TCP e informações TOS.
* **Versão 8:** Utiliza diversas formas de agregação, reduzindo o uso de recursos.
* **Versão 9:** Baseada em modelo, suportada por roteadores recentes, usada para fluxos de tráfego IPv4, IPv6, MPLS, BGP Next Hop. NetFlow versão 9 oferece vantagens para segurança, análise de tráfego e multicast. Também é flexível e possui um formato de exportação de arquivo extensível, facilitando o suporte a campos adicionais.

NetFlow v9 e IPFIX permitem ter modelos extensíveis, ajustando o conjunto de campos e pacotes de interesse. Eles também adicionam a capacidade de monitorar campos da camada 2.

## Recursos Chave

Administradores podem usar NetFlow de várias maneiras para obter informações valiosas sobre suas redes. Exemplos incluem:

* Monitoramento de banda e análise de tráfego;
* Análise de rede e gerenciamento de segurança;
* Monitoramento de aplicativos;
* Rastreamento de migração de aplicativos;
* Validação de QoS;
* Identificação de worms e malwares;
* Análise de tráfego de VPN e comportamento de acesso remoto;
* Análise do ASN de origem e destino;
* Rastreamento de portas de acesso;
* Monitoramento de utilização de protocolos.

## Monitoramento com NetFlow

Com os dados do NetFlow devidamente analisados, um administrador de rede pode entender o perfil de tráfego da rede, respondendo a perguntas como:

* Qual é o tráfego do protocolo UDP via porta 53 para os prefixos da rede?
* Quais são os root servers do meu DNS?
* Quais servidores DNS estão sendo consultados?

É simples filtrar ou agregar dados no coletor NetFlow e gerar relatórios específicos, baseados na combinação dos seguintes critérios:

* Endereços IP de origem ou destino;
* Interfaces;
* Portas de origem ou destino;
* Dispositivos que tiveram tráfego passando por eles;
* Sistemas autônomos de origem ou destino;
* Protocolos utilizados;
* Marcadores utilizados durante a comunicação;
* Quais endereços IP foram atacados.

## Sua Rede é Crítica?

Se sua rede é crítica para a empresa, a detecção proativa de anomalias é essencial. NetFlow possui as ferramentas para realizar essa tarefa.

Mesmo em redes grandes e organizadas, é comum encontrar aplicações desconhecidas utilizando banda de forma significativa. Essas aplicações podem ser cruciais para o negócio, mas desconhecidas para os administradores de rede, devido à falta de atenção aos requisitos de tráfego de novas aplicações.

## Benefícios do NetFlow

1. **Identificação das Aplicações de Rede:** Pode-se saber quais são as aplicações que estão utilizando a rede e identificá-las, visando otimizar o fluxo de informações para que os processos mais importantes recebam maior banda.
2. **Detecção de Anomalias:** Muitas anomalias nas redes comprometem a velocidade da operação. Com NetFlow, é possível detectar essas anomalias e reduzir sua ação, melhorando o fluxo de dados e a velocidade da rede.
3. **Verificação de Instabilidades:** As instabilidades da rede causam atrasos em processos internos. Com NetFlow, a equipe de TI pode identificar e mitigar essas instabilidades, melhorando a qualidade do serviço.
4. **Leitura do Uso de Recursos da Rede:** NetFlow identifica o uso dos recursos na rede, segmentando as aplicações que mais consomem banda. Com essa informação, é possível adequar os processos e diferenciar o fluxo de dados conforme necessário.
5. **Identificação de Impactos na Rede:** Causas estranhas que impactam a rede podem ser descobertas através de NetFlow, permitindo que a equipe de TI atue rapidamente para solucionar os problemas.
6. **Redução de Vulnerabilidades:** Identificando o tráfego que passa pela rede e caracterizando as aplicações, é possível reduzir as vulnerabilidades da rede e evitar a entrada de agentes maliciosos.

## Por Que Utilizar IPFIX?

IPFIX é composto por dois processos: exportação e amostragem, além de uma tabela de fluxo onde milhões de fluxos residem temporariamente. Possui o protocolo de telemetria de rede IPFIX 315, que promete reduzir o tempo de detecção de ataque DDoS para 1 segundo. Os caches de telemetria IPFIX tradicionais fluem até > 30 segundos, atrasando significativamente as respostas a ataques DDoS. Além do suporte sólido em Juniper MX, o IPFIX 315 foi introduzido na linha de produtos Juniper PTX.

## Diferença Entre NetFlow e sFlow

Fazendo uma analogia para monitoramento de tráfego de veículos: "Enquanto o NetFlow pode ser descrito como um observador de padrões de tráfego ('Quantos ônibus foram daqui para lá?'), o sFlow tira fotos de qualquer carro ou ônibus que esteja passando naquele momento."

---

| Formato de Fluxo | Sobre |
|------------------|-------|
| IPFIX            | IETF padrão para exportação de fluxo, pode ser personalizado e é baseado em modelo, como NetFlow. Está disponível em Barracuda Networks. |
| sFlow            | Baseado em amostragem - 1 em N "pacotes" capturados para análise de tráfego. [sFlow Products](http://www.sflow.org/products) |
| J-Flow           | Protocolo da Juniper para exportação de fluxos de roteadores, switches e firewalls. |
| NetStream        | Uma variação do NetFlow compatível com dispositivos Huawei. |



# Softwares para monitormaneto de NetFlow
* NETSCOUT
* ElastiFlow
* nfsen-ng
* NFStream
* GoFlow 2
* FastNetmon
* WanGuard
* NEXUSGUARD
* Grafana Labs
* Akamai DDoS Protections
* Cloudflare Docs
* vFlow
* Corero - the DDoS Protections specialist
* CERT NetSA Security Suite
* Elasticsearch



