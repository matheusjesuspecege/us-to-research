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

### 2.1. Resumo da Decisão

Criar o package **@linka/ui** para compartilhamento de componentes UI entre organizer e backoffice, migrando o dashboard existente do organizer para o monorepo como package reutilizável.

### 2.2. Contexto

O projeto do Linka Eventos funciona em um monorepo (turborepo + pnpm workspaces) com packages compartilhados em `packages/` e apps em `apps/`. Já existe o package `@linka/domain` que contém DTOs, requests e enums compartilhados.

O **organizer** possui um dashboard completo em React com:
- 10 gráficos usando recharts (tickets, vendas, check-ins, cupons, etc.)
- Componentes de UI (IndicatorCard, ChartCard, ExportChartDialog)
- Sistema de filtros com jotai atoms
- Data fetching com @tanstack/react-query
- Traduções com react-i18next

O **backoffice** atualmente utiliza PowerBI Embed que será descontinuado, necessitando migrar para o mesmo dashboard do organizer.

### 2.3. Decisão

Criar o package `@linka/ui` com a seguinte estrutura:

```
packages/ui/
├── src/
│   ├── components/       # IndicatorCard, ChartCard, ExportChartButton
│   ├── charts/           # Componentes de gráficos reutilizáveis
│   ├── pages/            # Dashboard page completa
│   └── filters/          # DashboardFilters, DateRangePicker, MultiSelect
```

**Export principal:**
- `@linka/ui` - exports: Dashboard, DashboardFilters, IndicatorCard, Charts

### 2.4. Dependências do Package

O package `@linka/ui` terá como dependências diretas:

| Dependência | Versão Atual (organizer) | Purpose |
|------------|--------------------------|---------|
| recharts | 3.7.0 | Componentes de gráficos |
| @radix-ui/* | 1.1.15 | Dialog, Popover, Slot |
| tailwindcss | 3.4.1 | Estilização |
| jotai | 2.8.2 | Estado local dos filtros |
| @tanstack/react-query | 5.70.0 | Data fetching |
| react-i18next | 14.0.0 | Internacionalização |
| clsx, tailwind-merge | - | Utilitários |
| @ads/components-react | 2.0.7 | Componentes base |
| @ads/tokens | 1.6.1 | Tokens de design |

### 2.5. Arquitetura de Dados

**Separação de responsabilidades:**

```
┌─────────────────────────────────────────────────────────┐
│                     APP (organizer/backoffice)          │
│  - Hooks de data fetching (useEventDashboardMetrics)     │
│  - Lógica de negócio específica                          │
│  - Configuração de API/rotas                             │
└─────────────────────┬───────────────────────────────────┘
                      │ props (dados processados)
                      ▼
┌─────────────────────────────────────────────────────────┐
│                      @linka/ui                           │
│  - Componentes de apresentação                           │
│  - Gráficos (recharts)                                  │
│  - Filtros com jotai (estado local da UI)               │
│  - Traduções via i18n                                   │
└─────────────────────────────────────────────────────────┘
```

- O **package UI** recebe dados via props para renderização
- Os **hooks de data fetching** permanecem nos apps
- Os **atoms de filtros** (jotai) são internos ao package
- DTOs importados de `@linka/domain` (já existente)

### 2.6. Estratégia de Build e Dev

**Build:**
- turborepo com `dependsOn: ["^build"]` - já configurado
- Os apps declaram `"@linka/ui": "workspace:*"` no package.json
- Ao buildar o package, os apps consomem automaticamente

**Dev:**
- `pnpm dev:packages` ou `pnpm -w --filter @linka/ui dev` para watch mode
- Alterações no package refletem ao reiniciar o dev server dos apps
- Alternativa futura: usar `vite-plugin-dts` com watch mode

**Migração:**
1. Criar package `@linka/ui` com estrutura inicial
2. Migrar componentes do organizer/src/ui/pages/dashboard
3. Migrar componentes de ui/components (chart.tsx, skeleton, etc.)
4. Instalar como dependência no organizer (substituir importação local)
5. Instalar como dependência no backoffice (substituir PowerBI)
6. Remover código duplicado do organizer

### 2.7. Consequências

**Positivas:**
- Reuso do dashboard completo entre organizer e backoffice
- Manutenção centralizada dos componentes de gráficos
- Padronização da UI entre apps
- Remoção do PowerBI (licença e complexidade)
- Evolução independente do dashboard

**Pontos de Atenção:**
- Recharts e libs de gráficos precisarão estar no package
- React Query e Jotai são peerDependencies ou dependências diretas
- Tailwind configurado nos apps precisa reconhecer classes do package
- Componentes com traduções requerem i18n configurado nos apps consumidores
- Eventual refatoração de imports nos apps existentes 

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