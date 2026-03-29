## UC05 - Aplicar Cupom de Desconto

- **Ator Principal:** Participante
- **Resumo:** Este caso de uso representa o processo pelo qual um participante aplica um cupom de desconto no checkout para obter redução no valor total da compra.
- **Pré-condições:** O participante deve estar no checkout com-ingressos selecionados.
- **Pós-condições:** Desconto aplicado no resumo do pedido ou mensagem de erro exibida.

### Cenário Principal

| Ações do Ator | Ações do Sistema |
|---|---|
| 1. No painel de resumo do pedido, insere o código do cupom no campo de texto | |
| 2. Clica no botão "Adicionar" | 3. Valida o cupom informado |
| | 4. Se válido, exibe o desconto aplicado no resumo com nome do cupom e valor descontado |
| | 5. Disponibiliza opção para remover o cupom |

### Restrições/Validações

- Apenas um cupom pode estar ativo por pedido
- Não há restrição por CPF ou e-mail do participante
- Cupom pode estar sujeito a regras específicas configuradas pelo organizador

### Cenário Alternativo

**A1: Remover cupom aplicado**
- Participante clica na opção de remover cupom
- Sistema remove o desconto e atualiza o valor total

### Cenário de Exceção

**E1: Cupom inválido**
- Exibe mensagem de erro abaixo do campo indicando que o cupom é inválido

**E2: Cupom expirado**
- Exibe mensagem de erro abaixo do campo indicando que o cupom expirou

**E3: Cupom não encontrado**
- Exibe mensagem de erro abaixo do campo indicando que o cupom não foi encontrado

### Requisitos Não-Funcionais

- Validação ocorre no momento do clique no botão "Adicionar"
- Mensagem de erro deve ser clara e explicar o motivo da rejeição
