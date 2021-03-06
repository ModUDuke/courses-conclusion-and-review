---
title: 'IV & RDD'
description: 'If you want to go through these topics in more detail, take our free Causal Inference with R - IV & RDD course here on DataCamp.'
---

## The Logic of Instrumental Variables Analysis

```yaml
type: VideoExercise
key: 77e659ac36
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/219558904
```


---

## IV: What is the Relationship Between the Instrument & the Outcome?

```yaml
type: PureMultipleChoiceExercise
key: 77e659ac35
lang: r
xp: 50
skills: 1
```

As the videos discussed, there are some strict requirements to use instrumental variables analysis, so we will review the relationship between the instrument and the outcome. Which one of these is the correct assumption for IV analysis?

`@hint`


`@possible_answers`
- The instrument has a direct causal effect on the outcome, but is only correlated with the treatment.
- [The instrument has a direct causal effect on the treatment, but is only correlated with the outcome.]
- The instrument has no direct causal effect on either the treatment or the outcome.
- The instrument has a direct causal effect on both the treatment and the outcome.

`@feedback`
- That's not correct. The instrument should only be correlated with the outcome, and must have a causal effect on the treatment variable. Try again.
- Correct! Nice job.
- The instrument must have a causal effect on the treatment (but not on the outcome) to use an instrumental variables analysis. Try again.
- The instrument should have a causal effect on the treatment, but should only be correlated wit the outcome. Try again.

---

## What is the Relationship Between the Instrument & the Treatment?

```yaml
type: PureMultipleChoiceExercise
key: 22957c2411
lang: r
xp: 50
skills: 1
```

Now let us review the relationship between the instrument and the treatment.  Which one of these is the correct assumption for IV analysis?

`@hint`


`@possible_answers`
- The instrument is not correlated with the treatment.
- The treatment has a causal effect on the instrument.
- The treatment and the outcome have a causal effect on the instrument.
- [The instrument has a causal effect on the treatment.]

`@feedback`
- Incorrect. Not only does the instrument need to be correlated with the treatment, it must have a causal effect on the treatment. Try again.
- That is backwards. The instrument needs to have a causal effect on the treatment, so try again.
- This doesn't make much sense: we're trying to find the effect of the treatment on the outcome! Try again.
- Correct!

---

## What is the Relationship Between the Instrument & the Other Pre-Treatment Variables?

```yaml
type: PureMultipleChoiceExercise
key: 8cf442d5b7
lang: r
xp: 50
skills: 1
```

The instrument is one of many variables that could be confounding the effect of what we really want to study: the effect of our treatment on the outcome. Let us review the relationship of the instrument to this larger pool of potential confounders. Which of the following statements is correct for an IV analysis?

`@hint`


`@possible_answers`
- The instrument must be correlated with all measured pre-treatment variables.
- The pre-treatment variables have a causal effect on the instrument.
- We do not need to worry about unobserved pre-treatment variables, they are by definition not correlated with the instrument.
- [The instrument is uncorrelated with the other pre-treatment variables.]

`@feedback`
- This is very incorrect. It should have no correlation to any other pre-treatment variables, a.k.a. is randomly assigned. Try again.
- Incorrect. The other pre-treatment variables should have no correlation with the instrument. Try again.
- This is not true. Just because we don't have data on a variable does not mean it might not affect the instrument. Try again.
- Correct!

---

## How Do We Actually Calculate a Causal Effect with Instrumental Variables Analysis?

```yaml
type: PureMultipleChoiceExercise
key: 431456917c
lang: r
xp: 50
skills: 1
```

So now we can summarize the main purpose of IV analysis. Once again, how does the instrumental variable help us understand the causal effect of the treatment on the outcome?

`@hint`


`@possible_answers`
- The treatment affects the instrument, which affects the outcome. The causal effect of the treatment on the outcome is equal to the correlation of the instrument and the treatment.
- The treatment affects the outcome, and the instrument is correlated with the outcome. To get the effect of the treatment on the outcome, we calculate the correlation of the instrument on the outcome.
- [The instrument affects the treatment, and the treatment affects the outcome. To get the effect of the treatment on the outcome, we find the correlation of the instrument on the outcome, and subtract out the effect of the instrument on the treatment.]
- The instrument and the treatment combine to create the outcome. So the treatment effect is the sum of the effect of the instrument on the treatment and the effect of the treatment on the outcome.

`@feedback`
- This is not the design of IV analysis. We need to subtract out the effect of the instrument on the treatment from the correlation of the instrument on the outcome. Try again.
- Incorrect. We need to subtract out the effect of the instrument on the treatment from the correlation of the instrument on the outcome. Try again.
- Correct! Way to go!
- That is not exactly the process. We do not add these effects together to find the causal effect. Try again.

---

## Some Terminology for Instrumental Variables

```yaml
type: VideoExercise
key: ffa44f7179
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/219565557
```


---

## The Problem with Weak Instruments

```yaml
type: VideoExercise
key: 0999e6e6f0
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/219559996
```


---

## An Example of Using a Weak Instrument

```yaml
type: PureMultipleChoiceExercise
key: d8cf103994
lang: r
xp: 50
skills: 1
```

A public health specialist names Phoebe is interested in how a person's wealth (their assets minus their debts) might effect their health. Phoebe has longitudinal data on people's wealth and health, but she's having trouble determining whether wealth has a causal effect on health with traditional regression models. Phoebe's concern is that a person's health varies endogenously with their weath; a person's wealth might have a positive causal effect on their health, but a person's health could also have a positive causal effect on their wealth. 

To untangle this causal relationship, Phoebe decides to conduct an instrumental variable analysis of wealth's effect on health with inheritance as an exogenous instrument of wealth (that is, inheritance effects a person's wealth but does not have any direct or indirect relationship with a person's health other than through how it might affect wealth). However, Phoebe's analysis yields no statistically significant results. Phoebe also tests the relationship between inheritance and wealth, and finds that there is only a very weak correlation. Which of the following could this imply?

`@hint`


`@possible_answers`
- Inheritance has a direct causal effect on health.
- [These results are uninformative about any potential causality between wealth and health.]
- People who inherit money often feel guilty, leading to a decline in health.
- People are more likely to inherit money when they themselves have poor health.

`@feedback`
- Although this instrumental variable would be poor for this analysis (an instrument should not have a direct effect on the dependent variable), this is not an example of a "weak" instrumental variable.
- Correct! Only a small percentage of people ever inherit a substantial amount of money, and those who do tend to have better wealth to begin with. So despite our theories, the data we have might have very little statistical power on the relationship between wealth and health.
- This answer is very similar to the first one. In this case, the problem is not that the instrument is 'weak' but that the instrument has a direct causal effect on health.
- Although this instrumental variable would be poor for this analysis (an instrument should be randomly assigned), this is not an example of a 'weak' instrumental variable.

---

## Let's Code - Practice Using IV to Solve Noncompliance in the OHIE

```yaml
type: VideoExercise
key: 3bc678cfb9
xp: 50
video_link: //player.vimeo.com/video/306239756
```


---

## Practice Using IV to Solve Noncompliance in the OHIE.

```yaml
type: NormalExercise
key: 0a5fd5af11
lang: r
xp: 100
skills: 1
```

In an earlier course, you analyzed data from the Oregon Healthcare Insurance Experiment (OHIE) where you assumed that everyone who was offered Medicaid coverage ended up getting covered. Now let us relax this assumption and instead assume that not everyone who was offered Medicaid coverage actually enrolled. This is a more realistic model of what actually happened, and it plays into the strengths of the Instrumental Variables method.

So we will use assignment to the treatment group as an instrument, and we will check to see if that instrument shows us whether Medicaid had any effect on one of our health outcomes of interest, the number of people who were identified as having depression during a health screening.

`@instructions`
- 1) Explore the data on your own, using functions like head(), str(), and summary()
- 2) Compute the Intention-to-Treat effect of being offered insurance on having a positive depression screening
- 3) Estimate the 2SLS effect of taking up the offer on positive depression screening using two separate calls to `lm()`

`@hint`
- Remember to include the correct additional demographic control variables in your regression models. There will be a lot of them, but you do not need to include `age_19_34_inp` or `race_white_inp`.

