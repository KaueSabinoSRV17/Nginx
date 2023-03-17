# Load Balancing

Uma implementação útil de um Proxy Reverso é o conceito de Load Balancer

Um Load Balancer nada mais é do que uma mesma aplicação em mais de um servidor,
com o servidor que faz o Proxy Reverso balanceando o tráfego entre estes diferentes
servidores igualmente. 

Isso é muito útil para garantir que a aplicação não fique sobre carregada!

Existem diferentes algoritimos de Load Balancing, cada um 
sendo útil para um caso diferente do outro

## Round Robin

É o Algoritmo padrão do Nginx. Dado uma lista de servidores no 
`upstream`, ele balancear a carga mandando requisições do primeiro até o
último da lista, e voltando ao primeiro após o último receber uma requisição.

É ideal quando temos apenas servidores de conteúdo estático, sem processamento.

## Weighted Round Robin

Segue a mesma idéia do Round Robin, porém, podemos atribuir uma prioridade
maior para certos servidores.

É útil quando temos um servidor mais potente do que o outro. No caso, 
colocamos uma prioridade maior no servidor mais potente, para que o 
mais fraco não fique sobre carregado.

Exemplo: 

```conf
upstream {
    server url-1 weight=2;
    server url-2; # o padrão é 1!
}
```

## Least Connection

O Weighted Round Robin pode ainda não ser o ideal quando temos um 
sistema que pode atender certas requisições de forma simples, enquanto
outras de forma mais demorada. Para isso, é interessante implementar o
Least Connection

Ele tenta usar também a sequência do Weighted Round Robin, porém, ele 
vai dar prioridade a servidores que estão com menos conexões. Assim, garantimos
que não teremos uma sobrecarga devido ao fato de que algumas requisições levam menos
tempo do que outras.

Exemplo: 

```conf
upstream {
    least_conf;
    server url-1 weight=2;
    server url-2; # o padrão é 1!
}
```