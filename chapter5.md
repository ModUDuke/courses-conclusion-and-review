---
title: 'Modeling with Regression'
description: 'If you want to go through these topics in more detail, take our free Causal Inference with R - Modeling with Regression course here on DataCamp.'
---

## The Basics of Modeling Behavior

```yaml
type: VideoExercise
key: 812b575a73
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/231746347
```


---

## Discrete Choice Analysis

```yaml
type: VideoExercise
key: 09bccc78e5
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/231746571
```


---

## Lots of Variables vs. Confounders in Discrete Choice Analysis

```yaml
type: PureMultipleChoiceExercise
key: d81765e7b7
lang: r
xp: 50
skills: 1
```

Someone doing a Big Data analysis tells you the following. "I included over 1,000 variables in my analysis. Since I have so many control variables, so I do not have to worry about confounders." Do you agree?

`@hint`
`@possible_answers`
- Maybe
- Yes
- [No]

`@possible_answers`


`@feedback`
- There is a yes or no answer for this. Try again.
- That's incorrect. What if there are key elements to the causal chain that were left out by chance or omission? Try again.
- Correct! The total number of variables you include generally has no relationship to whether you have to worry about confounders or not. All of these 1,000 variables might be just randomly generated numbers from the computer. In that case it's actually worse to include them than to leave them out! What matters is the substantive interpretations of these variables, and whether they measure all variables that might have a causal effect on outcomes.

---

## Using Modeling When Experiments Are Impossible

```yaml
type: VideoExercise
key: 4c6f64e320
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/231747210
```


---

## Why Use Models Instead of Experiments?

```yaml
type: undefined
key: 37e8196773
```



---

## Let's Code: Red Wine - The Secret to Living Longer?

```yaml
type: undefined
key: d89266b4c8
```



---

## Red Wine: the Secret to Living Longer?

```yaml
type: NormalExercise
key: 326e16239a
lang: r
xp: 100
skills: 1
```

Red wine has resveratrol, a substance that reduces the risk for heart disease. Moderate consumption of red wine is believed to promote longevity. Jenny is very health-conscious and wants to figure out whether red wine is a longevity promoter. She is interested in examining the effect of wine consumption on longevity. She doesn't have the capacity to run a huge medical experiment herself, so she decides to instead download some public data and develop some models to see what she can learn. The data set `Data.wine` contains 4 variables and 60 observations. The data dictionary is below.
  
Data Dictionary:
     `ID` - subject identifier
     `Wine`- drinking level (light, moderate, and heavy)
     `Age` - age at death
     `Exercise` - hours spent on exercise per week

`@instructions`
- 1) Get a sense of the variable names, types, and values in our dataset.
- 2) Create a box plot that compares the amount a person drinks to how long they live.
- 3) Run a regression to see the connection between wine consumption and the average age at death.
- 4) Does the amount you exercise affect this relationship between wine drinking and lifespan?
- 5) Run a regression on wine consumption and lifespan that compensates for exercise level.

`@hint`


`@pre_exercise_code`
```{r}
  library(plyr)
  library(ggplot2)
  set.seed(123)
#Dataframe
  Wine <- c(rep("light",30),rep("moderate",20),rep("heavy",10))
  Wine <- factor(sample(Wine,replace = FALSE),levels = c("light","moderate","heavy"))
  ID <- 1:60
  Age <- rep(NA,60)
  Exercise <- rep(NA,60)
  Data.wine <- data.frame(ID,Wine,Age,Exercise)
#moderate drinkers live longer, heavy drinkers live the least
  Data.wine$Age[Data.wine$Wine=="light"] <- round(rnorm(30,78,10),0)
  Data.wine$Age[Data.wine$Wine=="moderate"] <- round(rnorm(20,85,6),0)
  Data.wine$Age[Data.wine$Wine=="heavy"] <- round(rnorm(10,75,6),0)
  
#Moderate drinkers also exercise more 
  Data.wine$Exercise <- round((Data.wine$Age + 10)/10 + rnorm(60,0,1),0)
  Data.wine$Exercise[Data.wine$Exercise<0] <- 0
  
  col <- rep("red",60)
  col[Data.wine$Wine=="light"] <- "green"
  col[Data.wine$Wine=="moderate"] <- "orange"
  col[Data.wine$Wine=="heavy"] <- "yellow"
```

