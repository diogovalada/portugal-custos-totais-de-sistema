# Frentes de trabalho dos agentes

> Estado: proposta, que acompanha o [PROTOCOLO.md](../PROTOCOLO.md) e o [ROTEIRO.md](../ROTEIRO.md).
> Cada frente corre numa sessão de agente própria. A integração faz-se só com a integração contínua verde e com revisão por uma sessão diferente da que escreveu a alteração.
> Nenhum número entra no modelo sem passar pelo registo de pressupostos.

| Frente | Depende de | Em paralelo |
|---|---|---|
| Coordenação e protocolo | — | não |
| Plataforma de reprodutibilidade | — | sim |
| Registo de pressupostos e verificação de fontes | Plataforma de reprodutibilidade | sim |
| Clima e renováveis | Plataforma de reprodutibilidade, Registo de pressupostos e verificação de fontes | sim |
| Hídrica | Plataforma de reprodutibilidade, Registo de pressupostos e verificação de fontes | sim |
| Procura | Plataforma de reprodutibilidade, Registo de pressupostos e verificação de fontes, Clima e renováveis | sim |
| Parque, vizinhos e interligações | Plataforma de reprodutibilidade, Registo de pressupostos e verificação de fontes | sim |
| Custos e finanças | Registo de pressupostos e verificação de fontes | sim |
| Núcleo do modelo | Plataforma de reprodutibilidade | sim |
| Validação e teste de computação | Núcleo do modelo, Clima e renováveis, Hídrica, Procura, Parque, vizinhos e interligações, Custos e finanças | não |
| Corridas de cenários e adequação | Núcleo do modelo, Validação e teste de computação | sim |
| Resultados, relatório e ponte DGEG | Corridas de cenários e adequação, Custos e finanças | sim |
| Verificação independente e equipa vermelha | Coordenação e protocolo, Registo de pressupostos e verificação de fontes | sim |
| Participação e comentários | Plataforma de reprodutibilidade, Coordenação e protocolo | sim |
| Comparação com o estudo DGEG (quando publicado) | Resultados, relatório e ponte DGEG | não |

## Coordenação e protocolo

Sessão persistente do agente principal.

Tarefas:
- escrever o PROTOCOLO.md (até 12 páginas, a partir do desenho aprovado), o ROTEIRO.md, o registo de decisões e o registo público de desvios;
- aprovar os esquemas das tabelas neutras propostos pela plataforma;
- fundir todas as alterações: só com integração contínua verde e revisão por uma sessão diferente da que escreveu a alteração;
- distribuir o trabalho pelas sessões paralelas, com no máximo cerca de 8 ativas;
- preparar, para cada ponto de decisão do autor, um memorando de 1 página com recomendação por omissão;
- escrever a nota semanal ao autor, às sextas;
- conduzir os congelamentos de factos (13-11 e 4-12) e as publicações;
- preparar a nota de critérios de qualidade, a partir dos anexos A e B de docs/avaliacao-e-plano-2026-10-08.md, para o autor assinar.

Entradas: pedidos de fusão de todas as frentes; relatórios de verificação; comentários triados.

Saídas:
- PROTOCOLO.md com DOI;
- ROTEIRO.md;
- docs/decisoes.md e docs/desvios.md;
- etiquetas de versão;
- memorandos ao autor;
- nota de critérios de qualidade.

**Concluída quando:** Nota de critérios de qualidade pronta a assinar a 13-10. Protocolo aprovado a 20-10 e publicado com DOI a 21-10. Cada ponto de decisão tem memorando e decisão registada. Versão preliminar publicada a 20-11 e versão 1.0 a 11-12, com o registo de discrepâncias vazio ou divulgado.

## Plataforma de reprodutibilidade

Reestruturação do repositório:
- README em português claro;
- CONTRIBUIR.md;
- LICENSE (MIT) e LICENSE-DOCS (CC BY 4.0), depois da aprovação das licenças e do nome pelo autor;
- CITATION.cff com o autor;
- documentos antigos movidos para docs/referencia/, sem os apagar (feito a 8-10-2026).

