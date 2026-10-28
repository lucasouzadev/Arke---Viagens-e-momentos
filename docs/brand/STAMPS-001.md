# STAMPS-001 — Sistema de memórias e selos

**Status:** proposta de produto/arte. O stamp é um **registro pessoal de experiência**, não carimbo governamental nem verificação automática de presença. Referência de papel postal é linguagem visual; não copiar frames, ilustrações ou obras de terceiros.

## 1. O papel do stamp

O Arke não é apenas sobre onde alguém **vai**: também sobre onde **esteve** e o que decidiu guardar. O stamp torna uma memória reconhecível no contexto da Trip e do Place, sem adicionar tela de conquistas.

**Fluxo no segundo cartão:** relógio → Memórias → carrossel de lugares, se aplicável → lista/coleção rolável de stamps → toque abre leitura/edição no mesmo cartão expandido. O mapa permanece relacionado ao lugar.

## 2. Estrutura visual proposta

- Formato base: selo postal de cantos recortados ou borda perfurada, com leitura boa mesmo sem borda.
- Camadas: **moldura neutra do sistema**, **imagem/ilustração autorizada**, **local** (nome), **data ou período opcional**, **marca pessoal discreta em azul opaco**, **nota opcional**.
- O formato deve funcionar com foto horizontal/vertical, ausência de foto, nome longo e acessibilidade.
- **Uma única cor de marca** para detalhe editorial; borda, papel, texto e separadores seguem o modo claro/escuro nativo. Sem selo salmão, dourado, verde ou outras cores decorativas; fotografia mantém cores próprias.
- Diferença entre fotos reais de usuário e arte gerada/ilustrada deve ficar evidente quando relevante.
- Evitar carimbos de passaporte reais, símbolos oficiais, selos de aprovação e numerações de "visita verificada".

### Quatro famílias a explorar, não quatro recursos separados

| Variante | Característica | Quando usar |
| --- | --- | --- |
| Postal | recorte tradicional, foto grande | memória com imagem |
| Traço | pequeno trecho/linha da rota abstrata | registro de percurso sem foto |
| Lugar | ilustração/fotografia autorizada e título | lugar visitado |
| Cartão | superfície simples para texto longo | anotações e sentimentos |

Não exigir escolha de template no fluxo básico; o usuário registra o momento e a visualização se adapta aos dados.

## 3. Dados mínimos (conceituais)

`MemoryStamp`: `id`, `ownerId`, `tripId?`, `placeId?`, `title`, `note?`, `happenedOn?`, `media?`, `visibility`, `createdAt`, `updatedAt`.

- `happenedOn` pode ser apenas dia ou desconhecido; não inventar data/horário.
- `placeId` pode faltar quando a memória é de uma viagem inteira.
- `visibility`: `private` por padrão, `tripShared` somente por ação consciente.
- Mídia inclui referência de autoria/permissão; evitar persistir GPS EXIF em imagem compartilhada por padrão.
- Stamp pode ser criado **sem** avaliação e avaliação **sem** stamp.
- Um lugar pode ter múltiplos stamps, inclusive de diferentes participantes, sem sobrescrita.

## 4. Estados e conteúdo

| Situação | Resultado |
| --- | --- |
| Nenhum stamp | convite discreto “Registre um momento desta viagem” |
| Pin não visitado | CTA de registro voluntário; não criar stamp automático |
| Sem foto | composição tipográfica com textura original leve |
| Foto ausente/offline | moldura e texto preservados |
| Lugar desconhecido | registrar memória sem pin forçado |
| Grupo | mostrar quem criou; conteúdo pessoal não vira compartilhado sozinho |
| Exclusão | confirmação/possibilidade de desfazer quando viável |

O registro é sempre **declarado pelo usuário**. Caso surja uma certificação de visita no futuro, ela exigirá especificação, privacidade, antifraude e comunicação própria.

## 5. Comportamentos

- Entrada do stamp no carrossel/coleção sem mudar o detent contra a vontade do usuário.
- Movimento opcional: discreto encaixe do selo ao salvar, feedback de papel e haptic breve quando habilitado.
- Reduzir Movimento: substituir efeito por transição curta ou imediata.
- Scroll vertical dentro do painel com itens com altura estável; carregamento de foto não deve mover conteúdo de maneira brusca.
- Sem animações confete em série, contadores de conquista, XP ou bloqueio de memórias por "nível".
- Long press, zoom de foto e edição devem ter equivalentes por botão e controle de foco.

## 6. Acessibilidade

- Bordas decorativas não podem cortar imagem/legenda.
- Leitura sem borda/sem cor funciona; descrever stamp com texto útil ("Memória de Milan Duomo, 12 de setembro").
- Imagem possui texto alternativo definido pela pessoa quando compartilhada ou descrição apropriada no contexto pessoal.
- Fontes em escala grande expandem o cartão, não sobrepõem mídia e ações.
- Voz/teclado navegam coleção por itens, não por rotação arbitrária.

## 7. Direitos e compartilhamento

- Usar imagens próprias, conteúdo do usuário com direitos e elementos artísticos originais.
- Não embutir recortes de Pinterest, fotografias de terceiros ou brasões em bibliotecas open source sem licença.
- Compartilhar stamp não compartilha automaticamente álbum, localização precisa, EXIF ou itens financeiros.

## Questões para aprovação

Versões finais das bordas, caráter da ilustração, escolha de 1 formato padrão, se haverá exportação PNG/álbum, política de mídia e exclusão, integração com mapa. Ver [BRAND-QUALITY-001](BRAND-QUALITY-001.md).
