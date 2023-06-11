# Branch Organization

## Git Flow suggests a standard branch organization in a repository:

* main: The main branch contains stable, production-ready code. All merges into main should be thoroughly tested and
  verified.
* develop: The develop branch is the general development branch. It contains the latest changes and new features that
  are
  not yet ready for production.
* feature: For each new feature or task, a separate branch is created branching off from develop. After completing the
  work, the feature branch is merged into develop.
* release: Release branches are used for preparing new releases of the project. They are created before publishing a new
  version and can be fixed or enhanced before final merging into main and develop.
* hotfix: Hotfix branches are used for quickly fixing issues in the production environment. They branch off from main,
  fix
  the problem, and then merge back into both main and develop.