Ambiente pixi (conda-forge) com pixi.lock:
- Python 3.12, pypsa 1.3.0, linopy 0.9.1, highspy 1.15.1 e highspy-extras 1.15.1 (HiPO), snakemake 9.x;
- ambiente separado, fixado no PyPSA-Eur v2026.09.0, só para pré-processamento;
- nenhum pacote com menos de 14 dias. Em particular, não usar atlite 0.7.0 nem powerplantmatching 0.9.1, publicados a 7-10-2026.

Fluxo de trabalho e contratos:
- esqueleto Snakemake: dados brutos, tabelas neutras, redes, corridas, contabilidade, relatório;
- esquemas pandera para as tabelas neutras;
- manifesto de aquisição: URL, data, SHA-256, licença;
- manifesto por corrida: commit, lock, configuração, entradas, solver e opções, estado, objetivo, memória máxima, tempo.

GitHub Actions:
- pr.yml, em menos de 10 minutos: ruff, testes, esquemas, verificação de pressupostos, guarda de diretórios por frente, guarda de memória de 13 GB;
- nightly.yml: caso ci-small comparado com métricas de referência;
- estudo.yml: matriz a pedido, até 20 tarefas em paralelo, 6 horas por tarefa, artefactos guardados;
- release.yml: etiqueta, imagem no GHCR identificada por digest, depósito no Zenodo.

Comandos: pixi run reproduce, reproduce-core, figures, ci-small, test.

Saídas: config/, schemas/, workflow/, .github/ e o contrato de diretórios por frente.

**Concluída quando:** Até 14-10:
- pixi run test e ci-tiny passam num servidor do GitHub em menos de 10 minutos;
- a guarda de diretórios rejeita uma alteração de teste feita fora do diretório da frente;
- estudo.yml lança 3 tarefas fictícias;
- existem esquemas para todas as tabelas neutras.

A partir de 30-10: a reprodução semanal num contentor limpo está verde.

## Registo de pressupostos e verificação de fontes

Ficheiro dados/pressupostos.csv, com os campos:
- id, valor, unidade, ano monetário, intervalo;
- URL, cópia no Wayback, página ou tabela, citação literal, data de recolha;
- agente extrator e agente verificador;
- estado: verificado-robô, verificado-manual-segundo-agente ou pendente;
- quem provavelmente contestará o valor.

Robô de verificação. Para cada linha:
- descarrega a fonte, com cache;
- extrai o texto (pdftotext, HTML, ou openpyxl para XLSX);
- procura a citação por correspondência aproximada;
- lê o número e compara-o com o valor depois da conversão de unidades (pint) e de moeda.

A conversão de moeda passa por um módulo único: deflator HICP do Eurostat e câmbios anuais do BCE.

Fontes ilegíveis para o robô (PDF digitalizado, páginas JavaScript) exigem verificação manual registada por um segundo agente.

Outros entregáveis:
- linter que falha se houver números literais em código ou configuração fora de uma lista de exceções;
- registo de factos datados, cada um com «verificado em»;
- protocolo de dupla extração cega para os 25 a 40 parâmetros decisivos, ordenados por uma triagem rápida de sensibilidade.

Entradas: propostas de linhas das frentes de dados.

Saídas: pressupostos.csv, factos.csv e relatório de divergências.

**Concluída quando:** O robô falha nos 5 erros semeados e passa nas linhas válidas. Os erros semeados são: URL falso, citação alterada, unidade errada, ano monetário errado e número ausente da citação. Testes do módulo de moeda verdes até 16-10. Até 23-10: 100% das linhas verificadas, pelo robô ou manualmente, e dupla extração dos parâmetros decisivos sem divergências por resolver.

## Clima e renováveis

PECD v4.2 histórico (1980–2024), via Copernicus CDS, para Portugal, Espanha e França:
- fatores de capacidade horários de eólica em terra, eólica offshore e solar, por região NUTS2 e por zona offshore;
- temperatura ponderada pela população.

As séries nacionais de eólica estão descontinuadas no PECD; agregar a partir de NUTS2.

Mapeamento das regiões para os 9 nós (Portugal: Norte, Centro, Lisboa e Vale do Tejo, Sines, restante Sul). Em Espanha, ponderar pela capacidade instalada.

Potenciais elegíveis por nó e tecnologia:
- correr uma vez o PyPSA-Eur v2026.09.0 sobre o cutout pré-construído;
- correr num contentor de agente, não num servidor do GitHub, porque estes têm só 14 GB de disco;
- comparar com o potencial eólico do LNEG.

