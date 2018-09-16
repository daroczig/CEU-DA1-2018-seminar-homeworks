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
key: 4687bc8b73
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
key: cb55bc4f77
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
key: a442603d24
```

Generate a sequence between `0` and `4*pi` with a step of `0.1`. Store the resulting vector as `x`.

`@hint`
Use the `seq` function. Check the manual via `?seq` for more details.


`@pre_exercise_code`
```{r}
rm(x)
```

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


---

## Draw functions

```yaml
type: NormalExercise
xp: 100
```

Draw a cosine wave by reusing `x` from the previous example (it's already available in your session), applying `cos` and using the `plot` function:

`@instructions`
- Compute the cosine of `x` and store the resulting vector as `y`.
- Plot these values by the original `x` values with a red line using the `x` vector from the previous exercise.

`@hint`
Apply `cos` on `x`, then `plot` it along with `x` using the `col` argument to specify `red` color. Don't forget to set the `type` of the plot to lines.

`@pre_exercise_code`
```{r}
x <- seq(0, 4*pi, by = 0.1)
```

`@sample_code`
```{r}
x
```

`@solution`
```{r}
y <- cos(x)
plot(x, y, col = 'red', type = 'l')
```

`@sct`
```{r}
ex() %>% check_function("cos") %>% check_result() %>% check_equal()
ex() %>% check_object("y") %>% check_equal()
ex() %>% check_function("plot") %>% {
  check_arg(., "x") %>% check_equal()
  check_arg(., "y") %>% check_equal()
  check_arg(., "col") %>% check_equal()
  check_arg(., "type") %>% check_equal()
}
```

---

## Draw functions again

```yaml
type: NormalExercise
xp: 100
```

Redraw the previous plot using the `curve` function.

`@solution`
```{r}
curve(cos, to = 4*pi, col = 'red')
```

`@sct`
```{r}
ex() %>% check_function("plot") %>% {
  check_arg(., "to") %>% check_equal()
  check_arg(., "col") %>% check_equal()
}
```

---

## Code syle: file names

```yaml
type: MultipleChoiceExercise
xp: 50
```

Which of the below R script names is good? What's the problem with the other 3?

`@instructions`
- fitModels.R
- fit-models.R
- fit models.R
- fit.models.R

`@hint`
Read Hadley's code style at http://adv-r.had.co.nz/Style.html

`@sct`
```{r}
ex() %>% check_mc(correct = 2)
```

---

## Code syle: object names

```yaml
type: MultipleChoiceExercise
xp: 50
```

Which of the below R object names is good? What's the problem with the other 3?

`@instructions`
- student_summary
- summary
- studentSummary
- student.summary

`@hint`
Read Hadley's code style at http://adv-r.had.co.nz/Style.html

`@sct`
```{r}
ex() %>% check_mc(correct = 1)
```

---

## Code syle: file whitespace

```yaml
type: MultipleChoiceExercise
xp: 50
```

Which of the below R command examples is good? What's the problem with the other 3?

`@instructions`
- bmi <- weight/ height ^2
- bmi <- weight / height*height
- bmi = weight / (height * height)
- bmi <- weight / (height * height)

`@hint`
Read Hadley's code style at http://adv-r.had.co.nz/Style.html

`@sct`
```{r}
ex() %>% check_mc(correct = 4)
```

