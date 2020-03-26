---
title: Experiments
description: 'If you want to go through these topics in more detail, take our free Causal Inference with R - Experiments course here on DataCamp.'
---

## Randomized Experiments.

```yaml
type: VideoExercise
key:
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/198212082
```


---

## Rainfall in Sonoma County and Sales on eBay

```yaml
type: PureMultipleChoiceExercise
key:
lang: r
xp: 50
skills: 1
```

It turns out that rainfall in Sonoma County, California is highly correlated with eBay's total gross merchandise volume: 
![](https://assets.datacamp.com/production/repositories/1145/datasets/b97fef1a9b4ea4e8357ac2b39d04bf4c4e77cb34/ebayandsonomarainfall.png)

Which of the following answers could support a **causal explanation** for this relationship?

`@hint`


`@possible_answers`
- Across the world, people prefer to buy more eBay products on rainy days.
- Climate change has caused Sonoma County to have increased rainfall and has encouraged the global population to do more shopping from home.
- eBay sales and rainfall in Sonoma County have both been increasing at similar rates in recent years
- [Rainfall motivates residents of Sonoma County to buy and sell goods on eBay at extraordinarily high rates]

`@feedback`
- This answer is close to correct, but not quite. Remember, eBay sells its goods to people across the world---why would the correlation be so strong with rainfall just in Sonoma County? Try again.
- This is a possible explanation for the correlation between eBay sales and rainfall in Sonoma County, but not one that involves the rainfall causing the sales. Instead it would suggest that this correlation is spurious. Try again.
- This is what it means for there to be a correlation between rainfall in Sonoma County and eBay sales, but it is not a causal explanation for this correlation. Try again.
- Good Job. As ridiculous as this sounds, it is what a causal relationship between rainfall in Sonoma County and eBay sales might suggest. Of course, residents of Sonoma County would have to be providing a huge proportion of all eBay transactions for this to be correct.

---

## iPhone Sales and Sales on eBay

```yaml
type: PureMultipleChoiceExercise
key:
lang: r
xp: 50
skills: 1
```

Annual Apple iPhone sales are highly correlated with annual eBay sales. If this relationship is **spurious** (misleading and false), what might be causing this high correlation?

`@hint`


`@possible_answers`
- Most transactions on eBay are for Apple iPhones.
- [Time causes technology sales and technology usage to increase]
- Most people only shop on eBay using the iPhone's eBay app.
- Buying an iPhone makes people more comfortable with using technology for market transactions.

`@feedback`
- This would suggest a causal relationship rather than a spurious correlation. Try again.
- Correct! This would cause both iPhone and eBay sales to increase, but has nothing to say about a link between the two.
- This would suggest a causal relationship rather than a spurious correlation. Try again.
- This would suggest a causal relationship rather than a spurious correlation. Try again.

---

## p Values, Confidence Intervals, & Hypothesis Tests

```yaml
type: VideoExercise
key:
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/205124286
```


---

## Confidence Intervals.

```yaml
type: PureMultipleChoiceExercise
key:
lang: r
xp: 50
skills: 1
```

Why might it be risky to implement a policy that has an that has average treatment effect with a confidence interval that overlaps with zero?

`@hint`


`@possible_answers`
- Because the confidence interval equation defaults to 0 with large amounts of data.
- [Because having zero in one's confidence interval implies that a treatment effect could have a positive or negative effect on the outcome of interest.]
- Because having zero in one's confidence interval implies that a treatment effect has no effect.
- It's incorrect to think this would be risky; as long as relationship between the policy and its treatment effect are within the desired range, a confidence interval that includes zero is not a problem.

`@feedback`
- This is not true. With tremendous sample size (n > 1,000,000), confidence intervals rarely cross 0, even for relatively insignificant treatment effects. Try again.
- Correct! It would be very risky to implement a policy that could potentially have the opposite effect than you intended.
- This is often how such confidence intervals are interpreted, but this is a mistake. A confidence interval that contains zero does is not evidence that there is no treatment effect, but that it is uncertain whether there is a treatment effect. Try again.
- A confidence interval that contains zero is inherently problematic.  Try again.

---

## Reading Average Treatment Effect & Confidence Intervals in a Table: Depression in the Oregon Health Experiment.

```yaml
type: VideoExercise
key:
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/198212094
```


---

## Let's Code: Practice with OHIE Data.

```yaml
type: VideoExercise
key:
xp: 50
video_link: //player.vimeo.com/video/279737708
```


---

## Oregon Health Experiment Data: Data Structures.

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 1
```

Let's say you're wondering how much mens' and womens' health differed in the experiment, and what the data says about Medicaid's effects on those differences, so you decide to look at some of the basic health numbers in the data. A simulated version of the Oregon Health Insurance Experiment data, `OHIE`, is available in the workspace. With this dataframe, we will make some quick calculations to learn about any differences. Our first step will be to separate out the treatment and control groups into new dataframes.

`@instructions`
- 1) Use the `str` function to examine the structure of the `OHIE` dataframe.
- 2) Create a dataframe called `TreatmentGroup` that only contains respondents that were selected into the `OHIE` treatment group (`OHIE$treatment==1). 
- 3) Create a dataframe called `ControlGroup` that only contains respondents that were not selected into the `OHIE` treatment group (`OHIE$treatment==0).

`@hint`
- The treatment group is identified when `treatment` equals 1.
- You can use the `subset` function on the `OHIE` dataframe based on the treatment value.

`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)
set.seed(1)
load(url("https://assets.datacamp.com/production/repositories/1145/datasets/9aab9e80125d94148dd065f169df4d4263b9f619/OHIEexperimental.Rda"))
OHIE <- OHIE[!is.na(OHIE$treatment),c("id","treatment","gender_inp","bp_sar_inp","bp_dar_inp")]
```

`@sample_code`
```{r}
# 1) Let's get a sense of the OHIE dataframe by looking at its structure with the str() command:

    str()   

# Note: Since we are going to run several t-tests, we can simplify the syntax in  later steps by separating the OHIE dataset into two dataframes that represent its treatment and control groups. There are several ways to do this in R. We recommend using R's bracket accessor's or dplyr's select function. As an example, below shows how to create a data.frame called "df.gender.0" that only contains respondents with gender equal to 0 with R's bracket syntax.

    df.gender.0<-OHIE[OHIE$gender_inp==0,]
 
