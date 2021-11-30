# Repositório de códigos para o blog
Desenvolvido para auxiliar a integração de formulários, links, banners e outros scripts para o blog.

## Itens

- [Materiais Gratuitos](#materiais-gratuitos)
- [Formulário para posts de Materiais Gratuitos](#formulario-para-posts-de-materiais-gratuitos)
- [Gatilho](#gatilho)
- [POPUP Modal](#popup-modal)

### Materiais Gratuitos
###### Scrip para definição de campanha para Materiais Educativos Gratuitos
Crie uma nova página e Selecione o template **Material**.

![Template Material](https://blog.huggy.io/assets/images/template-material.png)

No corpo do texto, inserira um campo do tipo HTML e cole o código abaixo alterando as variáveis **{URL_ENDPOINT}**, **{ID_CAMPANHA}** e  **{URL_PAGINA_OBRIGADO}**. _Manter as aspas(") no inicio e final_

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
Inserira um campo do tipo HTML no texto e cole o código abaixo alterando as variáveis **{LINK_BANNER}** e **{URL_BANNER}**. _Manter as aspas(") no inicio e final_

![Campo HTML](https://blog.huggy.io/assets/images/campo-html.png)

```
    <script>
        var endpoint = "{URL_ENDPOINT}";
        var id_campanha = "{ID_CAMPANHA}";
        var tituloBox = "{TITULO_BOX}"; // Exibi o modal após 5 segundos
        var descricaoBox = "{DESCRICAO_box}";
        var imagemBox = "{URL_IMAGEM}";
    </script>
    <style>.box-custom-material{border-radius:30px;overflow:hidden;background:url(assets/images/bg-box.svg) right center no-repeat #f5f5f5;padding:32px 28px 22px 66px;width:100%;max-width:770px;margin:30px auto;font-size:14px;line-height:1.4em;color:#617984}.box-custom-material .info{max-width:570px}.box-custom-material .tt{font-weight:500;font-size:20px;line-height:1.6em;color:#263645;margin:0 0 5px 0}.box-form-custom{display:flex;justify-content:space-between;align-items:flex-start}.box-form-custom img{max-width:365px;width:100%}.box-form-custom form{width:262px;padding-top:36px;flex-shrink:0;margin-right:30px}.box-form-custom input,.box-form-custom select{border:0;background-color:#fff;margin-bottom:15px;border-radius:5px;width:100%;font-family:Rubik;color:#617984;font-size:13px;padding:.5em .923em}.box-form-custom button{background:#ff0068;border-radius:35px;font-family:Poppins;font-weight:500;font-size:12px;line-height:1.6em;color:#fff;padding:.406em 1.5em}@media(max-width:992px){.box-custom-material{max-width:calc(100% - 50px);padding-left:35px}}@media(max-width:767px){.box-custom-material{padding:32px 28px}.box-form-custom{flex-wrap:wrap}.box-form-custom img{display:table;margin:0 auto;order:1}.box-form-custom form{order:2;width:100%;margin-right:0}.box-form-custom button{display:table;margin:0 auto;max-width:80%}}</style>
    <div class="box-custom-material"> <div class="tt">Temos conteúdos exclusivos para você.</div><div class="info">Receba entrevistas com profissionais, cursos, materiais e conteúdos exclusivos no seu e-mail. Tudo para fazer o seu negócio crescer com a ajuda de conversas no WhatsApp. </div><div class="box-form-custom"> <form action="" onsubmit="enviarDados(this); return false;"> <input name="endpoint" id="endpoint" type="hidden" value=""> <input name="id_da_campanha" id="id_da_campanha" type="hidden" value=""> <input type="hidden" name="utm_source" value=""> <input type="hidden" name="utm_medium" value=""> <input type="hidden" name="utm_campaign" value=""> <input type="hidden" name="utm_term" value=""> <input type="hidden" name="utm_content" value=""> <input type="text" name="nome" placeholder="Nome Completo" required> <input type="email" name="email" placeholder="E-mail" required> <select name="segmento" required> <option value="">Segmento do negócio</option> </select> <select name="segmento" required> <option value="">Quantidade de atendimentos diários</option> </select> <button>Quero receber!</button> </form> <img src="/assets/images/imagem-box.png" alt=""> </div></div>
    <script>var queryForm=function(e){!(!e||!e.reset)&&e.reset;var n=window.location.toString().split("?"),t=[];if(n.length>1){var a=n[1].split("&");for(i in a){var o=a[i].split("=");t[o[0]]=decodeURIComponent(o[1])}}document.querySelectorAll("input[type=hidden]").forEach((e,n)=>{var a=t[e.name];a&&(document.getElementsByName(e.name)[0].value=a)})};function enviarDados(e){var n=new FormData(e);n.get("id_da_campanha")&&n.get("endpoint")&&(n.append("rdtrk",""),$.ajax({type:"POST",url:n.get("endpoint"),data:n,contentType:!1,cache:!1,processData:!1,dataType:"json",success:function(n){url?window.location.replace(url):(e.style.display="none",e.reset(),document.querySelector(".form-obrigado").style.display="block")},error:function(e){alert("Ops! Ocorreu um erro ao enviar os dados!"),console.error(JSON.stringify(e))}}))}setTimeout(function(){queryForm()},3e3),id_campanha&&(document.getElementById("id_da_campanha").value=id_campanha),endpoint&&(document.getElementById("endpoint").value=endpoint);</script>
```

### Gatilho
###### Adicionando um gatilho como link.

Basta selecionar a imagem ou texto adicionar um Link e no campo adicionar o código abaixo alterado **{ID_DO_GATILHO}** pelo valor correspondente ao gatilho. _Manter as aspas(") no inicio e final_
```javascript:Huggy.startTrigger('{ID_DO_GATILHO}');```

### POPUP Modal
###### Adicionando um popup para exibição
Inserira um campo do tipo HTML no texto e cole o código abaixo alterando as variáveis **{LINK_BANNER}** e **{URL_BANNER}**. _Manter as aspas(") no inicio e final_

![Campo HTML](https://blog.huggy.io/assets/images/campo-html.png)

```
    <script>
        var modalShow = 5000; // Exibi o modal após 5 segundos
        var modalLink = "{LINK_BANNER}";
        var modalImagem = "{URL_BANNER}";
    </script>
    <style>#modal-show{position:fixed;width:100%;height:100%;background-color:rgba(0,0,0,.8);top:0;left:0;display:none;justify-content:center;align-items:center;z-index:1000}#modal-show div{position:relative;max-width:90%;animation:show-modal .2s ease-in-out;animation-fill-mode:forwards}#modal-show div::after{content:"";position:absolute;left:0;top:0;position:absolute;z-index:0;width:100%;height:100%}#modal-show a{border:0}#modal-show .close{position:absolute;right:5%;top:9%;display:block;width:40px;height:40px;border:0;z-index:1}#modal-show .button{position:absolute;left:30%;bottom:13%;display:block;width:41%;height:48px;border:0;z-index:1}#modal-show img{border:0;max-width:100%}@-webkit-keyframes show-modal{0%{opacity:0;transform:scale(0)}100%{opacity:1;transform:scale(1)}}@keyframes show-modal{0%{opacity:0;transform:scale(0)}100%{opacity:1;transform:scale(1)}}</style>
    <script>modalShow&&modalImagem&&(setTimeout(function(){document.getElementById("modal-show").style.display="flex"},modalShow),document.getElementById("modalLinkEl").attributes("href",modalLink),document.getElementById("modalImagemEl").attributes("src",modalImagem));</script>
    <div id="modal-show"> <div> <a href="javascript:;" onclick="document.getElementById('modal-show').style.display='none';" class="close"></a> <a href="" id="modalLinkEl" target="_blank" class="button"></a> <img src="" id="modalImagemEl" alt=""/> </div></div>
```