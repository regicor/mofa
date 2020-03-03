Bootstrap:docker  
From:ubuntu:18.04

%post
    # Installing ubuntu dependencies
    apt-get update
    apt-get install -y libcurl4-gnutls-dev libxml2-dev libssl-dev libmariadb-client-lgpl-dev ibglib2.0-dev libcairo2-dev \
    ghostscript libxt-dev r-base python-pip
    pip install mofapy2
    apt-get clean
    rm -rf /var/lib/apt/lists/*
    # Installing all R packages
    Rscript -e 'r = getOption("repos"); r["CRAN"] = "https://cran.rstudio.com/"; options(repos = r); install.packages(c("devtools","BiocManager"))'
    Rscript -e 'r = getOption("repos"); r["CRAN"] = "https://cran.rstudio.com/"; options(repos = r); source("https://bioconductor.org/biocLite.R"); BiocInstaller::biocLite("cowplot")'
    Rscript -e 'install.packages("devtools", dependencies = TRUE, repos = "https://cran.rstudio.com"); library(devtools); devtools::install_github("bioFAM/MOFA2/MOFA2", build_opts = c("--no-resave-data --no-build-vignettes"))'
    ##
%test
    R --version
    
    
    
    
