# Arke — Onde vamos?

**Um mapa, uma viagem, tudo no mesmo lugar.**

O Arke é um projeto open source de planejamento de viagens solo e em grupo. A proposta reúne Pins, roteiros, gastos, metas de economia, avaliações e memórias em uma única interface espacial.

> **Estado do projeto:** documentação de produto e design. A etapa **DOCS-002** está em revisão. Não há app publicado, backend, workflows de CI, integrações financeiras nem builds distribuídos.

## Princípios aprovados

- **Uma tela, dois cartões:** mapa e Pins no superior; navegação contextual e conteúdo no inferior.
- **Sem tab bar:** cinco contextos selecionados por um relógio dentro do segundo cartão.
- **Carrossel horizontal** de lugares, com anterior/próximo parcialmente visíveis; **scroll vertical** para explorar registros e stamps.
- **Três posições** do painel inferior: Explorar, Equilibrado e Detalhes.
- **Pins podem existir antes de viagens**; a mesma viagem pode ser individual ou compartilhada.
- **UI nativa independente**: Swift/SwiftUI (Liquid nos controles) e Kotlin/Compose (flat no Android).
- **Documentation-first:** nada de código de produção sem nova autorização.

## Comece aqui

Consulte o [índice integral da documentação](docs/INDEX.md).

| Tema | Documento |
| --- | --- |
| Visão de produto | [Visão](docs/produto/VISAO.md) |
| Dois cartões aprovados | [DESIGN-001](docs/design/DESIGN-001.md) |
| Relógio e carrossel aprovados | [DESIGN-002](docs/design/DESIGN-002.md) |
| Linguagem iOS/Android | [DESIGN-003](docs/design/DESIGN-003.md) |
| **Proposta de física e gestos** | [DESIGN-004](docs/design/DESIGN-004.md) |
| **Proposta de sistema visual** | [DESIGN-005](docs/design/DESIGN-005.md) |
| **Estados vazios e rascunhos** | [UX-001](docs/produto/UX-001-ESTADOS.md) |
| **Colaboração** | [GROUP-001](docs/produto/GROUP-001.md) |
| **Gastos e Cofrinho** | [FINANCE-001](docs/produto/FINANCE-001.md) |
| Testes futuros | [QUALITY-001](docs/qualidade/QUALIDADE.md) · [QUALITY-002](docs/qualidade/MATRIZ-UX-002.md) |
| Fases | [Roadmap](docs/ROADMAP.md) |

Leia [CONTRIBUTING.md](CONTRIBUTING.md) e [OPEN_SOURCE.md](OPEN_SOURCE.md). A licença definitiva ainda será escolhida e imagens externas de referência não devem ser redistribuídas sem autorização.

**A palavra “proposta” importa:** os documentos novos não aprovam automaticamente papéis de grupo, sistema financeiro, paleta ou animações.
