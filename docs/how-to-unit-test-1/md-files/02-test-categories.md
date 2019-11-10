## Test Categories

Tests are divided in 3 categories:
- unit tests
- integration tests
- e2e tests


## Unit tests

- Focus on a <span class="text-highlight">**single class**</span> by replacing real collaborators with <span class="text-highlight-red">*test doubles*</span>.
- <span class="text-highlight">Isolated</span>, very fast to execute and small.


## Integration tests

- Focus on the <span class="text-highlight">**proper integration of different modules**</span> of the code including uncontrolled code.
- Run slower than unit tests, require and application context and some resources


## E2E tests

- Focus on the <span class="text-highlight">**client's point of view**</span>.
- <span class="text-highlight-red">*Test doubles are usually not used*</span>, the point is to test the real system.
- Run really slow, significant amount of time is required