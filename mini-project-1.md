Mini Data-Analysis Deliverable 1
================

# Welcome to your (maybe) first-ever data analysis project!

And hopefully the first of many. Let’s get started:

1.  Install the [`datateachr`](https://github.com/UBC-MDS/datateachr)
    package by typing the following into your **R terminal**:

<!-- -->

    install.packages("devtools")
    devtools::install_github("UBC-MDS/datateachr")

2.  Load the packages below.

``` r
library(datateachr)
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✔ ggplot2 3.3.5     ✔ purrr   0.3.4
    ## ✔ tibble  3.1.6     ✔ dplyr   1.0.8
    ## ✔ tidyr   1.2.0     ✔ stringr 1.4.0
    ## ✔ readr   2.1.2     ✔ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

3.  Make a repository in the <https://github.com/stat545ubc-2022>
    Organization. You will be working with this repository for the
    entire data analysis project. You can either make it public, or make
    it private and add the TA’s and Lucy as collaborators. A link to
    help you create a private repository is available on the
    \#collaborative-project Slack channel.

# Instructions

## For Both Milestones

-   Each milestone is worth 45 points. The number of points allocated to
    each task will be annotated within each deliverable. Tasks that are
    more challenging will often be allocated more points.

-   10 points will be allocated to the reproducibility, cleanliness, and
    coherence of the overall analysis. While the two milestones will be
    submitted as independent deliverables, the analysis itself is a
    continuum - think of it as two chapters to a story. Each chapter, or
    in this case, portion of your analysis, should be easily followed
    through by someone unfamiliar with the content.
    [Here](https://swcarpentry.github.io/r-novice-inflammation/06-best-practices-R/)
    is a good resource for what constitutes “good code”. Learning good
    coding practices early in your career will save you hassle later on!

## For Milestone 1

**To complete this milestone**, edit [this very `.Rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-1.Rmd)
directly. Fill in the sections that are tagged with
`<!--- start your work below --->`.

**To submit this milestone**, make sure to knit this `.Rmd` file to an
`.md` file by changing the YAML output settings from
`output: html_document` to `output: github_document`. Commit and push
all of your work to the mini-analysis GitHub repository you made
earlier, and tag a release on GitHub. Then, submit a link to your tagged
release on canvas.

**Points**: This milestone is worth 45 points: 43 for your analysis, 1
point for having your Milestone 1 document knit error-free, and 1 point
for tagging your release on Github.

# Learning Objectives

By the end of this milestone, you should:

-   Become familiar with your dataset of choosing
-   Select 4 questions that you would like to answer with your data
-   Generate a reproducible and clear report using R Markdown
-   Become familiar with manipulating and summarizing your data in
    tibbles using `dplyr`, with a research question in mind.

# Task 1: Choose your favorite dataset (10 points)

The `datateachr` package by Hayley Boyce and Jordan Bourak currently
composed of 7 semi-tidy datasets for educational purposes. Here is a
brief description of each dataset:

-   *apt_buildings*: Acquired courtesy of The City of Toronto’s Open
    Data Portal. It currently has 3455 rows and 37 columns.

-   *building_permits*: Acquired courtesy of The City of Vancouver’s
    Open Data Portal. It currently has 20680 rows and 14 columns.

-   *cancer_sample*: Acquired courtesy of UCI Machine Learning
    Repository. It currently has 569 rows and 32 columns.

-   *flow_sample*: Acquired courtesy of The Government of Canada’s
    Historical Hydrometric Database. It currently has 218 rows and 7
    columns.

-   *parking_meters*: Acquired courtesy of The City of Vancouver’s Open
    Data Portal. It currently has 10032 rows and 22 columns.

-   *steam_games*: Acquired courtesy of Kaggle. It currently has 40833
    rows and 21 columns.

-   *vancouver_trees*: Acquired courtesy of The City of Vancouver’s Open
    Data Portal. It currently has 146611 rows and 20 columns.

**Things to keep in mind**

-   We hope that this project will serve as practice for carrying our
    your own *independent* data analysis. Remember to comment your code,
    be explicit about what you are doing, and write notes in this
    markdown document when you feel that context is required. As you
    advance in the project, prompts and hints to do this will be
    diminished - it’ll be up to you!

-   Before choosing a dataset, you should always keep in mind **your
    goal**, or in other ways, *what you wish to achieve with this data*.
    This mini data-analysis project focuses on *data wrangling*,
    *tidying*, and *visualization*. In short, it’s a way for you to get
    your feet wet with exploring data on your own.

And that is exactly the first thing that you will do!

