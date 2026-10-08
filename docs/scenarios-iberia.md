# Cenários ibéricos

> Estado editorial: working  
> Última verificação factual: 2026-08-12  
> Âmbito: procura, política, infraestrutura, clima e narrativas PT–ES–FR  
> Documento canónico para: definição dos cenários; não para parâmetros técnicos nucleares  
> Rever quando: houver alteração legal, plano, eleição, autorização ou data de projeto

Factos nesta página são temporalmente instáveis. Cada release deve reverificá-los.

## Taxonomia

- **Baseline legal/político:** leis, autorizações e infraestrutura em vigor.
- **Projetos esperados:** em construção ou suficientemente avançados, sempre com sensibilidade de atraso.
- **Contrafactuais:** extensões, aceleração, não-entrega e stress; nunca apresentados como política vigente.

## Nuclear espanhol

**FACT:** autorização legal vigente e calendário político/protocolar são relógios diferentes. No snapshot de 2026-08-12, Almaraz pedira uma data comum de 08-06-2030 e o CSN emitira parecer favorável condicionado em 16-07-2026, mas não existia ainda ordem ministerial final do MITECO.

| Unidade | Autorização vigente | Cessação PGRR/protocolo |
|---|---:|---:|
| Almaraz I | 01-11-2027 | 11-2027 |
| Almaraz II | 31-10-2028 | 10-2028 |
| Ascó I | 02-10-2030 | 10-2030 |
| Cofrentes | 30-11-2030 | 11-2030 |
| Ascó II | 02-10-2031 | 09-2032 |
| Vandellós II | 26-07-2030 | 02-2035 |
| Trillo | 17-11-2034 | 05-2035 |

