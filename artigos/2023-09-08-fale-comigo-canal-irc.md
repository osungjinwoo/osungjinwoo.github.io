---
title: Fale comigo pelo IRC via tor
date: 2023-09-08 12:43:00 +0800
categories: [irc]
tags: [irc, portal, comunicacao] # TAG names should always be lowercase
image:
    path: img/robot-irc.png
---

- [Welcome](#welcome)
- [O que é IRC](#o-que-é-o-irc)
- [anonimato](#o-irc-garante-anonimato)
- [Instalação](#tutorial-de-instalação)

# Welcome

Seja bem-vindo, este é o primeiro post do meu blog, e vou te ensinar como você pode se conectar comigo via IRC usando uma conexão criptografada via tor.

## O que é o IRC?

Eu não sou prolixo, então vou explicar resumidamente.
IRC é um protocolo de comunicação que nasceu numa época onde a internet era lenta, os computadores não tinham muito espaço e você era cobrado por banda usada da internet. (Imagina quem baixada videos, filmes, jogos, final do mês chorava).

Então o protocolo surgiu na intenção de facilitar a comunicação sem usar muita banda larga. IRC é um dos chats favoritos de hackers e pode ser usado via terminal. Que hacker não gosta de fazer tudo no terminal, não é mesmo?

Inclusive na segunda temporada de Mr.Robot no episódio 5, o Elliot usa o irc para falar com a darlene, enquanto cria um exploit, veja:

![terminal-irc](https://cdn.geekwire.com/wp-content/uploads/2016/07/IRC-conversation-630x394.png)

# O IRC garante anonimato?

Depende de quem gerencia o servidor, por isso escolhi o servidor do Slackjeff, o cara além de ser incrível e contribuir com a comunidade, criou um server criptografado na rede onion(toor) pra garantir o anonimato.

### Tutorial de Instalação

Primeiro, vamos instalar as dependências:

```bash
sudo apt install tor irssi proxychains4 openssl -y
```

### Criando um certificado

Por incrível que pareça, a onion só deixa logar com certificado.

Então, entre na pasta padrão do irc

```bash
cd .irssi/
```

Crie uma chave utilizando o openssl:

```bash
openssl req -newkey rsa:2048 -days 730 -x509 -keyout your_nick.key -out your_nick.cert -nodes
```

Una as chaves

```bash
cat your_nick.cert your_nick.key > your_nick.pem
```

Pegue o fingerprint, você vai precisar no proximo passo

```bash
openssl x509 -sha1 -noout -fingerprint -in your_nick.pem | sed -e 's/^.*=//;s/://g;y/ABCDEF/abcdef/'
```

> algo como isto: `c2ba4db1ccc82cd3f8ec50ebcc3461628f95ab27`


### Canal de teste

Primeiro vamos nos conectar ao servidor privado do SlackJeff de forma normal, sem o protocolo de criptografia onion, edite o seguinte arquivo:

```
nano ~/.irssi/config
```

Agora insira o seguinte comando, conforme mostro no exemplo logo abaixo:

```
  {
    address = "irc.slackjeff.com.br";
    chatnet = "Slackjeff";
    port = "6697";
    use_tls = "yes";
    tls_verify = "no";
  },
```

![irssi exemplo](/assets/img/posts/config-irssi.png)

Salve o arquivo editado.

### Conectando-se ao IRSSI

Inicie o irssi no seu terminal.

```
irssi
/server irc.slackjeff.com.br
/nick seunomehacker

### vamos registrar um nome de usuário
/msg NickServ REGISTER SuaSenhafoda seuemail@example.com
```

### Adicionando o certificado a sua conta

```
### vamos nos identificar com o nome de usuário criado
/msg NickServ IDENTIFY seunomehacker SuaSenhafoda

### Agora adicione o fingerprint que você salvou anteriormente:
/msg NICKSERV CERT ADD c2ba4db1ccc82cd3f8ec50ebcc3461628f95ab27

```

### Adicionando o certificado para o servidor

Adicione a rede base e o local do certificado

```bash

/network add -sasl_username <YourFreenodeUsername> -sasl_password ~/.irssi/your_nick.pem -sasl_mechanism EXTERNAL networkwithtor
```

Adicione a sua rede onion, no meu caso vou adicionar os servidor do slackjaff, la voce pode criar uma sala e usar uma conexão segura.

```bash
/server add -auto -net freenodetor -ssl -ssl_cert ~/.irssi/your_nick.pem slack265fbszrg7eyagbc3aat6eiqpcqwivixoakzlsuphzyw422huyd.onion 6697
/save
```

### Ultimos ajustes

Verifique o arquivo de configuração em `~/.irssi/config`.

```
 {
    address = "slack265fbszrg7eyagbc3aat6eiqpcqwivixoakzlsuphzyw422huyd.onion";
    chatnet = "networkwithtor";
    port = "6697";
    use_tls = "yes";
    tls_cert = "~/.irssi/al4xs.pem";
    tls_verify = "no";
    autoconnect = "yes";
  }
```

Se estiver parecido com isso OK.

> a onion não verifica o tls, e a porta criptografada sempre será 6697.

Dê uma olhada na ultima linha em `/etc/proxychains4.conf`, tem que estar parecido com isto:

```
[ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
socks5  127.0.0.1 9050
```

> Se quiser altere o strick chain para randon chain, apenas comentando e descomentando a linha.

### Inicie sua rede tor

```bash
sudo service tor start
sudo service tor status
```

### E seja bem-vindo a nossa sala de bate papo

```bash
proxychains4 irssi
/j #mundo-libre
/join #defcon4
```

> #mundo-libre (sala do slackjeff)
> #defcon4 (Sala do al4xs)

>Quer aprender os comandos mais legais do IRC? fiz um post falando sobre eles, veja:
{: .prompt-info }

[**Tutorial completo de comandos IRSSI - CLIQUE AQUI**](/posts/comandos-Irssi/)
