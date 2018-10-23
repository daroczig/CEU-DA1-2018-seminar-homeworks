---
title: 'Week 6'
description: 'If you get stuck, I suggest revisiting the R sources of the <a href="https://github.com/daroczig/CEU-R-lab">"Data Analytics 1a - Exploration" class on GitHub</a>, and also feel free to check other classes on DataCamp! And in case you really get stuck ... feel free to open a ticket on GitHub and ask for help.'
---

## Creating data.table objects

```yaml
type: NormalExercise
xp: 50
key: 68ef0e987f
```

- Load the `nycflights13` package
- Check the structure of the `flights` dataset
- Load the `data.table` package
- Create a new `data.table` object called `dt` with the content of the `flights` dataset

`@sample_code`
```{r}
nycflights13
```

`@solution`
```{r}
library(nycflights13)
str(flights)
library(data.table)
dt <- data.table(flights)
```

`@sct`
```{r}
ex() %>% check_function("str") %>% check_arg("object") %>% check_equal()
ex() %>% check_object("dt") %>% check_equal()
```

---

## Count rows

```yaml
type: NormalExercise
xp: 100
key: ff104da3a7
```

Count the number or rows in the `dt` object and store in the `n` variable!

`@pre_exercise_code`
```{r}
library(data.table); library(nycflights13); dt <- data.table(flights)
```

`@sample_code`
```{r}
dt
```

`@solution`
```{r}
n <- nrow(dt) # data.frame approach
n <- dt[, .N] # data.table approach
```

`@sct`
```{r}
ex() %>% check_object("n") %>% check_equal()
```

---

## Filter

```yaml
type: NormalExercise
xp: 100
key: 5744f0ec3a
```

Count the number of flights in the `dt` dataset starting from `JFK` and store the result in the `n` variable! Note, that `dt` is already available in the workspace, no need to create it or load `data.table`.

`@hint`
Use `?flights` or `str(flights)` to see the structure and the column names of the original `flights` object that we have converted into a `data.table` object called `dt.`

`@pre_exercise_code`
```{r}
library(data.table); library(nycflights13); dt <- data.table(flights)
```

`@sample_code`
```{r}
dt
```

`@solution`
```{r}
n <- dt[origin == 'JFK', .N]
```

`@sct`
```{r}
ex() %>% check_object("n") %>% check_equal()
```

---

## Frequencies

```yaml
type: NormalExercise
xp: 100
key: e876be0168
```

Count the number of flights per `origin` and store the resulting object in the `n` variable! Please use the `data.table` approach instead of the `table` command to solve this exercise.

`@pre_exercise_code`
```{r}
library(data.table); library(nycflights13); dt <- data.table(flights)
```

`@sample_code`
```{r}
dt
```

`@solution`
```{r}
n <- dt[, .N, by = origin]
```

`@sct`
```{r}
ex() %>% check_object("n") %>% check_equal()
```

---

## More Filters

```yaml
type: NormalExercise
xp: 100
key: 21de93a8b6
```

Count the number of flights in the `dt` dataset starting from `JFK` and heading to `LAX`, and store the result in the `n` variable! 

`@pre_exercise_code`
```{r}
library(data.table); library(nycflights13); dt <- data.table(flights)
```

`@sample_code`
```{r}
dt
```

`@solution`
```{r}
n <- dt[origin == 'JFK' & dest == 'LAX', .N]
```

`@sct`
```{r}
ex() %>% check_object("n") %>% check_equal()
```

---

## Filtered Averages

```yaml
type: NormalExercise
xp: 100
key: ce02261cf4
```

Compute the average air time of flights in the `dt` dataset leaving from `JFK` to `LAX`, and store the result in the `n` variable! 

`@hint`
You might have to get rid of the `NA`s before computing the `mean`, eg via adding `is.na` as an additional filter or using the `na.rm` argument of the `mean` function.

`@pre_exercise_code`
```{r}
library(data.table); library(nycflights13); dt <- data.table(flights)
```

`@sample_code`
```{r}
dt
```

`@solution`
```{r}
n <- dt[origin == 'JFK' & dest == 'LAX', mean(air_time, na.rm = TRUE)]
```

`@sct`
```{r}
ex() %>% check_object("n") %>% check_equal()
```


---

## Summaries

```yaml
type: NormalExercise
xp: 100
key: c9e11e6fb2
```

Compute the minimum and the maximum distances of flights in the `dt` dataset split by the origin airport, and store the result in the `n` variable! The resulting `data.table` object should have the following column names: `origin`, `min` and `max`, and store it in the `res` variable.

`@pre_exercise_code`
```{r}
library(data.table); library(nycflights13); dt <- data.table(flights)
```

`@sample_code`
```{r}
dt
```

`@solution`
```{r}
res <- dt[, list(
              min = min(distance), 
              max = max(distance)), by = origin]
```

`@sct`
```{r}
ex() %>% check_object("res") %>% check_equal()
```


---

## A More Complex Summary

```yaml
type: NormalExercise
xp: 100
key: a1f74e6bb0
```

Compute the minimum, the (arithmetic) average, the standard deviation and the max of the air time of flights in the `dt` dataset split by the origin airport, and store the result in the `res` variable! The resulting `data.table` object should have the following column names: `airport`, `min`, `avg`, `stddev` and `max`.

`@pre_exercise_code`
```{r}
library(data.table); library(nycflights13); dt <- data.table(flights)
```

`@sample_code`
```{r}
dt
```

`@solution`
```{r}
res <- dt[, list(
              min = min(air_time, na.rm = TRUE), 
              avg = mean(air_time, na.rm = TRUE),
              stddev = sd(air_time, na.rm = TRUE),
              max = max(air_time, na.rm = TRUE)), by = list(airport = origin)]
```

`@sct`
```{r}
ex() %>% check_function("min") %>% check_arg("na.rm") %>% check_equal()
ex() %>% check_object("res") %>% check_equal()
```


---

## A Barplot

```yaml
type: NormalExercise
xp: 100
key: 1e38da7d28
```

Use the `ggplot2` package to generate a barplot on the number of flights (in the `dt` dataset) per the origin airport.

`@pre_exercise_code`
```{r}
library(data.table); library(nycflights13); dt <- data.table(flights); library(ggplot2)
```

`@sample_code`
```{r}
dt
```

`@solution`
```{r}
ggplot(dt, aes(origin)) + geom_bar()
```

`@sct`
```{r}
ex() %>% {
  check_function(., "ggplot") %>% check_arg("data") %>% check_equal()
  check_function(., "aes") %>% {
    check_arg(., "x") %>% check_equal(eval = FALSE) 
  }
  check_function(., "geom_bar")
}
```
