# WORKFLOW — Ciclo de trabalho dos agents

**Status:** processo documental para agents; nenhuma ferramenta de automação de app configurada.

## 1. Entrada

Ler `AGENTS.md`, `docs/ROADMAP.md`, `docs/STATUS.md`, `docs/agents/HANDOFF.md`, ADRs e especificações da tarefa. Verificar branch/PR atual; **não presumir que documentos de PR aberto já estão em main**.

Confirmar: `taskId`, objetivo, tipo (documentação, design, bug, feature, segurança), prioridade, plataforma(s), dependências, decisões abertas, arquivos no escopo, condições de aceite e permissão de publicação. Ler também [PROMPT-OBRIGATORIO](PROMPT-OBRIGATORIO.md), [CANARY](CANARY.md), [QUALITY-GATES](QUALITY-GATES.md), [SAFEGUARDS](SAFEGUARDS.md), standards e threat model quando aplicável.

## 2. Planejamento

- Explicar a menor alteração que satisfaz o objetivo, impacto no mapa e cartões, estados e riscos.
- Levantar alternativas quando houver conflito com decisão aceita; solicitar aprovação, não redefinir produto sozinho.
- Documentar diferenças intencionais entre iOS e Android e potenciais efeitos em serviços/dados.
- Identificar verificação aplicável: revisão de texto/links para docs, matrizes visuais para protótipos, builds/testes e E2E apenas quando existir código.

## 3. Execução

Preferir PRs delimitados por marco. Respeitar origem do branch e mudanças concorrentes. Não substituir informação de outros agents sem comparar alterações. Proposta, aprovado e implementado são estados diferentes.

## 4. Auditoria — SEMPRE

| Dimensão | Conferência |
| --- | --- |
| Produto | dois cartões, relógio/carrossel, Pins e decisões aceitas |
| UX/UI | hierarquia, fluxo linear, acessibilidade e alterações indesejadas |
| Viewport | safe areas, teclado, fontes grandes, landscape/tablets, clipping/overlap |
| Natividade | SwiftUI Liquid iOS e Compose Flat Android, sem tela cross-platform |
| Tema | um azul de marca, restantes cores nativas e tema automático |
| Dados | privacidade, escopos pessoal/grupo, conflitos e rascunhos |
| Segurança | secrets, permissões de PR, third-party assets, efeitos de backend |
| Testes | registrar evidência executada, falhas, não aplicável e não testado |
| Conteúdo público | se mudou experiência de usuários, texto em linguagem simples |

Para trabalho apenas documental, **não alegar** compilação, validação em simuladores ou E2E. Classificar cada gate com evidência ou justificativa; **NÃO EXECUTADO não significa PASSOU**. Usar [QUALITY-GATES](QUALITY-GATES.md).

## 5. Entrega

- Descrever exatamente o que foi alterado e o que não foi.
- Comparar aceite do contrato com evidências rastreáveis.
- Criar ou atualizar PR (não mesclar automaticamente); checar links internos.
- Atualizar `docs/STATUS.md` e o último handoff; se marco mudou, atualizar `docs/ROADMAP.md`.
- Classificar necessidade de changelog e diferenciar **projeto em desenvolvimento** de **app já lançado**.

## 6. Próximo agent

Recebe link da branch/PR, SHA quando possível, documentos canônicos, decisões aceitas/pendentes, riscos, resultados de testes e **primeiro próximo passo**. Nenhuma indicação vaga como “continuar de onde parei”.

Modelos: [TASK-CONTRACT](TASK-CONTRACT.md), [HANDOFF](HANDOFF.md), [REVIEW-PROTOCOL](REVIEW-PROTOCOL.md).
