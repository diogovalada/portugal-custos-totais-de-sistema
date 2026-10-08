# Custos totais do sistema elétrico português

Estudo aberto e reproduzível para comparar o custo económico, a adequação e os principais impactos de portefólios elétricos alternativos para Portugal no contexto ibérico.

O projeto terminou a primeira auditoria metodológica e de dados e entra agora numa fatia vertical exploratória. Ainda não existe um resultado quantitativo sobre qual portefólio é preferível. Uma análise independente de planeamento e adequação é realizável; uma réplica operacional integral da REN, da distribuição ou da estabilidade dinâmica não é realizável apenas com dados abertos.

## Começar aqui

- [Estado corrente](PROJECT_STATUS.md): decisões provisórias, conclusões, bloqueios e próximos passos.
- [Plano de execução](execution-plan.md): fatia vertical, três checkpoints, materialidade e sequência mínima.
- [Desenho do projeto](project-design.md): perguntas, âmbito, limites, viabilidade e governação.
- [Contabilidade de custos](cost-accounting.md): fronteira económica e prevenção de dupla contagem.
- [Metodologia de modelação](modelling-methodology.md): arquitetura, ferramentas, incerteza, adequação e validação.
- [Cenários ibéricos](scenarios-iberia.md): procura, política, interligações, clima e ramos espanhóis.
- [Dossier nuclear](nuclear.md): opções nucleares espanholas e hipóteses para um eventual projeto português.
- [Índice de dados](data/index.md): estado das fontes, lacunas e ligações para as auditorias temáticas.
- [Registo de decisões](decision-log.md): decisões adotadas e alterações de posição.
- [Auditoria de investigação de 2026-08-12](archive/research-audit-2026-08-12.md): síntese da ronda de 100 agentes, incertezas reduzidas, lacunas duras e efeito do limite de concorrência.
- [Benchmark de âmbito de 2026-08-12](archive/scope-benchmark-2026-08-12.md): comparação com estudos suecos, NEA, RTE e o framework britânico para controlar underscope e scope creep.

O documento monolítico anterior foi preservado como [snapshot histórico](archive/project-memory-2026-08-10.md). Não deve ser atualizado nem citado como posição corrente quando exista um documento canónico mais recente. As auditorias datadas preservam a evidência de cada ronda de investigação; as conclusões correntes continuam a pertencer aos documentos canónicos e aos registos.

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
LICENSE                    # licença de código, por decidir
LICENSE-DOCS               # licença de documentação, por decidir
CITATION.cff
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
environment/
src/
tests/
data/
  raw/
  interim/
  processed/
  manifests/
```

`registers/` contém metadados de investigação. `data/` fica reservado aos inputs do modelo, transformações e manifests. Dados sem licença de redistribuição não devem ser versionados; nesses casos serão publicados, quando permitido, o script de aquisição, a proveniência, o checksum e os derivados autorizados.

Os nomes acima descrevem o estado-alvo; os ficheiros de licença e citação só serão criados depois da decisão de P1. Código, documentação e derivados de dados podem exigir licenças distintas, e cada dataset distribuído conservará também a sua proveniência e condições próprias.

## Âmbito de trabalho atual

O default científico é um estudo elétrico continental PT–ES, com França como fronteira limitada e ilhas separadas. A implementação começa menor: 2–5 zonas, um ano horário, capacidades fixas, hidro/storage agregados e PyPSA/HiGHS. PyPSA-Eur pode fornecer receitas ou inputs seletivos, mas o workflow completo não é requisito de P0. Só depois do pipeline vertical funcionar entram investimento, três anos meteorológicos e adequação dos portefólios. Isto continua a ser uma hipótese de trabalho até C1.
