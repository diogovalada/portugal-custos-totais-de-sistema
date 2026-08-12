# Metodologia de modelação, incerteza e validação

> Estado editorial: working  
> Última verificação factual: 2026-08-11  
> Âmbito: arquitetura do modelo, ferramentas, computação, adequação e validação  
> Documento canónico para: como o estudo será calculado e testado  
> Rever quando: mudar o stack, a resolução ou o desenho experimental

## Enquadramento metodológico

A metodologia da NEA é pública, mas não existe um standard universal e codificado de “full system costs”. A [taxonomia NEA de 2018](https://www.oecd.org/en/publications/the-full-costs-of-electricity-provision_9789264303119-en.html) separa custos da central, custos de sistema/rede e externalidades. O [estudo de 2019](https://www.oecd.org/en/publications/the-costs-of-decarbonisation_9789264312180-en.html) usa GenX e despacho horário, mas é greenfield, impõe shares de renováveis e adiciona alguns custos de rede da literatura. [POSY](https://www.oecd-nea.org/tools/abstract/detail/nea-1929/) é uma referência Julia/MILP aberta, não um substituto para adequação probabilística, rede detalhada ou estabilidade.

**DECISION D-MOD-001:** aproveitar a taxonomia e o princípio whole-system da NEA, sem importar valores genéricos como se fossem portugueses.

System LCOE é inadequado como métrica principal porque profile, balancing e grid costs dependem do benchmark, penetração, localização, flexibilidade e caminho de transição. A formulação preferida é:

> whole-system resource cost and social cost under common reliability and emissions constraints

## Arquitetura

1. Modelo brownfield de expansão e despacho para Portugal e Espanha.
2. França como nó limitado/endógeno ou condição de fronteira sujeita a stress, nunca como importação infinita; Marrocos se material.
3. Pelo menos PT, ES e FR, preferencialmente 10–30 clusters ibéricos ou nós principais com DC load flow/transport documentado.
4. Cronologia horária completa no caso elétrico principal. Períodos representativos apenas se preservarem armazenamento sazonal, incluírem semanas críticas e forem validados em 8 760/8 784 horas.
5. Vários anos coerentes de procura, vento, solar e hidro, preservando correlações PT–ES–FR e secas plurianuais.
6. Depois de congelar portefólios, unit commitment/economic dispatch com rampas, mínimos, min-up/down, arranques, part-load, reservas, manutenção, avarias e forecast error. Usar 15/5 minutos nos períodos críticos necessários.
7. Adequação em módulo sequencial probabilístico, com clima, avarias, manutenção, interligações e limites energéticos de hidro/storage.
8. Rede e segurança em módulos: perdas, congestionamento, redispatch, N-1 e screens de reativa, inércia e tensão. Estabilidade dinâmica nacional não é uma alegação do núcleo aberto.
9. Externalidades e incidência financeira em satellite accounts ligados ao [ledger de custos](cost-accounting.md).

O padrão LOLE continental português identificado era ≤1,46 h/ano; deve ser confirmado antes de cada release na [ERSE](https://www.erse.pt/eletricidade/seguranca-de-abastecimento/).

## Stack open source

**ASSUMPTION A-STACK-001:** PyPSA + PyPSA-Eur, fixados a commits exatos, com HiGHS para o caminho reproduzível principal.

Snapshot em 2026-08-10: PyPSA 1.2.2 e PyPSA-Eur 2026.02.0. Estes números não são pins ainda; o run manifest deve guardar o commit e lockfile efetivamente usados.

Fontes: [PyPSA](https://github.com/PyPSA/PyPSA), [PyPSA-Eur](https://github.com/PyPSA/pypsa-eur), [documentação](https://pypsa-eur.readthedocs.io/en/stable/index.html), [licenças upstream](https://pypsa-eur.readthedocs.io/en/latest/licenses/) e [otimização](https://docs.pypsa.org/latest/user-guide/optimization/overview/).

O PyPSA é o framework, não um cadastro português. O PyPSA-Eur usa `powerplantmatching` para coordenadas de muitas centrais convencionais e atribui-as espacialmente a buses/regiões. Estas coordenadas e o bus inferido são úteis para modelação, mas não equivalem ao crosswalk oficial grupo–subestação–terminal. O workflow [documenta a atribuição espacial e nearest-neighbour](https://github.com/PyPSA/pypsa-eur/blob/master/scripts/build_powerplants.py).

Alternativas para comparação:

- GenX, forte em planeamento elétrico/UC/reservas, mas sem pipeline ibérico equivalente;
- Calliope/Euro-Calliope, legível e multi-carrier, com representação de rede mais agregada;
- SpineOpt, forte em estocástico/multi-energia, mas mais complexo;
- Switch, sólido mas com tooling de dados sobretudo norte-americano;
- Temoa/OSeMOSYS para trajetórias coarse;
- Dispa-SET para validação operacional;
- POSY como referência NEA.

Nenhum destes oferece sozinho adequação probabilística turnkey com LOLE/EENS/ELCC; será necessário um módulo próprio ou integração adicional.

## Envelope computacional

Ordens de grandeza, não garantias:

| Modelo | Recursos plausíveis com solver aberto |
|---|---|
| PT+ES, 2–5 zonas, LP, 8 760 h | 8–16 GB, 4–8 cores; minutos a cerca de 1 h |
| Ibéria, 15–30 zonas, LP com hidro/storage | 32–64 GB, 8–16 cores; dezenas de minutos a horas |
| Sector-coupled a 3 h | 64–128 GB, 16–32 cores; horas/overnight |
| Sector-coupled horário | Pode exigir 128–256 GB e runs longos |
| UC anual plant-level, 100–300 unidades | 64–256 GB; horas a dias |
| Cinco anos meteorológicos acoplados | Frequentemente 128–256 GB; runs independentes podem ser distribuídos |

Um portátil basta para V0 e screening zonal. Para o principal, RAM, CPU, solver e formulação dominam; GPU não é a prioridade. Rolling horizon para UC e runs independentes por weather year controlam o custo. A [documentação de resolução espacial do PyPSA-Eur](https://pypsa-eur.readthedocs.io/en/latest/spatial_resolution/) deve ser usada para benchmarking.

Configuração inicial: 10–30 clusters, 8 760 horas, investimento contínuo, despacho linear, reservatórios/bombagem/baterias explícitos, 3–5 weather years separados e UC em stress weeks/rolling horizon.

## Incerteza

“Least cost” é condicional e não uma previsão. O produto deve procurar portefólios acessíveis, adequados e tecnicamente plausíveis através de múltiplas incertezas.

| Classe | Exemplos | Tratamento |
|---|---|---|
| Aleatória | clima, avarias, reparação, linhas | Monte Carlo sequencial |
| Paramétrica | CAPEX, eficiência, combustível, CO2, procura | sensibilidade e amostragem global |
| Profunda | nuclear, H2, política, build rates | narrativas sem probabilidades falsas |
| Estrutural | rede/copperplate, foresight, UC, storage | ensemble de formulações/modelos |
| Solução | portefólios quase ótimos | MGA a +1%, +3% e +5% |

Desenho recomendado:

1. pré-registar pergunta, fronteira, custos, métricas, cenários e tolerâncias;
2. usar 6–10 narrativas coerentes, evitando full factorial;
3. amostrar parâmetros correlacionados dentro de cada narrativa;
4. testar portefólios out-of-sample em clima e avarias;
5. comparar determinístico, estocástico risk-neutral, CVaR e minimax regret quando viável;
6. mostrar value of stochastic solution, price of robustness, regret e alternativas quase ótimas.

## Clima e seca

- objetivo científico de 30–40 anos coerentes PT–ES–FR, com ERA5/PECD e bias correction;
- procura, vento, PV, hidro e derating devem usar o mesmo ano/calendário;
- preservar sequências plurianuais e carry-over de reservatórios;
- perfect foresight funciona como lower bound, com sensibilidade rolling/limited foresight;
- separar reanalysis histórico de climate-change ensembles;
- validar períodos representativos contra cronologia integral.

Tolerâncias iniciais para agregação temporal: erro do objetivo <1%, capacidades principais <5%, nenhuma inversão da conclusão política e adequação estatisticamente consistente. São pressupostos a rever, não standards universais.

## Adequação

Depois de congelar cada portefólio:

- sequential Monte Carlo por climate year e histórias de avaria/reparação;
- manutenção e derating correlacionado quando justificável;
- common random numbers entre portefólios;
- intervalos de confiança e teste de convergência;
- bootstrap por climate-year/outage history, não por horas independentes;
- se não houver ENS, reportar upper bound estatístico, nunca “risco zero”.

Meta inicial de convergência: half-width do IC95 ≤10% relativo para LOLE/EENS não nulos, sujeita a revisão. Métricas: LOLE, EENS, LOLP, probabilidade anual, quantis ENS, shortfall máximo, duração dos eventos, dependência de importação em scarcity e decomposição por constraint.

Adequação não equivale a N-1, frequência, tensão ou estabilidade dinâmica.

## Backcast e validação

Backcast:

1. fixar capacidades, procura, combustíveis/CO2, interligações e outages históricos;
2. correr despacho sem investimento;
3. comparar energia, mix, reservatórios, curtailment, flows, emissões e duration curves;
4. não exigir reprodução de preços sem bids, uplift e comportamento estratégico;
5. fixar métricas antes de calibrar e guardar resultados pré/pós-calibração;
6. preservar um holdout de anos para alegações principais.

Validação matemática/software:

- casos pequenos resolvidos à mão para geração, storage, hidro, rede, carbono e load shedding;
- testes dimensionais e identidades de balanço, SOC, água, perdas, desconto e salvage;
- regression tests e checksums;
- primal/dual feasibility, gap, runtime, termination e warnings em cada run;
- repetição dos headline runs com tolerâncias apertadas e, quando possível, outro solver/modelo;
- declarar não-unicidade quando o custo é estável mas o mix varia.

A intercomparação deve avançar por degraus: one-node, storage/hydro, PT–ES, UC, expansão, carbono e adequação. Um difference register atribuirá discrepâncias a dados, formulação, solver ou incerteza estrutural.

## Manifest de execução

Cada run deve registar run ID, timestamp, Git commit/dirty state, hash de configuração e inputs, versões do modelo/dependências/solver, random seeds, threads, máquina, cenário, pesos, parent run, status, gap, resíduos, runtime, logs e checksums dos outputs.
