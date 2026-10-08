# Custos Totais do Sistema Elétrico em Portugal

Um estudo independente, aberto e totalmente reproduzível sobre quanto custa o sistema elétrico de Portugal continental em 2035, 2040 e 2050. Compara a trajetória oficial com alternativas que dão ao país a mesma segurança de abastecimento e as mesmas emissões.

## Porquê

As decisões de energia dos próximos anos vão marcar o custo da eletricidade durante décadas. Estão em cima da mesa:

- a estratégia de armazenamento;
- os leilões de eólica offshore;
- manter ou não as centrais a gás;
- as interligações;
- o nuclear espanhol, e se vale a pena preparar uma opção nuclear em Portugal.

Comparar o custo de cada central isoladamente (o «LCOE») não chega para estas decisões. O que conta é o custo do **sistema completo** necessário para fornecer eletricidade a todas as horas, incluindo nos anos secos: centrais, armazenamento, redes, interligações e reservas.

A Direção-Geral de Energia e Geologia (DGEG) está a preparar um estudo oficial de custos totais do sistema. Este estudo é independente desse e foi desenhado para:

- ter a máxima qualidade e utilidade;
- correr inteiramente com ferramentas e dados abertos, para que qualquer pessoa o possa verificar e reproduzir com um só comando;
- receber críticas e propostas de cenários de qualquer pessoa, incluindo de quem discorda;
- permitir comparar os seus resultados com os do estudo oficial (mesmos horizontes e mesma decomposição de custos).

## Como funciona, em resumo

- **Modelo:** um modelo de otimização do investimento e da operação do sistema elétrico, feito com ferramentas abertas (PyPSA e o solver HiGHS).
- **Portugal e vizinhos:** Portugal escolhe o seu parque ao menor custo. Espanha e França seguem os seus planos oficiais, mas operam hora a hora em conjunto com Portugal.
- **Clima:** o sistema é dimensionado com vários anos meteorológicos e depois testado em 44 anos reais de vento, sol, temperatura e água, incluindo as piores secas.
- **Segurança:** todos os portefólios cumprem a mesma norma oficial de segurança de abastecimento.
- **Resultados:** saem por quatro pilares: custo para o consumidor, segurança de abastecimento, independência energética e energia limpa.
- **Sem respostas únicas:** não se apresenta um «mix ideal» único. Os resultados são diferenças de custo entre portefólios, limiares («a opção X compensa se custar menos de Y») e intervalos de soluções quase equivalentes.

## Estado

**Fase de desenho.** O protocolo do estudo está em proposta e ainda não foi aprovado nem registado. Não existem resultados.

| Documento | Conteúdo |
|---|---|
| [PROTOCOLO.md](PROTOCOLO.md) | O desenho do estudo: perguntas, métodos, cenários, pressupostos, validação e o que o estudo pode e não pode afirmar |
| [ROTEIRO.md](ROTEIRO.md) | Datas, marcos e decisões pendentes |
| [CONTRIBUIR.md](CONTRIBUIR.md) | Como comentar, contestar um pressuposto ou propor um cenário |
| [docs/decisoes.md](docs/decisoes.md) | Registo das decisões tomadas |
| [docs/frentes-de-trabalho.md](docs/frentes-de-trabalho.md) | Divisão do trabalho entre agentes |
| [docs/avaliacao-e-plano-2026-10-08.md](docs/avaliacao-e-plano-2026-10-08.md) | Avaliação que levou à reorientação do projeto, incluindo observações ao caderno de encargos da DGEG |
| [docs/referencia/](docs/referencia/README.md) | Notas de investigação anteriores: dados, contabilidade e cenários. Material de consulta, não canónico |


## Licença

A definir antes da primeira publicação de resultados. A proposta é MIT para o código e CC BY 4.0 para o texto, os dados derivados e os resultados. Os dados de terceiros mantêm as suas licenças.
