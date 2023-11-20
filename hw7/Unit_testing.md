Task 4.

Operations with a Book Collection

```java
package org.example;

import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import java.io.ByteArrayOutputStream;
import java.io.PrintStream;

import java.util.ArrayList;

import static org.junit.jupiter.api.Assertions.assertEquals;

/**
 * Unit test for Book.
 */
public class BookTest {

    private final PrintStream standardOut = System.out;
    private final ByteArrayOutputStream outputStreamCaptor = new ByteArrayOutputStream();

    ArrayList<Book> books = new ArrayList<Book>();

    @BeforeEach
    public void setUp() {
        books.add(new Book("TestName1", "TestAuthor1", "test", 1996));
        books.add(new Book("TestName2", "TestAuthor2", "test", 2000));
        books.add(new Book("TestName3", "TestAuthor4", "dev", 1985));
        books.add(new Book("TestName4", "TestAuthor4", "dev", 2005));
        books.add(new Book("TestName5", "TestAuthor4", "devOps", 2000));

        System.setOut(new PrintStream(outputStreamCaptor));
    }

    @AfterEach
    public void tearDown() {
        System.setOut(standardOut);
    }

    @Test
    public void printTest() {
        String expected = "List of authors: [TestAuthor1, TestAuthor2, TestAuthor4, TestAuthor4, TestAuthor4]";
        Book.print(books);
        assertEquals(expected, outputStreamCaptor.toString().trim());
    }
}
```
