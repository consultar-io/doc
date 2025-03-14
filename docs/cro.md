# CRO (Conselho Regional de Odontologia)

## Introdução

Esta API permite consultar e buscar informações sobre profissionais e
estabelecimentos registrados nos Conselhos Regionais de Odontologia (CRO) do Brasil.

## Endpoints

### 1. Consultar

Consulta detalhes de um registro específico.

#### Endpoint

`GET /api/cro/consultar/`

#### Requisição

| Parâmetro         | Tipo    | Obrigatório | Descrição                                           | Exemplo  |
| ----------------- | ------- | ----------- | --------------------------------------------------- | -------- |
| `uf`              | Texto   | Sim         | UF do CRO                                           | `SP`     |
| `numero_registro` | Inteiro | Sim         | Número do registro (zeros à esquerda são removidos) | `123456` |
| `categoria`       | Texto   | Sim         | Categoria do profissional/estabelecimento           | `cd`     |

#### Resposta

| Parâmetro           | Tipo  | Descrição                                            | Exemplo              |
| ------------------- | ----- | ---------------------------------------------------- | -------------------- |
| `uf`                | Texto | UF do CRO                                            | `SP`                 |
| `numero_registro`   | Texto | Número do registro                                   | `123456`             |
| `categoria`         | Texto | Categoria do profissional/estabelecimento            | `CIRURGIÃO-DENTISTA` |
| `nome_razao_social` | Texto | Nome ou razão social do profissional/estabelecimento | `JOÃO SILVA`         |
| `situacao`          | Texto | Situação do registro                                 | `ATIVO`              |

#### Erros

| Código HTTP | Erro                     | Mensagem                                                   |
| ----------- | ------------------------ | ---------------------------------------------------------- |
| `403`       | `PLANO_INATIVO`          | `Plano inativo para realizar consultas.`                   |
| `403`       | `CREDITOS_INSUFICIENTES` | `Sem créditos suficientes para consulta.`                  |
| `404`       | `NAO_ENCONTRADO`         | `Nenhum registro encontrado com os parâmetros informados.` |

#### Exemplos

##### Exemplo de Requisição (cURL)

```bash
curl -X GET 'https://consultar.io/api/cro/consultar?uf=sp&numero_registro=123456&categoria=cd' -H 'Authorization: Token <seu-token>'
```

##### Exemplo de Resposta de Sucesso (200)

```json
{
  "uf": "SP",
  "numero_registro": "123456",
  "categoria": "CIRURGIÃO-DENTISTA",
  "nome_razao_social": "JOÃO SILVA",
  "situacao": "ATIVO"
}
```

##### Exemplo de Resposta de Erro (404)

```json
{
  "error": "NAO_ENCONTRADO",
  "message": "Nenhum registro foi encontrado para os parâmetros informados."
}
```

### 2. Buscar por Nome

Realiza busca de profissionais/estabelecimentos por nome.

#### Endpoint

`GET /api/cro/buscar/`

#### Requisição

| Parâmetro         | Tipo  | Obrigatório | Descrição                                            | Exemplo      |
| ----------------- | ----- | ----------- | ---------------------------------------------------- | ------------ |
| nome_razao_social | Texto | Sim         | Nome ou razão social do profissional/estabelecimento | `joao silva` |
| categoria         | Texto | Sim         | Categoria do profissional/estabelecimento            | `cd`         |

#### Resposta

| Parâmetro         | Tipo  | Descrição                                            | Exemplo              |
| ----------------- | ----- | ---------------------------------------------------- | -------------------- |
| uf                | Texto | UF do CRO                                            | `SP`                 |
| numero_registro   | Texto | Número do registro                                   | `123456`             |
| categoria         | Texto | Categoria do profissional/estabelecimento            | `CIRURGIÃO-DENTISTA` |
| nome_razao_social | Texto | Nome ou razão social do profissional/estabelecimento | `JOÃO SILVA`         |

#### Erros

| Código HTTP | Erro                        | Mensagem                                                   |
| ----------- | --------------------------- | ---------------------------------------------------------- |
| `400`       | `LIMITE_RESULTADO_EXCEDIDO` | `Mais de 100 registros encontrados. Refine sua busca.`     |
| `403`       | `PLANO_INATIVO`             | `Plano inativo para realizar consultas.`                   |
| `403`       | `CREDITOS_INSUFICIENTES`    | `Sem créditos suficientes para consulta.`                  |
| `404`       | `NAO_ENCONTRADO`            | `Nenhum registro encontrado com os parâmetros informados.` |

#### Exemplos

##### Exemplo de Requisição (cURL)

```bash
curl -X GET 'https://consultar.io/api/cro/buscar?nome_razao_social=joao%20silva&categoria=cd' -H 'Authorization: Token <seu-token>'
```

##### Exemplo de Resposta de Sucesso (200 OK)

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

##### Exemplo de Resposta de Erro (404 Not Found)

```json
{
  "error": "NAO_ENCONTRADO",
  "message": "Nenhum registro foi encontrado para os parâmetros informados."
}
```

## Categorias

| Código                | Descrição                                                        |
| --------------------- | ---------------------------------------------------------------- |
| `cd`                  | Cirurgião Dentista                                               |
| `tsb`                 | Técnico em Saúde Bucal                                           |
| `tpd`                 | Técnico em Prótese Dentária                                      |
| `asb`                 | Auxiliar em Saúde Bucal                                          |
| `apd`                 | Auxiliar de Prótese Dentária                                     |
| `estagiario`          | Estagiário                                                       |
| `clinica-assistencia` | Clínica Dentária/Entidade Prestadora de Assistência Odontológica |
| `laboratorio`         | Laboratório de Prótese Dentária                                  |
| `comercio-industria`  | Empresa de Produtos Odontológicos                                |

## Limites e Considerações

- Cada requisição consome 1 crédito do plano
- Limite máximo de 100 resultados por busca
- Todas as requisições são registradas no histórico de transações
- O token de autenticação deve ser mantido em segurança
- Em caso de comprometimento do token, contate o suporte para revogação