`@pre_exercise_code`
```{r}
set.seed(1)

#------------------------------------------
# Population characteristics for data generation
#------------------------------------------
n                          <- 20745
n_intvw                    <- 12229
frac_intvw                 <- (n_intvw-.5)/n
frac_treated               <- (6387-52)/n_intvw
frac_female                <- .5656
frac_19_34                 <- .3530
frac_35_49                 <- .3710
frac_50_64                 <- .2758
frac_white                 <- .688
frac_black                 <- .1033
frac_other                 <- .144
frac_hispa                 <- .180
frac_intv_english          <- .876
frac_ast_dx_pre_lottery    <- .193065
frac_dia_dx_pre_lottery    <- .071305
frac_hbp_dx_pre_lottery    <- .181944
frac_chl_dx_pre_lottery    <- .126666
frac_ami_dx_pre_lottery    <- .019789
frac_chf_dx_pre_lottery    <- .011121
frac_emp_dx_pre_lottery    <- .022078
frac_kid_dx_pre_lottery    <- .018562
frac_cancer_dx_pre_lottery <- .042767
frac_dep_dx_pre_lottery    <- .340665
frac_any_dx_pre_lottery    <- .159749
#------------------------------------------
# Initialize dataframe
#------------------------------------------
OHIE <- as.data.frame(matrix(0, ncol=23,nrow=n))

colnames(OHIE) <- c("id",
"intvw",
"lottery",
"gender_inp",
"age_19_34_inp",
"age_35_49_inp",
"age_50_64_inp",
"race_white_inp",
"race_black_inp",
"race_nwother_inp",
"hispanic_inp",
"itvw_english_inp",
"ast_dx_pre_lottery",
"dia_dx_pre_lottery",
"hbp_dx_pre_lottery",
"chl_dx_pre_lottery",
"ami_dx_pre_lottery",
"chf_dx_pre_lottery",
"emp_dx_pre_lottery",
"kid_dx_pre_lottery",
"cancer_dx_pre_lottery",
"dep_dx_pre_lottery",
"any_dx_pre_lottery")#Factors=factor(),

#------------------------------------------
# Simulate pre-lottery data
#------------------------------------------
OHIE$id                                                        <- seq(1,n,1)
OHIE$intvw                                                     <- as.integer(runif(n)<frac_intvw)
OHIE[OHIE$intvw==0,c("lottery","gender_inp","age_19_34_inp","age_35_49_inp","age_50_64_inp","race_white_inp","race_black_inp","race_nwother_inp","hispanic_inp","itvw_english_inp","ast_dx_pre_lottery","dia_dx_pre_lottery","hbp_dx_pre_lottery","chl_dx_pre_lottery","ami_dx_pre_lottery","chf_dx_pre_lottery","emp_dx_pre_lottery","kid_dx_pre_lottery","cancer_dx_pre_lottery","dep_dx_pre_lottery")] <- NA
OHIE$lottery[!is.na(OHIE$lottery)]                         <- as.integer(runif(n_intvw)<frac_treated)
OHIE$gender_inp[!is.na(OHIE$gender_inp)]                       <- as.integer(runif(n_intvw)<frac_female)
classdraw                                                      <- runif(n_intvw)
class                                                          <- 1*(classdraw<frac_19_34) + 2*(classdraw<(frac_19_34+frac_35_49) & classdraw>frac_19_34) + 3*(classdraw>(frac_19_34+frac_35_49))
OHIE$age_19_34_inp[!is.na(OHIE$age_19_34_inp)]                 <- as.integer(class==1)
OHIE$age_35_49_inp[!is.na(OHIE$age_35_49_inp)]                 <- as.integer(class==2)
OHIE$age_50_64_inp[!is.na(OHIE$age_50_64_inp)]                 <- as.integer(class==3)
OHIE$race_white_inp[!is.na(OHIE$race_white_inp)]               <- as.integer(runif(n_intvw)<frac_white)
OHIE$race_black_inp[!is.na(OHIE$race_black_inp)]               <- as.integer(runif(n_intvw)<frac_black)
OHIE$race_nwother_inp[!is.na(OHIE$race_nwother_inp)]           <- as.integer(runif(n_intvw)<frac_other)
OHIE$hispanic_inp[!is.na(OHIE$hispanic_inp)]                   <- as.integer(runif(n_intvw)<frac_hispa)
OHIE$itvw_english_inp[!is.na(OHIE$itvw_english_inp)]           <- as.integer(runif(n_intvw)<frac_hispa)
OHIE$ast_dx_pre_lottery[!is.na(OHIE$ast_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_ast_dx_pre_lottery)
OHIE$dia_dx_pre_lottery[!is.na(OHIE$dia_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_dia_dx_pre_lottery)
OHIE$hbp_dx_pre_lottery[!is.na(OHIE$hbp_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_hbp_dx_pre_lottery)
OHIE$chl_dx_pre_lottery[!is.na(OHIE$chl_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_chl_dx_pre_lottery)
OHIE$ami_dx_pre_lottery[!is.na(OHIE$ami_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_ami_dx_pre_lottery)
OHIE$chf_dx_pre_lottery[!is.na(OHIE$chf_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_chf_dx_pre_lottery)
OHIE$emp_dx_pre_lottery[!is.na(OHIE$emp_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_emp_dx_pre_lottery)
OHIE$kid_dx_pre_lottery[!is.na(OHIE$kid_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_kid_dx_pre_lottery)
OHIE$cancer_dx_pre_lottery[!is.na(OHIE$cancer_dx_pre_lottery)] <- as.integer(runif(n_intvw)<frac_cancer_dx_pre_lottery)
OHIE$dep_dx_pre_lottery[!is.na(OHIE$dep_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_dep_dx_pre_lottery)
OHIE$dep_dx_pre_lottery[!is.na(OHIE$dep_dx_pre_lottery)]       <- as.integer(runif(n_intvw)<frac_any_dx_pre_lottery)

#------------------------------------------
# Variable labels
#------------------------------------------
names(OHIE)[(length(OHIE)-10):length(OHIE)] <- c("asthma pre lottery","diabetes pre lottery","hypertension pre lottery","high cholesterol pre lottery","heart attack pre lottery","congestive heart failure pre lottery","emphysema/COPD pre lottery","kidney failure pre lottery","cancer pre lottery","depression pre lottery","any of diabetes, high bp, high chol, heart attack, or cong heart failure pre lottery")

#------------------------------------------
# Simulate first stage
#------------------------------------------
OHIE$insurance <- 0*(OHIE$lottery)
OHIE[OHIE$intvw==0,c("insurance")] <- NA
colnames(OHIE)[length(OHIE)] <- c("insurance")

draw <- runif(n_intvw)
xb   <- -2.82+1*(OHIE$lottery[!is.na(OHIE$lottery)]==1)+.75*(OHIE$gender_inp[!is.na(OHIE$lottery)]==1)+.5*(OHIE$age_19_34_inp[!is.na(OHIE$lottery)]==1)+1*(OHIE$age_35_49_inp[!is.na(OHIE$lottery)]==1)+2*(OHIE$age_50_64_inp[!is.na(OHIE$lottery)]==1)+1.3*(OHIE$race_white_inp[!is.na(OHIE$lottery)]==1)-.4*(OHIE$race_black_inp[!is.na(OHIE$lottery)]==1)-.2*(OHIE$race_nwother_inp[!is.na(OHIE$lottery)]==1)+.1*(OHIE$hispanic_inp[!is.na(OHIE$lottery)]==1)-.7*(OHIE$itvw_english_inp[!is.na(OHIE$lottery)]==1)
p    <- exp(xb)/(1+exp(xb))
OHIE$insurance[!is.na(OHIE$insurance)] <- as.integer(draw<p)

#------------------------------------------
# Simulate second stage
#------------------------------------------
OHIE<-cbind(OHIE,matrix(0,dim(OHIE)[1],19))
colnames(OHIE)[(length(OHIE)-18):length(OHIE)]             <- c("bp_sar_inp","bp_dar_inp","bp_hyper","hbp_dx_post_insurance","hbp_diure_med_inp","chl_inp","chl_h","hdl_inp","hdl_low","chl_dx_post_insurance","antihyperlip_med_inp","a1c_inp","a1c_dia","dia_dx_post_insurance","diabetes_med_inp","pos_depression_screen","dep_dx_post_insurance","antidep_med_inpbinary","cvd_risk_point")
OHIE[OHIE$intvw==0,c("bp_sar_inp","bp_dar_inp","bp_hyper","hbp_dx_post_insurance","hbp_diure_med_inp","chl_inp","chl_h","hdl_inp","hdl_low","chl_dx_post_insurance","antihyperlip_med_inp","a1c_inp","a1c_dia","dia_dx_post_insurance","diabetes_med_inp","pos_depression_screen","dep_dx_post_insurance","antidep_med_inpbinary","cvd_risk_point")] <- NA

# # Hypertension diagnosis (should be .056 + .0176)
# draw <- runif(n_intvw)
# xb   <- -2.82+.22*(OHIE$insurance[!is.na(OHIE$hbp_dx_post_insurance)]==1)
# p    <- exp(xb)/(1+exp(xb))
# OHIE$hbp_dx_post_insurance[!is.na(OHIE$hbp_dx_post_insurance)] <- as.integer(draw<p)
# print("Hypertension")
# print(mean(OHIE$hbp_dx_post_insurance[OHIE$insurance==0],na.rm=TRUE))
# print(mean(OHIE$hbp_dx_post_insurance[OHIE$insurance==1],na.rm=TRUE)-mean(OHIE$hbp_dx_post_insurance[OHIE$insurance==0],na.rm=TRUE))

# # Current use of hypertension medication (should be .139 + .0066)
# draw <- runif(n_intvw)
# xb   <- -1.825+.0716*(OHIE$insurance[!is.na(OHIE$hbp_diure_med_inp)]==1)
# p    <- exp(xb)/(1+exp(xb))
# OHIE$hbp_diure_med_inp[!is.na(OHIE$hbp_diure_med_inp)] <- as.integer(draw<p)
# print("Hypertension Meds")
# print(mean(OHIE$hbp_diure_med_inp[OHIE$insurance==0],na.rm=TRUE))
# print(mean(OHIE$hbp_diure_med_inp[OHIE$insurance==1],na.rm=TRUE)-mean(OHIE$hbp_diure_med_inp[OHIE$insurance==0],na.rm=TRUE))

# # Hypercholesterolemia diagnosis after insurance (should be .061 + .0239)
# draw <- runif(n_intvw)
# xb   <- -2.72+.371*(OHIE$insurance[!is.na(OHIE$chl_dx_post_insurance)]==1)
# p    <- exp(xb)/(1+exp(xb))
# OHIE$chl_dx_post_insurance[!is.na(OHIE$chl_dx_post_insurance)] <- as.integer(draw<p)
# print("Hypercholesterolemia")
# print(mean(OHIE$chl_dx_post_insurance[OHIE$insurance==0],na.rm=TRUE))
# print(mean(OHIE$chl_dx_post_insurance[OHIE$insurance==1],na.rm=TRUE)-mean(OHIE$chl_dx_post_insurance[OHIE$insurance==0],na.rm=TRUE))

# # Current use of high cholesterol medication (should be .085 + .0380)
# draw <- runif(n_intvw)
# xb   <- -2.36+.384*(OHIE$insurance[!is.na(OHIE$antihyperlip_med_inp)]==1)
# p    <- exp(xb)/(1+exp(xb))
# OHIE$antihyperlip_med_inp[!is.na(OHIE$antihyperlip_med_inp)] <- as.integer(draw<p)
# print("Hypercholesterolemia Meds")
# print(mean(OHIE$antihyperlip_med_inp[OHIE$insurance==0],na.rm=TRUE))
# print(mean(OHIE$antihyperlip_med_inp[OHIE$insurance==1],na.rm=TRUE)-mean(OHIE$antihyperlip_med_inp[OHIE$insurance==0],na.rm=TRUE))

# Positive depression screen (should be .3 - .0915)
draw <- runif(n_intvw)
xb   <- -.828-.55*(OHIE$insurance[!is.na(OHIE$pos_depression_screen)]==1)-.8*(OHIE$gender_inp[!is.na(OHIE$lottery)]==1)+.5*(OHIE$age_19_34_inp[!is.na(OHIE$lottery)]==1)+1*(OHIE$age_35_49_inp[!is.na(OHIE$lottery)]==1)+2*(OHIE$age_50_64_inp[!is.na(OHIE$lottery)]==1)+1.3*(OHIE$race_white_inp[!is.na(OHIE$lottery)]==1)-.4*(OHIE$race_black_inp[!is.na(OHIE$lottery)]==1)-.2*(OHIE$race_nwother_inp[!is.na(OHIE$lottery)]==1)+.1*(OHIE$hispanic_inp[!is.na(OHIE$lottery)]==1)-.7*(OHIE$itvw_english_inp[!is.na(OHIE$lottery)]==1)
p    <- exp(xb)/(1+exp(xb))
OHIE$pos_depression_screen[!is.na(OHIE$pos_depression_screen)] <- as.integer(draw<p)
# print("Positive depression screen")
# print(mean(OHIE$pos_depression_screen[OHIE$insurance==0],na.rm=TRUE))
# print(mean(OHIE$pos_depression_screen[OHIE$insurance==1],na.rm=TRUE)-mean(OHIE$pos_depression_screen[OHIE$insurance==0],na.rm=TRUE))

# # Depression diagnosis after insurance (should be .048 + .0381)
# draw <- runif(n_intvw)
# xb   <- -3.22+.571*(OHIE$insurance[!is.na(OHIE$dep_dx_post_insurance)]==1)
# p    <- exp(xb)/(1+exp(xb))
# OHIE$dep_dx_post_insurance[!is.na(OHIE$dep_dx_post_insurance)] <- as.integer(draw<p)
# print("Depression diagnosis after insurance")
# print(mean(OHIE$dep_dx_post_insurance[OHIE$insurance==0],na.rm=TRUE))
# print(mean(OHIE$dep_dx_post_insurance[OHIE$insurance==1],na.rm=TRUE)-mean(OHIE$dep_dx_post_insurance[OHIE$insurance==0],na.rm=TRUE))

# # Current use of depression meds (should be .168 + .0549)
# draw <- runif(n_intvw)
# xb   <- -1.825+.46*(OHIE$insurance[!is.na(OHIE$antidep_med_inpbinary)]==1)
# p    <- exp(xb)/(1+exp(xb))
# OHIE$antidep_med_inpbinary[!is.na(OHIE$antidep_med_inpbinary)] <- as.integer(draw<p)
# print("Current use of depression meds")
# print(mean(OHIE$antidep_med_inpbinary[OHIE$insurance==0],na.rm=TRUE))
# print(mean(OHIE$antidep_med_inpbinary[OHIE$insurance==1],na.rm=TRUE)-mean(OHIE$antidep_med_inpbinary[OHIE$insurance==0],na.rm=TRUE))

# # Diabetes diagnosis after insurance (should be .011 + .0383)
# draw <- runif(n_intvw)
# xb   <- -4.44+1.451*(OHIE$insurance[!is.na(OHIE$dia_dx_post_insurance)]==1)
# p    <- exp(xb)/(1+exp(xb))
# OHIE$dia_dx_post_insurance[!is.na(OHIE$dia_dx_post_insurance)] <- as.integer(draw<p)
# print("Diabetes diagnosis after insurance")
# print(mean(OHIE$dia_dx_post_insurance[OHIE$insurance==0],na.rm=TRUE))
# print(mean(OHIE$dia_dx_post_insurance[OHIE$insurance==1],na.rm=TRUE)-mean(OHIE$dia_dx_post_insurance[OHIE$insurance==0],na.rm=TRUE))

# # Continuous outcomes
# OHIE$bp_sar_inp[!is.na(OHIE$bp_sar_inp)]         <- rnorm(n_intvw,mean=119.3,sd=16.9)-.52*(OHIE$insurance[!is.na(OHIE$bp_sar_inp)]==1)
# OHIE$bp_dar_inp[!is.na(OHIE$bp_dar_inp)]         <- rnorm(n_intvw,mean= 76.0,sd=12.1)-.81*(OHIE$insurance[!is.na(OHIE$bp_dar_inp)]==1)
# OHIE$bp_hyper[!is.na(OHIE$bp_sar_inp)]           <- as.integer(OHIE$bp_sar_inp[!is.na(OHIE$bp_sar_inp)]>=140 & OHIE$bp_dar_inp[!is.na(OHIE$bp_sar_inp)]>=90)
# OHIE$chl_inp[!is.na(OHIE$chl_inp)]               <- rnorm(n_intvw,mean=204.1,sd=34.0)+2.2*(OHIE$insurance[!is.na(OHIE$chl_inp)]==1)
# OHIE$hdl_inp[!is.na(OHIE$hdl_inp)]               <- rnorm(n_intvw,mean= 47.6,sd=13.1)+2.2*(OHIE$insurance[!is.na(OHIE$hdl_inp)]==1)
# OHIE$chl_h[!is.na(OHIE$chl_inp)]                 <- as.integer(OHIE$chl_inp[!is.na(OHIE$chl_inp)]>=240)
# OHIE$hdl_low[!is.na(OHIE$hdl_inp)]               <- as.integer(OHIE$hdl_inp[!is.na(OHIE$hdl_inp)]< 40 )
# OHIE$a1c_inp[!is.na(OHIE$a1c_inp)]               <- rnorm(n_intvw,mean=  5.3,sd= 0.6)+0.1*(OHIE$insurance[!is.na(OHIE$hdl_inp)]==1)
# OHIE$a1c_dia[!is.na(OHIE$a1c_inp)]               <- as.integer(OHIE$a1c_inp[!is.na(OHIE$a1c_dia)]>=6.5)
# OHIE$cvd_risk_point[!is.na(OHIE$cvd_risk_point)] <- rnorm(n_intvw,mean=  8.2,sd= 7.5)-0.2*(OHIE$insurance[!is.na(OHIE$cvd_risk_point)]==1)

#------------------------------------------
# Pare down data
#------------------------------------------
OHIE <- OHIE[!is.na(OHIE$pos_depression_screen),c("id","intvw","lottery","gender_inp","age_19_34_inp","age_35_49_inp","age_50_64_inp","race_white_inp","race_black_inp","race_nwother_inp","hispanic_inp","itvw_english_inp","insurance","pos_depression_screen")]

# # Add code for ivreg2 function
# ivreg2 <- function(form,endog,iv,data,digits=3){
    # # library(MASS)
    # # model setup
    # r1 <- lm(form,data)
    # y <- r1$fitted.values+r1$resid
    # x <- model.matrix(r1)
    # aa <- rbind(endog == colnames(x),1:dim(x)[2])  
    # z <- cbind(x[,aa[2,aa[1,]==0]],data[,iv])  
    # colnames(z)[(dim(z)[2]-length(iv)+1):(dim(z)[2])] <- iv  
    # # iv coefficients and standard errors
    # z <- as.matrix(z)
    # pz <- z %*% (solve(crossprod(z))) %*% t(z)
    # biv <- solve(crossprod(x,pz) %*% x) %*% (crossprod(x,pz) %*% y)
    # sigiv <- crossprod((y - x %*% biv),(y - x %*% biv))/(length(y)-length(biv))
    # vbiv <- as.numeric(sigiv)*solve(crossprod(x,pz) %*% x)
    # res <- cbind(biv,sqrt(diag(vbiv)),biv/sqrt(diag(vbiv)),(1-pnorm(biv/sqrt(diag(vbiv))))*2)
    # res <- matrix(as.numeric(sprintf(paste("%.",paste(digits,"f",sep=""),sep=""),res)),nrow=dim(res)[1])
    # rownames(res) <- colnames(x)
    # colnames(res) <- c("Coef","S.E.","t-stat","p-val")
    # # First-stage F-test
    # y1 <- data[,endog]
    # z1 <- x[,aa[2,aa[1,]==0]]
    # bet1 <- solve(crossprod(z)) %*% crossprod(z,y1)
    # bet2 <- solve(crossprod(z1)) %*% crossprod(z1,y1)
    # rss1 <- sum((y1 - z %*% bet1)^2)
    # rss2 <- sum((y1 - z1 %*% bet2)^2)
    # p1 <- length(bet1)
    # p2 <- length(bet2)
    # n1 <- length(y)
    # fs <- abs((rss2-rss1)/(p2-p1))/(rss1/(n1-p1))
    # firststage <- c(fs)
    # firststage <- matrix(as.numeric(sprintf(paste("%.",paste(digits,"f",sep=""),sep=""),firststage)),ncol=length(firststage))
    # colnames(firststage) <- c("First Stage F-test")
    # # Hausman tests
    # bols <- solve(crossprod(x)) %*% crossprod(x,y) 
    # sigols <- crossprod((y - x %*% bols),(y - x %*% bols))/(length(y)-length(bols))
    # vbols <- as.numeric(sigols)*solve(crossprod(x))
    # sigml <- crossprod((y - x %*% bols),(y - x %*% bols))/(length(y))
    # x1 <- x[,!(colnames(x) %in% "(Intercept)")]
    # z1 <- z[,!(colnames(z) %in% "(Intercept)")]
    # pz1 <- z1 %*% (solve(crossprod(z1))) %*% t(z1)
    # biv1 <- biv[!(rownames(biv) %in% "(Intercept)"),]
    # bols1 <- bols[!(rownames(bols) %in% "(Intercept)"),]
    # # Durbin-Wu-Hausman chi-sq test:
    # # haus <- t(biv1-bols1) %*% ginv(as.numeric(sigml)*(solve(crossprod(x1,pz1) %*% x1)-solve(crossprod(x1)))) %*% (biv1-bols1)
    # # hpvl <- 1-pchisq(haus,df=1)
    # # Wu-Hausman F test
    # resids <- NULL
    # resids <- cbind(resids,y1 - z %*% solve(crossprod(z)) %*% crossprod(z,y1))
    # x2 <- cbind(x,resids)
    # bet1 <- solve(crossprod(x2)) %*% crossprod(x2,y)
    # bet2 <- solve(crossprod(x)) %*% crossprod(x,y)
    # rss1 <- sum((y - x2 %*% bet1)^2)
    # rss2 <- sum((y - x %*% bet2)^2)
    # p1 <- length(bet1)
    # p2 <- length(bet2)
    # n1 <- length(y)
    # fs <- abs((rss2-rss1)/(p2-p1))/(rss1/(n1-p1))
    # fpval <- 1-pf(fs, p1-p2, n1-p1)
    # #hawu <- c(haus,hpvl,fs,fpval)
    # hawu <- c(fs,fpval)
    # hawu <- matrix(as.numeric(sprintf(paste("%.",paste(digits,"f",sep=""),sep=""),hawu)),ncol=length(hawu))
    # #colnames(hawu) <- c("Durbin-Wu-Hausman chi-sq test","p-val","Wu-Hausman F-test","p-val")
    # colnames(hawu) <- c("Wu-Hausman F-test","p-val")  
    # # Sargan Over-id test
    # ivres <- y - (x %*% biv)
    # oid <- solve(crossprod(z)) %*% crossprod(z,ivres)
    # sstot <- sum((ivres-mean(ivres))^2)
    # sserr <- sum((ivres - (z %*% oid))^2)
    # rsq <- 1-(sserr/sstot)
    # sargan <- length(ivres)*rsq
    # spval <- 1-pchisq(sargan,df=length(iv)-1)
    # overid <- c(sargan,spval)
    # overid <- matrix(as.numeric(sprintf(paste("%.",paste(digits,"f",sep=""),sep=""),overid)),ncol=length(overid))
    # colnames(overid) <- c("Sargan test of over-identifying restrictions","p-val")
    # if(length(iv)-1==0){
      # overid <- t(matrix(c("No test performed. Model is just identified")))
      # colnames(overid) <- c("Sargan test of over-identifying restrictions")
    # }
    # full <- list(results=res, weakidtest=firststage, endogeneity=hawu, overid=overid)
    # return(full)
# }
```

`@sample_code`
```{r}
# The dataset `OHIE` and the function `ivreg2` are both available in your workspace. Here is a data dictionary to help you make sense of the variable names and what they are representing:

# Data Dictionary:

#  `id` - patient ID
#  `intvw` - was patient interviewed?
#  `lottery` - did patient win in the Medicaid lottery?
#  `gender_inp` - gender, where 1 is female*
#  `age_19_34_inp` - 1 if age is between 19 and 34*
#  `age_35_49_inp` - 1 if age is between 35 and 49*
#  `age_50_64_inp` - 1 if age is between 50 and 64*
#  `race_white_inp` -  1 if race is white*
#  `race_black_inp` - 1 if race is black*
#  `race_nwother_inp` - 1 if race is nonwhite and nonblack*
#  `hispanic_inp` - 1 if hispanic*
#  `itvw_english_inp` - 1 if interview was held in english*
#  `insurance` - did patient have health insurance at all?
#  `pos_depression_screen` - 1 if patient tested positive for depression
#  *note: `_inp` variable suffix - recorded during in-person interview

# 1) On your own, explore the dataframe and get familiar with the ranges of values and data types it contains. We suggest using commands like head(), str(), and summary() for different variables to get a sense of what the data look like. 





# 2) Let's see what answer we get if we treat the lottery as an experiment where we consider getting the option for Medicaid as our treatment, and see if it shows any effect on our outcome of interest, the ratio of people with positive depression screens, which is captured in the variable `pos_depression_screen`. Using a linear regression, compute the Intention-to-Treat effect of being assigned to the treatment group ("lottery" variable) on positive depression screening, while also controlling for gender, age, ethnicity, and interview language (so it will be a long list of variable names). Exclude `age_19_34_inp` and `race_white_inp` from the set of right hand side dummy variables.

    Solution2<-summary(lm( ~ ,data=OHIE))
	summary()

# Good. If you take a look at Solution1, you'll see that having the option of getting insurance through the lottery seems to have a small downward pressure on our positive depression screen variable, which is good! But is this really a causal effect? Let's try again with IV analysis and see what we get.


# 3) Now we will use the 2-Stage Least Squares method to calculate our causal effect through our instrumental variable, `lottery`.  

# The first stage is to find the correlation between the treatment and the instrument, which we will store this correlation in the variable `prediction`. Fill out the following function with the dependent and independent variables we need to control for (it should be the same list of variables as in the previous regression):

    OHIE$prediction<-predict(lm( ~ ,data=OHIE))
    
# The second stage is to find the correlation between our outcome and our adjusted treatment variable `prediction`, holding the same other variables constant. So use `prediction` to compute the the 2SLS effect of insurance takeup on depression by using `lottery` as an instrument for the endogenous takeup indicator "insurance". This will give us the causal effect of health insurance on our outcome of interest, the ratio of people with positive depression screen scores.

	Solution3<-summary(lm( ~ prediction+... ,data=OHIE))
	summary()


```

`@solution`
```{r}
Solution2<-summary(lm(pos_depression_screen~lottery+gender_inp+age_35_49_inp+age_50_64_inp+race_black_inp+race_nwother_inp+hispanic_inp+itvw_english_inp,data=OHIE))
OHIE$prediction<-predict(lm(insurance~lottery+gender_inp+age_35_49_inp+age_50_64_inp+race_black_inp+race_nwother_inp+hispanic_inp+itvw_english_inp,data=OHIE),data=OHIE)
Solution3<-summary(lm(pos_depression_screen~prediction+gender_inp+age_35_49_inp+age_50_64_inp+race_black_inp+race_nwother_inp+hispanic_inp+itvw_english_inp,data=OHIE),data=OHIE)
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution2") %>% check_equal()
ex() %>% check_object("Solution3") %>% check_equal()
success_msg("Good work! This estimate for the causal effect of insurance on our outcome variable, positive depression screens, is about 5 times larger than we saw in the Intention-to-Treat analysis. It looks like health insurance does improve health outcomes, at least for this variable.")
```

---

