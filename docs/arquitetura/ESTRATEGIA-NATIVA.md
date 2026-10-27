# Arquitetura — Duas bases nativas, um produto

**Esta página é planejamento. A implementação está adiada até autorização.**

| Área | iOS | Android |
| --- | --- | --- |
| Linguagem | Swift | Kotlin |
| Interface | SwiftUI | Jetpack Compose |
| Mapa | MapKit | Google Maps SDK ou alternativa validada |
| Persistência | SwiftData ou biblioteca nativa avaliada | Room ou biblioteca nativa avaliada |
| Testes de UI | XCUITest | Compose UI Test / Espresso |
| Automação futura | Xcode em runner macOS | Gradle/Android SDK em runner Linux |
| Distribuição futura | TestFlight | APK |

## Restrições

- Não usar React Native, Expo, Flutter ou WebView como camada de UI do produto.
- Não copiar literalmente componentes de iOS no Android nem o contrário.
- Compartilhar linguagem de domínio, contratos, critérios e recursos visuais autorizados, **não uma UI cross-platform**.
- Fixar versões/SDKs somente após prova real das toolchains.

## Fronteiras

Domínio conceitual Arke → implementações locais independentes (SwiftUI / Compose) → persistência e mapas nativos → possível API de sincronização no futuro.

## Colaboração e backend

Antes de implementar compartilhamento: decidir autenticação, convites, papéis, isolamento de viagem, visibilidade de registros pessoais, revogação e retenção. Usar IDs estáveis, autoria, versionamento de alterações, idempotência e estratégia de conflitos.

## Gate

Começar programação apenas com interface e interações revisadas, modelo de domínio mínimo definido, fornecedor de mapas decidido e critérios de qualidade acordados.