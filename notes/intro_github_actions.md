# Introduction to Github Actions

Author: Almas K

Date: June 5, 2021

### What is continuous integration/continuous development (CI/CD) ?

- Continuous integration = process of frequently committing code to shared repo to detect errors sooner

[Redhat-Ci/CD](https://www.redhat.com/en/topics/devops/what-is-ci-cd)

- a method of development that involves automation at different stages of the development of an app or lesson in our case 

- main concepts include "continuous integration, continuous delivery, and continuous deployment." 

- " "CI" in CI/CD always refers to continuous integration, which is an automation process for developers. Successful CI means new code changes to an app are regularly built, tested, and merged to a shared repository. " 

![image](https://www.redhat.com/cms/managed-files/ci-cd-flow-mobile_0.png)

[CI/CD Smashing magazine](https://www.smashingmagazine.com/2020/10/handling-continuous-integration-delivery-github-actions/)

- A "trigger" leads to CI/CD workflow being executed 

- in our case a trigger is a git commit

### Github Actions and CI/CD

[CI Quickstart Github](https://docs.github.com/en/actions/quickstart)

[About CI-Github](https://docs.github.com/en/actions/guides/about-continuous-integration)

- "GitHub Actions is an API for cause and effect on GitHub: orchestrate any workflow, based on any event, while GitHub manages the execution, provides rich feedback, and secures every step along the way." -[Github blog release note](https://github.blog/2019-08-08-github-actions-now-supports-ci-cd/)

- A user (us) configures a workflow to run when a certain Github event occurs (the "trigger"), like when new code is pushed, and can set schedule on these events 

- these workflows include a series of commands like tests after the event 

![Github actions img](https://docs.github.com/assets/images/help/images/overview-actions-simple.png)

#### Basics of how it works:

[Learn Github actions](https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions?learn=getting_started)

- you need a yml file in the .github/workflows directory
    - this is the workflow file 
    - workflows = made up of 1 or more jobs that are either scheduled/triggered
    - can be used to "build, test, package, release, or deploy a project on GitHub."
- jobs= set of steps that are executed on the same runner
    - multiple jobs on 1 workflow
    - usually run parallel, can be configured to run sequentially     

-![parts of github actions](https://docs.github.com/assets/images/help/images/overview-actions-design.png)

- steps= individual commands/tasks for a job

  - either an action or a shell command

  - each step runs on the same runner allowing jobs to share data

- Actions: 

  - standalone commands combined into steps to make a job
  - smallest building blocks of a workflow 
  - to use it must include it into a step

- Runners

  - server with the Github actions runner application installed 
  - usually hosted by github, can host own
  - runs each job on a fresh virtual environment, reports the progress, logs and other results on Github
  - based on Ubuntu (Linux), Windows, macOS

### Example Workflow File

Store workflow files in a hidden 

```yml
name: learn-github-actions #name of the workflow that appears in Actions tab
on: [push] # event that leads to a trigger
jobs: # the start of a all the jobs grouped together 
  check-bats-version: # name of job 
    runs-on: ubuntu-latest # type of runner, fresh Ubuntu linux runner
    steps: # steps in the check-bats version job 
      - uses: actions/checkout@v2 # retrieve community action named checkout@v2
      - uses: actions/setup-node@v1 # install the node package and use npm command
      - run: npm install -g bats # use np to install bats 
      - run: bats -v # run the bats command with parameter that outputs software version 
```

the `on: [push]`means that job runs every time a push event occurs so every time a change is pushed 

![Workflow overview](https://docs.github.com/assets/images/help/images/overview-actions-event.png)



### Additional Features: Variables and Scripts

https://docs.github.com/en/actions/learn-github-actions/essential-features-of-github-actions



#### Variables

- You can set custom variables for each workflow run by setting these in YAML workflow file (see example from github docs below)

````yml
jobs:
  example-job:
      steps:
        - name: Connect to PostgreSQL # name of step (optional)
          run: node client.js
          env:
            POSTGRES_HOST: postgres
            POSTGRES_PORT: 5432
````

 The `POSTGRES_HOST` and `POSTGRES_PORT` are custom variables 

#### Scripts

- To run scripts and shell commands use the `run` keyword  which 
