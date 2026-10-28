# STATUS — Estado verificável do Arke

**Atualizado em:** 27/10/2026. **Documento de controle** (não substitui decisões em ADR nem planejamento em ROADMAP).

## Visão rápida

- **Fase:** documentação antes de implementação ([ADR-005](decisoes/ADR-005.md)).
- **Branch de trabalho documental:** `docs/design-004-ux-flows`.
- **Revisão remota:** [PR #1](https://github.com/lucasouzadev/Arke---Viagens-e-momentos/pull/1), aberto; merge **não confirmado**.
- **Código nativo de app:** não iniciado neste repositório.
- **CI, TestFlight, APK, backend e deploy:** não configurados nesta fase.
- **Decisões aceitas:** duas bases nativas, dois cartões, Pin independente, Cofrinho informativo, documentation-first, uma cor azul opaca e tema do dispositivo.
- **Ainda propostas:** física detalhada, identidade final, stamps, grupos, finanças, permissões, fornecedor de mapa, modelo de dados final.
- **Governança M0 em revisão:** [prompt universal](agents/PROMPT-OBRIGATORIO.md), [gates de qualidade](agents/QUALITY-GATES.md), [salvaguardas](agents/SAFEGUARDS.md), [modelo de risco](agents/THREAT-MODEL.md), arquitetura, acessibilidade, segurança e jurídico.
- **Canário:** tratamento confirmado no chat; literal **não armazenado** no GitHub. O padrão pode ser levado a futuras sessões pelas preferências pessoais de cada agent, sob controle do responsável; não é possível validar perfis externos apenas pelo repositório.
- **Verificações reais do conjunto M0:** texto, coerência de links e escopo documental; nenhum teste de segurança real, conformidade jurídica ou app nativo foi executado.

## Milestones — status, não previsão

| Marco | Estado | Evidência / restrição |
| --- | --- | --- |
| M0 — governança agents e documentação | **em revisão** | `AGENTS.md`, ROADMAP unificado, workflow, handoff/status e changelog propostos neste PR |
| M0 — baselines interdisciplinares | **em revisão** | prompt obrigatório, G-01..G-15, threat model, arquitetura, acessibilidade, segurança e jurídico na mesma branch |
| M1 — contratos de UI | **planejado** | DESIGN-001/002/003 aprovados em conceito; DESIGN-004/005 propostos |
| M2 — arquitetura nativa | **planejado** | direções SwiftUI/Compose documentadas; sem código |
| M3 — domínio de viagens | **planejado** | entidades, grupo e finanças em proposta |
| M3 — contratos de dados (propostos) | **em revisão documental** | Pin/Place/Trip, permissão granular e sync/offline especificados; nenhum backend ativo |
| M4 — qualidade/distribuição | **planejado** | quality-gates especificados; sem workflows executáveis |
| M5 — implementação | **bloqueado** | requer autorização explícita, contratos e ferramentas escolhidos |

## Próxima decisão necessária

Revisar o **pacote documental M0** e o conteúdo aberto no [PR #1](https://github.com/lucasouzadev/Arke---Viagens-e-momentos/pull/1). **Não** declarar aprovado todo conteúdo do PR pelo simples fato de M0 ter sido solicitado.

## Impedimentos

- Identidade gráfica e HEX definitivo de azul por validar.
- Participantes e políticas de compartilhamento não definidos.
- Mapa Android/provedor, offline e sync não decididos.
- App não deve ser iniciado ainda.
- Atualizações públicas de app só após release verificável.

## Auditoria da última mudança

Revisão documental e verificação de links internos são aplicáveis. Testes de interface, simulador, Maestro/E2E, segurança operacional de builds e publicação de releases **não foram executados**. Ver [HANDOFF](agents/HANDOFF.md).

**Manutenção:** o agent que avançar um milestone ou fizer handoff deve atualizar esta página na mesma alteração, com fatos e links — nunca estados otimistas.
