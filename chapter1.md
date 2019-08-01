---
title: 'collection of review exercies'
output: html_document
free_preview: true
---

## Comparing Breakfast Cereals: Outcome Variables

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

## Anscombe Quartet

```yaml
type: PureMultipleChoiceExercise
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
- R's correlation function is broken.

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