1.1 Out of the 7 datasets available in the `datateachr` package, choose
**4** that appeal to you based on their description. Write your choices
below:

**Note**: We encourage you to use the ones in the `datateachr` package,
but if you have a dataset that you’d really like to use, you can include
it here. But, please check with a member of the teaching team to see
whether the dataset is of appropriate complexity. Also, include a
**brief** description of the dataset here to help the teaching team
understand your data.

<!-------------------------- Start your work below ---------------------------->

1: CHOICE_1\_cancer_sample  
2: CHOICE_2\_flow_sample  
3: CHOICE_3\_steam_games  
4: CHOICE_4\_vancouver_trees

<!----------------------------------------------------------------------------->

1.2 One way to narrowing down your selection is to *explore* the
datasets. Use your knowledge of dplyr to find out at least *3*
attributes about each of these datasets (an attribute is something such
as number of rows, variables, class type…). The goal here is to have an
idea of *what the data looks like*.

*Hint:* This is one of those times when you should think about the
cleanliness of your analysis. I added a single code chunk for you below,
but do you want to use more than one? Would you like to write more
comments outside of the code chunk?

<!-------------------------- Start your work below ---------------------------->

-   Number of rows and columns of each data set  
    `flow_sample` has the least rows of data but the most variables.
    `cancer_sample` has the same number of variables as “flow_sample,”
    but a bit more records are included. `steam_game` and
    `vancouver_trees` both have 21 variables, and there are over 146k
    rows of data in “vancouver_trees.”

``` r
### EXPLORE HERE ###
t <- rbind(
  cbind("number of rows",nrow(cancer_sample),nrow(flow_sample),nrow(steam_games),nrow(vancouver_trees)),
  cbind("number of variables",ncol(cancer_sample),ncol(cancer_sample),ncol(steam_games),ncol(steam_games))
  )
table <- data.frame(t)
colnames(table) <- c("","cancer_sample","flow_sample","steam_games","vancouver_trees")
knitr::kable(table)
```

|                     | cancer_sample | flow_sample | steam_games | vancouver_trees |
|:--------------------|:--------------|:------------|:------------|:----------------|
| number of rows      | 569           | 218         | 40833       | 146611          |
| number of variables | 32            | 32          | 21          | 21              |

-   Class type of each dataset  
    Four datasets have very similar class types.

``` r
t1 <- rbind(
  cbind("cancer_sample",class(cancer_sample)),
  cbind("flow_sample",class(flow_sample)),
  cbind("steam_games",class(steam_games)),
  cbind("vancouver_trees",class(vancouver_trees))
)
table1 <- data.frame(t1)
colnames(table1) <- c("Dataset","Class")
knitr::kable(table1)
```

| Dataset         | Class       |
|:----------------|:------------|
| cancer_sample   | spec_tbl_df |
| cancer_sample   | tbl_df      |
| cancer_sample   | tbl         |
| cancer_sample   | data.frame  |
| flow_sample     | tbl_df      |
| flow_sample     | tbl         |
| flow_sample     | data.frame  |
| steam_games     | spec_tbl_df |
| steam_games     | tbl_df      |
| steam_games     | tbl         |
| steam_games     | data.frame  |
| vancouver_trees | tbl_df      |
| vancouver_trees | tbl         |
| vancouver_trees | data.frame  |

-   Variables in each dataset

