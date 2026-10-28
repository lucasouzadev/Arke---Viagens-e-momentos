# Arke — Onde vamos?

**Um mapa, uma viagem, tudo no mesmo lugar.**

O Arke é um projeto aberto de planejamento de viagens solo e em grupo. Pins, roteiros, gastos, metas de economia, avaliações e memórias compõem uma única experiência centrada no mapa.

> **Estado atual:** projeto **documentation-first**. Não há app, backend, CI de build, distribuição ou integração financeira nesta entrega.

## Princípios aprovados

- **Uma tela principal e dois cartões**: mapa/Pins acima, navegação e conteúdo abaixo.
- **Sem tab bar tradicional:** relógio de cinco contextos dentro do segundo cartão.
- **Carrossel horizontal** finito de lugares; **scroll vertical** para atividades, detalhes e stamps.
- **Três posições do painel:** Explorar, Equilibrado e Detalhes.
- **Pins independentes de viagens**; uma Trip pode ser solo ou compartilhada.
- **iOS nativo em SwiftUI, Android nativo em Compose**, sem framework cross-platform para UI.
- **Uma única cor de marca:** azul opaco; fundos, superfícies, textos e aparência Light/Dark seguem o dispositivo. HEX candidato em [THEME-001](docs/brand/THEME-001.md).
- **Documentação antes do código**, até nova autorização.

## Novidades do projeto

Estamos organizando as funções de viagens, os dois cartões e como as informações serão apresentadas, antes de desenvolver o aplicativo. **Ainda não existe uma versão para instalar.**

Veja o [**CHANGELOG — Novidades do Arke**](CHANGELOG.md), escrito sem linguagem técnica. Quando houver aplicativo disponível, as novidades de cada versão também poderão aparecer em um modal dentro dele (ainda não implementado).

## Como o projeto é organizado

| O que você procura? | Documento |
| --- | --- |
| Plano principal | [ROADMAP](docs/ROADMAP.md) |
| Situação atual | [STATUS](docs/STATUS.md) |
| Instruções dos agents | [AGENTS.md](AGENTS.md) |
| Continuidade entre agents | [HANDOFF](docs/agents/HANDOFF.md) |
| Guia de alterações públicas | [CHANGELOG-GUIDE](docs/agents/CHANGELOG-GUIDE.md) |
| Futuro modal de novidades | [NEWS-MODAL](docs/releases/NEWS-MODAL.md) |
| Índice de todas as especificações | [Documentação](docs/INDEX.md) |
| Contratos de design | [DESIGN-001](docs/design/DESIGN-001.md) e [DESIGN-004](docs/design/DESIGN-004.md) |
| Marca e cor única | [BRAND-001](docs/brand/BRAND-001.md) e [THEME-001](docs/brand/THEME-001.md) |
| Segurança/qualidade | [QUALITY-001](docs/qualidade/QUALIDADE.md) |
| Decisões aceitas | [ADRs](docs/decisoes/README.md) |

Leia [CONTRIBUTING.md](CONTRIBUTING.md) e [OPEN_SOURCE.md](OPEN_SOURCE.md). Código e marca ainda não possuem licença final aprovada. Imagens e fontes externas não devem ser distribuídas sem autorização.

**Propostas novas não são decisões aceitas automaticamente.**
