# Humanizador

Um skill pro Claude Code que remove sinais de escrita gerada por IA em textos em português brasileiro, tornando-os mais naturais e humanos.

## Instalação

### Recomendado (clonar direto no diretório de skills do Claude Code)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Itisfilipe/humanizador.git ~/.claude/skills/humanizador
```

### Instalação manual (apenas o arquivo de skill)

Se você já tem o repositório clonado (ou baixou o `SKILL.md`), copie o arquivo de skill pro diretório de skills do Claude Code:

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

Ou peça ao Claude pra humanizar o texto diretamente:

```
Por favor, humanize este texto: [seu texto]
```

## Visão geral

Baseado na página [Wikipedia "Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), mantida pelo WikiProject AI Cleanup, com padrões adaptados **semanticamente** para o português brasileiro. Tradução literal não funciona: os cacoetes de IA em português são diferentes dos cacoetes em inglês.

O skill inclui uma auditoria final "obviamente gerado por IA" e uma segunda reescrita, para pegar cacoetes que sobreviveram ao primeiro rascunho.

### Princípio central: humanizar não é informalizar

O objetivo não é transformar todo texto num post casual. Um texto formal, bem estruturado e informativo pode ser perfeitamente humano. O skill respeita o registro do texto original (formal, semiformal, casual) e não força gírias, fragmentos artificiais, primeira pessoa ou opiniões onde não cabem. O texto reescrito deve ser **bem escrito**, não apenas "não-IA".

### Isso não engana detectores de IA

Este skill remove padrões que fazem texto soar artificial **para leitores humanos** (conectivos empilhados, vocabulário inflado, tom de redação do ENEM, etc). Detectores de IA como GPTZero e Undetectable AI funcionam de forma diferente: analisam padrões **estatísticos** (perplexidade, distribuição de tokens, previsibilidade) que não têm relação com estilo. O texto reescrito continua sendo gerado por IA, e os detectores vão continuar identificando isso. O objetivo do skill é qualidade de escrita, não evasão de detecção.

### Insight-chave da Wikipedia

> "LLMs usam algoritmos estatísticos para prever o que vem a seguir. O resultado tende ao mais estatisticamente provável, que se aplica à maior variedade de casos."

## 28 Padrões detectados (com exemplos Antes/Depois)

### Padrões de conteúdo

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 1 | **Inflação de importância** | "desempenha um papel fundamental no cenário..." | "coleta e publica os principais dados estatísticos" |
| 2 | **Conectivos excessivos** | "Além disso... Nesse sentido... Diante do exposto..." | Remover ou conectar de forma natural |
| 3 | **Construções impessoais** | "Pode-se afirmar que... Trata-se de..." | Voz ativa e direta |
| 4 | **Linguagem promocional** | "aninhada no coração do Nordeste, beleza incomparável" | "tem um centro histórico preservado" |
| 5 | **Gerúndios pendurados** | "promovendo a inclusão... fortalecendo os laços..." | Remover ou dar dados concretos |
| 6 | **Atribuições vagas** | "Especialistas afirmam que..." | "Um estudo de 2023 da USP mostrou..." |
| 7 | **Seções formulaicas** | "Apesar dos desafios... perspectivas promissoras" | Fatos específicos sobre desafios reais |

### Padrões de linguagem

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 8 | **Vocabulário de IA** | "arcabouço robusto... alavancar... tangibilizar..." | "mudou a política de avaliação" |
| 9 | **Evitação do verbo "ser"** | "configura-se como... serve como... consolida-se como..." | "é" |
| 10 | **Paralelismos negativos** | "Não se trata apenas de X, trata-se de Y" | Dizer direto o que a coisa é |
| 11 | **Regra de três** | "inovação, colaboração e crescimento" | Número natural de itens |
| 12 | **Variação forçada de sinônimos** | "protagonista... personagem principal... figura central..." | "protagonista" (repetir quando mais claro) |
| 13 | **Falsas gradações** | "dos primórdios da civilização à era digital" | Listar tópicos diretamente |
| 14 | **Nominalização excessiva** | "a realização da implementação da otimização" | "a equipe otimizou" |
| 15 | **Alternância mecânica de adversativas** | "Todavia... Entretanto... Não obstante... Contudo..." | "mas" |

### Padrões de estilo

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 16 | **Travessão em excesso** | "a ferramenta — que foi — promete — algo que —" | Usar vírgulas, pontos ou parênteses |
| 17 | **Negrito excessivo** | "**gestão**, **comunicação**, **análise**" | "gestão, comunicação, análise" |
| 18 | **Listas com cabeçalho em negrito** | "**Velocidade:** O sistema processa..." | Converter em prosa |
| 19 | **Emojis decorativos** | "🚀 Lançamento: 💡 Insight:" | Remover emojis |
| 20 | **Markdown e artefatos técnicos** | `turn0search0`, `utm_source=chatgpt.com` | Remover |
| 21 | **Title Case em títulos** | "Negociações Estratégicas E Parcerias" | "Negociações estratégicas e parcerias" |

### Padrões de comunicação

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 22 | **Artefatos de chatbot** | "Ótima pergunta! Espero ter ajudado!" | Remover completamente |
| 23 | **Disclaimers de limitação** | "Embora informações específicas sejam limitadas..." | Encontrar fontes ou remover |
| 24 | **Tom servil** | "Excelente observação! Você tem toda razão!" | Responder diretamente |

### Preenchimento e hedging

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 25 | **Frases de preenchimento** | "Com o intuito de", "No que tange a" | "Para", "Sobre" |
| 26 | **Hedging excessivo** | "pode-se potencialmente argumentar que poderia..." | "pode" |
| 27 | **Conclusões genéricas** | "O futuro é promissor" | Planos ou fatos específicos |
| 28 | **Tom de redação do ENEM** | "Conforme preconiza... Sob essa ótica... Faz-se necessário que o Estado..." | Linguagem direta e concreta |

### Bônus: erros comuns ao humanizar e falsos positivos

O skill inclui uma seção de **erros comuns** (forçar informalidade, inventar anedotas, fragmentar frases artificialmente, perder informação, trocar clichê de IA por clichê de colunista) e uma seção de **falsos positivos**: gramática perfeita, vocabulário amplo, tom formal e texto longo não são sinais de IA. O que entrega é a **combinação** de padrões.

## Exemplo completo

Pergunta: "Escreva um post de blog sobre o impacto da IA na educação brasileira."

**Antes (resposta típica de IA):**
> # O Impacto da Inteligência Artificial na Educação Brasileira
>
> A inteligência artificial deixou de ser coisa de filme de ficção científica e já faz parte do dia a dia de milhões de brasileiros, mesmo que muita gente nem perceba. Na educação, essa transformação está acontecendo de forma acelerada, e o Brasil se encontra num momento decisivo: ou abraça essas ferramentas de maneira inteligente, ou corre o risco de ampliar ainda mais as desigualdades que já existem no sistema educacional do país. Plataformas adaptativas, tutores virtuais e sistemas de correção automática já são realidade em diversas escolas e universidades, mas a adoção ainda é muito desigual entre as redes pública e privada.
>
> Um dos maiores benefícios que a IA traz para a educação é a possibilidade de personalizar o aprendizado. Cada aluno aprende num ritmo diferente, e qualquer professor que já enfrentou uma sala com 40 estudantes sabe que é praticamente impossível dar atenção individualizada para todo mundo. Ferramentas baseadas em IA conseguem identificar onde cada aluno está com dificuldade e adaptar o conteúdo de acordo, oferecendo exercícios extras em pontos fracos e avançando mais rápido onde o estudante já domina o assunto. Isso não substitui o professor, mas funciona como um assistente que está disponível 24 horas por dia.
>
> Ao mesmo tempo, não dá para ignorar os desafios que isso traz no contexto brasileiro. A gente está falando de um país onde muitas escolas ainda não têm acesso estável à internet, onde faltam computadores e onde boa parte dos professores não recebeu formação para lidar com essas tecnologias. Implementar soluções de IA sem resolver esses problemas básicos de infraestrutura é como tentar construir o telhado de uma casa que ainda não tem parede. Existe também a questão da privacidade dos dados dos alunos, um tema que ainda é tratado com pouca seriedade por muitas instituições.
>
> Outro ponto que gera bastante debate é o uso de ferramentas como o ChatGPT e similares por parte dos estudantes. Muitas instituições reagiram com medo, tentando proibir o uso dessas tecnologias, mas a tendência que tem se mostrado mais produtiva é a de integrar essas ferramentas no processo de ensino. Algumas universidades brasileiras já estão reformulando suas avaliações para que os alunos usem IA como parte do trabalho, focando mais no pensamento crítico e na capacidade de fazer boas perguntas do que na simples reprodução de conteúdo decorado. Isso, no fundo, é preparar o aluno para o mercado de trabalho que já existe lá fora.
>
> O caminho que a educação brasileira vai percorrer com a inteligência artificial depende muito das decisões que estão sendo tomadas agora. Investir em formação de professores, garantir infraestrutura mínima para todas as escolas e criar políticas públicas que orientem o uso responsável dessas tecnologias são passos fundamentais. A IA não vai resolver todos os problemas da educação no Brasil, seria ingenuidade acreditar nisso, mas tem potencial para ser uma ferramenta poderosa de democratização do conhecimento. O importante é que essa transformação aconteça de forma inclusiva, e não apenas para quem já tem acesso a tudo.

**Depois (humanizado):**
> # O impacto da inteligência artificial na educação brasileira
>
> A inteligência artificial já faz parte do cotidiano de milhões de brasileiros, mesmo que muita gente não perceba. Na educação, a mudança é visível: plataformas adaptativas, tutores virtuais e sistemas de correção automática já funcionam em escolas e universidades pelo país. Mas a adoção é desigual. Escolas particulares avançam rápido, enquanto boa parte da rede pública ainda não tem o básico para acompanhar.
>
> O benefício mais evidente na sala de aula é a personalização. Qualquer professor que já enfrentou uma turma de 40 alunos sabe que dar atenção individual a cada um é inviável. Ferramentas de IA identificam onde cada aluno tem dificuldade e ajustam o conteúdo: mais exercícios nos pontos fracos, avanço mais rápido onde o estudante já domina a matéria. Não substitui o professor, mas funciona como um reforço disponível a qualquer hora. O problema é onde isso precisa funcionar. Muitas escolas brasileiras ainda não têm internet estável, faltam computadores e a maioria dos professores não recebeu formação para usar essas tecnologias. Adotar soluções de IA nessas condições não resolve nada. A privacidade dos dados dos alunos é outra questão que segue mal resolvida.
>
> O ChatGPT e ferramentas similares provocaram pânico em muitas universidades, que tentaram proibir o uso. A abordagem que tem funcionado melhor é oposta: integrar a IA ao processo de avaliação. A PUC-RS e a Unicamp, por exemplo, já reformularam provas e trabalhos para que o aluno use essas ferramentas, mas precise demonstrar pensamento crítico sobre o resultado. O foco sai da reprodução de conteúdo decorado e vai para a capacidade de formular perguntas e avaliar respostas. Isso faz sentido: o mercado de trabalho já opera assim.
>
> O que vai acontecer com a educação brasileira depende de decisões que estão sendo tomadas agora. Formar professores para lidar com IA, garantir que escolas tenham pelo menos internet funcional e criar regras claras de uso são os passos mais urgentes. A IA não vai consertar os problemas estruturais da educação no Brasil, mas ignorá-la também não é opção.

## Referências

- [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) - Fonte primária
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup) - Organização mantenedora
- [Humanizer](https://github.com/blader/humanizer) - Skill original em inglês por [@blader](https://github.com/blader)

## Histórico de versões

- **2.1.0** - Correção de filosofia: humanizar não é informalizar. Adicionadas seções sobre erros comuns ao humanizar, princípio de respeitar o registro original, e verificação de qualidade da escrita. Exemplos reescritos com texto de qualidade em vez de texto casual forçado.
- **2.0.0** - Reescrita completa: 28 padrões (vs 21), adaptação semântica pro PT-BR em vez de tradução literal, padrões exclusivos do português (tom de redação do ENEM, nominalização, alternância de adversativas, evitação de cópula), seção de falsos positivos
- **1.0.0** - Versão inicial

## Licença

MIT
