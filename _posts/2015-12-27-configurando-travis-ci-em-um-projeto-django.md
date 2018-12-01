---
layout: post
title:  "Configurando Travis-CI em um projeto Django"
date:   2015-12-27 22:39:00 -0300
categories: Github Open-source
---
### **O que é:**

Travis-CI é um serviço de integração continua (CI :P) que pode ser conectado à repositórios do GitHub. Basicamente ele fica encarregado de rodar testes a cada vez que há uma alteração no repositório, e caso aconteça algum erro / falha os responsáveis serão avisados.

### **Como configurar:**

*   Primeiro crie uma conta em [https://travis-ci.org/](https://travis-ci.org/)
*   Logado na conta, dê acesso Travis-CI à sua conta do GitHub [https://travis-ci.org/auth](https://travis-ci.org/auth) e indique qual repositório será monitorado.
*   Na raiz do seu repositório crie um arquivo .travis.yml para manter as configurações para o build do projeto, com o seguinte conteúdo:

https://gist.github.com/paulo-romano/e272ad570dec90f33897

*   Salve as alterações no repositório (commit) na alteração e suba-a (push) para o GitHub.
*   Entre no painel do repositório ([https://travis-ci.org/](https://travis-ci.org/)) e espere o build terminar. O site carrega automaticamente a página quando identifica que o repositório monitorado sofreu mudanças. Pronto, se tudo foi configurado certo, e não tenha erros no seu código, a build aconteceu sem problemas.

### **Alterando no README.md:**

Agora diga pra todo mundo que seu projeto está redondo e sem erros, indicando na página principal do projeto no GitHub, para isso:

*   Pagina do Travis-CI para o projeto, no cabeçalho há uma imagem logo ao lado do nome do projeto, preferencialmente ![passing](https://pauloromano.files.wordpress.com/2015/12/passing.png)(kkkk)... Clique nele e no dropdown logo abaixo de "branch" da caixa que se abrirá, mude para Markdown e copie o conteúdo gerado na caixa de texto.
*   Na raiz do projeto adicione um arquivo README.md (Caso já não o tenha feito). Este arquivo será lido pelo o github e será exibido como pagina de boas vindas do seu repositório.
    *   No final deste arquivo, cole o conteúdo copiado (instrução anterior).
*   Salve as alterações no repositório (commit) na alteração e suba-a (push) para o GitHub. Pronto, com isso ao acessar o repositório será exibido o status do build para o projeto.
