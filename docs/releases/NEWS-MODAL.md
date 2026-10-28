# NEWS-MODAL — Contrato editorial e de UX para novidades do aplicativo

**Status:** documentação de recurso futuro; **NÃO implementado**. Fonte pública: [CHANGELOG](../../CHANGELOG.md). Regras editoriais: [CHANGELOG-GUIDE](../agents/CHANGELOG-GUIDE.md).

## Objetivo

Quando o Arke possuir builds públicas, oferecer um modal/painel contextual simples chamado **“Novidades do Arke”**, para informar de forma acessível o que realmente mudou, com linguagem comum. Deve caber na lógica de **dois cartões**, sem introduzir uma nova tab bar ou fluxo longo.

## Regra de publicação (obrigatória)

Modal mostra somente entradas com **versão disponibilizada de verdade** para a plataforma da pessoa. Nunca mostrar:
- proposta, PR ou commit isolado;
- versão não liberada ao canal/usuário;
- planejamento de funcionalidades;
- build de teste privado como se fosse atualização geral;
- promessas de lançamento ou métricas não comprovadas.

## Modelo de registro editorial (conceitual, não API implementada)

| Campo | Regra |
| --- | --- |
| `id` | identificador estável e único da nota publicada, ex. `arke-1.0.0` |
| `version` | versão real e atribuída ao app |
| `publishedAt` | data efetiva de liberação ao público pertinente |
| `platforms` | iOS, Android ou ambas, conforme evidência |
| `availability` | released (fonte conferida); drafts ficam fora do feed |
| `title` | título em português simples |
| `summary` | uma frase explicando benefício |
| `changes` | pontos curtos de novidades/melhorias/correções |
| `detailsUrl` | opcional; link seguro para changelog |
| `minSupportedVersion` | opcional, somente se necessário |
| `locale` | pt-BR inicial, com fallback editorial se houver outros idiomas |

Não definir **neste marco** endpoint, framework, banco ou algoritmo de sincronização. Changelog Markdown continua a fonte editorial humana; a forma de publicação de metadados será definida no marco técnico.

## Comportamento da UI proposto

- Disponível por ação contextual discreta (por exemplo, “O que mudou?”) dentro da experiência atual.
- Ao iniciar uma nova versão elegível, oferecer um modal leve **não obrigatório**. A pessoa fecha e continua no mesmo mapa/Trip/Place/contexto.
- Uma nota já lida não deve interromper repetidamente. Futuro mecanismo de `lastSeenReleaseId` preferencialmente local e sem rastreamento por padrão.
- Manter opção de abrir histórico completo na própria experiência.
- Não exibir quando não há versão elegível; se offline, usar conteúdo local seguro ou não mostrar convite enganoso.
- Para várias versões ignoradas, apresentar síntese coerente com acesso ao histórico, não uma sequência de modais obrigatórios.
- Botões claros: **Entendi**, **Ver todas**. Sem forçar avaliação, login, push ou compartilhamento.
- Autoabertura, frequência e posição precisam de teste de UX e aprovação antes da implementação.

## Acessibilidade e plataforma

- Fonte escalável, contraste adaptado ao tema do device, foco lógico, VoiceOver/TalkBack e botão de fechar.
- Mesma informação e ações em iOS e Android; apresentação e animação usam componentes nativos.
- Azul único de marca para ação/seleção e restante da UI semântico do SO.
- Reduzir movimento elimina transições desnecessárias; modal não deve cobrir ações de edição nem perder drafts.
- Sem coleta de métricas de leitura por padrão.

## Aceite documental agora

Contrato editorial coerente com o changelog e o README, sem afirmar recurso implementado. Testes nativos e do modal: **não executados nesta fase**. Futuras entregas seguirão [QUALITY-001](../qualidade/QUALIDADE.md) e [QUALITY-002](../qualidade/MATRIZ-UX-002.md).
