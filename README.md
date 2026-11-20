# Dashboard de Vendas Porsche

## Perguntas de negócio

1. **Quais famílias de modelo geram mais receita?**
   Mostra onde concentrar estoque, marketing e equipe de vendas. Resposta: o 911 gera 33,3% da receita com 23 das 100 vendas.

2. **Em quais estados a receita se concentra?**
   Indica os mercados prioritários e o quanto a operação depende de poucas regiões. Resposta: TX, CA e AZ somam 36,6% da receita.

3. **Como os clientes pagam, e quanto vale cada forma?**
   Ajuda a negociar com bancos e financeiras e a planejar o fluxo de caixa. Resposta: Wire Transfer responde por 31% da receita.

## Prompt

O prompt completo que gerou a dashboard está em [`PROMPT.md`](PROMPT.md). Ele pedia uma dashboard em um único `index.html`, com visual inspirado na Porsche, filtros por modelo, cidade, estado, ano da venda e pagamento, e KPIs calculados dinamicamente.

O que mudou até a versão final:

- O filtro de ano ganhou a opção "Data inválida", para manter os 100 registros sem inventar datas.
- Os gráficos passaram a agrupar por família do modelo (911, Taycan, Cayenne etc.), porque 40 modelos em 100 vendas deixavam o gráfico fragmentado.
- O gráfico de estados ficou limitado aos 8 maiores, com a soma dos demais.
- Os gráficos foram feitos com HTML, CSS e JavaScript puro, sem Chart.js, para a página funcionar mesmo offline.
- Os KPIs de valor passaram a aparecer resumidos (ex.: US$ 12,83 mi), com o valor exato embaixo, para caber no celular.

## Tratamento da base

- Mantidas só as colunas sanitizadas. Cliente e vendedor ficaram de fora por não terem versão sanitizada.
- Preço, ano do modelo e quilometragem convertidos de texto para número, colados como valores.
- Validação: 100 registros, sem valores vazios, sem IDs ou linhas duplicadas.
- 24 datas inválidas (ex.: 2024-02-30) mantidas e tratadas como "Data inválida".
- Criada a coluna "Família", derivada da primeira palavra do modelo.

## Ferramenta de IA

Usei um agente de IA (Claude) com acesso aos arquivos do projeto, que analisou a planilha, gerou o código e testou a dashboard no navegador. Não usei o ChatGPT com Canvas.

## Dashboard publicada

_[cole aqui o link do GitHub Pages]_