``` r
glimpse(cancer_sample)
```

    ## Rows: 569
    ## Columns: 32
    ## $ ID                      <dbl> 842302, 842517, 84300903, 84348301, 84358402, …
    ## $ diagnosis               <chr> "M", "M", "M", "M", "M", "M", "M", "M", "M", "…
    ## $ radius_mean             <dbl> 17.990, 20.570, 19.690, 11.420, 20.290, 12.450…
    ## $ texture_mean            <dbl> 10.38, 17.77, 21.25, 20.38, 14.34, 15.70, 19.9…
    ## $ perimeter_mean          <dbl> 122.80, 132.90, 130.00, 77.58, 135.10, 82.57, …
    ## $ area_mean               <dbl> 1001.0, 1326.0, 1203.0, 386.1, 1297.0, 477.1, …
    ## $ smoothness_mean         <dbl> 0.11840, 0.08474, 0.10960, 0.14250, 0.10030, 0…
    ## $ compactness_mean        <dbl> 0.27760, 0.07864, 0.15990, 0.28390, 0.13280, 0…
    ## $ concavity_mean          <dbl> 0.30010, 0.08690, 0.19740, 0.24140, 0.19800, 0…
    ## $ concave_points_mean     <dbl> 0.14710, 0.07017, 0.12790, 0.10520, 0.10430, 0…
    ## $ symmetry_mean           <dbl> 0.2419, 0.1812, 0.2069, 0.2597, 0.1809, 0.2087…
    ## $ fractal_dimension_mean  <dbl> 0.07871, 0.05667, 0.05999, 0.09744, 0.05883, 0…
    ## $ radius_se               <dbl> 1.0950, 0.5435, 0.7456, 0.4956, 0.7572, 0.3345…
    ## $ texture_se              <dbl> 0.9053, 0.7339, 0.7869, 1.1560, 0.7813, 0.8902…
    ## $ perimeter_se            <dbl> 8.589, 3.398, 4.585, 3.445, 5.438, 2.217, 3.18…
    ## $ area_se                 <dbl> 153.40, 74.08, 94.03, 27.23, 94.44, 27.19, 53.…
    ## $ smoothness_se           <dbl> 0.006399, 0.005225, 0.006150, 0.009110, 0.0114…
    ## $ compactness_se          <dbl> 0.049040, 0.013080, 0.040060, 0.074580, 0.0246…
    ## $ concavity_se            <dbl> 0.05373, 0.01860, 0.03832, 0.05661, 0.05688, 0…
    ## $ concave_points_se       <dbl> 0.015870, 0.013400, 0.020580, 0.018670, 0.0188…
    ## $ symmetry_se             <dbl> 0.03003, 0.01389, 0.02250, 0.05963, 0.01756, 0…
    ## $ fractal_dimension_se    <dbl> 0.006193, 0.003532, 0.004571, 0.009208, 0.0051…
    ## $ radius_worst            <dbl> 25.38, 24.99, 23.57, 14.91, 22.54, 15.47, 22.8…
    ## $ texture_worst           <dbl> 17.33, 23.41, 25.53, 26.50, 16.67, 23.75, 27.6…
    ## $ perimeter_worst         <dbl> 184.60, 158.80, 152.50, 98.87, 152.20, 103.40,…
    ## $ area_worst              <dbl> 2019.0, 1956.0, 1709.0, 567.7, 1575.0, 741.6, …
    ## $ smoothness_worst        <dbl> 0.1622, 0.1238, 0.1444, 0.2098, 0.1374, 0.1791…
    ## $ compactness_worst       <dbl> 0.6656, 0.1866, 0.4245, 0.8663, 0.2050, 0.5249…
    ## $ concavity_worst         <dbl> 0.71190, 0.24160, 0.45040, 0.68690, 0.40000, 0…
    ## $ concave_points_worst    <dbl> 0.26540, 0.18600, 0.24300, 0.25750, 0.16250, 0…
    ## $ symmetry_worst          <dbl> 0.4601, 0.2750, 0.3613, 0.6638, 0.2364, 0.3985…
    ## $ fractal_dimension_worst <dbl> 0.11890, 0.08902, 0.08758, 0.17300, 0.07678, 0…

``` r
glimpse(flow_sample)
```

    ## Rows: 218
    ## Columns: 7
    ## $ station_id   <chr> "05BB001", "05BB001", "05BB001", "05BB001", "05BB001", "0…
    ## $ year         <dbl> 1909, 1910, 1911, 1912, 1913, 1914, 1915, 1916, 1917, 191…
    ## $ extreme_type <chr> "maximum", "maximum", "maximum", "maximum", "maximum", "m…
    ## $ month        <dbl> 7, 6, 6, 8, 6, 6, 6, 6, 6, 6, 6, 7, 6, 6, 6, 7, 5, 7, 6, …
    ## $ day          <dbl> 7, 12, 14, 25, 11, 18, 27, 20, 17, 15, 22, 3, 9, 5, 14, 5…
    ## $ flow         <dbl> 314, 230, 264, 174, 232, 214, 236, 309, 174, 345, 185, 24…
    ## $ sym          <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, N…

