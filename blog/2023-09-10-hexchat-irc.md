---
title: Como acessar o IRC modo GUI com hexchat
date: 2023-09-10 15:29:00 +0800
categories: [irc]
tags: [irc, portal, comunicacao, tor, deepweb] # TAG names should always be lowercase
image:
    path: img/irc-hexchat.png
---

# Sumario

- [Instalando o Hexchat](#instalando-hexchat)
- [Hexchat via TOR](#hechat-via-tor-na-rede-onion)
- [Comandos para usar no hexchat](#comandos)

Sem dúvidas esse é o jeito mais intuitivo para acessar o IRC, se você gosta do modo GUI(Interface Gráfica), este modelo é ideal pra você!

# Instalando HexChat

Utilize o repositorio pra baixa-lo:

```bash
sudo apt install hexchat -y
```

Busque no seu menu por hexchat após a instalação, ou digite no terminal:

```bash
hexchat
```

Ao abrir a interface insira suas informações de NickName que o hexchat deverá exibir, escolha o servidor que você deseja acessar e clique em conectar!

![Irc-hexchat-login](img/irc-part-list1.png)

O IRC ira te sugerir um canal pra você entrar direto, mas você pode escolher pra mostrar uma lista de canais do servidor:

![irc-hexchat-options](img/irc-part-list2.png)

Quando ele abrir a lista de canais você pode pesquisar por um canal específico digitando o nome dele e clicando em `Search`, seleciona-lo e clicar em `Join Channel` para entrar:

![irc-hexchat-list](img/irc-part-list3.png)

Ao lado esquerdo você verá o nome dos canais em que você entrou e poderá navegar entre eles com apenas um único clique, no lado direito você verá usuários presentes no canal e na linha inferior você poderá digitar sua mensagem para enviar.

![irc-hexchat-send](img/irc-part-list4.png)

# Hechat via TOR na rede Onion

Também podemos utiliza-lo para acessar a rede onion que é muito legal.

Primeiro com hexchat aberto clique em `settings`, e vá em `preferências`, selecione `network setup` e insira o proxy server do tor: 127.0.0.1 na porta 9050 utilizando socks5 em todas as conexões e clique em ok.

![hexchat-tor1](img/hexchat-tor1.png)

Agora precisamos adicionar um canal da rede onion, então encerre o hexchat e abra novamente.

Adicione o nome do servidor que deseja se conectar e clique em `edit..` clique em `add` para adicionar o link da onion seguido da porta 6697(porta criptografada).

Por padrão a onion não faz validação de certificado, portanto, selecione a opção `aceitar certificados inválidos`, revise as configurações e clique em ok.

![hexchat-tor2](img/hexchat-tor2.png)

Inicie o serviço do tor

```bash
sudo service tor start
```

Inicie o hexchat novamente, connect no canal já configurado para rede tor.

e divirta-se no canal de sua preferência.

Eu recomendo o canal:
#mundo-libre

![HexChat-color](img/hexchat-color.png)

# Comandos

> E se você não sabe nenhum comando do IRC, basta ler este artigo que explico tudo que você precisa saber pra se divertir:
{: .prompt-info }

[**Tutorial completo de comandos IRSSI - CLIQUE AQUI**](/posts/comandos-Irssi/)
