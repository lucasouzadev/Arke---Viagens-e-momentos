# THEME-001 — Azul único + aparência nativa do dispositivo

**Regra de direção: APROVADA — uma única cor de marca, azul opaco, com claro/escuro seguindo o sistema.**  
**Código exato: CANDIDATO A VALIDAR — `#4C728A`.** Sem app, design system implementado ou testes em dispositivo.

## 1. Cor da marca

| Token | Valor candidato | Natureza |
| --- | --- | --- |
| `arkeBlue` | `#4C728A` | azul dessaturado, sólido, 100% opaco, sem gradiente |

Este é **o único token cromático proprietário** do Arke. Não criar escala de azuis, azul-céu adicional, ciano, salmão, laranja ou segunda cor de destaque.

> "Opaco" aqui significa cor sólida, sem alpha como parte do token. Não significa obrigatoriamente escurecer toda a interface. O Liquid Glass do iOS segue o comportamento do sistema e **não modifica o valor da cor da marca**.

A escolha do código hex é uma proposta de implementação visual, **não uma decisão final de tonalidade**. A decisão aprovada é a restrição a **um azul** e a adoção do tema automático do dispositivo.

## 2. O restante é do sistema

| Papel | iOS | Android | Regra |
| --- | --- | --- | --- |
| Fundo da tela | background semântico do sistema | background/surface do tema nativo | sem cor de marca no fundo inteiro |
| Cartões | superfícies semânticas | Surface do Material 3 | claros ou escuros conforme dispositivo |
| Texto primário/secundário | label/secondary label | onSurface/onSurfaceVariant | sem HEX proprietário |
| Separadores | cores do sistema | outline/outlineVariant neutro | sem tintas azuis extras |
| Ícones inativos | cor secundária do sistema | cor de conteúdo secundário | sem outra cor de destaque |
| Ação principal / Pin ativo | `arkeBlue` | `arkeBlue` | única cor intencional do Arke |
| Erro/destrutivo | cor de erro nativa com rótulo | error do sistema com rótulo | exceção semântica de segurança, não marca |

- Seguir **automaticamente o tema Light ou Dark definido no dispositivo**, incluindo atualizações enquanto o app está em primeiro plano.
- Não criar um botão "Tema do Arke" nem paletas paralelas. Preferências de acessibilidade também vêm do sistema.
- Não usar cores de papel de parede como segundo *accent* de marca por padrão. No Android, manter as superfícies adaptáveis e **a ação de marca no mesmo azul**, sem a cor dinâmica substituir sua identidade.
- Fotografias e mapa real têm suas **cores próprias do conteúdo**, não fazem parte da paleta de UI. Não aplicar filtro azul artificial sobre mapa/roteiro para simular dominância.

## 3. Distribuição no layout de dois cartões

- Superior: mapa real em destaque; azul opaco nos Pins e ações selecionadas e, se não houver mapa, em área ilustrativa original simples.
- Inferior: superfície **neutra do sistema**. Azul apenas em seleção de contexto/ação primária/traços editoriais discretos; restante tipografia/ícones em cores semânticas.
- Relógio: ativo em azul e opções inativas neutras; ícone + texto garantem que a seleção não dependa da cor.
- Carrossel: nome ativo pelo peso/tamanho e, se necessário, um indicador azul; vizinhos neutros.
- Stamps: borda neutra, destaque opcional azul, fotos com suas cores naturais. **Sem cores decorativas concorrentes.**

## 4. Contraste — verificação matemática do candidato

A luminância sRGB de `#4C728A` contra **branco sólido** gera contraste de aproximadamente **5,15:1** (válido para texto comum em par opaco). A avaliação precisa ser repetida ao escolher a tonalidade final.

**Atenção:** a mesma cor sobre superfícies Dark pode não atingir 4,5:1 para texto pequeno. Portanto:
- Para texto no Dark, usar `onSurface` do sistema; azul pode ser usado em **formas de seleção / preenchimentos**, não em labels de baixo contraste.
- Em botão com preenchimento azul, usar conteúdo branco somente depois de validar contraste e estados especiais.
- Glass, mapa, imagem, estados pressionados/disabled e barras do sistema exigem validação específica; cálculo em superfície sólida não basta.
- WCAG como referência: 4,5:1 para texto comum e 3:1 para texto grande, com análise separada de componentes e ícones.

## 5. Liquid iOS ≠ gradiente de marca

No iOS, o vidro é um **material nativo de interface**, aplicável a controles. A marca continua com **uma cor azul sólida**; não pintar painéis inteiros de vidro azul. No Android, usar superfícies flat e feedback nativo, sem blur fabricado.

## 6. Itens ainda abertos

Hex exato; validação de contraste sobre mapas/fotos e estados Disabled; legibilidade com transparência reduzida; formas de ícones, tipografia, marca gráfica, testes Light/Dark e alto contraste.

**A decisão de cor única e tema automático não está em discussão nesta rodada.**

Relacionados: [ADR-006](../decisoes/ADR-006.md), [BRAND-001](BRAND-001.md), [PLATFORM-001](PLATFORM-001.md), [BRAND-QUALITY-001](BRAND-QUALITY-001.md).

Referências: [Apple Colors](https://developer.apple.com/design/human-interface-guidelines/color), [Android Compose Material 3](https://developer.android.com/develop/ui/compose/designsystems/material3), [W3C Contrast Minimum](https://www.w3.org/WAI/WCAG21/Understanding/contrast-minimum).
