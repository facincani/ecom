# Projeto:  Serviço de Pedidos + Catálogo de Produtos

## Descrição Geral

Para completar nosso ecossitema precisamos de um serviço de **catálogo de produtos**, além disso evoluções são necessárias no **sistema de pedidos**

---

## Descrição do Serviço de Catálogo de Produtos

### 🛠️ Funções principais
- Cadastro de produtos com:
  - Nome
  - Descrição
  - Preço
  - Estoque disponível
- Listagem e busca de produtos
- Atualização de estoque (após pedidos)

### 💾 Persistência
- Tabela de **produtos**

#### ✅ Validações
- Nome obrigatório
- Preço deve ser **positivo**
- Estoque não pode ser **negativo**

---

### 2. Serviço de Pedidos

#### 🛠️ Funções principais
- Consultar pedidos por cliente
- Atualizar **status do pedido** (ex: `PENDENTE`, `ENVIADO`, `CANCELADO`)

#### 🔁 Requisições HTTP externas
- Ao criar o pedido, o serviço de pedidos consulta o serviço de catálogo para:
  - Verificar se o(s) produto(s) existe(m)
  - Checar se há **estoque suficiente**
- Após criar o pedido, envia requisição para o serviço de catálogo para **atualizar o estoque**

#### ✅ Validações
- Não permitir pedido com **produto inexistente**
- Não permitir pedido com **quantidade superior ao estoque**

