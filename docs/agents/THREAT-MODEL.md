# THREAT-MODEL — Modelo reutilizável de ameaças

**Status:** template; nenhuma avaliação de segurança real foi concluída.

## Quando obrigatório

Antes de implementar ou alterar: autenticação/convites, partilha de Trip, upload de foto/stamp, GPS e mapa com localização, finanças declarativas compartilhadas, deep links, sync/API, pagamento futuro, analytics, exportação, exclusão/backup e infraestrutura de release.

## Template

```markdown
# Ameaças — <feature> / <taskId>
Responsável e data:
Estado: proposto | revisado | bloqueado
Componentes e diagrama de fluxo:
Dados pessoais/sensíveis e titulares:
Entradas e saídas:
Fronteiras de confiança (device/backend/terceiros/CI):
Quem pode ver, criar, editar e apagar? (owner/editor/viewer/pessoal):
Casos de abuso:
- atacante ganha acesso a Trip de terceiro por ID previsível
- convite exposto/reutilizado ou não revogado
- foto publica GPS pelo EXIF
- logs públicos revelam rota/data
- sync sobrescreve dinheiro/rascunho
Impacto/probabilidade e prioridade:
Salvaguarda por ameaça e MASVS/MASWE aplicável:
Testes de autorização/armazenamento/rede/provedores:
Risco residual e quem aprova:
Planos de contenção/reversão:
Evidências executadas / não executadas:
Links ADR, STATUS, PR e revisão legal:
```

## Regras

- Estar autenticado não é suficiente: testar **autorização objeto-a-objeto** e escopo pessoal/grupo.
- Confiar em esconder controles é falha; backend/servidor deve impor permissões quando existir.
- Validar entrada e limites de recursos, isolamento de mídia, retenção/eliminação, e efeitos do offline.
- Não colocar nomes reais, tokens, coordenadas pessoais, segredos ou provas sensíveis no repositório público.
- P0/P1 abertos bloqueiam promoção/release e exigem contenção, conforme [QUALITY-GATES](QUALITY-GATES.md).
- Revisão é proporcional ao risco; uma tabela preenchida **não comprova proteção técnica**.

Referências: [OWASP MASVS](https://mas.owasp.org/MASVS/), [OWASP MASTG](https://mas.owasp.org/MASTG/), [SECURITY-PRIVACY](../standards/SECURITY-PRIVACY.md).
