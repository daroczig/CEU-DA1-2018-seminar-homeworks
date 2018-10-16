---
title: 'Week 5'
description: 'If you get stuck, I suggest revisiting the R sources of the <a href="https://github.com/daroczig/CEU-R-lab">"Data Analytis 1a - Exploration" class on GitHub</a>, and also feel free to check other classes on DataCamp! And in case you really get stuck ... feel free to open a ticket on GitHub and ask for help.'
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

