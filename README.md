# ttn-frontend
Example repo of the imaginary app "Toad Town News" 

As of 1-20-26: This repo's true purpose is to showcase various ways a caller workflow and a reusable workflow are related. See the **__Workflows__** section for more details regarding these relationships. 

# Workflows

This section describes the workflows used in this repository. Note several of these are caller workflows; the brunt of business logic may be in the reusable workflow called. These reusable workflows are located in the org-mushroom-kingdom/ttn-workflows repo TO DO LINK unless otherwise noted.

## sc-changelog-check-exists-and-naming-caller.yml (Frontend Changelog Check (Exists/Naming))

Name: Frontend Changelog Check (Exists/Naming)
Filename: `sc-changelog-check-exists-and-naming-caller.yml`
Reusable Workflow Filename: `org-mushroom-kingdom/ttn-workflows/.github/workflows/changelog-quality-checks.yml`

## Scenario

This is an example of how a reusable workflow (XXXX.yml) can be called upon from a caller workflow, with the specific caveat that the reusable workflow needs to check out its own repository in order to run a script to perform the brunt of its logic. This requires passing a token present in the caller workflow repository to the reusable workflow repository.

Refer to the Medium Article [Github Actions: Checking Out And Utilizing a Reusable Workflow's Repository](https://pages.github.com/) for more details on this scenario as well as the ttn-workflows README TODO LINK
 
### Trigger

The `sc-changelog-check-exists-and-naming-caller.yml` caller workflow will activate when a pull request is opened, synchronized, or reopened IF the pull request meets the following criteria:
-  The source branch is a release branch (begins with the string 'release') 
-  The target branch is main 

## Get Article Titles

Name: TODO
Filename: TODO
Reusable Workflow: TODO

## Scenario

This is an example of how a reusable workflow (`get-article-titles.yml`) can be called upon from a caller workflow, with the specific caveat that the reusable workflow needs to check out its own repository in order to read a file in that repository. It's very similar to **__Frontend Changelog Check__**'s scenario, but this time instead of using a PAT and passing that to the reusable workflow, we instead are going to use a Github App to create an installation access token. This time, the Github App must be installed on the reusable workflow's repository. 