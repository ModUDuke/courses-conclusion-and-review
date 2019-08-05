---
title: Introduction
description: 'If you want to go through these topics in more detail, take our free Causal Inference with R - Introduction course here on DataCamp.'
---

## INTRO: Comparing Breakfast Cereals: Outcome Variables

```yaml
type: PureMultipleChoiceExercise
key: 362bf33c36
lang: r
xp: 50
skills: 1
```

The food scientists at breakfast cereal manufacturer Puritan Wheat Inc. have developed a new breakfast cereal product called TechnoCrunch. It has a biodegradable nanomaterial coating designed to keep its flakes crispy in milk for longer than the flakes in its competitor cereal, NeoPuffs. Now Puritan Wheat wants to run an experiment to see if the formula works, so it compares the time it takes for TechnoCrunch to get soggy in milk versus the time it takes for NeoPuffs to get soggy. 

In this experiment on the two cereals, which of the following is the outcome variable in Puritan Wheat's analysis?

`@hint`


`@possible_answers`
- The brand of cereal.
- The amount of milk that each flake of cereal can absorb.
- [The time it takes for the cereal to get soggy.]
- Individual flakes.

`@feedback`
- This is the experimental condition that causes the outcome, i.e. the treatment variable, also called the independent variable (because we have the freedom to manipulate its value in an experiment). Try again.
- This is likely correlated with how the dependent variable, but is not mentioned in the prompt. Try again
- Correct! The outcome variable is one's outcome of interest. You will see it also called the dependent variable, because its value depends on the treatment. You might also see the treatment being called the independent variable, because we have the freedom to manipulate its value in an experiment.
- Not quite. Try again.

---

## Comparing Breakfast Cereals: Units of Analysis

```yaml
type: PureMultipleChoiceExercise
key: 50d28d8b25
lang: r
xp: 50
skills: 1
```

Puritan Wheat generates some data from a sample of individual flakes in a box of TechnoCrunch and from a box of its competitor's cereal, NeoPuff's. Puritan Wheat intends to examine the average time it takes for each flake to become soggy. What is the unit of analysis in this study?

`@hint`


`@possible_answers`
- The brand of cereal
- The amount of milk that each flake of cereal can absorb
- The time it takes for the cereal to get soggy
- [Individual flakes]

`@feedback`
- This is the experimental condition that causes the outcome, i.e. the treatment (a.k.a. independent) variable. Try again.
- Not quite. Try again.
- This is the outcome (a.k.a. dependent) variable in our analysis, try again.
- Correct! The unit of analysis is what or who is being studied or sampled. Often our unit of analyses are individual people, but in this example, we are studying a sample of cereal flakes.

---

## Anscombe Quartet

```yaml
type: MultipleChoiceExercise
key: c229f94a13
lang: r
xp: 50
skills: 1
```

On the right are a series of numerical distributions. The correlations between the x and y axis in each graph is about the same. What does this mean?

`@possible_answers`
- The graphs are identical.
- [Correlations do not give a perfect summary of how a dataset is distributed.]
- There is no meaningful difference in the distribution of datapoints across these graphs.
- The correlation function is broken.

`@hint`


`@pre_exercise_code`
```{r}
library(gridExtra)
library(ggplot2)

#correlation
cor1 <- format(cor(anscombe$x1, anscombe$y1), digits=4)
cor2 <- format(cor(anscombe$x2, anscombe$y2), digits=4)
cor3 <- format(cor(anscombe$x3, anscombe$y3), digits=4)
cor4 <- format(cor(anscombe$x4, anscombe$y4), digits=4)

#define the OLS regression
line1 <- lm(y1 ~ x1, data=anscombe)
line2 <- lm(y2 ~ x2, data=anscombe)
line3 <- lm(y3 ~ x3, data=anscombe)
line4 <- lm(y4 ~ x4, data=anscombe)

circle.size = 5
colors = list('red', '#0066CC', '#4BB14B', '#FCE638')

#plot1
plot1 <- ggplot(anscombe, aes(x=x1, y=y1)) + geom_point(size=circle.size, pch=21, fill=colors[[1]]) +
  geom_abline(intercept=line1$coefficients[1], slope=line1$coefficients[2]) +
  annotate("text", x = 12, y = 5, label = paste("correlation = ", cor1))

#plot2
plot2 <- ggplot(anscombe, aes(x=x2, y=y2)) + geom_point(size=circle.size, pch=21, fill=colors[[2]]) +
  geom_abline(intercept=line2$coefficients[1], slope=line2$coefficients[2]) +
  annotate("text", x = 12, y = 3, label = paste("correlation = ", cor2))

#plot3
plot3 <- ggplot(anscombe, aes(x=x3, y=y3)) + geom_point(size=circle.size, pch=21, fill=colors[[3]]) +
  geom_abline(intercept=line3$coefficients[1], slope=line3$coefficients[2]) +
  annotate("text", x = 12, y = 6, label = paste("correlation = ", cor3))

#plot4
plot4 <- ggplot(anscombe, aes(x=x4, y=y4)) + geom_point(size=circle.size, pch=21, fill=colors[[4]]) +
  geom_abline(intercept=line4$coefficients[1], slope=line4$coefficients[2]) +
  annotate("text", x = 15, y = 6, label = paste("correlation = ", cor4))

grid.arrange(plot1, plot2, plot3, plot4, top='Anscombe Quartet', bottom="Syntax to produce graphs borrowed from Sean Dolinar (stats.seandolinar.com-Tutorials)")
```

