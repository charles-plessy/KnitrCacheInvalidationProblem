Knitr cache invalidation problem
================================

On one of my computer and one of my colleague's computer, some knitr vignettes
always have their cache invalidated because their computations are made in a
temporary directory with a randomised name.

Here the files `KnitrCacheOK.Rmd` and `vignettes/KnitrCacheInvalid.Rmd` are the
same (MD5 sum `cac5e8bcaf9cf4d5c4c07558beec6bb8`), but knitting the one in the
`vignettes` directory always yields a different random number, demonstrating
that the cache was not used.

The problem appears to be triggered by the use of `BuildType: Package` in the
RStudio project file.  Thus, if you open the project with the
`KnitrCacheInvalidationProblem.Rproj` you will reproduce the problem, but not
with the `KnitrCacheInvalidationNoProblem.Rproj` file, which differs only by a
single line.

    diff KnitrCacheInvalidationProblem.Rproj KnitrCacheInvalidationNoProblem.Rproj
    15d14
    < BuildType: Package

The issue is discussed in more details on RStudio's support site:

<https://community.rstudio.com/t/rmarkdown-not-using-the-cache-under-linux/141903>

It might have been reported earlier to some extent at:

<https://community.rstudio.com/t/caching-chunks-in-rstudio-does-not-work/9040>
