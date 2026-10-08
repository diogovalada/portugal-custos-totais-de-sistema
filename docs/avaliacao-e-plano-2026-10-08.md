# Avaliação do repositório e proposta de plano

> Data: 2026-10-08
> Natureza: proposta para decisão. Não substitui os documentos existentes enquanto não for aceite.
> Origem: revisão assistida por IA, feita a pedido do coordenador do projeto.

## 1. Resumo

**O núcleo científico do repositório está, no essencial, certo.** Compara portefólios completos sob a mesma procura, fiabilidade e emissões. Separa custos reais de transferências e externalidades. Recusa o "LCOE de sistema" por tecnologia como resultado principal. Trata Portugal no contexto ibérico. E trata o nuclear português como limiar de break-even, não como estimativa de um projeto que não existe.

**Os problemas estão noutras três camadas:**

1. **Falta a estratégia.** O repositório ignora o estudo oficial da DGEG, que já tem caderno de encargos, calendário (até 180 dias de execução e pelo menos 30 dias de debate público) e fragilidades concretas. Um estudo independente desenhado no vácuo arrisca chegar tarde e responder a outra pergunta.
2. **O processo está sobredimensionado.** O repositório tem cerca de 19 000 palavras de planeamento (270 KB com o arquivo), 45 pressupostos, 18 lacunas, 111 fontes, 7 fases, 3 checkpoints e 3 níveis de fidelidade. Não tem nenhuma linha de código nem um único resultado numérico. Boa parte da investigação de dados serve uma réplica operacional da rede que o próprio repositório classifica como inviável: ilhas, topologia AT/MT/BT, PMU/EMT, curvas de rendimento por grupo, crosswalk DGEG→EIC→nó e pedidos LADA.
3. **O estudo está desalinhado com a intenção.** Dois dos quatro pilares da WePlanet, custo para o consumidor e independência energética, foram remetidos para "contas satélite" ou "adiados". E a escrita é ilegível para quem se pretende convencer e envolver.

**Recomendação:** reorganizar o projeto em três frentes, por ordem de alavancagem:

- **A. Influenciar** já o estudo da DGEG, com critérios técnicos concretos (Anexos A e B).
- **B. Construir** um estudo aberto e enxuto. Segue o desenho dos estudos-país da NEA, com quatro adaptações a Portugal, e alinha-se com os horizontes 2035/2050 do estudo oficial.
- **C. Auditar** o estudo oficial durante o debate público, correndo os seus cenários num modelo aberto.

**Sobre a NEA:** não existe uma "metodologia NEA" normativa e codificada. Existe um quadro conceptual e uma prática de estudos por país (Suíça 2022, Suécia 2026). Recomenda-se seguir explicitamente o desenho do estudo sueco como modelo. Dá legitimidade e é simples o suficiente para uma equipa pequena.

## 2. O contexto que muda o problema: o estudo CTS da DGEG

Fontes: [proposta de caderno de encargos, v1, abril de 2026](https://www.dgeg.gov.pt/media/bmhnybiw/estudo-de-cts_custos-totais-do-sistema.pdf), [página da consulta pública](https://www.dgeg.gov.pt/pt/destaques/estudo-sobre-os-custos-totais-do-sistema-cts/) e [Jornal de Negócios, 16-04-2026](https://www.jornaldenegocios.pt/empresas/energia/detalhe/dgeg-vai-estudar-a-evolucao-dos-custos-do-mix-energetico-incluindo-o-nuclear).

- **Origem e consulta:** anunciado pelo Secretário de Estado Jean Barroca em outubro de 2025. A proposta de caderno de encargos esteve em discussão pública até 5 de maio de 2026.
- **Execução:** o caderno é entregue à REN, ao abrigo do art. 106.º, n.º 2, al. m) do DL 15/2022. A adjudicação faz-se por consulta a pelo menos 3 entidades e o estudo dura no máximo 180 dias. Segue-se um debate público de pelo menos 30 dias.
- **Fronteira e horizontes:** fronteira no Sistema Elétrico Nacional, com Espanha a entrar como "pressupostos". Horizontes 2035 e 2050.
- **Opções em estudo:** eólica offshore, potência firme (nuclear e gás), interligações (incluindo Marrocos), armazenamento e flexibilidade.
- **Sete módulos:** diagnóstico, cenários, cálculo dos custos totais, comparação internacional, interligações e armazenamento, impactos tarifários e risco.
- **Método:** a metodologia, os cenários e as métricas são propostos pelo adjudicatário e validados pela DGEG em entregáveis intermédios.

