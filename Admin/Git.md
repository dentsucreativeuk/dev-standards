# Git standards
The following standards dictate the minimum level requirements for any work undertaken in a Whitespace project. These standards should be considered in addition to the known best practices for git usage and do not replace them unless explicitly overriden.

## Commit messages

Commit messages **must** be concise, clear and describe broadly the work done in that commit. They **must** be written in the imperative present tense, and the first line of a commit **should** be within 50 characters in length.

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
If a commit is occuring on a Github repository and it fixes or relates to a ticketed issue, the issue number with a preceeding hash **must** be referred to in the commit message. E.g:

```
"Add blue buttons to CSS (fixes #2432)"
```

This will automatically relate the commit to the issue in both directions and make issue tracking a lot easier.

## Branching

The guidelines in footnote[1] **should** be followed in most cases.

Every git repository should at the very least contain a `master` branch. The `HEAD` of which **must** contain code that is considered ready for production targets.

There are a number of acceptable generic branches:

 * `develop` - To be used when a new project is being generally worked on and can be comitted to directly.
 * `hotfix[-*]` - To be used when a quick fix is required to a project that is not necessarily part of a job.

In all other cases, the job number plus a short description of the work after a forward slash **must** be used, e.g:

```
XX0001/minor-map-amends
AC0023/leaflets
```

### When using versioned projects

In versioned projects such as applications or libraries, additional branches may also be used[1]:

 * `release[-v#-#-#]` - As a target for release-ready code which **must** only receive bug fixes as commits. These fixes can be merged back into `develop`.
 * `feature/feature-name` - For creating specific, stand-alone features of a project. **must** merge back into `develop` when completed.

In the case of versioned projects, Work **should not** take place directly in the `develop` branch but otherwise use a feature or `release` branch to instigate changes.

## Cleaning up and releasing
In addition to the extra branches, tags should be created at every release for versioned projects. The format for tags **must** follow `v#-#-#` Where the numbering uses the Semantic versioning system[2].

Once a feature or job based branch has been merged into `master` via `release` or `develop`, it **must** be deleted.

### When using Capistrano managed projects

Releases within Capistrano managed projects typically done via tags. A tag would be created off the master branch, and this tag would be deployed to the corresponding deployment stage.

This is enforced for Staging and Production environments. The schema for naming these tags is outlined below.

#### Staging

Releases tagged for staging should follow the following schema

`staging-[release-number]`

In order to create a tag, use the commands below. Also note the version number below is just an example, follow the numbering convention, i.e. if the current release is *staging-1.1.0* the next release your tag will be *staging-1.1.1*

`git tag staging-1.0.0`

`git push origin --tags`

#### Production

Releases tagged for production should follow the following schema

`production-[release-number]`

In order to create a tag, use the commands below. Also note the version number below is just an example, follow the numbering convention, i.e. if the current release is *production-1.1.0* the next release your tag will be *production-1.1.1*

`git tag production-1.0.0`

`git push origin --tags`

## Merging
Merges should always be performed using the `--no-ff` flag or the "Always generate merge commit" option. This option **must** be used to avoid the loss of historical information about branches that have since been removed as well as preserve the integrity of commits which were made within the branch itself.

When a merge is complete and any conflicts are resolved, the merged branch **must** then be deleted unless it is a permanent branch, (i.e. `master` or `develop`).

 * [1] http://nvie.com/posts/a-successful-git-branching-model/
 * [2] http://semver.org