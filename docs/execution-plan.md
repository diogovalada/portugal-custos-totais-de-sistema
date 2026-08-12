# Plano de execução

> Estado editorial: working  
> Última atualização: 2026-08-12  
> Âmbito: sequência, dependências, entregáveis, gates e envelope de recursos  
> Documento canónico para: execução faseada do estudo  
> Não é canónico para: estado corrente, metodologia, pressupostos, decisões ou conteúdo das lacunas  
> Rever quando: mudar o charter, a sequência crítica, um gate ou um entregável

## Regra de propriedade

Este documento responde a cinco perguntas duráveis: em que ordem avançar, o que exige cada fase, o que ela entrega, como se aceita o resultado e quando se deve parar ou reduzir a ambição.

Outros artefactos mantêm responsabilidades distintas:

- [PROJECT_STATUS.md](../PROJECT_STATUS.md): estado volátil, bloqueios presentes e ações imediatas;
- [project-design.md](project-design.md): propósito, âmbito, limites e governação;
- [cost-accounting.md](cost-accounting.md): ontologia e regras contabilísticas;
- [modelling-methodology.md](modelling-methodology.md): formulação, ferramentas, incerteza e validação;
- [`assumptions.csv`](../registers/assumptions.csv): valores, confiança e review triggers;
- [decision-log.md](decision-log.md): decisões adotadas e conclusões substituídas;
- [`data-gaps.csv`](../registers/data-gaps.csv): conteúdo e ação própria de cada lacuna.

O plano referencia IDs desses registos, sem copiar os seus valores. Não contém percentagem concluída, estado de tarefas, calendário ou backlog detalhado. Uma fase termina por evidência e critérios de aceitação, não pela passagem do tempo.

## Sequência e gates

| Fase | Resultado que permite avançar | Gate |
|---|---|---|
| P1 — Protocolo e fundações | contrato científico e infraestrutura mínima reproduzível | G1 — charter adotado |
| P2 — Ledger histórico | MVP público que reconcilia energia, custos e proveniência | G2 — ledger reconciliado |
| P3 — Modelo histórico ibérico | backcast PT–ES com capacidades fixas e holdout | G3 — representação histórica aceite |
| P4 — Expansão e cenários | portefólios comparáveis sob constraints comuns | G4 — resultados robustos e contabilisticamente válidos |
| P5 — Adequação e módulos | risco probabilístico e limites técnicos quantificados | G5 — claims técnicos proporcionais à evidência |
| P6 — Replicação e publicação | release reproduzida, revista e auditável | G6 — autorização de publicação |

O caminho crítico é `P1 → P2 → P3 → P4 → P5 → P6`. Trabalho preparatório pode decorrer em paralelo, mas não elimina os gates.

## P1 — Protocolo e fundações

### Objetivo

Fechar o contrato científico antes de produzir resultados politicamente interpretáveis e garantir que as fases seguintes têm uma base reproduzível.

### Dependências

- resolver ou adotar os pressupostos marcados `needed_by_phase=P1`, incluindo `A-SCOPE-001`, `A-SCOPE-002`, `A-FRANCE-001`, `A-ISLANDS-001`, `A-STACK-001`, `A-DEMAND-BOUNDARY-001`, `A-COUNTERFACTUAL-001`, `A-EMISSIONS-001` e os campos ainda `TBD`;
- preservar `D-COST-001`, `D-MOD-001`, `D-GOV-001` e `D-DATA-001`;
- medir as lacunas antes de fazer pedidos administrativos amplos.

### Entregáveis

- protocolo versionado com pergunta, fronteiras, horizonte, anos-alvo e critérios de alegação;
- ontologia de custos e schema dos três ledgers;
- cenário/configuração-base sem resultados políticos;
- ambiente bloqueado, estrutura de testes e fixture sintética mínima;
- catálogo priorizado de inputs portugueses e espanhóis, licenças, manifests e pedidos administrativos;
- decisão separada sobre licenças de saída para código, documentação e derivados de dados, mais metadados de citação; as escolhas finais entram no decision log;
- plano de pré-registo, revisão e conflitos de interesse.

### G1 — Critérios de aceitação

- todas as escolhas necessárias a P2 foram convertidas em decisões ou permanecem sensibilidades explicitamente delimitadas;
- fronteira geográfica, setores, ano monetário, taxa social, procura e fiabilidade são coerentes entre protocolo, ledger e configuração;
- cada categoria de custo tem owner, unidade, tratamento contabilístico e teste contra dupla contagem;
- a fixture sintética executa aquisição simulada, transformação, ledger e testes numa máquina limpa;
- fontes essenciais de P2 têm licença classificada e alternativa documentada quando não redistribuíveis;
- protocolo e métricas são congelados antes dos cenários politicamente sensíveis.

