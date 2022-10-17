# Repositório de códigos para o blog

Desenvolvido para auxiliar a integração de formulários, links, banners e outros scripts para o blog.

## Itens

- [Materiais Gratuitos](#materiais-gratuitos)
- [Formulário para posts de Materiais Gratuitos](#formulário-para-posts-de-materiais-gratuitos)
- [Gatilho](#gatilho)
- [POPUP Modal](#popup-modal)

### Materiais Gratuitos

###### Scrip para definição de campanha para Materiais Educativos Gratuitos

Crie uma nova página e Selecione o template **Material**.

![Template Material](https://blog.huggy.io/assets/images/template-material.png)

No corpo do texto, Insira um campo do tipo HTML e cole o código abaixo alterando as variáveis **{URL_ENDPOINT}**, **{ID_CAMPANHA}** e **{URL_PAGINA_OBRIGADO}**. _Manter as aspas(") no inicio e final_

![Campo HTML](https://blog.huggy.io/assets/images/campo-html.png)

```
<script>
    var endpoint = "{URL_ENDPOINT}";
    var id_campanha = "{ID_CAMPANHA}";
    var url = "{URL_PAGINA_OBRIGADO}";
</script>
```

### Formulário para posts de Materiais Gratuitos

###### Adicionando formulário em post

Insira um campo do tipo HTML no texto e cole o código abaixo alterando as variáveis **{URL_ENDPOINT}**, **{ID_CAMPANHA}**, **{URL_MATERIAL}**, **{TITULO_BOX}**, **{DESCRICAO_box}** e **{URL_IMAGEM}**. _Manter as aspas(") no inicio e final_

![Campo HTML](https://blog.huggy.io/assets/images/campo-html.png)

```
<script>
    var endpoint = "{URL_ENDPOINT}";
    var id_campanha = "{ID_CAMPANHA}";
    var url_material = "{URL_MATERIAL}";
    var tituloBox = "{TITULO_BOX}";
    var descricaoBox = "{DESCRICAO_box}";
    var imagemBox = "{URL_IMAGEM}";
</script>
<style>.box-custom-material{border-radius:30px;overflow:hidden;background:url(/assets/images/bg-box.svg) right center no-repeat #f5f5f5;padding:32px 28px 22px 66px;width:100%;max-width:770px;margin:30px auto;font-size:14px;line-height:1.4em;color:#617984}.box-custom-material .info{max-width:570px}.box-custom-material .tt{font-weight:500;font-size:20px;line-height:1.6em;color:#263645;margin:0 0 5px 0}.box-form-custom{display:flex;justify-content:space-between;align-items:flex-start}.box-form-custom img{max-width:365px;width:100%}.box-form-custom .formulario{width:262px;padding-top:36px;flex-shrink:0;margin-right:30px}.box-form-custom input,.box-form-custom select{border:0;background-color:#fff;margin-bottom:15px;border-radius:5px;width:100%;font-family:Rubik;color:#617984;font-size:13px;padding:.5em .923em}.box-form-custom button{background:#ff0068;border-radius:35px;font-family:Poppins;font-weight:500;font-size:12px;line-height:1.6em;color:#fff;padding:.406em 1.5em}#content-material-obrigado{font-size:15px;display:none}#content-material-obrigado .tt{font-family:Poppins,sans-serif;font-weight:700;font-size:28px;line-height:1.4em;color:#49585f;margin:58px 0 20px 0;display:flex}#content-material-obrigado .tt img{vertical-align:middle;margin-left:8px}#content-material-obrigado p{font-size:15px;line-height:1.6em;margin-bottom:1.4em;max-width:480px;font-family:Rubik,sans-serif}#content-material-obrigado .btn{font-family:Poppins,sans-serif;display:table;margin:27px auto;font-size:12px;line-height:1.25em;padding:.688em 2em;color:#fff;background:var(--ghost-accent-color);border-radius:36px;text-decoration:none}@media(max-width:992px){.box-custom-material{max-width:calc(100% - 50px);padding-left:35px}}@media(max-width:767px){.box-custom-material{padding:32px 28px}.box-form-custom{flex-wrap:wrap}.box-form-custom img{display:table;margin:0 auto;order:1}.box-form-custom .formulario{order:2;width:100%;margin-right:0}.box-form-custom button{display:table;margin:0 auto;max-width:80%}}</style>
<div class="box-custom-material"> <div id="content-material"> <div id="tituloBox" class="tt"></div><div id="descricaoBox" class="info"></div><div class="box-form-custom"> <div class="formulario"> <form id="form-dados" action="" onsubmit="return false;"> <input name="endpoint" id="endpoint" type="hidden" value=""> <input name="id_da_campanha" id="id_da_campanha" type="hidden" value=""> <input type="hidden" name="utm_source" value=""> <input type="hidden" name="utm_medium" value=""> <input type="hidden" name="utm_campaign" value=""> <input type="hidden" name="utm_term" value=""> <input type="hidden" name="utm_content" value=""> <input type="text" name="nome" placeholder="Nome Completo" required> <input type="email" name="email" placeholder="E-mail" required> <input type="text" name="empresa" placeholder="Empresa" required> <input type="url" name="site" placeholder="Site" required> </form> <button onclick="enviarDados(document.getElementById('form-dados'));">Quero receber!</button> </div><img id="imagemBox" style="display:none" src="" alt=""> </div></div><div id="content-material-obrigado"> <h3 class="tt">Obrigado! <img src="/assets/images/icon-higgor.png" alt=""></h3> <p>Em alguns instantes você receberá em seu e-mail uma cópia do material solicitado. Se preferir, clique no botão abaixo e acesso material agora mesmo.</p><p>Aproveite o contéudo!</p><a href="#" id="bt-material" target="_blank" class="btn" title="Baixar gratuitamente">Baixar gratuitamente</a> </div></div>
<script>var queryForm=function(e){!(!e||!e.reset)&&e.reset;var t=window.location.toString().split("?"),n=[];if(t.length>1){var o=t[1].split("&");for(i in o){var a=o[i].split("=");n[a[0]]=decodeURIComponent(a[1])}}document.querySelectorAll("input[type=hidden]").forEach((e,t)=>{var o=n[e.name];o&&(document.getElementsByName(e.name)[0].value=o)})};function enviarDados(e){if(e.checkValidity()){var t=new FormData(e);t.get("id_da_campanha")&&t.get("endpoint")&&(t.append("rdtrk",""),$.ajax({type:"POST",url:t.get("endpoint"),data:t,contentType:!1,cache:!1,processData:!1,dataType:"json",success:function(e){document.getElementById("content-material").style.display="none",document.getElementById("content-material-obrigado").style.display="block"},error:function(e){alert("Ops! Ocorreu um erro ao enviar os dados!"),console.error(JSON.stringify(e))}}),document.getElementById("content-material").style.display="none",document.getElementById("content-material-obrigado").style.display="block")}else e.reportValidity()}setTimeout(function(){queryForm()},3e3),id_campanha&&(document.getElementById("id_da_campanha").value=id_campanha),endpoint&&(document.getElementById("endpoint").value=endpoint),tituloBox&&(document.getElementById("tituloBox").innerHTML=tituloBox),descricaoBox&&(document.getElementById("descricaoBox").innerHTML=descricaoBox),url_material&&document.getElementById("bt-material").setAttribute("href",url_material),imagemBox&&(document.getElementById("imagemBox").setAttribute("src",imagemBox),document.getElementById("imagemBox").style.display="block");</script>
```

### Gatilho

###### Adicionando um gatilho como link.

Basta selecionar a imagem ou texto adicionar um Link e no campo adicionar o código abaixo alterado **{ID_DO_GATILHO}** pelo valor correspondente ao gatilho. _Manter as aspas(") no inicio e final_
`javascript:Huggy.startTrigger('{ID_DO_GATILHO}');`

###### Adicionando um gatilho a imagem.

Insira um campo do tipo HTML no texto e cole o código abaixo alterando as variáveis **{ID_DO_GATILHO}** e **{URL_DA_IMAGEM}**. _Manter as aspas(") no inicio e final_

````<div onclick="javascript:Huggy.startTrigger('{ID_DO_GATILHO}')"
          style="cursor:pointer">
	<img src="{URL_DA_IMAGEM}"
     alt="" style = "display: block; margin-left: auto; margin-right: auto; width: 100%;" border="0"/>
</div>```

### POPUP Modal
###### Adicionando um popup para exibição
Insira um campo do tipo HTML no texto e cole o código abaixo alterando as variáveis **{LINK_BANNER}** e **{URL_BANNER}**. _Manter as aspas(") no inicio e final_

![Campo HTML](https://blog.huggy.io/assets/images/campo-html.png)

```
<script>
    var modalShow = 5000; // Exibi o modal após 5 segundos
    var modalLink = "{LINK_BANNER}";
    var modalImagem = "{URL_BANNER}";
</script>
<style>#modal-show{position:fixed;width:100%;height:100%;background-color:rgba(0,0,0,.8);top:0;left:0;display:none;justify-content:center;align-items:center;z-index:1000}#modal-show div{position:relative;max-width:90%;animation:show-modal .2s ease-in-out;animation-fill-mode:forwards}#modal-show div::after{content:"";position:absolute;left:0;top:0;position:absolute;z-index:0;width:100%;height:100%}#modal-show a{border:0}#modal-show .close{position:absolute;right:5%;top:9%;display:block;width:40px;height:40px;border:0;z-index:1}#modal-show .button{position:absolute;left:30%;bottom:13%;display:block;width:41%;height:48px;border:0;z-index:1}#modal-show img{border:0;max-width:100%}@-webkit-keyframes show-modal{0%{opacity:0;transform:scale(0)}100%{opacity:1;transform:scale(1)}}@keyframes show-modal{0%{opacity:0;transform:scale(0)}100%{opacity:1;transform:scale(1)}}</style>
<div id="modal-show"> <div> <a href="javascript:;" onclick="document.getElementById('modal-show').style.display='none';" class="close"></a> <a href="" id="modalLinkEl" target="_blank" class="button"></a> <img src="" id="modalImagemEl" alt=""/> </div></div>
<script>modalShow&&modalImagem&&(setTimeout(function(){document.getElementById("modal-show").style.display="flex"},modalShow),document.getElementById("modalLinkEl").setAttribute("href",modalLink),document.getElementById("modalImagemEl").setAttribute("src",modalImagem));</script>
```
````
