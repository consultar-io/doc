# CPF - Cadastro de Pessoas Físicas

## Introdução

Esta API permite consultar informações sobre pessoas físicas registradas no Cadastro de Pessoas Físicas (CPF) do Brasil.

## Endpoints

### 1. Consultar

Consulta detalhes de um CPF específico.

#### Endpoint

`GET /api/v1/cpf/consultar`

#### Requisição

| Parâmetro         | Tipo  | Obrigatório | Descrição                       | Exemplo       |
| ----------------- | ----- | ----------- | ------------------------------- | ------------- |
| `cpf`             | Texto | Sim         | Número do CPF (apenas números)  | `87135740009` |
| `data_nascimento` | Texto | Sim         | Data de nascimento (AAAA-MM-DD) | `1990-01-01`  |

#### Resposta

| Parâmetro            | Tipo  | Descrição                      | Exemplo                                                                                                                                         |
| -------------------- | ----- | ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `cpf`                | Texto | Número do CPF                  | `87135740009`                                                                                                                                   |
| `nome`               | Texto | Nome completo da pessoa        | `MARIA DA SILVA`                                                                                                                                |
| `data_nascimento`    | Texto | Data de nascimento             | `1990-01-01`                                                                                                                                    |
| `situacao`           | Texto | Situação do CPF                | `REGULAR`                                                                                                                                       |
| `data_inscricao`     | Texto | Data da inscrição no CPF       | `2005-03-15` ou `anterior a 10/11/1990`                                                                                                         |
| `digito_verificador` | Texto | Dígito verificador             | `00`                                                                                                                                            |
| `codigo_controle`    | Texto | Código de controle da consulta | `2407.5A88.0E55.746B`                                                                                                                           |
| `data_emissao`       | Texto | Data de emissão do comprovante | `2024-05-09`                                                                                                                                    |
| `hora_emissao`       | Texto | Hora de emissão do comprovante | `12:05:47`                                                                                                                                      |
| `qrcode_url`         | Texto | URL do QR Code para validação  | `https://servicos.receita.fazenda.gov.br/Servicos/CPF/ca/ResultadoAut.asp?cp=87135740009&cc=24075A880E55746B&de=09052025&he=120547&dv=00&em=01` |

#### Erros

| Código HTTP | Erro                     | Mensagem                                                   |
| ----------- | ------------------------ | ---------------------------------------------------------- |
| `400`       | `REQUISICAO_INVALIDA`    |                                                            |
| `403`       | `PLANO_INATIVO`          | `Plano inativo para realizar consultas.`                   |
| `403`       | `CREDITOS_INSUFICIENTES` | `Sem créditos suficientes para consulta.`                  |
| `404`       | `NAO_ENCONTRADO`         | `Nenhum registro encontrado com os parâmetros informados.` |

#### Exemplos

##### Exemplo de Requisição (cURL)

```bash
curl -X GET 'https://consultar.io/api/v1/cpf/consultar?cpf=12345678900&data_nascimento=1990-01-01' -H 'Authorization: Token <seu-token>'
```

##### Exemplo de Resposta de Sucesso (200)

```json
{
  "cpf": "12345678900",
  "nome": "MARIA DA SILVA SANTOS",
  "data_nascimento": "1990-01-01",
  "situacao": "REGULAR",
  "data_inscricao": "2005-03-15",
  "digito_verificador": "00",
  "codigo_controle": "2406.5A89.0E54.747B",
  "data_emissao": "2024-05-09",
  "hora_emissao": "12:05:47",
  "qrcode_url": "https://servicos.receita.fazenda.gov.br/Servicos/CPF/ca/ResultadoAut.asp?cp=12345678900&cc=24065A890E54747B&de=09052024&he=120547&dv=00&em=01"
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
