# QUALITY-002 — Matriz de comportamento por fluxo

**Status:** plano de testes, sem resultados de execução. Nenhum protótipo nativo ou CI foi executado nesta etapa.

## Cenários funcionais e de UX

| ID | Fluxo | Ação | Esperado |
| --- | --- | --- | --- |
| MAP-01 | mapa | mover/zoom durante cartão equilibrado | não altera detent/contexto |
| MAP-02 | Pin | tocar Pin e alternar lugar no carrossel | mesma seleção, sem loop |
| MAP-03 | Pin pendente | cancelar/voltar | sem perda de Pins existentes |
| MAP-04 | Pin pendente | toque duplo em salvar | apenas um novo Pin |
| CAR-01 | carrossel | primeiro/último item | limites finitos, vizinhos corretos |
| CAR-02 | carrossel | zero/um lugar | CTA ou título único sem swipe inerte |
| CAR-03 | carrossel | swipe diagonal/rápido | não puxa cartão nem muda contexto |
| CLOCK-01 | relógio | navegar pelos cinco contextos | sem tab bar, sem perda de Trip/Place |
| CLOCK-02 | relógio | fechar sem selecionar | mantém categoria e devolve foco |
| CLOCK-03 | relógio | fonte 200%/leitor de tela | lista alternativa, alvos legíveis |
| PANEL-01 | puxador | navegar três estados | scroll interno isolado |
| PANEL-02 | teclado | digitar em painel expandido | texto/ações visíveis |
| DRAFT-01 | drafts | editar, trocar contexto e voltar | draft recuperado |
| OFF-01 | offline | salvar com rede indisponível | indicação correta e retomada |
| GROUP-01 | permissão | viewer tenta editar | bloqueio real, mensagem objetiva |
| GROUP-02 | convite | revogar membro | sem novos acessos; retenção informada |
| FIN-01 | gastos | incluir duas moedas | nunca somar silenciosamente |
| FIN-02 | cofrinho | abrir meta pessoal em Trip de grupo | privada por padrão |
| MEMORY-01 | stamp | imagem indisponível | fallback preserva conteúdo |
| NAV-01 | volta | teclado → relógio → editor | ordem previsível |

## Revisão por plataforma

### iOS (futuro)

- Liquid nos controles sem reduzir contraste.
- Safe areas, Dynamic Type, VoiceOver, Reduce Motion.
- Estado da navegação após gesto do sistema e mudança de orientação.
- Testes UI XCUITest e screenshots quando o código existir.

### Android (futuro)

- Material flat, fonte escalada, TalkBack, back previsível.
- Insets/gestos do sistema, teclado IME, tamanhos compactos e tablets.
- Compose UI tests, screenshots e cenários de back/gestos quando houver código.

## Evidências mínimas

Nenhum caso recebe status “passou” sem execução real: anexar vídeo/capturas, versão de app, dispositivo/viewport, log/resultado do teste e desvio encontrado. Mockups validam direção visual, não comportamento em dispositivo. Ver [QUALITY-001](QUALIDADE.md).