``` r
glimpse(steam_games)
```

    ## Rows: 40,833
    ## Columns: 21
    ## $ id                       <dbl> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14…
    ## $ url                      <chr> "https://store.steampowered.com/app/379720/DO…
    ## $ types                    <chr> "app", "app", "app", "app", "app", "bundle", …
    ## $ name                     <chr> "DOOM", "PLAYERUNKNOWN'S BATTLEGROUNDS", "BAT…
    ## $ desc_snippet             <chr> "Now includes all three premium DLC packs (Un…
    ## $ recent_reviews           <chr> "Very Positive,(554),- 89% of the 554 user re…
    ## $ all_reviews              <chr> "Very Positive,(42,550),- 92% of the 42,550 u…
    ## $ release_date             <chr> "May 12, 2016", "Dec 21, 2017", "Apr 24, 2018…
    ## $ developer                <chr> "id Software", "PUBG Corporation", "Harebrain…
    ## $ publisher                <chr> "Bethesda Softworks,Bethesda Softworks", "PUB…
    ## $ popular_tags             <chr> "FPS,Gore,Action,Demons,Shooter,First-Person,…
    ## $ game_details             <chr> "Single-player,Multi-player,Co-op,Steam Achie…
    ## $ languages                <chr> "English,French,Italian,German,Spanish - Spai…
    ## $ achievements             <dbl> 54, 37, 128, NA, NA, NA, 51, 55, 34, 43, 72, …
    ## $ genre                    <chr> "Action", "Action,Adventure,Massively Multipl…
    ## $ game_description         <chr> "About This Game Developed by id software, th…
    ## $ mature_content           <chr> NA, "Mature Content Description  The develope…
    ## $ minimum_requirements     <chr> "Minimum:,OS:,Windows 7/8.1/10 (64-bit versio…
    ## $ recommended_requirements <chr> "Recommended:,OS:,Windows 7/8.1/10 (64-bit ve…
    ## $ original_price           <dbl> 19.99, 29.99, 39.99, 44.99, 0.00, NA, 59.99, …
    ## $ discount_price           <dbl> 14.99, NA, NA, NA, NA, 35.18, 70.42, 17.58, N…

``` r
glimpse(vancouver_trees)
```

    ## Rows: 146,611
    ## Columns: 20
    ## $ tree_id            <dbl> 149556, 149563, 149579, 149590, 149604, 149616, 149…
    ## $ civic_number       <dbl> 494, 450, 4994, 858, 5032, 585, 4909, 4925, 4969, 7…
    ## $ std_street         <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ genus_name         <chr> "ULMUS", "ZELKOVA", "STYRAX", "FRAXINUS", "ACER", "…
    ## $ species_name       <chr> "AMERICANA", "SERRATA", "JAPONICA", "AMERICANA", "C…
    ## $ cultivar_name      <chr> "BRANDON", NA, NA, "AUTUMN APPLAUSE", NA, "CHANTICL…
    ## $ common_name        <chr> "BRANDON ELM", "JAPANESE ZELKOVA", "JAPANESE SNOWBE…
    ## $ assigned           <chr> "N", "N", "N", "Y", "N", "N", "N", "N", "N", "N", "…
    ## $ root_barrier       <chr> "N", "N", "N", "N", "N", "N", "N", "N", "N", "N", "…
    ## $ plant_area         <chr> "N", "N", "4", "4", "4", "B", "6", "6", "3", "3", "…
    ## $ on_street_block    <dbl> 400, 400, 4900, 800, 5000, 500, 4900, 4900, 4900, 7…
    ## $ on_street          <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ neighbourhood_name <chr> "MARPOLE", "MARPOLE", "KENSINGTON-CEDAR COTTAGE", "…
    ## $ street_side_name   <chr> "EVEN", "EVEN", "EVEN", "EVEN", "EVEN", "ODD", "ODD…
    ## $ height_range_id    <dbl> 2, 4, 3, 4, 2, 2, 3, 3, 2, 2, 2, 5, 3, 2, 2, 2, 2, …
    ## $ diameter           <dbl> 10.00, 10.00, 4.00, 18.00, 9.00, 5.00, 15.00, 14.00…
    ## $ curb               <chr> "N", "N", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "…
    ## $ date_planted       <date> 1999-01-13, 1996-05-31, 1993-11-22, 1996-04-29, 19…
    ## $ longitude          <dbl> -123.1161, -123.1147, -123.0846, -123.0870, -123.08…
    ## $ latitude           <dbl> 49.21776, 49.21776, 49.23938, 49.23469, 49.23894, 4…

-   Number of missing values  
    There is no missing value in `cancer_sample`, and around 21.1% of
    entries are missing in `steam_games`.

``` r
t2 <- rbind(
cbind("cancer_sample",sum(is.na(cancer_sample)),round(sum(is.na(cancer_sample))/(nrow(cancer_sample)*ncol(cancer_sample)),3)*100),
cbind("flow_sample",sum(is.na(flow_sample)),round(sum(is.na(flow_sample))/(nrow(flow_sample)*ncol(flow_sample)),3)*100),
cbind("steam_games",sum(is.na(steam_games)),round(sum(is.na(steam_games))/(nrow(steam_games)*ncol(steam_games)),3)*100),
cbind("vancouver_trees",sum(is.na(vancouver_trees)),round(sum(is.na(vancouver_trees))/(nrow(vancouver_trees)*ncol(vancouver_trees)),3)*100)
)
table2 <- data.frame(t2)
colnames(table2) <- c("Dataset","Number of Miss Values","Missing Percentage")
knitr::kable(table2)
```

