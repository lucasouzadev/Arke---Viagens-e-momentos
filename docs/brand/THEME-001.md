# THEME-001 — Tokens semânticos Light / Dark

**Status:** hipótese de paleta para revisão visual. Não é um design system final nem representa contraste testado sobre mapas reais, fotos ou vidro dinâmico.

## Princípio

Um único **vocabulário semântico** com dois modos. Componentes devem solicitar papéis como `onSurface`, `accent` ou `pinActive`, e não espalhar valores HEX pela UI. Diferentes plataformas podem mapear os papéis a materiais próprios.

## Proposta de tokens

| Token | Light | Dark | Uso |
| --- | --- | --- | --- |
| `canvas` | `#FCFEFE` | `#0C161C` | fundo geral |
| `surfaceContent` | `#FFFFFF` | `#15242C` | segundo cartão |
| `surfaceRaised` | `#F2F6F7` | `#20313A` | itens elevados |
| `mapAtmosphere` | `#BCECF7` | `#173A49` | atmosfera/placeholder de mapa, **não mapa real** |
| `textPrimary` | `#183F4E` | `#F2FAFC` | informação fundamental |
| `textSecondary` | `#4A6570` | `#B8CDD4` | metadados legíveis |
| `actionFill` | `#0E5367` | `#83D8E9` | ação principal |
| `onActionFill` | `#FFFFFF` | `#08252D` | conteúdo da ação |
| `stampWarm` | `#D45B44` | `#FF9B7C` | destaque editorial/ilustrativo, não texto pequeno sobre branco |
| `pinActive` | `#183F4E` | `#83D8E9` | forma do Pin com contorno |
| `outline` | derivado por opacidade/tema | derivado por tema | separador não textual; contraste a confirmar |

**Não usar `stampWarm` light para texto comum em branco:** contraste calculado ≈3,90:1, abaixo de 4,5:1 requerido para texto normal. Alterar cor ou aplicação.

## Pares calculados de contraste em cores sólidas (WCAG)

Os seguintes resultados derivam de luminância relativa sRGB e são **checagens matemáticas**, não teste visual/device:

| Par | Razão aproximada | Uso recomendado |
| --- | ---: | --- |
| `textPrimary` / `mapAtmosphere` light | 8,86:1 | textos em atmosfera plana |
| `textPrimary` / branco | 11,29:1 | títulos e corpo |
| `textSecondary` / branco | 6,20:1 | metadados |
| `onActionFill` / `actionFill` light | 8,57:1 | botões |
| `textPrimary` / `surfaceContent` dark | 15,04:1 | títulos escuros |
| `textSecondary` / `surfaceContent` dark | 9,63:1 | texto secundário escuro |
| `onActionFill` / `actionFill` dark | 9,87:1 | botões dark |
| `stampWarm` / `surfaceContent` dark | 7,75:1 | destaque editorial escuro |

Critério inicial: **4,5:1 para texto comum**, **3:1 para texto grande**; ícones/elementos UI essenciais exigem avaliação separada de contraste não textual. Nenhum valor garante legibilidade sob vidro translúcido/foto.

## Mapas, glass e fotografia

- Mapas reais possuem cores variáveis: rótulos/botões recebem superfície contrastante e/ou scrim avaliado **no pior trecho da imagem**.
- Liquid Glass iOS: usar materiais **do sistema** em controles, respeitar Reduce Transparency/Increase Contrast; não fixar transparência sobre o mapa e presumir contraste.
- Android: superfícies flat/Material 3 com cores semânticas. Dynamic Color, se oferecido, será opção avaliada sem perder distinção dos Pins.
- Fotos e stamps preservam cores autorais; overlays/legendas têm superfícies próprias.

## Luz, escuro e condições extremas

- Light e Dark devem ter **igual capacidade funcional**. Dark não é mera inversão de Light.
- Testar sol direto, brilho baixo, daltonismo simulado, alto contraste e contraste de ícones.
- Estado de erro/sucesso requer símbolo e texto; nunca somente vermelho/verde.
- Não usar cor azulada no fundo escuro sem avaliação crítica; a tonalidade aqui é apenas teste.
- Preferências do sistema têm prioridade sobre decoração.

## Fontes e referências

- Apple Materials: https://developer.apple.com/design/human-interface-guidelines/materials
- Material 3 Compose: https://developer.android.com/develop/ui/compose/designsystems/material3
- WCAG contraste: https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum

Relacionado: [BRAND-001](BRAND-001.md), [PLATFORM-001](PLATFORM-001.md), [BRAND-QUALITY-001](BRAND-QUALITY-001.md).
