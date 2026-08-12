# Estado do projeto

> Estado editorial: working  
> Última atualização: 2026-08-12  
> Âmbito: síntese corrente e navegação  
> Documento canónico para: estado, bloqueios e próximos passos  
> Rever quando: for tomada uma decisão, concluída uma auditoria ou alterada uma fonte temporalmente instável

## Situação atual

O projeto está na fase de protocolo, arquitetura e inventário de dados. Não foi ainda construído o modelo quantitativo nem selecionado um portefólio energético.

**FACT — viabilidade:** é possível produzir independentemente um estudo credível de custo de recursos e adequação para o sistema elétrico continental português/ibérico. Com dados abertos não é possível alegar uma réplica operacional validada pela REN, um modelo integral da distribuição ou validação nacional de estabilidade transitória/EMT.

**ASSUMPTION — default de trabalho:** primeira versão electricity-only do bulk system continental PT+ES; França limitada; Açores e Madeira separados; PyPSA-Eur com HiGHS; 10–30 clusters; 8 760 horas; reservatórios, bombagem e baterias explícitos; 3–5 anos meteorológicos iniciais; validação UC/adequação separada.

## Conclusões consolidadas

A auditoria documental de 2026-08-12, realizada por 100 agentes de investigação organizados em coordenadores temáticos e subagentes, está preservada em [research-audit-2026-08-12.md](docs/archive/research-audit-2026-08-12.md). Os documentos temáticos e os registos abaixo contêm o estado canónico posterior à reconciliação.

| Domínio | Conclusão corrente | Documento canónico |
|---|---|---|
| Unidades e nós | Backbone público para grandes unidades e coordenadas de várias centrais; crosswalk físico ao nó continua incompleto | [Ativos](docs/data/generation-and-storage-assets.md) |
| Parâmetros unitários | Existem priors abertos e a REN recebe valores reais; detalhe português por grupo não é aberto | [Ativos](docs/data/generation-and-storage-assets.md) |
| Hidro | Planeamento por reservatório PT–ES é viável; hill charts, tailwater, limites por grupo e Tâmega operacional continuam críticos | [Hidro](docs/data/hydro.md) |
| Reservas e redispatch | Grande parte está pública no SIME a 15 minutos; falta contexto físico e sinais de segundos | [Operações](docs/data/system-operations.md) |
| Distribuição | Dados de subestação/zona são ricos; grafo elétrico e custos nodais não são públicos | [Rede e estabilidade](docs/data/grid-and-stability.md) |
| Baterias | Totais oficiais por corte existem; cadastro PT–ES harmonizado MW/MWh/nó/estado/BTM continua confidence-scored | [Ativos](docs/data/generation-and-storage-assets.md) |
| Custos realizados | Redes reguladas e projetos selecionados têm dados; all-in privado permanece fraco | [Custos de projetos](docs/data/project-costs.md) |
| Estabilidade | Requisitos, indicadores e planeamento são públicos; estados e modelos dinâmicos não | [Rede e estabilidade](docs/data/grid-and-stability.md) |
| Nuclear português | Não existe projeto definido cujos custos possam ser observados; exige análise paramétrica | [Nuclear](docs/nuclear.md) |
| Ilhas | Mensal/anual e qualidade são públicos; operação sub-horária não é aberta | [Ilhas](docs/data/islands.md) |
| Fiabilidade | LOLE oficial 1,46 h/ano PT e 1,5 h/ano ES; VOLL oficiais zonais identificados | [Metodologia](docs/modelling-methodology.md) |
| Clima | PECD v4.2 resolve o backbone futuro licenciado; conversão por bacia e caudas continuam ensemble uncertainty | [Metodologia](docs/modelling-methodology.md) |
| Transmissão | PyPSA-Eur/OSM suporta DC de planeamento; IGM/CGM e estado operacional não são abertos | [Rede e estabilidade](docs/data/grid-and-stability.md) |
| Espanha | P3 zonal e hidro por reservatório são possíveis; unidade–nó, parâmetros UC e rede elétrica oficial continuam assimétricos | [Índice de dados](docs/data/index.md) |
| Computação | LP 10–30 clusters é viável; UC × weather × ensemble × ELCC domina risco e orçamento | [Metodologia](docs/modelling-methodology.md) |

