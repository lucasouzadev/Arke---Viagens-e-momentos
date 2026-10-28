# BRAND-QUALITY-001 — Revisão de marca, cores e stamps

**Status:** checklist de revisão. Não há capturas de apps nativos nem testes de device realizados neste estágio.

## Gate de identidade

- [ ] Nome/slogan e símbolo analisados quanto a diferenciação e eventual conflito.
- [ ] Marca legível em 16, 24, 48 e 1024 px (icone com/sem texto).
- [ ] Favicon, avatar, splash, ícone iOS e ícone Android distinguíveis.
- [ ] Tipografia licenciada e hierarquia localizável, com fontes do sistema como fallback.
- [ ] Stamps e mídias originais/autorizados; direitos separados da licença de código.
- [ ] Diretriz de uso público da marca e materiais visuais aprovada.

## Gate Light/Dark

- [ ] `textPrimary`, `textSecondary`, botões e indicadores avaliados em superfície sólida e **mapa/foto real**.
- [ ] Texto comum alcança no mínimo 4,5:1 nos pares apresentados; texto grande 3:1.
- [ ] Ícones essenciais, componentes e indicadores testados para contraste não textual.
- [ ] `stampWarm` Light nunca aplicado como texto comum sobre branco sem mudança de cor.
- [ ] Liquid, acessibilidade de transparência e contraste testados em dispositivo.
- [ ] Tema flat Android consistente com Material 3 e fontes escaladas.
- [ ] Pin ativo reconhecível sem cor; estados de erro/sucesso não dependem de matiz.
- [ ] Tema dark projetado semanticamente, não invertido automaticamente.

## Gate Stamp

- [ ] Stamp sem foto, com foto vertical, horizontal, ausente e indisponível.
- [ ] Texto de 1–3 linhas, nomes de lugar longos, escalas ampliadas.
- [ ] Stamps múltiplos por Place e participantes diferenciados.
- [ ] Privacidade pessoal por padrão; ação explícita para compartilhar.
- [ ] Nenhuma afirmação de visita verificada sem mecanismo próprio.
- [ ] Entrada/edição/remoção e scroll não alteram contexto ou detent de maneira inesperada.
- [ ] Movimento reduzido, foco, alternativa sem gesto e VoiceOver/TalkBack.
- [ ] Exportação futura não vaza EXIF ou localização precisa involuntariamente.

## Validação futura obrigatória

Criar mockups originais claro/escuro de quatro estados (primeiro acesso, Pin, viagem, stamp), depois implementar protótipo nativo isolado **apenas após autorização**, executar matriz por viewport e E2E; anexar evidências. Uma imagem bonita não comprova velocidade ou acessibilidade.

Veja [QUALITY-001](../qualidade/QUALIDADE.md), [QUALITY-002](../qualidade/MATRIZ-UX-002.md), [THEME-001](THEME-001.md), [STAMPS-001](STAMPS-001.md).
