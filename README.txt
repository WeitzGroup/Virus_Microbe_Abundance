R scripts and data for "An examination of the relationship between virus and microbial cell abundances in the global oceans" by Wigington et al. (in review)

Contact:
Joshua S. Weitz - corresponding author
jsweitz@gatech.edu

For users with RStudio, the file VirMic_analysis.Rmd includes all of the code for re-running the analysis, including a list of packages which are installed (if needed) with the first chunk of code. The analysis is broken into chunks which can be run as independently of one another. 

For users who choose to run R in a terminal, running the code below creates a function which will run all of the code in the VirMic_analysis.Rmd file.

	runAllChunks <- function(rmd, envir=globalenv()){
	  tempR <- tempfile(tmpdir = ".", fileext = ".R")
	  on.exit(unlink(tempR))
	  knitr::purl(rmd, output=tempR)
	  sys.source(tempR, envir=envir)
	}
	
	runAllChunks("VirMic_analysis.Rmd")

Note:
The manuscript indicates that 10,000 bootstrap replicates were made which is reflected in the output figures and datasets. However, for the purpose of reproducibility, the R script indicates that 100 replicates are to be made so as not to burden users with excessive replicates until they are ready to change the number of replicates themselves. At this point, within the same cluster in the R script, the saving step can be uncommented to save the intermediate datasets to reflect the desired number of replicates by the experienced user. 
