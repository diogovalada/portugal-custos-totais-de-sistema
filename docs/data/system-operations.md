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

Os dados existentes permitem backcast, necessidades de reserva, custos agregados e calibração de proxies. Não permitem reconstruir a segurança operacional completa ou atribuir causalidade nodal a cada ação.

## Tratamento no modelo

- co-otimizar reserva com energia, rampas e SOC;
- distinguir capacidade contratada, ativação física, settlement e custo de recursos;
- calibrar necessidades com histórico, mas stressar forecast error e contingências;
- validar períodos críticos a 15/5 minutos;
- reportar shortfalls e valores sombra separadamente;
- não contar pagamentos de balancing como custo social adicional quando os recursos físicos já estão na função objetivo.
