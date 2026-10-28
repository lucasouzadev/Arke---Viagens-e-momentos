# Roadmap — documentar, revisar, construir

| ID | Entrega | Estado |
| --- | --- | --- |
| DOCS-001 | visão, escopo, jornadas, ADRs e qualidade | publicada |
| DESIGN-001 | dois cartões sem barra inferior | direção aprovada |
| DESIGN-002 | relógio, carrossel e mapa sincronizado | direção aprovada |
| DESIGN-003 | Liquid iOS e Flat Android | direção aprovada; detalhes a validar |
| DOCS-002 | aprofundar gestos, estados, visual, grupo e finanças | proposta em revisão |
| DESIGN-004 | física e acessibilidade do relógio/carrossel | proposto |
| DESIGN-005 | semântica visual e temas | proposto |
| UX-001 | estados vazios, Pin pendente, rascunhos | proposto |
| GROUP-001 | convites, papéis e visibilidade | proposto |
| FINANCE-001 | gastos, cofrinho e moedas | proposto |
| QUALITY-002 | cenários de validação | proposto |
| BRAND-001 | linguagem da marca, nome, símbolo e iconografia | **proposto em revisão** |
| THEME-001 | **azul único e tema nativo** (regra aprovada); hex candidato e contraste pendentes | **regra aprovada; tom em revisão** |
| STAMPS-001 | memórias em selos, variantes, dados e privacidade | **proposto em revisão** |
| PLATFORM-001 | handoff nativo de estilo | **proposto em revisão** |
| BRAND-QUALITY-001 | requisitos de validação visual | **proposto em revisão** |
| DOMAIN-001 | modelo mínimo e papéis definitivos | pendente |
| NATIVE-001 | implementação SwiftUI | **adiada por decisão do usuário** |
| NATIVE-002 | implementação Jetpack Compose | **adiada por decisão do usuário** |
| BUILD-001 | GitHub Actions, TestFlight, APK | **adiada; documentação apenas** |

## Ordem de revisão proposta

1. Revisar comportamento do relógio, carrossel e detents em DESIGN-004.
2. Revisar proposta de marca em [BRAND-001](brand/BRAND-001.md) e apenas o **tom exato do azul único** / contraste em [THEME-001](brand/THEME-001.md); temas são automáticos.
3. Selecionar vocabulário visual dos [STAMPS-001](brand/STAMPS-001.md): formato base, registro e compartilhamento.
4. Criar mockups **originais** de iOS Liquid e Android Flat para quatro estados; validar modo claro/escuro e acessibilidade.
5. Revisar UX-001 e QUALITY-002; resolver grupo/finanças.
6. Registrar aprovações em ADRs e atualizar documentos; somente depois iniciar planejamento de código.

**Gate de programação futura:** autorização explícita, domínio/privacidade acordados, mapa escolhido, documentação consolidada e quality gates definidos.
