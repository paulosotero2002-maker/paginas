# Contributing — Padrões de Issues, PRs e Deploy

Este repositório segue um fluxo simples e consistente para garantir rastreabilidade, qualidade e segurança em deploys.

1) Issues
- Crie uma Issue para cada trabalho que desejamos fazer, categorizando como:
  - Correção (bug)
  - Melhoria (enhancement)
  - Nova função (feature)
- Use um título claro e a seguinte estrutura no corpo da issue:
  - Resumo curto
  - Problema/Justificativa
  - Requisitos/critério de aceite
  - Passos para reproduzir (se for bug)
  - Links relevantes
- Adicione labels: `type:bug`, `type:enhancement`, `type:feature`, `priority:low|med|high`.

2) Pull Requests (PRs)
- Sempre abra um PR que referencia a Issue correspondente no primeiro parágrafo da descrição (ex: "Closes #12").
- No corpo do PR inclua:
  - Referência da Issue (obrigatório)
  - Descrição das mudanças
  - Checklist de QA (unit tests, lint, build, smoke)
  - Notas de deploy (migrations, flags, riscos)
- Use branch names com padrão: `type/short-description` (ex: `feature/add-contributing-md`).
- Não faça merge direto em produção; use PRs revisados e aprovados.

3) Deploys
- Deploys são gerenciados via PRs com pipelines de CI que:
  - Executam lint, build, testes unitários e E2E
  - Publicam artefatos e atualizam versões
- Marque a Issue como resolvida quando o PR for mergeado e o deploy estiver concluído.

4) Interface e UX — Motion Principles
- Toda interface deve implementar:
  - Skeletons para conteúdos carregados assincronamente.
  - Lazy-loading de componentes e assets pesados.
  - Animações suaves de entrada/saída e feedback visual de carregamento/progresso.
- Consulte a Skill Motion Principles: https://github.com/kylezantos/design-principles para padrões detalhados.

5) Observabilidade e Telemetria
- Instrumente o sistema para:
  - Erros e performance (Sentry, Datadog ou NewRelic).
  - Tracing/metrics com OpenTelemetry.
- Assegure que logs estruturados sejam enviados a uma plataforma observável.

6) Qualidade de Código e Lint
- Configure checagens automáticas:
  - Linters/formatters (Biome/ESLint, Prettier/alternative)
  - Ferramentas de segurança/arquitetura (Knip, Stryker, arch-contract)
- Regra: PRs não devem passar CI se houver falhas críticas de lint ou quebra de contrato arquitetural.

7) Testes e Cobertura
- Adote testes em três níveis:
  - Unitários (rápidos, com Vitest/Jest)
  - Integração (componentes/serviços)
  - E2E (Playwright)
- Gere relatório de cobertura e publique em Codecov.

8) Checklist mínimo para PRs
- [ ] Referencia a Issue (ex: "Closes #NN")
- [ ] Passou no lint
- [ ] Testes unitários passam
- [ ] Build e smoke local OK
- [ ] Observabilidade básica instrumentada para mudanças relevantes

9) Como ajudar um agente (bots/IA)
- Todo agente que automatiza tarefas deve seguir este arquivo: criar Issue, abrir PR com referência e atualizar status da Issue na descrição do PR.

---

Este arquivo foi gerado automaticamente por um agente; por favor, revise e adapte conforme necessidades da equipe.
