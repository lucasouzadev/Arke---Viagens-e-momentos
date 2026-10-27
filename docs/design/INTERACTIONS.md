# INTERACTIONS — Contrato de estado e eventos

**Proposta de engenharia, não API implementada.**

## Estado da home

- activeTripId: viagem ativa opcional
- activePlaceId: lugar ativo opcional
- activeContext: planning | expenses | savings | reviews | memories
- panelDetent: explore | balanced | details
- contextualWheelOpen: boolean
- mapViewport: câmera e bounds (conceituais)
- pendingPin: coordenada ainda não salva
- selectionSource: map | carousel | restored | search | none
- draftsByContext: rascunhos isolados
- scrollAnchorByContext: posição de cada área
- participantView: personal | shared (sujeito a permissão)

## Invariantes

1. Exatamente um contexto e um estado de painel.
2. Trocar categoria não apaga viagem, lugar, rascunho nem seleção.
3. Pin ativo alcançável pelo carrossel ou fallback contextual.
4. activeTripId vazio permite Pins soltos.
5. Scroll/câmera programáticos não geram evento redundante.
6. Fechar relógio devolve foco ao disparador.
7. Mudanças só eliminam rascunho com confirmação/regra explícita.

## Eventos

| Evento | Mudança | Preservação |
| --- | --- | --- |
| SelectMapPin(id) | seleciona lugar e alinha carrossel | contexto/painel |
| SelectCarouselPlace(id) | seleciona lugar e realça Pin | contexto/painel |
| SelectContext(ctx) | muda categoria e fecha relógio | lugar/viagem/rascunho |
| SetPanelDetent(d) | muda proporção | categoria/lugar |
| BeginPin(point) | define Pin pendente | Pins salvos |
| ConfirmPin | persiste Pin futuramente | vínculo opcional com viagem |
| CancelPin | cancela apenas pendência | Pins salvos |
| SelectTrip(id) | troca viagem e filtra lugares | visibilidade dos dados de terceiros |

Áreas de gesto: mapa=pan/zoom; puxador=detent; faixa de títulos=horizontal; corpo=vertical. Toda ação crítica deve possuir equivalente acessível por toque. Estados especiais: nenhuma viagem, viagem vazia, um lugar, offline, erro, sem permissão ou sem mídia.