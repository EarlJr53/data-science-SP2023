Regression Case Study: PSAAP II
================
Brooke Moss
2023-04-23

- <a href="#grading-rubric" id="toc-grading-rubric">Grading Rubric</a>
  - <a href="#individual" id="toc-individual">Individual</a>
  - <a href="#due-date" id="toc-due-date">Due Date</a>
- <a href="#orientation-exploring-simulation-results"
  id="toc-orientation-exploring-simulation-results">Orientation: Exploring
  Simulation Results</a>
  - <a href="#q1-perform-your-initial-checks-to-get-a-sense-of-the-data"
    id="toc-q1-perform-your-initial-checks-to-get-a-sense-of-the-data"><strong>q1</strong>
    Perform your “initial checks” to get a sense of the data.</a>
  - <a
    href="#q2-visualize-t_norm-against-x-note-that-there-are-multiple-simulations-at-different-values-of-the-input-variables-each-simulation-result-is-identified-by-a-different-value-of-idx"
    id="toc-q2-visualize-t_norm-against-x-note-that-there-are-multiple-simulations-at-different-values-of-the-input-variables-each-simulation-result-is-identified-by-a-different-value-of-idx"><strong>q2</strong>
    Visualize <code>T_norm</code> against <code>x</code>. Note that there
    are multiple simulations at different values of the Input variables:
    Each simulation result is identified by a different value of
    <code>idx</code>.</a>
  - <a href="#modeling" id="toc-modeling">Modeling</a>
    - <a
      href="#q3-the-following-code-chunk-fits-a-few-different-models-compute-a-measure-of-model-accuracy-for-each-model-on-df_validate-and-compare-their-performance"
      id="toc-q3-the-following-code-chunk-fits-a-few-different-models-compute-a-measure-of-model-accuracy-for-each-model-on-df_validate-and-compare-their-performance"><strong>q3</strong>
      The following code chunk fits a few different models. Compute a measure
      of model accuracy for each model on <code>df_validate</code>, and
      compare their performance.</a>
    - <a
      href="#q4-use-a-combination-of-eda-and-train-validation-error-to-build-a-model-by-selecting-reasonable-predictors-for-the-formula-argument-document-your-findings-under-observations-below-try-to-build-the-most-accurate-model-you-can"
      id="toc-q4-use-a-combination-of-eda-and-train-validation-error-to-build-a-model-by-selecting-reasonable-predictors-for-the-formula-argument-document-your-findings-under-observations-below-try-to-build-the-most-accurate-model-you-can"><strong>q4</strong>
      Use a combination of EDA and train-validation error to build a model by
      selecting <em>reasonable</em> predictors for the <code>formula</code>
      argument. Document your findings under <em>observations</em> below. Try
      to build the most accurate model you can!</a>
  - <a href="#contrasting-ci-and-pi"
    id="toc-contrasting-ci-and-pi">Contrasting CI and PI</a>
    - <a
      href="#q5-the-following-code-will-construct-a-predicted-vs-actual-plot-with-your-model-from-q4-and-add-prediction-intervals-study-the-results-and-answer-the-questions-below-under-observations"
      id="toc-q5-the-following-code-will-construct-a-predicted-vs-actual-plot-with-your-model-from-q4-and-add-prediction-intervals-study-the-results-and-answer-the-questions-below-under-observations"><strong>q5</strong>
      The following code will construct a predicted-vs-actual plot with your
      model from <em>q4</em> and add prediction intervals. Study the results
      and answer the questions below under <em>observations</em>.</a>
- <a href="#case-study-predicting-performance-ranges"
  id="toc-case-study-predicting-performance-ranges">Case Study: Predicting
  Performance Ranges</a>
  - <a
    href="#q6-you-are-consulting-with-a-team-that-is-designing-a-prototype-heat-transfer-device-they-are-asking-you-to-help-determine-a-dependable-range-of-values-for-t_norm-they-can-design-around-for-this-single-prototype-the-realized-value-of-t_norm-must-not-be-too-high-as-it-may-damage-the-downstream-equipment-but-it-must-also-be-high-enough-to-extract-an-acceptable-amount-of-heat"
    id="toc-q6-you-are-consulting-with-a-team-that-is-designing-a-prototype-heat-transfer-device-they-are-asking-you-to-help-determine-a-dependable-range-of-values-for-t_norm-they-can-design-around-for-this-single-prototype-the-realized-value-of-t_norm-must-not-be-too-high-as-it-may-damage-the-downstream-equipment-but-it-must-also-be-high-enough-to-extract-an-acceptable-amount-of-heat"><strong>q6</strong>
    You are consulting with a team that is designing a prototype heat
    transfer device. They are asking you to help determine a <em>dependable
    range of values</em> for <code>T_norm</code> they can design around for
    this <em>single prototype</em>. The realized value of
    <code>T_norm</code> must not be too high as it may damage the downstream
    equipment, but it must also be high enough to extract an acceptable
    amount of heat.</a>
