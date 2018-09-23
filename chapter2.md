---
title: 'Week 2'
description: 'If you get stuck, I suggest revisiting the R sources of the <a href="https://github.com/daroczig/CEU-R-lab">"Data Analytis 1a - Exploration" class on GitHub</a>, and also feel free to check other classes on DataCamp!'
---

## Loading data

```yaml
type: MultipleChoiceExercise
xp: 50
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
```

---

## Filtering

```yaml
type: NormalExercise
xp: 50
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
```

---

