---
title: Criação e Visualização de Ficheiros HTML com Python
layout: lesson
slug: criacao-visualizacao-ficheiros-html-python
date: 2012-07-17
translation_date: 2022-10-31
authors:
- William J. Turkel
- Adam Crymble
reviewers:
- Jim Clifford
editors:
- Miriam Posner
translator: 
- Felipe Lamarca
translation-editor:
- Jimmy Medeiros
translation-reviewer:
- Gabriela Kucuruza
- Ana Carolina Erthal
difficulty: 2
review-ticket: https://github.com/programminghistorian/ph-submissions/issues/462
activity: presenting
topics: [python, website]
abstract: "Com esta lição aprenderá a criar ficheiros HTML com scripts Python e a usar o Python para abrir automaticamente um ficheiro HTML no Firefox."
original: creating-and-viewing-html-files-with-python
avatar_alt: Criança desenhando numa tábua
doi: A INDICAR
---

{% include toc.html %}

## Objetivos da Lição

Esta lição usa o Python para criar e visualizar um ficheiro HTML. Se você escrever programas que produzem HTML, você pode utilizar qualquer navegador para ver seus resultados. Isso é especialmente conveniente se o seu programa cria automaticamente hiperlinks ou entidades gráficas, como gráficos e diagramas.

Aqui você irá aprender como criar ficheiros HTML com scripts Python e como utilizar o Python para abrir um ficheiro HTML automaticamente no Firefox.

## Ficheiros Necessários para esta Lição

- `obo.py`

Caso não possua esses ficheiros da lição anterior, você pode fazer o *download* do programming-historian-5, um [ficheiro zip da lição anterior](/assets/python-lessons5.zip).

## Criando HTML com Python

