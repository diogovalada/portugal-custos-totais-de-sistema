# Snapshot arquivado — memória do projeto

Última atualização: 2026-08-10  
Estado: snapshot histórico, não canónico. Não atualizar. Consultar `PROJECT_STATUS.md` e os documentos temáticos para o estado corrente.

## Objetivo

Construir um estudo transparente, reproduzível e preferencialmente open source dos custos totais/full system costs do sistema elétrico português, tratando explicitamente a integração no MIBEL, as limitações das interligações da Península Ibérica e a incerteza tecnológica, política e climática.

O estudo deve permitir comparar portefólios, e não apenas LCOE de tecnologias isoladas. Entre os ramos de cenário já identificados estão:

- manutenção versus encerramento do nuclear espanhol;
- diferentes CAPEX, prazo, WACC e desempenho de nuclear hipotético em Portugal;
- anos húmidos, normais, secos e secas plurianuais;
- evolução da procura, população, eletrificação e procura flexível na Península;
- expansão de renováveis, baterias, bombagem, redes e interligações;
- diferentes disponibilidades de importação/exportação e políticas espanholas;
- requisitos de adequação, reservas, estabilidade, tensão e potência reativa.

## Conclusão de alto nível

Um estudo independente de nível **planeamento/adequação** é viável com informação pública, reconstruções documentadas, pedidos administrativos e parâmetros probabilísticos.

Não é possível, apenas com open data, apresentar o resultado como:

- réplica operacional validada pela REN;
- modelo nacional completo de estabilidade transitória/EMT;
- power flow fiel de toda a distribuição AT/MT/BT;
- reconstrução exata do custo final all-in de todos os projetos privados.

Resumo da auditoria:

| Tema | Estado correto |
|---|---|
| Unidades e nós | backbone público para grandes unidades; crosswalk/nós incompletos |
| Parâmetros unitários | operador detém; priors abertos; detalhe português não público |
| Hidro | operação básica das grandes cascatas largamente pública; curvas/regras finas em falta |
| Reservas/redispatch | substancialmente público no SIME; contexto físico e segundos em falta |
| Distribuição | dados zonais/subestações ricos; modelo elétrico e custos nodais fechados |
| Baterias | reconstrução parcial; sem cadastro nacional completo |
| Custos realizados | bons nas redes reguladas; all-in privado fraco |
| Estabilidade | requisitos/indicadores/planeamento públicos; dinâmica operacional fechada |
| Nuclear Portugal | projeto específico não existe; usar cenários/limiares |
| Ilhas | mensal/anual público; operação sub-horária não aberta |

Nenhum dos dez temas deve ser rotulado em bloco como “totalmente inacessível”. Também nenhum está integralmente aberto e pronto a usar.

### Conclusões antigas expressamente substituídas

Não voltar a afirmar sem qualificação que:

- “a ENTSO-E não tem cadastro de unidades” — tem backbone production unit/generation unit >=100 MW; falta o nó e a pequena produção;
- “reservas, ativações e redispatch não estão públicos” — o SIME publica grande parte a 15 minutos;
- “não há afluências/turbinamento por barragem” — o SNIRH tem séries extensas para muitas grandes albufeiras;
- “a distribuição é opaca em bloco” — subestações, PTD, cargas, curto-circuito e hosting capacity são públicos; falta o modelo elétrico;
- “não há custos realizados” — existem nas redes reguladas e projetos selecionados; falta o all-in privado;
- “os custos do projeto nuclear português estão escondidos” — o projeto definido ainda não existe.

A linguagem deve distinguir sempre:

1. aberto e reutilizável;
2. público mas fragmentado, autenticado ou sem licença clara;
3. existente numa entidade e potencialmente solicitável;
4. não público/confidencial;
5. ainda não produzido ou inexistente.

“Não encontrado publicamente” não prova que um dado não exista. “Acessível para consulta” também não significa que possa ser redistribuído no GitHub.

## Decisões ainda não fechadas

Não converter recomendações de investigação em decisões sem confirmação:

- fronteira principal: Portugal continental, MIBEL ou PT+ES+FR;
- ano-base monetário, horizonte e anos-alvo;
- eletricidade apenas no paper inicial ou sector coupling;
- granularidade espacial e tratamento de Espanha/França/Marrocos;
- procura exógena versus serviços energéticos/endógenos;
- taxa social central e casos de WACC privado;
- standard de fiabilidade e VOLL por classe;
- número de weather years e desenho estocástico;
- tratamento da distribuição como ledger, proxy zonal ou módulo de rede;
- inclusão dos Açores/Madeira no estudo principal ou papers separados;
- profundidade de externalidades e monetização;
- tecnologia/modelo secundário para intercomparação.

Working default recomendado, ainda não decisão final: estudo inicial electricity-only do bulk system continental PT+ES, França limitada, ilhas separadas, PyPSA-Eur/HiGHS, cronologia horária e contas de recursos/financeira/externalidades separadas.

## Princípio de contabilidade a preservar

O resultado económico principal deve adotar a perspetiva de planeador social e contabilizar recursos reais e danos externos. Tarifas, impostos, subsídios, receitas de mercado, pagamentos de capacidade, pagamentos de reservas e rendas de congestionamento são normalmente transferências dentro da fronteira do estudo, não custos de recursos adicionais.

É necessário declarar antecipadamente:

- fronteira geográfica: Portugal, MIBEL ou Europa;
- setores incluídos: apenas eletricidade ou também transportes, calor, hidrogénio e indústria;
- horizonte, ano-base monetário, taxa de desconto e valor residual;
- procura fixa ou serviços energéticos/endógenos;
- critério de fiabilidade e tratamento de ENS/VOLL/LOLE.

Não somar duas vezes, entre outros:

- CAPEX e a respetiva anuidade;
- anuidade integral e valor residual incompatível;
- CAPEX/OPEX das redes e tarifas que os recuperam;
- custos físicos de despacho e pagamentos grossistas;
- custo social do carbono e pagamentos ETS usados para o representar;
- custos físicos das reservas e pagamentos de capacidade/ativação;
- investimento de adequação e pagamentos do capacity market;
- perdas físicas de armazenamento e o valor grossista das mesmas perdas;
- perdas de rede como geração adicional e novamente como energia comprada;
- incentivo de demand response e desutilidade do consumidor;
- ativos de ligação cobrados ao produtor e novamente à rede;
- emprego/salários/valor acrescentado como benefício quando trabalho e investimento já são custos;
- receitas, lucros e congestion rents subtraídos ao custo social;
- custos de geração estrangeira e pagamentos de importação, quando ambos os sistemas são endógenos.

### Formulação económica mínima

Para procura/serviço fixo:

NPV esperado = soma descontada de investimento + FOM + rede + desmantelamento - valor residual + custo operacional esperado por cenário.

O custo operacional deve incluir pelo menos combustível/eficiência, VOM, arranque, no-load, ramping/cycling, reserves/balancing reais, storage/degradação, demand response/desutilidade, ENS x VOLL, comércio externo quando aplicável e externalidades.

Para procura elástica, maximizar welfare ou minimizar:

recursos + danos externos - utilidade dos serviços energéticos.

Se for usada anuidade:

CRF(r,L) = r(1+r)^L / ((1+r)^L - 1)

e custo anual = CAPEX x CRF + FOM. Usar euros reais de um ano-base e taxas reais compatíveis.

Âncoras metodológicas:

- EIB economic appraisal: https://www.eib.org/files/publications/20220169_economic_appraisal_of_investment_projects_en.pdf
- ENTSO-E 4th CBA Guideline para redes/benefícios: https://eepublicdownloads.blob.core.windows.net/public-cdn-container/clean-documents/news/2024/entso-e_4th_CBA_Guideline_240409.pdf

### Três contas que não devem ser misturadas

1. **Custo económico/de recursos:** CAPEX, FOM, VOM, combustíveis, redes, armazenamento, flexibilidade, perdas, adequação, comércio externo quando está fora da fronteira e desmantelamento.
2. **Incidência financeira:** preços grossistas, tarifas, proveitos permitidos, impostos, subsídios, CfD/PPA, pagamentos de capacidade, rendas de congestionamento, margens e faturas por grupo de consumidor.
3. **Externalidades:** clima, poluição atmosférica, acidentes, água, solo, biodiversidade, ruído, segurança de abastecimento e outros efeitos não mercantis.

O custo primário deve ser o custo incremental/contrafactual de fornecer o mesmo serviço com a mesma fiabilidade e restrição de emissões. System LCOE ou VALCOE podem ser indicadores secundários, mas não propriedades intrínsecas de uma tecnologia.

### Tratamentos contabilísticos específicos

