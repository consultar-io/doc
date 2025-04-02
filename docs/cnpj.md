# CNPJ (Cadastro Nacional de Pessoa Jurídica)

!!! warning "Documentação em Elaboração"

    Essa documentação ainda está em elaboração. Entre em contato com o Suporte para mais informações.

## Introdução

Esta API permite consultar e buscar informações sobre empresas e
estabelecimentos registrados no Cadastro Nacional de Pessoa Jurídica (CNPJ) do Brasil.

## Endpoints

### 1. Consultar

Consulta detalhes de um CNPJ específico.

#### Endpoint

`GET /api/cnpj/consultar/`

#### Requisição

| Parâmetro | Tipo  | Obrigatório | Descrição                    | Exemplo          |
| --------- | ----- | ----------- | ---------------------------- | ---------------- |
| `cnpj`    | Texto | Sim         | CNPJ da empresa (14 dígitos) | `42515236000100` |

#### Resposta

| Campo                                   | Tipo   | Descrição                                            | Exemplo                                                                     |
| --------------------------------------- | ------ | ---------------------------------------------------- | --------------------------------------------------------------------------- |
| `cnpj`                                  | Texto  | CNPJ completo (14 dígitos)                           | `42515236000100`                                                            |
| `cnpj_formatado`                        | Texto  | CNPJ formatado (XX.XXX.XXX/XXXX-XX)                  | `42.515.236/0001-00`                                                        |
| `cnpj_base`                             | Texto  | Base do CNPJ (8 primeiros dígitos)                   | `42515236`                                                                  |
| `cnpj_ordem`                            | Texto  | Ordem do CNPJ (4 dígitos)                            | `0001`                                                                      |
| `cnpj_dv`                               | Texto  | Dígitos verificadores do CNPJ (2 dígitos)            | `00`                                                                        |
| `razao_social`                          | Texto  | Razão social da empresa                              | `EXPANDA TECNOLOGIA DA INFORMACAO LTDA`                                     |
| `nome_fantasia`                         | Texto  | Nome fantasia da empresa                             | `EXPANDA`                                                                   |
| `natureza_juridica_codigo`              | Texto  | Código da natureza jurídica                          | `2062`                                                                      |
| `natureza_juridica_descricao`           | Texto  | Descrição da natureza jurídica                       | `Sociedade Empresária Limitada`                                             |
| `capital_social`                        | Número | Capital social da empresa                            | `250000.0`                                                                  |
| `capital_social_formatado`              | Texto  | Capital social formatado em reais                    | `R$ 250.000,00`                                                             |
| `porte_empresa_codigo`                  | Texto  | Código do porte da empresa                           | `01`                                                                        |
| `porte_empresa_descricao`               | Texto  | Descrição do porte da empresa                        | `Microempresa (ME)`                                                         |
| `ente_federativo_responsavel`           | Texto  | Ente federativo responsável                          | ``                                                                          |
| `matriz_filial_codigo`                  | Texto  | Código indicando se é matriz ou filial               | `1`                                                                         |
| `matriz_filial_descricao`               | Texto  | Descrição (Matriz ou Filial)                         | `Matriz`                                                                    |
| `situacao_cadastral_codigo`             | Texto  | Código da situação cadastral                         | `02`                                                                        |
| `situacao_cadastral_descricao`          | Texto  | Descrição da situação cadastral                      | `Ativa`                                                                     |
| `data_situacao_cadastral`               | Data   | Data da última atualização da situação cadastral     | `2021-06-29`                                                                |
| `motivo_situacao_cadastral_codigo`      | Texto  | Código do motivo da situação cadastral               | `00`                                                                        |
| `motivo_situacao_cadastral_descricao`   | Texto  | Descrição do motivo da situação cadastral            | `Sem motivo`                                                                |
| `situacao_especial`                     | Texto  | Situação especial da empresa                         | ``                                                                          |
| `data_situacao_especial`                | Data   | Data da situação especial                            | `null`                                                                      |
| `cidade_exterior`                       | Texto  | Cidade no exterior (se aplicável)                    | ``                                                                          |
| `pais_exterior_codigo`                  | Texto  | Código do país no exterior                           | ``                                                                          |
| `pais_exterior_descricao`               | Texto  | Descrição do país no exterior                        | ``                                                                          |
| `data_inicio_atividades`                | Data   | Data de início das atividades                        | `2021-06-29`                                                                |
| `cnae_principal_codigo`                 | Texto  | Código do CNAE principal                             | `6209100`                                                                   |
| `cnae_principal_descricao`              | Texto  | Descrição do CNAE principal                          | `Suporte técnico, manutenção e outros serviços em tecnologia da informação` |
| `lista_cnae_secundarios`                | Lista  | Lista de CNAEs secundários                           |                                                                             |
| `lista_cnae_secundarios.codigo`         | Texto  | Código do CNAE secundário                            | `6201501`                                                                   |
| `lista_cnae_secundarios.descricao`      | Texto  | Descrição do CNAE secundário                         | `Desenvolvimento de programas de computador sob encomenda`                  |
| `tipo_logradouro`                       | Texto  | Tipo do logradouro                                   | `AVENIDA`                                                                   |
| `logradouro`                            | Texto  | Nome do logradouro                                   | `ENG LUIZ CARLOS BERRINI`                                                   |
| `numero`                                | Texto  | Número do endereço                                   | `1748`                                                                      |
| `complemento`                           | Texto  | Complemento do endereço                              | `CONJ 1710`                                                                 |
| `bairro`                                | Texto  | Bairro                                               | `CIDADE MONCOES`                                                            |
| `cep`                                   | Texto  | CEP                                                  | `04571000`                                                                  |
| `uf`                                    | Texto  | UF                                                   | `SP`                                                                        |
| `municipio_codigo`                      | Texto  | Código do município                                  | `7107`                                                                      |
| `municipio_descricao`                   | Texto  | Nome do município                                    | `SAO PAULO`                                                                 |
| `ddd1`                                  | Texto  | DDD do telefone principal                            | `41`                                                                        |
| `telefone1`                             | Texto  | Telefone principal                                   | `96869828`                                                                  |
| `ddd2`                                  | Texto  | DDD do telefone secundário                           | ``                                                                          |
| `telefone2`                             | Texto  | Telefone secundário                                  | ``                                                                          |
| `ddd_fax`                               | Texto  | DDD do fax                                           | ``                                                                          |
| `fax`                                   | Texto  | Número do fax                                        | ``                                                                          |
| `email`                                 | Texto  | Email da empresa                                     | `meucnpj@contabilizei.com.br`                                               |
| `lista_qsa`                             | Lista  | Lista de sócios e administradores                    |                                                                             |
| `lista_qsa.tipo_qsa_codigo`             | Texto  | Código do tipo de sócio e administrador              | `2`                                                                         |
| `lista_qsa.tipo_qsa_descricao`          | Texto  | Descrição do tipo de sócio e administrador           | `PF`                                                                        |
| `lista_qsa.nome_qsa`                    | Texto  | Nome do sócio e administrador                        | `GABRIEL DOMENEGHETTI DE BARROS`                                            |
| `lista_qsa.cpf_cnpj_qsa`                | Texto  | CPF/CNPJ do sócio e administrador                    | `XXX670478XX`                                                               |
| `lista_qsa.cpf_cnpj_qsa_formatado`      | Texto  | CPF/CNPJ do sócio e administrador formatado          | `XXX.670.478-XX`                                                            |
| `lista_qsa.qualificacao_qsa_codigo`     | Texto  | Código da qualificação do sócio e administrador      | `49`                                                                        |
| `lista_qsa.qualificacao_qsa_descricao`  | Texto  | Descrição da qualificação do sócio e administrador   | `Sócio-Administrador`                                                       |
| `lista_qsa.data_entrada_qsa`            | Data   | Data de entrada do sócio e administrador             | `2021-06-29`                                                                |
| `lista_qsa.pais_exterior_qsa_codigo`    | Texto  | Código do país do sócio e administrador              | `105`                                                                       |
| `lista_qsa.pais_exterior_qsa_descricao` | Texto  | Descrição do país do sócio e administrador           | `Estados Unidos da America`                                                 |
| `lista_qsa.cpf_representante_legal_qsa` | Texto  | CPF do representante legal do sócio e administrador  | `XXX670478XX`                                                               |
| `lista_qsa.nome_representante_qsa`      | Texto  | Nome do representante legal do sócio e administrador | `GABRIEL DOMENEGHETTI DE BARROS`                                            |
| `lista_qsa.faixa_etaria_qsa_codigo`     | Texto  | Código da faixa etária do sócio e administrador      | `3`                                                                         |
| `lista_qsa.faixa_etaria_qsa_descricao`  | Texto  | Descrição da faixa etária do sócio e administrador   | `21-3`                                                                      |

