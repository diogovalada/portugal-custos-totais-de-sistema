# Plano de execução

> Estado editorial: working
> Última atualização: 2026-08-13
> Âmbito: sequência mínima, checkpoints, critérios de promoção e recursos
> Documento canónico para: execução do estudo
> Não é canónico para: valores dos pressupostos, conteúdo das lacunas ou decisões adotadas

## Princípio

O projeto deve seguir o caminho mais curto até um resultado falsificável. Controlos científicos bloqueiam alegações proporcionais ao seu risco; não bloqueiam protótipos internos concebidos para aprender.

Existem dois modos de trabalho:

- **exploratório:** spikes, fixtures e modelos descartáveis podem avançar com proxies identificadas; não produzem conclusões públicas nem alteram decisões silenciosamente;
- **claim-bearing:** configurações, métricas, inputs e tolerâncias relevantes estão congelados e os resultados podem sustentar alegações dentro da fidelidade validada.

Não criar um novo documento, modelo ou pipeline quando uma configuração, teste ou secção de um artefacto existente resolver o problema. Dados e runs só recebem manifests completos quando forem usados num resultado preservado.

## Três checkpoints

| Checkpoint | Antes de | Evidência mínima |
|---|---|---|
| C1 — contrato científico | tratar comparações como evidência substantiva ou comunicá-las fora da exploração interna | pergunta, fronteiras, contrafactuais, headline, procura, fiabilidade, emissões, horizonte principal e limites de claims congelados |
| C2 — modelo qualificado | promover resultados a headlines candidatos ou conclusões de draft | backcast/holdout aceite, contabilidade coerente, adequação dos finalistas e módulos materiais incorporados ou limitados |
| C3 — release reproduzível | divulgar qualquer headline ou versão citável | reprodução limpa, licenças verificadas, revisão proporcional e ligação de cada headline aos inputs/config/run |

Os checkpoints não são autorizações para investigação interna. Uma falha reduz a alegação ou a fidelidade; não obriga a preencher uma lacuna com falsa precisão.

## Sequência mínima

### P0 — Fatia vertical exploratória

Começa imediatamente, antes de C1, e serve para descobrir problemas reais de dados e formulação.

Configuração inicial:

- Portugal e Espanha como 2–5 zonas; França como fronteira limitada;
- um ano fechado para calibração exploratória e outro para holdout futuro;
- capacidades fixas, procura horária, VRE, térmicas agregadas, hidro/storage agregados e interligações;
- PyPSA + HiGHS, sem investimento, UC detalhado, 15/5 minutos ou modelos alternativos;
- balanço físico e um esqueleto de 8–12 categorias de custo de recursos;
- ambiente mínimo, uma fixture manual por identidade crítica e um manifest gerado automaticamente.

Entregável: pipeline executável ponta a ponta e relatório curto de cobertura/resíduos. Não é necessário concluir o ledger financeiro, externalidades, cadastro unitário ou pedidos administrativos para executar P0.

Se o protótipo não fechar o balanço, reduzir zonas, categorias ou período até localizar o erro. Se nem uma versão nacional/anual for reproduzível, publicar primeiro o diagnóstico de dados.

### P1 — Charter-lite e C1

O charter congela apenas escolhas que podem alterar a interpretação:

1. sistema continental PT+ES, setores e condições de fronteira;
2. custo de recursos PT+ES como objetivo e regra separada para reportar a perspetiva portuguesa;
3. um horizonte/ano-alvo principal; outros anos são extensões ou sensibilidades;
4. procura e denominadores, padrão de fiabilidade e tratamento das emissões;
5. contrafactuais concretos: referência all-tech, no-new-nuclear, extensões espanholas por unidade e nuclear português paramétrico em blocos inteiros;
6. moeda, desconto como distribuição/sensibilidade e categorias do headline;
7. claims permitidos e condições que obrigam a apresentar intervalos ou indiferença.

Não é necessário resolver em C1 externalidades completas, distribuição detalhada, ilhas, Marrocos, modelo secundário, taxa de avaria por grupo ou licença de todas as fontes potenciais. Basta classificá-los como `core`, `satellite` ou `deferred` e identificar qualquer efeito que possa invalidar o primeiro resultado.

C1 é satisfeito quando estas escolhas são registadas no decision log e existe uma configuração-base legível pela máquina. O congelamento aplica-se aos runs interpretáveis posteriores; P0 pode ser refeito livremente.

### P2 — Evidência e ledger em paralelo

P2 deixa de ser um gate obrigatório antes do backcast. O mínimo necessário ao core é:

- pipelines e proveniência dos inputs efetivamente usados;
- reconciliação física do período histórico escolhido;
- esqueleto de custo de recursos com ano monetário, unidade, fonte e regra contra dupla contagem;
- classificação jurídica apenas dos dados que entram no artefacto preservado;
- cobertura e resíduos conhecidos.

O ledger financeiro/distributivo integral, a monetização de externalidades, três anos completos, custos privados por projeto e um cadastro unitário perfeito são workstreams satélite. Podem gerar releases próprias, mas não bloqueiam P3/P4 salvo se o custo omitido for comparável à diferença entre alternativas.

Pedidos administrativos devem ser estreitos e orientados por uma lacuna observada no protótipo. Não pedir um dump amplo apenas porque pode vir a ser útil.

### P3 — Backcast qualificado

Construir o modelo histórico com capacidades fixas:

- começar em 2–5 zonas e aumentar resolução apenas por teste de materialidade;
- usar pelo menos um período de calibração e um holdout que não participa na afinação;
- comparar balanço, produção, mix, armazenamento/hidro, comércio, emissões e restrições observáveis;
- congelar métricas e tolerâncias antes da calibração claim-bearing;
- identificar explicitamente parâmetros genéricos, correspondências inferidas e proxies;
- não exigir reprodução de preços sem bids, uplift e comportamento estratégico.

