# python-nfce-get

Biblioteca em python que recupera as informações de uma nota fiscal consumidor eletronica (NFCE) e converte em um JSON para processamento da forma que você precisar.

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=9b6a84d1-544b-4413-8c39-bb02a0de21ea&metric=alert_status)](https://sonarcloud.io/dashboard?id=9b6a84d1-544b-4413-8c39-bb02a0de21ea)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=9b6a84d1-544b-4413-8c39-bb02a0de21ea&metric=bugs)](https://sonarcloud.io/dashboard?id=9b6a84d1-544b-4413-8c39-bb02a0de21ea)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=9b6a84d1-544b-4413-8c39-bb02a0de21ea&metric=code_smells)](https://sonarcloud.io/dashboard?id=9b6a84d1-544b-4413-8c39-bb02a0de21ea)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=9b6a84d1-544b-4413-8c39-bb02a0de21ea&metric=coverage)](https://sonarcloud.io/dashboard?id=9b6a84d1-544b-4413-8c39-bb02a0de21ea)
[![Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=9b6a84d1-544b-4413-8c39-bb02a0de21ea&metric=vulnerabilities)](https://sonarcloud.io/dashboard?id=9b6a84d1-544b-4413-8c39-bb02a0de21ea)

## Uso

Inicialmente ela suporta o parse para o(s) estado(s):

- Paraná

A biblioteca faz o parse de duas formas:

- Informando a url do QRCode da nota. (Ex: Na nota do mercado, você escaneia o qrCode e informa o link para o parse)
- Salvando o html da url do site da receita.

### No seu código

```python
from nfceget import app

json = app.json_from_qrcode_link('http://www.fazenda.pr.gov.br/nfce/qrcode?p=41200976430438005123450150002022071015187452|2|1|1|E9C67EF7E8B75CD401B3F6D3B1FD716ED22B3890')

print(json)
```

O resultado será algo como:
```json
{'local': {'name': 'IRMAOS MUFFATO E CIA LTDA', 'cnpj': '76.430.438/0053-00', 'address': 'Av Victor Ferreira do Amaral,1088,,Taruma,Curitiba,PR'}, 'itens': [{'name': 'CEBOLA KG', 'code': '3355', 'quantity': '0,79', 'unit': 'Kg', 'unitaryValue': '2,98', 'totalValue': '2,35'}, .... ], 'totals': {'quantityItens': '26', 'total': '281,03', 'discounts': '5,09', 'valueToPay': '275,94', 'taxes': '62,65'}, 'nfce': {'numero': '204507', 'serie': '15', 'date': '01/09/2020 15:22:18', 'protocolo': '141201044877471', 'version': '4.00', 'chave': '41200976430438005123450150002022071015187452'}}
```

## Como instalar

```bash
make ci-dependencies
```

## Como testar

```bash
make test-coverage
make test
```
