Business Intelligence Project
================
<Joy Jerono>
\<16th Oct\>

- [Student Details](#student-details)
- [Setup Chunk](#setup-chunk)
- [Understanding the Dataset (Exploratory Data Analysis
  (EDA))](#understanding-the-dataset-exploratory-data-analysis-eda)
  - [Loading the Dataset](#loading-the-dataset)
    - [Source:](#source)
    - [Reference:](#reference)
  - [dplyr - For data manipulation —-](#dplyr---for-data-manipulation--)
  - [ggplot2 - For data visualizations using the Grammar for Graphics
    package
    —-](#ggplot2---for-data-visualizations-using-the-grammar-for-graphics-package--)
  - [ggrepel - Additional options for the Grammar for Graphics package
    —-](#ggrepel---additional-options-for-the-grammar-for-graphics-package--)
  - [ggraph - Additional options for the Grammar for Graphics package
    —-](#ggraph---additional-options-for-the-grammar-for-graphics-package--)
  - [tidytext - For text mining —-](#tidytext---for-text-mining--)
  - [tidyr - To tidy messy data —-](#tidyr---to-tidy-messy-data--)
  - [widyr - To widen, process, and re-tidy a dataset
    —-](#widyr---to-widen-process-and-re-tidy-a-dataset--)
  - [gridExtra - to arrange multiple grid-based plots on a page
    —-](#gridextra---to-arrange-multiple-grid-based-plots-on-a-page--)
  - [knitr - for dynamic report generation
    —-](#knitr---for-dynamic-report-generation--)
  - [kableExtra - for nicely formatted output tables
    —-](#kableextra---for-nicely-formatted-output-tables--)
  - [formattable - To create a formattable object
    —-](#formattable---to-create-a-formattable-object--)
- [A formattable object is an object to which a formatting function and
  related](#a-formattable-object-is-an-object-to-which-a-formatting-function-and-related)
- [attributes are attached.](#attributes-are-attached)
  - [circlize - To create a cord diagram or visualization
    —-](#circlize---to-create-a-cord-diagram-or-visualization--)
- [by Gu et al. (2014)](#by-gu-et-al-2014)
  - [memery - For creating data analysis related memes
    —-](#memery---for-creating-data-analysis-related-memes--)
- [The memery package generates internet memes that optionally include
  a](#the-memery-package-generates-internet-memes-that-optionally-include-a)
- [superimposed inset plot and other atypical features, combining the
  visual](#superimposed-inset-plot-and-other-atypical-features-combining-the-visual)
- [impact of an attention-grabbing meme with graphic results of data
  analysis.](#impact-of-an-attention-grabbing-meme-with-graphic-results-of-data-analysis)
  - [magick - For image processing in R
    —-](#magick---for-image-processing-in-r--)
  - [yarrr - To create a pirate plot
    —-](#yarrr---to-create-a-pirate-plot--)
  - [radarchart - To create interactive radar charts using ChartJS
    —-](#radarchart---to-create-interactive-radar-charts-using-chartjs--)
  - [igraph - To create ngram network diagrams
    —-](#igraph---to-create-ngram-network-diagrams--)
  - [wordcloud2 - For creating wordcloud by using ’wordcloud2.JS
    —-](#wordcloud2---for-creating-wordcloud-by-using-wordcloud2js--)
  - [readr - Load datasets from CSV files
    —-](#readr---load-datasets-from-csv-files--)

# Student Details

|                       |     |
|-----------------------|-----|
| *Student ID Number*   | …   |
| Micheal Achoki 132434 |     |

Joy Jerono 132502 Oscar Frankline 134981 Adrianna Bitutu 134126 Paul
Wesley 135732 \| … \| \| BBIT 4B \| … \| \| Fearless Achievers \| … \|

# Setup Chunk

*Note:* the following KnitR options have been set as the global
defaults: <BR>
`knitr::opts_chunk$set(echo = TRUE, warning = FALSE, eval = TRUE, collapse = FALSE, tidy = TRUE)`.

More KnitR options are documented here
<https://bookdown.org/yihui/rmarkdown-cookbook/chunk-options.html> and
here <https://yihui.org/knitr/options/>.

{r setup, include=FALSE} library(formatR) knitr::opts_chunk\$set(
warning = FALSE, collapse = FALSE )

# Understanding the Dataset (Exploratory Data Analysis (EDA))

## Loading the Dataset

### Source:

The dataset that was used can be downloaded here: \<<a
href="https://github.com/20230821-20231128-BI2-BBIT4-2/BBT4206-R-Lab4of15-DataTransforms-fearless-achievers/blob/main/data/student_performance_dataset.csv\"
class="uri">https://github.com/20230821-20231128-BI2-BBIT4-2/BBT4206-R-Lab4of15-DataTransforms-fearless-achievers/blob/main/data/student_performance_dataset.csv\</a>\>

### Reference:

*\<Cite the dataset here using APA\>  
Refer to the APA 7th edition manual for rules on how to cite datasets:
<https://apastyle.apa.org/style-grammar-guidelines/references/examples/data-set-references>*

{r Dataset Loader} library(readr)

.libPaths() lapply(.libPaths(), list.files) if
(require(“languageserver”)) { require(“languageserver”) } else {
install.packages(“languageserver”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } if (!is.element(“renv”,
installed.packages()\[, 1\])) { \# install.packages(“renv”, dependencies
= TRUE, repos = “<https://cloud.r-project.org>” \# nolint \# }

lapply(.libPaths(), list.files) if (!is.element(“languageserver”,
installed.packages()\[, 1\])) { install.packages(“languageserver”,
dependencies = TRUE, repos = “<https://cloud.r-project.org>”) }
require(“languageserver”)

## dplyr - For data manipulation —-

if (!is.element(“dplyr”, installed.packages()\[, 1\])) {
install.packages(“dplyr”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“dplyr”)

## ggplot2 - For data visualizations using the Grammar for Graphics package —-

if (!is.element(“ggplot2”, installed.packages()\[, 1\])) {
install.packages(“ggplot2”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“ggplot2”)

## ggrepel - Additional options for the Grammar for Graphics package —-

if (!is.element(“ggrepel”, installed.packages()\[, 1\])) {
install.packages(“ggrepel”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“ggrepel”)

## ggraph - Additional options for the Grammar for Graphics package —-

if (!is.element(“ggraph”, installed.packages()\[, 1\])) {
install.packages(“ggraph”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“ggraph”)

## tidytext - For text mining —-

if (!is.element(“tidytext”, installed.packages()\[, 1\])) {
install.packages(“tidytext”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“tidytext”)

## tidyr - To tidy messy data —-

if (!is.element(“tidyr”, installed.packages()\[, 1\])) {
install.packages(“tidyr”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“tidyr”)

## widyr - To widen, process, and re-tidy a dataset —-

if (!is.element(“widyr”, installed.packages()\[, 1\])) {
install.packages(“widyr”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“widyr”)

## gridExtra - to arrange multiple grid-based plots on a page —-

if (!is.element(“gridExtra”, installed.packages()\[, 1\])) {
install.packages(“gridExtra”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“gridExtra”)

## knitr - for dynamic report generation —-

if (!is.element(“knitr”, installed.packages()\[, 1\])) {
install.packages(“knitr”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“knitr”)

## kableExtra - for nicely formatted output tables —-

if (!is.element(“kableExtra”, installed.packages()\[, 1\])) {
install.packages(“kableExtra”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“kableExtra”)

## formattable - To create a formattable object —-

# A formattable object is an object to which a formatting function and related

# attributes are attached.

if (!is.element(“formattable”, installed.packages()\[, 1\])) {
install.packages(“formattable”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“formattable”)

## circlize - To create a cord diagram or visualization —-

# by Gu et al. (2014)

if (!is.element(“circlize”, installed.packages()\[, 1\])) {
install.packages(“circlize”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“circlize”)

## memery - For creating data analysis related memes —-

# The memery package generates internet memes that optionally include a

# superimposed inset plot and other atypical features, combining the visual

# impact of an attention-grabbing meme with graphic results of data analysis.

if (!is.element(“memery”, installed.packages()\[, 1\])) {
install.packages(“memery”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“memery”)

## magick - For image processing in R —-

if (!is.element(“magick”, installed.packages()\[, 1\])) {
install.packages(“magick”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“magick”)

## yarrr - To create a pirate plot —-

if (!is.element(“yarrr”, installed.packages()\[, 1\])) {
install.packages(“yarrr”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“yarrr”)

## radarchart - To create interactive radar charts using ChartJS —-

if (!is.element(“radarchart”, installed.packages()\[, 1\])) {
install.packages(“radarchart”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“radarchart”)

## igraph - To create ngram network diagrams —-

if (!is.element(“igraph”, installed.packages()\[, 1\])) {
install.packages(“igraph”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“igraph”)

## wordcloud2 - For creating wordcloud by using ’wordcloud2.JS —-

if (!is.element(“wordcloud2”, installed.packages()\[, 1\])) {
install.packages(“wordcloud2”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“wordcloud2”)

## readr - Load datasets from CSV files —-

if (!is.element(“readr”, installed.packages()\[, 1\])) {
install.packages(“readr”, dependencies = TRUE, repos =
“<https://cloud.r-project.org>”) } require(“readr”)

\##load dataset student_performance_dataset \<- readr::read_csv(
“data/20230412-20230719-BI1-BBIT4-1-StudentPerformanceDataset.CSV”, \#
nolint col_types = readr::cols( class_group = readr::col_factor(levels =
c(“A”, “B”, “C”)), gender = readr::col_factor(levels = c(“1”, “0”)), YOB
= readr::col_date(format = “%Y”), regret_choosing_bi =
readr::col_factor(levels = c(“1”, “0”)), drop_bi_now =
readr::col_factor(levels = c(“1”, “0”)), motivator =
readr::col_factor(levels = c(“1”, “0”)), read_content_before_lecture =
readr::col_factor(levels = c(“1”, “2”, “3”, “4”, “5”)),
anticipate_test_questions = readr::col_factor(levels = c(“1”, “2”, “3”,
“4”, “5”)), answer_rhetorical_questions = readr::col_factor(levels =
c(“1”, “2”, “3”, “4”, “5”)), find_terms_I_do_not_know =
readr::col_factor(levels = c(“1”, “2”, “3”, “4”, “5”)),
copy_new_terms_in_reading_notebook = readr::col_factor(levels = c(“1”,
“2”, “3”, “4”, “5”)), take_quizzes_and_use_results =
readr::col_factor(levels = c(“1”, “2”, “3”, “4”, “5”)),
reorganise_course_outline = readr::col_factor(levels = c(“1”, “2”, “3”,
“4”, “5”)), write_down_important_points = readr::col_factor(levels =
c(“1”, “2”, “3”, “4”, “5”)), space_out_revision =
readr::col_factor(levels = c(“1”, “2”, “3”, “4”, “5”)),
studying_in_study_group = readr::col_factor(levels = c(“1”, “2”, “3”,
“4”, “5”)), schedule_appointments = readr::col_factor(levels = c(“1”,
“2”, “3”, “4”, “5”)), goal_oriented = readr::col_factor(levels = c(“1”,
“0”)), spaced_repetition = readr::col_factor(levels = c(“1”, “2”, “3”,
“4”)), testing_and_active_recall = readr::col_factor(levels = c(“1”,
“2”, “3”, “4”)), interleaving = readr::col_factor(levels = c(“1”, “2”,
“3”, “4”)), categorizing = readr::col_factor(levels = c(“1”, “2”, “3”,
“4”)), retrospective_timetable = readr::col_factor(levels = c(“1”, “2”,
“3”, “4”)), cornell_notes = readr::col_factor(levels = c(“1”, “2”, “3”,
“4”)), sq3r = readr::col_factor(levels = c(“1”, “2”, “3”, “4”)), commute
= readr::col_factor(levels = c(“1”, “2”, “3”, “4”)), study_time =
readr::col_factor(levels = c(“1”, “2”, “3”, “4”)), repeats_since_Y1 =
readr::col_integer(), paid_tuition = readr::col_factor(levels = c(“0”,
“1”)), free_tuition = readr::col_factor(levels = c(“0”, “1”)),
extra_curricular = readr::col_factor(levels = c(“0”, “1”)),
sports_extra_curricular = readr::col_factor(levels = c(“0”, “1”)),
exercise_per_week = readr::col_factor(levels = c(“0”, “1”, “2”, “3”)),
meditate = readr::col_factor(levels = c(“0”, “1”, “2”, “3”)), pray =
readr::col_factor(levels = c(“0”, “1”, “2”, “3”)), internet =
readr::col_factor(levels = c(“0”, “1”)), laptop =
readr::col_factor(levels = c(“0”, “1”)), family_relationships =
readr::col_factor(levels = c(“1”, “2”, “3”, “4”, “5”)), friendships =
readr::col_factor(levels = c(“1”, “2”, “3”, “4”, “5”)),
romantic_relationships = readr::col_factor(levels = c(“0”, “1”, “2”,
“3”, “4”)), spiritual_wellnes = readr::col_factor(levels = c(“1”, “2”,
“3”, “4”, “5”)), financial_wellness = readr::col_factor(levels = c(“1”,
“2”, “3”, “4”, “5”)), health = readr::col_factor(levels = c(“1”, “2”,
“3”, “4”, “5”)), day_out = readr::col_factor(levels = c(“0”, “1”, “2”,
“3”)), night_out = readr::col_factor(levels = c(“0”, “1”, “2”, “3”)),
alcohol_or_narcotics = readr::col_factor(levels = c(“0”, “1”, “2”,
“3”)), mentor = readr::col_factor(levels = c(“0”, “1”)), mentor_meetings
= readr::col_factor(levels = c(“0”, “1”, “2”, “3”)),
`Attendance Waiver Granted: 1 = Yes, 0 = No` = readr::col_factor(levels
= c(“0”, “1”)), GRADE = readr::col_factor(levels = c(“A”, “B”, “C”, “D”,
“E”))),

                  locale = readr::locale())

View(student_performance_dataset)

summary(student_performance_dataset)

model_of_the_transform \<- preProcess(student_performance_dataset,
method = c(“scale”)) print(model_of_the_transform)
student_performance_dataset_scale_transform \<-
predict(model_of_the_transform,student_performance_dataset)

\##skewness sapply(student_performance_dataset\[, -4\], skewness, type =
2)

summary(student_performance_dataset_scale_transform)
student_performance_dataset \<-
as.numeric(unlist(student_performance_dataset_scale_transform\[, 4\]))
hist(student_performance_dataset, main =
names(student_performance_dataset_scale_transform)\[4\])

…to be continued
