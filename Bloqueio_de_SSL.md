# Bloqueio de Sites SSL

Edite o arquivo /etc/squid/squid.conf

Comente a linha abaixo colocando um # na frente da mesma:

 `acl Safe_ports port 443 563`

Coloque após as regras ACL de Liberacao e Bloqueio de sites o texto:

 ```
#
# Acl de Bloqueio de sites SSL
#
acl ssl_port 443
acl hps_bloq url_regex "/etc/squid/sslbloq"
http_acess deny CONNECT hps_bloq ssl_port
```

Salve o arquivo e saia

Crie o arquivo /etc/squid/sslbloq

Coloque os sites que terão navegação bloqueada. (um site por linha)
