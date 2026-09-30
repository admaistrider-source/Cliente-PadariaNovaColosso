# Time de agentes de desenvolvimento: Padaria Nova Colosso

Seis subagentes do Claude Code, pensados para o sistema da padaria (caixa, encomendas, produção, estoque, relatórios).

| Agente | Papel | Edita código? |
|---|---|---|
| `arquiteto` | Planeja a funcionalidade em etapas antes de começar | Não |
| `backend` | APIs, regras de negócio, banco, integrações | Sim |
| `frontend` | Telas do caixa, encomendas, estoque, relatórios | Sim |
| `qa-testes` | Reproduz bugs com testes e cobre casos de borda | Sim (testes) |
| `revisor-codigo` | Revisa o diff: bugs, segurança, LGPD | Não |
| `devops` | Deploy, CI, backups, monitoramento e infraestrutura | Sim (infra) |

## Como instalar
Copie a pasta `.claude/agents/` para a raiz do repositório do sistema:

```bash
cp -r agentes/.claude/agents <repositorio>/.claude/
```

O Claude Code carrega os agentes automaticamente. Confira com `/agents`.

## Fluxo sugerido
1. **arquiteto** faz o plano.
2. **backend** e **frontend** implementam (podem trabalhar em paralelo).
3. **qa-testes** escreve e roda os testes.
4. **revisor-codigo** revisa o diff.
5. **devops** cuida do CI e publica a nova versão.

Para bugs: comece pelo **qa-testes** (reproduzir), depois backend/frontend corrigem, e o revisor-codigo confere.

## Exemplos de uso
- "Use o arquiteto para planejar o cadastro de encomendas de bolo com sinal."
- "Peça ao qa-testes para reproduzir o erro ao abrir o sistema."
- "Use o devops para configurar o backup diário do banco."
- "Rode o revisor-codigo no meu diff antes de abrir o PR."

## Ajustes
Cada agente é um arquivo `.md` com um cabeçalho (`name`, `description`, `tools`, `model`) e as instruções. Quando a stack do projeto estiver definida, vale acrescentar nos agentes (ou no CLAUDE.md do repositório) a linguagem, framework e os comandos de teste.
