# Metodologia de modelação, incerteza e validação

> Estado editorial: working  
> Última verificação factual: 2026-08-13
> Âmbito: arquitetura do modelo, ferramentas, computação, adequação e validação  
> Documento canónico para: como o estudo será calculado e testado  
> Rever quando: mudar o stack, a resolução ou o desenho experimental

## Enquadramento metodológico

A metodologia da NEA é pública, mas não existe um standard universal e codificado de “full system costs”. A [taxonomia NEA de 2018](https://www.oecd.org/en/publications/the-full-costs-of-electricity-provision_9789264303119-en.html) separa custos da central, custos de sistema/rede e externalidades. O [estudo de 2019](https://www.oecd.org/en/publications/the-costs-of-decarbonisation_9789264312180-en.html) usa GenX e despacho horário, mas é greenfield, impõe shares de renováveis e adiciona alguns custos de rede da literatura. [POSY](https://www.oecd-nea.org/tools/abstract/detail/nea-1929/) é uma referência Julia/MILP aberta, não um substituto para adequação probabilística, rede detalhada ou estabilidade.

**DECISION D-MOD-001:** aproveitar a taxonomia e o princípio whole-system da NEA, sem importar valores genéricos como se fossem portugueses.

System LCOE é inadequado como métrica principal porque profile, balancing e grid costs dependem do benchmark, penetração, localização, flexibilidade e caminho de transição. A formulação preferida é:

> whole-system resource cost under common reliability and emissions constraints

Externalidades são apresentadas em contas físicas e variantes de custo social explicitamente separadas; não entram silenciosamente no headline de recursos.

Cada comparação terá uma ficha de contrafactual congelada: serviço/denominador, fronteira, trajetória brownfield, procura, fiabilidade, emissões, rede, clima, preços de recursos e efeitos incluídos. Custos de integração não são componentes universalmente aditivos nem atribuíveis a uma tecnologia sem esse benchmark.

## Arquitetura

1. Modelo brownfield de expansão e despacho para Portugal e Espanha, começando por um ano-alvo com trajetória suficiente para vintages, reforma/refurbishment/repowering, lead/build time, residual value e end effects. Tecnologias divisíveis podem ter investimento contínuo; nuclear e outros ativos lumpy são blocos enumerados ou decisões binárias.
2. França como nó limitado/endógeno ou condição de fronteira sujeita a stress, nunca como importação infinita; Marrocos se material.
3. Começar com 2–5 zonas PT–ES e França limitada. Aumentar para 4–8 ou mais clusters apenas se um teste demonstrar efeito material de congestionamento/localização; 10–30 nós não é requisito inicial.
4. Cronologia horária completa no caso elétrico principal. Períodos representativos apenas se preservarem armazenamento sazonal, incluírem semanas críticas e forem validados em 8 760/8 784 horas.
5. Vários anos coerentes de procura, vento, solar e hidro, preservando correlações PT–ES–FR e secas plurianuais.
6. Depois de congelar portefólios, usar unit commitment/economic dispatch em períodos críticos quando rampas, mínimos, arranques, reservas ou forecast error puderem alterar o resultado. Resolução de 15/5 minutos é validação localizada, não default anual.
7. Adequação em módulo sequencial probabilístico, com clima, avarias, manutenção, interligações e limites energéticos de hidro/storage.
8. Rede e segurança em módulos: perdas, congestionamento, redispatch, N-1 e screens de reativa, inércia e tensão. Estabilidade dinâmica nacional não é uma alegação do núcleo aberto.
9. Externalidades e incidência financeira em satellite accounts ligados ao [ledger de custos](cost-accounting.md).

Os padrões oficiais são zonais: LOLE ≤1,46 h/ano em Portugal continental e ≤1,5 h/ano em Espanha. Aplicam-se no mesmo Monte Carlo, mas como constraints separadas; não existe uma média ibérica defensável. Os VOLL oficiais antes da harmonização monetária são 12 433 EUR/MWh em Portugal e 22 879 EUR/MWh em Espanha. Fontes: [ERSE](https://www.erse.pt/eletricidade/seguranca-de-abastecimento/), [relatório VOLL/CONE](https://www.erse.pt/media/knfirrvo/relatorio-final-erse-voll-cone-dezembro-2025.pdf) e [resolução espanhola](https://www.boe.es/buscar/doc.php?id=BOE-A-2025-14438).

## Tiers de fidelidade

V0, V1 e V2 são rótulos de fidelidade, não uma ordem de execução concorrente com P0–P6:

- **V0:** balanço nacional ou zonal agregado;
- **V1:** sistema PT–ES com rede e principais nós/subestações representados;
- **V2:** detalhe unitário/operacional com UC, reservas, hidrologia cronológica e adequação estocástica nos módulos em que os dados o suportem.

Um módulo de estabilidade permanece separado e, sem dados e validação adicionais, é apenas screening — mesmo que outros módulos atinjam V2.

## Stack open source

**ASSUMPTION A-STACK-001:** PyPSA + HiGHS, fixados a versões exatas, constituem o caminho reproduzível principal. PyPSA-Eur é upstream opcional para scripts, convenções e inputs selecionados; P0 não exige instalar nem executar o workflow europeu completo.

Snapshot em 2026-08-10: PyPSA 1.2.2 e PyPSA-Eur 2026.02.0. Estes números não são pins ainda; o run manifest deve guardar versões/commits e lockfile efetivamente usados, incluindo PyPSA-Eur apenas quando alguma parte sua entrar no run.

Fontes: [PyPSA](https://github.com/PyPSA/PyPSA), [PyPSA-Eur](https://github.com/PyPSA/pypsa-eur), [documentação](https://pypsa-eur.readthedocs.io/en/stable/index.html), [licenças upstream](https://pypsa-eur.readthedocs.io/en/latest/licenses/) e [otimização](https://docs.pypsa.org/latest/user-guide/optimization/overview/).

O PyPSA é o framework, não um cadastro português. O PyPSA-Eur usa `powerplantmatching` para coordenadas de muitas centrais convencionais e atribui-as espacialmente a buses/regiões. Estas coordenadas e o bus inferido são úteis para modelação, mas não equivalem ao crosswalk oficial grupo–subestação–terminal. O workflow [documenta a atribuição espacial e nearest-neighbour](https://github.com/PyPSA/pypsa-eur/blob/master/scripts/build_powerplants.py).

### Validação escalonada

O caminho mínimo tem apenas:

1. **fixtures analíticas ou pequenos problemas independentes**, para balanços, storage/hidro, linha congestionada, carbono, investimento discreto e load shedding;
2. **PyPSA + HiGHS**, como modelo de planeamento principal;
3. **um simulador de adequação**, próprio e pequeno ou Antares-Simulator, apenas para portefólios finalistas.

GenX não é requisito. Só recebe um adaptador/piloto se um caso reduzido revelar discrepância estrutural, se a escolha do mix for sensível à formulação ou se uma revisão externa o exigir. Uma implementação Julia/JuMP completa também não é necessária quando fixtures resolvidas independentemente já testam as identidades.

Inputs preservados usam tabelas canónicas neutras, evitando que um modelo secundário dependa de objetos internos do PyPSA. Construir adaptadores apenas quando o respetivo modelo tiver passado o critério de promoção.

HiGHS continua a ser o caminho principal reproduzível de `A-STACK-001`. Um solver comercial pode ser usado em MILP/UC pesado, desde que o manifest registe produto e versão. Os casos principais devem ter reprodução no caminho aberto; se esta só for viável com scope reduzido, a diferença é declarada e a alegação de reprodutibilidade é reduzida em conformidade.

## Envelope computacional

Ordens de grandeza, não garantias:

| Modelo | Recursos plausíveis com solver aberto |
|---|---|
| PT+ES, 2–5 zonas, LP, 8 760 h | 8–16 GB, 4–8 cores; minutos a cerca de 1 h |
| Ibéria, 10–30 zonas, LP com hidro/storage | 64 GB seguro; 128 GB prudente nas primeiras execuções; minutos a horas com solver forte e potencialmente 5–24+ h no caminho aberto |
| Sector-coupled a 3 h | 64–128 GB, 16–32 cores; horas/overnight |
| Sector-coupled horário | Pode exigir 128–256 GB e runs longos |
| UC anual plant-level, 100–300 unidades | 64–256 GB; horas a dias |
| Cinco anos meteorológicos acoplados | Frequentemente 128–256 GB; runs independentes podem ser distribuídos |

Um portátil basta para V0 e screening zonal. Para o principal, RAM, CPU, solver, scaling numérico e formulação dominam; GPU não é a prioridade. O [Open Energy Benchmark](https://openenergybenchmark.org/blog/hipo_study) confirma milhões de variáveis a 10–30 nós/8 760 h e mostra que HiGHS/HiPO pode tornar o caminho aberto viável, mas com runtime e robustez não monotónicos. Mais de cerca de oito threads por solve HiGHS raramente compensa; é preferível paralelizar weather years/portefólios.

UC anual exato é o risco maior. O baseline é UC horário em janelas 48/96/168 h com overlap e estados/valores terminais validados; 15/5 minutos significam primeiro commitment congelado e redispatch/reservas nos períodos críticos. Adequação usa simulador rápido para todas as histórias e UC/ED detalhado apenas numa amostra estratificada dos eventos críticos.

Configuração P0: 2–5 zonas, 8 760 horas, capacidades fixas, despacho linear e hidro/storage agregados, num portátil. Primeira comparação P4: um ano-alvo, investimento contínuo apenas para tecnologias divisíveis, nuclear discreto, três weather years coerentes e UC apenas se um stress test mostrar materialidade.

## Incerteza

“Least cost” é condicional e não uma previsão. O produto deve procurar portefólios acessíveis, adequados e tecnicamente plausíveis através de múltiplas incertezas.

| Classe | Exemplos | Tratamento |
|---|---|---|
| Aleatória | clima, avarias, reparação, linhas | Monte Carlo sequencial |
| Paramétrica | CAPEX, eficiência, combustível, CO2, procura | sensibilidades primeiro; amostragem global apenas se material |
| Profunda | nuclear, H2, política, build rates | narrativas sem probabilidades falsas |
| Estrutural | rede/copperplate, foresight, UC, storage | testes de resolução/formulação promovidos por materialidade |
| Solução | portefólios quase ótimos | um slack MGA inicial quando a não-unicidade for relevante |

Desenho recomendado:

1. congelar em C1 pergunta, fronteira, custos, métricas e contrafactuais claim-bearing;
2. começar com referência, 2–3 contrafactuais e três weather years coerentes;
3. testar os finalistas out-of-sample em clima e avarias;
4. acrescentar apenas a sensibilidade cuja amplitude plausível seja comparável à diferença entre portefólios;
5. usar MGA, stochastic expansion, CVaR ou minimax regret apenas quando uma pergunta concreta justificar cada método.

## Clima e seca

- [PECD v4.2](https://cds.climate.copernicus.eu/datasets/sis-energy-pecd?tab=overview), CC BY 4.0, como backbone futuro; ERA5/ERA5-Land como baseline físico histórico e observações nacionais para calibração;
- usar três anos coerentes no primeiro screening; expandir para uma série histórica longa e, quando relevante, cadeias futuras nos testes de adequação dos portefólios fixos, até obter precisão suficiente — não em todos os runs de expansão;
- procura, vento, PV, hidro e derating devem usar o mesmo ano/calendário;
- preservar sequências plurianuais e carry-over de reservatórios;
- perfect foresight funciona como lower bound, com sensibilidade rolling/limited foresight;
- separar reanalysis histórico de climate-change ensembles;
- validar períodos representativos contra cronologia integral.

O PECD hidro é nacional/semanal e não substitui um modelo por bacia/cascata. Uma realização por GCM e seis GCM não estimam sozinhos caudas centenárias. Bias correction, weather-to-power, inflows por bacia, usos futuros da água e eventos compostos permanecem ensemble uncertainty, não erro a “corrigir” uma vez.

Tolerâncias iniciais para agregação temporal: erro do objetivo <1%, capacidades principais <5%, nenhuma inversão da conclusão política e adequação estatisticamente consistente. São pressupostos a rever, não standards universais.

## Adequação

Depois de congelar cada portefólio:

- sequential Monte Carlo por climate year e histórias de avaria/reparação;
- manutenção e derating correlacionado quando justificável;
- common random numbers entre portefólios;
- intervalos de confiança e teste de convergência;
- bootstrap por climate-year/outage history, não por horas independentes;
- se não houver ENS, reportar upper bound estatístico, nunca “risco zero”.

P4 deve incluir uma aproximação conservadora de capacidade firme/ELCC. Se P5 revelar capacidade ou custo corretivo material para cumprir o padrão zonal, o resultado regressa a P4 e é reotimizado ou reportado como condicionado. Adequação não é apenas um teste pass/fail posterior ao cálculo de custos.

Meta inicial de convergência: half-width do IC95 ≤10% relativo para LOLE/EENS não nulos, sujeita a revisão. Métricas: LOLE, EENS, LOLP, probabilidade anual, quantis ENS, shortfall máximo, duração dos eventos, dependência de importação em scarcity e decomposição por constraint.

Adequação não equivale a N-1, frequência, tensão ou estabilidade dinâmica.

## Backcast e validação

Backcast:

1. fixar capacidades, procura, combustíveis/CO2, interligações e outages históricos;
2. correr despacho sem investimento;
3. comparar energia, mix, reservatórios, flows, emissões, duration curves e o proxy de restrições/curtailment definido em [system-operations.md](data/system-operations.md);
4. não exigir reprodução de preços sem bids, uplift e comportamento estratégico;
5. fixar métricas antes de calibrar e guardar resultados pré/pós-calibração;
6. preservar um holdout de anos para alegações principais.

As métricas de backcast — identidade, resolução, agregação, denominador e tratamento de missing values — pertencem a esta metodologia; os valores-limite ficam em `A-BACKCAST-TOL-001`. `A-BACKCAST-YEARS` e essas tolerâncias são congelados em conjunto antes de qualquer calibração, e o holdout não pode ser usado para afinar nem parâmetros nem tolerâncias.

Validação matemática/software:

- casos pequenos resolvidos à mão para geração, storage, hidro, rede, carbono e load shedding;
- testes dimensionais e identidades de balanço, SOC, água, perdas, desconto e salvage;
- regression tests e checksums;
- primal/dual feasibility, gap, runtime, termination e warnings em cada run;
- repetição dos headline runs com tolerâncias apertadas e, quando possível, outro solver/modelo;
- reprodução independente avaliada por métrica com tolerâncias absolutas e/ou relativas fixadas em `A-REPRO-TOL-001` antes da tentativa;
- declarar não-unicidade quando o custo é estável mas o mix varia.

A validação avança por degraus: one-node, storage/hydro, PT–ES, expansão, carbono e adequação. Um difference register só é criado quando existir uma discrepância material a explicar.

## Manifest de execução

Runs preservados geram automaticamente, tanto quanto possível, run ID, timestamp, Git commit/dirty state, hash de configuração e inputs, versões do modelo/dependências/solver, seeds, threads, máquina, cenário, status, gap/resíduos, runtime, logs e checksums. Experiências descartáveis de P0 precisam apenas do mínimo para serem repetidas durante a exploração; manifests manuais extensos não são aceitáveis como rotina.