| Dataset         | Number of Miss Values | Missing Percentage |
|:----------------|:----------------------|:-------------------|
| cancer_sample   | 0                     | 0                  |
| flow_sample     | 125                   | 8.2                |
| steam_games     | 180899                | 21.1               |
| vancouver_trees | 191135                | 6.5                |

<!----------------------------------------------------------------------------->

1.3 Now that you’ve explored the 4 datasets that you were initially most
interested in, let’s narrow it down to 2. What lead you to choose these
2? Briefly explain your choices below, and feel free to include any code
in your explanation.

<!-------------------------- Start your work below ---------------------------->

We would like to choose datasets with more records and fewer missing
values. Since there is no missing value in “cancer_sample” and only 6.5%
missing entries in “vancouver_trees,” We will narrow down our choice to
these two datasets.
<!----------------------------------------------------------------------------->

1.4 Time for the final decision! Going back to the beginning, it’s
important to have an *end goal* in mind. For example, if I had chosen
the `titanic` dataset for my project, I might’ve wanted to explore the
relationship between survival and other variables. Try to think of 1
research question that you would want to answer with each dataset. Note
them down below, and make your final choice based on what seems more
interesting to you!

<!-------------------------- Start your work below ---------------------------->

-   `cancer_sample`: What is the relationship between diagnosis
    (malignant/benign) and mean radius of cell nucleus?

-   `vancouver_trees`: What is the difference in mean diameter in
    different species?

-   The research problem regarding cancer diagnosis is more interesting
    to me, so I will use `cancer_sample` as my dataset in the following
    questions.
    <!----------------------------------------------------------------------------->

# Important note

Read Tasks 2 and 3 *fully* before starting to complete either of them.
Probably also a good point to grab a coffee to get ready for the fun
part!

