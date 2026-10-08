# Custos Totais do Sistema Elétrico em Portugal, 2030–2050

**Protocolo do estudo: versão de desenho para aprovação (8 de outubro de 2026)**

> **Autoria e transparência.** Estudo de [nome do autor], publicado em nome próprio. O autor é membro da WePlanet, associação ambientalista que defende, entre outras tecnologias, a energia nuclear.
>
> O trabalho técnico (recolha de dados, código, corridas do modelo e redação) é executado por agentes de inteligência artificial, sob supervisão de um agente coordenador. O autor tem a decisão final.
>
> O autor compromete-se a publicar todos os resultados, sejam quais forem, e a responder publicamente a todos os comentários. Modelo, dados, pressupostos e resultados são abertos, e qualquer pessoa pode reproduzir cada número com um único comando.

Estado: proposta para aprovação. Depois de aprovada, será registada publicamente, com data e identificador permanente (DOI), antes de existir qualquer resultado.

O texto da caixa de autoria acima também é uma proposta: o texto final é decisão do autor (ver [ROTEIRO.md](ROTEIRO.md)).

---

## 1. Em resumo

- **O quê.** Um estudo independente, aberto e totalmente reproduzível do custo total do sistema elétrico de Portugal continental.
  - Os horizontes principais são 2035 e 2050, os mesmos do estudo oficial que a DGEG encomenda através da REN.
  - Acrescentamos 2030, como ponto de partida, e 2040, o ano em que várias decisões se cruzam.
- **A pergunta central.** Quanto custa a trajetória oficial? Quanto custariam alternativas que dão ao país a mesma segurança de abastecimento e as mesmas emissões? E quanto vale cada opção em discussão: eólica offshore, nuclear, gás, interligações (incluindo Marrocos), baterias, bombagem e flexibilidade da procura?
- **Como.** Com um modelo de otimização do investimento e da operação do sistema elétrico, construído com ferramentas abertas (PyPSA e o solver HiGHS).
  - Portugal escolhe o seu parque ao menor custo.
  - Espanha e França seguem os seus planos oficiais, mas operam hora a hora em conjunto com Portugal.
  - O dimensionamento considera vários anos meteorológicos em simultâneo.
  - Cada solução é depois testada em 44 anos reais de vento, sol, temperatura e água, incluindo as piores secas.
- **O que sai.**
  - Diferenças de custo entre portefólios completos.
  - Limiares a partir dos quais uma opção compensa.
  - Intervalos de soluções quase equivalentes em custo.
  - Indicadores para quatro pilares: custo para o consumidor final, segurança de abastecimento, independência energética e energia limpa.
  - O estudo não apresenta um «mix ideal» único.
- **Pontes com o estudo oficial.**
  - As mesmas métricas: custo total em € e em €/MWh fornecido, decomposto em geração, redes, armazenamento, serviços de sistema e outros.
  - Os mesmos horizontes.
  - Um kit para correr os cenários da DGEG no modelo aberto, logo que sejam publicados.
- **Quando.** Protocolo público a 21 de outubro; versão preliminar a 20 de novembro; versão 1.0 a 11 de dezembro de 2026.

---

## 2. As perguntas do estudo

Cada resultado principal responde a uma decisão concreta e é sempre de um destes quatro tipos:

- uma **diferença de custo** entre portefólios completos com a mesma segurança e as mesmas emissões;
- um **limiar**: «a opção X compensa se custar menos de Y»;
- uma **ação robusta**, que compensa em todos os futuros testados;
- um **intervalo** de soluções com custo quase igual.

| # | Pergunta | Decisão que informa | Quem decide, e quando |
|---|---|---|---|
| 1 | Qual o custo total do sistema (M€/ano e €/MWh fornecido, com a decomposição pedida pela DGEG) em 2035, 2040 e 2050? Compara-se a trajetória oficial com o portefólio de custo mínimo que tem a mesma segurança (norma de 1,46 h/ano) e as mesmas emissões. Quanto da diferença chega ao consumidor? | Avaliação do estudo CTS oficial; revisões do PNEC e da monitorização da segurança de abastecimento | Governo e DGEG; debate público do estudo CTS e próximas revisões |
| 2 | Que potência firme é necessária para cumprir a norma em todos os 44 anos, incluindo secas e escassez em Espanha? Pode vir de ciclos combinados existentes, turbinas novas, bombagem, baterias, flexibilidade da procura, nuclear ou importações. Quanta capacidade a gás deve ser mantida, e até quando? Porque é que a avaliação europeia (ERAA 2025) não vê riscos para Portugal e a avaliação nacional vê riscos acima da norma entre 2028 e 2035? | Mecanismo de capacidade, reserva estratégica e manutenção de centrais | Governo, DGEG, ERSE e REN; 2027, na sequência do parecer da ACER de 7-9-2026 |
| 3 | Que combinação de baterias (2, 4 e 8 horas), bombagem existente e nova e flexibilidade da procura é ótima em 2030–2050? As metas da ENAE (≈6,9 GW em 2030 e ≈9,76 GW em 2040) são curtas, adequadas ou excessivas? O que dá a bombagem nos anos secos que as baterias não dão? | Versão final da ENAE; leilões de baterias | Governo e DGEG; a consulta pública da ENAE terminou a 16-9-2026 |
| 4 | A partir de que combinação de custo de investimento, prazo de construção e custo de capital entram no mix de custo mínimo de 2040 e 2050 uma a três unidades nucleares grandes (≈1,1 GW) ou módulos pequenos (≈300 MW)? Quanto poupa ou custa cada unidade imposta? Como muda o limiar se Espanha prolongar o seu nuclear ou se a procura crescer muito? | Preparar, ou não, o enquadramento legal e regulatório para uma opção nuclear | Governo e Assembleia da República; 2027–2030 (um programa nuclear de raiz demora 10 a 15 anos) |
| 5 | Quanto vale para Portugal a extensão das centrais nucleares espanholas para lá do calendário atual (Almaraz autorizada até 8-6-2030; parque encerrado até 2035)? Mede-se em €/ano, segurança, importações e CO2. | Posição portuguesa junto de Espanha e da UE | Governo; antes das decisões espanholas de encerramento |
| 6 | Qual o valor líquido de mais capacidade entre Portugal e Espanha, e do calendário da ligação Espanha–França pelo golfo da Biscaia? A partir de que custo compensa uma ligação de 1 GW a Marrocos? Como muda a exposição a falhas vindas do estrangeiro, como o isolamento ou o apagão? | Candidatura a cofinanciamento europeu da ligação a Marrocos; planos de rede | Governo e REN; relançamento acordado em julho de 2026 |
| 7 | A partir de que custo de investimento entra a eólica offshore flutuante em 2035, 2040 e 2050? Quanto custa, ou poupa, impor os 2 GW previstos no PNEC? Quanto contribui para a segurança no inverno? | Primeiro leilão offshore | Governo e DGEG; leilão ainda por lançar |
| 8 | Quanto custa ao sistema cada GW adicional de centros de dados com consumo constante? E cada GW de eletrolisadores flexíveis? Quem paga? | Regras de atribuição de capacidade de ligação a grandes consumidores | DGEG e ERSE; procedimentos em curso |
| 9 | Quanto custa, em €/MWh e em €/família/ano, melhorar cada pilar? Por exemplo: reduzir a dependência de importações, eliminar o gás fóssil até 2040, ou cumprir a norma sem importações nas horas críticas. | Metas políticas do PNEC | Governo e Assembleia da República |
| 10 | Que conclusões se mantêm em todos os anos meteorológicos, custos de capital, contextos espanhóis e níveis de procura? O que teria de ser verdade para cada conclusão mudar? | Todas as anteriores | — |
| 11 | Se o parque previsto no PNEC para 2030 for construído, que quota de eletricidade renovável se obtém em cada um dos 44 anos meteorológicos, face à meta de 93%? A análise técnica da ENAE aponta para 82–85%. | Monitorização do PNEC | DGEG |

