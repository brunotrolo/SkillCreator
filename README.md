<p align="center">
  <img src="assets/banner.svg" width="880" alt="SkillCreator">
</p>

<p align="center">
  <em>Uma meta-skill para o Claude Code que cria novos agentes e skills &#8212; validação manual antes da automação, nunca do zero na primeira frase.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/github/stars/brunotrolo/SkillCreator?style=flat-square&color=D97757&label=stars" alt="Stars">
  <img src="https://img.shields.io/badge/pipeline-6%20fases-9C6BFF?style=flat-square" alt="Pipeline de 6 fases">
  <img src="https://img.shields.io/badge/metodologia-Maestros%20da%20IA-9C6BFF?style=flat-square" alt="Metodologia Maestros da IA">
  <img src="https://img.shields.io/badge/works%20with-Claude%20Code-1F1840?style=flat-square" alt="Works with Claude Code">
  <img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license">
</p>

<p align="center">
  <b>📄 README</b> &nbsp;·&nbsp; <a href="./.claude/skills/meta-agent-skill-creator/SKILL.md">🧠 SKILL.md</a> &nbsp;·&nbsp; <a href="./.claude/skills/meta-agent-skill-creator/references/template-checklist.md">✅ Checklist de template</a> &nbsp;·&nbsp; <a href="./.claude/skills/meta-agent-skill-creator/references/escalation-rules.md">🚨 Regras de escalonamento</a> &nbsp;·&nbsp; <a href="./LICENSE">⚖️ MIT License</a>
</p>

---

Uma skill para o Claude Code que **cria outras skills e agentes**, seguindo a
metodologia do canal **Maestros da IA**: a transição de execução manual
supervisionada para a automação total, sem pular a etapa de validação humana.

- **`meta-agent-skill-creator`**: conduz um **pipeline de 6 fases** — molde do
  arquiteto, teste manual "prompt a prompt", validação/refinamento de
  templates, geração do artefato final, otimização em contexto limpo e
  escalonamento de falhas críticas para humanos. Nunca gera um agente/skill
  "caixa-preta" a partir de uma frase vaga.

> O objetivo não é a velocidade da primeira geração — é que o agente/skill
> gerado não vire um "Frankenstein" indepurável. Para o detalhe de cada fase,
> veja o **[SKILL.md](./.claude/skills/meta-agent-skill-creator/SKILL.md)**.
> Este README é só o começo rápido.

---

## ⚡ Pré-requisitos e instalação

- **[Claude Code](https://docs.claude.com/en/docs/claude-code)**.
- Nenhuma dependência externa — a skill é só Markdown (`SKILL.md` + templates
  + referências), sem scripts obrigatórios.

### Instale — copie **apenas a pasta `.claude`** para o seu projeto

Rode **de dentro da pasta do seu projeto**:

**Windows (PowerShell):**
```powershell
git clone --depth 1 https://github.com/brunotrolo/SkillCreator.git .skill-tmp; New-Item -ItemType Directory -Force .claude | Out-Null; Copy-Item -Recurse -Force .skill-tmp\.claude\* .claude\; Remove-Item -Recurse -Force .skill-tmp
```

**Mac / Linux / Git Bash:**
```bash
git clone --depth 1 https://github.com/brunotrolo/SkillCreator.git .skill-tmp && mkdir -p .claude && cp -r .skill-tmp/.claude/. .claude/ && rm -rf .skill-tmp
```

Isso instala a skill `meta-agent-skill-creator` (SKILL.md + `templates/` +
`references/`) em `.claude/skills/`.

**Para atualizar:** rode o mesmo comando de novo.

Abra o Claude Code na pasta do projeto:
```bash
claude
```
A skill carrega automaticamente a partir de `.claude/skills/`.

---

## 🧩 Skill — `meta-agent-skill-creator`: como usar

Dispare em linguagem natural:
> "crie um agente que revisa PRs de segurança"
> "crie uma skill para automatizar o changelog do meu projeto"
> "monte um sub-agente que analisa logs de erro"

A skill conduz um **pipeline de 6 fases** — nunca gera o artefato final direto
da primeira frase, a não ser que já exista um template aprovado equivalente:

1. **Molde do Arquiteto** — define com você a persona/objetivo, as ferramentas
   de sistema necessárias, os arquivos de instrução base (`SKILL.md` ou o
   frontmatter em `.claude/agents/<nome>.md`, e `CLAUDE.md` se precisar de
   contexto persistente) e o critério de sucesso. Se algo for ambíguo, ela
   pergunta em vez de assumir.
2. **Execução manual de um caso de teste** ("prompt a prompt") — constrói um
   agente/skill de teste simples, passo a passo, mostrando cada arquivo
   gerado e resolvendo na hora qualquer problema de diretório, variável de
   ambiente, API key ou permissão de ferramenta. Cada correção vira regra da
   versão final.
3. **Validação e refinamento de templates** — gera variações de template,
   escolhe a mais limpa contra `references/template-checklist.md` e refina
   até a estrutura ficar estável. Para pedidos simples com um template já
   aprovado em `templates/`, pula direto para a Fase 4 (regra de
   escalonamento de esforço, para não desperdiçar tokens).
4. **Geração do artefato final** — compila o `SKILL.md`/frontmatter do
   agente incorporando cada correção técnica da Fase 2 como regra explícita,
   com ferramentas necessárias e limites conhecidos documentados — nunca uma
   lista genérica.
5. **Otimização em contexto limpo** — recomenda testar o resultado numa
   sessão nova (sem o histórico que o criou) e busca ineficiências de token,
   priorizando reuso de `templates/*.md` em vez de reinventar do zero.
6. **Escalonamento para humanos** — toda falha crítica (permissão negada, API
   key ausente, dependência quebrada) é reportada de forma clara e nunca
   falha em silêncio; nunca embute credenciais no artefato gerado.

Veja o passo a passo completo, com todas as regras, em
**[SKILL.md](./.claude/skills/meta-agent-skill-creator/SKILL.md)**.

---

<p align="center">
  ⭐ <b><a href="https://github.com/brunotrolo/SkillCreator/stargazers">Dê uma star no repo</a></b> para acompanhar novas melhorias.
</p>

<p align="center">
  <sub>
    Metodologia inspirada no canal <b>Maestros da IA</b> &nbsp;·&nbsp;
    <a href="https://docs.claude.com/en/docs/claude-code">Claude Code</a>
  </sub>
</p>

<p align="center">
  <sub>© <a href="https://github.com/brunotrolo">brunotrolo</a> · <a href="./LICENSE">MIT</a>.</sub>
</p>
