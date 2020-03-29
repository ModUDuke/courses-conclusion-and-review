---
title: 'Panel Data'
description: 'If you want to go through these topics in more detail, take our free Causal Inference with R - Panel Data course here on DataCamp.'
---

## The Common Trends Assumption.

```yaml
type: VideoExercise
key: bc0c024f07
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/226208683
```


---

## Interpreting Longitudinal Outcomes.

```yaml
type: PureMultipleChoiceExercise
key: bc0c024f08
lang: r
xp: 50
skills: 1
```

In the early 1970s, the mayor of Springfield, Oklahoma, noticed that his citizens had higher rates of diabetes than ever before. To combat diabetes, the mayor of Springfield implemented a permanent 2% sales tax on all food items that contained corn syrup in the year 1979. 

Now, the mayor of the town next door, Laughterville, is concerned about rates of diabetes in his city, and is considering implementing similar a tax on food items that contain corn syrup. To inform his decision, the mayor of Laughterville compares rates of diabetes (percentage of population) in Laughterville to rates of diabetes in Springfield over time. A table of the data is included below.

|     City      | 1950 | 1960 | 1970 | 1980 | 1990 | 2000 | 2010 |
|---------------|-----:|-----:|-----:|-----:|-----:|-----:|-----:|
| Springfield   |  .98 | 1.13 | 1.88 | 2.69 | 2.91 | 3.84 | 5.20 |
| Laughterville | 1.01 | 1.14 | 1.87 | 3.14 | 3.67 | 4.75 | 6.66 |

Based on this table, which conclusion about the effect of taxing corn syrup products on rates of diabetes seems most reasonable?

`@hint`


`@possible_answers`
- Taxes have no effect, given that rates of diabetes in Springfield were much higher following the implementation of the tax.
- [Taxes have a negative treatment effect on rates of diabetes (i.e. decreased rates of diabetes), given that rates of diabetes in Springfield were lower than those in Laughterville following the implementation of the tax.]
- Taxes have a positive treatment effect on rates of diabetes (i.e. increased rates of diabetes), given that rates of diabetes in Springfield were much higher following the implementation of the tax.

`@feedback`
- Not quite. Try comparing the outcomes of Springfield to Laughterville.
- Correct! This is exactly how we interpret difference-in-differences outcomes. Even though Springfield had higher rates of diabetes following the implementation of its tax on corn syrup products, it appears that Springfield's rate diabetes grew at a smaller rate than in Laughterville.
- Not quite. Try comparing the outcomes of Springfield to Laughterville.


---

## Graphical Analysis of the Common Trend Assumption and Diff-in-Diffs

```yaml
type: VideoExercise
key: 0d960ed709
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/226206681
```


---

## Interpreting Graphed Time Trends.

```yaml
type: MultipleChoiceExercise
key: 5226527508
lang: r
xp: 50
skills: 1
```

Whitney, a fan of the cult pro-environmental film "Birdemic", is interested in whether watching the movie encouraged people to purchase more solar panels. She found a time-series dataset that listed whether people owned solar panels, and whether individuals had watched Birdemic in 2010 (the year the film was released). The results of the interview are plotted to the right. What can we conclude from this graph?

`@possible_answers`
- Watching Birdemic motivated people to buy solar panels.
- [Watching Birdemic discouraged people from buying solar panels.]

`@hint`


`@pre_exercise_code`
```{r}
df<-data.frame(Year=rep(c(2008,2009,2010,2011,2012),2))
df$Treated<-as.factor(rep(c("Yes","No"),each=5))
df$Percent<-c(.02,.023,.026,.027,.028,.01,.013,.016,.02,.024)
library(ggplot2)
p<-ggplot(data=df,aes(x=Year,y=Percent,group=Treated,col=Treated))
p+geom_line()+geom_point()+
  theme(panel.grid.major = element_blank(), panel.grid.minor = element_blank(),
        panel.background = element_blank(), axis.line = element_line(colour = "black"))+
  ggtitle("Rate of Solar Panel Ownership by Watching Birdemic")+
  labs(y="Proportion Own Solar Panels",color="Watched Birdemic")
```

`@sct`
```{r}
msg1="Take a closer look at the chart. Does it seem to change after the year 2020? Try again." 
msg2="Correct! Rates of solar panel sales for both groups at the same rate prior to Birdemic's release, but the rate of this increase was smaller for those who watched Birdemic following 2010" 
ex() %>% check_mc(2, feedback_msgs = c(msg1, msg2))
```

---

## Why Would We Use a Lagged Dependent Variable?

```yaml
type: PureMultipleChoiceExercise
key: 8862cc8d4c
lang: r
xp: 50
skills: 1
```

Think about what you know about causal inference. What might be an advantage for modeling your data with a lagged dependent variable; that is, a dependent variable measured at a time point after your explanatory variables were measured?

`@hint`


`@possible_answers`
- Letting time pass allows confounding factors to disappear.
- It gives you more time to formulate your hypothesis.
- [It helps you more clearly establish the causal direction.]
- A dependent variable depends on time, so dependent variables always happen after the independent variables.

`@feedback`
- Time isn't really a factor with determing what is a confounder. If an outside variable affects outcomes, it's a confounder, no matter when in the process it happens. Try again.
- You should be testing a hypothesis you formed before you started, otherwise you aren't following the scientific method! Try again.
- Well done
- You have labeled the dependent and independent variables based on your theory and knowledge of the research question, not based on the direction of the arrow of time. So try again. 


---

## The 3 Kinds of Panel Data

```yaml
type: VideoExercise
key: d8dac97b22
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/226207544
```


---

## Let's Code: Practice Running Fixed and Random Effects Models.

```yaml
type: VideoExercise
key: 19920e92a6
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/314102565
```


---

## Practice Running Fixed and Random Effects Regression Models.

```yaml
type: NormalExercise
key: c1b037d54e
lang: r
xp: 100
skills: 1
```

Many students at Perry Elementary school write with gel pens. Iris, the school's librarian, is convinced that students could write faster if all the students were required to use ballpoint pens. To test her theory, Iris gets permission to conduct a secondary analysis of an annual student written exam. 

At the end of each school year, students are required to write a three paragraph answer to a short prompt. When students submit their exams, teachers note how long the students took to submit their exams, how many words were written in their exams, and ask the students how many hours of sleep they had slept the previous night. In addition, Iris identified whether the exams were written with a gel or ballpoint pen.

These style exams are given to students three years in a row. Iris was given permission to look at all three of these exams for a single class of students. Since it is possible that students who write with gel pens have different innate writing abilities than those who write with ballpoint pens, Iris decides to only study changes in writing speed for people who switched between using gel pens to ballpoint pens. 

Using the dataset, `Exams`, help Iris estimate the effect of using a ballpoint pen on a student's writing speed with *pooled OLS*, *fixed* and *random* effects models.

`@instructions`
- 1) Examine the structure of the data and the types of variables we have.
- 2) Look more closely at the values of our treatment variables.
- 3) Construct a pooled OLS model that measures the effect of ballpoint pens on student's writing speeds, controlling for age, sex, and hours slept (variables: `pen`,`speed`,`age`,`sex`,`sleep`) .
- 4) Examine the results on that model and interpret what they are saying.
- 5) Construct a fixed effects model that measures the effect of ballpoint pens on student's writing speeds, controlling for age, sex, and hours slept (variables: `pen`,`speed`,`age`,`sex`,`sleep`).
- 6) Determine whether the absolute value of the Gel pen effect is larger or smaller in the fixed effects model than in the pooled OLS model.
- 7) Construct a random effects model that measures the effect of ballpoint pens on student's writing speeds, controlling for age, sex, and hours slept (variables: `pen`,`speed`,`age`,`sex`,`sleep`).

