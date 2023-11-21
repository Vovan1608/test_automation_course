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

import static org.junit.jupiter.api.Assertions.*;

/**
 * Unit test for Book.
 */

public class BookTest {

    private final PrintStream standardOut = System.out;
    private final ByteArrayOutputStream outputStreamCaptor = new ByteArrayOutputStream();

    private final ArrayList<Book> books = new ArrayList<Book>();

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

    @Test
    public void prinNegativetTest() {
        String expected = "List of authors: [TestAuthor1, TestAuthor2, TestAuthor3, TestAuthor4, TestAuthor5]";
        Book.print(books);

        assertNotEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void printListInGivenGenreTest() {
        String genre = "dev";
        String expected = "The list of authors who have written books in a given genre - dev are [TestAuthor4, TestAuthor4]";
        Book.printListInGivenGenre(books, genre);

        assertEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void printListInGivenGenreNegativeTest() {
        String genre = "dev";
        String expected = "The list of authors who have written books in a given genre - test are [TestAuthor1, TestAuthor2]";
        Book.printListInGivenGenre(books, genre);

        assertNotEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void printListInGivenYearTest() {
        int year = 2000;
        String expected = "The list of authors who have written books in a given year - 2000 are [TestAuthor2, TestAuthor4]";
        Book.printListInGivenYear(books, year);

        assertEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void printListInGivenYearNegativeTest() {
        int year = 2000;
        String expected = "The list of authors who have written books in a given year - 2000 are [TestAuthor1, TestAuthor2]";
        Book.printListInGivenYear(books, year);

        assertNotEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void printListInGivenAuthorTest() {
        String author = "TestAuthor4";
        String expected = "The list of authors who have written books in a given author - TestAuthor4 are [TestAuthor4, TestAuthor4, TestAuthor4]";
        Book.printListInGivenAuthor(books, author);

        assertEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void printListInGivenAuthorNegativeTest() {
        String author = "TestAuthor4";
        String expected = "The list of authors who have written books in a given author - TestAuthor4 are [TestAuthor4, TestAuthor4]";
        Book.printListInGivenAuthor(books, author);

        assertNotEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void findBooksToGivenGenreTest() {
        String genre = "test";
        String expected = "All books that belong to a given genre - test are [TestName1, TestName2]";
        Book.findBooksToGivenGenre(books, genre);

        assertEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void findBooksToGivenGenreNegativeTest() {
        String genre = "test";
        String expected = "All books that belong to a given genre - test are [TestName4, TestName3]";
        Book.findBooksToGivenGenre(books, genre);

        assertNotEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void removeAllBooksWrittenByGivenAuthorTest() {
        String author = "TestAuthor4";
        String expected = "Removed books by author - TestAuthor4 are [TestName3, TestName4, TestName5]";
        Book.removeAllBooksWrittenByGivenAuthor(books, author);

        assertEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void removeAllBooksWrittenByGivenAuthorNegativeTest() {
        String author = "TestAuthor4";
        String expected = "Removed books by author - TestAuthor4 are [TestName1, TestName2, TestName3]";
        Book.removeAllBooksWrittenByGivenAuthor(books, author);

        assertNotEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void sortCollectionByGivenCriterionTest() {
        String criterion = "author";
        String expected = "[Book { title = 'TestName1' author = 'TestAuthor1' genre = 'test' year = '1996'}, Book { title = 'TestName2' author = 'TestAuthor2' genre = 'test' year = '2000'}, Book { title = 'TestName3' author = 'TestAuthor4' genre = 'dev' year = '1985'}]";
        Book.sortCollectionByGivenCriterion(books, criterion);

        assertEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void sortCollectionByGivenCriterionNegativeTest() {
        String criterion = "author";
        String expected = "[Book { title = 'TestName3' author = 'TestAuthor4' genre = 'dev' year = '1985'}, Book { title = 'TestName1' author = 'TestAuthor1' genre = 'test' year = '1996'}, Book { title = 'TestName2' author = 'TestAuthor2' genre = 'test' year = '2000'}]";
        Book.sortCollectionByGivenCriterion(books, criterion);

        assertNotEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void combineBookCollectionsTest() {
        ArrayList<Book> books1 = new ArrayList<Book>();
        ArrayList<Book> books2 = new ArrayList<Book>();

        books1.add(new Book("TestName1", "TestAuthor1", "test1", 1996));
        books2.add(new Book("TestName11", "TestAuthor11", "test11", 1997));

        String expected = "[Book { title = 'TestName1' author = 'TestAuthor1' genre = 'test1' year = '1996'}, Book { title = 'TestName11' author = 'TestAuthor11' genre = 'test11' year = '1997'}]";
        Book.combineBookCollections(books1, books2);

        assertEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void combineBookCollectionsNegativeTest() {
        ArrayList<Book> books1 = new ArrayList<Book>();
        ArrayList<Book> books2 = new ArrayList<Book>();

        books1.add(new Book("TestName1", "TestAuthor1", "test1", 1996));
        books2.add(new Book("TestName11", "TestAuthor11", "test11", 1997));

        String expected = "[Book { title = 'TestName1' author = 'TestAuthor1' genre = 'test1' year = '1996'}]";
        Book.combineBookCollections(books1, books2);

        assertNotEquals(expected, outputStreamCaptor.toString().trim());
    }

    @Test
    public void createSubcollectionTest() {
        String genre = "test";
        Book.createSubcollection(books, genre);

        assertTrue(outputStreamCaptor.toString().contains("TestName1") & outputStreamCaptor.toString().contains("TestName2"));
    }
}
```
