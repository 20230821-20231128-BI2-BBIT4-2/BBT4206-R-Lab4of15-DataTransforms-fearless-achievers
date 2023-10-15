Business Intelligence Project
================
<Adrianna Bitutu Ndubi>
<15 October 2023>

- [134126, Ndubi Adrianna](#student-details)
- [Setup Chunk](#setup-chunk)
- [Understanding the Dataset (Exploratory Data Analysis
  (EDA))](#understanding-the-dataset-exploratory-data-analysis-eda)
  - [Loading the Dataset](#loading-the-dataset)
    - [Source:student_performance_dataset(BI 2 Google Drive)](#source)
    - [Reference:](#reference)

# Student Details

|                                              |     |
|----------------------------------------------|-----|
| 134126                      | …   |
| Ndubi Adrianna Bitutu                            | …   |
| Fearless Achievers                          | …   |
| **BI Project Group Name/ID (if applicable)** | …   |

# Setup Chunk

**Note:** the following KnitR options have been set as the global
defaults: <BR>
`knitr::opts_chunk$set(echo = TRUE, warning = FALSE, eval = TRUE, collapse = FALSE, tidy = TRUE)`.

More KnitR options are documented here
<https://bookdown.org/yihui/rmarkdown-cookbook/chunk-options.html> and
here <https://yihui.org/knitr/options/>.

# Understanding the Dataset (Exploratory Data Analysis (EDA))

## Loading the Dataset

### Source:

The dataset that was used can be downloaded here: *\<https://docs.google.com/spreadsheets/d/1LwVZIklzc0JvyVPQul9CxGnu2spipZjXaCO_Zv8H2sc/edit#gid=2007896421\>*

### Reference:

*\<Cite the dataset here using APA\>  
Refer to the APA 7th edition manual for rules on how to cite datasets:
<https://apastyle.apa.org/style-grammar-guidelines/references/examples/data-set-references>*

``` r
library(readr)

# Provide the executable R code inside the various code chunks as guided by the
# lab work.

### PCA for Dimensionality Reduction on the student_perfomance_dataset Dataset ----
summary(student_performance_dataset)

model_of_the_transform <- preProcess(student_performance_dataset,
                                     method = c("scale", "center", "pca"))
print(model_of_the_transform)
student_performance_dataset_pca_transform <- predict(model_of_the_transform, # nolint
                                                    student_perfomance_dataset)
summary(student_perfomance_dataset_pca_transform)``

summary(student_performance_dataset)

# Calculate the skewness before the Yeo-Johnson transform
sapply(student_performance_dataset[, 1:8],  skewness, type = 2)

# Plot a histogram to view the skewness before the Yeo-Johnson transform
par(mfrow = c(1, 8))
for (i in 1:8) {
  hist(student_performance_dataset[, i], main = names(student_performance_dataset)[i])
}

model_of_the_transform <- preProcess(student_performance_dataset,
                                     method = c("YeoJohnson"))
print(model_of_the_transform)
student_performance_dataset_yeo_johnson_transform <- predict(model_of_the_transform, # nolint
                                                             student_performance_dataset)

# AFTER
summary(student_performance_dataset_yeo_johnson_transform)

# Calculate the skewness after the Yeo-Johnson transform
sapply(student_performance_dataset_yeo_johnson_transform[, 1:8],  skewness, type = 2)

# Plot a histogram to view the skewness after the Yeo-Johnson transform
par(mfrow = c(1, 8))
for (i in 1:8) {
  hist(student_performance_dataset_yeo_johnson_transform[, i],
       main = names(student_performance_dataset_yeo_johnson_transform)[i])
}



