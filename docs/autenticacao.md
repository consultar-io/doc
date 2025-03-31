# Autenticação

Todos os endpoints requerem autenticação usando Autenticação por Token.

## Criar Token da API

### Ambiente de Produção

Para obter um token de autenticação no ambiente de produção:

1. Acesse o [Painel](https://consultar.io/app)
2. Clique no seu e-mail ou nome de usuário no canto superior direito da tela
3. Selecione [Token da API](https://consultar.io/app/token/)
4. Clique no botão `Criar Token`
5. Copie o token gerado e guarde-o em um local seguro, pois ele não será exibido
   novamente.

### Ambiente de Desenvolvimento

Para obter um token de autenticação no ambiente de desenvolvimento:

1. Acesse o [Painel](https://consultar.io/app)
2. Acesse a página de [Suporte](https://consultar.io/app/ajuda/)
3. Solicite um token de desenvolvimento para o Suporte

## Autenticação por Token

O token deve ser enviado no cabeçalho `Authorization` da requisição:

`Authorization: Token <seu-token>`
