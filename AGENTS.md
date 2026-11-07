# Guia para agentes

Este arquivo explica como alterar o Humanizer PT-BR sem quebrar o pacote ou o prompt.

## Conteúdo do repositório

O Humanizer é uma skill escrita em Markdown. `SKILL.md` é o prompt lido pelos agentes. Não há etapa de compilação.

Mantenha a portabilidade. Não limite as instruções a um ou dois agentes. Esta tradução acompanha o projeto original em português brasileiro; evite mudanças de comportamento sem necessidade.

## Arquivos principais

- `SKILL.md` é a fonte de verdade e o único arquivo de skill. Contém metadados YAML portáveis, a explicação dos padrões de escrita de IA e padrões numerados em seis seções, por força e frequência.
- `README.md` explica instalação, uso e padrões.
- `CHANGELOG.md` contém notas de versão, das mais recentes às antigas. Notas antigas mantêm a numeração de sua versão.
- `.claude-plugin/plugin.json` descreve o plugin Claude e aponta o carregador para `SKILL.md` na raiz.
- `.claude-plugin/marketplace.json` permite adicionar este repositório como marketplace do Claude.
- `.cursor-plugin/plugin.json` descreve o plugin Cursor. Omita `skills` para carregar o `SKILL.md` da raiz.
- `agents/openai.yaml` contém nome de exibição, descrição curta e prompt padrão para agentes compatíveis com OpenAI.
- `scripts/validate-package.py` verifica arquivos e valores compartilhados.

## Regras para alterações

Mantenha `SKILL.md` e `README.md` sincronizados.

- **Padrões:** Numere a partir de 1, sem lacunas, dos mais fortes e frequentes aos demais. Crie um padrão apenas quando nenhum existente o cobrir; prefira integrar o sinal a um padrão existente. Ao adicionar, remover ou renumerar, atualize tabelas, título da seção no README e referências §. O validador deriva a quantidade dos títulos e confere os nomes no README.
- **Versão:** Mantenha a mesma versão em `metadata.version`, no primeiro título numérico de `CHANGELOG.md` e nos manifests Claude e Cursor. Não adicione `version` ao nível superior da skill.
- **Compatibilidade:** Mantenha instruções de instalação e uso portáveis. Claude Code, Cursor, OpenCode e Codex são exemplos, não limites.
- **Descrição:** Os manifests usam a primeira frase da descrição de `SKILL.md`.
- **Tamanho:** Cada palavra de `SKILL.md` é lida a cada uso. O limite é 5.500 palavras; acréscimos precisam justificar seu custo.
- **Histórico:** Registre mudanças de comportamento e correções não óbvias em `CHANGELOG.md`.
- **Verificações:** Antes de publicar, execute `python3 scripts/validate-package.py`, `npx skills add . --list` e `claude plugin validate .`.
- **Origem:** Preserve a licença MIT e a autoria original. Identifique adaptações desta tradução e mantenha referências históricas ao repositório de origem.

## Estilo de escrita

Use linguagem simples em comentários, prompts, documentação, descrições, mensagens de validação e relatos de progresso.

- Comece pela ideia principal.
- Use palavras comuns e voz ativa.
- Prefira frases e parágrafos curtos.
- Use o mesmo termo para o mesmo item.
- Use "deve" para requisitos.
- Use títulos, listas e tabelas quando ajudarem.
- Remova palavras repetidas ou desnecessárias.
- Limite siglas e explique termos técnicos.
- Evite negativas duplas.
- Preserve identificadores, comandos, caminhos, campos de schema, citações, expressões observadas e exemplos que determinam comportamento. Traduza a prosa dos exemplos sem perder o padrão demonstrado; adapte convenções exclusivas do inglês explicitamente.
- Preserve todo o significado técnico.

## Edição da skill

- Mantenha os metadados YAML válidos.
- Trate o prompt abaixo dos metadados como o produto.
- Prefira uma instrução breve e clara a novas exceções ou explicações repetidas.
