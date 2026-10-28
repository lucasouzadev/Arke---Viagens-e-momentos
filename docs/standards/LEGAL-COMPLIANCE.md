# LEGAL-COMPLIANCE — Checklist jurídico e conformidade

**Status:** mapa de obrigações/riscos para decisão humana, **não parecer jurídico nem declaração de conformidade**. Rever legislação vigente, país de oferta, público-alvo e fornecedores antes de lançamento. Agent não toma decisão legal definitiva.

## 1. Matriz aplicável ao Arke

| Tema | Referência | Decisões/provas exigidas antes de tratar dados ou lançar |
| --- | --- | --- |
| Dados pessoais/privacidade no Brasil | [LGPD, Lei 13.709/2018](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm) | finalidade, hipótese legal, minimização, transparência, direitos, segurança, retenção e contratos com terceiros |
| Segurança/incidentes | [ANPD Regulamento de Incidentes](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis) | classificação, responsável, registros, prazo aplicável, notificações à autoridade/titulares quando exigido |
| Acessibilidade e inclusão | [LBI, Lei 13.146/2015](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2015/lei/l13146.htm) | avaliar obrigações da oferta concreta; metas WCAG 2.2 AA adaptadas como benchmark técnico, a11y nativa |
| Mídia, fotos, código/ícones | [Lei de Direito Autoral, 9.610/1998](https://www.planalto.gov.br/ccivil_03/leis/l9610.htm) | licenças, autoria, direitos de imagem e compatibilidade com open source |
| Crianças/adolescentes, se acesso provável | [Lei 15.211/2025](https://www.planalto.gov.br/ccivil_03/_ato2023-2026/2025/lei/l15211.htm) | avaliação etária, medidas de proteção aplicáveis e revisão jurídica específica |
| Distribuição iOS | [Apple App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/) | política de privacidade no app/listagem, permissão de localização, exclusão/conta, descrição correta de dados |
| Distribuição Android | [Google Play Policy Center](https://play.google.com/about/developer-content-policy/) | User Data/Data Safety, permissões, versões de SDK, requisitos de publicação atuais |
| Mapa e conteúdo geográfico | termos do provedor escolhido (a decidir) | atribuição, cache, mapa offline, geocoding, fotos/licenças e limite de uso |
| Outros países | leis locais (ex.: GDPR se aplicável) | avaliação de escopo geográfico, controlador/processador, transferência internacional e direitos |

**A inclusão nesta tabela não significa que toda lei ou artigo se aplique automaticamente** a cada feature; criar avaliação jurídica por país/risco. Não considerar orientação de política de loja “lei” por si só.

## 2. Inventário mínimo antes de lançar qualquer coleta

Para cada dado (Pin, nome, fotos, localização, viagem, grupo, gastos, analytics):
- dono/titular e finalidade;
- hipótese legal adequada (não assumir que "consentimento" é única base);
- necessidade/proporcionalidade; acesso pessoal/grupo/terceiros;
- armazenamento local/remoto, operador, transferência internacional;
- retenção, exportação, eliminação, revogação e respaldo em backup;
- texto de transparência e contato de privacidade;
- risco residual e revisão responsável.

Localização precisa e itinerários podem expor hábitos de deslocamento; evitar coleta contínua desnecessária e tornar visibilidade explícita. Fotos podem carregar localização por EXIF e identificar terceiros.

## 3. Resposta a incidente e autoridade

A ANPD informa que, para incidentes comunicáveis sob sua Resolução CD/ANPD nº 15/2024, **a comunicação à ANPD e aos titulares é em três dias úteis**, ressalvadas disposições específicas. **Apenas o controlador com assessoria responsável deve decidir se o incidente se enquadra e qual prazo aplica**; agents devem sinalizar imediatamente, preservar evidências e não esperar prazo para começar contenção. Também verificar registro de incidentes e documentação exigida.

Nunca publicar detalhes de vulnerabilidade/PII no README, PR ou changelog. Comunicação externa precisa de revisão humana.

## 4. Controles preventivos

- Política de privacidade real e acessível, finalidades honestas; revisar Apple/Google antes da publicação.
- Consentimentos ou outras hipóteses legais quando pertinentes, gestão de direitos dos titulares e contato.
- Conteúdo gerado pelo usuário: direito de mídia, denúncias/moderação se houver partilha pública, exclusão e retenção.
- Critério para conteúdo de menores, contas de grupo, convites e compartilhamento; não presumir classificação etária.
- O Cofrinho **não** realiza operação financeira; quaisquer depósitos/transferências reais requerem nova avaliação regulatória e decisão de produto.
- Marca/logotipo, licenças de código e fotos do projeto open source devem ser revisados separadamente.

## 5. Salvaguarda de decisão

Itens juridicamente relevantes recebem **estado BLOQUEADO** se base/finalidade, direitos, permissões, licenças ou requisitos de loja estiverem indefinidos. O agent recomenda perguntas e evidências para revisão humana; não inventa texto legal final para produção nem classifica sozinho conformidade.

Referências: [Lei LGPD](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm), [LBI](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2015/lei/l13146.htm), [ANPD Comunicação de Incidente](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis), [ANPD RIPD](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/relatorio-de-impacto-a-protecao-de-dados-pessoais-ripd), [Apple](https://developer.apple.com/app-store/review/guidelines/), [Google Play](https://play.google.com/about/developer-content-policy/).
