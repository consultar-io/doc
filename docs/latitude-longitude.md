# Latitude/Longitude

## Introdução

Esta API permite consultar a latitude e longitude de um endereço.

## Endpoints

### 1. Consultar

Consulta as coordenadas geográficas de um endereço específico.

#### Endpoint

`GET /api/latitude-longitude/consultar/`

#### Requisição

| Parâmetro  | Tipo  | Obrigatório | Descrição                       | Exemplo                           |
| ---------- | ----- | ----------- | ------------------------------- | --------------------------------- |
| `endereco` | Texto | Sim         | Endereço completo para consulta | `av eng luis carlos berrini 1748` |

#### Resposta

| Campo                | Tipo   | Descrição                        | Exemplo                                                                                      |
| -------------------- | ------ | -------------------------------- | -------------------------------------------------------------------------------------------- |
| `endereco_formatado` | Texto  | Endereço formatado e normalizado | `"Av. Engenheiro Luís Carlos Berrini, 1748 - Itaim Bibi, São Paulo - SP, 04571-010, Brasil"` |
| `latitude`           | Número | Latitude do endereço             | `-23.612033`                                                                                 |
| `longitude`          | Número | Longitude do endereço            | `-46.6957961`                                                                                |

#### Erros

| Código HTTP | Erro                     | Mensagem                                                   |
| ----------- | ------------------------ | ---------------------------------------------------------- |
| `403`       | `PLANO_INATIVO`          | `Plano inativo para realizar consultas.`                   |
| `403`       | `CREDITOS_INSUFICIENTES` | `Sem créditos suficientes para consulta.`                  |
| `404`       | `NAO_ENCONTRADO`         | `Nenhum registro encontrado com os parâmetros informados.` |

#### Exemplos

##### Exemplo de Requisição (cURL)

```bash
curl -X GET 'https://consultar.io/api/latitude-longitude/consultar?endereco=av%20eng%20luis%20carlos%20berrini%201748' -H 'Authorization: Token <seu-token>'
```

##### Exemplo de Resposta de Sucesso (200)

```json
{
  "endereco_formatado": "Av. Engenheiro Luís Carlos Berrini, 1748 - Itaim Bibi, São Paulo - SP, 04571-010, Brasil",
  "latitude": -23.612033,
  "longitude": -46.6957961
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
- O endereço deve ser informado da forma mais completa possível para maior precisão
- As coordenadas geográficas retornadas são precisas para o número do endereço informado
