# BUILD-001 — Estratégia futura de GitHub Actions

**Somente especificação.** Este repositório ainda não possui workflows, builds, APK, IPA ou segredos.

## Plano

| Fluxo futuro | Disparo | Resultado |
| --- | --- | --- |
| iOS CI | PR/push | build sem assinatura e teste simulador |
| Android CI | PR/push | Gradle debug/testes sem secrets |
| TestFlight | manual, ambiente protegido | IPA assinado e enviado |
| Android APK | tag/manual autorizada | APK instalável como artefato |
| Release | tag revisada | notas e arquivos verificados |

## Segurança

- PR externo sem secrets, evitar pull_request_target para executar código não confiável.
- Releases com aprovação manual, ambiente protegido e permissões mínimas.
- Chaves App Store Connect, certificados, provisioning profiles e keystore fora do repo e logs.
- APK de debug e distribuição de produção são diferentes; assinatura de produção protegida.
- Nunca subir artifacts que contenham credenciais, perfis ou logs sensíveis.

## Antes de configurar

1. Projetos nativos existentes e compilados.
2. Identificadores oficiais/bundle IDs definidos.
3. Contas e permissões de publicação apropriadas.
4. Estrutura de assinatura Apple e estratégia Android aprovadas.
5. Testes visuais e E2E mínimos concluídos.

**Não habilitar credenciais ou deploy antes do produto precisar deles.**