# Registo de decisões

> Estado editorial: adopted  
> Última atualização: 2026-08-12  
> Âmbito: escolhas formais e conclusões expressamente substituídas  
> Documento canónico para: histórico de decisões

## Decisões adotadas

| ID | Data | Decisão | Consequência |
|---|---|---|---|
| D-COST-001 | 2026-08-10 | Usar custo de recursos/social planner como resultado económico principal | Manter incidência financeira e externalidades em ledgers separados |
| D-MOD-001 | 2026-08-10 | Usar a taxonomia NEA, não os seus valores genéricos como dados portugueses | Calibrar inputs ibéricos e comparar portefólios sob constraints comuns |
| D-GOV-001 | 2026-08-10 | Publicar protocolo antes dos cenários politicamente sensíveis | Evitar afinação retrospetiva de métricas e hipóteses |
| D-DATA-001 | 2026-08-10 | Nunca classificar uma categoria inteira como “inacessível” sem distinguir o tipo de acesso | Usar a taxonomia aberto/público fragmentado/solicitável/reservado/inexistente |
| D-DOCS-001 | 2026-08-11 | Substituir a memória monolítica por documentos canónicos temáticos e registos estruturados | O snapshot antigo passa a arquivo não canónico |
| D-DOCS-002 | 2026-08-12 | Tornar `docs/execution-plan.md` a única fonte canónica da sequência de execução | `project-design.md` conserva o contrato científico e `PROJECT_STATUS.md` apenas o estado volátil |
| D-PLAN-001 | 2026-08-12 | Adotar o conjunto mínimo de 13 correções convergidas na revisão externa Fable Max sem mudar a ordem P1–P6 ou os gates | Acrescentar a lacuna espanhola, pré-registo do backcast, regra de release intermédia, licenças de saída, dependências prospetivas e guardas de claims; `data-gaps.csv` passa a ser o único owner das prioridades e mantém `GAP-004` em `high` |

## Revisão externa do plano

| ID | Data | Revisor e configuração | Base | Resultado |
|---|---|---|---|---|
| REV-PLAN-001 | 2026-08-12 | `claude-fable-5`, esforço `max`, sessão `f0f29849-8ac5-4634-aadf-6eb08ad12330` | commit `1581ea3` e todos os documentos/registos ativos | 13 findings: 1 P1, 4 P2 e 8 P3; 13/13 remédios convergidos sem desacordo e incorporados por D-PLAN-001. A tentativa de re-review pós-edição foi recusada por quota; a regressão local confirmou schemas CSV, IDs, referências cruzadas, documentos canónicos e links locais. |

## Conclusões substituídas

Não voltar a afirmar sem qualificação:

- “a ENTSO-E não tem cadastro de unidades” — existe backbone ≥100 MW, mas não o nó físico e a pequena produção;
- “não existem coordenadas” — PyPSA-Eur/powerplantmatching fornece coordenadas de muitas centrais; não são necessariamente oficiais por grupo nem confirmam o bus físico;
- “reservas e redispatch não são públicos” — o SIME publica uma camada substancial a 15 minutos;
- “não há afluências/turbinamento por barragem” — o SNIRH tem séries extensas para muitas albufeiras;
- “a distribuição é opaca em bloco” — existem dados ricos de subestação/zona, mas não o modelo elétrico integral;
- “não há custos realizados” — existem nas redes reguladas e projetos selecionados;
- “os custos nucleares portugueses estão escondidos” — um projeto definido ainda não existe.

## Questões que ainda não são decisões

Fronteira, ano-base, horizonte, sector coupling, granularidade, procura endógena, taxa social, harmonização/uso do VOLL, weather years, distribuição, ilhas, externalidades e critérios dos pilotos GenX/Antares continuam em aberto. Os defaults correspondentes pertencem a [`registers/assumptions.csv`](../registers/assumptions.csv), não a esta tabela.