# 2) Create a dataframe called `TreatmentGroup` that only contains respondents that were selected into the `OHIE` treatment group (`OHIE$treatment==1).
    
    TreatmentGroup<-

# 3) Create a dataframe called `ControlGroup` that only contains respondents that were not selected into the `OHIE` treatment group (`OHIE$treatment==0). 
      
    ControlGroup<-
```

`@solution`
```{r}
str(OHIE)
TreatmentGroup <- OHIE[OHIE$treatment==1, ]
ControlGroup <- OHIE[OHIE$treatment==0, ]
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("TreatmentGroup") %>% check_equal()
ex() %>% check_object("ControlGroup") %>% check_equal()
success_msg("Good work!")
```

---

## Oregon Health Experiment Data: Balance Checks.

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 1
```

Now that we've created separate dataframes for the treatment and control groups, let's do some balance checks between the groups to see if they are sufficiently balanced to allow for our comparisons. Run a t-test between the two groups, examine the results, and decide whether the t-test is statistically significant by analyzing its confidence interval. In real analysis, you'll check for statistically significant balance on more than just one variable, but we'll just stick with gender for this set of questions.

`@instructions`
- 1) Run a t-test to see if there is a statistically significant difference in gender between the treatment and control groups (i.e. whether gender is balanced between the treatment and control group). 
- 2) After looking at the confidence interval of the t-test, can we say the t-test results are statistically significant? Answer "yes" or "no".

`@hint`
- For each of the following questions, use the `t.test` function to test whether the treatment and control group are different from each other.
- Your answer for the first question should look something like t.test(TreatmentGroup$variable,ControlGroup$variable). 
- If the 95% confidence interval includes 0, we cannot be confident that there is a difference between the treatment and control group, so that t-test result is not statistically significant.

`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)

set.seed(1)
load(url("https://assets.datacamp.com/production/repositories/1145/datasets/9aab9e80125d94148dd065f169df4d4263b9f619/OHIEexperimental.Rda"))
OHIE <- OHIE[!is.na(OHIE$treatment),c("id","treatment","gender_inp","bp_sar_inp","bp_dar_inp")]
TreatmentGroup <- OHIE[OHIE$treatment==1, ]
ControlGroup <- OHIE[OHIE$treatment==0, ]
```

`@sample_code`
```{r}
# 1) We need to determine whether gender is balanced between the treatment and control groups. This requires a two sample t-test. In R, the format of the t.test function is t.test(Variable1, Variable2). Try this with the treatment and control groups, and our gender variable gender_inp. To help, we fill in the first half of the t.test function with gender in the treatment group. Replace `y` with gender in the control group.

    t.test(TreatmentGroup$gender_inp,y)

# As a reminder, the number we are looking for is listed in the second line of results with the label `t =`. That is the difference in the means of our two variables (while accounting for any different variances in the two groups). 

# 2) To determine whether the t-test shows that gender is balanced, we need to determine whether its results are statistically significant. If the 95% confidence interval includes 0, the results are not statistically significant (i.e. our evidence does not suggest a great difference between the rate of gender in the treatment and control groups). Based on the confidence interval in Solution 1, do the results appear statistically significant? Answer with "Yes" or "No." 

    Solution2<-""
```

`@solution`
```{r}
t.test(TreatmentGroup$gender_inp,ControlGroup$gender_inp)
#This is one way to test (without eyes) whether the confidence interval overlaps with 0.
Solution1<-t.test(TreatmentGroup$gender_inp,ControlGroup$gender_inp)
Solution2<-ifelse(sign(Solution1$conf.int[1])==sign(Solution1$conf.int[2]),"Yes",
"No")
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution2") %>% check_equal()
success_msg("Good work! Since there is no significant difference in rates of gender between the treatment and control groups, we assume the groups are balanced on gender.")
```

---

## Oregon Health Experiment Data: Finding an Average Treatment Effect

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 1
```

Now that we've checked for balance between our treatment and control, let's check to see the effect of Medicaid on some of our medical outcomes of interest, like the patients' blood pressure. A person's blood pressure is measured by two numbers, e.g. 114/71, where the first number is the "systolic" blood pressure and the second is the "diastolic" blood pressure. These are counted in the `OHIE` dataframe through two variables: systolic pressure in `bp_sar_inp` and diastolic pressure in `bp_var_inp`. 

Now let's check the treatment effect on systolic blood pressure (`bp_sar_inp`) by comparing systolic blood pressure in the treatment and control groups. To check for statistical significance, let's look at p values of the t-test. A p-value below .05 suggests that a result is statistically significant.

`@instructions`
- 1) Manually calculate the average treatment effect on systolic blood pressure by subtracting the `mean` value for systolic blood pressure in the treatment group minus the `mean` value for systolic blood pressure in the control group.
- 2) Use a t.test to determine whether the treatment and control groups have significantly different average values for systolic blood pressure (variable `bp_sar_inp`).
- 3) After looking at the p-value of the t-test, can we say the t-test results are statistically significant? Answer "yes" or "no".

`@hint`
- 2) Your input for the t-tests should look something like t.test(TreatmentGroup$variable,ControlGroup$variable).

`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)

set.seed(1)
load(url("https://assets.datacamp.com/production/repositories/1145/datasets/9aab9e80125d94148dd065f169df4d4263b9f619/OHIEexperimental.Rda"))
OHIE <- OHIE[!is.na(OHIE$treatment),c("id","treatment","gender_inp","bp_sar_inp","bp_dar_inp")]
TreatmentGroup <- OHIE[OHIE$treatment==1, ]
ControlGroup <- OHIE[OHIE$treatment==0, ]
```

`@sample_code`
```{r}
#  1) Calculate the average treatment effect of Medicaid on the systolic blood pressure of units in the experiment. This is equal to the `mean` value for systolic blood pressure in the treatment group minus the `mean` value for systolic blood pressure in the control group. We help by filling out the front end of this equation, so fill out the second half:

    mean(TreatmentGroup$bp_sar_inp)-

#  2) Use a t-test to determine whether the treatment had a statistically significant effect on systolic blood pressure.
  
    t.test()

# 3) A p.value of less than .05 is generally considered statistically significant. Based on your results in Solution 2, did the experiment yield a statistically signficant average treatment effect on systolic blood pressure? Answer with "Yes" or "No."

    Solution3<-""
