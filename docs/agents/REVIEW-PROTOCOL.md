# REVIEW-PROTOCOL — Revisão e aprovação

**Status:** padrão de revisão documental. Revisor precisa comparar intenção, alteração e evidência.

## 1. Quem decide o quê

- **Responsável pelo produto:** aprova mudanças no conceito, fluxo, marca, permissões, escopo, roadmap de produto, integração financeira e liberação para programar.
- **Agent autor:** propõe e documenta; não confunde proposta com aceite.
- **Agent revisor:** avalia consistência, regressão, segurança, UX e qualidade; pode recomendar, **não aprovar decisões reservadas ao produto**.
- **Release:** não publicar TestFlight/APK ou ativar segredos sem autorização explícita e gates futuros.

## 2. Gates documentais

- [ ] Documento vincula milestone e tarefa.
- [ ] Não contradiz ADR aceito nem marca hipótese como decisão.
- [ ] Roadmap, índice, STATUS e HANDOFF foram reconciliados.
- [ ] Links relativos conferidos; nomenclatura consistente.
- [ ] Sem inventar executáveis, prints, resultados de testes ou release.
- [ ] Linguagem pública sem jargão e sem promessas não entregues.
- [ ] Nenhum segredo, dado privado ou asset não autorizado.

## 3. Gates de experiência e engenharia (sempre avaliar)

- [ ] Mapa + cartão inferior preservados; sem tab bar.
- [ ] Carrossel, relógio, três estados, drafts e navegação linear coerentes.
- [ ] iOS/Android adaptados com comportamento equivalente.
- [ ] Uma cor de marca e tema automático do sistema.
- [ ] Safe areas, teclado, fontes ampliadas, landscape, tablet, overflow, overlap, acessibilidade, offline e estados de erro.
- [ ] Mudanças backend/privacidade/finanças/permissões avaliadas.
- [ ] Testes/E2E quando houver app; documentação pura: “não executados — não aplicáveis nesta fase”.
- [ ] Gates **G-01..G-15** preenchidos com PASSOU/FALHOU/BLOQUEADO/NÃO EXECUTADO/NÃO APLICÁVEL e evidência/justificativa ([QUALITY-GATES](QUALITY-GATES.md)).
- [ ] Threat model para grupos, localização, mídia, autorização, dados ou redes; plano de contenção ([SAFEGUARDS](SAFEGUARDS.md)).
- [ ] Acessibilidade e segurança avaliadas segundo [ACCESSIBILITY](../standards/ACCESSIBILITY-UI.md) e [OWASP baseline](../standards/SECURITY-PRIVACY.md), sem alegar certificação.
- [ ] Avaliação legal/privacidade do contexto registrada, e revisão humana quando houver risco ([LEGAL](../standards/LEGAL-COMPLIANCE.md)).

**Canário:** validar que a forma de tratamento confirmada aparece nas respostas do chat, mas **nunca** em commits, documentação, descrição do PR, código, logs ou notas de release. Se o nome não estiver confirmado, G-15 fica bloqueado; não inferir identidade.

## 4. Política de PR

Autoria em branch, PR com resumo, documentos impactados, aceite, testes, não testes, riscos, aprovação requerida, mudança perceptível ao público, e handoff. **Não fazer merge automaticamente**. Depois de merge confirmado, atualizar STATUS e changelog de projeto; uma liberação de app terá registro separado e só após disponibilidade verificada.

## 5. Divergências

Documentar em `docs/OPEN-QUESTIONS.md` e apontar ADR proposto. Não contornar decisão por alteração indireta em README ou changelog.
