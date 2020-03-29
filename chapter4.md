---
title: Regressions
description: 'If you want to go through these topics in more detail, take our free Causal Inference with R - Regression course here on DataCamp.'
---

## The Basic Elements of a Regression Table

```yaml
type: VideoExercise
key: 38caf431ad
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/217554002
```


---

## Interpreting Regressions.

```yaml
type: MultipleChoiceExercise
key: 38caf432ad
lang: r
xp: 50
skills: 1
```

The popular online auctioneer, eGulf, wants to create an algorithm that will automatically provide recommended sales prices to eGulf sellers. In the case of wePhones, eGulf plans to base its algorithm on the age and sales price of previously sold WePhones. For the sake of convenience, eGulf bases their algorithm on a small stratified sample of 25 WePhones sold in the past week. 

eGulf runs an OLS regression to determine the relationship between WePhone age and sales price, and plots their results (illustrated in the R workspace). Each point on the plot indicates the age and selling price for a particular WePhone, and the line shows the results from an OLS regression on this data. What do these results suggest about the relationship of WePhone age and sales price?

`@possible_answers`
- [There is a negative relationship]
- There is no relationship
- There is a positive relationship

`@hint`


`@pre_exercise_code`
```{r}
set.seed(1)
library(ggplot2)
WePhone<-data.frame(age=rep(c(1,2,3,4,5),5))
WePhone$Feedback<-round(rnorm(n=25,mean=90,sd=3))
WePhone$Age<-WePhone$age+rnorm(n=25,mean=0,sd=.3)-WePhone$Feedback/10+mean(WePhone$Feedback/10)
WePhone$Value<-500-(9*WePhone$age^2)+ round(rnorm(n=25,mean=0,sd=30))
names(WePhone)[4]<-"Price Sold"
WePhone$`Price Sold`<-WePhone$`Price Sold`+20*(WePhone$Feedback-mean(WePhone$Feedback))
model<-lm(`Price Sold`~Age,data=WePhone)
ggplot(data=WePhone,aes(Age, `Price Sold`))+geom_point()+geom_abline(intercept = model$coefficients[1],slope=model$coefficients[2])+ ggtitle("Scatter Plot and OLS Regression of WePhone Age on Price Sold")

```

`@sct`
```{r}
msg1="Correct! As the age of WePhones increased, the price at which they were sold decreased."
msg2="Although the plot does not indicate if their results were statistically significant, they do indicate a relationship. Try again."
msg3="Think this through carefully. Does an increase in age increase or decrease the price sold of a WePhone? Try again."
ex() %>% check_mc(1, feedback_msgs = c(msg1, msg2, msg3))
```

---

## Reversing the Causal Direction?

```yaml
type: MultipleChoiceExercise
key: d3362faa14
lang: r
xp: 50
skills: 1
```

Causal interpretation of regression models can be tricky. Using the same data in the last example, an eGulf analyst decided to toy with a regression model where age is a function of price sold (i.e. price is the independent variable, and age is the dependent variable). The results of this model are visualized in the R workspace. If this model shows a causal relationship between age and price sold, with age as the dependent variable, what **exactly** should the analyst say to describe the results to his boss?

`@possible_answers`
- Older phones tend to sell for less
- Old age causes phones to sell for less
- [High sales prices causes phones to become younger]

`@hint`


`@pre_exercise_code`
```{r}
set.seed(1)
library(ggplot2)
WePhone<-data.frame(age=rep(c(1,2,3,4,5),5))
WePhone$Feedback<-round(rnorm(n=25,mean=90,sd=3))
WePhone$Age<-WePhone$age+rnorm(n=25,mean=0,sd=.3)-WePhone$Feedback/10+mean(WePhone$Feedback/10)
WePhone$Value<-500-(9*WePhone$age^2)+ round(rnorm(n=25,mean=0,sd=30))
names(WePhone)[4]<-"Price Sold"
WePhone$`Price Sold`<-WePhone$`Price Sold`+20*(WePhone$Feedback-mean(WePhone$Feedback))
model<-lm(Age~`Price Sold`,data=WePhone)
ggplot(data=WePhone,aes(`Price Sold`,Age))+geom_point()+geom_abline(intercept = model$coefficients[1],slope=model$coefficients[2])+ ggtitle("Scatter Plot and OLS Regression of WePhone Age on Price Sold")
```

`@sct`
```{r}
msg1="This phrasing does not address a causal interpretation of the relationship, but rather is a description of an association between WePhone age and sales price."
msg2="This is the most intuitive explanation for the relationship between WePhone sale price and age, but not for this particular regression model, which was designed to use age as the dependent variable. Try again."
msg3="Correct! Well, at least according to this model. This is an example of reverse causality. Obviously, we know that in reality the age of any object can only be influenced by time, so we know that this interpretation of their causal relationship is false: price sold cannot cause a phone's age. The analyst should try a different model next time."
ex() %>% check_mc(3, feedback_msgs = c(msg1, msg2, msg3))
```