```

`@solution`
```{r}
mean(TreatmentGroup$bp_sar_inp)-mean(ControlGroup$bp_sar_inp)
t.test(TreatmentGroup$bp_sar_inp,ControlGroup$bp_sar_inp)

#We can computationally determine whether the p-value is lower than .05 with the syntax below
Solution2<-t.test(TreatmentGroup$bp_sar_inp,ControlGroup$bp_sar_inp)
Solution3<-ifelse(Solution2$p.value<.05,"Yes","No")
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution3") %>% check_equal()
success_msg("Good work. The high p-value means that the estimate is not statistically significan, which is not what we were hoping for. Let's see if that's also true of the treatment effect on diastolic blood pressure.")
```

---

## Oregon Health Experiment Data: Finding Another ATE.

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 1
```

Now let's check the treatment effect on diastolic blood pressure values `bp_var_inp` across our treatment and control groups. Once again, we'll use a t-test to measure statistical significance, and assume a p-value of less than .05 is statistically significant.

`@instructions`
- 1) Run a t.test to determine if the treatment and control groups have significantly different average values for diastolic blood pressure (`bp_dar_inp`).
- 2) After looking at the p-value of the t-test, can we say the t-test results are statistically significant? Answer "Yes" or "No".

`@hint`
- 1) Your answers for the t-tests should look something like t.test(TreatmentGroup$variable,ControlGroup$variable).
- A p.value of less than .05 is generally considered statistically significant.

`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)

set.seed(1)
load(url("https://assets.datacamp.com/production/repositories/1145/datasets/9aab9e80125d94148dd065f169df4d4263b9f619/OHIEexperimental.Rda"))
OHIE <- OHIE[!is.na(OHIE$treatment),c("id","treatment","gender_inp","bp_sar_inp","bp_dar_inp")]
TreatmentGroup <- OHIE[OHIE$treatment==1, ]
ControlGroup <- OHIE[OHIE$treatment==0, ]
```

`@sample_code`
```{r}
# 1) Run a t-test that measures the average treatment effect on diastolic blood pressure.

    t.test()

# 2) Based on your t-test, did the treatment have a statistically significant effect on diastolic blood pressure? Answer with "Yes" or "No."

    Solution2<-""
```

`@solution`
```{r}
t.test(TreatmentGroup$bp_dar_inp,ControlGroup$bp_dar_inp)

#We can computationally determine whether the p-value is lower than .05 with the syntax below
Solution1<-t.test(TreatmentGroup$bp_dar_inp,ControlGroup$bp_dar_inp)
Solution2<-ifelse(Solution1$p.value<.05,"Yes","No")
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution2") %>% check_equal()
success_msg("Good work. Our estimate for the treatment effect on diastolic blood pressure had a p-value under .05, so we will say that it's statistically significant. Because some of our estimates were not statistically significant, and some are, we probably will need to work a little harder before we can conclude that our experiment suggests that the Medicaid program should be expanded.")
```

---

## Noncompliance in Experiments.

```yaml
type: VideoExercise
key:
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/198212091
```


---

## Offering a Higher Credit Card Limit: Quantifying Noncompliance Concerns.

```yaml
type: PureMultipleChoiceExercise
key:
lang: r
xp: 50
skills: 1
```

CreditCo, a large credit card company, decides to run an experiment. It sends an offer in the mail to a random group of 50% of its customers: those in the treatment group are invited to navigate to a webpage and opt in for a 10% higher credit limit. CreditCo wants to see how credit balances and late payments are impacted six months later as a result of the experiment. 

Suppose that, of the group that received the mail offer, 40% of people opted in. Do you think that noncompliance will be a problem for CreditCo's analysis? Why or why not?

`@hint`


`@possible_answers`
- No, because people in the treatment group likely used a coin flip to make their opt-in decision.
- Yes, because the opt-in rate is low.
- No, because an opt-in rate of 40% is actually quite high.
- [Yes, because the set of people opting in are probably people with worse spending habits.]

`@feedback`
- While this is a possibility, it is unlikely to actually be the case. Try again.
- This is partially correct. A low compliance rate is one symptom of a noncompliance problem.
- While high compliance rates indicate a lower noncompliance problem, the rate of 40% in this situation is likely to be problematic.
- Correct! In this situation, researchers at CreditCo should be worried about the spending habits of those who opted in to the offer.

---

## Ways to Deal with Noncompliance.

```yaml
type: PureMultipleChoiceExercise
key:
lang: r
xp: 50
skills: 1
```

Which one of the following approaches is *NOT* a way to deal with treatment noncompliance?

`@hint`


`@possible_answers`
- Bounds Analysis
- Instrumental Variables
- [Randomized Control Trial]
- Intention to Treat Analysis
- Assume Random Compliance

`@feedback`
- Bounds Analysis is definitely a common method used to deal with noncompliance, and we're looking for a way that is **NOT** appropriate, so try again.
- Instrumental variables is definitely a common method used to deal with noncompliance, and we're looking for a way that is **NOT** appropriate, so try again.
- Correct! Randomized Control Trials are not a valid way to correct for noncompliance, because they themselves are susceptible to treatment noncompliance.
- Intention to Treat Analysis is definitely a common way to deal with noncompliance, and we're looking for a way that is **NOT** appropriate, so try again
- Assuming Random Compliance is not always applicable, but it is nonetheless commonly used to deal with noncompliance, so try again.

---

## The Two Kinds of Natural Experiments.

```yaml
type: VideoExercise
key:
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/199856738
```


---

## As-if Natural Experiments.

```yaml
type: PureMultipleChoiceExercise
key:
lang: r
xp: 50
skills: 1
```

Which of the following is an accurate description of an "as-if" natural experiment?

`@hint`


`@possible_answers`
- A political study where treatment assignment was determined by factors outside the control of the investigators. Assignment to the treatment was completely random.
- [A business experiment where assignment to treatment was determined by factors outside the control of the investigators. Assignment to the treatment was not literally random, but it was unrelated to variables that affect the outcome.]
- A psychology study conducted in a naturalistic setting by investigators. Assignment to the treatment was completely random.
- A zoological experiment conducted in a naturalistic setting by investigators. Treatment assignment was not literally random, but it was unrelated to variables that affect the outcome.

