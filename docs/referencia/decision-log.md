# Registo de decisões

> Estado editorial: adopted
> Última atualização: 2026-08-13
> Âmbito: escolhas formais duráveis
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
| D-SCOPE-001 | 2026-08-13 | Adotar `core`, `satellite` e `deferred` como camadas vinculativas de âmbito | Módulos só entram no core por materialidade, representação testável e ausência de dupla contagem |
| D-PLAN-002 | 2026-08-13 | Substituir seis gates sequenciais por três checkpoints de claims e permitir uma fatia vertical exploratória antes do charter | P2 deixa de bloquear P3; protótipos internos podem preceder C1; C1/C2/C3 bloqueiam interpretação, conclusões de draft e divulgação pública, respetivamente |
| D-COST-002 | 2026-08-13 | Clarificar D-COST-001: o headline principal é custo de recursos PT+ES; externalidades são conta satélite e variante social explícita | Evita que cobertura ambiental incompleta bloqueie ou seja somada silenciosamente ao resultado principal |
| D-MOD-002 | 2026-08-13 | Usar investimento discreto para nuclear, feedback P4↔P5 de adequação e validação escalonada | PyPSA/HiGHS + fixtures é o mínimo; GenX e detalhe adicional só por materialidade; capacidade/custo corretivo regressa ao cálculo do portefólio |

`D-PLAN-002` substitui especificamente a sequência rígida e os seis gates preservados por `D-PLAN-001`; as restantes correções factuais e documentais de `D-PLAN-001` mantêm-se.

Questões abertas pertencem a [`assumptions.csv`](registers/assumptions.csv), o estado corrente a [`PROJECT_STATUS.md`](PROJECT_STATUS.md) e proveniência de revisões ao arquivo ou histórico Git — não a este registo.
