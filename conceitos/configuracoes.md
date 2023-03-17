# Configurando o Nginx

Há muitas configurações diferentes no Nginx. Antes de tudo, devemos saber onde está o arquivo 
de configuração sendo usado.

Para isso, digite o seguinte comando: 

	nginx -h

Ele vai apresentar todas as opções possíveis da CLI do nginx. Na linha onde a flag `-c` é apresentada,
podemos ver o caminho absoluto até o arquivo de configuração sendo usado por default.

É com este arquivo que vamos trabalhar!

## Instruções

No arquivo, haverá diversas intruções descritas. Se atente às seguintes: 

### Includes

Caso não esteja achando alguma instrução padrão, procure por `includes`. 
Ali estará descrito todos os arquivos incluidos na configuração do Nginx.

### Http

Dentro dela podemos configurar os Servers que vamos rodar com o Nginx 
(mais de um é válido).

#### Server

Deve estar dentro de `http`. Define um servidor no Nginx.

##### Listen

Define a porta a ser ouvida.

##### Location

Define uma Url no servidor.

##### Root

Dentro de location, define a pasta onde estarão os arquivos estáticos.

##### Index

Dentro de location, define um arquivo padrão a ser fornecido na rota.

## Comandos

### Flag `-h`

Mostra arquivos de configuração padrão e todas as opções da CLI.

### Flag `-t`

Testa suas alterações, para saber se nada vai quebrar ao recarregar.

### Flag `-s`

Manda um comando ao nginx

#### Reload

Recarrega configurações. Deve ser rodado quando mudamos alguma arquivo de configuração ou de conteúdo.

	nginx -s reload