---

## Reading a Bivariate Regression Table.

```yaml
type: MultipleChoiceExercise
key: 90d6e52a99
lang: r
xp: 50
skills: 1
```

The following table shows the regression results from the previous questions about eGulf's pricing algorithm for used wePhones. The coefficient for age reflects the slope in the previous line graph, and it suggests that for each additional year (or unit of age), the expected sales price of WePhones decreases by $61.99. The coefficient for the intercept matches the Y-axis intercept in the previous line graph. It indicates the predicted price sold for a WePhone at 0 years old (or more generally, it shows the value of an outcome when all other independent variables are at their reference point). 

| Variable   | Coefficient (SE) |
|------------|-----------------:|
|    Age     |   -61.99 (7.28)  |
| Intercept  |   592.56 (24.42) |

To determine the predicted sales price of a WePhone with a given age, we can start with the initial intercept value and add to it the total change in price for the age of the phone. In other words, based on this regression model the formula for predicting the price of a WePhone sold on eGulf is:

`Sales Price = 592.56 + Age * -61.99`

Based on this formula, what is a valid predicted price for a WePhone that is exactly two years old? You can use the R console as a scratch space to do your calculations.

`@possible_answers`
- 460.49
- [468.58]
- 472.57 
- 475.56

`@hint`


`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
msg1="Not quite. Try again."
msg2="Well done! Notice any advantages of regression models versus t-tests? In a t.test, we can only predict the outcome from a binary treatment variable (that is, the outcome for respondents in the treatment versus control group), In a regression model, we can predict the outcome from a continuous treatment variable (e.g. age)."
msg3="Oops, that's too high. Try again."
msg4="That's too low. Try again."
ex() %>% check_mc(2, feedback_msgs = c(msg1, msg2, msg3))

```

---

## Multiple Regression Models.

```yaml
type: PureMultipleChoiceExercise
key: 1272dad180
lang: r
xp: 50
skills: 1
```

Papers often report several regression models next to each other. This table shows a few truncated models from the example in the video, about the relationship between a country's property rights protections and its GDP. Model 1 shows the coefficient and standard error for the effect of property rights protection on GDP without any control variables. Model 2 shows the effect of property rights protection on GDP while controlling for the country's latitude, and Model 3 shows the same, while also controlling for whether the country is in Asia. Why might the effect of property rights protections on GDP decrease as we add more variables to our model?   

| Variable   | Model 1 | Model 2 | Model 3 |
|------------|--------:|--------:|---------|
| Protection |.52(.06) |.47(.06) |.43(.05) |
| Latitude   |         |.89(.49) |.37(.51) |
| Asia Dummy |         |         |-.62(.19)|

`@hint`


`@possible_answers`
- Because the inclusion of more variables weakens the statistical power of an independent variable
- Because omitting these variables caused the effect of property rights protection on GDP to be downwardly biased. 
- Because the inclusion of more variables strengthens the statistical power of an independent variable
- [Because omitting these variables caused the effect of property rights protection on GDP to be upwardly biased.]

`@feedback`
- Although this is often true, this is not indicated in this figure. If you look at the standard errors, the statistical significance of property rights protections on GDP is relatively small and consistent across models. Try again.
- This would mean that the omitted variables confound the relationship between property rights protections and GDP by decreasing the it. Try again
- This is usually not true, nor shown in this figure. Try again.
- Correct! Without controlling for these variables, the relationship between property rights protections and GDP seemed larger than it truly was.

---

## The Credibility of the Unconfoundedness Assumption.

```yaml
type: VideoExercise
key: 3a87588a15
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/217555887
```


---

## The Uncounfoundedness Assumption.

```yaml
type: PureMultipleChoiceExercise
key: 3f12d7ac14
lang: r
xp: 50
skills: 1
```

Although regression models are great for summarizing the association between variables, any causal interpretation of a regression models rests on the uncounfoundedness assumption (also known as the selection-on-observables assumption; and sometimes referred to as the conditional independence assumption). Which of the following summarizes this assumption?

`@hint`


`@possible_answers`
- [All variables that affect treatment assignment and the outcome of interest are observable and conditioned upon.]
- If something happens more frequently than expected during a given period, we can expect that it will happen less frequently in the future
- There is little or no multicollinearity in the data
- The residuals of a regression model are normally distributed.

