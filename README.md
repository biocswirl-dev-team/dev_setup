# Goals 
* CI: What checks can we implement to help pull requests better integrate into our existing codebases? 
* Project Management: How can we create dynamic outputs to our Slack and Asana and meet project milestones, and verify the file structures of our lessons, along with managing file size? 
* Code Scans: How can we verify the integrity of the R code and yaml files usign linters and code checks? 
* Deploy: When/how to create release versions and communicate with Bioconductor or CRAN? How can we let users know about lesson updates? 
* Automation: How can we automate all of the above to work seamlessly? 

# Actions Workflows
We currently have two workflows that are actively being maintained for the BiocSwirl project. 

### course-install.yaml
Installs all courses using devtools, should avoid as many dependencies as possible to recreate user environment

* Main BiocSwirl repo only 
* Installs ALL courses on all operating systems and recent R versions 
* Tries to load each course appropriately 
* Verify R package integrity
* File Directory check for install location
* Attempts to install and uninstall course (checks for clean uninstall) 
* Logs install errors 
* Scheduled cron job (Once weekly) 
	
Requirements: Devtools, R matrix, OS matrix, logging 

### course-checks.yaml
Checks for the integrity of the swirl course during active development, should use as many dependencies as required to recreate dev environment

* Used on all individual course repos 
* load in course locally using swirl 
* scan for large files
* load dependencies 
* tests lessons using Testthat, r cmd check (possible to log stalling for when data gets stuck on download?) 
* Check file structure integrity for swirl lessons/courses, also check for duplicates 
* uses yaml linter for lesson.yaml
* uses R linter
	
Requirements: R linter, Yaml linter, Bioconductor, swirl, swirlify, bash utils, etc.