Até aqui, começamos a aprender como usar o Python para fazer o *download* de fontes *online* e extrair informação delas de forma automática. Lembre-se de que nosso objetivo final é incorporar perfeitamente a programação em nossa prática de investigação. Em linha com este objetivo, nesta lição e na próxima aprenderemos como apresentar dados de volta à forma de HTML. Isso possui algumas vantagens. Primeiro, ao armazenar a informação no nosso disco rígido como um ficheiro HTML, podemos abri-lo com o Firefox e usar o [Zotero](https://www.zotero.org/) para indexar e fazer anotações posteriormente. Segundo, há uma ampla gama de opções de visualização para HTML que podemos usar mais tarde.

Caso ainda não tenha feito o [tutorial de HTML do W3 Schools](http://www.w3schools.com/html/default.asp), reserve alguns minutos para fazê-lo antes de continuar. Criaremos um documento HTML usando Python, então você precisará saber o que é um documento HTML!

## "*Hello World*" em HTML usando Python

Uma das ideias mais poderosas na ciência da computação é que um ficheiro que parece conter código sob uma perspectiva pode ser visto como dado sob outra. É possível, em outras palavras, escrever programas que manipulam outros programas. O que faremos a seguir é criar um ficheiro HTML que diz "*Hello World*" usando Python. Faremos isso armazenando *tags* HTML em uma string multilinha de Python e salvando os conteúdos em um novo ficheiro. Esse ficheiro será armazenado com uma extensão `.html` ao invés de uma extensão `.txt`.

Tipicamente um ficheiro HTML começa com uma [declaração do tipo de documento](http://www.w3schools.com/tags/tag_doctype.asp). Você viu isso quando escreveu um programa HTML "*Hello World*" em uma lição anterior. Para facilitar a leitura do nosso código, omitiremos o `doctype` neste exemplo. Lembre-se de que uma string multilinha é criada colocando o texto entre três aspas (veja abaixo):

``` python
# write-html.py

f = open('helloworld.html','w')

message = """<html>
<head></head>
<body><p>Hello World!</p></body>
</html>"""

f.write(message)
f.close()
```

Salve o programa acima como `write-html.py` e execute-o. Use `Ficheiro -> Abrir` (ou `Arquivo -> Abrir`, na versão brasileira) no editor de texto de sua escolha para abrir `helloworld.html` para verificar que seu programa de fato criou o ficheiro. O conteúdo deve se parecer com isto:

{% include figure.html filename="hello-world-html.png" caption="Fonte HTML gerada pelo programa Python" %}

Agora vá para o seu navegador Firefox e escolha `Ficheiro -> Nova Guia` (ou `Arquivo -> Nova aba`, na versão brasileira) , vá para a guia e escolha `Ficheiro -> Abrir Ficheiro` (ou `Arquivo -> Abrir arquivo`, na versão brasileira). Selecione `helloworld.html`. Você deve agora ser capaz de ver sua mensagem no navegador. Reserve um momento para pensar sobre isso: agora você tem a habilidade de escrever um programa que pode criar uma página web automaticamente. Não há razão pela qual você não possa escrever um programa para criar automaticamente um *site* inteiro, caso deseje.

<div class="alert alert-warning">
  Por questões de versionamento, é possível que seu navegador Firefox não possua a opção de abrir um ficheiro manualmente na guia. Nesse caso, procure pelo ficheiro HTML no seu diretório, clique nele com o botão direito e selecione a opção de abri-lo com o navegador Firefox. 
</div>

## Usando o Python para Controlar o Firefox

Nós criamos um ficheiro HTML automaticamente, mas depois precisamos deixar nosso editor, ir para o Firefox e abrir o ficheiro em uma nova guia. Não seria mais legal incluir essa etapa final no nosso programa Python? Digite ou copie o código abaixo e armazene-o como `write-html-2.py`. Quando executá-lo, ele deve criar seu ficheiro HTML e depois abri-lo automaticamente numa nova guia do Firefox. Maravilha!

### Instruções para Mac

Usuários de Mac precisarão especificar a localização precisa do ficheiro `.html` nos seus computadores. Para fazer isso, localize a pasta `programming-historian` que você criou para fazer esses tutoriais, clique com o botão direito nela e selecione "Obter Informações" (ou "*Get Info*").

Você pode então recortar e colar a localização do ficheiro listado depois de "Onde:" (ou "*Where:*") e se certificar de incluir uma barra final (/) para que o computador saiba que você deseja algo dentro desse diretório (e não o diretório em si).


``` python
# write-html-2-mac.py
import webbrowser

f = open('helloworld.html','w')

message = """<html>
<head></head>
<body><p>Hello World!</p></body>
</html>"""

f.write(message)
f.close()

#Altere o caminho para refletir a localização do ficheiro
filename = 'file:///Users/username/Desktop/programming-historian/' + 'helloworld.html'
webbrowser.open_new_tab(filename)
```

Caso você receba um erro "Ficheiro não encontrado" (ou "*File not found*"), você não mudou o caminho para o ficheiro corretamente.

### Instruções para Windows

``` python
# write-html-2-windows.py

import webbrowser

f = open('helloworld.html','w')

message = """<html>
<head></head>
<body><p>Hello World!</p></body>
</html>"""

f.write(message)
f.close()

webbrowser.open_new_tab('helloworld.html')
```

\*\*\*

Você não só escreveu um programa Python que pode escrever um HTML simples, mas também controlou seu navegador Firefox utilizando Python. Na próxima lição, focaremos em apresentar os dados que coletamos na forma de um ficheiro HTML.

## Leituras Sugeridas

-   Lutz, Learning Python
    -   Re-read and review Chs. 1-17

## Sincronização de Código

Para acompanhar lições futuras, é importante ter os ficheiros e programas corretos no seu diretório “programming-historian”. No final de cada lição, é possível fazer o *download* do ficheiro zip “programming-historian” para garantir que possui o código correto. Caso esteja acompanhando com a versão para Mac / Linux, você deve ter que abrir o ficheiro `obo.py` e mudar "file:///Users/username/Desktop/programming-historian/" para o caminho até o diretório no seu próprio computador.

-   [python-lessons6.zip](/assets/python-lessons6.zip)
