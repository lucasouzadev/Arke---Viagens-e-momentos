# DESIGN-003 — Identidade, plataformas e movimento

**Status:** princípios aprovados; métricas de tempo/geometry são hipóteses.

## Paleta de exploração (não final)

| Token | Cor | Aplicação |
| --- | --- | --- |
| Céu | #BCECF7 | mapa/ambiente claro |
| Profundo | #254C5D | texto e Pin selecionado |
| Papel | #FFFFFF | conteúdo principal |
| Neutro | #F2F5F6 | superfícies secundárias |
| Destaque | pendente | ações e estados |

Criar escala dark, alto contraste e tokens semânticos antes de padronizar.

## iOS — Liquid

Swift/SwiftUI + MapKit. **Liquid Glass dominante nos controles flutuantes**, relógio e chrome interativo, não sobre grandes áreas de texto. Transições com continuidade de origem, snapping e haptics discretos. Respeitar Reduce Motion.

## Android — Flat

Kotlin/Jetpack Compose; superfícies opacas, formas e contrastes claros; motion do Android e predictive back quando pertinente. **Não simular Liquid com blur decorativo.**

## Três posições do painel (proporções aproximadas)

| Estado | Mapa | Painel |
| --- | ---: | ---: |
| Explorar | 70% | 30% |
| Equilibrado (padrão) | 48% | 52% |
| Detalhes | 25% | 75% |

As alturas são adaptáveis à safe area, teclado, tablets, landscape e fonte ampliada. Usar fallback quando duas áreas mínimas não couberem.

## Motion

- Rápido, físico, interrompível, sem atrasar ações simples.
- Pin → lugar sem pulos duplos de câmera.
- Carrossel central com vizinhos parcialmente expostos.
- Relógio expande da própria ação.
- Puxador encaixa com feedback contido.
- Stamps podem ter movimento opcional, nunca obrigatório.
- Acessibilidade: remover/reduzir zoom e deslocamento em Reduce Motion/Remove Animations.

Cada ajuste visual exige auditoria [QUALITY-001](../qualidade/QUALIDADE.md).