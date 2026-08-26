# humanizer-br

Editor de texto em português que tira as marcas de escrita de IA.

Você entrega um texto, ela devolve reescrito sem os vícios que denunciam máquina. No caminho ela mexe no ritmo das frases, porque texto humano varia o tamanho e texto de IA quase nunca varia.

## Antes e depois

**Antes**

> No cenário atual, vale destacar que a escrita com inteligência artificial desempenha um papel fundamental na produção de conteúdo. Especialistas dizem que a tecnologia oferece insights valiosos — uma entrega não apenas rápida, mas também consistente. Com o objetivo de manter uma comunicação robusta, muitas equipes vêm mergulhando em ferramentas cada vez mais abrangentes, refletindo uma transformação mais ampla do mercado. O futuro parece promissor.

**Depois**

> Muita gente escreve com IA hoje, e o problema não é a velocidade. É que sai tudo com a mesma cadência, e com aquele parágrafo final morno que podia estar em qualquer outro texto. Dá pra sentir na segunda linha. O que me incomoda é que, em algum ponto daquele texto, ninguém precisou decidir nada.

Tem uma armadilha na hora de reescrever, e ela é fácil de cair. Você tira o texto inflado, coloca uma fila de frases curtas no lugar, e o resultado fica limpo e continua soando a máquina. Cinco frases de tamanho parecido em sequência são um padrão tão visível quanto o travessão.

A primeira versão deste exemplo caiu exatamente nisso, com frases de 6, 11, 8, 7 e 13 palavras. O texto com cara de IA, logo acima, tem frases de 19, 16, 25 e 4. Ele variava mais que a correção dele. A versão que ficou no "depois" vai de 6 a 21 palavras, e a frase curta está ali para quebrar a longa que veio antes.

## O que saiu, item por item

Cada linha abaixo está catalogada no SKILL.md, com a seção que trata dela.

| No texto original | Por que sai | Seção |
| --- | --- | --- |
| "No cenário atual" | Editorialização | Editorialização |
| "vale destacar que" | Conectivo de enchimento | Conectivos e Advérbios Excessivos |
| "desempenha um papel fundamental" | Cópula artificial | Cópulas Artificiais |
| "Especialistas dizem" | Atribuição vaga | Atribuições Vagas |
| "insights valiosos" | Expressão corporativa | Expressões Corporativas e Promocionais |
| "—" | Travessão | Pontuação e Formatação |
| "não apenas rápida, mas também consistente" | Paralelismo negativo | Paralelismos Negativos |
| "Com o objetivo de" | Preenchimento | Preenchimento e Hedging |
| "robusta", "abrangentes" | Adjetivo vago e promocional | Vocabulário Proibido |
| "mergulhando" | Verbo metafórico | Verbos Inflados e Metafóricos |
| "refletindo uma transformação mais ampla" | Gerúndio conclusivo | Análises Superficiais com Gerúndio |
| "O futuro parece promissor" | Conclusão genérica | Conclusões Genéricas |

## Instalar

Precisa de Node instalado. O `npx` vem junto.

**Claude Code**

```bash
npx skills add msigor/humanizer-br -a claude-code -g
```

**Cursor**

```bash
npx skills add msigor/humanizer-br -a cursor -g
```

**Codex**

```bash
npx skills add msigor/humanizer-br -a codex -g
```

O `-g` instala pro usuário, e a skill fica disponível em qualquer projeto. Tire o `-g` se quiser a skill só dentro do projeto onde você está.

Roda o mesmo comando sem `-a` e ele pergunta quais ferramentas você usa:

```bash
npx skills add msigor/humanizer-br
```

**Instalação manual**

Baixe o repositório e copie a pasta `skills/humanizer-br/` para o diretório da sua ferramenta:

| Ferramenta | Destino |
| --- | --- |
| Claude Code | `~/.claude/skills/` |
| Cursor | `~/.cursor/skills/` |
| Codex | `~/.codex/skills/` |

O resultado final precisa ser um `SKILL.md` dentro de uma pasta chamada `humanizer-br`. Exemplo no Claude Code: `~/.claude/skills/humanizer-br/SKILL.md`.

**Atualizar e remover**

```bash
npx skills update humanizer-br
npx skills remove humanizer-br
```

## Usar

Abra a ferramenta, cole o texto e peça a revisão. No Claude Code você chama por `/humanizer-br`, e nas outras funciona pedir pelo nome no meio da frase:

```
usa a skill humanizer-br neste texto:

<cola o texto aqui>
```

Funciona em texto que você escreveu e em texto que a IA escreveu. E no que passou pelos dois, que costuma ser o caso.

## O que volta

A resposta vem em quatro blocos, nessa ordem:

1. **Versão humanizada**, a primeira reescrita
2. **Auditoria anti-IA**, o que ainda soa automático nessa primeira versão
3. **Versão final**, a reescrita depois de corrigir o que a auditoria apontou
4. **Resumo das melhorias**, opcional, explica o que mudou

O segundo bloco existe porque uma passada só não resolve. A skill critica o próprio trabalho antes de te entregar.

## O que ela não faz

Ela edita texto que já existe. Não escreve do zero, e não inventa dado nem fonte pra preencher o buraco que sobra quando uma frase vazia é removida. Se o texto perdeu volume na reescrita, o volume era enchimento.

Também não prometo nota em detector de IA. O critério aqui é leitura humana, e um classificador pode achar o que quiser do resultado.

## De onde vem o conteúdo

As listas de vocabulário e as estruturas proibidas saem de duas fontes:

- [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), o guia que os editores da Wikipedia usam pra identificar texto gerado por máquina
- Sampaio, R. C. (2026). *Prompts para diminuir os marcadores de escrita por IA*. [Substack cardososampaio](https://cardososampaio.substack.com)

A Wikipedia entra com o catálogo de padrões, observado por gente que revisa artigo em volume alto. O Sampaio entra com o recorte de português brasileiro, que é onde o guia em inglês não alcança.

## Licença

MIT. Use e modifique como quiser. Ver [LICENSE](LICENSE).
