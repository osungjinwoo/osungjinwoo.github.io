---
title: "Ataque de notificações de emparelhagem falsificadas Apple Juice"
date: "2025-01-02"
categories: ["Segurança", "Hacking"]
tags: ["hacking", "mobile", "bluetooth", "ataque"]
excerpt: "Ataque via bluetooth"
image: "../blog/img/apple-juicy.png"
---

![Apple Juicy](./img/apple-juicy.png)

# DEFCON 31
Na última defcon edição 31 aconteceu algo que chocou os participantes, os celulares de quem participavam do evento foram inundados de notificações de emparelhamento de dispositivos apple, como: Airpods, Apple TV, Smarth Watch, etc.

A tela do celular não ficava em paz, você rejeitava uma solicitação, chegava outra.

Mais tarde no mastodon após membros comentarem sobre as notificações, um pesquisador conhecido como Jae Bochs respondeu a todos afirmando que tudo não passava de uma brincadeira que ele resolveu fazer no dia do evento com sua nova descoberta.

# O que é esse ataque?

Conhecido como `"Apple Juice"` este ataque consiste em explorar as requisições via bluetooth para emparelhamento entre dispositivos.

O BLEE (Bluetooth Low-Energy) é uma biblioteca que se comunica com aparelhos da apple através de um popup de solicitação inicial para emparelhar dispositivos para que futuramente os IOT’s se conectem ao dispositivo automaticamente.

Bochs ainda disse que o experimento não foi criado para roubar dados, apenas para enviar pacotes de publicidade bluetooth que não requerem emparelhamento( E como tal não são interrompidos pela alternancia do centro de controle.) Entretanto, ainda que você desligue o bluetooth pela central de controle da apple, você receberá a inundação de popups e seu bluetooth será ligado instantaneamente.

# A amplitude do ataque

Assim que soube dessa noticia da defcon, eu corri pra testar e descobri que esse ataque pode ser feito utilizando apenas um script em python no seu smarthphone ou computador desde que tenha acesso bluetooth, pode ser implementado num flipper zero (canivete suiço de hardware hacking), bem como ser utilizado em dispositivos iot’s que tenham blueetoth integrado.

Eu testei no meu ESP32 e fiquei emocionado de ver a notificação falsa subindo.

O link para o projeto você pode encontrar aqui [AppleJuice no GitHub](https://github.com/ECTO-1A/AppleJuice)

# Como isso me afeta?

Até o momento o que se sabe é que o projeto ainda está em andamento e possivelmente poderemos ver algum ataque sofisticado, mas pra felicidade de muitos, este ataque é inofensivo, inclusive a apple tem ciência disso e diz que não há necessidade de uma correção.

Embora as notificações sejam persistentes, existe uma forma de se livrar desse ataque randômico de dispositivos, basta ir nas configurações e desativar manualmente o blueetoth.

> OBS: Desligar o blueetoth na central de controle não adianta.

# Expectativas

Esse evento chamou a atenção dos pesquisadores e eles esperam futuramente poderem apresentar uma palestra utilizando esta falha do BLEE no junto ao próximo recurso do iOS 17 chamado “NameDrop”.

Um recurso que permitirá que iPhone’s compartilhem seus contatos entre sí ou com smarth watchs utilizando somente a aproximação. E pra quem é amante do hacking e da programação, fica uma expectativa grandiosa enquanto nos divertimos replicando o evento de inundações de popUps durante eventos de segurança para lembrar que: `Se você não está utilizando o bluetooth, mantenha-o desligado`