- **CAPEX:** escolher NPV multiperíodo com fluxos quando ocorrem ou anuidade equivalente; nunca ambos. Incluir construção, atraso, substituições/refurbishment e valor residual de forma consistente.
- **Taxa de desconto:** usar uma taxa social real comum na conta de recursos. WACC privado e contratos pertencem à conta financeira, salvo quando representam restrições ou riscos reais.
- **Reservas/balancing:** co-otimizar headroom, footroom, rampa, SOC e resposta. Contar combustível, arranques, desgaste, perdas e equipamento; pagamentos e oportunidade de mercado são normalmente transferências ou valores sombra.
- **Curtailment:** reportar MWh e percentagem. A compensação ou subsídio perdido não é automaticamente custo de recursos; o CAPEX/FOM já foi incorrido e o valor da energia perdida emerge do contrafactual.
- **Armazenamento:** separar EUR/MW e EUR/MWh; incluir eficiência, auxiliares, autodescarga, cronologia do SOC e degradação. Não contar simultaneamente degradação embutida no FOM/lifetime e custo integral por ciclo.
- **Adequação:** valorar ENS com VOLL e reportar LOLE/EENS/LOLH, duração e profundidade. Não adicionar pagamentos de capacidade se o investimento necessário já é endógeno.
- **Procura flexível:** distinguir deslocamento, redução voluntária com desutilidade/rebound e corte involuntário com VOLL. Incentivos são transferências se a desutilidade e os recursos já foram contabilizados.
- **Comércio:** numa fronteira ibérica, pagamentos PT–ES e rendas de congestionamento são transferências. Numa fronteira portuguesa, importações/exportações são valorizadas ao custo de oportunidade na fronteira e não se somam também os custos espanhóis.
- **Ativos existentes:** CAPEX histórico, dívida e subsídios passados são sunk para a decisão futura. Incluir custos evitáveis, refurbishment, encerramento e desmantelamento incrementais; mostrar book value/compensação noutra conta.
- **Carbono:** usar cap, preço de política ou dano social de forma explicitamente rotulada. Não somar pagamentos ETS e o mesmo dano climático.
- **Sector coupling:** contabilizar conversores, storage e redes de cada carrier; cobrar combustíveis e externalidades uma vez na origem; não comprar internamente eletricidade ao preço grossista e contar também o sistema que a produziu; usar denominadores por serviço útil.
- **Denominador:** EUR/MWh deve usar eletricidade final entregue, excluindo carga de armazenamento e exportações, salvo definição diferente explícita.

Cada linha do ledger deve ser marcada como: quantidade endógena x custo unitário exógeno; custo unitário endógeno; valor sombra/oportunidade; custo fixo exógeno; ou efeito omitido/não monetizado. Valores sombra são resultados úteis, não parcelas adicionais da função objetivo.

### Resultados mínimos

- NPV, custo anual equivalente e diferença de custo face ao contrafactual;
- custo forward relevante para decisão e conta completa do sistema atual como resultados separados;
- custo médio por MWh final entregue;
- cost stack por geração, redes, armazenamento, flexibilidade, adequação, comércio, desmantelamento e externalidades;
- conta financeira/distributiva separada;
- capacidade e produção por tecnologia/nó;
- importações/exportações, congestão, perdas e curtailment;
- carga/descarga, ciclos e degradação do armazenamento;
- reservas, ativações e shortfalls;
- LOLE, EENS, eventos extremos e intervalos de confiança;
- emissões diretas/lifecycle e impactos não monetizados.

## Metodologia recomendada

### O que aproveitar da NEA

A metodologia da NEA é pública, mas não existe um padrão universal e codificado de “full system costs”.

- A taxonomia de 2018 separa custos da central, custos de sistema/rede e custos externos: https://www.oecd.org/en/publications/the-full-costs-of-electricity-provision_9789264303119-en.html
- O estudo de 2019 usa GenX e despacho horário, mas é greenfield, impõe shares de VRE e não co-otimiza transmissão/distribuição; vários custos de rede foram acrescentados da literatura: https://www.oecd.org/en/publications/the-costs-of-decarbonisation_9789264312180-en.html
- POSY é uma implementação Julia/MILP aberta e útil como referência, mas não substitui adequação probabilística, redes detalhadas ou estabilidade: https://www.oecd-nea.org/tools/abstract/detail/nea-1929/

Decisão: usar a taxonomia e o princípio de custo total da NEA, não transplantar os seus valores genéricos para Portugal.

System LCOE é controverso porque profile, balancing e grid costs dependem do benchmark, penetração, localização, flexibilidade e caminho de transição; as parcelas podem sobrepor-se. Um teste “tecnologia X + storage fornece 100%” é uma monocultura artificial que elimina complementaridade wind/solar, hidro, rede, demand response e sector coupling. Formulação preferida do estudo:

**whole-system resource cost and social cost under common reliability and emissions constraints**

### Arquitetura de modelação

1. **Modelo brownfield de expansão e despacho** para Portugal e Espanha. França deve ser um nó endógeno ou uma condição de fronteira limitada e stress-tested; não uma fonte infinita de importações. Incluir Marrocos se material.
2. **Espaço:** pelo menos PT, ES e FR; preferencialmente 10–30 clusters ibéricos ou nós principais com DC load flow/transport explicitamente documentado.
3. **Tempo:** cronologia horária completa para o caso elétrico principal. Períodos representativos apenas com ligação sazonal, semanas extremas explícitas e validação em 8 760/8 784 horas.
4. **Tempo meteorológico:** décadas coerentes de procura, vento, solar e hidro; preservar correlações PT–ES–FR e sequências de seca.
5. **Validação operacional:** congelar portefólios candidatos e correr unit commitment/economic dispatch com rampas, mínimos, min-up/down, arranques, part-load, reservas, manutenção, avarias e forecast error. Usar 15/5 minutos em períodos críticos quando necessário.
6. **Adequação separada:** sequential Monte Carlo com clima coerente, avarias de unidades/interligações, manutenção e restrições energéticas de hidro/storage. Reportar LOLE, EENS e ELCC.
7. **Rede/segurança em módulos:** perdas, congestionamento, redispatch, N-1 e screens de reativa/inércia/tensão. Estabilidade dinâmica continua fora da validação pública.
8. **Externalidades e incidência financeira como satellite accounts**, evitando sobrecarregar o núcleo de expansão com efeitos mal monetizados.

O padrão de fiabilidade continental português atualmente identificado é LOLE <= 1,46 h/ano; deve ser novamente confirmado antes de cada release. Referência: https://www.erse.pt/eletricidade/seguranca-de-abastecimento/

## Ferramentas open source e compute

### Stack principal

Recomendação atual: **PyPSA + PyPSA-Eur**, fixados a versões/commits exatos, com HiGHS como solver aberto.

Snapshot verificado em 2026-08-10: PyPSA 1.2.2 e PyPSA-Eur 2026.02.0. Estes números envelhecem; o run manifest deve guardar o commit e lockfile realmente usados.

Razões:

- workflow europeu de dados já existente;
- subset PT/ES e representação de transmissão;
- expansão, despacho, storage, hidro, redes e sector coupling;
- licenças abertas no código e solver;
- comunidade ativa, documentação e testes.

Fontes:

- PyPSA: https://github.com/PyPSA/PyPSA
- PyPSA-Eur: https://github.com/PyPSA/pypsa-eur
- documentação: https://pypsa-eur.readthedocs.io/en/stable/index.html
- licenças e aviso sobre termos dos dados upstream: https://pypsa-eur.readthedocs.io/en/latest/licenses/
- otimização PyPSA: https://docs.pypsa.org/latest/user-guide/optimization/overview/

Alternativas:

- **GenX:** melhor alternativa para UC, reservas e power-sector planning; falta pipeline ibérico.
- **Calliope/Euro-Calliope:** multi-carrier legível e workflow europeu, mas rede é essencialmente transport e a migração de versões deve ser fixada.
- **SpineOpt:** forte para estocástico e operação multi-energia; maior complexidade e sem data builder ibérico.
- **Switch:** sólido no setor elétrico, mas tooling de dados é sobretudo norte-americano.
- **Temoa/OSeMOSYS:** úteis para trajetórias longas e modelos coarse; menos indicados como núcleo horário de rede/UC ibérico.
- **Dispa-SET:** opção de referência para validação operacional posterior.
- **POSY:** referência NEA, não stack principal.

Nenhuma destas ferramentas fornece adequação probabilística completa e turnkey com LOLE/EENS/ELCC; será necessário módulo/extensão separado.

### Envelope computacional aproximado

Estimativas de planeamento, não garantias:

| Modelo | Recursos plausíveis com solver aberto |
|---|---|
| PT+ES, 2–5 zonas, LP, 8 760 h | 8–16 GB RAM, 4–8 cores; minutos a cerca de 1 h |
| Iberia útil, 15–30 zonas, LP, hidro/storage | 32–64 GB, 8–16 cores; dezenas de minutos a algumas horas |
| Iberia sector-coupled, resolução 3 h | 64–128 GB, 16–32 cores; horas/overnight |
| Sector-coupled horário | Pode exigir 128–256 GB e runs longos |
| UC anual plant-level com 100–300 unidades | 64–256 GB; horas a dias, altamente dependente do MILP |
| Expansão com cinco anos meteorológicos acoplados | Frequentemente 128–256 GB; runs independentes podem ser distribuídos |

Um portátil é suficiente para V0 e screening zonal. O modelo principal pode exigir workstation/servidor CPU. GPU não é a prioridade para LP/MILP; RAM, solver e formulação dominam. Rolling-horizon UC e runs independentes por weather year reduzem custo.

HiGHS é adequado para o LP principal. Gurobi/CPLEX podem acelerar grandes MILP/UC em ordens de grandeza, mas o estudo deve manter um caminho open-source reproduzível pelo menos para os casos centrais de referência.

Referência oficial de escala PyPSA-Eur: https://pypsa-eur.readthedocs.io/en/latest/spatial_resolution/

Plano inicial:

- 10–30 clusters;
- 8 760 horas no caso electricity-only;
- investimento contínuo e despacho linear com HiGHS;
- reservatórios, bombagem e baterias explícitos;
- 3–5 weather years inicialmente como sensibilidades separadas;
- UC/stress-week em rolling horizon, não binários em toda a expansão desde o primeiro dia.

## Viabilidade para um investigador independente

### Veredito

É credível produzir um estudo publicável sobre o custo de recursos de cenários alternativos para o bulk-electricity mainland Portugal/Iberia. Não é credível prometer sozinho um “verdadeiro custo total” que cubra simultaneamente eletricidade, todos os setores, distribuição detalhada, estabilidade dinâmica, macroeconomia, finanças públicas, externalidades e welfare.

| Ambição | Viabilidade solo |
|---|---|
| Ledger histórico português | Alta; MVP em cerca de 8–12 semanas full-time |
| Expansão elétrica ibérica | Média-alta; preprint credível em cerca de 9–15 meses full-time |
| Mais adequação, weather years e módulos de rede/distribuição | Média; revisão especializada necessária |
| Sistema ibérico totalmente sector-coupled | Baixa-média; extensão de 18–36 meses |
| “Custo verdadeiro” economy-wide definitivo | Não é projeto de uma só pessoa |

Estimativa preliminar de orçamento direto para uma versão robusta: aproximadamente EUR 15 mil–60 mil, sobretudo revisão especializada/replicação; cloud e arquivo aproximadamente EUR 1 mil–10 mil. Uma versão bare-bones pode ser muito mais barata. Computação não deverá ser o maior bottleneck, salvo alta resolução, sector coupling ou muitos cenários estocásticos.

AI pode acelerar ETL, testes, documentação, geração de cenários, revisão de código e orquestração. Não substitui julgamento de power systems, interpretação institucional, validação independente nem peer review adversarial.

### Programa faseado

1. Research charter/protocolo e ontologia de custos.
2. Ledger histórico para 2–3 anos recentes, conciliando energia e dinheiro.
3. Modelo ibérico calibrado com capacidades históricas fixas.
4. Cenários 2030/2040 e sensibilidades.
5. Adequação probabilística e módulos de custos omitidos.
6. Replicação independente, consulta pública e preprint.

Critérios stop/go devem exigir reconciliação de balanços, backcast histórico, claims proporcionais ao modelo e reprodução numa máquina limpa.

O ledger histórico é um MVP autónomo: deve produzir valor público mesmo que a expansão/adequação posterior se revele mais difícil.

## Cenários ibéricos — snapshot temporal de 2026-08-10

Tudo nesta secção é temporalmente instável e deve ser reverificado antes de correr/publicar cenários.

### Regra de classificação

- **Baseline legal/político:** leis, autorizações e infraestrutura já em vigor.
- **Baseline de projetos esperados:** em construção ou suficientemente avançados, com sensibilidade de atraso.
- **Contrafactuais:** extensões, aceleração, não-entrega e stress; não apresentar como política vigente.

### Nuclear espanhol

O baseline legal continua a ser o encerramento dos sete reatores entre 2027 e 2035. Almaraz pediu extensão das duas unidades até junho de 2030 e o CSN emitiu parecer favorável com condições em 16-07-2026, mas isso ainda não era a decisão governamental final em 10-08-2026.

Datas de referência:

| Unidade | Encerramento de referência |
|---|---:|
| Almaraz I | novembro de 2027 |
| Almaraz II | outubro de 2028 |
| Ascó I | outubro de 2030 |
| Cofrentes | novembro de 2030 |
| Ascó II | setembro de 2032 |
| Vandellós II | fevereiro de 2035 |
| Trillo | maio de 2035 |

Fontes:

- PNIEC espanhol: https://www.miteco.gob.es/content/dam/miteco/es/energia/files-1/pniec-2023-2030/PNIEC_2024_240924.pdf
- sétimo plano de resíduos: https://www.enresa.es/documentos/ES_7-plan-general-residuos-radiactivos_.pdf
- parecer CSN Almaraz: https://www.csn.es/-/informe-favorable-almaraz

Ramos:

1. calendário legal atual;
2. Almaraz até junho de 2030;
3. extensão de cada central +5/+10 anos;
4. encerramento previsto com disponibilidade nuclear baixa/outage stress.

### Procura e política

- Portugal PNEC 2030: metas de aproximadamente 51% renováveis no consumo final e 93% na eletricidade, com cerca de 8,1 GW hidro com bombagem, 10,4 GW eólica onshore, 2 GW offshore, 20,8 GW PV, 2 GW baterias e 3,5 GW gás; tratar como ambição de política, não previsão neutra. Documento: https://apambiente.pt/sites/default/files/_Clima/20241118_pnec2030_para_aprov_ar.pdf
- Portugal consumiu cerca de 53,1 TWh da rede pública em 2025, enquanto o ramo industrial/hidrogénio do PNEC pode aproximar a procura de 90 TWh; separar conventional demand de green-industry boom. Fonte: https://www.ren.pt/en-gb/media/news/electricity-consumption-reaches-highest-ever-level-in-2025
- Espanha PNIEC 2030: meta de cerca de 81% renováveis na eletricidade e procura elétrica 34% acima de 2019, com aproximadamente 62 GW wind, 76 GW PV, 22,5 GW storage e 12 GW electrolysers; incluir ramo de procura elevada por centros de dados, indústria, EV e H2. Fonte: https://www.miteco.gob.es/es/prensa/ultimas-noticias/2024/septiembre/el-gobierno-aprueba-la-actualizacion-del-plan-nacional-integrado.html
- A proposta espanhola de rede H2030 usava aproximadamente 344 TWh/53,8 GW no caso PNIEC e 375,2 TWh/61,4 GW no caso de pedidos elevados; tratar como âncoras, não previsões.
- Demografia deve afetar sobretudo a componente doméstica/serviços; a grande incerteza é electrificação, data centres, indústria e hidrogénio. EUROPOP2025 baseline: PT cerca de 11,14 milhões em 2030 e 10,66 milhões em 2050; ES cerca de 50,95 milhões em 2030 e 53,88 milhões em 2050. O caso sem migração é muito inferior. Fonte: https://ec.europa.eu/eurostat/databrowser/product/page/PROJ_25NP

### Interligações

- Nova interligação PT–ES inaugurada em 02-07-2026: capacidade aproximada ES->PT 4,2 GW e PT->ES 3,5 GW. Fonte: https://www.ree.es/en/press-office/news/press-release/2026/07/espana-y-portugal-inauguran-la-nueva-interconexion
- ES–FR: cerca de 2,8 GW atuais; Bay of Biscay, 2 GW, esperado para início de 2028 e border total de cerca de 5 GW. Testar atraso/não-entrega e cerca de 8 GW em 2040. Fonte: https://www.rte-france.com/actualites/2026-05-28-landes-pose-cables-interconnexion-france-espagne
- As capacidades são direcionais e sujeitas a outage/derating. França nuclear não é capacidade firme portuguesa.
- MIBEL é integrado mas PT e ES continuam zonas de oferta distintas; não modelar nem isolamento nem copperplate permanente.
- Produtos day-ahead de 15 minutos entraram em vigor para entrega desde 01-10-2025. Estudos de rampas/storage/balancing devem validar períodos críticos a 15 minutos.

### TYNDP como envelope, não resposta

