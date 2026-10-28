# BRAND-001 — Identidade, expressão e linguagem do Arke

**Status:** proposta, não aprovada. **Escopo:** sistema de identidade e conteúdo; nenhum código ou logo definitivo.

## 1. Ideia central

**Arke — Onde vamos?** A proposta de marca deve comunicar **imaginar, planejar, viver e guardar**, sem transformar o app em agência de turismo, rede social de viajantes ou gamificação agressiva.

- **Acolhedor e prático**: o lugar é protagonista, as ações são pequenas.
- **Cartografia sensível**: Pins, trajetos e superfícies de mapa conectam ideias a lugares reais.
- **Colecionável, não competitivo**: stamps registram experiências e histórias; não há rankings, XP ou badges compulsórios.
- **Coletivo quando necessário**: uma viagem solo torna-se de grupo sem recomeçar.
- **Sem jargão desnecessário**: linguagem direta, pt-BR padrão, nomes internacionais localizáveis.

### Núcleo de marca

- Assinatura textual candidata: **Arke**.
- Descrição curta: **Viagens que começam com um lugar.**
- Linha editorial proposta: **Marque um lugar. Crie uma viagem. Guarde o que viveu.**
- O nome e slogan são candidatos; marca registrada, domínio e disponibilidade precisam ser investigados antes da finalização.

## 2. Arquitetura visual

**Identidade = composição + relação espacial + stamps originais**; não depende de uma cor única.

1. Cartão superior: atmosfera, mapa, viagem e seleção de Pins.
2. Cartão inferior: papel de leitura e ação; relógio/contexto, carrossel de lugares, conteúdo vertical.
3. Destaques: Pins, stamp, mídia e rota conectados sem elementos duplicados.
4. Corredor visual central: nome do destino deve dialogar com o Pin focado.

Evitar ornamentação que prejudique utilidade do mapa (rotas fictícias não podem parecer direções reais).

## 3. Marca gráfica — direções ainda alternativas

- **A — Rota contínua**: traço simples que cruza um ponto; funciona pequeno e sem texto.
- **B — Selo de origem**: contorno de stamp com ponto central; remete ao registro da viagem.
- **C — Marca tipográfica**: wordmark Arke forte, símbolo opcional.

Não eleger uma opção sem estudo de reconhecimento em 16–48 px, modo escuro, fundos complexos e diferenciação de apps existentes. Evitar símbolos nacionais oficiais, carimbos de fronteira e logotipos de terceiros.

## 4. Tipografia

- UI: preferir **San Francisco via fontes do sistema no iOS**, **Roboto/fonte do sistema no Android**, respeitando Dynamic Type e font scaling.
- Wordmark: futura família ou desenho proprietário; nenhuma fonte comercial incorporada sem licença.
- Hierarquia: viagem (expressiva), lugar ativo (focal), categorias (objetivas), detalhes (legíveis), microcopy (sem reduzir acessibilidade).
- Títulos longos, diacríticos, moeda, locale e nomes de lugares devem permitir expansão natural.
- Sem construir interface em fonte monoespaçada apenas por estética.

## 5. Iconografia

- Mesma **semântica** nas duas plataformas, desenho nativo distinto.
- Planejamento = rota; Gastos = recibo; Cofrinho = meta/poupança; Avaliações = estrela; Memórias = stamp.
- Pin vazio, pendente e ativo precisam de forma/borda e rótulo; cor isolada é insuficiente.
- Ícones dentro do relógio **sempre acompanhados de nome** na experiência acessível; fallback em lista.
- Evitar usar símbolo de estabelecimento aberto sem confirmação ou promessas de disponibilidade.
- Não exportar SF Symbols como assets Android; usar correspondentes licenciados e nativos.

## 6. Escrita de interface

| Situação | Exemplo de linguagem | Evitar |
| --- | --- | --- |
| Primeiro acesso | “Marque um lugar para começar.” | “Complete seu dashboard.” |
| Salvar ideia | “Salvar Pin” | “Criar viagem obrigatoriamente” |
| Criar grupo | “Convidar para esta viagem” | “Compartilhar toda a localização” |
| Memória | “Registrar momento” | “Visita verificada” sem comprovação |
| Offline | “Salvo neste dispositivo. Ainda não compartilhado.” | “Sincronizado” prematuramente |
| Cofrinho | “Valor que você registrou ter reservado” | “Depósito confirmado” |

## 7. Governança

Antes de aprovar: marca, naming, logotipo, favicon, avatar, tipografia, ícones, tokens light/dark, acessibilidade e direitos de assets. Registrar escolha em ADR futuro; nenhuma decisão desta página se converte em implementação automática.

Relacionado: [THEME-001](THEME-001.md), [STAMPS-001](STAMPS-001.md), [PLATFORM-001](PLATFORM-001.md).
