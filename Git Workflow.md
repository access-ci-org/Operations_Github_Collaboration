
# Collaboration Process
## Overview
![Git
Workflow](https://github.com/access-ci-org/Operations_Github_Collaboration/blob/CTT-222/aloftus/PR-workflow/Git%20Workflow.png)
## Workflow
1. Create a branch
    * Naming convention: ticket/username/short-description
    * `git branch {your/branch/name}`
    * `git commit -u origin {your/branch/name}`
      * where `{your/banch/name}` is the actual name of your branch, without the curly braces
#### CODE
1. Edit
   * `vim file1`
   * `vim file2`
1. Commit
   * `git status`
   * `git add file1 file2`
   * `git commit -m "updated file1 & file2"`
1. Push
   * `git push`
1. Test
   * Test according to the procedures specific to the project you are working on
1. Repeat EDIT > COMMIT > PUSH > TEST cycle until changes are complete and fully tested
#### REVIEW
1. Pull Request
   * Github.com > Project site > Pull requests > New pull request
   * *base: main* :arrow_left: *compare:{your/branch/name}* > Create pull request
     * If github reports merge conflicts, resolve those before submitting the PR
     * Add a title (a short summary of the primary change or enhancement)
     * Add a description (list of the major updates, copy of changelog is fine here)
     * Assignee (who will merge this to main)
     * Reviewers (at least one, more is better, who will review and approve this PR)
     * Create pull request
1. Review
   * Participate in the review commentary
   * For any issues, repeat the EDIT > COMMIT > PUSH > TEST cycle until all review issues are complete and fully tested
#### MERGE
1. Rebase
   * `git checkout main`
   * `git pull`
   * `git checkout {your/branch/name}`
   * `git rebase -i main`
     * "pick" the 1st commit
     * "squash" all the others
   * `git push -f origin {your/branch/name}`
   * test again
1. Merge to main
   * `git checkout main`
   * `git pull`
   * `git merge {your/branch/name}`
     * (Note: Repo settings will only allow a fast forward merge)
   * `git tag {tagname}`
     * where {tagname} follows the tag naming convention for the project you are working on
   * `git push --tags`
1. Delete your branch
   * `git branch -d {your/branch/name}`
   * `git push origin :{your/branch/name}`

# References
* [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow)
* [GitHub flow explained](https://scottchacon.com/2011/08/31/github-flow/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQxNTMyMzUxMyw3OTYzODQ2OTEsLTE1Mz
kyNTA1NDEsMTMwNzM0NDU1NiwtMTQxMTA4MjkyOCwtNTUyNDg1
NDUzLDM4OTgzNjM1MSwyMDM4ODQ0MjIwLC05NzczMjIyMDMsLT
E2MzUwNjgwMTcsMjkxNDI3MDcxLDU0MzExNjc1NSwtMzc5NTQz
MTk0LC0yMDg4NzQ2NjEyLC0zMzI0NTUzNjNdfQ==
-->
