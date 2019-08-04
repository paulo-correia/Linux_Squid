# Página de Erro Pesonalizada

Mova o arquivo /usr/share/squid/errors/pt-br/ERR\_ACCESS\_DENIED para ERR\_ACCESS\_DENIED.old com o comando:

 `mv /usr/share/squid/errors/pt-br/ERR_ACCESS_DENIED /usr/share/squid/errors/pt-br/ERR_ACCESS_DENIED.old`

** Crie** o arquivo /usr/share/squid/errors/pt-br/ERR\_ACCESS\_DENIED com o conteúdo:

 ```
 <html>
 <head>
 <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
 <title>Acesso Proibido</title>
 <script type="text/javascript" language="JavaScript"> // <![CDATA[
 function abrir(URL) {
 var width = 510;
 var height = 300;
 var left = 99;
 var top = 99;
 window.open(URL,'janela', 'width='+width+', height='+height+', top='+top+', left='+left+', scrollbars=yes, status=no, toolbar=no, location=no, directories=no, menubar=no, resizable=no, fullscreen=no'); } // ]]></script>
 
 <style type="text/css">
 </style>
 <h1><span style="color: red;"> 
 <strong>ACESSO PROIBIDO!</strong></span></h1>
 <h2>Este site não pode ser acessado!</h2>
 <hr noshade="noshade" size="1px" />
 Na tentativa de acessar o site: <strong><a href="%U">%U</a></strong>
 O seguinte erro foi encontrado:
 <ul>
 <li>
 <strong> Proibido o Acesso. </strong>
 O Servidor Firewall impediu seu acesso, pois <strong><em>o conteúdo do link solicitado</em></strong> pode prejudicar o bom funcionamento da rede e internet ou <strong><em>o administrador do servidor</em></strong> pode não estar de acordo com o seu acesso. Caso você não concorde com isso, preencha o formulário abaixo para solicitar o desbloqueio do site.<br>
 Não envie "print" deste formulário por e-mail, somente solicitações pelo formulário serão aceitas.</li>
 </ul>
 <form id="formulario" action="arquivo.php" method="post" name="formulario">
 <table style="text-align: left; width: 50px; background-color: red; height: 50px; border:1px solid #EECFA1" cellspacing="0" cellpadding="0">
 <tbody>
 <tr>
 <td style="vertical-align: top;">
 <table style="width: 700px; height: 168px; background-color: #FFF8DC;" border="0" cellspacing="6" cellpadding="1">
 <tbody>
 <tr style="font-family: Verdana; color:#333">
 <td scope="col" colspan="2">
 <span class="style1" >Formulário de desbloqueio de sites:</span></td>
 </tr>
 <tr>
 <td style="text-align: left; font-family: Verdana; color:#333;" scope="col">Nome:</td>
 <td scope="col" >
 <input style="border:1px solid #00FFFF" name="nome" value="Digite seu nome." type="text" class="form_campos" onFocus="if(this.value=='Digite seu nome.') {this.value=''}" onBlur="if(this.value==''){this.value='Digite seu nome.'}" size="54"/></td>
 </tr>
 <tr>
 <td style="text-align: left; font-family: Verdana; color:#333;" scope="col">Site:</td>
 <td scope="col">
 <input style="border:1px solid #00FFFF" id="site" class="form_campos" type="text" name="site" value="%U" readonly="readonly" size="80" /></td>
 </tr>
 <tr>
 <td style="text-align: left; font-family: Verdana; color:#333;" scope="col">Motivo:</td>
 <td scope="col">
 <textarea style="border:1px solid #00FFFF" onfocus="if(this.value==this.defaultValue)this.value='';" onblur="if(this.value=='')this.value=this.defaultValue;" class="form_campos" name="motivo" rows="6" cols="99" >Informe aqui por qual motivo que deseja acessar esse site.</textarea>
 <input type="hidden" name="empresa" value="Empresa">
 <input type="hidden" name="usuario" value="%a">
 </td>
 </tr>
 <tr>
 <td style="text-align: center;" scope="col" colspan="2">
 <input class="form_botao" type="submit" name="Enviar" value="Enviar " />
 <input class="form_botao" type="reset" name="Limpar" value="Limpar" />
 </td>
 </tr>
 </tbody>
 </table>
 </td>
 </tr>
 </tbody>
 </table>
 </form>
```

Será enviado ao arquivo .php o usuário, Empresa e site