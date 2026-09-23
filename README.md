# Porsche Sales Lab

Dashboard interativa em HTML desenvolvida a partir da base sanitizada de vendas Porsche do desafio da DIO.

## Objetivo

O projeto transforma uma planilha de 100 vendas em uma dashboard web filtrável, buscando responder perguntas de negócio que vão além de simplesmente contar unidades vendidas.

## Perguntas de negócio escolhidas

1. **Qual método de pagamento concentra mais receita e qual é o ticket médio de cada método?**  
   Escolhi essa pergunta para entender se certos meios de pagamento estão associados a transações de maior valor e para enxergar a composição financeira das vendas.

2. **Quais famílias Porsche geram mais valor?**  
   Em vez de analisar apenas cada versão individual, agrupei os modelos nas famílias 911, 718, Cayenne, Macan, Taycan e Panamera. A comparação usa receita total, número de vendas, ticket médio e mileage médio.

3. **Como a quilometragem se relaciona com o preço de venda?**  
   Essa pergunta busca observar se veículos com maior mileage tendem a aparecer com preço menor. A dashboard usa um scatter plot e calcula a correlação de Pearson dinamicamente para o recorte filtrado. A correlação é exploratória e não implica causalidade.

## Filtros

A dashboard permite filtrar por:

- Modelo Porsche
- Model Year
- State
- Pay Method
- Delivery Status
- Período de venda

Todos os indicadores e gráficos são recalculados automaticamente.

## Indicadores de topo

- Total de vendas
- Receita total
- Ticket médio
- Mileage médio
- Delivery rate (percentual de registros com status exatamente `Delivered`)

## Tratamento da base

A planilha original contém os campos em versão bruta e em versão sanitizada. Para a dashboard, usei apenas os campos sanitizados relevantes:

- `SaleDateSanitized`
- `PorscheModelSanitized`
- `ModelYearSanitized`
- `SalesPriceSanitized`
- `VehicleMileageSanitized`
- `PayMethodSanitized`
- `CitySanitized`
- `StateSanitized`
- `DeliveryStatusSanitized`

Preço, Model Year e mileage foram tratados como valores numéricos na dashboard. Os registros em que `SaleDateSanitized` ficou como `INVALID` permanecem nas análises gerais, mas são excluídos quando o usuário aplica um filtro de período.

## Prompt utilizado

> Crie uma dashboard executiva em um único arquivo HTML, responsiva e sem bibliotecas externas, usando apenas os campos sanitizados de uma planilha de 100 vendas Porsche.  
>  
> Inclua filtros por modelo, Model Year, State, Pay Method, Delivery Status e período.  
>  
> A dashboard deve responder três perguntas de negócio:  
> 1. Qual método de pagamento concentra mais receita e qual é o ticket médio por método?  
> 2. Quais famílias Porsche (911, 718, Cayenne, Macan, Taycan e Panamera) geram mais receita e maior valor por venda?  
> 3. Como a quilometragem se relaciona com o preço de venda? Use um scatter plot e calcule a correlação de Pearson dinamicamente.  
>  
> No topo, exiba total de vendas, receita, ticket médio, mileage médio e delivery rate.  
>  
> Use como referência visual o site oficial da Porsche Brasil: aparência premium, minimalista, contraste preto e branco, bastante espaço em branco e detalhes em vermelho. Não copie o site literalmente.  
>  
> Todos os gráficos, KPIs e insights precisam reagir aos filtros. O arquivo final deve funcionar sozinho no navegador.

## Refinamentos feitos depois do primeiro prompt

A primeira versão seguia perguntas semelhantes ao exemplo da aula, como modelos mais vendidos e Model Year dominante. Depois, o projeto foi refinado para ficar mais autoral:

- o filtro de cidade foi substituído por **State**;
- foi adicionado o filtro de **Delivery Status**;
- a análise de volume por modelo foi trocada por **receita por método de pagamento**;
- foi criada uma análise por **família Porsche**;
- foi adicionado um **scatter plot de mileage × preço** com correlação dinâmica;
- os KPIs foram ajustados para refletir as novas perguntas.

## Ferramenta utilizada

Utilizei o ChatGPT para gerar e refinar a dashboard em HTML a partir da base sanitizada e das perguntas de negócio. O resultado final é um arquivo HTML standalone, sem dependências externas.

## Arquivos do repositório

```text
.
├── index.html
├── README.md
└── porsche_database_sanitized.xlsx
```

## Como executar localmente

Baixe o repositório e abra o arquivo `index.html` em um navegador moderno.

## Dashboard publicada

**GitHub Pages:** (https://victoryumoto19.github.io/porsche-sales-dashboard/)

## Evidências

### Dashboard geral — sem filtros

A visão abaixo mostra a dashboard completa sem nenhum filtro aplicado, considerando as 100 vendas da base.

[Dashboard geral sem filtros](dashboard-geral.png)

### Exemplo de filtro aplicado — State = CA

Neste recorte, o filtro de **State** foi alterado para **CA**. A dashboard recalcula automaticamente os KPIs e todas as análises para considerar apenas as vendas desse estado.

[Dashboard com filtro State CA](dashboard-ca.png)

## Fonte visual

Referência de UI/UX: site oficial da Porsche Brasil.

---

Projeto desenvolvido para o desafio de dashboard HTML da DIO.
