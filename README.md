# 🛒 Mercadinho Virtual - POO Architecture

Este projeto é uma aplicação de E-commerce desenvolvida como parte da avaliação **AV2 de Programação Orientada a Objetos** do curso de Ciência da Computação da **Unifeso**.

O objetivo principal foi implementar uma arquitetura robusta no Front-end que respeite os pilares da POO, independentemente do framework visual.

## 👥 Membros do Grupo
* **João Victor Andrade** - 06009925
* **Rafael de Alcântara Peçanha Fernandes** - 06010477
* **Carlos Leonardo Carvalho Otoline** - 06010109
* **Andrey Campos** - 06009553
* **Nathan Salles Ramos** - 06009233
* **Vinícius Schonfelder** - 06010595

## 🛠 Tecnologias e Conceitos
* **React + Vite:** Interface do usuário.
* **JavaScript (ES6 Classes):** Modelagem do domínio.
* **POO:** Uso estrito de Classes, Herança, Polimorfismo e Encapsulamento.
* **Mock Service:** Simulação de API e Banco de Dados em memória.

## 📐 Diagrama de Classes (UML)

```mermaid
classDiagram
    class Produto {
        +int Id
        +string Nome
        +decimal Preco
        +string Categoria
        +AdicionarEstoque(int qtd) void
        +RemoverEstoque(int qtd) void
    }

    class ItemCarrinho {
        +int ProdutoId
        +Produto Produto
        +int Quantidade
        +CalcularSubtotal() decimal
    }

    class Carrinho {
        +int Id
        +List~ItemCarrinho~ Itens
        +AdicionarItem(Produto produto, int qtd) void
        +RemoverItem(int produtoId) void
        +CalcularTotal() decimal
        +FinalizarPedido() Pedido
    }

    class Pedido {
        +int Id
        +DateTime Data
        +decimal Total
        +Cliente Cliente
        +List~ItemCarrinho~ Itens
        +Pagamento Pagamento
        +GerarNotaFiscal() string
    }

    class Pagamento {
        <<abstract>>
        +decimal Valor
        +ProcessarPagamento() bool*
    }

    class PagamentoPix {
        +string ChavePix
        +ProcessarPagamento() bool
    }

    class PagamentoCartao {
        +string NumeroCartao
        +string Titular
        +ProcessarPagamento() bool
    }

    Carrinho "1" *-- "*" ItemCarrinho : contem
    ItemCarrinho "1" --> "1" Produto : referencia
    Pedido "1" --> "1" Carrinho : gera
    Pedido "1" --> "1" Pagamento : utiliza
    Pagamento <|-- PagamentoPix : herda
    Pagamento <|-- PagamentoCartao : herda


🚀 Como Rodar o Projeto
Clone o repositório:

Bash

git clone [https://github.com/SEU-USUARIO/NOME-DO-REPO.git](https://github.com/SEU-USUARIO/NOME-DO-REPO.git)
Instale as dependências:

Bash

npm install
Inicie o servidor de desenvolvimento:

Bash

npm run dev
✅ Critérios Atendidos
[x] Modelagem de Classes: Entidades Produto, Carrinho, Cliente implementadas em src/models.

[x] Herança e Polimorfismo: Classes PagamentoPix e PagamentoCartao estendem Pagamento.

[x] Tratamento de Exceções: Validações de domínio lançam erros tratados na interface.

[x] Encapsulamento: Proteção de dados sensíveis e lógica de negócio nas classes.
