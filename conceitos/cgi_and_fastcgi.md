# Protocolos da Web

Para executar requisitar e responder o resultado de lógica de programação na Web
foi criado um Protocolo de Comunicação chamado CGI. Ele serve como uma interface
entre um servidor e os executáveis com a regra de negócio, comunicação com
banco de dados e etc (geralmente era escrito em C++).

## FastCGI

O CGI tradicional apresenta um gargalo de performance: É necessário iniciar um
processo, executa-lo e mata-lo após sua conclusão. O custo computacional disso
é imenso. 

Para solucionar o problema, foi criado outro protocolo: O FastCGI.

Nele, um processo iniciado é mantido, e ele mesmo atende mais do que uma requisição,
caso haja outras requisições após a requisição que iniciou o processo.