Fontes: [PNIEC](https://www.miteco.gob.es/content/dam/miteco/es/energia/files-1/pniec-2023-2030/PNIEC_2024_240924.pdf), [7.º plano de resíduos](https://www.enresa.es/documentos/ES_7-plan-general-residuos-radiactivos_.pdf) e [parecer do CSN sobre Almaraz](https://www.csn.es/-/informe-favorable-almaraz).

Ascó II, Vandellós II e Trillo precisam de atos adicionais para chegar às datas protocolares. O fim dos 40 anos de projeto também não é encerramento automático. Ramos: autorizações vigentes; calendário protocolar; Almaraz até 08-06-2030; extensão específica +5/+10/+20 anos por central; e stress de baixa disponibilidade/avarias. Custos e parâmetros destas opções pertencem ao [dossier nuclear](nuclear.md).

## Procura e política

**FACT:** a versão final do PNEC, publicada pela [Resolução da Assembleia da República n.º 127/2025](https://diariodarepublica.pt/dr/detalhe/resolucao-assembleia-republica/127-2025-914597185), fixa 51% de renováveis no consumo final bruto e 93% na eletricidade em 2030. Inclui cerca de 8,1 GW hidro/bombagem, 10,4 GW eólica onshore, 2 GW offshore, 20,8 GW PV, 2 GW baterias e 3,5 GW gás. É uma ambição política, não previsão neutra.

**FACT:** o consumo da rede pública portuguesa foi aproximadamente 53,1 TWh em 2025; ramos PNEC de indústria verde/hidrogénio podem aproximar-se de 90 TWh. [REN](https://www.ren.pt/en-gb/media/news/electricity-consumption-reaches-highest-ever-level-in-2025).

**FACT:** o PNIEC espanhol apontava para cerca de 81% de renováveis elétricas em 2030, aproximadamente 62 GW wind, 76 GW PV, 22,5 GW storage e 12 GW de eletrolisadores, com procura muito acima de 2019. [MITECO](https://www.miteco.gob.es/es/prensa/ultimas-noticias/2024/septiembre/el-gobierno-aprueba-la-actualizacion-del-plan-nacional-integrado.html).

Separar pelo menos procura convencional e electro-industrial boom: veículos, data centres, indústria, bombas de calor e H2 dominam a incerteza mais do que a população. EUROPOP2025 sugeria cerca de 11,14 milhões em Portugal e 50,95 milhões em Espanha em 2030, com grande sensibilidade à migração. [Eurostat](https://ec.europa.eu/eurostat/databrowser/product/page/PROJ_25NP).

### Fronteira da procura

Cada cenário conserva dois ledgers reconciliados:

1. **eletricidade final direta** por setor;
2. **carga bruta da rede**, incluindo transformação/H2, storage e perdas e descontando behind-the-meter segundo a convenção da fonte.

Isto explica boa parte das diferenças entre PNEC/PNIEC, RMSA, ERAA e TYNDP. Âncoras úteis, que não devem ser somadas:

- Portugal: 53,1 TWh de procura de rede observada em 2025; ERAA 2030 cerca de 75,26 TWh/12,61 GW; ramos PNEC/RMSA de alta industrialização aproximam-se de 90 TWh;
- Espanha: 269,75 TWh incluindo autoconsumo versus 256,09 TWh de rede em 2025; PNIEC 2030 cerca de 273,81 TWh de eletricidade final e 357,70 TWh em barras, incluindo aproximadamente 55,82 TWh no setor de transformação.

H2, data centres e grandes projetos usam estados `acesso → autorização → FID → construção → commissioning → rampa`. Capacidade anunciada ou permitida não é convertida em `MW × 8 760`. Demand response desloca/reduz carga com duração, rebound e desutilidade; não reduz gratuitamente o consumo anual.

## Interligações

**FACT:** a nova interligação PT–ES inaugurada em 02-07-2026 elevou aproximadamente a capacidade para 4,2 GW ES→PT e 3,5 GW PT→ES. [REE](https://www.ree.es/en/press-office/news/press-release/2026/07/espana-y-portugal-inauguran-la-nueva-interconexion).

Estes valores são capacidade técnica potencial do sistema. As NTC comerciais variam por direção, mês, topologia e condição operacional e podem ser substancialmente inferiores; não usar 4,2/3,5 GW como limite horário invariável.

**FACT:** ES–FR tinha cerca de 2,8 GW. Bay of Biscay, 2 GW, iniciou o lançamento de cabos submarinos em junho de 2026 e mantinha entrada em serviço no início de 2028, levando a fronteira a cerca de 5 GW. Testar atraso/não-entrega. Cerca de 8 GW em 2040 continua objetivo dependente de projetos adicionais, não capacidade contratada. [RTE](https://www.rte-france.com/projets/nos-projets/golfe-de-gascogne).

As capacidades são direcionais, sujeitas a outage e derating. França nuclear não é capacidade firme portuguesa. Portugal e Espanha continuam zonas de oferta separadas: não modelar isolamento nem copperplate permanente. Produtos day-ahead de 15 minutos entraram em vigor para entrega desde 01-10-2025; períodos críticos devem ser validados a 15 minutos.

## TYNDP, hidrogénio e gás

Usar TYNDP para harmonizar condições de fronteira, não como resposta do estudo. O TYNDP 2024 incluía National Trends+, Distributed Energy e Global Ambition; o draft 2026 usa National Trends+ e variantes económicas. Fontes: [TYNDP 2024](https://tyndp.entsoe.eu/resources/tyndp2024-scenarios-report) e [TYNDP 2026](https://2026.entsos-tyndp-scenarios.eu/).

**FACT:** a data-alvo corrente de H2Med era 2032, não 2030. O baseline 2030 deve assumir ausência, com ramos de entrega, atraso e no-build depois. [H2Med](https://h2medproject.com/the-h2med-project-2/).

BarMar entrou em FEED em julho de 2026 e CelZa conserva alvo 2032, mas FEED, estatuto PCI e financiamento de estudos não são FID, autorização de construção nem contrato EPC.

Portugal e Espanha mantêm exposição a LNG. É necessário combinar gás/CO2 elevados com seca, encerramento nuclear e interligação limitada.

## Renováveis, storage e maturidade de projetos

Separar sempre potencial físico, técnico, económico e realizável. PNEC/PNIEC são metas; filas e licenças não são previsões.

- O LNEG estima potencial técnico português muito superior à meta solar, mas apenas cerca de 15,7 GW de eólica onshore no seu cenário territorial.
- O ENSPRESO2 de 2026 mostra que setbacks dominam o potencial onshore: valores da primeira edição não devem ser reutilizados como atuais.
- O PAER português reserva 2 706 km² e 9,4 GW offshore, mas é espaço de planeamento, não pipeline. Sem concurso comercial adjudicado no corte, 2 GW operacionais em 2030 é cenário stretch; o PDIRT usava aproximadamente 0,25 GW em 2030.
- Espanha também não tinha award/FID offshore comercial no corte; os 3 GW PNIEC não pertencem ao baseline esperado sem marcos adicionais.
- A consulta portuguesa de até 750 MVA de storage e os apoios espanhóis a 2,2 GW/9,4 GWh são pipeline/procedimento, não capacidade operacional.

Usar narrativas `slow`, `central` e `stretch` com build rates e haircuts por estágio. Repowering, ligação, aceitação, supply chain, portos, curtailment e procura flexível condicionam o realizável.

## Clima e emissões

O [PECD v4.2](https://cds.climate.copernicus.eu/datasets/sis-energy-pecd?tab=overview), CC BY 4.0, é o backbone futuro: 6 CMIP6 × 4 SSP, 2015–2100, com clima, vento, PV e hidro. ERA5/ERA5-Land servem o backcast físico. Cada realização conserva `SSP → GCM → tempo → PT–ES–FR → procura → vento → solar → hidro → derating`; não sortear países ou tecnologias independentemente.

Não existe um cap elétrico ibérico diretamente copiado da lei. ETS é UE-wide e PNEC/PNIEC são nacionais/economy-wide. O core deve usar uma restrição absoluta e explicitamente construída para emissões operacionais diretas da geração continental PT+ES, com reporting nacional separado. Imports, lifecycle, biomassa, CHP, pequenas unidades e créditos/remoções entram em variantes documentadas. Cap, preço ETS, shadow price e dano social são objetos diferentes.

## Biblioteca de branches

Esta lista é um menu de incertezas, não a matriz obrigatória do primeiro experimento:

1. policy 2030 com autorizações nucleares vigentes e trajetória PNEC/PNIEC realizável;
2. Almaraz até 2030;
3. extensão espanhola +5/+10/+20 anos;
4. slow delivery de renováveis, storage, redes e eletrificação;
5. electro-industrial boom;
6. seca ibérica severa e plurianual;
7. Bay of Biscay: atraso versus 5/8 GW ES–FR;
8. stress de gás e H2.

P4 começa com uma referência, 2–3 contrafactuais focais e três weather years coerentes. Os restantes branches só são promovidos quando a sua amplitude plausível puder alterar o resultado. Compound stresses prioritários para fases posteriores:

- nuclear closure + drought + high gas + Bay delay;
- high demand + delayed storage/grid;
- fast renewables + slow H2 demand + constrained exports.

Clima, procura, vento, solar e hidro devem ser cronologicamente coerentes. “Normal”, “húmido” e “seco” não podem ser construídos combinando fatores de capacidade independentes.
