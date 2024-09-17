# Sistemas e Relátorios
> Nesse documento, é passado algumas empresas, sistemas que auxiliam na mitigação, e também sites para tirar relátorios de ataques ddos.




### NETSCOUNT
* Contem um serviço para mitigação de ddos e mais funcionalidades para engenharia de trafego
* Relátorio de ataques
https://www.netscout.com/threatreport/

### Cenarios
> Como e possivel fazer a mitigacao?

* Equipamento locais (on premise)
 * online ou outline
* Nuvem de mitigacao
* Estrategia hibrida


# PF_RING (ntop.org):

### Foco
Aceleração de captura de pacotes em alta velocidade.
### Funcionalidade
Captura e transmissão de pacotes a taxas de linha (até 10 Gbps) em hardware comum, com suporte para drivers específicos para maximizar desempenho. Oferece uma API limpa e integração com nDPI para detecção de protocolos de camada 7.
### Aplicações
Amplamente utilizado em soluções de monitoramento de rede, IDS/IPS (Suricata), firewalls L7, e processamento de fluxos em tempo real​

# Suricata (suricata.io):
### Foco
Motor de detecção de ameaças e prevenção de intrusão.
### Funcionalidade
Realiza inspeção profunda de pacotes, monitoramento de rede, e identificação de ameaças com suporte nativo para desvio de fluxo (bypass) para otimização de processamento.
### Aplicações
Utilizado para IDS, IPS, e monitoramento de segurança de redes

# Wanguard (Andrisoft):
### Foco
Detecção e mitigação de DDoS, análise de tráfego de rede.
### Funcionalidade
Suporta várias tecnologias de roteamento e monitoramento, incluindo NetFlow, sFlow, e SNMP, para analisar, detectar e mitigar ameaças como ataques DDoS em tempo real.
### Aplicações
Usado por provedores de serviços de Internet (ISP) e grandes empresas para proteger infraestrutura de rede contra ataques DDoS​

# FastNetMon (fastnetmon.com):

### Foco
Mitigação de ataques DDoS.
### Funcionalidade
Detecta rapidamente anomalias de tráfego e ataques de negação de serviço em redes usando protocolos como NetFlow, IPFIX, e sFlow. Integração com ferramentas como BGP para mitigação automatizada.
### Aplicações
Projetado para provedores de serviços e empresas de grande porte que precisam proteger a disponibilidade da rede em ambientes de alta performance​(

# Kentik (kentik.com):
### Foco
Monitoramento e análise de performance de redes.
### Funcionalidade
Oferece uma plataforma de análise de tráfego em tempo real com capacidade de prever e mitigar problemas de rede. Suporta uma variedade de integrações e coleta de dados a partir de várias fontes.
### Aplicações
Usado para gerenciar grandes infraestruturas de rede, com foco em ISPs e empresas que precisam de insights profundos sobre o desempenho e segurança de redes.


# Made4Flow (made4it.com.br):
### Foco
Análise de NetFlow.
### Funcionalidade
Ferramenta para coleta e análise de dados NetFlow em redes de alta performance, oferecendo insights detalhados sobre o tráfego e permitindo diagnósticos rápidos de problemas de rede.
### Aplicações
Usada principalmente para monitoramento de redes em tempo real, otimização de tráfego, e detecção de anomalias​

# DPDK (dpdk.org):

### Foco
Processamento de pacotes de rede de alta performance.
### Funcionalidade
Biblioteca para processamento rápido de pacotes em CPUs multicore, projetada para maximizar a eficiência de processamento em sistemas de rede de alta demanda.
### Aplicações
Utilizado em sistemas de telecomunicações, data centers, e outras infraestruturas que exigem baixa latência e alto throughput para manipulação de pacotes​(

# XDP (iovisor.org):
### Foco 
Processamento de pacotes no kernel do Linux.
### Funcionalidade
Usa a tecnologia eBPF para processamento de pacotes a nível de kernel, permitindo criação de filtros altamente eficientes e controle direto sobre o tráfego de rede, reduzindo a sobrecarga de processamento.
### Aplicações
Ideal para sistemas de segurança de rede, mitigação de DDoS, e processamento de pacotes de baixa latência em grandes redes​

Essas ferramentas cobrem uma ampla gama de funcionalidades de monitoramento, captura de pacotes e segurança de redes, com foco em desempenho de alta velocidade e mitigação de ameaças.