`@hint`


`@pre_exercise_code`
```{r}
library(plm)
n=521
#Create rnorm function that allows for min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
      qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){ 
          base*round(x/base) 
  } 

set.seed(1)
#Dataframe
  Exams<-data.frame(id=1:n,wave=1)
#year 1:
    #age
        Exams$age<-10+rbinom(n=n,1,.2)
    #sex
        Exams$sex<-ifelse(rbinom(n=n,1,.55)==1,"Female","Male")
    #sleep
        Exams$sleep<-mround(rtnorm(n=n,mean=8,sd=1,min=5,max=9),.5)
    #pen
        Exams$pen<-ifelse(rbinom(n=n,1,.5+ifelse(Exams$sex=="Male",.25,0)+1/Exams$age)==1,"Ballpoint","Gel")
    #speed
        Exams$speed<-round((Exams$age/10+(Exams$sex=="Female")/3+(Exams$sleep/rtnorm(n,2,1,1,3)/4)+(Exams$pen=="Ballpoint")*rtnorm(n,.5,.1,0,1))*2+rnorm(n,3,.5),2)

#year 2:
  Exams2<-data.frame(id=1:n,wave=2)
    Exams2$age<-Exams$age+1
    Exams2$sex<-Exams$sex
    Exams2$sleep<-mround(Exams$sleep+rtnorm(n,0,.3,0,1),.5)
    Exams2$pen<-ifelse(rbinom(n,1,.75)==1,Exams$pen,ifelse(rbinom(n=n,1,.4+ifelse(Exams$sex=="Male",.25,0)+1/Exams$age)==1,"Ballpoint","Gel"))
    Exams2$speed<-round(((Exams2$age/10+(Exams2$sex=="Female")/3+(Exams2$sleep/rtnorm(n,2,1,1,3)/4)+(Exams2$pen=="Ballpoint")*rtnorm(n,.5,.1,0,1))*2+rnorm(n,3,.5))/5+Exams$speed,2)

#year 3:
Exams3<-data.frame(id=1:n,wave=3)
    Exams3$age<-Exams2$age+1
    Exams3$sex<-Exams2$sex
    Exams3$sleep<-mround(Exams2$sleep+rtnorm(n,0,.3,0,1),.5)
    Exams3$pen<-ifelse(rbinom(n,1,.75)==1,Exams2$pen,ifelse(rbinom(n=n,1,.4+ifelse(Exams2$sex=="Male",.25,0)+1/Exams2$age)==1,"Ballpoint","Gel"))
    Exams3$speed<-round(((Exams3$age/10+(Exams3$sex=="Female")/3+(Exams3$sleep/rtnorm(n,2,1,1,3)/4)+(Exams3$pen=="Ballpoint")*rtnorm(n,.5,.1,0,1))*2+rnorm(n,3,.5))/5+Exams2$speed,2)
  
#rbind
    Exams<-rbind(Exams,Exams2)
    Exams<-rbind(Exams,Exams3)
    Exams<-Exams[order(Exams$id,Exams$wave),]

```

`@sample_code`
```{r}
# 1) Before running any models, let's examine the data. The dataset contains seven variables. Wave refers to which date in the time series that we are looking at. Wave 1 refers to the first year the data was collected, whereas wave 3 refers to the last year that the data was collected. Since data was collected three times for each individual, each id variable occurs in the data set 3 times.

    str(Exams)
    head(Exams)

# 2) The meaning of the other variables is pretty intuitive. Sleep refers to the number of hours that the students slept the previous night, and speed refers to the number of words that each student wrote per a minute.

    summary(Exams$sleep)
    summary(Exams$speed)

# 3) Run a typical OLS model on the dataset, treating each repeated observation as an independent person (i.e. pooling the data), where speed is the dependent variable, pen is the independent variable, and where we have control variables for age, sex, and sleep. For reference, the syntax for glm models is glm(y ~ x + z1 + z2 + z3, data=df), where y is the dependent variable, x is the independent variable, z1-z3 are control variables, and df is the data frame. You do not need to use the id or wave variables in this model.

    Solution3<-glm()
  
# 4) If you answered question 3 correctly, you should see a large negative effect from using gel pens when you view the summary results: 

    summary(Solution3)
    
# However, when we pool the data this way, we are treating repeated observations as separate people. This is not true. Pooling our data this way will bias our parameter estimates, especially if there is variation in each student's underlying writing ability and these variations are correlated with whether they use gel pens.    
    
# 5) Now let's try estimating a fixed effects model. Random effects models work similarly to OLS models, except that it also controls for how observations in our sample are related. Basically, we want to control for student's different latent writing speeds, and only look at how switching between a gel and ballpoint pen effected their writing speeds compared to those who did not switch pens, To estimate a fixed effects model, we need to use the plm function. The syntax is  identical to glm, except that after the data statement, we specify how the data are grouped (by id and wave) and what type of effect that we want to examine (within person changes). Fill in the front part of the plm model so that it estimates the effect of using a gel pen on writing speed while controlling for age, sex, and sleep.
    
    Solution5<-plm(,index=c("id", "wave"), model="within")

# 6) If you answered question 5 correctly, you should notice that the model only gave us parameter estimates for sleep and gel pens. This is because the sex of students did not change across any years (again, we are only looking at how changes within individuals affected their writing speeds), and because the change in age was uniform across years for all respondents (that is, there was no variation in how student's ages changed across individuals - everyone grew one year older each wave). You should also notice that the parameter estimate for gel pens differs from the first model. Is the absolute value of the effect of gel pens larger or smaller in solution2 than in solution1. Answer with "Larger" or "Smaller".

    Solution6<-""

# 7 ) Although fixed effects models are very reliable, they often require large sample sizes to find statistically significant results, and they often exclude estimating effect that would be interesting to report in a regression model (for example, the effect of age and sex on writing speed). In such cases, we often use random effects models instead. Random effects models are almost identical to fixed effects models, except they make the somewhat strong assumption that the individual specific effects are uncorrelated with your other parameters. In this example, a random effects model assumes that every individual has a latent writing speed that is uncorrelated with anything else. Factors like age and sex simply improve their writing speeds. Estimate a random effects model that groups individuals by id and wave, but that also controls for age, sex, and sleep. The syntax should be identical to that in Question 2, except that the "model" parameter in the plm function should be switched from "within" to "random".

      Solution7<-plm()

```

`@solution`
```{r}
#models    
    Solution3<-glm(speed~pen+sleep+sex+age,data=Exams)
    Solution5<-plm(speed ~ age + sex + sleep + pen, data=Exams, index=c("id", "wave"), model="within")
    Solution6<-"Larger"
    Solution7<-plm(speed ~ age + sex + sleep + pen, data=Exams, index=c("id", "wave"), model="random")
    
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution7") %>% check_equal()
success_msg("Good work! You now know the basics to estimating fixed and random effects models with panel data. As you can see, these models often give very different results than typical pooled OLS models, and their estimates tend to be much more robust. You may still be wondering when you should use random versus fixed effects models. In general, if you can find statistically significant effects with fixed effects models, they are preferable to random effects models. However, there are a variety of tools available for comparing whether you get any benefit from using a fixed effects model (e.g. the Hausman test). In general, use you intution and see what other people have done in similar situations!")
```


