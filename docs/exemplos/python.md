# Exemplos em Python

Exemplos do uso da API do [Consultar.io](https://consultar.io/?utm_source=docs&utm_medium=referral&utm_campaign=python) em **Python**.

## Exemplos

- [Exemplo CNPJ](https://github.com/consultar-io/api/blob/main/python/cnpj.py) (cnpj.py)
- [Exemplo CPF](https://github.com/consultar-io/api/blob/main/python/cpf.py) (cpf.py)

## Requisitos

- Python 3.8 ou superior
- requests

## Instalação

### Passo 1

Instale Python 3.8 ou superior.

### Passo 2

Crie um ambiente virtual na raiz do projeto:

```bash
python3 -m venv venv
```

### Passo 3

Ative o ambiente virtual:

- Linux/MacOS:

```bash
source venv/bin/activate
```

- Windows:

```bash
venv\Scripts\activate
```

### Passo 4

Instale as dependências:

```bash
python3 -m pip install -r requirements.txt
```

### Passo 5

Substitua o token de API pelo seu token de API no script:

```python
API_TOKEN = "seu-token-aqui"
```

### Passo 6

Execute o script:

```bash
python3 nome_do_script.py
```
