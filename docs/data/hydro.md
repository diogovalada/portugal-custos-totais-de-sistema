# Hidrologia e cascatas

> Estado editorial: verified  
> Última verificação factual: 2026-08-12
> Âmbito: centrais, albufeiras, afluências, turbinamento, bombagem e restrições da água em Portugal e Espanha
> Documento canónico para: dados hidroelétricos e fidelidade das cascatas ibéricas
> Rever quando: houver novos exports SNIRH, Tâmega ou títulos harmonizados

## Conclusão

**FACT:** os dados operacionais básicos de muitas grandes cascatas históricas não são inacessíveis. O SNIRH permite exportar séries por estação de afluência, turbinamento, descarga, bombagem, cota e armazenamento, frequentemente diárias desde os anos 1990. Algumas estações incluem parâmetros horários e os exports preservam quality flags.

Fontes:

- [SNIRH monitorização](https://snirh.apambiente.pt/index.php?idMain=2&idItem=1);
- [inventário de albufeiras](https://snirh.apambiente.pt/index.php?idMain=1&idItem=7), incluindo capacidades, níveis, curvas cota-volume-área e relações montante/jusante;
- [boletim de armazenamento](https://snirh.apambiente.pt/index.php?idMain=1&idItem=1.3);
- [centrais hídricas DGEG](https://www.dgeg.gov.pt/pt/servicos-online/informacao-geografica/energia/energia-eletrica/);
- [concessões e usos múltiplos APA](https://apambiente.pt/agua/aproveitamentos-hidraulicos-concessoes);
- [CNPGB](https://cnpgb.apambiente.pt/).

O inventário SNIRH contém 236 albufeiras e expõe relações no mesmo rio e curvas cota-volume, por vezes também área, diretamente extraíveis. As relações não formam um grafo completo: omitem transvases e podem estar desatualizadas. Os PGRH e processos SIAIA acrescentam ligações artificiais e capacidades, incluindo Fronhas→Aguieira e o sistema Cávado–Rabagão–Homem.

O GIS DGEG `Centrais Hídricas` devolvia 134 objetos no corte, dos quais 130 classificados como mini-hídricas e apenas quatro como grandes hídricas. É valioso para pequena produção, licenças, potência e geometria, mas não é censo completo das grandes centrais. O catálogo dados.gov indica CC BY 4.0; deve obter-se confirmação de que essa licença cobre o serviço ArcGIS/WFS e os derivados.

Cobertura confirmada inclui Alto Lindoso, Alto Rabagão, Venda Nova, Aguieira, Alqueva, Pedrógão, Baixo Sabor, Touvedo, Salamonde, Caniçada, Paradela, Pocinho, Valeira, Régua, Carrapatelo, Crestuma, Cabril, Castelo do Bode, Bouçã, Raiva e Fronhas.

As séries contêm lacunas e quality flags. Cobertura longa não significa série completa. A interface é antiga e a licença não está normalizada como CC BY; publicar inicialmente scripts, proveniência e derivados e obter clarificação antes de redistribuição bulk.

## Espanha

**FACT:** a camada espanhola é muito mais forte do que uma representação puramente agregada ENTSO-E:

- o [Boletín Hidrológico Semanal](https://www.miteco.gob.es/es/agua/temas/evaluacion-de-los-recursos-hidricos/boletin-hidrologico.html) mantém histórico por reservatório desde 1988;
- o [Anuario de Aforos CEDEX](https://www.miteco.gob.es/es/agua/temas/evaluacion-de-los-recursos-hidricos/sistema-informacion-anuario-aforos.html) publica séries validadas de nível, reserva, entradas, saídas e evaporação, com cobertura heterogénea;
- os SAIH por confederação cobrem operação recente, mas sem API/schema nacional uniforme;
- a cartografia oficial de aproveitamentos liga `Central`, `Toma` e `Restitución`, permitindo reconstruir uma primeira topologia física.

Continuam ausentes um crosswalk canónico reservatório–central–UGH–nó, curvas completas e atuais, tempos de viagem, rendimentos por queda/carga e regras coordenadas de exploração. A simetria PT–ES é adequada para planeamento por reservatório, não para UC hidráulico fino por grupo.

## Obrigações e concessões

A lista APA de janeiro de 2026 referia 211 contratos correspondentes a 295 aproveitamentos. Títulos anteriores a outubro de 2012 não estão integralmente disponíveis no SILiAmb. PGRH, AIA, declarações ambientais e contratos contêm caudais ecológicos e outros usos, mas não existe ainda uma tabela nacional harmonizada.

As declarações ambientais EMAS da EDP publicam valores contratuais mensais e libertações efetivas de 2022–2024 para várias barragens. A libertação por um órgão dedicado não deve ser confundida com caudal total a jusante quando a obrigação também pode ser satisfeita por turbinamento.

Para Gouvães, Daivões e Alto Tâmega, as fichas CNPGB e o operador corrigem parte da geometria estática, mas volumes úteis, curvas atuais e séries operacionais desde 2022 continuam incompletos. As referências de 20 e 40 GWh usam fronteiras diferentes e não devem ser misturadas.

## Lacunas efetivas

- grafo hidráulico canónico validado, sobretudo derivações, pequenos alimentadores e transvases;
- curvas de rendimento turbina/bomba por queda e carga;
- tailwater e perdas hidráulicas;
- limites por grupo, zonas proibidas, rampas, arranques e tempos mínimos;
- restrições operacionais finas, tempos de propagação e regras multiuso;
- obrigações quantitativas harmonizadas;
- séries detalhadas de Gouvães, Daivões e Alto Tâmega;
- afluência natural/local separada das libertações a montante;
- licença normalizada para redistribuição bulk do SNIRH e de documentos dispersos.

Para planeamento, podem usar-se potência, níveis, curvas de volume, caudais, grafo reconstruído e eficiência calibrada constante/segmentada, com incerteza explícita. Isso não deve ser apresentado como unit commitment hidráulico de operador. A fronteira exata de `GAP-003` é agora: planeamento por reservatório é viável; parametrização hidráulica e operacional por grupo continua crítica.
