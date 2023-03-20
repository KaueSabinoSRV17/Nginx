# HTTP e HTTPS

Ao realizar conexões via HTTP, nós trafegamos dados em texto comum, entre Servidor e Cliente.

Isso não é nada seguro, pois qualquer um que interceptar a comunicação pode ter acesso total aos
dados, como usuários, senhas, contas bancárias, etc.

A solução foi o protocolo HTTPS

## HTTPS

O HTTPS é um protocolo que encripta os dados entre o Servidor e o Cliente. Nenhum agente terceiro 
é capaz de ter a acesso aos dados, apenas o Servidor e o Cliente.

Para que isso seja implementado, é necessário ter um certificado SSL na máquina do Servidor.

### Certificados SSL

Há diversas formas de obter certificados válidos, inclusive para teste.

OBS: Não devemos usar o ceritifcado de teste em produção, por quê nenhum navegador vai reconhece-lo como
válido

#### Fazendo um certificado de teste

Para emitir um certificado de teste, vamos usar o comando `openssl`

Para que seja um certificado auto-assinado, é importante usar o sub-comando `req -x509`.

    openssl req -x509 -days <validade do certificado em dias> -newkey <tipo de codificação:número de bits> -keyout <caminho para a chave> -out <caminho para o certificado>