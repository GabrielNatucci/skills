# Minhas skills para agentes

Seleção de skills para instalar em outros ambientes. Os comandos abaixo foram executados com sucesso no Codex em 17/11/2026, e a presença dos arquivos `SKILL.md` foi verificada. Isso confirma a instalação, não a execução de todos os fluxos de cada skill.

## Skills incluídas

| Skill | Origem | Finalidade |
| --- | --- | --- |
| `grill-me` | [mattpocock/skills](https://github.com/mattpocock/skills) | Atalho para a entrevista da skill `grilling`. |
| `grilling` | [mattpocock/skills](https://github.com/mattpocock/skills) | Questionar planos, decisões e ideias para refinar o raciocínio. |
| `vercel-react-best-practices` | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | Orientações de desempenho para React e Next.js. |
| `web-design-guidelines` | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | Revisão de interfaces, acessibilidade e experiência de uso. |
| `frontend-design` | [anthropics/skills](https://github.com/anthropics/skills) | Direção visual e criação de interfaces. |
| `skill-creator` | [anthropics/skills](https://github.com/anthropics/skills) | Criar, melhorar e avaliar skills. |
| `full-stop` | [t3dotgg/tstack](https://github.com/t3dotgg/tstack/tree/main/skills) | Conduzir o trabalho até um pull request pronto para revisão final, sem fazer merge. |

`web-design-guidelines` aparece uma única vez, mesmo tendo sido solicitada duas vezes.

## Instalar no Codex

Pré-requisitos: Node.js com npm/npx disponíveis e acesso à internet. O ambiente usado na verificação tinha Node.js `v26.13.0` e npm/npx `11.20.0`.

Cole os comandos abaixo no terminal. Eles funcionam como linhas independentes tanto no PowerShell quanto em shells de macOS/Linux:

```sh
npx --yes skills add https://github.com/mattpocock/skills --skill grill-me grilling --agent codex --global --yes
npx --yes skills add https://github.com/vercel-labs/agent-skills --skill vercel-react-best-practices web-design-guidelines --agent codex --global --yes
npx --yes skills add https://github.com/anthropics/skills --skill frontend-design skill-creator --agent codex --global --yes
npx --yes skills add https://github.com/t3dotgg/tstack --skill full-stop --agent codex --global --yes
```

O primeiro `--yes` permite ao npx obter o instalador sem perguntar; o último confirma as opções do instalador. `--agent codex` seleciona o Codex e `--global` instala para o usuário, em vez de apenas para um projeto.

Na instalação verificada, os arquivos ficaram em `~/.agents/skills/<nome-da-skill>/SKILL.md`. No Windows, `~` representa a pasta do usuário. As novas skills ficam disponíveis no próximo turno do Codex.

## Usar em outros agentes ou apenas em um projeto

Para escolher outro agente interativamente, remova `--agent codex` e o último `--yes` de cada comando. Para instalar apenas no projeto atual, remova também `--global` e execute na pasta desse projeto.

## Dependências e limites

- `grill-me` chama `grilling`; por isso ambas estão incluídas.
- **`full-stop` depende de `full-send`:** o arquivo instalado manda ler `../full-send/SKILL.md` e seguir o fluxo descrito nele. Conforme a seleção solicitada, apenas `full-stop` foi instalada do tstack. Portanto, esse fluxo tem uma dependência ausente; instalar o arquivo de `full-stop` sozinho não confirma que seu fluxo completo funciona. Para completar a dependência no futuro, será necessário incluir `full-send` ou obter uma versão independente da skill.
- A `skill-creator` desta seleção é a da Anthropic. O Codex também pode fornecer uma skill própria com o mesmo nome; use a origem para distinguir as duas.
- Os comandos consultam o estado atual dos repositórios e do instalador. Eles reproduzem a seleção, mas não fixam versões ou commits.

## Publicar no GitHub

Adicione este arquivo como `README.md` na raiz do seu repositório. Os comandos baixam as skills diretamente das origens; não é necessário copiar seus arquivos para esse repositório.

Cada skill continua sujeita aos termos e à licença de sua origem.
