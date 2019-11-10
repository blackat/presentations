# TDD: code differently

- <span class="text-highlight">Test-last approach.</span> Code first and then test.
- <span class="text-highlight">Test-first approach.</span> Test-driven development.


## Test-last

- Test are written <span class="text-highlight-red">*after*</span> the implementation.
- <span class="text-highlight">**Pros**</span> Functionalities of the unit are well understood.
- <span class="text-highlight">**Cons**</span>
    - Focus on <span class="text-highlight-red">*testing the implementation*</span> and the <span class="text-highlight-red">*interface (behaviour)*</span> of the SUT, hence:
        - tests tightly coupled with the implementation;
        - encourage (subconsciously) to select tests expected to pass successfully.
    - Temptation to not write tests at all especially close to dealines.


## Test-first (AKA TDD)

- Tests are writte <span class="text-highlight">*before*</span> the implementation.
- <span class="text-highlight">**Pros**</span>
    - Think about the <span class="text-highlight-red">**behaviour**</span> of the unit and not the <span class="text-highlight-red">*implementation*</span>.
    - High code coverage, only required functionlities are added.
- <span class="text-highlight">**Controversy**</span>
    - [TDD is dead](david.heinemeierhansson.com/2014/tdd-is-dead-long-live-testing.html)
    - [Really dead?](martinfowler.com/articles/is-tdd-dead/)
    - [Summary](www.infoq.com/news/2014/06/tdd-dead-controversy)


## TDD applications

- <span class="text-highlight">Bug chase:</span> identifiy and fix.
- <span class="text-highlight">API design:</span> improve usability, readability and correctness of the API.

## TDD to bug chase

- Write a test method to reproduce the issue, put the issue # in the name of the method.
- Execute the test and make it fail, the issue has been reproduced.
- Change the code to make the test passes.
- <span class="text-highlight">Strengh the net of automatic tests.</span>
- <span class="text-highlight">Test-first approach isn't it?</span>


## TDD to API design

- TDD is about <span class="text-highlight">design an API</span>:
    - think in terms of the API of the object by testing <span class="text-highlight-red">*its external behaviour*</span> and not the <span class="text-highlight-red">*implementation*</span>;
    - the test is the <span class="text-highlight-red">**client**</span> of the API implemented by the SUT.
- Focus on what is really required.
- <span class="text-highlight">**Rule.**</span> Never write code without a failing test.
- <span class="text-highlight-red">**Test are first class citizens.**</span> Refactor, maintain, keep them up-to-date as other classes.


## How to apply TDD
<img src="images/tdd.png" alt="Help the cat" width="50%"/>


## Red

- Write a test w.r.t. a <span class="text-highlight-red">*new functionality or requirement*</span> (clear and well defined task) that should be implemented.
    - <span class="text-highlight">**Where to start.**</span>
        - Typical case: the <span class="text-highlight">*the golden path*</span>.
    - Create class (SUT) and methods from non compiling test, run it and make it fail with clear assertion messages.


## Green (YAGNi + KISS)

- Make the test green with smallest amount of code (YAGNI) to have a simple solution (KISS).
- The test method must test a <span class="text-highlight-red">*single, clear and well defined requirement*</span>.


## Refactor (DRY)

- <span class="text-highlight">Change code for restructuring (clean code)</span>
    - significant method names
    - remove duplicated code
    - make the code readable and easy understandable.
- Tests are your documentation.
- No functionality change.