Nenhum destes domínios deve ser descrito em bloco como totalmente inacessível. É necessário distinguir: aberto e reutilizável; público mas fragmentado/licença incerta; existente e solicitável; reservado; ou ainda inexistente.

## Decisões abertas

- fronteira principal: Portugal continental, MIBEL ou PT+ES+FR;
- horizonte, anos-alvo e ano-base monetário;
- eletricidade apenas ou sector coupling numa fase posterior;
- granularidade espacial e representação de França/Marrocos;
- procura exógena ou serviços energéticos parcialmente endógenos;
- taxa social e harmonização/uso dos VOLL e padrões de fiabilidade já identificados;
- número de anos meteorológicos e desenho estocástico;
- profundidade do módulo de distribuição;
- inclusão das ilhas no paper principal ou em estudos separados;
- externalidades a monetizar;
- sequência e critério de aceitação dos pilotos GenX e Antares;
- definição normativa do cap elétrico de emissões e tratamento de imports/lifecycle;
- taxonomia final de procura direta versus carga bruta e maturidade de novas cargas;
- licenças de saída distintas para código, documentação e derivados de dados, mais metadados de citação.

As escolhas científicas e quantitativas estão registadas em [`registers/assumptions.csv`](registers/assumptions.csv). A política de licenças é um entregável de P1; todas só passam a decisões quando entram no [registo de decisões](docs/decision-log.md).

## Riscos prioritários

Resumo derivado de [`registers/data-gaps.csv`](registers/data-gaps.csv), snapshot de 2026-08-12; as classificações canónicas e efeitos na execução permanecem nesse registo.

Críticos: parâmetros térmicos validados por unidade; curvas e restrições hidráulicas finas, incluindo Tâmega; custos finais de projetos privados; modelos dinâmicos; séries insulares sub-horárias; fronteira/denominador da procura; cap elétrico de emissões ainda por construir.

Importantes mas contornáveis: crosswalk unidade–nó; cadastro de baterias; custo marginal local de distribuição; série canónica de curtailment; modelo de transmissão; lifecycle/repowering; potencial renovável realizável; forecast errors/reservas futuras; licenças REN/ESIOS/SNIRH.

Já suficientes para uma primeira versão: grande frota via ENTSO-E/DGEG/REN/ESIOS; balanço e balancing via REN/SIME/ENTSO-E/ESIOS; hidro por reservatório via SNIRH/MITECO/CEDEX; rede/cargas agregadas via REN/E-REDES/REE; custos agregados das redes reguladas; clima futuro via PECD v4.2.

## Próximos passos

O foco imediato é fechar o gate `G1` da fase `P1` definida no [plano de execução](docs/execution-plan.md):

- converter as escolhas de fronteira, setores, horizonte, moeda, desconto, procura e fiabilidade em decisões ou sensibilidades delimitadas;
- especificar o schema dos três ledgers e os testes de dupla contagem;
- definir tolerâncias de reconciliação e critérios de alegação antes do primeiro resultado;
- validar, com uma fixture sintética, o caminho aquisição → transformação → ledger → testes;
- medir os inputs mínimos de P2 e preparar apenas os pedidos administrativos correspondentes;
- construir o contrato neutro de inputs/outputs e fixtures que permitam pilotos PyPSA–GenX–Antares sem pipelines duplicados;
- congelar a ficha de contrafactual e os dois ledgers de procura antes de qualquer cenário político.

Estas ações são deliberadamente de curto horizonte. A ordem posterior, os entregáveis e os envelopes de recursos pertencem exclusivamente a [execution-plan.md](docs/execution-plan.md).

## Bloqueio atual

O charter ainda não foi adotado: `A-SCOPE-001`, `A-SCOPE-002` e várias escolhas `TBD` impedem considerar `G1` satisfeito. Não existe ainda bloqueio externo que impeça trabalho preparatório de P1.
