---
title: 'Week 5'
description: 'If you get stuck, I suggest revisiting the R sources of the <a href="https://github.com/daroczig/CEU-R-lab">"Data Analytics 1a - Exploration" class on GitHub</a>, and also feel free to check other classes on DataCamp! And in case you really get stuck ... feel free to open a ticket on GitHub and ask for help.'
---

## Creating data.table objects

```yaml
type: NormalExercise
xp: 50
key: 68ef0e987f
```

- Load the `ggplot2` package
- Check the structure of the `diamonds` dataset
- Load the `data.table` package
- Create a new `data.table` object called `dt` with the content of the `diamonds` dataset


`@sample_code`
```{r}
## R is great!
```

`@solution`
```{r}
library(ggplot2)
str(diamonds)
library(data.table)
dt <- data.table(diamonds)
```

`@sct`
```{r}
ex() %>% check_function("str") %>% check_arg("object") %>% check_equal()
ex() %>% check_object("dt") %>% check_equal()
```

---

## A Barplot

```yaml
type: NormalExercise
xp: 100
key: 69ec547f26
```

Use the `ggplot2` package to generate a barplot on the number of diamonds (in the `dt` dataset) per the `cut` quality.

`@pre_exercise_code`
```{r}
library(data.table)
library(ggplot2)
dt <- data.table(diamonds)
```

`@sample_code`
```{r}
str(dt)
```