### Stop/go

Se não for possível fechar uma fronteira coerente ou reproduzir os inputs mínimos, reduzir P2 ao subconjunto publicável e declarar o restante fora de âmbito. Não avançar para um modelo quantitativo que misture fronteiras ou ledgers incompatíveis.

## P2 — Ledger histórico

### Objetivo

Produzir um MVP autónomo para 2–3 anos recentes, conciliando fluxos físicos, custos de recursos e incidência financeira sem depender ainda de expansão ótima.

### Dependências

- G1 satisfeito;
- `GAP-004`, `GAP-006`, `GAP-007`, `GAP-012` e `GAP-015` medidos e tratados segundo o respetivo `effect_on_execution`;
- inventário inicial de unidades e correspondências de `GAP-001` suficiente para explicar a cobertura;
- ano-base monetário e regras de reconciliação adotados.

### Entregáveis

- pipelines de aquisição e transformação com manifests e checksums;
- balanço físico horário ou na melhor resolução licenciada;
- ledger de recursos, ledger financeiro e externalidades observáveis mantidos separados;
- reconciliação com REN, ENTSO-E, OMIE, ERSE, DGEG e outras fontes aplicáveis;
- relatório de cobertura, resíduos, revisões e limitações;
- pacote reproduzível e publicação autónoma do MVP.

### G2 — Critérios de aceitação

- balanços de energia e dinheiro fecham dentro de tolerâncias pré-registadas ou cada resíduo material está identificado;
- cada linha de custo tem fonte, unidade, ano monetário e classificação contabilística;
- transferências não são somadas ao custo de recursos;
- revisões, timezone, DST, gross/net e HHV/LHV são preservados;
- todos os dados versionados podem ser redistribuídos; os restantes têm scripts/manifests e instruções legais;
- licenças de saída e metadados de citação cobrem separadamente código, documentação e derivados distribuídos;
- uma reprodução limpa gera os outputs e testes esperados.

### Stop/go

Se os balanços não reconciliarem, não usar o ledger para calibrar P3. Publicar primeiro o diagnóstico de resíduos ou reduzir a granularidade até que a identidade física e contabilística seja verificável.

## P3 — Modelo histórico ibérico

### Objetivo

Construir e validar, na fronteira adotada em P1, um modelo brownfield com capacidades fixas antes de permitir investimento endógeno. O default de trabalho atual é PT–ES com França limitada, não uma decisão implícita deste plano.

### Dependências

- G2 satisfeito;
- `GAP-001`, `GAP-002`, `GAP-003`, `GAP-004`, `GAP-005`, `GAP-006`, `GAP-013` e `GAP-017` tratados ao nível exigido pela resolução escolhida;
- `GAP-011` auditado e os substitutos espanhóis aceites ou o teto de fidelidade correspondente declarado;
- `A-SPACE-001`, `A-TIME-001`, `A-STACK-001` e `A-DIST-001` adotados ou definidos como variantes estruturais;
- `A-BACKCAST-YEARS` e `A-BACKCAST-TOL-001` congelados antes da calibração; os anos de holdout são excluídos da calibração e da afinação das tolerâncias.

O backcast físico pode usar uma janela maior do que os 2–3 anos do ledger histórico de P2. Apenas os anos de sobreposição com `A-HISTORY-001` recebem reconciliação integral de custos; os restantes suportam validação física e operacional.

### Entregáveis

- inventário versionado e crosswalk de ativos com confiança/proveniência;
- modelo histórico na fronteira adotada, com rede e condições externas documentadas;
- hidro, storage, reservas e indisponibilidades representados à fidelidade suportada;
- relatório de calibração pré/pós-ajuste;
- avaliação de holdout e difference register;
- baseline histórico fixo para comparação dos cenários.

### G3 — Critérios de aceitação

- balanço, produção, mix, flows, reservatórios, emissões e o proxy documentado de restrições/curtailment passam `A-BACKCAST-TOL-001`; enquanto faltar uma série canónica de curtailment, aplica-se apenas o proxy definido em [system-operations.md](data/system-operations.md);
- a calibração não usa o holdout nem altera retrospetivamente os critérios;
- não são exigidos preços reproduzidos sem bids, uplift ou comportamento estratégico;
- correspondências inferidas, parâmetros sintéticos e proxies estão identificados;
- resolução espacial/temporal acrescenta valor demonstrável face a uma baseline simples;
- testes dimensionais, balanços, SOC, água, perdas e solver passam.

