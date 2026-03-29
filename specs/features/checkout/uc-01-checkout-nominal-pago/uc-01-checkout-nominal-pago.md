## UC01 - Realizar Checkout Nominal Pago

- **Ator Principal:** Participante
- **Atores Secundários:** Sistema de Pagamento, Sistema de E-mail
- **Resumo:** Este caso de uso representa o processo pelo qual um participante realiza a compra de ingressos nominais em um evento. O checkout é realizado em uma única tela organizada em três blocos: dados dos participantes, recebimento do ingresso e pagamento. O sistema cria automaticamente uma conta para o responsável pelosingressos ao concluir a compra.
- **Pré-condições:** O participante deve ter selecionado pelo menos um ingresso nominal pago no evento.
- **Pós-condições:** Criação automática de conta, reserva de ingressos por 15 minutos, envio de e-mail de boas-vindas e confirmação de pagamento.

### Cenário Principal

| Ações do Ator | Ações do Sistema |
|---|---|
| 1. Acessa o checkout com ingressos nominais pagos selecionados | 2. Exibe o checkout em tela única com três blocos e painel lateral de resumo do pedido |
| 3. Preenche os dados de cada participante (nome, e-mail, celular com DDI) | 4. Valida os campos obrigatórios em tempo real |
| 5. Preenche campos adicionais configurados pelo organizador (se houver) | 6. Valida campos customizados conforme regra de obrigatoriedade |
| 7. Seleciona o responsável pelos ingressos no dropdown do Bloco 2 | 8. Exibe campos para "Outro" se selecionado, ou usa dados do participante |
| 9. Marca checkbox de termos e condições | 10. Valida aceite obrigatório |
| 11. Opcionalmente marca recebimento de informações | |
| 12. Seleciona método de pagamento (Pix, Cartão de Crédito ou Boleto) | 13. Exibe campos do método selecionado |
| 14. Seleciona responsável pelo pagamento | 15. Pré-preenche dados do comprador |
| 16. Opcionalmente aplica cupom de desconto | 17. Valida cupom e exibe desconto no resumo |
| 18. Preenche dados de pagamento | 19. Valida dados do cartão/Pix/Boleto |
| 20. Clica em "Avançar para pagamento" | 21. Processa pagamento via Sistema de Pagamento |
| | 22. Se pagamento aprovado, cria conta automática |
| | 23. Reserva ingressos por 15 minutos |
| | 24. Envia e-mail de boas-vindas com link de criação de senha |
| | 25. Envia e-mail de confirmação após webhook de pagamento |

### Restrições/Validações

- Todos os campos obrigatórios devem estar preenchidos e válidos para habilitar o botão de avançar
- O campo de celular deve conter seletor de DDI com Brasil pré-selecionado
- CPF, empresa, cargo e outros campos customizados seguem obrigatoriedade definida pelo organizador
- Apenas um cupom por pedido
- Tempo de reserva dosingressos: 15 minutos
- Ao expirar o tempo, o participante é redirecionado para a página do evento

### Cenário Alternativo

**A1: Usuário logado com dados salvos**
- Se o participante estiver logado e possuir dados salvos, o sistema pré-preenche automaticamente os campos do comprador
- O participante pode editar qualquer campo antes de finalizar

**A2: Usuário opta por salvar dados para futuras compras**
- Se marcando a opção "Salvar dados para futuras compras", o sistema armazena dados do comprador vinculados ao usuário
- Dados do cartão são armazenados apenas como card_id (não dados sensíveis)

**A3: Alteração de dados salvos**
- Se o usuário modifica dados que estavam pré-preenchidos, o sistema atualiza os dados salvos com as novas informações

### Cenário de Exceção

**E1: Cartão de crédito recusado**
- O sistema retorna ao Bloco de pagamento mantendo todos os dados preenchidos
- Exibe mensagem de erro da operadora com instruções

**E2: E-mail já possui conta existente**
- O sistema usa a conta existente sem criar duplicata
- Os ingressos são vinculados à conta existente

**E3: Tempo expirado**
- Sistema redireciona para página do evento com os ingressos liberados

### Requisitos Não-Funcionais

- O checkout deve ser exibido em tela única com rolagem vertical contínua
- Painel lateral direito deve exibir resumo do pedido em tempo real
- Tempo de expiração do checkout: 15 minutos
- Segurança: não armazenar dados sensíveis de cartão no banco de dados
