# Servidores Web

Um Servidor Web é responsável por receber requisições (ouvindo conexões tcp) e decidir se:

- Ele deve mandar um arquivo estático.
- Ele deve delegar a requisição para outro Servidor, que terá uma aplicação rodando.

## Apache

O Servidor Web mais tradicional é o Apache. Ele se baseia em processos síncronos, ou seja, 
cada requisição gera um novo processo, esse processo comporta apenas uma requisição, e ele deve ser 
derrubado após a requisição acabar.

Não é ideal para múltiplas requisições (requisições essas não só do cliente, mas também entre os microserviços).

## Nginx

O Nginx é otimizado para múltiplas requisições, pois ele é assíncrono.

Quando o cliente faz uma requisição, ele cria um Processo Mestre. Este Processo Mestre pode ter
diversos Processos Colaboradores. Cada Processo Colaborador pode lidar com uma requisição também.

A quantidade de Colaboradores corresponde a quantidade de núcleos da máquina.
