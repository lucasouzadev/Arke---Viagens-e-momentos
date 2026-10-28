# SECURITY-PRIVACY — Segurança, privacidade e dados de viagem

**Status:** baseline de engenharia defensiva para especificações e implementações autorizadas. Adotar [OWASP MASVS](https://mas.owasp.org/MASVS/) por risco, usando [MASTG](https://mas.owasp.org/MASTG/) para teste. Isso **não é certificação** MASVS e não substitui threat modeling, segurança de backend ou revisão jurídica.

## 1. Inventário e ameaças

O Arke lida potencialmente com localização/roteiros, datas de viagem (podem indicar ausência do domicílio), membros de grupo, fotos/EXIF, avaliações, contribuições declaradas e convites. Inventariar: quem é titular, finalidade, base legal a confirmar, visibilidade, local de persistência, retenção, exclusão, terceiros, fluxo de dados e risco de abuso.

Antes de features em grupo, links, fotos, mapa externo, sync ou analytics: preencher [THREAT-MODEL](../agents/THREAT-MODEL.md). Default **privado**, autorização mínima, e falhas fechadas em operações que expõem dados.

## 2. Grupos OWASP MASVS traduzidos em gates

| Família | Controle adaptado ao Arke |
| --- | --- |
| MASVS-STORAGE | minimizar PII, preferir armazenamento protegido, tratar backups/caches, não vazar drafts ou localização em logs |
| MASVS-CRYPTO | usar criptografia madura fornecida pela plataforma; sem inventar algoritmo; gerenciamento e rotação de chaves |
| MASVS-AUTH | autorização por Trip/membro/registro **no servidor**, com revogação e testes IDOR/BOLA |
| MASVS-NETWORK | TLS, endpoints confiáveis, sem dados sensíveis em query-string/logs; validar redirects/deep links |
| MASVS-PLATFORM | permissões de localização/mídia apenas just-in-time; intents/deep links/exportação e backups protegidos |
| MASVS-CODE | validação de entrada, dependências verificadas, compilação segura, atualização e hardening proporcional |
| MASVS-RESILIENCE | definir necessidade por ameaça; não prometer inviolabilidade nem exigir anti-tamper inútil |
| MASVS-PRIVACY | transparência, finalidade, minimização, controles e exclusão; evitar rastreamento passivo |

## 3. Privacidade de localização e mídia

- GPS opcional: permitir Pin manual. Evitar pedir permissão em primeiro acesso sem motivo.
- Não oferecer localização contínua/histórico público implicitamente; compartilhar itinerário ≠ compartilhar posição ao vivo.
- Retirar ou restringir metadados EXIF/GPS antes de compartilhar imagem; preservar apenas informação autorizada.
- Convites com token expiração/escopo/revogação apropriados, sem identificar membros privados por enumeração.
- Gasto e Cofrinho são **declarativos**; não fazer rastreamento de contas bancárias sem aprovação/novo arcabouço.
- Minimizar telemetria; se necessária, documentar finalidade e escolhas de consentimento conforme lei/plataforma.

## 4. Segurança técnica

- Segredos **nunca** no git, screenshots, logs, bundles ou workflow de PR público. Chaves de API públicas restritas por bundle ID/package/SHA quando provedor permitir, com quotas e monitoramento.
- Autenticação não equivale a autorização; validar acesso para **cada entidade e ação**. Escopo pessoal e grupo não pode ser conferido só pelo front.
- Criptografar transporte; não armazenar senha/tokens em UserDefaults/SharedPreferences simples; usar armazenamento apropriado da plataforma para dados de credenciais quando necessário.
- Em offline/sync, autenticar alterações e evitar replay/duplicação, isolar Trip e detectar conflito; não sincronizar drafts privados automaticamente.
- Impedir acesso de PRs externos a ambientes protegidos, permissões mínimas GitHub Actions e dependências revisadas; builds assinados apenas em ambiente protegido após gate.
- Falhas e retries não podem corromper ou apagar dados. Backup/restauração e migração terão roteiro e teste antes de uso real.

## 5. Classes de incidentes e resposta

Se houver suspeita de vazamento, exposição acidental, falha de autorização ou segredo comprometido: **interromper publicação/execução de risco, conter, preservar evidência sanitizada e avisar responsável**. Seguir [SAFEGUARDS](../agents/SAFEGUARDS.md) e [LEGAL-COMPLIANCE](LEGAL-COMPLIANCE.md) sobre eventual notificação por autoridade competente. Nunca registrar PII no PR público.

## 6. Critério de bloqueio

Não considerar pronto recurso de grupo que confie só em filtros visuais; não lançar permissão de GPS ampla sem finalidade; não lançar upload de foto sem política de mídia/EXIF; não publicar app com segredos embutidos. Documentar testes MASVS pertinentes e o que não foi testado.

Referências: [OWASP MASVS](https://mas.owasp.org/MASVS/), [OWASP MASTG](https://mas.owasp.org/MASTG/), [Apple App Review Privacy](https://developer.apple.com/app-store/review/guidelines/), [ANPD](https://www.gov.br/anpd/pt-br).
