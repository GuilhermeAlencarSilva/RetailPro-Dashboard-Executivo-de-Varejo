🛍️ RetailPro – Dashboard Executivo de Varejo (Power BI + Python + Figma)

📆 Período analisado: 2023–2024
👤 Autor: [Seu Nome] – Analista de Dados Sênior
🧰 Ferramentas: Python, Power BI, Figma, DAX
📈 Modelo: Star Schema (Fato + 4 Dimensões)
🎨 Tema: Claro com detalhes em roxo e lilás

🧭 1. Contexto e Objetivo do Projeto

O RetailPro é um projeto completo de inteligência de negócios (BI) voltado ao setor varejista nacional, com o objetivo de transformar dados de vendas, operações e canais em insights acionáveis para executivos e gestores.

O painel foi desenvolvido para suporte à tomada de decisão estratégica, permitindo responder perguntas como:

Quais categorias e produtos geram maior rentabilidade?

Como estão os prazos, devoluções e satisfação dos clientes?

Quais canais têm melhor desempenho e ticket médio?

Onde estão as oportunidades de otimização logística e comercial?

O projeto foi desenvolvido seguindo o método DEASA (Definição, Estruturação, Análise, Solução e Apresentação), garantindo uma abordagem sistemática, exploratória e orientada a valor.

🧩 2. Estrutura Técnica do Projeto
🔹 Modelagem – Star Schema

A base de dados foi modelada em formato estrela, com uma tabela fato central e quatro dimensões:

| Tabela        | Tipo     | Descrição                                      |
| ------------- | -------- | ---------------------------------------------- |
| `Fato_Vendas` | Fato     | Contém 50.000 registros de vendas (2023–2024). |
| `Dim_Produto` | Dimensão | Nome, categoria, marca e custo unitário.       |
| `Dim_Regiao`  | Dimensão | Estado, região e cidade.                       |
| `Dim_Tempo`   | Dimensão | Data, mês, trimestre e ano.                    |
| `Dim_Loja`    | Dimensão | Loja física ou e-commerce, canal de venda.     |

Cada dimensão possui chave substituta (ID_) e se relaciona com a fato via relacionamento one-to-many.

🔹 Variáveis e Medidas criadas

| Tipo        | Nome                     | Fórmula DAX                                | Finalidade                    |
| ----------- | ------------------------ | ------------------------------------------ | ----------------------------- |
| Métrica     | `Receita Total`          | `SUM(Fato_Vendas[Receita])`                | Total de vendas em R$.        |
| Métrica     | `Lucro Total`            | `SUM(Fato_Vendas[Lucro])`                  | Lucro bruto por período.      |
| Métrica     | `Margem Média (%)`       | `AVERAGE(Fato_Vendas[Margem_pct])`         | Rentabilidade média.          |
| Métrica     | `Ticket Médio`           | `AVERAGE(Fato_Vendas[Ticket_Medio])`       | Valor médio gasto por compra. |
| Operacional | `Prazo Médio de Entrega` | `AVERAGE(Fato_Vendas[Prazo_Entrega_Dias])` | Tempo médio de entrega.       |
| Operacional | `% Devoluções Média`     | `AVERAGE(Fato_Vendas[Devolucoes_pct])`     | Taxa média de devoluções.     |
| Operacional | `Satisfação Média`       | `AVERAGE(Fato_Vendas[Satisfacao])`         | Nota média de experiência.    |
| Operacional | `Custo Logístico Médio`  | `AVERAGE(Fato_Vendas[Custo_Logistica])`    | Custo médio por entrega.      |

🧮 3. Geração dos Dados com Python

Os dados foram simulados de forma coerente usando Pandas e NumPy, com distribuição realista de:

Vendas por região e canal;

Sazonalidade (picos em novembro e dezembro);

Relação entre descontos, devoluções e satisfação;

Custos logísticos mais altos em e-commerce.

O script foi projetado para gerar 50.000 registros entre 2023 e 2024, permitindo replicabilidade e coerência estatística.

📊 4. Medidas Dax



🧠 5. Análise Exploratória e Insights

Antes da construção dos dashboards, foi realizada uma análise exploratória no Power BI, com foco em identificar padrões e outliers.

📊 Principais Achados

