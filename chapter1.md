---
title: 'Week 1'
description: 'Welcome! We will use this platform in the next few weeks for syntax-oriented homeworks, so that you can practice what we have learned in R.'
---

## The author of R## A numeric function

```yaml
type: MultipleChoiceExercise
key: 583049e0db
xp: 50
```

Which R function returns the square root of a number?

`@instructions`
- square
- root
- sqrt
- Sqrt

`@hint`
Remember, R commands are case sensitive!

`@sct`
```{r}
ex() %>% check_mc(correct = 3)
```


---

## Random numbers

```yaml
type: NormalExercise
xp: 50
key: 03a2bb5c40
```

Draw 5 random numbers from the uniform distribution between 0 and 1.

`@pre_exercise_code`
```{r}
set.seed(42)
```

`@sample_code`
```{r}
## specify a seed for the random number generator
set.seed(42)

## generate 5 random numbers


```

`@hint`
Use the `runif` function.


`@solution`
```{r}
set.seed(42)
runif(5)
```

`@sct`
```{r}
ex() %>% check_function("runif") %>% check_arg(., "n") %>% check_equal()
```

---

## Vectors

```yaml
type: NormalExercise
xp: 100
```

Generate 15 random numbers between 0 and 5 and store in variable `x`.

`@pre_exercise_code`
```{r}
set.seed(42)
```

`@sample_code`
```{r}
## specify a seed for the random number generator
set.seed(42)

## generate 15 random numbers between 0 and 5, then assign to x


```

`@solution`
```{r}
set.seed(42)
x <- runif(15, min = 0, max = 5)
```

`@sct`
```{r}
ex() %>% check_function("runif") %>% {
  check_arg(., "n") %>% check_equal()
  check_arg(., "max")
}
ex() %>% check_object("x") %>% check_equal()
```
