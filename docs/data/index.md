# Índice e estado dos dados

> Estado editorial: working  
> Última verificação factual: 2026-08-10  
> Âmbito: navegação, cobertura e prioridades  
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

## Matriz das lacunas originais

| Lacuna | Estado | Prioridade | Documento |
|---|---|---:|---|
| Registo de unidades e nós | backbone ≥100 MW e várias fontes geográficas; nó físico incompleto | alta | [Ativos](generation-and-storage-assets.md) |
| Rampas, mínimos, heat rates, arranques e avarias | priors abertos; valores portugueses validados não públicos | crítica | [Ativos](generation-and-storage-assets.md) |
| Cascatas, afluências, rendimentos e água | operação básica muito pública; curvas/regras finas em falta | crítica | [Hidro](hydro.md) |
| Reservas, ativações, redispatch e congestionamento | SIME substancial a 15 min; detalhe físico/segundos em falta | média-alta | [Operações](system-operations.md) |
| Topologia e custos marginais da distribuição | datasets zonais ricos; grafo/custos nodais fechados | alta | [Rede](grid-and-stability.md) |
| Registo de baterias MW/MWh | reconstruível parcialmente; sem cadastro nacional completo | alta | [Ativos](generation-and-storage-assets.md) |
| Custos realizados | bons em redes reguladas; all-in privado fraco | crítica | [Custos](project-costs.md) |
| Estabilidade, tensão e reativa | requisitos/planeamento públicos; operação/dinâmica fechada | crítica | [Rede](grid-and-stability.md) |
| Projeto nuclear português | objeto ainda não existe | estrutural | [Nuclear](../nuclear.md) |
| Operação dos Açores e Madeira | mensal/anual e qualidade; não sub-horário | crítica se incluído | [Ilhas](islands.md) |

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

## Regras transversais

- REN/ENTSO-E continentais não incluem Açores/Madeira; estatísticas nacionais podem incluí-los.
- Guardar timezone, DST, leap year, net/gross, HHV/LHV, provisional/final e revisões.
- Coordenada da central, região/bus inferido e ponto oficial de ligação são campos distintos.
- Não confundir potência nominal, ligação, injeção, disponibilidade e capacidade observada.
- Para dados visíveis sem autorização de redistribuição, publicar apenas scripts/manifests/derivados permitidos.
- Guardar a licença explícita de cada dataset; não inferir licença de uma página adjacente.

## Prioridades

Críticas: parâmetros térmicos unitários; curvas/restrições hidráulicas e novas centrais Tâmega; outturn privado; modelos dinâmicos; operação insular sub-horária.

Contornáveis: crosswalk unidade–nó; inventário de baterias; custos marginais locais da distribuição; curtailment canónico.

Já adequadas para V0/V1: grande frota, balanço, balancing, hidrologia básica, carga/subestações e custos agregados de redes.