## Key Variables in an Regression Discontinuity Design

```yaml
type: PureMultipleChoiceExercise
key: 0873ca9d88
lang: r
xp: 50
skills: 1
```

Which of the following variables is *not* a key (required) variable in a regression discontinuity design?

`@hint`


`@possible_answers`
- Outcome variable
- [Control variable]
- Treatment variable
- Running variable

`@feedback`
- The outcome variable is the variable of interest. Try again
- Correct! While most RD's use at least one control variable, doing so is not strictly necessary for RD analysis, i.e. it is possible, but not common, to run an RD without any control variables.
- The treatment variable is necessary in order to estimate any kind of causal effect. Try again
- The running variable is how the researcher divides the sample into treatment and control groups. Try again

---

## Identifying the Key Variables in an RD Design

```yaml
type: PureMultipleChoiceExercise
key: c874bebcac
lang: r
xp: 50
skills: 1
```

A pair of researchers named Jonah Berger and Devin Pope recently published a study about the results of professional basketball games that found that, surprisingly, sometimes losing can lead to winning. The researchers were looking at the determinants of winning in the National Basketball Association (NBA), and they had compiled a dataset of thousands of NBA games. When they looked at the halftime and final scores of each team, and after controlling for other important factors (like the winning percentage of each team), they found that teams who were slightly ahead at halftime were actually more likely to lose the game than the team that was behind at halftime. One theory to explain this outcome is that the team losing at halftime tries a little harder in the second half, while the team winning at halftime relaxes a little too much and loses the game.

So in this study, which variable is the outcome variable, which is the running variable, and which is the treatment variable?

`@hint`


`@possible_answers`
- The score at halftime is the outcome variable, winning the game is the running variable, and the home team losing at halftime is the treatment variable.
- Winning the game is the outcome variable, the home team losing at halftime is the running variable, and the score at halftime is the treatment variable.
- The score at halftime is the outcome variable, the home team losing at halftime is the running variable, and winning the game is the treatment variable.
- [Winning the game is the outcome variable, the score at halftime is the running variable, and the home team winning at halftime is the treatment variable.]

`@feedback`
- The outcome we are ultimately interested in is winning the game, so that is our outcome variable. Try again.
- This is close but not quite right. The running variable has to do with the halftime score, but it is not whether the home team is losing. Try again.
- The outcome we are ultimately interested in is winning the game, so that is our outcome variable. Try again.
- Correct!

---

## How to Compute Causal Effects in Regression Discontinuity Analysis

```yaml
type: VideoExercise
key: b56a22797e
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/218502963
```


---

## Let's Code - Examining Manipulation in Regression Discontinuity Design

```yaml
type: VideoExercise
key: 1d22c71666
xp: 50
video_link: //player.vimeo.com/video/306239772
```


---

## Examining Manipulation in Regression Discontinuity Design.

```yaml
type: NormalExercise
key: 32a4f677f9
lang: r
xp: 100
skills: 1
```

As we have mentioned, the main idea with Regression Discontinuity is that there should not be any difference in the people on either side of the cutoff. So a big part of RD analysis is to check whether this is actually true in our data. For example, the distributions of our variables should be the same on both sides of the cutoff. If people choose which side of the cutoff in order to influence the outcome, then we might worry that people on either side of the cutoff are not comparable.

Let's look at this by revisiting the NBA data we used before in previous exercises. In that data, we saw that teams that are losing by 1 or 2 points at halftime end up winning the games a lot more than you would expect. If the coaches and players know this is true, they might try to manipulate the score so that they are the ones losing by 1 or 2 at halftime (perhaps because they read that research paper published in Management Science!). If we look at a density plot of our data, we would see this as a kind of lump in the distribution on one side next to the cutoff, instead of a smooth curve in our data density.

So we will check the data to check our distributions near the cutoff with the statistical McCrary test, which tests whether there is a discontinuity in the data frequency distribution around the cutoff. We will look at plots and at the p-values of the McCrary tests, and if the p-values are at or below .05, then we can be 95% confident that manipulation has occurred. So let's find out if that is true in this NBA data.

`@instructions`
- 1) Examine the structure of the dataframe `NBA`
- 2) Using the function `DCdensity` to run a McCrary test and examine the plot the distribution of data near the cutoff
- 3) Check the statistical significance of the McCrary test through its p-value
- 4) Decide if the data is suitable for a regression discontinuity analysis
- 5) Using a new dataset, check updated data for manipulation via a McCrary test
- 6) Check this new McCrary test for statistical significance
- 7) Decide if this new data is suitable for a regression discontinuity analysis

`@hint`
- A p-value less than or equal to .05 means that we can have 95% confidence that the data has actually been manipulated. We will use the standard that anything less than 95% confidence in manipulation will be interpreted as no manipulation was occurring in these games.

`@pre_exercise_code`
```{r}
set.seed(1)
n <- 18060

# Initialize dataframe
NBA <- as.data.frame(matrix(0, ncol=10,nrow=n))
colnames(NBA) <- c("id","season","home.team","away.team","home.team.qual","away.team.qual","home.team.halftime.score","away.team.halftime.score","home.team.final.margin","home.team.win")

# Simulate baseline data
NBA$id         <- seq(1,n,1)
NBA$season     <- ifelse(NBA$id %in% seq( 0*1204+1, 1*1204,1),1994,
                  ifelse(NBA$id %in% seq( 1*1204+1, 2*1204,1),1995,
                  ifelse(NBA$id %in% seq( 2*1204+1, 3*1204,1),1996,
                  ifelse(NBA$id %in% seq( 3*1204+1, 4*1204,1),1997,
                  ifelse(NBA$id %in% seq( 4*1204+1, 5*1204,1),1998,
                  ifelse(NBA$id %in% seq( 5*1204+1, 6*1204,1),1999,
                  ifelse(NBA$id %in% seq( 6*1204+1, 7*1204,1),2000,
                  ifelse(NBA$id %in% seq( 7*1204+1, 8*1204,1),2001,
                  ifelse(NBA$id %in% seq( 8*1204+1, 9*1204,1),2002,
                  ifelse(NBA$id %in% seq( 9*1204+1,10*1204,1),2003,
                  ifelse(NBA$id %in% seq(10*1204+1,11*1204,1),2004,
                  ifelse(NBA$id %in% seq(11*1204+1,12*1204,1),2005,
                  ifelse(NBA$id %in% seq(12*1204+1,13*1204,1),2006,
                  ifelse(NBA$id %in% seq(13*1204+1,14*1204,1),2007,
                  ifelse(NBA$id %in% seq(14*1204+1,15*1204,1),2008,0)))))))))))))))
teamqual <- cbind(c("BOS","NJN","NYK","PHL","GSW","LAC","LAL","PHX","SAC","CHI","CLE","DET","IND","MIL","DAL","HOU","MEM","SAS","ATL","CHA","MIA","ORL","WSH","DEN","MIN","SEA","POR","UTA"),
                  matrix(rnorm(28*15,mean=0,sd=1), ncol=15))
NBA$home.team      <- sample(teamqual[,1],n,replace=TRUE)
NBA$away.team      <- sample(teamqual[,1],n,replace=TRUE)
print(paste0('Number of teams playing themselves: ',sum(NBA$home.team==NBA$away.team)/n*100,'%'))
for (i in 1:n) {
    if (NBA$home.team[i]==NBA$away.team[i]) {
        NBA$away.team[i] <- sample(setdiff(teamqual[,1],NBA$home.team[i]),1)
    }
}
print(paste0('Number of teams playing themselves: ',sum(NBA$home.team==NBA$away.team)/n*100,'%'))

# generate team qualities to explain outcomes for each game
for (i in 1:n) {
    NBA$away.team.qual[i] <- as.numeric(teamqual[teamqual[,1]==NBA$away.team[i],NBA$season[i]-1992])
    NBA$home.team.qual[i] <- as.numeric(teamqual[teamqual[,1]==NBA$home.team[i],NBA$season[i]-1992])
}

NBA$home.team <- as.factor(NBA$home.team)
NBA$away.team <- as.factor(NBA$away.team)

# Generate halftime scores
NBA$home.team.halftime.score  <- round(NBA$home.team.qual+rnorm(n, mean=48, sd=4), digits=0)
NBA$away.team.halftime.score  <- round(NBA$away.team.qual+rnorm(n, mean=47, sd=6), digits=0)
NBA$home.team.halftime.margin <- NBA$home.team.halftime.score - NBA$away.team.halftime.score
NBA$home.team.halftime.margin.newdata <- NBA$home.team.halftime.margin-2*(NBA$home.team.halftime.margin==1)-2.25*(NBA$home.team.halftime.margin==2)

# Remove games that are tied at halftime
print(dim(NBA))
NBA <- NBA[NBA$home.team.halftime.margin!=0,]
print(dim(NBA))
n1 <- dim(NBA)[1]

# Generate final score
NBA$home.team.winning.at.half <- NBA$home.team.halftime.margin>0
NBA$home.team.final.margin    <- round(2 - 5*NBA$home.team.winning.at.half + 2*NBA$home.team.halftime.margin -.05*NBA$home.team.halftime.margin^2 + NBA$home.team.qual - NBA$away.team.qual + rnorm(n1, mean=0, sd=10), digits=0)
NBA$home.team.win             <- NBA$home.team.final.margin>0

# Clean up data
NBA$season <- as.factor(NBA$season)
NBA <- NBA[,c("id","season","home.team","away.team","home.team.qual","away.team.qual","home.team.halftime.margin","home.team.final.margin","home.team.winning.at.half","home.team.win","home.team.halftime.margin.newdata")]


kernelwts<-function(X,center,bw,kernel="triangular"){
  dist<-(X-center)/bw
  if(kernel=="triangular"){
    w<-(1-abs(dist))
  } else if (kernel=="rectangular") {
    w<-1/2
  } else if (kernel=="epanechnikov") {
    w<-3/4*(1-dist^2)
  } else if (kernel=="quartic" | kernel=="biweight") {
    w<-15/16*(1-dist^2)^2
  } else if (kernel=="triweight") {
    w<-35/32*(1-dist^2)^3
  } else if (kernel=="tricube") {
    w<-70/81*(1-abs(dist)^3)^3
  } else if (kernel=="gaussian") {
    w<-1/sqrt(2*pi)*exp(-1/2*dist^2)
  } else if (kernel=="cosine") {
    w<-pi/4*cos(pi/2 * dist)
  } else {
    stop("Invalid kernel selection.")
  }
  w<-ifelse(abs(dist)>1&kernel!="gaussian",0,w)
  w<-w/sum(w)
  return(w)
}


DCdensity <- function(runvar,cutpoint,bin=NULL,bw=NULL,verbose=FALSE,plot=TRUE,ext.out=FALSE,htest=FALSE) {
  runvar <- runvar[complete.cases(runvar)]
  #Grab some summary vars
  rn <- length(runvar)
  rsd <- sd(runvar)
  rmin <- min(runvar)
  rmax <- max(runvar)
  if(missing(cutpoint)) {
    if(verbose) cat("Assuming cutpoint of zero.\n")
    cutpoint<-0
  }
  
  if(cutpoint<=rmin | cutpoint>=rmax){
   stop("Cutpoint must lie within range of runvar") 
  }
  
  if(is.null(bin)) {
    bin <- 2*rsd*rn^(-1/2)
    if(verbose) cat("Using calculated bin size: ",sprintf("%.3f",bin),"\n")
  }
  
  l <- floor((rmin - cutpoint)/bin)*bin + bin/2 + cutpoint #Midpoint of lowest bin
  r <- floor((rmax - cutpoint)/bin)*bin + bin/2 + cutpoint #Midpoint of highest bin
  lc <- cutpoint-(bin/2) #Midpoint of bin just left of breakpoint
  rc <- cutpoint+(bin/2) #Midpoint of bin just right of breakpoint
  j <- floor((rmax - rmin)/bin) + 2
  
  binnum <- round((((floor((runvar - cutpoint)/bin)*bin + bin/2 + cutpoint) - l)/bin) + 1)

  cellval <- rep(0,j)
  for(i in seq(1,rn)){
   cnum <- binnum[i]
   cellval[cnum] <- cellval[cnum]+1
  }
  cellval <- ( cellval / rn ) / bin

  cellmp <- seq(from=1,to=j,by=1)
  cellmp <- floor(((l + (cellmp - 1)*bin ) - cutpoint)/bin)*bin + bin/2 + cutpoint
  
  #If no bandwidth is given, calc it
  if(is.null(bw)){
    #bin number just left of breakpoint
    leftofc <-  round((((floor((lc - cutpoint)/bin)*bin + bin/2 + cutpoint) - l)/bin) + 1) 
    #bin number just right of breakpoint
    rightofc <- round((((floor((rc - cutpoint)/bin)*bin + bin/2 + cutpoint) - l)/bin) + 1)
    if ( rightofc - leftofc != 1) {
      stop("Error occurred in bandwidth calculation")
    }
    cellmpleft <- cellmp[1:leftofc]
    cellmpright <- cellmp[rightofc:j]
    
    #Estimate 4th order polynomial to the left
    P.lm <- lm(
      cellval ~ poly(cellmp,degree=4,raw=T), 
      subset=cellmp<cutpoint
    )
    mse4 <- summary(P.lm)$sigma^2
    lcoef <- coef(P.lm)
    fppleft <- 2*lcoef[3] +
      6*lcoef[4]*cellmpleft + 
      12*lcoef[5]*cellmpleft*cellmpleft
    hleft <- 3.348*(mse4*( cutpoint - l ) / sum(fppleft*fppleft))^(1/5)

    #And to the right
    P.lm <- lm(
      cellval ~ poly(cellmp,degree=4,raw=T), 
      subset=cellmp>=cutpoint
    )
    mse4 <- summary(P.lm)$sigma^2
    rcoef <- coef(P.lm)
    fppright <- 2*rcoef[3] +
      6*rcoef[4]*cellmpright +
      12*rcoef[5]*cellmpright*cellmpright
    hright <- 3.348*(mse4*( r - cutpoint ) / sum(fppright*fppright))^(1/5)


    bw = .5*( hleft + hright )
    if(verbose) cat("Using calculated bandwidth: ",sprintf("%.3f",bw),"\n")
  } 
  if( sum(runvar>cutpoint-bw & runvar<cutpoint) ==0 |
    sum(runvar<cutpoint+bw & runvar>=cutpoint) ==0)
    stop("Insufficient data within the bandwidth.")
  if(plot){
    #estimate density to either side of the cutpoint using a triangular kernel
    d.l<-data.frame(cellmp=cellmp[cellmp<cutpoint],cellval=cellval[cellmp<cutpoint],dist=NA,est=NA,lwr=NA,upr=NA)
    pmin<-cutpoint-2*rsd
    pmax<-cutpoint+2*rsd
    for(i in 1:nrow(d.l)) {
      d.l$dist<-d.l$cellmp-d.l[i,"cellmp"]
      w<-kernelwts(d.l$dist,0,bw,kernel="triangular")
      newd<-data.frame(dist=0)
      pred<-predict(lm(cellval~dist,weights=w,data=d.l),interval="confidence",newdata=newd)
      d.l$est[i]<-pred[1]
      d.l$lwr[i]<-pred[2]
      d.l$upr[i]<-pred[3]
    }
    d.r<-data.frame(cellmp=cellmp[cellmp>=cutpoint],cellval=cellval[cellmp>=cutpoint],dist=NA,est=NA,lwr=NA,upr=NA)
    for(i in 1:nrow(d.r)) {
      d.r$dist<-d.r$cellmp-d.r[i,"cellmp"]
      w<-kernelwts(d.r$dist,0,bw,kernel="triangular")
      newd<-data.frame(dist=0)
      pred<-predict(lm(cellval~dist,weights=w,data=d.r),interval="confidence",newdata=newd)
      d.r$est[i]<-pred[1]
      d.r$lwr[i]<-pred[2]
      d.r$upr[i]<-pred[3]
    }
    #plot to the left
    #return(list(d.l,d.r))
    plot(d.l$cellmp,d.l$est,
       lty=1,lwd=2,col="black",type="l",
       xlim=c(pmin,pmax),
       ylim=c(min(cellval[cellmp<=pmax&cellmp>=pmin]),
              max(cellval[cellmp<=pmax&cellmp>=pmin])),
       xlab=NA,
       ylab=NA,
       main=NA
    )
    
    lines(d.l$cellmp,d.l$lwr,
         lty=2,lwd=1,col="black",type="l"
    )
    lines(d.l$cellmp,d.l$upr,
          lty=2,lwd=1,col="black",type="l"
    )
    
    #plot to the right
    lines(d.r$cellmp,d.r$est,
        lty=1,lwd=2,col="black",type="l"
    )
    lines(d.r$cellmp,d.r$lwr,
          lty=2,lwd=1,col="black",type="l"
    )
    lines(d.r$cellmp,d.r$upr,
          lty=2,lwd=1,col="black",type="l"
    )
    
    #plot the histogram as points
    points(cellmp,cellval,type="p",pch=20)
  }
  cmp<-cellmp
  cval<-cellval
  padzeros <- ceiling(bw/bin)
  jp <- j + 2*padzeros
  if(padzeros>=1) {
    cval <- c(rep(0,padzeros),
               cellval,
               rep(0,padzeros)
             )
    cmp <- c(seq(l-padzeros*bin,l-bin,bin),
              cellmp,
              seq(r+bin,r+padzeros*bin,bin)
            )
  }
  
  #Estimate to the left
  dist <- cmp - cutpoint
  w <- 1-abs(dist/bw)
  w <- ifelse(w>0, w*(cmp<cutpoint), 0)
  w <- (w/sum(w))*jp
  fhatl <- predict(lm(cval~dist,weights=w),newdata=data.frame(dist=0))[[1]]
  
  #Estimate to the right
  w <- 1-abs(dist/bw)
  w <- ifelse(w>0, w*(cmp>=cutpoint), 0)
  w <- (w/sum(w))*jp
  fhatr<-predict(lm(cval~dist,weights=w),newdata=data.frame(dist=0))[[1]]
  
  #Calculate and display dicontinuity estimate
  thetahat <- log(fhatr) - log(fhatl)
  sethetahat <- sqrt( (1/(rn*bw)) * (24/5) * ((1/fhatr) + (1/fhatl)) )
  z<-thetahat/sethetahat
  p<-2*pnorm(abs(z),lower.tail=FALSE)

  if(verbose) {
    cat("Log difference in heights is ",
              sprintf("%.3f",thetahat),
              " with SE ",
              sprintf("%.3f",sethetahat),"\n"
        )
    cat("  this gives a z-stat of ",sprintf("%.3f",z),"\n")
    cat("  and a p value of ",sprintf("%.3f",p),"\n")
  }
  if(ext.out) 
    return(list(theta=thetahat,
                se=sethetahat,
                z=z,
                p=p,
                binsize=bin,
                bw=bw,
                cutpoint=cutpoint,
                data=data.frame(cellmp,cellval)
               )
          )
  else if (htest) {
      # Return an htest object, for compatibility with base R test output.
      structure(list(
          statistic   = c(`z` = z),
          p.value     = p,
          method      = "McCrary (2008) sorting test",
          parameter   = c(`binwidth`  = bin,
                          `bandwidth` = bw,
                          `cutpoint`  = cutpoint),
          alternative = "no apparent sorting"),
          class = "htest")
  }
  else return(p)
}

```

