---
title: 'collection of review exercies'
output: html_document
free_preview: true


## Introduction Chapter 
## If you want to go through these topics in more detail, take our free Causal Inference with R - Introduction course here on DataCamp.
---

## Comparing Breakfast Cereals: Outcome Variables

```yaml
type: MultipleChoiceExercise
key: 362bf33c36
lang: r
xp: 50
skills: 1
```

The food scientists at breakfast cereal manufacturer Puritan Wheat Inc. have developed a new breakfast cereal product called TechnoCrunch. It has a biodegradable nanomaterial coating designed to keep its flakes crispy in milk for longer than the flakes in its competitor cereal, NeoPuffs. Now Puritan Wheat wants to run an experiment to see if the formula works, so it compares the time it takes for TechnoCrunch to get soggy in milk versus the time it takes for NeoPuffs to get soggy. 

In this experiment on the two cereals, which of the following is the outcome variable in Puritan Wheat's analysis?

`@instructions`
- The brand of cereal.
- The amount of milk that each flake of cereal can absorb.
- The time it takes for the cereal to get soggy.
- Individual flakes.

`@sct`
```{r}
msg1 = "This is the experimental condition that causes the outcome, i.e. the treatment variable, also called the independent variable (because we have the freedom to manipulate its value in an experiment). Try again."
msg2 = "This is likely correlated with how the dependent variable, but is not mentioned in the prompt. Try again"
msg3 = "Correct! The outcome variable is one's outcome of interest. You will see it also called the dependent variable, because its value depends on the treatment. You might also see the treatment being called the independent variable, because we have the freedom to manipulate its value in an experiment."
msg4 = "Not quite. Try again"
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

---

## Comparing Breakfast Cereals: Units of Analysis

```yaml
type: MultipleChoiceExercise
key: 50d28d8b25
lang: r
xp: 50
skills: 1
```

Puritan Wheat generates some data from a sample of individual flakes in a box of TechnoCrunch and from a box of its competitor's cereal, NeoPuff's. Puritan Wheat intends to examine the average time it takes for each flake to become soggy. What is the unit of analysis in this study?

`@instructions`
- The brand of cereal.
- The amount of milk that each flake of cereal can absorb.
- The time it takes for the cereal to get soggy.
- Individual flakes.

`@sct`
```{r}
msg1 = "This is the experimental condition that causes the outcome, i.e. the treatment (a.k.a. independent) variable. Try again"
msg2 = "Not quite. Try again"
msg3 = "This is the outcome (a.k.a. dependent) variable in our analysis, try again."
msg4 = "Correct! The unit of analysis is 'what' or 'who' is being studied/sampled. Often our unit of analyses are individual people, but in this example, we are studying a sample of cereal flakes."
test_mc(correct = 4, feedback_msgs = c(msg1,msg2,msg3,msg4))
```