**Estado em 2026-10-08:** não encontrei informação pública sobre a versão final, a adjudicação ou o calendário. É a primeira coisa a apurar.

**O caderno tem méritos.** Inclui o nuclear e as interligações, os custos de rede e de estabilidade, o risco climático e o apagão de 28 de abril, e prevê debate público.

**O caderno não exige, e é precisamente o que a WePlanet tem pedido:**

- modelo, dados e pressupostos publicados ou reproduzíveis por terceiros;
- publicação dos entregáveis intermédios (metodologia, cenários, pressupostos) para comentário antes da modelação;
- modelação explícita de Espanha, em vez de "pressupostos";
- uma norma de fiabilidade comum a todos os cenários (a norma oficial de Portugal continental);
- vários anos meteorológicos e hidrológicos no dimensionamento, e não apenas no módulo de risco;
- um mix obtido por otimização tecnologicamente neutra;
- um tratamento explícito do custo de capital;
- revisão independente.

Há também riscos conceptuais de dupla contagem e de mistura entre custos e transferências (Anexo B).

**Implicação:** a decisão política vai ancorar-se no estudo oficial. A maior alavancagem da WePlanet está em três coisas, por esta ordem:

1. Tornar esse estudo melhor e mais aberto. É barato e tem de ser feito agora.
2. Ser o interlocutor tecnicamente competente quando o estudo sair, o que exige ter um modelo próprio.
3. Oferecer uma alternativa aberta nas perguntas que o estudo oficial tratar mal.

## 3. Avaliação do repositório

### 3.1 O que está certo e deve ser mantido

- **Métrica principal:** o custo de recursos, ou seja, o que o país efetivamente gasta. Transferências e externalidades ficam à parte. A lista de duplas contagens em [`cost-accounting.md`](cost-accounting.md) é boa e serve diretamente para criticar o caderno da DGEG.
- **Comparação de portefólios completos** sob a mesma procura, fiabilidade e emissões, em vez de LCOE ou de "custos de integração" atribuídos a uma tecnologia.
- **Fronteira:** contexto ibérico, França como fronteira limitada, ilhas fora.
- **Nuclear:** entra em blocos inteiros, distingue a extensão espanhola do nuclear novo português, e o resultado é um limiar de break-even.
- **Clima e fiabilidade:** anos meteorológicos coerentes, incluindo seca, e a norma de fiabilidade oficial por zona.
- **Credibilidade:** o protocolo é publicado antes dos resultados (D-GOV-001) e há uma lista clara do que o estudo pode e não pode afirmar.
- **Inventário de fontes:** tem valor como referência (REN Dados Técnicos, SNIRH, SIME, VOLL da ERSE, PECD, entre outras).

### 3.2 Problemas, por ordem de importância

1. **Não há estratégia nem teoria da mudança.** Não se diz para quem é o estudo, que decisão quer influenciar, nem quando tem de estar pronto. O estudo da DGEG nunca é mencionado.
2. **Há uma desproporção entre planear e fazer.** O plano diz que a primeira fatia deve levar semanas, mas o repositório continuou a crescer em documentação. O formato (IDs, registos, checkpoints, níveis de fidelidade, camadas core/satellite/deferred) é próprio de uma organização grande, não de uma ou duas pessoas. A burocracia não aumenta a credibilidade; resultados verificáveis aumentam.
3. **O rigor está no sítio errado.** Fixam-se tolerâncias para erros de agregação temporal e para intervalos de confiança de Monte Carlo antes de existir modelo, e prevê-se um backcast com holdout e calibração pré-registada. Entretanto, os pressupostos que de facto decidem o resultado têm tratamento leve ou ficam fora do modelo principal:
   - **custo de capital:** o repositório remete o WACC para a "conta financeira". Para nuclear contra renováveis é provavelmente o parâmetro mais decisivo, e o primeiro que os críticos vão atacar;
   - custo e prazo do nuclear novo, e custo do armazenamento;
   - nível da procura em 2035 e 2050 (eletrificação, hidrogénio, centros de dados);
   - o que Espanha constrói e quando fecha o nuclear;
   - anos secos.
