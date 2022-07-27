# bchwtz-courserunner

FROM rocker/verse:devel

# Install R-Dependencies
RUN Rscript -e 'install.packages(c("kableExtra","HistogramTools","ineq","fGarch","gtools","vcd","texreg","car","remotes"))'
# Install remote R-Dependencies
RUN Rscript -e 'remotes::install_github("bchwtz/fhswf", upgrade = "never")'
# Install Sys-Dependencies
RUN sudo apt update; sudo apt install -yq imagemagick
# Set Imagemagick PDF Policy (insecure)
RUN sudo sed -i -e 's/none/read|write/g' /etc/ImageMagick-6/policy.xml
# Install Tex-Dependencies
RUN tlmgr install microtype; tlmgr install multirow; tlmgr install carlito