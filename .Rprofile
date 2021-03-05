# set default CRAN mirror
local({r <- getOption("repos")
      r["CRAN"] <- "https://cloud.r-project.org"
      options(repos=r)})

# Function to quiet package loading
sshhh <- function(a.package){
  suppressWarnings(suppressPackageStartupMessages(
    library(a.package, character.only=TRUE)))
}

# Some R options
options(bitmapType="cairo")        # use cairo for images
options(stringsAsFactors=FALSE)    # stringsAsFactors=HELLNO
options(max.print=20)
options(scipen=10)                 # no scientific notation
options(editor="vim")              # the best there is
options(warn = -1)                 # no warnings
options(useFancyQuotes = FALSE)    # just no
options(menu.graphics=FALSE)       # no time for Tk to load
options(width = 80)
options(prompt="> ")
options(continue="... ")           # helps me realize when I forget to close
options(tab.width = 2)             # Tab width
utils::rc.settings(ipck=TRUE)      # tab complete package names

# pretty colors
require("colorout")

# I never want to save
q <- function (save="no", ...) {
  quit(save=save, ...)
}

# set up .Rhistory dump
.First <- function(){
  if(interactive()){
    library(utils)
    timestamp(,prefix=paste("##------ [",getwd(),"] ",sep=""))
  }
}

.Last <- function(){
  if(interactive()){
    hist_file <- Sys.getenv("R_HISTFILE")
    if(hist_file=="") hist_file <- "~/.rhist"
    savehistory(hist_file)
  }
}

# list of packages to auto-load if interactive
auto.loads <-c(
	"devtools",
	"magrittr",
	"dplyr",
	"tidyr",
	"readr",
	"ggplot2",
	"purrr",
	"knitr",
	"ggrepel",
	"patchwork",
	"cowplot")
# auto-load quietly
if(interactive()){
  invisible(sapply(auto.loads, sshhh))
}
# sapply(auto.loads, function(x) library(x, character.only=TRUE))

message("\n*** Successfully loaded expanded .Rprofile ***\n")
