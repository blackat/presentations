## Tips

- `mvn clean install` usually run only in CI
    - `mvn install` avoid cleaning up all the artifacts
- `mvn install -pl $moduleName -am`
    - `-pl` build only specified modules
    - `-am` build only modules the target depends on
- `-offline` go offline, no new snapshot, less traffic
- clean `.m2` from time to time to free up some space
- keep modules smalls to avoid
    - huge compilation time
    - coupling


## FAQ Session

Any doubts?
