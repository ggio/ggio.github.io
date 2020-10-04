---
title:  "Planilhas de controle de cadastros e atendimentos em política pública (Centro POP)"
date: 2020-10-03
description: ""
---

Em minha passagem como servidor público na política de assistência social em Conselheiro Lafaiete (MG), fiz parte da equipe do Centro de Referência Especializado para População em Situação de Rua (__Centro Pop__) entre 2017 e 2019. Talvez lá tenha tido meu primeiro e mais intenso contato com a clínica ampliada. Escutar e acolher pessoas em situação de rua é sem dúvida muito desafiador, requer uma séria crítica das ideias preconceituosas que trazemos do cotidiano e da formação e por isso mesmo permite um aprendizado importante através da prática profissional. Apesar dos pesares de trabalhar em serviço público em um período de acelerado sucateamento, sinto saudades da rotina de trabalho e do contato com o público.

Gosto de pensar que através dos atendimentos individuais e em grupo, discussões de caso e reuniões de equipe contribuí em qualificar e repensar a escuta ao público-alvo, nossos objetivos e os métodos de trabalho. Mas tenho certeza também que se perguntassem aos e às colegas qual foi minha principal contribuição ao setor, responderiam sem pestanejar: a criação da __planilha unificada do setor__. É sobre isso que trata esta postagem.

Uma vez empregada, a planilha permitiu a __simplificação dos processos__ de registro, a __unificação de documentos__ físicos e digitais e a __redução do tempo__ gasto pelo usuário em cumprir com as inevitáveis formalidades do serviço. Uma vez que todos os dados estavam no excel, foi possível também a __automatização__ do preenchimento e análise de informações. Com isso, conseguimos gerar automaticamente também o __relatório mensal__ do serviço, uma histórica penúria da coordenação e equipe nas políticas públicas. É possível que esta seja a principal vantagem do emprego da ferramenta, mas só foi possível uma vez que todo o trajeto foi percorrido.

O texto a seguir se organiza em grau crescente de complexidade, de forma a responder primeiro o interesse de servidores interessados em empregar a planilha, ainda que não tenham maiores conhecimentos ou interesse nos mistérios do Excel, e em seguida passo a relatar minhas escolhas técnicas na construção da planilha, algumas gambiarras e possíveis formas de melhorar o conjunto da obra. 

--- 

## Download da planilha e Manual

Sem mais delongas, disponibilizo abaixo os links para __download da planilha__ e do __manual__ que elaborei quando saí do setor. Nesse manual, há um passo a passo detalhado de uso e manutenção da planilha, aspectos práticos que podem ajudar quem tem dificuldade com o Excel e que por economia e espaço não vou tratar durante a postagem. O Manual trata de uma versão ligeiramente diferente da que disponibilizo aqui, mas serve bem ao propósito mesmo assim.

Incluí na planilha __alguns dados a título de exemplo__, para que você possa testar seu funcionamento e ver se atende aos seus objetivos. Para começar a usá-la, basta deletar essas informações e começar do zero. Recomendo acompanhar o texto com o Excel aberto para consulta.

<a href="{{ site.url }}/anexos/Planilha_de_controle.xlsm" class="pa3 tc ba br3 db"> Planilha de controle</a>

<a href="{{ site.url }}/anexos/Manual_planilha.pdf" class="pa3 tc ba br3 db">Manual de uso e manutenção</a>

A __senha para (des)proteger__ todas as abas é <mark>123</mark>. Minha recomendação é que tudo fique constantemente protegido, de forma a evitar que alguém apague as fórmulas por descuido. Caso queira mudar a senha, fique à vontade, mas não deixe de consultar antes o último tópico desse texto ("Fórmulas e VBA") e veja que isso pode ser mais difícil do que parece (mas, ainda sim, factível).

