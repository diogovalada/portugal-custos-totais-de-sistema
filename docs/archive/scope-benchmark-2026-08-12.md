# Benchmark de âmbito para custos totais do sistema — 2026-08-12

> Estado editorial: verified snapshot
> Data de corte: 2026-08-12
> Âmbito: comparação do desenho português com estudos e frameworks de custos de sistema
> Documento canónico para: evidência da auditoria pré-G1; a regra corrente de âmbito pertence a `docs/project-design.md`

## Pergunta da auditoria

O desenho atual omite algum componente capaz de invalidar a comparação de portefólios, ou transforma demasiados efeitos laterais em requisitos obrigatórios do primeiro paper?

Não existe uma definição universal em que “full system cost” signifique todos os efeitos económicos, sociais e ambientais imagináveis. No uso NEA, `total system cost` é o custo económico real de satisfazer a procura elétrica a todo o momento; não inclui automaticamente externalidades ou custos sociais. O framework britânico também separa custos diretamente pertencentes ao power system de impactos exteriores, que podem ser apresentados ao lado. Logo, profundidade científica não exige colocar tudo na mesma função objetivo.

## Estudos e famílias inspecionados

| Referência | Cobertura relevante | Principal aprendizagem de âmbito |
|---|---|---|
| NEA, Suécia, 2026 | POSY2 MILP; 17 bidding zones; eletricidade + H2; expansão e despacho horário de um snapshot 2050 | É o comparador mais próximo, mas usa um weather year base, perfect foresight, hidro agregado, transmissão comercial simplificada, reservas e parte da rede ex post; não modela distribuição, externalidades sociais ou trajetória multiperíodo |
| Estudos suecos comparados pela NEA | SEA/TIMES-Nordic, Qvist e Quantified Carbon/cGrid GenX, Svenska kraftnät/BID3 | A Suécia tem pelo menos cinco exercícios recentes, não um único estudo. Procura, weather years, comércio, fronteira setorial e custos tecnológicos explicam diferenças materiais |
| Kan, Hedenus e Reichenberg, 2020 | Europa endógena, foco sueco; geração, transmissão, storage e demand response; cap de 10 gCO2/kWh | Mostra que o valor do nuclear muda quando se permitem hidro e comércio inter-regional; confirma que a fronteira e o contrafactual podem dominar o resultado |
| NEA, Suíça, 2022 | Estudo nacional de cenários net-zero e custos de sistema | Confirma a família country-specific da NEA, mas não constitui metodologia normativa única nem dataset português |
| RTE, França, Energy Pathways 2050 | Seis mixes, três procuras, trajetória 2030–2060, Europa horária e 200 crónicas climáticas | É a referência exterior de maior profundidade: separa economia, adequação/flexibilidade, clima, rede, materiais, uso do solo e ambiente; exigiu dois anos, consulta de 120 organizações e capacidade institucional TSO |
| UK DECC/Frontier, 2016 | Framework conceptual de whole-system impacts com peer review | Define o impacto como diferença entre cenários reotimizados sob o mesmo serviço, fiabilidade e carbono; exige categorias exaustivas e não sobrepostas e põe macroeconomia, emprego, energia estratégica e externalidades não precificadas fora do core elétrico |
| IEA, Portugal, 2026 | Recomendações de política e roadmap de flexibilidade | Pede vários cenários além do PNEC, com sensibilidades ao ritmo renovável, novas cargas, custos tecnológicos e variabilidade climática/hídrica; confirma os eixos materiais do core sem exigir um modelo economy-wide |
| Heptonstall e Gross, 2021 | Revisão sistemática internacional de integração de VRE | Custos são contextuais, podem ser negativos a baixa penetração e tornam-se mais incertos a alta penetração; um adder universal por tecnologia não é defensável |
| Hirth, Ueckerdt e Edenhofer, 2015 | Framework económico de custos de integração | Todos os geradores têm efeitos de integração; a métrica coerente é marginal e dependente do valor/counterfactual, não uma propriedade fixa da tecnologia |