---

## 3. O que se compara e como

### 3.1 Fronteira e perspetiva

- **Sistema.** Portugal continental, apenas eletricidade.
  - O hidrogénio, os centros de dados, os veículos elétricos e as bombas de calor entram como procura de eletricidade.
  - Os Açores e a Madeira ficam de fora, por serem sistemas separados e com outra economia. Ficam para um estudo próprio.
- **Perspetiva: o custo para Portugal.**
  - Conta-se o investimento e a operação em Portugal, mais o valor das importações e menos o valor das exportações.
  - Cada troca é valorizada à média dos preços dos dois lados da fronteira, ou seja, a renda de congestionamento é repartida a meias.
- **Custo de recursos.** É o que o país gasta de facto em capital, combustível, operação e manutenção.
  - Alguns pagamentos apenas passam dinheiro de um agente para outro: pagamentos por capacidade, custos de interesse económico geral (CIEG), impostos, receitas do comércio de emissões e rendas de congestionamento. São **transferências**: aparecem numa tabela própria, mas não se somam ao custo.
  - O emprego e a balança comercial são indicadores, não custos.

### 3.2 Horizontes

- **2030, ponto de partida.** O parque é o previsto no PNEC 2030 e não é otimizado. Serve para testar a meta de 93% de eletricidade renovável nos 44 anos meteorológicos.
- **2035 e 2050, horizontes principais**, iguais aos da DGEG.
- **2040, horizonte intermédio**, por três razões:
  - é o ano da meta da ENAE para 2040;
  - é o primeiro ano depois do encerramento previsto do nuclear espanhol;
  - é o primeiro ano em que uma central nuclear portuguesa seria realista.
- **Encadeamento.**
  - 2035 parte do parque de 2030; 2040 parte do parque de 2035; 2050 parte do de 2040. A cada passo descontam-se os encerramentos.
  - Cada passo decide sem conhecer o futuro. É a abordagem dita «míope», a mais estável no PyPSA-Eur.
  - Assim, 2050 não ignora o que já foi construído.
  - A variante com previsão perfeita fica para a versão 1.1.

### 3.3 Espanha, França e Marrocos

- **Espanha.**
  - O parque é fixo em cada cenário, segundo o plano espanhol (PNIEC) e o cenário central do TYNDP 2026 (National Trends+).
  - A operação hora a hora é decidida pelo modelo, em conjunto com Portugal. O modelo não decide o que Espanha constrói.
  - Única exceção: se o parque espanhol não cumprir a norma espanhola (1,5 h/ano), acrescenta-se capacidade de reserva em Espanha. Assim, Portugal não pode apoiar-se num vizinho sem margem.
- **Nuclear espanhol.** Caso base: o calendário em vigor (Almaraz até 8-6-2030; todo o parque encerrado até 2035). Variante: extensão de vida.
- **França.**
  - Um nó, com parque e procura fixos segundo o TYNDP 2026.
  - As trocas da França com o resto da Europa entram como um perfil horário exógeno.
  - Num teste de stress, as exportações francesas para a Península são limitadas nas horas de escassez ibérica.
- **Marrocos.**
  - Nó simplificado, presente só nos casos com uma ligação Portugal–Marrocos de 1 GW, a partir de 2035.
  - Os dados são frágeis, por isso esta opção é apresentada como limiar de custo e com confiança baixa.
- **Variante «à maneira da DGEG».** Espanha é substituída por uma série de preços fixa, como os «pressupostos» do caderno de encargos. Mede-se o erro que essa simplificação introduz.

### 3.4 O modelo

- **Ferramentas.**
  - PyPSA 1.3: biblioteca aberta de modelação de sistemas elétricos, a mesma em que assentam o PyPSA-Eur e o PyPSA-Spain.
  - HiGHS: solver de otimização aberto.
  - Nenhum software comercial, para que qualquer pessoa possa correr tudo.
- **Uso do PyPSA-Eur (v2026.09.0).**
  - Corre uma única vez, para calcular os potenciais renováveis de cada região.
  - O resto é um pacote pequeno, próprio do estudo, que monta o modelo a partir de tabelas verificadas.
  - Razão: algumas milhares de linhas testadas conseguem ser auditadas no tempo disponível; alterações dispersas num fluxo de trabalho europeu de grande dimensão não conseguem.
- **Geografia: 9 nós.**
  - Portugal (5), seguindo as regiões NUTS II: Norte, Centro, Lisboa e Vale do Tejo, Sines e o restante Sul (Alentejo e Algarve).
  - Sines fica num nó próprio porque concentra grande parte da nova procura prevista: centros de dados e pedidos para a Zona de Grande Procura. Concentra também um reforço de rede aprovado de cerca de 536 M€.
  - Espanha (3): Noroeste, Norte e Leste, Centro e Sul. Os três corredores de interligação com Portugal ficam bem representados.
  - França (1).
  - As trocas entre nós estão limitadas pela capacidade em cada sentido. Reforçá-las tem um custo.
  - A geografia é imposta explicitamente. Por omissão, o PyPSA-Eur reparte os nós pelos países em proporção ao consumo e daria apenas 1 ou 2 nós a Portugal.
- **Consumo atual por nó.** Reparte-se segundo o consumo municipal de eletricidade publicado pela DGEG, e não pela regra por omissão do PyPSA-Eur (60% PIB, 40% população). Com essa regra, polos industriais com pouca população, como Sines, ficariam mal representados.
- **Nova procura por nó.** A localização de centros de dados, eletrolisadores e grandes consumidores novos é um pressuposto explícito, com fonte. Quando a localização não é pública, o pressuposto é assinalado como tal.
- **Duas etapas.**
  1. **Dimensionamento.** O modelo escolhe o que construir, manter ou encerrar em Portugal. Olha em simultâneo para três anos meteorológicos «de projeto», com um passo de 3 horas.
  2. **Verificação.** Com as capacidades fixas, o sistema é operado hora a hora em cada um dos 44 anos, com avarias simuladas nas centrais. É aqui que se mede a segurança de abastecimento.
  - Porquê assim: um ano médio esconderia o risco hídrico, e resolver os 44 anos de uma só vez é impossível nestes computadores. Dimensionar em três anos representativos e verificar em 44 é uma aproximação auditável.
- **Limites de computação, assumidos à partida.**
  - Cada problema tem de caber num servidor gratuito do GitHub (4 núcleos, 16 GB de memória, 6 horas por tarefa), com um máximo de 12 GB de memória.
  - O tamanho previsto é de 1,6 a 2 milhões de variáveis. É a faixa em que os testes públicos mostram o HiGHS a resolver de forma fiável.
  - Se o teste de computação de 28 de outubro falhar, aplicam-se estas medidas, por esta ordem:
    1. passo de 4 horas;
    2. Sines fundido no nó Sul;
    3. Espanha com 2 nós;
    4. dois anos de projeto, com uma restrição de reserva para anos secos;
    5. França como fronteira fixa.

