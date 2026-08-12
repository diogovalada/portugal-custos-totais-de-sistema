# Desenho, âmbito e governação do projeto

> Estado editorial: working  
> Última verificação: 2026-08-12  
> Âmbito: pergunta de investigação, fronteiras, viabilidade, fases e política de alegações  
> Documento canónico para: propósito e contrato científico do estudo  
> Rever quando: a fronteira ou ambição do estudo mudar

## Pergunta central

Quais os custos económicos, requisitos de investimento, riscos de adequação e principais impactos externos de portefólios alternativos capazes de fornecer o mesmo serviço elétrico a Portugal, no contexto físico e institucional ibérico, sob restrições comuns de fiabilidade e emissões?

O objeto comparado é o portefólio completo, não o LCOE isolado de uma tecnologia. O estudo deve representar, conforme a fase, geração, redes, armazenamento, flexibilidade, reservas, comércio, hidrologia, indisponibilidades e procura não servida.

## Objetivos

- produzir um estudo transparente, versionado e reproduzível;
- separar custo de recursos, incidência financeira e externalidades;
- comparar portefólios sob a mesma procura, fiabilidade e limite de emissões;
- tratar explicitamente Espanha, interligações e restrição da ligação ibérica à Europa;
- preservar cronologia e correlação de vento, solar, procura, hidro e secas;
- expor pressupostos, lacunas, intervalos e alternativas quase ótimas;
- permitir auditoria independente dos dados, código e alegações.

## Fronteira provisória

**ASSUMPTION A-SCOPE-001:** o primeiro paper será electricity-only e focado no bulk system continental PT+ES. França será representada como nó endógeno simplificado ou condição de fronteira limitada; Marrocos será incluído se material. Açores e Madeira serão analisados separadamente.

Esta escolha ainda precisa de adoção formal. Uma fronteira apenas portuguesa exige valorar importações ao custo de oportunidade na fronteira. Uma fronteira ibérica torna pagamentos PT–ES e rendas de congestionamento transferências internas.

## O que o estudo pode e não pode alegar

É defensável produzir um benchmark de planeamento/adequação e dizer:

- “dentro da fronteira e hipóteses declaradas, o cenário A apresenta custo de recursos estimado X–Y”;
- “o resultado é ou não robusto às sensibilidades testadas”;
- “o resultado é um benchmark cost-optimal, não uma previsão”;
- “a incidência portuguesa difere do custo ibérico devido a comércio e alocação regulatória”.

Não é defensável, sem evidência adicional:

- anunciar “o verdadeiro custo total” de uma tecnologia;
- atribuir todo o custo de backup ou rede a uma tecnologia sem contrafactual;
- inferir faturas diretamente do custo de recursos;
- tratar uma solução do modelo como prova da política ótima;
- alegar segurança dinâmica a partir de expansão linear;
- alegar fiabilidade com um só ano meteorológico;
- chamar integralmente reproduzível a um resultado dependente de inputs essenciais indisponíveis a terceiros.

Distribuição detalhada, estabilidade dinâmica e efeitos não monetizados devem ser descritos como módulos, proxies ou limitações, nunca implicitamente incorporados.

## Viabilidade independente

| Ambição | Avaliação |
|---|---|
| Ledger histórico português | Alta; adequado como MVP autónomo |
| Expansão elétrica ibérica | Média-alta; credível para investigação independente |
| Adequação e módulos de rede mais profundos | Média; requer revisão especializada |
| Sistema ibérico totalmente sector-coupled | Baixa-média; extensão posterior de grande dimensão |
| Custo economy-wide definitivo | Não é projeto de uma só pessoa |

Os envelopes de esforço, compute e orçamento pertencem ao [plano de execução](execution-plan.md), para que não existam estimativas concorrentes.

## Princípio de execução

A investigação deve avançar por gates verificáveis, começando por um protocolo e um ledger histórico antes de permitir expansão endógena ou interpretação política. O ledger é um MVP autónomo e deve conservar valor mesmo que as extensões posteriores sejam adiadas.

A sequência, as dependências, os entregáveis e os critérios stop/go são canónicos apenas em [execution-plan.md](execution-plan.md).

## Governação

**DECISION D-GOV-001:** publicar um protocolo antes dos cenários politicamente sensíveis.

Artefactos de governação obrigatórios:

- registo de pressupostos e ontologia de custos;
- registo de decisões e alterações;
- conflitos de interesse, financiamento e declaração de utilização de AI;
- revisão de método e código antes da interpretação política;
- auditoria específica de dados e regulação MIBEL;
- revisão adversarial das alegações após o draft;
- reprodução independente numa máquina limpa;
- preprint, período público de comentários e matriz de respostas;
- releases imutáveis com DOI.

Perfis externos prioritários: operação/adequação ibérica, regulação e tarifas, estatística e incerteza, clima/hidro, research software/licenciamento e externalidades quando monetizadas.

AI pode apoiar ETL, testes, documentação, cenários e revisão de código. A responsabilidade por decisões científicas, interpretação institucional e alegações permanece humana e deve ser identificável.
