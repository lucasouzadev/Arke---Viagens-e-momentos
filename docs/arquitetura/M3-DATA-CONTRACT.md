# M3-DATA-CONTRACT — Domínio e isolamento de dados

**Status:** proposta técnica M3 para futura decisão. **Não é API, schema SQL ou autorização de backend.** Base: [DOMINIO](DOMINIO.md), [GROUP-001](../produto/GROUP-001.md), [FINANCE-001](../produto/FINANCE-001.md), [PRIVACIDADE](PRIVACIDADE.md).

## 1. Invariantes antes de entidades

- **Pin e Place não são sinônimos.** Place referencia um lugar; Pin registra a seleção/salvamento da pessoa. Trip agrupa Pins/atividades sem apropriar-se automaticamente de um Pin pessoal.
- **Trip solo e Trip colaborativa têm a mesma estrutura**. Um membro atual não garante compartilhamento de todo dado ligado à viagem.
- **Toda entidade privada precisa de titular, escopo, autoria, timestamps e política de exclusão/retenção** quando aplicável.
- **Autorização é verificada no servidor** para cada acesso/escrita quando existir backend; ocultar botões não é segurança.
- **Ausência de rede não equivale a sincronização**. Alterações locais têm status claro e podem ser desfeitas/reconciliadas.
- **Cofrinho é declarativo**, sem custódia, depósito ou transferência. Expense e SavingsEntry são objetos diferentes.
- Metadados de viagem e horários não autorizam rastreamento GPS; mídia exige avaliação de EXIF e direitos de terceiros.

## 2. Agregados e vínculos conceituais

| Núcleo | Entidades | Limite de consistência sugerido |
| --- | --- | --- |
| Identidade | User, Membership, Invitation | relação e permissão verificáveis |
| Geografia | Place, Pin, TripPinLink | Place pode se repetir; não duplica Pin pessoal |
| Viagem | Trip, PlanItem | título, datas opcionais, fuso, autoria |
| Finanças | Expense, ExpenseShare, SavingsGoal, SavingsEntry | moeda/status declarativo, histórico de correções |
| Memórias | Review, MemoryStamp, Attachment | visibilidade por registro, direitos de mídia |
| Sincronização futura | Mutation, Revision, Tombstone | operação idempotente e auditável |

**Proposta nova — `TripPinLink`** (requer aprovação): associação entre Pin salvo e uma Trip, com autor e visibilidade própria. Desvincular da Trip não deve apagar o Pin pessoal por efeito colateral.

## 3. Campos gerais sugeridos (não contrato final)

`id` estável; `ownerId`; `createdAt`; `updatedAt`; `revision`; `visibility`; `deletedAt?` (se política de soft delete aprovada); `tripId?` somente quando fizer sentido; `createdBy`; `lastModifiedBy`. O propósito dos campos precede a escolha de banco.

Visibilidade candidata: `personal`, `tripShared`; `selectedMembers` **não aprovada**. A existência de `tripId` por si só **não muda visibilidade**.

## 4. Ciclos de vida e riscos

| Evento | Invariante | Erro proibido |
| --- | --- | --- |
| Salvar Pin solto | persiste em coleção pessoal | criar Trip sem consentimento |
| Vincular Pin a Trip | mantém owner, ajusta vínculo | tornar público por estar na Trip |
| Desvincular | remove vínculo específico | apagar Pin pessoal sem pedir |
| Excluir Pin | verificar ligações e escopo | cascade não revisada que apaga memórias |
| Convidar pessoa | token escopado, aprovação explícita | divulgar rota pessoal indiscriminadamente |
| Remover membro | bloquear novas leituras/escritas | deixar mídia privada acessível por URL antiga |
| Editar gasto em grupo | moeda/status/autoria revisáveis | sobrescrever valor concorrente silenciosamente |
| Registrar stamp | privado inicialmente | publicar GPS EXIF sem aviso |
| Salvar offline | operação pendente idempotente | mostrar “sincronizado” sem ack |

## 5. Contratos de dados que agents devem demonstrar

- Isolamento: usuário A não consulta/modifica item pessoal de B, mesmo sabendo ID.
- Vínculo: item pessoal não se torna compartilhado pela mera presença na viagem.
- Concorrência: revision/ETag/conflito específico por entidade; falhas preservam o valor anterior.
- Cancelamento e retry: mesmo `operationId` não cria registro duplicado.
- Deleção/revogação: media/cache/tokens/backups e retenção explicados ao titular.
- Datas/moedas: fuso local explícito, código de moeda e taxas com origem/instante documentados; sem soma de moedas diferentes.

## 6. Falhas e aprovação pendente

Autenticação/guest, owner/editor/viewer, provedor de mapas, retenção, política de exclusão, transações, sincronização e moeda-base ainda exigem decisão. Testes reais de banco e segurança **não executados** nesta fase.

Ver também [PERMISSIONS](PERMISSIONS.md), [SYNC-OFFLINE](SYNC-OFFLINE.md), [THREAT-MODEL](../agents/THREAT-MODEL.md), [LEGAL-COMPLIANCE](../standards/LEGAL-COMPLIANCE.md).
