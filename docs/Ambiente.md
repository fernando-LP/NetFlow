# Ambimente para monitoramento NETFLOW
O ambiente sera da seguinte forma, no roteador, switch ou equiapmento de preferencia na borda, colocamos ele para enviar os fluxos de rede para o servidor onde o elastich foi instalado.
Nesse servidor precisa conter alguns servicos rodando que sao:
* FileBeat
* ElasticSearch
* Kibana

![Imagem ilustrativa](../Imagens-NetFlow/Draw.png)

## 1 - Baixar ISO do debian
> Utilizamos a versao do debian 12 nesse tutorial.
ISO DEBIAN: https://www.debian.org/CD/http-ftp/

## Requisitos do sistema
Para uma base teste podemos utilizar o seguinte:
* 2 CPU
* 4G Ram
* 40G disco

## Instalacao do debian
1. Instalacao sem interface grafica
2. Habilitar o acesso SSH


