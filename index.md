---
title: Introdução
date: '2017-07-04'
---





## Introdução

A linguagem `R` é bem intuitiva. É possível fazer bastante coisa à base da tentativa e erro! Além disso, grande parte do conhecimento é escalável, isto é, quando você aprende a utilizar um certo tipo de função, o aprendizado pode ser replicado para funções parecidas. Essa ideia ficará bem clara quando falarmos dos pacotes do `tidyverse`, como o `dplyr` e o `ggplot2`.

Quando o aprendizado não for muito intuitivo ou a utilização de uma função for muito complicada, demandando às vezes conhecimento de Estatística ou Programação, você pode acabar precisando de uma forcinha. Felizmente, a comunidade R é bem ativa, e há várias formas de se conseguir ajuda. Nesta seção, vamos listar algumas dessas maneiras. Em seguida, faremos uma introdução ao RStudio, mostrando as suas principais funcionalidades. Então começaremos a conhecer o R, explorando diversos conceitos básicos.

--------------------------------------------------------------------------------



## Pedindo Ajuda

No R, há quatro principais entidades para se pedir ajuda:

- Help/documentação do R (comandos `help(nome_da_funcao)` ou `?nome_da_funcao`)

- Google

- Stack Overflow

- Coleguinha

A busca por ajuda é feita preferencialmente, mas não necessariamente, na ordem acima.

### Documentação do R

A documentação do R serve para você aprender a usar uma determinada função.


```r
?mean
help(mean)
```

Cinco dicas:

1. Os exemplos no final são particularmente úteis.
2. Leia a seção **Usage** para ter noção de como usar.
3. Os parâmetros estão descritos em **Arguments**. Identifique quais tipos de objetos eles recebem.
4. Caso essa função não atenda às suas necessidades, a seção **See Also** sugere funções relacionadas.
5. Alguns pacotes possuem tutorias de uso mais completos. Esses textos são chamados de `vignettes` e podem ser acessados com a função `vignette(package = 'nomeDoPacote')`. Por exemplo, `vignette(package = 'dplyr')`. Depois de ver a lista de artigos, escolha um nome e rode `vignette(topic = 'nome', package = 'nomeDoPacote')`. Por exemplo, `vignette(topic = 'introduction', package = 'dplyr')`.

### Google

Há uma comunidade gigantesca de usuários de R gerando diariamente uma infinidade de conteúdos e discussões. Não raramente, você irá encontrar discussões sobre o seu problema simplesmente jogando o seu erro no Google. Essa deve ser sua primeira tentativa! Pesquisas em inglês aumentam consideravelmente a chance de encontrar uma resposta.

Exemplo (repare no 'r' adicionado na busca, isso ajuda bastante):


```r
log("5")
## Error in log("5"): non-numeric argument to mathematical function
```

![](figures/ajuda_google.png)

### Stack Overflow