`@feedback`
- This describes a true natural experiment. Try again.
- Well done. Although there might be a pattern to who got treated in an as-if experiment, the pattern should cause no bias in one's outcome of interest.
- This would not even be a natural experiment! Try again.
- This would not even be a natural experiment! Try again.

---

## Let's Code - Putting it All Together

```yaml
type: VideoExercise
key:
xp: 50
video_link: //player.vimeo.com/video/279737460
```


---

## Putting it All Together with KittyCatch: Part 1 - Explore the Data.

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 2
```

Often, our experiments don't go as planned. This long and complex exercise will test your knowledge in resolving a question with realistic problems. 

KittyCatch is a location-based augmented reality game developed by Meowtec. In this game, players use their cell phones' GPS abilities to locate and capture virtual kittens. Although KittyCatch is free to play, Meowtec generates revenue from KittyCatch through pop-up ads, which appear about once for every half-mile the player walks while using the application, up to 5 times a day. Since Meowtec's revenue is highly dependent on how far people walk while playing KittyCatch, their primary goal for future updates to KittyCatch is to incentivize play.

One strategy to increase users' play time is to increase the distance between KittyCatch's "Points of Kinterest"; that is, increase the distance that users must travel to capture new kittens. Many players stop their sessions of KittyCatch before they catch a single kitten, and may be turned off by the need to travel farther to catch a kitten. However, Meowtec believes that the loss of play time for these players would be offset by the many other players who consistently travel as far as needed to catch a kitten. 

To test this hypothesis, Meowtec constructs an experiment: For a small random sample of players in Springfield, Massachusetts, Meowtec increases the distance that players must walk to reach a Point of Kinterest (specifically, from .25 miles to .5 miles). They compare these players to an equal random sample of players in Springfield, Massachusetts that have the default distance between Points of Kinterest (.25 miles). However, as they explore their data, they find a few problems with their experiment. 

With the dataset, `KittyCatch`, and the annotations in the R workspace, help Meowtec determine a valid and reliable average treatment effect from their experiment. Specifically, balance the data and correct for any coding errors in the original dataset to estimate a reliable average treatment effect. We will spend many more steps on this problem than in previous exercises, but also more representative of the types of steps that data scientists use when working with experimental data.  But first, we need to get familiar with the data.

`@instructions`
- 1) Take a look at the variable names and dataframe structure.
- 2) See what a "naive" treatment effect looks like.
- 3) Run a t-test to see a different early calculation of the treatment effect.
- 4) Examine the values of our outcome of interest, the distance the users walk.

`@hint`


`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)

set.seed(1)
#Create rnorm function that allows for random distribution with min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
    qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){ 
    base*round(x/base) 
  } 

n=688
#Create dataframe
  KittyCatch<-as.data.frame(matrix(nrow=n,ncol=4))
  names(KittyCatch)<-c("DistanceWalked","Age","TotalHoursPlayed","Treatment")
#Assign Treatment randomly
  KittyCatch$Treatment<-rbinom(n,1,.35)
#Assign Values to variables
 #DistanceWalked
  #Create Variable
    KittyCatch$DistanceWalked<-round(rtnorm(n=n, mean=.62, sd=.3, min = 0, max = 1.3),2)
  #Assign 4 Outliers to DistanceWalked among control
    KittyCatch$DistanceWalked[KittyCatch$Treatment==0][sample(sum(KittyCatch$Treatment==0),4)]<-round(rtnorm(n=4, mean=7.00, sd=.6, min = 5, max = 9),2)
  #Age
    #Create Variable
      KittyCatch$Age<-round(rtnorm(n=n, mean=14, sd=4, min = 10, max = 40))
    #Assign age to be correlated with DistanceWalked
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$DistanceWalked>median(KittyCatch$DistanceWalked),2,-2)))
    #Assign age to be correlated with treatment above age 18
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$Age>17 & KittyCatch$Treatment==1,4,0)))
    #Top code in control group
      KittyCatch$Age[KittyCatch$Treatment==0]<-ifelse(KittyCatch$Age[KittyCatch$Treatment==0]>18,18,KittyCatch$Age[KittyCatch$Treatment==0])
  #TotalHoursPlayed
    #Create Variable
      KittyCatch$TotalHoursPlayed<-round(rtnorm(n=n, mean=30, sd=10, min = 1, max = 50))
    #Make it correlated with distance walked
      KittyCatch$TotalHoursPlayed<-round(.8*KittyCatch$TotalHoursPlayed + .2*KittyCatch$TotalHoursPlayed*KittyCatch$DistanceWalked)
    #Randomly assign missing values, make the proportion larger in the treatment; and make the likelihood for NA correlate with larger values
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]<-ifelse(rbinom(sum(KittyCatch$Treatment==0),1,(.05+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]/mean(KittyCatch$TotalHoursPlayed))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0])
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]<-ifelse(rbinom(sum(KittyCatch$Treatment==1),1,(.25+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]/mean(KittyCatch$TotalHoursPlayed,na.rm = T))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1])
  #Make distance walked negatively correlated with treatment prior to balance, and positvely correlated with treatment after balance
      removed<-ifelse(KittyCatch$Age>17 | is.na(KittyCatch$TotalHoursPlayed),1,0)
      KittyCatch$DistanceWalked<-round(ifelse(removed==1 & KittyCatch$Treatment==0,1.5*KittyCatch$DistanceWalked,ifelse(removed==0 & KittyCatch$Treatment==1,1.3*KittyCatch$DistanceWalked,KittyCatch$DistanceWalked)),2)
```

`@sample_code`
```{r}
# 1) Let's dig into the data. We first run the structure function, str(), to get a sense of the dataset. DistanceWalked is our outcome of interest, and Treatment is the key independent variable that we care about. TotalHoursPlayed refers to how many hours the user has put into KittyCatch in total.

    str()

# 2) Although it is bad practice, let's begin this exercise by first taking a naive estimate of the average treatment effect on DistanceWalked before exploring the dataset. Subtract the mean of the control group from the mean of the treatment group and assign this to Solution2.

    Solution2<- 

# 3) Now let's do that again, but with a t-test.  
      
    t.test()

# You will see that, based on the t-test results, it seems that there is substantial negative treatment effect; respondents walked less in the treatment than in the control. But is this finding reliable?

# 4) Now let's examine our outcome of interest, DistanceWalked, with the summary function. 
    
    summary()
    