`@sct`
```{r}
- Look at the graphs to the right of the page. Are you sure they look identical?
- Yes. This is why statisticians have created so many different types of summary statistics, and why we encourage understanding so many of them.
- Not necessarily. The distributions certainly appear different to the eye, and so perhaps different dynamics are at work in each graph. Try again.
- Unless the webserver just broke, the correlation function is working perfectly, and it's not the reason these graphs seem different. Try again.

```

---

## Learn Engineering by Eating Cheese?

```yaml
type: PureMultipleChoiceExercise
key: 4b7a7da2a4
lang: r
xp: 50
skills: 1
```

![](https://assets.datacamp.com/production/repositories/1444/datasets/fdf1e1ca75881f0c95ccd9c843580761cda5612e/chart.jpeg)

As you can see in this chart, the per capita consumption of mozzarella cheese in the US is highly correlated with the number of PhDs awarded annually in Civil Engineering in the US. In fact, it’s a 95% correlation. Therefore, does this strong data prove that these two variables are **causally** connected?

`@hint`


`@possible_answers`
- Definitely. 95% correlations do not just happen in real life, so there must be a cause and effect reason behind it, even if we don’t know what it is.
- [No. This is just a spurious correlation between random variables, and even very strong correlations do not imply causation.]

`@feedback`
- It can be so tempting to assume that any strong correlations in our data are telling us about the cause and effect relationships going on in real life, but don’t give into that temptation! We’ll need to do more to find a causality. Try again.
- Correct! You will find many correlations in your data, sometimes very strong ones like this, but that does not mean there’s any causal relationship between them. Sometimes a correlation may help you ask better questions about what’s going on, but don’t assume they are causal by themselves.

---

## Understanding Confounders

```yaml
type: PureMultipleChoiceExercise
key: ac9bc35c31
lang: r
xp: 50
skills: 1
```

Why are confounding variables a potential problem for causal inference?

`@hint`


`@possible_answers`
- Because confounding variables prevent the treatment from being randomly assigned
- [Because confounding variables might alter the association between the treatment and dependent variable]
- Because confounders are not observed

`@feedback`
- Almost, but remember, the main reason we worry about confounders has to do with effects on the outcome, not on treatment assignment. Try again.
- Correct! Confounders are called *confounders* for a reason---because when they are present, we cannot distinguish the effect of treatment from the effect of the confounder. To learn causal effects, we want to compare people with treatment and people without treatment. If those two groups of people differ in their values of some potential confounding variable, then we can't tell if differences in outcomes are due to differences in treatment, or differences in the confounder.
- Unobserved variables are not always a problem in causal inference, because they may not have any effect on outomes. Try again.

---

## Baseball Ad Campaign: Early Success?

```yaml
type: PureMultipleChoiceExercise
key: 0ecec920ef
lang: r
xp: 50
skills: 1
```

Let’s see what happened in the first month of the ad campaign for our individual fan. Take a look at the following table:

| Month    |Attended|Ads Served|
|----------|-------:|---------:|
| April    |   0    |    0     |
| May      |   1    |    0     |
| June     |   2    |    0     |
| July     |   7    |    5     |
| August   |   -    |    -     |
| September|   -    |    -     |

Since the number of baseball games that this individual went to appears to increase after viewing 5 ads, can we conclude that the advertising campaign caused the individual to go to more games?

`@hint`


`@possible_answers`
- Yes, the treatment had a positive effect on the outcome variable.
- No, the treatment had no effect.
- [It's too early to tell.]

`@feedback`
- Not yet! We do not know whether the difference in games attended after being exposed to the ad-campaign was statistically significant, nor do we have a sense for any potential confounding variables.
- Not yet! We do not know whether the difference in games attended after being exposed to the ad-campaign was statistically significant, nor do we have a sense for any potential confounding variables.
- Correct! Stopping this analysis just because we like the results in the first month would be hacking our results. This month could just be due to confounders. We should let the ad campaign run for the whole season to get a better conclusion.

---

## Let’s Code: A Problem with Employee Unhappiness

```yaml
type: VideoExercise
key: 6b8a71d25a
xp: 50
video_link: //player.vimeo.com/video/276320364
```


---

## Unhappiness at Unter: Identifying Heterogeneous Outcomes - ATE

```yaml
type: NormalExercise
key: 311670fb1a
lang: r
xp: 100
skills: 1
```

The transportation network company, Unter Technologies, is interested in improving their employee morale and reducing employee turnover rate by downsizing their Human Resources (HR) Department.

To make sure this would not antagonize their workforce, Unter conducts an experiment: With a balanced sample of employees, Unter tells a treatment group that the HR Department will be downsized in the following year, and a control group that the HR Department will remain the same size in the following year (and magically, they don't end up discussing this with each other). Unter then surveys the employees to find out whether employees plan to look for new jobs, with response options 0="No" and 1="Yes."

With the dataframe, `UnterHR`, determine whether there is a negative or positive average treatment effect of reducing the size of Unter's HR department on employee turnover:

`@instructions`
- 1) Determine the average effect of reducing the size of HR (`treatment`) on whether employees plan to leave their job in the following year (`LeaveJob`).

`@hint`
- Try breaking the task into pieces. First find the mean rate of `LeaveJob`in the control condition (`Treatment==0`) then find the mean rate of `LeaveJob`in the treatment condition (`Treatment==1`).

`@pre_exercise_code`
```{r}
library(dplyr)
set.seed(1)
n=382
#Dataframe
  UnterHR<-data.frame(Treatment=rbinom(n,1,.4),Female=rbinom(n,1,.1),LeaveJob=0)
#LeaveJob
  #treatment makes men less likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),1,.2)
  #treatment makes wommen more likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]),1,.6)
```

`@sample_code`
```{r}
# Note 1: The average treatment effect is simply the mean outcome of the treatment group minus the mean outcome of the control group. The mean outcome overall is calculated below:

    mean(UnterHR$LeaveJob)

# Note 2: You will need to `subset` the data into treatment and control groups. For example, we create a data frame for just those in the treatment group below:

    dfTreated<-UnterHR[UnterHR$Treatment==1,]

# 1) Write the code that finds the average effect of reducing the size of HR (`treatment`) on whether employees plan to leave their job in the following year (`LeaveJob`). Assign this value to Solution1.

    Solution1<-
    
```

`@solution`
```{r}
Solution1<- mean(UnterHR$LeaveJob[UnterHR$Treatment==1])-mean(UnterHR$LeaveJob[UnterHR$Treatment==0])
```

`@sct`
```{r}
test_object("Solution1")
success_msg("Good work! It seems that reducing the size of HR reduced Unter employees' intentions to leave their jobs")
```

---

## Unhappiness at Unter: Identifying Heterogeneous Outcomes - CATEs

```yaml
type: MultipleChoiceExercise
key: 6217752659
lang: r
xp: 50
skills: 1
```

Since reducing the size of HR seems to reduce the rate of employee turnover, the CEO of Unter Technologies is now heavily considering this option.

However, his chief operating officer (COO) warns him that reducing the size of HR might be unpopular among certain minority groups within the company, particularly among women. The COO sends the CEO a figure (illustrated in the R workspace) showing the results of his experiment among men and women. Which of the following does the figure suggest?

`@possible_answers`
- [While the pooled average treatment effect is slightly negative, and the average treatment effect for men is negative, the average treatment effect for women is positive.]
- While the pooled average treatment effect is slightly positive, and the average treatment effect for men is positive, the average treatment effect for women is negative.
- While the pooled average treatment effect is slightly negative, and the average treatment effect for men is positive, the average treatment effect for women is negative.
- While the pooled average treatment effect is slightly positive, and the average treatment effect for men is negative, the average treatment effect for women is positive.

`@hint`


`@pre_exercise_code`
```{r}
library(dplyr)
set.seed(1)
n=382
#Dataframe
  UnterHR<-data.frame(Treatment=rbinom(n,1,.4),Female=rbinom(n,1,.1),LeaveJob=0)
#LeaveJob
  #treatment makes men less likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),1,.2)
  #treatment makes wommen more likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]),1,.6)
    library(ggplot2)
    library(scales)
    df<-data.frame(Treatment=c("Control","Control","Treatment","Treatment"),Gender=c("Male","Female","Male","Female"),Value=c(mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1])))
    df<-data.frame(Treatment=c("Control","Control","Control","Treatment","Treatment","Treatment"),Gender=c("Male","Female","Pooled","Male","Female","Pooled"),Value=c(mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),mean(UnterHR$LeaveJob[UnterHR$Treatment==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1])))
    df$Gender<-factor(df$Gender, levels = c("Male","Pooled","Female"))
    df$`Percent Intending to Quit`<-df$Value
    df$`Control and Treatment Groups`<-df$Treatment
    p<-ggplot(df, aes(x=`Control and Treatment Groups`,y=`Percent Intending to Quit`,group=Gender,color=Gender))
    p+geom_point(size=3)+geom_line(size=2)+scale_y_continuous(label = percent,limits = c(0,1))
```

`@sct`
```{r}

```

---

## Unhappiness at Unter: Identifying Heterogeneous Outcomes - CATEs (2)

```yaml
type: NormalExercise
key: a4ab5d9f9b
lang: r
xp: 100
skills: 1
```

Let's further analyze the heterogeneous effect of the treatment on men vs. women in Unter Technologies. With the dataframe, `UnterHR`, determine the average treatment effect of reducing the size of Unter's HR department on employee turnover by gender (`Female`).

`@instructions`
- 1) Determine the average effect of reducing the size of HR (`treatment`) on whether male employees (`Female = 0`) plan to leave the job in the following year (`LeaveJob`).
- 2) Determine the average effect of reducing the size of HR (`treatment`) on whether female employees (`Female = 1`) plan to leave the job in the following year (`LeaveJob`).