Comparação dos fatores de capacidade anuais com os observados pela REN em 2015–2025.

Com a frente Hídrica: implementar a regra dos anos de projeto e os conjuntos alternativos, e publicá-los com impressão digital.

Perfil simplificado para Marrocos, com confiança baixa.

Saídas: perfis_vre.parquet, potenciais.csv, temperatura.parquet, anos_projeto.csv.

**Concluída quando:** Tabelas válidas nos esquemas. Fatores de capacidade anuais dentro de ±10% dos observados, ou com correção documentada. Anos de projeto e impressão digital publicados a 23-10, antes de qualquer corrida de custos. Séries derivadas depositadas no Zenodo como rascunho.

## Hídrica

Albufeiras e bombagem por nó (REN Dados Técnicos 2025, DGEG, SNIRH): potências e energias armazenáveis. Agregados espanhóis equivalentes.

Cadeia de afluências:
1. séries semanais do PECD v4.2 para PT00 e ES00. São estimadas por um modelo estatístico, e o PECD assinala valores baixos no fio-de-água português;
2. energia anual de cada ano ajustada ao IPH da REN;
3. repartição pelos nós segundo a potência de cada bacia;
4. forma a 3 horas e a 1 hora.

O fio-de-água é calibrado com as estatísticas da REN.

Calibração: produção hídrica mensal modelada em 2015–2025 face à da REN, descontada a turbinagem de água bombeada.

Outros entregáveis:
- níveis medianos a 1 de outubro, piso P10 e caudais ecológicos aproximados;
- cadeias de 2 anos secos;
- candidatos a nova bombagem, com custos;
- índice hídrico anual para a regra dos anos de projeto;
- comparação com o método de afluências do PyPSA-Eur, onde houver dados.

Saídas: afluencias.parquet, armazenamento_hidrico.csv, candidatos_bombagem.csv, indice_hidrico_anual.csv.

**Concluída quando:** Índice hídrico anual entregue a 21-10. Até 28-10: produção hídrica anual modelada, sem bombagem, dentro de ±10% da REN em cada ano de 2015 a 2025, e correlação de Spearman de pelo menos 0,9 com o IPH. Se não for possível, o desvio fica documentado. Tabelas válidas nos esquemas.

## Procura

Cargas horárias de 2015–2025 para Portugal, Espanha e França (ENTSO-E Transparency, REN Data Hub).

Regressão à temperatura do PECD, para gerar a procura de cada um dos 44 anos.

Trajetórias:
- central: TYNDP 2026 National Trends+ para Portugal, reconciliado com os 53,1 TWh de 2025 da REN;
- alta eletro-industrial: centros de dados e grandes consumidores da avaliação nacional de adequação mais recente, 3 GW de eletrolisadores do PNEC e eletrificação rápida;
- baixa.

Componentes com perfil próprio:
- veículos elétricos, parte com carregamento inteligente;
- bombas de calor;
- centros de dados com consumo constante, e uma variante 10% flexível;
- eletrolisadores flexíveis, com armazenamento de hidrogénio e consumo anual fixo;
- uma parcela de resposta da procura, com custo de ativação.

Repartição do consumo atual pelos nós segundo o consumo municipal de eletricidade da DGEG (ficheiro de 2024, com códigos NUTS), e não pela regra por omissão do PyPSA-Eur. A nova procura (Zona de Grande Procura, Sines, eletrolisadores, centros de dados) é colocada por pressuposto explícito, com fonte.

Saídas: procura.parquet (por nó, cenário, horizonte, ano meteorológico e hora), componentes_procura.csv, flexibilidade.csv.

**Concluída quando:** No ano guardado: erro percentual absoluto médio horário de no máximo 5% e erro na ponta de no máximo 3%. Totais anuais iguais às fontes citadas. Âncoras com dupla extração até 23-10. Séries completas até 28-10.

## Parque, vizinhos e interligações

Portugal:
- parque existente, projetos comprometidos e encerramentos (REN, DGEG);
- capacidades da trajetória oficial: PNEC 2030 (Resolução da AR n.º 127/2025); RMSA-E 2025 para 2035 e 2040, a obter ou, se não for público, a pedir à DGEG; TYNDP 2026 National Trends+ para 2050;
- metas da ENAE.

