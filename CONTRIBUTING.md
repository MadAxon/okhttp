Contributing
============

Our goal with this project is to build a simple, fast, and secure component that you can trust. We
have scoped the project deliberately to address common use cases easily, and made it extensible so
it'll handle exotic use cases too.

Keeping the project small and stable limits our ability to accept new contributors. We are not
seeking new committers at this time, but some small contributions are welcome.

If you've found a bug, please contribute a failing test case so we can study and fix it.

If you have a new feature idea, please build it in an external library. There are
[many libraries][works_with_okhttp] that sit on top or hook in via existing APIs. If you build
something that integrates with OkHttp, tell us so that we can link it!


AI Agents and Development Tools Policy
--------------------------------------

We welcome engineers leveraging modern tooling, including AI coding assistants and autonomous agents (e.g., Claude, GitHub Copilot, Cursor), provided all contributions adhere strictly to the repository's quality bar:

* **Human-in-the-loop review**: Every change must be thoroughly reviewed and understood by an engineer before submission.
* **Strict automated verification**: Code must pass all tests (`./gradlew check`), style checks (`./gradlew spotlessCheck`), and compatibility validation (`./gradlew animalSnifferMain`).
* **Test coverage**: Bug fixes and features must include comprehensive unit and regression tests.
* **Architecture & API stability**: Public APIs must maintain backward binary compatibility, and internal implementation details (`okhttp3.internal.*`) must remain strictly encapsulated.

For detailed guidelines, environment setup, and agent rules, see [AGENTS.md](AGENTS.md).


Code Contributions
------------------

Get working code on a personal branch with tests passing before you submit a PR:

```
./gradlew clean check
```

Please make every effort to follow existing conventions and style in order to keep the code as
readable as possible.

Contribute code changes through GitHub by forking the repository and sending a pull request. We
squash all pull requests on merge.


Gradle Setup
------------

```
$ cat local.properties
sdk.dir=PATH_TO_ANDROID_HOME/sdk
org.gradle.caching=true
```

Running Android Tests
---------------------

```
$ ANDROID_SDK_ROOT=PATH_TO_ANDROID_HOME/sdk ./gradlew :android-test:connectedCheck -PandroidBuild=true
```

Committer's Guides
------------------

* [Concurrency][concurrency]
* [Debug Logging][debug_logging]
* [Releasing][releasing]
* [Agent & Engineering Guidelines][agents_guide]

[concurrency]: https://lysine.dev/okhttp/concurrency/
[debug_logging]: https://lysine.dev/okhttp/debug_logging/
[releasing]: https://lysine.dev/okhttp/releasing/
[works_with_okhttp]: https://lysine.dev/okhttp/works_with_okhttp/
[okhttp_build]: https://github.com/lysine-dev/okhttp/blob/master/okhttp/build.gradle.kts
[agents_guide]: AGENTS.md
