---
layout: post
title:  "Como contribuir para um projeto no Github"
date:   2016-01-08 10:33:00 -0300
categories: Github Open-source
---
Para contribuir para qualquer projeto no Github, primeiro é necessário fazer um fork, de modo que uma cópia seja feita na sua conta, onde será possível manter alterações como qualquer outro. Esta pagina tem como intuito ser uma introdução à este procedimento.

### Fazendo o Fork

1. Vá na pagina principal(https://github.com/<nome do usuário>/<repositório>/) do projeto e no canto superior direito, clique no botão "Fork".

![](https://help.github.com/assets/images/help/repository/fork_button.jpg)

2. Ao clicar em fork, como indicado acima, o navegador será redirecionado para a pagina da sua cópia do repositório. Copie para a área de transferência o caminho do diretório, clicando no botão esquerdo indicado na imagem a seguir:

![](https://help.github.com/assets/images/help/repository/clone-repo-clone-url-button.png)

3. Faça o clone local do seu repositório.

```
git clone https://github.com/<nome do usuário>/<repositório>.git
```

4. Faça as alterações, salve-as e envie para o seu repositório no Github:

```
git add .
git commit -m "Algum comentário relevante"
git push origin
```

> O bloco acima é so um exemplo, em caso de duvida acesse este [help](https://git-scm.com/docs/git-commit).

### Fazendo o Pull Request (PR)
1. Vá à pagina principal do fork na sua conta do Github e clique em "New pull requeste". Será redirecionado para um pagina com as diferenças entre os dois repositórios (o original e o fork). Verifique se não há algo errado e clique em "Create pull request", indique as alterações feitas para o mantedor do projeto e confirme.

### Atualizando o repositório local com o principal

Agora é preciso configurar o seu repositório para que seja possível atualizar a partir do repositório oficial: Para isso adicione um outro repositório remoto ao local:

```
git remote add upstream https://github.com/<nome do usuário>/<repositório>.git
git fetch upstream
git merge upstream/master
```

> por convenção usa-se "upstream" para se referenciar ao repositório oficial.