`@sample_code`
```{r}
# 1) The dataframe `NBA` is in your workspace. You can get a quick sense of the variables and some of their values with the str() or head() functions:



# The R function DCdensity() will generate a density plot of our data, and we can pick what value we want for our RD cutoff. In this case, it makes the most sense for our cutoff to be a tie score at halftime: that will let us easily interpret the plot when the teams are very close in score at halftime. Like in our previous exercises, we will focus on the home teams to avoid the issue of different team performance at home versus on the road.

# 2) We are hoping that the plot shows a smooth curve on both sides of the cutoff, which is a signal that the units on either side of the cutoff are comparable. The x-axis will be our running variable (point differential at halftime), and the y-axis is our density estimate for that score differential. Now run the McCrary test with the correct running variable in the NBA data and the cutoff at 0, which indicates when the halftime score is tied. Insert the correct variable names into the placeholder spots below and look at the resulting plot. 

      DCdensity(NBA$[running.var],[cutoff],plot=TRUE)

  
# 3) Now issue the command again (again by inserting the correct variable names in the placeholder spots), but print the p-value output for the McCrary test. Remember, if the p-value for the McCrary test is less than or equal to .05, then we can be 95% percent sure that there is manipulation going on in the data. If the p-value of the McCrary test is above .05 (especially if it is well above .05), then we can be pretty sure that there is no manipulation going on. You can easily print the p-value in R by simply wrapping the correctly filled DCdensity() function with the print() function:

      print(DCdensity(NBA$[running.var],[cutoff],plot=FALSE))
      

# 4) Based on the shape of the plot and the p value of the Mcrary test, would you say that we can run a valid Regression Discontinuity analysis on this data? Answer "Yes" or "No".
      
      Solution4 <- ""
      

# Good job. So we've been looking at our historical data from the NBA, but we also have just gotten access to a new, additional dataset about more recent games. These new results have come in after the research was published in the journal Management Science. Does it show that the teams have read the paper and are now trying to be the team that is losing at halftime? Let's find out by looking at the McCrary test results for the variable `home.team.halftime.margin.newdata`.
      
# 5) Let's first plot with the DCdensity function using the variable `home.team.halftime.margin.newdata` which is data from the most recent NBA season. Does it look any different than the previous data?

      DCdensity(NBA$[new.running.var],[cutoff],plot=TRUE)
      

# 6) Interesting: it looks like there is now big outlier near the cutoff of 0. But is this statistically signficant? Let's find out by printing the p-value of this McCrary test to see how it compares to the p-value on our initial data. You can do this by simply wrapping the finished command with the print() function:
  
      print(DCdensity(NBA$[new.running.var],[cutoff],plot=FALSE))
      
      
# 7) Based on this second McCrary test plot and p-value on the current season's data, would you say that we can run a valid Regression Discontinuity analysis on this new data? Answer "Yes" or "No"

      Solution7<-""


```

`@solution`
```{r}
    DCdensity(NBA$home.team.halftime.margin,0,plot=TRUE)
    print(DCdensity(NBA$home.team.halftime.margin,0,plot=FALSE))
    Solution4<-"Yes"
    DCdensity(NBA$home.team.halftime.margin.newdata,0,plot=TRUE)
    print(DCdensity(NBA$home.team.halftime.margin.newdata,0,plot=FALSE))
    Solution7<-"No"
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution4") %>% check_equal()
ex() %>% check_object("Solution7") %>% check_equal()
success_msg("Good work! That outlier just below the cutoff looks like a clear sign that the teams are trying to be losing by about a point at halftime. In fact, the p-value is so small that it is nearly 0, and it's hard to be more obvious than that in statistics! But there's more work to be done before we make any conclusions.  The McCrary test cannot prove manipulation just by itself, but it's a very helpful indicator that we should look closer at the exact mechanics going on in these new NBA teams during their games.")
```

---

## "Fuzzy" Regression Discontinuity - Addressing Blurry Lines Between Groups

```yaml
type: VideoExercise
key: 3140530dac
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/218504968
```


---

## Practice Computing Effects with Regression Discontinuity

```yaml
type: NormalExercise
key: 6bf34a7275
lang: r
xp: 100
skills: 1
```

Let's continue with the NBA research example. On your workspace is a simulated data set, called `NBA`, that closely resembles the data analyzed by Berger and Pope. The data frame `NBA` contains game characteristics for over 18,000 NBA games between 1994 and 2009. Will you get the same results as they did? Let's find out!

The outcome variable we are interested in is called `home.team.final.margin`, which is the final margin of victory (or loss) for the home team. The running variable in this RDD is called `home.team.halftime.margin`, which records the scoring difference between the home and visiting teams at halftime. Let's keep things simple and take a look at when the home team is winning at halftime, and define our treatment variable as the home team being ahead at halftime, i.e. when `home.team.halftime.margin > 0`. 

In this exercise, you will compute the treatment effect of being ahead at halftime on the final margin of victory. You will use regression methods as well as nonparametric methods to assess how robust the effect is.

`@instructions`
- 1) Use OLS regression to estimate the treatment effect of being behind at halftime on the final margin of victory under two different parametric scenarios
- 2) Estimate the treatment effect using non-parametric methods

`@hint`


