# Arke — Onde vamos?

**Um mapa, uma viagem, tudo no mesmo lugar.**

O Arke é um projeto open source de planejamento de viagens solo e em grupo. A proposta é reunir Pins, roteiros, gastos, metas de economia, avaliações e memórias em uma única interface espacial.

**Estado em 27/10/2026:** documentação de produto e design. Não há app publicado, backend, workflows de CI, integrações financeiras ou builds distribuídos.

## Princípios aprovados

- **Uma tela, dois cartões:** mapa/Pins acima; conteúdo e navegação contextual abaixo.
- **Sem barra de navegação inferior:** cinco categorias por um relógio/seletor dentro do cartão inferior.
- **Carrossel horizontal** para lugares, com anterior/próximo parcialmente visíveis; **rolagem vertical** para conteúdo e stamps.
- **Três posições:** Explorar, Equilibrado, Detalhes; puxador exclusivo redimensiona os cartões.
- **Pins podem existir antes das viagens**; viagem solo pode se tornar colaborativa.
- **UI nativa independente:** Swift/SwiftUI com Liquid Glass nos controles iOS; Kotlin/Compose flat no Android.
- **Documentation-first:** não iniciar código de produção sem novo marco aprovado.

## Índice

| Área | Documento |
| --- | --- |
| Status e navegação | [Índice documental](docs/INDEX.md) |
| Propósito | [Visão](docs/produto/VISAO.md) |
| Cinco contextos | [Escopo](docs/produto/ESCOPO.md) |
| Uso individual e coletivo | [Jornadas](docs/produto/JORNADAS.md) |
| Dois cartões | [DESIGN-001](docs/design/DESIGN-001.md) |
| Relógio, carrossel e mapa | [DESIGN-002](docs/design/DESIGN-002.md) |
| Linguagem e movimento | [DESIGN-003](docs/design/DESIGN-003.md) |
| Contratos de interface | [INTERACTIONS](docs/design/INTERACTIONS.md) |
| Plano técnico nativo | [Arquitetura](docs/arquitetura/ESTRATEGIA-NATIVA.md) |
| Entidades | [Domínio](docs/arquitetura/DOMINIO.md) |
| Segurança | [Privacidade](docs/arquitetura/PRIVACIDADE.md) |
| Auditoria e testes | [QUALIDADE](docs/qualidade/QUALIDADE.md) |
| Distribuição futura | [BUILD-001](docs/engenharia/DISTRIBUICAO.md) |
| Etapas | [Roadmap](docs/ROADMAP.md) |
| Decisões pendentes | [Questões abertas](docs/OPEN-QUESTIONS.md) |
| Decisões registradas | [ADRs](docs/decisoes/README.md) |

Leia [CONTRIBUTING.md](CONTRIBUTING.md) e [OPEN_SOURCE.md](OPEN_SOURCE.md). **A licença final ainda está em discussão; publicidade do repositório não significa licença irrestrita.** A imagem externa usada como referência não é reproduzida aqui.