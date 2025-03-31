# Autenticação

Todos os endpoints requerem autenticação usando Autenticação por Token.

## Criar Token da API

### Ambiente de Produção

Para obter um token de autenticação no ambiente de produção clique no botão com
o seu e-mail ou nome de usuário no canto superior direito da tela e
selecione `Token da API`.

Depois, clique no botão `Criar Token`.

Copie o token gerado e guarde-o em um local seguro, pois ele não será exibido novamente.

### Ambiente de Desenvolvimento

Para obter um token de autenticação no ambiente de desenvolvimento, entre em
contato com o Suporte.

## Autenticação por Token

O token deve ser enviado no cabeçalho `Authorization` da requisição:

`Authorization: Token <seu-token>`
