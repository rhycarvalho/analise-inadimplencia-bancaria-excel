Dashboard de Análise de Inadimplência Bancária

Projeto de portfólio feito em Excel + Power Query, simulando a rotina de um analista de dados numa instituição financeira: pegar uma base suja, tratar do zero e chegar a insights que sustentam decisão de negócio.

Por que esse projeto

Queria treinar tratamento de dados num cenário mais próximo do que se vê no mercado do que os tutoriais costumam mostrar ou seja, uma base cheia de problema de verdade, não só "preencher célula vazia". Escolhi o tema financeiro/bancário porque inadimplência é um assunto que qualquer analista de risco ou crédito vai encontrar cedo ou tarde.

o que aparece em exportações reais de sistema bancário:

datas em 4 formatos diferentes na mesma coluna (31/01/2025, 2025-01-31, 31-Jan-2025, 01/31/2025)
valores como texto, misturando vírgula e ponto decimal (R$ 1.115,23, 449.94, 80,23)
sinal negativo indevido em transações
categorias e status escritos de formas diferentes (Pago, PAGO, Quitado — mesma coisa)
duplicatas exatas e linhas 100% vazias (lixo de exportação)
campos nulos espalhados
Como tratei os dados

Tudo feito no Editor do Power Query, com cada transformação documentada nas etapas aplicadas.

Dois problemas valem menção porque não são óbvios de primeira:

Bug de localidade no Number.FromText — ao converter texto pra número sem especificar a cultura, o Power Query usa a configuração regional do Windows. Como meu Excel está em pt-BR, ele interpretava 306.87 como se o ponto fosse separador de milhar, virando 30687. Resolvido forçando Number.FromText(texto, "en-US") depois de padronizar o texto pro formato americano.


Estrutura do arquivo
Dados_Tratados — base limpa, como Tabela do Excel
Analises — as 4 tabelas acima, com fórmula (nada de número fixo — se o dado mudar, recalcula)
Dashboard — KPIs e gráficos

Ferramentas

Excel (Power Query, tabelas dinâmicas, fórmulas condicionais)
