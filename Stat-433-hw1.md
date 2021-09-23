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

2.  Draw plot

``` r
# the number of faculty who is in the department of art
a = sum(table$department == "Art") #52
# the number of faculty who is in the department of Educational Psychology
b = sum(table$department == "Educational Psychology") #35
# the number of faculty who is in the department of Computer Science
c = sum(table$department == "Computer Sciences") #65
#vector = c(a,b,c)
barplot(c(a,b,c),main = "Number of three departments", ylab = "total number", names.arg = c("Art","Educational Psychology","Computer Sciences"))
```

![](Stat-433-hw1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

github website: <https://github.com/xliao35/Homework1.git>