### 3.5 Clima e água

- **Base climática.** A Pan-European Climate Database v4.2 (PECD), do Copernicus e da ENTSO-E, com licença aberta CC BY 4.0. É a mesma base dos estudos europeus de adequação (ERAA) e de planeamento de rede (TYNDP). Dá:
  - fatores de capacidade horários da eólica e do solar, por região;
  - a temperatura ponderada pela população.
- **Anos.** 44 anos hidrológicos, de outubro de 1980 a setembro de 2024. O ano hidrológico começa a 1 de outubro, com a estação das chuvas.
- **Água.** O PECD dá afluências hídricas apenas semanais e para Portugal inteiro. Essas afluências são estimadas por um modelo estatístico, e o próprio PECD assinala valores duvidosos no fio-de-água português. Por isso:
  - a energia afluente de cada ano é ajustada ao índice de produtibilidade hidroelétrica (IPH) publicado pela REN, e o PECD dá apenas a forma ao longo do ano;
  - as afluências são repartidas pelos quatro nós portugueses segundo a potência instalada em cada bacia;
  - o fio-de-água é calibrado com as estatísticas da REN;
  - a calibração compara a produção hídrica mensal do modelo com a da REN **sem a turbinagem de água previamente bombeada**. Contá-la seria contar a mesma água duas vezes.
- **Albufeiras.**
  - Em cada ano, começam e acabam no nível mediano de 1 de outubro.
  - Uma corrida com dois anos secos seguidos, em que a água pode passar de um ano para o outro, testa as secas plurianuais.
- **Anos de projeto.** São escolhidos por uma regra publicada antes de qualquer cálculo de custos:
  - os 44 anos são ordenados pela energia hídrica afluente e divididos em três grupos iguais: secos, médios e húmidos;
  - em cada grupo escolhe-se o ano mais próximo da mediana do grupo;
  - em caso de empate, escolhe-se o ano com o inverno de menos vento e sol na Península;
  - cada ano escolhido pesa um terço.

  A regra, o código e os anos escolhidos são publicados com uma impressão digital (hash), que prova que não foram alterados depois.

### 3.6 Segurança de abastecimento: a mesma para todos

- **A norma.** Todos os portefólios cumprem a norma oficial de Portugal continental. A expectativa de horas com falta de abastecimento (LOLE) não pode passar de 1,46 horas por ano. A norma foi fixada pela DGEG sob proposta da ERSE.
  - A energia não fornecida vale 12 433 €/MWh (valor da ERSE).
  - Em Espanha, a norma é 1,5 h/ano e a energia não fornecida vale 22 879 €/MWh.
- **Porque é que a norma é imposta explicitamente.** O valor de 1,46 h resulta de dividir o custo de prolongar ciclos combinados existentes (18,2 €/kW·ano) pelo valor da energia não fornecida. Se a opção firme mais barata disponível fosse uma turbina a gás nova (74,8 €/kW·ano), um modelo que só «cobrasse» a energia não fornecida tenderia para cerca de 6 horas por ano. Por isso:
  - o prolongamento dos ciclos combinados existentes é uma opção do modelo, com os custos da ERSE e o potencial de 2,8 GW;
  - o dimensionamento tem uma restrição de capacidade firme mínima. A potência de cada tecnologia conta pela sua disponibilidade real nas horas críticas;
  - depois do dimensionamento, cada portefólio é testado nos 44 anos, com avarias. Se falhar a norma, a capacidade firme mínima sobe e o portefólio é reotimizado, até três vezes;
  - se ainda restar alguma falha, é publicada, juntamente com o custo de a corrigir.
- **Igualdade entre os dois países.** Dentro da otimização usa-se o mesmo valor da energia não fornecida em Portugal e em Espanha. Assim, o modelo não «empurra» os cortes de carga para o país com o valor mais baixo. Cada país é depois avaliado face à sua própria norma.
- **Como se mede.**
  - Operação horária em janelas semanais, com 48 horas de antecipação: o sistema não «adivinha» o ano inteiro.
  - Os níveis das albufeiras seguem as metas da corrida anual.
  - As avarias das centrais térmicas e nucleares são combinadas analiticamente.
  - Os intervalos de confiança obtêm-se reamostrando os anos.
  - Nas semanas mais críticas, uma simulação com avarias sorteadas confirma o resultado.
  - A simulação de Monte Carlo sequencial completa fica para a versão 1.1.

### 3.7 Como se conta o custo

- **Duas vistas.**
  - **Custo prospetivo:** só o que ainda se pode decidir. Serve para comparar opções.
  - **Custo total à maneira da DGEG:** o custo prospetivo, mais o custo dos ativos existentes (em anuidades) e das redes reguladas (com base nos proveitos permitidos pela ERSE). Serve para comparar com os €/MWh oficiais.
- **Duas linhas em cada vista:** «custo de recursos» e «custo de recursos + carbono». O carbono é valorizado ao preço do comércio europeu de emissões (CELE/ETS).
- **Componentes.**
  - Investimento anualizado, com um custo de capital base de 5% real.
  - Operação e manutenção.
  - Combustível.
  - Redes: transporte entre nós, interligações e uma estimativa de custos unitários de distribuição.
  - Armazenamento.
  - Serviços de sistema: reservas, estabilidade e energia não fornecida.
  - Saldo das trocas com o exterior.
- **Denominador.** MWh fornecidos a consumidores finais em Portugal continental, sem bombagem nem carregamento de baterias, sem perdas e sem exportações. Uma tabela de conversão dá os resultados com outros denominadores.
- **Moeda.** Euros de 2025, em termos reais. Todas as conversões passam por um único módulo: deflator do Eurostat (HICP) e câmbios do Banco Central Europeu.

### 3.8 Estabilidade da rede depois do apagão de 28 de abril de 2025

O relatório final dos peritos da ENTSO-E (março de 2026) aponta três fatores: falhas no controlo de tensão e de potência reativa, oscilações e desligamentos em cascata. A dinâmica da rede não pode ser simulada com dados abertos. O estudo usa por isso uma aproximação corrente, com custos:

- **Capacidade mínima em serviço.** Em cada hora, Portugal tem de ter em serviço uma capacidade mínima de uma de duas formas:
  - máquinas síncronas: hídrica, gás, nuclear ou biomassa;
  - equipamento que «forma rede»: baterias com controlo grid-forming ou compensadores síncronos.
- **Investimentos possíveis.** Compensadores síncronos e o acréscimo de custo das baterias grid-forming são investimentos que o modelo pode escolher.
- **Três níveis de exigência:** sem restrição, base e exigente. O nível base é calibrado com a prática da REN e da REE depois do apagão, se houver um valor citável. Caso contrário, os três níveis são apresentados como cenários.
- **Reserva.** A reserva para subir a produção cobre sempre a maior perda possível (o maior grupo gerador em Portugal), mais uma parcela ligada ao erro de previsão das renováveis.
- **Limite.** O estudo não afirma que um portefólio previne apagões. Mede quanto custa, em cada portefólio, garantir estes serviços.

### 3.9 Nuclear: um limiar, não uma estimativa

Não existe nenhum projeto nuclear português, e qualquer custo pontual seria inventado. Por isso:

- **Calendário.** O nuclear novo em Portugal só está disponível a partir de 2040.
- **Unidades impostas.**
  - Impõem-se 0, 1, 2 e 3 unidades de cerca de 1,1 GW, mais uma variante com 4 módulos de 300 MW.
  - Nestas corridas, o investimento nuclear não entra no custo, e o resto do sistema é reotimizado.
