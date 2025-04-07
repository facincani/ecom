
# Projeto: Sistema de Processamento de Pedidos de Compra

## Objetivo

Desenvolver um sistema capaz de receber e processar pedidos de compra no seguinte formato:

```json
{
  "cliente": "João da Silva",
  "UF": "SP",
  "itens": [
    { "descricao": "Notebook", "quantidade": 1, "precoUnitario": 3500.00 },
    { "descricao": "Mouse", "quantidade": 2, "precoUnitario": 150.00 }
  ]
}
```

## Funcionalidades do Sistema

### 1. Registro do Pedido

- O pedido deve ser **armazenado no banco de dados**.

### 2. Cálculo de Impostos

- O sistema deve realizar uma chamada para o serviço de **cálculo de imposto**, que calcula os tributos devidos com base na região do cliente.
- A alíquota aplicada varia de acordo com a região da UF informada:

| Região         | Alíquota |
|----------------|----------|
| Norte          | 45%      |
| Nordeste       | 40%      |
| Centro-Oeste   | 50%      |
| Sudeste        | 60%      |
| Sul            | 65%      |

### 3. Geração de Comprovante

O serviço de cálculo de imposto deve retornar um comprovante no seguinte formato:

```json
{
  "cliente": "João da Silva",
  "UF": "SP",
  "Regiao": "Sudeste",
  "itens": [
    { "descricao": "Notebook", "quantidade": 1, "precoUnitario": 3500.00 },
    { "descricao": "Mouse", "quantidade": 2, "precoUnitario": 150.00 }
  ],
  "subtotal": 3800.00,
  "imposto": 380.00,
  "total": 4180.00,
  "Aliquota_Aplicada": 60
}
```

### 4. Retorno ao Cliente

- O comprovante gerado deve ser **retornado ao cliente** como resposta da operação.
