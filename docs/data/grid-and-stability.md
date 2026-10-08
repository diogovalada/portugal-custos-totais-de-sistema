# Rede, distribuição e estabilidade

> Estado editorial: working  
> Última verificação factual: 2026-08-12
> Âmbito: topologia, custos de reforço, tensão, reativa, inércia e modelos dinâmicos  
> Documento canónico para: fidelidade física da rede e respetivas lacunas  
> Rever quando: houver novo PDIRT/PDIRD, licença E-REDES ou acesso CGMES

## Distribuição

**FACT:** a E-REDES disponibiliza uma camada aberta rica ao nível de subestação e zona, mas não um modelo elétrico nacional suficiente para load flow.

Fontes abertas:

- [características da rede](https://e-redes.opendatasoft.com/explore/dataset/caracteristicas-da-rede/): subestações, transformação, carga, curto-circuito e regime de neutro;
- [postos de transformação](https://e-redes.opendatasoft.com/explore/dataset/postos-transformacao-distribuicao/): localização e atributos de PTD;
- [capacidade de receção](https://e-redes.opendatasoft.com/explore/dataset/capacidade-rececao-rnd/information/): capacidade atual, comprometida e restrições por instalação/tensão;
- datasets quarto-horários de carga por subestação;
- [PDIRD e anexos](https://www.erse.pt/atividade/consultas-publicas/consulta-publica-126/abertura/): cargas, comprimentos, N-1, projetos e CAPEX planeado.

Snapshot 2026-08-10: aproximadamente 437 subestações, 72 mil PTD e mais de 14 milhões de registos quarto-horários de carga por subestação. Os totais são dinâmicos.

Algumas geometrias AT/MT são tecnicamente visíveis nos mapas RARI, mas estavam marcadas `restricted/internal`, sem licença pública clara. Não devem ser extraídas ou republicadas no projeto sem autorização escrita. Mesmo essas geometrias não fornecem extremos elétricos, estados de interruptores, condutores, R/X/B, ampacidade, taps ou proteções.

Lacunas efetivas:

- grafo AT/MT/BT canónico e estado normal de manobra;
- endpoints elétricos e conectividade;
- R/X/B, ampacidades, taps e transformadores;
- topologia BT nacional;
- carga/produção nodal completa;
- curvas locais EUR/MW ou EUR/MVA de reforço/hosting;
- catálogo de custos unitários e outturn por projeto;
- licença estável para geometrias restritas.

“Custo marginal de reforço” pode não existir como campo pré-calculado: é frequentemente o resultado lumpy de um estudo de ligação. Custos incrementais tarifários ERSE, encargos de ligação e projetos PDIRD são proxies sistémicos, não custos nodais observados.

É defensável construir um modelo zonal ou por subestação. Não é defensável afirmar que reproduz a RND real.

## Transmissão PT–ES–FR

**FACT:** não existe um snapshot aberto, versionado e adequadamente licenciado que combine topologia elétrica, R/X/B, ratings, taps, estados, outages, injeções nodais e correspondência projeto–custo realizado para a rede PT–ES–FR.

É necessário distinguir quatro objetos:

| Camada | Disponibilidade e uso |
|---|---|
| Topologia geográfica | Mapas TSO, OSM e PyPSA-Eur; útil para geometria e inventário aproximados |
| Modelo DC de planeamento | Reproduzível com PyPSA-Eur/OSM e parâmetros sintéticos; adequado a screening |
| CGMES/IGM/CGM | O standard CGMES é público, mas os modelos reais são trocados em infraestrutura segura ou por acesso institucional |
| Estado operacional | Switching, taps, shunts, fluxos P/Q, estimativa de estado e limites aplicáveis a uma hora não são open data |

Fontes públicas relevantes:

- [REN Data Hub — rede elétrica](https://datahub.ren.pt/pt/redes/rede-eletrica/) e PDIRT;
- REE: nós/capacidade de acesso, correntes de curto-circuito e parâmetros normalizados de linhas típicas;
- RTE/CRE: inventários GIS históricos e custos agregados;
- [TYNDP](https://www.entsoe.eu/outlooks/tyndp/2024/) e Transparency Platform: NTC/ATC, fluxos, grandes outages, redispatch e projetos;
- [PyPSA-Eur](https://github.com/PyPSA/pypsa-eur) e OSM: baseline aberta, mas com tipos de linha, transformadores, ratings e cargas parcialmente inferidos.

PT–ES e ES–FR continuam a ser representadas publicamente sobretudo por CNTC/NTC coordenados, não por um domínio flow-based operacional aberto. NTC não é o rating de uma linha e os 4,2/3,5 GW PT–ES inaugurados em 2026 não são limites comerciais horários garantidos.

O P3 pode comparar:

1. transporte zonal CNTC;
2. DC-KVL sintético, começando por 2–5 zonas e aumentando a resolução apenas se congestionamento/localização forem materiais;
3. topologias e deratings conservadores.

Essa escada permite estudar congestão estrutural e valor agregado de reforços. Não permite alegar reprodução da RNT/RdT/RPT, causalidade por ramo, N-1 oficial ou congestão operacional nodal. `GAP-013` separa agora esta lacuna de transmissão das lacunas de distribuição e estabilidade.

## Tensão, reativa e estabilidade

**FACT:** existe uma camada pública útil de requisitos, qualidade, planeamento e custos:

- [qualidade de energia REN por ponto](https://www.ren.pt/atividade/qualidade-de-energia): conformidade e eventos, não séries brutas;
- [PDIRT 2025–2034](https://www.erse.pt/media/5ugp1p1x/pdirt-2025-2034-proposta-inicial-vol-i-sem-anexos.pdf): estudos e investimento em reatores, STATCOM e compensadores;
- [Anexo 16](https://www.erse.pt/media/lx5n5kao/pdirt-2025-2034-proposta-inicial-vol-i-anexos-1-a-16.pdf): correntes de defeito mín./máx. e X/R projetados por nó;
- [requisitos RfG](https://www.dgeg.gov.pt/pt/areas-setoriais/energia/energia-eletrica/servicos-e-redes/codigos-de-rede-europeus/requisitos-geradores-rfg/): frequência, tensão, ride-through e controlo;
- [relatório do apagão ibérico de 2025](https://www.entsoe.eu/publications/blackout/28-april-2025-iberian-blackout/): PMU/SCADA e dinâmica detalhada, mas limitada ao incidente e anonimizada.

Existem ainda concursos e preços públicos de black start. O PDIRT propunha um portefólio condicional de reatores, STATCOM e compensador síncrono da ordem de EUR 127 milhões. Isto apoia screens e custos de investimento, não validação dinâmica.

## Camada não aberta

- SCADA/PMU contínuo e formas de onda;
- estado AC/estimativa de estado e P/Q/V nodal;
- taps, shunts e ordens de reativa operacionais;
- modelos dinâmicos/EMT por unidade;
- AVR, PSS, governors, controlos de inversores e proteções;
- séries horárias/sub-horárias de inércia e strength;
- IGM/CGM operacionais e casos completos de estabilidade;
- sequências detalhadas de defesa e reposição.

REN recebe muitos destes parâmetros; os modelos continentais ENTSO-E acessíveis por pedido/NDA são anonimizados ou simplificados e não substituem o modelo ibérico de tensão, transitórios, proteção e EMT.

Modelos genéricos, correntes do Anexo 16, envelopes RfG e despacho público podem alimentar proxies sintéticos. Os resultados devem ser chamados screening de plausibilidade, nunca validação TSO.
