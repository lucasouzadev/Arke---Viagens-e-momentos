# TASK-CONTRACT — Modelo obrigatório de tarefa

**Status:** contrato reutilizável para Issues, prompts de agentes e itens de roadmap. Não é código executável.

## Campos mínimos

| Campo | Como preencher |
| --- | --- |
| `taskId` | identificador estável; ex. `M0-DOCS-01` |
| `milestone` | M0 a M5 do [ROADMAP](../ROADMAP.md) |
| `status` | proposto / aprovado / em andamento / bloqueado / concluído |
| `objetivo` | resultado verificável em 1–3 frases |
| `contexto` | por que existe; situação atual |
| `escopo` | inclusões e exclusões explícitas |
| `referencias` | links de specs/ADRs/PR |
| `plataformas` | iOS, Android, ambas ou não aplicável |
| `dependencias` | IDs/decisões/bloqueios |
| `arquivos permitidos` | caminhos que o agente pode alterar |
| `aceite` | cenários observáveis e critérios de conclusão |
| `auditoria` | UX/UI, viewport, acessibilidade, segurança, dados, testes |
| `provas` | docs, capturas, logs, resultados de testes ou “não executado” |
| `notas publicas` | mudou o usuário? sim/não; texto leigo candidato |
| `handoff` | pendências e instrução para próxima pessoa/agente |
| `risco` | P0/P1/P2/P3, ameaça/impacto e salvaguarda |
| `gates` | G-01..G-15 de [QUALITY-GATES](QUALITY-GATES.md), estado e evidência |
| `canarioChat` | configuração efêmera fornecida pelo responsável **somente no chat**; documento apenas registra status sem nome |
| `compliance` | LGPD/LBI/loja/licenças aplicáveis ou justificativa de não aplicabilidade |

## Modelo copiável

```markdown
# TASK M?-XXXX — <Título>
Status: proposto
Milestone:
Objetivo:
Contexto:
Referências: AGENTS.md; docs/ROADMAP.md; ADRs...
Dentro do escopo:
Fora do escopo:
Plataformas:
Dependências e decisões pendentes:
Arquivos autorizados:
Critérios de aceite:
- [ ] ...
Auditoria UX/UI e responsividade:
- [ ] iOS (ou não aplicável, justificativa)
- [ ] Android (ou não aplicável, justificativa)
- [ ] safe area, teclado, overflow, temas, fontes, gestos, a11y
Auditoria backend/segurança/jurídico:
- [ ] ...
Gates G-01..G-15: estado + evidência/justificativa
G-15: CANARY confirmado no chat? Nome ausente de todos os arquivos? (não gravar valor)
Risco P0/P1/P2/P3 e plano de interrupção/recuperação:
Testes planejados/executados:
- Executado:
- Não executado e motivo:
Impacto público / changelog:
Evidências:
Riscos:
Próximo handoff:
```

## Regras de aceite

- **Documentação:** consistência entre ADR/roadmap/índice, termos claros, links válidos e estados honestos.
- **Design:** protótipo/descrição com estados e alternativas acessíveis; sem declarar validação nativa não realizada.
- **Código futuro:** compilação real da plataforma-alvo, regressão, safe areas, viewport, teclado, screenshots e E2E, inclusive impacto cross-platform.
- Nunca assumir `concluído` apenas por commit, PR aberto ou revisão superficial.

O agent não pode alargar escopo para “melhorar UX” contrariando dois cartões/relógio ou inventar quota/plano/funcionalidade. Exigir leitura de [PROMPT-OBRIGATORIO](PROMPT-OBRIGATORIO.md), [SAFEGUARDS](SAFEGUARDS.md) e os standards aplicáveis em cada execução.
