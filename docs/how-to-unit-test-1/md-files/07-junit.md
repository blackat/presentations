# Junit

```java
public class CatTest {

    @Before
    public void setUp() throws Exception {
    }

    @Test
    public void testMethodOne() throws Exception {
    }

    @After
    public void tearDown() throws Exception {
    }
}
```


## Simple Test Setup

- `@Before` runs method before each `@Test` method, but after any `@Before` method of the super class.
- `@After` runs method after each `@Test` method, but before any `@After` method of the super class.


## Heavy Test Setup

```java
public class CatPersistTest {
    @BeforeClass
    public static void setUpBeforeClass() throws Exception {
        logger.info("SetUpBeforeClass.");
    }
    @AfterClass
    public static void tearDownAfterClass() throws Exception {
        logger.info("TearDownAfterClass.");
    }
    @Before
    public void setUp() throws Exception {
        logger.info("SetUp().");
    }
    @After
    public void tearDown() throws Exception {
        logger.info("TearDown().");
    }
}
```


## Load Once

- `@BeforeClass` runs only once before all the tests in a class.
- `@AfterClass` runs only once after all the tests in a class.


## Test with inmemory database

```bash
INFO [main] (DriverManagerConnectionProviderImpl.java:166) - HHH000401: using driver [org.h2.Driver] at URL [jdbc:h2:mem:test]
INFO [main] (DriverManagerConnectionProviderImpl.java:172) - HHH000046: Connection properties: {user=sa}
INFO [main] (DriverManagerConnectionProviderImpl.java:180) - HHH000006: Autocommit mode: false
INFO [main] (DriverManagerConnectionProviderImpl.java:102) - HHH000115: Hibernate connection pool size: 20 (min=1)
INFO [main] (CatPersistTest.java:31) - SetUpBeforeClass.
INFO [main] (CatPersistTest.java:45) - SetUp().
INFO [main] (CatPersistTest.java:46) - ...insert data
INFO [main] (CatPersistTest.java:64) - A test.
INFO [main] (CatPersistTest.java:53) - TearDown().
INFO [main] (CatPersistTest.java:54) - ...remove data
--- 2nd test
INFO [main] (CatPersistTest.java:45) - SetUp().
INFO [main] (CatPersistTest.java:46) - ...insert data
INFO [main] (CatPersistTest.java:80) - Another test.
INFO [main] (CatPersistTest.java:53) - TearDown().
INFO [main] (CatPersistTest.java:54) - ...remove data
INFO [main] (CatPersistTest.java:37) - TearDownAfterClass.
INFO [main] (DriverManagerConnectionProviderImpl.java:281) - HHH000030: Cleaning up connection pool [jdbc:h2:mem:test]
```