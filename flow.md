# Work-flow

## Repositories
| Type | Description |
| ---| ---|
| NETN FOM  | Main Repository for the entire FOM including all related FOM Modules.|
| NETN-* | Repository for a specific FOM Module.|

## Branches

| Type | Description |
| ---| ---|
| Master Branch |The latest officially released version. |
| Develop Branch |The lastest development version with reviewed changes. |
| Maintenance Branches |Opened to maintain specific baseline or older version. |
| Release Branches |Temporary, used to prepare for a release.|
| Edit Branches |Temporary, used to develop proposed updates and closed after pull-request review and approval.|

## Making changes
All changes should be initiated by creating a GitHub Issue. Issues may also be created for the purpose of discussing possible future changes without suggesting a concrete plan of action.

The develop branch should at all times contain only changes that have been reviewed and approved by at least one party that was not directly involved in making them. To this end, we adapt a workflow involving edit branches, pull requests and pull request reviews.

The workflow is closely based the commonly used “Gitflow” workflow, originally presented [here](https://nvie.com/posts/a-successful-git-branching-model/).

### Creating a Pull Request
When ready to make a change, create a branch based on the develop branch. Name the branch on the form “edit/...”, and include the number of the issue where the changes are discussed in the branch name.

An edit branch may refer to more than one Issue, in which case its name should preferably include the numbers of all of them. This is not mandatory, however.

Make the changes on the branch, and push the branch to GitHub.

When you think the changes are ready, create a Pull Request, pointing it to the develop branch. Add reviewers to the PR as appropriate. Link the PR to each Issue it addresses, if it has not been automatically linked already.

### Reviewing a Pull Request
When reviewing a pull request, comment on individual changes in the “Files changed” view. Then click the button marked “Review changes”, add any additional comments not related to individual changes, select Comment, Approve or Request changes, and submit the review.

### Merging a Pull Request
Any edits that happen as a result of discussions and reviews of the PR should be committed and pushed to the same edit branch, which will automatically update the Pull Request.

The PR must be reviewed and approved by at least one party from a different organization than the creator of the PR before it can be merged to the develop branch.

If discussions of a PR raises questions that have not been addressed in a GitHub Issue, they should be added to a new or existing Issue and agreed upon before the PR is approved or merged.

## Releases
### Making a release of a single module
1. Create a release branch based on the develop branch, with a name on the form “release/...”, including the intended name of the release in the branch name.
2. Make any final, pre-RC changes on the release branch, such as setting correct meta data, updating the changelog or adding documentation. Remember this includes setting the version name to the upcoming release or release candidate version wherever it is mention inside the repository, such as the FOM module identification table.
3. Create a tag at the commit intended as the release candidate. Name it <version-name>-rcN, where N is the sequential number of the RC for this version, starting at 1.
4. Optional: Make a release.
5. Perform review activities.

If changes are necessary before a full release:

* Continue from step 2, making any necessary changes

If, after step 5, the RC is to be promoted to a full release:

6. Create a tag with the same name as the version to be released.
7. Make a release.
8. Merge the release branch into the develop branch and the master branch, then delete the release branch.

### Making a release of the entire NETN FOM
A release of the NETN FOM as a whole must include specific, released versions of every individual FOM module that makes up the FOM.

1. Create a release branch based on the develop branch, with a name on the form “release/...”, including the intended name of the release in the branch name.
2. On this branch, replace all individual FOM module files whose versions will change in this release with the new released version. FOM module versions that are RC's are allowed.
3. Make any final, pre-RC changes on the release branch, such as setting correct meta data, updating the changelog or adding documentation. Remember this includes setting the version name to the upcoming release or release candidate version wherever it is mention inside the repository.
4. Create a tag at the commit intended as the release candidate. Name it <version-name>-rcN, where N is the sequential number of the RC for this version, starting at 1.
5. Optional: Make a release.
6. Perform review activities.

If changes are necessary before a full release:

* Continue from step 2, making any necessary changes to individual FOM modules, making new releases of those FOM modules, and replacing their files with their new versions on the release branch.

If, after step 6, the RC is to be promoted to a full release:

7. Make final releases of any RC versions of individual FOM modules included in this RC. The final FOM module releases must be identical to their respective RC versions in all but administrative details. Replace the RC version files with the final release version files on the release branch.
8. Create a tag with the same name as the version to be released.
9. Make a release.
10. Merge the release branch into the develop branch and the master branch, then delete the release branch.

## Maintenance branches
For practical purposes, it is sometimes necessary to maintain older versions of individual FOM modules, or the FOM as a whole. In order to do maintenance work on an old version, create a new branch based on the tag for the released version in question. Name it <base-version-name>-maintenance. Maintenance branches are permanent, and will never be deleted. Maintenance branches may be merged to the develop branch if this is desired, but the opposite will never happen. Releases may be made on a maintenance branch according to the regular release procedures, as if the maintenance branch was the develop branch, except there is no equivalent to the master branch. Names of maintenance releases must never clash with names of regular releases.