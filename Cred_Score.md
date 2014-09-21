#Bank ABC Credit Scorecard Apps
========================================================
author: 
date: 

First Slide
========================================================

##Simple Application for All

###- Used by Bank Officials to make loan application decision
###- Used customers by to know their credit scores in Bank ABC
###- banks use it to set limit on their lending portfolio
###- Individuals use it to manage their credit profile 
Second Slide
========================================================
##Easy for Everybody to Use

###- An online application for all to assess
###- Enter Late Amount payment
###- Enter Balance in Account
###- Credit Scores will be returned 

Slide With Code
========================================================


```r
library(shiny)
shinyUI(pageWithSidebar(
    headerPanel("Bank ABC Credit Scorecard"),
    sidebarPanel(
      textInput(inputId='Late_amount', label= "Late Amount"),
      textInput(inputId = 'Balance', label= "Balance in Account"),
      submitButton('Submit')
      ),
    mainPanel(
      p('Output Late Amount'),
      textOutput('Late_amount'),
      p('Output Balance in Account'),
      textOutput('Balance'),
      p('Output Credit Score'),
      textOutput('Credit_Score')
      )
    )
  )
```

<!--html_preserve--><div class="container-fluid">
<div class="row-fluid">
<div class="span12" style="padding: 10px 0px;">
<h1>Bank ABC Credit Scorecard</h1>
</div>
</div>
<div class="row-fluid">
<div class="span4">
<form class="well">
<label for="Late_amount">Late Amount</label>
<input id="Late_amount" type="text" value=""/>
<label for="Balance">Balance in Account</label>
<input id="Balance" type="text" value=""/>
<div>
<button type="submit" class="btn btn-primary">Submit</button>
</div>
</form>
</div>
<div class="span8">
<p>Output Late Amount</p>
<div id="Late_amount" class="shiny-text-output"></div>
<p>Output Balance in Account</p>
<div id="Balance" class="shiny-text-output"></div>
<p>Output Credit Score</p>
<div id="Credit_Score" class="shiny-text-output"></div>
</div>
</div>
</div><!--/html_preserve-->

Slide With Code
========================================================


```r
library(shiny)
Late_amount <<- 0
Balance <<- 0
Credit_Score <<- 0
Decision <<- as.character("Declined")
shinyServer(
  function(input, output) {
    output$Late_amount <- renderText({input$Late_amount})
    output$Balance <- renderText({input$Balance})
    output$Credit_Score <- renderText({as.numeric(
      -3.3489 + 0.00005*(as.numeric(input$Late_amount))
      + 2.7348*(as.numeric(input$Balance)))})
    })
```

========================================================
## Necessary Statistical Package

###- Provides instant credit scores
###- Inputs the relevant predictors
###- Relies on modern mechine learning algorithms
###- Can be assessed from any location with internet 
