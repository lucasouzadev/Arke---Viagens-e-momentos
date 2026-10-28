# DESIGN-005 — Sistema visual adaptativo iOS / Android

**Status:** proposta para revisão. Não substitui a direção já aprovada em [DESIGN-003](DESIGN-003.md). Nenhum arquivo de fonte ou imagem externa é redistribuído.

**Aprofundamento:** a definição detalhada da proposta de marca, paleta Light/Dark, stamps, diferenças de plataformas e critérios de aceite está centralizada no [índice BRAND-001](../brand/README.md). Evitar criar uma segunda fonte conflitante para os tokens.

## Identidade conjunta

Arke deve ser reconhecível **pela composição de dois cartões, relação mapa/conteúdo, linguagem de viagens e stamps**, não por copiar pixels entre plataformas. A segunda plataforma não é uma conversão automática da primeira.

### Papéis visuais

| Papel semântico | Uso | Observação |
| --- | --- | --- |
| canvas | fundo da tela | não deve competir com o mapa |
| mapSurface | cartão superior | usa mapa real quando disponível |
| contentSurface | cartão inferior | alto contraste e rolagem fluida |
| chromeSurface | botão de relógio, ferramentas | iOS glass; Android opaco |
| primaryText | títulos e ação atual | legível em claro/escuro |
| secondaryText | descrição/metadata | contraste suficiente |
| selectedPlace | Pin e título selecionados | reforçar com escala/forma |
| accent | ações primárias | ver THEME-001, ainda proposto |
| status | erro/sucesso/atenção | nunca depender somente de cor |

### Cores experimentais, NÃO finais

- Sky: `#BCECF7` — atmosfera da referência.
- Deep: `#254C5D` — contraste no mapa claro.
- Paper: `#FFFFFF` — cartão de conteúdo.
- Mist: `#F2F5F6` — camada auxiliar.

**Não usar Sky como mapa geográfico simplificado definitivo; o mapa precisa revelar ruas, lugares e informações úteis.** O aprofundamento de tokens foi movido para [THEME-001](../brand/THEME-001.md). Estes valores são referências anteriores, não tokens contraditórios aprovados.

## Tipografia e alinhamento

- Título de viagem destacado no cartão superior, mas nunca cobrindo Pins críticos.
- No cartão inferior, nome do lugar é o centro editorial; nomes vizinhos ficam parcialmente visíveis e acessíveis.
- Escala tipográfica via estilos dinâmicos iOS/Android; não fixar tamanhos que cortem idiomas/acentos.
- Em textos longos, priorizar hierarquia e truncamento com leitura completa por acessibilidade.
- Números financeiros usam símbolos/moedas e formatadores locais; nunca confiar só em cor.

## iOS — Liquid

- Usar materiais e controles SwiftUI do sistema para elementos flutuantes.
- Manter Glass em **ferramentas**; texto longo, carrossel e stamps preferem superfície sólida.
- O relógio expande a partir do próprio botão com foco e redução de movimento.
- Evitar blur sobre fotos que reduz contraste; respeitar preferências de acessibilidade.

## Android — Flat

- Compose nativo, superfícies e formas sólidas com contraste e hierarquia.
- Ícones, gestos, tipografia e feedback seguem convenções Android.
- Não imitar automaticamente botões/transições Apple; mesma intenção funcional, execução própria.

## Temas e responsividade

- Claro: referência Sky/Paper como exploração.
- Escuro: **a definir por tokens semânticos**, não por simples inversão de cores.
- Alto contraste: exigir separação perceptível entre Pin ativo, outros Pins, mapa e conteúdo.
- Landscape/teclado/fonte ampliada: permitir trocar distribuição das proporções e, se necessário, apresentar relação mapa–conteúdo em variação adaptativa **sem criar cinco telas novas**.
- Testar alvos de toque, truncamento, notch/insets e leitor de tela antes da aprovação de mockups.

## Itens a aprovar

Paleta final, família tipográfica/licença, radius, densidade, stamp original, motion token, dark mode, ícones e direitos de marca. Esses itens não estão decididos nesta entrega.