`@feedback`
- Correct. Put even more simply, any causal interpretation of a regression model assumes that the relationships observed in the data are unconfounded. In most cases, this is impossible to verify empirically. However, it is a pretty large assumption. Most variations of regression models that we will describe in later chapters try to reduce the strength of this assumption.
- This is actually a summary of the gambler's fallacy. Try again
- This is an assumption that regression models make, but it is not a description of the unconfoundedness assumption
- This is an assumption that regression models make, but it is not a description of the unconfoundedness assumption

---

## Let’s Code: Toying with OLS - Outliers & Statistical Power.

```yaml
type: VideoExercise
key: 0043c7bdab
xp: 50
video_link: //player.vimeo.com/video/293196260
```


---

## Toying with OLS I: Outliers.

```yaml
type: NormalExercise
key: 1bb5748da5
lang: r
xp: 100
skills: 1
```

Although the math behind determining an OLS regression model is complicated, understanding what it's trying to do is surprisingly straightforward. Understanding how regression models work can yield important insight into understanding how they can be biased. In this question, we will examine how outliers can effect regression slopes. Using data provided by the popular online auctioneer eGulf about the relationship between WePhone age and sales price, follow the sample code to answer the following question about outliers:

`@instructions`
- 1) Refresh our memories on what the eGulf data looks like.
- 2) Run a glm model on how a phone's age affects its sales price on eGulf.
- 3) Examine a graph of this relationship.
- 4) Examine the impact of outliers at different phone ages through graphs.
- 5) Decide when outliers will have the least impact in this regression.

`@hint`
- The syntax for glm is "glm(Y~X,data=df)" where Y is the name of the independent variable, X is the name of the dependent variable, and df is the name of the dataframe.

`@pre_exercise_code`
```{r}
set.seed(1)
library(ggplot2)
WePhone<-data.frame(age=rep(c(1,2,3,4,5),4))
WePhone$Feedback<-round(rnorm(n=20,mean=90,sd=3))
WePhone$Age<-WePhone$age+rnorm(n=20,mean=0,sd=.3)-WePhone$Feedback/10+mean(WePhone$Feedback/10)
WePhone$Value<-500-(9*WePhone$age^2)+ round(rnorm(n=20,mean=0,sd=30))
names(WePhone)[4]<-"Price Sold"
WePhone$`Price Sold`<-WePhone$`Price Sold`+20*(WePhone$Feedback-mean(WePhone$Feedback))
WePhone$age<-NULL
WePhone$Feedback<-NULL
names(WePhone)[2]<-"PriceSold"
```

`@sample_code`
```{r}
# 1) As a quick refresher, let's glimpse at the first few lines of data. In the dataframe `WePhone`, Age refers to the number of years old the WePhone was, and Price Sold refers to the dollars it sold for. Use the head() function to look at these initial lines:



# It looks like these phones ranged between 1-6 years old, and they sold for about $180-$620. You might guess that the newest phones should sell for more money, so let's look at that correlated the Age and PriceSold variables are.


# 2) We will use a regression model to show us the correlation between a WePhone's Age and Price Sold across all the rest of the dataset. Run a glm model named `model` of Age on PriceSold using the dataframe `WePhone`, and then run the summary() command on that model to look at the results.
  
      model<-
      summary(model)

# These results show that the correlation we saw in the first few results from the head() command stay true through the rest of the data. These things are often easier to understand through a graph, so let's look at that next.

    
# 3) Below visualizes the regression model as a line, and the data points as dots. The line that it (and any regression model) produces minimizes the vertical distance (squared) between each data point and the regression line.  We've already generated the code for this graph, so select both of the following lines and hit the "Run Code" button to see the graph:

    plot(WePhone$PriceSold ~ WePhone$Age)
    abline(model)
    
# It looks like there's a pretty consistent negative correlation between age and the price sold, which makes sense. As phones get older, they are worth less money.


# 4) But what happens when we introduce outliers to the data? The following examples show what happen to the regression line when we insert an observation with an unusually high price sold ($2499) given its age at three points of the graph, when Age = 1, 3, and 5. For each of the following conditions, select the code and hit "Run Code", paying attention to any differences in the slope as we change the Age for this outlier.

  # No outlier
    plot(WePhone$PriceSold[1:20] ~ WePhone$Age[1:20], ylim=c(0, 1000))
    abline(glm(PriceSold~Age,data=WePhone[1:20,]))
    
  # Adding a $2499 outlier at Age = 1
    WePhone[21,]<-c(1,2499)
    plot(WePhone$PriceSold ~ WePhone$Age, ylim=c(0, 1000))
    abline(glm(PriceSold~Age,data=WePhone))
    
  # Adding a $2499 outlier at Age = 3
    WePhone[21,]<-c(3,2499)
    plot(WePhone$PriceSold ~ WePhone$Age, ylim=c(0, 1000))
    abline(glm(PriceSold~Age,data=WePhone))
    
  # Adding a $2499 outlier at Age = 5
    WePhone[21,]<-c(5,2499)
    plot(WePhone$PriceSold ~ WePhone$Age, ylim=c(0, 1000))
    abline(glm(PriceSold~Age,data=WePhone))


# 5) Now that you have seen the graphs change as we introduced outliers, answer the following question. When does an outlier in a regression model's dependent variable, "Y", causes the **LEAST** amount of bias (or change in slope) in its relationship to an independent variable, "X"? Answer the solution with "A", "B", or "C".

# (A) When the outlier in Y occurs at low values of X
# (B) When the outlier in Y occurs at middle values of X
# (C) When the outlier in Y occurs at high values of X

      Solution5<-""
```