- **Limiar.** A poupança obtida mostra quanto o sistema pode pagar por cada central:
  - limiar do custo de investimento = poupança anual ÷ (potência × fator de anuidade × fator de juros durante a construção), descontados os custos de operação;
  - isto dá o limiar para qualquer custo de capital do nuclear (de 3% a 10%) e qualquer prazo de construção (7, 10 e 15 anos), sem novas corridas;
  - reporta-se o limiar médio e o marginal, isto é, quanto vale a última unidade acrescentada.
- **Teste de fecho.** Com o nuclear oferecido ao custo do limiar mais e menos 10%, o modelo tem de o construir ou de o rejeitar, como previsto.
- **Projetos reais como referência.** São marcados no gráfico, harmonizados para euros de 2025 a partir de fontes primárias:
  - o pressuposto da NEA no estudo sobre a Suécia: 7 000 USD de 2024 por kW, com 7 anos de construção;
  - Flamanville 3;
  - Hinkley Point C e Sizewell C;
  - Dukovany II;
  - os pequenos reatores modulares de Darlington.
- **Custos de sistema do nuclear incluídos:**
  - reserva para a perda da maior unidade;
  - paragens para reabastecimento;
  - limites de carga mínima e de variação de potência;
  - desmantelamento e resíduos;
  - ligação à rede;
  - um custo fixo de programa próprio de um país estreante (regulador, planos de emergência, parte de um repositório).
- **2035.** O nuclear português não é realista em 2035. A pergunta nuclear para esse ano é a extensão das centrais espanholas.

---

## 4. Cenários e sensibilidades

### 4.1 Portefólios: o que Portugal controla

1. **Trajetória oficial.** Combina:
   - o PNEC 2030, aprovado pela Resolução da Assembleia da República n.º 127/2025;
   - o relatório de monitorização da segurança de abastecimento mais recente (RMSA-E 2025), para 2035 e 2040;
   - o cenário central do TYNDP 2026 para Portugal, em 2050;
   - as metas de armazenamento da ENAE.

   Só se acrescenta o reforço necessário para cumprir a norma de fiabilidade.
2. **Custo mínimo neutro.** Todas as opções competem:
   - solar;
   - eólica em terra, incluindo repotenciação;
   - eólica offshore flutuante, a partir de 2035;
   - baterias de 2, 4 e 8 horas;
   - novos projetos de bombagem;
   - manter ou fechar os ciclos combinados existentes;
   - turbinas a gás novas, preparadas para hidrogénio;
   - nuclear novo, a partir de 2040;
   - reforço da interligação Portugal–Espanha e ligação a Marrocos;
   - flexibilidade da procura;
   - compensadores síncronos.
3. **Custo mínimo sem nuclear novo.**
4. **Nuclear imposto.** Uma, duas ou três unidades de cerca de 1,1 GW entre 2040 e 2050. Variante com 4 módulos de 300 MW.
5. **Sem gás fóssil a partir de 2040.** Só turbinas a hidrogénio ou a biometano, ao respetivo custo.
6. **Autonomia (2050).** Portugal cumpre a norma com as importações limitadas a 0% e a 50% da capacidade de interligação nas horas críticas. É o preço explícito da independência.

### 4.2 Quanto vale cada opção da DGEG

Para cada opção, compara-se com o custo mínimo neutro de 2035 e de 2050. As opções são: eólica offshore, gás novo, nuclear novo (só em 2050), reforço Portugal–Espanha, ligação a Marrocos, baterias, nova bombagem e flexibilidade da procura. Para cada uma calcula-se:

- quanto sobe o custo sem essa opção;
- quanto custa impô-la ao nível dos planos oficiais (por exemplo, os 2 GW de offshore do PNEC).

Para a ENAE em 2040, testam-se três casos: metas impostas, armazenamento livre e 1,5 vezes as metas.

O resultado é a tabela «quanto custa cada meta».

### 4.3 Futuros externos: o que Portugal não controla

- **Central.**
  - Cenário central do TYNDP 2026.
  - Calendário nuclear espanhol em vigor.
  - Ligação Espanha–França pela Biscaia em 2028, de 2,8 para 5 GW.
  - Preços centrais de gás e de CO2.
- **Nuclear espanhol prolongado.**
- **Procura eletro-industrial alta.**
  - Centros de dados e outros grandes consumidores segundo a avaliação nacional de adequação mais recente.
  - 3 GW de eletrolisadores, como no PNEC.
  - Eletrificação rápida.
- **Procura baixa.** Eletrificação lenta.
- **Ibéria condicionada.** Biscaia atrasada para 2032; renováveis e armazenamento espanhóis 25% abaixo do plano.
- **Choque de combustíveis.** Gás e CO2 a níveis semelhantes aos de 2022.

### 4.4 Sensibilidades, testadas uma de cada vez

Aplicam-se aos portefólios de custo mínimo, com e sem nuclear novo, para 2050, a partir do parque de 2040 da cadeia central. As exceções estão indicadas.

- **Custo de capital:**
  - uniforme de 3% e de 7% (cadeia completa);
  - diferenciado por tecnologia, com evidência de terceiros (cadeia completa).
- **Custos de tecnologia:** baterias ±30%; solar e eólica em terra ±25%; offshore flutuante alto e baixo.
- **Flexibilidade:** flexibilidade da procura nula e alta; centros de dados 10% flexíveis.
- **Norma de fiabilidade:** 0,5 e 3 horas por ano.
- **Estabilidade:** sem restrição e nível exigente.
- **Recursos:**
  - potencial eólico em terra limitado ao estimado pelo LNEG;
  - afluências hídricas −15%, como aproximação às alterações climáticas.
- **Interligação:** Portugal–Espanha a 3,0 GW nos dois sentidos.
- **Emissões:** emissões residuais permitidas em 2050 (gás de reserva).
- **Resolução temporal:** passo horário face a passo de 3 horas.
- **Fronteira:** Espanha como série de preços, à maneira da DGEG (2035 e 2050).
- **Procura marginal:** mais 1 GW de centros de dados com consumo constante, em 2035 e 2050. Dá o custo marginal para o sistema.

### 4.5 Testes de stress: o módulo de risco

Com o parque fixo e operação hora a hora:

- **Água e clima:**
  - o ano mais seco;
  - dois anos secos seguidos;
  - uma seca de vento e sol no inverno, coincidente com escassez em Espanha.
- **Exposição ao exterior:**
  - Portugal isolado de Espanha durante uma semana de ponta de inverno;
  - capacidade de importação reduzida durante várias semanas, como após o apagão;
  - exportações francesas limitadas nas horas de escassez ibérica.
- **Combustíveis:** choque de gás e CO2 num ano seco.
- **Nuclear:** atraso de 5 anos e sobrecusto de 50%, nos portefólios com nuclear.
- **Variante «avaliação nacional»:**
  - centros de dados altos;
  - Tapada do Outeiro fora do mercado;
  - bombagem menos disponível;
  - baterias com hipóteses conservadoras.

  O objetivo é perceber porque é que a avaliação nacional vê riscos que a europeia não vê.

Os resultados são apresentados numa matriz de risco, como pede a DGEG.

### 4.6 Robustez

