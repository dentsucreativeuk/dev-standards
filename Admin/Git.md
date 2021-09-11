# Git Source Control
> Part of [Administration](/Admin/Index.md)

The below guidance details our overall process for dealing with version control in a consistent, predictable manner which works for all developers. There may be small deviations amongst repositories, but regardless of this, there are four 🌟 golden rules 🌟 which should always be followed:

 1. 🌟 **Only commit into a feature branch** (ideally with a job number and descriptive name).
 2. 🌟 **Never merge from release branches into any other branch** (for example, `release/development`, `release/production` etc).
 3. 🌟 **Keep your branches focused**—don't merge in other branches, work on unrelated issues (use a new branch), or rebase on release branches. Trust in git, and keep your head.
 4. 🌟 **If in doubt, ask.** Don't plough on regardless—it's almost always better to let someone else know if a situation is causing concern.

### Ultimately, following this guidance—whatever the work, and however quickly you need to do the job—will mean more time for everyone to do the great work they want.

## Which projects does this apply to?
In short, any new project that is not specifically following another standard **must** follow these guidelines.

## Branch types

### Main branch
The main branch (usually called `main` or `master` should be used as the starting point for any new work. It contains all work that has reached production release and has proven to be working.

### Release branches
The following branches are release branches; used for deployment to external environments:

 - `release/development`
 - `release/staging`
 - `release/production`

Used when deploying feature branches, Commits **must never** be made directly to the release branches.

The release branches **must** only contain commits that have been merged in from feature branches.

## Feature branches
These are the branches in which work commits can be made. There are two main types of feature branch:

 1. A **work** branch, prefixed by a job number.
 2. A **hotfix** branch, prefixed with `hotfix/`.

A hotfix branch can be used for short term and emergency fixes. For all other types of work, use a work branch.

An example repository during work in progress might look like this:

 - `main`
 - `WJOBB0001/new-search`
 - `WJOBB0001/featured-cta-panels`
 - `WJOBB0003/related-services`
 - `hotfix/memcache-issue`
 - `release/staging`
 - `release/development`
 - `release/production`

With `WJOBB0001/new-search`, `WJOBB0001/featured-cta-panels` and `WJOBB0003/related-services` being projects in progress, which may have been merged into `release/development` already, and a single `hotfix/memcache-issue` branch which contains commits resolving a side-effect of a past deployment.

## Working in the repository
An example workflow for a simple change could therefore run as follows:

 1. A repository is cloned.
 2. The branch `main` is checked out, fetched and pulled.
 3. A new branch named `WJOBB0001/new-search` is created using the tip of `main` as a base.
 4. Work is then done within `WJOBB0001/new-search` and 10 commits are made. The work is tested using a local web server.
 5. Once the work is functionally complete, it is merged into `release/development` and deployed to the development environment.
 6. After the work is approved, the branch `WJOBB0001/new-search` is then merged into `release/staging` or `release/production`, depending on the number of environments.
 7. Only when the work is live and complete would the `WJOBB0001/new-search` branch be merged into `main` and then **deleted** from both the local and any remote repositories it has been pushed to.

### Deploying & transpiling front end code
Until we have fully developed CI solutions, deploying is still performed directly by the developer, usually using a tool such as Capistrano. However, it is worth considering the following aspects:

 - Check the correct release branch is checked out before deploying as front end assets e.g: running Webpack, gulp, SVG sprites etc should be created from the correct source code for deployment.
 - Ensure the correct work branch is checked out after a deployment, so work continues within that branch.

### Further development needed?
If more work is required after step 5 or 6, then the original branch `WJOBB0001/new-search` should be checked out and further commits made. It can then be re-merged into the appropriate release branches to repeat steps 5 onwards.

### Rolling back
If the work is cancelled then the release branches must be cleaned. Either by reverting the merge commits, or if not yet pushed, resetting the head to the point before the merge commits.

### Avoiding conflicts
Conflicts are an inevitable part of Git management, and while never completely avoidable, there are steps we can take to reduce their impact and frequency of occurence:

 1. **Keep commits small and simple.** The old adage "push once, commit often" still applies, and for good reason. Smaller commits mean less work to reason about when merging, and make commit messages easier to write.
 2. **Avoid working outside your remit.** When working within files, avoid changing code that isn't directly related to the work. This ensures commit patches are easy to digest as well as the reliability of potential merges.

## Commit messages
Commit messages **must** be concise, clear and broadly describe the work done in that commit. They **should** be written in the imperative present tense, and the first line of a commit **should** be within 50 characters in length. If a commit message needs to be described more thoroughly use the [_Subject and Message_](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/git-commit.html#_discussion) syntax: where the first line is taken as the subject, then a line return, then the body of the message.

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
Merges **must** be performed using the `--no-ff` flag or an equivalent "Always create merge commits" option. This will help avoid the loss of topological information about branches that have since been removed.

## Bitbucket pull requests
On a protected Bitbucket repository, the **release** branches may not be directly writeable. In this case, merges can be made with a pull request.

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

## FAQ

### Why only branch from `main`?

Consider this scenario:

1. **developer A** branches from `main` into branch `XX001/dev-1-work` and produces a number of commits.
2. **developer A** then needs the work reviewed. This branch is then merged into `release/development` and the work in that branch is deployed.
3. Some days later, **developer B** branches from `release/development` and creates `XX002/dev-2-work`. Commits are made, and then **developer B** also needs to deploy. The branch is then merged back into `release/development` and reviewed.
4. **developer A's** work is delayed by three weeks. The client cannot put it live without sign off from another party.
5. **developer B's** work is approved! The work is merged from `XX002/dev-2-work` into `release/production` and deployed.
6. The QA team notice that work done by **developer A** has been also put live, as it was within the `release/development` branch at the time **developer B** created their branch.
7. The client calls, absolutely livid that the change has been put live, and the dev team have to scramble to figure out what went wrong.

This is a rather extreme example, but not without precedent. The important thing to remember is that `main` is the only branch which contains work which is both complete and live, which is what will form the basis of all further work.

### Why not use `release/production` instead of `main` as the root branch?

The `release/production` branch is a release branch, which means it can contain the sum of many other branches not yet approved to be merged into `main`. Using `main` as the root branch for all new work ensure that only live, approved and fully tested work forms the basis of new commits.

### What is the importance of "merge commits"?

When merging a branch into another, Git has a very useful feature to keep the branch topology tidy, called "fast forwards". If it determines the new commits are chronologically in advance of the tip of your release branch, it will simply "fast forward" the release to the tip of the new branch during a commit. This produces a nice clean history, especially when viewing in graph modes. Unfortunately, this has the added side effect of essentially wiping out the historical information of where a branch was created, which commits were made within it, and then when it was merged.

The benefit to a merge commit, is that despite its tendency to produce more complex topology graphs, the history is retained and makes understanding the work which went into an old (often deleted) branch much easier.
