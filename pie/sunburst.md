## SUNBURST
- package: sunburstR
- data: mtcars  
<pre>
library(tidyverse) 
library(sunburstR)  
</pre>

### Make the Data sunburst-able
<pre>
df_sb <- mtcars %>%
  select(am, gear, carb) %>%
  group_by(am, gear, carb) %>%
  summarise(num = n()) %>%  
  mutate(path = paste(am, gear, carb, sep="-"))
  #create a sunburst-able variable
</pre>
### Create a Sunburst
<pre>
df_sb %>%
  ungroup() 
  #ungroup before selecting necessary columns
  select(path, num) %>% 
  sunburst()
  #this is a html widget
</pre>

