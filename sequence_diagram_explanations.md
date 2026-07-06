# Diagrama de Sequência

O Diagrama de Sequência UML descreve a interação entre objetos em um sistema em uma ordem temporal. Ele mostra a sequência de mensagens trocadas entre os participantes para realizar uma funcionalidade específica. Abaixo, detalhamos o diagrama de sequência para o caso de uso "Fazer Pedido" no sistema da Coca-Cola.

## Caso de Uso: Fazer Pedido

Este diagrama ilustra o fluxo de eventos quando um `Cliente` realiza um pedido no sistema.

### Participantes:

*   **Cliente**: O ator que inicia o processo de fazer um pedido.
*   **Sistema de Pedidos**: A interface principal ou módulo de controle que gerencia a interação do cliente.
*   **Catálogo de Produtos**: O módulo responsável por fornecer informações sobre os produtos disponíveis.
*   **Gerenciador de Pedidos**: O módulo que lida com a criação e gestão dos pedidos.
*   **Detalhes do Pedido**: O módulo que gerencia os itens individuais dentro de um pedido.
*   **Gerenciador de Estoque**: O módulo responsável por atualizar as quantidades de produtos em estoque.

### Fluxo de Eventos:

1.  **Cliente Acessa o Sistema**: O `Cliente` envia uma mensagem para o `Sistema de Pedidos` para acessar a funcionalidade de pedidos.
2.  **Sistema Solicita Produtos**: O `Sistema de Pedidos` solicita a lista de produtos disponíveis ao `Catálogo de Produtos`.
3.  **Catálogo Retorna Produtos**: O `Catálogo de Produtos` responde com a lista de produtos ao `Sistema de Pedidos`.
4.  **Cliente Seleciona Produtos**: O `Cliente` seleciona os produtos desejados e suas respectivas quantidades no `Sistema de Pedidos`.
5.  **Sistema Cria Pedido**: O `Sistema de Pedidos` envia uma mensagem para o `Gerenciador de Pedidos` para criar um novo pedido, passando o `ID_Cliente` e a `Data_Pedido`.
6.  **Pedido Criado**: O `Gerenciador de Pedidos` confirma a criação do pedido ao `Sistema de Pedidos`.
7.  **Loop para Cada Produto Selecionado**:
    *   **Adicionar Item ao Pedido**: Para cada produto selecionado, o `Sistema de Pedidos` envia uma mensagem ao `Detalhes do Pedido` para adicionar o item, incluindo `ID_Pedido`, `ID_Produto`, `Quantidade` e `Preço_Unitário`.
    *   **Item Adicionado**: O `Detalhes do Pedido` confirma que o item foi adicionado.
    *   **Remover Quantidade do Estoque**: O `Sistema de Pedidos` solicita ao `Gerenciador de Estoque` para remover a quantidade do produto correspondente.
    *   **Quantidade Removida**: O `Gerenciador de Estoque` confirma a remoção da quantidade.
8.  **Calcular Valor Total**: Após adicionar todos os itens, o `Gerenciador de Pedidos` calcula o `Valor_Total` do pedido.
9.  **Retornar Valor Total**: O `Gerenciador de Pedidos` retorna o `Valor_Total` ao `Sistema de Pedidos`.
10. **Confirmar Pedido ao Cliente**: O `Sistema de Pedidos` exibe a confirmação do pedido e o `Valor_Total` ao `Cliente`.

### Diagrama de Sequência:

![Diagrama de Sequência - Fazer Pedido](/home/ubuntu/sequence_diagram_fazer_pedido.png)