Espanha:
- parques do PNIEC e do TYNDP 2026;
- calendário nuclear unidade a unidade (Orden TED/864/2026 para Almaraz), com variante de extensão;
- regra de reforço de adequação para cumprir 1,5 h/ano.

França: parque, procura e perfil exógeno das trocas com o resto da Europa.

Interligações, por sentido:
- Portugal–Espanha: 4,2 GW e 3,5 GW desde 2-7-2026, mais os projetos do TYNDP 2026;
- Espanha–França: de 2,8 para 5 GW com a Biscaia em 2028, e a evolução prevista no TYNDP;
- candidatos de reforço, com custos das fichas de projeto do TYNDP;
- candidato Portugal–Marrocos de 1 GW.

Taxas de avaria por tecnologia, dos anexos do ERAA 2025.

Saídas: parque.csv, trajetoria_oficial.csv, interligacoes.csv, candidatos_rede.csv, taxas_avaria.csv.

**Concluída quando:** Até 23-10:
- totais de 2024 e 2025 dentro de 2% dos da REN e da REE;
- cada capacidade de cenário ligada a uma linha do registo;
- nuclear espanhol verificado unidade a unidade em atos oficiais;
- tabelas válidas nos esquemas.

## Custos e finanças

Base: technology-data v0.15.0, convertido para euros de 2025.

Ajustes com fonte para:
- nuclear grande e pequenos reatores modulares, com prémio de primeiro projeto e custo fixo de programa estreante;
- eólica offshore flutuante;
- baterias;
- bombagem, local a local;
- compensadores síncronos e acréscimo de custo grid-forming;
- ligações em corrente contínua.

Retenção dos ciclos combinados, a partir da ERSE/AFRY:
- 18,2 €/kW·ano para o prolongamento só com custos de operação, com potencial de 2,8 GW;
- 75,5 €/kW·ano para o prolongamento longo;
- conversão explícita para a convenção do modelo. Os valores da ERSE são por kW firme: o solar aparece com 30 260 €/kW·ano.

Preços:
- gás e CO2 do TYNDP 2026 (versão de projeto), mais um caso de choque.

Custo de capital:
- uniforme a 3%, 5% e 7%;
- diferenciado por tecnologia, com evidência de terceiros.

Redes e outros custos:
- custos unitários de rede: planos da REN e da E-REDES, proveitos permitidos pela ERSE;
- custos dos ativos existentes, para a vista DGEG;
- acréscimo para o sistema de gás.

Âncoras nucleares harmonizadas, só com fontes primárias. A taxa de 6,7% de Sizewell C e o prémio de 120% do CSIRO ficam de fora até haver fonte primária.

Tabela de simetria.

Saídas: custos_tecnologia.csv, combustiveis_co2.csv, custo_capital.csv, custos_rede.csv, ancoras_nucleares.csv, tabela_simetria.md.

**Concluída quando:** Até 23-10:
- todos os custos no registo, com valor base e intervalo;
- comparação com pelo menos dois outros catálogos, com desvios acima de 30% explicados;
- testes de conversão monetária verdes;
- parâmetros decisivos com dupla extração;
- tabela de simetria publicada com o protocolo.

## Núcleo do modelo

Pacote do estudo sobre PyPSA 1.3.0 e linopy.

Formulação:
- construtor da rede a partir das tabelas neutras;
- os 3 anos de projeto em sequência, com pesos de probabilidade no objetivo e níveis das albufeiras fixados em cada fronteira de ano. É equivalente a um problema estocástico de duas fases neutro ao risco: um caso de teste compara-o com n.set_scenarios num exemplo pequeno;
- variante de aversão ao risco com n.set_scenarios e CVaR;
- cadeia míope 2030→2035→2040→2050.

Restrições:
- limite ou preço de CO2;
- reserva ascendente pelo menos igual ao maior grupo português, mais o erro de previsão;
- capacidade síncrona ou grid-forming mínima;
- capacidade firme mínima, com cada tecnologia contada pela sua disponibilidade nas horas críticas;
- blocos nucleares impostos com custo de investimento nulo;
- limites ao ritmo de construção;
- expansão das interligações;
- resposta da procura;
- ponto de ligação para o reforço em Espanha;
- o mesmo VOLL em Portugal e em Espanha no objetivo.