---

## The Assumptions of Difference-in-Differences Analysis

```yaml
type: PureMultipleChoiceExercise
key: c2d707b4b8
lang: r
xp: 50
skills: 1
```

What is the main assumption that we make when we study a causal effect by comparing trends among a treatment group with trends among a control group?

`@hint`


`@possible_answers`
- [Systematic differences between the treatment and control group are less likely to confound the average treatment effect.]
- You can see systematic changes across a population with time.
- It inherently uses a smaller sample of people, so fewer random differences should arise between datasets.

`@feedback`
- Correct! This is especially the case when we use time-series data. Systematic differences between the treatment and control group are only important if we expect the treatment to have a difference effect on different types of people. For example, if it turned out that the death penalty was only a deterrent for homicide in states with high urban populations, but our treatment group only contained states with high rural populations, we would not see any causal effect of the death penalty on homicide rates.
- Actually, you can see systematic changes across a population with time even with repeated cross sectional datasets. Try again.
- This is close, but having larger samples is generally good for studying causal effects.

---

## The Advantage of Longitudinal Data

```yaml
type: PureMultipleChoiceExercise
key: cd49576c07
lang: r
xp: 50
skills: 1
```

What is the main advantage you get from studying a causal effect with longitudinal dataset rather than repeated cross-sectional datasets?

`@hint`


`@possible_answers`
- [Systematic differences between the treatment and control group are less likely to confound the average treatment effect.]
- You can see systematic changes across a population with time.
- It inherently uses a smaller sample of people, so fewer random differences should arise between datasets.

`@feedback`
- Correct! This is especially the case when we use time-series data. Systematic differences between the treatment and control group are only important if we expect the treatment to have a difference effect on different types of people. For example, if it turned out that the death penalty was only a deterrent for homicide in states with high urban populations, but our treatment group only contained states with high rural populations, we would not see any causal effect of the death penalty on homicide rates.
- Actually, you can see systematic changes across a population with time even with repeated cross sectional datasets. Try again.
- This is close, but having larger samples is generally good for studying causal effects.


---

## Repeated Cross-Sectional Data vs Time-Series Data

```yaml
type: PureMultipleChoiceExercise
key: d1ecc09b78
lang: r
xp: 50
skills: 1
```

When we have repeated cross-sectional data, we have a different sample at each time point. With this sort of data, we cannot estimate within person fixed effects or any difference-in-differences style outcome, as we only have a response from each surveyed individual at one separate time point. Nonetheless, why might repeated cross-sectional data be useful?

`@hint`


`@possible_answers`
- Because it increases your sample size.
- [It can help reveal time trends among a population and outcome of interest.]
- To remove bias that could result from generational differences across a population.
- It is cheaper than gathering longitudinal samples.

`@feedback`
- This is sort of true, but not really the main reason people use repeated cross-sectional survey.
- Correct!
- This is a possible advantage of repeated cross-sectional data, although it is relatively uncommon to have so many cross sections in a dataset that you could even pick up generational differences in outcomes (i.e. cohort effects). Try again.
- This is sort of true, except it is still very expensive to conduct multiple cross-sectional surveys. Cost is less of an issue than is the difficulty in reaching out to individuals who took the survey before.

---

## Practice Implementing a Difference-in-Differences Model

```yaml
type: NormalExercise
key: 0935eeebd0
lang: r
xp: 100
skills: 1
```

The mayor of Sommersdale Ontario is interested in combatting homelessness in his city with a Housing First policy. This policy would have the city pay for cheap apartments for all homeless people with no-strings attached. Supporters of the Housing First policy claim that the majority of the costs in implementing the policy would be offset by the reduced of resources that the city would need to spend on homeless shelters, jail time, and emergency room visits for the chronically homeless. 

While the mayor of Sommersdale is convinced that the Housing First policy would substantially reduce rates of homelessness, he is uncertain whether implementing the program would substantially reduce other city expenditures on the homeless. As a preliminary analysis, the Mayor of Sommersdale gathered data on incarceration rates among 10 cities at two time points, 2005 and 2015, half of which implemented Housing First between 2009 and 2013. Conduct a difference-in-differences analysis with the dataset `Jail` to examine whether the Housing First policy reduced incarceration rates.

`@instructions`
- 1) Examine the dataframe `Jail` to see what data we have.
- 2) Use a t-test to compare the rate of incarceration in 2005 among cities that eventually implemented the Housing First Policy to cities that never implemented the Housing First Policy.
- 3) Use a t-test to compare the rate of incarceration in 2015 among cities that implemented the Housing First Policy to cities that never implemented the Housing First Policy.
- 4) Use a difference-in-differences model to estimate whether cities that implemented the Housing First policy tended to have lower rates of incarceration than one would expect based on common trends.

`@hint`


`@pre_exercise_code`
```{r}
n=10
#Create rnorm function that allows for min and max
    rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
        qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
    }
#Create rounding function that allows to round to numbers above 1
    mround <- function(x,base){ 
        base*round(x/base) 
    } 

set.seed(13)
#Dataframe with year 1
    Jail1<-data.frame(City=c("Moraine","Netarts","Oak City","Heritage Creek","Gallitzin","Trout Valley","Allendale","Boaz","Texanna","Ayer"),Year=2005,rate=round(rtnorm(n,mean=115,sd=50,min=50,max=200),0),Implemented=rbinom(10,1,.4))
    Jail1$rate<-ifelse(Jail1$Implemented==1, Jail1$rate+20,Jail1$rate)
#Dataframe with year 2
    Jail2<-data.frame(City=Jail1$City,Year=2015,Implemented=Jail1$Implemented)
#year 2 rate
    Jail2$rate<-Jail1$rate+Jail2$Implemented*(-20)+ round(rtnorm(n,mean=20,sd=10,min=0,max=50),0)
#Append data
    Jail<-rbind(Jail1,Jail2)
    Jail<-Jail[order(Jail$City,Jail$Year),]
    Jail$Year<-factor(Jail$Year)
    rm("Jail2")
    rm("Jail1")
    
```

`@sample_code`
```{r}
# 1) Since our dataset is small, let's first directly examine the dataset. We have 10 unique cities with 2 time points of data. Cities that implemented the Housing First policy between 2009-2013 are marked with 1 for Implemented. The rate variable refers to rates in incarceration per 100,000. Let's just start by printing the dataframe:
  
    Jail

# 2) Let's use a t.test to assess whether cities that eventually implemented the Housing First policy (`Implemented==1`) tended to have higher rates of incarceration (`rate`) in 2005 (`Year==2005`) than cities that had not implemented the Housing First Policy (`Implemented==0`).

      Solution2<-t.test()

# 3) If you answered Question 2 correctly, you should notice that the rate of incarceration was higher in 2005 among cities that eventually implemented the Housing First policy. Now use a t.test to assess whether cities that implemented the Housing First policy (`Implemented==1`) tended to have higher rates of incarceration (`rate`) in 2015 (`Year==2015`) than cities that had not implemented the Housing First Policy (`Implemented==0`).

      Solution3<-t.test()

# If you answered Question 3 correctly, you should notice that the rate of incarceration was almost equal in 2015 among cities that implemented the Housing First policy and those that did not. If we examined the 2015 data alone, or if we only examined cities that implemented the Housing First Policy we might conclude that implementing the Housing First policy had no effect on incarceration rates. However, there was an increasing trend of incarceration across cities, suggesting that the Housing First policy was actually reducing the rates of incarceration. So let's model this trend with a difference-in-differences policy. 

# 4) To do this, we simply need to construct a linear model that predicts incarceration based on implementation and year, and with an "interaction" term between implementation and year, which estimates measures whether implementating the policy altered the relationship (or trend) between time and incarceration rates. To include an interaction term in your model, simply multiply the two terms that you want to interact. It will look like the following: glm(y ~ x + z + x*z) or simply glm(y ~ x*z), where you insert the correct variable names for y, x, and z.

      Solution4<-glm()
      

```

