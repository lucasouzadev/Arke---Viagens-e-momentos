# HANDOFF — Continuidade entre agents

**Função:** protocolo e registro do **último handoff conhecido**. O progresso canônico de milestones fica em [STATUS](../STATUS.md); a ordem de execução fica em [ROADMAP](../ROADMAP.md). Esses três documentos têm responsabilidades distintas.

## Regras para qualquer handoff

Todo agent que encerrar uma tarefa, suspender por impedimento ou transferir responsabilidade precisa atualizar esta seção de execução na **mesma branch**:
1. Identidade: data, tarefa, branch, PR, último SHA verificado.
2. O que foi alterado **com caminhos e evidências**.
3. O que foi verificado de fato e o que **não** foi testado.
4. Qual decisão está aprovada, proposta ou bloqueada.
5. Riscos, pendências, arquivos sob edição concorrente e **próxima ação concreta**.
6. Atualização necessária em STATUS/ROADMAP/CHANGELOG; não deixar status conflitante.
7. Nenhum segredo, token, dado pessoal ou log sensível no handoff.

Registros históricos importantes devem ficar em comentários de PR ou arquivos de histórico próprios, não em cópias paralelas de STATUS. Este documento mantém **a passagem mais recente relevante**.

## Última passagem registrada — 27/10/2026

**De:** documentação de produto e design para M0 Agent Foundation.  
**Branch de integração documental:** `docs/design-004-ux-flows`  
**PR:** [#1](https://github.com/lucasouzadev/Arke---Viagens-e-momentos/pull/1) — aberto, sem merge confirmado.  
**Escopo:** documentação apenas; sem app, builds, CI, backend ou credenciais.

### Fonte de verdade encontrada

- ADR-001 a 008 aprovados como **direções**, não implementação; o ADR-008 não informa o nome de tratamento.
- DESIGN-004/005, GROUP-001, FINANCE-001, STAMPS e detalhes visuais seguem como **propostas**.
- Cor de marca: **um azul sólido**; tonalidade exata candidata, não aprovada. Tema automático por dispositivo.
- M0 deve substituir o ROADMAP existente por uma estrutura **única** em `docs/ROADMAP.md`; **não** criar `ROADMAP-V2.md`.
- M0 foi ampliado com **PROMPT-OBRIGATORIO / QUALITY-GATES / SAFEGUARDS / THREAT-MODEL** e quatro standards: arquitetura, acessibilidade, segurança e jurídico. São direções documentais, sem testes nativos ou certificação.
- Canário obrigatório foi solicitado para **toda resposta em chat**; o tratamento foi confirmado no chat e deve poder ser recuperado de preferências pessoais privadas da ferramenta. Nunca gravar o valor em código/artefatos; não presumir que contas distintas compartilhem configurações. Ver [CANARY](CANARY.md).
- M3 recebeu propostas de [modelo de dados](../arquitetura/M3-DATA-CONTRACT.md), [permissões](../arquitetura/PERMISSIONS.md) e [sync/offline](../arquitetura/SYNC-OFFLINE.md). Nenhum schema/backend implementado.

### Próximo passo após este PR

1. Revisar `AGENTS.md`, `docs/agents/PROMPT-OBRIGATORIO.md`, `QUALITY-GATES.md`, `SAFEGUARDS.md`, os quatro arquivos em `docs/standards/`, `docs/ROADMAP.md`, `docs/STATUS.md` e o restante dos protocolos no mesmo PR.
2. Revisar `CHANGELOG.md` como texto público de progresso, sem alegar release de app, e o contrato do modal futuro.
3. Confrontar diferenças entre main/branch; revisar e **só mesclar mediante aprovação**.
4. Depois da aprovação, selecionar primeira tarefa documental M0 aberta para execução, mantendo NATIVE/BUILD bloqueados.

### Verificações desta fase

Leitura e coerência de documentação/linkage; **sem compilação Swift/Kotlin, sem execução em iOS/Android, sem testes E2E ou publicação de aplicativo**.

> Ao concluir trabalho futuro, substituir esta seção pela passagem atualizada, mantendo os modelos e o link para a história do PR.
