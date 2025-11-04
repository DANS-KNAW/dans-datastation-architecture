Common Practices
================

Here are some miscellaneous common practices to follow when developing for the DANS Data Station Architecture. It is assumed that you are using IntelliJ. If
this is not the case, please adapt accordingly.

Code Style
----------

* Install the IntelliJ [code style] and [inspections]. Format the source code with these settings in our own projects. Resolve the warnings
  indicated by the inspections.
* In Dataverse try to minimize code changes due to reformatting, so only apply formatting to code that you have changed anyway.
* In the POM file keep the order the of the elements as follows (note that some are optional):
    * `modelVersion`
    * `parent`
    * `groupId`
    * `artifactId`
    * `version`
    * `name`
    * `url`
    * `description`
    * `inceptionYear`
    * `properties`
    * `scm`
    * `dependencyManagement`
    * `dependencies`
    * `build`
    * `repositories`
    * `distributionManagement`
    * `profiles`

### Lombok

Use [Lombok]{:target=_blank} for:

* Adding loggers with the `@Slf4j` annotation (this names the logger after the fully qualified class name automatically).
* Creating getters, setters and constructors on value objects (i.e. the main purpose of the object is to store values and not to perform operations).

Dependency Management
---------------------
Dependency management of Java projects is done with Maven. Projects should inherit from `dd-parent`. The first thing that most projects will include is
`io.dropwizard:dropwizard-core`.

Testing
-------

* Unit test names should be as descriptive as possible. Since this will often involve creating long test names, use `snake_case` instead of `camelCase` here.
* Unit tests will often need to write some temporary data to disk. The location for this is `<project-dir>/target/test/<ClassNameOfUnitTest>`. By working under
  `target` we make sure the unit tests don't interfere with the project itself or the test files we are using for [debugging](#debugging).
* Unit tests should clear their temporary directory **before** the tests start, but leave everything on disk after finishing. This allows you to diagnose
  any problems with a test by running it and inspecting its temporary directory.

Debugging
---------

For debugging use the scripts in [dans-dev-scripts]{:target=_blank}. Start the environment with `start-env.sh`. This sets up configuration files under
`<project-dir>/etc/` for use during debugging and create directory to store input and output files under `<project-dir>/data/`. Start the program with the
`start-*debug.sh` helper scripts and then attach IntelliJ to the VM.

Documentation
-------------
Each module has its associated documentation site, which is published at `dans-knaw.github.io`. The archetype sets up the project with a skeleton site. Use
the `start-mkdocs.sh` script in [dans-dev-scripts]{:target=_blank} to start the site locally and see what it looks like after you have made your changes.

Each documentation site follows a common structure which depends on the type of module: library, microservice, or command-line application. See existing
documentation sites for examples.

### JavaDocs

If the project is a library it should include JavaDocs. Extensive code examples are best relegated to separated pages, outside
the JavaDocs, so that you can make full use of the extended Markdown support of mkdocs. You can then link to those from the JavaDocs.


[code style]: dev/dans-intellij-codestyles.xml

[inspections]: dev/dans-intellij-inspections.xml

[dans-dev-scripts]: {{ dans_dev_scripts_repo }}

[Lombok]: https://projectlombok.org/