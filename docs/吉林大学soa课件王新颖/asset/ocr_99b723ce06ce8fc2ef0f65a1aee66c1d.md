```
```java
public class CounterTest extends junit.framework.TestCase {
    Counter counter1;

    public CounterTest() { }  // default constructor

    protected void setUp() {  // creates a (simple) test fixture
        counter1 = new Counter();
    }

    protected void tearDown() { } // no resources to release

    public void testIncrement() {
        assertTrue(counter1.increment() == 1);
        assertTrue(counter1.increment() == 2);
    }

    public void testDecrement() {
        assertTrue(counter1.decrement() == -1);
    }
}
```
```

> Note that each test begins with a *brand new* counter

> This means you don’t have to worry about the order in which the tests are run