`@pre_exercise_code`
```{r}
# require(rdd)

set.seed(1)
n <- 18060

# Initialize dataframe
NBA <- as.data.frame(matrix(0, ncol=10,nrow=n))
colnames(NBA) <- c("id","season","home.team","away.team","home.team.qual","away.team.qual","home.team.halftime.score","away.team.halftime.score","home.team.final.margin","home.team.win")

# Simulate baseline data
NBA$id         <- seq(1,n,1)
NBA$season     <- ifelse(NBA$id %in% seq( 0*1204+1, 1*1204,1),1994,
                  ifelse(NBA$id %in% seq( 1*1204+1, 2*1204,1),1995,
                  ifelse(NBA$id %in% seq( 2*1204+1, 3*1204,1),1996,
                  ifelse(NBA$id %in% seq( 3*1204+1, 4*1204,1),1997,
                  ifelse(NBA$id %in% seq( 4*1204+1, 5*1204,1),1998,
                  ifelse(NBA$id %in% seq( 5*1204+1, 6*1204,1),1999,
                  ifelse(NBA$id %in% seq( 6*1204+1, 7*1204,1),2000,
                  ifelse(NBA$id %in% seq( 7*1204+1, 8*1204,1),2001,
                  ifelse(NBA$id %in% seq( 8*1204+1, 9*1204,1),2002,
                  ifelse(NBA$id %in% seq( 9*1204+1,10*1204,1),2003,
                  ifelse(NBA$id %in% seq(10*1204+1,11*1204,1),2004,
                  ifelse(NBA$id %in% seq(11*1204+1,12*1204,1),2005,
                  ifelse(NBA$id %in% seq(12*1204+1,13*1204,1),2006,
                  ifelse(NBA$id %in% seq(13*1204+1,14*1204,1),2007,
                  ifelse(NBA$id %in% seq(14*1204+1,15*1204,1),2008,0)))))))))))))))
teamqual <- cbind(c("BOS","NJN","NYK","PHL","GSW","LAC","LAL","PHX","SAC","CHI","CLE","DET","IND","MIL","DAL","HOU","MEM","SAS","ATL","CHA","MIA","ORL","WSH","DEN","MIN","SEA","POR","UTA"),
                  matrix(rnorm(28*15,mean=0,sd=1), ncol=15))
NBA$home.team      <- sample(teamqual[,1],n,replace=TRUE)
NBA$away.team      <- sample(teamqual[,1],n,replace=TRUE)
print(paste0('Number of teams playing themselves: ',sum(NBA$home.team==NBA$away.team)/n*100,'%'))
for (i in 1:n) {
    if (NBA$home.team[i]==NBA$away.team[i]) {
        NBA$away.team[i] <- sample(setdiff(teamqual[,1],NBA$home.team[i]),1)
    }
}
print(paste0('Number of teams playing themselves: ',sum(NBA$home.team==NBA$away.team)/n*100,'%'))

# generate team qualities to explain outcomes for each game
for (i in 1:n) {
    NBA$away.team.qual[i] <- as.numeric(teamqual[teamqual[,1]==NBA$away.team[i],NBA$season[i]-1992])
    NBA$home.team.qual[i] <- as.numeric(teamqual[teamqual[,1]==NBA$home.team[i],NBA$season[i]-1992])
}

NBA$home.team <- as.factor(NBA$home.team)
NBA$away.team <- as.factor(NBA$away.team)

# Generate halftime scores
NBA$home.team.halftime.score  <- round(NBA$home.team.qual+rnorm(n, mean=48, sd=4), digits=0)
NBA$away.team.halftime.score  <- round(NBA$away.team.qual+rnorm(n, mean=47, sd=6), digits=0)
NBA$home.team.halftime.margin <- NBA$home.team.halftime.score - NBA$away.team.halftime.score

# Remove games that are tied at halftime
print(dim(NBA))
NBA <- NBA[NBA$home.team.halftime.margin!=0,]
print(dim(NBA))
n1 <- dim(NBA)[1]

# Generate final score
NBA$home.team.winning.at.half <- NBA$home.team.halftime.margin>0
NBA$home.team.final.margin    <- round(2 - 5*NBA$home.team.winning.at.half + 2*NBA$home.team.halftime.margin -.05*NBA$home.team.halftime.margin^2 + NBA$home.team.qual - NBA$away.team.qual + rnorm(n1, mean=0, sd=10), digits=0)
NBA$home.team.win             <- NBA$home.team.final.margin>0

# Clean up data
NBA$season <- as.factor(NBA$season)
NBA <- NBA[,c("id","season","home.team","away.team","home.team.qual","away.team.qual","home.team.halftime.margin","home.team.final.margin","home.team.winning.at.half","home.team.win")]

#####################################################
#####################################################



#####################################################

bread <- function(x, ...)
{
  UseMethod("bread")
}

bread.lm <- function(x, ...)
{
  if(!is.null(x$na.action)) class(x$na.action) <- "omit"
  sx <- summary.lm(x)
  return(sx$cov.unscaled * as.vector(sum(sx$df[1:2])))
}

bread.mlm <- function(x, ...)
{
  if(!is.null(x$na.action)) class(x$na.action) <- "omit"
  sx <- summary.lm(x)
  rval <- diag(ncol(residuals(x))) %x% sx$cov.unscaled * as.vector(sum(sx$df[1:2]))
  colnames(rval) <- rownames(rval) <- colnames(vcov(x))
  return(rval)
}

bread.glm <- function(x, ...)
{
  if(!is.null(x$na.action)) class(x$na.action) <- "omit"
  sx <- summary(x)
  wres <- as.vector(residuals(x, "working")) * weights(x, "working")
  dispersion <- if(substr(x$family$family, 1, 17) %in% c("poisson", "binomial", "Negative Binomial")) 1
    else sum(wres^2)/sum(weights(x, "working"))
  return(sx$cov.unscaled * as.vector(sum(sx$df[1:2])) * dispersion)
}

bread.nls <- function(x, ...)
{
  if(!is.null(x$na.action)) class(x$na.action) <- "omit"
  sx <- summary(x)
  return(sx$cov.unscaled * as.vector(sum(sx$df[1:2])))
}

bread.polr <- function(x, ...)
{
  vcov(x) * x$n
}

bread.clm <- function(x, ...)
{
  vcov(x) * x$n
}

bread.survreg <- function(x, ...)
  length(x$linear.predictors) * x$var

bread.gam <- function(x, ...)
{
  if(!is.null(x$na.action)) class(x$na.action) <- "omit"
  sx <- summary(x)
  sx$cov.unscaled * sx$n
}
  
bread.coxph <- function(x, ...)
{
  rval <- x$var * x$n
  dimnames(rval) <- list(names(coef(x)), names(coef(x)))
  return(rval)

}

bread.hurdle <- function(x, ...)
{
  x$vcov * x$n
}

bread.zeroinfl <- function(x, ...)
{
  x$vcov * x$n
}

bread.mlogit <- function(x, ...)
{
  if(!is.null(x$na.action)) class(x$na.action) <- "omit"
  vcov(x) * length(residuals(x))
}

bread.rlm <- function(x, ...)
{
  if(!is.null(x$na.action)) class(x$na.action) <- "omit"
  xmat <- model.matrix(x)
  xmat <- naresid(x$na.action, xmat)
  wts <- weights(x)
  if(is.null(wts)) wts <- 1
  res <- residuals(x)
  psi_deriv <- function(z) x$psi(z, deriv = 1)
  rval <- sqrt(abs(as.vector(psi_deriv(res/x$s)/x$s))) * wts * xmat    
  rval <- chol2inv(qr.R(qr(rval))) * nrow(xmat)
  return(rval)
}


#####################################################

sandwich <- function(x, bread. = bread, meat. = meat, ...)
{
  if(is.list(x) && !is.null(x$na.action)) class(x$na.action) <- "omit"
  if(is.function(bread.)) bread. <- bread.(x)
  if(is.function(meat.)) meat. <- meat.(x, ...)
  n <- NROW(estfun(x))
  return(1/n * (bread. %*% meat. %*% bread.))
}

meat <- function(x, adjust = FALSE, ...)
{
  if(is.list(x) && !is.null(x$na.action)) class(x$na.action) <- "omit"
  psi <- estfun(x, ...)
  k <- NCOL(psi)
  n <- NROW(psi)
  rval <- crossprod(as.matrix(psi))/n
  if(adjust) rval <- n/(n-k) * rval
  rownames(rval) <- colnames(rval) <- colnames(psi)
  return(rval)
}

vcovOPG <- function(x, adjust = FALSE, ...)
{
  if(is.list(x) && !is.null(x$na.action)) class(x$na.action) <- "omit"
  psi <- estfun(x, ...)
  k <- NCOL(psi)
  n <- NROW(psi)
  rval <- chol2inv(qr.R(qr(psi)))
  if(adjust) rval <- n/(n-k) * rval
  rownames(rval) <- colnames(rval) <- colnames(psi)
  return(rval)
}


#####################################################

zoo <- function (x = NULL, order.by = index(x), frequency = NULL,
  calendar = getOption("zoo.calendar", TRUE)) 
{
    ## process index "order.by"    
    if(length(unique(MATCH(order.by, order.by))) < length(order.by))
      warning(paste("some methods for", dQuote("zoo"),
      "objects do not work if the index entries in", sQuote("order.by"), "are not unique"))
    index <- ORDER(order.by)
    order.by <- order.by[index]

    if(is.matrix(x) || is.data.frame(x)) x <- as.matrix(x)
    if(is.matrix(x) && sum(dim(x)) < 1L) x <- NULL
    if(missing(x) || is.null(x))
      x <- numeric()
    else if(is.factor(x))         
      x <- factor(rep(as.character(x), length.out = length(index))[index],
        levels = levels(x), ordered = is.ordered(x))
    else if(is.matrix(x) || is.data.frame(x)) 
      x <- (x[rep(1:NROW(x), length.out = length(index)), , 
        drop = FALSE])[index, , drop = FALSE]
    else if(is.atomic(x)) 
      x <- rep(x, length.out = length(index))[index]
    else stop(paste(dQuote("x"), ": attempt to define invalid zoo object"))

    if(!is.null(frequency)) {
      delta <- suppressWarnings(try(diff(as.numeric(order.by)), silent = TRUE))
      freqOK <- if(class(delta) == "try-error" || any(is.na(delta))) FALSE
        else if(length(delta) < 1) TRUE
        else identical(all.equal(delta*frequency, round(delta*frequency)), TRUE)
      if(!freqOK) {
        warning(paste(dQuote("order.by"), "and", dQuote("frequency"),
        	"do not match:", dQuote("frequency"), "ignored"))
        frequency <- NULL
      } else {
        if(frequency > 1 && identical(all.equal(frequency, round(frequency)), TRUE))
	  frequency <- round(frequency)
      }
      if(!is.null(frequency) && identical(class(order.by), "numeric") | identical(class(order.by), "integer")) {
        orig.order.by <- order.by
        order.by <- floor(frequency * order.by + .0001)/frequency
        if(!isTRUE(all.equal(order.by, orig.order.by))) order.by <- orig.order.by
	if(calendar && frequency %in% c(4, 12)) {
	  order.by <- if(frequency == 4) as.yearqtr(order.by) else as.yearmon(order.by)	
	}
      }
    }

    attr(x, "oclass") <- attr(x, "class")
    attr(x, "index") <- order.by
    attr(x, "frequency") <- frequency
    class(x) <- if(is.null(frequency)) "zoo" else c("zooreg", "zoo")
    return(x)
}

print.zoo <- function (x, style = ifelse(length(dim(x)) == 0,
    "horizontal", "vertical"), quote = FALSE, ...) 
{
    style <- match.arg(style, c("horizontal", "vertical", "plain"))
    if (is.null(dim(x)) && length(x) == 0) style <- "plain"
    if (length(dim(x)) > 0 && style == "horizontal") style <- "plain"
    if (style == "vertical") {
	y <- as.matrix(coredata(x))
        if (length(colnames(x)) < 1) {
            colnames(y) <- rep("", NCOL(x))
        }
		if (NROW(y) > 0) {
			rownames(y) <- index2char(index(x), frequency = attr(x, "frequency"))
		}
        print(y, quote = quote, ...)
    }
    else if (style == "horizontal") {
        y <- as.vector(x)
        names(y) <- index2char(index(x), frequency = attr(x, "frequency"))
        print(y, quote = quote, ...)
    }
    else {
        cat("Data:\n")
        print(coredata(x))
        cat("\nIndex:\n")
        print(index(x))
    }
    invisible(x)
}

summary.zoo <- function(object, ...) 
{
	y <- as.data.frame(object)
	if (length(colnames(object)) < 1) {
		lab <- deparse(substitute(object))
		colnames(y) <- if (NCOL(object) == 1) lab
		  else paste(lab, 1:NCOL(object), sep=".")
	}
	if (NROW(y) > 0) {
		summary(cbind(data.frame(Index = index(object)), y), ...)
	} else summary(data.frame(Index = index(object)), ...)
}


is.zoo <- function(object)
  inherits(object, "zoo")

str.zoo <- function(object, ...)
{
  cls <- if(inherits(object, "zooreg")) "zooreg" else "zoo"
  if(NROW(object) < 1) cat(paste(sQuote(cls), "series (without observations)\n")) else {
    cat(paste(sQuote(cls), " series from ", start(object), " to ", end(object), "\n", sep = ""))
    cat("  Data:")
    str(coredata(object), ...)
    cat("  Index: ")
    str(index(object), ...)
    if(cls == "zooreg") cat(paste("  Frequency:", attr(object, "frequency"), "\n"))
  }
}

"[.zoo" <- function(x, i, j, drop = TRUE, ...)
{
  if(!is.zoo(x)) stop("method is only for zoo objects")
  rval <- coredata(x)
  n <- NROW(rval)
  n2 <- if(nargs() == 1) length(as.vector(rval)) else n
  if(missing(i)) i <- 1:n

  if (all(class(i) == "matrix")) i <- as.vector(i)
  ## also support that i can be index:
  ## if i is not numeric/integer/logical, it is interpreted to be the index
  if (all(class(i) == "logical"))
    i <- which(rep(i, length.out = n2))
  else if (inherits(i, "zoo") && all(class(coredata(i)) == "logical")) {
    i <- which(coredata(merge(zoo(,time(x)), i)))
  } else if(!((all(class(i) == "numeric") || all(class(i) == "integer")))) 
    i <- which(MATCH(index(x), i, nomatch = 0L) > 0L)
  
  if(length(dim(rval)) == 2) {
    drop. <- if (length(i) == 1) FALSE else drop
    rval <- if (missing(j)) rval[i, , drop = drop., ...]
      else rval[i, j, drop = drop., ...]
    if (drop && length(rval) == 1) rval <- c(rval)
    rval <- zoo(rval, index(x)[i])
  } else
    rval <- zoo(rval[i], index(x)[i])

  attr(rval, "oclass") <- attr(x, "oclass")
  attr(rval, "levels") <- attr(x, "levels")
  attr(rval, "frequency") <- attr(x, "frequency")
  if(!is.null(attr(rval, "frequency"))) class(rval) <- c("zooreg", class(rval))

  return(rval)
}

"[<-.zoo" <- function (x, i, j, value) 
{
  ## x[,j] <- value and x[] <- value can be handled by default method
  if(missing(i)) return(NextMethod("[<-"))

  ## otherwise do the necessary processing on i
  n <- NROW(coredata(x))
  n2 <- if(nargs() == 1) length(as.vector(coredata(x))) else n
  n.ok <- TRUE
  value2 <- NULL
  
  if (all(class(i) == "matrix")) i <- as.vector(i)
  if (all(class(i) == "logical")) {
    if (length(i) == n) {
		i <- which(i)
		n.ok <- TRUE
	} else {
		i <- which(rep(i, length.out = n))
		n.ok <- all(i <= n2)
	}
  } else if (inherits(i, "zoo") && all(class(coredata(i)) == "logical")) {
    i <- which(coredata(merge(zoo(,time(x)), i)))
    n.ok <- all(i <= n2)
  } else if(!((all(class(i) == "numeric") || all(class(i) == "integer")))) {
    ## all time indexes in index(x)?
    i.ok <- MATCH(i, index(x), nomatch = 0L) > 0L
    if(any(!i.ok)) {
      if(is.null(dim(value))) {
        value2 <- value[!i.ok]
        value <- value[i.ok]
      } else {
        value2 <- value[!i.ok,, drop = FALSE]
        value <- value[i.ok,, drop = FALSE]      
      }
      i2 <- i[!i.ok]
      i <- i[i.ok]
    }
    i <- which(MATCH(index(x), i, nomatch = 0L) > 0L)
    n.ok <- all(i <= n2)
  }
  if(!n.ok | any(i < 1)) stop("Out-of-range assignment not possible.")
  rval <- NextMethod("[<-")

  if(!is.null(value2)) {
    rval2 <- if(missing(j)) zoo(value2, i2) else {
      value2a <- matrix(NA, nrow = length(i2), ncol = NCOL(rval))
      colnames(value2a) <- colnames(rval)
      value2a[, j] <- value2
      zoo(value2a, i2)
    }
    rval <- c(rval, rval2)
  }
  return(rval)
}

"$.zoo" <- function(object, x) {
  if(length(dim(object)) != 2) stop("not possible for univariate zoo series")
  if(is.null(colnames(object))) stop("only possible for zoo series with column names")
  wi <- pmatch(x, colnames(object))
  if(is.na(wi)) NULL else object[, wi]
}

"$<-.zoo" <- function(object, x, value) {
  if(length(object) == 0L) {
    is.plain <- function(x)
      all(class(x) %in% c("array", "integer", "numeric", "factor", "matrix", "logical"))
    if(is.plain(value)) value <- zoo(value,
      if(length(index(object))) index(object) else seq_along(value), attr(object, "frequency"))
    return(setNames(merge(object, value, drop = FALSE), x))
  }
  if(length(dim(object)) != 2) stop("not possible for univariate zoo series")
  if(NCOL(object) > 0L & is.null(colnames(object))) stop("only possible for zoo series with column names")
  wi <- match(x, colnames(object))
  if(is.na(wi)) {
    if(!is.null(value)) {
      object <- cbind(object, value)
      if(is.null(dim(object))) dim(object) <- c(length(object), 1)
      colnames(object)[NCOL(object)] <- x  
    }
  } else {
    if(is.null(value)) {
      object <- object[, -wi, drop = FALSE]
    } else {   
      object[, wi] <- value
    }
  }
  object
}

head.zoo <- function(x, n = 6, ...) {
	stopifnot(length(n) == 1L)
	xlen <- NROW(x)
    n <- if (n < 0L) 
        max(NROW(x) + n, 0L)
    else min(n, xlen)
	if (length(dim(x)) == 0) x[seq_len(n)]
	else x[seq_len(n),, drop = FALSE]
}
 
tail.zoo <- function(x, n = 6, ...) {
    stopifnot(length(n) == 1L)
    xlen <- NROW(x)
    n <- if (n < 0L) 
        max(xlen + n, 0L)
    else min(n, xlen)
	if (length(dim(x)) == 0) x[seq.int(to = xlen, length.out = n)]
	else x[seq.int(to = xlen, length.out = n),, drop = FALSE]
}

range.zoo <- function(..., na.rm = FALSE)
    range(sapply(list(...), coredata), na.rm = na.rm)


scale.zoo <- function (x, center = TRUE, scale = TRUE) {
	x[] <- xs <- scale(coredata(x), center = center, scale = scale)
	attributes(x) <- c(attributes(x), attributes(xs))
	x
}

with.zoo <- function(data, expr, ...) {
    stopifnot(length(dim(data)) == 2)
    eval(substitute(expr), as.list(data), enclos = parent.frame())
}

xtfrm.zoo <- function(x) coredata(x)

subset.zoo <- function (x, subset, select, drop = FALSE, ...) 
{
    if (missing(select)) 
        vars <- TRUE
    else {
        nl <- as.list(1:ncol(x))
        names(nl) <- colnames(x)
        vars <- eval(substitute(select), nl, parent.frame())
    }
    if (missing(subset)) {
        subset <- rep(TRUE, NROW(x))
    } else {
        e <- substitute(subset)
	if("time" %in% colnames(x)) {
	  xdf <- as.data.frame(x)
          subset <- eval(e, xdf, parent.frame())
          xdf$time <- time(x)
          subset2 <- eval(e, xdf, parent.frame())
	  if(!identical(subset, subset2))
  	      warning("'time' is a column in 'x' (not the time index)")
	} else {
          subset <- eval(e, cbind(as.data.frame(x), time = time(x)), parent.frame())
	}
        if (!is.logical(subset)) stop("'subset' must be logical")
    }
    x[subset & !is.na(subset), vars, drop = drop]
}

names.zoo <- function(x) {
  cx <- coredata(x)
  if(is.matrix(cx)) colnames(cx) else names(cx)
}

"names<-.zoo" <- function(x, value) {
  if(is.matrix(coredata(x))) {
    colnames(x) <- value
  } else {
    names(coredata(x)) <- value
  }
  x
}

rev.zoo <- function(x) {
  ix <- rev(ORDER(time(x)))
  zoo(coredata(x), time(x)[ix])
}

ifelse.zoo <- function(test, yes, no) {
	if(!is.zoo(test)) test <- zoo(test, index(yes))
	merge(test, yes, no, retclass = NULL)
	ifelse(test, yes, no)
}

mean.zoo <- function(x, ...)  mean(coredata(x), ...)

median.zoo <- if(getRversion() <= "3.3.3") {
  function(x, na.rm = FALSE) median(coredata(x), na.rm = na.rm)
} else {
  function(x, na.rm = FALSE, ...) median(coredata(x), na.rm = na.rm, ...)
}

quantile.zoo <- function(x, ...) quantile(coredata(x), ...)

transform.zoo <- function(`_data`, ...)
{
  ## zoo series elements
  if(is.null(dim(coredata(`_data`)))) warning("transform() is only useful for matrix-based zoo series")
  ix <- index(`_data`)
  freq <- attr(`_data`, "frequency")
  `_data` <- as.data.frame(`_data`)

  ## get transformations
  e <- eval(substitute(list(...)), `_data`, parent.frame())
  trafo <- names(e)
  inx <- match(trafo, names(`_data`))
  matched <- !is.na(inx)

  ## evaluate transformations
  if(any(matched)) {
    `_data`[inx[matched]] <- e[matched]
    `_data` <- data.frame(`_data`)
  }
  if (!all(matched)) 
    `_data` <- do.call("data.frame", c(list(`_data`), e[!matched]))

  ## return zoo
  zoo(`_data`, ix, freq)
}

`dim<-.zoo` <- function(x, value) {
  d <- dim(x)
  l <- length(x)
  ok <- isTRUE(all.equal(d, value)) ||                                  ## no change
    (is.null(d) && l == 0L && all(value == c(length(index(x)), 0L))) || ## zero-length vector -> 0-column matrix
    (is.null(d) && l > 0L && all(value == c(l, 1L))) ||                 ## positive-length vector -> 1-column matrix
    (!is.null(d) && d[2L] <= 1L && is.null(value))                      ## 0- or 1-column matrix -> vector
  if(!ok) warning("setting this dimension may lead to an invalid zoo object")
  NextMethod()
}


#################################################

estfun <- function(x, ...)
{
  UseMethod("estfun")
}

estfun.lm <- function(x, ...)
{
  xmat <- model.matrix(x)
  xmat <- naresid(x$na.action, xmat)
  if(any(alias <- is.na(coef(x)))) xmat <- xmat[, !alias, drop = FALSE]
  wts <- weights(x)
  if(is.null(wts)) wts <- 1
  res <- residuals(x)
  rval <- as.vector(res) * wts * xmat
  attr(rval, "assign") <- NULL
  attr(rval, "contrasts") <- NULL
  if(is.zoo(res)) rval <- zoo(rval, index(res), attr(res, "frequency"))
  if(is.ts(res)) rval <- ts(rval, start = start(res), frequency = frequency(res))
  return(rval)
}

estfun.mlm <- function(x, ...)
{
  xmat <- model.matrix(x)
  xmat <- naresid(x$na.action, xmat)
  wts <- weights(x)
  if(is.null(wts)) wts <- 1
  res <- residuals(x)
  cf <- coef(x)
  rval <- lapply(1:NCOL(res), function(i) {
    rv <- as.vector(res[,i]) * wts * xmat
    colnames(rv) <- paste(colnames(cf)[i], colnames(rv), sep = ":")
    rv
  })  
  rval <- do.call("cbind", rval)
  attr(rval, "assign") <- NULL
  attr(rval, "contrasts") <- NULL
  if(any(alias <- is.na(as.vector(cf)))) rval <- rval[, !alias, drop = FALSE]
  if(is.zoo(res)) rval <- zoo(rval, index(res), attr(res, "frequency"))
  if(is.ts(res)) rval <- ts(rval, start = start(res), frequency = frequency(res))
  return(rval)
}

estfun.glm <- function(x, ...)
{
  xmat <- model.matrix(x)
  xmat <- naresid(x$na.action, xmat)
  if(any(alias <- is.na(coef(x)))) xmat <- xmat[, !alias, drop = FALSE]
  wres <- as.vector(residuals(x, "working")) * weights(x, "working")
  dispersion <- if(substr(x$family$family, 1, 17) %in% c("poisson", "binomial", "Negative Binomial")) 1
    else sum(wres^2, na.rm = TRUE)/sum(weights(x, "working"), na.rm = TRUE)
  rval <- wres * xmat / dispersion
  attr(rval, "assign") <- NULL
  attr(rval, "contrasts") <- NULL
  res <- residuals(x, type = "pearson")
  if(is.ts(res)) rval <- ts(rval, start = start(res), frequency = frequency(res))
  if(is.zoo(res)) rval <- zoo(rval, index(res), attr(res, "frequency"))
  return(rval)
}

estfun.rlm <- function(x, ...)
{
  xmat <- model.matrix(x)
  xmat <- naresid(x$na.action, xmat)
  wts <- weights(x)
  if(is.null(wts)) wts <- 1
  res <- residuals(x)
  psi <- function(z) x$psi(z) * z
  rval <- as.vector(psi(res/x$s)) * wts * xmat
  attr(rval, "assign") <- NULL
  attr(rval, "contrasts") <- NULL
  if(is.ts(res)) rval <- ts(rval, start = start(res), frequency = frequency(res))
  if(is.zoo(res)) rval <- zoo(rval, index(res), attr(res, "frequency"))
  return(rval)
}

estfun.polr <- function(x, ...)
{
  ## link processing
  mueta <- x$method
  if(mueta == "logistic") mueta <- "logit"
  mueta <- make.link(mueta)$mu.eta
  
  ## observations
  xmat <- model.matrix(x)[, -1L, drop = FALSE]
  n <- nrow(xmat)
  k <- ncol(xmat)
  m <- length(x$zeta)
  mf <- model.frame(x)
  y <- as.numeric(model.response(mf))
  w <- model.weights(mf)
  if(is.null(w)) w <- rep(1, n)

  ## estimates  
  prob <- x$fitted.values[cbind(1:n, y)]
  xb <- if(k >= 1L) as.vector(xmat %*% x$coefficients) else rep(0, n)
  zeta <- x$zeta
  lp <- cbind(0, mueta(matrix(zeta, nrow = n, ncol = m, byrow = TRUE) - xb), 0)

  ## estimating functions
  rval <- matrix(0, nrow = n, ncol = k + m + 2L)
  if(k >= 1L) rval[, 1L:k] <- (-xmat * as.vector(lp[cbind(1:n, y + 1L)] - lp[cbind(1:n, y)]))
  rval[cbind(1:n, k + y)] <- -as.vector(lp[cbind(1:n, y)])
  rval[cbind(1:n, k + y + 1L)] <- as.vector(lp[cbind(1:n, y + 1L)])
  rval <- rval[, -c(k + 1L, k + m + 2L), drop = FALSE]
  rval <- w/prob * rval

  ## dimnames and return
  dimnames(rval) <- list(rownames(xmat), c(colnames(xmat), names(x$zeta)))
  return(rval)
}

###########################


estfun.clm <- function(x, ...)
{
  if(x$threshold != "flexible") stop("only flexible thresholds implemented at the moment")

  ## link processing
  mueta <- make.link(x$link)$mu.eta
  
  ## observations
  xmat <- model.matrix(x)
  if(length(xmat) > 1L) stop("estimating functions for scale regression not implemented yet")
  xmat <- xmat$X[, -1L, drop = FALSE]
  n <- nrow(xmat)
  k <- ncol(xmat)
  m <- length(x$alpha)
  mf <- model.frame(x)
  y <- as.numeric(model.response(mf))
  w <- model.weights(mf)
  if(is.null(w)) w <- rep(1, n)

  ## estimates  
  prob <- x$fitted.values
  xb <- if(k >= 1L) as.vector(xmat %*% x$beta) else rep(0, n)
  zeta <- x$alpha
  lp <- cbind(0, mueta(matrix(zeta, nrow = n, ncol = m, byrow = TRUE) - xb), 0)

  ## estimating functions
  rval <- matrix(0, nrow = n, ncol = k + m + 2L)
  if(k >= 1L) rval[, 1L:k] <- (-xmat * as.vector(lp[cbind(1:n, y + 1L)] - lp[cbind(1:n, y)]))
  rval[cbind(1:n, k + y)] <- -as.vector(lp[cbind(1:n, y)])
  rval[cbind(1:n, k + y + 1L)] <- as.vector(lp[cbind(1:n, y + 1L)])
  rval <- rval[, -c(k + 1L, k + m + 2L), drop = FALSE]
  rval <- w/prob * rval

  ## dimnames, re-order and return
  dimnames(rval) <- list(rownames(xmat), c(colnames(xmat), names(x$alpha)))
  ix <- if(k >= 1L) c((k + 1L):(k + m), 1L:k) else 1L:m
  return(rval[, ix, drop = FALSE])
}

estfun.coxph <- function(x, ...)
{
  wts <- x$weights
  if(is.null(wts)) wts <- 1
  wts * residuals(x, type = "score", ...)
}

estfun.survreg <- function(x, ...)
{
  mf <- model.frame(x)
  xmat <- model.matrix(terms(x), mf)
  wts <- model.weights(mf)
  if(is.null(wts)) wts <- 1
  res <- residuals(x, type = "matrix")
  rval <- as.vector(res[,"dg"]) * wts * xmat
  if(NROW(x$var) > length(coef(x))) {
    rval <- cbind(rval, res[,"ds"])
    colnames(rval)[NCOL(rval)] <- "Log(scale)"
  }
  attr(rval, "assign") <- NULL
  
  return(rval)
}

estfun.nls <- function(x, ...)
{
  rval <- as.vector(x$m$resid()) * x$m$gradient()
  colnames(rval) <- names(coef(x))
  rval
}

estfun.hurdle <- function(x, ...) {
  ## extract data
  Y <- if(is.null(x$y)) model.response(model.frame(x)) else x$y
  X <- model.matrix(x, model = "count")
  Z <- model.matrix(x, model = "zero")
  beta <- coef(x, model = "count")
  gamma <- coef(x, model = "zero")
  fulltheta <- x$theta

  offset <- x$offset
  if(is.list(offset)) {
    offsetx <- offset$count
    offsetz <- offset$zero
  } else {
    offsetx <- offset
    offsetz <- NULL
  }
  if(is.null(offsetx)) offsetx <- 0
  if(is.null(offsetz)) offsetz <- 0
  if(x$dist$zero == "binomial") linkobj <- make.link(x$link)
  wts <- weights(x)
  if(is.null(wts)) wts <- 1
  Y1 <- Y > 0

  ## count component: working residuals
  eta <- as.vector(X %*% beta + offsetx)
  mu <- exp(eta)
  theta <- fulltheta["count"]

  wres_count <- as.numeric(Y > 0) * switch(x$dist$count,
    "poisson" = {
      (Y - mu) - exp(ppois(0, lambda = mu, log.p = TRUE) -
        ppois(0, lambda = mu, lower.tail = FALSE, log.p = TRUE) + eta)    
    },
    "geometric" = {
      (Y - mu * (Y + 1)/(mu + 1)) - exp(pnbinom(0, mu = mu, size = 1, log.p = TRUE) -
        pnbinom(0, mu = mu, size = 1, lower.tail = FALSE, log.p = TRUE) - log(mu + 1) + eta)
    },
    "negbin" = {
      (Y - mu * (Y + theta)/(mu + theta)) - exp(pnbinom(0, mu = mu, size = theta, log.p = TRUE) -
        pnbinom(0, mu = mu, size = theta, lower.tail = FALSE, log.p = TRUE) +
	log(theta) - log(mu + theta) + eta)
    })
  
  ## zero component: working residuals
  eta <- as.vector(Z %*% gamma + offsetz)
  mu <- if(x$dist$zero == "binomial") linkobj$linkinv(eta) else exp(eta)
  theta <- fulltheta["zero"]

  wres_zero <- switch(x$dist$zero,
    "poisson" = {
      ifelse(Y1, exp(ppois(0, lambda = mu, log.p = TRUE) -
        ppois(0, lambda = mu, lower.tail = FALSE, log.p = TRUE) + eta), -mu)
    },
    "geometric" = {
      ifelse(Y1, exp(pnbinom(0, mu = mu, size = 1, log.p = TRUE) -
        pnbinom(0, mu = mu, size = 1, lower.tail = FALSE, log.p = TRUE) - log(mu + 1) + eta), -mu/(mu + 1))
    },
    "negbin" = {
      ifelse(Y1, exp(pnbinom(0, mu = mu, size = theta, log.p = TRUE) -
        pnbinom(0, mu = mu, size = theta, lower.tail = FALSE, log.p = TRUE) +
        log(theta) - log(mu + theta) + eta), -mu * theta/(mu + theta))
    },
    "binomial" = {
      ifelse(Y1, 1/mu, -1/(1-mu)) * linkobj$mu.eta(eta)
    })

  ## compute gradient from data
  rval <- cbind(wres_count * wts * X, wres_zero * wts * Z)
  colnames(rval) <- names(coef(x))
  rownames(rval) <- rownames(X)
  return(rval)
}

estfun.zeroinfl <- function(x, ...) {
  ## extract data
  Y <- if(is.null(x$y)) model.response(model.frame(x)) else x$y
  X <- model.matrix(x, model = "count")
  Z <- model.matrix(x, model = "zero")
  beta <- coef(x, model = "count")
  gamma <- coef(x, model = "zero")
  theta <- x$theta

  offset <- x$offset
  if(is.list(offset)) {
    offsetx <- offset$count
    offsetz <- offset$zero
  } else {
    offsetx <- offset
    offsetz <- NULL
  }
  if(is.null(offsetx)) offsetx <- 0
  if(is.null(offsetz)) offsetz <- 0
  linkobj <- make.link(x$link)
  wts <- weights(x)
  if(is.null(wts)) wts <- 1
  Y1 <- Y > 0

  eta <- as.vector(X %*% beta + offsetx)
  mu <- exp(eta)
  etaz <- as.vector(Z %*% gamma + offsetz)
  muz <- linkobj$linkinv(etaz)

  ## density for y = 0
  clogdens0 <- switch(x$dist,
    "poisson" = -mu,
    "geometric" = dnbinom(0, size = 1, mu = mu, log = TRUE),
    "negbin" = dnbinom(0, size = theta, mu = mu, log = TRUE))
  dens0 <- muz * (1 - as.numeric(Y1)) + exp(log(1 - muz) + clogdens0)

  ## working residuals  
  wres_count <- switch(x$dist,
    "poisson" = ifelse(Y1, Y - mu, -exp(-log(dens0) + log(1 - muz) + clogdens0 + log(mu))),
    "geometric" = ifelse(Y1, Y - mu * (Y + 1)/(mu + 1), -exp(-log(dens0) +
      log(1 - muz) + clogdens0 - log(mu + 1) + log(mu))),
    "negbin" = ifelse(Y1, Y - mu * (Y + theta)/(mu + theta), -exp(-log(dens0) +
      log(1 - muz) + clogdens0 + log(theta) - log(mu + theta) + log(mu))))
  wres_zero <- ifelse(Y1, -1/(1-muz) * linkobj$mu.eta(etaz),
    (linkobj$mu.eta(etaz) - exp(clogdens0) * linkobj$mu.eta(etaz))/dens0)

  ## compute gradient from data
  rval <- cbind(wres_count * wts * X, wres_zero * wts * Z)
  colnames(rval) <- names(coef(x))
  rownames(rval) <- rownames(X)
  return(rval)
}

estfun.mlogit <- function(x, ...)
{
  x$gradient
}

##########################################

vcovHC <- function(x, ...) {
  UseMethod("vcovHC")
}

vcovHC.default <- function(x, 
  type = c("HC3", "const", "HC", "HC0", "HC1", "HC2", "HC4", "HC4m", "HC5"),
  omega = NULL, sandwich = TRUE, ...)
{
  type <- match.arg(type)
  rval <- meatHC(x, type = type, omega = omega)
  if(sandwich) rval <- sandwich(x, meat = rval, ...)
  return(rval)
}

meatHC <- function(x, 
  type = c("HC3", "const", "HC", "HC0", "HC1", "HC2", "HC4", "HC4m", "HC5"),
  omega = NULL)
{
  ## ensure that NAs are omitted
  if(is.list(x) && !is.null(x$na.action)) class(x$na.action) <- "omit"

  ## extract X
  X <- model.matrix(x)
  if(any(alias <- is.na(coef(x)))) X <- X[, !alias, drop = FALSE]
  attr(X, "assign") <- NULL
  n <- NROW(X)

  ## get hat values and residual degrees of freedom
  diaghat <- try(hatvalues(x), silent = TRUE)
  df <- n - NCOL(X)
  
  ## the following might work, but "intercept" is also claimed for "coxph"
  ## res <- if(attr(terms(x), "intercept") > 0) estfun(x)[,1] else rowMeans(estfun(x)/X, na.rm = TRUE)
  ## hence better rely on
  ef <- estfun(x)
  res <- rowMeans(ef/X, na.rm = TRUE)
  ## handle rows with just zeros
  res[apply(abs(ef) < .Machine$double.eps, 1L, all)] <- 0
  
  ## if omega not specified, set up using type
  if(is.null(omega)) {
    type <- match.arg(type)
    if(type == "HC") type <- "HC0"
    switch(type,
      "const" = { omega <- function(residuals, diaghat, df) rep(1, length(residuals)) * sum(residuals^2)/df },
      "HC0"   = { omega <- function(residuals, diaghat, df) residuals^2 },
      "HC1"   = { omega <- function(residuals, diaghat, df) residuals^2 * length(residuals)/df },
      "HC2"   = { omega <- function(residuals, diaghat, df) residuals^2 / (1 - diaghat) },
      "HC3"   = { omega <- function(residuals, diaghat, df) residuals^2 / (1 - diaghat)^2 },
      "HC4"   = { omega <- function(residuals, diaghat, df) {
        n <- length(residuals)
	p <- as.integer(round(sum(diaghat),  digits = 0))
	delta <- pmin(4, n * diaghat/p)
        residuals^2 / (1 - diaghat)^delta
      }},
      "HC4m"  = { omega <- function(residuals, diaghat, df) {
        gamma <- c(1.0, 1.5) ## as recommended by Cribari-Neto & Da Silva
        n <- length(residuals)
	p <- as.integer(round(sum(diaghat),  digits = 0))
	delta <- pmin(gamma[1], n * diaghat/p) + pmin(gamma[2], n * diaghat/p)
        residuals^2 / (1 - diaghat)^delta
      }},
      "HC5"   = { omega <- function(residuals, diaghat, df) {
        k <- 0.7 ## as recommended by Cribari-Neto et al.
        n <- length(residuals)
	p <- as.integer(round(sum(diaghat),  digits = 0))
	delta <- pmin(n * diaghat/p, pmax(4, n * k * max(diaghat)/p))
        residuals^2 / sqrt((1 - diaghat)^delta)
      }}
    )
  }
  
  ## process omega
  if(is.function(omega)) omega <- omega(res, diaghat, df)
  rval <- sqrt(omega) * X
  rval <- crossprod(rval)/n

  return(rval)
}

vcovHC.mlm <- function(x, 
  type = c("HC3", "const", "HC", "HC0", "HC1", "HC2", "HC4", "HC4m", "HC5"),
  omega = NULL, sandwich = TRUE, ...)
{
  ## compute meat "by hand" because meatHC() can not deal with
  ## residual "matrices"
  
  ## ensure that NAs are omitted
  if(is.list(x) && !is.null(x$na.action)) class(x$na.action) <- "omit"

  ## regressors, df, hat values
  X <- model.matrix(x)
  attr(X, "assign") <- NULL
  if(any(alias <- apply(coef(x), 1, function(z) all(is.na(z))))) X <- X[, !alias, drop = FALSE]
  n <- NROW(X)
  diaghat <- hatvalues(x)
  df <- n - NCOL(X)

  ## residuals
  res <- residuals(x)
 
  ## if omega not specified, set up using type
  if(is.null(omega)) {
    type <- match.arg(type)
    if(type == "HC") type <- "HC0"
    switch(type,
      "const" = { omega <- function(residuals, diaghat, df) rep(1, length(residuals)) * sum(residuals^2)/df },
      "HC0"   = { omega <- function(residuals, diaghat, df) residuals^2 },
      "HC1"   = { omega <- function(residuals, diaghat, df) residuals^2 * length(residuals)/df },
      "HC2"   = { omega <- function(residuals, diaghat, df) residuals^2 / (1 - diaghat) },
      "HC3"   = { omega <- function(residuals, diaghat, df) residuals^2 / (1 - diaghat)^2 },
      "HC4"   = { omega <- function(residuals, diaghat, df) {
        n <- length(residuals)
	p <- as.integer(round(sum(diaghat),  digits = 0))
	delta <- pmin(4, n * diaghat/p)
        residuals^2 / (1 - diaghat)^delta
      }},
      "HC4m"  = { omega <- function(residuals, diaghat, df) {
        gamma <- c(1.0, 1.5)
        n <- length(residuals)
	p <- as.integer(round(sum(diaghat),  digits = 0))
	delta <- pmin(gamma[1], n * diaghat/p) + pmin(gamma[2], n * diaghat/p)
        residuals^2 / (1 - diaghat)^delta
      }},
      "HC5"   = { omega <- function(residuals, diaghat, df) {
        k <- 0.7
        n <- length(residuals)
	p <- as.integer(round(sum(diaghat),  digits = 0))
	delta <- pmin(n * diaghat/p, pmax(4, n * k * max(diaghat)/p))
        residuals^2 / sqrt((1 - diaghat)^delta)
      }}
    )
  }
  
  ## process omega
  omega <- apply(res, 2, function(r) omega(r, diaghat, df))

  ## compute crossproduct X' Omega X
  rval <- lapply(1:ncol(omega), function(i) as.vector(sqrt(omega[,i])) * X)
  rval <- do.call("cbind", rval)
  rval <- crossprod(rval)/n
  colnames(rval) <- rownames(rval) <- colnames(vcov(x))

  ## if necessary compute full sandwich
  if(sandwich) rval <- sandwich(x, meat = rval, ...)
  return(rval)
}

###################################################

coeftest <- function(x, vcov. = NULL, df = NULL, ...)
{
  UseMethod("coeftest")
}

coeftest.default <- function(x, vcov. = NULL, df = NULL, ...)
{
  ## use S4 methods if loaded
  coef0 <- if("stats4" %in% loadedNamespaces()) stats4::coef else coef
  vcov0 <- if("stats4" %in% loadedNamespaces()) stats4::vcov else vcov

  ## extract coefficients and standard errors
  est <- coef0(x)
  if(is.null(vcov.)) se <- vcov0(x) else {
      if(is.function(vcov.)) se <- vcov.(x, ...)
        else se <- vcov.
  }
  se <- sqrt(diag(se))

  ## match using names and compute t/z statistics
  if(!is.null(names(est)) && !is.null(names(se))) {
    if(length(unique(names(est))) == length(names(est)) && length(unique(names(se))) == length(names(se))) {
      anames <- names(est)[names(est) %in% names(se)]
      est <- est[anames]
      se <- se[anames]
    }
  }  
  tval <- as.vector(est)/se

  ## apply central limit theorem
  if(is.null(df)) {
    df <- try(df.residual(x), silent = TRUE)
    if(inherits(df, "try-error")) df <- NULL
  }
  if(is.null(df)) df <- 0

  if(is.finite(df) && df > 0) {
    pval <- 2 * pt(abs(tval), df = df, lower.tail = FALSE)
    cnames <- c("Estimate", "Std. Error", "t value", "Pr(>|t|)")
    mthd <- "t"
  } else {
    pval <- 2 * pnorm(abs(tval), lower.tail = FALSE)
    cnames <- c("Estimate", "Std. Error", "z value", "Pr(>|z|)")
    mthd <- "z"
  }
  rval <- cbind(est, se, tval, pval)
  colnames(rval) <- cnames
  class(rval) <- "coeftest"
  attr(rval, "method") <- paste(mthd, "test of coefficients")
  ##  dQuote(class(x)[1]), "object", sQuote(deparse(substitute(x))))
  return(rval)
} 

coeftest.glm <- function(x, vcov. = NULL, df = Inf, ...)
  coeftest.default(x, vcov. = vcov., df = df, ...)  

coeftest.mlm <- function(x, vcov. = NULL, df = NULL, ...)
{
  ## obtain vcov
  v <- if(is.null(vcov.)) vcov(x) else if(is.function(vcov.)) vcov.(x) else vcov.

  ## nasty hack: replace coefficients so that their names match the vcov() method
  x$coefficients <- structure(as.vector(x$coefficients), .Names = colnames(vcov(x)))

  ## call default method
  coeftest.default(x, vcov. = v, df = df, ...)
}

coeftest.survreg <- function(x, vcov. = NULL, df = Inf, ...)
{
  if(is.null(vcov.)) v <- vcov(x) else {
      if(is.function(vcov.)) v <- vcov.(x)
  	else v <- vcov.
  }
  if(length(x$coefficients) < NROW(x$var)) {
    x$coefficients <- c(x$coefficients, "Log(scale)" = log(x$scale))
  }
  coeftest.default(x, vcov. = v, df = df, ...)  
} 

coeftest.breakpointsfull <- function(x, vcov. = NULL, df = NULL, ...)
{
  est <- coef(x, ...)
  if(is.null(df)) {
    df <- df.residual(x, ...)
    df <- as.vector(rep(df, rep(NCOL(est), length(df))))
  }  

  rnames <- as.vector(t(outer(rownames(est), colnames(est), paste)))
  est <- as.vector(t(est))
  
  se <- vcov(x, vcov. = vcov., ...)

  se <- as.vector(sapply(seq_along(se), function(x) sqrt(diag(se[[x]]))))
  tval <- est/se

  if(any(is.finite(df) && df > 0)) {
    pval <- 2 * pt(abs(tval), df = df, lower.tail = FALSE)
    cnames <- c("Estimate", "Std. Error", "t value", "Pr(>|t|)")
    mthd <- "t"
  } else {
    pval <- 2 * pnorm(abs(tval), lower.tail = FALSE)
    cnames <- c("Estimate", "Std. Error", "z value", "Pr(>|z|)")
    mthd <- "z"
  }
  rval <- cbind(est, se, tval, pval)
  colnames(rval) <- cnames
  rownames(rval) <- rnames
  class(rval) <- "coeftest"
  attr(rval, "method") <- paste(mthd, "test of coefficients")
  ##  dQuote(class(x)[1]), "object", sQuote(deparse(substitute(x))))
  return(rval)
} 

print.coeftest <- function(x, ...)
{
  mthd <- attr(x, "method")
  if(is.null(mthd)) mthd <- "Test of coefficients"
  cat(paste("\n", mthd,":\n\n", sep = ""))
  printCoefmat(x, ...)
  cat("\n")
  invisible(x)
}

##########################################################

Formula <- function(object) {

  stopifnot(inherits(object, "formula"))

  object_split <- split_formula(object)

  structure(object, lhs = object_split$lhs, rhs = object_split$rhs,
    class = c("Formula", "formula"))
}

as.Formula <- function(x, ...) UseMethod("as.Formula")

as.Formula.default <- function(x, ..., env = parent.frame()) Formula(as.formula(x, env = env))

as.Formula.Formula <- function(x, ...) x

as.Formula.formula <- function(x, ..., env) {

  ## preserve original environment
  if(missing(env)) env <- environment(x)

  ## combine all arguments to formula list
  x <- c(list(x), list(...))
  x <- lapply(x, as.formula)
  
  ## split all 
  x_split <- lapply(x, split_formula)
  x_lhs <- do.call("c", lapply(x_split, "[[", "lhs"))
  x_rhs <- do.call("c", lapply(x_split, "[[", "rhs"))

  ## recombine
  x_all <- paste_formula(x_lhs, x_rhs)
  
  ## create formula
  ## (we have everything to do this by hand, but for encapsulating code
  ## call Formula() again...which splits again)
  rval <- Formula(x_all)

  ## re-attach original environment
  environment(rval) <- env
  return(rval)
}

is.Formula <- function(object) inherits(object, "Formula")

formula.Formula <- function(x, lhs = NULL, rhs = NULL, collapse = FALSE,
  update = FALSE, drop = TRUE, ...)
{
  ## available parts
  lpart <- 1L:length(attr(x, "lhs"))
  rpart <- 1L:length(attr(x, "rhs"))

  ## default: keep all parts
  lhs <- if(is.null(lhs)) lpart else lpart[lhs]
  rhs <- if(is.null(rhs)) rpart else rpart[rhs]
  if(any(is.na(lhs))) {
    lhs <- as.vector(na.omit(lhs))
    if(length(lhs) < 1L) lhs <- 0L
    warning("subscript out of bounds, not all 'lhs' available")
  }
  if(any(is.na(rhs))) {
    rhs <- as.vector(na.omit(rhs))
    if(length(rhs) < 1L) rhs <- 0L
    warning("subscript out of bounds, not all 'rhs' available")
  }  

  ## collapse: keep parts separated by "|" or collapse with "+"
  collapse <- rep(as.logical(collapse), length.out = 2)

  rval <- paste_formula(attr(x, "lhs")[lhs], attr(x, "rhs")[rhs],
    lsep = ifelse(collapse[1L], "+", "|"),
    rsep = ifelse(collapse[2L], "+", "|"))

  ## omit potentially redundant terms
  if(all(collapse) & update) rval <- update(rval, if(length(rval) > 2) . ~ . else ~ .)

  ## reconvert to Formula if desired
  if(!drop) rval <- Formula(rval)

  ## re-attach original environment
  environment(rval) <- environment(x)

  return(rval)
}

terms.Formula <- function(x, ..., lhs = NULL, rhs = NULL, dot = "separate")
{
  ## simplify to standard formula
  form <- simplify_to_formula(x, lhs = lhs, rhs = rhs)

  ## if necessary try to expand/update/simplify formula parts with dot
  if(has_dot(form)) {
    x_orig <- x
    dot <- match.arg(dot, c("separate", "sequential"))

    ## lhs and rhs calls
    ll <- formula(x, rhs = 0L, collapse = TRUE)[[2L]]
    rr <- attr(x, "rhs")

    ## update and simplify again
    for(i in seq_along(rr)) {
      if(dot == "sequential" && i > 1L) ll <- c_formula(ll, rr[[i - 1L]], sep = "+")
      fi <- paste_formula(ll, rr[[i]]) #probably better than:# paste_formula(NULL, c_formula(rr[[i]], ll, sep = "-"))
      rr[[i]] <- update(formula(terms(fi, ...)), . ~ .)[[3L]]
    }
    attr(x, "rhs") <- rr
    form <- simplify_to_formula(x, lhs = lhs, rhs = rhs)

    ## call traditional terms()
    mt <- terms(form, ...)

    ## store updating for future reference (e.g., in model.part)
    attr(mt, "Formula_with_dot") <- x_orig
    attr(mt, "Formula_without_dot") <- x
    attr(mt, "dot") <- dot
  } else {
    ## call traditional terms()
    mt <- terms(form, ...)
  }
  
  return(mt)
}

model.frame.Formula <- function(formula, data = NULL, ..., lhs = NULL, rhs = NULL, dot = "separate")
{
  model.frame(terms(formula, lhs = lhs, rhs = rhs, data = data, dot = dot), data = data, ...)
}

model.matrix.Formula <- function(object, data = environment(object), ..., lhs = NULL, rhs = 1, dot = "separate")
{
  form <- formula(object, lhs = lhs, rhs = rhs, collapse = c(FALSE, TRUE))
  mt <- delete.response(terms(form, data = data, dot = dot))
  model.matrix(mt, data = data, ...)
}

## as model.response() is not generic, we do this:
model.part <- function(object, ...)
  UseMethod("model.part")

model.part.formula <- function(formula, data, ..., drop = FALSE) {
  formula <- Formula(formula)
  NextMethod()
}

model.part.Formula <- function(object, data, lhs = 0, rhs = 0, drop = FALSE, terms = FALSE, dot = NULL, ...) {

  ## *hs = NULL: keep all parts
  if(is.null(lhs)) lhs <- 1L:length(attr(object, "lhs"))
  if(is.null(rhs)) rhs <- 1L:length(attr(object, "rhs"))

  if(isTRUE(all.equal(as.numeric(lhs), rep(0, length(lhs)))) &
     isTRUE(all.equal(as.numeric(rhs), rep(0, length(rhs)))))
    stop("Either some 'lhs' or 'rhs' has to be selected.")

  if(is.null(dot)) {
    if(is.null(attr(attr(data, "terms"), "dot"))) {
      dot <- "separate"
    } else {
      dot <- attr(attr(data, "terms"), "dot")
    }
  } else {
    dot <- match.arg(dot, c("separate", "sequential"))
  }

  ##
  if(has_dot(object) &&
     !is.null(attr(data, "terms")) &&
     all(c("Formula_with_dot", "Formula_without_dot", "dot") %in% names(attributes(attr(data, "terms")))) &&
     dot == attr(attr(data, "terms"), "dot") &&
     simplify_to_formula(object, lhs = lhs, rhs = rhs) == simplify_to_formula(attr(attr(data, "terms"), "Formula_with_dot"), lhs = lhs, rhs = rhs)
  ) {
    object <- attr(attr(data, "terms"), "Formula_without_dot")
  }

  ## construct auxiliary terms object
  mt <- terms(object, lhs = lhs, rhs = rhs, dot = dot, data = data)

  ## subset model frame
  ix <- attr(mt, "variables")[-1L]
  if(is.null(ix)) {
    ix <- 0
  } else {
    ix <- sapply(ix, deparse)
    if(!all(ix %in% names(data))) stop(
      paste("'data' does not seem to be an appropriate 'model.frame':",
      paste(paste("'", ix[!(ix %in% names(data))], "'", sep = ""), collapse = ", "),
      "not found")
    )
  }
  rval <- data[, ix, drop = drop]
  if(!is.data.frame(rval)) names(rval) <- rownames(data)
  if(terms) attr(rval, "terms") <- mt
  return(rval)
}

update.Formula <- function(object, new,...) {

  new <- Formula(new)
  
  ## extract all building blocks
  o_lhs <- attr(object, "lhs")
  o_rhs <- attr(object, "rhs")
  n_lhs <- attr(new, "lhs")
  n_rhs <- attr(new, "rhs")
  lhs <- rep(list(NULL), length = max(length(o_lhs), length(n_lhs)))
  rhs <- rep(list(NULL), length = max(length(o_rhs), length(n_rhs)))

  ## convenience function for updating components
  update_components <- function(x, y) {
    xf <- yf <- ~ .
    xf[[2L]] <- x
    yf[[2L]] <- y
    update(xf, yf)[[2L]]
  }
    
  if(length(lhs) > 0L) for(i in 1L:length(lhs)) {
    lhs[[i]] <- if(length(o_lhs) < i) n_lhs[[i]]
      else if(length(n_lhs) < i) o_lhs[[i]]
      else update_components(o_lhs[[i]], n_lhs[[i]])
  }

  if(length(rhs) > 0L) for(i in 1L:length(rhs)) {
    rhs[[i]] <- if(length(o_rhs) < i) n_rhs[[i]]
      else if(length(n_rhs) < i) o_rhs[[i]]
      else update_components(o_rhs[[i]], n_rhs[[i]])
  }

  ## recombine
  rval <- paste_formula(lhs, rhs)
  
  ## create formula
  ## (we have everything to do this by hand, but for encapsulating code
  ## call Formula() again...which splits again)
  rval <- Formula(rval)  
  
  ## preserve original environment
  environment(rval) <- environment(object)
  
  return(rval)
}

length.Formula <- function(x) {
  ## NOTE: return length of both sides, not only rhs
  c(length(attr(x, "lhs")), length(attr(x, "rhs")))
}

print.Formula <- function(x, ...) {
  ## we could avoid calling formula() by computing on the internal
  ## structure attr(x, "rhs") <- attr(x, "lhs") <- NULL
  ## but this is probably cleaner...
  print(formula(x))
  invisible(x)
}

all.equal.Formula <- function(target, current, ...) {
  rval <- NULL
  
  if(length(target)[1L] != length(current)[1L]) {
    rval <- c(rval, paste("Length mismatch: target, current differ in number of LHS parts: ",
      length(target)[1L], ", ", length(current)[1L], sep = ""))
  } else if(!isTRUE(all.equal(attr(target, "lhs"), attr(current, "lhs")))) {
    rval <- c(rval, "Formula mismatch: LHS formulas differ in contents")
  }

  if(length(target)[2L] != length(current)[2L]) {
    rval <- c(rval, paste("Length mismatch: target, current differ in number of RHS parts: ",
      length(target)[2L], ", ", length(current)[2L], sep = ""))
  } else if(!isTRUE(all.equal(attr(target, "rhs"), attr(current, "rhs")))) {
    rval <- c(rval, "Formula mismatch: RHS formulas differ in contents")
  }
  
  if(is.null(rval)) TRUE else rval
}

str.Formula <- function(object, ...) {
  le <- length(object)
  ls <- if(sum(le) > 2L | any(le > 1L)) "s" else ""
  writeLines(c(
    sprintf("'Formula' with %s left-hand and %s right-hand side%s: %s",
      le[1L], le[2L], ls, format(object)),
    sprintf("  ..- attr(*, \".Environment\")=%s", format(attr(object, ".Environment")))))
  invisible()
}

## convenience tools #################################################

## split formulas
split_formula <- function(f) {

  stopifnot(inherits(f, "formula"))

  rhs <- if(length(f) > 2) f[[3L]] else f[[2L]]
  lhs <- if(length(f) > 2) f[[2L]] else NULL

  extract_parts <- function(x, sep = "|") {
    if(is.null(x)) return(NULL)
    
    rval <- list()
    if(length(x) > 1L && x[[1L]] == sep) {
      while(length(x) > 1L && x[[1L]] == sep) {
        rval <- c(x[[3L]], rval)
        x <- x[[2L]]
      }
    }
    return(c(x, rval))
  }

  list(lhs = extract_parts(lhs), rhs = extract_parts(rhs))
}

## combine (parts of) formulas
c_formula <- function(f1, f2, sep = "~") {

  stopifnot(length(sep) == 1L, nchar(sep) == 1L,
    sep %in% c("~", "+", "-", "|", "&"))

  if(sep == "~") {
    rval <- . ~ .
    rval[[3L]] <- f2	
    rval[[2L]] <- f1
  } else {
    rval <- as.formula(paste(". ~ .", sep, "."))
    rval[[3L]][[3L]] <- f2
    rval[[3L]][[2L]] <- f1
    rval <- rval[[3L]]
  }

  return(rval)
}

## reassemble formulas
paste_formula <- function(lhs, rhs, lsep = "|", rsep = "|") {

  stopifnot(all(nchar(lsep) == 1L), all(lsep %in% c("+", "|", "&")))
  stopifnot(all(nchar(rsep) == 1L), all(rsep %in% c("+", "|", "&")))
  
  if(length(lhs) > 1L) lsep <- rep(lsep, length.out = length(lhs) - 1L)
  if(length(rhs) > 1L) rsep <- rep(rsep, length.out = length(rhs) - 1L)

  if(is.null(lhs)) lhs <- list()
  if(is.null(rhs)) rhs <- list()
  
  if(!is.list(lhs)) lhs <- list(lhs)
  if(!is.list(rhs)) rhs <- list(rhs)

  lval <- if(length(lhs) > 0L) lhs[[1L]] else NULL
  if(length(lhs) > 1L) {
    for(i in 2L:length(lhs)) lval <- c_formula(lval, lhs[[i]], sep = lsep[[i - 1L]])
  }
  rval <- if(length(rhs) > 0L) rhs[[1L]] else 0 ## FIXME: Is there something better?
  if(length(rhs) > 1L) {
    for(i in 2L:length(rhs)) rval <- c_formula(rval, rhs[[i]], sep = rsep[[i - 1L]])
  }

  c_formula(lval, rval, sep = "~")
}

## simplify a Formula to a formula that can be processed with
## terms/model.frame etc.
simplify_to_formula <- function(Formula, lhs = NULL, rhs = NULL) {

  ## get desired subset as formula and Formula
  form <- formula(Formula, lhs = lhs, rhs = rhs)
  Form <- Formula(form)

  ## convenience functions for checking extended features
  is_lhs_extended <- function(Formula) {
    ## check for multiple parts
    if(length(attr(Formula, "lhs")) > 1L) {
      return(TRUE)
    } else {
    ## and multiple responses
      if(length(attr(Formula, "lhs")) < 1L) return(FALSE)
      return(length(attr(terms(paste_formula(NULL,
        attr(Formula, "lhs"), rsep = "+")), "term.labels")) > 1L)
    }
  }

  is_rhs_extended <- function(Formula) {
    ## check for muliple parts
    length(attr(Formula, "rhs")) > 1L
  }

  ## simplify (if necessary)
  ext_lhs <- is_lhs_extended(Form)
  if(ext_lhs | is_rhs_extended(Form)) {
    form <- if(ext_lhs) {
      if(length(attr(Form, "rhs")) == 1L & identical(attr(Form, "rhs")[[1L]], 0)) {
	paste_formula(NULL, attr(Form, "lhs"), rsep = "+")    
      } else {
        paste_formula(NULL, c(attr(Form, "lhs"), attr(Form, "rhs")), rsep = "+")
      }
    } else {
      paste_formula(attr(Form, "lhs"), attr(Form, "rhs"), rsep = "+")	 
    }
  }

  ## re-attach original environment and return
  environment(form) <- environment(Formula)
  return(form)
}

## check whether formula has a dot (FIXME: can other problems than just '.' occur?)
has_dot <- function(formula) inherits(try(terms(formula), silent = TRUE), "try-error")

###################################################################

kernelwts<-function(X,center,bw,kernel="triangular"){
  dist<-(X-center)/bw
  if(kernel=="triangular"){
    w<-(1-abs(dist))
  } else if (kernel=="rectangular") {
    w<-1/2
  } else if (kernel=="epanechnikov") {
    w<-3/4*(1-dist^2)
  } else if (kernel=="quartic" | kernel=="biweight") {
    w<-15/16*(1-dist^2)^2
  } else if (kernel=="triweight") {
    w<-35/32*(1-dist^2)^3
  } else if (kernel=="tricube") {
    w<-70/81*(1-abs(dist)^3)^3
  } else if (kernel=="gaussian") {
    w<-1/sqrt(2*pi)*exp(-1/2*dist^2)
  } else if (kernel=="cosine") {
    w<-pi/4*cos(pi/2 * dist)
  } else {
    stop("Invalid kernel selection.")
  }
  w<-ifelse(abs(dist)>1&kernel!="gaussian",0,w)
  w<-w/sum(w)
  return(w)
}

IKbandwidth <-function (X,Y,cutpoint=NULL,verbose=FALSE,kernel="triangular") {
  #Implementation of Imbens-Kalyanaraman optimal bandwidth
  # for regression discontinuity
  sub<-complete.cases(X)&complete.cases(Y)
  X <- X[sub]
  Y <- Y[sub]
  Nx<-length(X)
  Ny<-length(Y)
  if(Nx!=Ny)
    stop("Running and outcome variable must be of equal length")
  if(is.null(cutpoint)) {
    cutpoint<-0
    if(verbose) cat("Using default cutpoint of zero.\n")
  } else {
    if(! (typeof(cutpoint) %in% c("integer","double")))
      stop("Cutpoint must be of a numeric type")
  }
  #Now we should be ready to start
  #Pilot bandwidth
  h1<-1.84*sd(X)*Nx^(-1/5)
  left<-X>=(cutpoint-h1) & X<=cutpoint
  right<-X>cutpoint & X<=(cutpoint+h1)
  Nl<-sum(left)
  Nr<-sum(right)
  Ybarl<-mean(Y[left])
  Ybarr<-mean(Y[right])
  fbarx<-(Nl+Nr)/(2*Nx*h1)
  varY<-(sum((Y[left]-Ybarl)^2)+sum((Y[right]-Ybarr)^2))/(Nl+Nr)
  medXl<-median(X[X<=cutpoint])
  medXr<-median(X[X>cutpoint])
  Nl<-sum(X<cutpoint)
  Nr<-sum(X>=cutpoint)
  cX<-X-cutpoint
  if(sum(X[left]>medXl)==0 | sum(X[right]<medXr)==0)
    stop("Insufficient data in vicinity of the cutpoint to calculate bandwidth.")
  #Model a cubic within the pilot bandwidth
  mod<-lm(Y~I(X>=cutpoint)+poly(cX,3,raw=T),subset=(X>=medXl&X<=medXr))
  m3<-6*coef(mod)[5]
  #New bandwidth estimate
  h2l<-3.56*(Nl^(-1/7))*(varY/(fbarx*max(m3^2,0.01)))^(1/7)
  h2r<-3.56*(Nr^(-1/7))*(varY/(fbarx*max(m3^2,0.01)))^(1/7)
  left<-(X>=(cutpoint-h2l)) & (X<cutpoint)
  right<-(X>=cutpoint) & (X<= (cutpoint+h2r))
  Nl<-sum(left)
  Nr<-sum(right)
  if(Nl==0 | Nr==0)
    stop("Insufficient data in vicinity of the cutpoint to calculate bandwidth.")
  #Estimate quadratics for curvature estimation
  mod<-lm(Y~poly(cX,2,raw=T),subset=right)
  m2r<-2*coef(mod)[3]
  mod<-lm(Y~poly(cX,2,raw=T),subset=left)
  m2l<-2*coef(mod)[3]
  rl<-720*varY/(Nl*(h2l^4))
  rr<-720*varY/(Nr*(h2r^4))
  #Which kernel are we using?
  # Method for finding these available in I--K p. 6
  if(kernel=="triangular") {
    ck<-3.43754
  } else if (kernel=="rectangular") {
    ck<-5.40384
  } else if(kernel=="epanechnikov") {
    ck<-3.1999
  } else if(kernel=="quartic" | kernel=="biweight") {
    ck<-3.65362
  } else if(kernel=="triweight") {
    ck<-4.06065
  } else if(kernel=="tricube") {
    ck<-3.68765
  } else if(kernel=="gaussian") {
    ck<-1.25864
  } else if(kernel=="cosine") {
    ck<-3.25869
  } else {
    stop("Unrecognized kernel.") 
  }
  #And there's our optimal bandwidth
  optbw<-ck*(2*varY/(fbarx*((m2r-m2l)^2+rr+rl)))^(1/5)*(Nx^(-1/5))
  left<-(X>=(cutpoint-optbw)) & (X<cutpoint)
  right<-(X>=cutpoint) & (X<= (cutpoint+optbw))
  if(sum(left)==0 | sum(right)==0)
    stop("Insufficient data in the calculated bandwidth.")
  names(optbw)<-NULL
  if(verbose) cat("Imbens-Kalyanamaran Optimal Bandwidth: ",sprintf("%.3f",optbw),"\n")
  return(optbw)
  }


RDestimate<-function(formula, data, subset=NULL, cutpoint=NULL, bw=NULL, kernel="triangular", se.type="HC1", cluster=NULL, verbose=FALSE, model=FALSE, frame=FALSE) {
  call<-match.call()
  if(missing(data)) data<-environment(formula)
  formula<-as.Formula(formula)
  X<-model.frame(formula,rhs=1,lhs=0,data=data,na.action=na.pass)[[1]]
  Y<-model.frame(formula,rhs=0,lhs=NULL,data=data,na.action=na.pass)[[1]]
  if(!is.null(subset)){
    X<-X[subset]
    Y<-Y[subset]
    if(!is.null(cluster)) cluster<-cluster[subset]
  }
  if (!is.null(cluster)) {
    cluster<-as.character(cluster)
    robust.se <- function(model, cluster){
      M <- length(unique(cluster))
      N <- length(cluster)           
      K <- model$rank
      dfc <- (M/(M - 1)) * ((N - 1)/(N - K))
      uj  <- apply(estfun(model), 2, function(x) tapply(x, cluster, sum));
      rcse.cov <- dfc * sandwich(model, meat. = crossprod(uj)/N)
      rcse.se <- coeftest(model, rcse.cov)
      return(rcse.se[2,2])
    }
  }
  na.ok<-complete.cases(X)&complete.cases(Y)
  if(length(all.vars(formula(formula,rhs=1,lhs=F)))>1){
   type<-"fuzzy" 
   Z<-model.frame(formula,rhs=1,lhs=0,data=data,na.action=na.pass)[[2]]
   if(!is.null(subset)) Z<-Z[subset]
   na.ok<-na.ok&complete.cases(Z)
   if(length(all.vars(formula(formula,rhs=1,lhs=F)))>2)
     stop("Invalid formula. Read ?RDestimate for proper syntax")
  } else {
   type="sharp" 
  }
  covs<-NULL
  if(length(formula)[2]>1){
    covs<-model.frame(formula,rhs=2,lhs=0,data=data,na.action=na.pass)
    if(!is.null(subset)) covs<-subset(covs,subset)
    na.ok<-na.ok&complete.cases(covs)
    covs<-subset(covs,na.ok)
  }
  X<-X[na.ok]
  Y<-Y[na.ok]
  if(type=="fuzzy") Z<-as.double(Z[na.ok])
  
  if(is.null(cutpoint)) {
    cutpoint<-0
    if(verbose) cat("No cutpoint provided. Using default cutpoint of zero.\n")
  }
  if(frame) {
    if(type=="sharp") {
      if (!is.null(covs))
        dat.out<-data.frame(X,Y,covs)
      else
        dat.out<-data.frame(X,Y)
    } else {
      if (!is.null(covs))
        dat.out<-data.frame(X,Y,Z,covs)
      else
        dat.out<-data.frame(X,Y,Z)
    }
  }
  if(is.null(bw)) {
    bw<-IKbandwidth(X=X,Y=Y,cutpoint=cutpoint,kernel=kernel, verbose=verbose)
    bws<-c(bw,.5*bw,2*bw)
    names(bws)<-c("LATE","Half-BW","Double-BW")
  } else if (length(bw)==1) {
    bws<-c(bw,.5*bw,2*bw)
    names(bws)<-c("LATE","Half-BW","Double-BW")
  } else {
    bws<-bw
  }
  
  #Setup values to be returned
  o<-list()
  o$type<-type
  o$call<-call
  o$est<-vector(length=length(bws),mode="numeric")
  names(o$est)<-names(bws)
  o$bw<-as.vector(bws)
  o$se<-vector(mode="numeric")
  o$z<-vector(mode="numeric")
  o$p<-vector(mode="numeric")
  o$obs<-vector(mode="numeric")
  o$ci<-matrix(NA,nrow=length(bws),ncol=2)
  o$model<-list()
  if(type=="fuzzy") {
    o$model$firststage<-list()
    o$model$iv<-list()
  }
  o$frame<-list()
  o$na.action<-which(na.ok==FALSE)
  class(o)<-"RD"
  X<-X-cutpoint
  Xl<-(X<0)*X
  Xr<-(X>=0)*X
  Tr<-as.integer(X>=0)
  
  for(bw in bws){
    ibw<-which(bw==bws)
  #Subset to within the bandwidth, except for when using gaussian weighting
    sub<- X>=(-bw) & X<=(+bw)
  
    
  if(kernel=="gaussian") 
    sub<-TRUE

  w<-kernelwts(X,0,bw,kernel=kernel)
  o$obs[ibw]<-sum(w>0)
    
  if(type=="sharp"){
    if(verbose) {
      cat("Running Sharp RD\n")
      cat("Running variable:",all.vars(formula(formula,rhs=1,lhs=F))[1],"\n")
      cat("Outcome variable:",all.vars(formula(formula,rhs=F,lhs=1))[1],"\n")
      if(!is.null(covs)) cat("Covariates:",paste(names(covs),collapse=", "),"\n")
    }
    if(!is.null(covs)) {
      data<-data.frame(Y,Tr,Xl,Xr,covs,w)
      form<-as.formula(paste("Y~Tr+Xl+Xr+",paste(names(covs),collapse="+",sep=""),sep=""))
    } else {
      data<-data.frame(Y,Tr,Xl,Xr,w)
      form<-as.formula(Y~Tr+Xl+Xr)
    }

    mod<-lm(form,weights=w,data=subset(data,w>0))
    if(verbose==TRUE) {
      cat("Model:\n")
      print(summary(mod))
    }
    o$est[ibw]<-coef(mod)["Tr"]
    if (is.null(cluster)) {
      o$se[ibw]<-coeftest(mod,vcovHC(mod,type=se.type))[2,2]
    } else {
      o$se[ibw]<-robust.se(mod,cluster[na.ok][w>0])
    }
    o$z[ibw]<-o$est[ibw]/o$se[ibw]
    o$p[ibw]<-2*pnorm(abs(o$z[ibw]),lower.tail=F)
    o$ci[ibw,]<-c(o$est[ibw]-qnorm(.975)*o$se[ibw],o$est[ibw]+qnorm(.975)*o$se[ibw])

    if(model) o$model[[ibw]]=mod
    if(frame) o$frame[[ibw]]=dat.out

  } else {
    if(verbose){
      cat("Running Fuzzy RD\n")
      #CLEAN UP
      cat("Running variable:",all.vars(formula(formula,rhs=1,lhs=F))[1],"\n")
      cat("Outcome variable:",all.vars(formula(formula,rhs=F,lhs=1))[1],"\n")
      cat("Treatment variable:",all.vars(formula(formula,rhs=1,lhs=F))[2],"\n")
      if(!is.null(covs)) cat("Covariates:",paste(names(covs),collapse=", "),"\n")
    }

    if(!is.null(covs)) {
      data<-data.frame(Y,Tr,Xl,Xr,Z,covs,w)
      form<-as.Formula(paste(
              "Y~Z+Xl+Xr+",paste(names(covs),collapse="+"),
              "|Tr+Xl+Xr+",paste(names(covs),collapse="+"),sep=""))
      form1<-as.Formula(paste("Z~Tr+Xl+Xr+",paste(names(covs),collapse="+",sep="")))
    } else {
      data<-data.frame(Y,Tr,Xl,Xr,Z,w)
      form<-as.Formula(Y~Z+Xl+Xr|Tr+Xl+Xr)
      form1<-as.formula(Z~Tr+Xl+Xr)
    }
    
    mod1<-lm(form1,weights=w,data=subset(data,w>0))
    mod<-ivreg(form,weights=w,data=subset(data,w>0))
    if(verbose==TRUE) {
      cat("First stage:\n")
      print(summary(mod1))
      cat("IV-RD:\n")
      print(summary(mod))
    }
    o$est[ibw]<-coef(mod)["Z"]
    if (is.null(cluster)) {
      o$se[ibw]<-coeftest(mod,vcovHC(mod,type=se.type))[2,2]
    } else {
      o$se[ibw]<-robust.se(mod,cluster[na.ok][w>0])
    }
    o$z[ibw]<-o$est[ibw]/o$se[ibw]
    o$p[ibw]<-2*pnorm(abs(o$z[ibw]),lower.tail=F)
    o$ci[ibw,]<-c(o$est[ibw]-qnorm(.975)*o$se[ibw],o$est[ibw]+qnorm(.975)*o$se[ibw])
    
    if(model) {
      o$model$firststage[[ibw]]<-mod1
      o$model$iv[[ibw]]=mod
    }
    if(frame) o$frame=dat.out
  }
  }
  return(o)
}

summary.RD<-function(object,digits=max(3, getOption("digits") - 3),...){
  cat("\n")
  cat("Call:\n")
  print(object$call)
  cat("\n")
  
  cat("Type:\n")
  cat(object$type,"\n\n")
  
  #If the model wasn't included in the output, we need to get it
  mod<-FALSE
  if("model" %in% names(object$call)) mod<-object$call$model
  if(!mod){
    object$call$model<-TRUE
    object$call$verbose<-FALSE
    object<-eval.parent(object$call)
  }
  n<-length(object$est)

  obs<-vector(length=n)
  if(object$type=="sharp") {
    for(i in 1:n) obs[i]<-length(residuals(object$model[[i]]))
  } else {
    for(i in 1:n) obs[i]<-length(residuals(object$model$iv[[i]]))
  }
  cat("Estimates:\n")
  #Need to get this to give at least as much as stata does in fuzzy designs
  stars<-vector(length=n)

  for(i in 1:n) {
    stars[i]<-if (object$p[i]<0.001) "***" else if(object$p[i]<0.01) "**" else if(object$p[i]<0.05) "*" else if(object$p[i]<0.1) "." else " "
  }

  out<-matrix(
    c(object$bw,
      object$obs,
      object$est,
      object$se,
      object$z,
      object$p),
    nrow=n)
  rownames(out)<-names(object$est)
  colnames(out)<-c("Bandwidth","Observations","Estimate","Std. Error","z value","Pr(>|z|)")

  print.default(cbind(apply(out,2,function(x) format(x,digits=digits)),
                      " "=stars),quote=FALSE,print.gap=2,right=FALSE)
  cat("---\n")
  cat("Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1\n\n")
  
  out<-list(coefficients=out)
  class(out)<-"summary.RD"
  fstat<-matrix(NA,nrow=n,ncol=4)
  if(object$type=="sharp") {
    for(i in 1:n) {
      fstat[i,]<-c(summary(object$model[[i]])$fstatistic[[1]],
               summary(object$model[[i]])$fstatistic[[2]],
               summary(object$model[[i]])$fstatistic[[3]],
        pf(summary(object$model[[i]])$fstatistic[[1]],
          summary(object$model[[i]])$fstatistic[[2]],
          summary(object$model[[i]])$fstatistic[[3]])
      )
    }
    fstat[,4]<-2*apply(cbind(fstat[,4],1-fstat[,4]),1,min)
  } else {
    for(i in 1:n) {
      fstat[i,]<-c(
        summary(object$model$iv[[i]])$waldtest[1],
        summary(object$model$iv[[i]])$waldtest[3],
        summary(object$model$iv[[i]])$waldtest[4],
        summary(object$model$iv[[i]])$waldtest[2])
    }
  }
  colnames(fstat)<-c("F","Num. DoF","Denom. DoF","p")
  rownames(fstat)<-names(object$est)
  cat("F-statistics:\n")
  print.default(apply(fstat,2,function(x) format(x,digits=digits)),quote=FALSE,print.gap=2,right=FALSE)
  out$fstat<-fstat
  return(invisible(out))
}

##########################################################
##########################################################
    
```