### Stop/go

Se parâmetros unitários ou de rede não sustentarem a resolução pretendida, recuar para zonas/subestações e transformar detalhe incerto em distribuições. Não promover uma inferência geográfica a nó oficial nem uma proxy a validação de operador.

## P4 — Expansão e cenários

### Objetivo

Comparar portefólios brownfield nos anos-alvo adotados e respetivos contrafactuais sob a mesma procura, fiabilidade, emissões e contabilidade.

### Dependências

- G3 satisfeito;
- narrativas de [scenarios-iberia.md](scenarios-iberia.md) materializadas em configurações versionadas;
- `A-WEATHER-001`, `A-AGG-001`, `A-AGG-002`, `A-MGA-001` e pressupostos nucleares adotados como distribuições/sensibilidades;
- `A-TECHCOST-001`, `A-FUELCO2-001` e `A-CLIMATE-DATA-001` resolvidos com versões, licenças e transformações documentadas;
- `GAP-009` limita claims a superfícies paramétricas enquanto não existir projeto português.
- `GAP-014`, `GAP-016` e `GAP-018` materializados em narrativas, constraints e ensembles explícitos, sem transformar metas ou potenciais técnicos em previsões.

### Entregáveis

- registry de cenários e matriz de compound stresses;
- runs de expansão/dispatch com manifests completos;
- portefólios, capacidade, produção, rede, storage, comércio e cost stacks;
- análise de sensibilidade, incerteza estrutural e alternativas quase ótimas;
- comparação entre custo de recursos, incidência financeira e externalidades;
- shortlist congelada de portefólios candidatos para P5.

### G4 — Critérios de aceitação

- todos os portefólios satisfazem constraints comuns ou as violações são reportadas;
- nenhum headline depende apenas de um weather year, cenário político ou valor pontual incerto;
- accounting identities e reconciliação com P2 continuam válidas;
- períodos representativos, quando usados, passam `A-AGG-001` e `A-AGG-002` ou são rejeitados;
- near-optimalidade e não-unicidade são reportadas;
- custos, atraso e financiamento correlacionados não são contados duas vezes;
- cada resultado é rastreável a config, inputs, commit, solver e random seeds.

### Stop/go

Não selecionar um “mix verdadeiro”. Se rankings mudarem materialmente com hipóteses plausíveis, o resultado deve ser uma fronteira, intervalo ou decisão condicional. Portefólios que falhem robustez básica não avançam como candidatos principais.

## P5 — Adequação e módulos técnicos

### Objetivo

Testar os portefólios congelados fora da otimização de expansão e quantificar risco de escassez, operação crítica e custos omitidos.

### Dependências

- G4 satisfeito e shortlist imutável;
- `A-RELIABILITY-001`, `A-ADEQUACY-001`, `A-TIME-002`, `A-WEATHER-002` e `A-MODEL2-001` confirmados pelos pilotos aplicáveis;
- `GAP-002` e `GAP-003` tratados probabilisticamente;
- `GAP-005` e `GAP-008` definem o limite entre análise de rede, screening e validação dinâmica;
- `GAP-010` só entra se as ilhas forem formalmente incluídas.

### Entregáveis

- sequential Monte Carlo com LOLE, EENS, quantis e intervalos de confiança;
- UC/economic dispatch em rolling horizon e períodos sub-horários críticos;
- testes de interligações, manutenção, avarias e restrições energéticas;
- módulos de distribuição, estabilidade, externalidades ou outros custos omitidos na fidelidade autorizada;
- ELCC ou métricas equivalentes quando metodologicamente defensáveis;
- relatório de claims permitidos e efeitos ainda não monetizados.

### G5 — Critérios de aceitação

- convergência estatística cumpre `A-ADEQUACY-001` ou a limitação é quantificada;
- common random numbers e bootstrap por história/climate year são usados nas comparações;
- ausência observada de ENS é reportada como upper bound, nunca risco zero;
- adequação, N-1, frequência, tensão e estabilidade dinâmica permanecem conceitos separados;
- resultados a 15/5 minutos não contradizem materialmente o despacho horário sem explicação;
- modelos sintéticos são rotulados como screening e não como validação TSO.

### Stop/go

Se a camada dinâmica não for acessível, excluir claims de segurança transitória em vez de os preencher com confiança falsa. Se um portefólio falhar adequação, regressar a P4 com a falha documentada e uma nova versão do candidato; não ajustar silenciosamente o resultado congelado.

## Regra mínima para releases intermédias

