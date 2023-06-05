
<!-- README.md is generated from README.Rmd. Please edit that file -->

# validateHOT 🎯

<!-- badges: start -->
<!-- badges: end -->

The goal of validateHOT is to validate the results of your validation
task (also known as holdout task). A validation task is essential to
make sure that your collected data of a *MaxDiff*, *CBC*, or *ACBC* are
valid and can also predict outside task that were **not** included in
estimating your utility scores. At the moment, validateHOT provides the
following functions:

<ul>
<li>
`createHOT`: creates the validation/holdout task for you. For example,
in a *CBC* the total utilities are calculated by the sum of each
attribute level. You have to specify the attribute levels for each
alternative in the validation/holdout task and it will calculate the
total utility for each alternative in the validation/holdout task.
</li>
<li>
`accuracy`: generates the number of correct predicted choice or
no-choice divided by the total number of predictions. Only possible for
a binary output, e.g., buy vs. no-buy correctly predicted.
</li>
<li>
`f1`: generates the F1-Score. F1-Score is calculated by the following
formula $\frac{2 * precision * recall}{precision + recall}$. Only
possible for a binary output, e.g., buy vs. no-buy correctly predicted.
</li>
<li>
`f1`: generates the F1-Score. F1-Score is calculated by the following
formula $\frac{2 * precision * recall}{precision + recall}$. Only
possible for a binary output, e.g., buy vs. no-buy correctly predicted.
</li>

## Installation

You can install the development version of validateHOT from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("JoshSchramm94/validateHOT")
```

## Example

This is a basic example which shows you how to solve a common problem:

What is special about using `README.Rmd` instead of just `README.md`?
You can include R chunks like so:

You’ll still need to render `README.Rmd` regularly, to keep `README.md`
up-to-date. `devtools::build_readme()` is handy for this. You could also
use GitHub Actions to re-render `README.Rmd` every time you push. An
example workflow can be found here:
<https://github.com/r-lib/actions/tree/v1/examples>.
