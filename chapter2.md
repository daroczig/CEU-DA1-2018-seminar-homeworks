---
title: 'Week 2'
description: 'If you get stuck, I suggest revisiting the R sources of the <a href="https://github.com/daroczig/CEU-R-lab">"Data Analytis 1a - Exploration" class on GitHub</a>, and also feel free to check other classes on DataCamp!'
---

## Loading data

```yaml
type: MultipleChoiceExercise
xp: 50
key: 1dd5a88e66
```

Which R function can load a text file with comma-separated values?

`@instructions`
- read.table
- read_excel
- Read.csv
- load.csv

`@hint`
Remember, R commands are case sensitive! If a function is not familiar, feel free to check the manual with `?`.

`@sct`
```{r}
ex() %>% check_mc(correct = 1)
```

---

## The structure of an R object

```yaml
type: NormalExercise
xp: 50
key: d4c6bb60e7
```

Check the structure of the already loaded `mtcars` object!


`@sample_code`
```{r}
mtcars
```

`@hint`
Use the `str` function.


`@solution`
```{r}
str(mtcars)
```

`@sct`
```{r}
ex() %>% check_function("str") %>% check_arg(., "object") %>% check_equal()
```

---

## Matrix indexing

```yaml
type: NormalExercise
xp: 50
key: 4efeb6f04d
```

Save the weight of the Toyota Corolla into a variable called `tcw`!


`@sample_code`
```{r}
mtcars
```

`@solution`
```{r}
tcw <- mtcars[20, 'wt']
```

`@sct`
```{r}
ex() %>% check_object("tcw")
ex() %>% check_object("tcw") %>% check_equal()
```

---

## Number of variables

```yaml
type: NormalExercise
xp: 50
key: 79d051bb76
```

Count the number of columns in `mtcars` store in variable `mcols`!


`@sample_code`
```{r}
mtcars
```

`@hint`
Use the `ncol` function to count columns.

`@solution`
```{r}
mcols <- ncol(mtcars)
```

`@sct`
```{r}
ex() %>% check_object("mcols")
ex() %>% check_object("mcols") %>% check_equal()
ex() %>% check_function("ncol") %>% check_arg(., "x") %>% check_equal()
```

---

## Filtering 1

```yaml
type: NormalExercise
xp: 100
```

Compute the number of rows in `mtcars` with 4 gears and store in variable `m4g`!


`@sample_code`
```{r}
mtcars
```

`@hint`
Use the `nrow` function to count rows and `subset` to filter the data.

`@solution`
```{r}
m4g <- nrow(subset(mtcars, gear == 4))
```

`@sct`
```{r}
ex() %>% check_object("m4g")
ex() %>% check_object("m4g") %>% check_equal()
ex() %>% check_function("nrow") %>% check_arg(., "x") %>% check_equal()
```

---

## Filtering 2

```yaml
type: NormalExercise
xp: 100
```

Compute the maximum weight of cars in `mtcars` with 4 gears and store in variable `x`!


`@sample_code`
```{r}
mtcars
```

`@solution`
```{r}
x <- max(subset(mtcars, gear == 4)$wt)
```

`@sct`
```{r}
ex() %>% check_object("x")
ex() %>% check_object("x") %>% check_equal()
ex() %>% check_function("max") %>% check_arg(., "...") %>% check_equal()
```

---

## Filtering 3

```yaml
type: NormalExercise
xp: 100
```

Compute the minimum number of carburetors of cars in `mtcars` with 4 gears and store in variable `x`!


`@sample_code`
```{r}
mtcars
```

`@solution`
```{r}
x <- min(subset(mtcars, gear == 4)$carb)
```

`@sct`
```{r}
ex() %>% check_object("x")
ex() %>% check_object("x") %>% check_equal()
ex() %>% check_function("min") %>% check_arg(., "...") %>% check_equal()
ex() %>% check_function("subset") %>% check_arg(., "x") %>% check_equal()
```

---

## Filtering 4

```yaml
type: NormalExercise
xp: 100
```

Compute the median of the gross horsepower of cars in `mtcars` that are heavier than 1987 lbs in variable `x`!

`@sample_code`
```{r}
mtcars
```

`@solution`
```{r}
x <- median(subset(mtcars, wt > 1.987)$hp)
```

`@sct`
```{r}
ex() %>% check_object("x")
ex() %>% check_object("x") %>% check_equal()
ex() %>% check_function("median") %>% check_arg(., "x") %>% check_equal()
ex() %>% check_function("subset") %>% check_arg(., "x") %>% check_equal()
```

---

## Summaries

```yaml
type: NormalExercise
xp: 100
```

Store the weight of the heaviest car from `mtcars` in the `heavy` variable.

`@sample_code`
```{r}
mtcars
```

`@solution`
```{r}
heavy <- max(mtcars$wt)
```

`@sct`
```{r}
ex() %>% check_object("heavy")
ex() %>% check_object("heavy") %>% check_equal()
ex() %>% check_function("max") %>% check_arg(., "...") %>% check_equal()
```

---

## Something new

```yaml
type: NormalExercise
xp: 150
```

Store the name of the heaviest car from `mtcars` in the `heavy_car` variable.

`@sample_code`
```{r}
heavy <- max(mtcars$wt)
mtcars
```

`@solution`
```{r}
heavy_car <- row.names(subset(mtcars, wt == heavy))
```

`@sct`
```{r}
ex() %>% check_object("heavy")
ex() %>% check_object("heavy_car")
ex() %>% check_object("heavy_car") %>% check_equal()
ex() %>% check_function("max") %>% check_arg(., "...") %>% check_equal()
ex() %>% check_function("subset") %>% check_arg(., "x") %>% check_equal()
ex() %>% check_function("row.names") %>% check_arg(., "x") %>% check_equal()
```

---

## Something newer

```yaml
type: NormalExercise
xp: 150
```

Store the name of the heaviest car from `mtcars` in the `heavy_car` variable without using `subset` and `max`.

`@sample_code`
```{r}
mtcars
```

`@hint`
Have you looked up the docs of `which.max`?

`@solution`
```{r}
heavy_car <- row.names(mtcars)[which.max(mtcars$wt)]
```

`@sct`
```{r}
ex() %>% check_object("heavy")
ex() %>% check_object("heavy_car")
ex() %>% check_object("heavy_car") %>% check_equal()
ex() %>% check_function("row.names") %>% check_arg(., "x") %>% check_equal()
ex() %>% check_function("which.max") %>% check_arg(., "x") %>% check_equal()
```