Um artefacto de P2 ou P4 só ativa esta regra quando recebe uma tag de release, DOI ou anúncio externo. Commits e outputs internos de trabalho não são releases.

Antes de qualquer release intermédia:

- o âmbito e as alegações ficam limitados ao gate já alcançado e passam, sem flexibilização, a política de alegações de [project-design.md](project-design.md);
- uma reprodução limpa gera os outputs anunciados dentro de tolerâncias declaradas para esse artefacto;
- método, dados/licenças e alegações recebem revisão proporcional ao que é tornado público;
- a versão é imutável e citável, com commit, configuração, manifests e limitações identificados;
- as licenças de saída de código, documentação e derivados de dados estão decididas e não contradizem os termos dos inputs.

Esta verificação é uma versão limitada de P6, não uma autorização antecipada para claims que dependam de P5 ou G6.

## P6 — Replicação e publicação

### Objetivo

Submeter dados, código, método e alegações a reprodução e revisão independentes antes da conclusão pública.

### Dependências

- G5 satisfeito para os claims incluídos;
- protocolo, decision log, assumptions register, manifests e limitações atualizados;
- `A-REPRO-TOL-001` congelado antes da reprodução independente;
- licenças e permissões verificadas para todos os artefactos distribuídos.

### Entregáveis

- pacote de reprodução numa máquina limpa;
- relatório de revisão técnica, regulatória e contabilística;
- revisão adversarial de claims e matriz agree/disagree/resolution;
- preprint, anexos, dataset permitido e repositório documentado;
- período público de issues e response matrix;
- release imutável, citação e DOI.

### G6 — Critérios de aceitação

- terceiro independente reproduz os headline results dentro de `A-REPRO-TOL-001`;
- findings materiais estão resolvidos ou publicados como desacordo explícito;
- nenhuma fonte restrita, credencial ou dado confidencial é distribuído;
- conclusões respeitam os limites definidos em [project-design.md](project-design.md);
- cada número principal liga a run manifest e cenário;
- versão pública, paper e artefactos não divergem.

### Stop/go

Não publicar uma conclusão principal que falhe reprodução, dependa de dados essenciais inacessíveis sem alternativa ou exceda a fidelidade validada. É aceitável publicar um resultado condicional ou negativo sobre os limites do estudo.

## Dependências e trabalho paralelizável

O conteúdo canónico de cada lacuna permanece em [`data-gaps.csv`](../registers/data-gaps.csv). Os campos `first_needed_by_phase` e `effect_on_execution` permitem distinguir uma ausência que bloqueia um claim de uma que apenas reduz fidelidade.

Em paralelo com o caminho crítico podem avançar:

- catálogo, licenças e pedidos administrativos, desde P1;
- crosswalk de ativos, reconstrução hidro e inventário de baterias, desde P1/P2;
- contratação de revisão e preparação da reprodução, antes de P6;
- desenho dos módulos de adequação e testes sintéticos, sem usar resultados futuros;
- documentação e manifests em todas as fases.

Não devem avançar antes do gate correspondente: calibração histórica antes de G2; investimento endógeno antes de G3; adequação dos candidatos antes de G4; interpretação política antes do protocolo e dos testes aplicáveis.

## Envelope de recursos

Estas são ordens de grandeza de planeamento, não calendário ou compromisso:

| Resultado | Esforço plausível |
|---|---|
| P1 + P2, incluindo ledger histórico | cerca de 8–12 semanas full-time para um MVP estreito |
| P1–P4, preprint elétrico ibérico | cerca de 9–15 meses full-time; prolongar se a intercomparação GenX entrar no caminho crítico |
| P5 com adequação e módulos profundos | esforço adicional material e revisão especializada |
| Extensão totalmente sector-coupled | aproximadamente mais 18–36 meses; fora do núcleo inicial |
| Estudo economy-wide definitivo | não é projeto de uma só pessoa |

Orçamento direto preliminar para P1–P6: EUR 15 mil–60 mil, sobretudo revisão especializada e reprodução. Cloud e arquivo: EUR 1 mil–10 mil. Computação só tende a dominar com alta resolução, UC anual, sector coupling ou grandes ensembles.

Os perfis de revisão e a responsabilidade pelo uso de AI permanecem canónicos na secção de governação de [project-design.md](project-design.md).

## Mudanças ao plano

Uma alteração de fase, gate ou propriedade canónica exige entrada no [decision log](decision-log.md). Alterações de valores permanecem no assumptions register; alterações de estado ficam exclusivamente em `PROJECT_STATUS.md`. O histórico Git preserva versões anteriores, mas apenas esta página define a sequência corrente.
