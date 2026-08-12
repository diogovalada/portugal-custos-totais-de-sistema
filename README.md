# Custos totais do sistema elétrico português

Estudo aberto e reproduzível para comparar o custo económico, a adequação e os principais impactos de portefólios elétricos alternativos para Portugal no contexto ibérico.

O projeto encontra-se na fase de desenho metodológico e auditoria de dados. Ainda não existe um resultado quantitativo sobre qual portefólio é preferível. A conclusão atual é apenas sobre a viabilidade do estudo: uma análise independente de nível de planeamento e adequação é realizável; uma réplica operacional integral da REN, da distribuição ou da estabilidade dinâmica não é realizável apenas com dados abertos.

## Começar aqui

- [Estado corrente](PROJECT_STATUS.md): decisões provisórias, conclusões, bloqueios e próximos passos.
- [Plano de execução](docs/execution-plan.md): fases, dependências, entregáveis, gates e recursos.
- [Desenho do projeto](docs/project-design.md): perguntas, âmbito, limites, viabilidade e governação.
- [Contabilidade de custos](docs/cost-accounting.md): fronteira económica e prevenção de dupla contagem.
- [Metodologia de modelação](docs/modelling-methodology.md): arquitetura, ferramentas, incerteza, adequação e validação.
- [Cenários ibéricos](docs/scenarios-iberia.md): procura, política, interligações, clima e ramos espanhóis.
- [Dossier nuclear](docs/nuclear.md): opções nucleares espanholas e hipóteses para um eventual projeto português.
- [Índice de dados](docs/data/index.md): estado das fontes, lacunas e ligações para as auditorias temáticas.
- [Registo de decisões](docs/decision-log.md): decisões adotadas e alterações de posição.

O documento monolítico anterior foi preservado como [snapshot histórico](docs/archive/project-memory-2026-08-10.md). Não deve ser atualizado nem citado como posição corrente quando exista um documento canónico mais recente.

## Convenções de conhecimento

Os documentos distinguem quatro categorias:

- **FACT** — afirmação apoiada por uma fonte identificada e com data de verificação;
- **ASSUMPTION** — hipótese de modelação ainda sujeita a sensibilidade;
- **DECISION** — escolha metodológica ou de governação adotada;
- **OPEN** — questão ainda não resolvida.

As fontes, pressupostos e lacunas têm identificadores estáveis nos ficheiros em [`registers/`](registers/README.md). Um estado editorial `verified` significa que o documento foi revisto, não que todos os factos permaneçam verdadeiros indefinidamente. Política, software, projetos, capacidades e licenças devem ser reverificados antes de cada release.

## Estrutura prevista

```text
README.md
PROJECT_STATUS.md
docs/
  execution-plan.md
  project-design.md
  cost-accounting.md
  modelling-methodology.md
  scenarios-iberia.md
  nuclear.md
  decision-log.md
  data/
  archive/
registers/
data/
  raw/
  interim/
  processed/
  manifests/
```

`registers/` contém metadados de investigação. `data/` fica reservado aos inputs do modelo, transformações e manifests. Dados sem licença de redistribuição não devem ser versionados; nesses casos serão publicados, quando permitido, o script de aquisição, a proveniência, o checksum e os derivados autorizados.

## Âmbito de trabalho atual

O default de trabalho é um primeiro estudo apenas elétrico do sistema continental PT–ES, com França representada como fronteira limitada, cronologia horária, vários anos meteorológicos e PyPSA-Eur/HiGHS. Açores e Madeira são tratados como sistemas separados. Isto é uma hipótese de trabalho, não uma decisão científica fechada.
