Bioconductor has a repository and release schedule that differs from R.
It has a 'devel' and 'release' branch. The 'release' branch is emitted
twice per year (in April and October), to which bug fixes but not new features
are introduced. The whole system is a bit complicated. Basically the best way 
to install Bioconductor packages is with `BiocInstaller::biocLite()`.

BiocInstaller
=============
* Used to install and update Bioconductor, CRAN and some GitHub packages.
* Using `source("http://bioconductor.org/biocLite.R")` installs *and*
attaches the `BiocInstaller` package, with which you can install other
packages and check the version of Bioconductor in use.
* Since the `BiocInstaller` package is automatically attached, you don't need
to load it with `library()` or `require()`:



```r
search()
```

```
##  [1] ".GlobalEnv"        "package:stats"     "package:graphics" 
##  [4] "package:grDevices" "package:utils"     "package:datasets" 
##  [7] "package:vimcom"    "package:setwidth"  "package:colorout" 
## [10] "package:methods"   "Autoloads"         "package:base"
```

```r
source("http://bioconductor.org/biocLite.R")
```

```
## Bioconductor version 3.1 (BiocInstaller 1.18.4), ?biocLite for help
```

```r
search()
```

```
##  [1] ".GlobalEnv"            "package:BiocInstaller"
##  [3] "package:stats"         "package:graphics"     
##  [5] "package:grDevices"     "package:utils"        
##  [7] "package:datasets"      "package:vimcom"       
##  [9] "package:setwidth"      "package:colorout"     
## [11] "package:methods"       "Autoloads"            
## [13] "package:base"
```

### biocLite
* Installs or updates Bioconductor, CRAN and some GitHub packages in a
Bioconductor release.

* It is a wrapper around `install.packages()`, but with the repository chosen
according to the version of Bioconductor in use, rather than to the version 
relevant at the time of the R release.

* It also nudges users to update packages.


**Usage**

```r
biocLite(pkgs=c("Biobase", "IRanges", "AnnotationDbi"),
         suppressUpdates=FALSE,
         suppressAutoUpdate=FALSE,
         siteRepos=character(),
         ask=TRUE, ...)
```

**Examples**


```r
# Installs default packages (Biobase, IRanges and AnnotationDbi) if not already
# installed, and updates previously installed packages.
biocLite()

# Install a CRAN package
biocLite("Hmisc")
# Install several Bioconductor packages
biocLite(c("limma", "edgeR"))
# Install a GitHub package
biocLite("kbroman/broman")
```

### Package Groups
Returns the names of packages associated with Bioconductor publications.

* `all_group()`: All Bioconductor packages;
* `biocases_group()`: Bioconductor Case Studies;
* `RBioinf_group()`: R Programming for Bioinformatics;
* `monograph_group()`: Bioinformatics and Computational Biology Solutions
Using R and Bioconductor;

**Examples**

```r
bioc_pkgs <- all_group()
str(bioc_pkgs)
```

```
##  chr [1:1024] "a4" "a4Base" "a4Classif" "a4Core" "a4Preproc" ...
```

```r
bioc_pkgs[sample(length(bioc_pkgs), 10)]
```

```
##  [1] "ArrayExpress" "proteoQC"     "bgafun"       "GSEABase"    
##  [5] "switchBox"    "Category"     "InPAS"        "gpls"        
##  [9] "AtlasRDF"     "siggenes"
```


### useDevel
Use the development version of Bioconductor. See `?BiocInstaller::usedevel` for
an excellent description.

