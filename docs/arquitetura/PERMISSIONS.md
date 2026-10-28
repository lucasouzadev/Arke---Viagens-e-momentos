# PERMISSIONS — Matriz de autorização e compartilhamento

**Status:** proposta M3. Esta matriz não atribui papéis no sistema nem habilita compartilhamento. Papéis `owner/editor/viewer` ainda requerem aprovação.

## 1. Princípio de decisão

**Negar por padrão.** Para cada acesso futuro, avaliar **identidade autenticada + objeto + ação + Trip + Membership ativo + visibilidade do item + autoria/ownership + condições da operação**. O servidor deve garantir essas condições em operações e downloads, não só na UI.

## 2. Tipos de informação

| Tipo | Privacidade inicial | Mudança permitida proposta |
| --- | --- | --- |
| Pin pessoal | pessoal | vincular à Trip com compartilhamento explícito |
| Trip/atividade | compartilhada somente aos membros autorizados | editar conforme papel |
| Expense | pessoal ou compartilhado por escolha expressa | membros veem apenas parcela autorizada |
| SavingsEntry individual | **pessoal**, mesmo em Trip grupo | compartilhar só por opt-in informado |
| SavingsGoal | pessoal por padrão | meta conjunta opcional e explícita |
| Review/Stamp/Photo | pessoal | compartilhar registro específico, não álbum inteiro |
| Convite | token restrito ao destinatário/escopo | revogar e expirar |
| Coordenadas ao vivo | **não coletadas por padrão** | exige novo escopo/decisão/avaliação |

## 3. Papéis propostos por ação (NÃO APROVADOS)

| Ação em dado tripShared | Owner | Editor | Viewer |
| --- | --- | --- | --- |
| Consultar roteiro compartilhado | permitir | permitir | permitir |
| Criar/editar Pin ou atividade compartilhada | permitir | permitir | negar |
| Convidar | permitir | **decidir** | negar |
| Alterar papéis/excluir Trip | permitir, com salvaguardas | negar | negar |
| Ver entrada pessoal de cofrinho alheio | **negar** | **negar** | **negar** |
| Ver gastos compartilhados | permitir | permitir | permitir conforme escopo |
| Alterar registro de terceiro | **decidir por tipo/escopo** | **decidir por tipo/escopo** | negar |
| Exportar dados pessoais de terceiros | negar | negar | negar |

**Owner da viagem não é owner dos dados pessoais dos outros participantes.**

## 4. Casos obrigatórios de teste futuro

1. IDOR/BOLA: usar ID de Pin/Trip/Attachment de terceiro deve ser negado, inclusive download direto.
2. Um Viewer não pode editar via API mesmo que modifique payload.
3. Revogação do participante bloqueia novas requisições, convites antigos, rotas de mídia e deep links.
4. Expiração/uso único de convite, escopo de Trip e proteção contra enumeração são regras a aprovar.
5. Pin que foi pessoal não se torna compartilhado implicitamente por vínculo.
6. Alterações em andamento quando revogação acontece: proteger dados e informar estado pendente, sem gravar em Trip sem acesso.
7. Offline: não prometer remoção retroativa de cópia já sincronizada; definir limites de cache e retenção, respeitando lei/política.
8. Não revelar se um objeto privado existe por diferenças de resposta (autorização/enumeração).
9. Transferir propriedade da Trip requer consenso/política e trilha auditável.

## 5. Perguntas que bloqueiam backend

Autenticação, papel inicial, política de convites, limites de autor/editor, revogação de cache, direitos de exportação/exclusão e trilha de auditoria. Até aprovação, **não escrever regras de autorização produtivas**.

Relacionados: [GROUP-001](../produto/GROUP-001.md), [PRIVACIDADE](PRIVACIDADE.md), [SECURITY-PRIVACY](../standards/SECURITY-PRIVACY.md).
