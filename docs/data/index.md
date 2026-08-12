# Índice e estado dos dados

> Estado editorial: working  
> Última verificação factual: 2026-08-12  
> Âmbito: navegação, cobertura e encaminhamento das lacunas  
> Documento canónico para: visão transversal das fontes e lacunas  
> Rever quando: uma auditoria temática mudar de conclusão

## Taxonomia de acesso

Cada dado deve ser classificado como:

1. aberto e reutilizável;
2. público, mas fragmentado, autenticado ou sem licença clara;
3. existente numa entidade e potencialmente solicitável;
4. não público ou confidencial;
5. ainda não produzido ou inexistente.

“Não encontrado publicamente” não prova inexistência. Consulta pública não implica autorização para redistribuir no GitHub.

## Matriz das lacunas auditadas

| Lacuna | Estado | Documento |
|---|---|---|
| Registo de unidades e nós | backbone ≥100 MW e várias fontes geográficas; nó físico incompleto | [Ativos](generation-and-storage-assets.md) |
| Rampas, mínimos, heat rates, arranques e avarias | priors abertos; valores portugueses validados não públicos | [Ativos](generation-and-storage-assets.md) |
| Cascatas, afluências, rendimentos e água | operação básica muito pública; curvas/regras finas em falta | [Hidro](hydro.md) |
| Reservas, ativações, redispatch e congestionamento | SIME substancial a 15 min; detalhe físico/segundos em falta | [Operações](system-operations.md) |
| Topologia e custos marginais da distribuição | datasets zonais ricos; grafo/custos nodais fechados | [Rede](grid-and-stability.md) |
| Registo de baterias MW/MWh | reconstruível parcialmente; sem cadastro nacional completo | [Ativos](generation-and-storage-assets.md) |
| Custos realizados | bons em redes reguladas; all-in privado fraco | [Custos](project-costs.md) |
| Estabilidade, tensão e reativa | requisitos/planeamento públicos; operação/dinâmica fechada | [Rede](grid-and-stability.md) |
| Projeto nuclear português | objeto ainda não existe | [Nuclear](../nuclear.md) |
| Operação dos Açores e Madeira | mensal/anual e qualidade; não sub-horário | [Ilhas](islands.md) |
| Inputs espanhóis endógenos | camada agregada forte; auditoria/licenças e detalhe hidro assimétricos | secção “Espanha” abaixo |

O registo machine-readable encontra-se em [`registers/data-gaps.csv`](../../registers/data-gaps.csv).

## Fontes transversais

| Necessidade | Fonte inicial | Nota |
|---|---|---|
| Balanço continental | [REN Data Hub](https://datahub.ren.pt/pt/) | dashboard e séries agregadas; auditar termos |
| Carga/produção distribuída | [E-REDES Open Data](https://e-redes.opendatasoft.com/pages/homepage/) | muitos datasets CC BY 4.0 e 15 min desde anos recentes |
| Produção, carga, unidades, flows e outages | ENTSO-E Transparency Platform | conta/token; licença item a item |
| Mercado diário/intradiário | [OMIE](https://www.omie.es/en/file-access-list) | formatos e janela de arquivo variáveis |
| Estatísticas e licenças | DGEG | páginas e datasets com regimes de reutilização diferentes |
| Regulação e custos | ERSE | PDF/XLS; proveito permitido não é cash cost contemporâneo |
| Hidrologia | APA/SNIRH | séries ricas, interface antiga e licença pouco clara |
| Clima | ERA5/ERA5-Land, PECD, IPMA | ERA5 para base; IPMA sobretudo calibração |
| Demografia/macroeconomia | Eurostat e INE | arquivar pulls porque as séries são revistas |
| Gás e carbono | MIBGAS, DGEG, EEX/ETS/EEA | spot/auction não equivale a delivered fuel cost |
| Emissões | APA/UNFCCC/EEA ETS | lifecycle requer fonte e fronteira adicionais |

## Espanha como camada endógena

O modelo PT–ES não pode tratar Espanha como simples condição externa. O [ESIOS da REE](https://www.esios.ree.es/en/) publica carga, produção, mercados, intercâmbios, unidades estruturais e curtailment renovável nodal; a ENTSO-E acrescenta Transparency Platform, ERAA/PECD e dados europeus harmonizados. PyPSA-Eur fornece um ponto de partida reproduzível para rede, ativos e perfis.

Estas fontes são substitutos aceites para um P3 agregado, mas não tornam a fidelidade simétrica. Em particular, a hidro espanhola será inicialmente representada com armazenamento/produção agregados ENTSO-E, afluências ERAA quando disponíveis e proxies meteorológicas PECD, não com uma reconstrução de cascatas ao nível SNIRH. Os termos de acesso e redistribuição do ESIOS e de cada pacote ENTSO-E têm de ser classificados antes do uso.

`GAP-011` regista esta assimetria. Sem dados adicionais, o estudo pode tirar conclusões ibéricas agregadas e testar política espanhola, mas não alegar validação unitária, nodal ou de cascata com a mesma profundidade do lado português.

## Regras transversais

- REN/ENTSO-E continentais não incluem Açores/Madeira; estatísticas nacionais podem incluí-los.
- Guardar timezone, DST, leap year, net/gross, HHV/LHV, provisional/final e revisões.
- Coordenada da central, região/bus inferido e ponto oficial de ligação são campos distintos.
- Não confundir potência nominal, ligação, injeção, disponibilidade e capacidade observada.
- Para dados visíveis sem autorização de redistribuição, publicar apenas scripts/manifests/derivados permitidos.
- Guardar a licença explícita de cada dataset; não inferir licença de uma página adjacente.

## Prioridade e efeito na execução

A classificação de prioridade, a primeira fase afetada e a consequência de cada lacuna pertencem exclusivamente a [`registers/data-gaps.csv`](../../registers/data-gaps.csv). Este índice resume cobertura e encaminha para a evidência temática sem repetir essas classificações.
