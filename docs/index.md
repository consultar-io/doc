# CRO

## Autenticação

Todos os endpoints requerem autenticação usando Autenticação por Token

## Autenticação por Token

O token deve ser enviado no cabeçalho `Authorization` da requisição:

`Authorization: Token <seu-token>`

Para obter um token de autenticação, entre em contato com o suporte.

## Endpoints

### Consultar CRO

Consulta um CRO (Conselho Regional de Odontologia) específico.

#### Endpoint

`GET /api/cro/consultar/`

#### Parâmetros de Consulta

- `uf` (string, opcional): UF do registro
- `numero_registro` (string, obrigatório): Número do CRO (zeros à esquerda
  são removidos automaticamente)
- `categoria` (string, obrigatório): Categoria do profissional

**Categorias disponíveis:**

- `cd`: Cirurgião Dentista
- `tsb`: Técnico em Saúde Bucal
- `tpd`: Técnico em Prótese Dentária
- `asb`: Auxiliar em Saúde Bucal
- `apd`: Auxiliar de Prótese Dentária
- `estagiario`: Estagiário
- `clinica-assistencia`: Clínica Dentária/Entidade Prestadora de Assistência
  Odontológica
- `laboratorio`: Laboratório de Prótese Dentária
- `comercio-industria`: Empresa de Produtos Odontológicos

#### Exemplo de Requisição (cURL)

```bash
curl -X GET 'https://consultar.io/api/cro/consultar?uf=sp&numero_registro=123456&categoria=cd' \
-H 'Authorization: Token <seu-token>'
```

#### Respostas

**Sucesso (200 OK):**

```json
{
  "uf": "SP",
  "numero_registro": "123456",
  "categoria": "CIRURGIÃO-DENTISTA",
  "nome_razao_social": "JOÃO SILVA",
  "situacao": "ATIVO"
}
```

ou

**Erro (403 Forbidden):**

```json
{
  "error": "PLANO_INATIVO",
  "message": "Você não possui um plano ativo para realizar consultas."
}
```

ou

```json
{
  "error": "CREDITOS_INSUFICIENTES",
  "message": "Você não possui créditos suficientes para realizar essa consulta."
}
```

**Erro (404 Not Found):**

```json
{
  "error": "NAO_ENCONTRADO",
  "message": "Nenhum registro foi encontrado para os parâmetros informados."
}
```

### Buscar CRO por Nome

Busca profissionais por nome.

#### Endpoint

`GET /api/cro/buscar/`

#### Parâmetros

- `nome_razao_social` (string, obrigatório): Nome do profissional
- `categoria` (string, obrigatório): Categoria do profissional (mesmas opções do
  endpoint anterior)

#### Exemplo de Requisição (cURL)

```bash
curl -X GET 'https://consultar.io/api/cro/buscar?nome_razao_social=joao%20silva&categoria=cd' \
-H 'Authorization: Token <seu-token>'
```

#### Respostas

**Sucesso (200 OK):**

```json
[
  {
    "uf": "SP",
    "numero_registro": "123456",
    "categoria": "CIRURGIÃO-DENTISTA",
    "nome_razao_social": "JOÃO SILVA"
  },
  {
    "uf": "SP",
    "numero_registro": "123457",
    "categoria": "CIRURGIÃO-DENTISTA",
    "nome_razao_social": "JOÃO DOS SANTOS SILVA"
  }
]
```

**Erro (400 Bad Request):**

```json
{
  "error": "LIMITE_RESULTADO_EXCEDIDO",
  "message": "Existem mais de 100 registros com os parâmetros informados.
    Por favor, faça uma pesquisa mais específica."
}
```

**Erro (403 Forbidden):**

```json
{
  "error": "PLANO_INATIVO",
  "message": "Você não possui um plano ativo para realizar consultas."
}
```

ou

```json
{
  "error": "CREDITOS_INSUFICIENTES",
  "message": "Você não possui créditos suficientes para realizar essa consulta."
}
```

**Erro (404 Not Found):**

```json
{
  "error": "NAO_ENCONTRADO",
  "message": "Nenhum registro foi encontrado para os parâmetros informados."
}
```

## Observações

- Todas as consultas consomem 1 crédito do plano do usuário
- O sistema possui um limite de 100 resultados para buscas por nome
- As consultas são registradas no histórico de transações do usuário
- O token de autenticação deve ser mantido em segurança
- Em caso de perda ou comprometimento do token,
  você pode revogá-lo com o suporte