#### Erros

| Código HTTP | Erro                     | Mensagem                                                   |
| ----------- | ------------------------ | ---------------------------------------------------------- |
| `400`       | `CNPJ_INVALIDO`          | `CNPJ inválido.`                                           |
| `403`       | `PLANO_INATIVO`          | `Plano inativo para realizar consultas.`                   |
| `403`       | `CREDITOS_INSUFICIENTES` | `Sem créditos suficientes para consulta.`                  |
| `404`       | `NAO_ENCONTRADO`         | `Nenhum registro encontrado com os parâmetros informados.` |

#### Exemplos

##### Exemplo de Requisição (cURL)

```bash
curl -X GET 'https://consultar.io/api/cnpj/consultar?cnpj=42515236000100' -H 'Authorization: Token <seu-token>'
```

##### Exemplo de Resposta de Sucesso (200)

```json
0{
  "cnpj": "42515236000100",
  "cnpj_formatado": "42.515.236/0001-00",
  "cnpj_base": "42515236",
  "cnpj_ordem": "0001",
  "cnpj_dv": "00",
  "razao_social": "EXPANDA TECNOLOGIA DA INFORMACAO LTDA",
  "nome_fantasia": "EXPANDA",
  "natureza_juridica_codigo": "2062",
  "natureza_juridica_descricao": "Sociedade Empresária Limitada",
  "capital_social": 250000.0,
  "capital_social_formatado": "R$ 250.000,00",
  "porte_empresa_codigo": "01",
  "porte_empresa_descricao": "Microempresa (ME)",
  "ente_federativo_responsavel": "",
  "matriz_filial_codigo": "1",
  "matriz_filial_descricao": "Matriz",
  "situacao_cadastral_codigo": "02",
  "situacao_cadastral_descricao": "Ativa",
  "data_situacao_cadastral": "2021-06-29",
  "motivo_situacao_cadastral_codigo": "00",
  "motivo_situacao_cadastral_descricao": "Sem motivo",
  "situacao_especial": "",
  "data_situacao_especial": null,
  "cidade_exterior": "",
  "pais_exterior_codigo": "",
  "pais_exterior_descricao": "",
  "data_inicio_atividades": "2021-06-29",
  "cnae_principal_codigo": "6209100",
  "cnae_principal_descricao": "Suporte técnico, manutenção e outros serviços em tecnologia da informação",
  "lista_cnae_secundarios": [
    {
      "codigo": "6201501",
      "descricao": "Desenvolvimento de programas de computador sob encomenda"
    },
    {
      "codigo": "6201502",
      "descricao": "Web design"
    },
    {
      "codigo": "6202300",
      "descricao": "Desenvolvimento e licenciamento de programas de computador customizáveis"
    },
    {
      "codigo": "6203100",
      "descricao": "Desenvolvimento e licenciamento de programas de computador não-customizáveis"
    },
    {
      "codigo": "6204000",
      "descricao": "Consultoria em tecnologia da informação"
    },
    {
      "codigo": "6311900",
      "descricao": "Tratamento de dados, provedores de serviços de aplicação e serviços de hospedagem na internet"
    },
    {
      "codigo": "6319400",
      "descricao": "Portais, provedores de conteúdo e outros serviços de informação na internet"
    },
    {
      "codigo": "8599603",
      "descricao": "Treinamento em informática"
    }
  ],
  "tipo_logradouro": "AVENIDA",
  "logradouro": "ENG LUIZ CARLOS BERRINI",
  "numero": "1748",
  "complemento": "CONJ  1710",
  "bairro": "CIDADE MONCOES",
  "cep": "04571000",
  "uf": "SP",
  "municipio_codigo": "7107",
  "municipio_descricao": "SAO PAULO",
  "ddd1": "41",
  "telefone1": "96869828",
  "ddd2": "",
  "telefone2": "",
  "ddd_fax": "",
  "fax": "",
  "email": "meucnpj@contabilizei.com.br",
  "lista_qsa": [
    {
      "tipo_qsa_codigo": "2",
      "tipo_qsa_descricao": "PF",
      "nome_qsa": "GABRIEL DOMENEGHETTI DE BARROS",
      "cpf_cnpj_qsa": "XXX670478XX",
      "cpf_cnpj_qsa_formatado": "XXX.670.478-XX",
      "qualificacao_qsa_codigo": "49",
      "qualificacao_qsa_descricao": "Sócio-Administrador",
      "data_entrada_qsa": "2021-06-29",
      "pais_exterior_qsa_codigo": "",
      "pais_exterior_qsa_descricao": "",
      "cpf_representante_legal_qsa": "",
      "nome_representante_qsa": "",
      "faixa_etaria_qsa_codigo": "3",
      "faixa_etaria_qsa_descricao": "21-30"
    },
    {
      "tipo_qsa_codigo": "2",
      "tipo_qsa_descricao": "PF",
      "nome_qsa": "FERNANDO HENRIQUE PEREIRA PINHO",
      "cpf_cnpj_qsa": "XXX805398XX",
      "cpf_cnpj_qsa_formatado": "XXX.805.398-XX",
      "qualificacao_qsa_codigo": "49",
      "qualificacao_qsa_descricao": "Sócio-Administrador",
      "data_entrada_qsa": "2021-06-29",
      "pais_exterior_qsa_codigo": "",
      "pais_exterior_qsa_descricao": "",
      "cpf_representante_legal_qsa": "",
      "nome_representante_qsa": "",
      "faixa_etaria_qsa_codigo": "3",
      "faixa_etaria_qsa_descricao": "21-30"
    },
    {
      "tipo_qsa_codigo": "2",
      "tipo_qsa_descricao": "PF",
      "nome_qsa": "GABRIEL GONCALVES BAU",
      "cpf_cnpj_qsa": "XXX133018XX",
      "cpf_cnpj_qsa_formatado": "XXX.133.018-XX",
      "qualificacao_qsa_codigo": "22",
      "qualificacao_qsa_descricao": "Sócio",
      "data_entrada_qsa": "2023-07-03",
      "pais_exterior_qsa_codigo": "",
      "pais_exterior_qsa_descricao": "",
      "cpf_representante_legal_qsa": "",
      "nome_representante_qsa": "",
      "faixa_etaria_qsa_codigo": "3",
      "faixa_etaria_qsa_descricao": "21-30"
    },
    {
      "tipo_qsa_codigo": "2",
      "tipo_qsa_descricao": "PF",
      "nome_qsa": "BRUNO OLIVEIRA DE ANDRADE E SILVA",
      "cpf_cnpj_qsa": "XXX240708XX",
      "cpf_cnpj_qsa_formatado": "XXX.240.708-XX",
      "qualificacao_qsa_codigo": "22",
      "qualificacao_qsa_descricao": "Sócio",
      "data_entrada_qsa": "2024-09-19",
      "pais_exterior_qsa_codigo": "",
      "pais_exterior_qsa_descricao": "",
      "cpf_representante_legal_qsa": "",
      "nome_representante_qsa": "",
      "faixa_etaria_qsa_codigo": "3",
      "faixa_etaria_qsa_descricao": "21-30"
    }
  ]
}
```