```

`@solution`
```{r}
#1
str(KittyCatch)
#2
Solution2<- mean(KittyCatch$DistanceWalked[KittyCatch$Treatment==1]) -  mean(KittyCatch$DistanceWalked[KittyCatch$Treatment==0])
#3
t.test(KittyCatch$DistanceWalked[KittyCatch$Treatment==1],KittyCatch$DistanceWalked[KittyCatch$Treatment==0])
#4
summary(KittyCatch$DistanceWalked)
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution2") %>% check_equal()

success_msg("Great Job! Notice that the maximum value is much larger than the mean, median, and 3rd quartile of the dataset. This outlier might bias our t-test results by violating its assumption that the data is normally distributed.")
```

---

## Putting it All Together with KittyCatch: Part 2 - Use Graphs to Understand the Outcome.

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 2
```

As we saw in the previous exercise, the maximum value for our outcome of interest - the distance users walked - is much larger than the mean, median, and 3rd quartile of the dataset. This outlier might bias our t-test results by violating its assumption that the data is normally distributed, so we need to deal with outliers for this variable. Let's create some charts to see the current distribution of `DistanceWalked`, and then let's try a method to deal with the outliers and make another chart to see if our method makes our data look more like a normal distribution.

`@instructions`
- 1) Chart the values of our outcome of interest.
- 2) Examine the highest distances that our sample users walked.
- 3) Use top coding to help us handle outlier values of DistanceWalked.
- 4) Create a new chart to see if Step 3 helps make our values look more normal.

`@hint`


`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)

set.seed(1)
#Create rnorm function that allows for random distribution with min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
    qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){ 
    base*round(x/base) 
  } 

n=688
#Create dataframe
  KittyCatch<-as.data.frame(matrix(nrow=n,ncol=4))
  names(KittyCatch)<-c("DistanceWalked","Age","TotalHoursPlayed","Treatment")
#Assign Treatment randomly
  KittyCatch$Treatment<-rbinom(n,1,.35)
#Assign Values to variables
 #DistanceWalked
  #Create Variable
    KittyCatch$DistanceWalked<-round(rtnorm(n=n, mean=.62, sd=.3, min = 0, max = 1.3),2)
  #Assign 4 Outliers to DistanceWalked among control
    KittyCatch$DistanceWalked[KittyCatch$Treatment==0][sample(sum(KittyCatch$Treatment==0),4)]<-round(rtnorm(n=4, mean=7.00, sd=.6, min = 5, max = 9),2)
  #Age
    #Create Variable
      KittyCatch$Age<-round(rtnorm(n=n, mean=14, sd=4, min = 10, max = 40))
    #Assign age to be correlated with DistanceWalked
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$DistanceWalked>median(KittyCatch$DistanceWalked),2,-2)))
    #Assign age to be correlated with treatment above age 18
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$Age>17 & KittyCatch$Treatment==1,4,0)))
    #Top code in control group
      KittyCatch$Age[KittyCatch$Treatment==0]<-ifelse(KittyCatch$Age[KittyCatch$Treatment==0]>18,18,KittyCatch$Age[KittyCatch$Treatment==0])
  #TotalHoursPlayed
    #Create Variable
      KittyCatch$TotalHoursPlayed<-round(rtnorm(n=n, mean=30, sd=10, min = 1, max = 50))
    #Make it correlated with distance walked
      KittyCatch$TotalHoursPlayed<-round(.8*KittyCatch$TotalHoursPlayed + .2*KittyCatch$TotalHoursPlayed*KittyCatch$DistanceWalked)
    #Randomly assign missing values, make the proportion larger in the treatment; and make the likelihood for NA correlate with larger values
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]<-ifelse(rbinom(sum(KittyCatch$Treatment==0),1,(.05+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]/mean(KittyCatch$TotalHoursPlayed))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0])
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]<-ifelse(rbinom(sum(KittyCatch$Treatment==1),1,(.25+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]/mean(KittyCatch$TotalHoursPlayed,na.rm = T))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1])
  #Make distance walked negatively correlated with treatment prior to balance, and positvely correlated with treatment after balance
      removed<-ifelse(KittyCatch$Age>17 | is.na(KittyCatch$TotalHoursPlayed),1,0)
      KittyCatch$DistanceWalked<-round(ifelse(removed==1 & KittyCatch$Treatment==0,1.5*KittyCatch$DistanceWalked,ifelse(removed==0 & KittyCatch$Treatment==1,1.3*KittyCatch$DistanceWalked,KittyCatch$DistanceWalked)),2)
```

`@sample_code`
```{r}
# 1) Run a density plot on DistanceWalked to observe the long right tail in the distribution of our outcome of interest.

     plot(density())

# 2) Since the dataset is relatively small, let's use the `head` and `order` commands to examine the highest DistanceWalked observations in the dataset. The following syntax will order the top results by the outcome of interest. Use it as a guide; replace the dataframe and variable names to those we care about:

    head(Dataframe[order(Dataframe$Variable,decreasing=T),])

# Note: Notice that the four largest values for DistanceWalked are more than three times as large as the 5th largest value for DistanceWalked. These are clearly outliers. However, we should also note that all of these values are in the control group, so removing them from our dataset, as we had done with previous outliers, might also bias our estimates by lowering the mean values for the treatment group. Instead, let's say that our maximum distance we will allow is 2. This is known as top-coding. We will top-code these values so that they are still the largest values in the dataset, but so that they are not outliers and do not violate our assumptions of a normal distribution. 

# 3) Top coding can be arbitrary (and there are better methods for handling outliers), but for this assignment, use the following syntax as a model to create an ifelse statement that says that any value of DistanceWalked over 2 will be changed to equal 2: dataframe$variable<-ifelse(dataframe$variable>x,y,dataframe$variable). 
    
#Note: x is the current value of the variable, and y is the final value we want.
    
    

# 4) If you completed question 3 correctly, the distribution of DistanceWalked should now look much more normal. Create a new density plot of DistanceWalked to see if that is true.
    
    plot(density())
    
```

`@solution`
```{r}
#1  
plot(density(KittyCatch$DistanceWalked))
#2
head(KittyCatch[order(KittyCatch$DistanceWalked,decreasing=T),])
#3
KittyCatch$DistanceWalked<-ifelse(KittyCatch$DistanceWalked>2,2,KittyCatch$DistanceWalked)
#4
plot(density(KittyCatch$DistanceWalked))
```

