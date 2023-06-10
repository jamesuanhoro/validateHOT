
<!-- README.md is generated from README.Rmd. Please edit that file -->

# validateHOT 🎯

<!-- badges: start -->
<!-- badges: end -->

The goal of validateHOT is to validate the results of your validation
task (also known as holdout task). A validation task is essential to
make sure that your collected data of a *MaxDiff*, *CBC*, or *ACBC* are
valid and can also predict outside task that were **not** included in
estimating your utility scores. Although commercial studies often do not
include a validation/holdout task (Yang, Toubia, and Jong 2018), it is
highly recommended to do so (Orme 2015; Rao 2014). This validation/
holdout task does not only help to check whether everything went right
during data collection but also to determine your final model.
<code>validatHOT</code> provides some of the relevant metrics to test
the performance of your data in predicting a holdout task. In [Sawtooth
Software’s](https://sawtoothsoftware.com/) *CBC* a fixed validation/
holdout task is automatically implemented. If you conduct a *MaxDiff* or
*ACBC* study these have to be programmed by yourself.

👉🏾 <u>**What you need to provide**</u>: <br> After collecting your data,
and running your initial *Hierarchical Bayes* models, you can turn to
<code>validateHOT</code> and test how good your model predicts choices
in the validation/ holdout task. Herefore, you only have to insert your
**raw** utility scores as well as the actual choice of your validation/
holdout task. You can use the <code>merge()</code> provided by
<code>base</code> package (2023). Afterward, you can read in your data
file and enjoy <code>validateHOT</code>.

👈🏾 <u>**What you get**</u>:<br> At the moment, <code>validateHOT</code>
provides functions for 3 key areas:

<ul>
<li>
validation metrics mainly reported in preference measurement studies
</li>
<li>
metrics that are usually reported in machine learning (i.e., confusion
matrix)
</li>
<li>
simulation methods, for example, to determine optimal product
combinations
</li>
</ul>

For all 3 key areas, the <code>createHOT</code> function is essential.
This function creates the total utilities for each alternative in the
validation/holdout task and also in the simulation method, respectively.
Rao (2014, 82) mentions the additive utility model stating that the
total utility of a profile or conjoint model is the sum of its attribute
levels. <code>createHOT</code> will do exactly this for you.

### Classical validation metrics

<ul>
<li>
<code>hitrate</code>: creates the *Hit Rate* (correctly predicted
choices) of your validation task. The output will contain the chance
level in your validation task ($\frac{1}{alternatives}$) in percentage.
The number of correctly predicted partcipants’ choices as well as the
percentage of how many choices were correctly predicted. If you specify
an optional <code>Group</code> argument the output is split by groups.
</li>
<li>
<code>kl</code>: Kullback-Leibler-Divergence which measures the
divergence between the actual choice distribution and the predicted
choice distribution (Ding et al. 2011; HG 2018). Output provides both
divergence between *predicted* from *observed* and *observed* from
*predicted* due to the asymmetry of the Kullback-Leibler divergence. If
you specify an optional <code>Group</code> argument the output is split
by groups.
</li>
<li>
<code>mae</code>: average absolute error, i.e., deviation between
predicted and stated choice share. If you specify an optional
<code>Group</code> argument the output is split by groups.
</li>
<li>
<code>medae</code>: since the averaged absolute error can be highly
influenced by the If you specify an optional <code>Group</code> argument
the output is split by groups.
</li>
<li>
<code>mhp</code>: averaged hit probability of participant’s actual
choice in the validation/ holdout task. If you specify an optional
<code>Group</code> argument the output is split by groups.
</li>
<li>
<code>rmse</code>: provides the root-mean-squared error of deviation
between predicted and stated choice share. If you specify an optional
<code>Group</code> argument the output is split by groups.
</li>
</ul>

### Confusion Matrix

<ul>
<li>
<code>accuracy</code>:
</li>
<li>
<code>f1</code>:
</li>
<li>
<code>precision</code>:
</li>
<li>
<code>recall</code>:
</li>
<li>
<code>specificity</code>:
</li>
</ul>

### Simulation Methods

<ul>
<li>
<code>freqassort</code>: Inspired by the former
[*turfR*](https://github.com/cran/turfR) package,
<code>freqassort</code> will give you the averaged frequency, how many
products the participants will choose from your in the function
determined potential assortment. For the <code>method</code> argument
you can decide between <code>method = “threshold”</code> (if utility of
product is larger than the utility of *none*, it is marked as potential
purchase option) and <code>method = “First Choice”</code> (only product
with highest utility is considered. If its utility is above the utility
of *none*, it is marked as potential purchase option). If you specify an
optional <code>Group</code> argument the output is split by groups.
</li>
<li>
<code>reach</code>: Inspired by the former
[*turfR*](https://github.com/cran/turfR) package, <code>reach</code>
will give you the averaged percentage of how many participants you can
reach (buy *at least* one of the products) with your in the function
determined potential assortment. or the <code>method</code> argument you
can decide between <code>method = “threshold”</code> (if utility of
product is larger than the utility of *none*, it is marked as potential
purchase option) and <code>method = “First Choice”</code> (only product
with highest utility is considered. If its utility is above the utility
of *none*, it is marked as potential purchase option). If you specify an
optional <code>Group</code> argument the output is split by groups.
</li>
<li>
<code>shareofpref</code>: provides you the aggregated share of
preference, including the lower and upper confidence interval, which is
calculated according to the $mean +/- 1.96 x \frac{sd}{\sqrt(n)}$. If
you specify an optional <code>Group</code> argument the output is split
by groups and provided in a <code>list</code> element.
</li>
</ul>

### Data Frames provided by <code>validateHOT</code>

<ul>
<li>
<code>ACBC</code>: Example data set with raw utilities of an *ACBC*
study conducted in Sawtooth. Price was linear-coded while the other
attributes were coded as part-worths.
</li>
<li>
<code>ACBC_interpolate</code>: Example data set with raw utilities of an
*ACBC* study conducted in Sawtooth. Price was piecewise-coded, another
attribute was linear-coded while the other attributes were coded as
part-worths.
</li>
<li>
<code>CBC</code>: Example data set with raw utilities of an *CBC* study
conducted in Sawtooth. All attributes were coded as part-worth.
</li>
<li>
<code>CBC_lin</code>: Example data set with raw utilities of an *CBC*
study conducted in Sawtooth. One attribute was linear coded while the
other attributes are part-worth coded.
</li>
<li>
<code>MaxDiff</code>: Example data set with raw utilities of an
*MaxDiff* study conducted in Sawtooth.
</li>
</ul>
<ul>
<li>
<code>accuracy</code>: generates the number of correct predicted choice
or no-choice divided by the total number of predictions. Only possible
for a binary output, e.g., buy vs. no-buy correctly predicted.
</li>
<li>
<code>f1</code>: generates the F1-Score. F1-Score is calculated by the
following formula $\frac{2 * precision * recall}{precision + recall}$.
Only possible for a binary output, e.g., buy vs. no-buy correctly
predicted.
</li>
</ul>

## Why <code>validateHOT</code>

comparison to Metrics

studi seminar für preference measurement techniques –\> often not
getting in touch with *R* before, so wanted to make it easier for them.
this

## Installation

You can install the development version of validateHOT from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("JoshSchramm94/validateHOT")
```

## Example

## References

<div id="refs" class="references csl-bib-body hanging-indent">

<div id="ref-ding2011" class="csl-entry">

Ding, Min, John R. Hauser, Songting Dong, Daria Dzyabura, Zhilin Yang,
SU Chenting, and Steven P. Gaskin. 2011. “Unstructured Direct
Elicitation of Decision Rules.” *Journal of Marketing Research* 48 (1):
116–27. <https://doi.org/10.1509/jmkr.48.1.116>.

</div>

<div id="ref-philentropy" class="csl-entry">

HG, Drost. 2018. “Philentropy: Information Theory and Distance
Quantification with r” 3: 765.
<https://joss.theoj.org/papers/10.21105/joss.00765>.

</div>

<div id="ref-Orme.2015" class="csl-entry">

Orme, Bryan K. 2015. “Including Holdout Choice Tasks in Conjoint
Studies.”
<https://sawtoothsoftware.com/resources/technical-papers/including-holdout-choice-tasks-in-conjoint-studies>.

</div>

<div id="ref-base" class="csl-entry">

R Core Team. 2023. “R: A Language and Environment for Statistical
Computing.” <https://www.R-project.org/>.

</div>

<div id="ref-rao2014a" class="csl-entry">

Rao, Vithala R. 2014. *Applied Conjoint Analysis*. Springer Berlin
Heidelberg. <https://doi.org/10.1007/978-3-540-87753-0>.

</div>

<div id="ref-yang2018" class="csl-entry">

Yang, Liu (Cathy), Olivier Toubia, and Martijn G. de Jong. 2018.
“Attention, Information Processing, and Choice in Incentive-Aligned
Choice Experiments.” *Journal of Marketing Research* 55 (6): 783–800.
<https://doi.org/10.1177/0022243718817004>.

</div>

</div>