- **Alternativas quase ótimas.**
  - Para 2050, procuram-se portefólios com um custo até 2% e até 5% acima do mínimo.
  - Para cada tecnologia, procura-se o máximo e o mínimo de capacidade possível dentro dessa margem. As tecnologias são: nuclear, offshore, eólica em terra, solar, baterias, bombagem, gás e interligações.
  - Isto mostra se o ótimo é «plano» (muitas soluções com custo quase igual) ou «estreito».
  - Entra na versão 1.0. A análise para 2035 faz-se se houver tempo.
- **Arrependimento.**
  - Quatro portefólios (oficial, custo mínimo, sem nuclear novo e nuclear imposto) são operados em quatro futuros: central, nuclear espanhol prolongado, procura alta e Ibéria condicionada. Em cada futuro, pode acrescentar-se reforço de adequação, pagando o respetivo custo.
  - Mede-se quanto se perde por ter escolhido o portefólio «errado».
  - Identificam-se as ações sem arrependimento para 2026–2030 e os sinais que devem levar a mudar de rumo.
- **Anos de projeto.** O dimensionamento é repetido com três conjuntos alternativos:
  - um com mais anos secos;
  - um com os segundos anos mais próximos das medianas;
  - um com um único ano médio, à maneira do estudo da NEA.
- **Aversão ao risco.** Uma variante dá mais peso aos piores anos e mede o «prémio de seguro».
- **Regras de leitura, fixadas antes dos resultados:**
  - diferenças inferiores a 2% do custo total do sistema, ou dentro da banda quase ótima de 2%, são reportadas como **indistinguíveis**;
  - uma tecnologia só é dita «no mix de custo mínimo» se estiver presente no caso central e em pelo menos três dos quatro conjuntos de anos de projeto.

### 4.7 Cenários propostos por terceiros

- **A chamada.**
  - Chamada aberta de 21 de outubro a 27 de novembro.
  - Usa-se um modelo de folha CSV, com validador automático.
  - É dirigida a todos, com convite expresso à APREN, à ZERO, à academia (IST, FEUP, NOVA, INESC TEC, LNEG, entre outros), à REN, à ERSE, a consultoras e à WePlanet.
  - O princípio: «o vosso cenário, os vossos números, o nosso modelo aberto».
- **Calendário de inclusão.**
  - As primeiras 4 propostas completas recebidas até 6 de novembro entram na versão preliminar.
  - Até mais 4, recebidas até 27 de novembro, entram na versão 1.0.
  - As restantes entram na versão 1.1.
  - São todas corridas exatamente como propostas, e publicadas.
- **Cenários «inspirados em críticos».** Garantem a simetria, são rotulados como interpretação nossa e nunca são atribuídos a ninguém:
  - **pró-renováveis:** solar e baterias baratos, muita flexibilidade;
  - **ambientalista:** procura baixa, sem gás novo;
  - **cético do nuclear:** custos e prazos como os de Flamanville e Hinkley Point, custo de capital de 8% a 10%;
  - **otimista do nuclear:** pressupostos da NEA para a Suécia.

### 4.8 Volume de cálculo e o que se corta primeiro

- **Volume.**
  - Cerca de 175 problemas de dimensionamento e cerca de 1 100 anos de operação horária.
  - Tudo corre em servidores gratuitos do GitHub, até 20 em paralelo, o que dá cerca de 1,5 a 2 dias de cálculo.
  - Uma reprodução completa por terceiros custa o mesmo tempo e zero euros.
- **Se o calendário apertar, corta-se por esta ordem** (decidida agora):
  1. alternativas quase ótimas para 2035;
  2. varrimento da quota de renováveis;
  3. cenários de terceiros para lá dos 4 primeiros;
  4. matriz de arrependimento, que fica só para 2050;
  5. Marrocos, que passa a usar valores da literatura;
  6. faturas por tipo de consumidor, que ficam só para a família de referência;
  7. sensibilidades de 2040.
- **Nunca se corta:**
  - a mesma fiabilidade para todos os portefólios;
  - os vários anos meteorológicos;
  - a validação antes dos resultados;
  - a verificação dupla dos pressupostos decisivos;
  - a reprodutibilidade.

---

## 5. Pressupostos principais e fontes

Os valores abaixo foram recolhidos e verificados pelos agentes de desenho a 8 de outubro de 2026. Antes de entrarem no modelo, cada um volta a ser verificado pelo robô de fontes. Os decisivos são ainda extraídos por dois agentes independentes (secção 8).

| Tema | Valor base | Variação testada | Fonte |
|---|---|---|---|
| Custo de capital (também usado como taxa de desconto) | 5% real, igual para todas as tecnologias | 3% e 7%; diferenciado por tecnologia; nuclear de 3% a 10% no limiar | Prática do estudo da NEA sobre a Suécia (2026) |
| Moeda | Euros de 2025, reais | — | Deflator HICP (Eurostat); câmbios do BCE |
| Custos de tecnologias | technology-data do PyPSA v0.15.0 (euros de 2025), com ajustes documentados | Intervalos das fontes; comparação com pelo menos dois outros catálogos | PyPSA technology-data; NREL ATB; IEA e NEA; Agência Dinamarquesa de Energia |
| Nuclear novo | Sem valor pontual: calcula-se o limiar | 3 000 a 15 000 €/kW; 7, 10 e 15 anos de construção; custo de capital de 3% a 10% | Projetos reais usados como referência |
| Manter os ciclos combinados existentes | 18,2 €/kW·ano (prolongamento só com custos de operação; potencial de 2,8 GW); 75,5 €/kW·ano (prolongamento longo) | Cenários alto e baixo da ERSE | ERSE e AFRY, relatório final de VOLL e CONE, dezembro de 2025 |
| Energia não fornecida | 12 433 €/MWh em Portugal; 22 879 €/MWh em Espanha | — | ERSE (dezembro de 2025) |
| Norma de fiabilidade | 1,46 h/ano em Portugal; 1,5 h/ano em Espanha | 0,5 e 3 h/ano | DGEG, sob proposta da ERSE; regulação espanhola |
| Combustíveis e CO2 | Pressupostos do TYNDP 2026 (versão de projeto) | Baixo, alto e choque como em 2022 | ENTSO-E e ENTSOG |
| Procura | Central: TYNDP 2026 National Trends+ para Portugal, ajustado aos 53,1 TWh consumidos em 2025 | Baixa; eletro-industrial alta | REN; TYNDP 2026; RMSA-E 2025 |
| Parque oficial em 2030 | Solar 20,8 GW; eólica em terra 10,4 GW; eólica offshore 2,0 GW; hídrica 8,1 GW, dos quais 3,9 GW de bombagem; gás natural 3,5 GW; eletrolisadores 3 GW; meta de 93% de eletricidade renovável | — | PNEC 2030 (Resolução da AR n.º 127/2025) |
| Armazenamento | ENAE: cerca de 6,9 GW em 2030 e 9,76 GW em 2040 | Metas impostas, livres, ou 1,5 vezes | Governo; consulta pública de 28 de agosto a 16 de setembro de 2026 |
| Interligações | Portugal–Espanha: 4,2 GW (de Espanha para Portugal) e 3,5 GW (no sentido inverso) desde 2-7-2026. Espanha–França: de 2,8 para 5 GW com a Biscaia (2028) | Portugal–Espanha a 3,0 GW nos dois sentidos, ou mais 1 a 3 GW; Biscaia só em 2032 | REE e REN; TYNDP 2026 |
| Nuclear espanhol | Almaraz até 8-6-2030; todo o parque encerrado até 2035 | Extensão de vida | Orden TED/864/2026 |
| Clima | PECD v4.2, de 1980 a 2024 | Três conjuntos de anos de projeto; afluências −15% | Copernicus e ENTSO-E (licença CC BY 4.0) |
| Potenciais renováveis | Áreas elegíveis calculadas com PyPSA-Eur e atlite | Eólica em terra limitada ao potencial do LNEG | PyPSA-Eur v2026.09.0; LNEG |
| Redes | Transporte entre nós com custo endógeno; distribuição por custos unitários | ±50% | ERSE (proveitos permitidos); planos de investimento da REN e da E-REDES |

