## Maven

- Address both how software is built and dependencies.
- Conventions: 
    - `src/main/java`, `src/main/resources`
    - `src/test/java`, `src/test/resources`
- POM (Project Object Model)


## Reactor

- Entity handling multi-module projects:
    - collect the available modules
    - sort them in the correct build order 
    - build them one by one


## Build Lifecycles

It is a list of pre-defined <span class="text-highlight">**phases**</span> to give order to <span class="text-highlight">**goal**</span> execution.

```bash
 1  validate
 2  generate-sources
 3  process-sources
 4  generate-resources
 5  process-resources
 6  compile
 7  process-test-sources
 8  process-test-resources
 9  test-compile
10  test
11  package
12  install
13  deploy
```


## Lifecycle Examples

```bash
mvn clean install
```

```bash
mvn clean package -Pprofile-ambulance
```

```bash
mvn test -Pjacoco-coverage
```

Running a phase causes the execution of all the associated goals.


## Plug-ins

- Primary way to extend Maven:
    - `org.apache.maven.plugin.AbstractMojo`
- Plugin provides a set of goals:
    - `mvn [plugin-name]:[goal-name]`
- Goals can be associated with phases of the lifecycle:

```xml
<execution>
    <id>jacoco-site</id>
    <phase>package</phase>
    <goals>
        <goal>report</goal>
    </goals>
</execution>
```


## Repositories

- `.m2` local repo
- remote repo (Nexus)
- both store artifacts: `groupId:artifactId:version`


## SNAPSHOT

- instable version, nighly built, under development, <span class="text-highlight">**latest build**</span>, <span class="text-highlight">**not release yet**</span>
- not allowed in a release, can get frequent updates
    - `maven-metadata-local.xml` tells which is the latest snapshot
    - `<updatePolicy>` always, daily (default), never


## Dependency Resolution

When an application is built:
- <span class="text-highlight">**stable:**</span> maven searches for dependencies in the local repo, if stable version not found, it searches in the remote one and copies it into the local one.
- <span class="text-highlight">**SNAPSHOT:**</span> version is not stable, maven searches a newer version in the remote repo once a day
    - `foo-1.0-20110506.110000-1.jar` artifact of the 06/05/2011 at 11:00:00



## SNAPSHOT Configuration

```xml
<repository>
    <id>foo-repository</id>
    <url>...</url>
    <snapshots>
        <enabled>true</enabled>
        <updatePolicy>always/daily/xxx min/never</updatePolicy>
    </snapshots>
</repository>
```


## Continuous Integration (CI)

> practice of integrating all developer working code to a shared mainline (<span class="text-highlight">**trunk**</span>) several times a day

- detect problems fast
- locate problems easier


## Continuous...

- <span class="text-highlight">Delivery:</span> codebase is always deployable, go to production in one click.
- <span class="text-highlight">Deployment</span> everytime the CI build passes, changes are automatically pushed to production.