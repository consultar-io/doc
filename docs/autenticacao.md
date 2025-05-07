# Autenticação

Todos os endpoints requerem autenticação usando Autenticação por Token.

## Criar Token de API

Para obter um token de autenticação:

1. Cadastre-se no [Consultar.io](https://consultar.io/cadastrar/?utm_source=docs&utm_medium=referral&utm_campaign=link)
2. Acesse o [Painel](https://consultar.io/painel/?utm_source=docs&utm_medium=referral&utm_campaign=link)
3. Clique no seu nome de usuário no canto superior direito da tela
4. Selecione [Token de API](https://consultar.io/painel/token/?utm_source=docs&utm_medium=referral&utm_campaign=link)
5. Clique no botão `Criar Token`
6. Copie o token gerado e guarde-o em um local seguro, pois ele não será exibido
   novamente.

## Autenticação por Token

O token deve ser enviado no cabeçalho `Authorization` da requisição:

`Authorization: Token <seu-token>`

## Limites e Considerações

- O token de autenticação deve ser mantido em segurança
- Em caso de comprometimento do token, entre em contato com o Suporte
