# HackseqRNA Development Environment Setup Guide! 

## General 
1. Install R https://cloud.r-project.org/ 
(Rstudio is also very useful as an IDE https://rstudio.com/products/rstudio/download/) 

2. Install Git https://git-scm.com/book/en/v2/Getting-Started-Installing-Git


## BiocSwirl
1. Clone the repo into your directory of choice
(using HTTPS) 
```
git clone https://github.com/biocswirl-dev-team/BiocSwirl.git
```
2. In R, install the following packages using the following lines: 
```
install.packages(c("swirlify", "BiocManager")) 
```
3. Follow the Bioconductor guide on installing packages: https://cran.r-project.org/web/packages/BiocManager/vignettes/BiocManager.html

4. Follow the Swirlify guide on writing courses: http://swirlstats.com/swirlify/

## BiocTerm
1. Install Tmux and vim
(on ubuntu) 
```
sudo apt update && sudo apt upgrade 
sudo apt install tmux vim 
```
2. Clone the repo into your directory of choice
(using HTTPS) 
```
git clone https://github.com/biocswirl-dev-team/BiocTerm.git
```
3. Launch Tmux with the BiocTerm configs
```
./dev-biocterm.sh
```
If you have issues launching, make sure you are in the repo directory and the script has the correct permissions to run (you can use chmod for this). 

## Development workflow
![](https://i.imgur.com/1L8WBer.png?raw=true)
