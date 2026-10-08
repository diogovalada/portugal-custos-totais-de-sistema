# Açores e Madeira

> Estado editorial: working  
> Última verificação factual: 2026-08-10  
> Âmbito: dados operacionais e contabilísticos dos sistemas insulares  
> Documento canónico para: cobertura e limites das ilhas  
> Rever quando: EDA/EEM/SREA/DREM publicarem novas séries ou licenças

## Arquitetura física

**FACT:** os Açores têm nove sistemas elétricos independentes. Madeira e Porto Santo são também sistemas independentes. Não podem ser agregados como um único nó síncrono nem misturados com dados REN/ENTSO-E do continente.

## Dados públicos

- [SREA](https://srea.azores.gov.pt/relatorio/energia-eletrica-producao-por-tipo-de-energia-kwh/): produção mensal por fonte e ilha;
- [EDA qualidade de serviço](https://eda.pt/regulacao/qualidade-de-servico/relatorios-de-qualidade-de-servico): relatórios e anexos Excel por ilha;
- [DREM](https://estatistica.madeira.gov.pt/download-now/economica/energia-pt/energia-ee-pt/energia-eletrica/energia-ee-quadros-pt.html): produção e emissão por fonte;
- [EEM qualidade](https://www.eem.pt/pt/conteudo/publicacoes/qualidade-de-servico/relatorios-e-auditorias/relatorios-de-qualidade-de-servico/);
- [inventário de baterias EEM](https://eeminov.eem.pt/cb/);
- contas reguladas EDA com informação por ilha, atividade e central.

Os Excel EDA incluem SAIFI, SAIDI, TIEPI, END, causas e estatísticas semanais de tensão, frequência, flicker, harmónicas, desequilíbrio, cavas e sobretensões. Servem validação agregada de qualidade, não substituem SCADA.

## Lacunas por sistema

- procura horária/15-min;
- despacho por grupo/tecnologia;
- combustível por grupo;
- SOC e carga/descarga de baterias;
- curtailment e reservas;
- indisponibilidades cronológicas;
- frequência e SCADA brutos.

Não usar os ficheiros de 5 minutos `PT-MA` da Electricity Maps como medição operacional: estavam classificados como modelados a partir de agregados. [Referência](https://portal.electricitymaps.com/datasets/PT-MA).

As fontes insulares não apresentavam uma licença open standard uniforme. Até clarificação, publicar scripts/proveniência e pedir autorização antes de redistribuir raw files.

**OPEN:** decidir se as ilhas serão papers próprios ou um módulo posterior. O default corrente é separá-las do estudo continental.

