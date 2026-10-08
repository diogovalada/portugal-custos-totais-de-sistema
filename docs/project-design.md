# Desenho, âmbito e governação do projeto

> Estado editorial: working  
> Última verificação: 2026-08-13
> Âmbito: pergunta de investigação, fronteiras, viabilidade, fases e política de alegações  
> Documento canónico para: propósito e contrato científico do estudo  
> Rever quando: a fronteira ou ambição do estudo mudar

## Pergunta central

Quais os custos económicos, requisitos de investimento, riscos de adequação e principais impactos externos de portefólios alternativos capazes de fornecer o mesmo serviço elétrico a Portugal, no contexto físico e institucional ibérico, sob restrições comuns de fiabilidade e emissões?

O objeto comparado é o portefólio completo, não o LCOE isolado de uma tecnologia. O estudo deve representar, conforme a fase, geração, redes, armazenamento, flexibilidade, reservas, comércio, hidrologia, indisponibilidades e procura não servida.

## Objetivos

- produzir um estudo transparente, versionado e reproduzível;
- separar custo de recursos, incidência financeira e externalidades;
- comparar portefólios sob a mesma procura, fiabilidade e limite de emissões;
- tratar explicitamente Espanha, interligações e restrição da ligação ibérica à Europa;
- preservar cronologia e correlação de vento, solar, procura, hidro e secas;
- expor pressupostos, lacunas, intervalos e alternativas quase ótimas;
- permitir auditoria independente dos dados, código e alegações.

## Guardas de âmbito antes de C1

**DECISION D-SCOPE-001 / A-SCOPE-TIERS-001:** cada componente é classificado como `core`, `satellite` ou `deferred`. A comparação com estudos suecos, NEA, RTE e o framework britânico está preservada no [benchmark de âmbito de 2026-08-12](archive/scope-benchmark-2026-08-12.md).

O primeiro resultado científico tem como **core** o bulk system PT–ES: geração, fuel, hidro, armazenamento, flexibilidade, reservas físicas, transmissão/interligações, ligação, perdas, comércio externo aplicável, desmantelamento, procura comum, emissões e adequação sob cronologia e weather uncertainty coerentes. Inclui brownfield/build rates, ledger histórico e reprodução proporcional aos claims.

Ficam em **satellite accounts ou screens** a incidência financeira, externalidades, distribuição zonal/subestação, estabilidade, segurança geopolítica e avaliação institucional/financeira nuclear. Permanecem visíveis e podem condicionar a interpretação, mas não bloqueiam automaticamente o primeiro paper.

Ficam **deferred ou em estudos separados** o load flow nacional da distribuição, validação dinâmica TSO, economy-wide macroeconomics, sector coupling ibérico integral, ilhas dentro da otimização continental e custo determinístico de um projeto nuclear português inexistente.

Um módulo só sobe ao core se puder inverter a viabilidade ou ranking, tiver representação validável e não duplicar uma constraint ou custo. Uma issue curta deve identificar o claim afetado, evidência de materialidade, implementação mínima e critério de saída. Não é necessário criar um novo documento ou ritual de aprovação. Esta regra protege simultaneamente contra underscope e scope creep.

## Fronteira provisória

**ASSUMPTION A-SCOPE-001:** o primeiro paper será electricity-only e focado no bulk system continental PT+ES. França será representada como nó endógeno simplificado ou condição de fronteira limitada; Marrocos será incluído se material. Açores e Madeira serão analisados separadamente.

Esta escolha ainda precisa de adoção formal. Uma fronteira apenas portuguesa exige valorar importações ao custo de oportunidade na fronteira. Uma fronteira ibérica torna pagamentos PT–ES e rendas de congestionamento transferências internas.

## Charter-lite C1 — escolhas ainda não adotadas

O benchmark internacional não justifica alargar mais o core. Antes de resultados interpretáveis, C1 deve congelar apenas:

| Decisão | Recomendação | Reserva |
|---|---|---|
| Fronteira e setores | PT+ES continentais, electricity-only | França limitada; ilhas separadas; Marrocos só se material |
| Perspetiva económica | Objetivo = custo de recursos PT+ES | Reportar separadamente custo/incidência para Portugal; não inferir a parcela portuguesa do total ibérico |
| Horizonte | Um ano-alvo principal com trajetória brownfield e valor terminal | 2030/2040/2050 adicionais só depois do primeiro resultado ou como checkpoints da mesma trajetória |
| Procura | Eletricidade final e carga bruta da rede reconciliadas | Novas cargas por maturidade; H2 flexível sem modelar toda a economia |
| Fiabilidade e emissões | Padrões zonais PT/ES e constraint operacional comum explicitamente construída | VOLL, imports, lifecycle e biomassa em tratamentos identificados |
| Contrafactuais | Referência all-tech, no-new-nuclear, LTO espanhol unitário e FOAK PT paramétrico | Nuclear e outros ativos lumpy em blocos inteiros |
| Moeda e desconto | Um ano monetário e uma taxa social comum no resource ledger | Taxa como distribuição/sensibilidade; WACC fica no ledger financeiro |
| Claims | Benchmark condicional de planeamento, não previsão nem réplica TSO | Intervalos ou fronteira de indiferença quando o ranking não for robusto |

As escolhas ainda abertas só passam a `adopted` quando forem aceites e registadas em [decision-log.md](decision-log.md). Resolução espacial, número de weather years, modelos secundários e módulos satélite são decisões de implementação promovidas por materialidade, não requisitos adicionais de C1.

## O que o estudo pode e não pode alegar

É defensável produzir um benchmark de planeamento/adequação e dizer:

- “dentro da fronteira e hipóteses declaradas, o cenário A apresenta custo de recursos estimado X–Y”;
- “o resultado é ou não robusto às sensibilidades testadas”;
- “o resultado é um benchmark cost-optimal, não uma previsão”;
- “a incidência portuguesa difere do custo ibérico devido a comércio e alocação regulatória”.

Não é defensável, sem evidência adicional:

- anunciar “o verdadeiro custo total” de uma tecnologia;
- atribuir todo o custo de backup ou rede a uma tecnologia sem contrafactual;
- tratar “tecnologia X + armazenamento fornece 100%” como comparação neutra entre tecnologias, porque elimina deliberadamente complementaridades do portefólio;
- inferir faturas diretamente do custo de recursos;
- tratar uma solução do modelo como prova da política ótima;
- alegar segurança dinâmica a partir de expansão linear;
- alegar fiabilidade com um só ano meteorológico;
- chamar integralmente reproduzível a um resultado dependente de inputs essenciais indisponíveis a terceiros.

Distribuição detalhada, estabilidade dinâmica e efeitos não monetizados devem ser descritos como módulos, proxies ou limitações, nunca implicitamente incorporados.

## Viabilidade independente

| Ambição | Avaliação |
|---|---|
| Ledger histórico português | Alta; adequado como MVP autónomo |
| Expansão elétrica ibérica | Média-alta; credível para investigação independente |
| Adequação e módulos de rede mais profundos | Média; requer revisão especializada |
| Sistema ibérico totalmente sector-coupled | Baixa-média; extensão posterior de grande dimensão |
| Custo economy-wide definitivo | Não é projeto de uma só pessoa |

Os envelopes de esforço, compute e orçamento pertencem ao [plano de execução](execution-plan.md), para que não existam estimativas concorrentes.

## Princípio de execução

A investigação começa por uma fatia vertical exploratória, sem alegações públicas, e só depois congela o protocolo para runs interpretáveis. O ledger histórico continua a ter valor autónomo, mas a sua versão integral não bloqueia o backcast nem o protótipo de expansão.

A sequência, os três checkpoints e os critérios de materialidade são canónicos apenas em [execution-plan.md](execution-plan.md).

## Governação

**DECISION D-GOV-001:** publicar um protocolo antes dos cenários politicamente sensíveis.

Controlos mínimos, aplicados quando se tornam relevantes:

- configuração machine-readable e ontologia de custos;
- registo curto de decisões materiais;
- conflitos de interesse, financiamento e declaração de utilização de AI;
- revisão de método/código e especialistas apenas para os claims efetivamente mantidos;
- reprodução numa máquina limpa antes de headlines públicos;
- revisão adversarial, licenças e release citável em P6.

Perfis externos são selecionados pelo conteúdo publicado: operação/adequação para claims de fiabilidade, economia/contabilidade para custos, regulação para incidência e especialistas ambientais apenas quando esses efeitos forem quantificados.

AI pode apoiar ETL, testes, documentação, cenários e revisão de código. A responsabilidade por decisões científicas, interpretação institucional e alegações permanece humana e deve ser identificável.
