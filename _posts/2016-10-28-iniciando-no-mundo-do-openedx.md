---
layout: post
title:  "Iniciando No Mundo Do Openedx"
date:   2016-10-28 23:34:40 -0200
categories: openedx
---
![Open edX](https://open.edx.org/sites/all/themes/edx_open/logo.png)

### Sobre a iniciativa
A iniciativa, sem fins lucrativos, [edX](http://bit.ly/site-edx) foi iniciada pelas universidades Havard e MIT, com o intuito de ser um MOOC (Curso Online Aberto e Massivo, traduzindo do inglês) para disponibilizar curso de diversas faculdades de todo o mundo.

O [Open edx](http://bit.ly/site-open-edx), é a plataforma opensource, que roda por trás do edx. É composta basicamente do sistema de gerenciamento de cursos (CMS) e pelo sistema de gerenciamento de alunos (LMS), porem é altamente "plugavel" atravez da criação de XBlocks.

### Por que Open edX
* Python e Django em maior parte do código.
* Possui um excelente aplicativo mobile.
* Altamente "plugavel" e customizável, através de XBlocks e bem estruturado.
* Várias instituições utilizam como plataforma de ensino a distancia, veja lista neste [link](http://bit.ly/open-edx-powered).

### Instalação e execução
Neste pequeno tutorial, vamos ver como instalar e executar a versão de desenvolvimento (devstack) da plataforma Open edX.

> Tomei como base [este topico](http://edx.readthedocs.io/projects/edx-installing-configuring-and-running/en/latest/installation/devstack/install_devstack.html#install-devstack) da documentação oficial, que é bem completa neste quesito, porem, em inglês.
> Não vou entrar muito em detalhes sobre o vagrant, um bom começo para estudos pode ser esta pagina da [wikipedia](https://en.wikipedia.org/wiki/Vagrant_(software)).

Primeiro é necessário instalar os pré-requisitos: VirtualBox + Vagrant, que pode ser visto neste [link](http://www.edivaldobrito.com.br/virtualbox-no-linux/); e a instalação do [NFS](https://pt.wikipedia.org/wiki/Network_File_System) que mostrarei a seguir.

* Instale o pacote:
```
sudo apt install nfs-kernel-server
```

* E após a instalação, verifique se o mesmo está em execução da seguinte forma:
```
sudo service nfs-kernel-server status
```

> Para ver uma lista de comandos possíveis, troque o parâmetro "status" por "help".

Com os pré-requisitos instalados é hora de começar a configuração da plataforma propriamente dita. Para isso, tirei como base a própria documentação. Para isso, siga os seguintes passos:

* Crie uma pasta de trabalho:
```
mkdir eucalyptus.2
cd eucalyptus.2
```

* Baixe o script que auxiliará na instalação:
```
curl -OL https://raw.githubusercontent.com/edx/configuration/open-release/eucalyptus.2/util/install/install_stack.sh
```

* Baixe e execute a versão de desenvolvimento da maquina virtual:
```
bash install_stack.sh devstack open-release/eucalyptus.2
```

> Para baixar a versão de produção basta trocar o parâmetro "devstack" por "fullstack", mas não irei aborda-la neste tutorial.

* Conecte-se à maquina:
```
vagrant ssh
```

> Se aparecer a mensagem de boas vindas, parabéns, a maquina estará funcionando corretamente, do contrário, pode dar um grito aqui que ti ajudarei. A seguir apresentarei os passos para executar tanto o LMS, quanto o CMS.

Agora é chegada a hora de executar a plataforma:

* Uma vez conectado a maquina (vide passo anterior), há duas opçoes para configurar o ambiente, trocar para o usuário "edxapp" (que configurará automaticamente o ambiente) ou manualmente (que explicarei em um poste futuro... quem sabe rsrs):
```
sudo su edxapp
#não será requisitado senha.
```

Agora, com auxilio do [paver](https://github.com/paver/paver) (não é pra comer XD~), vamos executar a aplicação voltada para o aluno (LMS):
```
paver devstack lms --fast
```

* Espere carregar ate aparecer a famosa mensagem do servidor de desenvolvimento do Django, informando que para para-lo é só teclar CONTROL+C e acesse o caminho [127.0.0.1:8000](http://127.0.0.1:8000) no seu navegador. Pronto, é só se cadastrar.

* E para executar a aplicação voltada para o instrutor (CMS):
```
paver devstack cms --fast
```

> O parâmetro "--fast" diz ao paver para não atualizar as dependências do python e não compilar os assets... deixa ele ai, demora muito sem ele, vai por mim.
> Apos se registrar o sistema irá "mandar" um e-mail de ativação, olhe no terminal, o conteúdo do e-mail estará, clique no link de ativação.


(Opcional) Para tornar-se um usuário administrador:
```
cd ~
./manage.py lms shell --settings=aws #para abrir o shell
# ...
>>> from django.contrib.auth.models import User
>>> me = User.objects.get(username='[nome do usuário]')
>>> me.is_staff = True
>>> me.is_superuser = True
>>> me.save()
#tecle CONTROL+D para sair.
```
