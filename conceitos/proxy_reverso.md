# Proxy Reverso

Um Proxy nada mais é do que um intermédio entre um cliente e um servidor.

Podemos ter um conjunto de configurações no Proxy, como por exemplo URLs proibídas,
que não devem ser acessadas.

## Proxies Tracidionais

Proxies Tradicionais estão entre o Cliente que faz a requisição 
e o Servidor Final que atende o Cliene. 

## Proxies Reversos

A ídeia de um Proxy Reverso é ser um servidor entre o Cliente que fez a
Requisição e diversos outros Servidores.

Isso se encontra necessário para implementar a Arquitetura de Microserviços, pois
assim podemos acessar múltiplos servidores diferentes, cada um com um serviço diferente, através de um único servidor (a técnica é chamada API Gateway)

## Microserviços

A idéia é separar regras de negócios que não precisam estar juntas
em diferentes aplicações. No caso, app Frontend deverão saber 
a rota para cada serviço diferente, ou acessar apenas um caminho, que 
implemeta um Proxy Reverso

## Load Balancer

Outra implementação útil de um Proxy Reverso é o conceito de Load Balancer

Um Load Balancer nada mais é do que uma mesma aplicação em mais de um servidor,
com o servidor que faz o Proxy Reverso balanceando o tráfego entre estes diferentes
servidores igualmente. 

Isso é muito útil para garantir que a aplicação não fique sobre carregada!

## Diretivas

### Proxy Pass

Esta diretiva deve ir dentro de uma `location`, e descreve um 
redirecionamento a outro endpoint.

```conf
location {
    proxy_pass http://outro-lugar
}
```

### Upstream

Esta diretiva é usada para estabelecer um Load Balancer.

Dentro dela, devemos estabelecer todos os caminhos para cada
servidor diferente (sem http ou https no começo da URL)

```conf
upstream {
    server caminho-para-um-microserviço1
    server caminho-para-um-microserviço2
}
```