`@solution`
```{r}
    head(WePhone)
    model<-glm(PriceSold~Age,data=WePhone)
    summary(model)
    Solution5<-"B"
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution5") %>% check_equal()
success_msg("Good work! Outliers typically effect the slope of a bivariate regression line least when they occur at middle values of X. When an outlier significantly alters the slope of a regression line, we refer to it as an 'influence point.' These typically need to be dealt with or removed to produce reliable regression results (i.e. a single outlier could mask the entire relationship between two variables). As a caveat, it should be noted that outliers do not always bias bivariate relationships (e.g. when an unusually high value of Y occurs with an unusually high value of X), but such outliers tend to have great statistical 'leverage,' which can lead to substantial bias in multivariate relationships (such as when a regression model includes more than one key independent variable). ")
```

---

## Toying with OLS II: Statistical Power.

```yaml
type: NormalExercise
key: a1c86897de
lang: r
xp: 100
skills: 1
```

Since OLS models are so easy to visualize, they provide a nice tool for understanding why models that use more observations tend to have more statistical power. In the following question, we have two datasets provided by the popular online auctioneer eGulf about the relationship between WePhone age and sales price, one with 25 observations. For each of these datasets, we add 25 randomly generated observations that have no relationship between WePhone age and sales price, to represent "statistical noise" - unexplained variation in our sample. Follow the sample code to create regression models with these two datasets, and answer the following question:

`@instructions`
- 1) Take a look at summary statistics of the two WePhone datasets.
- 2) Build glm models that estimate the effect of phone ages on sales prices in both datasets.
- 3) Which regression model most accurately represents the true relationship between WePhone `Age` and `SalesPrice`?

`@hint`


`@pre_exercise_code`
```{r}
#Original dataset
set.seed(1)
library(ggplot2)
WePhone<-data.frame(age=rep(c(1,2,3,4,5),5))
WePhone$Feedback<-round(rnorm(n=25,mean=90,sd=3))
WePhone$Age<-WePhone$age+rnorm(n=25,mean=0,sd=.3)-WePhone$Feedback/10+mean(WePhone$Feedback/10)
WePhone$Value<-500-(9*WePhone$age^2)+ round(rnorm(n=25,mean=0,sd=30))
names(WePhone)[4]<-"Price Sold"
WePhone$`Price Sold`<-WePhone$`Price Sold`+20*(WePhone$Feedback-mean(WePhone$Feedback))
WePhone$age<-NULL
WePhone$Feedback<-NULL
names(WePhone)[2]<-"PriceSold"
WePhone1<-WePhone

#Second dataset
WePhone<-data.frame(age=rep(c(1,2,3,4,5),20))
WePhone$Feedback<-round(rnorm(n=100,mean=90,sd=3))
WePhone$Age<-WePhone$age+rnorm(n=100,mean=0,sd=.3)-WePhone$Feedback/10+mean(WePhone$Feedback/10)
WePhone$Value<-500-(9*WePhone$age^2)+ round(rnorm(n=100,mean=0,sd=30))
names(WePhone)[4]<-"Price Sold"
WePhone$`Price Sold`<-WePhone$`Price Sold`+20*(WePhone$Feedback-mean(WePhone$Feedback))
WePhone$age<-NULL
WePhone$Feedback<-NULL
names(WePhone)[2]<-"PriceSold"
WePhone2<-WePhone

#Random noise
noise<-data.frame(Age=c(1,2,3,4,5)+rnorm(n=25,mean=0,sd=.3))
noise$PriceSold<-round(rnorm(n=25,mean=400,sd=100))

#Append random noise
WePhone1<-rbind(WePhone1,noise)
WePhone2<-rbind(WePhone2,noise)
rm(list = c("noise","WePhone"))
```