`@sample_code`
```{r}
# Plotting the Age at Death among Different Drinking Levels
  
# 1) The primary outcome of interest is difference in age at death (`Age`) among different drinking levels (`Wine`).  The first 6 observations is below:
  
  	head(Data.wine)
  
# 2) Let's create a box plot that plots the primary outcome as a function of drinking level using ggplot. Is there any evidence of a relationship between the two variables? Run the R code below.
  
  	ggplot(Data.wine, aes(x=Wine, y=Age, fill=Wine))+geom_boxplot()
  
# The mean values of age at death look different, but are they? Let's use linear regression (lm) to find out. 
  
# 3) Regress `Age` on `Wine` and print the summary statistics. Please provide the R code below.
  
  
  
# Hours of Exercise among Different Drinking Levels
  
# The results from simple regression show that moderate wine consumption is associated with longer life expectancy. However, can we draw the conclusion that moderate consumption of red wine promotes longevity? Moderate wine consumers may be more health-conscious and have better self-control. The might have other healthy habits (i.e., physical exercise) that contribute to longevity. 
  
# 4) Let's create a 3 by 3 table that contains averages of `Exercise` by drinking level in the first column and the standard deviations of `Exercise` by drinking level in the second column. Run the R code below. 
  
    ddply(Data.wine,~Wine, summarise, mean = mean (Exercise), sd = sd(Exercise))
  
# Interesting. It looks like moderate drinkers also exercise more hours per week than light drinkers or heavy drinkers.
  
# 5) Now, let's control for hours spent on exercise per week (`Exercise`) in the linear regression. Run a multiple linear regression of `Age` on `Wine` and `Exercise`, and then look at the summary statistics. Please provide the R code below.
  
  	Solution5<-
    summary(Solution5)
  
```

`@solution`
```{r}
  ggplot(Data.wine, aes(x=Wine, y=Age, fill=Wine))+geom_boxplot()
  Solution2<-lm(Age ~ Wine, Data.wine)
  	summary(Solution2)
  ddply(Data.wine,~Wine, summarise, mean = mean (Exercise), sd = sd(Exercise))
  Solution5<-lm(Age ~ Wine + Exercise, Data.wine)
  	summary(Solution5)
```

`@sct`
```{r}
ex() %>% check_error()
success_msg("Good work! The base group (light drinkers) is represented by the intercept. We saw that light drinkers have an average life span of about 79 years. In addition, as we saw in the table we generated, moderate consumers spend the most time on exercise. And when we ran our model, the regression coefficient of the effect of red wine and exercise on moderate drinkers is 3.2010, indicating the expected life of moderate drinkers is 3.2010 years longer than that of light drinkers. The p-value of this coefficient is just above .05, suggesting the difference in expected life between those two groups is almost significant at 5% significance level, but not quite.  This implies that wine consumption cannot explain the age differences between moderate drinkers and light drinkers. However, the coefficient on `Exercise` is significantly positive at 1% significance level. Thus, longevity is driven mostly by physical activity instead of wine consumption in this case.")
```

---

## Does This Model Hold Up Under Pressure?

```yaml
type: undefined
key: 1db7c46923
```



---

## Do We Have Problems with a Confounder?

```yaml
type: PureMultipleChoiceExercise
key: 4dfa681543
lang: r
xp: 50
skills: 1
```

The results of the previous exercise were not as clear as we were hoping: instead of seeing red wine with a positive treatment effect, rose wine with a smaller positive treatment effect, and white wine with no effect, we only saw a single positive effect for red wine. But this was with a more complex dataset than we had for our very first question about the impact of resveratrol on life expectancy. Perhaps we have a problem with a confounding variable that is affecting our model. Which of the following variables do you think might be confounding the impact of resveratrol on life expectancy?

`@hint`


`@possible_answers`
- [count (the average number of drinks per week)]
- female (what gender the participants are)
- activity (average minutes of exercise per week)
- Age (the lifespan of the participants)

`@feedback`
-  Correct! Imagine that one of our subjects, Suzy, has 1 drink/week with .30 mg total resveratrol in it, but another subject, Johnny, drinks 30+ glasses of alcohol to get the same amount of resveratrol. We should probably think that Johnny's extra 29 alcoholic drinks per week are affecting his overall health in a way that may confound our treatment effect. So let's try working on that issue to see if it changes our analysis.
-  Gender can often be a factor to look at, but if you look at our sample you'll see we have roughly a 50/50 split between men and women, so that is probably not the first place to look for issues. Try again.
-  Activity may be important, but there is another variable that can impact the amount of resveratrol that our participants may be ingesting. Try again.
-  This is our outcome variable, and it's unlikely that people's lifespan has a complicated reverse-causal effect on resveratrol's effect on lifespan, so try again.

---

## Finishing Up with A Final Model

```yaml
type: undefined
key: 25c1a1738e
```
