# bchwtz-courserunner

FROM rocker/verse:devel

# Install R-Dependencies
RUN Rscript -e 'install.packages(c("kableExtra","HistogramTools","ineq","fGarch","gtools","vcd","texreg","car","remotes","transformr","feasts"))'

# Install ImageMagick and set PDF Policy (insecure)
RUN sudo apt update &&\
    sudo apt install -yq imagemagick &&\
    sudo sed -i -e 's/none/read|write/g' /etc/ImageMagick-6/policy.xml

# Install FHSWF & TeX-Dependencies & Check for Functionality
RUN Rscript -e 'remotes::install_github("bchwtz/fhswf", upgrade = "never")' &&\
    Rscript -e 'fhswf::install_fhswf()'

RUN Rscript -e 'rmarkdown::draft("A.Rmd", template = "fhswf-presentation", package = "fhswf", edit=FALSE); fhswf::render_presentation("A/A.Rmd")' &&\
    rm -r A/ &&\
    Rscript -e 'rmarkdown::draft("B.Rmd", template = "fhswf-seminarpaper", package = "fhswf", edit=FALSE); fhswf::render_seminarpaper("B/B.Rmd")' &&\
    rm -r B/

# Exemplarily build Course Material to check for Functionality
RUN git clone https://github.com/bchwtz/bchwtz-stat &&\
    cd bchwtz-stat/slides &&\
    make clean pdf gif clean-cache &&\
    cd .. &&\
    Rscript -e 'bookdown::render_book("index.Rmd")' &&\
    cp -r slides _book &&\
    cp -r data _book &&\
    cd .. &&\
    rm -r bchwtz-stat/