`@sample_code`
```{r}
# 1) We have two datasets, WePhone1 and WePhone2. The first contains 25 real observations and 25 random observations; the second contains 100 real observations and 25 random observations. As a reminder, each dataset contains two variables, "Age"" and "PriceSold." Run the summary command on both `WePhone1` and `WePhone2` to see what we have:



# 2) On the surface, these datasets look quite similar. But how do their different sample sizes affect estimates from regression models? Build regression models using the glm function that shows the effect of Age on PriceSold for WePhones in each dataset.

# glm in dataset WePhone1
    
        Solution2<-glm()

# glm in dataset WePhone2
    
        Solution3<-glm()

#Note: We should view the output of these models with the summary function to answer the next question.
        summary(Solution2)
        summary(Solution3)
        
        
# 3) Although the estimates in Solution2 and Solution3 are similar and are both statistically significant, these models arrive at very different standard errors (a core measurement of the accuracy of our estimates). Larger standard errors indicate that we are less certain of our estimates. Which of the two models' estimates are we more certain in, "Solution2" or "Solution3"?
      
        Solution4<-""
      
# Note: For fun, we can plot these models on a graph with error bars using the smooth function in ggplot. In this case, the error bars represent the range of values that we are 95% sure the true population estimate lies between. Again greater error bars indicate that we have less certainty about the true relationship of our variables.
      
ggplot(NULL, aes(x=Age,y=PriceSold))+
    theme_bw()+
    geom_smooth(data=Solution2, color="red",fill="red",method='lm')+
    geom_smooth(data=Solution3, color="blue",fill="blue",method='lm')
      
```

`@solution`
```{r}
summary(WePhone1)
summary(WePhone2)
Solution2<-glm(PriceSold ~ Age, data=WePhone1)
Solution3<-glm(PriceSold ~ Age, data=WePhone2)
Solution4<-"Solution3"
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution2") %>% check_equal()
ex() %>% check_object("Solution3") %>% check_equal()
ex() %>% check_object("Solution4") %>% check_equal()
success_msg("Good work! Larger datasets tend to be more robust to 'statistical noise' - unexplained variation in the sample. In this example, statistical noise decreased the relationship between Age and PriceSold (i.e. the coefficient of Age in the model). However, it is possible for statistical noise to induce spurious relationships as well.")
```

---

## Let’s Code: Toying with OLS III - Model Selection.

```yaml
type: VideoExercise
key: 4ca7d61f52
xp: 50
video_link: //player.vimeo.com/video/293196276
```


---

## Toying with OLS III: Model Selection.

```yaml
type: NormalExercise
key: 23daa37fbe
lang: r
xp: 100
skills: 1
```

NixSplash, a water conservationist group in Utah, wants to make a targeted ad campaign to encourage high water consumers to reduce their water usage. To determine who to target with their ad campaign, NixSplash conducts a survey across a random sample of the population. However, the intern who put together NixSplash's survey asked a bunch of odd questions. Use NixSplash's survey dataset, `Survey`, to generate the best model for predicting a household's water usage.

  *** =instructions
- 1) Examine the data from the survey
- 2) Build a regression model that includes all statistically significant predictors of a household's water usage (`Water`).
- 3) Build a regression model that includes all intuitive predictors of a household's water usage (`Water`).
- 4) Decide which way of modeling is better.

`@instructions`


`@hint`


`@pre_exercise_code`
```{r}
set.seed(1)
n=1337
#Create rnorm function that allows for min and max
rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
  qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
}
#Create rounding function that allows to round to numbers above 1
mround <- function(x,base){ 
  base*round(x/base) 
} 
#Dataset
  Survey<-data.frame(YardSize=round(rtnorm(n,.2,sd=.1,min=.05,max=5),2),
                     Rainfall=round(rtnorm(n,8,sd=1,min=4,max=12),1),
                     NSprinkler=rbinom(n,1,.2),
                     Dunking=rbinom(n,1,.15),
                     Massage=rbinom(n,1,.05),
                     Coffee=rbinom(n,1,.35)
                     )
  Survey$Water<-(Survey$YardSize*10+Survey$Rainfall+Survey$NSprinkler*5+rnorm(n,10,4))*15
```

