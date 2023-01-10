# test-github-ui-merging

This repository demonstrates the use of the following GitHub repository
configuration to ensure that signed commits retain their original signing
metadata instead of being overwritten by GitHub's signing key:

- Only enable **Allow rebase merging**
  (_Add all commits from the head branch onto the base branch individually._).
- Add the branch protection rules:
    - **Require linear history**: _Prevent merge commits from being pushed to matching branches._
    - **Require branches to be up to date before merging**: (_This ensures pull requests targeting a matching branch have been tested with the latest code. This setting will not take effect unless at least one status check is enabled._
    - **Require signed commits**: _Commits pushed to matching branches must have verified signatures._

---

This repository has the following PRs to demonstrate the configuration:

- `feat/1-merged-pr`: A PR that has been merged. Note that the commit signing metadata has been preserved (hopefully :pray:).
- `feat/2-mergeable-pr`: A PR that is allowed to be merged because it meets the above criteria.
- `feat/3-unmergeable-pr-behind`: A PR that is behind the `main` branch and requires updating via `git rebase`.
- `feat/4-unmergeable-pr-merge-commits`: A PR that is up to date with the `main` branch but is not linear because it has merge commits.
