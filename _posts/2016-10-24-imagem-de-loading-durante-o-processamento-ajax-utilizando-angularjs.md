---
layout: post
title:  "Imagem de Loading durante o processamento Ajax utilizando AngularJS"
date:   2016-10-24 16:35:40 -0300
categories: AngularJs JavaScript Front-end
---
No intuito de evitar que o usuário pense que a aplicação está travada, costuma-se apresentar pequenas imagens animadas, como a que segue abaixo:
<p align="center">
  <img src="http://www.drivethrurpg.com/shared_images/ajax-loader.gif" width="200px" height="200px">
</p>

> Eu vou assumir que o leitor tem um conhecimento básico de angular, mas qualquer dúvida pode pedir ajudar. ;)

Utilizando AngularJS, este processo pode ser facilitado criando-se uma diretiva (abaixo), que identificará se deve esconder ou apresentar o elemento de acordo com a quantidade de requestes pendentes de resposta.

```js
app = angular.module("meuApp");

app.directive('loading', function ($http){
    return {
        restrict: 'A',
        link: function (scope, elm) {
            //Neste ponto, é uma função que retornará true, caso ainda haja requestes pendentes
            scope.isLoading = function () {
                return $http.pendingRequests.length > 0;
            };

            //Com a função acima, crio um "verificador", quando o valor retornado pela função (isLoading) declara acima.
            scope.$watch(scope.isLoading, function (isLoading) {
                if(isLoading) { //Auto explicativo...
                    elm.show();
                }else{
                    elm.hide();
                }
            });
        }
    };

});
```

Com a diretiva pronta, bastá colocar o seguinte html ao final da pagina (antes deo ).
```html
<div class="loading-spiner-holder">
  <div class="loading-spiner">
    <img src="[Caminho para a imagem]" />
  </div>
</div>
```

Agora só falta posicionar corretamente a imagem e para isso, usaremos as classes à seguir:
```css
.loading-spiner-holder{
  position: absolute;
  top: 50%;
  left: 50%;
  margin-top: -100px;
  margin-left: -100px;
}
.loading-spiner img{
  width: 200px;
  height: 200px;
}
```

Pronto, se tudo deu certo, sua aplicação / pagina estará indicando que há um processamento pendente.

Esta mesma abordagem poderia ser utilizada para esconder a pagina, porem, prefiro mostrar o gif animado.
