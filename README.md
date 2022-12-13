Projeto desenvolvido como atividade do curso de desenvolvimento Full Stack da b7web.

foi utilizado html, css e javascript. com o projeto foi possivel fazer requisições vindas do arquivo etapas.js porem seria possivel fazer essas requisiçoes utilizando promise ou async await por exemplo.

No css foi utilizado flexbox

transformações necessárias para alcançar o modelo dimensional para análise de nepotismo.

Primeiro realizamos a remoção de caracteres indesejados na base como virgulas, hífen e aspas, removemos também os espaços duplos. Como foi proposto realizar a validação do CPF utilizamos uma biblioteca do python (https://pypi.org/project/validate-docbr/) que foi responsável pela validação do CPF e em casos onde o CPF não foi válido ele foi removido do dataset.

Depois utilizamos Regex, que são expressões regulares, para separar o nome do sobrenome com o intuito de evitar problemas de pessoas que possuíam nomes compostos como Pedro José por exemplo, consideramos como sobrenome o último valor de caracteres no nome completo. Finalizando a etapa de separação dos nomes e sobrenomes realizamos um JOIN, junção entre duas tabelas, com o dataset base do IBGE para acrescentarmos a nossa base de dados os campos Código do IBGE, Estado e a Sigla de cada estado feito isso separamos esses valores em uma tabela chamada Dim_localidade como proposto no modelo dimensional elaborado deixando apenas a coluna Código do IBGE no nosso dataset que futuramente irá compor a nossa tabela Fact_indicados. Porém antes realizamos a separação do dataset pelos Tipos de cargos ficando os que possuíam cargos indicados na tabela Fact_indicados e os de cargos Eleitos e Concursados na Dim_indicadores.

Feito essa separação começamos a validação dos possíveis casos de nepotismo, realizamos uma junção das tabelas Fact_indicados e Dim_indicadores pelo Sobrenome e por Cidade visando encontrar apenas os casos que ocorrem dentro das regiões vigentes da pessoa que indicou, para isso o método de junção que traz apenas as intersecções contidas nas tabelas seguindo os parâmetros passados, assim conseguimos encontrar os possíveis casos de nepotismo feito isso criamos uma coluna responsável por indicar se aquele cadastro possui possível caso de Nepotismo, em outros casos onde não foram encontrados os requisitos para ocorrência de Nepotismo criamos uma coluna indicando que não possuía Nepotismo, feito toda essa identificação e separação dos cadastros do nosso dataset realizamos a junção das bases separadas para identificação e finalizamos o tratamento da dimensão Dim_indicadores e Fact_indicadores. 

Para finalizar realizamos o carregamento de todas as tabelas concluídas no diretório de processamento indicando que todos os dados foram processados e estão prontos para serem consumidos e para criar a análise deles.

### Visualização 

Com base na disponibilização dos dados e no tratamento obtido foi utilizado o Power BI como ferramenta de visualização, optamos por utilizar no DashBoard um mapa que é capaz de mostra as localidades onde há casos possíveis de nepotismo.

Utilizamos também um gráfico de barras onde ele traz informações de quantidade de nepotismo por Estados, utilizamos também quatro cartões que são responsáveis por trazer informações resumidas de casos de nepotismo como quantidade total e estado com mais casos de nepotismo.

Resultado obtido: 



