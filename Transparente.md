# Transparente

Deixe o arquivo **squid.conf** igual ao conteúdo abaixo:

 ```
#
# Porta do Proxy
# 

http_port 8080 transparent

#
# Nome do Host
# 

visible_hostname debi-squid.localhost 

#
# ACLS Padrao
# 

acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 563 # https, snews
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl purge method PURGE
acl CONNECT method CONNECT

#
# Confirma as ACLS Padrao
# 

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
icp_access allow all 

#
# Permite a navegacao apenas para IPS especificos
# 

acl grupo src "/etc/squid/ips_a"
http_access deny !grupo 

#
# ACL de Liberacao e Bloqueio de sites
# 

acl hp_livres url_regex "/etc/squid/livres"
acl hp_bloq url_regex "/etc/squid/bloqueados" 

#
# Permite a navegacao apenas para os usuarios logados e para os IPS especificos
# 

http_access allow hp_livres grupo
http_access deny hp_bloq grupo 

#
# Bloqueia todo o resto
# 

http_access deny all 

#
# Opcoes de Refresh
# 

refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern . 0 20% 4320 

#
# Erros em Portugues 
# 

error_directory /usr/share/squid/errors/Portuguese
```

Para criar o arquivo **ips\_a**, execute o comando:

 ```
nano ips_a
ou
vi ips_a
```

Coloque os endereços de IP que irão usar. (um IP por linha)

Para criar o arquivo **livres**, execute o comando:

 ```
nano livres
ou
vi livres
```

Coloque os sites que terão navegação livre. (um site por linha)

Para criar o arquivo **bloqeados**, execute o comando:

 ```
nano bloqueados
ou
vi bloqueados
```

Coloque os sites que terão navegação bloqueada. (um site por linha)

Edite como o arquivo **/etc/squid/squid.conf** e substitua nome.dominio pelo conteudo do **/etc/hostname** se o nome não tiver ponto coloque **nome.localhost**.

Após a edição salve e feche o arquivo.

Após todas as configurações, como **root** execute o comando:

 `squid -k rconfigure`

**Obs:** Se trocar a regra **http\_access deny all** por **http\_access allow all**, a regra **acl hp\_livres url\_regex "/etc/squid/livres"** e o arquivo **livres** não são mais necessários. (Só será bloqueado os bloqueados)

É necessário fazer o redirecionamento das portas 80 e 443 clicando [aqui](https://github.com/paulo-correia/Linux_Iptables)

**Obs**: O redirecionamento da porta 443 pode não deixar sites ssl funcionarem corretamente.

Para bloquear sites SSL (Https) clique [aqui](https://github.com/paulo-correia/Linux_Squid/blob/master/Bloqueio_de_SSL.md)