`@hint`
- Remember, you can determine the ATE by subtracting the mean rate of the outcome in the control condition by the mean rate of the outcome in the treatment condition.
- You will need to use the `mean` and `subset` commands.
- Try breaking the task into pieces. First find the mean rate of `LeaveJob`in the control condition (`Treatment=0`) then find the mean rate of `LeaveJob`in the treatment condition (`Treatment=1`).

`@pre_exercise_code`
```{r}
library(dplyr)
set.seed(1)
n=382
#Dataframe
  UnterHR<-data.frame(Treatment=rbinom(n,1,.4),Female=rbinom(n,1,.1),LeaveJob=0)
#LeaveJob
  #treatment makes men less likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),1,.2)
  #treatment makes wommen more likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]),1,.6)
```

`@sample_code`
```{r}
# Note: Since we are interested in understanding the rates of intention to leave by treatment and gender, we might want to examine a three way table of this relationship first. The following syntax prints the numbers of men and women who intend to leave work by treatment group and gender:

    xtabs(~LeaveJob+Treatment+Female, data=UnterHR)

# Note: This question is tricky because we want to subset the data based on two condition (i.e. whether someone is treated and whether someone is female). Below is an example of how to get the mean rate of leaving a job for men who were treated. The `&` symbol is used to add an additional condition:

    mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0])

# 1) Write the code that determines the average treatment effect among men. Assign this value to Solution1.

    Solution1<- 

# 2) Write the code that determines the average treatment effect among women. Assign this value to Solution2.

    Solution2<-
```

`@solution`
```{r}
Solution1 <- mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0])-mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0])
Solution2 <- mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1])-mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1])
```

`@sct`
```{r}
test_object("Solution1")
test_object("Solution2")
success_msg("Good work! We can see a clear difference in the treatment effect among men and women. This is a clear example of a conditional average treatment effect.")
```

---

## Insert exercise title here

```yaml
type: NormalExercise
key: deb104dc83
xp: 100
```

blorpy bloro	anasdf thenadlknals dkjf ;ajsdoiuf asdf dlijdf	

`@instructions`
Firstj do that
then do this man
woah

`@hint`
i told you to do that you person of character!

`@pre_exercise_code`
```{r}
library(dplyr)
library(ggplot2)

do stuff	

nvme<-1
```

`@sample_code`
```{r}
what is it for? man
```

`@solution`
```{r}
the solution is nvme=1
```

`@sct`
```{r}
nvme=1

did you get nvme=1? then great!
```