`@sample_code`
```{r}
# Note: Here is a data dictionary about the variables:
#    Water refers to the number of gallons (in hundreds) that the respondent has used in the past year
#    YardSize refers to the number of acres that the respondent owns
#    Rainfall refers to the number of annual inches in rain that fell on the respondent's property in the past year
#    NSprinkler refers to whether the respondent's neighbor runs a sprinkler system on a daily basis
#    Dunking refers to whether the respondent lives within walking distance of a Dunking Donuts
#    Massage refers to whether the respondent has ever gotten a massage
#    Coffee refers to whether the respondent drinks coffee on a daily basis. 

# 1) As usual, let's first examine the dataset. Start by running the summary() command on the dataframe `Survey`:

    summary()


# 2) Some of the survey questions may seem irrelevant to how much water a household uses, but let's find out for certain. Let's first run an OLS regression model for water usage while using all variables in the dataset. 
  
# Note: We can find the summary statistics from a generalized linear regression model by inserting the glm() code as the parameter for the summary() command, like the following: summary(glm(Water ~ YardSize, data=Survey)). Now do that for yourself, but include all of the variables in the dataframe:



# If you did this correctly, you should see a statistically significant effect from all variables except Dunking and Massage.


# 3) Since the variables Dunking and Massage have no significant effect on Water, let's try removing them from our model and see what changes. Enter the summary(glm()) code with these variables omitted:



# So which model is better? A model that predicts water usage with all of our available variables, or a model that predicts water usage without Dunking or Coffee? It turns out that statisticians have developed a variety of tools to measure how well a model specification fits the data (i.e. a model's "goodness of fit"). The GLM function includes one such parameter, its "AIC" (Akaike information criterion). The math behind AICs is complicated, but in practice, a model's AIC can be used to compare the goodness of fit between two models. A model with a lower AIC than another is considered to fit the data better. 


# 4) In the above example, the AIC of our second model is lower than in our first example, but only very slightly ( a rule of thumb is that a difference of 5 is considered substantial). This suggests that the models fit the data more or less equally well. So which should we choose? Should NixSplash incorporate some of our unintuitive variables into their model and ad-campaign? In other words, should we include all variables in our model even if it is unclear why proximity to Dunking Donuts, Massage frequency, and Coffee-drinking habits would effect water useage? Answer Solution 4 with "Yes" or "No".

      Solution4<-""
      
```

`@solution`
```{r}
summary(Survey)
summary(glm(Water~YardSize+Rainfall+NSprinkler+Rainfall+Dunking+Massage+Coffee,data=Survey))
summary(glm(Water~YardSize+Rainfall+NSprinkler+Rainfall+Coffee,data=Survey))
Solution4<-"No"
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution4") %>% check_equal()
success_msg("Good work! Even though our model in Solution 1 appears similar to our model in Solution2,  we should **not** include all of these variables into our final model, or use them to inform NixSplash's ad-campaign. Statistical models should always be guided by theory. If there is no clear reason why a variable should effect an outcome of interest, we should not include it in our model, even if it improves model fit. As a reminder, statistical models do not provide definitive proof of causality; they are simply a tool that we can use to test our assumptions about the world.")
```

---

## Matching Methods.

```yaml
type: VideoExercise
key: 1665b0b39b
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/217555077
```


---

## Let’s Code: Communication Skills in Video Games.

```yaml
type: VideoExercise
key: abcb56164f
xp: 50
video_link: //player.vimeo.com/video/293196315
```


---

## Communication Skills in Video Games: Do We Have to Use Matching Methods?

```yaml
type: NormalExercise
key: 02cba6354e
lang: r
xp: 100
skills: 1
```

A recent study examined how playing the multiplayer online battle arena video game, Neo Elite Raging Denizens (NERD), affects people's communication skills. Despite the player's coarse language in the game, a detailed psychological survey indicated that NERD players have better language skills than average. This finding held even when the researchers used OLS regression and controlled for various factors that are related to language skills. This made the researchers wonder: does NERD cause people how to communicate better? The researchers knew their sample was highly unbalanced, so they thought that matching techniques may be required.

`@instructions`
- 1) Examine the dataset `NERD`.
- 2) Estimate a standard OLS regression model for communication skills (`Communication`) based on all other variables in the `NERD` dataset.
- 3) Check the statistical significance of that regression model.
- 4) Check for balance between treatment and control groups.

`@hint`
- The syntax for a simple t-test is t.test(variable1, variable2)

`@pre_exercise_code`
```{r}
#Original dataset


library(dplyr)
library(data.table)
library(MatchIt)

set.seed(7)
n=8008
#Create rnorm function that allows for min and max
    rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
      qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
    }
#Create rounding function that allows to round to numbers above 1
    mround <- function(x,base){ 
      base*round(x/base) 
    } 
#Create dataset
    NERD<-data.frame(ParentEducation=round(rtnorm(n,15,sd=3,min=10,max=20),1),
                     BooksOwned=round(rtnorm(n,60,sd=15,min=35,max=100),1),
                     ReadsBlogs=rbinom(n,1,.25),
                     Siblings=rbinom(n,1,.7),
                     Bilingual=rbinom(n,1,.1),
                     LikesBooks=rbinom(n,1,.3)
    )
    NERD$Treatment<-NERD$ParentEducation+NERD$BooksOwned/4+NERD$ReadsBlogs*10-NERD$Siblings*5+NERD$LikesBooks*10 +rnorm(n,10,3)
    NERD$Treatment<-NERD$Treatment/max(NERD$Treatment)
    NERD$Treatment<-ifelse(NERD$ParentEducation<17 | NERD$BooksOwned<70,0,NERD$Treatment)
    NERD$Treatment<-NERD$Treatment
    NERD$Treatment<-rbinom(n,1,NERD$Treatment)
    NERD$Communication<-2.5*NERD$Treatment+NERD$ParentEducation^1.4+-.01*NERD$Treatment*NERD$ParentEducation+-.01*NERD$Treatment*NERD$BooksOwned^1.2+NERD$BooksOwned*.6+1.5*NERD$ReadsBlogs+NERD$LikesBooks*.7 + NERD$Siblings + .25*NERD$Bilingual +rnorm(n,5,1) 
    NERD$Communication<-round(NERD$Communication/max(NERD$Communication)*10)
```

