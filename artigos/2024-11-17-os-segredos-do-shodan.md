---
title: Os segredos do Shodan - Google dos hackers
date: 2024-11-17 17:17:00 +0800
categories: [tutorial]
tags: [Shodan, busca, attack, web, dicas, tutorial] # TAG names should always be lowercase
image:
    path: img/shodan.jpeg
---

Embora eu ame um título persuasivo, não existe segredo algum no Shodan. Entretanto, se você é um pesquisador de segurança, você vai amar esse guia que preparei para você e como é de lei por aqui, artigo rápido e objetivo.

# Shodan ou Google?

Resumidamente, o `Shodan` é comparado com o google por sua capacidade de indexação, mas o google indexa word wide web, enquanto Shodan é capaz de indexar quase tudo que está online interagindo diretamente com o serviço e armazenando os metadados que chamamos de "banner".

# Primeiro acesso ao Shodan

Agora deixe-me te mostrar como fazer `pesquisas eficientes` e não genéricas com a maioria dos hunters/pesquisadores fazem.

Acesse o [Shodan Web](https://account.shodan.io/login?continue=http%3A%2F%2Fwww.shodan.io%2Fdashboard) para utilizar a barra de pesquisa do Shodan.

Sim, você precisará fazer login na sua conta para conseguir fazer buscas personalizadas e talvez ter uma conta membro, lembro de ter pago 5 doláres para ser membro definitivo.

# Query's de busca

Vou utilizar a empresa Tesla Motors para exemplificar.

Então, para realizar uma busca por dominios com os mesmos certificados registrados:

```text
ssl:tesla.com
```

> obs: Muito útil para capturar subdomínios.

Agora, faça uma busca por organização:
```text
org:"Tesla Motors Inc."
```

Se você quiser é fácil fazer um filtro específico baseado em qualquer informação que temos na tela, seja um corpo de resposta, um pedaço do cabeçalho, do certificado, uma porta específica ou dominio.

Vamos fazer o primeiro filtro por portas abertas:
```text
org:"Tesla Motors Inc." port:80
```

Vamos fazer um segundo filtro por servidor:
```text
org:"Tesla Motors Inc." port:80 Server: BigIP
```

Aqui estão algumas pesquisas para ambientes vulneraveis para fins didáticos:

```text
city:Sorocaba IP Camera
country:BR webcam
os:windows 7 authenticated: disable
os:"Windows 7" vuln:"MS17-010"
os:"Windows 7" port:445 vuln:"MS17-010" country:"BR"
port:22 product:"OpenSSH" version:<7.0
port:21 "230 Login successful"
port:5900 has_screenshot:true
"Microsoft-IIS/7.5" http.title:"WebDAV"
product:"Microsoft SMB" smb.version:1
product:"Mikrotik" vuln:"CVE-2018-14847"
product:"MongoDB" port:27017 "Authentication disabled"
product:"Exim" vuln:"CVE-2019-10149"
product:"Elastic" port:9200
```

É realmente muito fácil realizar pesquisas, e o Shodan ainda oferece uma interface em modo cli para os amantes de terminal como eu.

# Shodan modo CLI

Para instalar utilize o PIP do python3:

```bash
pip3 install shodan
```

Vamos fazer as buscas como aprendemos na web:

```bash
shodan:search ssl:tesla.com
```

```bash
shodan host 2.18.50.207
```

```bash
shodan domain tesla.com
```

É possível monitorar também sites usando alertas.

```bash
shodan alert create "tesla" 2.18.50.207
```

Você também pode habilitar o que deseja monitorar:

```bash
shodan alert enable <ID do alerta> new_service,open_database,vulnerable,ssl_expired,internet_scanner,uncommon
```

Para visualizar seus alertas:
```bash
shodan alert list
```

> Você também pode gerenciar seus alertas na web seguindo link: [Shodan Monitor](https://monitor.shodan.io/dashboard)


Você também pode realizar download de informações de uma organização específica através do seu terminal:

```bash
shodan download --limit -1 results 'title:"Tesla Motors Inc"'
shodan parse --fields ip_str,port,org --separator , results.json.gz
```

E por fim ver, estatísticas:

```bash
shodan stats --facets org tesla
```
## Truque (JumpTheCat)

Eu sei que não é fácil lembrar todos os comandos, você sempre vai precisar pesquisar por eles em algum momento e o que eu faço é ter uma função carregada no meu terminal, assim basta eu digitar o comando: `shodanquery` e tenho tudo que preciso para fazer minhas pesquisas.

Edite seu .bashrc ou .zshrc para adicionar a função:

```bash
shodanquery () {
	echo "shodan scan submit --force <IP>"
	echo "shodan search tesla.com"
	echo "shodan alert list"
	echo "shodan alert domain hackerone.com"
}
```
Salve, feche e abra seu terminal novamente, depois digite o comando: `shodanquery`.

## Considerações

É possível realizar reconhecimento de um site ou até buscar por vulnerabilidades, o Shodan pode parecer dificil, mas depois que você aprende utilizar as querys de pesquisas, ele abre caminhos pra você.

E se você gosta de uma tela retro cyberpunk, você pode se divertir com isso: [Shodan Retro Anos 2000 - Clique Aqui](https://2000.shodan.io)

Obrigado por ler até aqui.

---

> Quer bater um papo comigo? Não deixe de aparecer na sala #Defcon4 do IRC, estou por lá todos os dias.
{: .prompt-info }

[**Clique AQUI e veja como acessar a sala**](/posts/fale-comigo-canal-irc/)
