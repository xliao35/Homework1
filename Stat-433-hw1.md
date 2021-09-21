Homework1
================
Xucen Liao
9/21/2021

``` r
#checking condition
#install.packages('xml2')
library('xml2')
```

    ## Warning: package 'xml2' was built under R version 3.6.2

``` r
#install.packages("rvest")
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.6.2

``` r
#Webscrap
page <- read_html("https://guide.wisc.edu/faculty/")
faculty = page %>% html_nodes(".uw-people") %>% html_elements("p") %>% html_text2()

name = 0
position = 0
department = 0
degree = 0
for (i in seq(1:length(faculty))){
  information = strsplit(faculty[i],"\n")
  name = append(name,information[[1]][1])
  position = append(position,information[[1]][2])
  department = append(department,information[[1]][3])
  degree = append(degree,information[[1]][4])
}  
table = data.frame(name, position, department, degree)  
table = table[-c(1),]
```
