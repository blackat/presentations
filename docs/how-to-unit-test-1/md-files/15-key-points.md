# Key points

- <span class="text-highlight">Code for everybody</span>
- <span class="text-highlight">SUT:</span> System Under Test, `userRepositorySUT`
- <span class="text-highlight">Collaborator or DOC (Dependent on Component):</span> entity required by a SUT to achieve a goal, same granularity of the SUT.
- <span class="text-highlight">Test doubles or fake replacement:</span> an object that <span class="text-highlight-red">*conforms to the interface*</span> of the required Collaborator and takes its place (mock, spy, fake object, etc.).



- <span class="text-highlight">Test fixture:</span> well know and fixed environment to have a repeatable test.
- <span class="text-highlight">Four phases:</span> setup, exercise, verify, teardown.
- <span class="text-highlight">Naming convention:</span> respect it!