- TYNDP 2024: National Trends+, Distributed Energy e Global Ambition.
- Draft TYNDP 2026: cenário central National Trends+ e variantes económicas alta/baixa para 2035/2040; as variantes não são caminhos completos alternativos de descarbonização.
- Usar inputs TYNDP para harmonizar fronteiras e comparação, mantendo contrafactuais próprios de nuclear, build rates, interligações e clima.

Fontes:

- https://tyndp.entsoe.eu/resources/tyndp2024-scenarios-report
- https://2026.entsos-tyndp-scenarios.eu/

### Hidrogénio, gás e clima

- H2Med tem data-alvo atual de 2032, não 2030. Cenário 2030 base: sem capacidade H2Med; depois testar entrega, atraso e no-build. https://h2medproject.com/the-h2med-project-2/
- Portugal e Espanha mantêm exposição a LNG; combinar high gas/CO2 com drought e nuclear closure.
- Usar clima cronológico correlacionado. Casos mínimos: normal, húmido, seca severa e seca plurianual; não usar capacity factors independentes.

### Matriz mínima recomendada

1. Policy 2030 com datas nucleares atuais.
2. Almaraz até 2030.
3. Extensão nuclear espanhola +5/+10 anos.
4. Slow delivery de renováveis, storage, rede e electrificação.
5. Electro-industrial boom.
6. Seca ibérica severa/plurianual.
7. Bay of Biscay atraso versus 5/8 GW ES–FR.
8. Gas/H2 stress.

Compound stresses prioritários:

- nuclear closure + drought + high gas + Bay delay;
- high demand + delayed storage/grid;
- fast renewables + slow H2 demand + constrained exports.

## Auditoria das dez lacunas de dados

### 1. Registo canónico de unidades e respetivos nós

**Diagnóstico corrigido:** existe uma boa espinha dorsal canónica para grandes unidades, mas não um registo nacional completo ligado aos nós.

#### ENTSO-E — base principal para unidades grandes

O ficheiro `ProductionAndGenerationUnits_r3` cobre production units existentes ou planeadas com capacidade >=100 MW e relaciona-as com os respetivos generation units. Campos relevantes:

- código e nome da production unit;
- código e nome dos generation units;
- estado e datas de validade;
- tecnologia;
- potência instalada;
- localização textual;
- nível de tensão;
- zona de oferta e área de controlo.

Fontes:

- especificação: https://transparencyplatform.zendesk.com/hc/en-us/articles/36496214610449
- capacidade por production unit: https://transparencyplatform.zendesk.com/hc/en-us/articles/36496107495953
- produção real por generation unit: https://transparencyplatform.zendesk.com/hc/en-us/articles/39309514389777-ActualGenerationOutputPerGenerationUnit-16-1-A-r3
- File Library: https://transparencyplatform.zendesk.com/hc/en-us/articles/35960137882129-File-Library-Guide
- obrigação e limiar de 100 MW, artigo 14.º: https://eur-lex.europa.eu/eli/reg/2013/543/oj
- códigos EIC: https://www.entsoe.eu/data/energy-identification-codes-eic/

Limites:

- não identifica subestação, barramento, terminal, bay ou ponto de entrega;
- “localização” pode ser apenas texto genérico e o nível de tensão não determina o nó;
- a maioria da produção solar, eólica, cogeração, pequena hídrica e baterias fica fora do cadastro unitário por causa do limiar;
- a capacidade >=1 MW é publicada apenas agregada por tecnologia;
- um EIC válido não prova que a unidade esteja operacional;
- a lista EIC central não contém necessariamente todos os códigos locais emitidos pela REN, que é o Local Issuing Office português.

#### Outras peças do crosswalk

- DGEG WFS/ArcGIS por tecnologia: licenças, processo, nome, proprietário, potência, datas, concelho, geometria. https://www.dgeg.gov.pt/pt/servicos-online/informacao-geografica/energia/energia-eletrica/
- Projetos licenciados DGEG: https://www.dgeg.gov.pt/pt/areas-setoriais/energia/energia-eletrica/producao-de-energia-eletrica/projetos-licenciados/
- Mapa anual REN: identifica a instalação RNT de ligação para várias centrais diretamente ligadas à transmissão. https://www.ren.pt/media/fcbh2aqx/mapa-eletricidade-2026-ren.pdf
- E-REDES, capacidade de receção: nós/subestações, níveis de tensão e geração agregada, mas não unidades individuais. https://e-redes.opendatasoft.com/explore/dataset/capacidade-rececao-rnd/information/
- Lista de unidades de oferta OMIE: útil para o mercado, mas uma unidade de oferta pode agregar várias unidades físicas. https://www.omie.es/informes_mercado/listados/lista_unidades.pdf

Snapshot DGEG testado em 2026-08-10: 17 objetos térmicos, 134 hídricos, 2 890 eólicos, 732 solares e 24 de cogeração. Não interpretar estes números como centrais operacionais:

- eólica/solar podem ter um objeto por aerogerador, bloco ou polígono;
- as camadas incluem projetos licenciados/em licenciamento e não apenas operação;
- a camada térmica observada não cobria algumas grandes CCGT;
- não há EIC, OMIE, subestação ou barramento;
- a ligação por proximidade geográfica é inferência, não correspondência oficial.

Crosswalk-alvo:

`central -> grupo -> processo DGEG -> EIC -> unidade OMIE -> proprietário -> subestação/nó -> tensão -> MW/MWh -> estado -> datas de validade`

Fundamento para pedir a base:

- O Decreto-Lei n.º 15/2022 sujeita produção e armazenamento a controlo prévio.
- O artigo 29.º prevê na licença, entre outros, ponto de receção na RESP, potência de injeção, potência instalada, mínimo estável, níveis mínimo/máximo de regulação e obras de ligação.
- O artigo 106.º prevê uma base atualizada REN/GGS articulada com a base de referência da DGEG.

Logo, muitos campos existem administrativamente mesmo quando não aparecem no WFS/PDF público. Pedir exportação existente, identificadores de articulação e histórico de validade.

Fonte consolidada: https://diariodarepublica.pt/dr/legislacao-consolidada/decreto-lei/2022-177634029

### 2. Rampas, mínimos técnicos, heat rates, arranques e avarias

**Diagnóstico:** existem dados genéricos abertos e a REN detém grande parte dos valores portugueses, mas o conjunto validado unidade a unidade não é público.

- O MPGGS demonstra que a REN/GGS recebe indisponibilidades, potência disponível, parâmetros dinâmicos, limites, planos de manutenção e outros dados unitários: https://www.erse.pt/media/q10chfti/mpggs_articulado-250911.pdf
- A RMSA-E 2025 usa tempos de arranque, tempo mínimo de paragem e rampas dos CCGT, mas não publica os valores: https://www.dgeg.gov.pt/media/wq4bi1to/rmsa-e-2025.pdf
- O ERAA fornece priors reproduzíveis por tecnologia e vintage para eficiência, mínimo, rampas, min-up/down, arranque, FOR e tempo médio de reparação: https://www.entsoe.eu/eraa/2025/modelling-data/
- A ENTSO-E publica produção por grupo >=100 MW e grandes indisponibilidades, mediante conta/token.

Priors ERAA ilustrativos para CCGT, nunca substituir por “dados portugueses”:

- eficiência aproximadamente 40–60% consoante vintage;
- mínimo técnico frequentemente 50% em categorias antigas e 40% nas recentes;
- min-on/off cerca de 2–3 h;
- rampa de subida cerca de 2–4% de Pmax/min;
- FOR cerca de 5–8%;
- manutenção planeada de referência cerca de 27 dias/ano.

Limiar de transparência ENTSO-E:

- produção real por generation unit: >=100 MW;
- indisponibilidade/alteração material: tipicamente mudança >=100 MW;
- production units: cobertura adicional para instalações >=200 MW com mudança >=100 MW.

Consequência: os eventos publicados são úteis para validar operação e inferir falhas grandes, mas não formam um censo de deratings/outages portugueses.

Lacuna efetiva:

- curvas de heat rate por grupo e por carga;
- custos físicos de arranque/no-load;
- rampas e mínimos validados por grupo;
- FOR/EFORd por unidade com exposição consistente;
- histórico completo de deratings e avarias abaixo dos limiares europeus.

Fontes complementares:

- ACER REMIT: eventos materialmente relevantes, janela/qualidade limitadas, CAPTCHA e potenciais duplicados;
- OMIE: bom histórico unitário espanhol; o diretório português de indisponibilidades estava vazio no teste de 2026-08-10;
- plano de manutenção anual móvel existe na REN/GGS, mas a versão integral unitária não foi encontrada aberta.

### 3. Cascatas hídricas, afluências, rendimentos e obrigações da água

**Correção importante:** os dados operacionais básicos das principais cascatas históricas são em larga medida públicos.

