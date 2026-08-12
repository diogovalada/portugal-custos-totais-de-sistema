# Ativos de geração e armazenamento

> Estado editorial: working  
> Última verificação factual: 2026-08-11  
> Âmbito: cadastro, localização, nós, parâmetros unitários e baterias  
> Documento canónico para: inventário físico e técnico dos ativos  
> Rever quando: houver novo export DGEG/REN/ENTSO-E ou atualização do PyPSA-Eur

## Unidades e nós

**FACT:** `ProductionAndGenerationUnits_r3` da ENTSO-E constitui uma boa espinha dorsal para production units existentes/planeadas ≥100 MW e os generation units que as compõem. Inclui códigos, nomes, estado/validade, tecnologia, potência, localização textual, tensão, bidding zone e control area.

Fontes: [especificação](https://transparencyplatform.zendesk.com/hc/en-us/articles/36496214610449), [capacidade por production unit](https://transparencyplatform.zendesk.com/hc/en-us/articles/36496107495953), [produção real por generation unit](https://transparencyplatform.zendesk.com/hc/en-us/articles/39309514389777-ActualGenerationOutputPerGenerationUnit-16-1-A-r3), [File Library](https://transparencyplatform.zendesk.com/hc/en-us/articles/35960137882129-File-Library-Guide), [Regulamento 543/2013](https://eur-lex.europa.eu/eli/reg/2013/543/oj) e [EIC](https://www.entsoe.eu/data/energy-identification-codes-eic/).

Limites:

- não identifica subestação, barramento, terminal, bay ou ponto de entrega;
- localização textual e tensão não determinam o nó;
- o limiar exclui a maioria de solar, eólica, cogeração, pequena hídrica e baterias;
- capacidade ≥1 MW é publicada agregada por tecnologia;
- EIC válido não comprova operação;
- a lista EIC central pode omitir códigos locais emitidos pela REN.

### Coordenadas e PyPSA-Eur

**FACT:** o PyPSA-Eur, através do `powerplantmatching`, fornece `lat`/`lon` para muitas centrais convencionais a partir de várias bases e permite correções customizadas. Depois atribui espacialmente a central a uma região/bus, com nearest-neighbour para casos não correspondidos. [Código oficial](https://github.com/PyPSA/pypsa-eur/blob/master/scripts/build_powerplants.py) e [campos do powerplantmatching](https://powerplantmatching.readthedocs.io/en/latest/basics/).

Isto corrige a formulação “coordenadas geralmente não disponíveis”: coordenadas aproximadas da central estão frequentemente disponíveis. Porém, podem ser centroides/geocoding pelo nome, não coordenadas oficiais por grupo, e o `bus` resultante é uma inferência de modelação, não o ponto físico confirmado. O exemplo oficial mostra que a camada ENTSO-E isolada pode ter `lat/lon` ausentes e que o preenchimento vem do matching. [Exemplo](https://powerplantmatching.readthedocs.io/en/latest/examples/example/).

### Peças complementares

- DGEG WFS/ArcGIS: processos, proprietário, potência, datas, concelho e geometria. [Geoinformação](https://www.dgeg.gov.pt/pt/servicos-online/informacao-geografica/energia/energia-eletrica/).
- [Projetos licenciados DGEG](https://www.dgeg.gov.pt/pt/areas-setoriais/energia/energia-eletrica/producao-de-energia-eletrica/projetos-licenciados/).
- [Mapa REN 2026](https://www.ren.pt/media/fcbh2aqx/mapa-eletricidade-2026-ren.pdf): instalação RNT de ligação para várias centrais.
- [Capacidade de receção E-REDES](https://e-redes.opendatasoft.com/explore/dataset/capacidade-rececao-rnd/information/): nós e geração agregada, não crosswalk unitário.
- [Unidades de oferta OMIE](https://www.omie.es/informes_mercado/listados/lista_unidades.pdf): uma unidade de mercado pode agregar ativos físicos.

Snapshot DGEG testado em 2026-08-10: 17 objetos térmicos, 134 hídricos, 2 890 eólicos, 732 solares e 24 de cogeração. Não são contagens de centrais operacionais: podem existir objetos por aerogerador/bloco/polígono, projetos em licenciamento, duplicados e omissões.

Crosswalk-alvo:

```text
central → grupo → processo DGEG → EIC → unidade OMIE → proprietário
        → subestação/nó → tensão → MW/MWh → estado → validade
```

Cada match deve guardar fonte, método, distância, confiança e datas de validade.

O [Decreto-Lei n.º 15/2022](https://diariodarepublica.pt/dr/legislacao-consolidada/decreto-lei/2022-177634029), artigos 29.º e 106.º, indica que licença/ponto de receção e uma base articulada DGEG–REN existem administrativamente. Isto sustenta pedir exports e identificadores, não prova publicação.

## Parâmetros técnicos por grupo

**FACT:** REN/GGS recebe indisponibilidades, potência disponível, parâmetros dinâmicos, limites e planos de manutenção. A RMSA usa arranques, mínimos de paragem e rampas de CCGT sem publicar os valores unitários.

Fontes: [MPGGS](https://www.erse.pt/media/q10chfti/mpggs_articulado-250911.pdf), [RMSA-E 2025](https://www.dgeg.gov.pt/media/wq4bi1to/rmsa-e-2025.pdf) e [ERAA modelling data](https://www.entsoe.eu/eraa/2025/modelling-data/).

Priors ERAA ilustrativos para CCGT, nunca rotulados como dados portugueses:

- eficiência aproximadamente 40–60% por vintage;
- mínimo técnico frequentemente 40–50%;
- min-on/off cerca de 2–3 h;
- rampa ascendente cerca de 2–4% Pmax/min;
- FOR cerca de 5–8%;
- manutenção planeada de referência cerca de 27 dias/ano.

Produção ENTSO-E por generation unit cobre ≥100 MW; eventos de indisponibilidade material usam tipicamente mudanças ≥100 MW. São úteis para validação e grandes avarias, não um censo de deratings.

Lacunas críticas: heat-rate curve por carga, custo físico de arranque/no-load, rampas/mínimos validados, FOR/EFORd por unidade e histórico de deratings abaixo do limiar. ACER REMIT e OMIE são complementos; o plano integral de manutenção REN não foi encontrado aberto.

## Baterias

**FACT:** não existe um cadastro público português autoritativo e completo combinando MW, MWh, nó, estado e datas.

Fontes parciais:

- [JRC European Energy Storage Inventory](https://ses.jrc.ec.europa.eu/storage-inventory): MW/MWh, tecnologia, estado e coordenadas, com estimativas e sem nó;
- licenciamento/registo DGEG;
- agregados e modelo de reporte ERSE;
- balanços REN;
- APA/SIAIA, PRR/Fundo Ambiental e promotores;
- [baterias EEM](https://eeminov.eem.pt/cb/).

O armazenamento autónomo >1 MW requer licença, até 1 MW registo prévio, e o armazenamento associado integra o processo de produção. O indicador regulatório G5 pede MW, MWh, tecnologia, propriedade e autónomo/co-localizado. [Manual de reporte ERSE](https://www.erse.pt/media/bvzfelpi/manual-reporte.pdf).

Snapshots a rever: JRC tinha 74 projetos portugueses, 56 eletroquímicos; ERSE reportava 7 MW/26 MWh na RNT no fim de 2024; REN reportava 19 MW instalados em julho de 2026. Diferenças podem refletir data, âmbito e definição. [Relatório ERSE](https://www.erse.pt/media/f4eh0fph/relat%C3%B3rio-art249-dl15_2022.pdf).

Campos a pedir: ID, estado, standalone/co-localizada/behind-the-meter, MW de carga/descarga, MWh bruto/útil, química, localização, nó/tensão, datas de licença/teste/operação e ativo associado.