O [Stack Overflow](http://stackoverflow.com/) e o [Stack Overflow em Português](http://pt.stackoverflow.com/) são sites de Pergunta e Resposta amplamente utilizados por todas as linguagens de programação, e o R é uma delas. Nos EUA, chegam até a usar a reputação dos usuários como diferencial no currículo!

Provavelmente o Google lhe indicará uma página deles quando você estiver procurando ajuda. E quando todas as fontes possíveis de ajuda falharem, o Stack Overflow lhe dará o espaço para **criar sua própria pergunta**.

**Um ponto importante**: como fazer uma **boa** pergunta no Stack Overflow?

No site, tem um tutorial com uma lista de boas práticas, [que se encontra aqui](http://pt.stackoverflow.com/help/how-to-ask). Algumas dicas são

- ser conciso;
- ser específico;
- ter mente aberta; e
- ser gentil.

Porém, no caso do R, há outro requisito que vai aumentar muito sua chance de ter uma boa resposta: **exemplinho minimal e reprodutível**.

- Ser **minimal**: usar bancos de dados menores e utilizar pedaços de códigos apenas suficientes para apresentar o seu problema. Não precisa de banco de dados de um milhão de linhas e nem colocar o seu código inteiro para descrever a sua dúvida.

- Ser **reprodutível**: o seu código deve rodar fora da sua máquina. Se você não fornecer uma versão do seu problema que rode (ou que imite seu erro), as pessoas vão logo desistir de te ajudar. Por isso, nunca coloque bancos de dados que só você tem acesso. Use bancos de dados que já vem no R ou disponibilize um exemplo (possivelmente anonimizado) em `.csv` na web para baixar. E se precisar utilizar funções diferentes, coloque as `library`'s correspondentes.

--------------------------------------------------------------------------------



## RStudio

O RStudio é o melhor ambiente de desenvolvimento de códigos em R disponível. Você pode baixá-lo [neste link](https://www.rstudio.com/products/rstudio/download/preview/).

Muitas das ferramentas são aprendidas conforme o uso, e há bons materiais sobre o RStudio na internet (por exemplo, [esta página](https://csgillespie.github.io/efficientR/set-up.html#rstudio)). Uma funcionalidade importante é a criação de projetos, permitindo dividir o trabalho em múltiplos ambientes, cada um com o seu diretório, documentos e *workspace*. A seguir, apresentamos algumas estruturas para a organização de um projeto.

**Estrutura 1**. Por extensão de arquivo.


```bash
nome_do_projeto/
  - .Rprofile   # códigos para rodar assim que abrir o projeto
  - R/          # Código R, organizado com a-carrega.R, b-prepara bd.R, c-vis.R, d-modela, ...
  - RData/      # Dados em formato .RData
  - csv/        # Dados em .csv
  - png/        # gráficos em PNG
  - nome_do_projeto.Rproj
```

**Estrutura 2**. Típico projeto de análise estatística.


```bash
project/
  - README.Rmd   # Descrição do pacote
  - set-up.R     # Pacotes etc
  - R/           # Código R, organizado com 0-load.R, 1-tidy.R, 2-vis.R, ...
  - data/        # Dados (estruturados ou não)
  - figures/     # gráficos (pode ficar dentro de output/)
  - output/      # Relatórios em .Rmd, .tex etc
  - project.Rproj
```

**Estrutura 3**. Pacote do R (avançado).


```bash
project/
  - README.md    # Descrição do pacote
  - DESCRIPTION  # Metadados estruturados do pacote e dependências
  - NAMESPACE    # importações e exportações do pacote
  - vignettes/   # Relatórios em .Rmd
  - R/           # Funções do R
  - data/        # Dados estruturados (tidy data)
  - data-raw/    # Dados não estruturados e arqs 0-load.R, 1-tidy.R, 2-vis.R, ...
  - project.Rproj
```

Ao abrir o RStudio, você verá 4 quadrantes. Observe a figura abaixo.

![](figures/rstudio-editor.png)

Esses quadrantes representam o **editor**, o **console**, o **environment** e o **output**.  Eles vêm nesta ordem, e depois você pode organizá-los da forma que preferir.

Listamos abaixo as funções dos principais painéis:

- **Editor/Scripts**: é onde escrevemos nossos códigos.
- **Console**: é onde rodamos o código e recebemos as saídas. O R vive aqui!
- **Environment**: painel com todos os objetos criados na sessão.
- **Files**: mostra os arquivos no diretório de trabalho. É possível navegar entre diretórios.
- **Plots**: painel onde os gráficos serão apresentados.
- **Help**: janela onde a documentação das funções serão apresentadas.
- **History**: painel com um histórico dos comandos rodados.

Conhecer atalhos ajuda bastante quando estamos programando no RStudio. Veja os principais:

- **CTRL+ENTER**: roda a linha selecionada no script. Os atalhos mais utilizado.
- **ALT+-**: (<-) sinal de atribuição. Você usará o tempo todo.
- **CTRL+SHIFT+M**: (%>%) operador *pipe*. Guarde esse atalho, você usará bastante.
- **CTRL+1**: altera cursor para o script.
- **CTRL+2**: altera cursor para o console.
- **CTRL+ALT+I**: cria um chunk no R Markdown.
- **ALT+SHIFT+K**: janela com todos os atalhos disponíveis.

--------------------------------------------------------------------------------



## R Markdown

O R Markdown é um tipo de documento especial que contém tanto textos quanto códigos em R, tudo escrito no mesmo lugar. 

O *markdown* nada mais é do que um documento de texto com alguns padrões básicos de formatação, como negrito, itálico, títulos, subtítulos, itens e referências cruzadas. Já os *chunks* são pedaços de códigos em R encapsulados por três crases (```). Os códigos são executados sempre que o documento é processado.


```
## ```{r}
## isto é um chunk. 
## ```
```

<div class='admonition note'>
<p class='admonition-title'>
Nota
</p>
<p>
Este site foi escrito em R Markdown. Toda vez que aparecer exemplos de código de R, havia um chunk no .Rmd original.
</p>
</div>

Para produção de relatórios, o R Markdown possui algumas vantagens, como:

1. **Simplicidade e foco**. Permite ao usuário o foco na análise e não na formatação do documento.
1. **Versátil**. Pode ser utilizado para gerar documentos em $\LaTeX$, `Word`, `HTML` e apresentações em `beamer`, `pptx` e `HTML` (de vários tipos). Pode ainda gerar sites, livros, dissertações de mestrado e até mesmo dashboards interativos.
1. **Reprodutível**. O R Markdown nada mais é que um arquivo de texto. Além disso, ele tenta te obrigar a fazer o documento mais autocontido possível. Assim, um documento `.Rmd` é fácil de compartilhar e de ser utilizado pelo receptor. Lembre-se, o receptor pode ser o futuro você! Vale enfatizar que a reprodutibilidade é considerada como um dos princípios fundamentais da ciência. Então, só de usar R Markdown, você já está colaborando com o método científico. :)
1. **Flexível**. É possível configurar e criar *templates* de análises para quaisquer tipos de aplicações e clientes. Os textos podem ser parametrizados por números que variam de versão para versão, mensalmente, por exemplo, tudo escrito somente em R. 

Criar um R Markdown novo no RStudio é fácil. Clique no botão de criar arquivo e selecione R Markdown.


```r
knitr::include_graphics("figures/criar_rmarkdown.png")
```

![plot of chunk unnamed-chunk-21](figures/criar_rmarkdown.png)

Para detalhes sobre como utilizar o R Markdown, leia o  [r4ds](http://r4ds.had.co.nz/r-markdown.html) e [o tutorial do RStudio](http://rmarkdown.rstudio.com/lesson-1.html).

--------------------------------------------------------------------------------



## Instalar pacotes

O grande trunfo do R são seus pacotes. Assim, fique bastante à vontade para instalar e atualizar muitos e muitos pacotes ao longo da sua experiência com o R.

Existem três principais maneiras de instalar pacotes. Em ordem de frequência, são:

- Via CRAN (Comprehensive R Archive Network): `install.packages("nome-do-pacote")`.
- Via Github: `devtools::install_github("nome-do-repo/nome-do-pacote")`.
- Via arquivo .zip/.tar.gz: `install.packages("C:/caminho/nome-do-pacote.zip", repos = NULL)`.

### Via CRAN

Instale pacotes que não estão na sua biblioteca usando a função `install.packages("nome_do_pacote")`. Por exemplo:


```r
install.packages("magrittr")
```



E, de agora em diante, não precisa mais instalar. Basta carregar o pacote com `library(magrittr)`.

<div class='admonition note'>
<p class='admonition-title'>
Dica!
</p>
<p>
Escreva nome_do_pacote::nome_da_funcao() se quiser usar apenas uma função de um determinado pacote. O operador :: serve para isso. Essa forma também é útil quando se tem duas funções com o mesmo nome e precisamos garantir que o código vá usar a função do pacote correto.
</p>
</div>

### Via Github

Desenvolvedores costumam disponibilizar a última versão de seus pacotes no Github, e alguns deles sequer estão no CRAN. Mesmo assim ainda é possível utilizá-los instalando diretamente pelo github. O comando é igualmente simples:


```r
devtools::install_github("rstudio/shiny")
```

Apenas será necessário o username e o nome do repositório (que geralmente tem o mesmo nome do pacote). No exemplo, o username foi "rstudio" e o repositório foi "shiny". 

Se você não é familiar com o github, não se preocupe! Os pacotes disponibilizados na plataforma geralmente têm um `README` cuja primeira instrução é sobre a instalação. Se não tiver, provavelmente este pacote não te merece! =)

### Via arquivo .zip/.tar.gz

Se você precisar instalar um pacote que está zipado no seu computador (ou em algum servidor), utilize o seguinte comando:


```r
install.packages("C:/caminho/para/o/arquivo/zipapo/nome-do-pacote.zip", repos = NULL)
```

É semelhante a instalar pacotes via CRAN, com a diferença que agora o nome do pacote é o caminho inteiro até o arquivo. O parâmetro `repos = NULL` informa que estamos instalando a partir da máquina local.

A aba ***Packages*** do RStudio também ajuda a administrar os seus pacotes.

![](figures/instalar_pacote_rstudio.png)

--------------------------------------------------------------------------------



## R como calculadora

Pelo console, é possível executar qualquer comando do R.


```r
1:30
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30
```

Esse comando é uma forma simplificada de criar um vetor de inteiros de 1 a 30.
Os números que aparecem entre colchetes ([1] e [24]) indicam o índice do primeiro elemento impresso em cada linha.

<div class='admonition note'>
<p class='admonition-title'>
Quando compilamos?
</p>
<p>
Quem vem de linguagens como o C ou Java espera que seja necessário compilar o código em texto para o código das máquinas (geralmente um código binário). No R, isso não é necessário. O R é uma linguagem de programação dinâmica que interpreta o seu código enquanto você o executa.
</p>
</div>

Tente jogar no console `2 * 2 - (4 + 4) / 2`. Pronto! Com essa simples expressão você já é capaz de pedir ao R para fazer qualquer uma das quatro operações aritméticas básicas. A seguir, apresentamos uma lista resumindo como fazer as principais operações no R.


```r
1 + 1    # adição
## [1] 2
4 - 2    # subtração
## [1] 2
2 * 3    # multiplicação
## [1] 6
5 / 3    # divisão
## [1] 1.666667
4 ^ 2    # potência
## [1] 16
5 %% 3   # resto da divisão de 5 por 3
## [1] 2
5 %/% 3  # parte inteira da divisão de 5 por 3
## [1] 1
```

Além do mais, as operações e suas precedências são mantidas como na matemática, ou seja, divisão e multiplicação são calculadas antes da adição e subtração. E os parênteses nunca são demais!

Uma outra forma de executar uma expressão é escrever o código no **editor** e teclar `Ctrl + Enter` ou `Ctrl + R`. Assim, o comando é enviado para o **console**, onde é diretamente executado.

Se você digitar um comando incompleto, como `5 + `, e apertar `Enter`, o R mostrará um `+`, o que não tem nada a ver com somar alguma coisa. Isso significa que o R está esperando que você complete o seu comando. Termine o seu comando ou aperte `Esc` para recomeçar.

```
> 5 -
+ 
+ 5
[1] 0
```

Se você digitar um comando que o R não reconhece, ele retornará uma mensagem de erro. 

NÃO ENTRE EM PÂNICO! 

Ele só está avisando que não conseguiu interpretar o comando. Você pode digitar outro comando normalmente em seguida.

```
> 5 % 5
Error: unexpected input in "5 % 5"
> 5 - 5
[1] 0
```

--------------------------------------------------------------------------------



## Objetos

O R te permite salvar dados dentro de um objeto. Para isso, utilizamos o operador `<-`.

No exemplo abaixo, salvamos o valor 1 em `a`. Sempre que o R encontrar o símbolo `a`, ele vai substituí-lo por 1.


```r
a <- 1
a
## [1] 1
```


<div class='admonition note'>
<p class='admonition-title'>
Atenção!
</p>
<p>
O R diferencia letras maiúsculas e minúsculas, isto é, <b>a</b> é considerado um objeto diferente de <b>A</b>.
</p>
</div>

### Objetos atômicos

Existem cinco classes básicas ou “atômicas” no R:

- character 
- numeric 
- integer 
- complex 
- logical 

Veja alguns exemplos:


```r
# characters

"a"
## [1] "a"
"1"
## [1] "1"
"positivo"
## [1] "positivo"
"Error: objeto x não encontrado"
## [1] "Error: objeto x não encontrado"

# numeric

1
## [1] 1
0.10
## [1] 0.1
0.95
## [1] 0.95
pi
## [1] 3.141593

# integer

1L
## [1] 1
5L
## [1] 5
10L
## [1] 10

# complex (raramente utilizado para análise de dados)

2 + 5i
## [1] 2+5i

# logical

TRUE
## [1] TRUE
FALSE
## [1] FALSE
```


Para saber a classe de um objetivo, você pode usar a função `class()`.


```r
x <- 1
class(x)
## [1] "numeric"

y <- "a"
class(y)
## [1] "character"

z <- TRUE
class(z)
## [1] "logical"
```

### Vetores

Vetores no R são os objetos mais simples que podem guardar objetos atômicos.


```r
vetor1 <- c(1, 2, 3, 4)
vetor2 <- c("a", "b", "c")

vetor1
## [1] 1 2 3 4
vetor2
## [1] "a" "b" "c"
```

Um vetor tem sempre a mesma classe dos objetos que guarda.


```r
class(vetor1)
## [1] "numeric"
class(vetor2)
## [1] "character"
```

De forma bastante intuitiva, você pode fazer operações com vetores.


```r
vetor1 - 1
## [1] 0 1 2 3
```

Quando você faz `vetor1 - 1`, o R subtrai `1` de cada um dos elementos do vetor. O mesmo acontece quando você faz qualquer operação aritmética com vetores no R.


```r
vetor1 / 2
vetor1 * 10
```

Você também pode fazer operações que envolvem mais de um vetor:


```r
vetor1 * vetor1
## [1]  1  4  9 16
```

Neste caso, o R irá alinhar os dois vetores e multiplicar elemento por elemento. Isso pode ficar um pouco confuso quando os dois vetores não possuem o mesmo tamanho:


```r
vetor2 <- 1:3
vetor * vetor2
## Error in eval(expr, envir, enclos): object 'vetor' not found
```

O R alinhou os dois vetores e, como eles não possuíam o mesmo tamanho, foi repetindo o vetor menor até completar o vetor maior. Esse comportamento é chamado de **reciclagem** e é útil para fazer operações elemento por elemento (vetorizadamente), mas às vezes pode ser confuso. Com o tempo, você aprenderá a se aproveitar dele.

### Misturando objetos

<div class='admonition note'>
<p class='admonition-title'>
Vetores são homogêneos
</p>
<p>
Os elementos de um vetor são sempre da mesma classe. Ou todos são numéricos, ou são todos character, ou todos são lógicos etc. Não dá para ter um número e um character no mesmo vetor, por exemplo.
</p>
</div>

Se colocarmos duas ou mais classes diferentes dentro de um mesmo vetor, o R vai forçar que todos os elementos passem a pertencer à mesma classe. O número `1.7` viraria `"1.7"` se fosse colocado ao lado de um `"a"`.


```r
y <- c(1.7, "a")  ## character
y <- c(TRUE, 2)   ## numeric
y <- c(TRUE, "a") ## character
```

A ordem de precedência é:

**DOMINANTE** `character > complex > numeric > integer > logical` **RECESSIVO**

### Forçando classes explicitamente

Você pode coagir um objeto a ser de uma classe específica com as funções `as.character()`, `as.numeric()`, `as.integer()` e `as.logical()`. É equivalente à função `convert()` do SQL. 


```r
x <- 0:4
class(x)
## [1] "integer"
as.numeric(x)
## [1] 0 1 2 3 4
as.logical(x)
## [1] FALSE  TRUE  TRUE  TRUE  TRUE
as.character(x)
## [1] "0" "1" "2" "3" "4"
```

Se o R não entender como coagir uma classe na outra, ele soltará um `warning` informado que colocou `NA` no lugar.


```r
x <- c("a", "b", "c")
as.numeric(x)
## Warning: NAs introduced by coercion
## [1] NA NA NA
```

<div class='admonition note'>
<p class='admonition-title'>
Observação
</p>
<p>
O <b>NA</b> tem o mesmo papel que o <b>null</b> do SQL. Porém, há um <b>NULL</b> no R também, com diferenças sutis que vamos abordar mais adiante.
</p>
</div>

### Matrizes

Matrizes são vetores com duas dimensões (e por isso só possuem elementos de uma mesma classe).


```r
m <- matrix(1:6, nrow = 2, ncol = 3)
m
##      [,1] [,2] [,3]
## [1,]    1    3    5
## [2,]    2    4    6
dim(m) # funçăo dim() retorna a dimensăo do objeto.
## [1] 2 3
```

Repare que os números de 1 a 6 foram dispostos na matriz coluna por coluna (*column-wise*), ou seja, preenchendo de cima para baixo e depois da esquerda para a direita.

**Operações úteis**


```r
m[3,  ]   # seleciona a terceira linha
m[ , 2]   # seleciona a segunda coluna
m[1, 2]   # seleciona o primeiro elemento da segunda coluna
t(m)      # matriz transposta
m %*% n   # multiplicação matricial
solve(m)  # matriz inversa de m
```

### Fatores

Fatores podem ser vistos como vetores de inteiros que possuem rótulos (levels).


```r
sexo <- c("M", "H", "H", "H", "M", "M", "H")
fator <- as.factor(sexo)
fator
## [1] M H H H M M H
## Levels: H M
as.numeric(fator)
## [1] 2 1 1 1 2 2 1
```

Eles são úteis para representar uma variável categórica (nominal e ordinal). Na modelagem, eles serão tratados de maneira especial em funções como `lm()` e `glm()`. 

A função `levels()` retorna os rótulos do fator:


```r
levels(fator)
## [1] "H" "M"
```

A ordem das categorias de um fator pode importar. Como exemplo, temos as caselas de referência de modelos estatísticos e a ordem das barras de um gráfico. Para ajudar nesta tarefa, consulte o pacote [forcats](https://github.com/tidyverse/forcats).

<div class='admonition note'>
<p class='admonition-title'>
Um erro comum e desastroso
</p>
<p>
Quando um vetor de números está como <b>factor</b>, ao tentar transformá-lo em <b>numeric</b>, você receberá um vetor de inteiros que não tem nada a ver com os valores originais!
</p>
</div>


```r
numeros <- factor(c("10", "55", "55", "12", "10", "-5", "-90"))

as.numeric(numeros)
#Por essa eu năo esperava!
```

Para evitar isso, use `as.character()` antes de transformar para número.


```r
as.numeric(as.character(numeros))
## Error in eval(expr, envir, enclos): object 'numeros' not found
# Agora está OK!
```


### Valores especiais

Existem valores reservados para representar dados faltantes, infinitos, e indefinições matemáticas.

- **NA** (Not Available) significa dado faltante/indisponível. É o `null` do SQL ou o `.` do SAS. O `NA` tem uma classe, ou seja, podemos ter `NA` numeric, `NA` character etc.
- **NaN** (Not a Number) representa indefinições matemáticas, como `0/0` e `log(-1)`. Um `NaN` é um `NA`, mas a recíproca não é verdadeira.
- **Inf** (Infinito) é um número muito grande ou o limite matemático, por exemplo, `1/0` e `10^310`. Aceita sinal negativo `-Inf`. 
- **NULL** representa a ausência de informação. Conceitualmente, a diferença entre `NA` e `NULL` é sutil, mas, no R, o `NA` está mais alinhado com os conceitos de estatística (ou como gostaríamos que os dados faltantes se comportassem em análise de dados) e o `NULL` está em sintonia com comportamentos de lógica de programação.
- Use as funções `is.na()`, `is.nan()`, `is.infinite()` e `is.null()` para testar se um objeto é um desses valores.


```r
x <- c(NaN, Inf, 1, 2, 3, NA)
is.na(x)
## [1]  TRUE FALSE FALSE FALSE FALSE  TRUE
is.nan(x)
## [1]  TRUE FALSE FALSE FALSE FALSE FALSE
```

### Listas

Listas são um tipo especial de vetor que aceita elementos de classes diferentes.


```r
x <- list(1:5, "Z", TRUE, c("a", "b"))
x
## [[1]]
## [1] 1 2 3 4 5
## 
## [[2]]
## [1] "Z"
## 
## [[3]]
## [1] TRUE
## 
## [[4]]
## [1] "a" "b"
```

É um dos objetos mais importantes para armazenar dados e vale a pena saber manuseá-los bem. Existem muitas funções que fazem das listas objetos incrivelmente úteis.

Criamos uma lista com a função `list()`, que aceita um número arbitrário de elementos. Listas aceitam QUALQUER tipo de objeto. Podemos ter listas dentro de listas, por exemplo. Como para quase todas as classes de objetos no R, as funções `is.list()` e `as.list()` também existem.

Na lista `pedido` abaixo, temos `numeric`, `Date`, `character`, vetor de `character` e `list` contida em uma lista:


```r
pedido <- list(pedido_id = 8001406,
               pedido_registro = as.Date("2017-05-25"),
               nome = "Athos", 
               sobrenome = "Petri Damiani", 
               cpf = "12345678900", 
               email = "athos.damiani@gmail.com", 
               qualidades = c("incrível", "impressionante"),
               itens = list(
                 list(descricao = "Ferrari", 
                      frete = 0, 
                      valor = 500000),
                 list(descricao = "Dolly", 
                      frete = 1.5, 
                      valor = 3.90)
               ), 
               endereco = list(entrega = list(logradouro = "Rua da Glória", 
                                              numero = "123",
                                              complemento = "apto 71"),
                               cobranca = list(logradouro = "Rua Jose de Oliveira Coutinho",
                                               numero = "151",
                                               complemento = "5o andar")
               )
)
```

**Operações úteis**


```r
pedido$cpf     # elemento chamado 'cpf'
pedido[1]      # nova lista com apenas o primeiro elemento
pedido[[2]]    # segundo elemento
pedido["nome"] # nova lista com apenas o elemento chamado 'nome'
```

Certamente você se deparará com listas quando for fazer análise de dados com o R. Nos tópicos mais aplicados, iremos aprofundar sobre o tema. O pacote [purrr](https://github.com/hadley/purrr) contribui com funcionalidades incríveis para listas.

### data.frame

Um `data.frame` é o mesmo que uma tabela do SQL ou um spreadsheet do Excel, por isso são objetos muito importantes. 

Usualmente, seus dados serão importados para um objeto `data.frame`. Em grande parte do curso, eles serão o principal objeto de estudo.

Os `data.frame`'s são listas especiais em que todos os elementos possuem **o mesmo comprimento**. Cada elemento dessa lista pode ser pensado como uma coluna da tabela. Seu comprimento representa o número de linhas. 

Já que são listas, essas colunas podem ser de classes diferentes. Essa é a grande diferença entre `data.frame`'s e matrizes. Algumas funções úteis:

- `head()` - Mostra as primeiras 6 linhas.
- `tail()` - Mostra as últimas 6 linhas.
- `dim()` - Número de linhas e de colunas.
- `names()` - Os nomes das colunas (variáveis).
- `str()` - Estrutura do data.frame. Mostra, entre outras coisas, as classes de cada coluna.
- `cbind()` - Acopla duas tabelas lado a lado.
- `rbind()` - Empilha duas tabelas.

O exemplo abaixo mostra que uma lista pode virar `data.frame` se todos os elementos tiverem o mesmo comprimento.


```r
minha_lista <- list(x = c(1, 2, 3), y = c("a", "b"))
as.data.frame(minha_lista)
## Error in (function (..., row.names = NULL, check.rows = FALSE, check.names = TRUE, : arguments imply differing number of rows: 3, 2
```


```r
minha_lista <- list(x = c(1, 2, 3), y = c("a", "b", "c"))
as.data.frame(minha_lista)
##   x y
## 1 1 a
## 2 2 b
## 3 3 c
```

--------------------------------------------------------------------------------



## Controles de Fluxo

Como toda boa linguagem de programação, o R possui estruturas de `if`'s, `else`'s, `for`'s, `while`'s etc. Esses **controles de fluxo** são importantes na hora de programar. 

### IF e ELSE

O seguinte trecho de código só será executado se o objeto `x` for igual a 1. Repare que a condição de igualdade é representada por dois iguais `==`.


```r
x <- 2

if(x == 1) {         
  Sys.time()      # Devolve a data/hora no momento da execução.
}
```



```r
x <- 1

if(x == 1) {
  Sys.time()
}
## [1] "2017-07-04 00:57:30 UTC"
```

O R só vai executar o que está na expressão dentro das chaves `{}` se o que estiver dentro dos parênteses `()` retornar `TRUE`.

A sintaxe com o `else` e o `if else` é


```r
if(x < 0) {
  
  sinal <- "negativo"
  
} else if(x == 0) {
  
  sinal <- "neutro"
  
} else if(x > 0) {
  
  sinal <- "positivo"
}

sinal
## [1] "positivo"
```

<div class='admonition note'>
<p class='admonition-title'>
Diferença entre SQL e R nas comparações lógicas
</p>
<p>
<b>Igualdade</b>: no SQL é só um sinal de igual: <2 = 1. No R são dois: 2 == 1.
<br>
<b>Diferença</b>: teste de diferente no R é != em vez de de <>.
<br>
<b>Negação</b>: em vez de usar a palavra "not" igual ao SQL, usamos !. Por exemplo, "entidade_id not in ('100515')" fica "!entidade_id %in% c('100515')".
</p>
</div>


### for

Vamos usar o `for` para somar todos os elementos de um vetor.


```r

x <- 1:10   # Cria um vetor com a sequência 1, 2, ..., 10.
soma <- 0

for(i in 1:10) {
  soma <- soma + x[i]
}

soma
## [1] 55
```

De forma equivalente, podemos usar diretamente a função `sum()`.


```r
sum(x)
## [1] 55
```

Agora, vamos imprimir na tela o resultado da divisão de cada elemento de um vetor por dois. Para isso, utilizaremos a função `print()`.


```r
vetor <- 30:35
indices <- seq_along(vetor) # cria o vetor de índices segundo o tamanho 
                            # do objeto vetor.   
for(i in indices) {
  print(vetor[1:i] / 2)
}
## [1] 15
## [1] 15.0 15.5
## [1] 15.0 15.5 16.0
## [1] 15.0 15.5 16.0 16.5
## [1] 15.0 15.5 16.0 16.5 17.0
## [1] 15.0 15.5 16.0 16.5 17.0 17.5
```

No trecho de código acima, preste atenção no resultado individual de cada uma das operações para entender como o R funciona.

Para finalizar, listamos na tabela abaixo os principais operadores lógicos.


|Operador   |Descrição                                 |
|:----------|:-----------------------------------------|
|x < y      |x menor que y?                            |
|x <= y     |x menor ou igual a y?                     |
|x > y      |x maior que y?                            |
|x >= y     |x maior ou igual a y?                     |
|x == y     |x igual a y?                              |
|x != y     |x diferente de y?                         |
|!x         |Negativa de x                             |
|x &#124; y |x ou y são verdadeiros?                   |
|x & y      |x e y são verdadeiros?                    |
|xor(x, y)  |x ou y são verdadeiros (apenas um deles)? |

--------------------------------------------------------------------------------




## Funções

O R vem com muitas funções implementadas, com as quais você pode fazer facilmente muitas  tarefas complicadas, como gerar números aleatórios. Em geral, o nome das funções é bem intuitivo, por exemplo, `mean()` é a função que calcula a média e `round()` é a função que arredonda um número.


```r
mean(1:10)
## [1] 5.5
round(pi) #Note que 'pi' é um objeto pré-definido pelo R.
## [1] 3
```

Para entender melhor o funcionamento das funções no R, considere o seguinte exemplo:


```r
die <- 1:6
round(mean(die))
## [1] 4
```

A ilustração abaixo mostra o que acontece quando você executa `round(mean(die))` no R.

![](figures/round.png)

Passamos dados para as funções por meio de argumentos. No R, esses argumentos estão documentados na página de ajuda de cada uma das funções, que pode ser acessada digitando `help(nome_da_funcao)` ou `?nome_da_funcao`.

### Criando suas próprias funções

No R, você pode (e deve) criar as suas próprias funções. É uma prática que evita retrabalho, simplifica o código e, eventualmente, diminui o tempo de execução das análises. Veja abaixo um exemplo de como criar uma função.


```r
soma <- function(x, y = 0) {
  resposta <- x + y
  return(resposta)
}
```

A função acima tem:

- o nome `soma`;
- os argumentos `x` e `y`;
- o corpo `resposta <- x + y`; e
- o valor padrão `0` para o argumento `y` (`y = 0`).

Após rodar o código anterior, você pode usá-la como qualquer outra função:


```r
soma(2, 1) # soma de 2 + 1
## [1] 3
soma(2) # soma de 2 + 0, pois y = 0 por default.
## [1] 2
```

O argumento `y` possui o valor padrão `0`. Isso quer dizer que ele valerá zero caso o usuário não passe um valor explicitamente.

O [Advanced-R](http://adv-r.had.co.nz/) é um excelente livro para quem quiser masterizar a arte de criar funções. 

--------------------------------------------------------------------------------



## Fórmulas

Fórmulas são objetos do tipo `y ~ x`. Em geral, elas representam associações entre objetos, como em um modelo de regressão. As funções as usam de diversas maneiras, mas o exemplo mais emblemático vem da modelagem estatística.


```r
formula <- y ~ x1 + x2
class(formula)
## [1] "formula"
```

A função `lm()` é a que ajusta um modelo linear no R, e `lm(y ~ x)` lê-se "regressão linear de y explicada por x".


```r
minha_formula <- Sepal.Width ~ Petal.Length + Petal.Width
class(minha_formula)
## [1] "formula"
lm(minha_formula, data = iris)
## 
## Call:
## lm(formula = minha_formula, data = iris)
## 
## Coefficients:
##  (Intercept)  Petal.Length   Petal.Width  
##       3.5870       -0.2571        0.3640
```

No caso específico dos modelos lineares, são nas fórmulas que conseguimos descrever as variáveis explicativas e suas interações. A fórmula `y ~ x1 * x2` significa "y regredido por x1, x2 e a interação entre x1 e x2". Fórmulas aparecem frequentemente em tarefas de modelagem.

Demais usos de fórmulas aparecerão em outras funções, como as do pacote `ggplot2`, com outros significados, e a documentação nos dirá como usá-las.

--------------------------------------------------------------------------------



## Gráficos (base)

O R já vem com funções básicas que fazem gráficos estatísticos de todas as naturezas. 

- Vantagens: são rápidas e simples.
- Desvantagens: são feias e difíceis para gerar gráficos complexos.

Nesta seção, mostraremos como construir alguns tipos de gráficos usando as funções base do R, mas [o nosso foco em visualização de dados](http://material.curso-r.com/ggplot/) está nas funções do pacote `ggplot2`.

### Gráfico de dispersão

Para construir um gráfico de dispersão, utilizamos a função `plot()`. Seus principais parâmetros são:

- `x`, `y` - Vetores para representarem os eixos x e y.
- `type` -  Tipo de gráfico. Pode ser pontos, linhas, escada, entre outros.

Para mais detalhes sobre os argumentos, ver `help(plot)`.

<div class='admonition note'>
<p class='admonition-title'>
Outras formas de utilizar a função plot()
</p>
<p> 
Além de gerar gráficos de dispersão, tentar chamar a função <b>plot(objeto_diferentao)</b> para qualquer tipo de objeto do R geralmente gera um gráfico interessante! Sempre tente fazer isso, a menos que seu objeto seja um <b>data.frame</b> com milhares de colunas!
</p>
</div>


```r
n <- 100
x <- 1:n
y <- 5 + 2 * x + rnorm(n, sd = 30)
plot(x, y)
```

![plot of chunk unnamed-chunk-65](figures//unnamed-chunk-65-1.png)

O parâmetro `type = "l"` indica que queremos que os pontos sejam interligados por linhas.


```r
plot(x, y, type = "l")
```

![plot of chunk unnamed-chunk-66](figures//unnamed-chunk-66-1.png)

### Histograma

Para construir histogramas, utilizamos a função `hist()`. Os principais parâmetros são:

- `x` - O vetor numérico para o qual o histograma será construído.
- `breaks` - O número (aproximado) de retângulos.


```r
hist(rnorm(1000))
```

![plot of chunk unnamed-chunk-67](figures//unnamed-chunk-67-1.png)


```r
hist(rnorm(1000), breaks = 6)
```

![plot of chunk unnamed-chunk-68](figures//unnamed-chunk-68-1.png)

### Boxplot

Para construir histogramas, utilizamos a função `boxplot()`. Os principais parâmetros são:

- `x` - O vetor numérico para o qual o boxplot será construído.


```r
boxplot(InsectSprays$count, col = "lightgray")
```

![plot of chunk unnamed-chunk-69](figures//unnamed-chunk-69-1.png)

Observe que o argumento `col=` muda a cor da caixa do boxplot.

Para mapear duas variáveis ao gráfico, utilizamos um objeto da classe `formula` e o argumento `data=`.


```r
boxplot(count ~ spray, data = InsectSprays, col = "lightgray")
```

![plot of chunk unnamed-chunk-70](figures//unnamed-chunk-70-1.png)

### Gráfico de barras

Para construir gráficos de barras, precisamos combinar as funções `table()` e `barplot()`.

No gráfico abaixo, primeiro criamos uma tabela de frequências com a função `table()` e, em seguida, construímos o gráfico com a função `barplot()`. A função `data()` carrega bases de dados de pacotes instalados. Veja `help(data)` para mais detalhes.


```r
data(diamonds, package = "ggplot2")
tabela <- table(diamonds$color)
tabela
## 
##     D     E     F     G     H     I     J 
##  6775  9797  9542 11292  8304  5422  2808
barplot(tabela)
```

![plot of chunk unnamed-chunk-71](figures//unnamed-chunk-71-1.png)

Também podemos mapear duas variáveis a um gráfico de barras utilizando tabelas de dupla entrada.


```r
VADeaths
##       Rural Male Rural Female Urban Male Urban Female
## 50-54       11.7          8.7       15.4          8.4
## 55-59       18.1         11.7       24.3         13.6
## 60-64       26.9         20.3       37.0         19.3
## 65-69       41.0         30.9       54.6         35.1
## 70-74       66.0         54.3       71.1         50.0
```


```r
barplot(VADeaths)
```

![plot of chunk unnamed-chunk-73](figures//unnamed-chunk-73-1.png)

--------------------------------------------------------------------------------



## Exercícios

**Sugestão**: resolva os exercícios em arquivo R Markdown, aproveitando para fazer anotações e registrar suas dúvidas ao longo do caminho.

--------------------------------------------------------------------------------

**1.** Calculo o número de ouro no R.

Dica: o número de ouro é dado pela expressão $\frac{1 + \sqrt{5}}{2}$.


--------------------------------------------------------------------------------

**2.** Qual o resultado da divisão de 1 por 0 no R? E de -1 por 0?


--------------------------------------------------------------------------------

**3.** Quais as diferenças entre `NaN`, `NULL`, `NA` e `Inf`? Digite expressões que retornam cada um desses resultados.


--------------------------------------------------------------------------------

**4.** Sem rodar o código, calcule o que a expressão `5 + 3 * 10 %/% 3 == 15` vai resultar no R. Em seguida, apenas utilizando parênteses, faço a expressão retornar o valore contrário (i.e., se originariamente for `TRUE`, faça retornar `FALSE`).


--------------------------------------------------------------------------------

**5.** Por que o código abaixo retorna erro? Arrume o código para retornar o valor `TRUE`.


```r
x <- 4
if(x = 4) {
  TRUE
}
```


--------------------------------------------------------------------------------

**6.** Usando `if` e `else`, escreva um código que retorne a string "número" caso o valor seja da classe `numeric` ou `integer`; a string "palavra" caso o valor seja da classe `character`; e `NULL` caso contrário.
 

--------------------------------------------------------------------------------

**7.** Use o `for` para retornar o valor mínimo do seguinte vetor: `vetor <- c(4, 2, 1, 5, 3)`. Modifique o seu código para receber vetores de qualquer tamanho.

--------------------------------------------------------------------------------

**8.** Usando apenas `for` e a função `length()`, construa uma função que calcule a média de um vetor número qualquer. Construa uma condição para a função retornar `NULL` caso o vetor não seja numérico.

--------------------------------------------------------------------------------

**9.** Rode `help(runif)` para descobrir o que a função `runif()` faz. Em seguida, use-a para escrever uma função que retorne um número aleatório inteiro entre 0 e 10 (0 e 10 inclusive).

--------------------------------------------------------------------------------

**10.** Rode `help(sample)` para descobrir o que a função `sample()` faz. Em seguida, use-a para escrever uma função que escolha uma linha aleatoriamente de uma matriz e devolva os seus valores.


--------------------------------------------------------------------------------

**11.** Rode `help(paste)` e `help(names)` para descobrir o que as funções `paste()` e `names()` fazem. Em seguida, use-as para escrever um código para gerar a fórmula `mpg ~ cyl + disp + hp + drat + wt + qsec + vs + am + gear + carb` a partir do data frame `mtcars`.

--------------------------------------------------------------------------------




## Respostas

--------------------------------------------------------------------------------

**1.** Calculo o número de ouro no R.

Dica: o número de ouro é dado pela expressão $\frac{1 + \sqrt{5}}{2}$.

**Resposta:**


```r
(1 + sqrt(5))/2
## [1] 1.618034
```



--------------------------------------------------------------------------------

**2.** Qual o resultado da divisão de 1 por 0 no R? E de -1 por 0?

**Resposta:**

Infinito e -Infinito.


```r
1/0
## [1] Inf
-1/0
## [1] -Inf
```

--------------------------------------------------------------------------------

**3.** Quais as diferenças entre `NaN`, `NULL`, `NA` e `Inf`? Digite expressões que retornam cada um desses resultados.

**Resposta:**


```r
# NaN é o resultado de uma operação matemática inválida. 
# Significa Not A Number.

0/0
## [1] NaN

# NULL é o vazio do R. É como se o objeto não existisse.

NULL
## NULL
a = NULL


# veja que um vetor, mesmo sem elementos não é NULL

is.null(integer(length = 0)) 
## [1] FALSE

# NA é uma constante lógica do R. Siginifica Not Availlable. 
# NA pode ser convertido para quase todos os tipos de vetores do R. 
# É usado principalmente para indicar valores faltantes.

NA
## [1] NA
as.numeric(c("1", "2", "a"))
## Warning: NAs introduced by coercion
## [1]  1  2 NA

# Inf é significa infinito. É o resultado de operações matemáticas 
# cujo limite é infinito.

1/0
## [1] Inf
1/Inf
## [1] 0
```

--------------------------------------------------------------------------------

**4.** Sem rodar o código, calcule o que a expressão `5 + 3 * 10 %/% 3 == 15` vai resultar no R. Em seguida, apenas utilizando parênteses, faço a expressão retornar o valore contrário (i.e., se originariamente for `TRUE`, faça retornar `FALSE`).

**Resposta:**

O resultado da parte esquerda é 14, por isso a expressão retornará `FALSE`. Para fazê-la retornar `TRUE`, basta colocar parênteses em volta de `3 * 10`.


```r
5 + (3 * 10) %/% 3 == 15
## [1] TRUE
```

--------------------------------------------------------------------------------

**5.** Por que o código abaixo retorna erro? Arrume o código para retornar o valor `TRUE`.


```r
x <- 4
if(x = 4) {
  TRUE
}
```

**Resposta:**

A expressão `x = 4` está tentando atribuir o valor 4 ao objeto `x` dentro do if, o que não é permitido pois o controlador `if` só aceita valores lógicos. Para corrigir o código e fazê-lo retornar `TRUE`, basta trocar `=` por `==`.


```r
x <- 4
if(x == 4) {
  TRUE
}
## [1] TRUE
```

--------------------------------------------------------------------------------

**6.** Usando `if` e `else`, escreva um código que retorne a string "número" caso o objeto `x` seja da classe `numeric` ou `integer`; a string "palavra" caso o objeto seja da classe `character`; e `NULL` caso contrário.
 
**Resposta:**


```r
x <- 1
# x <- 1L
# x <- "1"

if(is.numeric(x)) {
  "número"
} else if(is.character(x)) {
  "palavra"
} else { 
  NULL
}
## [1] "número"
```

Note que a função `is.numeric()` retorna `TRUE` para as classes `integer` e `numeric`.

--------------------------------------------------------------------------------

**7.** Use o `for` para retornar o valor mínimo do seguinte vetor: `vetor <- c(4, 2, 1, 5, 3)`. Modifique o seu código para receber vetores de qualquer tamanho.

**Resposta:**


```r

vetor <- c(4, 2, 1, 5, 3)
minimo <- Inf

for(i in 1:5) {
  
  if(minimo > vetor[i]) {
    minimo <- vetor[i]
  }
  
}

minimo
## [1] 1
```

**Lembrete**: o R já possui a função `min()` para calcular o mínimo de um conjunto de valores.

--------------------------------------------------------------------------------

**8.** Usando apenas `for` e a função `length()`, construa uma função que calcule a média de um vetor número qualquer. Construa uma condição para a função retornar `NULL` caso o vetor não seja numérico.

**Resposta:**


```r
media <- function(x) {
  
  i <- 1
  tamanho <- length(x)
  soma <- 0
  
  for(i in 1:tamanho){
    soma <- soma + x[i]
  }
  
  return(soma/tamanho)
}

media(1:3)
## [1] 2
```

--------------------------------------------------------------------------------

**9.** Rode `help(runif)` para descobrir o que a função `runif()` faz. Em seguida, use-a para escrever uma função que retorne um número aleatório inteiro entre 0 e 10 (0 e 10 inclusive).

**Resposta:**

A função `runif()` gera números reais aleatórios entre um valor mínimo e um valor máximo.


```r
alea <- function() {
  
  x <- runif(n = 1, min = 0, max = 10)
  x <- round(x)
  
  return(x)
}

alea()
## [1] 4
```

Veja que construímos uma função sem argumentos. Podemos generalizá-la incluindo os argumentos da função `runif()`.


```r
alea <- function(n, min, max) {
  
  x <- runif(n = n, min = min, max = max)
  x <- round(x)
  
  return(x)
}

alea(2, 2, 5)
## [1] 5 2
alea(5, 100, 105)
## [1] 105 105 104 100 103
```

Observe que não há problema em usar os mesmos nomes para os argumentos. Isso se deve aos *environments*. Para saber mais, confira [este post](http://curso-r.com/blog/2017/06/19/2017-06-19-environments/).

--------------------------------------------------------------------------------

**10.** Rode `help(sample)` para descobrir o que a função `sample()` faz. Em seguida, use-a para escrever uma função que escolha uma linha aleatoriamente de uma matriz e devolva os seus valores.

**Resposta:**


```r
matriz <- matrix(runif(20), nrow = 5, ncol = 4)

linha_alea <- function(matriz) {
  
  x <- 1:nrow(matriz)
  
  linha <- sample(x, size = 1)
  
  return(matriz[linha,])
}

matriz
##           [,1]      [,2]      [,3]      [,4]
## [1,] 0.3892763 0.7633635 0.3707031 0.7381129
## [2,] 0.7848258 0.6510383 0.1397464 0.8971824
## [3,] 0.5232812 0.0180222 0.1419734 0.7114565
## [4,] 0.5092140 0.9650082 0.3545131 0.5984268
## [5,] 0.4442231 0.6210985 0.1462894 0.4045183
linha_alea(matriz)
## [1] 0.7848258 0.6510383 0.1397464 0.8971824
```

--------------------------------------------------------------------------------

**11.** Rode `help(paste)` e `help(names)` para descobrir o que as funções `paste()` e `names()` fazem. Em seguida, use-as para escrever um código para gerar a fórmula `mpg ~ cyl + disp + hp + drat + wt + qsec + vs + am + gear + carb` a partir do data frame `mtcars`.

**Resposta:**


```r
variaveis <- names(mtcars)

esq <- "mpg ~ "
dir <- paste(variaveis[-1], collapse = " + ")

formula <- paste0(esq, dir)
as.formula(formula)
## mpg ~ cyl + disp + hp + drat + wt + qsec + vs + am + gear + carb
## <environment: 0x4327790>
```

Observe que a função `paste0()` é equivalente à função `paste()` com o argumento `sep = ""`.

--------------------------------------------------------------------------------

