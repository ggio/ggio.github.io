---
layout: postad-gads
categories: blog
title:  "Forçando sua carroça velha a rodar aquele jogo de última geração"
date: 2015-12-04
description: Com o avanço tecnológico, nossas máquinas se tornam obsoletas cada vez mais rápido. Nem sempre dá acompanhar essa corrida, mas sempre dá pra tentar uma gambiarra.
comments: true
logoface-blog: true
---

<p class="intro">Essa tal de obsolescência programada é foda. Ano após ano, os gráficos e efeitos especiais ficam cada vez melhores, mais nítidos e "realistas", muitas vezes sem uma melhora equivalente do enredo e da jogabilidade. Parece que a pretensão é fornecer a experiência mais próxima possível de uma realidade digital ("Uau, parece de verdade!"). Mera pornografia industrial acompanhada de uma mitologia meio bobinha do avanço tecnológico.</p>

Sendo assim, e sabendo que há todo um universo de __jogos alternativos__ que subvertem essa lógica rasteira e permitem outras experiências com jogos, eu lá perderia meu tempo e dinheiro tentando participar dessa verdadeira corrida armamentista para tentar rodar um jogo de última geração? __Mas é claro que sim!__ O post trata exatamente dessa busca.

Há uns 5 anos atrás, montei um __PC razoável__ para jogos. Não era nooossa, mas, poxa, rodava até bem qualquer jogo da época. Meia-década depois, os últimos lançamentos se recusam sequer a inicializar no que julgam ser uma carroça tão indigna. 

Mais especificamente, eu estava interessado em dois jogos: __Fallout 4__ e __Witcher 3__. Eu fui dito mais que explicitamente que meu PC não estava a altura da tarefa, mas __não podia deixar de dar aquela forçada__.

O problema não foi instalar, mas sim rodar os jogos. O Fallout 4 quebrava automaticamente, o Witcher 3 ignorava meus apelos e fingia que não tinha nada acontecendo.

<figure>
    <img src="{{ '/assets/aux/carroca/error.jpg' | prepend: site.baseurl }}" alt="Erro no lançamento do Fallout 4" style="width: 40%; height: 40%"> 
    <figcaption>Error!</figcaption>
</figure>

Minha configuração é a seguinte:

* AMD Phenom X3 2.8 ghz
* 4 gb de RAM
* Placa de vídeo: GTS 250
* Windows 7 64 bits

Migrar para o __Windows 10__ poderia ser um primeiro passo para preparar a máquina para esses jogos, mas por motivos de ainda preservar alguma dignidade e privacidade, eu me recuso a instalar a distribuição. Provavelmente o tempo me fará dar o braço a torcer, mas por enquanto vamos com o que temos. O __Windows 8__ seria uma opção, mas aí contou a preguiça mesmo.

