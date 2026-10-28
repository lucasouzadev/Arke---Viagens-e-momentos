# DOMINIO — Entidades conceituais

**Não é um schema SQL ou contrato de API.**

| Entidade | Papel |
| --- | --- |
| User | identidade/titular de registros |
| Place | lugar ou ponto geográfico |
| Pin | referência salva no mapa, com viagem opcional |
| Trip | unidade de planejamento com título, datas opcionais e membros |
| Membership | vínculo User↔Trip, papel e permissões |
| PlanItem | atividade ou trecho opcionalmente ligado a Place |
| Expense | despesa prevista/realizada, moeda, responsável, rateio |
| SavingsGoal | meta informativa pessoal ou compartilhada |
| SavingsEntry | contribuição declarada, não transferência financeira |
| Review | opinião/nota e mídia de um lugar |
| MemoryStamp | registro visual de visita |
| Attachment | imagem, URL, nota ou arquivo com titular e permissões |

## Invariantes

- Um Trip pode ter 1..N participantes. Solo e grupo são a mesma entidade.
- Pin pode existir sem Trip; um Place pode se repetir em vários Pins/viagens.
- Expense e SavingsEntry não provam pagamento ou custódia.
- Review e MemoryStamp são independentes e podem estar associados ao mesmo Place.
- Cada registro precisa de autor, propriedade e visibilidade.
- Remoção de membro exige regra de acesso, exclusão e retenção.
- Fusos horários e moedas não devem ser convertidos silenciosamente.

## Papéis sugeridos (não aprovados)

owner / editor / viewer. Permissões granulares de custos, memórias, convites e exclusão ainda precisam de decisão.

## Futuro
## Detalhamento proposto em M3

A separação Pin/Place/Trip, `TripPinLink` candidato, isolamento pessoal/grupo, revisões e idempotência foi aprofundada em [M3-DATA-CONTRACT](M3-DATA-CONTRACT.md). Para controles por entidade veja [PERMISSIONS](PERMISSIONS.md); para mutações offline, [SYNC-OFFLINE](SYNC-OFFLINE.md). Essas propostas **não são schema/APIs aprovadas**.


Estado de interface não é banco de dados. Sincronização exige versionamento, conflitos, isolamento por viagem e idempotência.