`@sct`
```{r}
ex() %>% check_error()

success_msg("Nice work so far!")
```

---

## Putting it All Together with KittyCatch: Part 3 - Balance the Data.

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 2
```

So we've looked at our dataframe structure, run some "naive" treatment effect calculations, and identified and corrected for some outliers on our outcome of interest, the distance our users walked while playing KittyCatch during the experiment. Now we are ready to check our treatment and control groups for balance across several variables, and deal with tricky problems that might come up.

`@instructions`
- 1) Create a boxplot to help us look for balance between treatment and control groups.
- 2) Is the distance people walk correlated with their age?
- 3) Are the ages of users balanced in the treatment and control groups?
- 4) Subset the data to help us compare groups with similar ages.
- 5) Check if these new subsets are balanced on user age.

`@hint`


`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)

set.seed(1)
#Create rnorm function that allows for random distribution with min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
    qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){ 
    base*round(x/base) 
  } 

n=688
#Create dataframe
  KittyCatch<-as.data.frame(matrix(nrow=n,ncol=4))
  names(KittyCatch)<-c("DistanceWalked","Age","TotalHoursPlayed","Treatment")
#Assign Treatment randomly
  KittyCatch$Treatment<-rbinom(n,1,.35)
#Assign Values to variables
 #DistanceWalked
  #Create Variable
    KittyCatch$DistanceWalked<-round(rtnorm(n=n, mean=.62, sd=.3, min = 0, max = 1.3),2)
  #Assign 4 Outliers to DistanceWalked among control
    KittyCatch$DistanceWalked[KittyCatch$Treatment==0][sample(sum(KittyCatch$Treatment==0),4)]<-round(rtnorm(n=4, mean=7.00, sd=.6, min = 5, max = 9),2)
  #Age
    #Create Variable
      KittyCatch$Age<-round(rtnorm(n=n, mean=14, sd=4, min = 10, max = 40))
    #Assign age to be correlated with DistanceWalked
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$DistanceWalked>median(KittyCatch$DistanceWalked),2,-2)))
    #Assign age to be correlated with treatment above age 18
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$Age>17 & KittyCatch$Treatment==1,4,0)))
    #Top code in control group
      KittyCatch$Age[KittyCatch$Treatment==0]<-ifelse(KittyCatch$Age[KittyCatch$Treatment==0]>18,18,KittyCatch$Age[KittyCatch$Treatment==0])
  #TotalHoursPlayed
    #Create Variable
      KittyCatch$TotalHoursPlayed<-round(rtnorm(n=n, mean=30, sd=10, min = 1, max = 50))
    #Make it correlated with distance walked
      KittyCatch$TotalHoursPlayed<-round(.8*KittyCatch$TotalHoursPlayed + .2*KittyCatch$TotalHoursPlayed*KittyCatch$DistanceWalked)
    #Randomly assign missing values, make the proportion larger in the treatment; and make the likelihood for NA correlate with larger values
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]<-ifelse(rbinom(sum(KittyCatch$Treatment==0),1,(.05+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]/mean(KittyCatch$TotalHoursPlayed))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0])
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]<-ifelse(rbinom(sum(KittyCatch$Treatment==1),1,(.25+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]/mean(KittyCatch$TotalHoursPlayed,na.rm = T))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1])
  #Make distance walked negatively correlated with treatment prior to balance, and positvely correlated with treatment after balance
      removed<-ifelse(KittyCatch$Age>17 | is.na(KittyCatch$TotalHoursPlayed),1,0)
      KittyCatch$DistanceWalked<-round(ifelse(removed==1 & KittyCatch$Treatment==0,1.5*KittyCatch$DistanceWalked,ifelse(removed==0 & KittyCatch$Treatment==1,1.3*KittyCatch$DistanceWalked,KittyCatch$DistanceWalked)),2)
  KittyCatch$DistanceWalked<-ifelse(KittyCatch$DistanceWalked>2,2,KittyCatch$DistanceWalked)
```

`@sample_code`
```{r}
# 1) Next, we'll want to make sure that our control groups and treatment groups are balanced. Let's compare the age of the control group and treatment group with boxplots. Replace the variable names below for creating this boxplot: 

    boxplot(dataframe$variable[dataframe$Treatment==0], dataframe$variable[dataframe$Treatment==1], names=c("Control","Treatment")) 

# Note: Notice that the medians and interquartile ranges are very similar between the treatment and control groups, but that the largest values in the treatment group rest much higher than in the control group. It turns out that this did not happen by chance; by default, KittyCatch only requires respondents to enter their ages if they state that they are younger than 18; however, for the experiment, all respondents in the treatment group were required to enter their ages. 

# 2) It could be problematic if the ages among the treatment group are different than those in the control group, especially if Age is correlated with DistanceWalked. Run a cor() function between Age and DistanceWalked to see if they are indeed correlated. Replace the variable names in the following syntax:

    cor(dataframe$variable1, dataframe$variable2):

# 3) Are the treatment and control groups balanced on Age, or are they imbalanced? Let's run a t-test to see. As a reminder, the syntax for this is:
      
    t.test(dataframe$variable[dataframe$Treatment==0],dataframe$variable[dataframe$Treatment==1])

# 4) As you can see, they are imbalanced. There are two options to deal with this problem. One option is to ignore it, as we know that age was top-coded in the control group, and may be the entire cause of the imbalance between the treatment and control group. However, what if people who opted into the treatment group tended to be older on average? This could bias our results. The best way to deal with this problem is with a different modeling technique (e.g. regression models). However, since we want to continue using t-tests for this module, a good way to deal with this problem is to subset the data to only use observations we can be sure are similarly aged. Since we can only be sure of the age of respondents in the treatment group for those younger than 18, let's subset the dataset to only include respondents who are 17 or younger. Correct the syntax below to accomplish this: 
    
    KittyCatch<-dataframe[dataframe$variable<=17,].
  
# 5) If you completed question 4 correctly, Age among the treatment and control groups should now be balanced. Run the t-test from Question 3 again to see if the two groups are now balanced on Age.
    
    t.test()