4. **Os pilares da WePlanet estão desalinhados.** "Custo ao consumidor" e "independência" estão em contas satélite ou adiados. No entanto, são baratos de calcular a partir dos resultados do modelo (secção 6.4). Sem eles, o estudo não responde às perguntas que a WePlanet coloca publicamente.
5. **O plano reinventa o modelo.** Prevê um modelo PyPSA à medida e trata o PyPSA-Eur como opcional. Deveria ser o inverso. O PyPSA-Eur já faz a conversão clima→produção (ERA5), a rede (OSM), o parque existente, os custos tecnológicos e a agregação espacial. Existe até um fork espanhol publicado ([PyPSA-Spain](https://pypsa-spain.readthedocs.io/), Gallego-Castillo e Victoria, 2025). Usar a ferramenta-padrão europeia acelera o trabalho e protege a credibilidade: "usámos o modelo aberto que muitos grupos académicos usam" pesa mais do que "usámos o modelo da WePlanet".
6. **A escrita é ilegível para o público-alvo.** Mistura português e inglês técnico, siglas e IDs. Um processo aberto e participativo exige documentos que um engenheiro do setor, um jornalista ou um técnico do ministério consigam ler em 15 minutos.
7. **A estabilidade ficou totalmente de fora.** Uma validação dinâmica é de facto inviável com dados abertos. Mas há uma aproximação simples e corrente: exigir uma inércia ou potência de curto-circuito mínima e custear compensadores síncronos ou baterias grid-forming. É uma omissão relevante, por duas razões: houve o apagão de 28 de abril de 2025, e o caderno da DGEG pede explicitamente estes custos.
8. **Há factos a envelhecer.** Por exemplo, sobre Almaraz o repositório (corte de 2026-08-12) diz que faltava a ordem ministerial. Ora, a Ordem TED/864/2026, de 12 de agosto, já prolongou as duas unidades até 8-6-2030 ([World Nuclear News](https://world-nuclear-news.org/articles/government-approves-extended-operation-of-almaraz-plant)). Quanto mais documentação houver, maior o custo de a manter correta. Não verifiquei os factos do repositório de forma sistemática.
9. **A fronteira económica está por resolver.** A proposta atual otimiza PT+ES em conjunto, o que põe o modelo a decidir também o que Espanha constrói. E deixa sem resposta a pergunta "quanto custa a Portugal". A secção 6.2 propõe uma alternativa.

### 3.3 Veredicto por camada

| Camada | Estado | Veredicto |
|---|---|---|
| Conceitos económicos | Corretos | Manter |
| Desenho do modelo | Correto, algo ambicioso na adequação e na validação | Simplificar para a v0.1; acrescentar apenas o que mudar resultados |
| Dados | Investigação extensa, muito além do necessário | Usar como referência; não continuar |
| Processo e governação | Sobredimensionado | Substituir por um protocolo curto e um roteiro de versões |
| Estratégia, público e calendário | Ausentes | Criar (este documento) |
| Comunicação | Ilegível para não especialistas | Reescrever |

## 4. A metodologia da NEA: seguir, adaptar ou ignorar?

A NEA oferece três coisas diferentes.

**1. Um quadro conceptual.** O custo total junta o custo da central (LCOE) aos custos de sistema: perfil, balanceamento, rede e ligação. O custo total do sistema é o custo económico de satisfazer a procura em todas as horas. As externalidades ficam à parte ([NEA 2018](https://www.oecd.org/en/publications/the-full-costs-of-electricity-provision_9789264303119-en.html)).

**2. Um estudo genérico de 2019** ([The Costs of Decarbonisation](https://www.oecd.org/en/publications/the-costs-of-decarbonisation_9789264312180-en.html)). Impõe quotas de renováveis a um país estilizado, sem hidro nem interligações. É o mais citado no debate pró-nuclear e também o mais criticado. Não deve servir de modelo: um estudo construído assim seria descartado como enviesado.

**3. Uma prática de estudos por país**, feitos a pedido e em cooperação com governos: Suíça (2022), [Suécia (2026)](https://www.oecd-nea.org/upload/docs/application/pdf/2026-03/system_cost_study_of_sweden.pdf) e Coreia (em curso). O estudo sueco tem este desenho:

- **Modelo:** otimização de custo mínimo do investimento e do despacho horário, com o modelo POSY2, para um ano-alvo (2050) e 17 nós elétricos.
- **Casos:** um caso base e 20 sensibilidades, testadas uma de cada vez e agrupadas em sete conjuntos: custos, nuclear (incluindo risco de construção), renováveis (anos bons e maus), procura alta e baixa, comércio e interligações, flexibilidade, e emissões residuais.
- **Custo de capital:** 5% real para todas as tecnologias; 8% para o nuclear novo na sensibilidade de risco de construção.
- **Simplificações:**
  - um único ano meteorológico no caso base;
  - hidro agregada, sem armazenamento plurianual;
  - rede de distribuição não modelada;
  - reforços de transporte e custos de balanceamento calculados à parte.
- **Validação e cooperação:** o modelo foi validado contra 2023, e a procura e os cenários foram definidos com a Agência Sueca de Energia.

**Recomendação: adotar explicitamente o desenho do estudo sueco da NEA como modelo.** É o mais próximo de um padrão reconhecido, foi feito por um organismo intergovernamental da OCDE e é simples o suficiente para uma equipa pequena. Com quatro adaptações, cada uma justificada pelas características de Portugal:

| Adaptação | Porquê |
|---|---|
| Espanha modelada hora a hora, com as capacidades dos planos espanhóis e variantes | Portugal é um sistema pequeno, muito acoplado a Espanha. Tratar Espanha como uma série de preços falha precisamente nos períodos críticos. |
| Vários anos meteorológicos e hídricos, incluindo anos secos, no cálculo principal | A produção hídrica portuguesa varia muito de ano para ano. A própria NEA aponta o ano único como a principal fraqueza de estudos comparáveis. |
| Verificação da adequação dos portefólios finais contra a norma oficial de fiabilidade | Garante que todos os cenários oferecem a mesma segurança de abastecimento, condição para uma comparação justa. |
| Tudo aberto: modelo, dados, configurações e resultados | É o critério que a WePlanet pede ao Governo. A NEA não publica o POSY2 com os dados. |

**Duas regras adicionais:**

1. **Não apresentar "custos de sistema por tecnologia" como resultado principal.** Dependem do contrafactual e são contestados. O resultado principal deve ser a diferença de custo total entre portefólios e o limiar de custo a partir do qual uma tecnologia entra no mix.
2. **Usar um custo de capital único no caso base,** como a NEA. O custo diferenciado por risco tecnológico é uma sensibilidade obrigatória. O resultado nuclear apresenta-se como uma superfície de break-even: custo de investimento × custo de capital.

## 5. Estratégia proposta

### 5.1 Três frentes

| Frente | O quê | Quando | Esforço |
|---|---|---|---|
| A. Influenciar | Nota técnica com critérios de qualidade e riscos do caderno da DGEG; pedir o estado e o calendário do estudo e a publicação dos entregáveis intermédios | Já | Baixo |
| B. Construir | Estudo aberto enxuto (modelo NEA + 4 adaptações), alinhado com 2035 e 2050 | 2–4 meses até à v0.1 | Médio |
| C. Auditar | Quando a DGEG publicar cenários ou resultados, corrê-los no modelo aberto e publicar uma revisão dentro do debate público | Janela de pelo menos 30 dias | Baixo, se a frente B estiver pronta |

- A frente A tem a melhor relação entre impacto e esforço.
- A frente B é o que dá credibilidade às frentes A e C.
- A frente C é onde a WePlanet pode ter mais impacto público.

Uma opção a ponderar: sugerir ao Ministério que convide a NEA, de que Portugal é membro, ou outro organismo independente para rever o estudo oficial.

### 5.2 Credibilidade de um estudo feito por uma organização pró-nuclear

É o maior risco do projeto e deve ser enfrentado de frente:

- **Protocolo antes dos resultados:** publicar perguntas, cenários, métricas, pressupostos e fontes antes de haver resultados.
- **Convidar quem discorda:** associações ambientalistas e de renováveis, academia e operadores devem ser convidados a propor cenários e pressupostos, com resposta pública a cada contributo.
- **Pressupostos de terceiros:** usar fontes como os planos oficiais, a ENTSO-E, a Comissão Europeia e a NEA/IEA, e não valores escolhidos à medida.
- **Otimização tecnologicamente neutra:** o nuclear tem de ganhar o seu lugar no mix.
- **Publicar sempre os resultados, quaisquer que sejam.** É provável que, nalguns cenários, o nuclear novo em Portugal não entre no mix de custo mínimo. Um resultado como "o nuclear entra se o custo de investimento for inferior a X €/kW, com custo de capital Y%" é robusto, útil e defensável qualquer que seja X.
- **Declarar a origem:** a WePlanet como iniciadora, o financiamento e o uso de IA. Considerar um pequeno grupo consultivo com pessoas de fora.

### 5.3 Fora do âmbito

A descentralização económica do país é uma pergunta diferente. Incluí-la diluiria o estudo e a sua credibilidade. Se for relevante, entra apenas como cenário de localização da procura, nunca como objetivo do estudo.

## 6. Desenho do estudo aberto (v0.1)

### 6.1 Perguntas

1. Qual o custo total do sistema, e o custo médio por MWh, em 2035 e 2050? Compara-se a trajetória do PNEC com o portefólio de custo mínimo que tem as mesmas emissões e a mesma fiabilidade.
2. A partir de que custo de investimento, prazo e custo de capital é que o nuclear novo entra no mix português de 2050? E quanto poupa ou custa?
3. Quanto vale para Portugal a extensão do nuclear espanhol para lá do calendário de encerramento (2030–2035)?
4. Que potência firme é necessária para cumprir a norma de fiabilidade num ano seco com pouca importação? Pode vir de armazenamento, bombagem, gás, interligações ou nuclear.

### 6.2 Fronteira e perspetiva

- **Desenho principal:**
  - Portugal continental é otimizado (investimento e despacho);
  - Espanha tem capacidades fixas segundo o PNIEC/TYNDP, com variantes, e despacho horário endógeno;
  - França, e Marrocos se for material, entram como fronteira simplificada.

  É o desenho dos estudos da NEA (Suécia) e da RTE (França): o país decide o seu mix e os vizinhos seguem os seus planos.
- **Custo para Portugal:** investimento e operação em Portugal, mais importações, menos exportações, ambas valorizadas ao preço marginal do modelo. É diretamente comparável com o estudo nacional da DGEG.
- **Sensibilidade:** otimização conjunta PT+ES.
- **Setores:** só eletricidade. A procura é tratada por cenários, com o hidrogénio e os centros de dados como cargas.

### 6.3 Cenários

**Horizontes:** 2035 e 2050, alinhados com a DGEG. Em 2035 o nuclear novo em Portugal é irrealista, porque um programa de raiz leva 10 a 15 anos. O nuclear que conta em 2035 é a extensão espanhola.

**Casos:**

1. Referência: trajetória oficial (PNEC).
2. Custo mínimo, com otimização tecnologicamente neutra.
3. Custo mínimo sem nuclear novo.
4. Nuclear imposto em blocos (por exemplo, 1 a 2 unidades de cerca de 1 GW), para medir quanto custa ou poupa.

**Sensibilidades** (cerca de 15 a 20, uma de cada vez, como a NEA):

- custo de capital: uniforme a 3, 5 e 7%; diferenciado para o nuclear a 8–10%;
- custo e prazo do nuclear novo (intervalos NEA/IEA, harmonizados para euros de um ano-base);
- custo das baterias e da eólica offshore;
- procura alta e baixa;
- ano seco, médio e húmido;
- Espanha com e sem extensão nuclear;
- interligação com França atrasada;
- preços do gás e do CO2.

### 6.4 Métricas por pilar

| Pilar | Métricas |
|---|---|
| Custo | Custo total anual (M€); €/MWh entregue; decomposição por geração, armazenamento, redes e serviços de sistema; diferença face à referência |
| Segurança | LOLE/EENS face à norma oficial; margem firme sem importações; horas de dependência de importação em escassez; indicador de inércia e força da rede |
| Independência | Importações líquidas (TWh); gás importado; dependência de combustível de importação contínua (gás) contra combustível armazenável durante anos (urânio) |
| Limpeza | Emissões diretas; emissões de ciclo de vida (indicador); ocupação de solo (km²) |

O custo total do sistema por MWh entregue é a melhor aproximação de longo prazo ao custo para o consumidor, porque todos os custos acabam pagos por consumidores ou contribuintes. Por isso, a v0.1 não precisa de um modelo tarifário. A repartição por tipo de consumidor é uma pergunta distributiva, que fica para depois.

### 6.5 Modelo e dados

- **Modelo:** PyPSA-Eur recortado para a Península Ibérica, com França como fronteira; 4 a 10 nós, resolução horária, solver HiGHS. Aproveitar o PyPSA-Spain onde for útil.
- **Custos:** `technology-data` do PyPSA, com ajustes documentados; nuclear segundo NEA/IEA.
- **Correções portuguesas onde importam:** capacidades instaladas (REN Dados Técnicos, DGEG), produção hídrica calibrada pelo índice de produtibilidade hidroelétrica da REN e procura da REN. A investigação já feita no repositório serve aqui.
- **Estabilidade:** restrição simples de inércia mínima, satisfeita por compensadores síncronos ou baterias grid-forming com custo.
- **Redes:** o modelo inclui as interligações e o transporte entre nós. A distribuição e as ligações entram como custos unitários documentados.
- **Validação leve:** correr 2024 ou 2025 com as capacidades reais e comparar a produção por tecnologia, as importações e as emissões. Sem holdout nem calibração formal.

### 6.6 Deliberadamente fora da v0.1

- ilhas;
- topologia da distribuição;
- estabilidade dinâmica;
- unit commitment por grupo;
- pedidos LADA de dados técnicos;
- contabilidade financeira e tarifária;
- externalidades monetizadas;
- trajetória multiperíodo;
- adequação por Monte Carlo completo: só na v1.0, e só se a verificação simples mostrar risco.

## 7. Plano de trabalho

| # | Entregável | Duração indicativa | Concluído quando |
|---|---|---|---|
| E0 | Apurar o estado do estudo da DGEG: versão final do caderno, adjudicação, adjudicatário, datas e publicação dos entregáveis intermédios. Por pedido direto e, se necessário, ao abrigo da LADA (prazo de 10 dias úteis). | 1–2 semanas | Calendário conhecido |
| E1 | Nota técnica "Critérios de qualidade para o Estudo CTS", com base nos Anexos A e B, enviada ao Ministério, à DGEG e à REN, e publicada | 2–3 semanas | Enviada e publicada |
| E2 | Protocolo público (até 10 páginas, linguagem clara): perguntas, fronteira, cenários, métricas e tabela de pressupostos com fontes. Período de comentários de 3–4 semanas, com convites dirigidos. | 3–5 semanas, em paralelo com E3 | Publicado, com comentários respondidos |
| E3 | Modelo v0.1: PyPSA-Eur ibérico a correr, validação com 2024/25, caso base e 3–4 casos para 2035 e 2050 | 6–10 semanas | Resultados reproduzíveis com um único comando |
| E4 | Resultados preliminares públicos: sensibilidades, break-even nuclear e anos secos | 4–6 semanas, depois de E3 | Relatório curto, mais notebook e dados |
| E5 | Revisão por 1–2 modeladores externos | Contínuo | Comentários respondidos |
| E6 | Kit de comparação: correr os cenários e pressupostos da DGEG logo que sejam publicados, e publicar uma revisão durante o debate público | Quando a DGEG publicar | Revisão publicada dentro do prazo |
| E7 | v1.0: adequação probabilística, mais anos meteorológicos, revisão por pares e DOI | Depois de E4 e E6 | Versão citável publicada |

**Dependências:**

- E0 determina a urgência de E1 e de E6.
- E3 não depende de E2: o protocolo tem de estar fechado antes de publicar resultados (E4), não antes de construir o modelo.

## 8. O que fazer ao repositório

Proposta, ainda não executada e dependente de decisão:

- **Arquivar** os documentos atuais em `docs/referencia/` como notas de investigação, e deixar de os manter como plano vivo.
- **Substituir** por:
  - um `README.md` claro, em português;
  - `PROTOCOLO.md`;
  - `ROTEIRO.md`, uma versão curta deste plano;
  - um `pressupostos.csv` que o modelo leia diretamente;
  - `CONTRIBUIR.md`.
- **Simplificar o vocabulário:** abandonar C1/C2/C3, P0–P6, V0–V2, core/satellite/deferred e os IDs nos textos públicos. Usar versões (v0.1 preliminar, v1.0 final) e uma secção "o que este estudo pode e não pode afirmar".
- **Abrir à participação:** ativar o GitHub Discussions e criar um modelo de issue "contestar um pressuposto".
- **Escolher licenças antes de publicar resultados:** por exemplo, MIT para o código e CC BY 4.0 para o texto e os resultados.

## 9. Riscos

| Risco | Mitigação |
|---|---|
| Acusação de enviesamento | Secção 5.2 |
| Chegar depois do estudo oficial | E1 e E6 não dependem do estudo completo; os horizontes estão alinhados |
| Capacidade limitada (uma pessoa) | Ferramenta-padrão, âmbito curto na v0.1, procurar 1–2 parceiros |
| Erros introduzidos por IA (factos, números) | Cada número usado no modelo tem uma fonte verificada por uma pessoa; documentos curtos |
| Dados portugueses em falta | Quase tudo o que a v0.1 precisa é aberto; pedir apenas o que um resultado mostre ser decisivo |

## 10. Decisões necessárias

1. Aceitar a reorientação em três frentes: influenciar, construir de forma enxuta e auditar?
2. Quem trabalha no projeto e com que disponibilidade? Há modeladores na WePlanet, ou um parceiro académico?
3. Conhece-se o estado do estudo da DGEG (adjudicatário, datas)?
4. Identidade: estudo "da WePlanet", ou projeto aberto iniciado pela WePlanet com um grupo consultivo?
5. Reestruturar o repositório conforme a secção 8?
6. Sugerir ao Ministério uma revisão independente do estudo oficial (NEA ou outro organismo)?

---

## Anexo A — Critérios de qualidade propostos para o Estudo CTS (rascunho)

Estes critérios complementam os dois critérios de processo já enviados ao Ministério: transparência e reprodutibilidade, e processo aberto e participativo.

1. **Otimização tecnologicamente neutra.** O mix de cada horizonte resulta de uma otimização de custo mínimo em que todas as tecnologias competem, incluindo nuclear, eólica offshore, armazenamento, gás e interligações. Os cenários "com" e "sem" uma tecnologia são contrafactuais explícitos, não quotas impostas.
2. **Contexto ibérico explícito.** Espanha é modelada com despacho horário e capacidades segundo o PNIEC/TYNDP. Inclui variantes para o calendário nuclear espanhol (encerramento até 2035 contra extensão) e para as interligações com França.
3. **Variabilidade climática e hídrica no dimensionamento.** O cálculo usa vários anos meteorológicos reais e coerentes, incluindo pelo menos um ano seco, e não apenas um ano médio.
4. **A mesma fiabilidade para todos.** Todos os cenários cumprem a norma de fiabilidade oficial de Portugal continental, verificada por simulação probabilística. O valor da energia não fornecida é o oficial da ERSE.
5. **Contabilidade sem dupla contagem.** Os custos de recursos são separados das transferências: pagamentos por capacidade, tarifas, CIEG e receitas de leilões ETS. O emprego e a balança comercial aparecem como indicadores à parte, não somados aos custos.
6. **Custo de capital explícito e testado.** Uma taxa de referência declarada, com sensibilidade de custo de capital diferenciado por risco tecnológico. Os resultados incluem limiares, por exemplo o custo de investimento a partir do qual o nuclear entra no mix.
7. **Transparência técnica.** Modelo, dados de entrada, pressupostos e resultados horários publicados sob licença aberta, com preferência por ferramentas open source. A metodologia, os cenários e os pressupostos são publicados para comentário antes da modelação.
8. **Revisão independente.** Revisão por uma entidade externa (por exemplo a NEA, o JRC ou a academia) antes da versão final.

## Anexo B — Observações ao caderno de encargos (v1, abril de 2026)

| # | Ponto do caderno | Risco | Sugestão |
|---|---|---|---|
| 1 | Fronteira no SEN; Espanha como "pressupostos" | Subestimar a interdependência PT–ES nos períodos críticos | Despacho horário explícito de Espanha, com capacidades segundo os planos e variantes |
| 2 | Metodologia, cenários e métricas propostos pelo adjudicatário e validados pela DGEG | Escolhas determinantes feitas sem escrutínio | Publicar os entregáveis intermédios para comentário, coerente com o §5.1 do próprio caderno |
| 3 | Sem requisito de abertura | Estudo não reproduzível e contestável | Publicar os pressupostos completos e os resultados horários; ferramentas abertas sempre que possível |
| 4 | "Pagamentos por capacidade" listados como custo, ao lado de CAPEX e O&M (geração e flexibilidade) | Dupla contagem: são transferências que remuneram esse mesmo investimento | Contar o investimento e a operação; tratar os pagamentos na análise tarifária |
| 5 | Reservas: custos de reserva primária, secundária e terciária | Somar o custo físico e os pagamentos de mercado | Contar o custo físico; os pagamentos são transferências |
| 6 | "Custo de carbono associado a cada tecnologia" via ETS | Com uma restrição de emissões, o preço do CO2 é um resultado; as receitas ETS revertem em grande parte para o Estado; somar ETS e custo social duplica | Declarar uma única abordagem: limite de emissões, preço ETS ou custo social |
| 7 | Emprego e balança comercial entre os "custos" | O emprego é um input já pago no CAPEX e O&M; somá-lo como benefício duplica | Indicadores à parte, não somados |
| 8 | "Custo marginal de longo prazo em função da penetração de renováveis variáveis" | Se interpretado como quotas impostas (NEA 2019), enviesa o resultado | Mix por otimização; quotas apenas como contrafactuais declarados |
| 9 | Métricas de segurança "propostas pelo adjudicatário" | Cenários com fiabilidades diferentes não são comparáveis | Norma oficial (LOLE) e VOLL da ERSE, iguais para todos os cenários |
| 10 | Anos secos apenas no módulo de risco | Dimensionamento feito para um ano médio | Vários anos, incluindo secos, no próprio dimensionamento |
| 11 | "CAPEX (e custo de capital associado)" sem especificar | O pressuposto mais decisivo fica implícito | Taxa de referência declarada e sensibilidade por tecnologia |
| 12 | Nuclear considerado em 2035 | O nuclear novo em Portugal antes de cerca de 2040 é irrealista | Em 2035, testar a extensão do nuclear espanhol; o nuclear novo português apenas em 2050 |
| 13 | Sete módulos em 180 dias, incluindo comparação internacional e tarifas | Superficialidade nos módulos centrais | Priorizar os módulos 2, 3, 5 e 7 |
| 14 | Sem revisão independente | Contestação pública sem árbitro técnico | Revisão por uma entidade externa antes da versão final |
