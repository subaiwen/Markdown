## SUNBURST
- package: sunburstR

- data: mtcars  

```R
library(tidyverse) 
library(sunburstR)  
```

### Make the Data sunburst-able
```R
df_sb <- mtcars %>%
  select(am, gear, carb) %>%
  group_by(am, gear, carb) %>%
  summarise(num = n()) %>%  
  mutate(path = paste(am, gear, carb, sep="-")) #create a sunburst-able variable
```

### Create a Sunburst
```R
df_sb %>%
  ungroup()  #ungroup before selecting necessary columns
  select(path, num) %>% 
  sunburst() #this is a html widget

```

![sunburst](C:\Users\igola\Desktop\sunburst.png)