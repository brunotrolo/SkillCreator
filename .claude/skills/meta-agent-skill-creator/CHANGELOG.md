# Changelog da skill `meta-agent-skill-creator`

Histórico de mudanças em `SKILL.md`, `templates/` e `references/`, com o
motivo de cada mudança (ver Fase 5, item 4, do `SKILL.md`). Formato: mais
recente primeiro.

## Não versionado

- Adicionado exemplo de execução completa ao `SKILL.md` (caso
  `log-error-summarizer`), extraído de um teste real do pipeline: revelou
  que agentes somente-leitura não devem ganhar `Bash` quando `Grep`/`Glob`
  já cobrem a necessidade (ex.: contagem de ocorrências via `Grep` no modo
  `count` em vez de `wc -l` via shell). Essa lição é específica de domínio
  — não foi propagada para `templates/agent-template.md`, que continua
  agnóstico; fica só registrada aqui e no exemplo do `SKILL.md`.
- Adicionado exemplo concreto do "resumo curto (3-6 linhas)" da Fase 1 —
  faltava um exemplo real de densidade esperada.
- Clarificado o bullet "edição pontual" em "Quando NÃO usar esta skill":
  uma edição que muda ferramentas/permissões/critério de sucesso é mudança
  de escopo e deve passar por uma Fase 1 (rápida) + Fase 4, não é edição
  pontual.
- Fase 5, item 4, reescrito: o registro em `CHANGELOG.md` é sempre
  obrigatório; atualizar `templates/`/`references/` só quando a lição for
  genérica o bastante para outros casos (antes o texto implicava que as
  duas coisas aconteciam sempre juntas, o que o próprio exemplo do
  `log-error-summarizer` contradizia).
- Criado este `CHANGELOG.md`.

## Rodada 4 de auditoria

- Fase 4 exigia seções com nomes literais idênticos ("Ferramentas
  necessárias", "Limites conhecidos") em todo artefato gerado, mas
  `templates/agent-template.md` usa nomes diferentes para o mesmo
  conteúdo. Relaxada a exigência para apontar às seções de cada template
  em vez de um nome universal fixo.
- Esclarecido que a Fase 1 é sempre obrigatória nesta sessão, enquanto as
  Fases 2–3 podem ser puladas apenas quando já existe template aprovado.

## Rodadas 1–3 de auditoria (criação inicial)

- Adicionada seção "Quando NÃO usar esta skill" — faltava, apesar de ser
  exigida pela própria skill nos artefatos que ela gera.
- Adicionada regra de escalonamento de esforço na Fase 3: o ciclo de 5+5
  variações é só para artefatos novos/diferentes; um pedido simples com
  template já aprovado pula direto para a Fase 4.
- Removida a menção a um diretório `scripts/` que não existia na estrutura
  de arquivos definida na Fase 4; esclarecido que só se cria quando há de
  fato um script.
- Corrigida a terminologia "AGENTS.md" (não é como o Claude Code nomeia
  subagentes) para `.claude/agents/<nome>.md`, batendo com o exemplo de
  árvore de arquivos da própria Fase 4.
