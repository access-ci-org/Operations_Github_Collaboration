# Repository Naming Conventions
Guidelines for naming new repositories in the ACCESS-CI.org Operations team.

## Name
Follow common repo name patterns like:

Descriptive prefix that indicating purpose:
* `Operations_`
* `Operations_WebApp_`

Suffix indicating (limiting) the target deployment:
* `_Infrastructure`
* `_Django`

For examples, see also:
https://github.com/orgs/access-ci-org/repositories?q=Operations_

## Settings
* Restrict `main` branch to allow only Fast Forward merges
  * Settings > General > Pull Requests
    * Allow merge commits: No :x:
    * Allow squash merging: Yes :white_check_mark:
    * Allow rebase merging: No :x:
  * Settings > Rules > Rulesets
    * Name: "FF only"
    * Target branches: "default"
    * Rules:
      * Restrict deletions
      * Require linear history
      * Block force pushes
