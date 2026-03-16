# Humanizador

Um skill para Claude Code que remove sinais de escrita gerada por IA em textos em português brasileiro, tornando-os mais naturais e humanos.

## Instalação

### Recomendado (clonar direto no diretório de skills do Claude Code)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Itisfilipe/humanizador.git ~/.claude/skills/humanizador
```

### Instalação manual (apenas o arquivo de skill)

Se você já tem o repositório clonado (ou baixou o `SKILL.md`), copie o arquivo de skill para o diretório de skills do Claude Code:

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

Ou peça ao Claude para humanizar o texto diretamente:

```
Por favor, humanize este texto: [seu texto]
```

## Visão geral

Baseado no guia [Wikipedia's "Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), mantido pelo WikiProject AI Cleanup, com padrões adaptados para português brasileiro. Este guia vem de observações de milhares de instâncias de texto gerado por IA.

O skill também inclui uma auditoria final "obviamente gerado por IA" e uma segunda reescrita, para pegar cacoetes de IA que sobreviveram ao primeiro rascunho.

### Insight-chave da Wikipedia

> "LLMs usam algoritmos estatísticos para prever o que vem a seguir. O resultado tende ao resultado estatisticamente mais provável, que se aplica à maior variedade de casos."

## 21 Padrões Detectados (com exemplos Antes/Depois)

### Padrões de conteúdo

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 1 | **Inflação de importância** | "desempenha um papel fundamental no cenário..." | "coleta e publica os principais dados estatísticos" |
| 2 | **Conectivos excessivos** | "Além disso... Nesse sentido... Diante do exposto..." | Remover ou usar conexões naturais |
| 3 | **Construções impessoais** | "Pode-se afirmar que... Faz-se necessário..." | Voz ativa e direta |
| 4 | **Linguagem promocional** | "localizada no coração do Nordeste, beleza incomparável" | "tem um centro histórico preservado" |
| 5 | **Gerúndios superficiais** | "promovendo a inclusão... fortalecendo os laços..." | Remover ou dar dados concretos |
| 6 | **Atribuições vagas** | "Especialistas afirmam que..." | "Um estudo de 2023 da USP mostrou..." |
| 7 | **Seções formulaicas** | "Apesar dos desafios... perspectivas promissoras" | Fatos específicos sobre desafios reais |

### Padrões de linguagem

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 8 | **Vocabulário de IA** | "arcabouço robusto... alavancar... tangibilizar..." | "mudou a política de avaliação" |
| 9 | **Regra de três** | "inovação, colaboração e crescimento" | Número natural de itens |
| 10 | **Variação forçada de sinônimos** | "protagonista... personagem principal... figura central..." | "protagonista" (repetir quando mais claro) |
| 11 | **Falsas gradações** | "dos primórdios da civilização à era digital" | Listar tópicos diretamente |

### Padrões de estilo

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 12 | **Travessão excessivo** | "a ferramenta — que foi — promete — algo que —" | Usar vírgulas ou pontos |
| 13 | **Negrito excessivo** | "**gestão**, **comunicação**, **análise**" | "gestão, comunicação, análise" |
| 14 | **Listas com cabeçalho em negrito** | "**Velocidade:** O sistema processa..." | Converter em prosa |
| 15 | **Emojis decorativos** | "🚀 Lançamento: 💡 Insight:" | Remover emojis |

### Padrões de comunicação

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 16 | **Artefatos de chatbot** | "Ótima pergunta! Espero ter ajudado!" | Remover completamente |
| 17 | **Disclaimers de limitação** | "Embora informações específicas sejam limitadas..." | Encontrar fontes ou remover |
| 18 | **Tom servil** | "Excelente observação! Você tem toda razão!" | Responder diretamente |

### Preenchimento e hedging

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 19 | **Frases de preenchimento** | "Com o intuito de", "No que diz respeito a" | "Para", "Sobre" |
| 20 | **Hedging excessivo** | "pode-se potencialmente argumentar que poderia..." | "pode" |
| 21 | **Conclusões genéricas** | "O futuro é promissor" | Planos ou fatos específicos |

## Exemplo completo

Pergunta: "Quais são os impactos do trabalho remoto no Brasil?"

**Antes (resposta típica de IA):**
> O trabalho remoto no Brasil passou por uma transformação significativa nos últimos anos, especialmente após a pandemia de COVID-19. Nesse contexto, é importante destacar que o trabalho remoto trouxe diversos benefícios para os profissionais brasileiros. Além disso, a flexibilidade proporcionada pelo home office permitiu que trabalhadores de regiões menos favorecidas pudessem acessar oportunidades em grandes centros, contribuindo para a descentralização do mercado de trabalho e fomentando o desenvolvimento regional.
>
> No que diz respeito à produtividade, estudos indicam que profissionais em regime remoto tendem a apresentar níveis de produtividade iguais ou superiores. Essa constatação desafia paradigmas tradicionais de gestão e evidencia a necessidade de uma abordagem mais holística.
>
> - 💡 **Flexibilidade:** Profissionais podem trabalhar de qualquer lugar, promovendo qualidade de vida.
> - 🚀 **Produtividade:** Estudos apontam ganhos de produtividade em diversos setores.
> - ✅ **Inclusão:** O modelo remoto pode contribuir para a inclusão de profissionais de regiões diversas.
>
> Diante do exposto, pode-se afirmar que o trabalho remoto configura-se como uma tendência irreversível no cenário brasileiro. Apesar dos desafios inerentes, as perspectivas são promissoras, impulsionando a inovação e fortalecendo a competitividade do país no cenário global.

**Depois (humanizado):**
> Antes da pandemia, trabalho remoto no Brasil era coisa de dev em startup. Depois de 2020, virou rotina pra milhões de pessoas.
>
> O que mudou de verdade foi geográfico. Gente de Recife e Floripa começou a pegar vaga em SP sem se mudar. Salário de capital com custo de vida de cidade menor. Durou um tempo, até as empresas começarem a ajustar faixa por localidade.
>
> Todo mundo usa produtividade como argumento, mas os dados são bagunçados. A FGV fez uma pesquisa em 2022 que mostrou aumento de produtividade auto-reportada — que, convenhamos, não prova nada.
>
> O lado ruim: muita gente que conheço trabalha mais horas em casa do que no escritório. Não tem hora pra fechar o laptop. E no interior, internet por rádio que cai na chuva ainda é a realidade.
>
> Em 2025, a onda de "volta ao escritório" tá forte. Várias empresas grandes querem presencial 3-4 dias. Se vai durar, ninguém sabe.

## Referências

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) - Fonte primária
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) - Organização mantenedora
- [Humanizer](https://github.com/blader/humanizer) - Skill original em inglês por [@blader](https://github.com/blader)

## Histórico de versões

- **1.0.0** - Versão inicial adaptada para português brasileiro

## Licença

MIT
