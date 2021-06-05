# Goals 

## Github Actions workflow
	- See here for some good examples: https://github.com/actions/starter-workflows

### BiocSwirl Workflows: 
## CI
What checks can we implement to help pull requests better integrate into our existing codebases? 

## Project Management 
How can we create dynamic outputs to our Slack and Asana and meet project milestones, and verify the file structures of our lessons, along with managing file size?   

## Code Scans
How can we verify the integrity of the R code and yaml files usign linters and code checks? 

## Deploy
When/how to create release versions and communicate with Bioconductor or CRAN? How can we let users know about lesson updates? 

## Automation
How can we automate all of the above to work seamlessly? 

### tools 
	- Docker, R CMD Check, github actions, docker image, testthat, jobs, etc. 

## Job Structure
### Job Requirements
### Jobs needed
	- R version Check 
	- Operating System Check 
	- File Directory check for install location 
	- YAML lintr for lesson.yaml
	- Check file structure integrity for swirl lessons/courses, also check for duplicates 
	- Check for large files
	  


