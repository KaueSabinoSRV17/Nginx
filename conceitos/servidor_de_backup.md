# Servidores como Backup

Caso algum serviço esteja fora do ar no momento, podemos estipular
um servidor reserva, ou backup, para atender as requisições durante um 
período de tempo

## Instruções

### Backup

Para esta configuração, devemos marcar um servidor do 
`upstream` como `backup`:

```conf
upstream {
    server localhost:fora_do_ar;
    server localhost:8081 backup;
}
```

### Max Fails

Define por quantas vezes a requisição pode falhar para ser considerada
indisponível. Idealmente manter no padrão, que é 1

```conf 
upstream {
    server localhost:fora_do_ar max_fails=3;
    server localhost:8081 backup;
}
```

### Fail Timeout

Define por quanto tempo o serviço com defeito será considerado 
indisponível, caso haja apenas 1 `max_fails`. Caso haja mais do que
um, então também é o tempo que ele espera para outra request falhar para 
contar como uma fail.

```conf
upstream {
    server localhost:fora_do_ar fail_timeout=120s;
    server localhost:8081 backup;
}
```

### Health Check

Apenas disponível na versão paga no Nginx. Estipula que de tempos em 
tempos será mandada uma request de teste para o `location` desejado.

```conf
location {
    health_check;
}
```