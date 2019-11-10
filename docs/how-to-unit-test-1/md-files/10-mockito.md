# Mockito

<img src="images/escape-egg.jpg" alt="Help the cat" width="50%"/>

Escape from old testing patterns.


## Object mock

- <span class="text-highlight">**Stunt Double**</span> is a trained replacements used for dangerous action sequences in movies.
- <span class="text-highlight">**Test Double**</span> acts as stunt double, it is a skilled replacement of the collaborator class.
- <span class="text-highlight">**Mock Object**</span>
    - Return the <span class="text-highlight-red">*expected value*</span> to a SUT inside a <span class="text-highlight-red">*well known test context*</span>.
    - Keep track of invocation count.


## Overview

- <span class="text-highlight">**Mock out external dependencies (collaborators).**</span> Interactions are with the mock not with the real object (network, database or another service).
- <span class="text-highlight">**Set an expectation.**</span> The mock return the expected values.


## Features

- <span class="text-highlight">Verify if a method has been called or not.</span> Verify, never, times.
- <span class="text-highlight">Throw exceptions.</span> Test exceptional conditions like a database failure.
- <span class="text-highlight">Consecutive calls.</span> Call a method in a loop, provide the list of the expected values.
- <span class="text-highlight">Answer and callbacks.</span> Return a dynamic result and not a fixed value.
- <span class="text-highlight">Spying objects.</span> Spy a real object to provide some mocked behaviour.



## Matchers

- <span class="text-highlight">Built-in matchers.</span> Wildcards:
    - `anyInt()`
    - `anyString()`
    - `any(java.lang.Class<T> clazz)`


## Annotations

```java
@RunWith(MockitoJUnitRunner.class)
public class MockitoAnnotationTest {
    ...
}
```

- `@Mock` create and inject a mock instance.
- `@Spy` to spy an existing instance.
- `@InjectMocks` to inject mock instances into the SUT