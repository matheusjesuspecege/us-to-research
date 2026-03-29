## UC02 - Realizar Checkout Nominal Gratuito

- **Ator Principal:** Participante
- **Atores Secundários:** Sistema de E-mail
- **Resumo:** Este caso de uso representa o processo pelo qual um participante realiza a inscrição em um evento gratuito com-ingressos nominais. O checkout é realizado em tela única organizada em dois blocos: dados dos participantes e recebimento do ingresso. Não há bloco de pagamento por ser gratuito.
- **Pré-condições:** O participante deve ter selecionado pelo menos um ingresso nominal gratuito no evento.
- **Pós-condições:** Criação automática de conta e envio de e-mail de boas-vindas.

### Cenário Principal

| Ações do Ator | Ações do Sistema |
|---|---|
| 1. Acessa o checkout com-ingressos nominais gratuitos selecionados | 2. Exibe o checkout em tela única com dois blocos e painel lateral de resumo |
| 3. Preenche os dados de cada participante (nome, e-mail, celular com DDI) | 4. Valida os campos obrigatórios em tempo real |
| 5. Preenche campos adicionais configurados pelo organizador (se houver) | 6. Valida campos customizados conforme regra de obrigatoriedade |
| 7. Seleciona o responsável pelos-ingressos no dropdown do Bloco 2 | 8. Exibe campos para "Outro" se selecionado, ou usa dados do participante |
| 9. Marca checkbox de termos e condições | 10. Valida aceite obrigatório |
| 11. Opcionalmente marca recebimento de informações | |
| 12. Clica em "Confirmar inscrição" | 13. Cria conta automática |
| | 14. Envia e-mail de boas-vindas com link de criação de senha |
| | 15. Envia e-mail de confirmação de inscrição |

### Restrições/Validações

- Todos os campos obrigatórios devem estar preenchidos e válidos para habilitar o botão de confirmar
- O campo de celular deve conter seletor de DDI com Brasil pré-selecionado
- Campos customizados seguem obrigatoriedade definida pelo organizador
- Não há tempo de expiração para checkout gratuito

### Cenário Alternativo

**A1: Usuário logado**
- Se o participante estiver logado, não é necessária a criação automática de conta
- Os-ingressos são vinculados diretamente ao perfil do usuário logado

**A2: E-mail já possui conta existente**
- O sistema usa a conta existente sem criar duplicata

### Cenário de Exceção

**E1: E-mail já possui conta existente**
- O sistema usa a conta existente sem criar duplicata
- Os-ingressos são vinculados à conta existente

### Requisitos Não-Funcionais

- O checkout deve ser exibido em tela única com rolagem vertical contínua
- Painel lateral direito deve exibir resumo do pedido
- Não há contador de tempo para checkout gratuito
