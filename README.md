Knitr cache invalidation problem
================================

In RStudio projects using `BuildType: Package` option, the cache of RMarkdown files
in the `vignettes` directory is always invalidated.

To demonstrate this, I have created a minimal RMarkdown file that outputs one
random number, and placed copies in the main directory or in subdirectories
called `subdir` or `vignettes`.

    $ find . -name KnitrCacheTest.Rmd | xargs md5sum
    cac5e8bcaf9cf4d5c4c07558beec6bb8  ./KnitrCacheTest.Rmd
    cac5e8bcaf9cf4d5c4c07558beec6bb8  ./vignettes/KnitrCacheTest.Rmd
    cac5e8bcaf9cf4d5c4c07558beec6bb8  ./subdir/KnitrCacheTest.Rmd

Two project files, differing only by `BuildType: Package` are available
to open the project in a configuration that will trigger or not the
issue.  The files are called `KnitrCacheInvalidationProblem.Rproj`
and `KnitrCacheInvalidationNoProblem.Rproj`.

The issue is discussed in more details on RStudio's support site:

<https://community.rstudio.com/t/rmarkdown-not-using-the-cache-under-linux/141903>
