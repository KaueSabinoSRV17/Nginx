# Chace no Servidor

O chace não é exclusivo para Navegadores e outros clientes do Nginx. Podemos realizar o cache
também no lado do Servidor.

Isso é útil quando existe um processamento Backend, que pode sim mudar, mas não é comum de mudar,
e que também é o mesmo resultado para todos os clientes que fazem o acesso a esse serviço.

## Diretivas

Antes de apresentar as diretivas da configuração do Nginx, vale ressaltar que a diretiva será diferente
para os casos de se usar `Proxy Reverso` e `FastCGI`:

- Proxy Reverso: `proxy_cache_path`
- FastCGI: `fast_cgi_cache_path`

### Keys

Devemos estipular `keys` no escopo de location.

Keys nada mais são do que a identificação do que vai definir que aquela rota será cacheada.

Podemos fazer essa definição com qualquer variável do Nginx.

Diretivas dentro de `http`:

```conf
proxy_cache_path <caminho onde o cache será armazenado> levels=<número de levels, separados por :> keys_zone=<zona de cache>:<tempo de validade do cache>
```

Diretivas dentro de `location`:

```conf
server {
    proxy_cache <zona de chace>;
    proxy_cache_key <variaveis que definem a key>;
}
```

## Monitoramento

Para realizar o monitoramento do status do cache sem a acessar a máquina do servidor, podemos 