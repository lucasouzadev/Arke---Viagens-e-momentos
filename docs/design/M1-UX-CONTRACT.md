# M1-UX-CONTRACT — Contrato de interface para iOS e Android

**Status:** especificação **proposta** de M1, não aprovada nem implementada. Não autoriza código.  
**Base aprovada:** [DESIGN-001](DESIGN-001.md), [DESIGN-002](DESIGN-002.md), [DESIGN-003](DESIGN-003.md), [ADR-002](../decisoes/ADR-002.md), [ADR-006](../decisoes/ADR-006.md).

## 1. Modelo único de interface

- **Home:** dois cartões contíguos; superior contém mapa/Pins; inferior contém seletor de contextos, carrossel finito de lugares e conteúdo vertical.
- **Contextos do relógio:** Planejamento, Gastos, Cofrinho, Avaliações, Memórias. Nunca criar tab bar convencional.
- **Detents:** Explorar, Equilibrado (inicial) e Detalhes; proporções de intenção e não tamanho rígido.
- **Pin antes de Trip:** lugar salvo não força criar viagem; associação posterior mantém dados.
- **Tema:** apenas um azul opaco de marca; superfícies, tipografia e claro/escuro seguem automaticamente o dispositivo.
- **Natividade:** mesmas capacidades iOS SwiftUI/MapKit (Liquid em controles) e Android Compose (flat); não exigir paridade visual literal.

## 2. Estados mínimos e matrizes

| Recurso | Estado feliz | Estados especiais obrigatórios |
| --- | --- | --- |
| Mapa | pan, zoom, Pin selecionado | sem GPS, offline, zero Pins, localização negada, provedor indisponível |
| Carrossel | Place ativo com vizinhos | zero/um/último, título longo, item excluído, swipe rápido |
| Relógio | abrir, escolher contexto e fechar | cancelar, fonte grande, TalkBack/VoiceOver, Reduce Motion |
| Puxador | três detents com snap | conflito com scroll, teclado, landscape/tablet, interrupção de drag |
| Planejamento | Pin → rascunho → salvar/vincular Trip | cancelar, falha, offline, toque duplo, retomada |
| Gastos | lista/edição de despesa informativa | moeda distinta, ausência de permissão, editar simultaneamente |
| Cofrinho | meta e progresso declarativo | meta zerada, privado por padrão, sem dinheiro real |
| Avaliações | nota/registro por lugar | nenhuma avaliação, foto faltante, texto longo |
| Memórias | stamp e lista vertical | sem foto, muitos stamps, mídia faltando, privacidade |
| Grupo | convidar e colaborar conforme papel | revogado, viewer, Trip solo, rascunhos pessoais |

## 3. Contratos de interação

| Origem | Evento | Resultado necessário | O que NÃO pode acontecer |
| --- | --- | --- | --- |
| Pin do mapa | `SelectMapPin` | carrossel alinha 1 vez | câmera/reseleção recursivas |
| Carrossel | `SelectCarouselPlace` | Pin ativa e câmera ajusta quando apropriado | múltiplos commits de seleção |
| Relógio | `SelectContext` | troca conteúdo preservando Trip/Place/drafts | abrir nova tab/nav stack |
| Puxador | `SetPanelDetent` | rearranjo fluido | scroll interno arrastar cartões |
| Pin pendente | `ConfirmPin` | persistir e confirmar somente após sucesso | falso “salvo” ou duplicata |
| Cancelar Pin | `CancelPin` | desfaz apenas pendência | apagar dados persistidos |
| Trocar Trip | `SelectTrip` | filtrar locais autorizados e isolar drafts | vazar dados pessoais de outra Trip |

Estados/eventos completos em [INTERACTIONS](INTERACTIONS.md); [DESIGN-004](DESIGN-004.md) detalha zonas e gestos; [UX-001](../produto/UX-001-ESTADOS.md) aborda falhas.

## 4. Estratégia sem gesto (não opcional)

Para cada gesto arrastar/girar/deslizar, o agente deve prever alternativa de toque/foco e leitor de tela: selecionar contexto em lista, ir ao lugar anterior/próximo, expandir/recolher conteúdo, pesquisar/selecionar local sem GPS. Sem gesto circular obrigatório. Orientação e semântica acessível são requisitos centrais.

## 5. Qualidade e viewport

- **iOS:** safe areas, Dynamic Type, VoiceOver, Voice Control, Reduce Motion/Transparency; teste dos materiais Liquid em mapa real.
- **Android:** insets e IME, fonte ampliada, TalkBack, back/gestos, superfície flat e displays adaptativos.
- **Ambas:** viewport compacta/padrão/tablet, landscape, temas nativos, texto 200%, teclado, nomes longos, imagens ausentes, rota/offline, ausência de overlaps e clipping.
- **Síncrono/offline:** garantir rascunhos e status reais, não simular dados remotos confirmados.
- **Segurança:** registro de local e fotos privado por padrão; autorização no backend futuro; sem permissão de GPS obrigatória.

## 6. Handoff de M1 para implementação futura

Um agente só poderá implementar este contrato após:
1. aprovação das decisões propostas (design/fornecedor de mapa/permissões);
2. autorização explícita para código;
3. tarefas M1 com [TASK-CONTRACT](../agents/TASK-CONTRACT.md);
4. passagem por [PROMPT-OBRIGATORIO](../agents/PROMPT-OBRIGATORIO.md), [QUALITY-GATES](../agents/QUALITY-GATES.md), [SAFEGUARDS](../agents/SAFEGUARDS.md) e [ACCESSIBILITY-UI](../standards/ACCESSIBILITY-UI.md);
5. demonstração por vídeos/screenshots, testes reais de interface e E2E por plataforma, falhas rastreadas;
6. atualização do STATUS/HANDOFF/CHANGELOG segundo evidências, sem declarar release antecipadamente.

Este documento é uma **base de aceite para os agents**, não design final pixel-perfect ou garantia de conformidade legal.