```

`@solution`
```{r}
#1
boxplot(KittyCatch$Age[KittyCatch$Treatment==0],KittyCatch$Age[KittyCatch$Treatment==1],names=c("Control","Treatment"))
#2
cor(KittyCatch$Age,KittyCatch$DistanceWalked)
#3
t.test(KittyCatch$Age[KittyCatch$Treatment==0],KittyCatch$Age[KittyCatch$Treatment==1])
#4
KittyCatch<-KittyCatch[KittyCatch$Age<=17,]
#5
t.test(KittyCatch$Age[KittyCatch$Treatment==0],KittyCatch$Age[KittyCatch$Treatment==1])
```

`@sct`
```{r}
ex() %>% check_error()

success_msg("Great! We've made a lot of progress, so let's look further at the quality of our data.")
```

---

## Putting it All Together with KittyCatch: Part 4 - Missing Data Problems.

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 2
```

Let's continue our look at our data by checking for balance on our treatment variable and outcome variable, and looking to see how correlated they are. One common problem in data science is missing data: empty gaps in the values of some variables that will throw off our results. If we find any in our key variables, we will need to deal with them.

`@instructions`
- 1) Check for balance on TotalHoursPlayed
- 2) See the correlation between the number of hours played and distance walked.
- 3) Look at the average values of TotalHoursPlayed in the treatment and control groups.
- 4) Is DistanceWalked balanced across treatment and control groups?
- 5) Use a rough method to remove some problem data entries

`@hint`


`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)

set.seed(1)
#Create rnorm function that allows for random distribution with min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
    qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){ 
    base*round(x/base) 
  } 

n=688
#Create dataframe
  KittyCatch<-as.data.frame(matrix(nrow=n,ncol=4))
  names(KittyCatch)<-c("DistanceWalked","Age","TotalHoursPlayed","Treatment")
#Assign Treatment randomly
  KittyCatch$Treatment<-rbinom(n,1,.35)
#Assign Values to variables
 #DistanceWalked
  #Create Variable
    KittyCatch$DistanceWalked<-round(rtnorm(n=n, mean=.62, sd=.3, min = 0, max = 1.3),2)
  #Assign 4 Outliers to DistanceWalked among control
    KittyCatch$DistanceWalked[KittyCatch$Treatment==0][sample(sum(KittyCatch$Treatment==0),4)]<-round(rtnorm(n=4, mean=7.00, sd=.6, min = 5, max = 9),2)
  #Age
    #Create Variable
      KittyCatch$Age<-round(rtnorm(n=n, mean=14, sd=4, min = 10, max = 40))
    #Assign age to be correlated with DistanceWalked
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$DistanceWalked>median(KittyCatch$DistanceWalked),2,-2)))
    #Assign age to be correlated with treatment above age 18
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$Age>17 & KittyCatch$Treatment==1,4,0)))
    #Top code in control group
      KittyCatch$Age[KittyCatch$Treatment==0]<-ifelse(KittyCatch$Age[KittyCatch$Treatment==0]>18,18,KittyCatch$Age[KittyCatch$Treatment==0])
  #TotalHoursPlayed
    #Create Variable
      KittyCatch$TotalHoursPlayed<-round(rtnorm(n=n, mean=30, sd=10, min = 1, max = 50))
    #Make it correlated with distance walked
      KittyCatch$TotalHoursPlayed<-round(.8*KittyCatch$TotalHoursPlayed + .2*KittyCatch$TotalHoursPlayed*KittyCatch$DistanceWalked)
    #Randomly assign missing values, make the proportion larger in the treatment; and make the likelihood for NA correlate with larger values
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]<-ifelse(rbinom(sum(KittyCatch$Treatment==0),1,(.05+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]/mean(KittyCatch$TotalHoursPlayed))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0])
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]<-ifelse(rbinom(sum(KittyCatch$Treatment==1),1,(.25+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]/mean(KittyCatch$TotalHoursPlayed,na.rm = T))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1])
  #Make distance walked negatively correlated with treatment prior to balance, and positvely correlated with treatment after balance
      removed<-ifelse(KittyCatch$Age>17 | is.na(KittyCatch$TotalHoursPlayed),1,0)
      KittyCatch$DistanceWalked<-round(ifelse(removed==1 & KittyCatch$Treatment==0,1.5*KittyCatch$DistanceWalked,ifelse(removed==0 & KittyCatch$Treatment==1,1.3*KittyCatch$DistanceWalked,KittyCatch$DistanceWalked)),2)
  KittyCatch$DistanceWalked<-ifelse(KittyCatch$DistanceWalked>2,2,KittyCatch$DistanceWalked)
  KittyCatch<-KittyCatch[KittyCatch$Age<=17,]
```

`@sample_code`
```{r}
# 1) Now let's look for balance in the last variable we know about the treatment and control groups, TotalHoursPlayed. Run the summary function on the variable TotalHoursPlayed.  

    summary()

# 2) Notice from the summary function that 96 values are labeled "NA". These cases are missing information, in large part because KittyCatch allows users to opt out of recording how many hours they play. This could be very problematic, as it indicates that we only have distance walked information for respondents who selected to do so. Let's find the correlation between TotalHoursPlayed and DistanceWalked the entire sample population. Replace the variable names in the following syntax: 

    cor(dataframe$variable1, dataframe$variable2, use="complete").

# That doesn't look too good.
    
# 3) Even more worrisome, the NA values for TotalHoursPlayed appear at higher rates for respondents in the treatment group than in the control group. Check the average values of TotalHoursPlayed in both treatment and control groups, in separate lines, using the syntax: mean(is.na(dataframe$variable)) Also remember that you can select units within a dataframe by their Treatment value with the syntax variable[dataframe$Treatment==x]. 
    
    mean()
    mean()

# 4) This isn't the end for our analysis, though. Let's look for some good news about our data within TotalHoursPlayed. One simple thing we can do is see if that variable is balanced across the treatment and control groups for the units that we actually do have information for, so run a t-test between the treatment and control groups on the variable TotalHoursPlayed.
    
    t.test()

# Note: While total hours played appears balanced among the treatment and control groups for those whose information is available, the fact that its missingness is correlated with DistanceWalked and is also patterned among the treatment and control groups is cause for concern. Specifically, this could suggest that respondents in the treatment group play more KittyCatch than those in the control group, and are likely to walk further with KittyCatch due to this. 
  
# 5) A simple, albeit imperfect, solution to this problem is listwise deletion; that is, removing respondents from our sample who did not report their total hours played. Subset KittyCatch to respondents who reported their total hours played. The syntax for this will be:
    
    KittyCatch<-dataframe[!is.na(dataframe$variable),].
```

