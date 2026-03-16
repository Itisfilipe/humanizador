# Humanizador

Um skill para Claude Code que remove sinais de escrita gerada por IA em textos em português brasileiro, tornando-os mais naturais e humanos.

## Instalacao

### Recomendado (clonar direto no diretorio de skills do Claude Code)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Itisfilipe/humanizador.git ~/.claude/skills/humanizador
```

### Instalacao manual (apenas o arquivo de skill)

Se voce ja tem o repositorio clonado (ou baixou o `SKILL.md`), copie o arquivo de skill para o diretorio de skills do Claude Code:

```bash
mkdir -p ~/.claude/skills/humanizador
cp SKILL.md ~/.claude/skills/humanizador/
```

## Uso

No Claude Code, invoque o skill:

```
/humanizador

[cole seu texto aqui]
```

Ou peca ao Claude para humanizar o texto diretamente:

```
Por favor, humanize este texto: [seu texto]
```

## Visao geral

Baseado no guia [Wikipedia's "Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), mantido pelo WikiProject AI Cleanup, com padroes adaptados para portugues brasileiro. Este guia vem de observacoes de milhares de instancias de texto gerado por IA.

O skill tambem inclui uma auditoria final "obviamente gerado por IA" e uma segunda reescrita, para pegar cacoetes de IA que sobreviveram ao primeiro rascunho.

### Insight-chave da Wikipedia

> "LLMs usam algoritmos estatisticos para prever o que vem a seguir. O resultado tende ao resultado estatisticamente mais provavel, que se aplica a maior variedade de casos."

## 21 Padroes Detectados (com exemplos Antes/Depois)

### Padroes de conteudo

| # | Padrao | Antes | Depois |
|---|--------|-------|--------|
| 1 | **Inflacao de importancia** | "desempenha um papel fundamental no cenario..." | "coleta e publica os principais dados estatisticos" |
| 2 | **Conectivos excessivos** | "Alem disso... Nesse sentido... Diante do exposto..." | Remover ou usar conexoes naturais |
| 3 | **Construcoes impessoais** | "Pode-se afirmar que... Faz-se necessario..." | Voz ativa e direta |
| 4 | **Linguagem promocional** | "localizada no coracao do Nordeste, beleza incomparavel" | "tem um centro historico preservado" |
| 5 | **Gerundios superficiais** | "promovendo a inclusao... fortalecendo os lacos..." | Remover ou dar dados concretos |
| 6 | **Atribuicoes vagas** | "Especialistas afirmam que..." | "Um estudo de 2023 da USP mostrou..." |
| 7 | **Secoes formulaicas** | "Apesar dos desafios... perspectivas promissoras" | Fatos especificos sobre desafios reais |

### Padroes de linguagem

| # | Padrao | Antes | Depois |
|---|--------|-------|--------|
| 8 | **Vocabulario de IA** | "arcabouco robusto... alavancar... tangibilizar..." | "mudou a politica de avaliacao" |
| 9 | **Regra de tres** | "inovacao, colaboracao e crescimento" | Numero natural de itens |
| 10 | **Variacao forcada de sinonimos** | "protagonista... personagem principal... figura central..." | "protagonista" (repetir quando mais claro) |
| 11 | **Falsas gradacoes** | "dos primordios da civilizacao a era digital" | Listar topicos diretamente |

### Padroes de estilo

| # | Padrao | Antes | Depois |
|---|--------|-------|--------|
| 12 | **Travessao excessivo** | "a ferramenta — que foi — promete — algo que —" | Usar virgulas ou pontos |
| 13 | **Negrito excessivo** | "**gestao**, **comunicacao**, **analise**" | "gestao, comunicacao, analise" |
| 14 | **Listas com cabecalho em negrito** | "**Velocidade:** O sistema processa..." | Converter em prosa |
| 15 | **Emojis decorativos** | "🚀 Lancamento: 💡 Insight:" | Remover emojis |

### Padroes de comunicacao

| # | Padrao | Antes | Depois |
|---|--------|-------|--------|
| 16 | **Artefatos de chatbot** | "Otima pergunta! Espero ter ajudado!" | Remover completamente |
| 17 | **Disclaimers de limitacao** | "Embora informacoes especificas sejam limitadas..." | Encontrar fontes ou remover |
| 18 | **Tom servil** | "Excelente observacao! Voce tem toda razao!" | Responder diretamente |

### Preenchimento e hedging

| # | Padrao | Antes | Depois |
|---|--------|-------|--------|
| 19 | **Frases de preenchimento** | "Com o intuito de", "No que diz respeito a" | "Para", "Sobre" |
| 20 | **Hedging excessivo** | "pode-se potencialmente argumentar que poderia..." | "pode" |
| 21 | **Conclusoes genericas** | "O futuro e promissor" | Planos ou fatos especificos |

## Exemplo completo

**Antes (tom de IA):**
> Otima pergunta! Aqui esta um texto sobre o tema. Espero que ajude!
>
> A inteligencia artificial configura-se como um marco transformador no cenario tecnologico contemporaneo, desempenhando um papel fundamental na evolucao do desenvolvimento de software. No cenario atual, essas ferramentas inovadoras — situadas na intersecao entre pesquisa e pratica — estao remodelando a forma como engenheiros idealizam, iteram e entregam solucoes, evidenciando seu papel crucial nos fluxos de trabalho modernos.
>
> Em sua essencia, a proposta de valor e clara: otimizar processos, fomentar colaboracao e promover alinhamento. Nao se trata apenas de autocomplete; trata-se de desbloquear criatividade em escala. A ferramenta serve como catalisador. O assistente funciona como parceiro. O sistema se consolida como alicerce da inovacao.
>
> - 💡 **Velocidade:** A geracao de codigo e significativamente mais rapida.
> - 🚀 **Qualidade:** A qualidade do output foi aprimorada.
> - ✅ **Adocao:** O uso continua crescendo.
>
> Apesar dos desafios tipicos de tecnologias emergentes, o ecossistema continua a prosperar. O futuro e promissor. Se precisar de mais alguma coisa, e so falar!

**Depois (humanizado):**
> Assistentes de codigo com IA te deixam mais rapido nas partes chatas. Nao em tudo. Definitivamente nao em arquitetura.
>
> Eles mandam bem em boilerplate: config, scaffolding de teste, refatoracao repetitiva. Tambem mandam bem em parecer certo estando errado. Eu ja aceitei sugestao que compilou, passou no lint e ainda assim errou o ponto, porque eu parei de prestar atencao.
>
> As pessoas com quem converso caem em dois grupos. Uns usam como autocomplete pra tarefas chatas e revisam cada linha. Outros desativam depois que a ferramenta fica sugerindo padroes que nao querem. As duas reacoes fazem sentido.
>
> As metricas de produtividade sao escorregadias. O GitHub pode dizer que usuarios do Copilot "aceitam 30% das sugestoes", mas aceitar nao e acertar, e acertar nao e gerar valor. Se voce nao tem testes, ta basicamente chutando.

## Referencias

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) - Fonte primaria
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) - Organizacao mantenedora
- [Humanizer](https://github.com/blader/humanizer) - Skill original em ingles por [@blader](https://github.com/blader)

## Historico de versoes

- **1.0.0** - Versao inicial adaptada para portugues brasileiro

## Licenca

MIT
