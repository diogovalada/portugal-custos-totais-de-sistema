# Roteiro até à versão 1.0

> Estado: proposta, à espera da aprovação do autor (ponto de decisão 1). Desenho do estudo: [PROTOCOLO.md](PROTOCOLO.md). Frentes de trabalho dos agentes: [docs/frentes-de-trabalho.md](docs/frentes-de-trabalho.md). Decisões registadas: [docs/decisoes.md](docs/decisoes.md).
>
> As datas pressupõem a aprovação do desenho até cerca de 12 de outubro. Se a aprovação atrasar, as datas deslocam-se o mesmo número de dias, exceto as da versão 1.0, que se protegem com a ordem de corte.

**Princípios**
- **Datas fixas.** Se algo atrasar, corta-se pela ordem combinada (ver o fim), não se adia.
- **Decisões do autor.** O autor intervém apenas em cinco pontos de decisão, mais um que só acontece se for necessário. Cada ponto chega com um memorando de uma página e uma recomendação.
- **Nota semanal.** Às sextas, o agente coordenador envia ao autor uma nota de uma página.
- **Ritmo de trabalho.** Os agentes trabalham em paralelo, com até cerca de oito sessões ativas ao mesmo tempo.

| Data | Marco | Concluído quando | Quem |
|---|---|---|---|
| Qui 8 out | Desenho proposto | Este documento entregue | Agente coordenador |
| Sex 9 out | **Ponto de decisão 1:** aprovação do desenho. Credenciais criadas | Desenho aprovado. Credenciais criadas e configuradas como segredos: Copernicus CDS, ENTSO-E Transparency, Zenodo ligado ao ORCID. Repositório público, com Actions, Discussions e Pages ativos | Autor |
| Seg 12 out | Arranque das frentes paralelas | Sessões lançadas: plataforma, pressupostos, clima, hídrica, procura, parque, custos, núcleo do modelo e verificação independente | Agente coordenador |
| Qua 14 out | Plataforma pronta. Nota de critérios de qualidade enviada, se o autor o decidir | Licenças e CITATION criados, depois da aprovação do autor. Integração contínua verde num caso mínimo. Nota enviada à DGEG (cts@dgeg.gov.pt), à REN e à ERSE, com pedido de informação sobre o estado do estudo oficial. A reestruturação do repositório (README, CONTRIBUIR, docs/referencia) já foi feita a 8 out | Agentes; envio pelo autor |
| Sex 16 out | Rascunho do protocolo. Robô de verificação de fontes ativo. Dados climáticos descarregados | O robô deteta os 5 erros semeados. Descarga do PECD concluída | Agentes |
| 16–19 out | Equipa vermelha sobre o protocolo | Relatório publicado, com resposta a cada ponto | Agentes de verificação |
| Ter 20 out | **Ponto de decisão 2:** protocolo, licenças e texto de autoria | Aprovação registada | Autor |
| Qua 21 out | **Protocolo público com DOI.** Chamada aberta para cenários e para contestação de pressupostos | Protocolo enviado à DGEG, REN e ERSE. Canais de comentário ativos. Convites enviados | Agentes; convites pelo autor |
| Sex 23 out | **Ponto de decisão 3:** entradas e cenários | Todas as tabelas de entrada estão verificadas. Os pressupostos decisivos têm dupla extração sem divergências. Os anos de projeto estão publicados com impressão digital, antes de qualquer corrida de custos. A lista final de cenários está aprovada | Agentes; aprovação do autor |
| Seg 26 out | Núcleo do modelo pronto | Casos de teste e testes de coerência verdes. Caso reduzido corre em menos de 10 minutos | Agentes |
| Qua 28 out | Teste de computação. Hídrica calibrada | Resolução decidida: 90% das corridas abaixo de 3 h e de 12 GB. Custo mínimo de 2035 completo num servidor do GitHub. Produção hídrica dentro de ±10% da REN | Agentes |
| Seg 2 nov | **Relatório de validação público.** Arranque da produção | Reconstituição de 2023–2025 face às tolerâncias registadas. Modelo independente concorda no sinal e a menos de 15%. Se houver desvios: **ponto de decisão extra** do autor | Agentes; autor se necessário |
| Sex 6 nov | Prazo dos cenários de terceiros para a versão preliminar | Até 4 propostas validadas e em execução | Agentes |
| Seg 9 nov | Núcleo de resultados | Cadeias 2035→2040→2050 dos portefólios principais concluídas. Verificação nos 44 anos e ciclo de fiabilidade concluídos | Agentes |
| Sex 13 nov | Todas as corridas da versão preliminar concluídas. Congelamento de factos | Todas as corridas em estado ótimo, com manifestos. Factos datados reverificados | Agentes |
| 13–17 nov | Equipa vermelha sobre os resultados. Recálculo independente. Reprodução limpa | Recálculo coincide a 0,1%. Reprodução coincide a 0,1% | Agentes de verificação |
| Qua 18 nov | **Ponto de decisão 4:** aprovação da versão preliminar e do plano de divulgação | Aprovação registada | Autor |
| **Sex 20 nov** | **VERSÃO PRELIMINAR 0.9 PÚBLICA** | Disponíveis: relatório, sumário, 4 notas de decisão, tabelas DGEG, perguntas difíceis, dados, código e DOI. Janela de comentários aberta até 4 de dezembro | Agentes; divulgação pelo autor |
| 20 nov – 4 dez | Trabalho da versão 1.0 em paralelo com os comentários | Alternativas quase ótimas (2050), matriz de arrependimento completa, faturas por tipo de consumidor, nota sobre interligações e Marrocos, varrimento de renováveis, site de resultados | Agentes |
| Sex 27 nov | Prazo final dos cenários de terceiros para a 1.0 | Até 4 propostas adicionais validadas | Agentes |
| Sex 4 dez | Fecho dos comentários. Segundo congelamento de factos | Todos os comentários com resposta registada | Agentes |
| 7–9 dez | Correções, nova corrida completa com um comando e reprodução limpa | Testes de regressão verdes. Diferenças face à versão preliminar explicadas | Agentes |
| Qui 10 dez | **Ponto de decisão 5:** aprovação da versão 1.0 | Aprovação registada | Autor |
| **Sex 11 dez** | **VERSÃO 1.0 (DOI)** | Relatório final, registo de respostas, kit de comparação DGEG pronto e testado | Agentes; divulgação pelo autor |
| Publicação DGEG + 3 dias úteis | Cenários da DGEG corridos no modelo aberto | Diferenças internas apuradas | Agentes |
| Publicação DGEG + 10 dias úteis | Nota comparativa pública, submetida no debate público (pelo menos 30 dias) | Cada número da DGEG ligado a uma página do documento oficial | Agentes; autor |
| Fev–mar 2027 | Versão 1.1 | Inclui: Monte Carlo sequencial de adequação, clima futuro (projeções do PECD), otimização conjunta Portugal e Espanha, horizonte de 2045, comparação internacional pelo mesmo método, módulo tarifário completo, cenários de terceiros pendentes e submissão de um artigo | Agentes; autor |

