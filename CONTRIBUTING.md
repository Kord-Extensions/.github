# Contributor Guidelines

Kord Extensions maintains a variety of projects, both intended for use by its community and
by the world at large. We believe that well-maintained code is key when it comes to running
a project properly - for that reason, please follow these points when contributing to our
repositories:

* **Follow our Code of Conduct:** All contributions must follow our Code of Conduct. If
  you haven't read it yet, we would ask that you 
  [go ahead and do that now](https://github.com/Kord-Extensions/.github/blob/master/CODE_OF_CONDUCT.md).

* **Don't fight the framework:** If a project is making use of a specific framework or
  toolset, then you are expected to make use of it. If you feel like there's a better
  option, *please open an issue instead of trying to contribute the necessary changes.*

  We've picked the tools we're using for a reason, and the project is probably too far ahead 
  to make a rewrite in another framework worthwhile. For that reason, it's important to open 
  an issue - otherwise, you may be working on code that ultimately never gets used.

* **Don't stand on people's toes:** If you'd like to tackle an issue, we'd love to have your
  help! That said, you need to ensure that issue isn't already being handled - check whether
  the issue is assigned to someone first. Once you've checked things out, leave a comment on
  the issue and we'll assign it to you if it's not already being worked on.

* **Open pull requests early:** Once an issue has been assigned to you, feel free to get 
  started! Fork the repository, then **create a new branch for your work** (this is important).
  Create your pull request as soon as you can, ideally after your first commit to the branch -
  and mark it as a draft. This gives us an easier way to keep track of things, and to offer 
  help if you need it.

* **Adhere to the prevailing style:** To keep things readable and maintainable, we enforce a
  set of style guidelines using a linter (in the case of Kotlin, this is a combination of
  Detekt and klint). Running a Gradle task in any of our projects should install a git hook
  that runs the linter when you create a commit, but you can always run it yourself as well.

  Code that does not successfully lint will fail to build, and your PR will not be merged 
  until the build passes. If git hooks don't work for your workflow, please ensure you
  always lint before you push!

* **Avoid feature creep:** When authoring a pull request, ensure that it addresses a 
  well-defined issue. Do not submit solutions for more than one problem in a single PR.
  Instead, create multiple branches and submit a separate PR for each one.

  If your pull request is blocking another pull request that you wish to work on, we
  recommend you hold back and wait for us to review and merge the current PR. While
  it is possible to work on both, it can be a heavier workload - especially if the
  blocking PR requires a lot of changes.

* **Avoid trivial contributions:** We will be unlikely to accept PRs that address extremely 
  small issues, such as a single-line comment or documentation edit, spelling corrections, 
  and so on. Instead, please open an issue or contact a staff member directly.

  We will accept PRs that address a large number of trivial changes, however.