A planilha e o manual são disponibilizados com uma [Licença Creative Commons - Atribuição 3.0 Brasil](https://creativecommons.org/licenses/by/3.0/br/). Isso significa que você pode usar, adaptar e compartilhar o código à vontade. Nesses casos, mencionar a autoria do projeto inicial seria bacana.

--- 

## O processo de construção

Basicamente, ao começar a trabalhar no setor e ser introduzido às ferramentas físicas e digitais de trabalho e registro de informação, reparei que existiam uma série de __redundâncias__, quer dizer, que algumas informações eram registradas em dois, três, quatro lugares diferentes. Além de gerar __trabalho desnecessário__ para a equipe (eu inclusive), o tarefismo acabava por nos tirar __tempo e energia__ que poderia ser melhor empregado no atendimento ao público ou planejamento das ações. Os próprios usuários, muitos analfabetos ou com escolarização precária, veja só, precisavam __assinar de duas a cinco vezes__ (!) o próprio nome, gerando justificada impaciência e frustração. 

Com a concordância e apoio da coordenação (a Aline Gonzaga é um anjo na terra, que fique registrado desde já), comecei o processo de revissão dessas ferramentas com o apoio, críticas e sugestões dos veteranos no serviço (agradeço aos colegas Daniel Matos, Danusa Azevedo, Ediney Martins, Roseli Rita e Grace Kelly).

Cabe reconhecer, é claro, que foi o __registro dessas informações pela equipe desde a abertura__ do setor em 2014 que permitiu que tenhamos ainda hoje essas informações. Alguns dos primeiros usuários cadastrados ainda vivem na cidade e frequentam o setor. Já os registros de passagens contribuem com a compreensão dos movimentos migratórios de usuários que ainda retornam ao setor em busca dos serviços de acolhimento ou de novas passagens.

O resultado geral foi a __unificação de três documentos__ digitais (ver imagem abaixo) em apenas um arquivo Excel (daí o apelido carinhoso "planilha unificada"). Registrar de forma mais consistente as informações dos usuários e atendimentos realizados permitiu também __eliminar alguns formulários em papel__, para a alegria de 100% dos frequentadores do Centro POP: usuários e equipe técnica.

![Diagrama da unificação de arquivos](/images/postagens/planilha/unificacao.png)

--- 
## A "planilha unificada"

A maior parte dos dados registrados no documento dizem respeito às informações que o setor precisa prestar através do “__Relatório mensal de atendimentos do Centro POP__” ao governo federal. O preenchimento do relatório é discutido e descrito em detalhes no documento “[Centro POP – Manual de instruções para o registro das informações especificadas na resolução nº04/2011](https://aplicacoes.mds.gov.br/sagi/atendimento/doc/Manual_de_Instrucoes_CENTRO_POP.pdf)”, publicado pelo então Ministério do Desenvolvimento Social e Combate à Fome em 2014.

O documento é composto por __seis abas__ (ou "planilhas", caso você queira usar o termo preciso), apresentadas a seguir. Todos os nomes e informações nas tabelas são fictícios. 

<div class="pa3 tl ba br3 db b--light-silver bg-near-white">
<p><span class="info"><i class="fa fa-info-circle fa-1x"></i></span>
<b>Obs.</b>: há certa ambiguidade no uso da palavra “planilha” ao longo dessa postagem e no manual. Tecnicamente, “planilha” refere-se a cada “folha” ou "aba" do documento Excel. São as páginas que compõe o documento. Já o nome do documento “planilha unificada” é informal e refere-se à unificação de diferentes planilhas em um mesmo documento.</p>
</div>

### 1. Cadastro

Trata-se do registro de informações básicas que serão usadas para o funcionamento das demais abas. Ao escolher uma linha para cadastro de um(a) usuário(a), este será atrelado a um __número de identificação__ (“__ID__”, vide primeira coluna), útil tanto para o conhecimento do total de cadastros realizados no setor quanto para o preenchimento simplificado de dados nas outras abas. Para um detalhamento sobre cada coluna, consulte o manual. Aumente o zoom para ver detalhes na imagem.

![Ficha de cadastro](/images/postagens/planilha/Cadastro.PNG)

### 2. Passagens

Registro de concessão de passagens no setor. Caso não seja útil em seu caso, basta não usá-la e quem sabe deletar a aba (lembrando de salvar um _backup_ antes por segurança).

Para o __registro de novas passagens__, basta informar o __número da ID__ do usuário e a planilha irá preencher automaticamente o respectivo nome e documento. 

![Ficha de Passagens](/images/postagens/planilha/Passagens.PNG)

### 3. Frequência CP

Registro de frequência dos usuários no setor. A partir do __nome completo do usuário__, a planilha irá identificar sua ID e só então registrar o usuário no relatório do mês informado. Escolhemos preencher o nome ao invés da ID por julgar que seria mais simples registrar as informações direto do __caderno de frequência__ que os usuários assinam na recepção, mas o método traz algumas dificuldades. Principalmente, requer que o nome informado seja exatamente o mesmo registrado na planilha de cadastro, com atenção até mesmo em acentos e espaços em branco (às vezes difíceis de perceber). Essas são algumas dificuldades em utilizar o Excel como banco de dados.

![Ficha de Frequência](/images/postagens/planilha/Frequencia.PNG)

### 4. Abordagens

Como o setor de Abordagem Social no município funcionava conjuntamente com o Centro POP, optamos por registrar no mesmo arquivo essas informações. A escolha permitiu uma maior interlocução entre as equipes. Fazer isso implicou também em manter unificados os dados de cadastro (que, afinal, servem para ambos os serviços). A aba tem a mesma função da de frequência, com a diferença de que o relatório de que é preciso informar os casos de __trabalho infantil__ e __exploração sexual de crianças e adolescentes__.

![Ficha de abordagens](/images/postagens/planilha/Abordagens.PNG)

### 5. Consulta Usuário

Ferramenta de consulta que procura __reunir todas as informações__ registradas sobre o usuário nas diferentes planilhas: informações cadastrais, frequência no setor e passagens concedidas. Esta planilha está configurada como relatório pronto para impressão, basta clicar em: <mark>Arquivo > Salvar como > Tipo de arquivo > PDF</mark>. Esse __relatório automático individual__ pode ser útil como anexo em discussões de caso e relatórios à justiça e outros setores. Para usá-lo, lembre-se de atualizar a logomarca do setor (se quiser), o endereço e meios de contato.

![Gráficos úteis](/images/postagens/planilha/Consulta.png)

### 6. Relatório Mensal

Por fim, o __relatório mensal gerado automaticamente__ a partir das informações lançadas nas outras abas. Para gerar as informações, basta __escolher o mês e ano__ correspondente, na primeira linha do relatório. 

__Exemplo__:

![Exemplo de relatório](/images/postagens/planilha/Relatorio.png)

Além das informações objetivas exigidas pelo governo federal, percebi que poderia gerar também alguns __gráficos e informações úteis__. 

Na imagem abaixo você pode perceber que a planilha identifica de forma automática __erros no preenchimento do cadastro__. Mais que mera obsessão pela correção dos dados, pequenos deslizes podem significar uma subnotificação dos casos. 

O gráfico em barra em seguida permitem conhecer a __distribuição da frequência no mês pelos usuários__. Com isso, podemos diferenciar os usuários que passam rapidamente pelo setor (algo comum entre os migrantes) e aqueles mais assíduos. Identificar esses usuários permite traçar melhores planos de atendimento e trabalho, visto que aumenta-se a possibilidade de construção de vínculo.

Incluí também um gráfico simples de pizza mostrando a __porcentagem de usuários vinculados à cidade__ (identificados como "Centro POP") e __migrantes__.

![Gráficos úteis](/images/postagens/planilha/Relatoriob.PNG)

Por fim, um dos gráficos que acho mais úteis, o __histórico total de frequência no setor__. Para tentar demonstrar sua utilidade, preferi usar o próprio gráfico do Centro POP de Lafaiete em dezembro de 2019. Percebe-se na imagem uma tendência de alta no mês de Julho e relativa baixa até o final do ano. Acredito que os dados de Janeiro a Maio não sejam tão conclusivos, caberia voltar a analisar daqui há alguns anos.

Para interpretar o gráfico, considere que os anos de __2018 e 2019 foram atípicos__. Em 2018, o setor passou por uma série de furtos e depredações que levaram a uma diminuição dos atendimentos prestados a partir de meados de Abril e Maio até a completa suspensão dos atendimentos em Novembro. Como se nota, o setor só voltou a funcionar propriamente em Julho de 2019. Ainda que tais solavancos tenham frustrado a intenção inicial de identificar os meses com maior e menor demanda, além de sua flutuação ao longo dos anos, o registro dessas informações permitiu uma análise quantitativa do prejuízo causado à população no período.

![Histórico do setor](/images/postagens/planilha/Historico.PNG)

### Considerações sobre o uso do Excel

Espero ter evidenciado a utilidade da planilha. Há entretanto, alguns __problemas decorrentes de utilizar o Excel como banco de dados__. Principalmente, por algum motivo misterioso que foge à capacidade de compreensão humana (a minha, no caso), as fórmulas, formatação do arquivo e configuração de intervalos protegidos (para que não se alterem as fórmulas por descuido) __insistem em parar de funcionar de tempos em tempos__. 

Para contornar o problema, quando inevitavelmente o frágil equilíbrio de dados e fórmulas for quebrado, recomenda-se contar com versões anteriores onde tudo ainda funcione, conforme descrito na seção __“_backup_ mensal”__ do manual.

Leve em consideração também que o documento foi construído na unha por um psicólogo repleto de boas vontades, mas com conhecimento _amador_ em tecnologias digitais, pra dizer o mínimo. O ideal era poder contar com __um banco de dados propriamente dito__, construído com ferramentas e por pessoas adequadas. Quem sabe compartilhando essas soluções provisórias alguém(ns) não se anima(m) a construir uma ferramenta completa para esses serviços.

--- 
## Fórmulas e VBA

Finalmente, cabe alguma palavra sobre as fórmulas e _scripts_ utilizados, para quem tiver interesse. 

A maior parte das fórmulas é bem simples na verdade, com uso abusivo do <mark>PROCV</mark>. Exceção é o uso do <mark>ÍNDICE</mark> e das __funções matriciais__. Quando vejo a função abaixo (usada na aba de Consulta), por exemplo, eu juro que não sei por onde começar a entendê-la (e sim, fui eu que escrevi). 

``` shell
{=SEERRO(ÍNDICE(Tabela.frequencia[];MENOR(SE(Tabela.frequencia[id]=$E$11;LINHA(Tabela.frequencia[id])-1);LINHA(A1));3);DATA(1990;1;1))}
```
Minha intenção inicial era detalhar também a construção desse emaranhado de fórmulas mas confesso que estou cansado e já faz tanto tempo que fiz a planilha que teria que basicamente aprender de novo, mas cabem alguns __comentários gerais__.

Algumas informações precisaram de  __mais de uma etapa para serem consolidadas__. O preenchimento automático do relatório, por exemplo, requereu (palavra horrorosa):

1. buscar com o <mark>ÍNDICE</mark> as pessoas atendidas no mês, 
2. o uso de __tabelas dinâmicas__ para suprimir as repetições,
3. como, por padrão, o Excel acha uma boa ideia que essas tabelas precisem ser atualizadas __MANUALMENTE__, tive que recorrer ao ___Visual Basic_ (VBA)__ para atualizá-las toda vez que alguma informação fosse alterada ou a planilha fosse selecionada. 

Esses _scraps_ e sínteses preliminares foram montados em geral nas linhas mais abaixo nessas planilhas. Originalmente, deixei todas as fontes brancas, para que essa gambiarra fique invisível. Recomendo deixar assim para não assustar o usuário final. Tenho certeza que alguém mais capacitado organizaria de forma mais limpa esses dados, mas o importante para mim é que o resultado final funcionou.


### VBA

Pra finalizar, deixo abaixo os _scripts_ do _Visual Basic_ usados em cada planilha. A principal utilidade, caso queira ou precise, é saber onde trocar a senha nas planilhas de consulta e relatório mensal. Para isso, basta substituir todas as entradas <mark>"123"</mark> abaixo pela nova senha. 

Para abrir o VBA no Excel, use o atalho <mark>Alt+F11</mark>, mas se você precisa dessa dica provavelmente irá pesquisar um pouco mais sobre ele.

* __Plan5 (Consulta Usuário)__

    ``` vb
    Private Sub Worksheet_Change(ByVal Target As Range)
    If Intersect(Target, Me.Range("E11")) Is Nothing Then Exit Sub
        ActiveSheet.Unprotect "123"
        Run "PT_Refresh"
        ActiveSheet.Protect "123"
    End Sub
    ```

* __Plan6 (Relatório Mensal)__

    ``` vb
    Private Sub Worksheet_Change(ByVal Target As Range)
        If Intersect(Target, Me.Range("I2")) Is Nothing Then Exit Sub
            ActiveSheet.Unprotect "123"
            Run "RM_Refresh"
            ActiveSheet.Protect "123"
    End Sub

    Private Sub Worksheet_Activate()
        'Sheets("Plan6").PivotTables("ids_unicas").RefreshTable
        ActiveSheet.Unprotect "123"
        Run "RM_Refresh"
        ActiveSheet.Protect "123"
    End Sub
    ```

* __Módulos__:
    - __Módulo 1__
    
    ``` vb
    Sub PT_Refresh()
    Dim pt As PivotTable
    Set pt = ActiveSheet.PivotTables("Tabela.din.consulta")
    pt.RefreshTable
    End Sub
    ```

    - __Módulo 2__

    ``` vb
    Sub RM_Refresh()
    Dim rm As PivotTable
    Set rm = ActiveSheet.PivotTables("ids_unicas")
    rm.RefreshTable
    
    Dim ab As PivotTable
    Set ab = ActiveSheet.PivotTables("ids_unicas_ab")
    ab.RefreshTable
    
    Dim dh As PivotTable
    Set dh = ActiveSheet.PivotTables("dados.hist")
    dh.RefreshTable
    
    End Sub
    ```



