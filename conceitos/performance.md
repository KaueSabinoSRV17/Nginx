# Performance no Nginx

Para garantir a performance das aplicações fornecidas pelo Nginx, basta 
algumas configurações simples.

## Configurando Caminhos que Consomem Imagens

Sempre que um cliente requisitar uma foto, podemos configurar
a resposta por um location de Regex, como o final de uma extensão de imagem.

## Chace entre Servidores

Para implementar chace entre servidores, é importante passar o header
`Cache-Control` com o valor `public`. Isso autoriza qualquer intermedíario
que possa trabalhar com cache, além de navegadores clientes, a faze-lo

## Instruções

### Expires

Define por quanto tempo o navegador deve guardar a imagem.

```conf
localtion {
    expires 1d;
}
```