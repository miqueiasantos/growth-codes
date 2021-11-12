# Repositório de códigos para o blog
Desenvolvido para auxiliar a integração de formulários, links, banners e outros scripts para o blog.

## Itens

- [Materiais Gratuitos](#materiais-gratuitos)
- [Gatilho](#gatilho)
- [POPUP Modal](#popup-modal)

### Materiais Gratuitos
###### Scrip para definição de campanha para Materiais Educativos Gratuitos
Crie uma nova página e Selecione o template **Material**.
![This is an image](https://blog.huggy.io/assets/images/template-material.png)
No corpo do texto, inserira um campo do tipo HTML e cole o código abaixo alterando as variáveis **{URL_ENDPOINT}** e **{ID_CAMPANHA}**. _Manter as aspas(") no inicio e final_
![This is an image](https://blog.huggy.io/assets/images/campo-html.png)
```
<script>
    var endpoint = "{URL_ENDPOINT}";
    var id_campanha = "{ID_CAMPANHA}";
</script>
```


### Gatilho
###### Adicionando um gatilho como link.

Basta selecionar a imagem ou texto adicionar um Link e no campo adicionar o código abaixo alterado **{ID_DO_GATILHO}** pelo valor correspondente ao gatilho. _Manter as aspas(") no inicio e final_
```javascript:Huggy.startTrigger('{ID_DO_GATILHO}');```

### POPUP Modal
###### Adicionando um popup para exibição
Inserira um campo do tipo HTML no texto e cole o código abaixo alterando as variáveis **{LINK_BANNER}** e **{URL_BANNER}**. _Manter as aspas(") no inicio e final_
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