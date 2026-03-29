## UC04 - Realizar Checkout Não Nominal Gratuito

- **Ator Principal:** Participante (autenticado)
- **Atores Secundários:** Sistema de E-mail
- **Resumo:** Este caso de uso representa o processo pelo qual um participante autenticado realiza a inscrição em um evento gratuito com-ingressos não nominais. O checkout é realizado em tela única com apenas o Bloco 2 (recebimento do ingresso). Exige autenticação obrigatória do participante.
- **Pré-condições:** O participante deve estar autenticado e ter selecionado pelo menos um ingresso não nominal gratuito no evento.
- **Pós-condições:** Envio de e-mail de confirmação de inscrição.

### Cenário Principal

| Ações do Ator | Ações do Sistema |
|---|---|
| 1. Acessa o checkout com-ingressos não nominais gratuitos selecionados | 2. Verifica que o participante está autenticado |
| 3. Exibe o checkout com Bloco 1 oculto e Bloco 2 visível | 4. Exibe o checkout em tela única com Bloco 2 e painel lateral |
| 5. Seleciona "Outro" como responsável pelos-ingressos | 6. Exibe campos: nome completo, e-mail e celular (obrigatórios) |
| 7. Preenche os dados do responsável | 8. Valida os campos obrigatórios |
| 9. Marca checkbox de termos e condições | 10. Valida aceite obrigatório |
| 11. Opcionalmente marca recebimento de informações | |
| 12. Clica em "Confirmar inscrição" | 13. Vincula-ingressos ao perfil do usuário logado |
| | 14. Envia e-mail de confirmação de inscrição |

### Restrições/Validações

- Participantedeve estar autenticado para acessar o checkout
- Se não estiver logado, redireciona para tela de login/cadastro
- Após autenticação, retorna ao checkout no ponto em que estava
- Bloco 1 (Dados dos participantes) não é exibido
- Bloco 3 (Pagamento) não é exibido por ser gratuito
- Não há tempo de expiração

### Cenário Alternativo

**A1: Participante não autenticado tenta acessar checkout**
- Sistema redireciona para tela de login ou cadastro
- Após autenticação, retorna ao checkout

### Cenário de Exceção

**E1: Participante não autenticado**
- Redireciona para tela de login/cadastro

### Requisitos Não-Funcionais

- Tela única com rolagem vertical contínua
- Autenticação obrigatória para acesso
- Sem contador de tempo para checkout gratuito