`@sample_code`
```{r}
# 1) As usual, let's first look at the variables in the dataset, which was collected by the researchers on a sample that included NERD gamers along with other people. Use the summary command on the dataframe `NERD`, and take a few minutes to understand what's in the data.


# Notes:
# The dependent variable in our model, Communication, was measured via a series of questions and put on a 1:10 scale, with 1=very poor communication skills and 10=very good communication skills. 
# The variable Treatment measures whether the respondent plays NERD. 
# The other variables in the dataset are factors that could possibly affect a person's communication ability. Most are measured as binary or "dummy" variables; for example, the Siblings variable gets a value of 1 if respondents have any brothers or sisters, but it does not count the number of siblings they have.


# 2) Let's first estimate a model for Communication skills based on every other variable in the dataset. Use R's glm() formula. 

      Solution2<-glm()


# 3) Is the effect of "Treatment" in Solution2 positive and statistically significant? Use the summary command on Solution2 to check, and then enter "Yes" or "No" for Solution3.
    
      Solution3<-""


# 4) Matching methods are most useful when the treatment group is likely to be different from the control group in ways that are unrelated to our outcome. Do we need to use them in this case? To determine if the treatment group differs from the population on any variable, let's run a t-test between the treatment and control groups on the first variable in the dataframe, ParentEducation. As a reminder, the syntax for a simple t-test is t.test(variable1, variable2)

	t.test()

# If you are curious, feel free to run t-tests on the other variables in the dataframe to see which are balanced and which are imbalanced.

```

`@solution`
```{r}
Solution2<-glm(Communication~ ParentEducation+BooksOwned+ReadsBlogs+Siblings+Bilingual+LikesBooks+Treatment,data=NERD)
  Solution3<-"Yes"
t.test(NERD$ParentEducation[NERD$Treatment==1],NERD$ParentEducation[NERD$Treatment==0])
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution2") %>% check_equal()
ex() %>% check_object("Solution3") %>% check_equal()
success_msg("Good work! There appears to be a positive and statistically significant effect for playing NERD on respondent's communication skills, but the t-test suggests that our Treatment group has much more educated parents than in our Control group, so our treatment and control groups are imbalanced. In the next question, we'll try to use matching methods to overcome this problem.")
```

---

## Communication Skills in Video Games: Propensity Score Matching in R.

```yaml
type: NormalExercise
key: 7b9e526139
lang: r
xp: 100
skills: 1
```

The researchers studying how playing NERD affects communication skills knew their sample was highly unbalanced, so they thought that matching techniques may be required. With the dataset, `NERD`, use matching techniques to better estimate the average treatment effect of playing NERD on communication skills. Regression models alone aren't always convincing for measuring causal effects in unbalanced data (even under unconfoundedness). A more robust way to test the effect of our treatment on communication skills is through matching methods. Matching methods balance the treatment group with the control group so that they are more identical.

In R, the best tool for doing matching is the "MatchIt" package. Let's use the MatchIt package to subset our NERD dataset so that our control group contains observations that are most similar to those in our treatment group. There are many methods for matching data, but in this question, we use MatchIt's default methods.

`@instructions`
- 1) Build a model for `Treatment` based on all of the control variables.
- 2) Subset our data to just the units who are likely to be in the treatment group.
- 3) Use matching techniques to balance the dataset.
- 4) Estimate standard OLS regression model for communication skills (`Communication`) based on all other variables in the matched dataset (`match.NERD`).
- 5) Check the statistical significance of the regression on the matched data.

`@hint`


