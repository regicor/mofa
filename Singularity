Bootstrap:docker
From:ubuntu:18.04

%post
    # Installing ubuntu dependencies
    apt-get update
    DEBIAN_FRONTEND=noninteractive
    apt-get install -y apt-utils
    apt-get install -y tzdata
    apt-get install -y software-properties-common
    apt-get update
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
    add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/'
    apt-get update
    apt-get install -y libcurl4-gnutls-dev libxml2-dev libssl-dev libmariadb-client-lgpl-dev ibglib2.0-dev libcairo2-dev \
    ghostscript libxt-dev 
    #libssh2-1-dev
    # Installing R and python-pip
    apt-get install -y r-base python-pip
    # Installing MOFA python dependencies
    pip install mofapy2
    apt-get clean
    rm -rf /var/lib/apt/lists/*
    # Installing all R packages
    Rscript -e 'r = getOption("repos"); r["CRAN"] = "https://cran.rstudio.com/"; options(repos = r); install.packages(c("devtools","BiocManager")); BiocManager::install("MultiAssayExperiment")'
    Rscript -e 'install.packages("devtools", dependencies = TRUE, repos = "https://cran.rstudio.com"); library(devtools); devtools::install_github("bioFAM/MOFA2/MOFA2", build_opts = c("--no-resave-data --no-build-vignettes"))'
%test
    R --version
    
    
    
    