- SNIRH permite exportar séries por estação: afluência, turbinamento, descarga, bombagem, cota e armazenamento. Muitas grandes barragens têm séries diárias desde os anos 1990. https://snirh.apambiente.pt/index.php?idMain=2&idItem=1
- Inventário SNIRH: capacidades, níveis, curvas cota-volume-área e relações montante/jusante. https://snirh.apambiente.pt/index.php?idMain=1&idItem=7
- Boletim de armazenamento: https://snirh.apambiente.pt/index.php?idMain=1&idItem=1.3
- Centrais hídricas DGEG: https://www.dgeg.gov.pt/pt/servicos-online/informacao-geografica/energia/energia-eletrica/
- Concessões e usos múltiplos APA: https://apambiente.pt/agua/aproveitamentos-hidraulicos-concessoes
- Grandes barragens/CNPGB: https://cnpgb.apambiente.pt/

Cobertura diretamente confirmada no SNIRH inclui, entre outras, Alto Lindoso, Alto Rabagão, Venda Nova, Aguieira, Alqueva, Pedrógão, Baixo Sabor, Touvedo, Salamonde, Caniçada, Paradela, Pocinho, Valeira, Régua, Carrapatelo, Crestuma, Cabril, Castelo do Bode, Bouçã, Raiva e Fronhas. Há falhas e quality flags; cobertura longa não equivale a série perfeita.

A lista APA de janeiro de 2026 referia 211 contratos de concessão correspondentes a 295 aproveitamentos hidráulicos. Títulos anteriores a outubro de 2012 não estão integralmente disponíveis no SILiAmb, pelo que TURH/contratos/autocontrolo antigos exigem pedido à APA/ARH.

Lacunas efetivas:

- topologia hidráulica canónica, incluindo derivações e transvases;
- curvas de rendimento turbina/bomba em função da queda e carga;
- curvas de restituição e perdas hidráulicas;
- regras comerciais de otimização e valor da água;
- obrigações quantitativas harmonizadas num único dataset;
- séries detalhadas de Gouvães, Daivões e Alto Tâmega;
- cobertura de mini-hídricas.

A licença do SNIRH não está normalizada como CC BY. Publicar inicialmente scripts, proveniência e derivados; confirmar autorização antes de redistribuir os ficheiros brutos em massa.

### 4. Reservas, ativações, redispatch e congestionamento

**Correção importante:** a maior parte dos dados necessários para despacho e contabilidade sistémica está publicamente acessível no SIME da REN.

Entrada principal: https://mercado.ren.pt/PT/Electr/InfoMercado/InfSistema

Disponível, frequentemente a 15 minutos:

- ofertas, necessidades, contratação, atribuições e preços de aFRR;
- ofertas, necessidades, ativações, energia e preços de mFRR;
- histórico de RR/TERRE;
- desvios e valorização por ISP/BRP;
- PDBF, PDVD, PHF e mFRR-R;
- energia e custo das restrições;
- motivos mensais de restrições.

Notas:

- FCR continua a ser serviço obrigatório e não remunerado; não existe uma série portuguesa de preço de contratação comparável a aFRR/mFRR.
- O produto RR/TERRE terminou em Portugal em 30-12-2025; conservar o histórico, mas não o projetar automaticamente.
- ENTSO-E fornece uma camada normalizada adicional, mas a completude portuguesa deve ser auditada item a item.

Resumo de restrições: https://mercado.ren.pt/PT/Electr/InfoMercado/InfSistema/Restricoes/Paginas/Total-Energia-Valorizacao.aspx

Lacunas efetivas:

- sinal AGC/aFRR de segundos;
- ativação FCR física por unidade;
- liquidação/faturas confidenciais;
- elemento congestionado, contingência N-1 e ação corretiva associados a cada redispatch;
- custo de oportunidade físico distinto do preço liquidado;
- série canónica de curtailment renovável com causa, tecnologia, localização e compensação;
- licença clara para redistribuição massiva dos dados SIME.

### 5. Topologia e custos marginais da distribuição

**Diagnóstico:** a E-REDES tem open data muito rico ao nível de subestação/zona, mas não publica um modelo elétrico completo para power flow.

Fontes abertas:

- características de subestações, transformação, carga e curto-circuito: https://e-redes.opendatasoft.com/explore/dataset/caracteristicas-da-rede/
- postos de transformação: https://e-redes.opendatasoft.com/explore/dataset/postos-transformacao-distribuicao/
- capacidade de receção: https://e-redes.opendatasoft.com/explore/dataset/capacidade-rececao-rnd/information/
- portal geral: https://e-redes.opendatasoft.com/pages/homepage/
- PDIRD e anexos: https://www.erse.pt/atividade/consultas-publicas/consulta-publica-126/abertura/

Snapshot testado em 2026-08-10: cerca de 437 subestações em “caracteristicas-da-rede”, 72 mil postos de transformação e mais de 14 milhões de registos quarto-horários de carga por subestação nos datasets regionais. Os totais mudam com atualizações.

Lacunas efetivas:

- grafo elétrico canónico AT/MT/BT;
- extremos de ramo, conectividade e estado normal de manobra;
- R/X/B, ampacidades, taps e parâmetros de transformadores;
- topologia BT nacional;
- curvas locais de reforço/hosting capacity em EUR/MW ou EUR/MVA;
- custos realizados projeto a projeto e catálogo de custos unitários;
- licença estável para reutilizar certas geometrias AT/MT presentes nos mapas, mas marcadas como restritas.

É possível um modelo zonal ou por subestação. Não é defensável afirmar que se reproduziu a RND real.

“Custo marginal de reforço” não é necessariamente uma tabela preexistente: muitas vezes é o output de um estudo de ligação locacional e lumpy. Custos incrementais tarifários ERSE, encargos de ligação e projetos PDIRD podem servir como proxies sistémicos/curvas aproximadas, mas não como EUR/MW nodal observado.

### 6. Registo completo de baterias com MW e MWh

**Diagnóstico:** parcialmente reconstruível, mas não existe um registo português público, autoritativo e completo.

- JRC European Energy Storage Inventory: projetos, MW/MWh, tecnologia, estado e coordenadas, mas com valores estimados e sem nó. https://ses.jrc.ec.europa.eu/storage-inventory
- DGEG licencia/regista armazenamento, mas as listas públicas não formam um cadastro próprio completo.
- ERSE publica agregados e possui um modelo de reporte MW/MWh dos operadores.
- REN publica potência e balanço agregados de baterias.
- APA/SIAIA, PRR/Fundo Ambiental e documentos dos promotores contêm fichas pontuais.
- Madeira/EEM publica características de baterias individuais: https://eeminov.eem.pt/cb/

Razões para esperar um registo administrativo melhor:

- armazenamento autónomo >1 MW requer licença DGEG;
- até 1 MW requer registo prévio;
- armazenamento associado é integrado no processo da produção;
- o indicador regulatório G5 obriga operadores a reportar MW, MWh, tecnologia, propriedade e autónomo/co-localizado.

Manual de reporte ERSE: https://www.erse.pt/media/bvzfelpi/manual-reporte.pdf

Persistem riscos de irrecuperabilidade: pequenas baterias behind-the-meter, MWh útil/química ausentes em registos antigos, histórico de estados não preservado e nó exato restringido por segurança/segredo comercial.

Snapshots úteis, a rever:

- API JRC em 2026-08-10: 74 projetos portugueses, 56 eletroquímicos; muitos MWh estimados, estados misturados e nomes genéricos;
- ERSE reportava 7 MW/26 MWh na RNT no fim de 2024 e zero agregado nas redes de distribuição abrangidas pelo reporte;
- REN reportava 19 MW instalados em julho de 2026;
- estes totais não substituem o cadastro e podem diferir por data, âmbito ou definição.

Fonte do snapshot ERSE: https://www.erse.pt/media/f4eh0fph/relat%C3%B3rio-art249-dl15_2022.pdf

Campos a pedir: ID, estado, standalone/co-localizada/behind-the-meter, MW de carga/descarga, MWh bruto/útil, química, localização, nó/tensão, datas de licença/teste/operação e ativo associado.

### 7. Custos realizados de projetos

**Diagnóstico:** há informação real relevante nas redes reguladas; falta um registo completo de custo final all-in por ativo, sobretudo na geração privada.

- PDIRD-E, incluindo valores reais 2020-2023: https://www.erse.pt/media/yxpjdvp2/proposta-pdird-e-2024-anexo-c3-a-anexo-i.pdf
- Contas reguladas reais E-REDES: https://www.e-redes.pt/sites/eredes/files/2025-11/Relat%C3%B3rio%20Contas%20Reguladas%20Reais%20E-REDES%202024%20-%20Resumo.pdf
- Relatórios e contas REN: https://www.ren.pt/
- Parâmetros regulatórios ERSE: https://www.erse.pt/media/dzdijgko/par%C3%A2metros-2026-2029.pdf
- BASE.gov: contratos, modificações e ocasional preço efetivo. https://www.base.gov.pt/Base4/pt/documentacao/formas-de-obter-dados-sobre-os-contratos-publicos/
- EDA, contas reguladas e ficheiros XLSX reais: https://www.eda.pt/regulacao/contas-reguladas
- Portal Mais Transparência e Tribunal de Contas para projetos financiados/auditados.