`@sample_code`
```{r}
# Before running a regression model, let's examine the data:
  
    str(NBA)

# The dataset contains eight variables: a game identifier, a season identifier, two team identifiers (for home and visitor), the quality of the home and visiting teams (a normalized verison of win percentage), and the halftime and end-of-game margins of victory for the home team.

# 1)  Let's start by creating a dummy variable that equals 1 if the home team is ahead at halftime, then store those results into the variable `home.team.winning.at.half` in the dataframe `NBA`. Note that a logical expression like `x > y` in R will return a value of `true` or `false` by default, but you can convert this into a numeric variable with a value of 1 or 0 by wrapping your variable definition in the `as.numeric()` function, like so: as.numeric(x > y). Enter the proper syntax between the () provided below to create the dummy variable when the home team has a positive point margin at halftime:

    NBA$home.team.winning.at.half <- as.numeric()


# 2) Let's assume that the effect of the halftime margin on the final margin is a linear one. Use the lm function to compute the RD estimate of being ahead at halftime on the final margin of victory. Include the following as additional controls in the regression, which are each separate variables listed in the str() results: home team's halftime margin, home team quality, and away team quality.

    summary(lm())

# Good. Here we tried using a linear model, but what if that effect is nonlinear?

# 3) Let's see what happens to our effect if we allow our model to handle a quadratic effect of halftime margin on the final margin. We can do this by adding I(home.team.halftime.margin^2) as an additional term in the model statement of lm.

    summary(lm())

  
# 4) Nice going. But what if the effect is nonlinear and also not really quadratic? As a last exercise, let's further relax the quadratic assumption of halftime margin. Instead of estimating an OLS regression using the lm function, we will now use a package called 'rdd' which gives us more options to test the sensitivity of the regression assumptions for our RD estimate.

# In this case, the function we will use is called RDestimate. Without getting into too many details, we will look at one of its functions that provides a nonparametric model that we can compare to our linear and quadratic models. Run the following syntax as your answer to Question 4, and compare the results to the prior estimate results:

    summary(RDestimate(home.team.final.margin ~ home.team.halftime.margin | home.team.qual+away.team.qual,data=NBA))


# 5) Now compare the results of our three causal effect estimates: the linear model and our two nonlinear models (with quadratic and nonparametric functions). Which kind of estimate do you think most closely captures the true causal effect of being behind (or ahead) at halftime on the final margin of victory? Write in "linear" or "nonlinear" as the answer to Solution5.

    Solution5<-""

```

`@solution`
```{r}
    NBA$home.team.winning.at.half <- as.numeric(NBA$home.team.halftime.margin>0)
    summary(lm(home.team.final.margin ~ home.team.winning.at.half+home.team.halftime.margin+home.team.qual+away.team.qual,data=NBA))
    summary(lm(home.team.final.margin ~ home.team.winning.at.half+home.team.halftime.margin+I(home.team.halftime.margin^2)+home.team.qual+away.team.qual,data=NBA))
    summary(RDestimate(home.team.final.margin ~ home.team.halftime.margin | home.team.qual+away.team.qual,data=NBA))
    Solution5<-"nonlinear"
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("Solution5") %>% check_equal()
success_msg("Good work! From the looks of it, the quadratic specification of halftime margin looks very similar to the nonparametric estimate (4.8 points versus 4.4 points, respectively), which suggests that they may be closer to the real effect. The linear specification seems to not capture the true relationship between halftime margin and final margin, as it only estimates an effect of 2.5 points.")
```

---

## ATEs, CATEs, and LATEs: What are the Differences?

```yaml
type: VideoExercise
key: 1d0efb7311
lang: r
xp: 50
skills: 1
video_link: //player.vimeo.com/video/219561649
```