`@solution`
```{r}
Solution2<-t.test(Jail$rate[Jail$Implemented==1 & Jail$Year==2005],Jail$rate[Jail$Implemented==0 & Jail$Year==2005])
Solution3<-t.test(Jail$rate[Jail$Implemented==1 & Jail$Year==2015],Jail$rate[Jail$Implemented==0 & Jail$Year==2015])
Solution4<-glm(rate~Year*Implemented,data=Jail)
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution4") %>% check_equal()
success_msg("Good work! Implementing a difference-in-differences analysis is relatively easy. We can see from the result of Solution2 that the estimate for Year 2005 and Implemented were positive, suggesting that there was an increasing trend in rates of incarceration over time, and cities that implemented the Housing First policy tended to have higher rates of incarceration. However, the interaction term 'Year2015:Implemented' was negative, meaning that over time, cities that implemented the Housing First policy had negative association with incarceration rates relative to those who did not implement the Housing First policy. In other words, cities that implemented the Housing First policy had lower rates of incarceration than one would expect based on common trends.")
```

---

## Practice Correcting for Changing Measurements.

```yaml
type: NormalExercise
key: d31f6a933d
lang: r
xp: 100
skills: 1
```

Since society is constantly changing, longitudinal surveys often change their questionnaires to better represent the world we live in. For example, prior to the amendment of the Immigration Act in 1965, only a very small percentage of the U.S. population had Asian heritage. Therefore, very few surveys at the time recorded "Asian American" as a response to questions about race - instead, lumping Asian Americans into an "other" race category. In fact, even the US census had not classified Asian Americans as a distinct ethnic group until 1980. 

Other times these changes can be more arbitrary. For example, a study might ask respondents to state how many hours of TV they tend to watch on a given day on a 1-3 scale, with response option 1 = 0-2 hours, 2=2-5 hours and 3 = 5+ hours. However, that study might increase the number of response options in the following year to allow for more detailed information. For example, respondents might be asked to record a precise estimate of how much TV they watch, rounded to the nearest hour.

While it is always good to have detailed data, changing survey response options can pose problems for data analysts. Our models will not know whether our response options changed unless we explicitly tell them so, therefore, changes in our measurements can significantly confound our model estimates. 
  
For practice, modify the `hours` variable in the dataset `TV`, to correct for the somewhat unintuitive findings produced by our difference-in-differences model that estimated how purchasing a new TV effects hours watched in the following year. Specifically:

`@instructions`
- 1) Examine the structure and data we have in our 2 years of data.
- 2) Estimate a difference-in-difference model for the effect of buying a new TV on the hours of television watched.
- 3) Standardize the measurement of hours watched between the two counting systems used in this survey.
- 4) Run another regression model to see if the standardized measurement gives us a more intuitive answer.

`@hint`


`@pre_exercise_code`
```{r}
n=157
#Create rnorm function that allows for min and max
    rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
        qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
    }
#Create rounding function that allows to round to numbers above 1
    mround <- function(x,base){ 
        base*round(x/base) 
    } 

set.seed(1)
#Dataframe with year 1
    TV1<-data.frame(ID=1:n,Wave=1,hours=round(rtnorm(n,mean=2,sd=.5,min=1,max=3),0))
    TV1$new<-rbinom(n,1,.33)
#Dataframe with year 2
    TV2<-TV1
    TV2$hours<-ifelse(TV1$hours==1,rtnorm(n,mean=1,sd=.5,min=0,max=2),ifelse(TV1$hours==2,rtnorm(n,mean=3,sd=1,min=2,max=5),ifelse(TV1$hours==3,rtnorm(n,mean=6,sd=1,min=5,max=10),0)))
    TV2$hours<-round(TV2$hours-.5*TV2$new*TV2$hours^2 + 4*TV1$hours*TV2$new,0)
    TV2$hours<-ifelse(TV2$hours<0,0,TV2$hours)
    TV2$Wave<-2
    
    summary(TV1$hours)
    summary(TV2$hours)
#Append data
    TV<-rbind(TV1,TV2)
    TV<-TV[order(TV$ID,TV$Wave),]
    TV$Wave<-factor(TV$Wave)
    rm("TV2")
    rm("TV1")
    
```

`@sample_code`
```{r}
# 1) We have two waves of data; each ID occurs in each wave one time. The variable `new` indicates whether our sample bought a new TV between the two waves. The  variable `hours` indicates how many hours each respondent used their TV in each wave. During the first wave, respondents were only given three response options for the hours variable, with response option 1 = "up to 2 hours", option 2 = "between 2 to 5 hours", and option 3 "over 5 hours". But during the second wave, the data collection system changed (a common problem in survey analysis). In the second wave, respondents simply recorded the number of hours they tend to watch TV each day.

# Let's first get a sense of what our dataset looks like.

    str(TV)
    head(TV)
    summary(TV$hours[TV$Wave==1])
    summary(TV$hours[TV$Wave==2])

# 2) When we estimate a difference-in-differences model that uses the purchase of a new TV as an interaction term, we see some strange results. We see a substantial increase in hours watched across waves, and a huge effect on hours watched among new TV owners.

    summary(glm(hours~Wave*new,data=TV))

# 3) But remember, the data collection system changed between year 1 and year 2 of this project, and these odd findings may be due to the change in our measurement of hours across the waves. So let's standardize how we count the hours of TV watched. Modify the hours variable in Wave 2 to match the hours variable in wave 1 according to the following plan:
#    - if `hours` at wave 2 is less than or equal to 2, set it to 1
#    - if `hours` at wave 2 is greater than 2 but less than or equal to 5, set it to 2
#    - if `hours` at wave 2 is greater than 5, set it to 3
# This can be done with the subsetting and/or ifelse functions. 

    TV$hours<-

# 4) If you did Question 3 correctly, the following difference-in-differences model should give much more coherent results because we standardized our measurement scheme. So did people who purchased a new TV then watch more hours of television?

    summary(glm(hours~Wave*new,data=TV))
    
```

`@solution`
```{r}
    TV$hours[TV$Wave==2]<-ifelse(TV$hours[TV$Wave==2]<=2,1,ifelse(TV$hours[TV$Wave==2]<=5,2,3))
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("TV") %>% check_equal()
success_msg("Good work! With the standardized measurements, we do indeed see an increase in watch time that is very statistically significant (the p value is about 0.003). So getting a new TV does seem to have a causal effect on how much television people watch. Measurement in surveys is always a tricky matter, because how you measure a response can impact what kinds of quantitative analysis methods you can use, as well as how to interpret the results. In addition, and just as importantly, the respondents will interpret different options in different ways: some might be intimidated if they see too many choices, and others may skip questions that ask for free form answers. It's complicated, so be sure to take it slowly, carefully, and talk about the analysis with other people.")
```

---

## Terminology of Panel Data

```yaml
type: VideoExercise
key: 71b8f49dd5
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/226207441
```


---

## Why Should We Use a Lagged Dependent Variable?

```yaml
type: PureMultipleChoiceExercise
key: 8c5abdde47
lang: r
xp: 50
skills: 1
```