**Regras sobre a origem dos números.**
- Só se usam números de terceiros, por esta ordem de preferência:
  1. fontes oficiais portuguesas;
  2. fontes europeias (ENTSO-E, Comissão Europeia);
  3. organismos intergovernamentais (NEA, IEA, IRENA, JRC);
  4. catálogos técnicos;
  5. literatura revista por pares.
- Nenhum número é produzido pelo autor ou pela WePlanet.
- Quando as fontes divergem, publica-se o intervalo completo.

---

## 6. Resultados por pilar

Não há índice composto: cada leitor pondera os pilares à sua maneira. O estudo mostra quanto custa melhorar cada um.

**Custo para o consumidor final**
- Custo total do sistema (M€/ano) e custo médio (€/MWh fornecido), nas duas vistas, com a diferença face à trajetória oficial.
- Decomposição no formato da DGEG, anual e por estação do ano, com a distribuição pelos 44 anos (percentis 10, 50 e 90).
- Preço de cada meta política, em M€/ano e em €/família/ano. Por exemplo: 2 GW de offshore, metas da ENAE, nenhum nuclear novo, nenhum gás fóssil em 2040.
- Exposição ao risco: custo no ano mais seco e com choque de combustíveis.
- Fatura indicativa:
  - na versão preliminar, para a família de referência da ERSE;
  - na versão 1.0, também para consumidores domésticos, PME e indústria.

  A fatura é uma incidência indicativa, não uma previsão tarifária.

**Segurança de abastecimento**
- Expectativa de horas de falha (LOLE, h/ano), com intervalo de confiança, face à norma de 1,46.
- Energia não fornecida esperada e no pior ano.
- Margem firme sem importações na pior semana.
- Dependência de importações nas 100 horas mais apertadas do ano.
- Ilhamento de uma semana: se o sistema aguenta, e quanta energia falta.
- Capacidade síncrona ou grid-forming disponível face ao mínimo exigido, e o custo de a garantir.
- Custo de cumprir a norma.

**Independência energética**
- Importações líquidas de eletricidade, em TWh e em percentagem da procura, num ano médio e num ano seco.
- Gás importado para produzir eletricidade (TWh e fatura em €), comparado com a capacidade do terminal de Sines nas semanas críticas.
- Autonomia de combustível armazenável: dias de gás armazenado, face a meses de combustível nuclear.
- Preço da independência: o custo dos portefólios de autonomia.

**Energia limpa**
- Emissões diretas de CO2 (Mt e g/kWh).
- Emissões de ciclo de vida, como indicador calculado com os fatores medianos do IPCC.
- Ocupação de solo e de mar (km²).
- Energia renovável desperdiçada (TWh e %).
- Óxidos de azoto e partículas (toneladas).
- Quota de eletricidade renovável. Serve, entre outras coisas, para o teste da meta de 93% em 2030.

**Produtos**
- Relatório em português (até 40 páginas), sumário executivo de 2 páginas e anexo técnico em inglês.
- Notas de decisão de 2 a 4 páginas, cada uma com a estrutura «decisão / o que o modelo diz / limiares / sinais a vigiar»:
  - **na versão preliminar:**
    - segurança de abastecimento e ciclos combinados, incluindo a divergência entre a avaliação europeia e a nacional;
    - armazenamento e ENAE;
    - nuclear: o limiar português e o valor do nuclear espanhol;
    - centros de dados e procura;
  - **na versão 1.0:** interligações e Marrocos.
- «Perguntas difíceis»: pelo menos 25 objeções previsíveis, cada uma com a resposta e com a figura ou o teste que a sustenta.
- Registo de afirmações: cada frase do sumário fica ligada às corridas que a sustentam e à sua robustez.
- Dados no Zenodo, com DOI e em formato aberto: resultados horários, redes resolvidas e tabelas.
- Site estático de resultados, na versão 1.0.
- **Anexo «Geografia do sistema elétrico»**, na versão 1.0 (3 a 5 páginas). Explica onde se produz, onde se consome e quanto custa ao sistema servir nova procura em cada zona da rede. Tem três partes:
  - **Quadro por região:** consumo, produção renovável e a relação entre os dois. Usa estatísticas da DGEG.
  - **Resultados do modelo por nó:** investimento, produção, trocas entre nós, congestionamento e energia renovável desperdiçada. Aparecem sempre ao lado dos totais nacionais, nunca somados a eles.
  - **Sensibilidade à localização da nova procura**, só se o teste de resolução mostrar que a localização pesa no custo. O limiar é fixado no registo prévio: por exemplo, mais de 1% do custo do sistema português. A sensibilidade desloca eletrolisadores e indústria eletrointensiva para os nós com excedente renovável. Os centros de dados ficam onde estão, porque a sua localização depende sobretudo de fibra, água e cabos submarinos. Se o limiar não for atingido, publica-se isso mesmo como resultado.

  O anexo não trata de descentralização económica, emprego, PIB regional nem habitação (ver secção 10).

---

## 7. Pontes com o estudo da DGEG

O estudo é desenhado de forma independente, para a máxima qualidade e utilidade. Estas pontes permitem pôr os dois estudos lado a lado sem trabalho adicional.

**Horizontes, métricas e vocabulário**
- **Horizontes:** 2035 e 2050, os mesmos da DGEG. Os anos de 2030 e 2040 vêm assinalados como extra.
- **Métricas iguais:**
  - «custo total do sistema» em € e «custo total médio» em €/MWh fornecido;
  - decomposição em geração, redes, armazenamento, serviços de sistema e outros;
  - resultados anuais e sazonais, como pede o Módulo 3.
- **Vocabulário:** usa-se o da DGEG (CTS, SEN, energia fornecida, serviços de sistema, potência firme).
- **Denominador:** documentado, com uma tabela de conversão para consumo final, consumo à saída da rede de transporte, e com ou sem autoconsumo.

**Custos e transferências**
- Uma tabela faz corresponder as 7 componentes de custo do caderno de encargos às linhas da nossa contabilidade. Cada linha vem marcada como custo de recursos, transferência ou indicador.
- O caderno levanta três riscos de dupla contagem:
  - lista «pagamentos por capacidade» duas vezes (em geração e em flexibilidade), ao lado do próprio investimento;
  - inclui o emprego e a balança comercial entre os custos;
  - pede um custo de carbono por tecnologia através do CELE.
- Mostramos também um total «à maneira da DGEG», reconciliado com o nosso, para que os números se possam comparar sem dupla contagem.

**Os sete módulos**
1. Diagnóstico → reconstituição de 2023–2025 e âncora de 2030.
2. Cenários → portefólios × futuros e o valor de cada opção.
3. Custos → tabelas principais.
4. Comparação internacional → tabela de métodos (NEA Suécia, NEA Suíça, RTE, PyPSA-Spain, DGEG). Na versão 1.0, se houver tempo, também o custo espanhol calculado pelo mesmo método.
5. Interligações e armazenamento → tabela de valor das opções e curvas armazenamento × interligação × reserva térmica.
6. Tarifas → faturas indicativas.
7. Risco → matriz de risco com as quatro famílias de risco da DGEG.

