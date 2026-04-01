---
description: Preenche a seção 2. ADR do prd.md analisando o contexto real do projeto
---

Analise o **prd.md** da feature $ARGUMENTS e o código fonte do monorepo para preencher a seção **2. Decisôes Técnicas (ADR)**.

**Atenção:** somente deve ser alterado a sessão **2. Decisôes Técnicas (ADR)**, existe uma separação clara entre **requisito do product owner** com as decisôes técnicas da sessão 2 que deve ser seguida. Todo o conteudo do product owner definido inicialmente deve ser mantido sem alteração, e o novo conteudo deve cumprir os requisitos originais.

**Passos:**
1. Localize o prd.md em **specs/features/$ARGUMENTS/prd.md** e compreenda o contexto.
2. leia package.json dos apps, packages existentes, estrutura de código (use o agente **explore**) para investigar: **apps/*/src**, **packages/**, estrutuda de componentes, hooks, pages e tudo que for necessário no contexto do projeto para ajudar na compreensão.
3. Mapeie dependencias, libs usadas, padrão de imports e preencha a seção **2. ADR** do prd.md com a estrutura correta.
4. Mostre uma prévia para aprovação.
5. Se, aprovado, edite o prd.md substituindo a seção 2.

**Obs:** Pergunte caso precise de alguma informação, antes de supor.