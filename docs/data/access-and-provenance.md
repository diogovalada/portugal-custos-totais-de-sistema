# Acesso, licenciamento e proveniência

> Estado editorial: working  
> Última verificação jurídica: 2026-08-12
> Âmbito: LADA, reutilização, pedidos, manifests e regras de publicação  
> Documento canónico para: aquisição legal e rastreabilidade dos dados  
> Rever quando: mudar a lei, licença, API ou resposta de uma entidade

## Acesso administrativo

Base principal: [Lei n.º 26/2016 — LADA, consolidada](https://diariodarepublica.pt/dr/legislacao-consolidada/lei/2016-106603618).

Pontos operacionais identificados:

- qualquer pessoa pode pedir documentos administrativos preexistentes sem demonstrar interesse especial;
- pedir formato eletrónico estruturado em que o documento já exista, dicionário de dados, inventário de tabelas e exports existentes;
- a entidade não tem de criar estudos ou cálculos novos;
- uma extração simples pode ser pedida quando não exceda manipulação simples; não há direito a um novo crosswalk, cálculo ou estudo;
- solicitar comunicação parcial com expurgo apenas do reservado;
- segredo comercial e segurança devem ser fundamentados concretamente;
- acesso e reutilização têm regimes diferentes, mas podem ser tratados em secções separadas do mesmo requerimento;
- documentos já publicados online podem ser reutilizados nos termos do artigo 21.º, n.º 1, salvo indicação contrária ou propriedade intelectual evidente; nos restantes casos pedir autorização;
- pedir expressamente redistribuição pública, eventual sublicença aberta e reutilização por terceiros, incluindo comercial; “investigação e GitHub” não chega;
- perante silêncio, recusa ou resposta parcial existe queixa para a CADA e, quando adequado, intimação judicial; o parecer CADA não é por si decisão executória.

Prazos confirmados no snapshot: acesso em 10 dias úteis; extensão excecional e fundamentada, por volume ou complexidade, até ao máximo de dois meses. Reutilização: 10 dias úteis, com uma única extensão de mais 10 dias, notificada e fundamentada. A queixa à CADA é apresentada em 20 dias seguidos após decisão ou expiração do prazo. Isto não constitui aconselhamento jurídico.

Precedente útil: [Parecer CADA 188/2021 sobre licenças DGEG](https://www.cada.pt/files/pareceres/2021/188.pdf).

## Estratégia de pedidos

Usar pedidos estreitos, um tema por requerimento e, quando possível, um snapshot ou ano-piloto:

1. DGEG — cadastro produção/armazenamento, processos e crosswalk de licenças; dirigir a `rai@dgeg.gov.pt` e pedir reencaminhamento se a custódia tiver transitado para a AGE, I.P.
2. REN–Rede Eléctrica Nacional, S.A. — EIC local, unidade–nó, parâmetros, operação, restrições e curtailment.
3. ERSE — reportes regulatórios, custos, balancing e dados insulares.
4. APA — títulos, concessões, caudais e autocontrolo hídrico; as ARH são serviços da APA e o canal formal é `rai@apambiente.pt`.
5. E-REDES — snapshot estático de planeamento, parâmetros e custos de reforço.
6. EDA/EEM — séries operacionais por sistema insular.

Modelo inicial:

> Ao abrigo da Lei n.º 26/2016, solicita-se acesso aos documentos e dados preexistentes abaixo identificados, no formato eletrónico estruturado em que já existam, bem como autorização e condições para reprodução pública, redistribuição e reutilização por terceiros. Não se solicita a criação de novo estudo ou crosswalk. Caso existam campos reservados, solicita-se comunicação parcial com expurgo apenas da matéria protegida e fundamentação concreta por campo/documento. Caso não exista a exportação pedida, solicita-se dicionário de dados, inventário de registos e identificação dos relatórios/tabelas preexistentes.

Para informação ambiental, aplicar o enquadramento dos artigos 3.º, n.º 1, alínea e), 4.º, n.º 4, e 11.º–18.º. As exceções são restritivas, o expurgo é obrigatório quando possível e a informação sobre emissões tem proteção reforçada. Para produtores privados, pedir primeiro a cópia já na posse da DGEG, ERSE, APA ou operador regulado.

Quando raw data não possam ser publicados, procurar acesso controlado/NDA/clean room e publicar apenas estatísticas autorizadas, parâmetros calibrados, hashes e código. O Regulamento (UE) 2022/868 e o [Decreto-Lei n.º 2/2025](https://diariodarepublica.pt/dr/detalhe/decreto-lei/2-2025-904570275) permitem explorar a AMA como ponto único e ambientes seguros para reutilização de certos dados públicos protegidos. Esta via não cria um direito de acesso, não supera segurança nacional/segredos e depende de a entidade poder autorizar a reutilização.

NDA ou ambiente seguro são fallback negocial, não direitos conferidos pela LADA nem condição a oferecer no primeiro pedido.

## Proveniência mínima por input preservado

Cada fonte promovida de descoberta para input de um resultado preservado deve registar:

- proprietário, título e URL;
- instante de aquisição e data de validade;
- versão/API;
- licença, atribuição e permissão de redistribuição;
- cobertura, granularidade, timezone e unidades;
- provisional/final e política de revisão;
- checksum do raw pull;
- script e versão da transformação;
- limitações jurídicas e técnicas.

O catálogo de descoberta encontra-se em [`registers/sources.csv`](../../registers/sources.csv). Um URL citado num Markdown não substitui o manifest do ficheiro efetivamente usado; uma fonte apenas investigada não precisa de manifest completo.

## Política de dados do repositório

- `data/raw/`: aquisições redistribuíveis ou instruções para as obter;
- `data/interim/`: transformações técnicas ainda não canónicas;
- `data/processed/`: inputs prontos para o modelo;
- `data/manifests/`: proveniência, hashes, schemas e licenças.

Não guardar credenciais, tokens embebidos ou geometrias classificadas `restricted`. Raw data sem licença ficam fora do Git; publicar script de aquisição, manifest, hash e benchmark sintético/reduzido quando permitido.

## Qualidade e temporalidade

Cada pipeline deve preservar timezone/DST, ano bissexto, unidades, gross/net, HHV/LHV, status provisional/final e revisão da fonte. Alterações políticas, licenças, software, projetos e capacidades devem ser reverificadas na data do run, não apenas na data do documento.
