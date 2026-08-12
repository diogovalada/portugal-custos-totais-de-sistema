# Auditoria de incertezas e dados — 2026-08-12

> Estado editorial: verified snapshot  
> Data de corte: 2026-08-12  
> Âmbito: incertezas que podiam ser reduzidas por investigação documental antes da implementação  
> Documento canónico para: evidência da ronda de investigação; as conclusões correntes pertencem aos documentos temáticos e aos registos

## Como foi feita

A auditoria mobilizou 100 agentes de investigação, organizados em coordenadores temáticos e subagentes `gpt-5.6-sol`, com raciocínio `high`, além da síntese do agente principal. Foram privilegiadas fontes primárias: legislação, reguladores, operadores de rede, estatísticas oficiais, datasets europeus, documentação de software e literatura metodológica original.

Os agentes não editaram o repositório. A síntese posterior confrontou as conclusões com os documentos canónicos e classificou cada ponto como facto verificado, pressuposto, decisão ainda aberta ou lacuna de dados.

Conclusões incompatíveis não foram resolvidas por votação. A síntese voltou à fonte primária: por exemplo, um memorando secundário usou 0,94 h/ano para Espanha, mas a resolução vigente do BOE fixa inequivocamente 1,5 h; o valor rejeitado não entrou nos registos. Esta auditoria preserva o resultado reconciliado, não uma concatenação dos relatórios dos agentes.

## Incertezas substancialmente fechadas

| Tema | Conclusão verificada | Consequência |
|---|---|---|
| Fiabilidade | Portugal continental usa LOLE 1,46 h/ano; Espanha usa 1,5 h/ano. Os VOLL oficiais são 12 433 EUR/MWh para Portugal e 22 879 EUR/MWh para Espanha, antes da harmonização monetária | Aplicar constraints e VOLL zonais, não uma média ibérica |
| Clima | O PECD v4.2 está disponível no CDS, CC BY 4.0, com histórico e 6 GCM × 4 SSP até 2100 | Usá-lo como backbone clima–energia futuro; ERA5/ERA5-Land ficam como baseline físico histórico |
| Computação | LP anual de 10–30 clusters é viável numa workstation/cloud moderada; GPU não é prioridade | O risco principal é o produto UC × weather × ensemble × ELCC, não o LP base |
| Acesso administrativo PT | Prazos, formatos e regimes de acesso/reutilização foram confirmados; existe ainda a via AMA/ambiente seguro do DL 2/2025 | Pedidos estreitos, por tema e ano-piloto, em formato estruturado já existente |
| Hidro de planeamento | SNIRH, PGRH, CNPGB, DGEG e documentos ambientais permitem séries, grande parte do grafo, curvas cota-volume e várias obrigações | `GAP-003` permanece crítico apenas para hidráulica/UC fino e cobertura não harmonizada |
| Espanha agregada | ESIOS, REData, MITECO, CEDEX, CNMC, ENTSO-E e ERAA suportam um P3 zonal agregado | Espanha deve ser endógena; continuam vedadas alegações unitárias/nodais simétricas |
| Custos tecnológicos | Existe uma hierarquia defensável por linha: outturn/projeto ibérico → EC 2026 → TYNDP → technology-data v0.15.0 → DEA/IRENA/IEA/JRC | Não adotar um único CSV como autoridade nem aplicar learning duas vezes |
| Modelo secundário | Um único segundo modelo integral é uma unidade de decisão errada | Usar uma suite: fixtures Julia/JuMP, GenX para planeamento e Antares para adequação, sujeita a pilotos |

