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


# Instalacao dos servicos
> Nesse momento com a maquina (vm) ja criada, vamos iniciar a instalacao dos servicos.
> Repare que todos os servicos estao na mesma versao, e interessante manter eles sempre na mesma versao para questoes de compatibildiade

## instale as bibliotecas Globais
Aqui estamos instalando algumas dependencias que iremos utilizar. Cuide bastante do clock do servidor, para ficar sincronizado com o horario dos seus equipamentos da rede.
```bash
apt update
apt upgrade
apt -y install wget ntp apt-transport-https gnupg unzip curl net-tools default-jre tcpdump
```
# Instalando elastic search
Voce pode querer baixar a versao mais atual do ElastichSearch, para isso pode acessar a seguinte pagina: https://www.elastic.co/pt/downloads/elasticsearch e selecionar a opcao apt-get em Packege managers

```bash
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.15.0-amd64.deb
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.15.0-amd64.deb.sha512
shasum -a 512 -c elasticsearch-8.15.0-amd64.deb.sha512 
dpkg -i elasticsearch-8.15.0-amd64.deb
```
Quando descompactar o o elatichsearch, o mesmo vai informar uma senha para voce, guarde ela, pois iremos utilizar depois.

![Imagem ilustrativa](../Imagens-NetFlow/senha_elastichSearch.png)

> Caso o comando `shasum` nao seja encontrado, sera preciso instalar o `perl` com o comando `apt install perl`.

### Alguns comandos interessantes do elatichSearch
```bash
If this node should join an existing cluster, you can reconfigure this with
'/usr/share/elasticsearch/bin/elasticsearch-reconfigure-node --enrollment-token <token-here>'
after creating an enrollment token on your existing cluster.

You can complete the following actions at any time:

Reset the password of the elastic built-in superuser with
'/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic'.

Generate an enrollment token for Kibana instances with
 '/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana'.

Generate an enrollment token for Elasticsearch nodes with
'/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node
```

### Iniciando serviços

```bash
systemctl daemon-reload
systemctl enable elasticsearch.service
systemctl start elasticsearch.service
systemctl status elasticsearch.service
curl -X GET 127.0.0.1:9200
```
> Nesse momento o elastichsearch ja deve esta rodando.

## Configuracoes do ElastichSearch
Agora vamos editar o arquivo de configuração e Alterar as opções abaixo no arquivo `/etc/elasticsearch/elasticsearch.yml`

1. Diretorio
`nano /etc/elasticsearch/elasticsearch.yml`

```bash
cluster.name: Netflow-Education
node.name: flow-01
network.host: IP DO SERVIDOR
http.port: 9200
# Enable security feactures
xpack.security.enabled: false
xpack.security.enrollment.enabled: false
xpack.security.http.ssl:
enabled: false
xpack.security.transport.ssl:
enabled: false
```
### Iniciando serviços
```bash
systemctl daemon-reload
systemctl restart elasticsearch.service
systemctl enable elasticsearch.service
```
### Testar acessar na WEB
Agora com a configuracao feita no ElastichSearch, podemos testar o acesso da pagina web

![Imagem ilustrativa](../Imagens-NetFlow/web_elastich.png)

# Instalacao do KIBANA
> Interface grafica para gerenciar o banco de dados e tambem graficos para visualizar.

Pagina oficial do KIBANA onde e possivel baixar a versao mais atual: https://www.elastic.co/pt/downloads/kibana

```bash
wget https://artifacts.elastic.co/downloads/kibana/kibana-8.15.0-amd64.deb
shasum -a 512 kibana-8.15.0-amd64.deb 
dpkg -i kibana-8.15.0-amd64.deb
```

## Acessar arquivo de configuração do Kibana

* Diretorio de configuracao: `nano /etc/kibana/kibana.yml`
```bash
# server.port: 5601
# server.host: "IP DO SERVIDOR"
# server.name: "kibana-flow"
# elasticsearch.hosts: ["http://IP DO SERVIDOR:9200"]
```


### Restart serviços
```bash
systemctl enable kibana.service
systemctl start kibana.service
systemctl status kibana.service
tail -f /var/log/kibana/kibana.log -n 1000
```

### Acessar na WEB o KIBANA
http://IP SERVIDOR:5601/

![Imagem ilustrativa](../Imagens-NetFlow/kibana_web.png)

> Selecione a opcao " Explore on my own "


# Instalacao FILEBEAT
Aplicacao responsavel por receber o fluxo dos equipamentos.

Pagina oficial para download: https://www.elastic.co/pt/downloads/beats/filebeat

```bash
wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.15.0-amd64.deb
wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.15.0-amd64.deb.sha512
shasum -a 512 -c filebeat-8.15.0-amd64.deb.sha512
dpkg -i filebeat-8.15.0-amd64.deb
```

## Configuracao FILEBEAT
* Diretorio: `/etc/filebeat/filebeat.yml`

> Ajustar os enderecos IPS que o FILEBEAT vai se comunicar
```bash
output.elasticsearch:
 #Array of hosts to connect to.
hosts: ["IP SERVIDOR:9200"]
 #Kibana Host
host: "IP SERVIDOR:5601"
```

###
