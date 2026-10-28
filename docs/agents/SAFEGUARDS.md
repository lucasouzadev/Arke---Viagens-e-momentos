# SAFEGUARDS — Salva-guarda, interrupção e recuperação

**Status:** protocolo obrigatório para ações de risco. Nenhum processo operacional de produção foi configurado.

## Regra fundamental

Uma falha tratada com transparência é aceitável; uma ação insegura ou destrutiva **escondida** não é. Agents não devem corrigir silenciosamente falha de acesso, vazamento, erro jurídico ou perda de dados para “terminar a tarefa”. Pare, contenha sem agravar, informe e registre.

## 1. Antes de qualquer ação com risco

1. **Classificar:** documental, mudança visual, dados, contas/grupos, localização/mídia, segurança, migração, infraestrutura, release.
2. **Identificar blast radius:** dispositivos, Trips, membros, dados locais/remotos, permissões e ambiente afetado.
3. **Validar autorização exata:** criar documento/branch é diferente de merge, apagar, deploy, assinatura ou publicar app.
4. **Inventário e checkpoint:** referências de commit/versões, backup recuperável se exigido e plano de reversão.
5. **Threat model** para mudanças com autenticação, convites, dados, uploads, localização, API ou backend.
6. **Condição de interrupção:** como reconhecer falha e retornar estado seguro.
7. **Comunicação:** responsável, canal e artefato adequado, sem segredos.

## 2. Stop conditions — interromper e escalar

| Evento | Ação segura mínima |
| --- | --- |
| Segredo/credencial em PR/log/artefato | suspender exposição, avisar responsável, **rotacionar/revogar credencial** por processo autorizado; remover texto público não basta |
| Falha de permissão entre grupos ou dados pessoais | bloquear fluxo/publicação afetada; preservar evidência sanitizada; revisar autorização no backend |
| Perda de dados/alteração destrutiva | parar escrita/migração; não tentar rollback sem avaliar compatibilidade; restaurar de fonte verificada |
| Incidente privacidade | escalonar imediatamente, registrar cronologia, classificar com equipe responsável pela LGPD |
| Direitos autorais/licença incertos | não publicar asset/dependência; solicitar autorização/licença |
| API/SDK desconhecido ou mudança de política de loja | não inventar capacidade; consultar docs oficiais e registrar dúvida |
| Conflito de ADR/produto | parar mudança contraditória, abrir proposta de decisão |
| Build/teste falhou | marcar FALHOU; não mascarar log, skip ou teste com “N/A” |
| Offline ou erro de sync | proteger drafts/dados, não mostrar sincronizado se não foi |
| User desautoriza ação | interromper futuras ações, preservar informações já permitidas |

## 3. Plano de recuperação (antes do evento)

Cada mudança operacional futura precisa descrever:
- **versão/commit** anterior conhecido e novo;
- tipo de dado e alcance;
- estratégia de reversão e compatibilidade de schema (rollback de app ≠ rollback de dados);
- backups verificados quando aplicáveis e processo testado para restaurar;
- responsável/autorização, passos de contenção, comunicação e critérios para retomar;
- verificação de integridade após correção e lições aprendidas.

**Não** aplicar comandos `force`, excluir coleções, purgar registros, apagar backups, reescrever histórico ou fazer migração irreversível como passo automático de "reparo". Produção requer janela/owner e plano aprovado.

## 4. Resposta de incidente (quando houver serviço em operação)

1. Registrar hora, incidente, sistema e descoberta **sem incluir PII nos logs públicos**.
2. Contenção proporcional autorizada, incluindo revogação de acessos/token se necessário.
3. Preservar evidências mínimas com controles de acesso; não publicar provas sensíveis no GitHub.
4. Avaliar impacto e pessoas afetadas; iniciar fluxo de proteção de dados e assessoria legal.
5. Definir comunicação, restabelecimento, testes e monitoramento; registrar pós-incidente.
6. Revisar [LEGAL-COMPLIANCE](../standards/LEGAL-COMPLIANCE.md) e prazos ANPD quando aplicáveis (não deixar agent interpretar sozinho).

## 5. Salvaguardas de documentação atual

- PR aberto não é merge nem versão pública; não iniciar código app ou credenciais.
- Não adicionar dados reais de localização, imagens protegidas, e-mails de convidados ou tokens.
- Verificar links, estados “proposto/aprovado”, origem das normas e ausência de licença presumida.
- Revisar marcos, atualizar STATUS e HANDOFF, rotular risco com evidência.
- Reversão documental deve usar novo commit explicativo, não ocultar decisão no histórico.

**Saída mínima de risco:** descrição → probabilidade/impacto → ações tomadas → evidência → estado residual → responsável pela decisão → próximo passo.

Relacionados: [QUALITY-GATES](QUALITY-GATES.md), [THREAT-MODEL](THREAT-MODEL.md), [LEGAL](../standards/LEGAL-COMPLIANCE.md).
