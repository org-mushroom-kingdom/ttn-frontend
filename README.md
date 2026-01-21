# ttn-frontend
Example repo of the imaginary app "Toad Town News" 

As of 1-20-26: This repo's true purpose is to show how a reusable workflow (from ttn-workflows) can be called upon from a caller workflow (sc-changelog-check-exists-and-naming-caller.yml). It's part of a greater example of how to checkout the reusable workflow's repository to access a script it has needed for certain work. Refer to the Medium Article [Github Actions: Checking Out And Utilizing a Reusable Workflow's Repository](https://pages.github.com/).
 
The sc-changelog-check-exists-and-naming-caller.yml caller workflow will activate when a pull request is opened, synchronized, or reopened IF the pull request meets the following criteria:
-  The source branch is a release branch (begins with the string 'release') 
-  The target branch is main 