Não confundir:

- investimento previsto;
- subsídio aprovado ou executado;
- incentivo pago;
- proveito permitido;
- valor de adjudicação;
- custo final all-in.

Lacunas efetivas dos projetos privados: EPC por pacote, terrenos, desenvolvimento, ligação, contingências, claims, owner’s costs, juros capitalizados, manutenção pesada e reconciliação final após litígios.

O próprio relatório BASE 2024 indicava informação de conclusão/preço efetivo em apenas cerca de 17% das empreitadas no corte analisado; adjudicação não garante outturn completo.

Fonte: https://www.base.gov.pt/Base4/media/2oeld2oi/relat%C3%B3rio-anual-2024-contrata%C3%A7%C3%A3o-p%C3%BAblica.pdf

Rota de reconstrução privada: registo da central -> NIPC/SPV -> certidão permanente/IES paga -> adições ao imobilizado e ativos em curso -> dívida/juros/depreciação/OPEX -> CMVM, financiamento público, BASE, SIAIA e divulgações do promotor. Produz estimativa parcial, não reconciliação auditada por ativo.

### 8. Estabilidade, tensão e potência reativa

**Diagnóstico:** existe uma camada pública útil de requisitos, indicadores e planeamento; a camada operacional/dinâmica não é open data.

- Qualidade de energia REN por ponto: https://www.ren.pt/atividade/qualidade-de-energia
- PDIRT e custos de reatores, STATCOM e compensadores: https://www.erse.pt/media/5ugp1p1x/pdirt-2025-2034-proposta-inicial-vol-i-sem-anexos.pdf
- Anexo 16: correntes de defeito mín./máx. e X/R projetados por nó: https://www.erse.pt/media/lx5n5kao/pdirt-2025-2034-proposta-inicial-vol-i-anexos-1-a-16.pdf
- Requisitos RfG: https://www.dgeg.gov.pt/pt/areas-setoriais/energia/energia-eletrica/servicos-e-redes/codigos-de-rede-europeus/requisitos-geradores-rfg/
- Relatório do apagão ibérico de 2025, com dados detalhados mas anonimizados: https://www.entsoe.eu/publications/blackout/28-april-2025-iberian-blackout/

Também existem preços/cadernos públicos de concursos de black start e o PDIRT propunha um portefólio condicional de reatores, STATCOM e compensador síncrono da ordem de EUR 127 milhões. Isto permite contabilização/proxies de investimento, não reconstrução da segurança dinâmica.

Não públicos:

- SCADA/PMU bruto e contínuo;
- estados AC e estimativas de estado;
- P/Q/V por nó e operações de taps/shunts;
- modelos dinâmicos e EMT por unidade;
- AVR, PSS, governor, controlos de inversores e proteções;
- séries detalhadas de inércia e short-circuit strength;
- IGM/CGM operacionais e casos completos de estabilidade.

Podem existir vias institucionais/NDA. Parâmetros genéricos e modelos sintéticos devem ser claramente rotulados como proxies e não como validação TSO.

O modelo dinâmico continental ENTSO-E disponível por pedido é anonimizado/simplificado e orientado a frequência/small-signal; não substitui o modelo ibérico detalhado de tensão, transitórios, proteção e EMT.

### 9. Custos e condições de um projeto nuclear específico em Portugal

**Diagnóstico:** não estão escondidos; um projeto português suficientemente definido ainda não existe.

Não há combinação definida de:

- sítio;
- tecnologia e central de referência;
- fornecedor/EPC;
- potência e calendário;
- ponto de ligação e reforços;
- sistema de refrigeração;
- estrutura regulatória e institucional;
- estratégia para combustível irradiado e resíduos;
- regime de financiamento e alocação de risco.

A estratégia nacional confirma que Portugal não possui centrais nucleares nem combustível irradiado de potência: https://diariodarepublica.pt/dr/detalhe/resolucao-conselho-ministros/129-2022-204953813

Há legislação, estudos históricos/territoriais e benchmarks internacionais suficientes para:

- cenários probabilísticos de CAPEX, prazo, WACC e desempenho;
- comparação de grande reator e SMR;
- prémio de país newcomer;
- análise de break-even/limiares de entrada no portefólio.

Não apresentar um ponto médio internacional como “LCOE nuclear português”. Custos de sítio, água, rede, regulação, resíduos e financiamento devem ser rubricas explícitas de incerteza.

#### Tratamento nuclear no modelo

Não usar uma única tecnologia “nuclear”. Separar:

1. unidades espanholas até às datas legais atuais;
2. extensões curtas específicas, como Almaraz;
3. extensões +5/+10/+20 anos com obras e autorização por unidade;
4. grande reator FOAK num país newcomer;
5. programa posterior replicado/NOAK apenas se houver aprendizagem e continuidade industrial;
6. importação nuclear francesa limitada por disponibilidade e redes.

Intervalos de partida, todos a harmonizar para o mesmo ano monetário e a tratar como cenários, não factos portugueses:

- LTO: cerca de 450/700/950 USD2020/kW e 10/20 anos; uma extensão de 2–3 anos exige caso específico.
- New build overnight: 3 500/7 000 USD2020/kW e stress FOAK >=8 000 em unidades comparáveis.
- Construção: 6–8 anos numa repetição bem-sucedida; 9–12 referência; 13–18 FOAK/stress.
- Taxa real comum: 3%/7%/10% na conta de recursos, mais WACC/contratos na conta financeira.
- Correlacionar CAPEX, atraso, financiamento e risco; não esconder todo o risco no WACC nem contar overrun duas vezes.
- Incluir maior perda de infeed, reservas, flexibilidade/load following, outage comum por design, água/arrefecimento e restrições climáticas.

Âncoras:

- NEA/IEA Projected Costs 2020: https://www.oecd.org/en/publications/projected-costs-of-generating-electricity-2020_a6002f3b-en.html
- NEA Nuclear Energy Outlook 2026: https://www.oecd-nea.org/upload/docs/application/pdf/2026-06/nuclear_energy_outlook_-_rev.pdf
- IAEA Milestones, programa newcomer e 19 áreas de infraestrutura: https://www-pub.iaea.org/MTCD/publications/PDF/PUB1997_web.pdf

Portugal tem legislação geral, mas não infraestrutura institucional, qualificação de sítio, estratégia de combustível irradiado, proposta de fornecedor ou estudo de rede/água de um projeto. Um newcomer pode necessitar aproximadamente 10–15 anos desde decisão inicial até operação, antes de qualquer atraso de construção específico.

Auditoria portuguesa:

- existe legislação de licenciamento, segurança, responsabilidade e avaliação ambiental;
- a missão IRRS da AIEA de 2022 já identificava necessidades de reforço institucional mesmo para o pequeno setor nuclear/radiológico existente;
- não foi localizada avaliação INIR/Milestones pública para um programa nuclear de potência;
- Ferrel/Livro Branco são históricos e não qualificam um sítio atual;
- Sines pode ser hipótese de screening por costa/rede/infraestrutura, mas nada está reservado ou nuclear-qualified;
- falta estudo moderno de sismo, tsunami, cheias, fonte fria, calor extremo, dispersão, ambiente, rede e alimentação de segurança;
- propostas parlamentares para estudo caducaram; não foi localizado estudo governamental contemporâneo concluído que escolha sítio, tecnologia, promotor ou financiamento.

IRRS 2022: https://www.iaea.org/sites/default/files/documents/review-missions/irrs_portugal_2022-03-28.pdf

Para waste/decommissioning, distinguir custo físico incremental da levy/fundo financeiro; não somar uma taxa estatutária e o mesmo backend cost de benchmark.

### 10. Séries operacionais detalhadas dos Açores e Madeira

**Diagnóstico:** existem agregados mensais/anuais e dados de qualidade ricos; não há séries operacionais abertas de alta frequência.

- Açores/SREA, produção mensal por tipo e ilha: https://srea.azores.gov.pt/relatorio/energia-eletrica-producao-por-tipo-de-energia-kwh/
- EDA, qualidade de serviço e anexos Excel por ilha: https://eda.pt/regulacao/qualidade-de-servico/relatorios-de-qualidade-de-servico
- Madeira/DREM, produção e emissão por fonte: https://estatistica.madeira.gov.pt/download-now/economica/energia-pt/energia-ee-pt/energia-eletrica/energia-ee-quadros-pt.html
- EEM, relatórios de qualidade: https://www.eem.pt/pt/conteudo/publicacoes/qualidade-de-servico/relatorios-e-auditorias/relatorios-de-qualidade-de-servico/
- EEM, inventário de baterias: https://eeminov.eem.pt/cb/