Fontes-chave: [DGEG — norma portuguesa](https://www.dgeg.gov.pt/pt/destaques/determinacao-da-norma-de-fiabilidade-para-portugal-continental/), [BOE — norma espanhola](https://www.boe.es/buscar/doc.php?id=BOE-A-2025-14438), [ERSE — VOLL/CONE](https://www.erse.pt/media/knfirrvo/relatorio-final-erse-voll-cone-dezembro-2025.pdf), [PECD v4.2](https://cds.climate.copernicus.eu/datasets/sis-energy-pecd?tab=overview), [Open Energy Benchmark](https://openenergybenchmark.org/blog/hipo_study), [LADA consolidada](https://diariodarepublica.pt/dr/legislacao-consolidada/lei/2016-106603618), [ERAA 2025](https://www.entsoe.eu/eraa/2025/modelling-data/) e [technology-data v0.15.0](https://github.com/PyPSA/technology-data/releases/tag/v0.15.0).

## Incertezas reduzidas, mas não fechadas

### Ativos, storage e ciclo de vida

- A ENTSO-E, DGEG, ESIOS/RAIPEE, REN/REE, ERSE e PyPSA-Eur fornecem uma boa espinha dorsal, mas não um crosswalk oficial e versionado `grupo → licença → EIC → nó`.
- Totais oficiais de baterias são utilizáveis apenas com perímetro e data. Portugal tinha 19 MW de baterias no fim de 2025 e um piso documentável de pelo menos 50 MWh; Espanha tinha 221,84 MW no indicador REE em julho de 2026. Isto não substitui cadastro asset-level, sobretudo BTM.
- Planeamento oficial publica capacidade líquida, não reformas e adições brutas. É necessário separar vida de projeto, autorização/concessão, calendário político, anúncio do proprietário, paragem real, mothballing, refurbishment e repowering.

### Procura

Devem coexistir dois balanços:

1. eletricidade final direta;
2. carga bruta da rede, incluindo transformação, storage e perdas e descontando behind-the-meter segundo a convenção da fonte.

PNEC/PNIEC, RMSA, ERAA e TYNDP não são previsões concorrentes simples: usam fronteiras e vintages diferentes. H2, data centres, indústria, EV, bombas de calor e autoconsumo precisam de módulos e estados de maturidade próprios.

### Renováveis e projetos

- Potencial físico, técnico, económico e realizável são objetos diferentes.
- Solar tem recurso técnico muito acima das metas; a entrega é limitada por rede, licenciamento, armazenamento, procura e valor capturado.
- Eólica onshore portuguesa aproxima-se mais do limite técnico; o resultado depende muito de setbacks e repowering.
- Offshore ibérico é sobretudo flutuante e não tinha concursos comerciais adjudicados no corte. Metas de 2 GW PT e 3 GW ES não devem ser tratadas como capacidade operacional garantida em 2030.
- Pipeline, acesso, ajuda, autorização, FID, construção e operação são estados distintos.

### Operação, reservas e rede

- A camada histórica de balancing é forte, mas preços/liquidações não são custos físicos.
- O primeiro relatório português FNAM publica máximos de flexibilidade, mas não necessidades não satisfeitas; não se somam automaticamente a contingência e FRR.
- O modelo público de transmissão PT–ES–FR continua sintético: OSM/PyPSA-Eur serve para screening, não como modelo TSO. CGMES é um standard; IGM/CGM reais são restritos.
- Distribuição continua adequada apenas para proxies por subestação/zona sem um snapshot elétrico licenciado.

## Lacunas que permanecem materialmente duras

| Lacuna | Porque não ficou resolvida pela web | Tratamento responsável |
|---|---|---|
| Parâmetros unitários reais | REN/REE recebem-nos, mas valores por grupo são reservados/confidenciais | Priors tecnológicos, distribuições e pedidos sanitizados |
| UC hidráulico fino | Faltam hill charts, tailwater, perdas, limites por grupo e operação detalhada, sobretudo Tâmega | Modelo de planeamento calibrado; sem claim de operador |
| Modelo TSO/estabilidade | Estados AC, proteções, PMU/SCADA e modelos dinâmicos não são open data | Screens sintéticos e eventual acesso institucional/NDA |
| Custos finais privados | Contas públicas não revelam all-in comparável por projeto | Intervalos, SPV/contratos quando disponíveis e claims limitados |
| BTM/storage asset-level | Microdados não são publicados e vários denominadores oficiais divergem | Totais imutáveis por corte + cadastro confidence-scored |
| Ilhas sub-horárias | EDA/EEM detêm os dados, mas a publicação é sobretudo agregada | Estudos separados e pedidos de um ano-piloto |
| Projeto nuclear português | Não existe site, tecnologia, vendor, instituição, financiamento ou pacote de resíduos definido | Superfícies paramétricas e break-even, nunca “estimativa do projeto” |

## Incertezas que são decisões, não falhas de pesquisa

- fronteira PT, PT–ES ou PT–ES com vizinhos endógenos;
- horizonte e anos-alvo;
- EUR reais de que ano e taxa social de desconto;
- electricity-only ou sector coupling;
- definição e alocação do cap elétrico de emissões;
- procura fixa, elástica ou por serviços;
- risk-neutral, CVaR, regret e pesos de narrativas;
- externalidades que entram no headline versus contas satélite;
- tolerâncias de backcast, reconciliação e reprodução.

Não existe uma pesquisa adicional que determine estas opções sem introduzir um juízo normativo. Devem ser decididas no protocolo e testadas por sensibilidades.

## Efeito de ter atingido o limite de agentes

O limite não deixou nenhum dos 23 tópicos principais sem relatório final. Alguns agentes que pretendiam subdividir ainda mais o trabalho tiveram de concluir partes diretamente. O caso explicitamente documentado foi a auditoria de política/projetos: nuclear teve revisor dedicado; storage, H2, interligações e reformas de mercado foram verificados pelo agente principal desse tópico.

O efeito foi, portanto, sobretudo de **redução de redundância e triangulação**, não de perda de uma área inteira. A confiança é alta nos factos assentes em uma fonte primária inequívoca; é menor onde:

- só houve uma leitura especializada sem segundo revisor independente;
- termos de licença são contraditórios ou não normalizados;
- endpoints foram testados pontualmente, mas não em toda a cobertura histórica;
- números dependem de definição, revisão retroativa ou perímetro;
- a conclusão exige inferência entre documentos administrativos dispersos.

Não faria uma segunda vaga ampla. O retorno marginal mais alto está agora em quatro ações dirigidas:

1. testes reprodutíveis dos pipelines e da cobertura real das APIs;
2. pedidos DGEG/REN/ERSE/APA/E-REDES e equivalentes espanhóis;
3. revisão especializada independente apenas do protocolo, contabilidade, adequação e claims nucleares/estabilidade;
4. pilotos computacionais PyPSA–GenX–Antares antes de congelar a arquitetura final.

## Resultado para a execução

A investigação reforça um `GO` condicionado para o estudo independente:

- `GO` para ledger histórico agregado, modelo ibérico zonal, expansão e adequação probabilística;
- `GO condicionado` para hidro por reservatório, rede DC sintética e UC por classes/unidades com priors;
- `NO-GO` para réplica operacional REN/REE, custos privados integrais, distribuição load-flow nacional, estabilidade TSO e estimativa de um projeto nuclear português inexistente.
