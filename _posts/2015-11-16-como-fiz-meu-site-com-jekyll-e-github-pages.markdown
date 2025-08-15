---
title:  "Como fiz meu site com Jekyll e GitHub Pages"
date: 2015-11-17
description: Um passo-a-passo de como fiz meu site com Jekyll e GitHub Pages e como você pode fazer o seu.
---

Após passar certo sufoco para construir e configurar este site com Jekyll e GitHub Pages, aqui está um passo-a-passo de <b>como você pode fazer o seu</b>. Sabe como é, eu sou de humanas. Se eu consegui, você também consegue.

O [Jekyll](https://jekyllrb.com/) é um gerador super-simplificado de sites estáticos. É grátis, código aberto, e uma ótima plataforma para blogs. Além disso, é a engrenagem por trás do [GitHub Pages](https://pages.github.com/), o que significa que você tem __hospedagem gratuita__ e integração facilitada com sua máquina através do [Git](https://git-scm.com/) (que é maravilhoso).

<figure class="mv4 tc">
    <img src="{{ site.url }}/assets/img/postagens/octojekyll.png" class="mw5" alt="Octogato - GitHub + Jekyll" />
    <figcaption>Octogato, o mascote do GitHub,<br> com o frasquinho do Jekyll <font color="red"><i class="fa fa-heart"></i></font></figcaption>
</figure>

Todo o sistema funciona com base em __arquivos de texto simples__, o que fará você se sentir [blogging like a hacker](https://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html) (olha a hype!). Aí está um primeiro obstáculo, você não terá uma interface gráfica mastigadinha como um tumblr, blogger ou worpress, mas contará com ótimos __guias e tutoriais__ para ajudar no processo e terá __controle completo__ sobre seu site ou blog.

Outros requisitos são saber se virar no __inglês__, já que a maioria dos usuários escrevem nesta língua e ter __paciência para procurar__ informações no google e na documentação do software.

O Jekyll roda nativamente no __Linux__, __Unix__, e no __Mac OS X__. Diz que até funciona no [Windows](https://jekyllrb.com/docs/windows/), mas saiba que vai ser meio na gambiarra.

Todo o passo-a-passo descrito nesta postagem foi feito no __Debian Jessie__, mas a maior parte é comum a todas as distribuições. Durante o guia, eu suponho que você não trema de medo do terminal, saiba rodar comandos como root e que convém um `apt-get update` antes de instalar qualquer coisa.

Além disso, nenhum conhecimento prévio é necessário, nem qualquer experiência com construção de websites. Vamos lá.

---

# Escolha um tema

Apesar de você ter a opção de começar um site do zero, nós vamos ser mais espertos do que isso e começar [escolhendo um __tema do jekyll__](https://jekyllthemes.org/).

Vá, gaste um tempo e escolha um que lhe agrade. Tem para todos os gostos, desde mais [simples](https://carte-noire.jacobtomlinson.co.uk/) e [minimalistas](https://nadjetey.github.io/redcup/) até alguns bem [completos](https://phlow.github.io/feeling-responsive/), [bacanosos](https://t413.com/SinglePaged/), e até meio [extravagantes](https://digitalmind.ch/themes/twister-jekyll-theme/demo/).

Da minha parte, comecei com o [Long Haul](https://brianmaierjr.com/long-haul/), criado por [Brian Maier](https://twitter.com/brianmaier). O tema é simples, bem instrumentalizado, e tem uma documentação razoável, mas acabei modificando muita coisa. Você também pode usar [minha própria versão do tema](https://github.com/ggio/ggio.github.io), a.k.a. este site que você acessa agora, como ponto de partida para o seu, mas recomendo começar com um tema mesmo, pela organização, limpeza e tals.

> <b> Atualização: </b> em 2025, migrei para o tema <a href="https://github.com/cotes2020/jekyll-theme-chirpy">Chirpy</a>, com alguns ajustes. Fiz isso basicamente porque queria algo minimalista e de fácil manutenção, ainda que com estilo. Continuo achando o <i>Long Haul</i> um ótimo ponto de partida, mas acabou caindo a ficha de que ele é um tema um tanto mais elaborado do que a média, com as vantagens e desvantagens disso.
{: .prompt-info }

---

# Meu GitHub, minha vida

Uma vez escolhido um tema, é hora de começar com o GitHub:

1. [Cadastre-se no GitHub](https://github.com/).
2. Faça uma ___fork___ do repositório do tema que você escolheu.
    <figure class="mv4 tc">
    <img src="{{ site.url }}/assets/img/postagens/fork.png" alt="Onde clicar para fazer a fork no GitHub" />
    <figcaption>Clica ali, ó.</figcaption> </figure>
3. Pronto, você já tem uma cópia completa (uma _fork_) do tema na sua conta.
4. Nas configurações, mude o nome do seu repositório para
`seu-nome-de-usuario.github.io`. Esta é a dica para que o [GitHub Pages](https://pages.github.com/) publique seu site.
    <figure class="mv4 tc">
        <img src="{{ site.url }}/assets/img/postagens/settings.png" alt="Onde mudar o nome do repositório no GitHub" />
        <figcaption>Ali você muda o nome.</figcaption>
    </figure>

Parabéns, você provavelmente já está online em `https://seu-nome-de-usuario.github.io` Talvez agora você queira trabalhar no formato e conteúdo antes de divulgar o endereço por aí. Vamos a isso.

---

# Trabalhando localmente com o Git e Jekyll

Para criar conteúdo e testar o site antes de deixá-lo brilhar na vida, nós precisamos do [Jekyll](https://jekyllrb.com/) para montar o site localmente e do [Git](https://git-scm.com/) para publicar as alterações no GitHub.

Você vai precisar também de um __editor de texto simples__. Eu recomendo fortemente o [Sublime Text](https://www.sublimetext.com/), que faz super juz ao nome, mas você pode usar qualquer um. O `gedit`, pré-instalado no Jessie, dá conta do recado.

## 1. Instale o Git


``` bash
apt-get install git
```

## 2. Instale o Jekyll

### Modo fácil

Depois de gastar horas pesquisando e instalando todos os [requisitos do Jekyll](https://jekyllrb.com/docs/installation/), descobri que é muito fácil instalá-lo no __Debian Jessie__. Tão fácil como:

``` bash
apt-get install jekyll
```

### Modo menos fácil

Mesmo que você seja desafortunado e sua distribuição não tenha esse pacote no repositório, ainda é bastante simples. Segue o passo-a-passo:

Instale as dependências [Ruby](https://www.ruby-lang.org/en/downloads/):

``` bash
apt-get install ruby
apt-get install ruby2.1-dev #=> ou a versão mais atual disponível
```

Agora as dependências [NodeJS](https://nodejs.org/):

``` bash
apt-get install curl
curl -sL https://deb.nodesource.com/setup | bash -
apt-get install nodejs
apt-get install build-essential
```

E, finalmente, o Jekyll:

``` bash
gem install jekyll --user-install
```


> Se você usa <b>Mac</b>, diz que o processo é parecido, mas substituindo o apt pelo <a href="https://brew.sh">Homebrew</a>.
> Agradeço ao <a href="https://www.facebook.com/diegolascasas">Las Casas</a> pela dica.
{: .prompt-info}

## 3. Clone seu repositório

Clonar um repositório significa fazer uma cópia em sua máquina. No terminal, navegue para onde deseja fazer o download (por exemplo, `/home/Site` ) e rode o comando abaixo, substituindo "endereço-do-repositório" pelo endereço real.

``` bash
git clone endereço-do-repositório
```

<figure class="mv4 tc">
    <img src="{{ site.url }}/assets/img/postagens/clone.png" alt="Como clonar o repositório no GitHub" />
    <figcaption>Use aquele endereço ali.</figcaption>
</figure>

## 4. Crie conteúdo


> Estrutura de pastas
>    <pre>     <i class="fa fa-folder-open"></i> <b>seu-nome-de-usuario.github.io</b>
>     ├── <i class="fa fa-file-text-o"></i> _config.yml
>     ├── <i class="fa fa-file-text-o"></i> index.html
>     ├── <span class="amarelo"><i class="fa fa-folder-open"></i></span> <b>_includes</b>
>     │   ├── <i class="fa fa-file-text-o"></i> footer.html
>     │   └── <i class="fa fa-file-text-o"></i> header.html
>     ├── <i class="fa fa-folder-open"></i> <b>_layouts</b>
>     │   ├── <i class="fa fa-file-text-o"></i> default.html
>     │   └── <i class="fa fa-file-text-o"></i> post.html
>     ├── <i class="fa fa-folder-open"></i> <b>_posts</b>
>     │   ├── <i class="fa fa-file-text-o"></i> 2011-10-25-coxinha-de-jaca.md
>     │   └── <i class="fa fa-file-text-o"></i> 2011-04-26-hello-world.md
>     └── <i class="fa fa-folder"></i> <b>_site</b></pre>
{: .prompt-tip}

A seguir, vai uma apresentação rápida de cada um dos itens. Saiba mais lendo a [documentação completa do Jekyll](https://jekyllrb.com/docs/structure/).

#### _config.yml

* Configurações gerais do site, como título e descrição, vão aqui.
* Seu tema provavelmente já tem tudo o que você precisa, consulte a documentação (se houver) e tome a liberdade de brincar à vontade com o código.

#### index.html

* Esta é sua homepage, cara :)

#### _includes

* Fragmentos reusáveis de código ou texto vão aqui. A ideia é evitar repetições desnecessárias.
* É comum que contenha o `header` e `footer` mas você pode usar para absolutamente qualquer coisa.
* Todo documento nessa pasta pode ser incluído facilmente em páginas e postagens com uma tag liquid.
Exemplo: {% raw %}`{% include xablau.html %}`{% endraw %}

#### _layouts

* São esquemas em HTML aplicáveis a páginas e posts.
* Para usá-los, você precisa anunciar com uma [YAML front matter](https://jekyllrb.com/docs/frontmatter/), um bloco simples de texto, separado por três traços, que __precisa ser a primeira coisa do arquivo__:

``` yaml
---
layout: post
title: Receita deliciosa de coxinha de jaca
---
```

#### _posts

* Aqui vão todas as suas postagens.
* Você pode escrever em [markdown](https://daringfireball.net/projects/markdown/syntax), que é infinitamente simples e recomendável, e usar HTML quando e se precisar.
* Os nomes dos arquivos precisam ser escritos em um __formato específico__: <br> ` YYYY-MM-DD-titulo.md `

Por exemplo, `2011-10-25-coxinha-de-jaca.md`, informa ao Jekyll a data 25 de Outubro de 2011 e o título "coxinha de jaca".

#### _site

* É nesta pasta que o Jekyll gera todos os arquivos que efetivamente serão servidos. Você pode ignorá-la sem remorso.
* Tudo aqui é constantemente reescrito, de forma que qualquer alteração que você fizer nesta pasta será perdida para todo o sempre.

## 5. Sirva e teste o site localmente

Navegue até a pasta do seu site e deixe o Jekyll fazer sua mágica:

``` bash
cd seu-nome-de-usuario.github.io
jekyll serve --watch
```
__Ta-dã__! Você pode ver seu site em ação em `https://localhost:4000`.

A flag `--watch` é opcional e faz com que suas alterações tenham efeito automaticamente (bastando atualizar a página no navegador).

>Perceba, porém, que o mesmo <b>não</b> vale para para alterações feitas em <b>`_config.yml`</b>. Para isso, você precisa interromper o processo no terminal com `ctrl+c` e rodar o seguinte comando (de preferência algumas vezes):
> ``` bash
> jekyll build
> ```
> Parece um detalhe, mas pode evitar você <i>chorar de raiva</i> após horas tentando mudar o título do site sem sucesso.
{: .prompt-warning}

## 6. Publique com Git

Uma vez satisfeito com as alterações, é hora de torná-las online com o [Git](https://git-scm.com/).


### Primeiro, um ajuste

Crie um arquivo de nome `.gitignore`, sem extensão, em sua pasta mãe com o seguinte conteúdo:

``` bash
_site
```

Sim, só isso. Este aquivo contém tudo que você quiser, err, que o git ignore. E eu sei que __você não quer que o git envie a pasta `_site`__ para o repositório (por padrão, o GitHub não precisa dela).

### Agora sim, publicando

Na pasta do site, rode:

``` bash
git add -A
git commit -m "minha primeira edição"
git push
```

Preencha seu login e senha do GitHub e __tcharã__, seu conteúdo está online. Confira em `https://seu-nome-de-usuario.github.io`.

__Entendendo os comandos acima__:

* `git add -A` "adiciona" todas as alterações que você realizou na pasta, inclusive as _deletações_ de arquivos, modificações e arquivos novos.
* `git commit -m "minha primeira edição"` "confirma" essas alterações e dá um nome para o _commit_. Este nome entre aspas é opcional e pode ser qualquer coisa, a finalidade é você poder se orientar caso precise [desfazer alguma alteração](https://git-scm.com/book/pt-br/v1/Git-Essencial-Desfazendo-Coisas).
* `git push` "empurra" o commit para o repositório remoto, ou seja, seu repositório no GitHub. Caso tenha problemas com essa etapa, tente `git push origin master`.

Parece complicado, né? No começo é um pouco mesmo, mas, acredite, o Git vai fazer valer a pena cada minuto gasto para aprender a usá-lo. Além de permitir a integração da sua máquina com o GitHub, o Git é __um poderoso software de controle de versões__ que vai tornar sua vida bem melhor.

Para entender mais, recomendo este [__guia prático__](https://rogerdudler.github.io/git-guide/index.pt_BR.html) e que você faça este [__mini-treinamento de 15 minutos__](https://try.github.io/levels/1/challenges/1). Além disso, a [documentação do Git](https://git-scm.com/doc) é completíssima, bem como o [tutorial da Atlassian](https://www.atlassian.com/git/tutorials/setting-up-a-repository).

---

# (Opcional / Avançado) Sincronizando o Jekyll local com o GitHub Pages

Tanto o [Jekyll](https://jekyllrb.com/docs/github-pages/#deploying-jekyll-to-github-pages) como o [GitHub Pages](https://help.github.com/articles/using-jekyll-with-pages/) sugerem que você sincronize sua instalação local do Jekyll com a usada pelo GitHub. É completamente opcional, mas isso __evita que você tenha surpresas__ com diferenças entre o site rodado na máquina e o gerado pelo GitHub.

Note que, para isso, você vai passar a precisar sempre de __acesso à internet__ para rodar o site localmente, mas é por uma boa causa.

__É fácil__:

1) Instale o [Bundler](https://bundler.io/).

``` bash
gem install bundler
```


2) Crie um arquivo com o nome `Gemfile` (sem extensão) na pasta do seu site com o seguinte conteúdo:

``` bash
source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
```

Caso não funcione, tente apenas com:

``` bash
source 'https://rubygems.org'
gem 'github-pages'
```

3) Navegue até a pasta e rode:

``` bash
bundle install
```

__Pronto__.

A partir de agora, você precisa rodar o Jekyll com o bundle. Basta adicionar `bundle exec` antes de todos os comandos jekyll. Por exemplo:


``` bash
bundle exec jekyll build
bundle exec jekyll serve --watch
```

Lembre-se de atualizar com `bundle update` frequentemente e você será feliz e próspero(a).

---

# Mais opcionais

Com os passos acima você já tem todos os instrumentos que precisa para construir e manter seu site Jekyll. A seguir, indico algumas implementações que fiz em meu site e que podem ser úteis para você.

## 404.md

Convém fazer uma [página de erro personalizada](/404.html) para seu site. Basta seguir as [instruções do GitHub](https://help.github.com/articles/custom-404-pages/).

## Tipografia é importante

Tome 10 minutos do seu tempo para ler este [guia interativo de tipografia](https://www.kaikkonendesign.fi/typography/#section/1), simples, acessível e direto ao ponto.

Você já deve saber, mas [nunca use preto](https://ianstormtaylor.com/design-tip-never-use-black/).


## Sitemap.xml

Gerar um Sitemap.xml é uma boa prática de [SEO](https://static.googleusercontent.com/media/www.google.com/en/us/webmasters/docs/search-engine-optimization-starter-guide.pdf) e fará com que a busca do google goste mais ainda de você. Basta seguir as [instruções do David Ensinger](https://davidensinger.com/2013/11/building-a-better-sitemap-xml-with-jekyll/).

## Integrando comentários do Disqus com Jekyll

O [Disqus](https://disqus.com/websites/) é uma plataforma de comentários bem útil e fácil de implementar. Eu até testei o [Muut](https://muut.com/), mas ele não é tão completo e bonitão.

Para integrar o Disqus com Jekyll, siga as [instruções do Perfectly Random](https://www.perfectlyrandom.org/2014/06/29/adding-disqus-to-your-jekyll-powered-github-pages/).

## Domínio customizado

O endereço padrão do github (seu-nome-de-usuario.github.io) já é gracinha o bastante, mas caso você queira, como eu quis, ter um domínio próprio, é fácil de fazer. O site continua hospedado no GitHub pages e um servidor de DNS faz o truque com o endereço. E, claro, você precisa pagar pelo domínio.

Eu segui as [instruções do Chen Jui Jing](https://www.chenhuijing.com/blog/setting-up-custom-domain-github-pages/), mas sugiro que você dê uma olhada também no [tutorial do Ensinger](https://davidensinger.com/2014/04/transferring-the-dns-from-namecheap-to-cloudflare-for-github-pages/).

## Adicionando Font Awesome

[Font Awesome](https://fontawesome.io/) é um pacote grátis com bilhões de [ícones úteis](https://fontawesome.io/icons/) e minimalistas, customizáveis e prontos para uso. É bem [facinho de implementar](https://fontawesome.io/get-started/).

<!--
## Realce de código com Prism.js

O Jekyll tem duas [opções nativas](https://jekyllrb.com/docs/templates/#code-snippet-highlighting) (leia-se mais leves e melhor integradas) de `realce de código` e o seu tema muito provavelmente também já vem com alguma opção __pronta para uso__.

Mas porque não dificultar um pouco implementando um sistema externo de realce? Foi o que eu fiz com o [Prism.js](https://prismjs.com/). O site deles tem as [instruções](https://prismjs.com/#basic-usage).

Detratores dirão que eu só fiz isso porque não consegui configurar nenhuma opção nativa, e eles estarão certos. Tirando que o Prism.js é lindo.
-->
## Integrando Jekyll com Reveal.js

[Reveal.js](https://lab.hakim.se/reveal-js/#/) é um sistema foda de criação de apresentações de slides em HTML. A integração com o Jekyll é bem descrita no [site do Luu Gia Thuy](https://luugiathuy.com/2015/04/jekyll-create-slides-with-revealjs/). Ele só esqueceu de dizer que, se você pretende modificar os temas padrão, você precisa __clonar__ (e não adicionar como submodule) o reveal.js à sua pasta. Você pode ter uma ideia melhor de como organizar as pastas e arquivos html dos slides no [meu repositório](https://github.com/ggio/ggio.github.io/tree/master/slides).

## Páginas de subcategorias

Pela natureza meio esquizo deste site, eu <del>quis</del> precisei dividir as postagens entre duas categorias, "Psicologia para concurso" e "blog", e isso __complica tudo__. Depois de pesquisar bastante, fiquei satisfeito com as instruções nessa [resposta no Stack Overflow](https://stackoverflow.com/a/26684859).

Obs.: Em 2020, junto com a mudança do tema, achei melhor simplificar e me livrar dessa divisão. Minha vida tem sido 34,5% mais fácil desde então.

---

# É isso

__Parece muito, mas é só o começo__. O universo de informação em volta do Jekyll e GitHub é gigantesco e logo logo você estará descobrindo novas soluções e ferramentas. Não se assuste com o volume de informação. Uma vez passado o susto inicial, você estará gerando sites estáticos com um estralar de dedos.

Nesse guia, eu abrangi a maior parte do que descobri até agora, mas muita coisa ficou de fora. Algo ficou mal explicado ou você empacou em alguma etapa? É só falar ;)
