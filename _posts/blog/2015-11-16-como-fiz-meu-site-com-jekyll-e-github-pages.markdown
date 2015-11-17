---
layout: post
categories: blog
title:  "Como fiz meu site com Jekyll e GitHub Pages"
date: 2015-11-16
description: 
comments: true
---

<p class="intro">

</p>

O Jekyll é um gerador de códigos estáticos.


Requisitos:

* inglês
* procurar
* Linux, Unix, or Mac OS X (Diz que tem como no [windows](http://jekyllrb.com/docs/windows/) )

Eu uso Debian Jessie.

Suponho que:

* você saiba um mínimo de linux, sabe entrar como root e que convém um apt-get update antes de instalar qualquer coisa.


Você __não__ precisa saber lhufas de HTML ou CSS, mas uma hora ou outra, se você for afabado como eu, vai acabar chafurdando nisso também.

<figure>
    <img src="{{ '/assets/aux/octojekyll.png' | prepend: site.baseurl }}" alt="Octogato - GitHub + Jekyll" style="width: 50%; height: 50%"> 
    <figcaption>Octogato, o mascote do GitHub, com o frasquinho do Jekyll <span class="bad"><i class="fa fa-heart"></i></span></figcaption>
</figure>


# Escolha um tema

Apesar de você ter a opção de começar um site do zero, nós vamos ser mais espertos do que isso e começar [escolhendo um __tema do jekyll__](http://jekyllthemes.org/).

Vá, gaste um tempo e escolha um que lhe agrade. Tem para todos os gostos, desde mais [simples](http://carte-noire.jacobtomlinson.co.uk/) e [minimalistas](http://nadjetey.github.io/redcup/) até alguns bem [completos](https://phlow.github.io/feeling-responsive/) e meio [extravagantes](http://digitalmind.ch/themes/twister-jekyll-theme/demo/).

Da minha parte, comecei com o [Long Haul](http://brianmaierjr.com/long-haul/), criado por [Brian Maier](https://twitter.com/brianmaier). O tema é simples, bem instrumentalizado, e tem uma documentação razoável, mas acabei modificando muita coisa. Você também pode usar [minha própria versão do tema](https://github.com/ggio/ggio.github.io), a.k.a. este site que você acessa agora, como ponto de partida para o seu, mas recomendo começar com um tema mesmo, pela organização e limpeza.

# Meu GitHub, minha vida

Uma vez escolhido um tema, é hora de começar com o GitHub:

1. [Cadastre-se no GitHub](https://github.com/).
2. Faça uma ___fork___ do repositório do tema que você escolheu. 
<figure>
    <img src="/assets/aux/fork.png" alt="Onde clicar para fazer a fork no GitHub"> 
    <figcaption>Clica ali, ó.</figcaption>
</figure>
3. Pronto, você já tem uma cópia completa (uma _fork_) do tema na sua conta.
4. Nas configurações, mude o nome do seu repositório para <code class="language-bash">seu-nome-de-usuario.github.io</code>. Esta é a dica para que o [GitHub Pages](https://pages.github.com/) publique seu site no endereço de mesmo nome.
<figure>
    <img src="/assets/aux/settings.png" alt="Onde mudar o nome do repositório no GitHub"> 
    <figcaption>Ali você muda o nome.</figcaption>
</figure>

Parabéns, seu site ou blog provavelmente já está online em <code class="language-bash">http://seu-nome-de-usuario.github.io</code>! Talvez agora você queira trabalhar no formato e conteúdo antes de espalhá-lo por aí. Vamos a isso.

# Trabalhando localmente com o Git e Jekyll

Para criar conteúdo e testar o site antes de deixá-lo brilhar na vida, nós precisamos do [Jekyll](http://jekyllrb.com/) para montar o site localmente e do [Git](https://git-scm.com/) para publicar as alterações no GitHub. 

Você vai precisar também de um __editor de texto simples__. Eu recomendo fortemente o [Sublime Text](http://www.sublimetext.com/), que faz super juz ao nome, mas você pode usar qualquer um. O `gedit`, pré-instalado no Jessie, dá conta do recado.

## 1. Instale o Git

<pre><code class="language-bash">apt-get install git</code></pre>

## 2. Instale o Jekyll

### Modo fácil

Depois de gastar horas pesquisando e instalando todos os [requisitos do Jekyll](http://jekyllrb.com/docs/installation/), descobri que é muito fácil instalá-lo no Debian Jessie. Tão fácil como:  

<pre><code class="language-bash">apt-get install jekyll</code></pre>

### Modo menos fácil

Mesmo que você seja desafortunado e sua distribuição não tenha esse pacote no repositório, ainda é bastante simples. Segue o passo-a-passo:

Instale as dependências [Ruby](http://www.ruby-lang.org/en/downloads/):

<pre><code class="language-bash">apt-get install ruby
apt-get install ruby2.1-dev
</code></pre>

Agora as dependências [NodeJS](http://nodejs.org/):

<pre><code class="language-bash">apt-get install curl
curl -sL https://deb.nodesource.com/setup | bash -
apt-get install nodejs
apt-get install build-essential</code></pre>

E, finalmente, o Jekyll:

<pre><code class="language-bash">gem install jekyll --user-install
</code></pre>

## 3. Clone seu repositório

Clonar um repositório significa fazer uma cópia em sua máquina. No terminal, navegue para onde deseja fazer o download (por exemplo, <code class="language-bash">/home/Site</code>) e rode o comando abaixo, substituindo "endereço-do-repositório" pelo endereço real.

<pre><code class="language-bash">git clone endereço-do-repositório</code></pre>

<figure>
    <img src="/assets/aux/clone.png" alt="Como clonar o repositório no GitHub">
    <figcaption>Use aquele endereço ali.</figcaption>
</figure>

## 4. Crie conteúdo

Sua pasta provavelmente tem uma estrutura similar a esta:

<div class="caixa-esq"><pre>     <span class="amarelo"><i class="fa fa-folder-open"></i></span> <b>seu-nome-de-usuario.github.io</b>
     <span class="sutil">├──</span> <i class="fa fa-file-text-o"></i> _config.yml
     <span class="sutil">├──</span> <i class="fa fa-file-text-o"></i> index.html
     <span class="sutil">├──</span> <span class="amarelo"><i class="fa fa-folder-open"></i></span><b>_includes</b>
     <span class="sutil">│</span>   <span class="sutil">├──</span> <i class="fa fa-file-text-o"></i> footer.html
     <span class="sutil">│</span>   <span class="sutil">└──</span> <i class="fa fa-file-text-o"></i> header.html
     <span class="sutil">├──</span> <span class="amarelo"><i class="fa fa-folder-open"></i></span> <b>_layouts</b>
     <span class="sutil">│</span>   <span class="sutil">├──</span> <i class="fa fa-file-text-o"></i> default.html
     <span class="sutil">│</span>   <span class="sutil">└──</span> <i class="fa fa-file-text-o"></i> post.html
     <span class="sutil">├──</span> <span class="amarelo"><i class="fa fa-folder-open"></i></span> <b>_posts</b>
     <span class="sutil">│</span>   <span class="sutil">├──</span> <i class="fa fa-file-text-o"></i> 2011-10-25-coxinha-de-jaca.md
     <span class="sutil">│</span>   <span class="sutil">└──</span> <i class="fa fa-file-text-o"></i> 2011-04-26-hello-world.md
     <span class="sutil">└──</span> <span class="amarelo"><i class="fa fa-folder"></i></span><b>_site</b></pre>
</div>

A seguir, vai uma apresentação rápida de cada um dos itens. Saiba mais lendo a [documentação completa do Jekyll](http://jekyllrb.com/docs/structure/).

#### _config.yml

* Configurações gerais do site, como título e descrição, vão aqui. 
* Seu tema provavelmente já tem tudo o que você precisa, consulte a documentação (se houver) e tome a liberdade de brincar à vontade com o código.
 
#### index.html

* Esta é sua homepage, cara :)

#### _includes

* Fragmentos reusáveis de HTML vão aqui. A ideia é evitar repetições desnecessárias.
* É comum que contenha o `header` e `footer` mas você pode usar para absolutamente qualquer coisa.
* Todo documento nessa pasta pode ser incluído facilmente em páginas e postagens com uma tag liquid. 
Exemplo: {% raw %}<pre><code class="language-bash">{% include xablau.html %}</code></pre>{% endraw %}

#### _layouts

* São esquemas em HTML aplicáveis a páginas e posts.
* Para usá-los, você precisa anunciar com uma [YAML front matter](http://jekyllrb.com/docs/frontmatter/), um bloco simples de texto, separado por três traços, que __precisa ser a primeira coisa do arquivo__:
<pre><code class="language-bash">---
layout: post
title: Receita deliciosa de coxinha de jaca
---</code></pre>

#### _posts

* Aqui vão todas as suas postagens.
* Você pode escrever em [markdown](https://daringfireball.net/projects/markdown/syntax), que é infinitamente simples e recomendável, e usar HTML quando e se precisar.
* Os nomes dos arquivos precisam ser escritos em um __formato específico__: 
<pre><code class="language-bash">YYYY-MM-DD-titulo.md</code></pre>
Por exemplo, <code class="language-bash">2011-10-25-coxinha-de-jaca.md</code>, informa ao Jekyll a data 25 de Outubro de 2011 e o título "coxinha de jaca".

#### _site

* É nesta pasta que o Jekyll gera todos os arquivos que efetivamente serão servidos. Você pode ignorá-la sem remorso.
* Tudo aqui é constantemente reescrito, de forma que qualquer alteração que você fizer nesta pasta será perdida para todo o sempre.

## 5. Sirva e teste o site localmente

Navegue até a pasta do seu site e deixe o Jekyll fazer sua mágica:

<pre><code class="language-bash">cd seu-nome-de-usuario.github.io
jekyll serve --watch</code></pre>

__Ta-dã__! Você pode ver seu site em ação em <code class="language-bash">http://localhost:4000</code>. 

A flag <code class="language-bash">--watch</code> é opcional e faz com que suas alterações tenham efeito automaticamente (bastando atualizar a página no navegador).

<div class="caixamarela">
<center><span class="amarelo"><i class="fa fa-exclamation-triangle fa-2x"></i>
</span></center>
<p>Perceba, porém, que o mesmo não vale para para alterações feitas em <code class="language-bash">_config.yml</code>. Para isso, você precisa interromper o processo no terminal com <code class="language-bash">ctrl+C</code> e rodar o seguinte comando (de preferência algumas vezes):</p>

<pre><code class="language-bash">jekyll build</code></pre>

<p>Parece um detalhe, mas pode evitar você <i>chorar de raiva</i> após horas tentando mudar o título do site sem sucesso.</p>
</div>

## 6. Publique com Git

Uma vez satisfeito com as alterações, é hora de torná-las online com o [Git](https://git-scm.com/). Na pasta do site, rode:

<pre><code class="language-bash">git add -A
git commit -m "minha primeira edição"
git push</code></pre>

Preencha seu login e senha do GitHub e __tcharã__, seu conteúdo está online. Confira em <code class="language-bash">http://seu-nome-de-usuario.github.io</code>.

__Entendendo os comandos acima__:

* <code class="language-bash">git add -A</code> "adiciona" todas as alterações que você realizou na pasta, inclusive as _deletações_ de arquivos, modificações e arquivos novos.
* <code class="language-bash">git commit -m "minha primeira edição"</code> "confirma" essas alterações e dá um nome para o _commit_. Este nome entre aspas é opcional e pode ser qualquer coisa, a finalidade é você poder se orientar caso precise [desfazer alguma alteração](https://git-scm.com/book/pt-br/v1/Git-Essencial-Desfazendo-Coisas).
* <code class="language-bash">git push</code> "empurra" o commit para o repositório remoto, ou seja, seu repositório no GitHub. Caso tenha problemas com essa etapa, tente <code class="language-bash">git push origin master</code>.

Parece complicado, né? No começo é um pouco mesmo, mas, acredite, o Git vai fazer valer a pena cada minuto gasto para aprender a usá-lo. Além de permitir a integração da sua máquina com o GitHub, o Git é __um poderoso software de controle de versões__ e tem tudo pra tornar sua vida melhor.

Para entender melhor, recomendo este [guia prático](http://rogerdudler.github.io/git-guide/index.pt_BR.html) e que você faça esse [mini-treinamento de 15 minutos](https://try.github.io/levels/1/challenges/1). Além disso, a [documentação do Git](https://git-scm.com/doc) é completíssima, bem como o [tutorial da Atlassian](https://www.atlassian.com/git/tutorials/setting-up-a-repository).


## (Opcional / Avançado) Sincronizando o Jekyll local com o GitHub Pages

Tanto o [Jekyll](http://jekyllrb.com/docs/github-pages/#deploying-jekyll-to-github-pages) como o [GitHub Pages](https://help.github.com/articles/using-jekyll-with-pages/) sugerem que você sincronize sua instalação local do Jekyll com aquela usada pelo GitHub. Isso evita que você tenha surpresas com diferenças entre o site rodado na máquina e o gerado pelo GitHub. 

Note que, para isso, agora você vai passar a  precisar de __acesso à internet__ mesmo para rodar o site localmente, mas é por uma boa causa.

É fácil:

1) Instale o [Bundler](http://bundler.io/).
    
<pre><code class="language-bash">gem install bundler</code></pre>

2) Crie um arquivo com o nome <code class="language-bash">Gemfile</code> (sem extensão) na pasta do seu site com o seguinte conteúdo:

<pre><code class="language-bash">source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']</code></pre>

<div class="caixa-esq">
<p><span class="info"><i class="fa fa-info-circle fa-lg"></i></span> Caso não funcione, tente apenas com:</p>

<pre><code class="language-bash">source 'https://rubygems.org'
gem 'github-pages'</code></pre>
</div>

3) Navegue até a pasta e rode:

<pre><code class="language-bash">bundle install</code></pre>

__Pronto__.

A partir de agora, você precisa adicionar <code class="language-bash">bundle exec</code> antes de todos os comandos jekyll. Por exemplo:

<pre><code class="language-bash">bundle exec jekyll build
bundle exec jekyll serve --watch</code></pre>

Lembre-se de atualizar com <code class="language-bash">bundle update</code> frequentemente e você será feliz e próspero(a).

# .gitignore (_site)
# 404.md
# Readme.md

# Domínio Custom


Meus:
# páginas categorias?

# diqus
# Awesome font
# Prism.js 
# Reveal.js
# Estilo: não usa preto, cara. fonte bacana, aqueles links.

Rápido:
# sitemap.xml

<div class="caixad">
{% include ads/gads-resp.html %}
</div>