`@solution`
```{r}
#1
summary(KittyCatch$TotalHoursPlayed)
#2
cor(KittyCatch$TotalHoursPlayed,KittyCatch$DistanceWalked,use="complete")
#3
mean(is.na(KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]))
mean(is.na(KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]))
#4
t.test(KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1],KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0])
#5
KittyCatch<-KittyCatch[!is.na(KittyCatch$TotalHoursPlayed),]
```

`@sct`
```{r}
ex() %>% check_error()


success_msg("Whew! We've explored the data, dealt with the issues, and now we can finally calculate the treatment effect of our experiment!")
```

---

## Putting it All Together with KittyCatch: Part 5 - Calculate the ATE

```yaml
type: NormalExercise
key:
lang: r
xp: 100
skills: 2
```

We've examined our data, checked for balance, and dealt with outliers and missing data. Now it's time to calculate the average treatment effect of making KittyCatch users walk farther to their next Point of Kinterest, and see if that effect is statistically significant.

`@instructions`
- 1) Calculate the average treatment effect of the `Treatment` on `DistanceWalked`.
- 2) Run a t.test to estimate the statistical significance of that result.
- 3) Based on question 2), indicate whether the above t.test is statistically significant with `Yes` or `No`.

`@hint`


`@pre_exercise_code`
```{r}
library(data.table)
library(dplyr)

set.seed(1)
#Create rnorm function that allows for random distribution with min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
    qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){ 
    base*round(x/base) 
  } 

n=688
#Create dataframe
  KittyCatch<-as.data.frame(matrix(nrow=n,ncol=4))
  names(KittyCatch)<-c("DistanceWalked","Age","TotalHoursPlayed","Treatment")
#Assign Treatment randomly
  KittyCatch$Treatment<-rbinom(n,1,.35)
#Assign Values to variables
 #DistanceWalked
  #Create Variable
    KittyCatch$DistanceWalked<-round(rtnorm(n=n, mean=.62, sd=.3, min = 0, max = 1.3),2)
  #Assign 4 Outliers to DistanceWalked among control
    KittyCatch$DistanceWalked[KittyCatch$Treatment==0][sample(sum(KittyCatch$Treatment==0),4)]<-round(rtnorm(n=4, mean=7.00, sd=.6, min = 5, max = 9),2)
  #Age
    #Create Variable
      KittyCatch$Age<-round(rtnorm(n=n, mean=14, sd=4, min = 10, max = 40))
    #Assign age to be correlated with DistanceWalked
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$DistanceWalked>median(KittyCatch$DistanceWalked),2,-2)))
    #Assign age to be correlated with treatment above age 18
      KittyCatch$Age<-round(KittyCatch$Age+(ifelse(KittyCatch$Age>17 & KittyCatch$Treatment==1,4,0)))
    #Top code in control group
      KittyCatch$Age[KittyCatch$Treatment==0]<-ifelse(KittyCatch$Age[KittyCatch$Treatment==0]>18,18,KittyCatch$Age[KittyCatch$Treatment==0])
  #TotalHoursPlayed
    #Create Variable
      KittyCatch$TotalHoursPlayed<-round(rtnorm(n=n, mean=30, sd=10, min = 1, max = 50))
    #Make it correlated with distance walked
      KittyCatch$TotalHoursPlayed<-round(.8*KittyCatch$TotalHoursPlayed + .2*KittyCatch$TotalHoursPlayed*KittyCatch$DistanceWalked)
    #Randomly assign missing values, make the proportion larger in the treatment; and make the likelihood for NA correlate with larger values
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]<-ifelse(rbinom(sum(KittyCatch$Treatment==0),1,(.05+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0]/mean(KittyCatch$TotalHoursPlayed))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==0])
      KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]<-ifelse(rbinom(sum(KittyCatch$Treatment==1),1,(.25+.05*KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1]/mean(KittyCatch$TotalHoursPlayed,na.rm = T))),NA,KittyCatch$TotalHoursPlayed[KittyCatch$Treatment==1])
  #Make distance walked negatively correlated with treatment prior to balance, and positvely correlated with treatment after balance
      removed<-ifelse(KittyCatch$Age>17 | is.na(KittyCatch$TotalHoursPlayed),1,0)
      KittyCatch$DistanceWalked<-round(ifelse(removed==1 & KittyCatch$Treatment==0,1.5*KittyCatch$DistanceWalked,ifelse(removed==0 & KittyCatch$Treatment==1,1.3*KittyCatch$DistanceWalked,KittyCatch$DistanceWalked)),2)
  KittyCatch$DistanceWalked<-ifelse(KittyCatch$DistanceWalked>2,2,KittyCatch$DistanceWalked)
  KittyCatch<-KittyCatch[KittyCatch$Age<=17,]
  KittyCatch<-KittyCatch[!is.na(KittyCatch$TotalHoursPlayed),]
```

`@sample_code`
```{r}
# 1) Now that we have balanced our data on all known dimensions, let's return the average treatment effect of being in the treatment group with distance walked playing KittyCatch by subtracting the mean DistanceWalked of our control group from the mean DistanceWalked of our treatment group. Assign this answer to Solution1.

    Solution1<-

# Great job. But is that value statistically significant? We don't want to get too excited about it until we know that as well.

# 2) Finally, let's test if the ATE is significant by running a t.test.
  
    t.test()

# 3) Is the p-value of a t-test less than .05? We will use as our standard of significance. Assign Solution3 with "Yes" or "No".

    Solution3<-""
```

`@solution`
```{r}
Solution1<-mean(KittyCatch$DistanceWalked[KittyCatch$Treatment==1])-mean(KittyCatch$DistanceWalked[KittyCatch$Treatment==0])
  t.test(KittyCatch$DistanceWalked[KittyCatch$Treatment==1],KittyCatch$DistanceWalked[KittyCatch$Treatment==0])
  Solution3<-"Yes"
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution1") %>% check_equal()
ex() %>% check_object("Solution3") %>% check_equal()
success_msg("Good work! Hooray!! Our naive estimate of the average treatment effect was opposite our estimate after we tried to balance the data. However, we had to ignore a large fraction of our observations to get to that conclusion. This is the difficulty of computing conditional average treatment effects with t-tests. However, this problem can be sidestepped with regression models. Our next module teaches how to use regression models in detail.")
```