Se a resolução adicional não alterar materialmente custo, ranking, congestionamento ou viabilidade, conservar a versão mais simples. Se o backcast falhar, o modelo pode continuar como experiência, mas não sustenta P4 claim-bearing.

### P4 — Primeira comparação forward

O primeiro desenho experimental usa:

- um ano-alvo principal e trajetória brownfield suficiente para representar retires, lead times e valor terminal;
- uma referência e 2–3 contrafactuais focais, não a matriz completa de possibilidades;
- três anos meteorológicos/hídricos coerentes no screening inicial;
- investimento contínuo para tecnologias divisíveis e decisões enumeradas/binárias para nuclear e outros ativos lumpy;
- procura, fiabilidade e emissões comuns;
- capacidade firme/ELCC conservadora ou constraint equivalente antes da adequação detalhada;
- sensibilidades unidimensionais ou narrativas coerentes, sem produto cartesiano.

MGA, amostragem global, stochastic expansion, CVaR e minimax regret só entram depois de o primeiro resultado mostrar qual incerteza pode alterar a decisão. GenX só entra se um caso reduzido revelar discrepância estrutural ou se a revisão exigir um challenger de expansão.

Entregável: portefólios candidatos e superfícies condicionais, nunca um “mix verdadeiro”. Nuclear português é reportado como superfície de break-even de custo, prazo e desempenho, não como estimativa pontual de um projeto inexistente.

### P5 — Adequação, materialidade e C2

Todos os portefólios finalistas recebem uma verificação probabilística de adequação proporcional ao claim:

- clima, avarias, manutenção, interligações e limites energéticos de hidro/storage;
- LOLE e EENS separados para Portugal e Espanha;
- common random numbers, convergência e intervalos de confiança;
- expansão do ensemble meteorológico apenas nos portefólios fixos e até precisão suficiente;
- UC/redispatch detalhado numa amostra de períodos críticos quando material.

Capacidade ou custo corretivo necessário para cumprir fiabilidade regressa a P4. O ciclo P4↔P5 termina quando a adequação deixa de alterar materialmente o portefólio ou quando a incerteza obriga a reportar uma fronteira em vez de um ranking.

Distribuição, estabilidade, reservas finas, externalidades, incidência, ilhas e segurança geopolítica começam como screens ou contas satélite. Um módulo sobe ao core apenas se:

1. puder alterar viabilidade, ranking ou diferença de custo;
2. tiver uma representação testável;
3. não duplicar custo ou constraint já incluído;
4. o ganho esperado justificar dados, compute e manutenção adicionais.

C2 é satisfeito quando o backcast/holdout, as identidades contabilísticas e a adequação dos finalistas suportam precisamente os headlines propostos. Efeitos omitidos materialmente comparáveis ao intervalo entre alternativas obrigam a reduzir a alegação.

### P6 — Publicação e C3

Antes de uma release citável:

- uma máquina limpa reproduz os outputs anunciados dentro de tolerâncias pré-fixadas;
- código, documentação e dados/derivados têm licenças compatíveis;
- cada headline liga a commit, configuração, inputs, solver e seeds;
- método, contabilidade, dados e claims recebem revisão apenas pelos perfis relevantes ao que é publicado;
- limitações, desacordos materiais e efeitos não monetizados acompanham os resultados;
- a versão pública é imutável e citável.

Preprint, DOI, período de comentários e response matrix pertencem a P6, não a P0/P1. Uma release intermédia aplica estas regras apenas ao artefacto e aos claims que efetivamente publica.

## Critério de materialidade

Não usar um limiar universal antes de observar a escala do problema. Para cada possível extensão, comparar o maior efeito plausível com:

- a diferença de custo entre portefólios;
- a margem de fiabilidade/emissões;
- a incerteza já reportada;
- o erro do backcast.

Se o efeito for claramente menor, fica como sensibilidade ou limitação. Se for comparável, testar uma representação simples. Só depois promover a versão detalhada. A nota de promoção pode ser uma issue curta com claim afetado, evidência, implementação mínima e critério de saída; não exige um novo artefacto de governação.

## Trabalho paralelo e adiado

Podem avançar em paralelo sem entrar no caminho crítico:

- pedidos administrativos acionados por lacunas verificadas;
- crosswalk unitário, hidro fino, baterias e custos realizados;
- ledger financeiro e externalidades;
- preparação de adequação e fixtures sintéticas.

Ficam adiados até existir evidência de materialidade: 10–30 clusters, UC anual unit-level, 15/5 minutos generalizados, modelo integral da distribuição, estabilidade dinâmica TSO, sector coupling completo, ilhas no modelo continental e intercomparação sistemática com vários modelos.

## Compute e esforço

P0 deve correr num portátil. Cloud só é contratada depois de profiling demonstrar que memória ou throughput bloqueiam um run necessário. Priorizar redução de dimensão, formulação e runs independentes por weather year antes de GPU ou infraestrutura permanente.

O primeiro objetivo de gestão é obter P0 em semanas, não completar P1+P2 como programa documental. Um preprint ibérico claim-bearing continua a ser trabalho de vários meses; módulos profundos e revisão especializada aumentam o calendário apenas quando os respetivos claims forem mantidos.

## Alterações ao plano

Registar no decision log apenas mudanças que alterem pergunta, headline, checkpoint, claim ou resultado reproduzível. Refactors, tarefas, experiências falhadas e estado corrente pertencem ao Git, às issues ou ao `PROJECT_STATUS.md`, não a novos rituais documentais.
