# Instalação do Logstash
Instalação do Logstash em sistemas linux

Primeiramente, devemos validar a versão do java que esta instalado na maquina.

```
java --version
```
A versão ideal será da 1.8.0_161 ou superior.

#### Instalações em distribuições Debian

Primeiro passo é fazer o download e instalação das chaves publicas.
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

Segundo passo é instalar o pacote apt-transport-https, necessário para a instalação no Debian.
```
sudo apt-get install apt-transport-https
```

Terceiro passo é salvar o repositório do Elasticsearch.
```
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list
```

Por fim iremos instalar o Logstash na maquina.
```
sudo apt-get update && sudo apt-get install logstash
```

#### Instalação em distribuições Centos

Primeiro passo é fazer o download e instalação das chaves publicas.
```
rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch
```

Segund passo é adicionar um novo arquivo na lista de repositório /etc/yum.repos.d/logstash.repo, e inserir o conteúdo dentro dele.
```
[logstash-6.x]
name=Elastic repository for 6.x packages
baseurl=https://artifacts.elastic.co/packages/6.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md
```

Por fim iremos instalar o Logstash na maquina.
```
sudo yum install logstash
```

#### Iniciar os serviços do Logstash
```
//Para ver se o serviço já esta iniciado basta usar o comando abaixo:
sudo systemctl status logstash.service

//Para inicar o serviço basta usar o comando abaixo:
sudo systemctl start logstash.service

//Para parar o serviço basta usar o comando abaixo:
sudo systemctl stop logstash.service
```

#### Instalação em Docker
Para instalação no docker [clique aqui](https://www.elastic.co/guide/en/logstash/current/docker.html) para ver o tutorial.
