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

In this scenario, a caller workflow `ttn-frontend` (and `ttn-backend`) rely on the reusable workflow `changelog-quality-checks.yml` which checks for a changelog file (referred to hereon as a CHANGELOG file) when a pull request is made from a release branch to the main branch (See **__Triggers** for more details). The logic surrounding the CHANGELOG file is strict and the file must meet certain criteria before merging into the preprod or main branch is allowed (see **__Business Logic__** for details).

This is an example of how a reusable workflow (`changelog-quality-checks.yml`) can be called upon from a caller workflow, with the specific caveat that the reusable workflow needs to check out its own repository in order to run a script to perform the brunt of its logic. This requires passing a token present in the caller workflow repository to the reusable workflow repository.

Refer to the Medium Article [Github Actions: Checking Out And Utilizing a Reusable Workflow's Repository](https://blog.devops.dev/github-actions-checking-out-and-utilizing-a-reusable-workflows-repository-992adbe7b3ae) for more details on this scenario as well as the [ttn-workflows README](https://github.com/org-mushroom-kingdom/ttn-workflows/blob/main/README.md)
 
### Trigger

The `sc-changelog-check-exists-and-naming-caller.yml` caller workflow will activate when a pull request is opened, synchronized, or reopened IF the pull request meets the following criteria:
-  The source branch is a release branch (begins with the string 'release') 
-  The target branch is prepord main 

### Business Logic

#### **Workflow Logic**

The `sc-changelog-check-exists-and-naming-caller.yml` workflow consists of one job `get-article-titles-caller` which is simply a call to the reusable workflow `changelog-quality-checks.yml` in ttn-workflows. See the documentation about the reusable workflow in the [ttn-workflows README](https://github.com/org-mushroom-kingdom/ttn-workflows/blob/main/README.md). 

A token with `repo` permissions is passed which allows the reusable workflow to checkout its own repo. 

## Get Article Titles

Name: TODO
Filename: TODO
Reusable Workflow: TODO

## Scenario

This is an example of how a reusable workflow (`get-article-titles.yml`) can be called upon from a caller workflow, with the specific caveat that the reusable workflow needs to check out its own repository in order to read a file in that repository. It's very similar to **__Frontend Changelog Check__**'s scenario, but this time instead of using a PAT and passing that to the reusable workflow, we instead are going to use a Github App to create an installation access token. This time, the Github App must be installed on the reusable workflow's repository. 