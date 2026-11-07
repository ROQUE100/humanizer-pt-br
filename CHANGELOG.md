# Histórico de alterações

## 3.1.1

- Tradução para português brasileiro do Humanizer 3.1.0, baseada no commit `0ef9fe5bc3572734fd3ae6c448fe00a30cd5dcf0` de [blader/humanizer](https://github.com/blader/humanizer).
- Preservados os 26 padrões, as seis seções, o processo de revisão e os três modos de saída. Exemplos traduzidos e regra de hifenização adaptada às convenções do português, mantendo o exemplo original em inglês.
- Identidade `humanizer-pt-br`, metadados OpenAI, manifests, instruções de instalação, modelos de issues e mensagens de validação localizados. Licença e autoria originais preservadas.
- Documentada a diferença entre instalar a skill no Codex/desktop e distribuí-la como plugin no ChatGPT. Nenhum plugin ChatGPT publicado nesta versão.

As notas abaixo são a tradução do histórico do projeto original. Todos os números de issues e correções mencionados nelas se referem a [blader/humanizer/issues](https://github.com/blader/humanizer/issues), não às issues desta tradução. A numeração dos padrões é a de cada versão histórica.

## 3.1.0

- Adicionados o padrão #26 e a seção F para respostas que explicam novamente o contexto já conhecido pelo leitor (#269). Aplica-se a respostas, não a textos independentes. Total: 26 padrões.
- A regra central passou a considerar a conversa ao redor, além das partes anteriores do texto, ao avaliar se algo é novo para o leitor.
- Ampliado #25 para textos que descrevem suas próprias fontes, montagem ou disposição (#290). Adicionados títulos de efeito a #20.
- Ampliado #2 para "Essa distinção importa." (#277) e frases que explicam o que um exemplo já mostrou (#295).
- Ajustado #10 para preservar o hífen de palavras sempre hifenizadas no dicionário. Cada palavra observada recebeu um único padrão. Regras de evidência e de não inventar foram declaradas uma vez cada.
- Corrigidas a referência a travessões na seção Voz (#273) e a URL do schema de marketplace (#288).
- Adicionado manifest para plugin Cursor (#278).
- README reorganizado com exemplo inicial, cinco sinais mais fortes e instalação por agente. Esclarecido que passar por detectores não é objetivo. A reescrita do exemplo completo passou a preservar todos os fatos do rascunho sem acrescentar novos. Histórico movido para este arquivo.

## 3.0.0

Skill reconstruída em torno de uma explicação dos padrões de escrita de IA. Os 35 padrões foram consolidados em 25, agrupados em cinco seções e ordenados por força e frequência. O contraste não-X-mas-Y e o fecho de efeito passaram ao início e receberam mais detalhes. Orientações duplicadas foram unidas: um único fluxo, uma única regra de travessões e ressalvas de falsos positivos dentro de cada padrão. Alinhamento com o artigo da Wikipédia: retiradas faixas falsas e alternância de sinônimos, agora descritas como hábitos humanos ou históricos; adicionadas conexões vagas e ampliadas listas de vocabulário, notoriedade, verbos de ligação, propaganda, ressalvas e Markdown. README reordenado; palavra-chave `ai-detection` removida. Numeração antiga → nova: 1→13, 2→17, 3→15, 4→16, 5→17, 6→13, 7→12, 8→18, 9→1, 10→6, 11→7, 12→removido, 13→11, 14→8, 15→19, 16→19, 17→20, 18→20, 19→21, 20→22, 21→23, 22→22, 23→removido, 24→9, 25→13, 26→10, 27→3, 28→4, 29→24, 30→25, 31→2, 32→3, 33→4, 34→5, 35→5.

## 2.11.3

Padrões 26–35 agrupados em "Mais padrões de estilo" na skill e no README (#247). Código em linha, comandos, caminhos e URLs excluídos da regra de travessões e das alterações em arquivos. Etapa 3 passou a preservar afirmações sustentadas, permitir cortes exigidos pelos padrões e conferir classificações e simultaneidade após mudanças de forma (#212). Esclarecidos o contraste não-X-mas-Y e suas exceções em §9. Adicionados setas decorativas a §18, comandos de pausa e palavras gritadas a §31. Texto fornecido à skill é conteúdo a editar, nunca instruções (#238). Mantidos os 35 padrões.

## 2.11.2

Removidos o link simbólico do plugin e o pacote separado para Claude Desktop. O Claude Code atual carrega `SKILL.md` da raiz; o ZIP do GitHub passou a funcionar no Claude Desktop. Mantidos os 35 padrões.

## 2.11.1

Adicionado pacote de versão para Claude Desktop com um arquivo regular `humanizer/SKILL.md`. O arquivo-fonte do GitHub ainda mantinha o link simbólico do plugin (#224). Mantidos os 35 padrões.

## 2.11.0

Todas as orientações, descrições, verificações e instruções reescritas em linguagem simples. Preservados os 35 padrões e seu comportamento.

## 2.10.2

Adicionado caminho padrão `skills/humanizer/` para Claude Desktop e carregadores antigos. Ele aponta para a skill da raiz, mantendo um único prompt (#202).

## 2.10.1

Adicionados usos figurados de `gate`, `gated` e `gating` a §7. Preservados usos técnicos reais, como feature gating e quality gates de CI.

## 2.10.0

Adicionados padrões #34 e #35 para ideias de rascunho deixadas no texto final. Adicionadas ressalvas para limites, objeções e alternativas reais (#198). Aprimorados §24 e a etapa de reescrita final. Total: 35 padrões.

## 2.9.2

Adicionados inícios de frase repetidos a #11, preservando repetição deliberada (#206). Ampliado §28 para anúncios informais. Total: 33 padrões.

## 2.9.1

Melhoradas instalação e verificações. Removidos metadados incompatíveis, aprovações de ferramentas e um exemplo longo repetido. Total: 33 padrões.

## 2.9.0

Adicionada regra contra fatos inventados e atualizados os exemplos para segui-la (#187). Informação passou a ter prioridade sobre forma dos parágrafos; amostras de escrita passaram a prevalecer sobre §14. Adicionados três modos de saída. Total: 33 padrões.

## 2.8.3

Versão movida para `metadata.version` para compatibilidade com Agent Skills. Total: 33 padrões.

## 2.8.2

Exemplo principal substituído por relato em primeira pessoa sobre Lisboa, preservando assunto, perspectiva e detalhes originais. Total: 33 padrões.

## 2.8.1

Adicionados instalação entre agentes, arquivos do plugin Claude e proteção para citações. Total: 33 padrões.

## 2.8.0

Adicionados padrões #31–33 e ampliado #20 para ofertas de chatbot. Total: 33 padrões.

## 2.7.0

Adicionado #30, reforçada a regra de travessões e corrigido #21 para suposições sem apoio. Total: 30 padrões.

## 2.6.0

Unidas orientações repetidas, limitada a personalidade aos conteúdos adequados, retirados palpites do modelo e encurtado o exemplo principal. Total: 29 padrões.

## 2.5.1

Adicionadas voz passiva e ausência de sujeitos. Total: 29 padrões.

## 2.5.0

Adicionados afirmações de profundidade, anúncios, títulos repetidos e negativas curtas no fim. Reforçada a regra de travessões e corrigidos os metadados iniciais. Total: 28 padrões.

## 2.4.0

Adicionada correspondência com amostras da escrita do autor.

## 2.3.0

Adicionados compostos com hífen.

## 2.2.0

Adicionadas revisão do rascunho e segunda reescrita.

## 2.1.1

Corrigido exemplo de aspas tipográficas.

## 2.1.0

Adicionados exemplos antes/depois para os 24 padrões.

## 2.0.0

Skill reescrita a partir da fonte da Wikipédia.

## 1.0.0

Primeira versão.