Think about what you know about causal inference. What might be an advantage for modeling your data with a lagged dependent variable; that is, a dependent variable measured at a time point after your explanatory variables were measured?

`@hint`


`@possible_answers`
- Letting time pass allows confounding factors to disappear.
- It gives you more time to formulate your hypothesis.
- [It helps you more clearly establish the causal direction.]
- A dependent variable depends on time, so dependent variables always happen after the independent variables.

`@feedback`
- Time isn't really a factor with determing what is a confounder. If an outside variable affects outcomes, it's a confounder, no matter when in the process it happens. Try again.
- You should be testing a hypothesis you formed before you started, otherwise you aren't following the scientific method! Try again.
- Well done
- You have labeled the dependent and independent variables based on your theory and knowledge of the research question, not based on the direction of the arrow of time. So try again.

---

## Confounders with Fixed Effects Models

```yaml
type: PureMultipleChoiceExercise
key: 8558b47720
lang: r
xp: 50
skills: 1
```

Suppose we are interested in how exercising in a gym affects a person's self-esteem. We try to gather a random sample of individuals at multiple time points, and examine whether individuals who increased their frequency of exercise in a gym had higher self-esteem. However, when assessing the data, we realize that we oversampled white men, who are known to exercise at gyms at high rates, and who tend to have relatively high self-esteem. If we estimate a fixed effects model with this data, will the fact that we oversampled white men confound our results?

`@hint`


`@possible_answers`
- Yes
- [No]

`@feedback`
- Try again
- Correct! Our oversampling of men would clearly confound our estimates in a typical OLS regression model, but since we are only looking at within-person changes, the fact that our sample is biased towards a group of men who tend to exercise and have high self-esteem should not confound our results. As long as the effect of exercise on self-esteem is equal among white men and all other people, and that White men change their rate of exercise as often as the rest of the population, our fixed effects models with this data should accurately reflect the effect of exercise on self-esteem among all people. What is most important is how  the rate of exercise among our sample *changed* over time. If few individuals in our sample increased or decreased their rate of exercise, or if only particular groups tended to change their rates of exercise, our fixed effects models would be biased and have limited statistical power. Individuals whose behavior does not change between waves cannot add to our understanding about how a change in that behavior effects changes in their outcomes.

---

## Practice Running Fixed & Random Effects Regression Models

```yaml
type: NormalExercise
key: 01c162cb87
lang: r
xp: 100
skills: 1
```

Many students at Perry Elementary school write with gel pens. Iris, the school's librarian, is convinced that students could write faster if all the students were required to use ballpoint pens. To test her theory, Iris gets permission to conduct a secondary analysis of an annual student written exam. 

At the end of each school year, students are required to write a three paragraph answer to a short prompt. When students submit their exams, teachers note how long the students took to submit their exams, how many words were written in their exams, and ask the students how many hours of sleep they had slept the previous night. In addition, Iris identified whether the exams were written with a gel or ballpoint pen.

These style exams are given to students three years in a row. Iris was given permission to look at all three of these exams for a single class of students. Since it is possible that students who write with gel pens have different innate writing abilities than those who write with ballpoint pens, Iris decides to only study changes in writing speed for people who switched between using gel pens to ballpoint pens. 

Using the dataset, `Exams`, help Iris estimate the effect of using a ballpoint pen on a student's writing speed with *pooled OLS*, *fixed* and *random* effects models.

`@instructions`
- 1) Examine the structure of the data and the types of variables we have.
- 2) Look more closely at the values of our treatment variables.
- 3) Construct a pooled OLS model that measures the effect of ballpoint pens on student's writing speeds, controlling for age, sex, and hours slept (variables: `pen`,`speed`,`age`,`sex`,`sleep`) .
- 4) Examine the results on that model and interpret what they are saying.
- 5) Construct a fixed effects model that measures the effect of ballpoint pens on student's writing speeds, controlling for age, sex, and hours slept (variables: `pen`,`speed`,`age`,`sex`,`sleep`).
- 6) Determine whether the absolute value of the Gel pen effect is larger or smaller in the fixed effects model than in the pooled OLS model.
- 7) Construct a random effects model that measures the effect of ballpoint pens on student's writing speeds, controlling for age, sex, and hours slept (variables: `pen`,`speed`,`age`,`sex`,`sleep`).

`@hint`


`@pre_exercise_code`
```{r}
library(plm)
n=521
#Create rnorm function that allows for min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
      qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){ 
          base*round(x/base) 
  } 

set.seed(1)
#Dataframe
  Exams<-data.frame(id=1:n,wave=1)
#year 1:
    #age
        Exams$age<-10+rbinom(n=n,1,.2)
    #sex
        Exams$sex<-ifelse(rbinom(n=n,1,.55)==1,"Female","Male")
    #sleep
        Exams$sleep<-mround(rtnorm(n=n,mean=8,sd=1,min=5,max=9),.5)
    #pen
        Exams$pen<-ifelse(rbinom(n=n,1,.5+ifelse(Exams$sex=="Male",.25,0)+1/Exams$age)==1,"Ballpoint","Gel")
    #speed
        Exams$speed<-round((Exams$age/10+(Exams$sex=="Female")/3+(Exams$sleep/rtnorm(n,2,1,1,3)/4)+(Exams$pen=="Ballpoint")*rtnorm(n,.5,.1,0,1))*2+rnorm(n,3,.5),2)

#year 2:
  Exams2<-data.frame(id=1:n,wave=2)
    Exams2$age<-Exams$age+1
    Exams2$sex<-Exams$sex
    Exams2$sleep<-mround(Exams$sleep+rtnorm(n,0,.3,0,1),.5)
    Exams2$pen<-ifelse(rbinom(n,1,.75)==1,Exams$pen,ifelse(rbinom(n=n,1,.4+ifelse(Exams$sex=="Male",.25,0)+1/Exams$age)==1,"Ballpoint","Gel"))
    Exams2$speed<-round(((Exams2$age/10+(Exams2$sex=="Female")/3+(Exams2$sleep/rtnorm(n,2,1,1,3)/4)+(Exams2$pen=="Ballpoint")*rtnorm(n,.5,.1,0,1))*2+rnorm(n,3,.5))/5+Exams$speed,2)

#year 3:
Exams3<-data.frame(id=1:n,wave=3)
    Exams3$age<-Exams2$age+1
    Exams3$sex<-Exams2$sex
    Exams3$sleep<-mround(Exams2$sleep+rtnorm(n,0,.3,0,1),.5)
    Exams3$pen<-ifelse(rbinom(n,1,.75)==1,Exams2$pen,ifelse(rbinom(n=n,1,.4+ifelse(Exams2$sex=="Male",.25,0)+1/Exams2$age)==1,"Ballpoint","Gel"))
    Exams3$speed<-round(((Exams3$age/10+(Exams3$sex=="Female")/3+(Exams3$sleep/rtnorm(n,2,1,1,3)/4)+(Exams3$pen=="Ballpoint")*rtnorm(n,.5,.1,0,1))*2+rnorm(n,3,.5))/5+Exams2$speed,2)
  
#rbind
    Exams<-rbind(Exams,Exams2)
    Exams<-rbind(Exams,Exams3)
    Exams<-Exams[order(Exams$id,Exams$wave),]

```