**Caminho crítico**

Hídrica e reconstituição do passado → validação (2 nov) → corridas de produção → relatório.

O maior risco de atraso está na hídrica: o PECD só dá afluências semanais nacionais, por isso é preciso calibrá-las com a REN. Por isso arranca no primeiro dia e tem entrega intermédia a 21 de outubro.

**Se a DGEG publicar antes de 20 de novembro**

Nessa altura o protocolo e o modelo validado já são públicos. Os resultados disponíveis saem como nota antecipada, no prazo de 10 dias úteis. O kit de comparação passa à frente das restantes tarefas.

**Ordem de corte, se o calendário apertar**
1. Alternativas quase ótimas para 2035.
2. Varrimento da quota de renováveis.
3. Cenários de terceiros para lá dos 4 primeiros.
4. Matriz de arrependimento, que fica só para 2050.
5. Marrocos, que passa a usar valores da literatura.
6. Faturas, que ficam só para a família de referência.
7. Sensibilidades de 2040.

**Nunca se corta**
- A mesma fiabilidade para todos os portefólios.
- Os vários anos meteorológicos.
- A validação antes dos resultados.
- A dupla verificação dos pressupostos decisivos.
- A reprodução com um comando.

**Feriados a ter em conta na divulgação:** 1 e 8 de dezembro.

## Decisões pendentes do autor

Cada ponto de decisão chega com um memorando de uma página e uma recomendação por omissão. O resumo:

| Até | Decisão | Recomendação |
|---|---|---|
| 9–12 out | **Aprovar o desenho:** as perguntas, os portefólios, os horizontes (2030, 2035, 2040, 2050) e as datas (protocolo a 21-10, versão preliminar a 20-11, versão 1.0 a 11-12) | Aprovar |
| 9–12 out | **Criar credenciais em nome do autor:** Copernicus Climate Data Store; token da ENTSO-E Transparency (pedido por email, pode demorar dias); Zenodo ligado ao ORCID; opcional, token ESIOS da REE. Sem elas, a aquisição de dados fica bloqueada. | Pedir já o token da ENTSO-E, que é o mais lento |
| 9–12 out | **Tornar o repositório público e ativar Discussions e Pages.** Hoje é privado. Ser público é condição do processo aberto e dá acesso gratuito aos servidores do GitHub Actions, que são o meio de cálculo previsto (num repositório privado os minutos gratuitos não chegam). | Tornar público agora, já com o protocolo em proposta, ou o mais tardar a 21-10 |
| 14 out | **Enviar a nota de critérios de qualidade** à DGEG, REN e ERSE, pedindo também o estado do estudo oficial. Decidir se sugere uma revisão independente do estudo oficial (NEA ou JRC). | Enviar e sugerir |
| 20 out | **Licenças:** MIT para o código; CC BY 4.0 para texto, dados derivados e resultados. **Nome e ORCID** para LICENSE e CITATION.cff. | Aprovar |
| 20 out | **Caixa de autoria:** publicação em nome próprio; filiação na WePlanet declarada; trabalho técnico feito por agentes de IA; compromisso de publicar todos os resultados e responder a todos os comentários | Aprovar com o texto que o autor preferir. Declarar a filiação protege mais do que omiti-la |
| 20 out | **Aprovar o protocolo antes do registo com DOI:** as regras de leitura (diferenças abaixo de 2% são indistinguíveis), as tolerâncias da reconstituição do passado, a regra dos anos de projeto e o limiar do anexo de geografia | Aprovar |
| 21 out | **Lista de convidados** a comentar e a propor cenários: APREN, ZERO, academia (IST, FEUP, NOVA, INESC TEC, LNEG), REN, ERSE, modeladores europeus e a WePlanet, com as mesmas regras para todos. Os convites saem em nome do autor. | Convidar todos |
| 23 out | **Pressupostos decisivos e cenários finais,** incluindo o custo de capital base de 5% real igual para todas as tecnologias e a definição de trajetória oficial | Aprovar |
| 28 out, se necessário | **Contingência de computação:** aceitar uma resolução mais grosseira, ou pagar computação com mais memória (cerca de 100 a 300 €) | Resolução mais grosseira. A reprodução por terceiros fica gratuita |
| 2 nov, se necessário | **Reconstituição do passado fora das tolerâncias:** publicar com o desvio explicado, ou adiar | Publicar, se o desvio não mudar as conclusões |
| 18 nov e 10 dez | **Aprovar a versão preliminar e a versão 1.0,** e a forma de divulgação | — |

### Riscos que o autor deve conhecer

- **Uso do GitHub Actions.** As [condições do GitHub](https://docs.github.com/en/site-policy/github-terms/github-terms-for-additional-products-and-features) restringem os servidores do GitHub a atividades ligadas à produção, teste, implantação ou publicação do projeto do repositório. Também proíbem cargas desproporcionadas face ao benefício. Correr os cenários do próprio estudo cabe razoavelmente na primeira condição. Mas 1,5 a 2 dias com 20 tarefas em paralelo é uma carga elevada, por isso é uma zona cinzenta. Há duas alternativas: sessões de agentes em paralelo, cada uma com 4 núcleos e 15 GB, mais lentas; ou uma máquina alugada, a cerca de 50 a 100 € por mês. Recomendação: usar o Actions para os testes e para a reprodução reduzida, e decidir no teste de computação de 28-10 se a matriz completa corre aí.
- **Calendário apertado.** A versão preliminar a 20-11 exige que a hídrica e a reconstituição do passado corram bem à primeira. A ordem de corte protege a versão 1.0, mas não elimina o risco.
- **Verificação.** Todo o trabalho é feito por agentes, por isso os erros têm de ser apanhados por testes, verificação de fontes e verificação independente (ver a secção 8 do protocolo). A revisão por peritos humanos só chega com a versão preliminar.
