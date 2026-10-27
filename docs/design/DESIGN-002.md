# DESIGN-002 — Relógio, carrossel e sincronização

**Status:** comportamento conceitual aprovado; física final a validar.

## Três eixos

| Controle | Significado | Resultado |
| --- | --- | --- |
| Relógio contextual | O que quero organizar? | troca Planejamento, Gastos, Cofrinho, Avaliações, Memórias |
| Carrossel horizontal | Sobre qual lugar? | seleciona lugar, realça Pin |
| Scroll vertical interno | O que há neste contexto? | mostra listas, stamps, edições |
| Puxador | Quanto mapa quero ver? | alterna Explorar, Equilibrado, Detalhes |

## Relógio

- Abre pelo botão no canto superior direito do cartão inferior.
- Seleção por **toque** é mandatória; arrasto radial e haptics são opcionais.
- Fecha ao escolher, cancelar ou tocar fora. Retorna foco ao botão disparador.
- Preserva viagem, lugar, rascunhos e scroll individual de cada categoria.
- Nenhuma barra externa de seções.

## Carrossel

- Lugar atual central, vizinhos visíveis em menor ênfase, snapping.
- **Não usar loop infinito por padrão**: limites da lista devem ser compreensíveis.
- Um único lugar não sugere falsamente que há vizinhos.
- Seleção de Pin move o carrossel; seleção no carrossel destaca Pin.
- Uma mudança programática de câmera ou scroll não dispara re-seleção em loop.
- IDs estáveis, ações idempotentes, nomes grandes/longos e estados vazios.

## Gestos

Mapa: pan/zoom/toque; carrossel: horizontal; conteúdo: vertical; puxador: vertical exclusivo; relógio: toque/foco. Sempre oferecer anterior/próximo, expandir/recolher e lista de contextos sem gesto para acessibilidade.