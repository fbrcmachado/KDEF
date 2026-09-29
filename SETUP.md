# Instalar o KDEF neste projeto

Este arquivo é a entrada para um agente que recebeu o URL deste repositório. O `manifest.json` versionado no repositório Git é a fonte oficial da versão do KDEF. Instale uma revisão concreta do repositório e mostre a versão dessa revisão. Não inferir que um arquivo local foi atualizado só porque existe versão mais recente no GitHub.

## 1. Inspecionar antes de alterar

Identificar a raiz do projeto e o Git em uso. Ler `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `.agents/skills/kdef/`, `.claude/skills/kdef/` e os comandos existentes, quando presentes. Preservar regras, mudanças não relacionadas e outros nomes de skill. Se o projeto já tiver KDEF ou Modo Escriba, comparar versão e diferenças antes de atualizar.

## 2. Instalar uma fonte canônica

Instalar o conteúdo deste repositório em `.agents/skills/kdef/`. Preferir `git submodule add <URL_DO_REPOSITORIO_KDEF> .agents/skills/kdef` se o projeto for Git e o usuário quiser seguir a fonte remota; usar cópia versionada se submódulos não forem apropriados. Não executar `git submodule add` sobre caminho já existente. A instalação mínima deve conter `SKILL.md`, `manifest.json`, `agents/openai.yaml` e `references/kdef_framework.md` na árvore instalada.

## 3. Adaptar aos agentes em uso

Usar os arquivos em `adapters/` como modelos e instalar só os hosts presentes ou pedidos pelo usuário:

| Host | Modelo neste repositório | Destino no projeto |
| --- | --- | --- |
| Codex e agentes que leem skills locais | `SKILL.md` e `manifest.json` na fonte | `.agents/skills/kdef/` |
| Regras do projeto | `adapters/AGENTS.snippet.md` | acrescentar a `AGENTS.md`, preservando o original |
| Claude Code | `adapters/claude/SKILL.md` | `.claude/skills/kdef/SKILL.md` |
| Claude Code (regras gerais) | `adapters/claude/CLAUDE.snippet.md` | acrescentar a `CLAUDE.md` se necessário |
| Windsurf | `adapters/windsurf/SKILL.md` | `.windsurf/skills/kdef/SKILL.md` |
| GitHub Copilot | `adapters/github/kdef.prompt.md` | `.github/prompts/kdef.prompt.md` |
| Cursor | `adapters/cursor/kdef.md` | `.cursor/commands/kdef.md` |
| Gemini CLI | `adapters/gemini/kdef.toml` | `.gemini/commands/kdef.toml` |
| Gemini CLI (regras gerais) | `adapters/gemini/GEMINI.snippet.md` | acrescentar a `GEMINI.md` se necessário |
| Antigravity | `adapters/antigravity/kdef.md` | `.agents/rules/kdef.md` |

Se Claude ou Gemini precisar importar `AGENTS.md`, usar os snippets correspondentes sem apagar conteúdo preexistente. Os adaptadores contêm apenas ponteiros, não cópias do manifesto ou da referência longa. Não adicionar pastas vazias de `docs/`, `work/`, `scripts/` ou `tests/` ao projeto consumidor.

## 4. Verificar

Confirmar que `manifest.json` é JSON válido, tem `version`, `edition` e uma lista não vazia de `capabilities`; que os caminhos do adaptador existem; e que o `SKILL.md` instalado aponta para a referência presente. Renderizar uma amostra da mensagem de ativação a partir do manifesto. Conferir `git status` e listar os arquivos alterados. Não afirmar que um host executou a skill sem testá-lo nele. Não fazer commit nem deploy como efeito desta instalação, salvo instrução explícita do usuário.

## 5. Atualizar

Se instalado como submódulo, atualizar a revisão com `git submodule update --remote .agents/skills/kdef`, revisar o diff e reaplicar somente os adaptadores modificados. Se instalado como cópia, substituir apenas os arquivos KDEF após comparar mudanças locais. Uma nova versão da mensagem aparecerá depois que `manifest.json` da instalação for atualizado. Não buscar `main` a cada ativação.