`@sample_code`
```{r}
# 1) Before running any models, let's examine the data. The dataset contains seven variables. Wave refers to which date in the time series that we are looking at. Wave 1 refers to the first year the data was collected, whereas wave 3 refers to the last year that the data was collected. Since data was collected three times for each individual, each id variable occurs in the data set 3 times.

    str(Exams)
    head(Exams)

# 2) The meaning of the other variables is pretty intuitive. Sleep refers to the number of hours that the students slept the previous night, and speed refers to the number of words that each student wrote per a minute.

    summary(Exams$sleep)
    summary(Exams$speed)

# 3) Run a typical OLS model on the dataset, treating each repeated observation as an independent person (i.e. pooling the data), where speed is the dependent variable, pen is the independent variable, and where we have control variables for age, sex, and sleep. For reference, the syntax for glm models is glm(y ~ x + z1 + z2 + z3, data=df), where y is the dependent variable, x is the independent variable, z1-z3 are control variables, and df is the data frame. You do not need to use the id or wave variables in this model.

    Solution3<-glm()
  
# 4) If you answered question 3 correctly, you should see a large negative effect from using gel pens when you view the summary results: 

    summary(Solution3)
    
# However, when we pool the data this way, we are treating repeated observations as separate people. This is not true. Pooling our data this way will bias our parameter estimates, especially if there is variation in each student's underlying writing ability and these variations are correlated with whether they use gel pens.    
    
# 5) Now let's try estimating a fixed effects model. Random effects models work similarly to OLS models, except that it also controls for how observations in our sample are related. Basically, we want to control for student's different latent writing speeds, and only look at how switching between a gel and ballpoint pen effected their writing speeds compared to those who did not switch pens, To estimate a fixed effects model, we need to use the plm function. The syntax is  identical to glm, except that after the data statement, we specify how the data are grouped (by id and wave) and what type of effect that we want to examine (within person changes). Fill in the front part of the plm model so that it estimates the effect of using a gel pen on writing speed while controlling for age, sex, and sleep.
    
    Solution5<-plm(,index=c("id", "wave"), model="within")

# 6) If you answered question 5 correctly, you should notice that the model only gave us parameter estimates for sleep and gel pens. This is because the sex of students did not change across any years (again, we are only looking at how changes within individuals affected their writing speeds), and because the change in age was uniform across years for all respondents (that is, there was no variation in how student's ages changed across individuals - everyone grew one year older each wave). You should also notice that the parameter estimate for gel pens differs from the first model. Is the absolute value of the effect of gel pens larger or smaller in solution2 than in solution1. Answer with "Larger" or "Smaller".

    Solution6<-""

# 7 ) Although fixed effects models are very reliable, they often require large sample sizes to find statistically significant results, and they often exclude estimating effect that would be interesting to report in a regression model (for example, the effect of age and sex on writing speed). In such cases, we often use random effects models instead. Random effects models are almost identical to fixed effects models, except they make the somewhat strong assumption that the individual specific effects are uncorrelated with your other parameters. In this example, a random effects model assumes that every individual has a latent writing speed that is uncorrelated with anything else. Factors like age and sex simply improve their writing speeds. Estimate a random effects model that groups individuals by id and wave, but that also controls for age, sex, and sleep. The syntax should be identical to that in Question 2, except that the "model" parameter in the plm function should be switched from "within" to "random".

      Solution7<-plm()

```

`@solution`
```{r}
#models    
    Solution3<-glm(speed~pen+sleep+sex+age,data=Exams)
    Solution5<-plm(speed ~ age + sex + sleep + pen, data=Exams, index=c("id", "wave"), model="within")
    Solution6<-"Larger"
    Solution7<-plm(speed ~ age + sex + sleep + pen, data=Exams, index=c("id", "wave"), model="random")
    
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution7") %>% check_equal()
success_msg("Good work! You now know the basics to estimating fixed and random effects models with panel data. As you can see, these models often give very different results than typical pooled OLS models, and their estimates tend to be much more robust. You may still be wondering when you should use random versus fixed effects models. In general, if you can find statistically significant effects with fixed effects models, they are preferable to random effects models. However, there are a variety of tools available for comparing whether you get any benefit from using a fixed effects model (e.g. the Hausman test). In general, use you intution and see what other people have done in similar situations!")
```

---

## Let's Code - Will Subsidies for Electric Cars Help Rural Towns?

```yaml
type: VideoExercise
key: dd8be1b9a4
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/314102576
```


---

## Putting It All Together: Will Subsidies for Electric Cars Help Out Rural Towns?

```yaml
type: NormalExercise
key: a13f46371b
lang: r
xp: 100
skills: 1
```

Located in a part of the country that has been losing heavy industry jobs for the last few decades, the Square Cities area includes the four cities of Greenville, Tarboro, Blackwater, and Milltown. While there are still a few factories and other industries in the area, these four city councils have been trying to make the area more attractive for new businesses and young millennials through new environmental policies, even though this is not always fully supported by the local residents who tend to be politically conservative. Nonetheless, the city of Greenville liked the idea of stimulating the purchase of electric cars, and in 2013, the city's governance decided to subsidize electric car purchases of Greenville residents. 

The city of Greenville now asks you to determine whether the city subsidy had a causal effect on the car purchase behavior of the town's residents. Let's use our analytical skills on panel data to complete the following:

`@instructions`
- 1) Estimate the association between qualifying for a car subsidy and purchasing an electric car with an OLS model on one cross section of the provided dataset (`survey2015`).
- 2) Estimate the association between changes in qualifying for a car subsidy and purchasing an electric car with a fixed effects model and panel data (`survey13.15lf`).
- 3) Estimate the association between qualifying for a car subsidy and purchasing an electric car with a lagged dependent variable approach and panel data (`survey13.15.wf`).
- 4) State whether the time trends reported in the provided data suggest that Greenville's subsidy was effective.
- 5) Determine whether Greenville and its neighbor, Blackwater, are relatively similar across demographic traits.
- 6) Compare trends of electric car ownership to those in Blackwater..

`@hint`


