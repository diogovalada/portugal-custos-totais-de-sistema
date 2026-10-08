# Operações, balancing e redispatch

> Estado editorial: working  
> Última verificação factual: 2026-08-12  
> Âmbito: reservas, ativações, desvios, redispatch, congestionamento e curtailment  
> Documento canónico para: dados de operação de mercado e sistema  
> Rever quando: mudar o desenho de balancing ou a interface SIME

## Camada pública

**FACT:** a maior parte dos dados necessários ao despacho agregado e à contabilidade de balancing encontra-se no [SIME da REN](https://mercado.ren.pt/PT/Electr/InfoMercado/InfSistema), frequentemente a 15 minutos.

Inclui:

- ofertas, necessidades, contratação, atribuições e preços aFRR;
- ofertas, necessidades, ativações, energia e preços mFRR;
- histórico RR/TERRE;
- desvios e valorização por ISP/BRP;
- PDBF, PDVD, PHF e mFRR-R;
- energia e custo de restrições;
- motivos mensais de restrições.

Resumo público de restrições: [energia e valorização](https://mercado.ren.pt/PT/Electr/InfoMercado/InfSistema/Restricoes/Paginas/Total-Energia-Valorizacao.aspx).

**FACT:** FCR é obrigatório e não remunerado no desenho identificado no [MPGGS vigente no snapshot](https://www.erse.pt/media/q10chfti/mpggs_articulado-250911.pdf); não há uma série portuguesa de preço de contratação comparável a aFRR/mFRR. A REN e a REE desligaram-se de RR/TERRE em 30-12-2025, a operação terminou nesse dia e o projeto foi encerrado no fim de março de 2026, segundo a [ENTSO-E](https://www.entsoe.eu/network_codes/eb/terre/). O histórico não deve ser projetado mecanicamente. A ENTSO-E fornece uma camada normalizada, cuja completude portuguesa deve ser testada item a item.

O ESIOS espanhol oferece uma camada comparável para programas, restrições técnicas, banda/energia de reservas, desvios, indisponibilidades e curtailment renovável nodal. Exige chave para a API e não foi localizada licença aberta geral. Os itens ENTSO-E explicitamente publicados sob CC BY 4.0 devem ser preferidos quando a cobertura for suficiente.

## Requisitos futuros de reserva e flexibilidade

**FACT:** as regras históricas não podem ser projetadas como uma percentagem fixa única:

- FCR é dimensionada e partilhada ao nível da Europa Continental;
- aFRR e mFRR têm tempos e critérios próprios;
- Portugal e Espanha estão a evoluir para metodologias conjuntas de FRR baseadas em erros de previsão e contingências;
- contingência, erro de previsão e flexibilidade de curto/longo prazo não devem ser somados sem verificar sobreposição.

O [primeiro relatório FNAM da ERSE](https://www.erse.pt/media/aehfahwe/relat%C3%B3rio-an%C3%A1lise-de-necessidades-de-flexibilidade-em-portugal.pdf), publicado em 24-07-2026, estima máximos de flexibilidade de curto prazo da ordem de 2,15–2,22 GW a subir e 2,76–2,84 GW a descer em 2030, aumentando em 2035. O próprio relatório trata estes valores como majorantes: pós-processou um despacho determinístico e não quantificou necessidades não satisfeitas por novo Monte Carlo/redispatch.

Não se devem transformar estes máximos numa constraint aditiva. O modelo separa requisito de contingência, quantil de forecast error e disponibilidade/deliverability; inércia, FFR e strength pertencem a screens próprios.

## Proxy de restrições/curtailment

**PROXY:** enquanto não existir uma série portuguesa canónica de curtailment, o backcast usa a energia e os motivos de restrições do SIME apenas como `restriction_proxy`. Uma observação só pode ser aproximada a curtailment renovável quando a documentação permita associá-la explicitamente a redução de produção renovável por restrição técnica; os restantes volumes ficam como redispatch/restrição sem reclassificação.

Esta proxy serve para testar ordem de grandeza e cronologia agregada. Não sustenta atribuição causal por tecnologia, nó, ativo ou compensação e não é equivalente à publicação espanhola de curtailment renovável nodal no ESIOS.

## Lacunas

- AGC/aFRR de segundos;
- ativação FCR física por unidade;
- liquidações e faturas reservadas;
- elemento congestionado, contingência e ação corretiva de cada redispatch;
- custo físico/oportunidade distinto do preço liquidado;
- curtailment renovável canónico com causa, tecnologia, localização e compensação;
- licença inequívoca para redistribuição massiva do SIME.
- metodologia final conjunta de FRR e séries futuras de erro de previsão;
- FRCE/ACE/AGC de alta frequência e deliverability física por recurso.

Os dados existentes permitem backcast, necessidades de reserva, custos agregados e calibração de proxies. Não permitem reconstruir a segurança operacional completa ou atribuir causalidade nodal a cada ação.

## Tratamento no modelo

- co-otimizar reserva com energia, rampas e SOC;
- distinguir capacidade contratada, ativação física, settlement e custo de recursos;
- calibrar necessidades com histórico, mas stressar forecast error e contingências;
- validar períodos críticos a 15/5 minutos;
- reportar shortfalls e valores sombra separadamente;
- não contar pagamentos de balancing como custo social adicional quando os recursos físicos já estão na função objetivo.

`A-RESERVE-REQ-001` guarda o tratamento provisório e `GAP-017` a evidência que falta. Requisitos futuros só passam a constraints após evitar explicitamente dupla contagem entre contingência, forecast error e envelopes FNAM.