- <a href="#references" id="toc-references">References</a>

*Purpose*: Confidence and prediction intervals are useful for studying
“pure sampling” of some distribution. However, we can combine CI and PI
with regression analysis to equip our modeling efforts with powerful
notions of uncertainty. In this challenge, you will use fluid simulation
data in a regression analysis with uncertainty quantification (CI and
PI) to support engineering design.

<!-- include-rubric -->

# Grading Rubric

<!-- -------------------------------------------------- -->

Unlike exercises, **challenges will be graded**. The following rubrics
define how you will be graded, both on an individual and team basis.

## Individual

<!-- ------------------------- -->

| Category    | Needs Improvement                                                                                                | Satisfactory                                                                                                               |
|-------------|------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Effort      | Some task **q**’s left unattempted                                                                               | All task **q**’s attempted                                                                                                 |
| Observed    | Did not document observations, or observations incorrect                                                         | Documented correct observations based on analysis                                                                          |
| Supported   | Some observations not clearly supported by analysis                                                              | All observations clearly supported by analysis (table, graph, etc.)                                                        |
| Assessed    | Observations include claims not supported by the data, or reflect a level of certainty not warranted by the data | Observations are appropriately qualified by the quality & relevance of the data and (in)conclusiveness of the support      |
| Specified   | Uses the phrase “more data are necessary” without clarification                                                  | Any statement that “more data are necessary” specifies which *specific* data are needed to answer what *specific* question |
| Code Styled | Violations of the [style guide](https://style.tidyverse.org/) hinder readability                                 | Code sufficiently close to the [style guide](https://style.tidyverse.org/)                                                 |

## Due Date

<!-- ------------------------- -->

All the deliverables stated in the rubrics above are due **at midnight**
before the day of the class discussion of the challenge. See the
[Syllabus](https://docs.google.com/document/d/1qeP6DUS8Djq_A0HMllMqsSqX3a9dbcx1/edit?usp=sharing&ouid=110386251748498665069&rtpof=true&sd=true)
for more information.

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.4.0      ✔ purrr   1.0.1 
    ## ✔ tibble  3.2.0      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.5.0 
    ## ✔ readr   2.1.4      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(modelr)
library(broom)
```

    ## 
    ## Attaching package: 'broom'
    ## 
    ## The following object is masked from 'package:modelr':
    ## 
    ##     bootstrap

``` r
## Helper function to compute uncertainty bounds
add_uncertainties <- function(data, model, prefix = "pred", ...) {
  df_fit <-
    stats::predict(model, data, ...) %>%
    as_tibble() %>%
    rename_with(~ str_c(prefix, "_", .))

  bind_cols(data, df_fit)
}
```

# Orientation: Exploring Simulation Results

*Background*: The data you will study in this exercise come from a
computational fluid dynamics (CFD) [simulation
campaign](https://www.sciencedirect.com/science/article/abs/pii/S0301932219308651?via%3Dihub)
that studied the interaction of turbulent flow and radiative heat
transfer to fluid-suspended particles\[1\]. These simulations were
carried out to help study a novel design of [solar
receiver](https://en.wikipedia.org/wiki/Concentrated_solar_power),
though they are more aimed at fundamental physics than detailed device
design. The following code chunk downloads and unpacks the data to your
local `./data/` folder.

``` r
## NOTE: No need to edit this chunk
## Download PSAAP II data and unzip
url_zip <- "https://ndownloader.figshare.com/files/24111269"
filename_zip <- "./data/psaap.zip"
filename_psaap <- "./data/psaap.csv"

curl::curl_download(url_zip, destfile = filename_zip)
unzip(filename_zip, exdir = "./data")
df_psaap <- read_csv(filename_psaap)
```

    ## Rows: 140 Columns: 22
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## dbl (22): x, idx, L, W, U_0, N_p, k_f, T_f, rho_f, mu_f, lam_f, C_fp, rho_p,...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

![PSAAP II irradiated core flow](./images/psaap-setup.png) Figure 1. An
example simulation, frozen at a specific point in time. An initial
simulation is run (HIT SECTION) to generate a turbulent flow with
particles, and that swirling flow is released into a rectangular domain
(RADIATED SECTION) with bulk downstream flow (left to right).
Concentrated solar radiation transmits through the optically transparent
fluid, but deposits heat into the particles. The particles then convect
heat into the fluid, which heats up the flow. The false-color image
shows the fluid temperature: Notice that there are “hot spots” where hot
particles have deposited heat into the fluid. The dataset `df_psaap`
gives measurements of `T_norm = (T - T0) / T0` averaged across planes at
various locations along the RADIATED SECTION.

### **q1** Perform your “initial checks” to get a sense of the data.

``` r
## TODO: Perform your initial checks
colnames(df_psaap)
```

    ##  [1] "x"      "idx"    "L"      "W"      "U_0"    "N_p"    "k_f"    "T_f"   
    ##  [9] "rho_f"  "mu_f"   "lam_f"  "C_fp"   "rho_p"  "d_p"    "C_pv"   "h"     
    ## [17] "I_0"    "eps_p"  "avg_q"  "avg_T"  "rms_T"  "T_norm"

``` r
summary(df_psaap)
```

    ##        x               idx           L                W          
    ##  Min.   :0.2500   Min.   : 1   Min.   :0.1292   Min.   :0.03198  
    ##  1st Qu.:0.4375   1st Qu.: 9   1st Qu.:0.1448   1st Qu.:0.03539  
    ##  Median :0.6250   Median :18   Median :0.1623   Median :0.03983  
    ##  Mean   :0.6250   Mean   :18   Mean   :0.1631   Mean   :0.04022  
    ##  3rd Qu.:0.8125   3rd Qu.:27   3rd Qu.:0.1819   3rd Qu.:0.04482  
    ##  Max.   :1.0000   Max.   :35   Max.   :0.2009   Max.   :0.04960  
    ##       U_0             N_p               k_f               T_f       
    ##  Min.   :1.667   Min.   :1527347   Min.   :0.07954   Min.   :241.9  
    ##  1st Qu.:1.846   1st Qu.:1707729   1st Qu.:0.08674   1st Qu.:262.3  
    ##  Median :2.075   Median :1909414   Median :0.09822   Median :291.4  
    ##  Mean   :2.094   Mean   :1929614   Mean   :0.09964   Mean   :298.3  
    ##  3rd Qu.:2.340   3rd Qu.:2154872   3rd Qu.:0.11123   3rd Qu.:331.7  
    ##  Max.   :2.583   Max.   :2387055   Max.   :0.12360   Max.   :370.5  
    ##      rho_f             mu_f               lam_f              C_fp       
    ##  Min.   :0.9637   Min.   :1.519e-05   Min.   :0.02393   Min.   : 813.2  
    ##  1st Qu.:1.0728   1st Qu.:1.672e-05   1st Qu.:0.02642   1st Qu.: 922.2  
    ##  Median :1.1943   Median :1.893e-05   Median :0.02976   Median :1013.4  
    ##  Mean   :1.2059   Mean   :1.902e-05   Mean   :0.03033   Mean   :1025.0  
    ##  3rd Qu.:1.3358   3rd Qu.:2.126e-05   3rd Qu.:0.03352   3rd Qu.:1131.3  
    ##  Max.   :1.4871   Max.   :2.340e-05   Max.   :0.03762   Max.   :1262.9  
    ##      rho_p            d_p                 C_pv             h       
    ##  Min.   : 7159   Min.   :8.497e-06   Min.   :362.2   Min.   :4569  
    ##  1st Qu.: 8053   1st Qu.:9.493e-06   1st Qu.:413.9   1st Qu.:5134  
    ##  Median : 9058   Median :1.061e-05   Median :462.5   Median :5830  
    ##  Mean   : 9144   Mean   :1.068e-05   Mean   :464.8   Mean   :5820  
    ##  3rd Qu.:10339   3rd Qu.:1.185e-05   3rd Qu.:516.9   3rd Qu.:6414  
    ##  Max.   :11128   Max.   :1.308e-05   Max.   :565.0   Max.   :7056  
    ##       I_0              eps_p            avg_q             avg_T      
    ##  Min.   :5664363   Min.   :0.3193   Min.   : 335025   Min.   :291.4  
    ##  1st Qu.:6363488   1st Qu.:0.3540   1st Qu.: 619232   1st Qu.:423.0  
    ##  Median :6943899   Median :0.3958   Median : 689560   Median :491.3  
    ##  Mean   :7095833   Mean   :0.4018   Mean   : 777490   Mean   :513.0  
    ##  3rd Qu.:7953745   3rd Qu.:0.4427   3rd Qu.: 978892   3rd Qu.:582.3  
    ##  Max.   :8849196   Max.   :0.4950   Max.   :1498542   Max.   :938.2  
    ##      rms_T           T_norm      
    ##  Min.   :3.387   Min.   :0.1215  
    ##  1st Qu.:4.937   1st Qu.:0.3889  
    ##  Median :5.698   Median :0.6328  
    ##  Mean   :5.961   Mean   :0.7360  
    ##  3rd Qu.:6.948   3rd Qu.:0.9795  
    ##  Max.   :9.254   Max.   :2.2840

**Observations**:

- Variables seem to be grouped by “f”, “p”, “fp”, and “pv”. This might
  be an opportunity to use `pivot_wider`.
- There are 3 variables that reference “T”, those being `avg_T`,
  `rms_T`, and `T_norm`.

The important variables in this dataset are:

| Variable | Category | Meaning                           |
|----------|----------|-----------------------------------|
| `x`      | Spatial  | Channel location                  |
| `idx`    | Metadata | Simulation run                    |
| `L`      | Input    | Channel length                    |
| `W`      | Input    | Channel width                     |
| `U_0`    | Input    | Bulk velocity                     |
| `N_p`    | Input    | Number of particles               |
| `k_f`    | Input    | Turbulence level                  |
| `T_f`    | Input    | Fluid inlet temp                  |
| `rho_f`  | Input    | Fluid density                     |
| `mu_f`   | Input    | Fluid viscosity                   |
| `lam_f`  | Input    | Fluid conductivity                |
| `C_fp`   | Input    | Fluid isobaric heat capacity      |
| `rho_p`  | Input    | Particle density                  |
| `d_p`    | Input    | Particle diameter                 |
| `C_pv`   | Input    | Particle isochoric heat capacity  |
| `h`      | Input    | Convection coefficient            |
| `I_0`    | Input    | Radiation intensity               |
| `eps_p`  | Input    | Radiation absorption coefficient  |
| `avg_q`  | Output   | Plane-averaged heat flux          |
| `avg_T`  | Output   | Plane-averaged fluid temperature  |
| `rms_T`  | Output   | Plane-rms fluid temperature       |
| `T_norm` | Output   | Normalized fluid temperature rise |

The primary output of interest is `T_norm = (avg_T - T_f) / T_f`, the
normalized (dimensionless) temperature rise of the fluid, due to heat
transfer. These measurements are taken at locations `x` along a column
of fluid, for different experimental settings (e.g. different dimensions
`W, L`, different flow speeds `U_0`, etc.).

### **q2** Visualize `T_norm` against `x`. Note that there are multiple simulations at different values of the Input variables: Each simulation result is identified by a different value of `idx`.

``` r
## TODO: Visualize the data in df_psaap with T_norm against x;
##       design your visual to handle the multiple simulations,
##       each identified by different values of idx
df_psaap %>%
  ggplot() +
  geom_line(aes(
    x = x,
    y = T_norm,
    group = idx,
    color = idx
  )) +
  scale_color_continuous(type = "viridis")
```

![](c11-psaap-assignment_files/figure-gfm/q2-task-1.png)<!-- -->

## Modeling

The following chunk will split the data into training and validation
sets.

``` r
## NOTE: No need to edit this chunk
# Addl' Note: These data are already randomized by idx; no need
# to additionally shuffle the data!
df_train <- df_psaap %>% filter(idx %in% 1:20)
df_validate <- df_psaap %>% filter(idx %in% 21:36)
```

One of the key decisions we must make in modeling is choosing predictors
(features) from our observations to include in the model. Ideally we
should have some intuition for why these predictors are reasonable to
include in the model; for instance, we saw above that location along the
flow `x` tends to affect the temperature rise `T_norm`. This is because
fluid downstream has been exposed to solar radiation for longer, and
thus is likely to be at a higher temperature.

Reasoning about our variables—at least at a *high level*—can help us to
avoid including *fallacious* predictors in our models. You’ll explore
this idea in the next task.

### **q3** The following code chunk fits a few different models. Compute a measure of model accuracy for each model on `df_validate`, and compare their performance.

``` r
## NOTE: No need to edit these models
fit_baseline <- 
  df_train %>% 
  lm(formula = T_norm ~ x)

fit_cheat <- 
  df_train %>% 
  lm(formula = T_norm ~ avg_T)

fit_nonphysical <- 
  df_train %>% 
  lm(formula = T_norm ~ idx)

## TODO: Compute a measure of accuracy for each fit above;
##       compare their relative performance
c("Baseline", rsquare(fit_baseline, df_validate))
```

    ## [1] "Baseline"          "0.474654559522053"

``` r
c("Cheat", rsquare(fit_cheat, df_validate))
```

    ## [1] "Cheat"             "0.637405082016864"

``` r
c("Non-Physical", rsquare(fit_nonphysical, df_validate))
```

    ## [1] "Non-Physical"        "0.00189841461293461"

**Observations**:

- Which model is *most accurate*? Which is *least accurate*?
  - The “cheat” model is the most accurate.
  - The “Non-Physical” model is the least accurate.
- What *Category* of variable is `avg_T`? Why is it such an effective
  predictor?
  - `avg_T` is an Output variable. This likely makes it such an
    effective predictor because `T_norm` is also an Output variable.
    Both are determined by `T`, making them inextricably linked.
- Would we have access to `avg_T` if we were trying to predict a *new*
  value of `T_norm`? Is `avg_T` a valid predictor?
  - If trying to predict a new value of `T_norm`, we would not have
    access to `avg_T`, since it is also an Output variable. Hence,
    `avg_T` is not a valid predictor.
- What *Category* of variable is `idx`? Does it have any physical
  meaning?
  - `idx` is a Metadata variable. It does not have any physical meaning,
    as it is a randomized id for each experiment.

### **q4** Use a combination of EDA and train-validation error to build a model by selecting *reasonable* predictors for the `formula` argument. Document your findings under *observations* below. Try to build the most accurate model you can!

``` r
df_train %>%
  select(c(-avg_q, -avg_T, -rms_T, -idx)) %>%
  pivot_longer(
    cols = -T_norm,
    names_to = "var",
    values_to = "value"
  ) %>%
  ggplot() +
  geom_smooth(aes(
    x = T_norm,
    y = value
  )) +
  facet_wrap(facets = vars(var), scales = "free")
```

    ## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

![](c11-psaap-assignment_files/figure-gfm/q4-eda-1.png)<!-- -->

``` r
df_train_input <- 
  df_train %>% 
  select(c(-avg_q, -avg_T, -rms_T, -idx))

for(i in names(df_train_input)){
  df_train_input %>% 
  lm(formula = T_norm ~ get(i)) %>% 
  rsquare(df_train) %>% 
  c(i) %>% 
  print()
}
```

    ## [1] "0.348376351842457" "x"                
    ## [1] "0.0540525890564629" "L"                 
    ## [1] "0.185464256541891" "W"                
    ## [1] "0.0951920799253826" "U_0"               
    ## [1] "0.0743132376025436" "N_p"               
    ## [1] "0.000130195117403531" "k_f"                 
    ## [1] "0.113393894945027" "T_f"              
    ## [1] "0.0240770212790086" "rho_f"             
    ## [1] "0.011769484704092" "mu_f"             
    ## [1] "0.0884671186154316" "lam_f"             
    ## [1] "0.210546712819414" "C_fp"             
    ## [1] "0.090615310018626" "rho_p"            
    ## [1] "0.0385662578839465" "d_p"               
    ## [1] "0.0182645563691741" "C_pv"              
    ## [1] "0.0270031843526128" "h"                 
    ## [1] "0.283926101277186" "I_0"              
    ## [1] "0.00790077418163371" "eps_p"              
    ## [1] "1"      "T_norm"

``` r
colnames(df_train_input)
```

    ##  [1] "x"      "L"      "W"      "U_0"    "N_p"    "k_f"    "T_f"    "rho_f" 
    ##  [9] "mu_f"   "lam_f"  "C_fp"   "rho_p"  "d_p"    "C_pv"   "h"      "I_0"   
    ## [17] "eps_p"  "T_norm"

rsquare(fit_q4, df_train)

rsquare(fit_q4, df_validate)

``` r
## TODO: Fit a model for T_norm using only *principled* predictors, try to
##       optimize your validation error.
fit_q4 <- 
  df_train %>% 
  lm(formula = T_norm ~ (x * L * W) + T_f + rho_f + U_0 + C_fp)

## NOTE: No need to change these error calculations; use them to
##       help define your model
rsquare(fit_q4, df_train)
```

    ## [1] 0.8779688

``` r
rsquare(fit_q4, df_validate)
```

    ## [1] 0.7817653

**Observations**:

- Predictors that seem useful:
  - `I_0`
  - `C_fp`
  - `W`
  - `x`
- To a lesser extent but still useful:
  - `L`
  - `T_f`
  - `rho_f`
  - `U_0`
- Interestingly, adding `I_0` to the current formula improves the fit
  relative to the training set but makes it worse when used on the
  validation set.
- *Note*: You don’t just have to fiddle with `formula`! Remember that
  you have a whole toolkit of *EDA* tools

## Contrasting CI and PI

Let’s revisit the ideas of confidence intervals (CI) and prediction
intervals (PI). Let’s fit a very simple model to these data, one which
only considers the channel location and ignores all other inputs. We’ll
also use the helper function `add_uncertainties()` (defined in the
`setup` chunk above) to add approximate CI and PI to the linear model.

``` r
## NOTE: No need to edit this chunk
fit_simple <-
  df_train %>%
  lm(data = ., formula = T_norm ~ x)

df_intervals <-
  df_train %>%
  add_uncertainties(fit_simple, interval = "confidence", prefix = "ci") %>%
  add_uncertainties(fit_simple, interval = "prediction", prefix = "pi")
```

The following figure visualizes the regression CI and PI against the
objects they are attempting to capture:

``` r
## NOTE: No need to edit this chunk
df_intervals %>%
  select(T_norm, x, matches("ci|pi")) %>%
  pivot_longer(
    names_to = c("method", ".value"),
    names_sep = "_",
    cols = matches("ci|pi")
  ) %>%

  ggplot(aes(x, fit)) +
  geom_errorbar(
    aes(ymin = lwr, ymax = upr, color = method),
    width = 0.05,
    size = 1
  ) +
  geom_smooth(
    data = df_psaap %>% mutate(method = "ci"),
    mapping = aes(x, T_norm),
    se = FALSE,
    linetype = 2,
    color = "black"
   ) +
  geom_point(
    data = df_validate %>% mutate(method = "pi"),
    mapping = aes(x, T_norm),
    size = 0.5
  ) +

  facet_grid(~method) +
  theme_minimal() +
  labs(
    x = "Channel Location (-)",
    y = "Normalized Temperature Rise (-)"
  )
```

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

    ## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

    ## Warning in simpleLoess(y, x, w, span, degree = degree, parametric =
    ## parametric, : pseudoinverse used at 0.24625

    ## Warning in simpleLoess(y, x, w, span, degree = degree, parametric =
    ## parametric, : neighborhood radius 0.50375

    ## Warning in simpleLoess(y, x, w, span, degree = degree, parametric =
    ## parametric, : reciprocal condition number 5.9817e-17

    ## Warning in simpleLoess(y, x, w, span, degree = degree, parametric =
    ## parametric, : There are other near singularities as well. 0.25376

![](c11-psaap-assignment_files/figure-gfm/data-simple-model-vis-1.png)<!-- -->

Under the `ci` facet we have the regression confidence intervals and the
mean trend (computed with all the data `df_psaap`). Under the `pi` facet
we have the regression prediction intervals and the `df_validation`
observations.

**Punchline**:

- Confidence intervals are meant to capture the *mean trend*
- Prediction intervals are meant to capture *new observations*

Both CI and PI are a quantification of the uncertainty in our model, but
the two intervals designed to answer different questions.

Since CI and PI are a quantification of uncertainty, they should tend to
*narrow* as our model becomes more confident in its predictions.
Building a more accurate model will often lead to a reduction in
uncertainty. We’ll see this phenomenon in action with the following
task:

### **q5** The following code will construct a predicted-vs-actual plot with your model from *q4* and add prediction intervals. Study the results and answer the questions below under *observations*.

``` r
## TODO: Run this code and interpret the results
## NOTE: No need to edit this chunk
## NOTE: This chunk will use your model from q4; it will predict on the
##       validation data, add prediction intervals for every prediction,
##       and visualize the results on a predicted-vs-actual plot. It will
##       also compare against the simple `fit_simple` defined above.
bind_rows(
  df_validate %>% 
    add_uncertainties(fit_simple, interval = "prediction", prefix = "pi") %>% 
    select(T_norm, pi_lwr, pi_fit, pi_upr) %>% 
    mutate(model = "x only"),
  df_validate %>% 
    add_uncertainties(fit_q4, interval = "prediction", prefix = "pi") %>% 
    select(T_norm, pi_lwr, pi_fit, pi_upr) %>% 
    mutate(model = "q4"),
) %>% 
  
  ggplot(aes(T_norm, pi_fit)) +
  geom_abline(slope = 1, intercept = 0, color = "grey80", size = 2) +
  geom_errorbar(
    aes(ymin = pi_lwr, ymax = pi_upr),
    width = 0
  ) +
  geom_point() +
  
  facet_grid(~ model, labeller = label_both) +
  theme_minimal() +
  labs(
    title = "Predicted vs Actual",
    x = "Actual T_norm",
    y = "Predicted T_norm"
  )
```

![](c11-psaap-assignment_files/figure-gfm/q5-task-1.png)<!-- -->

**Observations**:

- Which model tends to be more accurate? How can you tell from this
  predicted-vs-actual plot?
  - My q4 model tends to be more accurate, as shown by how far the
    points are spread from the grey line. The points in my model are
    much closer to the line, meaning the predicted and actual `T_norm`
    values are much closer.
- Which model tends to be *more confident* in its predictions? Put
  differently, which model has *narrower prediction intervals*?
  - My q4 model tends to be more confident in its predictions, as shown
    by its much narrower prediction intervals.
- How many predictors does the `fit_simple` model need in order to make
  a prediction? What about your model `fit_q4`?
  - `fit_simple` only needs 1 predictor, while my model needs 7.

Based on these results, you might be tempted to always throw every
reasonable variable into the model. For some cases, that might be the
best choice. However, some variables might be *outside our control*; for
example, variables involving human behavior cannot be fully under our
control. Other variables may be *too difficult to measure*; for example,
it is *in theory* possible to predict the strength of a component by
having detailed knowledge of its microstructure. However, it is
*patently infeasible* to do a detailed study of *every single component*
that gets used in an airplane.

In both cases—human behavior and variable material properties—we would
be better off treating those quantities as random variables. There are
at least two ways we could treat these factors: 1. Explicitly model some
inputs as random variables and construct a model that *propagates* that
uncertainty from inputs to outputs, or 2. Implicitly model the
uncontrolled variables by not including them as predictors in the model,
and instead relying on the error term $\epsilon$ to represent these
unaccounted factors. You will pursue strategy 2. in the following Case
Study.

# Case Study: Predicting Performance Ranges

### **q6** You are consulting with a team that is designing a prototype heat transfer device. They are asking you to help determine a *dependable range of values* for `T_norm` they can design around for this *single prototype*. The realized value of `T_norm` must not be too high as it may damage the downstream equipment, but it must also be high enough to extract an acceptable amount of heat.

In order to maximize the conditions under which this device can operate
successfully, the design team has chosen to fix the variables listed in
the table below, and consider the other variables to fluctuate according
to the values observed in `df_psaap`.

| Variable | Value    |
|----------|----------|
| `x`      | 1.0      |
| `L`      | 0.2      |
| `W`      | 0.04     |
| `U_0`    | 1.0      |
| (Other)  | (Varies) |

Your task is to use a regression analysis to deliver to the design team
a *dependable range* of values for `T_norm`, given their proposed
design, and at a fairly high level `0.8`. Perform your analysis below
(use the helper function `add_uncertainties()`!), and answer the
questions below.

*Hint*: This problem will require you to *build a model* by choosing the
appropriate variables to include in the analysis. Think about *which
variables the design team can control*, and *which variables they have
chosen to allow to vary*. You will also need to choose between computing
a CI or PI for the design prediction.

``` r
# NOTE: No need to change df_design; this is the target the client
#       is considering
df_design <- tibble(x = 1, L = 0.2, W = 0.04, U_0 = 1.0)
# NOTE: This is the "probability" level the customer wants
pr_level <- 0.8

## TODO: Fit a model, assess the uncertainty in your prediction, 
#        use the validation data to check your uncertainty estimates, and 
#        make a recommendation on a *dependable range* of values for T_norm
#        at the point `df_design`
fit_q6 <-
  df_train %>% 
  lm(formula = T_norm ~ x * L * W * U_0)

rsquare(fit_q6, df_train)
```

    ## [1] 0.7177773

``` r
rsquare(fit_q6, df_validate)
```

    ## [1] 0.7057262

``` r
df_intervals_q6 <-
  df_train %>%
  add_uncertainties(fit_q6, interval = "confidence", prefix = "ci", level = 0.8) %>%
  add_uncertainties(fit_q6, interval = "prediction", prefix = "pi", level = 0.8)

df_design %>% 
  add_uncertainties(fit_q6, interval = "prediction", prefix = "pi", level = 0.8)
```

    ## # A tibble: 1 × 7
    ##       x     L     W   U_0 pi_fit pi_lwr pi_upr
    ##   <dbl> <dbl> <dbl> <dbl>  <dbl>  <dbl>  <dbl>
    ## 1     1   0.2  0.04     1   1.92   1.28   2.57

``` r
df_validate %>%
  add_uncertainties(fit_q6, interval = "prediction", prefix = "pi", level = 0.8) %>% 
  select(T_norm, pi_lwr, pi_fit, pi_upr) %>% 
  mutate(in_interval = (T_norm <= pi_upr) & (T_norm >= pi_lwr)) %>% 
  group_by(in_interval) %>% 
  count()
```

    ## # A tibble: 2 × 2
    ## # Groups:   in_interval [2]
    ##   in_interval     n
    ##   <lgl>       <int>
    ## 1 FALSE           3
    ## 2 TRUE           57

``` r
bind_rows(
  df_validate %>% 
    add_uncertainties(fit_q6, interval = "prediction", prefix = "pi", level = 0.8) %>% 
    select(T_norm, pi_lwr, pi_fit, pi_upr) %>% 
    mutate(in_interval = (T_norm <= pi_upr) & (T_norm >= pi_lwr))
) %>% 
  
  ggplot(aes(T_norm, pi_fit)) +
  geom_abline(slope = 1, intercept = 0, color = "grey80", size = 2) +
  geom_errorbar(
    aes(ymin = pi_lwr, ymax = pi_upr, color = in_interval),
    width = 0
  ) +
  geom_point() +
  theme_minimal() +
  labs(
    title = "Predicted vs Actual",
    x = "Actual T_norm",
    y = "Predicted T_norm"
  )
```

![](c11-psaap-assignment_files/figure-gfm/q6-validation-1.png)<!-- -->

**Recommendation**:

- How much do you trust your model? Why?
  - I have reasonable trust in my model because most of the points fall
    in the prediction interval, it has an r-squared of \~0.7, and it
    takes into account all of the controlled variables.
- What kind of interval—confidence or prediction—would you use for this
  task, and why?
  - For this task, I believe I would use a prediction interval because
    the range of that interval would give me a dependable range of
    potential `T_norm` values to report to the client. Since a CI tells
    me where I’m most likely to find the points, versus a PI which tells
    me the range that the points are in, the CI wouldn’t be up to the
    task here.
- What fraction of validation cases lie within the interval you predict?
  How does this compare with `pr_level`?
  - 57 of 60 validation cases lie within the interval I predicted, which
    is 0.95, greater than the `pr_level` of 0.8.
  - Even when aiming for the `pr_level` of 0.8, I notice that it is
    difficult to hit that number.
- What interval for `T_norm` would you recommend the design team to plan
  around?
  - I would recommend the design team plan around an interval of
    `[1.2788, 2.5679]` for `T_norm` .
- Are there any other recommendations you would provide?
  - I would recommend that the client potentially change some of their
    controlled variables, as with their current set there is room for a
    very wide range of `T_norm` values, likely making their device
    unnecessarily complicated or potentially sacrificing its
    effectiveness.

*Bonus*: One way you could take this analysis further is to recommend
which other variables the design team should tightly control. You could
do this by fixing values in `df_design` and adding them to the model. An
exercise you could carry out would be to systematically test the
variables to see which ones the design team should more tightly control.

# References

- \[1\] Jofre, del Rosario, and Iaccarino “Data-driven dimensional
  analysis of heat transfer in irradiated particle-laden turbulent
  flow” (2020) *International Journal of Multiphase Flow*,
  <https://doi.org/10.1016/j.ijmultiphaseflow.2019.103198>