##### Exemplo de Resposta de Erro (404)

```json
{
  "error": "NAO_ENCONTRADO",
  "message": "Nenhum registro foi encontrado para os parâmetros informados."
}
```

## Códigos

### Porte da Empresa

| Código | Descrição                      |
| ------ | ------------------------------ |
| `00`   | Não informado                  |
| `01`   | Microempresa (ME)              |
| `03`   | Empresa de Pequeno Porte (EPP) |
| `05`   | Demais                         |

### Matriz/Filial

| Código | Descrição |
| ------ | --------- |
| `1`    | Matriz    |
| `2`    | Filial    |

### Situação Cadastral

| Código | Descrição |
| ------ | --------- |
| `01`   | Nula      |
| `02`   | Ativa     |
| `03`   | Suspensa  |
| `04`   | Inapta    |
| `08`   | Baixada   |

### Faixa Etária

| Código | Descrição |
| ------ | --------- |
| `1`    | 0-12      |
| `2`    | 13-20     |
| `3`    | 21-30     |
| `4`    | 31-40     |
| `5`    | 41-50     |
| `6`    | 51-60     |
| `7`    | 61-70     |
| `8`    | 71-80     |
| `9`    | 80+       |

### Identificador de Sócio

| Código | Descrição   |
| ------ | ----------- |
| `1`    | PJ          |
| `2`    | PF          |
| `3`    | Estrangeiro |

## Limites e Considerações

- Cada requisição consome 1 crédito do plano
- Todas as requisições são registradas no histórico de transações
- O token de autenticação deve ser mantido em segurança
- Em caso de comprometimento do token, contate o suporte para revogação
