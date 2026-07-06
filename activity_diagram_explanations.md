# Diagrama de Atividades

O Diagrama de Atividades UML é utilizado para modelar o fluxo de trabalho ou o processo de negócios de um sistema. Ele mostra a sequência de atividades, decisões, ramificações e junções que ocorrem durante a execução de um caso de uso. Abaixo, detalhamos o diagrama de atividades para o caso de uso "Fazer Pedido" no sistema da Coca-Cola.

## Caso de Uso: Fazer Pedido

Este diagrama ilustra o fluxo de atividades que um `Cliente` e o `Sistema de Pedidos` executam para completar um pedido.

### Fluxo de Atividades:

1.  **Início**: O processo começa.
2.  **Cliente Acessa o Sistema**: O `Cliente` inicia a interação acessando o sistema de pedidos.
3.  **Sistema Exibe Catálogo de Produtos**: O sistema apresenta ao cliente a lista de produtos disponíveis.
4.  **Decisão: Cliente Seleciona Produtos e Quantidades?**:
    *   **Sim**: Se o cliente selecionar produtos e quantidades, o fluxo continua para a criação do pedido.
    *   **Não**: Se o cliente não selecionar produtos ou decidir não continuar, o processo termina.
5.  **Sistema Cria Novo Pedido**: O sistema gera um novo registro de pedido.
6.  **Atividades Paralelas (Fork)**:
    *   **Adicionar Itens ao Pedido**: O sistema adiciona cada produto selecionado como um item individual ao pedido.
    *   **Calcular Subtotal de Cada Item**: Para cada item adicionado, o sistema calcula seu subtotal.
    *   **Atualizar Estoque (Remover Quantidade)**: Simultaneamente, o sistema atualiza o estoque, diminuindo a quantidade dos produtos que foram pedidos.
7.  **Junção (Join)**: As atividades paralelas se juntam após a conclusão de todas elas.
8.  **Calcular Valor Total do Pedido**: O sistema soma os subtotais de todos os itens para obter o valor total do pedido.
9.  **Sistema Confirma Pedido ao Cliente**: O sistema informa ao cliente que o pedido foi realizado com sucesso e apresenta o valor total.
10. **Fim**: O processo de fazer o pedido é concluído.

### Diagrama de Atividades:

![Diagrama de Atividades - Fazer Pedido](/home/ubuntu/activity_diagram_fazer_pedido.png)
