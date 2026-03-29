## UC03 - Realizar Checkout Não Nominal Pago

- **Ator Principal:** Participante
- **Atores Secundários:** Sistema de Pagamento, Sistema de E-mail
- **Resumo:** Este caso de uso representa o processo pelo qual um participante realiza a compra de-ingressos não nominais em um evento. O checkout é realizado em tela única organizada em dois blocos: recebimento do ingresso (sem dropdown de participantes) e pagamento. O sistema cria automaticamente uma conta para o responsável pelos-ingressos.
- **Pré-condições:** O participante deve ter selecionado pelo menos um ingresso não nominal pago no evento.
- **Pós-condições:** Criação automática de conta, reserva de-ingressos por 15 minutos, envio de e-mail de boas-vindas e confirmação de pagamento.

### Cenário Principal

| Ações do Ator | Ações do Sistema |
|---|---|
| 1. Acessa o checkout com-ingressos não nominais pagos selecionados | 2. Exibe o checkout em tela única com dois blocos (Bloco 1 não é exibido) e painel lateral de resumo |
| 3. No Bloco 2, seleciona "Outro" como responsável pelos-ingressos | 4. Exibe campos: nome completo, e-mail e celular (obrigatórios) |
| 5. Preenche os dados do responsável | 6. Valida os campos obrigatórios |
| 7. Marca checkbox de termos e condições | 8. Valida aceite obrigatório |
| 9. Opcionalmente marca recebimento de informações | |
| 10. No Bloco 3, seleciona método de pagamento (Pix, Cartão de Crédito ou Boleto) | 11. Exibe campos do método selecionado |
| 12. Seleciona responsável pelo pagamento | 13. Pré-preenche dados do comprador |
| 14. Opcionalmente aplica cupom de desconto | 15. Valida cupom e exibe desconto no resumo |
| 16. Preenche dados de pagamento | 17. Valida dados do cartão/Pix/Boleto |
| 18. Clica em "Avançar para pagamento" | 19. Processa pagamento via Sistema de Pagamento |
| | 20. Se pagamento aprovado, cria conta automática |
| | 21. Reserva-ingressos por 15 minutos |
| | 22. Envia e-mail de boas-vindas com link de criação de senha |
| | 23. Envia e-mail de confirmação após webhook de pagamento |

### Restrições/Validações

- Bloco 1 (Dados dos participantes) não é exibido em checkout não nominal
- Bloco 2 não exibe dropdown de participantes, apenas campos para "Outro"
- Todos os campos obrigatórios devem estar preenchidos e válidos
- Tempo de reserva: 15 minutos
- Ao expirar, redireciona para página do evento

### Cenário Alternativo

**A1: Usuário logado com dados salvos**
- Se o participante estiver logado e possuir dados salvos, o sistema pré-preenche automaticamente os campos
- O participante pode editar qualquer campo

**A2: Usuário opta por salvar dados para futuras compras**
- Armazena dados do comprador vinculados ao usuário

### Cenário de Exceção

**E1: Cartão de crédito recusado**
- Retorna ao Bloco de pagamento mantendo todos os dados preenchidos
- Exibe mensagem de erro da operadora

**E2: E-mail já possui conta existente**
- Usa a conta existente sem criar duplicata
- Ingressos vinculados à conta existente

**E3: Tempo expirado**
- Redireciona para página do evento com-ingressos liberados

### Requisitos Não-Funcionais

- Tela única com rolagem vertical contínua
- Painel lateral com resumo do pedido
- Tempo de expiração: 15 minutos
- Segurança: não armazenar dados sensíveis de cartão
