# Cenários ibéricos

> Estado editorial: working  
> Última verificação factual: 2026-08-10  
> Âmbito: procura, política, infraestrutura, clima e narrativas PT–ES–FR  
> Documento canónico para: definição dos cenários; não para parâmetros técnicos nucleares  
> Rever quando: houver alteração legal, plano, eleição, autorização ou data de projeto

Factos nesta página são temporalmente instáveis. Cada release deve reverificá-los.

## Taxonomia

- **Baseline legal/político:** leis, autorizações e infraestrutura em vigor.
- **Projetos esperados:** em construção ou suficientemente avançados, sempre com sensibilidade de atraso.
- **Contrafactuais:** extensões, aceleração, não-entrega e stress; nunca apresentados como política vigente.

## Nuclear espanhol

**FACT:** no snapshot de 2026-08-10, o baseline legal continuava a prever o encerramento dos sete reatores entre 2027 e 2035. Almaraz tinha pedido extensão até junho de 2030 e o CSN emitira parecer favorável condicionado em 16-07-2026, sem ainda constituir a decisão governamental final.

| Unidade | Data de referência |
|---|---:|
| Almaraz I | novembro de 2027 |
| Almaraz II | outubro de 2028 |
| Ascó I | outubro de 2030 |
| Cofrentes | novembro de 2030 |
| Ascó II | setembro de 2032 |
| Vandellós II | fevereiro de 2035 |
| Trillo | maio de 2035 |

Fontes: [PNIEC](https://www.miteco.gob.es/content/dam/miteco/es/energia/files-1/pniec-2023-2030/PNIEC_2024_240924.pdf), [7.º plano de resíduos](https://www.enresa.es/documentos/ES_7-plan-general-residuos-radiactivos_.pdf) e [parecer do CSN sobre Almaraz](https://www.csn.es/-/informe-favorable-almaraz).

Ramos: calendário legal; Almaraz até junho de 2030; extensão específica +5/+10 anos por central; e stress de baixa disponibilidade/avarias. Custos e parâmetros destas opções pertencem ao [dossier nuclear](nuclear.md).

## Procura e política

**FACT:** o PNEC português indicava aproximadamente 51% de renováveis no consumo final e 93% na eletricidade em 2030, com cerca de 8,1 GW hidro/bombagem, 10,4 GW eólica onshore, 2 GW offshore, 20,8 GW PV, 2 GW baterias e 3,5 GW gás. É uma ambição política, não previsão neutra. [PNEC Portugal](https://apambiente.pt/sites/default/files/_Clima/20241118_pnec2030_para_aprov_ar.pdf).

**FACT:** o consumo da rede pública portuguesa foi aproximadamente 53,1 TWh em 2025; ramos PNEC de indústria verde/hidrogénio podem aproximar-se de 90 TWh. [REN](https://www.ren.pt/en-gb/media/news/electricity-consumption-reaches-highest-ever-level-in-2025).

**FACT:** o PNIEC espanhol apontava para cerca de 81% de renováveis elétricas em 2030, aproximadamente 62 GW wind, 76 GW PV, 22,5 GW storage e 12 GW de eletrolisadores, com procura muito acima de 2019. [MITECO](https://www.miteco.gob.es/es/prensa/ultimas-noticias/2024/septiembre/el-gobierno-aprueba-la-actualizacion-del-plan-nacional-integrado.html).

Separar pelo menos procura convencional e electro-industrial boom: veículos, data centres, indústria, bombas de calor e H2 dominam a incerteza mais do que a população. EUROPOP2025 sugeria cerca de 11,14 milhões em Portugal e 50,95 milhões em Espanha em 2030, com grande sensibilidade à migração. [Eurostat](https://ec.europa.eu/eurostat/databrowser/product/page/PROJ_25NP).

## Interligações

**FACT:** a nova interligação PT–ES inaugurada em 02-07-2026 elevou aproximadamente a capacidade para 4,2 GW ES→PT e 3,5 GW PT→ES. [REE](https://www.ree.es/en/press-office/news/press-release/2026/07/espana-y-portugal-inauguran-la-nueva-interconexion).

**FACT:** ES–FR tinha cerca de 2,8 GW; Bay of Biscay, 2 GW, era esperado para início de 2028, levando a fronteira a cerca de 5 GW. Testar atraso/não-entrega e cerca de 8 GW em 2040. [RTE](https://www.rte-france.com/actualites/2026-05-28-landes-pose-cables-interconnexion-france-espagne).

As capacidades são direcionais, sujeitas a outage e derating. França nuclear não é capacidade firme portuguesa. Portugal e Espanha continuam zonas de oferta separadas: não modelar isolamento nem copperplate permanente. Produtos day-ahead de 15 minutos entraram em vigor para entrega desde 01-10-2025; períodos críticos devem ser validados a 15 minutos.

## TYNDP, hidrogénio e gás

Usar TYNDP para harmonizar condições de fronteira, não como resposta do estudo. O TYNDP 2024 incluía National Trends+, Distributed Energy e Global Ambition; o draft 2026 usa National Trends+ e variantes económicas. Fontes: [TYNDP 2024](https://tyndp.entsoe.eu/resources/tyndp2024-scenarios-report) e [TYNDP 2026](https://2026.entsos-tyndp-scenarios.eu/).

**FACT:** a data-alvo corrente de H2Med era 2032, não 2030. O baseline 2030 deve assumir ausência, com ramos de entrega, atraso e no-build depois. [H2Med](https://h2medproject.com/the-h2med-project-2/).

Portugal e Espanha mantêm exposição a LNG. É necessário combinar gás/CO2 elevados com seca, encerramento nuclear e interligação limitada.

## Matriz mínima

1. Policy 2030 com datas nucleares legais.
2. Almaraz até 2030.
3. Extensão espanhola +5/+10 anos.
4. Slow delivery de renováveis, storage, redes e eletrificação.
5. Electro-industrial boom.
6. Seca ibérica severa e plurianual.
7. Bay of Biscay: atraso versus 5/8 GW ES–FR.
8. Stress de gás e H2.

Compound stresses prioritários:

- nuclear closure + drought + high gas + Bay delay;
- high demand + delayed storage/grid;
- fast renewables + slow H2 demand + constrained exports.

Clima, procura, vento, solar e hidro devem ser cronologicamente coerentes. “Normal”, “húmido” e “seco” não podem ser construídos combinando fatores de capacidade independentes.