**Perguntas orientadoras do caderno (secção 2.2)**
- Uma tabela liga cada pergunta à secção e à figura do nosso relatório que lhe responde.
- A pergunta sobre o custo marginal de longo prazo em função da penetração de renováveis é respondida com um varrimento de 60% a 100% de renováveis. É declarado como contrafactual, não como cenário recomendado.

**Fronteira, fiabilidade e moeda**
- **Fronteira:** a DGEG trata Espanha como «pressupostos». Nós modelamos Espanha hora a hora e quantificamos a diferença com a variante «Espanha como série de preços».
- **Âmbito geográfico:** o caderno fala do Sistema Elétrico Nacional sem excluir as ilhas. Este estudo cobre apenas o continente, o que fica declarado.
- **Fiabilidade:** usamos a norma oficial e o valor da energia não fornecida da ERSE. As métricas de segurança da DGEG, que o adjudicatário ainda vai propor, poderão assim ser comparadas.
- **Moeda:** um conversor de moeda e de ano-base traz qualquer número da DGEG para euros de 2025.

**Kit de comparação**
- Um modelo de configuração e um script carregam as capacidades, a procura e os preços dos cenários da DGEG.
- Esses portefólios são então operados nos 44 anos, com verificação da norma e cálculo do custo nas duas contabilidades.
- Objetivo: publicar uma nota comparativa até 10 dias úteis depois da publicação da DGEG. Fica dentro do debate público de pelo menos 30 dias que o caderno prevê depois da conclusão do estudo.

**Contributo para o estudo oficial (se o autor o decidir)**
- Uma nota de critérios de qualidade, com base nos anexos de [docs/avaliacao-e-plano-2026-10-08.md](docs/avaliacao-e-plano-2026-10-08.md), segue para a DGEG (cts@dgeg.gov.pt), para a REN e para a ERSE até 14 de outubro.
- O protocolo segue a 21 de outubro, com a oferta de que o adjudicatário use o modelo aberto.

---

## 8. Validação e verificação

Os erros apanham-se por desenho, não por confiança. Cada número e cada linha de código passam por pelo menos dois «pares de olhos» independentes, e os testes automáticos correm a cada alteração.

1. **Registo prévio.**
   - Antes de qualquer resultado ficam registados, no Git e com DOI: as perguntas, os cenários, as métricas, as regras de leitura, as tolerâncias de validação e a regra dos anos de projeto.
   - Qualquer desvio posterior é registado publicamente.
2. **Cada número tem uma fonte verificável.**
   - A tabela de pressupostos é a única fonte de números do modelo. Cada linha indica a fonte, a página, a citação literal, a unidade e o ano monetário.
   - Um robô confirma que a citação existe na fonte e que o número bate certo depois da conversão de unidades e de moeda.
   - Quando a fonte é uma folha de cálculo ou um PDF digitalizado, um segundo agente verifica manualmente, e isso fica registado.
   - Nenhum número é escrito à mão no código.
3. **Dupla extração dos pressupostos decisivos.**
   - Os 25 a 40 parâmetros que mais pesam são extraídos por dois agentes, sem que nenhum veja o valor do outro. Incluem: custo de capital, custos do nuclear, da offshore, das baterias e da bombagem, preços do gás e do CO2, procura, interligações, energia das albufeiras e valor da energia não fornecida.
   - As divergências são resolvidas pelo agente coordenador e, se necessário, pelo autor.
4. **Casos de teste com resposta conhecida.** Problemas pequenos, cuja solução se calcula à mão, correm a cada alteração do código:
   - escolha entre duas tecnologias para uma curva de carga;
   - arbitragem de armazenamento;
   - congestionamento entre dois nós;
   - preço-sombra de um limite de CO2;
   - corte de carga ao valor da energia não fornecida;
   - unidades nucleares impostas;
   - anuidades e juros durante a construção;
   - balanço de uma albufeira;
   - cálculo da expectativa de falhas, comparado com uma simulação de um milhão de sorteios.
5. **Testes de coerência.**
   - Acrescentar uma opção nunca aumenta o custo ótimo.
   - Encarecer uma tecnologia nunca aumenta a sua capacidade.
   - Mais procura nunca reduz o custo.
   - Apertar o limite de CO2 nunca reduz o custo.

   Estes testes aplicam-se ao custo total otimizado. Não se aplicam ao custo para Portugal, que é calculado depois e pode legitimamente comportar-se de outra forma.
6. **Verificações em cada corrida.**
   - O balanço de energia fecha em cada nó e em cada hora.
   - Os custos por categoria somam o total.
   - Albufeiras e baterias ficam dentro dos seus limites.
   - O solver termina em estado ótimo.
   - Teste de «lucro nulo» para cada tecnologia: as receitas, incluindo as rendas das restrições, igualam os custos.
7. **Reconstituição do passado.**
   - 2023 e 2024 servem para calibrar. 2025 fica guardado e é avaliado uma única vez. 2022 (ano de seca) serve de diagnóstico.
   - Tolerâncias registadas antes de correr:
     - produção anual por tecnologia: eólica ±5%, solar ±10%, hídrica sem bombagem ±10%;
     - gás: ±25% ou ±1,5 TWh, comparando gás consumido com gás consumido. Em 2025 as centrais consumiram 13,8 TWh de gás e produziram cerca de 7,9 TWh de eletricidade de origem não renovável;
     - importações líquidas: ±2 TWh;
     - CO2: ±15%;
     - correlação mensal da produção hídrica: pelo menos 0,8.
   - O ano de 2025 inclui o apagão e a operação reforçada que se lhe seguiu, o que torna este teste exigente.
8. **Modelo independente.**
   - Um agente sem acesso ao código principal constrói um modelo mínimo, com Portugal e Espanha num nó cada, a partir apenas do protocolo e da tabela de pressupostos.
   - As diferenças principais (oficial face a custo mínimo; sem nuclear face a com nuclear; nuclear espanhol prolongado face ao central) têm de ter o mesmo sinal e diferir menos de 15%.
   - Diferenças maiores são investigadas e publicadas.
9. **Recálculo independente.** Um script que não partilha código com o modelo recalcula os números principais a partir dos resultados brutos. Os valores têm de coincidir a 0,1%.
10. **Verificações numéricas.**
    - Passo horário face a passo de 3 horas: o custo tem de ficar a menos de 2% e as capacidades principais a menos de 10%.
    - Resolução espacial: Portugal com 1 nó face a 5 nós, em 2035 e 2050. Mede quanto a geografia interna pesa no custo e serve de gatilho para a sensibilidade de localização do anexo de geografia.
    - Dois algoritmos do HiGHS são comparados numa amostra de corridas.
    - A memória usada e a gama dos coeficientes são vigiadas.
11. **Comparações externas.**
    - Adequação face ao ERAA 2025 e à avaliação nacional.
    - Mixes face ao TYNDP 2026.
    - Fatores de capacidade face aos observados pela REN.
    - Diferenças acima de 10% são explicadas num registo público.
