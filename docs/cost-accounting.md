# Contabilidade dos custos do sistema

> Estado editorial: working  
> Última verificação: 2026-08-11  
> Âmbito: fronteira económica, função objetivo, ledgers e prevenção de dupla contagem  
> Documento canónico para: significado de “total system cost” neste projeto  
> Rever quando: mudar a fronteira, a métrica de bem-estar ou o tratamento de externalidades

## Princípio central

**DECISION D-COST-001:** o resultado económico principal adota a perspetiva de planeador social e contabiliza recursos reais e danos externos. Preços, tarifas, impostos, subsídios, receitas de mercado, pagamentos de capacidade, pagamentos de reservas e rendas de congestionamento são normalmente transferências dentro da fronteira, não custos de recursos adicionais.

O estudo comparará o custo incremental ou contrafactual de fornecer o mesmo serviço com o mesmo padrão de fiabilidade e a mesma restrição de emissões. System LCOE e VALCOE podem ser resultados secundários, mas não são propriedades intrínsecas de uma tecnologia.

## Três contas separadas

1. **Recursos económicos:** investimento, FOM, VOM, combustíveis, redes, armazenamento, flexibilidade, perdas, adequação, comércio externo quando fora da fronteira, desmantelamento e outros recursos reais.
2. **Incidência financeira:** preços grossistas, tarifas, proveitos permitidos, impostos, subsídios, CfD/PPA, capacidade, rendas de congestionamento, margens e faturas por grupo.
3. **Externalidades:** clima, poluição atmosférica, acidentes, água, solo, biodiversidade, ruído, segurança de abastecimento e impactos não mercantis.

Os três ledgers podem ser apresentados lado a lado, mas não somados sem uma regra explícita.

## Formulação económica mínima

Para procura ou serviço fixo:

```text
NPV esperado = investimento descontado
             + FOM + rede + desmantelamento
             - valor residual
             + custo operacional esperado por cenário
```

O custo operacional inclui combustível e eficiência, VOM, arranque, no-load, ramping/cycling, recursos físicos de reservas, degradação e perdas de armazenamento, flexibilidade/desutilidade, ENS × VOLL, comércio externo aplicável e externalidades.

Para procura elástica, o problema deve maximizar welfare ou minimizar recursos e danos externos menos a utilidade dos serviços energéticos.

Quando se usa uma anuidade:

```text
CRF(r,L) = r(1+r)^L / ((1+r)^L - 1)
custo anual = CAPEX × CRF + FOM
```

Usar euros reais de um ano-base e taxas reais compatíveis. As âncoras iniciais são o [guia de appraisal económico do EIB](https://www.eib.org/files/publications/20220169_economic_appraisal_of_investment_projects_en.pdf) e a [4.ª CBA Guideline da ENTSO-E](https://eepublicdownloads.blob.core.windows.net/public-cdn-container/clean-documents/news/2024/entso-e_4th_CBA_Guideline_240409.pdf).

## Regras contra dupla contagem

Não somar simultaneamente:

- CAPEX e a sua anuidade;
- anuidade integral e valor residual incompatível;
- CAPEX/OPEX de rede e tarifas que os recuperam;
- custos físicos de despacho e pagamentos grossistas;
- dano social do carbono e pagamentos ETS que representam o mesmo efeito;
- custos físicos de reservas e pagamentos de capacidade/ativação;
- investimento de adequação e pagamentos do capacity market;
- perdas de armazenamento como recurso físico e novamente ao preço grossista;
- perdas de rede como geração adicional e energia comprada;
- incentivo de demand response e a mesma desutilidade do consumidor;
- ligação cobrada ao produtor e novamente contabilizada na rede;
- emprego, salários ou valor acrescentado como benefício quando os inputs já são custos;
- receitas, lucros ou congestion rents subtraídos ao custo social;
- custos espanhóis endógenos e pagamentos portugueses de importação pela mesma energia.

## Tratamentos específicos

- **CAPEX:** usar NPV multiperíodo quando os fluxos ocorrem ou anuidade equivalente; incluir construção, atraso, substituições e valor residual de forma coerente.
- **Desconto:** aplicar uma taxa social real comum ao ledger de recursos. WACC privado e contratos pertencem ao ledger financeiro, salvo quando representam uma restrição real.
- **Reservas:** co-otimizar headroom, footroom, rampas, SOC e resposta. Contar combustível, arranques, desgaste, perdas e equipamento; pagamentos são normalmente transferências.
- **Curtailment:** reportar MWh e percentagem. A compensação não é automaticamente custo de recursos; o valor da energia perdida emerge do contrafactual.
- **Armazenamento:** separar EUR/MW e EUR/MWh e representar eficiência, auxiliares, autodescarga, SOC e degradação. Não duplicar degradação no lifetime/FOM e por ciclo.
- **Adequação:** valorar ENS com VOLL e reportar LOLE/EENS/LOLH, duração e profundidade. Não somar pagamentos de capacidade quando o investimento já é endógeno.
- **Procura flexível:** distinguir deslocamento, redução voluntária com desutilidade/rebound e corte involuntário com VOLL.
- **Comércio:** numa fronteira ibérica, pagamentos PT–ES e rendas são transferências. Numa fronteira portuguesa, valorar importações ao custo de oportunidade sem somar os custos espanhóis.
- **Ativos existentes:** CAPEX, dívida e subsídios passados são sunk para decisões futuras. Contar custos evitáveis, refurbishment, encerramento e desmantelamento incrementais; book value pertence à conta financeira.
- **Carbono:** usar cap, preço de política ou dano social com rótulo explícito; não contar ETS e o mesmo dano.
- **Sector coupling:** contabilizar conversores, storage e redes de cada carrier e cobrar combustíveis/externalidades uma vez na origem.
- **Nuclear backend:** distinguir custo físico incremental de waste/decommissioning da levy ou fundo financeiro.
- **Denominador:** EUR/MWh usa eletricidade final entregue, excluindo carga de armazenamento e exportações, salvo definição explícita diferente.

Cada linha do ledger deve ser classificada como quantidade endógena × custo unitário exógeno, custo unitário endógeno, valor sombra, custo fixo exógeno ou efeito omitido/não monetizado. Valores sombra são resultados e não parcelas adicionais da função objetivo.

## Outputs mínimos

- NPV, custo anual equivalente e diferença para o contrafactual;
- custo forward para decisão e conta integral do sistema existente, separadamente;
- custo médio por MWh final entregue;
- cost stack de geração, redes, armazenamento, flexibilidade, adequação, comércio, desmantelamento e externalidades;
- ledger financeiro/distributivo separado;
- capacidade e produção por tecnologia/nó;
- comércio, congestionamento, perdas e curtailment;
- ciclos e degradação de armazenamento;
- reservas, ativações e shortfalls;
- LOLE, EENS, eventos extremos e intervalos de confiança;
- emissões diretas/lifecycle e impactos não monetizados.