Solver:
- HiPO, com IPX como recurso;
- limites finitos e verificação da gama de coeficientes;
- crossover só nas corridas principais, e só se couber no tempo.

Pós-processamento e simulação:
- contabilidade nas duas vistas, reconciliada com o objetivo;
- custo para Portugal, com as trocas valorizadas à média dos preços de fronteira;
- métricas dos quatro pilares;
- operação horária com capacidades fixas, em janelas semanais com 48 horas de antecipação e metas de albufeira;
- convolução analítica de avarias, com intervalos por reamostragem;
- verificação das semanas críticas com avarias sorteadas;
- módulo de alternativas quase ótimas.

Testes:
- pelo menos 15 casos com resposta analítica;
- testes de coerência, aplicados só ao objetivo do problema e não ao custo para Portugal;
- lucro nulo com rendas das restrições: bloqueante nos casos de teste, apenas diagnóstico em produção.

Entradas: tabelas neutras.

Saídas, por corrida: resultados/<id>/rede.nc, manifesto.json, contabilidade.csv, metricas.csv.

**Concluída quando:** Até 26-10:
- casos de teste e testes de coerência verdes;
- contabilidade igual ao objetivo a 1e-6 nos casos de teste;
- equivalência entre a formulação sequencial e a estocástica demonstrada;
- convolução de avarias a menos de 2% de um Monte Carlo com 10^6 sorteios;
- ci-small corre em menos de 10 minutos;
- código revisto pela verificação independente.

## Validação e teste de computação

Teste de computação nos servidores do GitHub, com decisão registada:
- passo de 3 horas face a 4 horas;
- HiPO face a IPX;
- 3 face a 2 anos de projeto;
- alavancas aplicadas pela ordem do protocolo.

Verificação do passo horário face ao de 3 horas, no custo mínimo de 2035 e 2050, com o ano mediano.

Reconstituição do passado:
- 2023 e 2024 servem de calibração;
- 2025 é avaliado uma única vez, depois de congelada a calibração;
- 2022 serve de diagnóstico de seca.

Comparação com as tolerâncias registadas no protocolo. O gás compara-se combustível com combustível: 13,8 TWh consumidos em 2025, e não os 7,9 TWh de produção não renovável.

Relatório de validação público.

**Concluída quando:** Decisão de resolução a 28-10, com 90% das corridas de dimensionamento abaixo de 3 horas e abaixo de 12 GB de memória. Relatório de validação público a 2-11. Tolerâncias inalteradas desde o registo, o que é verificável no histórico Git. Desvios explicados e levados ao autor.

## Corridas de cenários e adequação

Matriz de cenários em Snakemake e estudo.yml.

Portefólios e opções:
- cadeias dos portefólios principais;
- ciclo de fiabilidade, até 3 iterações, com reforço em Espanha;
- tabela de valor das opções (sem a opção e com a opção imposta) para 2035 e 2050;
- variantes da ENAE para 2040;
- portefólios de autonomia e sem gás.

Nuclear:
- k = 0 a 3 unidades e módulos de 300 MW;
- 3 custos de capital uniformes e 2 níveis de procura;
- testes de fecho a ±10%.

Futuros, sensibilidades e stress:
- futuros externos;
- sensibilidades;
- testes de stress;
- conjuntos alternativos de anos de projeto;
- variante Espanha como série de preços;
- mais 1 GW de centros de dados.

Verificação horária:
- 44 anos para os portefólios finalistas em 2035, 2040 e 2050;
- 10 anos críticos para os restantes.

Análises adicionais:
- matriz de arrependimento 4×4;
- cenários de terceiros;
- na versão 1.0: alternativas quase ótimas e varrimento da quota de renováveis.

Saídas: resultados com manifestos, índice de corridas e depósito no Zenodo.

**Concluída quando:** Conjunto da versão preliminar completo a 13-11: todas as corridas em estado ótimo e com manifesto, e as falhas registadas com a sua causa. Cada portefólio cumpre 1,46 h/ano, ou é assinalado com o défice e o custo de o corrigir. Conjunto da versão 1.0 completo a 7-12.

