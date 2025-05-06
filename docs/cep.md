# CEP

## Introdução

Esta API permite consultar os dados de um endereço a partir de um CEP.

## Endpoints

### 1. Consultar

Consulta detalhes de um CEP específico.

#### Endpoint

`GET /api/cep/consultar`

#### Requisição

| Parâmetro | Tipo  | Obrigatório | Descrição                   | Exemplo    |
| --------- | ----- | ----------- | --------------------------- | ---------- |
| `cep`     | Texto | Sim         | CEP do endereço (8 dígitos) | `04571000` |

#### Resposta

| Campo        | Tipo   | Descrição                      | Exemplo                                    |
| ------------ | ------ | ------------------------------ | ------------------------------------------ |
| `cep`        | Texto  | CEP do endereço sem formatação | `"04571000"`                               |
| `uf`         | Texto  | Unidade Federativa do endereço | `"SP"`                                     |
| `localidade` | Texto  | Nome da cidade                 | `"São Paulo"`                              |
| `bairro`     | Texto  | Nome do bairro                 | `"Cidade Monções"`                         |
| `logradouro` | Texto  | Nome do logradouro             | `"Avenida Engenheiro Luiz Carlos Berrini"` |
| `latitude`   | Número | Latitude do CEP                | `-23.609635`                               |
| `longitude`  | Número | Longitude do CEP               | `-46.6943792`                              |

#### Erros

| Código HTTP | Erro                     | Mensagem                                                   |
| ----------- | ------------------------ | ---------------------------------------------------------- |
| `403`       | `PLANO_INATIVO`          | `Plano inativo para realizar consultas.`                   |
| `403`       | `CREDITOS_INSUFICIENTES` | `Sem créditos suficientes para consulta.`                  |
| `404`       | `NAO_ENCONTRADO`         | `Nenhum registro encontrado com os parâmetros informados.` |

#### Exemplos

##### Exemplo de Requisição (cURL)

```bash
curl -X GET 'https://consultar.io/api/cep/consultar?cep=04571000' -H 'Authorization: Token <seu-token>'
```

##### Exemplo de Resposta de Sucesso (200)

```json
{
  "cep": "04571000",
  "uf": "SP",
  "localidade": "São Paulo",
  "bairro": "Cidade Monções",
  "logradouro": "Avenida Engenheiro Luiz Carlos Berrini",
  "latitude": -23.609635,
  "longitude": -46.6943792
}
```

##### Exemplo de Resposta de Erro (404)

```json
{
  "error": "NAO_ENCONTRADO",
  "message": "Nenhum registro foi encontrado para os parâmetros informados."
}
```

## Limites e Considerações

- Cada requisição de "Consultar" consome 1 crédito
- Todas as requisições são registradas no histórico de transações
- O token de autenticação deve ser mantido em segurança
- Em caso de comprometimento do token, entre em contato com o Suporte
- O CEP pode ser informado com ou sem hífen
- As coordenadas geográficas (latitude e longitude) são aproximadas para a
  região do CEP
