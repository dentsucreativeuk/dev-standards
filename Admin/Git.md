# Git standards
The following standards dictate the minimum level requirements for any work undertaken in a Whitespace project. These standards should be considered in addition to the known best practices for git usage and do not replace them unless explicitly overriden.

There are four main aspects when working with Git:

 - Branching
 - Comitting
 - Merging
 - Pull requests
 - Deployment

## Branching & Merging
The guidelines in footnote[1] **should** be followed in most cases, and **must** be followed for versioned software.

Every git repository should at the very least contain a `master` branch. The `HEAD` of which **must** contain code that is considered ready for production targets.

### Types of branches
There are two main "types" of branch within our working guidelines. Target branches are created as merge targets, with no commits made directly to them. Working branches are created to contain individual commits.

The following standard branch names are used:

 * `master` - A target branch containing the current production code at its `HEAD`.
 * `develop` - A target branch which should contain code syncronised with the main development/UAT environment at its `HEAD`.
 * `feature/[name]` - Working branches containing single project work. There may be many of these with different `description` values at once. See example below.
 * `try/[name]` - Working branches containing experimental project work.
 * `release/v[version]` - An additional target branch for pre-releases of versioned projects.
 * `hotfix-[name]` - Working branches used when a quick fix is required to a project that is not necessarily part of a job.

In the case that a job code is being used, a short description of the work after a forward slash **must** also be used, e.g:

```
feature/XX0001/minor-map-amends
feature/XX0001/optimising-maps
feature/AC0023/leaflets
try/XX0001/double-columns
```

In the case of all projects, Work **should not** take place directly in the target branches like `develop` or `master`.

## Committing
Commit messages **must** be concise, clear and broadly describe the work done in that commit. They **should** be written in the imperative present tense, and the first line of a commit **should** be within 50 characters in length.

If a commit cannot be described in one subject or phrase, it **must** be split into smaller, more detailed commits.

Examples:

```
// Valid commits:
"Fix AJAX run-time issue for unauthorised users"
"Add more padding around the layout boxes"
"Alter header height to fit new navigation"

// Invalid commits:
"WIP" // Non descriptive
"Stuff" // Non descriptive
"Altered header height" // (Past tense)
"Amend all JS to use CommonJS includes as this was never going to be reliant on any sort of transpiling process so the ES6 imports are all breaking when run via node" // Too long (use Subject and Message form).
```

### Comitting in Github
If a commit is occuring on a Github repository and it fixes or relates to a ticketed issue, the issue number with a preceeding hash **may** be referred to in the commit message. E.g:

```
"Add blue buttons to CSS (fixes #2432)"
```

This will automatically relate the commit to the issue in both directions and make issue tracking a lot easier.

## Merging
Merges **should** be performed using the `--no-ff` flag or an equivalent "Create merge commit" option. This will help avoid the loss of historical information about branches that have since been removed as well as preserve the integrity of commits which were made within the branch itself.

When a merge is complete and any conflicts are resolved, the merged branch **must** then be deleted unless it is a target branch, (i.e. `master` or `develop`).

## Bitbucket pull requests
On a protected Bitbucket repository, the `master` or `develop` branches may not be directly writeable. In this case, merges can be made with a rull request.

Pull requests are usually handled by a single repository or project leader, who is responsible for reviewing and merging branches. It is then the responsibility of either the project lead or developer to deploy the resulting code. This decision is made during the pull request.

### Creating pull requests
To create a pull request, three things are required:

 1. A subject (usually the broad name of the work done).
 2. An overall description of the work.
 3. The name of a reveiwer who can approve the request.

Once this information is available, a pull request can be made using the BitBucket website. See "Pull requests" within the repository navigation.

**Note:** Throughout the lifetime of a pull request, there may be comments requesting clarification or amendments to the work. This may result in further work required. **When commits are created on the branch being merged, the pull request will be automatically updated**.

### Approving
**Certain repositories require at least one approval before a PR can be merged**. If you are responsible for approvals, remember to review and approve or comment within a timely manner, explaining what is required should the approval be declined.

### Merging
**Once the PR has been approved and all checks passed, it can be merged**. This will be done by the reviewer or project lead.

## Deployments
There are two deployment methods used at Whitespace. The difference being when the project is versioned or not.

### Within non-versioned projects
In a non-versioned project, the `develop` branch is used for deploying to the development environment, and `master` is used for deploying to the production and staging environments.

#### Example workflow
An example workflow for producing a new feature, releasing it and cleaning up within a **non-versioned project** would be as follows:

 1. A branch is created from `develop` called `feature/my-great-feature`. It receives 6 commits until the work is completed.
 2. The work is then merged back into `develop` and after testing and deployment to the development environment, the `feature/my-great-feature` branch is removed.
 3. The `develop` branch is then merged into `master` and deployed subsequently to the staging environment. If this works, it is then deployed to the production environment.

### Within versioned projects
Non-development releases within versioned projects are typically done via tags. A tag **must** be created within the `master` branch, and this tag would be deployed to the corresponding deployment stage.

Tags should be created at every release. The format for tags **must** follow `v#-#-#` Where the numbering uses the Semantic versioning system[2].

This is enforced for Staging and Production environments.

#### Example workflow
An example workflow for producing a new feature, releasing it and cleaning up within a **versioned project** would be as follows:

 1. A branch is created from `develop` called `feature/my-great-feature`. It receives 10 commits until the work is completed.
 2. The work is then merged back into `develop` and after testing and deployment to the development environment, the `feature/my-great-feature` branch is removed.
 3. A `release/v1.4.0` branch is made from the tip of `develop` and then deployed to a staging environment.
 4. Once tested and known to be working, the `release/v1.4.0` branch is merged into master and deployed into production.

 * [1] http://nvie.com/posts/a-successful-git-branching-model/
 * [2] http://semver.org