Os anexos Excel EDA fornecem SAIFI, SAIDI, TIEPI, END, causas e, por ponto/semana, estatísticas de tensão/frequência, flicker, harmónicas, desequilíbrio, cavas e sobretensões. São bons para validação de qualidade, mas não são SCADA contínuo. As contas reguladas EDA têm informação real por ilha/atividade/central e são uma fonte especialmente rica de custos e investimentos.

Lacunas efetivas por ilha:

- procura horária/15-min;
- despacho por grupo ou tecnologia;
- combustível por grupo;
- SOC, carga e descarga das baterias;
- curtailment;
- reservas;
- cronologia de indisponibilidades;
- frequência/SCADA bruto.

Os Açores têm nove sistemas elétricos independentes. Madeira e Porto Santo são também sistemas independentes; não devem ser agregados como um único nó síncrono.

Não usar os ficheiros de 5 minutos “PT-MA” da Electricity Maps como medição operacional da Madeira: a cobertura estava classificada como modelada a partir de agregados mensais/anuais e não substitui SCADA/EEM.

Referência: https://portal.electricitymaps.com/datasets/PT-MA

SREA, DREM, EDA e EEM não apresentavam uma licença open standard uniforme. Para GitHub, publicar inicialmente aquisição/proveniência e pedir autorização de reutilização dos ficheiros brutos.

## Fontes transversais para o modelo

As dez lacunas não substituem o catálogo completo de dados. Stack de partida:

| Necessidade | Fonte primária | Nota |
|---|---|---|
| Balanço mainland e cross-check | REN Data Hub, https://datahub.ren.pt/pt/ | Dashboard near-real-time; API documentada sobretudo diária/mensal; termos restringem extração/reutilização |
| Procura/produção distribuída a 15 min | E-REDES Open Data, https://e-redes.opendatasoft.com/pages/homepage/ | Muitos datasets CC BY 4.0; 15 min sobretudo desde 2023; documentar revisões e profiling |
| Produção, carga, unidades, flows, outages | ENTSO-E Transparency Platform | Conta/token; confirmar CC BY item a item |
| Mercado diário/intradiário | OMIE, https://www.omie.es/en/file-access-list | Formatos/resolução mudaram; arquivo online de cerca de seis anos é móvel; termos não são licença open standard |
| Estatísticas/geo/licenças | DGEG | Datasets catalogados em dados.gov tendem a CC BY; páginas diretas nem sempre explicitam licença |
| Custos regulados/tarifas | ERSE | PDF/XLS, nem sempre licença aberta; proveito permitido não é custo cash contemporâneo |
| Hidrologia | APA/SNIRH | Séries ricas, interface legacy e licença pouco clara |
| Clima e perfis | ERA5/ERA5-Land, IPMA | ERA5 horário desde 1940/1950 e reutilizável; IPMA requer auditoria de termos e é sobretudo calibração |
| Demografia/macroeconomia | Eurostat e INE | APIs/downloads com proveniência; arquivar pulls porque séries são revistas |
| Gás e carbono | MIBGAS, DGEG, EEX/ETS/EEA | Spot/auction não equivale a custo delivered da central; licenças de futures podem ser restritas |
| Emissões | APA/UNFCCC/EEA ETS | Operacional/territorial; lifecycle requer outra fonte e fronteira |

Regras:

- REN/ENTSO-E mainland não incluem Açores/Madeira.
- Valores nacionais Eurostat/DGEG podem incluir ilhas.
- Guardar timezone, DST, leap years, net/gross, HHV/LHV, provisional/final e revisões.
- Para dados visíveis mas não redistribuíveis, publicar download scripts, manifests e transformações permitidas.
- Na E-REDES, guardar a licença explícita de cada dataset e pedir clarificação quando boilerplate antigo contradiga CC BY; geometrias marcadas restricted não entram no repositório sem autorização.

## Incerteza, adequação e validação

### Resultado epistemológico

“Least cost” é sempre condicional, não previsão. O produto principal deve mostrar portefólios que permanecem acessíveis, adequados e tecnicamente plausíveis em várias incertezas.

### Classes de incerteza

| Classe | Exemplos | Tratamento |
|---|---|---|
| Aleatória | clima, avarias, duração de reparação, line outages | Monte Carlo sequencial |
| Paramétrica/epistémica | CAPEX, eficiência, WACC, fuel/CO2, procura | amostragem global e sensibilidade |
| Profunda/narrativa | nuclear, H2, política, build rates, interligações | cenários sem probabilidades falsas |
| Estrutural | copperplate/rede, perfect/limited foresight, UC, storage formulation | ensemble de configurações/modelos |
| Solução | muitos portefólios quase ótimos | MGA/near-optimal a +1%, +3%, +5% |

Desenho:

1. pré-registar pergunta, fronteira, custos, métricas, cenários e tolerâncias;
2. usar 6–10 narrativas coerentes, evitando full factorial;
3. dentro de cada narrativa, amostrar parâmetros correlacionados; Morris/emulador para screening e Sobol/Shapley para importância global quando justificável;
4. testar cada portefólio num ensemble out-of-sample de clima e avarias;
5. comparar caso determinístico, estocástico risk-neutral, risk-averse/CVaR e robust/minimax regret quando computacionalmente possível;
6. mostrar value of stochastic solution, price of robustness, regret e near-optimal alternatives.

### Clima e seca

- Meta científica: 30–40 anos meteorológicos coerentes PT–ES–FR, usando ERA5/PECD e bias correction contra observações.
- Load, wind, PV, hydro e derating devem vir do mesmo ano/calendário; nunca combinar “anos típicos” independentes.
- Preservar sequências plurianuais e estado terminal/carry-over de reservatórios.
- Não impor ciclos anuais que apaguem a seca plurianual; perfect foresight deve ser lower bound com sensibilidade rolling/limited foresight.
- Separar ensemble histórico/reanalysis de ensemble climate-change; não fingir que todos os membros são equiprováveis.
- Representative periods devem ligar storage/reservoirs, conter stress weeks e passar validação contra cronologia completa.
- Tolerâncias iniciais sugeridas para aceitar agregação: erro de objetivo <1%, capacidades principais <5%, nenhuma mudança da conclusão política e adequação estatisticamente consistente.

### Adequação

Depois de congelar cada portefólio:

- sequential Monte Carlo por climate year e amostras de avaria/reparação;
- unidades e interligações com manutenção e derating correlacionado quando justificado;
- common random numbers entre portefólios;
- convergência e intervalos de confiança publicados;
- alvo inicial de convergência: half-width do IC95 <=10% relativo para LOLE/EENS não nulos, sujeito a revisão científica;
- bootstrap ao nível de climate-year/outage history, não horas independentes;
- se não ocorrer ENS, reportar upper bound estatístico e não “risco zero”.

Métricas: LOLE, EENS, LOLP, probabilidade anual de loss of load, p50/p90/p95/p99 ENS, shortfall máximo, duração/energia dos eventos, import dependence em scarcity e decomposição por constraint.

Adequação não equivale a N-1, frequência, tensão ou estabilidade dinâmica.

### Backcast e holdout

1. Fixar capacidades, procura, fuel/CO2, interligações e outages históricos.
2. Correr despacho sem investimento.
3. Comparar energia, mix, reservoirs, curtailment, flows, emissions e duration curves.
4. Não exigir que um social-planner reproduza preços sem bids, uplift e comportamento estratégico.
5. Fixar métricas/tolerâncias antes de calibrar e preservar resultados pré/pós-calibração.
6. Usar blocos de anos para treino/validação e manter holdout intocado para claims principais.

### Validação matemática/software

- casos pequenos resolvidos à mão para geração, storage, hidro, rede, carbono e load shedding;
- testes de unidades/dimensões, balanço, SOC, water balance, perdas, discounting e salvage;
- regression tests e checksums;
- registar primal/dual feasibility, gap, runtime, termination e warnings;
- repetir headline runs com tolerâncias mais apertadas e, quando possível, solver/modelo independente;
- se custo for estável e capacidade variar, declarar não-unicidade em vez de escolher um mix “verdadeiro”.

Fazer intercomparação faseada com um segundo modelo/equipa: one-node, storage/hydro, PT–ES, UC, expansão, carbono e finalmente adequação. Manter um difference register que atribua discrepâncias a dados, formulação, solver ou incerteza estrutural.

## Acesso administrativo e reutilização

