# data_curation

---
title: "Soil nutrients in Agua Salud Plantations"
author: "Gabi"
date: "7/5/2020"
output: html_document
draft: true 
---

## Introduction 

  * Use and Importance of native tree species for timber plantations. 


  * _Dalbergia_ and _Terminalia_ use for timber plantations and specific nutrient acquisition and growth.

  _Dalbergia retusa_ and _Terminalia amazonia_ are two neotropical species used for timber extraction (Moya & Muñoz, 2010).
  
  | ![](https://pfaf.org/Admin/PlantImages/Dalbergia-retusa-2.jpg) | ![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Terminalia_argentea.jpg/220px-Terminalia_argentea.jpg) |
|:---:|:---:|
| *Dalbergia retusa* | *Terminalia amazonia* |
   
  

  * Nutrient facilitation by nitrogen fixers. 

  * Hypothesis
  
## Methods 

### Study site 

This study was conducted in the native species plantation of the [Agua Salud](https://striresearch.si.edu/smartreforestation/#)  project in the Panama Canal watershed (9°13′N, 79°47′W, 330m a.s.l.), administered by the Smithsonian Tropical Research Institute

### Experimental desing 

Our research focuses on 33 plots with the mixtures of two target species treatment, being _Terminalia amazonia_ and _Dalbergia retusa_ the studied species. Each of these plots are divided by 15 x 15 tree rows, were the first row is composed of groups of three individuals of _T. amazonia_ alternated by three _D. retusa’s_ individuals. The next row is composed of the alternate of an individual of each species, where each individual is separated by three meters. This design creates hexagonal subplots of a _T. amazonia_ encircled by six _D. retusa_ and vice versa, allowing to test the tree species interactions. (FIG X). The treatment (a) has four replicates of D.retusa in the center, and treartment (b) has four replicates of centered T.amazonia. 

![](C:/Users/Gabriela/Desktop/Data curation/experimental-desing.png)

Figure 1. Two species mixture design with version “a” and “b”.  Nine species groups are numbered in center of plot.  


## Results

```{r, anova, cache=TRUE, echo = FALSE}

library("ggplot2")
library("dplyr")
library("plotrix") 
library("psych")
library("pgirmess")
library("lsr")

TODOS <- read.csv(file = "All_DALBRE_TERMAM.csv")

##------------------   AMMONIUM 

group_by(TODOS, Species) %>%
  summarise(
    count = n(),
    mean = mean(Ammonium, na.rm = TRUE),
    sd = sd(Ammonium, na.rm = TRUE), 
    SE = std.error(Ammonium, na.rm = TRUE)
  )


plot_AmmTodos <-ggplot(TODOS, aes(x=Species, y=Ammonium, fill=Species )) + 
  geom_boxplot ()
plot_AmmTodos +  scale_fill_grey() + theme_classic() + 
  labs(y="Ammonium (mgN/L)", x="Treatment")

```