This project is semi-guided, but meant to be *independent*. For this
reason, you will complete tasks 2 and 3 below (under the **START HERE**
mark) as if you were writing your own exploratory data analysis report,
and this guidance never existed! Feel free to add a brief introduction
section to your project, format the document with markdown syntax as you
deem appropriate, and structure the analysis as you deem appropriate.
Remember, marks will be awarded for completion of the 4 tasks, but 10
points of the whole project are allocated to a reproducible and clean
analysis. If you feel lost, you can find a sample data analysis
[here](https://www.kaggle.com/headsortails/tidy-titarnic) to have a
better idea. However, bear in mind that it is **just an example** and
you will not be required to have that level of complexity in your
project.

# Task 2: Exploring your dataset (15 points)

If we rewind and go back to the learning objectives, you’ll see that by
the end of this deliverable, you should have formulated *4* research
questions about your data that you may want to answer during your
project. However, it may be handy to do some more exploration on your
dataset of choice before creating these questions - by looking at the
data, you may get more ideas. **Before you start this task, read all
instructions carefully until you reach START HERE under Task 3**.

2.1 Complete *4 out of the following 8 exercises* to dive deeper into
your data. All datasets are different and therefore, not all of these
tasks may make sense for your data - which is why you should only answer
*4*. Use *dplyr* and *ggplot*.

1.  Plot the distribution of a numeric variable.
2.  Create a new variable based on other variables in your data (only if
    it makes sense)
3.  Investigate how many missing values there are per variable. Can you
    find a way to plot this? *4. Explore the relationship between 2
    variables in a plot.*
4.  Filter observations in your data according to your own criteria.
    Think of what you’d like to explore - again, if this was the
    `titanic` dataset, I may want to narrow my search down to passengers
    born in a particular year… *6. Use a boxplot to look at the
    frequency of different observations within a single variable.* You
    can do this for more than one variable if you wish! *7. Make a new
    tibble with a subset of your data, with variables and observations
    that you are interested in exploring.* *8. Use a density plot to
    explore any of your variables* (that are suitable for this type of
    plot).

2.2 For each of the 4 exercises that you complete, provide a *brief
explanation* of why you chose that exercise in relation to your data (in
other words, why does it make sense to do that?), and sufficient
comments for a reader to understand your reasoning and code.

<!-------------------------- Start your work below ---------------------------->

-   **Task 6. Use a boxplot to look at the frequency of different
    observations within a single variable.**

``` r
cancer_sample$diagnosis <-
  cancer_sample$diagnosis %>% recode_factor("B" = "benign", "M" = "malignant")

cancer_sample %>% 
  ggplot(aes(diagnosis,radius_mean)) +
  geom_boxplot(width = 0.4) +
  theme_bw()
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

I firstly refactor the levels of `diagnosis` as “benign” and
“malignant”, instead of “B” and “M”, which can make more sense to the
readers.  
This boxplot is reasonable since it shows relationship between a
numerical variable (`radius_mean`) and an explortabry variable
(`diagnosis`). The plot indicates that medium of cell nucleus radius is
much larger in malignant group, and the max radius mean in benign group
is a bit higher than the medium radius mean in maglignant.

-   **Task8. Use a density plot to explore any of your variables**

``` r
cancer_sample %>% 
  ggplot(aes(x = radius_mean)) + 
  geom_density() +
  theme_bw()
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

This is a density plot for `radius_mean`, which makes sense since it is
a numerical variable. From the plot, it is clear that radius mean is
concentrated between 10 and 15.

-   **Task 4. Explore the relationship between 2 variables in a plot.**

``` r
cancer_sample %>% 
  ggplot(aes(x = radius_mean, y = concavity_mean)) +
  geom_point() +
  geom_smooth(method = "lm", formula = y ~ x) +
  theme_bw()
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

I used a scatter plot to explore the relationship between two numerical
variables. The plot shows a positive correlation between `radius_mean`
and `concavity_mean`.

-   **Task 7. Make a new tibble with a subset of your data, with
    variables and observations that you are interested in exploring.**

``` r
cancer_subsample <- 
  cancer_sample %>% 
    select(c(1:12))
head(cancer_subsample)
```

    ## # A tibble: 6 × 12
    ##       ID diagn…¹ radiu…² textu…³ perim…⁴ area_…⁵ smoot…⁶ compa…⁷ conca…⁸ conca…⁹
    ##    <dbl> <fct>     <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>
    ## 1 8.42e5 malign…    18.0    10.4   123.    1001   0.118   0.278   0.300   0.147 
    ## 2 8.43e5 malign…    20.6    17.8   133.    1326   0.0847  0.0786  0.0869  0.0702
    ## 3 8.43e7 malign…    19.7    21.2   130     1203   0.110   0.160   0.197   0.128 
    ## 4 8.43e7 malign…    11.4    20.4    77.6    386.  0.142   0.284   0.241   0.105 
    ## 5 8.44e7 malign…    20.3    14.3   135.    1297   0.100   0.133   0.198   0.104 
    ## 6 8.44e5 malign…    12.4    15.7    82.6    477.  0.128   0.17    0.158   0.0809
    ## # … with 2 more variables: symmetry_mean <dbl>, fractal_dimension_mean <dbl>,
    ## #   and abbreviated variable names ¹​diagnosis, ²​radius_mean, ³​texture_mean,
    ## #   ⁴​perimeter_mean, ⁵​area_mean, ⁶​smoothness_mean, ⁷​compactness_mean,
    ## #   ⁸​concavity_mean, ⁹​concave_points_mean

For simplicity, I will use mean values to explore the research
questions.
<!----------------------------------------------------------------------------->

# Task 3: Write your research questions (5 points)

So far, you have chosen a dataset and gotten familiar with it through
exploring the data. Now it’s time to figure out 4 research questions
that you would like to answer with your data! Write the 4 questions and
any additional comments at the end of this deliverable. These questions
are not necessarily set in stone - TAs will review them and give you
feedback; therefore, you may choose to pursue them as they are for the
rest of the project, or make modifications!

<!--- *****START HERE***** --->

-   What is the difference in distribution of radius mean in benign and
    malignant diagnosis?
-   Is diagnosis result associated with radius of mean?
-   What is the relationship between radius mean and compactness mean?
-   What is the difference in symmetry mean in cell nucleus with
    different radius mean?

# Task 4: Process and summarize your data (13 points)

From Task 2, you should have an idea of the basic structure of your
dataset (e.g. number of rows and columns, class types, etc.). Here, we
will start investigating your data more in-depth using various data
manipulation functions.

### 1.1 (10 points)

Now, for each of your four research questions, choose one task from
options 1-4 (summarizing), and one other task from 4-8 (graphing). You
should have 2 tasks done for each research question (8 total). Make sure
it makes sense to do them! (e.g. don’t use a numerical variables for a
task that needs a categorical variable.). Comment on why each task helps
(or doesn’t!) answer the corresponding research question.

Ensure that the output of each operation is printed!

**Summarizing:**

1.  Compute the *range*, *mean*, and *two other summary statistics* of
    **one numerical variable** across the groups of **one categorical
    variable** from your data.
2.  Compute the number of observations for at least one of your
    categorical variables. Do not use the function `table()`!
3.  Create a categorical variable with 3 or more groups from an existing
    numerical variable. You can use this new variable in the other
    tasks! *An example: age in years into “child, teen, adult, senior”.*
4.  Based on two categorical variables, calculate two summary statistics
    of your choosing.

**Graphing:**

5.  Create a graph out of summarized variables that has at least two
    geom layers.
6.  Create a graph of your choosing, make one of the axes logarithmic,
    and format the axes labels so that they are “pretty” or easier to
    read.
7.  Make a graph where it makes sense to customize the alpha
    transparency.
8.  Create 3 histograms out of summarized variables, with each histogram
    having different sized bins. Pick the “best” one and explain why it
    is the best.

Make sure it’s clear what research question you are doing each operation
for!

<!------------------------- Start your work below ----------------------------->

-   **What is the difference in symmetry mean of cell nucleus with
    different radius mean?**

-   summarizing 3 + graphing 5

-   factor the radius mean  
    From Task2, we see the radius mean is concentrated between 10
    and 15. Therefore, the level would be “Large” if radius mean is
    greater than 15, “Medium” if the radius mean is between 10 and 15,
    “Small” otherwise.

``` r
cancer_subsample <- cancer_subsample %>% 
  mutate(radius_level = case_when(radius_mean>15 ~ "Large",
                                   radius_mean<10 ~ "Small",
                                   TRUE ~ "Medium"))

cancer_subsample %>% select(radius_mean,radius_level) %>% head()
```

    ## # A tibble: 6 × 2
    ##   radius_mean radius_level
    ##         <dbl> <chr>       
    ## 1        18.0 Large       
    ## 2        20.6 Large       
    ## 3        19.7 Large       
    ## 4        11.4 Medium      
    ## 5        20.3 Large       
    ## 6        12.4 Medium

``` r
cancer_subsample %>% 
  ggplot(aes(radius_level, smoothness_mean )) + 
  geom_boxplot(width = 0.1) +
  stat_summary(fun = "mean", geom = "point", shape = 8,
               size = 2, color = "dark green") +
  theme_bw()
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

The range of mean of smoothness is wider for cell nucleus with larger
radius. Medium of smoothness mean in ‘Large’ group is the largest.

-   **Is diagnosis result associated with area mean?**
-   summarizing 2 + graphing 5

``` r
cancer_subsample <- cancer_subsample %>% 
  mutate(area_level = case_when(area_mean < quantile(area_mean,0.25) ~ "1st quater",
                                area_mean > quantile(area_mean,0.75) ~ "4th quater",
                                (area_mean < quantile(area_mean,0.75)) & (area_mean > quantile(area_mean,0.5)) ~ "3rd quater",
                                TRUE ~ "2nd quater"))
cancer_subsample %>% select(area_mean,area_level)
```

    ## # A tibble: 569 × 2
    ##    area_mean area_level
    ##        <dbl> <chr>     
    ##  1     1001  4th quater
    ##  2     1326  4th quater
    ##  3     1203  4th quater
    ##  4      386. 1st quater
    ##  5     1297  4th quater
    ##  6      477. 2nd quater
    ##  7     1040  4th quater
    ##  8      578. 3rd quater
    ##  9      520. 2nd quater
    ## 10      476. 2nd quater
    ## # … with 559 more rows

``` r
t <- cancer_subsample %>% 
  group_by(diagnosis,area_level) %>% 
  count()
t
```

    ## # A tibble: 8 × 3
    ## # Groups:   diagnosis, area_level [8]
    ##   diagnosis area_level     n
    ##   <fct>     <chr>      <int>
    ## 1 benign    1st quater   139
    ## 2 benign    2nd quater   129
    ## 3 benign    3rd quater    83
    ## 4 benign    4th quater     6
    ## 5 malignant 1st quater     3
    ## 6 malignant 2nd quater    15
    ## 7 malignant 3rd quater    58
    ## 8 malignant 4th quater   136

``` r
t %>% 
  ggplot(aes(x = area_level)) +
  geom_col(aes(x=area_level,y = n), alpha = 0.5, fill = "grey") +
  geom_bar(aes(weight = n,fill = diagnosis),position="dodge") +
  theme_bw()
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

I classified four groups of area mean according to quantitle of the
variable. Grey bar is total observation in each area level group, and
red and blue bar are number of observation in benign diagnosis group and
malignant diagnosis group respectively. It is clear there are less and
less observations in benign group as area level gets higher. By
contrast, number of observations increases in maglignant group as area
level gets higher.

-   **Is there any relationship between radius mean and number of
    concave portions of the contour?**
-   summarizing 4 + graphing 5

``` r
cancer_subsample %>% 
  group_by(diagnosis,radius_level) %>% 
  summarise(range = range(concave_points_mean),mean = mean(concave_points_mean), median = median(concave_points_mean),sd = sd(concave_points_mean))
```

    ## `summarise()` has grouped output by 'diagnosis', 'radius_level'. You can
    ## override using the `.groups` argument.

    ## # A tibble: 10 × 6
    ## # Groups:   diagnosis, radius_level [5]
    ##    diagnosis radius_level  range   mean median     sd
    ##    <fct>     <chr>         <dbl>  <dbl>  <dbl>  <dbl>
    ##  1 benign    Large        0.0266 0.0491 0.0470 0.0168
    ##  2 benign    Large        0.0853 0.0491 0.0470 0.0168
    ##  3 benign    Medium       0      0.0260 0.0239 0.0146
    ##  4 benign    Medium       0.0780 0.0260 0.0239 0.0146
    ##  5 benign    Small        0      0.0179 0.0150 0.0176
    ##  6 benign    Small        0.0786 0.0179 0.0150 0.0176
    ##  7 malignant Large        0.0231 0.0952 0.0899 0.0348
    ##  8 malignant Large        0.201  0.0952 0.0899 0.0348
    ##  9 malignant Medium       0.0203 0.0652 0.0646 0.0201
    ## 10 malignant Medium       0.105  0.0652 0.0646 0.0201

``` r
cancer_subsample %>% 
  ggplot(aes(x = radius_mean, y = concave_points_mean , color = diagnosis)) +
  geom_point() +
  geom_smooth(method = "lm", formula = y ~ x) +
  theme_bw()
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->

In both diagnosis groups, there is a positive relationship between
radius mean and number of concave points. The slope of malignant
diagnosis is steeper.

-   **What is the difference in distribution of radius in benign and
    malignant diagnosis?**

-   summarizing 1 + graphing 8

``` r
cancer_sample %>% 
  group_by(diagnosis) %>% 
  summarise(range = range(radius_mean),mean = mean(radius_mean),min = min(radius_mean), max = max(radius_mean))
```

    ## `summarise()` has grouped output by 'diagnosis'. You can override using the
    ## `.groups` argument.

    ## # A tibble: 4 × 5
    ## # Groups:   diagnosis [2]
    ##   diagnosis range  mean   min   max
    ##   <fct>     <dbl> <dbl> <dbl> <dbl>
    ## 1 benign     6.98  12.1  6.98  17.8
    ## 2 benign    17.8   12.1  6.98  17.8
    ## 3 malignant 11.0   17.5 11.0   28.1
    ## 4 malignant 28.1   17.5 11.0   28.1

``` r
cancer_sample %>% 
  ggplot(aes(x = radius_mean))+
  geom_histogram(aes(fill = diagnosis),bins = 10)
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->

``` r
cancer_sample %>% 
  ggplot(aes(x = radius_mean))+
  geom_histogram(aes(fill = diagnosis),bins = 30)
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-22-1.png)<!-- -->

