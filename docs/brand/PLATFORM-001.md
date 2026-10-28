# PLATFORM-001 — Handoff visual nativo iOS / Android

**Status:** guia para o futuro, sem SwiftUI/Compose implementados.

## Equivalência = tarefas, não pixels

Uma pessoa em qualquer plataforma precisa conseguir: tocar Pin, mudar Place, abrir relógio, selecionar os cinco contextos, expandir segundo cartão, ler e criar stamps e usar alternativas sem gesto.

| Componente Arke | iOS (SwiftUI futuro) | Android (Compose futuro) | Não fazer |
| --- | --- | --- | --- |
| Cartão do mapa | MapKit e controles com materiais do sistema | mapa nativo e ferramentas flat | mapa apenas decorativo |
| Relógio contextual | controle flutuante Liquid, fallback lista | popover ou sheet flat contextual | tab bar permanente |
| Carrossel | scroll snapping nativo | pager/row com snapping | loop infinito / seleção fantasma |
| Puxador | pan/drag isolado | drag isolado com insets | scroll move painel |
| Stamps | cartão sólido dentro do painel | cartão sólido dentro do painel | foto sob vidro que compromete texto |
| Edição | área contextual que acomoda teclado | área contextual que acomoda IME | abrir cinco rotas de navegação |
| Acessibilidade | VoiceOver, Dynamic Type, Reduce Motion | TalkBack, font scale, Remove Animations | controles acessíveis só por swipe |

## Políticas de Material

### iOS

Liquid Glass é uma camada funcional para navegação e controles. **O cartão de conteúdo não deve virar um bloco de Liquid Glass**: superfície de leitura precisa ser estável. Se ações sobre o mapa usarem vidro transparente, conferir contraste real e respeitar ajustes de acessibilidade do dispositivo. **Azul da marca sempre sólido (100% opaco)**; o material de vidro é do sistema, não uma segunda paleta.

### Android

Flat significa hierarquia por superfícies, tipografia, formas e movimento, **não ausência de feedback**. Compose usa superfícies e tipografia semânticas Material 3, seguindo Light/Dark do sistema. Não gerar uma segunda cor de destaque por wallpaper/Dynamic Color; manter **o mesmo azul da marca** nos estados selecionados. Não simular translucidez Apple por blur arbitrário.

## Política de aparência

- **iOS e Android seguem automaticamente a aparência Light/Dark do dispositivo.** Não haverá seletor próprio de tema.
- Fundos, cartões, textos, separadores e ícones inativos usam tokens semânticos nativos, não uma paleta manual por plataforma.
- A única cor customizada de UI do Arke é `arkeBlue`. Cores de erro/aviso do sistema são exceções funcionais, não cores de marca.
- Mapas e fotos mantêm seus próprios tons; o tema aplica apenas chrome/controles e superfícies do app.

## Critérios de comparação

- Os dois cartões e a navegação interna continuam evidentes em light/dark.
- Nenhuma plataforma tem aba inferior, dashboard ou menu escondendo o relógio.
- Foco de mapa e seleção de lugar sincronizados; diferenças de animação são intencionais.
- Textos, moeda, compartilhamento e mídia obedecem idioma e padrões da plataforma.
- Gestos de sistema/back competem menos que ações do produto; existe caminho alternativo sem gesto.
- Tabulação/VoiceOver/TalkBack leem a hierarquia natural: viagem → lugar/contexto → conteúdo.
- Conferir landscape/tablet, teclado, estados vazios, altura mínima e safe areas.

## Fontes oficiais de orientação

- Apple Materials: https://developer.apple.com/design/human-interface-guidelines/materials
- Apple Layout: https://developer.apple.com/design/human-interface-guidelines/layout
- Compose Material 3: https://developer.android.com/develop/ui/compose/designsystems/material3

A validação de implementação depende de screenshots/telemetria de gestos/E2E e dispositivos reais; documentos não são resultados de teste.
