# Squid
![](https://github.com/paulo-correia/Linux_Squid/blob/master/Squid_logo.jpg)

O Squid é um servidor proxy que suporta HTTP, HTTPS, FTP e outros.

Ele reduz a utilização da conexão e melhora os tempos de resposta fazendo cache de requisições frequentes de páginas web numa rede de computadores.

Ele pode também ser usado como um proxy reverso.

# Instalação
Toda a instalação é feita como **root**

### Debian

Instale o pacote do squid, execute o comando:

 `apt-get install squid3`

### CentOS

 Instale o pacote do squid, execute o comando:

 `yum -y install squid`

## Configuração

Utilize o </span>[Iptables](https://github.com/paulo-correia/Linux_Iptables) para compartilhar as placas de rede (mínimo 02)</span>

Edite o arquivo /etc/squid/squid.conf

E escolhendo um dos tipos abaixo :

### ![Transparente] (https://github.com/paulo-correia/Linux_Squid/blob/master/Transparente.md)

### ![Configurado no Navegador] (https://github.com/paulo-correia/Linux_Squid/blob/master/Configurado_no_Navegador.md)

### ![Autenticado](https://github.com/paulo-correia/Linux_Squid/blob/master/Autenticado.md)

### ![Bloqueio de Sites SSL](https://github.com/paulo-correia/Linux_Squid/blob/master/Bloqueio_de_SSL.md)

## ![Página de Erro Pesonalizada](https://github.com/paulo-correia/Linux_Squid/blob/master/Pagina_de_Erro_Personalizada.md)

## Debug

Colocando a linha mais abaixo no squid.conf antes da linha do access.log é habilitado o debug, onde são exibidas por qual(is) regras (ACL) foi barrado ou passou.

Ele grava estas informações no cache.log

 `debug_options ALL,1 33,2 28,9`