Fontes principais: [NEA Suécia 2026](https://www.oecd-nea.org/upload/docs/application/pdf/2026-03/system_cost_study_of_sweden.pdf), [Kan et al. 2020](https://doi.org/10.1016/j.energy.2020.117015), [NEA Suíça 2022](https://doi.org/10.1787/ac21f8be-en), [RTE Energy Pathways 2050](https://analysesetdonnees.rte-france.com/en/publications/energy-pathways-2050), [UK whole-system framework](https://www.gov.uk/government/publications/whole-power-system-impacts-of-electricity-generation-technologies), [IEA Portugal 2026](https://www.iea.org/reports/portugal-2026/policy-recommendations-for-portugal), [Heptonstall e Gross](https://doi.org/10.1038/s41560-020-00695-4) e [Hirth et al.](https://doi.org/10.1016/j.renene.2014.08.065).

## Comparação de profundidade

| Dimensão | NEA Suécia 2026 | RTE França 2050 | Desenho PT–ES atual |
|---|---|---|---|
| Geração, storage, comércio | Core endógeno | Core endógeno | Core endógeno |
| Transmissão | 17 zonas; fluxos comerciais, não físicos; reforço em parte ex post | Modelação TSO e europeia profunda | CNTC + DC sintético validado; sem claim TSO |
| Distribuição | Omitida | Custos e efeitos estudados em módulo | Proxy/ledger satélite; load flow nacional fora do core |
| Adequação | Alguns requisitos não modelados; reservas por regressões ex post | Análise explícita de segurança de abastecimento | Monte Carlo zonal obrigatório antes dos claims finais |
| Estabilidade dinâmica | Não modelada diretamente | Estudos técnicos separados | Screens satélite; validação TSO fora de âmbito aberto |
| Clima/weather | Um ano base + sensibilidades | 200 crónicas IPCC em cada hora | 3–5 anos no screening; 30–40 + PECD no alvo científico |
| Hidro | Equivalentes zonais; sem carry-over multi-ano | Modelação TSO mais profunda | Reservatórios/cascatas quando os dados o permitem; ensemble contínuo |
| Trajetória | Snapshot 2050 | 2030/2040/2050/2060 | Brownfield multiperíodo proposto |
| Externalidades/ambiente | Fora do total system cost principal | Módulos físicos de ciclo de vida, materiais, solo e ambiente | Ledger físico e contas satélite; monetização seletiva |
| Incidência financeira | Secundária | Financiamento e economia analisados separadamente | Ledger financeiro separado do custo de recursos |
| Reprodutibilidade aberta | Não foi localizado pacote público POSY2 + dados | Publicação extensa, mas não réplica completa do TSO | Requisito explícito com PyPSA/HiGHS e dados licenciados |

O projeto PT–ES não está subdimensionado no desenho científico. Em weather uncertainty, adequação probabilística, trajetória brownfield, hidro e reprodutibilidade pretende até superar a profundidade publicada pelo caso NEA sueco. Não poderá igualar a profundidade da RTE em rede, consulta institucional e validação operacional, e não deve fingir que consegue.

## Âmbito recomendado antes de G1

### Núcleo mínimo publicável

Obrigatório para responder à pergunta central:

1. bulk system continental PT–ES, com França limitada/endógena e stress de vizinhos;
2. custo de recursos de geração, fuel, armazenamento, transmissão/interligação, ligação, flexibilidade, reservas físicas, perdas, desmantelamento e comércio externo aplicável;
3. procura e contrafactual comuns, constraints zonais de fiabilidade e uma constraint de emissões declarada;
4. cronologia horária, hidro e storage intertemporal, indisponibilidades, múltiplos anos meteorológicos e eventos de seca;
5. brownfield e ritmos/lead times de construção, não apenas um greenfield 2050;
6. adequação probabilística dos portefólios finais;
7. ledger histórico/backcast e reprodução aberta proporcionais aos claims.

### Contas e módulos satélite

Devem existir e permanecer visíveis, mas não bloquear todos o primeiro resultado:

- incidência financeira, tarifas, faturas e distribuição de custos;
- poluição, lifecycle GHG, água, biodiversidade, solo, materiais e acidentes;
- distribuição por subestação/zona e custos incrementais proxy;
- inércia, tensão, reativa, grid-forming, black start e outros screens de estabilidade;
- segurança de combustível, geopolítica, resiliência rara e consequências macroeconómicas;
- avaliação institucional e de financiamento de um programa nuclear português.

Um satélite só sobe ao core quando: pode alterar a viabilidade ou ranking do portefólio; existe uma representação validável; e a sua inclusão não duplica uma constraint ou custo já contabilizado.

### Adiado ou estudo separado

- load flow nacional AT/MT/BT e modelo dinâmico/EMT de nível TSO;
- economia portuguesa completa, emprego e feedback macroeconómico;
- sistema energético ibérico integral com todos os carriers e escolhas de consumo;
- Açores e Madeira dentro da mesma otimização continental;
- estimativa determinística de um projeto nuclear português ainda inexistente;
- imputação de um único “custo de integração” intrínseco a cada tecnologia.

## Diagnóstico de scope creep

O risco atual não vem da lista de fenómenos identificados, mas de não distinguir `conhecer`, `quantificar em satélite` e `endogeneizar no core`. Se distribuição, estabilidade, externalidades, incidência, sector coupling, ilhas e economia-wide forem todos gates do primeiro paper, o projeto deixa de ser exequível por um independente.

A arquitetura faseada já contém quase todas as salvaguardas certas. O ajuste necessário é tornar `A-SCOPE-TIERS-001` vinculativo no charter, etiquetar cada output como `core`, `satellite` ou `deferred`, e proibir que um novo módulo entre no caminho crítico sem um change note que identifique claim, materialidade, dados, compute, owner e efeito no calendário/gate.

## Resultado da auditoria

- **Underscope:** não foi encontrada uma omissão estrutural nova que invalide o core proposto.
- **Scope creep:** risco alto se os módulos já inventariados forem tratados como simultaneamente obrigatórios.
- **Recomendação:** preservar a ambição como mapa completo, mas congelar um núcleo elétrico publicável e promover módulos apenas por materialidade demonstrada.
