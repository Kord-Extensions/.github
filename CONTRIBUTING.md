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

# Code Style

As some contributors appear to be confused about the canonical code style used by Kord Extensions,
this attempts to clarify a few things.

## Whitespace

Kord Extensions uses **four-space-width tabs** for indentation for most file types. This means that users and
contributors may configure their editors to display indents in whatever way works best for them, and it may
also make it easier for visually-impaired users and contributors to browse the source code.

YAML (`.yml`) files use **two spaces** instead, as YAML files may not be tab-indented and are often deeply nested.

## Blank Lines

Some style conventions
(such as [the one used by kotlinx.coroutines](https://github.com/Kotlin/kotlinx.coroutines/blob/master/CONTRIBUTING.md))
disallow blank lines in function bodies.
At Kord Extensions, the goal is not to write golfed code - instead, code should be separated into logically defined
blocks, split with singular blank lines.

In general, this means grouping similar types of statements together, and separating them with blank lines.

### Data vs Logic

**Split variable definitions and functional expressions where possible and when logic allows.** For example:

```kt
// This is incorrect.

val hello = "hello"
val world = "world"
println("$hello, $world!")
val question = "What's up?"
println(question)

// Do this instead.

val hello = "hello"
val world = "world"
val question = "What's up?"

println("$hello, $world!")
println(question)
```

### Function vs Property/Variable

**Split function calls and property/variable access where possible and when logic allows.** For example:

```kt
// This is incorrect.

val x: SomeObj
x.doThing()
x.variable = 42
val something: x.getThing()
x.doOtherThing(something)
x.takeMap(
  mapOf("a" to "b"), 
  "c"
)

// Do this instead.

val x: SomeObj
val something: x.getThing()

x.doThing()
x.doOtherThing(something)

x.variable = 42

x.takeMap(
  mapOf("a" to "b"), 

  "c"
)
```

### Lines vs Blocks

**Split single-line expressions and blocks, and split separate blocks.** For example:

```kt
// This is incorrect.

val x: Something
x.doSomething {
  // ...
}
x.doThing()
x.doSomethingElse{
  // ...
}

// Do this instead.

val x: Something

x.doSomething {
  // ...
}

x.doThing()

x.doSomethingElse{
  // ...
}
```

### Long Wrapped Statements

**When dealing with statements wrapped within symbol characters (such as parentheses), don't let them get too long.**
Additionally, add commas to the end of lists, and follow the other rules. For example:

```kt
// This is incorrect.

private fun addGeneratedFiles(target: Project, extension: KordExExtension, kordVersion: Version?, kordExVersion: Version) {
  // ...

  doSomething(1, 2, "a", "b", listOf(null), true, null, false)
}

// Do this instead.

private fun addGeneratedFiles(
  target: Project,
  extension: KordExExtension,
  kordVersion: Version?,
  kordExVersion: Version,
) {
  // ...

  doSomething(
    1, 2, 
    "a", "b",

    listOf(null), 

    true, false,
  )
}
```

### Grouped Calls

**When using the same function/property multiple times, split them from other function/property uses.**
For example:

```kt
// This is incorrect.

val properties = Properties()
properties.setProperty("settings.dataCollection", extension.dataCollection.readable)
properties.setProperty("modules", extension.modules.joinToString())
properties.setProperty("versions.kordEx", kordExVersion.version)
properties.setProperty("versions.kord", kordVersion?.version)
properties.store(outputFile.get().asFile.writer(), null)

// Do this instead.

val properties = Properties()

properties.setProperty("settings.dataCollection", extension.dataCollection.readable)
properties.setProperty("modules", extension.modules.joinToString())
properties.setProperty("versions.kordEx", kordExVersion.version)
properties.setProperty("versions.kord", kordVersion?.version)

properties.store(outputFile.get().asFile.writer(), null)
```

### Chained Access/Complex Arguments

**When chaining multiple function/property uses in one statement, split them onto separate lines.**
Also, if you're chaining a lot of functions in the same statement, split them into groupings as explained earlier. 
This also applies when you're passing complex arguments to functions.

For example:

```kt
// This is incorrect.

val sourceSet = target.extensions.getByType(SourceSetContainer::class.java).first { it.name == "main" }
sourceSet.output.dir(mapOf("builtBy" to task), outputDir)

// Do this instead.

val sourceSet = target
  .extensions
  .getByType(SourceSetContainer::class.java)
  .first { it.name == "main" }

sourceSet.output.dir(
  mapOf("builtBy" to task),

  outputDir
)
```

---

## Example

### Incorrect

```kt

private fun addGeneratedFiles(target: Project, extension: KordExExtension, kordVersion: Version?, kordExVersion: Version) {
  val outputDir = target.layout.buildDirectory.dir("generated")
  val outputFile = target.layout.buildDirectory.file("generated/kordex.properties")
  val task = target.tasks.create("generateMetadata") {
    group = "generation"
    description = "Generate KordEx metadata."
    outputs.file(outputFile)
    doLast {
      val properties = Properties()
      properties.setProperty("settings.dataCollection", extension.dataCollection.readable)
      properties.setProperty("modules", extension.modules.joinToString())
      properties.setProperty("versions.kordEx", kordExVersion.version)
      properties.setProperty("versions.kord", kordVersion?.version)
      properties.store(outputFile.get().asFile.writer(), null)
    }
  }

  val sourceSet = target.extensions.getByType(SourceSetContainer::class.java).first { it.name == "main" }

  sourceSet.output.dir(mapOf("builtBy" to task), outputDir)
}
```

### Correct

```kt
private fun addGeneratedFiles(
  target: Project,
  extension: KordExExtension,
  kordVersion: Version?,
  kordExVersion: Version
) {
  val outputDir = target.layout.buildDirectory.dir("generated")
  val outputFile = target.layout.buildDirectory.file("generated/kordex.properties")

  val task = target.tasks.create("generateMetadata") {
    group = "generation"
    description = "Generate KordEx metadata."

    outputs.file(outputFile)

    doLast {
      val properties = Properties()

      properties.setProperty("settings.dataCollection", extension.dataCollection.readable)
      properties.setProperty("modules", extension.modules.joinToString())
      properties.setProperty("versions.kordEx", kordExVersion.version)
      properties.setProperty("versions.kord", kordVersion?.version)

      properties.store(outputFile.get().asFile.writer(), null)
    }
  }

  val sourceSet = target
    .extensions
    .getByType(SourceSetContainer::class.java)
    .first { it.name == "main" }

  sourceSet.output.dir(
    mapOf("builtBy" to task),

    outputDir
  )
}
```
