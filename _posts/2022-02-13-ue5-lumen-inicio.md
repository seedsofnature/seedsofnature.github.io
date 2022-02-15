---
title: Criando um bunker subterranêo e iluminando usando Lumen da UE5
layout: post
author: sal
categories: []
image: assets/images/8.png

---
Olá, esse é o primeiro post aqui do devblog, meu nome é Kelvin Rosa ('frost'), sou o desenvolvedor por trás da Lightshaft, nesse Blog irei falar do jogo no qual passei anos fazendo protótipos, parando, repensando e começando de novo.

O foco do blog é mostrar o andamento do jogo, as tecnologias aplicadas, talvez uns tutoriais.

Seeds of Nature esta em desenvolvimento na minha cabeça a mais de 8 anos, é um jogo complexo com mecânicas de sobrevivência, simulação, fazenda e muito mais. Baseado no objetivo final do jogo o processo é bem complicado para um exercito de um homem só, meu foco principal (a área que eu domino) é programação, não sou bom com desenhos, até sei modelar em 3D, animar, fazer design de levels, mas para acelerar o desenvolvimento do jogo e finalizar uma demo para mostrar a ideia principal do jogo, eu compro modelos 3D prontos que se encaixariam com o resultado que desejo, meu jogo se chama Seeds of Nature, sigla SON (que inglês quer dizer filho, Meu filho >.<).

Eu até gostaria de ter alguém a bordo que pudesse cuidar da parte 3D, mas meu orçamento para contratar alguém é $0, 100% do dinheiro investido no jogo atualmente foi tirado dos meus fundos. Coloquei este projeto no <a href="https://www.patreon.com/lightshaft">Patreon</a> exatamente para tentar arrecadar fundos para acelerar o desenvolvimento do jogo. Nesse blog vou falar sobre o processo de desenvolvimento, criar alguns tutoriais e talvez postar algo a respeito de meus pets de espécies incomuns que estarão presente no jogo, vamos ao que interessa, nesse primeiro post irei falar sobre o processo de iluminação do jogo.

## O Bunker

Atualmente o jogo possui muitas mecânicas prontas, irei falar sobre algumas delas em posts futuros, a iluminação era algo que eu não estava nem ligando até remodelar a história do jogo e perceber que seria algo essencial. Como qualquer bom jogo de sobrevivência e fazenda ter um ciclo de dia e noite é essencial, agora imagina se você necessita de ambientes escuros no seu jogo como por exemplo um bunker subterrâneo!

A parte inicial do jogo vai ser focada em um bunker, será o lugar onde você iniciará sua jornada, não posso falar muito sobre a narrativa ainda, mas sua aventura/vida ira iniciar dentro de um bunker que está ficando sem recursos básicos, suplementos, você está trancado lá dentro fazem 3 anos, não sabe o que aconteceu com a superfície nesses anos que se passaram. O sistema de energia está começando a apresentar falhas, você tem apenas 2 semanas de comida garantida. Não resta outra opção a não ser ir para a superficie.

O bunker está equipado com vários equipamentos sobrevivencialistas, livros, receitas, ou seja você tem uma breve preparação para sobreviver lá fora caso necessário.

Como se trata de um bunker eu quis fazer dele um local que não recebe luz externa, como o jogo possui um sistema de iluminação dinâmica, ciclo de dia e noite, estações, climas diferentess, necessitei usar uma skylight (luz emitida pelo céu ou material de céu), isso faz com que todo o mundo do jogo seja iluminado inclusive partes subterrâneas isso fez com que o bunker ficasse iluminado em seu interior, não é o resultado que eu esperava. Deixando apenas uma luz direcional funciona já que a iluminação não é global, mas o ambiente externo fica muito escuro, e sem realismo nos climas.

![ee](/assets/images/7.png "No interior é possível ver uma luz constante, proveniente do skylight, mesmo com as sombras corretas.")

## Writing code blocks

There are two types of code elements which can be inserted in Markdown, the first is inline, and the other is block. Inline code is formatted by wrapping any word or words in back-ticks, `like this`. Larger snippets of code can be displayed across multiple lines using triple back ticks:

    .my-link {
        text-decoration: underline;
    }

If you want to get really fancy, you can even add syntax highlighting using Rouge.

![walking]({{ site.baseurl }}/assets/images/3.jpg)

## Reference lists

The quick brown jumped over the lazy.

Another way to insert links in markdown is using reference lists. You might want to use this style of linking to cite reference material in a Wikipedia-style. All of the links are listed at the end of the document, so you can maintain full separation between content and its source or reference.

## Full HTML

Perhaps the best part of Markdown is that you're never limited to just Markdown. You can write HTML directly in the Markdown editor and it will just work as HTML usually does. No limits! Here's a standard YouTube embed code as an example:

<p><iframe style="width:100%;" height="315" src="https://www.youtube.com/embed/Cniqsc9QfDo?rel=0&showinfo=0" frameborder="0" allowfullscreen></iframe></p>