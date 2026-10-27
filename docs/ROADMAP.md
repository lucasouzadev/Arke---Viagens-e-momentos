# Roadmap — documentar, revisar, construir

| ID | Entrega | Estado |
| --- | --- | --- |
| DOCS-001 | visão, escopo, jornadas, ADRs e qualidade | publicada |
| DESIGN-001 | dois cartões sem barra inferior | direção aprovada |
| DESIGN-002 | relógio, carrossel e mapa sincronizado | direção aprovada |
| DESIGN-003 | Liquid iOS, Flat Android | direção aprovada; detalhes a validar |
| DOCS-002 | aprofundar gestos, estados, visual, grupo e finanças | **proposta em revisão** |
| DESIGN-004 | física e acessibilidade do relógio/carrossel | **proposto** |
| DESIGN-005 | semântica visual e temas | **proposto** |
| UX-001 | estados vazios, Pin pendente, rascunhos | **proposto** |
| GROUP-001 | convites, papéis e visibilidade | **proposto** |
| FINANCE-001 | gastos, cofrinho e moedas | **proposto** |
| QUALITY-002 | cenários de validação | **proposto** |
| DOMAIN-001 | modelo mínimo e papéis definitivos | pendente |
| BRAND-001 | identidade visual final e licenças | pendente |
| NATIVE-001 | implementação SwiftUI | **adiada por decisão do usuário** |
| NATIVE-002 | implementação Jetpack Compose | **adiada por decisão do usuário** |
| BUILD-001 | GitHub Actions, TestFlight, APK | **adiada; documentação apenas** |

## Ordem de revisão proposta

1. Avaliar DESIGN-004: comportamento de relógio, carrossel, mapa e detents.
2. Validar UX-001 e QUALITY-002: estados vazios, rascunhos, teclado, acessibilidade e falhas.
3. Avaliar DESIGN-005: identidade, dark mode, ícones e originalidade dos stamps.
4. Decidir GROUP-001: convites, papéis, privacidade e edição simultânea.
5. Decidir FINANCE-001: moeda, rateio e visibilidade de metas.
6. Registrar decisões finais em ADRs; atualizar escopo e matrizes; somente depois planejar código.

**Gate de programação futura:** design revisado, domínio mínimo e política de acesso acordados, fornecedor de mapa selecionado, testes definidos e autorização explícita para implementação.
