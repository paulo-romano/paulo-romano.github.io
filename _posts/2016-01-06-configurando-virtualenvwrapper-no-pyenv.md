---
layout: post
title:  "Configurando Virtualenvwrapper no Pyenv"
date:   2016-01-06 10:33:00 -0300
categories: Python
---
## O que é

Você encontrará uma explicação mais detalhada [neste post](https://pythonhelp.wordpress.com/2012/10/17/virtualenv-ambientes-virtuais-para-desenvolvimento/) excelente do Valdir Stumm. Mas reduzidamente:

* O **Pyenv** é um "gerenciador" de versões de Python, facilita a instalação e troca entre as versões do Python. Apesar de ser exclusivo para sistemas *unix like*, para quem usa vagrant também pode ser uma mão na roda. Neste [post](https://pauloromano.wordpress.com/2016/01/05/gerenciando-versoes-do-python-com-o-pyenv/) do [Allisson Azevedo](http://allissonazevedo.com/) Um excelente passo-a-passo para instala-lo.

* O **Virtualenvwrapper** é uma extensão para facilitar a criação, manipulação e uso de ambientes virtuais do Python.


## Configuração do plugin Virtualenvwrapper

1. Baixe a ultima versão do plugin dentro do diretório .pyenv/plugins/ do seu usuário:

```console
git clone https://github.com/yyuu/pyenv-virtualenvwrapper.git ~/.pyenv/plugins/pyenv-virtualenvwrapper
```

2. Ativação do plugin:
Adicione a linha abaixo no final do seu .bashrc. Que se encontra dentro do diretório do seu usuário.
```console
pyenv virtualenvwrapper
```

Atualize o terminal
```console
source ~/.bashrc
```
> Caso tenha colocado no .profile, adeque a instrução acima.

Pronto, agora é possível utilizar todos os comando do virtualenvwrapper, como o **mkvirtualenv** (para criar um virtualenv) ou **workon** . Mais comandos [aqui](https://virtualenvwrapper.readthedocs.org/en/latest/command_ref.html) e veja também a [documentação](https://virtualenvwrapper.readthedocs.org/en/latest/).