`@pre_exercise_code`
```{r}
# Authors: James Speckart, Brian Aronson, and Attila Gyetvai
library(ggplot2)
library(plyr)
library(plm)
# Initialization
nG <- 390
nB <- 403
n <- nG + nB
set.seed(100)

# City demographics
citydemos<-matrix(c("24.7k","48.6k",38.0,50.9,35.1,"43.8k", "23.1k","46.1k",35.9,51.7,34.8,"42.1k","24.3k","49.1k",38.2,50.4,34.9,"42.0k","25.3k","48.9k",37.8,50.8,35.2,"41.9k"), ncol=6, byrow=TRUE)
colnames(citydemos)<-c("Population","  Median Income", "  Median Age","  % Female", "  % Trees", "  City GDP per Capita")
rownames(citydemos)<-c("Greenville", "Blackwater", "Tarboro", "Milltown")
citydemos<-citydemos[1:2,]
citydemos<-citydemos[,-5]
citydemos<-as.table(citydemos)

# Set up data frame
# Year 1
survey1 <- data.frame(ID = 1:n, year = 2010, city = c(rep("Greenville", nG), rep("Blackwater", nB)))
survey1$income <- ifelse(survey1$city=="Greenville", 1000*(exp(rlnorm(nG, meanlog=1, sdlog=0.2))+30), 
                                                     1000*(exp(rlnorm(nB, meanlog=0.8, sdlog=0.2))+20))
incomeG <- survey1$income[survey1$city=="Greenville"]
incomeB <- survey1$income[survey1$city=="Blackwater"]
survey1$carenature <- 0.75*survey1$income + rnorm(n, 0, 20000)
survey1$carenature <- (survey1$carenature - min(survey1$carenature))/max(survey1$carenature - min(survey1$carenature))
carenatureG <- survey1$carenature[survey1$city=="Greenville"]
carenatureB <- survey1$carenature[survey1$city=="Blackwater"]
cartypeG <- ifelse(incomeG > quantile(incomeG, 0.25), rbinom(nG, 1, 0.9), rbinom(nG, 1, 0.3))
cartypeG[cartypeG>0] <- 1 + rbinom(length(carenatureG[cartypeG>0]), 1, 0.5*carenatureG[cartypeG>0]/max(carenatureG[cartypeG>0]))
cartypeB <- ifelse(incomeB > quantile(incomeB, 0.25), rbinom(nB, 1, 0.9), rbinom(nB, 1, 0.3))
cartypeB[cartypeB>0] <- 1 + rbinom(length(carenatureB[cartypeB>0]), 1, 0.35*carenatureB[cartypeB>0]/max(carenatureB[cartypeB>0]))
survey1$cartype <- c(cartypeG, cartypeB)
survey1$cartype <- factor(survey1$cartype, labels = c("None", "Combustion engine", "Electric"))

# From year 2 on
datagen <- function(df.old, year.var, trans.mat.G, trans.mat.B) {
  
  df.new <- data.frame(ID = 1:n, year = year.var, city = c(rep("Greenville", nG), rep("Blackwater", nB)))
  df.new$income <- df.old$income * (1.02 + rnorm(n, 0, 0.05))
  df.new$carenature <- pmin(pmax(df.old$carenature + rnorm(n, 0, 0.05), 0), 1)
  df.new$cartype[df.new$city=="Greenville" & df.old$cartype=="None"] <- which(rmultinom(length(which(df.new$city=="Greenville" & df.old$cartype=="None")), 1, trans.mat.G[1,])==1, arr.ind = TRUE)[,1] - 1
  df.new$cartype[df.new$city=="Blackwater" & df.old$cartype=="None"] <- which(rmultinom(length(which(df.new$city=="Blackwater" & df.old$cartype=="None")), 1, trans.mat.B[1,])==1, arr.ind = TRUE)[,1] - 1
  df.new$cartype[df.new$city=="Greenville" & df.old$cartype=="Combustion engine"] <- which(rmultinom(length(which(df.new$city=="Greenville" & df.old$cartype=="Combustion engine")), 1, trans.mat.G[2,])==1, arr.ind = TRUE)[,1] - 1
  df.new$cartype[df.new$city=="Blackwater" & df.old$cartype=="Combustion engine"] <- which(rmultinom(length(which(df.new$city=="Blackwater" & df.old$cartype=="Combustion engine")), 1, trans.mat.B[2,])==1, arr.ind = TRUE)[,1] - 1
  df.new$cartype[df.new$city=="Greenville" & df.old$cartype=="Electric"] <- which(rmultinom(length(which(df.new$city=="Greenville" & df.old$cartype=="Electric")), 1, trans.mat.G[3,])==1, arr.ind = TRUE)[,1] - 1
  df.new$cartype[df.new$city=="Blackwater" & df.old$cartype=="Electric"] <- which(rmultinom(length(which(df.new$city=="Blackwater" & df.old$cartype=="Electric")), 1, trans.mat.B[3,])==1, arr.ind = TRUE)[,1] - 1
  df.new$cartype <- factor(df.new$cartype, labels = c("None", "Combustion engine", "Electric"))
  return(df.new)
                      
}
trans.mat.pre <- matrix(c(0.8, 0.15, 0.05, 0.075, 0.8, 0.125, 0.05, 0.075, 0.875), 3, 3, byrow = TRUE)
trans.mat.post <- matrix(c(0.8, 0.1, 0.1, 0.1, 0.65, 0.25, 0.05, 0.06, 0.89), 3, 3, byrow = TRUE)
survey2 <- datagen(survey1, 2011, trans.mat.pre, trans.mat.pre)
survey3 <- datagen(survey2, 2012, trans.mat.pre, trans.mat.pre)
survey4 <- datagen(survey3, 2013, trans.mat.post, trans.mat.pre)
survey5 <- datagen(survey4, 2014, trans.mat.post, trans.mat.pre)
survey6 <- datagen(survey5, 2015, trans.mat.post, trans.mat.pre)
survey7 <- datagen(survey6, 2016, trans.mat.post, trans.mat.pre)

# Long data
survey <- rbind(survey1, survey2, survey3, survey4, survey5, survey6, survey7)
survey <- survey[order(survey$ID, survey$year),]

# Lag carenature
# lg <- function(x)c(NA, x[1:(length(x)-1)])
# survey <- ddply(survey, ~ID, transform, l.carenature = lg(carenature))

# DD plot
# df.plot <- aggregate(cartype=="Electric" ~ year + city, survey, sum)
# df.tmp <- aggregate(cartype!="None" ~ year + city, survey, sum)
# names(df.plot) <- c("year", "city", "num.electric")
# df.plot$share.electric <- df.plot$num.electric/df.tmp$cartype
# ggplot(df.plot[df.plot$city=="Greenville",], aes(x = year, y = share.electric, color = city)) +
#   geom_point() +
#   geom_line() +
#   labs(x = "Year", y = "Share of electric cars")
# ggplot(df.plot, aes(x = year, y = share.electric, color = city)) +
#   geom_point() +
#   geom_line() +
#   labs(x = "Year", y = "Share of electric cars")

#Converting DD Plot into single command to run in sample code
GraphRates<-function(){
df.plot <- aggregate(cartype=="Electric" ~ year + city, survey, sum)
df.tmp <- aggregate(cartype!="None" ~ year + city, survey, sum)
names(df.plot) <- c("year", "city", "num.electric")
df.plot$share.electric <- (df.plot$num.electric/df.tmp$cartype)/5
ggplot(df.plot[df.plot$city=="Greenville",], aes(x = year, y = share.electric, color = city)) +
    geom_point() +
    geom_line() +
    labs(x = "Year", y = "Share of electric cars")
}

GraphComparingCities<-function(){
df.plot <- aggregate(cartype=="Electric" ~ year + city, survey, sum)
df.tmp <- aggregate(cartype!="None" ~ year + city, survey, sum)
names(df.plot) <- c("year", "city", "num.electric")
df.plot$share.electric <- (df.plot$num.electric/df.tmp$cartype)/5
ggplot(df.plot[df.plot$city=="Greenville",], aes(x = year, y = share.electric, color = city)) +
    geom_point() +
    geom_line() +
    labs(x = "Year", y = "Share of electric cars")
ggplot(df.plot, aes(x = year, y = share.electric, color = city)) +
    geom_point() +
    geom_line() +
    labs(x = "Year", y = "Share of electric cars")
}



#Beginning parts of question:
rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
        qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
    }
mround <- function(x,base){
    base*round(x/base)
}
set.seed(100)
n=213
#prep initial data
survey2015<-data.frame(
    below.threshold=rbinom(n,1,.45),
    college=rbinom(n,1,.25),
    male=rbinom(n,1,.6),
    id=1:n
)
#allow threshold info to vary
    survey2013<-survey2015
    subsam<-rbinom(n,1,.2)
    survey2013$below.threshold[subsam==1]<-1-survey2013$below.threshold[subsam==1]
#make miles driven correlated with male and threshold
    survey2013$milesdriven<-rtnorm(n,mean=15000,sd=8000,min=6000,max=25000)+4000*survey2013$male-2000*survey2013$below.threshold
#determine factors for buying electric
    a<-survey2013$milesdriven/10000+.4*survey2013$male+.05*survey2013$college+survey2013$below.threshold
a<-(a-min(a))/max(a)/1.5
summary(a)
    survey2013$bought.electric<-rbinom(n,1,.05)
    survey2015$bought.electric<-rbinom(n,1,a)
#miles driven in 2015 determined by buying electric
    survey2015$milesdriven<-survey2013$milesdriven+
    rtnorm(n,mean=0,sd=2000,min=-5000,max=5000)
    survey2015$milesdriven[survey2015$bought.electric==1]<-survey2015$milesdriven[survey2015$bought.electric==1]*  rtnorm(length(survey2015$milesdriven[survey2015$bought.electric==1]),mean=1.5,sd=.1,min=1,max=2)
survey2015$milesdriven[survey2015$milesdriven>30000]<-survey2015$milesdriven[survey2015$milesdriven>30000]-10000

#two wave versions of this (long format)
    survey13.15lf<-rbind(survey2013,survey2015)
    survey13.15lf$year<-rep(c(2013,2015),each=n)
    survey13.15lf<-survey13.15lf[order(survey13.15lf$id,survey13.15lf$year),]

#two wave versions of this (wide format)
    temp1<-survey2013
    names(temp1)<-paste(names(temp1),"2013",sep=".")
    temp2<-survey2015
    names(temp2)<-paste(names(temp2),"2015",sep=".")
    survey13.15wf<-cbind(temp1,temp2)


```

