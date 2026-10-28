# AGENTS.md — Regras centrais do Arke

Este arquivo é o ponto de entrada obrigatório para agents de documentação, design, iOS, Android, backend, revisão e CI. Não substitui as especificações; indica **onde encontrar a fonte de verdade** e o que pode ser alterado.

## 0. Comece sempre aqui

Antes de propor ou editar qualquer arquivo:
1. Leia [ROADMAP](docs/ROADMAP.md), [STATUS](docs/STATUS.md) e [HANDOFF](docs/agents/HANDOFF.md).
2. Consulte [o índice documental](docs/INDEX.md), [as decisões aceitas](docs/decisoes/README.md) e as especificações do escopo.
3. Siga [WORKFLOW](docs/agents/WORKFLOW.md), [TASK-CONTRACT](docs/agents/TASK-CONTRACT.md) e [REVIEW-PROTOCOL](docs/agents/REVIEW-PROTOCOL.md).
4. Se o trabalho afetar algo visível para pessoas, leia [CHANGELOG-GUIDE](docs/agents/CHANGELOG-GUIDE.md) e [CHANGELOG](CHANGELOG.md).

Se os documentos divergirem, registre o conflito; **não invente aprovação**. A autoridade é: decisão explícita registrada em ADR > requisito aceito em especificação > plano proposto. O STATUS informa andamento, **não redefine produto**.

## 1. Restrições de produto

- **Arke é map-first**: dois cartões na home (mapa acima; conteúdo/navegação dentro do cartão abaixo).
- **Sem tab bar convencional**, dashboard ou cinco pilhas de telas. Navegação pelo relógio de contextos; carrossel horizontal finito de lugares e conteúdo vertical independente.
- Planejamento, Gastos, Cofrinho, Avaliações e Memórias são contextos do mesmo cartão.
- Pins podem existir antes de viagens. Uma viagem pode ser individual ou em grupo.
- Uma única **cor de marca azul opaca**, HEX ainda candidato; demais superfícies, textos e modo claro/escuro seguem as APIs semânticas do dispositivo. [ADR-006](docs/decisoes/ADR-006.md).
- iOS: **Swift/SwiftUI** e Liquid Glass nativo nos controles. Android: **Kotlin/Jetpack Compose** e interface flat nativa. **Não usar React Native, Expo, Flutter ou camada híbrida como UI de produção**. [ADR-001](docs/decisoes/ADR-001.md).
- Cofrinho inicial é registro informativo de metas, não carteira, depósito ou transferência.
- Não supor permissões de grupo, privacidade, marca final ou provedor de mapas enquanto estiverem em aberto.

## 2. Estado atual e limites

**Fase documentation-first.** Não criar código de app, backend, pipelines executáveis, assinaturas, builds ou distribuir aplicativos até aprovação explícita de novo marco. Rascunho de especificação não é autorização para implementar.

**Não** fazer merge, promover branch, habilitar secrets, publicar release, executar migração ou excluir arquivos sem autorização para a ação. Em repositório público, nunca expor dados privados, tokens, keystores, certificados, segredos ou mídia de terceiros não autorizada.

Agents podem escrever documentação aprovada para o escopo do PR. Qualquer ambiguidade que altere arquitetura/experiência exige alternativa, riscos e pedido de decisão (ADR se aceito).

## 3. Protocolo de mudança

1. Receber um contrato de tarefa claro; se não houver, redigi-lo primeiro.
2. Confirmar dependências, decisões, permissões, riscos e arquivos autorizados.
3. Desenvolver em branch/PR, escopo pequeno. Não sobrepor alterações simultâneas de outros agents sem reconciliar.
4. Auditar, **em toda tarefa**: UX/UI, gestos, safe areas, overflow, teclado, acessibilidade, modo claro/escuro, localização, responsividade iOS/Android e impacto de backend/segurança; marcar **não aplicável com justificativa** quando realmente não houver UI/código.
5. Quando existir código, executar testes de unidades/integração, screenshots de múltiplas viewports e E2E (Maestro/XCUITest/Compose conforme acordado). **Nunca relatar teste não executado como aprovado.**
6. Atualizar [STATUS](docs/STATUS.md) e [HANDOFF](docs/agents/HANDOFF.md) com evidências, pendências e próximo passo; atualizar ROADMAP quando marco/tarefa mudar.
7. Se houver mudança **perceptível ao usuário**, propor texto leigo para [CHANGELOG](CHANGELOG.md) segundo o [guia editorial](docs/agents/CHANGELOG-GUIDE.md); só rotular como versão disponível quando houver release efetiva.
8. Publicar PR com checklist, links, riscos e evidências; não fazer merge por conta própria.

## 4. Definição de concluído

Uma tarefa termina somente com escopo/aceite atendidos, documentos e links coerentes, testes adequados (ou limite documentado), ausência de segredos/artefatos indevidos, STATUS/HANDOFF atualizados e PR disponível para revisão. **PR aberto não é merge; arquivo escrito não é funcionalidade entregue.**

## 5. Arquivos operacionais

| Pergunta | Fonte |
| --- | --- |
| O que vem depois? | [ROADMAP](docs/ROADMAP.md) |
| O que está acontecendo agora? | [STATUS](docs/STATUS.md) |
| Como retomar entre agents? | [HANDOFF](docs/agents/HANDOFF.md) |
| Como trabalhar e revisar? | [WORKFLOW](docs/agents/WORKFLOW.md) · [REVIEW-PROTOCOL](docs/agents/REVIEW-PROTOCOL.md) |
| Como especificar uma tarefa? | [TASK-CONTRACT](docs/agents/TASK-CONTRACT.md) |
| O que mudou para o público? | [CHANGELOG](CHANGELOG.md) · [CHANGELOG-GUIDE](docs/agents/CHANGELOG-GUIDE.md) |
| Como aparecerá no app? | [NEWS-MODAL](docs/releases/NEWS-MODAL.md) — futuro, não implementado |
