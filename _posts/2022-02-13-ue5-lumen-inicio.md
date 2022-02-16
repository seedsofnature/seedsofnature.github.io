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

    Testeqweqw sadaseqw eqwe qw

  
_(No interior é possível ver uma luz constante, proveniente do skylight, mesmo com as sombras corretas.)_

Isso fez eu repensar a iluminação do meu jogo, tentei usar Distance Fields e Ambient Occlusion, funcionou? Nahh, não como eu gostaria, precisei dar Bake, e várias manchas estranhas apareceram dentro do bunker, tinham a ver com o tamanho do distance mesh de cada objeto. Resolvi estudar mais um pouco zerei o valor da SkyLight, ajustei as luzes direcionais do sol e da lua. Deu certo? Sim! funcionou, mas notei que todo o ambiente externo ficou meio sem vida, com cores fracas, eu precisava da skylight. Algumas horas depois eu havia me tocado que estava usando a Unreal Engine 5 e que ela tinha uma nova tecnologia de iluminação chamada Lumen. Dei uma lida na documentação, assisti a alguns tutoriais, e chegou a hora de testar, Project Settings>Rendering>Global Ilumination: Lumen. Reiniciar a UE5, e pronto, lá estava meu bunker, todo escuro, sem luz interna!! Era o resultado que eu esperava.

Agora posso criar interiores, cavernas, mais bunkers, tudo usando uma luz com comportamento real. Hoje em dia existem placas de video com raytracing custando o olho da cara, que usam raytracing baseado no hardware, o Lumen nada mais é que um raytracing via software. O desempenho foi afetado um pouco, mas muito pouco, coisa que na versão definitiva da Unreal Engine 5 provavelmente vai ter melhorado e muito. Resumindo o “Lumen” é incrível!

Primeiro teste com o protótipo do bunker e o Lumen:

![](/assets/images/15.png)  
_(Já aqui temos uma iluminação mais real, a única luz entrando dentro do bunker é a que esta passando pelo porta, vindo do sol.)_

Com alguns ajustes no interior, temos uma boa iluminação interna!  
Notei que quanto mais luz eu coloco, mais pesado fica o calculo e diminui os frames, mas basta setar para as luzes não afetarem o calculo do ambiente. Mas de qualquer forma optei por usar poucas luzes, pois todos os sistemas do jogos serão dinâmicos, cada luz dessa pode ser definida a um interruptor, e poderão ser criadas dinamicamente pelos jogadores. Mas isso já fica para outro post onde irei explicar o sistema de energia elétrica do jogo.

![](/assets/images/9.png)  
_(Parte Interna do Bunker (WIP) - Subsolo sala de entrada com luzes internas acesas.)_

![](/assets/images/20.png)  
_(Parte Interna do Bunker (WIP) - Escada do Subsolo para a parte interna da superfície, com as luzes acesas.)_

![](/assets/images/8.png)  
_(Parte Interna do Bunker (WIP) - Nível da superfície com as luzes acesas.)_

![](/assets/images/10.png)  
_(Parte Interna do Bunker (WIP) - Parte interna do bunker na Superfície, com vista da escada para o subsolo e entrada do bunker com vista exterior, luz interna acesa.)_

![](/assets/images/11.png)  
_(Parte Interna do Bunker (WIP) - Parte interna da superfície, com vista para fora, e luz apenas na primeira sala.)_

![](/assets/images/12.png)  
_(Parte Interna do Bunker (WIP) - Vista da primeira sala para fora do bunker com luzes apagadas, aqui ´é possivel ver que a luz ambiente segue normalmente lá fora.)_

![](/assets/images/13.png)  
_(Parte Externa do Bunker (WIP) - Da pra ver no meio das sombras a porta do bunker, e toda a escuridão lá dentro pois as luzes estão apagadas.)_

![](/assets/images/14.png)  
_(Parte Externa do Bunker (WIP) - Agora com as luzes internas acesas da pra ver que a luz se comporta de forma real, tanto as sombras internas estão mais claras como também da pra ver a sombra e a luz externa passando pela porta do lado de dentro do bunker.)_

## Ativando o Lumen em seu projeto

Para usar o Lumen como iluminação padrão em seu projeto, basta navegar até Project Setting, clique em Rendering depois navegue até Global Illumination e em Dynamic Global Ilumination Method, selecione Lumen, a UE5 vai pedir para ativar Generate Mesh Distance Fields, caso ainda não esteja ativado(esse processo é automatico pela engine) ele vai pedir para reinciar a Engine, após reiniciar a iluminação global usando Lumen vai estar ativada.

É possivel controlar a qualidade usando Post Process Volumes, mas isso fica para um post mais a fundo sobre o Lumen.

Então é isso, esse é meu primeiro post, espero melhorar na forma de apresentar daqui pra frente. Sinta-se livre para comentar abaixo, sugestões são bem vindas, me sigam nas redes sociais, links no card abaixo.