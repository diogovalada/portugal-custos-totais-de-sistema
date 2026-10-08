# Estado do projeto

> Estado editorial: working  
> Última atualização: 2026-08-13
> Âmbito: síntese corrente e navegação  
> Documento canónico para: estado, bloqueios e próximos passos  
> Rever quando: for tomada uma decisão, concluída uma auditoria ou alterada uma fonte temporalmente instável

## Situação atual

O projeto está a transitar da auditoria metodológica e de dados para P0, a primeira fatia vertical exploratória. Ainda não foi construído o modelo quantitativo nem selecionado um portefólio energético.

**FACT — viabilidade:** é possível produzir independentemente um estudo credível de custo de recursos e adequação para o sistema elétrico continental português/ibérico. Com dados abertos não é possível alegar uma réplica operacional validada pela REN, um modelo integral da distribuição ou validação nacional de estabilidade transitória/EMT.

**ASSUMPTION — default de P0:** primeira versão electricity-only do bulk system continental PT+ES; França limitada; Açores e Madeira separados; PyPSA com HiGHS; 2–5 zonas; 8 760 horas; capacidades fixas; hidro e armazenamento agregados; um ano exploratório. PyPSA-Eur é fonte/receita opcional, não workflow obrigatório. Investimento, três weather years e adequação entram apenas depois de o pipeline vertical funcionar.

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
| Computação | P0 com 2–5 zonas cabe num portátil; 10–30 clusters e UC × weather × ensemble × ELCC só entram por materialidade | [Metodologia](docs/modelling-methodology.md) |
| Âmbito | O core elétrico não tem omissão estrutural nova; distribuição profunda, estabilidade, externalidades, incidência, ilhas e economy-wide devem permanecer satélites ou estudos separados salvo materialidade demonstrada | [Desenho](docs/project-design.md) |

Nenhum destes domínios deve ser descrito em bloco como totalmente inacessível. É necessário distinguir: aberto e reutilizável; público mas fragmentado/licença incerta; existente e solicitável; reservado; ou ainda inexistente.

## Decisões abertas para C1

- perspetiva do headline: custo PT+ES e métrica separada para Portugal;
- um horizonte/ano-alvo principal e trajetória brownfield mínima;
- ano-base monetário e distribuição da taxa social;
- formulação final da procura e dos dois denominadores;
- contrafactuais focais e cap operacional de emissões;
- fronteira exata de França e padrão de fiabilidade nos runs forward.

Já estão adotados a separação das ilhas e a classificação `core` / `satellite` / `deferred`; electricity-only PT+ES continental continua a ser o default proposto para confirmação em C1. Granularidade, número de weather years, distribuição, externalidades, modelos secundários e licenças de saída são decisões de implementação ou release; não bloqueiam P0 nem acrescentam itens a C1 sem materialidade demonstrada.

As escolhas científicas e quantitativas estão registadas em [`registers/assumptions.csv`](registers/assumptions.csv). Licenças são verificadas quando uma fonte entra num artefacto preservado e as licenças de saída são decididas antes da release. Escolhas duráveis só passam a decisões quando entram no [registo de decisões](docs/decision-log.md).

## Riscos prioritários

Resumo derivado de [`registers/data-gaps.csv`](registers/data-gaps.csv), snapshot de 2026-08-12; as classificações canónicas e efeitos na execução permanecem nesse registo.

Críticos: parâmetros térmicos validados por unidade; curvas e restrições hidráulicas finas, incluindo Tâmega; custos finais de projetos privados; modelos dinâmicos; séries insulares sub-horárias; fronteira/denominador da procura; cap elétrico de emissões ainda por construir.

Importantes mas contornáveis: crosswalk unidade–nó; cadastro de baterias; custo marginal local de distribuição; série canónica de curtailment; modelo de transmissão; lifecycle/repowering; potencial renovável realizável; forecast errors/reservas futuras; licenças REN/ESIOS/SNIRH.

Já suficientes para uma primeira versão: grande frota via ENTSO-E/DGEG/REN/ESIOS; balanço e balancing via REN/SIME/ENTSO-E/ESIOS; hidro por reservatório via SNIRH/MITECO/CEDEX; rede/cargas agregadas via REN/E-REDES/REE; custos agregados das redes reguladas; clima futuro via PECD v4.2.

## Próximos passos

O foco imediato é P0 no [plano de execução](docs/execution-plan.md):

- criar ambiente mínimo e uma fixture de balanço;
- obter apenas os inputs necessários a um ano horário PT–ES com França limitada;
- executar capacidades fixas com hidro/storage agregados;
- produzir balanço físico, cobertura/resíduos e um esqueleto de custo de recursos;
- usar os problemas observados para fechar o charter-lite C1, em vez de antecipar todos os módulos;
- preparar pedidos administrativos apenas para lacunas que o protótipo demonstre serem materiais.

Não iniciar ainda GenX, Antares, UC anual, 10–30 clusters, externalidades monetizadas ou o ledger financeiro integral.

## Bloqueio atual

Não existe bloqueio que impeça P0. O charter ainda não satisfaz C1 e, portanto, nenhum output exploratório pode ser apresentado como comparação interpretável de portefólios. Isso é uma limitação de claims, não uma razão para adiar o primeiro modelo executável.