## Resultados, relatório e ponte DGEG

Ponte DGEG:
- tabelas no formato DGEG: cinco categorias, anual e sazonal;
- tabela de transferências e reconciliação com as 7 componentes do caderno de encargos;
- conversão de denominadores e conversor monetário;
- tabela de respostas às perguntas orientadoras do caderno;
- kit de comparação DGEG: dgeg.yaml e script de ingestão.

Resultados:
- superfície de limiar nuclear, com âncoras e certificado de fecho;
- tabela de valor das opções;
- painéis dos quatro pilares e preço de cada pilar;
- matriz de arrependimento e sinais de mudança;
- faturas indicativas;
- registo de afirmações (claims.csv), com a robustez de cada uma.

Publicações:
- relatório Quarto em português, até 40 páginas, com todos os números lidos dos resultados;
- sumário de 2 páginas;
- anexo técnico em inglês;
- notas de decisão: 4 na versão preliminar e mais 1 na 1.0;
- Perguntas difíceis, com pelo menos 25 objeções;
- secção «o que o estudo pode e não pode afirmar»;
- site estático, na versão 1.0.

Saídas: relatorio/, notas/, tabelas_dgeg/, kit_dgeg/.

**Concluída quando:** O verificador de números não encontra nenhum número escrito à mão. Todas as figuras são regeneradas na integração contínua. O teste de fecho do limiar nuclear está verde. O kit DGEG corre de ponta a ponta um cenário fictício, construído com números do RMSA e do PNEC, em menos de 48 horas de cálculo. Aprovação da equipa vermelha e do autor a 18-11 e a 10-12.

## Verificação independente e equipa vermelha

Sessões só com acesso de leitura, separadas das que produzem.

Verificação:
- dupla extração cega dos parâmetros decisivos;
- modelo mínimo independente: Portugal e Espanha com um nó cada, em linopy simples, construído só a partir do protocolo e do registo, sem acesso ao código principal;
- recálculo independente dos números principais a partir dos resultados brutos, sem importar o pacote do estudo;
- concordância entre HiPO e IPX numa amostra de corridas;
- reprodução em contentor limpo antes de cada versão.

Equipa vermelha:
- duas rondas: sobre o protocolo (16 a 19-10) e sobre os resultados (13 a 17-11);
- dois olhares simétricos, pró-renováveis e pró-nuclear, mais um auditor de contas e código;
- auditoria da tabela de simetria por um agente que não viu resultados.

Registo público de discrepâncias.

**Concluída quando:** Até 2-11, o modelo independente concorda no sinal e a menos de 15% nas diferenças principais; caso contrário, a discrepância é investigada e publicada. O recálculo coincide a 0,1%. A reprodução limpa coincide a 1e-3 relativo na versão preliminar e na 1.0. Todas as constatações da equipa vermelha têm resposta pública.

## Participação e comentários

Canais e modelos:
- modelos de issue: Contestar um pressuposto, Propor cenário, Reportar erro;
- GitHub Discussions;
- modelo CSV de cenário, com validador automático.

Contacto e resposta:
- rascunhos de convites para o autor enviar, a peritos e a partes com posições opostas;
- registo público de respostas;
- triagem, com confirmação de receção em 48 horas;
- conversão dos comentários aceites em alterações com testes;
- política de erratas.

**Concluída quando:** Canais e modelos ativos a 21-10. Até 4 cenários de terceiros validados a 6-11 e até mais 4 a 27-11. Todos os comentários recebidos até 4-12 têm resposta pública no registo publicado com a versão 1.0: aceite, rejeitado com razão ou adiado para a 1.1.

## Comparação com o estudo DGEG (quando publicado)

Quando a DGEG publicar:
1. extrair cenários, pressupostos e resultados, com referência à página;
2. carregá-los pelo kit como portefólios fixos;
3. operá-los nos 44 anos, com verificação da norma;
4. recalcular o custo nas duas contabilidades;
5. escrever uma nota comparativa lado a lado, no formato DGEG;
6. submetê-la no debate público.

**Concluída quando:** Corridas internas concluídas em 3 dias úteis. Nota pública em 10 dias úteis após a publicação, com cada número da DGEG ligado a uma página do documento oficial.