``` r
cancer_sample %>% 
  ggplot(aes(x = radius_mean))+
  geom_histogram(aes(fill = diagnosis),bins = 60)
```

![](mini-project-1_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->

I tried three histogram plots with three different bin sizes, and
`bin = 30` is the most suitable one. Since if bin size is too small
(`bin = 10`), some information will be lost. If bin size is too large
(`bin = 60`), the variation in the plot will be too detailed and it is
hard for us to find a pattern from the plot.

<!----------------------------------------------------------------------------->

### 1.2 (3 points)

Based on the operations that you’ve completed, how much closer are you
to answering your research questions? Think about what aspects of your
research questions remain unclear. Can your research questions be
refined, now that you’ve investigated your data a bit more? Which
research questions are yielding interesting results?

<!-------------------------- Start your work below ---------------------------->

From the plots above, we can discover differences in metrics in benign
diagnosis group and malignant diagnosis group, and the plots also
indicate relationship between variables. However, it is still unclear
whether the association or differences are statistically significant.
The result from the bar plot of the number of observations in different
area levels is the most impressive. Most of the observations in the
benign group have a small area mean. By contrast, observations in the
malignant group tend to have larger areas. The research question may be
refined as to whether area mean has a significant association with
diagnosis.
<!----------------------------------------------------------------------------->

### Attribution

Thanks to Icíar Fernández Boyano for mostly putting this together, and
Vincenzo Coia for launching.
