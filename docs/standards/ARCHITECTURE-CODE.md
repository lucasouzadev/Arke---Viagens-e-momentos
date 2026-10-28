# ARCHITECTURE-CODE — Arquitetura sólida e qualidade do código

**Status:** baseline de engenharia para validação documental agora e implementação futura **somente se autorizada**. Evitar arquitetura ornamental; escolher complexidade mínima capaz de preservar testes, dados e UX.

## Princípios obrigatórios

1. **Separação de responsabilidades:** apresentação ≠ regras de negócio ≠ armazenamento ≠ integração de mapa/rede.
2. **Interfaces por responsabilidade**, nomes claros e dependências apontando para o domínio; inversão de dependência quando facilitar troca/teste, sem camadas vazias.
3. **Fonte de verdade definida por tipo de estado:** seleção efêmera da UI, rascunhos recuperáveis, dados locais persistidos, dados sincronizados e dados remotos autoritativos não são a mesma coisa.
4. **Fluxo de dados unidirecional** e comandos/eventos rastreáveis para mapa ⇄ carrossel; impedir loops, seleções duplicadas e reentrância.
5. **Código legível**: tipos fortes, funções pequenas com responsabilidade concreta, composição antes de herança quando vantajosa, tratamento de erros explícito; SOLID é heurística, **não licença para abstração excessiva**.
6. **Dependências mínimas e revisadas:** usar bibliotecas oficiais/suportadas quando possível; verificar licença, manutenção, risco, compatibilidade, pinning e custo.
7. **Nativo de ponta a ponta:** Swift/SwiftUI/MapKit e Kotlin/Compose; sem Expo/React Native/Flutter como UI de produção. Mesmos contratos de comportamento, layouts adaptados por plataforma.
8. **Sem dados perdidos ou resultados fingidos:** guardar rascunhos, mostrar estados saving/saved/error/offline, retries idempotentes, cancelamento e recuperação.
9. **Observabilidade e desempenho:** logs sem PII, parâmetros mensuráveis, sem bloquear thread principal, evitar loops de layout, recomposição ou atualizações de mapa por frame.
10. **Testabilidade:** negócio independente de views, contratos de dados simuláveis, casos de borda como zero/um/muitos Pins e diferentes permissões.

## Camadas candidatas (não esquema definitivo)

```text
SwiftUI / Compose
  -> StateHolder (intents, UI state, lifecycle)
    -> Domain (casos de uso e invariantes de Trip/Pin/Place)
      -> Repository interfaces (capabilities e políticas)
        -> implementação local, mapa, mídia, eventual API remota
```

A localização dos módulos e frameworks de persistência fica por decidir em M2. Não criar repositório/microserviço separado para cada entidade sem necessidade.

## iOS — orientações de implementação futura

- `@MainActor`/isolamento de UI coerente, operações longas assíncronas e canceláveis; evitar `Task` soltas e retenção de recursos.
- View mantém apresentação, não realiza persistência/segurança diretamente. Estado recuperável para troca de app/cena/teclado; não confiar só no ciclo de vida de View.
- Usar APIs nativas disponíveis no deployment target validado; Liquid Glass em **controles**, conteúdo legível em superfície estável.
- MapKit camera e Pin selection sincronizados por intenção única; cancelar animação obsoleta.
- Segredos nunca hardcoded; permissões e dados sensíveis nos mecanismos corretos da plataforma.

## Android — orientações de implementação futura

- UI Compose orientada a estado imutável, `ViewModel`/state holder com lifecycle e SavedState conforme necessidade; Compose não é banco de dados.
- Coroutines estruturadas, `Flow` observável com coleta ligada ao lifecycle e cancelamento; evitar trabalho pesado no main thread.
- `remember`/`rememberSaveable` somente para estado apropriado; persistência durável pertence à camada de dados.
- Estados recomponíveis, chaves estáveis, listas eficientes, back preditivo e insets/IME tratados.
- Arquitetura recomendada de UI/data/(domain opcional), repositórios e dependências testáveis; Google Maps provider ainda pendente.

## Contratos comuns entre plataformas

- `SelectMapPin`, `SelectCarouselPlace`, `SelectContext`, `SetPanelDetent`, `BeginPin`, `ConfirmPin`, `CancelPin`, `SelectTrip` possuem semânticas equivalentes.
- Uma ação do usuário → uma mudança final de seleção; efeitos programáticos não voltam como nova intenção de usuário.
- Viagem muda sem vazar rascunho/privacidade entre grupos; cancelar não elimina Pin salvo.
- Relógio **não cria pilhas de navegação independentes**, e scroll de conteúdo **não arrasta cartão**.
- Dados offline recuperáveis com estado de sincronização honesto. Versão/autor para resolução de conflitos sem perda silenciosa.
- Domínio de dinheiro inclui moeda explícita, sem soma incorreta de moedas nem custódia.

## Código limpo ≠ perfeccionismo

Evitar arquivos gigantes e "god objects", mas também evitar interfaces para cada função, frameworks inventados, padrões escolhidos só por moda e refatorações sem valor. Toda abstração precisa justificar **necessidade, risco e teste**.

## Checagens a exigir futuramente

Format/lint/typecheck; testes unitários e de contrato; regressões de state machine; teste de lifecycle; profiling de renderização/mapa; UI screenshots/a11y; diff de dependências e licença; compile real e E2E onde aplicável.

Referências oficiais: [Android Guide to App Architecture](https://developer.android.com/topic/architecture), [Android Offline-first](https://developer.android.com/topic/architecture/data-layer/offline-first), [Apple SwiftUI](https://developer.apple.com/documentation/swiftui). Os detalhes de frameworks são **candidatos**, não decisões já aprovadas.