| Tema       | Insight                                                  | Interpretação                                         |
| ---------- | -------------------------------------------------------- | ----------------------------------------------------- |
| Receita    | O E-commerce representa 58% da receita total.            | Canal com maior alcance e ticket médio.               |
| Margem     | Margem média de 24%, com forte variação por categoria.   | Cosméticos e Moda são os mais rentáveis.              |
| Devoluções | Região Nordeste tem as maiores taxas de devolução (12%). | Prazos de entrega maiores e mais reclamações.         |
| Satisfação | Média geral: 4,2/5.                                      | Impactada negativamente por atraso e custo logístico. |
| Custos     | Custo logístico médio: R$ 22,10.                         | 35% maior em e-commerce.                              |

💡 Conclusão geral:
Margem e satisfação têm relação inversa com devoluções e prazos — a eficiência operacional impacta diretamente a experiência do cliente e o lucro.

📊 6. Estrutura dos Dashboards
🟣 Página 1 – Resumo Executivo (CEO View)

KPIs: Receita, Lucro, Margem, Ticket Médio.

Gráfico: Receita × Lucro (coluna + linha).

Visuais complementares:

Top 5 produtos por receita (barras horizontais).

Ranking de campanhas por margem.

Insight Box: texto automático destacando alertas (ROI negativo, margem baixa).

🎯 Público: diretoria e C-level (visão de 30 segundos).

🟣 Página 2 – Produtos & Categorias

KPIs: Receita, Lucro, Margem, Quantidade Vendida.

Top N Produtos (barras horizontais) com seletor interativo.

Gráfico de Rosca: participação da receita por categoria.

Scatter: correlação Margem × Receita × Lucro.

📈 Insight: produtos de alto faturamento nem sempre possuem maior margem — importante balancear volume e rentabilidade.

🟣 Página 3 – Operações & Logística

KPIs: Prazo, Devoluções, Satisfação, Custo Logístico.

Gráfico de Linhas: % Devoluções por Região e Mês.

Scatter: Prazo × Devoluções × Satisfação (identifica gargalos).

Tabela: detalhamento por região e categoria.

Barras: % Devoluções por Categoria.

📦 Insight: Prazos longos e altos descontos aumentam devoluções em até 20%.

🟣 Página 4 – Clientes & Canais

KPIs: Receita, Lucro, Ticket Médio, Quantidade Média por Pedido.

Colunas: Ticket Médio por Canal (Físico × E-commerce).

Rosca: % Receita por Canal.

Barras Horizontais: Top Categorias por Ticket Médio.

Scatter: Ticket × Margem × Canal.

🛒 Insight: o E-commerce tem ticket 35% maior, mas margem 8 p.p. menor.

🎨 7. Design & UX (Figma)

O layout foi criado no Figma, respeitando princípios de design de dashboards:

Tema claro e limpo, com contraste de roxo/lilás (#6A1B9A e #E1BEE7);

Hierarquia visual linear (de cima para baixo);

Ícones contextuais (📈 💰 📦 etc.) reforçando leitura visual;

Slicers horizontais padronizados para consistência de navegação.

💬 Resultado: um dashboard que equilibra clareza executiva e profundidade analítica.

🚀 8. Conclusões e Recomendações Estratégicas
📈 Comerciais

Expandir presença digital — E-commerce é o principal gerador de receita.

Reavaliar política de descontos em regiões com devoluções altas.

Incentivar mix de produtos com maior margem (Beleza, Moda).

🚚 Operacionais

Investir em logística para reduzir prazos médios (meta: ≤5 dias).

Reduzir custo logístico unitário via agrupamento de entregas.

Integrar métricas de satisfação à operação (NPS interno).

🎯 Gerenciais

Implementar alertas automáticos de ROI negativo e devoluções acima da média.

Consolidar um painel mobile para gestores regionais.

Manter revisão trimestral das métricas de eficiência.

| Etapa            | Ferramenta             | Uso                            |
| ---------------- | ---------------------- | ------------------------------ |
| Geração de Dados | Python (Pandas, NumPy) | Simulação coerente de dados.   |
| Modelagem        | Power BI Data Model    | Estrutura em estrela.          |
| Visualização     | Power BI               | Dashboards interativos e DAX.  |
| Design           | Figma                  | Prototipagem de layout visual. |
| Documentação     | Markdown               | GitHub, Medium, LinkedIn.      |

🏁 9. Valor do Projeto

O RetailPro demonstra domínio de todo o ciclo analítico:

Modelagem de dados coerente;

Construção de indicadores estratégicos;

Design orientado à decisão;

Comunicação executiva e storytelling visual.

Este projeto mostra como um analista de dados sênior transforma dados brutos em histórias de negócio poderosas — um case completo de Data-Driven Decision Making.

📎 10. Links e Contatos

💡 Medium: [seu artigo completo]

💼 LinkedIn: 
