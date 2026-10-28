# QUALITY-GATES — Critérios universais e prova de conclusão

**Status:** política obrigatória para agents. Complementa [QUALITY-001](../qualidade/QUALIDADE.md), [QUALITY-002](../qualidade/MATRIZ-UX-002.md) e [REVIEW-PROTOCOL](REVIEW-PROTOCOL.md).

## 1. Estados obrigatórios de cada gate

- **PASSOU:** evidência disponível (teste executado ou documento revisado).
- **FALHOU:** não atende; abrir correção.
- **BLOQUEADO:** depende de autorização, decisão, ferramenta ou evidência ainda indisponível.
- **NÃO EXECUTADO:** teste aplicável, mas não executado; nunca converter em PASSOU.
- **NÃO APLICÁVEL:** fora do escopo **com justificativa objetiva**.

Qualquer teste não executado em uma tarefa de implementação que dele dependa impede declarar **concluído**. Na fase somente documental, avaliações funcionais de código são **não aplicáveis à entrega atual** e devem constar como **não executadas** para o futuro.

## 2. Matriz de gates

| ID | Gate | Pergunta obrigatória | Evidência esperada |
| --- | --- | --- | --- |
| G-01 | Direção/ADR | Mudança respeita dois cartões, sem tab bar, único azul e stack nativa? | diff + documentos |
| G-02 | Escopo/entrega | Tarefa tem ID, aceite, dependências, arquivos autorizados e decisão? | contrato de tarefa |
| G-03 | Arquitetura | Camadas, fronteiras, fluxo unidirecional e fonte de verdade são coerentes? | desenho/diff/testes |
| G-04 | Código limpo | Sem duplicação injustificada, responsabilidades claras, erros explícitos? | revisão/lint |
| G-05 | UX/UI | Mapa/carrossel/relógio/drag, estados de erro e rascunhos não regrediram? | fluxo/screens |
| G-06 | Responsividade | Safe areas, IME/teclado, overflow, texto 200%, rotação/tablet? | screenshots/test matrix |
| G-07 | Acessibilidade | Leitor de tela, equivalentes sem gesto, foco, contraste e movimento reduzido? | testes iOS/Android |
| G-08 | Segurança | MASVS de risco, secrets, autorização backend, dependências, links e mídia? | threat model + testes |
| G-09 | Privacidade/jurídico | Dados/finalidade/base legal/visibilidade/licenças/lojas avaliados? | revisão + pendências |
| G-10 | Dados/offline | Nenhuma duplicação, vazamento inter-trip, perda de draft, sync enganoso? | casos de borda |
| G-11 | Performance | Sem bloqueio do main thread, loops de câmera/recompose, consumo excessivo? | medição/profiling |
| G-12 | Testes/regressão | Testes unitários, contratos, E2E e screenshots aplicáveis realizados? | links/logs/execução |
| G-13 | Operação/release | Deploy seguro, assinatura, rollback e versionamento confiáveis? | plano/execução real |
| G-14 | Continuidade/comunicação | STATUS/HANDOFF/ROADMAP/changelog consistentes? | links e revisão editorial |
| G-15 | Canário privado de chat | Cada resposta ao responsável incluiu o nome confirmado na conversa ou nas preferências privadas e persistentes do agent? O nome ficou ausente de qualquer arquivo/PR/código/log? | verificação da conversa + auditoria do diff, **sem transcrever nome** |

Cada gate deve ter responsável por revisão e **resultado textual**, jamais simplesmente caixas marcadas sem justificativa.

## 3. Classificação de risco e bloqueio

- **P0 — Bloqueador crítico:** exposição de dados pessoais, auth bypass, secret publicado, perda destrutiva irrecuperável, violação evidente de proteção de menores, operações financeiras não autorizadas. **Parar e escalar. Não relevar automaticamente.**
- **P1 — Alto:** inacessibilidade de função essencial, vazamento de dados entre Trips, erro de moeda/rateio com consequência, regressão que impede salvar/editar, recurso crítico sem teste. **Não promover release sem decisão e correção**.
- **P2 — Moderado:** falha de visual secundário, desempenho degradado sem perda de tarefa, estado raro coberto por workaround. Registrar e priorizar conforme impacto.
- **P3 — Baixo:** detalhe cosmético sem impacto funcional ou acessibilidade. Registrar sem mascarar.

**Exceção (“waiver”)**: desvio não crítico e devidamente justificado só pode ser aceito pelo responsável autorizado, com escopo, prazo de reavaliação, mitigação e evidências. Não há waiver automático para P0, obrigação legal ou segredo exposto.

## 4. Checklist de PR obrigatório

```markdown
### Qualidade e segurança (anexar no PR)
- Task ID / milestone / autorização:
- Mudança, dependências e ADRs:
- Impacto iOS / Android / backend:
- G-01 .. G-15: estado + evidência ou justificativa
- Matriz de viewport e a11y:
- Testes executados + resultados + ambiente:
- Testes não executados / justificativa:
- Threat model e avaliação legal (quando pertinente):
- P0/P1 em aberto:
- Plano de recuperação / rollback se aplicável:
- STATUS, HANDOFF, ROADMAP e CHANGELOG:
- Responsável pela aprovação:
```

Não prometer “100% livre de bugs” ou “compliance garantida”. Ao publicar mudanças documentais, checar links, contradições e conteúdo indevidamente sensível; **não inventar evidência de dispositivos**.

## 5. Gate real versus simulação

Uma checklist em Markdown não impede tecnicamente merge. Quando CI for autorizado no futuro, automatizar verificações **que são automatizáveis** (lint, teste, SAST, secrets, dependências, builds, screenshots quando possível). UX, a11y, arquitetura, privacidade e jurídico precisam adicionalmente de revisão humana. Não criar Actions nesta fase.

Links: [PROMPT](PROMPT-OBRIGATORIO.md), [CANARY](CANARY.md), [SAFEGUARDS](SAFEGUARDS.md), [ACESSIBILIDADE](../standards/ACCESSIBILITY-UI.md), [ARQUITETURA](../standards/ARCHITECTURE-CODE.md), [SEGURANÇA](../standards/SECURITY-PRIVACY.md), [JURÍDICO](../standards/LEGAL-COMPLIANCE.md).
