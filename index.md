---
title: Introdução
date: '2017-01-30'
---





## Introdução

A linguagem `R` é intuitiva. Muita coisa sai do jeito certo no chute! Para ver um exemplo disso, é interessante começar fazendo do R uma grande calculadora.

Mas antes disso, vamos aprender a mexer no RStudio!

--------------------------------------------------------------------------------

<!-- ## Exercícios -->
<!-- Pratique! Será que você consegue resolver os exercícios abaixo? -->
<!-- 1. Calcule o número de ouro no R. -->
<!-- $$ \frac{1 + \sqrt{5}}{2} $$ -->
<!-- 2. O que dá divisão de 1 por 0 no R? E -1 por 0?  -->
<!-- 3. Quais as diferenças entre `NaN`, `NULL`, `NA` e `Inf`? -->
<!-- 4. Tente mentalmente calcular o que dá a conta `5 + 3 * 10 %/% 3 == 15` no R, sem rodar. -->
<!-- 5. Adicionando apenas parênteses, faça a expressão acima retornar o resultado contrário. -->
<!-- 6. O que acontece se você rodar: -->
<!-- ```{r, eval = F} -->
<!-- x <- 4 -->
<!-- if(x = 4) { -->
<!--   'isso aqui apareceu' -->
<!-- } -->
<!-- x -->
<!-- ``` -->
<!-- 7. Como você faria para que o código da pergunta anterior fizesse com que `'isso aqui apareceu'` fosse impresso no console mas nenhum erro aparecesse? -->
<!-- 8.  **Difícil**: Usando `for`, `if` e `else` escreva as seguintes frases no console: -->
<!-- ```{r, eval=FALSE} -->
<!-- > 1 elefante(s) incomoda(m) muita gente -->
<!-- > 2 elefante(s) incomoda(m) incomoda(m) muito mais -->
<!-- > 3 elefante(s) incomoda(m) muita gente -->
<!-- > 4 elefante(s) incomoda(m) incomoda(m) incomoda(m) incomoda(m) muito mais -->
<!-- ``` -->
<!-- *Dica*: Leia o help da função `paste` e preste atenção no argumento `collapse`. -->
<!-- 9. Crie um vetor com o nome `x` que contenha os números `1, 20, 40, 50, 60` no R. -->
<!-- 10. Crie um vetor com o nome `x` de 100 números aleatórios entre 0 e 1. -->
<!-- 11. Calcule a média do vetor criado na questão anterior. -->
<!-- 12. Crie um vetor com 100 elementos. 99 deles são números aleatórios entre 0 e 1 e o último elemento tem o valor `NA`. Calcule também a média deste vetor. -->
<!-- *Dica*: Olhe atentamente os argumentos da função `mean`. -->
<!-- 13. Crie uma função que calcula a média de um vetor. Use `for` ou `while` nesta função. -->
<!-- 14. Crie uma função que simule um dado, ou seja, gera aleatóriamente um número inteiro entre 1 e 6. -->
<!-- 15. Crie uma função que simula o lançamento de `n` dados, e devolve a soma de seus resultados. -->
<!-- 16. **Difícil** Faça um histograma dos resultados da soma de 3 dados. Isto é, crie um vetor com 1000 resultados que aconteceram após somar 3 dados. Em seguida faça o histograma. -->
<!-- **Esses exercícios possuem resposta [aqui](https://curso-r.github.io/verao2017/r-como-calculadora/respostas)** -->



## RStudio

O RStudio é o melhor ambiente de desenvolvimento de R disponível. Você pode [baixar aqui](https://www.rstudio.com/products/rstudio/download/preview/).

Há muitas ferramentas nele que se aprende conforme o uso e há bons materiais sobre na internet (por exemplo [esta página](https://csgillespie.github.io/efficientR/set-up.html#rstudio)). Uma funcionalidade importante que vale citar é a criação de projetos. Uma estrutura sugerida de organização de um projeto é

**Estrutura 1**: Por extensão de arquivo.


```bash
nome_do_projeto/
  - .Rprofile   # códigos para rodar assim que abrir o projeto
  - R/          # Código R, organizado com a-carrega.R, b-prepara bd.R, c-vis.R, d-modela, ...
  - RData/      # Dados em formato .RData
  - csv/        # Dados em .csv
  - png/        # gráficos em PNG
  - nome_do_projeto.Rproj
```

**Estrutura 2**: Típico projeto de análise estatística.


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

**Estrutura 3**: Pacote do R (avançado).


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

Assim que abrir o RStudio você verá 4 quadrantes do jeito que a figura abaixo mostra

![](figures/rstudio-editor.png)

Nela estão dispostos **editor**, **console**, **environment** e **output**.  Normalmente eles vêm nesta ordem, depois você pode organizá-los da forma que preferir. O R vive no quadrante **console**!

--------------------------------------------------------------------------------



## RMarkdown

O RMarkdown é um tipo de documento especial que contém tanto textos quanto códigos de R, tudo escrito em um mesmo lugar. 

O *markdown* nada mais é do que um documento de texto com alguns padrões básicos de formatação, como negrito, itálico, títulos, subtítulos, itens e referências cruzadas. Já os *chunks* são pedaços de códigos em R encapsulados por três crases "```". Os códigos são executados sempre que o documento é processado.


```
## ```{r}
## 
## isto é um chunk. 
## ```
```

<div class='admonition note'>
<p class='admonition-title'>
Nota
</p>
<p>
Este site foi escrito em RMarkdown. Toda vez que aparecer exemplos de código de R é porque havia um chunk no .Rmd original.
</p>
</div>

Para produção de relatórios, o RMarkdown possui algumas vantagens, dentre as quais estão:

1. **Simplicidade e foco**. Permite o usuário a focar na análise e não na formatação do documento.
1. **Versátil**. Pode ser utilizado para gerar documentos em $\LaTeX$, `Word`, `HTML` e apresentaçőes em `beamer`, `pptx` e `HTML` (de vários tipos). Pode ainda gerar sites, livros, dissertaçőes de mestrado e até mesmo dashboards interativos.
1. **Reprodutível**. O RMarkdown nada mais é que um arquivo de texto. Além disso, ele tenta te obrigar a fazer o documento mais autocontido possível. Assim, um documento `.Rmd` é fácil de compartilhar e de ser utilizado pelo receptor. Lembre-se, o receptor pode ser o futuro você! Vale enfatizar que a reprodutibilidade é considerada como um dos princípios fundamentais da ciência. Então só de usar RMarkdown, você já está colaborando com a ciência :)
1. **Flexível**. É possível configurar e criar templates de análises para quaisquer tipos de aplicações e clientes. Os textos podem ser parametrizados por números que variam de versão para versão, por exemplo mensalmente, tudo escrito somente em R. 

Para criar um RMarkdown novo no RStudio é fácil. Clique no botão de criar arquivo e selecione RMarkdown.


```r
knitr::include_graphics("figures/criar_rmarkdown.png")
```

![plot of chunk unnamed-chunk-20](figures/criar_rmarkdown.png)

Para detalhes sobre como utilizar o RMarkdown, leia  [aqui](http://r4ds.had.co.nz/r-markdown.html) e [ aqui](http://rmarkdown.rstudio.com/lesson-1.html).

--------------------------------------------------------------------------------



## R como calculadora

Pelo console é possível executar qualquer comando do R.


```r
1:30
##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
## [24] 24 25 26 27 28 29 30
```

Esse comando é uma forma simplificada de criar um vetor de inteiros de 1 a 30.
Você pode ignorar esses números que aparecem entre parênteses. Na verdade eles 
só indicam o índice do primeiro elemento impresso nessa linha.

<div class='admonition note'>
<p class='admonition-title'>
Quando compilamos?
</p>
<p>
Quem vem de linguagens como o C ou Java, espera que seja necessário compilar o código em texto para o código de máquinas (geralmente um código binário). No R, isso não é necessário. O R é uma linguagem de programação dinâmica que interpreta o seu código enquanto você o executa.
</p>
</div>

Tente jogar no console `2 * 2 - (4 + 4) / 2`. Pronto. Com essa simples expressão você já é capaz de imaginar (e certeiramente) como pedir ao R para fazer qualquer tipo de operação aritmética. Lição aprendida!

Além do mais, as operações e suas precedências são mantidas como na matemática, ou seja, divisão e multiplicação são calculadas antes da adição e subtração. E os parênteses nunca são demais!

Agora que você já conhece o RStudio, digite a expressão `2 * 2 - (4 + 4) / 2` no
**console** e tecle `Enter`. Uma outra forma de chamar uma expressão é escrever
o código no **editor** e teclar `Ctrl + Enter` ou `Ctrl + R`. Assim o comando é enviado para o **console** onde é diretamente executado.

Se você digitar um comando incompleto, como `5 + ` e apertar `Enter`, o R irá mostrar um `+`, o que não tem nada a ver com somar alguma coisa, e sim significa que o R está esperando que vocę complete o seu comando. Termine o seu comando ou aperte `Esc` para recomeçar.

```
> 5 -
+ 
+ 5
[1] 0
```

Se você digitar um comando que o R não reconhecer, ele irá retornar uma mensagem de erro. Não entre em pânico. Ele só está avisando que não conseguiu interpretar o comando. Depois você já pode digitar mais um comando.

```
> 5 % 5
Error: unexpected input in "5 % 5"
> 5 - 5
[1] 0
```

--------------------------------------------------------------------------------



## Pedindo Ajuda

No R, há quatro principais entidades para recorrer quando se precisa de ajuda:

- Help / documentação do R (comandos `help(funcao)` ou `?funcao`)
- Stack Overflow
- Google
- Coleguinha

### Documentação do R

A documentação do R serve para você aprender a usar uma determinada função.


```r
?mean
help(mean)
```

Cinco dicas:

- Os exemplos no final são particularmente úteis.
- Atente-se na parte **Usage** para ter noção de como usar.
- Os parâmetros estăo descritos na parte **Arguments**. Identifique quais tipos de objetos eles recebem.
- Caso essa função não atenda às suas necessidades, a seção **See Also** sugere funções relacionadas.
- Alguns pacotes possuem tutorias de uso mais completos. Esses textos são chamados de `vignettes` e podem ser acessados com a função `vignette(package = 'nomeDoPacote')`. Por exemplo, `vignette(package = 'dplyr')`. Depois de ver a lista de artigos, escolha um nome e rode `vignette(topic = 'nome', package = 'nomeDoPacote')`. Por exemplo, `vignette(topic = 'introduction', package = 'dplyr')`

### Google

Há uma comunidade gigantesca de usuários de R que todos os dias geram infinidades de conteúdos e discussões. Não raro, você irá encontrar discussões sobre o seu problema simplesmente jogando o copiar/colar do seu erro no diretamente Google. Essa deve ser sua primeira tentativa!

Exemplo (repare no 'R' adicionado na busca, também ajuda):


```r
log("5")
## Error in log("5"): non-numeric argument to mathematical function
```

![](figures/ajuda_google.png)

### Stack Overflow

O [Stack Overflow](http://stackoverflow.com/) e o [Stack Overflow em Português](http://pt.stackoverflow.com/) são sites de Pergunta e Resposta amplamente utilizados por todas as linguagens de programação e R é uma delas. É tão utilizado que nos EUA eles chegam a usar a reputaçăo dos usuários como diferenciais no currículo!

Provavelmente o Google te indicará uma página deles quando você estiver procurando ajuda. E quando todas as fontes possíveis de ajuda falharem o Stack Overflow te dará o espaço para **criar sua própria pergunta**.

**Um ponto importante:** Como fazer uma **boa** pergunta no Stack Overflow?

No site tem um tutorial com uma lista de boas práticas, [que se encontra aqui](http://pt.stackoverflow.com/help/how-to-ask). Algumas dicas são

- Ser conciso
- Ser específico
- Ter mente aberta
- Ser gentil

Porém, no caso do R há outro requisito que vai aumentar muito sua chance de ter uma boa resposta: **exemplinho minimal e reprodutível**.

- Ser **minimal**: usar bancos de dados menores e utilizar pedaços de códigos apenas suficientes para gerar o seu problema. Năo precisa de banco de dados de um milhăo de linhas e nem colocar o seu código inteiro para mostrar seu problema.

- Ser **reprodutível**: o seu código deve rodar fora da sua máquina. Se você não fornecer uma versão do seu problema que rode (ou que imite seu erro), as pessoas vão logo desistir de te ajudar. Por isso, nunca coloque bancos de dados que só você tem acesso. Em vez disso, use bancos de dados que já vem no R ou disponibilize um exemplo (possivelmente anonimizado) em `.csv` na web para baixar. E se precisar utilizar funções diferentes, coloque as `library`'s correspondentes.

--------------------------------------------------------------------------------



## Instalar pacotes

O grande trunfo do R são seus pacotes então é uma boa você ficar bastante à vontade em instalar e atualizar muitos e muitos pacotes ao longo da sua experiência com o R.

Existem três principais maneiras de instalar pacotes. Em ordem de frequência, são:

- Via CRAN (Comprehensive R Archive Network) `install.packages("magrittr")`
- Via Github `devtools::install_github("rstudio/shiny")`
- Via arquivo .zip/.tar.gz `install.packages("C:/caminho/pacote.zip", repos = NULL)`

### Via CRAN

Quando quiser utilizar um pacote, instale usando a função `install.packages("nome_do_pacote")`. Por exemplo:


```r
install.packages("magrittr")
```



E de agora em diante basta carregar o pacote com `library(magrittr)`. Não precisa mais instalar.

<div class="dica">
Dica! Escreva `nome_do_pacote::nome_da_funcao()` se quiser usar apenas uma função de um determinado pacote. O operador `::` serve para isso. Essa forma também é útil quando se tem duas funções com o mesmo nome e precisamos garantir que o código vá usar a função do pacote correto.
</div>

### Via Github

Desenvolvedores costumam disponibilizar a última versão de seus pacotes no Github e alguns deles sequer estão no CRAN. Mesmo assim ainda é possível utilizá-los instalando diretamente pelo github. O comando é igualmente simples:


```r
devtools::install_github("rstudio/shiny")
```

O que será necessário é o username e o nome do repositório. No exemplo o username foi "rstudio" e o pacote foi "shiny". 

Não se preocupe, geralmente esses pacotes que ficam no github possuem um `README` cuja primeira instrução é de como instalar o pacote via github. Se não tiver, provavelmente este pacote não te merece =)!

### Via arquivo .zip/.tar.gz

Se você precisar instalar um pacote que está zipado no seu computador (ou em algum servidor) há a opção de assim o fazer sem maiores problemas. 


```r
install.packages("C:/caminho/para/o/arquivo/zipapo/pacote.zip", repos = NULL)
```

É quase igual a instalar pacotes via CRAN, com a diferença que agora o nome do pacote é o caminho inteiro até o arquivo, e com o parâmetro `repos = NULL` para informar que estamos instalando a partir da máquina local.

A aba ***Packages*** do RStudio ajuda a administrar seus pacotes também.

![](figures/instalar_pacote_rstudio.png)

--------------------------------------------------------------------------------



## Controles de Fluxo

Como toda boa linguagem de programação, o R possui estruturas de `if`'s, `else`'s, `for`'s e etc. (os controles de fluxo) que são importantes na hora de programar. 

### `if` e `else`

O seguinte trecho de código só será executado se o objeto `x` for igual a 1.


```r
x <- 2
if(x == 1) {
  print("oi")
}
```


```r
x <- 1
if(x == 1) {
  print("oi")
}
## [1] "oi"
```

O R só vai executar o que está na expressão dentro das chaves `{}` se o que estiver dentro dos parênteses `()` retornar `TRUE`.

A sintaxe com o `else` e o `if else` é


```r
if(<condição1>) {
  
} else if (<condição2>) {
  
} else if (<condição3>) {
  
} else {
  
}
```

<div class='admonition note'>
<p class='admonition-title'>
Diferença entre SQL e R nas comparações lógicas
</p>
<p>
- **Igualdade** no SQL é só um sinal de igual: `2 = 1`. No R são dois: `2 == 1`.
- **Diferença** O teste de diferente no R é `!=` ao invés de de `<>`.
- **Negação** ao invés de usar a palavra `not` que nem no SQL, usamos `!`. Por exemplo, `entidade_id not in ('100515')` fica `!entidade_id %in% c('100515')`.
</p>
</div>


### for

Sintaxe do `for`:


```r
for(contador in 1:5){
  # várias coisas...
  print(contador)
}
## [1] 1
## [1] 2
## [1] 3
## [1] 4
## [1] 5
```

Outro exemplo:


```r
vetor <- 30:35
indices <- seq_along(vetor)
for(i in indices){
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

--------------------------------------------------------------------------------




## Objetos


```r
a <- 1
a
## [1] 1
```

O R permite que você salve dados guardando estes dentro de um objeto. 

No exemplo acima, salvamos o valor `1` em `a` e sempre que o R encontrar o nome `a` ele vai substituir por `1`.

<div class='admonition note'>
<p class='admonition-title'>
Atenção!
</p>
<p>
O R entende letras maiúsculas e minúsculas, isto é `a` é considerado um objeto diferente de `A`.
</p>
</div>

### Objetos atômicos

Existem cinco classes básicas ou "atômicas" no R:

- character `"UAH!"` (é o varchar do SQL)
- numeric `0.95` (números reais)
- integer `100515` (inteiros)
- complex `2 + 5i` (números complexos, a + bi)
- logical `TRUE` (booleanos, TRUE/FALSE)

### Vetores

Vetores no R são os objetos mais simples que podem guardar objetos atômicos.


```r
vetor <- c(1, 2, 3, 4)
class(vetor)
## [1] "numeric"
```

De forma bastante intuitiva você pode fazer operações com vetores.


```r
vetor - 1
## [1] 0 1 2 3
```

Quando você faz `vetor - 1`, o R subtrai `1` de cada um dos elementos do vetor. O mesmo acontece quando você faz qualquer operação aritmética com vetores no R. Tente jogar no console


```r
vetor / 2
vetor * 10
```

Você também pode fazer operações que envolvem mais de um vetor:


```r
vetor * vetor
## [1]  1  4  9 16
```

Neste caso, o R irá alinhar os dois vetores e multiplicar elemento por elemento. Isso pode ficar um pouco confuso quando os dois vetores não possuem o mesmo tamanho:


```r
vetor2 <- 1:3
vetor * vetor2
## Warning in vetor * vetor2: longer object length is not a multiple of
## shorter object length
## [1] 1 4 9 4
```

Agora o R alinhou os dois vetores, e como eles não possuiam o mesmo tamanho, ele foi repetindo o menor vetor até completar o vetor maior. 

Esse comportamento é chamado de **reciclagem**. Isso é útil para fazer operações com os vetores elementos por elementos (vetorizadamente), mas as vezes pode ser confuso. Com o tempo você aprenderá a se aproveitar desse comportamento.

### Misturando objetos

<div class='admonition note'>
<p class='admonition-title'>
Vetores são homogêneos
</p>
<p>
Os elementos de um vetor são sempre da mesma classe. Ou todos são numéricos, ou são todos character e assim por diante. Não dá para ter um número e um character no mesmo vetor, por exemplo.
</p>
</div>



```r
y <- c(1.7, "a")  ## character
y <- c(TRUE, 2)   ## numeric
y <- c(TRUE, "a") ## character
```

Se colocarmos duas ou mais classes diferentes dentro de um mesmo vetor, o R vai forçar que todos os elementos passem a pertencer à mesma classe. O número `1.7` viraria `"1.7"` se fosse colocado ao lado de um `"a"`.

A ordem de precedência é 

**DOMINANTE** `character > complex > numeric > integer > logical` **RECESSIVO**

### Forçando classes explicitamente

Assim como o `convert()` do SQL faz, você pode coagir um objeto a ser de uma classe da sua escolha com as funções `as.character()`, `as.numeric()`, `as.integer()` e `as.logical()`. 


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

Se o R não entender como coagir uma classe na outra ele soltará um `warning` informado que colocou `NA` no lugar.


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
O `NA` tem o mesmo papel que o `null` do SQL. Porém, há um `NULL` no R também, com diferenças sutis que vamos abordar mais adiante. Năo confundir!
</p>
</div>

### Matrizes

Matrizes săo vetores com duas dimensőes (e por isso só possuem elementos de uma mesma classe).


```r
m <- matrix(1:6, nrow = 2, ncol = 3)
m
##      [,1] [,2] [,3]
## [1,]    1    3    5
## [2,]    2    4    6
dim(m) # funçăo dim() retorna a dimensăo do objeto.
## [1] 2 3
```

Repare que os números de 1 a 6 foram dispostos na matriz de coluna a coluna (*column-wise*), ou seja, preenchendo de cima para baixo e depois da esquerda para a direita.

**Utilidades**


```r
m[3,  ]   # seleciona uma linha
m[ , 2]   # seleciona uma coluna
m[1, 2]   # seleciona um elemento
t(m)      # matriz transposta
m %*% n   # multiplicação matricial
solve(m)  # matriz inversa
```

### Fatores

Fatores podem ser vistos como vetores de inteiros que possuem rótulos (labels).


```r
sexo <- c("M", "H", "H", "H", "M", "M", "H")
fator <- as.factor(sexo)
fator
## [1] M H H H M M H
## Levels: H M
as.numeric(fator)
## [1] 2 1 1 1 2 2 1
```

Eles são úteis para representar uma variável categórica (nominal e ordinal) e têm relevância em modelagem, onde serão tratados de maneira especial em funções como `glm()`. 

A funçăo `levels()` retorna os rótulos do fator:


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
Quando um vetor de números está como `factor`. Ao tentar transformar o vetor em `numeric`, você receberá um vetor de inteiros que não tem nada a ver com os valores originais!
</p>
</div>


```r
numeros <- factor(c("10", "55", "55", "12", "10", "-5", "-90"))
```

```
as.numeric(numeros)
## [1] 3 5 5 4 3 1 2    # <-- Por essa eu năo esperava!
```

Para evitar isso, use `as.character()` antes de transformar para número.

```
as.numeric(as.character(numeros))
## [1]  10  55  55  12  10  -5 -90   # <-- Agora está OK
```

### Valores especiais

Existem valores reservados para representar dados faltantes, infinitos, e indefiniçőes matemáticas.

- **NA** (Not Available) significa dado faltante/indisponível. É o `null` do SQL ou o `.` do SAS. O `NA` tem uma classe, podemos ter `NA` numeric, `NA` character e etc.
- **NaN** (Not a Number) representa indefinições matemáticas, como `0/0` e `log(-1)`. Um `NaN` é um `NA`, mas a recíproca não é verdadeira.
- **Inf** (Infinito) é um número muito grande ou o limite matemático, por exemplo, `1/0` e `10^310`. Aceita sinal negativo `-Inf`. 
- **NULL** representa a ausęncia de informação. Conceitualmente, a diferença entre `NA` e `NULL` é sutil, mas no R o `NA` está mais alinhado com os conceitos de estatística (ou como gostaríamos que os dados faltantes se comportassem em análise de dados) e o `NULL` está em sintonia com comportamentos de lógica de programação.
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

É um dos objetos mais importantes para armazenar dados e vale a pena saber manuseá-los bem. Existem muitas funçães que fazem das listas objetos incrivelmente úteis.

Criamos uma lista pela função `list()`, que aceita um número arbitrário de elementos. Listas aceitam QUALQUER tipo de objeto. Podemos ter listas dentro de listas, por exemplo. Como para quase todos os objetos no R, as funçőes `is.list()` e `as.list()` também existem.

Na lista `pedido` abaixo temos `numeric`, `Date`, `character`, vetor de `character` e `list` contida em uma lista:


```r
pedido <- list(pedido_id = 8001406,
               pedido_registro = as.Date("2016-12-12"),
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

**Utilidades**


```r
pedido$cpf     # elemento chamado 'cpf'
pedido[1]      # nova lista com apenas o primeiro elemento
pedido[[2]]    # segundo elemento
pedido["nome"] # nova lista com apenas o elemento chamado 'nome'
```

Certamente você se deparará com listas quando for fazer análise de dados com o R, nos tópicos mais aplicados iremos aprofundar sobre o tema. O pacote [purrr](https://github.com/hadley/purrr) contribui com funcionalidades incríveis para listas.

### `data.frame`

Um `data.frame` é o mesmo que uma tabela do SQL ou um spreadsheet do Excel, por isso são objetos muito importantes. 

Usualmente seus dados serão importados para um objeto `data.frame` e em grande parte do curso os teremos como principal objeto de estudo.

`data.frame`s são listas especiais em que todos os seus elementos possuem **o mesmo comprimento**. Cada elemento dessa lista pode ser pensado como uma coluna da tabela e seu comprimento representa o número de linhas. 

Já que são listas, essas colunas podem ser de classes diferentes. Essa é a grande diferença entre `data.frame`s e matrizes. Algumas funções úteis:

- `head()` Mostra as primeiras 6 linhas.
- `tail()` Mostra as últimas 6 linhas.
- `dim()` Número de linhas e de colunas.
- `names()` Os nomes das colunas (variáveis).
- `str()` Estrutura do data.frame. Mostra, entre outras coisas, as classes de cada coluna.
- `cbind()` Acopla duas tabelas lado a lado.
- `rbind()` Empilha duas tabelas.

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

#### Exemplo de data.frame: iris {-}


```r
head(iris)  
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 1          5.1         3.5          1.4         0.2  setosa
## 2          4.9         3.0          1.4         0.2  setosa
## 3          4.7         3.2          1.3         0.2  setosa
## 4          4.6         3.1          1.5         0.2  setosa
## 5          5.0         3.6          1.4         0.2  setosa
## 6          5.4         3.9          1.7         0.4  setosa
str(iris)
## 'data.frame':	150 obs. of  5 variables:
##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
##  $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...
```

--------------------------------------------------------------------------------



## Funções

O R vem com muitas funções implementadas com as quais você pode fazer muitas  tarefas complicadas, como gerar números aleatórios. Geralmente o nome das funções é bem intuitivo, por exemplo `mean` é a função que calcula a média, `round` é a função que arredonda um número, etc.


```r
round(5.634)
## [1] 6
```

Para entender melhor o funcionamento das funções no R considere o seguinte exemplo.


```r
die <- 1:6
round(mean(die))
## [1] 4
```

A ilustração abaixo mostra o que acontece quando você executa `round(mean(die))` no R.

![](figures/round.png)

Passamos dados para as funções por meio de argumentos. No R, esses argumentos estão documentados na página de ajuda de cada uma das funções, que pode ser acessada digitando `help(nome_da_funcao)` ou `?nome_da_funcao`.

### Criando suas próprias funções

Sintaxe:


```r
soma <- function(x, y = 0) {
  resposta <- x + y
  return(resposta)
}
```

A função acima tem 

- o nome `soma`
- os argumentos `x` e `y`
- o corpo `resposta <- x + y`
- o valor padrão `0` para o argumento `y` (`y = 0`)

Para usá-la é como qualquer outra função:


```r
soma(2, 1) # soma de 2 + 1
## [1] 3
soma(2) # soma de 2 + 0
## [1] 2
```

Atente-se que o argumento `y` possui um valor padrão `0`. Isso quer dizer que ele valerá zero caso o usuário não passe nenhum valor a ele explicitamente.

O [Advanced-R](http://adv-r.had.co.nz/) é um excelente livro para quem quiser masterizar a arte de se fazer funções. 

--------------------------------------------------------------------------------



## Gráficos - base

O R já vem com funções básicas que fazem gráficos estatísticos de todas as naturezas. 

- Vantagens: São rápidas e simples.
- Desvantagens: São feias e difíceis para gerar gráficos complexos.

### Gráfico de dispersão

**Funçăo** `plot()`

Parâmetros principais (ver `help(hist)` para mais detalhes):

- `x`, `y` Vetores para representarem os eixos x e y.
- `type` Tipo de gráfico. Pode ser pontos, linhas, escada e etc.

<div class='admonition note'>
<p class='admonition-title'>
Atenção!
</p>
<p> 
Além de gerar gráficos de dispersão, tentar chamar a função `plot(objeto_diferentao)` para qualquer tipo de objeto do R geralmente sai um gráfico interessante! Sempre tente fazer isso. A menos que seu objeto seja um `data.frame` com milhares de colunas!!!
</p>
</div>


```r
n <- 100
x <- 1:n
y <- 5 + 2 * x + rnorm(n, sd = 30)
plot(x, y)
```

![plot of chunk unnamed-chunk-59](figures//unnamed-chunk-59-1.png)

O parâmetro `type = "l"` indica que queremos que os pontos sejam interligados por linhas.


```r
plot(x, y, type = "l")
```

![plot of chunk unnamed-chunk-60](figures//unnamed-chunk-60-1.png)

### Histograma

**Funçăo** `hist()`

Parâmetros principais (ver `help(hist)` para mais detalhes):

- `x` O vetor numérico pra histogramar.
- `breaks` O número (aproximado) de retângulos.


```r
hist(rnorm(1000))
```

![plot of chunk unnamed-chunk-61](figures//unnamed-chunk-61-1.png)

### Boxplot

**Função** `boxplot()`

Parâmetros principais (ver `help(boxplot)` para mais detalhes):

**Uma variável**


```r
boxplot(InsectSprays$count, col = "lightgray")
```

![plot of chunk unnamed-chunk-62](figures//unnamed-chunk-62-1.png)

**Duas variáveis** Usamos fórmula e o parâmetro `data`!


```r
boxplot(count ~ spray, data = InsectSprays, col = "lightgray")
```

![plot of chunk unnamed-chunk-63](figures//unnamed-chunk-63-1.png)

### Gráfico de barras

**Função** `table()`, `barplot()`

Primeiro crie uma tabela de contagens (ou qualquer outro sumário) e depois crie o gráfico com `barplot()`.

**Tabela com uma variável** usando `table()`.


```r
data(diamonds, package = "ggplot2")
## Error in find.package(package, lib.loc, verbose = verbose): there is no package called 'ggplot2'
tabela <- table(diamonds$color)
## Error in table(diamonds$color): object 'diamonds' not found
tabela
## Error in eval(expr, envir, enclos): object 'tabela' not found
barplot(tabela)
## Error in barplot(tabela): object 'tabela' not found
```

**Tabela com duas variáveis** em uma tabela de dupla entrada.


```r
VADeaths
##       Rural Male Rural Female Urban Male Urban Female
## 50-54       11.7          8.7       15.4          8.4
## 55-59       18.1         11.7       24.3         13.6
## 60-64       26.9         20.3       37.0         19.3
## 65-69       41.0         30.9       54.6         35.1
## 70-74       66.0         54.3       71.1         50.0
barplot(VADeaths) 
```

![plot of chunk unnamed-chunk-65](figures//unnamed-chunk-65-1.png)

--------------------------------------------------------------------------------



## Fórmulas


```r
formula <- y ~ x1 + x2
class(formula)
## [1] "formula"
```

Fórmulas são coisas do tipo `y ~ x` e as funções as usam de maneiras diversas, mas o exemplo mais emblemático vem da modelagem estatística.

A função `lm()` é a que ajusta uma regressão linear no R e `lm(y ~ x)` lê-se "regressão linear de y explicada por x".


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

No caso específico das regressões lineares, são nas fórmulas que conseguimos descrever as variáveis explicativas e suas interações. A fórmula `y ~ x1 * x2` significa "y regredido por x1, x2 e a interação entre x1 e x2". Fórmulas aparecem frequentemente em tarefas de modelagem.

Demais usos de fórmulas aparecerão em outras funções (como o `ggplot`) com outros significados e a documentação nos dirá como usá-las.

--------------------------------------------------------------------------------



## Miscelâneas

### Vetor de letras do alfabeto


```r
letters
##  [1] "a" "b" "c" "d" "e" "f" "g" "h" "i" "j" "k" "l" "m" "n" "o" "p" "q"
## [18] "r" "s" "t" "u" "v" "w" "x" "y" "z"
LETTERS
##  [1] "A" "B" "C" "D" "E" "F" "G" "H" "I" "J" "K" "L" "M" "N" "O" "P" "Q"
## [18] "R" "S" "T" "U" "V" "W" "X" "Y" "Z"
```

### Operadores aritméticos


|Operador      |Descrição                            |
|:-------------|:------------------------------------|
|x + y         |Adição de x com y                    |
|x - y         |Subtração de y em x                  |
|x \* y        |Multiplicaçăo de x e y               |
|x / y         |Divisão de x por y                   |
|x^y ou x\*\*y |x elevado a y-ésima potência         |
|x%%y          |Resto da divisão de x por y (módulo) |
|x%/%y         |Parte inteira da divisão de x por y  |

### Operadores lógicos


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


<script src="https://cdn.datacamp.com/datacamp-light-latest.min.js"></script>




<script src="https://cdn.datacamp.com/datacamp-light-latest.min.js"></script>




1. Calcule o número de ouro no R.

$$ \frac{1 + \sqrt{5}}{2} $$

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiIjIERpZ2l0ZSBhIGV4cHJlc3NcdTAwZTNvIHF1ZSBjYWxjdWxhIG8gblx1MDBmYW1lcm8gZGUgb3Vyby5cbiIsInNvbHV0aW9uIjoiIyBEaWdpdGUgYSBleHByZXNzXHUwMGUzbyBxdWUgY2FsY3VsYSBvIG5cdTAwZmFtZXJvIGRlIG91cm8uXG4oMSArIHNxcnQoNSkpLzIiLCJzY3QiOiJ0ZXN0X291dHB1dF9jb250YWlucyhcIjEuNjE4MDM0XCIsIGluY29ycmVjdF9tc2cgPSBcIlRlbSBjZXJ0ZXphIGRlIHF1ZSBpbmRpY291IGEgZXhwcmVzc1x1MDBlM28gY29ycmV0YW1lbnRlP1wiKVxuc3VjY2Vzc19tc2coXCJDb3JyZXRvIVwiKSJ9</div>





2. O que dá divisão de 1 por 0 no R? E -1 por 0? 

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiIxLzBcbi0xLzAiLCJzY3QiOiJ0ZXN0X291dHB1dF9jb250YWlucyhcIkluZlwiLCBpbmNvcnJlY3RfbXNnID0gXCJUZW0gY2VydGV6YSBkZSBxdWUgaW5kaWNvdSBhIGV4cHJlc3NcdTAwZTNvIGNvcnJldGFtZW50ZT9cIilcbnRlc3Rfb3V0cHV0X2NvbnRhaW5zKFwiLUluZlwiLCBpbmNvcnJlY3RfbXNnID0gXCJUZW0gY2VydGV6YSBkZSBxdWUgaW5kaWNvdSBhIGV4cHJlc3NcdTAwZTNvIGNvcnJldGFtZW50ZT9cIilcbnN1Y2Nlc3NfbXNnKFwiQ29ycmV0byFcIikifQ==</div>



3. Quais as diferenças entre `NaN`, `NULL`, `NA` e `Inf`? Digite expressões que
retornam cada um desses resultados.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiIjIE5hTlxuXG4jIE5VTExcblxuIyBOQVxuXG4jIEluZlxuIiwic29sdXRpb24iOiIjIE5hTiBcdTAwZTkgbyByZXN1bHRhZG8gZGUgdW1hIG9wZXJhXHUwMGU3XHUwMGUzbyBtYXRlbVx1MDBlMXRpY2EgaW52XHUwMGUxbGlkYS4gU2lnbmlmaWNhIE5vdCBBIE51bWJlclxuMC8wXG4jIE5VTEwgXHUwMGU5IG8gdmF6aW8gZG8gUi4gXHUwMGM5IGNvbW8gc2UgbyBvYmpldG8gblx1MDBlM28gZXhpc3Rpc3NlXG5OVUxMXG5hID0gTlVMTFxuaXMubnVsbChpbnRlZ2VyKGxlbmd0aCA9IDApKSAjIHZlamEgcXVlIHVtIHZldG9yLCBtZXNtbyBzZW0gZWxlbWVudG9zIG5cdTAwZTNvIFx1MDBlOSBOVUxMXG4jIE5BIFx1MDBlOSB1bWEgY29uc3RhbnRlIGxcdTAwZjNnaWNhIGRvIFIuIFNpZ2luaWZpY2EgTm90IEF2YWlsbGFibGUuIE5BIHBvZGUgc2VyIFxuIyBjb252ZXJ0aWRvIHBhcmEgcXVhc2UgdG9kb3Mgb3MgdGlwb3MgZGUgdmV0b3JlcyBkbyBSLiBcdTAwYzkgdXNhZG8gcHJpbmNpcGFsbWVudGUgcGFyYVxuIyBpbmRpY2FyIHZhbG9yZXMgZmFsdGFudGVzLlxuTkFcbiMgSW5mIFx1MDBlOSBzaWduaWZpY2EgaW5maW5pdG8uIFx1MDBjOSBvIHJlc3VsdGFkbyBkZSBvcGVyYVx1MDBlN1x1MDBmNWVzIG1hdGVtXHUwMGUxdGljYXMgY3VqbyBsaW1pdGUgXHUwMGU5IGluZmluaXRvLlxuMS8wXG4xL0luZiJ9</div>



4. Tente mentalmente calcular o que dá a conta `5 + 3 * 10 %/% 3 == 15` no R, sem rodar.

5. Adicionando apenas parênteses, faça a expressão acima retornar o resultado contrário.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiI1ICsgMyAqIDEwICUvJSAzID09IDE1Iiwic29sdXRpb24iOiI1ICsgKDMgKiAxMCkgJS8lIDMgPT0gMTUiLCJzY3QiOiJ0ZXN0X291dHB1dF9jb250YWlucyhcIlRSVUVcIiwgaW5jb3JyZWN0X21zZyA9IFwiVGVtIGNlcnRlemEgZGUgcXVlIGluZGljb3UgYSBleHByZXNzXHUwMGUzbyBjb3JyZXRhbWVudGU/XCIpXG5zdWNjZXNzX21zZyhcIkNvcnJldG8hXCIpIn0=</div>





6. O que acontece se você rodar:


```r
x <- 4
if(x = 4) {
  'isso aqui apareceu'
}
x
```



<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJ4IDwtIDRcbmlmKHggPSA0KSB7XG4gICdpc3NvIGFxdWkgYXBhcmVjZXUnXG59XG54In0=</div>

7. Como você faria para que o código da pergunta anterior fizesse com que `'isso aqui apareceu'` fosse impresso no console mas nenhum erro aparecesse?

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJ4IDwtIDRcbmlmKHggPSA0KSB7XG4gICdpc3NvIGFxdWkgYXBhcmVjZXUnXG59XG54Iiwic29sdXRpb24iOiJ4IDwtIDRcbmlmKHggPT0gNCkge1xuICAnaXNzbyBhcXVpIGFwYXJlY2V1J1xufVxueCIsInNjdCI6InRlc3Rfb3V0cHV0X2NvbnRhaW5zKFwiaXNzbyBhcXVpIGFwYXJlY2V1XCIsIGluY29ycmVjdF9tc2cgPSBcIlRlbSBjZXJ0ZXphIGRlIHF1ZSBpbmRpY291IGEgZXhwcmVzc1x1MDBlM28gY29ycmV0YW1lbnRlP1wiKVxudGVzdF9lcnJvcigpXG5zdWNjZXNzX21zZyhcIkNvcnJldG8hXCIpIn0=</div>





--------------------------------------------------------------------------------



<script src="https://cdn.datacamp.com/datacamp-light-latest.min.js"></script>




1. 

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiIoMSArIHNxcnQoNSkpLzIifQ==</div>

2. 

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiIxLzBcbi0xLzAifQ==</div>

3. 

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiIjIE5hTiBcdTAwZTkgbyByZXN1bHRhZG8gZGUgdW1hIG9wZXJhXHUwMGU3XHUwMGUzbyBtYXRlbVx1MDBlMXRpY2EgaW52XHUwMGUxbGlkYS4gU2lnbmlmaWNhIE5vdCBBIE51bWJlclxuMC8wXG4jIE5VTEwgXHUwMGU5IG8gdmF6aW8gZG8gUi4gXHUwMGM5IGNvbW8gc2UgbyBvYmpldG8gblx1MDBlM28gZXhpc3Rpc3NlXG5OVUxMXG5hID0gTlVMTFxuaXMubnVsbChpbnRlZ2VyKGxlbmd0aCA9IDApKSAjIHZlamEgcXVlIHVtIHZldG9yLCBtZXNtbyBzZW0gZWxlbWVudG9zIG5cdTAwZTNvIFx1MDBlOSBOVUxMXG4jIE5BIFx1MDBlOSB1bWEgY29uc3RhbnRlIGxcdTAwZjNnaWNhIGRvIFIuIFNpZ2luaWZpY2EgTm90IEF2YWlsbGFibGUuIE5BIHBvZGUgc2VyIFxuIyBjb252ZXJ0aWRvIHBhcmEgcXVhc2UgdG9kb3Mgb3MgdGlwb3MgZGUgdmV0b3JlcyBkbyBSLiBcdTAwYzkgdXNhZG8gcHJpbmNpcGFsbWVudGUgcGFyYVxuIyBpbmRpY2FyIHZhbG9yZXMgZmFsdGFudGVzLlxuTkFcbiMgSW5mIFx1MDBlOSBzaWduaWZpY2EgaW5maW5pdG8uIFx1MDBjOSBvIHJlc3VsdGFkbyBkZSBvcGVyYVx1MDBlN1x1MDBmNWVzIG1hdGVtXHUwMGUxdGljYXMgY3VqbyBsaW1pdGUgXHUwMGU5IGluZmluaXRvLlxuMS8wXG4xL0luZiJ9</div>

5.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiI1ICsgKDMgKiAxMCkgJS8lIDMgPT0gMTUifQ==</div>

6. 

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiI+IHggPC0gNFxuPiBpZih4ID0gNCkge1xuRXJybzogJz0nIGluZXNwZXJhZG8gaW4gXCJpZih4ID1cIlxuPiAgICdpc3NvIGFxdWkgYXBhcmVjZXUnXG5bMV0gXCJpc3NvIGFxdWkgYXBhcmVjZXVcIlxuPiB9XG5FcnJvOiAnfScgaW5lc3BlcmFkbyBpbiBcIn1cIlxuPiB4XG5bMV0gNCJ9</div>

7.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJ4IDwtIDRcbmlmKHggPT0gNCkge1xuICAnaXNzbyBhcXVpIGFwYXJlY2V1J1xufVxueCJ9</div>

8.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJmb3IgKGkgaW4gMTo0KXtcbiAgaWYoaSAlJSAyID09IDApe1xuICAgIHByaW50KHBhc3RlKGksIFwiZWxlZmFudGUocylcIiwgcGFzdGUocmVwKFwiaW5jb21vZGEobSlcIiwgdGltZXMgPSBpKSwgY29sbGFwc2UgPSBcIiBcIiksIFwibXVpdG8gbWFpc1wiKSlcbiAgfSBlbHNlIHtcbiAgIHByaW50KHBhc3RlKGksIFwiZWxlZmFudGUocykgaW5jb21vZGEobSkgbXVpdGEgZ2VudGVcIikpIFxuICB9XG59In0=</div>

9.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJ4IDwtIGMoMSwgMjAsIDQwLCA1MCwgNjApIn0=</div>

10.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJ4IDwtIHJ1bmlmKDEwMCkifQ==</div>

11.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJtZWFuKHgpIn0=</div>

12.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJ4IDwtIGMocnVuaWYoOTkpLCBOQSlcbm1lYW4oeCwgbmEucm0gPSBUKSJ9</div>

13.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJtZWRpYSA8LSBmdW5jdGlvbih4KXtcbiAgaSA8LSAxXG4gIHRhbWFuaG8gPC0gbGVuZ3RoKHgpXG4gIHNvbWEgPC0gMFxuICBmb3IoaSBpbiAxOnRhbWFuaG8pe1xuICAgIHNvbWEgPC0gc29tYSArIHhbaV1cbiAgfVxuICByZXR1cm4oc29tYS90YW1hbmhvKVxufSJ9</div>

14.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJkYWRvIDwtIGZ1bmN0aW9uKCl7XG4gIHNhbXBsZSgxOjYsIDEpXG59In0=</div>

15.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJzb21hX2RhZG9zIDwtIGZ1bmN0aW9uKG4pe1xuICBzb21hIDwtIDBcbiAgZm9yKGkgaW4gMTpuKXtcbiAgICBzb21hIDwtIHNvbWEgKyBzYW1wbGUoMTo2LCAxKVxuICB9XG4gIHJldHVybihzb21hKVxufSJ9</div>

16.

<div data-datacamp-exercise data-height="300" data-encoded="true">eyJsYW5ndWFnZSI6InIiLCJzYW1wbGUiOiJyZXN1bHRhZG9zIDwtIGludGVnZXIobGVuZ3RoID0gMTAwMClcbmZvcihpIGluIDE6MTAwMCl7XG4gIHJlc3VsdGFkb3NbaV0gPC0gc29tYV9kYWRvcygzKVxufVxuaGlzdChyZXN1bHRhZG9zKSJ9</div>


