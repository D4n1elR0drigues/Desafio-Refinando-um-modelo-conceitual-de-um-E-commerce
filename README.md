# Desafio-Refinando-um-modelo-conceitual-de-um-E-commerce

# 🛒 Sistema de E-commerce - Banco de Dados Relacional

Desafio: Refinar o modelo apresentado acrescentando os seguintes pontos:
- Cliente PJ e PF – Uma conta pode ser PJ ou PF, mas não pode ter as duas informações;
- Pagamento – Pode ter cadastrado mais de uma forma de pagamento;
- Entrega – Possui status e código de rastreio;

Este repositório apresenta o **modelo conceitual e relacional** de um sistema de **E-commerce**, incluindo entidades relacionadas a clientes, pedidos, produtos, fornecedores, estoque, entregas e formas de pagamento.

---

## 📐 Diagrama Entidade-Relacionamento

---

## 🗃️ Descrição das Entidades

### 📌 Cliente
- `idCliente`: Identificador único
- `Nome`, `Identificação` (CPF/CNPJ), `Endereço completo` (CEP, cidade, estado, rua, número, bairro)
- `Tipo conta`: Pessoa física ou jurídica

### 📌 Pedido
- `idPedido`: Identificador do pedido
- `Status`, `Descrição`, `Frete`
- `Cliente_idCliente`: Referência ao cliente
- `Entrega_idEntrega`: Referência à entrega

### 📌 Entrega
- `idEntrega`: Identificador
- Endereço completo de entrega
- `Status da entrega`, `Código de rastreio`, `Placa do transporte`

### 📌 Produtos
- `idProdutos`: Identificador do produto
- `Categoria`, `Descrição`, `Valor`

### 📌 Fornecedor
- `idFornecedor`: Identificador
- `Razão Social`, `CNPJ`

### 📌 Terceiro - Vendedor
- `idTerceiro`: Identificador
- `Razão Social`, `Local`

### 📌 Estoque
- `idEstoque`: Identificador
- `Local`: Localização do estoque

---

## 🔁 Tabelas Associativas

### ✅ Produtos por Vendedor
Relaciona produtos aos vendedores terceiros.
- `Terceiro_idTerceiro`
- `Produtos_idProdutos`
- `Quantidade`

### ✅ Disponibilizando um Produto
Relaciona fornecedores aos produtos que fornecem.
- `Fornecedor_idFornecedor`
- `Produtos_idProdutos`

### ✅ Produtos_has_Estoque
Relaciona produtos aos estoques onde estão armazenados.
- `Produtos_idProdutos`
- `Estoque_idEstoque`
- `Quantidade`

### ✅ Relação de Produto/Pedido
Relaciona os produtos incluídos em cada pedido.
- `Produtos_idProdutos`
- `Pedido_idPedido`
- `Quantidade`

### ✅ Liberação de Pedido
Controla a autorização de pedidos com base no status de pagamento.
- `idPedido`
- `StatusPagamento`
- Referências a `Cliente`, `FormaPagamento`

---

## 💳 Forma de Pagamento
- `idFormaPagamento`: Identificador
- `Nome`, `Tipo`, `Descrição`

---

## 🔄 Fluxo de Negócio

1. **Clientes** realizam **pedidos** contendo um ou mais **produtos**.
2. Os produtos são ofertados por **fornecedores** ou **vendedores terceiros**.
3. Os produtos são gerenciados em **estoques** com controle de quantidade.
4. Após o pedido, o cliente define uma **forma de pagamento**, e o sistema controla a **liberação**.
5. O pedido é enviado para **entrega**, com acompanhamento via **código de rastreio**.
6. O sistema registra todas as **relações** entre clientes, pedidos, produtos, pagamentos e entregas.

---

## 📁 Estrutura do Repositório

- `E-commerce.png`: Diagrama ER do banco de dados
- `README.md`: Documentação do projeto

---

## 🎯 Objetivo

Este projeto tem como objetivo apresentar uma modelagem robusta e refinada de banco de dados para um sistema de **E-commerce**, abrangendo desde o cadastro de produtos até a entrega final ao cliente. A estrutura foi pensada para suportar:

- **Clientes PF ou PJ**: Cada cliente pode ser pessoa física **ou** jurídica, mas não ambos. Essa distinção é representada pela coluna `TipoConta` e campos exclusivos de identificação.
- **Formas de pagamento múltiplas**: Um cliente pode registrar **várias formas de pagamento**, sendo que cada pedido será associado a uma dessas opções no momento da liberação.
- **Controle completo de entrega**: A entrega possui **status atualizado** e **código de rastreio**, permitindo que o cliente acompanhe o andamento de seu pedido de forma transparente.
- **Gestão de produtos, fornecedores e vendedores terceiros**: A estrutura contempla múltiplos fornecedores, vendedores independentes e gestão de estoque com controle de quantidades por local.
- **Relação detalhada entre pedidos e produtos**: Cada pedido pode conter múltiplos produtos com suas respectivas quantidades.

O modelo foi construído com foco em escalabilidade, integridade referencial e clareza no relacionamento entre as entidades envolvidas no processo de compras online.

---

## 🧠 Autor

Projeto elaborado com fins acadêmicos e de aprendizado em **modelagem de banco de dados para sistemas de e-commerce**.

