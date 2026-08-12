# Acesso, licenciamento e proveniência

> Estado editorial: working  
> Última verificação jurídica: 2026-08-10  
> Âmbito: LADA, reutilização, pedidos, manifests e regras de publicação  
> Documento canónico para: aquisição legal e rastreabilidade dos dados  
> Rever quando: mudar a lei, licença, API ou resposta de uma entidade

## Acesso administrativo

Base principal: [Lei n.º 26/2016 — LADA, consolidada](https://diariodarepublica.pt/dr/legislacao-consolidada/lei/2016-106603618).

Pontos operacionais identificados:

- qualquer pessoa pode pedir documentos administrativos preexistentes sem demonstrar interesse especial;
- pedir formato eletrónico nativo, dicionário de dados, inventário de tabelas e exports existentes;
- a entidade não tem de criar estudos ou cálculos novos;
- uma extração simples de base preexistente pode ser pedida;
- solicitar comunicação parcial com expurgo apenas do reservado;
- segredo comercial e segurança devem ser fundamentados concretamente;
- acesso e reutilização/publicação são pedidos distintos;
- pedir explicitamente condições de reutilização para investigação e GitHub;
- perante silêncio, recusa ou resposta parcial existe queixa para a CADA.

Prazos anotados, a confirmar antes do envio: resposta normal em 10 dias; extensão excecional fundamentada até dois meses; queixa à CADA normalmente em 20 dias após silêncio/recusa/satisfação parcial. Isto não constitui aconselhamento jurídico.

Precedente útil: [Parecer CADA 188/2021 sobre licenças DGEG](https://www.cada.pt/files/pareceres/2021/188.pdf).

## Estratégia de pedidos

Usar pedidos estreitos e separados:

1. DGEG — cadastro produção/armazenamento, processos e crosswalk de licenças.
2. REN — EIC local, unidade–nó, parâmetros, operação, restrições e curtailment.
3. ERSE — reportes regulatórios, custos, balancing e dados insulares.
4. APA/ARH — títulos, concessões, caudais e autocontrolo hídrico.
5. E-REDES — snapshot estático de planeamento, parâmetros e custos de reforço.
6. EDA/EEM — séries operacionais por sistema insular.

Modelo inicial:

> Ao abrigo da Lei n.º 26/2016, solicita-se acesso aos documentos e dados preexistentes abaixo identificados, preferencialmente no formato eletrónico nativo em que são mantidos, bem como às condições de reutilização para investigação e publicação. Caso existam campos reservados, solicita-se comunicação parcial com expurgo apenas da matéria protegida e fundamentação concreta por campo/documento. Caso não exista a exportação pedida, solicita-se dicionário de dados, inventário de registos e identificação dos relatórios/tabelas preexistentes.

Para informação ambiental, considerar também os artigos 17.º e 18.º. Para produtores privados, pedir primeiro a cópia já na posse da DGEG, ERSE, APA ou operador regulado.

Quando raw data não possam ser publicados, procurar acesso controlado/NDA/clean room e publicar apenas estatísticas autorizadas, parâmetros calibrados, hashes e código. Acesso institucional não transforma automaticamente os inputs em open data.

## Proveniência mínima por fonte

Cada fonte deve registar:

- proprietário, título e URL;
- instante de aquisição e data de validade;
- versão/API;
- licença, atribuição e permissão de redistribuição;
- cobertura, granularidade, timezone e unidades;
- provisional/final e política de revisão;
- checksum do raw pull;
- script e versão da transformação;
- limitações jurídicas e técnicas.

O registo inicial encontra-se em [`registers/sources.csv`](../../registers/sources.csv). Um URL citado num Markdown não substitui o registo nem o manifest do ficheiro efetivamente usado.

## Política de dados do repositório

- `data/raw/`: aquisições redistribuíveis ou instruções para as obter;
- `data/interim/`: transformações técnicas ainda não canónicas;
- `data/processed/`: inputs prontos para o modelo;
- `data/manifests/`: proveniência, hashes, schemas e licenças.

Não guardar credenciais, tokens embebidos ou geometrias classificadas `restricted`. Raw data sem licença ficam fora do Git; publicar script de aquisição, manifest, hash e benchmark sintético/reduzido quando permitido.

## Qualidade e temporalidade

Cada pipeline deve preservar timezone/DST, ano bissexto, unidades, gross/net, HHV/LHV, status provisional/final e revisão da fonte. Alterações políticas, licenças, software, projetos e capacidades devem ser reverificadas na data do run, não apenas na data do documento.

