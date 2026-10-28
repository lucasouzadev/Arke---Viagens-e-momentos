# CHANGELOG-GUIDE — Escrever novidades que todo mundo entende

**Objetivo:** uma fonte pública em linguagem simples, útil no [README](../../README.md) e, futuramente, em um modal de “Novidades” do Arke.

## 1. Duas situações, sem confundi-las

**Agora (sem aplicativo lançado):** registrar **avanços do projeto** em `CHANGELOG.md`, deixando explícito que são documentação, decisões ou estudos. Não há versionamento de app nem funcionalidade “disponível”.

**Quando existir app publicado:** registrar **novidades efetivamente disponibilizadas aos usuários**, com versão, data real de liberação e plataformas confirmadas. O modal exibirá apenas essas entradas publicadas. **Não** expor melhorias que estão só em PR, TestFlight interno ou protótipo como se fossem públicas.

## 2. Tom de voz

- Escrever em **pt-BR cotidiano**, 1 ideia por frase, sujeito + verbo + benefício.
- Explicar o que a pessoa conseguirá fazer ou o que ficou mais fácil, não ferramentas utilizadas.
- Evitar “refactor”, “backend”, “CI”, “PR”, “hotfix”, “UX polish”, “migrations”, “deploy”.
- Preferir: “Agora você pode salvar lugares mesmo antes de criar uma viagem”.
- Só escrever “Agora você pode...” depois que a funcionalidade estiver **disponível** na versão indicada.
- Não criar métricas, promessas de desempenho, segurança ou privacidade sem evidência.
- Não incluir identificadores pessoais, rastros de localização, nomes de membros de grupo ou conteúdo privado.

## 3. Estrutura pública

### Antes do primeiro lançamento

```markdown
## Projeto em desenvolvimento — DD de mês de AAAA

Estamos organizando como o Arke vai funcionar, antes de desenvolver o aplicativo.

### O que avançou
- Definimos ... 
- Organizamos ...

> Essas mudanças são de planejamento. O aplicativo ainda não está disponível.
```

### Depois de uma versão realmente distribuída

```markdown
## Versão X.Y.Z — DD de mês de AAAA
Disponível para: iOS e/ou Android [apenas se confirmado]

### Novidades
- Agora você pode ...

### Melhorias
- Ficou mais fácil ...

### Correções
- Corrigimos um problema que ...

[O que continua em desenvolvimento: opcional; não prometer prazo]
```

## 4. Critérios editoriais

- Cada versão: título humano de até ~60 caracteres e abertura curta (~120 caracteres) pensando no modal.
- Preferir 1–5 pontos úteis, cada ponto até ~140 caracteres; versão longa pode ficar no GitHub.
- Incluir plataforma específica apenas quando for diferente.
- Separar bug fix discreto de novas funcionalidades; evitar tecnicismos mesmo quando a causa for técnica.
- Ordem: benefício mais relevante, seguida de melhorias e correções.
- Release não concluído? Adicionar texto como **rascunho interno no PR**, não no feed público de versões.

## 5. Quem faz e quando

1. Agent verifica se a tarefa muda algo **perceptível para o usuário**.
2. Redige sugestão leiga no contrato de tarefa/PR; sem afirmar disponibilidade.
3. Revisor valida factualidade, plataforma, escopo e português claro.
4. Responsável pelo produto aprova publicação.
5. Quando houver versão efetivamente liberada e confirmada, atualizar `CHANGELOG.md` e a fonte de dados do futuro modal segundo [NEWS-MODAL](../releases/NEWS-MODAL.md).
6. Sincronizar chamada “Novidades” do README com o último item **realmente público**; não duplicar manualmente textos divergentes.

## 6. Conduta em correções sensíveis

Nunca revelar exploração de vulnerabilidade ou dados privados. Se uma correção de segurança relevante for comunicada, descrever proteção e ação necessária sem divulgar passos de ataque. Corrigir ou retirar nota imprecisa com rastreabilidade, não reescrever silenciosamente o passado.

> Fonte humana do histórico: `CHANGELOG.md`. O modal é um canal de apresentação futuro, não uma fonte alternativa de verdade.
