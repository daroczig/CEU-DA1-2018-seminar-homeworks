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

## Creating Vectors

```yaml
type: NormalExercise
xp: 100
key: fa2a369a49
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

---

## Stats

```yaml
type: NormalExercise
xp: 100
```

Compute the arithmetic mean of the random numbers you generated in the previous exercise. No need to recreate the `x` variable, it's already available in your session.

`@hint`
Use the `mean` function to compute the arithmetic mean.

`@pre_exercise_code`
```{r}
set.seed(42)
x <- runif(15, min = 0, max = 5)
```

`@sample_code`
```{r}
x
```

`@solution`
```{r}
mean(x)
```

`@sct`
```{r}
ex() %>% check_function("mean") %>% check_result() %>% check_equal()
```

---

## Dataviz

```yaml
type: NormalExercise
xp: 100
```

Plot these numbers on a histogram with the main title being "Histogram of 15 random numbers"! No need to recreate the `x` variable, it's already available in your session.

`@hint`
Use the `hist` function.

`@pre_exercise_code`
```{r}
set.seed(42)
x <- runif(15, min = 0, max = 5)
```

`@sample_code`
```{r}
x
```

`@solution`
```{r}
hist(x, main = "Histogram of 15 random numbers")
```

`@sct`
```{r}
ex() %>% check_function("hist") %>% check_arg(., "main") %>% check_equal()
```

---

## Sequences

```yaml
type: NormalExercise
xp: 100
```

Generate a sequence between `0` and `4*pi` with a step of `0.1`. Store the resulting vector as `x`.

`@hint`
Use the `seq` function. Check the manual via `?seq` for more details.

`@solution`
```{r}
x <- seq(0, 4*pi, by = 0.1)
```

`@sct`
```{r}
ex() %>% check_function("seq") %>% {
  check_arg(., "to") %>% check_equal()
  check_arg(., "by") %>% check_equal()
}
ex() %>% check_object("x") %>% check_equal()
```


