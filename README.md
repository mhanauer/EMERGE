---
title: "EMERGE"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Data loading
```{r}
setwd("S:/Indiana Research & Evaluation/EMERGE CRR/Data")
base = read.csv("base.csv", header = TRUE)
month6 = read.csv("month6.csv", header = TRUE)
```
Merge on matched pairs
```{r}
colnames(base)[1] = "ClientID"
all_dat = merge(base, month6, by = "ClientID", all.y = TRUE)
all_dat$ClientID == month6$ClientID
all_dat_complete = na.omit(all_dat)
dim(all_dat_complete)
head(all_dat_complete)
write.csv(all_dat_complete, "all_dat_complete.csv", row.names = FALSE)
```