12. **Equipa vermelha e simetria.**
    - Agentes separados, apenas com acesso de leitura, fazem duas rondas de crítica (uma ao protocolo e outra aos resultados):
      - um com o olhar da indústria das renováveis e outro com o de um defensor do nuclear, cada um à procura de pressupostos enviesados contra «o seu lado»;
      - um terceiro audita as contas e o código.
    - Uma tabela de simetria garante que cada risco e custo de integração se aplica a todas as tecnologias pela mesma regra: prémios de primeiro projeto, limites ao ritmo de construção, reservas e estabilidade.
13. **Congelamento de factos.**
    - A 13 de novembro e a 4 de dezembro reverificam-se todos os factos datados: ENAE, leilões, nuclear espanhol, interligações e tarifas.
    - Cada facto leva a indicação «verificado em».
14. **Revisão humana.**
    - O autor aprova o estudo nos pontos de decisão.
    - A versão preliminar é aberta a peritos externos e a partes com posições opostas.

---

## 9. Reprodutibilidade

- **Repositório e licenças.**
  - Repositório público no GitHub.
  - Licenças:
    - código: MIT;
    - texto, figuras, dados derivados e resultados: CC BY 4.0;
    - dados de terceiros: mantêm as licenças originais, listadas numa tabela própria.
- **Ambiente fixado.**
  - Gestor de ambientes pixi (conda-forge), com ficheiro de bloqueio.
  - Python 3.12, PyPSA 1.3.0, linopy 0.9.1 e highspy 1.15.1, com o componente HiPO.
  - Um ambiente separado, fixado no PyPSA-Eur v2026.09.0, usado só para o pré-processamento.
  - Só se usam versões publicadas há pelo menos duas semanas.
  - A imagem de contentor é publicada com impressão digital.
- **Fluxo de trabalho.** Snakemake leva os dados brutos até aos números do relatório. Comandos:
  - `pixi run reproduce`: refaz tudo a partir dos dados processados arquivados no Zenodo, sem precisar de chaves de acesso;
  - `pixi run reproduce --from-raw`: refaz também a aquisição dos dados (exige chaves do Copernicus e da ENTSO-E);
  - `pixi run figures`: refaz todas as tabelas e figuras em menos de 30 minutos, a partir dos resultados arquivados;
  - `pixi run ci-small`: caso de demonstração, em 5 minutos.
- **Dados.**
  - Nenhum ficheiro grande vai para o Git.
  - Cada ficheiro adquirido tem o URL, a data e a impressão digital (SHA-256) registados num manifesto.
  - As séries derivadas (clima por nó, afluências, procura) e os resultados vão para o Zenodo, com um DOI por versão.
- **Manifesto por corrida.**
  - Regista a versão do código, o ambiente, a configuração, os dados de entrada, o solver e as opções usadas, o estado final, o valor do objetivo, o tempo e a memória.
  - Cada tabela e figura indica de que corridas vem.
- **Integração contínua.**
  - Testes a cada alteração, em menos de 10 minutos.
  - Um caso reduzido todas as noites, comparado com valores de referência.
  - A matriz de cenários, a pedido, em servidores gratuitos do GitHub.
  - Uma reprodução semanal num contentor limpo.
- **Transparência dos agentes.**
  - As instruções dadas aos agentes, incluindo as regras de neutralidade, estão versionadas no repositório.
  - Cada pressuposto regista o agente que o extraiu e o que o verificou.

---

## 10. O que o estudo pode e não pode afirmar

**Pode:**
- comparar o custo de recursos de portefólios completos com a mesma segurança e as mesmas emissões, sob pressupostos declarados;
- dizer a partir de que custo uma opção compensa, e que ações compensam em todos os futuros testados;
- mostrar se o ótimo é plano ou estreito;
- quantificar o efeito dos anos secos, dos preços dos combustíveis, de Espanha e da procura.

**Não pode:**
- prever preços de mercado nem tarifas. As faturas são incidência indicativa;
- afirmar que um portefólio previne apagões. A estabilidade é tratada por uma aproximação com custos, não por uma simulação dinâmica;
- estimar o custo de um projeto concreto, nuclear ou outro;
- atribuir probabilidades aos futuros;
- dizer o que Espanha deve construir;
- tratar em detalhe a rede de distribuição, as ilhas ou a operação abaixo da hora;
- monetizar externalidades além do CO2. Essas são reportadas em unidades físicas;
- tratar o emprego, o PIB regional ou a balança comercial como benefícios a descontar do custo. São indicadores, e os salários já estão contidos nos custos;
- afirmar efeitos sobre a descentralização económica, a fixação de empresas ou pessoas, ou a habitação. O modelo não representa nenhum destes mecanismos;
- dizer qual é a melhor política. O custo mínimo é um critério entre vários: os quatro pilares e outros valores também contam.

---

## 11. Processo de comentários e revisão

- **Protocolo.** Publicado a 21 de outubro, aberto a comentários. As alterações feitas depois do registo vão para o registo público de desvios.
- **Versão preliminar.**
  - Publicada a 20 de novembro, com duas semanas de comentários, até 4 de dezembro.
  - Há convites diretos a peritos (academia, operadores, regulador, modeladores europeus) e a partes com posições opostas (associações de renováveis e ambientalistas, entre outras).
- **Canais.**
  - GitHub Discussions.
  - Modelos de issue: «Contestar um pressuposto», «Propor cenário», «Reportar erro».
  - Email.
- **Resposta a todos.** Cada comentário recebe uma resposta pública de um de três tipos:
  - aceite, com a alteração feita e o seu efeito nos resultados;
  - rejeitado, com a razão;
  - adiado para a versão 1.1.
- **Versão 1.0.** Publicada a 11 de dezembro, com o registo de respostas.
- **Erros.**
  - Qualquer correção depois de uma publicação dá origem a uma nova versão com DOI e a uma nota de errata, que diz o que mudou e em quanto.
  - Quem encontrar um erro que mude uma conclusão é agradecido no relatório.
- **Depois da 1.0.** Versão 1.1 em fevereiro ou março de 2027, e submissão de um artigo a uma revista com revisão por pares.

---

## 12. Glossário

- **Custo de recursos:** o que o país gasta de facto em capital, combustível, operação e manutenção.
- **Transferência:** um pagamento que passa dinheiro de um agente para outro sem consumir recursos, como um imposto ou um pagamento por capacidade.
- **LOLE:** número esperado de horas por ano em que a produção e as importações não chegam para a procura.
- **Energia não fornecida (VOLL):** o valor económico que os consumidores atribuem a cada MWh que fica por fornecer.
- **Potência firme:** a capacidade com que se pode contar nas horas críticas.
- **Portefólio:** o conjunto completo de centrais, armazenamento, redes e interligações de um cenário.
- **Anos de projeto:** os anos meteorológicos usados para dimensionar o sistema.
- **Alternativas quase ótimas:** soluções com custo apenas ligeiramente acima do mínimo, mas com composição diferente.
- **Custo de capital:** a rentabilidade exigida por quem financia um investimento, em termos reais.
- **Limiar (break-even):** o custo a partir do qual uma opção deixa de compensar.
- **Nó:** uma região do modelo, dentro da qual a rede não é representada em detalhe.
- **Afluência:** a água que chega às albufeiras e aos rios equipados.
- **Fio-de-água:** central hídrica sem albufeira significativa, que produz consoante o caudal do rio.
- **Grid-forming:** capacidade de um equipamento eletrónico, como uma bateria, de impor tensão e frequência à rede, como faz uma máquina síncrona.
- **Compensador síncrono:** máquina rotativa que não produz energia, mas dá inércia e controlo de tensão à rede.