`@pre_exercise_code`
```{r}
#Original dataset

library(dplyr)
library(data.table)
library(MatchIt)

set.seed(7)
n=8008
#Create rnorm function that allows for min and max
    rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
      qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
    }
#Create rounding function that allows to round to numbers above 1
    mround <- function(x,base){ 
      base*round(x/base) 
    } 
#Create dataset
    NERD<-data.frame(ParentEducation=round(rtnorm(n,15,sd=3,min=10,max=20),1),
                     BooksOwned=round(rtnorm(n,60,sd=15,min=35,max=100),1),
                     ReadsBlogs=rbinom(n,1,.25),
                     Siblings=rbinom(n,1,.7),
                     Bilingual=rbinom(n,1,.1),
                     LikesBooks=rbinom(n,1,.3)
    )
    NERD$Treatment<-NERD$ParentEducation+NERD$BooksOwned/4+NERD$ReadsBlogs*10-NERD$Siblings*5+NERD$LikesBooks*10 +rnorm(n,10,3)
    NERD$Treatment<-NERD$Treatment/max(NERD$Treatment)
    NERD$Treatment<-ifelse(NERD$ParentEducation<17 | NERD$BooksOwned<70,0,NERD$Treatment)
    NERD$Treatment<-NERD$Treatment
    NERD$Treatment<-rbinom(n,1,NERD$Treatment)
    NERD$Communication<-2.5*NERD$Treatment+NERD$ParentEducation^1.4+-.01*NERD$Treatment*NERD$ParentEducation+-.01*NERD$Treatment*NERD$BooksOwned^1.2+NERD$BooksOwned*.6+1.5*NERD$ReadsBlogs+NERD$LikesBooks*.7 + NERD$Siblings + .25*NERD$Bilingual +rnorm(n,5,1) 
    NERD$Communication<-round(NERD$Communication/max(NERD$Communication)*10)

# Import model from previous question
       FirstModel<-glm(Communication~ ParentEducation+BooksOwned+ReadsBlogs+Siblings+Bilingual+LikesBooks+Treatment,data=NERD)
```

`@sample_code`
```{r}
# Note: You may want to refresh your memory of the variables in `NERD` with the str(), head(), or summary() commands).

# 1) Let's use the tools in the MatchIt package for R to help us try a Propensity Score approach to matching units in our treatment and control groups. The following syntax builds a model for estimating "Treatment" by all other control variables in our dataset `NERD` with the matchit() command: matchit(Treatment ~ control1 + control2 + control3 + control4 + control5, data = NERD). Use that syntax to populate the dataframe `match.it`:
    
    match.it <-


# 2) Now let's subset the NERD dataset to observations that have a high predicted probability for being in the treatment group. We have generated that code for you, so select the following code and hit the "Run Code" button:

	matched.NERD <- match.data(match.it)[1:ncol(NERD)]


# 3) Let's use the summary() command on our new datafame `matched.NERD`: 

	summary()
    
# The "Summary of balance for all data" shows mean values of each variable across our original treatment and control groups, and the "Summary of balance for matched data" shows mean values of each variable across our matched dataset. You may notice that the mean values for most variables between the treatment and control groups are now pretty similar. The "Sample sizes" output shows that the algorithm matched one observation in the control group for each observation in the treatment group.
    
    
# 4) Let's now estimate a generalized linear regression model for communication skills that uses all of our control variables and our matched dataset (matched.NERD). 

      Solution4<-glm()


# 5) Use the summary command on Solution4 to check its statistical significant. Is the effect of "Treatment" in Solution4 both positive and statistically significant?  Answer with "Yes" or "No".
    
      summary(Solution4)
      Solution5<-""

#Note: For the sake of comparison, the syntax below shows us our regression results when our data were unmatched. Notice that the treatment effect was positive.
      summary(FirstModel)
      
     
```

`@solution`
```{r}
match.it <- matchit(Treatment ~ ParentEducation+BooksOwned+ReadsBlogs+Siblings+Bilingual+LikesBooks, data = NERD)
  matched.NERD <- match.data(match.it)[1:ncol(NERD)]
  summary(match.it)
  Solution4<-glm(Communication~ ParentEducation+BooksOwned+ReadsBlogs+Siblings+Bilingual+LikesBooks+Treatment,data=matched.NERD)
  summary(Solution4)
  Solution5<-"No"
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution4") %>% check_equal()
ex() %>% check_object("Solution5") %>% check_equal()
success_msg("Good work! In our unmatched model, the treatment effect (playing NERD) appeared to have a positive and statistically significant effect on respondent's communication skills. However, when we balanced the data, this effect disappeared. It turns out that the original treatment effect was spurious; it resulted from our biased sample of people who play NERD. When we compared people who played NERD to relatively similar people who don't play nerd, this treatment effect disappeared. That means that playing NERD does not improve people's communication skills; rather, NERD players have good communication skills because the people who are attracted to NERD tend to have good communication skills. Or in other words, this association results from a selection bias - not from a treatment effect.")
```