Base legal principal: Lei n.º 26/2016 — LADA, consolidada. https://diariodarepublica.pt/dr/legislacao-consolidada/lei/2016-106603618

Pontos operacionais:

- qualquer pessoa pode pedir documentos administrativos preexistentes sem demonstrar interesse especial;
- pedir o formato eletrónico nativo, dicionário de dados, inventário de tabelas e exportações já existentes;
- a entidade não tem de criar estudos ou fazer novos cálculos;
- uma extração simples de uma base preexistente pode ser pedida, mas não uma análise nova;
- pedir comunicação parcial com expurgo apenas dos campos reservados;
- segredo comercial e segurança de infraestruturas devem ser fundamentados concretamente;
- acesso e reutilização/publicação são pedidos distintos;
- pedir explicitamente licença de reutilização para investigação e publicação em repositório;
- perante silêncio, recusa ou resposta parcial, existe via de queixa para a CADA.

Prazos anotados:

- resposta normal: 10 dias;
- prorrogação excecional fundamentada pode chegar a dois meses;
- queixa à CADA: normalmente 20 dias após silêncio, recusa ou satisfação parcial.

Isto não é aconselhamento jurídico. Confirmar sempre a versão consolidada da lei e os prazos antes de enviar.

Precedente útil sobre licenças DGEG: https://www.cada.pt/files/pareceres/2021/188.pdf

Estratégia: pedidos separados e estreitos, em vez de um pedido único com todas as categorias.

1. DGEG — registo de produção/armazenamento e crosswalk de licenças.
2. REN — EIC local, unidade–nó, parâmetros, operação, restrições e curtailment.
3. ERSE — reportes regulatórios, custos, reservas e dados insulares.
4. APA/ARH — títulos, concessões, caudais e autocontrolo hídrico.
5. E-REDES — modelo estático de planeamento e custos de reforço.
6. EDA/EEM — séries operacionais insulares.

Formulação-base:

> Ao abrigo da Lei n.º 26/2016, solicita-se acesso aos documentos e dados preexistentes abaixo identificados, preferencialmente no formato eletrónico nativo em que são mantidos, bem como às condições de reutilização para investigação e publicação. Caso existam campos reservados, solicita-se comunicação parcial com expurgo apenas da matéria protegida e fundamentação concreta por campo/documento. Caso não exista a exportação pedida, solicita-se dicionário de dados, inventário de registos e identificação dos relatórios/tabelas preexistentes.

Para dados ambientais, invocar também os artigos 17.º e 18.º. Para produtores privados, pedir prioritariamente a cópia na posse de DGEG, ERSE, APA ou operador regulado.

A LADA abrange diretamente autoridades como DGEG, ERSE e APA e pode abranger concessionários/empresas de serviço público no exercício materialmente administrativo ou ambiental. Quando raw data não puderem ser publicados, negociar acesso controlado/NDA/clean room e publicar apenas estatísticas, parâmetros calibrados, hashes e código.

## Reprodutibilidade, governação e claims

### Artefactos obrigatórios

Cada fonte deve ter:

- proprietário e URL;
- data/hora de aquisição;
- versão/API;
- licença e texto de atribuição;
- granularidade, timezone, unidades e cobertura;
- provisional/final;
- checksum do raw pull;
- script de transformação;
- permissão de redistribuição e notas jurídicas.

Cada run deve criar manifest imutável com:

- run ID, timestamp, Git commit e dirty-tree status;
- hash de configuração e inputs;
- versões de modelo, dependências e solver;
- opções, random seeds, threads, CPU/RAM/OS;
- cenário, pesos/probabilidades e parent run;
- status, gap, resíduos, runtime, logs e checksums de outputs.

Repositório-alvo:

~~~text
README.md
CITATION.cff
LICENSE
environment/lockfile
Snakefile
config/base + config/scenarios
src/ingestion + accounting + model + validation + reporting
data/sources.csv + raw-manifests + schemas + derived
tests/unit + integration + regression + accounting-identities
docs/protocol + cost-ontology + assumptions + licensing + limitations + decision-log
results
paper
containers
run-manifests
~~~

Não guardar credenciais. Raw data sem licença de redistribuição fica fora do repositório; publicar manifests, hashes, scripts de aquisição e um benchmark sintético/reduzido.

### Governação

- publicar protocolo antes dos cenários politicamente relevantes;
- manter assumptions register, cost ontology, decision log, conflitos de interesse, financiamento e declaração de uso de AI;
- revisão de métodos/código antes da interpretação;
- auditoria separada de dados/regulação MIBEL;
- adversarial claims review depois do draft;
- pagar uma reprodução independente numa máquina limpa;
- preprint + issues públicos durante 30–45 dias + response matrix;
- releases imutáveis com DOI.

Perfis externos prioritários: operações/adequação ibérica, regulação/tarifas, estatística/incerteza, clima/hidro, research software/licensing e externalidades se monetizadas.

### Formulações defensáveis

- “Dentro da fronteira elétrica ibérica e das hipóteses, o cenário A tem custo de recursos estimado X–Y.”
- “O resultado é/não é robusto às sensibilidades testadas.”
- “É um benchmark cost-optimal, não uma previsão.”
- “Incidência portuguesa difere do custo ibérico devido a comércio e alocação regulatória.”
- “Distribuição detalhada, estabilidade dinâmica e impactos não monetizados estão fora do núcleo ou em módulos separados.”

Evitar:

- “o verdadeiro custo total da tecnologia X”;
- atribuir backup/grid cost a uma tecnologia sem contrafactual e regra de alocação;
- inferir faturas a partir de custo de recursos;
- dizer que o modelo prova a política ótima;
- claims de segurança dinâmica a partir de expansão linear;
- fiabilidade baseada num só weather year;
- chamar totalmente reproduzível a um estudo cujos inputs essenciais não podem ser obtidos por terceiros.

## Hierarquia atual dos riscos de dados

### Críticos

- parâmetros térmicos validados por unidade;
- curvas/restrições hidráulicas finas e novas centrais do Tâmega;
- custos finais de projetos privados;
- modelos dinâmicos e dados de estabilidade;
- séries insulares sub-horárias.

### Importantes, mas contornáveis

- crosswalk unidade–nó;
- inventário de baterias;
- custos marginais locais da distribuição;
- curtailment canónico.

### Já suficientes para uma primeira versão

- grande frota via ENTSO-E + DGEG + REN;
- balanço, reservas, ativações e restrições via REN/SIME;
- hidrologia básica das principais cascatas via SNIRH;
- rede e cargas agregadas por subestação via E-REDES;
- custos reais agregados das redes reguladas;
- dados mensais/anuais das ilhas para calibração agregada.

## Próximos passos recomendados

1. Descarregar os quatro conjuntos ENTSO-E de unidades, produção e indisponibilidades e filtrar Portugal.
2. Construir o crosswalk inicial ENTSO-E–DGEG–REN–E-REDES–OMIE, com um campo de confiança e proveniência por correspondência.
3. Quantificar cobertura: número de unidades e percentagem de MW identificados, ligados a nó e com séries operacionais.
4. Criar um data catalogue com licença, periodicidade, granularidade, identificadores, cobertura e checksum.
5. Implementar os pedidos LADA prioritários depois de medir exatamente os campos em falta.
6. Definir versões do modelo por fidelidade:
   - V0: balanço nacional/zonal;
   - V1: Portugal–Espanha e nós/subestações principais;
   - V2: unit commitment, reservas, hidrologia cronológica e adequação estocástica;
   - módulo separado de triagem de estabilidade, sem alegar validação TSO.
7. Tratar todos os parâmetros não observados como distribuições/sensibilidades, nunca como valores exatos não documentados.

## Registo desta memória

- 2026-08-10, versão inicial: objetivo, contabilidade resumida e auditoria das dez lacunas.
- 2026-08-10, auditoria de completude: restaurados metodologia NEA/whole-system, arquitetura do modelo, ferramentas/compute, viabilidade solo, cenários ibéricos, nuclear paramétrico, fontes transversais, incerteza/adequação/validação, LADA, reprodutibilidade, governação e limites dos claims.
- 2026-08-10, segunda auditoria de completude: comparadas individualmente as linhas de cost accounting, metodologia, open-source models/compute, viabilidade/governação, incerteza/validação, cenários ibéricos, nuclear, inventário português e as dez verificações dirigidas; acrescentados limiares, priors, fontes complementares, alternativas de acesso e conclusões substituídas.

À data deste snapshot, este ficheiro era a memória canónica do projeto. Desde 2026-08-11 é apenas arquivo histórico; o estado corrente vive em `PROJECT_STATUS.md` e nos documentos temáticos. Factos políticos, versões de software, capacidades de interligação, projetos e licenças devem ser reverificados na data de cada análise/release.
