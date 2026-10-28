# QUALITY-001 — Critérios obrigatórios de qualidade

Para **cada mudança futura** em planejamento, UX/UI ou código, avaliar iOS e Android separadamente. Não considerar mockups ou docs evidência de teste real. O protocolo de comprovação e bloqueio fica em [QUALITY-GATES](../agents/QUALITY-GATES.md). **WCAG 2.2 AA é meta interna adaptada a native apps**, e OWASP MASVS é baseline de segurança, não certificação automática. Avaliação jurídica está em [LEGAL-COMPLIANCE](../standards/LEGAL-COMPLIANCE.md).

## Auditoria de interface e viewport

- [ ] Composição permanente de dois cartões; **sem tab bar tradicional**.
- [ ] Safe areas, status bar, indicador de gesto e teclado preservados.
- [ ] Telas pequenas, padrão, grandes, tablet, orientação retrato/paisagem.
- [ ] Fonte 100%, 130% e 200%; títulos longos, traduções, valores e moedas.
- [ ] Zero clipping, overflow, elementos fora da tela, sobreposição ou controles ocultos.
- [ ] Teclado não cobre editor/ação de confirmar e não elimina rascunhos.
- [ ] Áreas de toque e foco acessíveis, contraste, semântica, rótulos dos ícones.
- [ ] VoiceOver/TalkBack, Reduce Motion/Remove Animations, alternativas sem gestos.
- [ ] Estados vazios, sem rede, erro, loading, permissões insuficientes, mídia faltante.
- [ ] Gestos rápidos/concorrentes não alteram seleção ou detent inesperadamente.
- [ ] Scroll interno não redimensiona cartão; puxador não arrasta mapa/conteúdo.
- [ ] Alterações de aparência não degradam desempenho nem provocam saltos de layout.

## Matriz de dispositivos (alvos, não certificações)

| Perfil | iOS | Android | Objetivo |
| --- | --- | --- | --- |
| Compacto | iPhone menor suportado | ~360×800 dp | áreas mínimas |
| Padrão | iPhone moderno | ~412×915 dp | navegação principal |
| Tablet | iPad | 600dp+ | larguras máximas |
| Acessibilidade | Dynamic Type ampliado | fontScale 2.0 | foco e scroll |
| Paisagem | landscape | landscape | teclado e fallback |

## E2E obrigatório quando existir código

1. Abrir mapa + segundo cartão sem barra de abas.
2. Criar, confirmar/cancelar e restaurar Pin após reabrir.
3. Pin → carrossel e carrossel → Pin exatamente uma vez por ação.
4. Alternar cinco contextos pelo relógio sem perda de viagem, lugar e rascunho.
5. Mover puxador pelos três detents; scroll vertical independente.
6. Registrar gasto, meta, avaliação e stamp, testando privado vs grupo.
7. Testar teclado, fonte ampliada, leitor de tela e navegação alternativa.
8. Comparar screenshots iOS/Android, registrar divergências e correções.
9. Exercitar interrupções, app em segundo plano, offline e retorno do Android.
10. Assegurar que CI de PR externo não acessa credenciais de distribuição.

## Evidências de PR

Capturas/gravações por plataforma, matriz de viewport, relatórios E2E e avaliação manual, riscos e justificativa de diferenças intencionais. Ferramentas candidatas: XCUITest, Compose UI Tests, Maestro e testes de screenshot. Não afirmar execução sem evidência.