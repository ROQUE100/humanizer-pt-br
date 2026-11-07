# Humanizer PT-BR

Tradução para português brasileiro do [Humanizer, de blader/Siqi Chen](https://github.com/blader/humanizer), mantida por [ROQUE100](https://github.com/ROQUE100). Base: versão 3.1.0, commit [`0ef9fe5`](https://github.com/blader/humanizer/commit/0ef9fe5bc3572734fd3ae6c448fe00a30cd5dcf0). Mantém os 26 padrões, a estrutura e o processo do original, com adaptação das convenções linguísticas. Versão desta tradução: 3.1.1.

O projeto original é patrocinado por [cfo.ai](https://cfo.ai). Essa atribuição não indica patrocínio desta tradução.

[![Estrelas no GitHub](https://img.shields.io/github/stars/ROQUE100/humanizer-pt-br?style=flat)](https://github.com/ROQUE100/humanizer-pt-br/stargazers)

O Humanizer PT-BR torna a escrita de IA mais natural sem mudar seu conteúdo. Baseia-se no guia [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), usado por editores da Wikipédia para reconhecer textos de IA, e funciona no Claude Code, Codex e em outros agentes compatíveis com skills.

**Antes:**
> Estou empolgado em anunciar que os rascunhos compartilhados finalmente chegaram! 🚀 Durante meses, nossa equipe se afogou em arquivos chamados final_v7.docx — e sabíamos que precisava haver um jeito melhor. Agora duas pessoas podem editar o mesmo documento ao mesmo tempo, com cada mudança aparecendo ao vivo para ambas. Não é apenas uma funcionalidade; é uma nova forma de colaborar. Os comentários ficam ancorados na frase exata a que se referem, mesmo quando o texto ao redor muda. E o melhor? Está disponível hoje em todos os planos, totalmente de graça. Pense nisso.

**Depois:**
> Os rascunhos compartilhados estão disponíveis a partir de hoje. Durante meses, nossa equipe trocou arquivos chamados final_v7.docx, então criamos uma forma de duas pessoas editarem o mesmo documento ao mesmo tempo, vendo as mudanças uma da outra ao vivo. Os comentários ficam presos à frase a que se referem, mesmo quando o texto ao redor muda. É gratuito em todos os planos.

O projeto original relata que, em um teste cego, os avaliadores preferiram sua reescrita ao texto de IA nas 16 comparações ([#229 no original](https://github.com/blader/humanizer/issues/229)). Esse resultado não é uma avaliação desta tradução.

O Humanizer edita para leitores humanos. Passar por detectores de IA não é um objetivo; o original informa que detectores ainda sinalizam a maioria de suas saídas.

## Os cinco sinais mais fortes

Estes são os sinais mais comuns de escrita de IA. Uma ocorrência já justifica a revisão:

1. **Não X, mas Y:** "Não é apenas uma funcionalidade, é uma transformação."
2. **Fechos de efeito:** "Pense nisso."
3. **Frases que parecem profundas:** "Em sua essência, o que realmente importa é..."
4. **Abertura encenada:** "A questão é a seguinte." "Sinceramente?"
5. **Discussão com uma objeção inexistente:** "Não estou dizendo X, mas..."

Ao todo, o Humanizer verifica [26 padrões](#os-26-padrões).

## Instalação

O identificador da skill traduzida é `humanizer-pt-br`. A forma de invocação depende do agente.

### Claude Code

```text
/plugin marketplace add ROQUE100/humanizer-pt-br
/plugin install humanizer-pt-br@humanizer-pt-br
```

O plugin responde a `/humanizer-pt-br:humanizer-pt-br`. Requer Claude Code 2.1.142 ou posterior. Em versões anteriores, use `npx skills add ROQUE100/humanizer-pt-br --global --agent claude-code`.

### Codex

```bash
npx skills add ROQUE100/humanizer-pt-br --global --agent codex
```

Para invocar explicitamente no Codex, use `$humanizer-pt-br`.

### ChatGPT

A documentação da OpenAI prevê skills independentes no aplicativo desktop e skills empacotadas como plugins para distribuição no ChatGPT web, desktop e celular. Este repositório contém a skill e seus metadados OpenAI; a publicação como plugin do ChatGPT é uma etapa separada. Instalar no Codex não instala automaticamente no ChatGPT web. Consulte [como criar e distribuir skills](https://learn.chatgpt.com/docs/build-skills) e a disponibilidade na sua conta.

### Claude.ai e Claude Desktop

Baixe este repositório como ZIP (**Code → Download ZIP**) e envie-o como skill nas configurações.

### Outros agentes

```bash
npx skills add ROQUE100/humanizer-pt-br --global --agent '*'
```

Isso instala a skill nos agentes compatíveis com o Skills CLI, incluindo Gemini CLI, GitHub Copilot e Windsurf. Omita `--global` para instalar somente no projeto atual. Para agentes não reconhecidos pelo CLI, copie `SKILL.md` para a pasta de skills correspondente.

## Uso

Invoque a skill diretamente no agente que usa comandos com barra:

```text
/humanizer-pt-br

[cole seu texto aqui]
```

Ou peça em linguagem natural:

```text
Humanize este texto: [seu texto]
```

Para reescrever um arquivo, indique o caminho:

```text
Humanize a prosa em docs/launch-post.md
```

### Acompanhar sua voz

Para aproximar a reescrita do seu estilo, inclua uma amostra:

```text
/humanizer-pt-br

Esta é uma amostra da minha escrita para referência de estilo:
[cole 2 a 3 parágrafos escritos por você]

Agora humanize este texto:
[cole o texto de IA]
```

O Humanizer acompanha ritmo, vocabulário, pontuação e particularidades intencionais da amostra, inclusive travessões quando você os usa.

## Como funciona

Um modelo de linguagem escolhe o que provavelmente vem a seguir, favorecendo formulações que atendem a muitos leitores e assuntos. Uma pessoa escreve para um leitor e um assunto específicos. Os sinais procurados são formas dessa escolha genérica: anunciar importância sem acrescentar fatos, aplicar ritmo ou formatação por fórmula, dar peso exagerado a um fato comum, deixar resíduos da conversa ou explicar novamente o que o leitor já sabe.

Segundo o guia [Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), modelos usam algoritmos estatísticos para prever a continuação; o resultado tende ao que tem maior probabilidade de servir ao maior número de situações.

O Humanizer marca os sinais mais fortes primeiro, faz uma primeira versão sem ficar preso à estrutura original, confere os padrões e as afirmações e escreve a versão final. Não deve inventar. Nomes, números, datas, citações, referências e outros detalhes factuais precisam vir da fonte ou do autor. Se faltar um detalhe, pergunta em vez de inventar.

Ao receber texto colado, entrega a primeira versão, uma crítica curta do que ainda soa artificial e a versão final. Ao receber um arquivo, altera somente a prosa e preserva código, dados, metadados e destinos de links. Textos pessoais mantêm opiniões e peculiaridades; textos técnicos e de referência continuam neutros e claros.

## Os 26 padrões

Os padrões estão ordenados por força e frequência. Os cinco primeiros justificam edição em uma ocorrência. Os marcados como *fracos isoladamente* exigem outros sinais no mesmo trecho, pois um autor cuidadoso pode usá-los de propósito.

### A. Encenação em vez de afirmação

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 1 | **Não X, mas Y** | "Não é apenas X, é Y", "Isso não significa X. Significa Y." | Expresse a ideia diretamente |
| 2 | **Fechos de efeito e fragmentos dramáticos** | "Esse é o verdadeiro ganho." após cada seção; "Isso mostra a importância de..." após um exemplo; "Sem referência. Sem nostalgia." | Corte fechos repetitivos e una os fragmentos em uma afirmação específica |
| 3 | **Frases que parecem profundas** | "Em sua essência, o que importa é...", "Simetria é a linguagem da confiança" | Substitua a fórmula pela afirmação específica |
| 4 | **Abertura encenada antes da ideia** | "Vamos mergulhar", "Sinceramente? Depende..." | Remova a preparação e apresente a ideia |
| 5 | **Discussão com uma objeção inexistente** | "Isso não é principalmente sobre...", "Uma abordagem tentadora seria..." | Remova a objeção ou opção artificial e preserve afirmações reais |

### B. Ritmo por fórmula

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 6 | **Trios forçados** | "inovação, inspiração e conhecimento"; três exemplos e uma lição | Use quantos itens o sentido pedir |
| 7 | **Inícios de frase repetidos** | "Ela reparou... Ela reparou... Ela guardou..." | Una as frases ou mude o sujeito |
| 8 | **Travessões como conexão universal** (*fraco isoladamente*) | "instituições—não as pessoas—mas isso continua—" | Use pontos, vírgulas, dois-pontos ou parênteses; acompanhe a amostra do autor |
| 9 | **Ressalvas acumuladas** (*fraco isoladamente*) | "poderia potencialmente ser possível argumentar" | Mantenha ressalvas sustentadas pela fonte |
| 10 | **Compostos com hífen em excesso** (*fraco isoladamente*) | "the report is high-quality" | No inglês, siga a posição e o dicionário; no português, a ortografia do composto |
| 11 | **Voz passiva e sujeitos ausentes** (*fraco isoladamente*) | "Nenhum arquivo de configuração necessário" | Identifique quem age quando isso ajudar |

### C. Exagero e autoridade emprestada

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 12 | **Vocabulário recorrente de IA** | "explorar a fundo... testemunho... panorama... evidenciando" | Use palavras simples |
| 13 | **Importância exagerada** | "marcando um momento crucial", "apesar dos desafios... prospera", "o futuro é promissor" | Preserve o fato e termine no último dado concreto |
| 14 | **Conexão ou associação vaga** | "associado à liderança de", "em conexão com" | Explicite a relação informada pela fonte |
| 15 | **Gerúndios com análise superficial** | "simbolizando... refletindo... evidenciando..." | Preserve apenas o que a fonte sustenta |
| 16 | **Linguagem publicitária** | "situada na deslumbrante região" | Diga o que a coisa é |
| 17 | **Autoridade emprestada** | "Especialistas acreditam...", "citada no NYT, BBC, FT e The Hindu" | Identifique a fonte e o que disse ou remova a afirmação ou lista |
| 18 | **Evitar ser, estar e ter** | "serve como... conta com... ostenta" | Use ser, estar e ter quando equivalentes |

### D. Formatação por fórmula

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 19 | **Negrito decorativo** | "**OKRs**, **KPIs**"; "**Desempenho:** O desempenho melhorou" | Remova o negrito e transforme rótulos desnecessários em prosa |
| 20 | **Títulos decorativos** | "Negociações Estratégicas E Parcerias", "🚀 Fase de lançamento:", "A decisão, em uma tela" | Use maiúscula inicial, retire decoração e identifique o conteúdo |
| 21 | **Aspas tipográficas** (*fraco isoladamente*) | `disse “o projeto”` | `disse "o projeto"` |

### E. Resíduos da conversa e do rascunho

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 22 | **Resíduos de chatbot** | "Ótima pergunta! ... Espero que ajude!" | Remova a moldura e preserve o conteúdo |
| 23 | **Avisos sobre limites de conhecimento e suposições** | "Embora os detalhes nas fontes sejam limitados, parece..." | Diga o que a fonte mostra ou corte a frase |
| 24 | **Título repetido na primeira frase** | "## Desempenho" + "Velocidade importa." | Deixe o título cumprir sua função |
| 25 | **Falar do documento em vez do assunto** | "Esta função foi adicionada para substituir...", "compilado de...", "A tabela abaixo compara..." | Descreva o assunto; explique convenções apenas quando não forem evidentes |

### F. Escrever para o leitor errado

| # | Padrão | Antes | Depois |
|---|--------|-------|--------|
| 26 | **Explicar de novo o que o leitor já sabe** | Uma resposta percorre diagnóstico e provas antes de chegar à decisão | Comece pela decisão e deixe o diagnóstico e a comprovação para o chamado seguinte |


## Exemplo completo

**Antes (com aparência de IA):**
> Passei recentemente cinco dias inesquecíveis em Lisboa em outubro passado, e preciso dizer — essa cidade roubou meu coração. Desde o momento em que entrei no meu charmoso hotel no histórico bairro de Alfama, soube que estava num lugar muito especial.
>
> Sim, as famosas ladeiras são um desafio — com incontáveis escadas entre o hotel e todo o resto, minhas pernas sentiram cada uma! — mas cada subida recompensa com vistas panorâmicas de tirar o fôlego, que fazem tudo valer a pena.
>
> Nenhuma viagem estaria completa sem o icônico elétrico 28, num trajeto de cerca de quarenta minutos com outros viajantes ansiosos por capturar a magia. E a comida? Simplesmente divina. Embora os pastéis de nata da Pastéis de Belém sejam um tesouro nacional, meu favorito veio de uma joia escondida na Graça, ainda quente do forno.
>
> Mas o que torna Lisboa especial não são apenas os pontos turísticos — é a sensação. Basta subir um ou dois quarteirões a partir das praças principais para descobrir uma cidade mais tranquila e autêntica, que convida a desacelerar e saborear cada momento.
>
> Claro, o imperdível Castelo de São Jorge oferece vistas deslumbrantes dos telhados. As filas podem ser longas, mas a experiência vale muito a pena para qualquer amante de história ou viajante curioso.
>
> Eu voltaria? Com certeza — na primavera e com sapatos melhores! Lisboa não é apenas um lugar para visitar; é um lugar para se apaixonar, de novo e de novo. ✨

**Depois:**
> Passei cinco dias em Lisboa em outubro passado. Meu hotel ficava no alto de Alfama, com muitas escadas entre ele e todo o resto, e minhas pernas sentiram cada uma. As vistas lá de cima compensavam a subida.
>
> Todo mundo recomenda o elétrico 28, então fui. O trajeto levou cerca de quarenta minutos, e a maioria dos passageiros era de turistas fotografando pelas janelas. Os pastéis da Pastéis de Belém são os famosos, mas meu favorito veio de um lugar na Graça, ainda quente do forno.
>
> A parte de Lisboa de que mais gostei começa um ou dois quarteirões acima das praças principais, onde as ruas ficam tranquilas e ninguém tem pressa. O Castelo de São Jorge tem boas vistas dos telhados e uma fila longa para vê-las.
>
> Eu voltaria, na primavera e com sapatos melhores.

## Fontes

- [Wikipédia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), fonte da lista de padrões.
- [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_AI_Cleanup), responsável pela página.
- [Humanizer original](https://github.com/blader/humanizer), de blader/Siqi Chen, fonte desta tradução.

## Histórico de versões

Consulte [CHANGELOG.md](CHANGELOG.md).

## Licença

MIT. O arquivo [LICENSE](LICENSE) preserva integralmente o aviso original de Siqi Chen.

Se o Humanizer ajudar, uma estrela facilita que outras pessoas o encontrem.
