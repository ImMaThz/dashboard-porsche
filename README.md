# Dashboard de Vendas Porsche

## Perguntas de negócio

1. **Quais famílias de modelo geram mais receita?**
   Mostra onde concentrar estoque, marketing e equipe de vendas. Resposta: o 911 gera 33,3% da receita com 23 das 100 vendas.

2. **Em quais estados a receita se concentra?**
   Indica os mercados prioritários e o quanto a operação depende de poucas regiões. Resposta: TX, CA e AZ somam 36,6% da receita.

3. **Como os clientes pagam, e quanto vale cada forma?**
   Ajuda a negociar com bancos e financeiras e a planejar o fluxo de caixa. Resposta: Wire Transfer responde por 31% da receita.


## Tratamento da base

- Mantidas só as colunas sanitizadas. Cliente e vendedor ficaram de fora por não terem versão sanitizada.
- Preço, ano do modelo e quilometragem convertidos de texto para número, colados como valores.
- Validação: 100 registros, sem valores vazios, sem IDs ou linhas duplicadas.
- 24 datas inválidas (ex.: 2024-02-30) mantidas e tratadas como "Data inválida".
- Criada a coluna "Família", derivada da primeira palavra do modelo.

## Ferramenta de IA

Utilizei o Claude como ferramenta de inteligência artificial para auxiliar na análise dos dados e no desenvolvimento da dashboard.

O prompt inicial solicitou a criação de uma dashboard interativa em HTML, CSS e JavaScript, com identidade visual inspirada na Porsche, indicadores de vendas, gráficos e filtros interativos.

Durante o desenvolvimento, foram realizados ajustes nas instruções para melhorar o visual, corrigir funcionalidades, aprimorar os filtros e validar os cálculos apresentados.

A IA foi utilizada como ferramenta de apoio durante o desenvolvimento, enquanto as escolhas e validações do projeto foram acompanhadas ao longo do processo.

Ferramenta utilizada: Claude.

## Dashboard publicada

🔗 **Dashboard publicada:** _[cole aqui o link do GitHub Pages]_

(Final do solicitado pela DIO.)


== Anotações extras. ==

## Objetivo

Permitir que uma diretoria comercial veja, em poucos segundos, **de onde vem a receita**: quais modelos vendem mais valor, em quais estados e por quais formas de pagamento, com a possibilidade de cruzar esses recortes usando filtros.

## Indicadores (KPIs)

Todos são recalculados a cada mudança de filtro:

- Total de vendas
- Receita total
- Ticket médio
- Quantidade de modelos distintos
- Modelo com maior receita

## Filtros

Modelo, Cidade, Estado, Ano da venda e Forma de pagamento. Os filtros podem ser combinados, cada filtro ativo aparece como uma etiqueta removível, e há um botão para limpar todos. O botão **Exportar CSV** baixa as vendas do recorte atual.

## Tratamento dos dados

A planilha original tem 21 colunas: quase todo campo aparece em versão crua e versão sanitizada.

- **Só colunas sanitizadas** foram usadas (data, modelo, ano, preço, quilometragem, pagamento, cidade, estado, status).
- **Preço, ano e quilometragem** foram convertidos de texto para número.
- **Cliente e vendedor** ficaram de fora, porque não têm versão sanitizada.
- **Validação:** 100 registros, nenhum valor vazio, nenhum ID ou linha duplicada, nenhuma cidade associada a dois estados.
- **24 datas inválidas** (ex.: `2024-02-30`, `April 31st, 2024`) estão marcadas como `INVALID` na própria planilha. Os 100 registros foram mantidos; no filtro de ano, essas vendas aparecem como **"Data inválida"**, sem inventar um ano.
- **18 vendas têm data posterior a novembro de 2026** (até outubro de 2027). Como é uma base fictícia de desafio, os registros foram mantidos.
- **Família do modelo:** coluna derivada da primeira palavra do modelo (ex.: "911 Turbo S" → 911), criada porque 40 modelos diferentes em 100 vendas deixariam o gráfico fragmentado.

## Tecnologias

- HTML5, CSS3 e JavaScript puro (sem bibliotecas)
- Gráficos de barras feitos com HTML e CSS, com animação por `transition`
- Layout responsivo com CSS Grid e media queries
- Tudo em um único arquivo `index.html`, com os dados incorporados: funciona sem servidor e sem internet

## Testes realizados

Executados em navegador automatizado (Chrome), com os resultados comparados a cálculos independentes feitos em Python sobre a planilha:

- Receita total (US$ 12.827.800,50), ticket médio (US$ 128.278,01), 40 modelos e modelo líder (911 Dakar) conferidos
- Cada filtro individualmente e combinações de 2 e 3 filtros
- Remoção de filtro pela etiqueta e botão Limpar filtros
- Mensagem de aviso quando a combinação não tem vendas
- Exportação de CSV com o número correto de linhas
- Sem rolagem horizontal em tablet (820 px) e celular (390 px)
- Nenhum erro no console

## Como executar localmente

1. Baixe ou clone este repositório.
2. Dê dois cliques no `index.html`. Ele abre no navegador.


## Capturas de tela

| Computador | Celular |
|---|---|
| ![Computador](screenshots/desktop.png) | ![Celular](screenshots/celular.png) |

---
Desenvolvido por Matheus Candido.
