# Codex Frontend Craft v2

## Resumo (pt-BR)
Super skill de design system para front-end no GPT-5 Codex. Versão com guias adicionais de comandos e anti-padrões para reforçar consistência e qualidade visual.

## Descrição
Projeto que define regras, critérios e fluxo de trabalho para gerar UI/UX de qualidade, evitando resultados genéricos.

## O que inclui
- `skill.yaml` com metadados da skill
- `system.md` com o guia principal de design
- `commands.md` com comandos e checks
- `anti-patterns.md` com erros comuns e o que evitar

## Instalação passo a passo (pt-BR)
1. Baixe o projeto (zip) ou clone o repositório.
2. Localize a pasta de skills do Codex (`$CODEX_HOME/skills`). Padrão:
   - Windows: `%USERPROFILE%\\.codex\\skills`
   - macOS/Linux: `~/.codex/skills`
3. Copie a pasta do projeto para `.../skills/codex-frontend-craft-v2`.
4. Verifique se `skill.yaml`, `system.md`, `commands.md` e `anti-patterns.md` estão dentro dessa pasta.

Exemplos:
```bash
mkdir -p "$HOME/.codex/skills"
git clone https://github.com/bugeeapps/codex-frontend-craft-v2.git "$HOME/.codex/skills/codex-frontend-craft-v2"
```

```powershell
$skills = Join-Path $env:USERPROFILE ".codex\\skills"
New-Item -ItemType Directory -Force -Path $skills | Out-Null
git clone https://github.com/bugeeapps/codex-frontend-craft-v2.git (Join-Path $skills "codex-frontend-craft-v2")
```

## Step-by-step installation (EN)
1. Download the project (zip) or clone the repo.
2. Find your Codex skills folder (`$CODEX_HOME/skills`). Defaults:
   - Windows: `%USERPROFILE%\\.codex\\skills`
   - macOS/Linux: `~/.codex/skills`
3. Copy the project folder to `.../skills/codex-frontend-craft-v2`.
4. Make sure `skill.yaml`, `system.md`, `commands.md`, and `anti-patterns.md` are inside that folder.

Examples:
```bash
mkdir -p "$HOME/.codex/skills"
git clone https://github.com/bugeeapps/codex-frontend-craft-v2.git "$HOME/.codex/skills/codex-frontend-craft-v2"
```

```powershell
$skills = Join-Path $env:USERPROFILE ".codex\\skills"
New-Item -ItemType Directory -Force -Path $skills | Out-Null
git clone https://github.com/bugeeapps/codex-frontend-craft-v2.git (Join-Path $skills "codex-frontend-craft-v2")
```

## Uso no Codex CLI (pt-BR)
1. Abra o Codex CLI.
2. Ative a skill pelo nome `codex-frontend-craft-v2` (ex.: no prompt "Use a skill codex-frontend-craft-v2 para ...").
3. Descreva o que você precisa (tipo de tela, público, stack, restrições).

## Using in Codex CLI (EN)
1. Open Codex CLI.
2. Activate the skill by name `codex-frontend-craft-v2` (e.g. in the prompt "Use the codex-frontend-craft-v2 skill to ...").
3. Describe your UI requirements (page type, audience, stack, constraints).

## Exemplos de prompts (pt-BR)
- "Use a skill codex-frontend-craft-v2 para criar um design system de UI com direção visual clara."
- "Gere uma tela de onboarding com animações leves e layout inesperado."
- "Refatore o CSS para hierarquia visual melhor, sem mudar a lógica."

Exemplo completo de invocação:
```text
Use codex-frontend-craft-v2.

Modo: craft:explore -> craft:proposal -> craft:build

Contexto do produto:
Página de dashboard financeiro para founders,
usada à noite, ambiente escuro, foco em decisões rápidas.

Stack:
React + Tailwind
Não mudar lógica nem dados.

Objetivo:
Refinar visual, tipografia, espaçamento e hierarquia.
Eliminar aparência genérica.
```

3️⃣ Prompt CURTO para "deixar a página bonita" (copiar/colar)

Esse é o atalho mental

```text
codex "
Use codex-frontend-craft-v2.
Modo: craft:build.

Deixe esta página bonita.
Sem alterar lógica.
Sem layout genérico.
"
```

Simples. Brutal. Funciona.

4️⃣ Quer auditar antes de mudar?
```text
codex "
Use codex-frontend-craft-v2.
Modo: craft:audit.

Analise esta página React/Tailwind
e aponte todos os padrões genéricos.
"
```

## Example prompts (EN)
- "Use the codex-frontend-craft-v2 skill to design a bold marketing page with a unique visual direction."
- "Create a SaaS dashboard UI with a signature layout and strong typography."
- "Improve spacing and hierarchy using Tailwind without touching business logic."

## Links
- Repositório: https://github.com/bugeeapps/codex-frontend-craft-v2
- Versão v1: https://github.com/bugeeapps/codex-frontend-craft

Uso livre por Pedro Noronha.

## Parâmetros da skill (pt-BR)
- name: `codex-frontend-craft-v2` (nome da skill no Codex CLI)
- description: "Production-grade frontend with extreme design intentionality." (resumo do foco)
- scope: `frontend`, `react`, `tailwind` (contextos onde aplica)
- poder de fogo: pipeline técnico com comandos + anti-padrões + checks para consistência de design system (escala tipográfica, hierarquia, grid, espaçamento, tokens semânticos, paleta, estados, acessibilidade, motion e responsividade) em UI de produção

## Skill parameters (EN)
- name: `codex-frontend-craft-v2` (skill name in Codex CLI)
- description: "Production-grade frontend with extreme design intentionality." (focus summary)
- scope: `frontend`, `react`, `tailwind` (where it applies)
- power level: technical pipeline with commands + anti-patterns + checks for design-system consistency (type scale, hierarchy, grid, spacing, semantic tokens, palette, states, accessibility, motion, responsiveness) in production UI
