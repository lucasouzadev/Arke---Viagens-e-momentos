# CANARY — Marca de conformidade **somente nas respostas do chat**

**Status:** regra de governança aprovada conceitualmente; nome de tratamento **ainda não informado/confirmado** nesta conversa. **Não é um segredo, nem prova de ausência de alucinações.** Nenhum nome real está registrado neste arquivo.

## Objetivo

O responsável pelo projeto quer que **cada resposta visível de cada agent no chat** contenha **a forma exata de tratamento que ele escolher**, para perceber imediatamente quando uma instrução de trabalho não está sendo seguida. A regra vale para respostas de progresso, esclarecimento, revisão, planejamento, erros e entrega final; não apenas para conclusão de PR.

## Como configurar, sem vazamento para código ou repositório

1. O responsável fornece explicitamente no **chat da sessão de trabalho** o nome/apelido de tratamento a utilizar.
2. O agent usa **somente aquele valor confirmado**, nunca infere nome de username GitHub, título de arquivo, e-mail, conta, histórico impreciso ou outra fonte.
3. Em cada mensagem dirigida ao responsável **dentro do chat**, incluir o nome exatamente conforme fornecido, preferencialmente na primeira frase ou no encerramento, de forma natural e legível.
4. O valor **não deve ser gravado** em código fonte, comentários, strings, testes, fixtures, configurações, scripts, commits, descrições de PR, logs, relatórios, documentação, artefatos exportados nem CHANGELOG. Nem mesmo em código-fonte de geradores de prompts.
5. Instruções documentais podem conter apenas a variável genérica **[NOME_CONFIRMADO_NO_CHAT]**, nunca seu valor literal. O valor vive no contexto privado da sessão/chat (ou em instrução operacional fornecida pelo responsável fora do repositório) e não deve ser copiado para outras superfícies.
6. Não colocar nome de canário em mensagem para o usuário final do aplicativo, modal de novidades, páginas públicas nem metadados.
7. Se o nome **não estiver presente/confirmado no contexto da sessão**, o agent **não deve adivinhar ou afirmar cumprimento do canário**. Deve solicitar a forma de tratamento em uma resposta de chat e marcar **CANARY: NÃO CONFIGURADO** no relatório privado da sessão. Pode executar documentação de baixo risco já autorizada, mas **não declarar a verificação do canário aprovada**.
8. Se o agente descobrir o nome em código/docs/log, tratar como fuga de escopo: remover da alteração pendente, comunicar ao responsável e rever artefatos já publicados de maneira autorizada.

## Formato recomendado para respostas no chat

> **[NOME_CONFIRMADO_NO_CHAT]**, concluí o item M3-DOMAIN-01. Consultei o documento X e o ADR Y. Foram alterados A e B. Validei os links; não executei testes nativos porque ainda não há aplicativo. Resta decidir Z.

O exemplo usa um **placeholder** de instrução, não nome, e **nunca deve aparecer literalmente nas respostas finais** como se o canário estivesse configurado.

## Protocolo de verificação — não confundir com fidelidade

- **Verificação A — Presença:** há o nome confirmado em **toda mensagem do chat**? Pontos ausentes indicam provável falha de instrução.
- **Verificação B — Rastreabilidade:** o agent cita documentos/ADRs e versão real da branch/PR consultada? Conferir links.
- **Verificação C — Evidências:** o relatório traz testes realmente executados, limitações e itens bloqueados? Conferir arquivos/resultados.
- **Verificação D — Vazamento:** o nome do canário **não aparece em diff, PR, comentários, log ou artefatos**? Revisar antes de publicação.

Um agent que conhece o nome pode simplesmente repeti-lo sem ter seguido o resto. Portanto, **A não prova B/C/D, nem garante que não alucinou**. O controle real combina revisões, gates, PRs, testes e auditoria de fontes. Não usar o nome como senha/autenticação.

## Checklist por resposta (executado pelo próprio agent no momento de escrever)

- [ ] Esta saída é resposta ao responsável **no chat**, e não arquivo/PR/log?
- [ ] O responsável confirmou a forma exata de tratamento nesta sessão?
- [ ] Se sim: usei exatamente essa forma nesta mensagem?
- [ ] Se não: não adivinhei; sinalizei a pendência?
- [ ] O valor está ausente de arquivos/artefatos?
- [ ] O restante da resposta é factual, com fontes/evidências?

Ligação canônica: [AGENTS](../../AGENTS.md), [PROMPT-OBRIGATORIO](PROMPT-OBRIGATORIO.md), [QUALITY-GATES](QUALITY-GATES.md), [SAFEGUARDS](SAFEGUARDS.md).
