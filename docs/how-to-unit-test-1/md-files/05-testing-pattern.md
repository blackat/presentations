# Testing pattern

```
test do
    setup
    exercise
    verify
    teardown
end
```


## Setup

```java
@Before
public void setUp() { ... }
```

- <span class="text-highlight">SUT</span> is set up,
- <span class="text-highlight">test fixture</span> is created.


## Exercise

```java
@Test
public void testMethod() { ... }
```

- <span class="text-highlight">The method</span> of the SUT is executed.


## Verify

```java
public static void assertEquals(java.lang.String message,
                                java.lang.Object expected,
                                java.lang.Object actual)
```

- The result of the exercise phase is verified against the expected value.



## Teardown

```java
@After
public void tearDown() { ... }
```

- SUT and fake collaborators are destroyed, memory is released.