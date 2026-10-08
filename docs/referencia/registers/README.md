# Registos do projeto

Este diretório contém metadados de investigação, não dados de entrada do modelo.

- `sources.csv`: catálogo de descoberta da investigação; não substitui o manifest e não tem de ser normalizado integralmente antes de P0;
- `assumptions.csv`: backlog de hipóteses e review triggers; valores efetivamente executados devem migrar para configurações machine-readable e não ser copiados manualmente entre ambos;
- `data-gaps.csv`: lacunas, substitutos públicos, ações de acesso e efeito sobre a execução;
- `requests/`: pedidos administrativos, respostas e condições recebidas.

Os IDs são estáveis. O registo não é uma checklist que tenha de ser totalmente resolvida antes de prototipar: `needed_by_phase` limita o primeiro claim que precisa do parâmetro. Quando um dataset entra num resultado preservado, o respetivo manifest passa a ser canónico para versão, hash e licença efetivamente usados. Documentos narrativos podem resumir um registo, mas não devem criar uma segunda versão canónica. Alterações materiais ficam no histórico Git e, quando mudem pergunta, headline ou checkpoint, entram em `../decision-log.md`.