`@sample_code`
```{r}
# Intro: Greenville collected a lot of relevant information about their experiment. As a first cut, they shared a series of annual surveys they collect about town-member's demographic's and car-purchases. Greenville suggests that you compare the rate of electric car purchases in 2015 for citizens who were below the necessary income threshold for attaining a subsidy to citizens who were above the necessary income threshold for attaining a subsidy (i.e. those who did not qualify). They expect that individuals right below the income threshold would be more likely to purchase electric cars, controlling for other demographic characteristics. 

# 1) Use dataset "survey2015" to estimate the association between qualifying for a car purchase (`below.threshold`) and purchasing an electric car (`bought.electric`) controlling for college education (`college`), gender (`male`), and miles driven that year (`milesdriven`)

    summary(survey2015)
    glm()

# Note: For simplicity, we ask that you run this as an OLS regression (glm's default), rather than as logistic regression. However, in most cases, a logistic regression would be more appropriate for this question.
    
# 2) If you had answered the above correctly, you will see that being below the threshold for subsidies had no significant association with buying an electric car. Why might be the case? Greenville argues that our model is misspecified, as our independent variables might be endogenously confounded. Greenville suggests that we try running a fixed effects model, to more directly test whether falling below or above the subsidy threshold over time motivates households to purchase electric cars. Run a fixed effects model on a the long-formatted panel dataset `survey13.15lf` to see whether people who qualified for subsidies (`below.threshold`) in 2015 but not 2013 (or vice-versa) were more likely to purchase electric cars (`bought.electric`), controlling for (`milesdriven`). As a hint, we filled in some of the model for you.
  
    summary(survey13.15lf)
    plm( index=c("id", "year"), model="within")    
    
# Note: Notice that we did not control for college or male in this model. The reason why is because these variables did not change (i.e. they were time-invariant); if we include them in a fixed effects model, we will not estimate a coefficient for them, as they have no variance in the fixed-effects approach.
    
# 3) The answer still seems to be "no", the subsidy did not incentivize car purchases. Greenville now argues that the problem with the fixed-effects approach is that their sample was not large enough. Less than a quarter of the sample ever changed income thresholds. Moreover, the causal relationship between miles driven and buying an electric car is not clear in this model; driving more miles may incentivize electric car ownership, but buying an electric car may incentivize driving more miles. This unclear causal relationship may have confounded the relationship between qualifying for subsidies and purchasing an electric car. As a final test, Greenville suggests that you run a regression model with a lagged dependent variable. Specifically, they ask you use a wide-format version of this panel data (survey13.15wf) to test the effect of qualifying for a car purchase in 2013 (`below.threshold.2013`) on purchasing an electric car in 2015 (`bought.electric.2015`) controlling for other 2013 variables, including college education (`college.2013`), gender (`male.2013`), and miles driven that year (`milesdriven.2013`)
    
    summary(survey13.15wf)
    glm()
     
# Note: If you ran the above model correctly, you will see a positive statistically significant effect of qualifying for electric car subsidies in 2013 on electric car ownership in 2015. It seems that the potentially reverse causal relationship between miles driven and electric car ownership in 2015 was confounding this relationship. 

# 4a) The mayor of Greenville reflects on our findings, and now asks and important question: "The subsidies seem to motivate people near the subsidy threshold to purchase more electric cars, but does this really matter in the grand scheme of things? Did the policy really improve rates of electric car ownership in Greenville?" One of his consultants sugggests that we look at the following graph (to see it, run GraphRates()) to generate a graph that displays the share of electric cars within all cars in Greenville and neighboring Blackwater on a year-by-year basis, including when Greenville created a subsidy for electric cars in 2013: 

    GraphRates()      

# 4b) This consultant argues that rates of electric car ownership have grown a great deal over the past few years, therefore the subsidy must have been effective. Based on this graph, can you tell whether the subsidy was effective? Write "yes" or "no" for Solution1.
    
    Solution4 <- ""

# 5) Let's think of a way to use the Difference-in-Differences approach to find out if this is a causal effect. In the Difference-in-Differences approach, we should try to compare rates of electric car ownership among otherwise very similar cities. The mayor of Greenville suggests we compare Greenville to the nearby city of Blackwater, which did not subsidize electric car purchases over the same years. If the cities are very similar across key demographics, then we can feel confident that we can compare them with a difference-in-differences approach. Print out the table of collected demographics with the following line of code, and answer the following question with "yes" or "no": Would you consider the cities to be relatively similar across these core demographic traits?

    print(citydemos, right=TRUE)
    Solution5 <- ""

# Note: We accept all solutions for the above question, as the does not have a clear answer. Keep in mind that these are very much the type of question you will encounter in the real world.
    
# 6) Regardless of your answer above, let's assume that the two cities are similar enough to warrant comparison. Run the following code to illustrate a comparison of the share of electric cars owned in Greenville and Blackwater. Assuming the differences are statistically significant, can you say with relative confidence whether the subsidy worked in Greenville? Write "yes" or "no" for Solution2.
    
    GraphComparingCities()
    Solution6 <- ""

    
```

`@solution`
```{r}
#1)
summary(glm(bought.electric~below.threshold+college+male+milesdriven,data=survey2015))
#2)
summary(plm(bought.electric~below.threshold+college+male+milesdriven, data = survey13.15lf, index=c("id", "year"), model="within"))
#3)
summary(glm(bought.electric.2015~below.threshold.2013+college.2013+male.2013+milesdriven.2013,data=survey13.15wf))
Solution4 <- "no"
Solution5 <- "maybe"
Solution6 <- "yes"
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution4") %>% check_equal()
ex() %>% check_object("Solution6") %>% check_equal()
success_msg("Congratulations! By now, you should have a sense of the sorts of causal inference problems that panel data can help us overcome. There are a variety of methodological approaches you can take with panel data, each with their own pros and cons. This is why it is always critical to carefully think through what your cause and outcomes of interest are, and how they might be related causally. If you found this course useful, consider trying our other courses on Causal Inference with R.")
```
