# 1. PRD - packages

**Status:** developing

## 1.1 Requisito do Produto

**Título:** Migrar novo dashboard para package no monorepo e inserir no organizador/backoffice
**Tipo:** Refactor
**Story Points:** 13
**Tags:** Frontend
**Responsável:** Matheus Gomes Rodrigues de Jesus

---

### Tópico 1 - Contextualização

- O painel do organizador no Linka Eventos conta atualmente com um dashboard que centraliza as principais informações de acompanhamento de um evento, exibindo dados de inscrições, vendas, check-ins, acessos e receita em tempo real. Esse dashboard é acessado diretamente pelo menu lateral do painel do organizador e representa uma das telas mais estratégicas da plataforma, sendo o ponto central de monitoramento durante a realização de um evento;

- O cenário atual apresenta um problema de natureza arquitetural com impacto direto na evolução do produto. O componente de dashboard está implementado de forma isolada, sem estar organizado como um package compartilhável dentro do monorepo da plataforma. Isso limita a capacidade do time de desenvolvimento de reutilizar, manter e evoluir esse componente de maneira eficiente, gerando acoplamento desnecessário e dificultando futuras expansões;

- Como consequência, qualquer evolução no dashboard exige esforço desproporcional, aumenta o risco de inconsistências entre ambientes e torna o ciclo de desenvolvimento mais lento. A ausência de uma estrutura padronizada também compromete a escalabilidade da plataforma a longo prazo;

- A proposta é migrar o dashboard para um package dentro do monorepo e integrá-lo ao painel do organizador, substituindo definitivamente o componente anterior. Essa migração será acompanhada de mudanças visuais no dashboard, entregando ao mesmo tempo uma melhoria arquitetural e uma experiência atualizada para o organizador;

- Os benefícios esperados são a padronização da arquitetura da plataforma, maior facilidade de manutenção e evolução do dashboard, redução do risco de regressões em futuras entregas e uma interface mais moderna e consistente para o organizador acompanhar seus eventos em tempo real.

---

### Tópico 2 - Migração e desativação do dashboard anterior

- Com a conclusão da migração do dashboard para o novo package no monorepo, o componente anterior deve ser definitivamente desativado, deixando de ser renderizado em qualquer contexto da plataforma;

- O novo dashboard deve ocupar exatamente o mesmo ponto de acesso do anterior dentro do menu lateral do painel do organizador, garantindo continuidade na experiência de navegação sem impacto na jornada do organizador;

- O time de desenvolvimento deve validar, antes da desativação do dashboard anterior, que todas as informações anteriormente exibidas estão disponíveis e funcionando corretamente no novo componente.

---

### Tópico 6 - Critérios de não-regressão

- A migração não deve alterar nenhuma das regras de negócio já existentes relacionadas ao cálculo e exibição dos dados de inscrições, vendas, check-ins e receita;

- O acesso ao dashboard pelo menu lateral deve continuar funcionando para todos os organizadores com eventos ativos na plataforma, sem necessidade de qualquer ação adicional por parte deles;

- Caso a migração seja realizada com o ambiente de produção ativo, o time deve garantir que a substituição do componente ocorra de forma atômica, sem período de indisponibilidade do dashboard para os organizadores.

---

## 2. Decisões Técnicas (ADR)

### 2.2. Contexto

Qual é o problema que estamos observando e que motiva essa decisão ou mudança ?

### 2.3. Decisão

Qual é a mudança que estamos propondo e/ou implementando?

### 2.4. Consequências

O que se torna mais fácil ou mais dificil de fazer por causa dessa mudança ?

---

## 3. Itens Filhos

| ID | Título |
|----|--------|
| 27566 | - |
| 27567 | - |
| 27565 | - |
| 27564 | - |

---

## 4. Links Relacionados

| Tipo | Detalhes |
|------|----------|
| Branch | GBus/27375 |
| Commit | ea647f0d2a0d2e177318a32b0020dbbc7a3b5c60 |
| Pull Request | #24429 |

---

## 5. Informações Adicionais

- **Estado:** Active
- **Coluna:** Developing
- **Criado em:** 2026-03-17
- **Última alteração:** 2026-03-30