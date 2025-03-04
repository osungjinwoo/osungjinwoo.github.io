---
title: O FBI foi hackeado por um troll
date: 2023-09-29 15:57:00 +0800
categories: [notices]
tags: [hackers, hackeado, fbi] # TAG names should always be lowercase
image:
    path: img/fbi-hack.jpg
---

# O aviso

Por volta das 22 horas do dia 12 de novembro de 2021, um pesquisador de segurança conhecido como Vinny Troia fundador da Night Lion & Shadowbyte recebeu uma mensagem do hacker POMPOMPURIN dizendo:

- Pompompurin: Aproveite
- Vinny troia: Aproveite o que
- Pompompurin: Espero que goste

Como você podem ver na imagem abaixo:

![mensagem](img/pompompurin-mensagem.jpg)

Audácia ou sadísmo?


# O Email falso

No dia seguinte, 13 de novembro de 2021 o domínio do FBI.gov foi usado para enviar cerca de 10 mil e-mails falsos para dezenas de milhares de pessoas sobre uma investigação em andamento do Night Lion sobre um suposto grupo de hackers chamados de "The Dark Overlord" em que o autor Vinny Troia estaria envolvido como um participante dos crimes de extorsão deste grupo.


![fake e-mail](https://www.seytonic.com/content/images/size/w1000/2021/11/fakefbiemail.png)


O e-mail além de ser autentico, foi enviado com o assunto: 

<kbd>Urgente: Autor de ameaça no sistema.</kbd>


Na época e-mail deixou muitas pessoas aflitas e embora já sabemos que o e-mail seja uma trollagem, porque Pompompurin tentaria incriminar Vinny troia?

# Uma breve história da treta entre os hackers

Em sua defesa, Vinny troia usou um de seus sites para se defender após receber o e-mail legítimo do FBI.

Ele argumenta que não foi a primeira vez que isso aconteceu, na verdade, da última vez Pompompurin enviou uma mensagem informando que um site de crianças desaparecidas e exploradas publicou uma página divulgando ele como a cara do predador sexual.


![incriminado](img/incriminado.png)


 Antes disso, uma aviso de um ataque de negação de serviço em um dos sites gratuitos onde o qual oferece verificações de violações para consumidores. Antes disso sofreu um hack no twitter onde Pompompurin invadiu seu tweeter e fez varios tweets engraçados se passando por ele enviando tweets infantis a reporteres importantes e ainda antes disso Pompompurin tentou incriminá-lo pelo hack na empresa Astoria; e antes disso outras coisas.

 Enfim, ao que se sabe a dupla são Arqui-inimigos declarados e o hack do FBI foi só mais um evento da saga.

 Vinny troia ainda provoca dizendo que hackers menos inteligentes levam todos os créditos por hacks mas na verdade, são apenas bode expiatório para hackers de verdade ficarem encobertos. 
 
 Declaração que provavelmente não agradou Pompompurin que já contactou ele para provar que o hack era sim dele.


# O hack do FBI

O FBI possuí uma página pública chamada de "portal empresarial de aplicação da lei" onde varias entidades e agências acessam a página para utilizar recursos.

E o primeiro erro que o FBI cometeu foi disponibilizar um recurso para que qualquer pessoa que visita-se essa página pudesse `solicitar uma conta` na plataforma.

![Pagina FBI](img/fbi-page.png)

Ao clicar no botão nada acontece, mas o FBI havia disponibilizando uma documento em pdf como suporte onde explicava que assim que você concluísse o processo de inscrição, você receberia um e-mail do FBI de confirmação.


# A vulnerabilidade

O grande problema é que esse processo de envio do e-mail após a conclusão de envio da solicitação da conta, enviava uma requisição de e-mail pré-fabricado ao servidor, que por sua vez disparava o e-mail legitimo, mas a fabricação do e-mail acontecia do lado do cliente.

![Pagina FBI](img/fbi-page1.png)


Ou seja, o hacker TROLL percebeu que é possível modificar completamente o e-mail e indicar ao servidor pra quem o e-mail seria enviado para então o servidor realizar o disparo do e-mail.

Portanto, o TROLL injetou um script malicioso que automatizou todo o processo e enviou de um total de 100.000 e-mails como já evidenciei acima.

---

> Gostou do novo poste? Quer bater um papo comigo? Não deixe de aparecer na sala #defcon4 do IRC, estou por lá todos os dias.
{: .prompt-info }

[**Clique AQUI e veja como acessar a sala**](/posts/fale-comigo-canal-irc/)
