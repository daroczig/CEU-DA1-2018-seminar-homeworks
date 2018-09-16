---
title: 'Week 1'
description: 'Welcome! We will use this platform in the next few weeks for syntax-oriented homeworks, so that you can practice what we have learned in R.'
---

## The author of R

```yaml
type: MultipleChoiceExercise
```

Who is one of the authors of the R programming language?

`@instructions`

- Roy Co
- Ronald McDonald
- Ross Ihaka

`@sct`

```r
msg1 <- "That's someone who makes soups."
msg2 <- "That's a clown who likes burgers."
msg3 <- "Correct! Head over to the next exercise!"
ex() %>% check_mc(correct = 3,
                  feedback_msgs = c(msg1, msg2, msg3))
```
