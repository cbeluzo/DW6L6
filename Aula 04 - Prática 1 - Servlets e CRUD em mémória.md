# **Atividade I: CRUD de Clientes e Produtos em Memória Utilizando Servlets e Arrays**

#### **Objetivo**
Nesta atividade, você vai implementar um sistema web básico para gerenciamento de **Clientes**, **Produtos**, e a associação de **Produtos** aos **Clientes** (compras) utilizando **Servlets** e **ArrayList**. Todos os dados serão armazenados em memória (durante o tempo de execução) sem persistência de dados em banco de dados ou arquivos. Você deverá criar funcionalidades de **CRUD (Create, Read, Update, Delete)** para os **Clientes**, **Produtos** e suas **associações**.

#### **Requisitos Funcionais**
- **Clientes**:
  - Cadastro de clientes (nome e ID único gerado automaticamente).
  - Edição de dados de clientes.
  - Remoção de clientes.
  - Listagem de todos os clientes cadastrados.

- **Produtos**:
  - Cadastro de produtos (nome, preço e ID único gerado automaticamente).
  - Edição de produtos.
  - Remoção de produtos.
  - Listagem de todos os produtos cadastrados.

- **Associação de Produtos a Clientes (Compras)**:
  - Associar um ou mais produtos a um cliente (criando uma lista de compras).
  - Remover produtos da lista de compras de um cliente.
  - Listar os produtos comprados por um cliente.

#### **Requisitos Técnicos**
- **Classes de Modelo**:
  - Crie uma classe `Cliente` que armazene os dados básicos de um cliente: `id` (int), `nome` (String), e uma lista de produtos (ArrayList de `Produto`).
  - Crie uma classe `Produto` que armazene os dados básicos de um produto: `id` (int), `nome` (String), `preco` (double).

- **Servlets**:
  - **Clientes**:
    - Um servlet para **adicionar** clientes.
    - Um servlet para **listar** todos os clientes.
    - Um servlet para **editar** dados de um cliente (nome).
    - Um servlet para **remover** clientes.
  
  - **Produtos**:
    - Um servlet para **adicionar** produtos.
    - Um servlet para **listar** todos os produtos.
    - Um servlet para **editar** dados de um produto (nome e preço).
    - Um servlet para **remover** produtos.

  - **Associação Cliente-Produto (Compras)**:
    - Um servlet para **associar** produtos a um cliente (adicionar produtos à lista de compras do cliente).
    - Um servlet para **listar** os produtos comprados por um cliente específico.
    - Um servlet para **remover** produtos da lista de compras de um cliente.

#### **Fluxo de Trabalho**
- Comece criando as classes de modelo para **Cliente** e **Produto**.
- Implemente os servlets para realizar as operações de CRUD.
- Armazene os dados de clientes, produtos e compras em `ArrayList` para manter as informações em memória.
- Teste todas as operações de CRUD via navegação entre as páginas e interação com formulários simples.

---
