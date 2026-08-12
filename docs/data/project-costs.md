# Custos realizados de projetos

> Estado editorial: working  
> Última verificação factual: 2026-08-12
> Âmbito: outturn, contas reguladas e reconstrução de projetos privados  
> Documento canónico para: evidência empírica de custos de ativos  
> Rever quando: houver novas contas, auditorias ou informação de conclusão

## Conclusão

**FACT:** existe informação real relevante para redes reguladas e alguns projetos públicos/financiados. Não existe um registo público completo do custo final all-in por ativo, sobretudo na geração privada.

Um ledger histórico agregado é, ainda assim, viável para 2022–2024 se cada entrada distinguir `observed`, `regulated_outturn`, `cash_or_settlement`, `allowed_revenue`, `projected` e `modelled_estimate`. Rede regulada pode ser tratada com boa evidência; combustível/CO2 e custos operacionais privados exigem proxies e intervalos. O gate G2 não deve exigir que todos os custos privados sejam cash outturn observado.

Fontes principais:

- [PDIRD-E, incluindo valores reais 2020–2023](https://www.erse.pt/media/yxpjdvp2/proposta-pdird-e-2024-anexo-c3-a-anexo-i.pdf);
- [contas reguladas reais E-REDES 2024](https://www.e-redes.pt/sites/eredes/files/2025-11/Relat%C3%B3rio%20Contas%20Reguladas%20Reais%20E-REDES%202024%20-%20Resumo.pdf);
- relatórios e contas REN;
- [parâmetros regulatórios ERSE](https://www.erse.pt/media/dzdijgko/par%C3%A2metros-2026-2029.pdf);
- [BASE.gov](https://www.base.gov.pt/Base4/pt/documentacao/formas-de-obter-dados-sobre-os-contratos-publicos/);
- [contas reguladas EDA](https://www.eda.pt/regulacao/contas-reguladas);
- Portal Mais Transparência e Tribunal de Contas.

Não confundir investimento previsto, subsídio aprovado/executado, incentivo pago, proveito permitido, valor de adjudicação e custo final all-in.

O relatório BASE de 2024 indicava informação de conclusão/preço efetivo em apenas cerca de 17% das empreitadas do corte analisado. [Relatório BASE](https://www.base.gov.pt/Base4/media/2oeld2oi/relat%C3%B3rio-anual-2024-contrata%C3%A7%C3%A3o-p%C3%BAblica.pdf). Uma adjudicação também não inclui necessariamente claims, owner’s costs e financiamento.

## Lacunas privadas

- EPC por pacote;
- terreno, desenvolvimento e licenciamento;
- ligação e reforços;
- contingência e claims;
- owner’s costs;
- juros capitalizados;
- manutenção pesada;
- reconciliação final após litígio.

## Reconstrução possível

```text
registo da central → NIPC/SPV → IES/contas → ativos em curso e adições
→ dívida/juros/depreciação/OPEX → CMVM/financiamento/BASE/SIAIA/promotor
```

Esta rota produz uma estimativa parcial e intervalos, não uma reconciliação auditada por ativo. Custos históricos devem ainda ser distinguidos de custos forward relevantes à decisão, conforme [contabilidade](../cost-accounting.md).

## Custos forward

A hierarquia provisória de `A-TECHCOST-001` é por linha, não por catálogo inteiro:

1. outturn ou orçamento de projeto ibérico comparável;
2. matriz europeia EC SWD(2026) 616 para 2030/2040/2050;
3. TYNDP para planeamento/interligações;
4. `technology-data` v0.15.0 com overrides explícitos;
5. DEA, IRENA, IEA, JRC e literatura para detalhe e bounds.

Não misturar overnight com all-in/financiado, €/kW com €/kWh, potência input com output ou custos que incluem/excluem ligação. `technology-data` contém alternativas incompatíveis para baterias, PHS e H2; nuclear é referência norte-americana e offshore exclui ligação. Bounds de catálogos são narrativas tecnológicas, não P10/P50/P90 automáticos.
