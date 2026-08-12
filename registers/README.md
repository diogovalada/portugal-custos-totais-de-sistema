# Registos do projeto

Este diretório contém metadados de investigação, não dados de entrada do modelo.

- `sources.csv`: catálogo de fontes e condições de acesso/reutilização;
- `assumptions.csv`: hipóteses de modelação, review triggers e fase em que precisam de estar resolvidas;
- `data-gaps.csv`: lacunas, substitutos públicos, ações de acesso e efeito sobre a execução;
- `requests/`: pedidos administrativos, respostas e condições recebidas.

Os IDs são estáveis. Documentos narrativos podem resumir um registo, mas não devem criar uma segunda versão canónica do mesmo parâmetro. Alterações materiais devem preservar o valor anterior no histórico Git e, quando constituam uma decisão, ser anotadas em `docs/decision-log.md`.
