# Definição do Domínio do Sistema de Informação da Coca-Cola

Para a atividade avaliativa, o sistema de informação da Coca-Cola será modelado com foco nos seguintes aspectos principais:

## 1. Produtos

O sistema gerenciará uma variedade de produtos oferecidos pela Coca-Cola. Cada produto terá atributos como:

*   **ID do Produto**: Identificador único.
*   **Nome**: Nome comercial do produto (ex: Coca-Cola Original, Coca-Cola Zero, Fanta Laranja).
*   **Descrição**: Detalhes sobre o produto.
*   **Tipo**: Categoria do produto (ex: Refrigerante, Suco, Água).
*   **Tamanho/Volume**: Capacidade da embalagem (ex: 350ml, 1L, 2L).
*   **Preço Unitário**: Preço de venda por unidade.
*   **Status**: Disponibilidade (Ativo, Inativo).

## 2. Clientes

Os clientes da Coca-Cola podem ser distribuidores, varejistas ou grandes contas. Os atributos dos clientes incluirão:

*   **ID do Cliente**: Identificador único.
*   **Nome da Empresa**: Nome do cliente.
*   **CNPJ/CPF**: Documento de identificação fiscal.
*   **Endereço**: Endereço de faturamento e entrega.
*   **Telefone**: Contato telefônico.
*   **Email**: Endereço de email.
*   **Tipo de Cliente**: (ex: Distribuidor, Varejista).

## 3. Pedidos

O sistema registrará os pedidos feitos pelos clientes. Um pedido pode conter múltiplos produtos. Os atributos do pedido serão:

*   **ID do Pedido**: Identificador único.
*   **ID do Cliente**: Referência ao cliente que fez o pedido.
*   **Data do Pedido**: Data em que o pedido foi realizado.
*   **Status do Pedido**: (ex: Pendente, Processando, Enviado, Entregue, Cancelado).
*   **Valor Total**: Valor total do pedido.
*   **Data de Entrega Estimada**: Data prevista para a entrega.

### Detalhes do Pedido

Cada pedido terá itens detalhados, com:

*   **ID do Detalhe do Pedido**: Identificador único.
*   **ID do Pedido**: Referência ao pedido principal.
*   **ID do Produto**: Referência ao produto solicitado.
*   **Quantidade**: Quantidade do produto solicitado.
*   **Preço Unitário no Pedido**: Preço do produto no momento do pedido.
*   **Subtotal**: Subtotal do item.

## 4. Estoque

O controle de estoque é crucial para a gestão de produtos. Os atributos do estoque incluirão:

*   **ID do Estoque**: Identificador único.
*   **ID do Produto**: Referência ao produto em estoque.
*   **Quantidade Disponível**: Número de unidades do produto em estoque.
*   **Localização**: Armazém ou centro de distribuição.
*   **Data da Última Atualização**: Data da última modificação no registro de estoque.

## 5. Fornecedores (Opcional para MER, mas útil para contexto)

Embora não seja o foco principal dos diagramas iniciais, é importante considerar que a Coca-Cola interage com fornecedores de matérias-primas e embalagens. Atributos poderiam incluir:

*   **ID do Fornecedor**: Identificador único.
*   **Nome do Fornecedor**: Nome da empresa fornecedora.
*   **Contato**: Pessoa de contato.
*   **Telefone**: Telefone de contato.
*   **Endereço**: Endereço do fornecedor.

Este domínio servirá como base para a criação dos diagramas UML e de banco de dados solicitados na atividade.
