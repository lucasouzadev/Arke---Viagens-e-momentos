# UX-001 — Estados vazios, erros, rascunhos e interrupções

**Status:** proposta funcional para revisão. Complementa [JORNADAS](JORNADAS.md).

## Matriz de estados da tela principal

| Situação | Cartão de mapa | Cartão inferior | Ação segura |
| --- | --- | --- | --- |
| Primeira abertura, sem viagem | mapa de exploração, sem Pin falso | convite “Marque um lugar” | criar Pin |
| Sem GPS permitido | permitir mover/pesquisar mapa | aviso não bloqueante | Pin manual |
| Pin provisório | realce distinto, não confundido com salvo | confirmação contextual | salvar/cancelar |
| Pins sem viagem | mostrar ideias | “Criar viagem com este Pin” | vincular sem perder ideia |
| Viagem vazia | destino/área da viagem ou mapa exploratório | orientação de primeiro lugar | adicionar Pin |
| Um único lugar | um Pin ativo | título central, sem vizinhos falsos | editar/consultar |
| Muitos lugares | múltiplos Pins legíveis | carrossel com vizinhos | selecionar |
| Carregando dados | mapa utilizável quando possível | skeleton breve com contexto | cancelar se apropriado |
| Offline | último conteúdo local se existir | indicador de conectividade | editar local com aviso claro |
| Falha ao salvar | não fingir sucesso | rascunho + ação Tentar novamente | repetir sem duplicar |
| Sem permissão de grupo | lugares autorizados apenas | conteúdo oculto com explicação | solicitar acesso |
| Foto quebrada | mapa intacto | fallback sem quebrar stamp | editar/remover mídia |

## Pin: máquina de criação conceitual

`idle → pending → editing → saving → saved`; de `pending/editing` pode ir para `cancelled` sem criar registro. Falha em `saving` leva a `failed` com dados recuperáveis. **Salvar nunca deve apagar rascunho antes de confirmação persistida.**

### Invariantes

- Cancelar Pin pendente não apaga Place existente, Pins antigos nem viagem.
- Pin salvo mas sem Trip permanece na coleção pessoal.
- Ação repetida (toque duplo/reenvio) não gera Pins duplicados.
- Mostrar confirmação após persistência, não no início da animação.
- Revisar se ação de remover de Trip deve ou não excluir Pin pessoal; padrão proposto: desvincular, não destruir.

## Editores e teclado

- Conteúdo é editado dentro do cartão expandido, salvo exceção de editor especializado.
- Teclado deve elevar ou ajustar conteúdo sem ocultar salvar/cancelar.
- Alternar contexto durante edição preserva drafts individualizados; se ação destrutiva for inevitável, perguntar antes.
- Fechamento por Voltar respeita ordem: primeiro teclado, depois overlay do relógio, depois edição; não sair da viagem por engano.
- Reabertura recupera rascunho quando permitido pela arquitetura de persistência.

## Relação mapa ↔ conteúdo

- Selecionar Pin preserva contexto atual. Se categoria não tiver registros do lugar, mostrar estado vazio daquela categoria, sem redirecionar sozinho a Planejamento.
- Alternar categoria não reposiciona mapa arbitrariamente.
- Trocar Trip com draft não salvo deve guardar versão isolada ou confirmar saída; jamais misturar edições entre Trips.

## Comunicação

Mensagens curtas, acionáveis, sem culpar usuário. Diferenciar “Não foi salvo” de “Salvo apenas neste dispositivo” e de “Compartilhado com o grupo”. Não criar badges de status supostos.

## Aceite para futura implementação

Cobrir todos os estados em iOS e Android com screenshots, testes por toque/teclado/leitor de tela, offline e repetição rápida. Usar [QUALITY-001](../qualidade/QUALIDADE.md) como gate.
