# Collaboration Process

<!-- vim-markdown-toc GFM -->

* [Overview](#overview)
    * [Workflow](#workflow)
        * [CODE](#code)
        * [REVIEW](#review)
        * [MERGE](#merge)
* [Addendum](#addendum)
    * [Notes](#notes)
    * [FAQ](#faq)
    * [References](#references)

<!-- vim-markdown-toc -->


# Overview
![Git Workflow](/git_workflow.png)

## Workflow
1. Create a branch from `main` on the ACCESS-CI repository
    * Branch naming convention: {TICKET}/{USER}/{short-description}
      * Example: `CTT-222/blau/fix_set_upstream`
    * `git checkout -b {BRANCH} main`
    * `git push -u origin {BRANCH}`
      * where `{BRANCH}` is the actual name of your branch, without the curly braces

### CODE
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

### REVIEW
1. Pull Request
   * Github.com > Project site > Pull requests > New pull request
   * *base: main* :arrow_left: *compare:{BRANCH}* > Create pull request
     * If github reports merge conflicts, resolve those before submitting the PR
     * Title: (a short summary of the primary change or enhancement)
     * Description: (list of the major updates, copy of CHANGELOG is fine here)
       * (See also: [How to manage a CHANGELOG](/changelogging.md))
     * Assignee: (who will merge this to main, usually the developer themselves)
     * Reviewers: (who will review and approve this PR)
       * (at least one, more is better)
       * Sugestions:
         * component owner
         * component owner backup
         * peer developers
     * Create pull request
1. Review
   * Participate in the review commentary
   * For any issues, repeat the EDIT > COMMIT > PUSH > TEST cycle until all review issues are complete and fully tested

### MERGE
Two options here:
* Option 1: use "Squash and merge" from the web interface
* Option 2: Rebase and force push to main from a local git client

For Option 1,
![Squash and merge](/squash-and-merge.png "Squash and merge via github web
interface")

For Option 2, follow the commands below ...
1. Rebase
   * `git checkout main`
   * `git pull`
   * `git checkout {BRANCH}`
   * `git rebase -i main`
     * "pick" the 1st commit
     * "squash" all the others
     * When prompted to edit the commit message, add a new line at the top with
       the format `{TICKET}: {short description}`
       * Example: `CTT-222: fix the git push --set-upstream cmd`
   * `git push -f origin {BRANCH}` :warning: (use with caution, always type out branch name and review command before hitting Enter)
   * test again
1. Merge to main
   * `git checkout main`
   * `git pull`
   * `git merge {BRANCH}`
     * (Note: Repo settings will only allow a fast forward merge)
   * `git tag {tagname}`
     * where {tagname} follows the tag naming convention for the project you are working on
       (most common is [Semantic Versioning](https://semver.org/))
     * add tags when appropriate (ie: not doing a release, just adding a tag)
     * when making a release, add the tag as part of the release creation
       process

   * `git push --tags`
1. Delete your branch
   * `git branch -d {BRANCH}`
   * `git push origin :{BRANCH}`

# Addendum

## Notes
* The commands presented here are for working from the cmdline. If working in
  a different tool, make the appropriate adjustments.
* Any text inside curly braces (`{` and `}`) denotes a placeholder. Replace
  them (the entire placeholder including the curly braces) with the appropriate
  value.
* The "rebase" option may cause problems if:
  * The repo has a workflow that publishes development versions with "guessed"
    version strings that are not unique (ie: test.pypi.org)
  * For these repos, the "Squash and merge" option may be preferred.

## FAQ
See: [Frequently Asked Questions](/faq.md)

## References
* [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow)
* [GitHub flow explained](https://scottchacon.com/2011/08/31/github-flow/)