`@solution`
```{r}
ggplot(dt, aes(cut)) + geom_bar()
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

---

## Another Barplot

```yaml
type: NormalExercise
xp: 100
```

Use the `ggplot2` package to generate a stacked barplot on the number of diamonds per the `cut` quality (x axis) and `clarity` (represented with the color of the bar section).

`@hint`
Specify the `fill` aesthetic to define the color breakdown of a bar (eg `clarity`).

`@pre_exercise_code`
```{r}
library(data.table)
library(ggplot2)
dt <- data.table(diamonds)
```

`@sample_code`
```{r}
str(dt)
```

`@solution`
```{r}
ggplot(dt, aes(cut, fill = clarity)) + geom_bar()
```

`@sct`
```{r}
ex() %>% {
  check_function(., "ggplot") %>% check_arg("data") %>% check_equal()
  check_function(., "aes") %>% {
    check_arg(., "x") %>% check_equal(eval = FALSE) 
    check_arg(., "fill") %>% check_equal(eval = FALSE) 
  }
  check_function(., "geom_bar")
}
```

---

## Boxplot

```yaml
type: NormalExercise
xp: 100
```

Use the `ggplot2` package to generate a boxplot on the prices split by the `cut` quality.

`@pre_exercise_code`
```{r}
library(data.table)
library(ggplot2)
dt <- data.table(diamonds)
```

`@sample_code`
```{r}
str(dt)
```

`@solution`
```{r}
ggplot(dt, aes(cut, price)) + geom_boxplot()
```

`@sct`
```{r}
ex() %>% {
  check_function(., "ggplot") %>% check_arg("data") %>% check_equal()
  check_function(., "aes") %>% {
    check_arg(., "x") %>% check_equal(eval = FALSE) 
    check_arg(., "y") %>% check_equal(eval = FALSE) 
  }
  check_function(., "geom_boxplot")
}
```

---

## Scatterplot

```yaml
type: NormalExercise
xp: 100
```

Use the `ggplot2` package to generate a scatterplot on the weight and the prices of the diamonds.

`@hint`
The weight is recorded in the `carat` column. Use `carat` on the `x` axis to visualize the `price` as a function of that.

`@pre_exercise_code`
```{r}
library(data.table)
library(ggplot2)
dt <- data.table(diamonds)
```

`@sample_code`
```{r}
str(dt)
```

`@solution`
```{r}
ggplot(dt, aes(carat, price)) + geom_point()
```

`@sct`
```{r}
ex() %>% {
  check_function(., "ggplot") %>% check_arg("data") %>% check_equal()
  check_function(., "aes") %>% {
    check_arg(., "x") %>% check_equal(eval = FALSE) 
    check_arg(., "y") %>% check_equal(eval = FALSE) 
  }
  check_function(., "geom_point")
}
```

---

## Fitting model

```yaml
type: NormalExercise
xp: 100
```

Use the `ggplot2` package to generate a scatterplot on the weight and the prices of the diamonds -- just like in the previous exercise. But add a model on the top of the points as a new layer.

`@hint`
After specifying the `geom_point()` layer, use the `geom_smooth` function as well.

`@pre_exercise_code`
```{r}
library(data.table)
library(ggplot2)
dt <- data.table(diamonds)
```

`@sample_code`
```{r}
str(dt)
```

`@solution`
```{r}
ggplot(dt, aes(carat, price)) + geom_point() + geom_smooth()
```

`@sct`
```{r}
ex() %>% {
  check_function(., "ggplot") %>% check_arg("data") %>% check_equal()
  check_function(., "aes") %>% {
    check_arg(., "x") %>% check_equal(eval = FALSE) 
    check_arg(., "y") %>% check_equal(eval = FALSE) 
  }
  check_function(., "geom_point")
  check_function(., "geom_smooth")
}
```

---

## Fitting a linear model

```yaml
type: NormalExercise
xp: 100
```

Use the `ggplot2` package to generate a scatterplot with a trend line on the weight and the prices of the diamonds -- just like in the previous exercise, but add a *linear* model on the top of the points this time.

`@hint`
Look at the `method` argument of the `geom_smooth` function!

`@pre_exercise_code`
```{r}
library(data.table)
library(ggplot2)
dt <- data.table(diamonds)
```

`@sample_code`
```{r}
str(dt)
```

`@solution`
```{r}
ggplot(dt, aes(carat, price)) + geom_point() + geom_smooth(method = 'lm')
```

`@sct`
```{r}
ex() %>% {
  check_function(., "ggplot") %>% check_arg("data") %>% check_equal()
  check_function(., "aes") %>% {
    check_arg(., "x") %>% check_equal(eval = FALSE) 
    check_arg(., "y") %>% check_equal(eval = FALSE) 
  }
  check_function(., "geom_point")
  check_function(., "geom_smooth") %>% check_arg("method")
}
```


---

## Faceting

```yaml
type: NormalExercise
xp: 100
```

Use the `ggplot2` package to generate a boxplot on the prices split by the `cut` quality -- broken down by the color of the diamonds in subplots.

`@hint`
Use `facet_wrap` to split into subplots.

`@pre_exercise_code`
```{r}
library(data.table)
library(ggplot2)
dt <- data.table(diamonds)
```

`@sample_code`
```{r}
str(dt)
```

`@solution`
```{r}
ggplot(dt, aes(cut, price)) + geom_boxplot() + facet_wrap(~color)
```

`@sct`
```{r}
ex() %>% {
  check_function(., "ggplot") %>% check_arg("data") %>% check_equal()
  check_function(., "aes") %>% {
    check_arg(., "x") %>% check_equal(eval = FALSE) 
    check_arg(., "y") %>% check_equal(eval = FALSE) 
  }
  check_function(., "geom_boxplot")
  check_function(., "facet_wrap") %>% check_arg("facets")
}
```



---

## A complex example

```yaml
type: NormalExercise
xp: 200
```

Use the `ggplot2` package to generate a barplot on the prices with a custom split.

- Create a `dt` object from `diamonds` as a `data.table` object
- Create a new variable in `dt` called `pricecat`: using the "cheap" label on diamonds with less than $1,000 price, "expensive" on diamonds above $10,000 and "average" on all other diamonds
- Generate a barplot on this new variable with the correct order of the bars

`@hint`
Use `facet_wrap` to split into subplots.

`@pre_exercise_code`
```{r}
library(data.table)
library(ggplot2)
```

`@sample_code`
```{r}
dt <- data.table(diamonds)
```

`@solution`
```{r}
dt <- data.table(diamonds)
dt[, pricecat := cut(price, c(0, 1000, 10000, Inf), labels = c('cheap', 'average', 'expensive'))]
ggplot(dt, aes(pricecat)) + geom_bar()
```

`@sct`
```{r}
ex() %>% check_function("cut") %>% check_arg("labels") %>% check_equal()
ex() %>% {
  check_function(., "ggplot") %>% check_arg("data") %>% check_equal()
  check_function(., "aes") %>% {
    check_arg(., "x") %>% check_equal(eval = FALSE) 
  }
  check_function(., "geom_bar")
}
```
