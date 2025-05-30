# (How-To) Manage CHANGELOG

## What is changelog?
The file `CHANGELOG` provides a summary of significant changes, features, and
bug fixes for each version of the contents in a repo.  It usually lives at the top level of the git repo.

## Format
File format is plain text.
Each entry should include:
* Version
* Date
* Who did the work
* Itemized list of changes to any of the following:
  * Features / Enhancements
  * Functionality
  * Bugfixes
* Jira issue numbers (where applicable)

## Example

```
v3.49.0 2025-01-27 JP
  - Enhance cider/v1/info_resourceid/ to return node_count (CTT-419)
  - Enhance cider/v1/access-active-groups/ to return resource summary (CTT-420)
  - Fix docker requirements.txt django-bootstrap5 syntax

v3.36.0 2024-10-29 Eric, JP
  - CTT-237 Change path converter of str to path for glue2 and resource_v4
    software by ID routes
  - Fix /wh2/glue2/v1/software_full/ bug that wasn't returning info_sideid

v3.35.0 2024-10-17 JP, Andy
  - Change Field to Fields, add Fields of Science to main page
  - CTT-144 add info_resourceid
```
(from https://github.com/access-ci-org/Operations_Warehouse_Django)
