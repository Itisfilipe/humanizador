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

Pergunta: "Quais sao os impactos do trabalho remoto no Brasil?"

**Antes (resposta tipica de IA):**
> O trabalho remoto no Brasil passou por uma transformacao significativa nos ultimos anos, especialmente apos a pandemia de COVID-19. Nesse contexto, e importante destacar que o trabalho remoto trouxe diversos beneficios para os profissionais brasileiros. Alem disso, a flexibilidade proporcionada pelo home office permitiu que trabalhadores de regioes menos favorecidas pudessem acessar oportunidades em grandes centros, contribuindo para a descentralizacao do mercado de trabalho e fomentando o desenvolvimento regional.
>
> No que diz respeito a produtividade, estudos indicam que profissionais em regime remoto tendem a apresentar niveis de produtividade iguais ou superiores. Essa constatacao desafia paradigmas tradicionais de gestao e evidencia a necessidade de uma abordagem mais holistica.
>
> - 💡 **Flexibilidade:** Profissionais podem trabalhar de qualquer lugar, promovendo qualidade de vida.
> - 🚀 **Produtividade:** Estudos apontam ganhos de produtividade em diversos setores.
> - ✅ **Inclusao:** O modelo remoto pode contribuir para a inclusao de profissionais de regioes diversas.
>
> Diante do exposto, pode-se afirmar que o trabalho remoto configura-se como uma tendencia irreversivel no cenario brasileiro. Apesar dos desafios inerentes, as perspectivas sao promissoras, impulsionando a inovacao e fortalecendo a competitividade do pais no cenario global.

**Depois (humanizado):**
> Antes da pandemia, trabalho remoto no Brasil era coisa de dev em startup. Depois de 2020, virou rotina pra milhoes de pessoas.
>
> O que mudou de verdade foi geografico. Gente de Recife e Floripa comecou a pegar vaga em SP sem se mudar. Salario de capital com custo de vida de cidade menor. Durou um tempo, ate as empresas comecarem a ajustar faixa por localidade.
>
> Todo mundo usa produtividade como argumento, mas os dados sao baguncados. A FGV fez uma pesquisa em 2022 que mostrou aumento de produtividade auto-reportada — que, convenhamos, nao prova nada.
>
> O lado ruim: muita gente que conheco trabalha mais horas em casa do que no escritorio. Nao tem hora pra fechar o laptop. E no interior, internet por radio que cai na chuva ainda e a realidade.
>
> Em 2025, a onda de "volta ao escritorio" ta forte. Varias empresas grandes querem presencial 3-4 dias. Se vai durar, ninguem sabe.

## Referencias

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) - Fonte primaria
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) - Organizacao mantenedora
- [Humanizer](https://github.com/blader/humanizer) - Skill original em ingles por [@blader](https://github.com/blader)

## Historico de versoes

- **1.0.0** - Versao inicial adaptada para portugues brasileiro

## Licenca

MIT