O passo a passo que eu descrevo a seguir acompanha a instruções deste [vídeo russo](https://www.youtube.com/watch?v=efaqAwNS5lU). É claro que eu não entendo lhufas de russo, mas a tradução automática das legendas ajudou.

<span class="amarelo"><i class="fa fa-exclamation-triangle fa-lg"></i></span> Um aviso: mesmo que você consiga iniciar o jogo, __não há garantia alguma de que ele seja minimamente jogável__ em seu PC! Mas isso não nos fará deixar de tentar, não é mesmo?

## Instalando o SDK

Para convencer nosso PC de que ele pode pelo menos tentar rodar os jogos, vamos precisar do [Software Development Kit (SDK) do Windows 8](https://msdn.microsoft.com/pt-br/windows/desktop/hh852363.aspx). "Ah, mas você disse que usa o Windows 7"! Sim, mas por alguma bruxaria o SDK do Windows 8 não vê problema nenhum em ser instalado no 7.

<figure>
    <img src="{{ '/assets/aux/carroca/sdk.jpg' | prepend: site.baseurl }}" alt="Octogato - GitHub + Jekyll" style="width: 60%; height: 60%"> 
    <figcaption>A instalação te dá mil opções, você só precisa da primeira.</figcaption>
</figure>

Aguarde o término da interminável instalação e reinicie o PC.

## Nosso amiguinho dxcpl.exe 

Vá na ferramenta de busca do Windows e procure por <code class="language-bash">dxcpl</code>. Deve ser o primeiro resultado. 

Primeiro, vamos escolher os executáveis que queremos dar aquela forçada.

<figure>
    <img src="{{ '/assets/aux/carroca/list.jpg' | prepend: site.baseurl }}" alt="Edit list em dxcpl.exe" style="width: 40%; height: 40%"> 
    <figcaption>Informe ali o caminho dos executáveis dos jogos (os .exe principais, e não os launchers!).</figcaption>
</figure>

Por exemplo, indique o <code class="language-bash">Fallout4.exe</code> e __não__ o <code class="language-bash">Fallout4Launcher.exe</code>. 

Agora vamos estabelecer limites para o lançamento dos executáveis que selecionamos. Tente primeiro com o __directX 11_1__, como na imagem a seguir: 

<figure>
    <img src="{{ '/assets/aux/carroca/11-1.jpg' | prepend: site.baseurl }}" alt="Feature level limit: 11_1 | dxcpl.exe" style="width: 40%; height: 40%"> 
    <figcaption>Ali.</figcaption>
</figure>

Pronto. Já pode tentar executar o jogo. Caso não funcione, abaixe ainda mais o limite:

<figure>
    <img src="{{ '/assets/aux/carroca/11-0.jpg' | prepend: site.baseurl }}" alt="Edit list em dxcpl.exe" style="width: 40%; height: 40%"> 
    <figcaption>De novo.</figcaption>
</figure>

Você também pode tentar antes sem a opção <code class="language-bash">Force WARP</code>, mas provavelmente vai precisar dela.

Pronto, tente de novo rodar o jogo.

Funciona? Ainda não? Uma última configuração e com sorte agora vai:

## Modo de compatibilidade

Vá até as propriedades dos executáveis (agora sim, de ambos os .exe principais e launchers) e ative o modo de compatibilidade de acordo. 

<figure>
    <img src="{{ '/assets/aux/carroca/propriedades.jpg' | prepend: site.baseurl }}" alt="Edit list em dxcpl.exe" style="width: 40%; height: 40%"> 
    <figcaption>Assim.</figcaption>
</figure>

<figure>
    <img src="{{ '/assets/aux/carroca/compatibilidade.jpg' | prepend: site.baseurl }}" alt="Edit list em dxcpl.exe" style="width: 40%; height: 40%"> 
    <figcaption>Bem ali.</figcaption>
</figure>

Faça o mesmo com o <code class="language-bash">Fallout4.exe</code> ou o executável do jogo em questão. Você pode começar com a compatibilidade para o Windows 8 e reduzir para o 7 caso não funcione (mesmo que não seja essa sua distribuição).

## Sucesso!

Se você fez tudo certo e a posição dos planetas está a seu favor, você já deve ter conseguido iniciar seu objeto de desejo!

No meu caso, eis a prova para ambos os jogos:

<figure>
    <img src="{{ '/assets/aux/carroca/fallout4.jpg' | prepend: site.baseurl }}" alt="Fallout 4 início" style="width: 40%; height: 40%"> 
    <figcaption>Fallout 4</figcaption>
</figure>

<figure>
    <img src="{{ '/assets/aux/carroca/witcher3.jpg' | prepend: site.baseurl }}" alt="Witcher 3 início" style="width: 40%; height: 40%"> 
    <figcaption>Witcher 3</figcaption>
</figure>

__Maravilhoso, não é mesmo?__ E disseram que era impossível! Aproveite para tentar ver o vídeo introdutório antes de assistir ao peso do jogo lentamente fritar o seu PC até travar tudo por completo. Bem, pelo menos foi o que aconteceu comigo.

<center>
<video autoplay="" loop="" muted="">
<source src="http://webmbassy.com/v/star-wars-terminator-2-mash-up-its-working-anakin-skywalker-14098428930.webm" type="video/webm" alt=" It's working! Só que não.">
</video>
</center>

Se você, como eu, não teve muita sorte, apenas dizer que sinto muito. Quer dizer que nossa empreitada foi inútil? Talvez, mas pelo menos tentamos bravamente. O que aprendemos com isso? Praticamente nada.

<div class="caixad">
{% include ads/gads-resp.html %}
</div>