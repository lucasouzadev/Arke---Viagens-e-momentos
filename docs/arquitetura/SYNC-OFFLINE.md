# SYNC-OFFLINE — Persistência, conflitos e retomada

**Status:** proposta M3, sem escolha de backend ou sync engine. O Arke prioriza **integridade e explicação honesta ao usuário** acima de “parecer instantaneamente sincronizado”.

## 1. Estados separados

- `editing`: alteração local não confirmada pelo armazenamento durável.
- `savedLocal`: gravada no aparelho (sem implicar que chegou ao grupo).
- `pendingSync`: está na fila de sincronização.
- `synced`: confirmação do serviço autoritativo.
- `conflict`: atualização simultânea necessita resolução.
- `failed`: falha persistente; dado e ação de retry preservados.
- `revoked`: permissão removida; não permitir nova escrita remota.

A interface deve distinguir esses estados com texto adequado e leitores de tela; não trocar por “salvo” ambíguo.

## 2. Intenção e operação

Cada mutação futura deve possuir `operationId` estável e deduplicável, `actorId`, `entityId`, `baseRevision`, `timestamp`, `scope` e payload validado. Forma exata e contrato API permanecem pendentes.

- Repetir envio da mesma operação não duplica Pins, expenses, saves ou stamps.
- Estado privado/sync é separado por usuário e Trip; não vazar drafts em usuário logado diferente no device.
- Ao alternar usuário/Trip, parar fila inadequada; respeitar autorização atual do servidor antes de reenvio.
- Não aplicar otimisticamente operações **irreversíveis** como exclusão geral sem reversão/confirm.
- Mensagem “compartilhado” só após autorização e confirmação adequadas.

## 3. Resolução de conflitos proposta por tipo

| Entidade | Estratégia proposta | Nunca fazer |
| --- | --- | --- |
| Carrossel/contexto/detent | local efêmero, sem sincronizar | servidor sobrescrever gesto do usuário |
| Draft | local/por user+Trip+contexto, recuperação e retenção definidas | publicar texto incompleto ao grupo |
| Pin/TripPinLink | revisão com merge apenas de campos não conflitantes | apagar vínculo ou Pin com cascade não revisada |
| PlanItem | conflitos com autoria e compare-and-swap | perder edição de terceiro sem aviso |
| Expense/SavingsEntry | correção auditável, usuário resolve conflito | last-write-wins silencioso em valores |
| Review/Stamp | revisão com história e permissão por objeto | compartilhar foto privada por sincronização |
| Membership/Invitation | backend autoritativo e revogação imediata de novas ações | cache conceder acesso novo |

## 4. UX de erro, rede e recuperação

| Situação | Comportamento |
| --- | --- |
| Sem rede | mostrar conteúdo local autorizado e indicador “no dispositivo” |
| Reconexão | fila em ordem/estratégia definida, retries com backoff, sem duplicar |
| Falha de permissão | não reapresentar como “aguardando”; preservar draft privado, informar limitação |
| Conflito de edição | apresentar diferença e decisão, especialmente valores/roteiro |
| Falha do app/teclado | recuperar draft durable já salvo sem fingir sync |
| Foto ausente | metadados e texto continuam visíveis; mídia reenvia conforme direitos |
| Mudança de contas | limpar contexto e caches privados conforme política, sem entregar dados de outra conta |

## 5. Infraestrutura futura

Selecionar estratégia local-first ou offline-first, backend, política de retention/backup e proteção de fila **somente depois de revisar entidades e ameaças**. Evitar prometer offline de mapas quando só há offline de registros de viagem. Planejar migrações forward/backward e testes de restauração e rollback.

## 6. Matriz de validação futura

- Reiniciar app durante pendingSync preserva operação/draft.
- Duas edições simultâneas em Expense nunca perdem dinheiro declarado silenciosamente.
- Usuário removido do grupo não consegue nova escrita, mesmo com fila offline antiga.
- Retry e timeout criam **um** Pin/Expense/Stamp.
- Troca de conta não mostra Trip anterior nem seus registros pessoais.
- Reconciliar data/hora/moeda sem transformação invisível.
- Retenção/exclusão reais dependem de política e observabilidade e teste com dados sintéticos.

Leia [QUALITY-GATES](../agents/QUALITY-GATES.md), [PERMISSIONS](PERMISSIONS.md), [M3-DATA-CONTRACT](M3-DATA-CONTRACT.md) e [SAFEGUARDS](../agents/SAFEGUARDS.md).
