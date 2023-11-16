Task 1

These tasks are based on the basic methods of the String class. To solve them, you can choose 4 points. Demonstrate the correctness of the created methods.

1. Write a method that takes two strings and returns true if they are equal, and false otherwise. Consider the possibility of case-sensitive and case-insensitive comparison.

2. Implement a method that takes a string and two indices, and returns the substring that is contained between those indices.

3. Create a method that checks whether a certain substring is contained in a given string, and returns the index of its first occurrence.

4. Write a method that replaces all occurrences of one substring with another in a given string.

5. Implement a method that determines whether a string contains digits, and returns true or false accordingly.

6. Write a method that removes all leading and trailing spaces from a string.

7. Create a method that splits a string into an array of substrings according to a given delimiter.

```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;
import java.util.Arrays;

class Task1 {

    public static boolean isCompareTwoStrings (String str1, String str2) {
        boolean compareResult = str1.toLowerCase().equals(str2.toLowerCase());

        return compareResult;
    }

    public static String makeSubstring (String str, int startIndex, int endIndex) {
        String subString = str.substring(startIndex, endIndex);

        return subString;
    }

    public static int checkSubstringInString (String str, String subStr) {
        int index = str.indexOf(subStr);

        return index;
    }

    public static String replaceallOccurrencesOfOneSubstringWithAnother (String str, String subStrYouWant, String subStrInStr) {
        String resStr = str.replaceAll(subStrYouWant, subStrInStr);

        return resStr;
    }

    public static boolean hasStringDigits (String str) {
        Pattern pattern = Pattern.compile("\\d", Pattern.CASE_INSENSITIVE);
        Matcher matcher = pattern.matcher(str);
        boolean matchFound = matcher.find();

        return matchFound;
    }

    public static String removeAllLeadingAndTrailingSpaces (String str) {
        String trimStr = str.trim();

        return trimStr;
    }

    public static String[] splitString (String str, String delimiter) {
        String[] splitString = str.split(delimiter);

        return splitString;
    }

    public static void main (String[] args) {

        boolean res1 = Task1.isCompareTwoStrings("Vova", "Sasha");

        System.out.println("Result of task1: " + res1);
        System.out.println();

        String res2 = Task1.makeSubstring("SoftSrve", 3, 8);

        System.out.println("Result of task2: " + res2);
        System.out.println();

        int res3 = Task1.checkSubstringInString("SoftServe", "Serve");

        System.out.println("Result of task3: " + res3);
        System.out.println();


        String str1 = "SoftServeSoftServSoftServe";
        String resStr =  Task1.replaceallOccurrencesOfOneSubstringWithAnother(str1, "Sof", "Fas");
        System.out.println(resStr);
        System.out.println();

        String str2 = "Soft22Serve";
        boolean res4 = Task1.hasStringDigits(str2);
        System.out.println("Result of task4: " + res4);
        System.out.println();

        String res5 = Task1.removeAllLeadingAndTrailingSpaces("    SoftServe        ");
        System.out.println("Result of task5: " + res5);
        System.out.println();

        String text = "FIFA will never regret it";
        String[] res6 = Task1.splitString(text, " ");
        System.out.println("Result of task6: " + Arrays.toString(res6));
    }
}
```

Task 2

Create a class Rectangle to represent a rectangle. The class should have the following fields:

width: the width of the rectangle, of type double.
height: the height of the rectangle, of type double.
angle: the angle between the sides, of type double. The angle is always 90 degrees.
The class should have the following constructors:

A default constructor that initializes all fields to their default values.
A constructor that takes the width and height.
The class should have the following getters and setters:

For each field of the class, a getter should be created that returns the current value of the field.
For each field of the class, a setter should be created that sets a new value for the field.
Task:

Implement the Rectangle class according to the problem statement.

Additional requirements:

The class should be encapsulated.
The class should be tested.
Methods that can be implemented in the Rectangle class:

A method calculateArea() that calculates the area of the rectangle.
A method calculatePerimeter() that calculates the perimeter of the rectangle.
A method getDiagonal() that returns the length of the diagonal of the rectangle.
Demonstrate the correctness of the created methods.

```java
import java.lang.Math;

class Rectangle {

    private double width;
    private double height;
    private double angle = 90;

    public Rectangle () {

    }

    public Rectangle (double width, double height) {
        this.width = width;
        this.height = height;
    }

    public double getWidth () {
        return this.width;
    }

    public void setWidth (double width) {
        this.width = width;
    }

    public double getHeight () {
        return this.height;
    }

    public void setHeight (double height) {
        this.height = height;
    }

    public double getAngle () {
        return this.angle;
    }

    public void setAngle (double angle) {
        this.angle = angle;
    }

    public double calculateArea(double width, double height, double angle) {
        double area = width * height * Math.sin(angle);

        return area;
    }

    public double calculatePerimeter (double width, double height) {
        int doubled = 2;
        double perimeter = doubled * (width + height);

        return perimeter;
    }

    @Override
    public String toString() {
        return "Triangel { " +
                "width = '" + width + '\'' +
                " height = '" + height + '\'' +
                " angle = '" + angle + '\'' +
                '}';
    }

    public static void main (String[] args) {

        Rectangle rect = new Rectangle(2, 5);

        System.out.println(rect.toString());

        System.out.println(rect.calculateArea(2, 5, 90));
        System.out.println(rect.calculatePerimeter(2, 5));
    }
}
```

Task 3
Analysis of a Collection of Numbers

Create an ArrayList that will store integers (Integer). Fill the collection with 20 random numbers from 1 to 100. Use the Random class to generate random numbers.

1. Print all elements of the collection to the console.

2. Find and print the minimum and maximum numbers in the collection.

3. Calculate and print the average value of the numbers in the collection.

4. Remove all even numbers from the collection, and then print the updated collection to the console.

5. Check if the collection contains a given number (for example, 50), and print the result to the console.

6. Sort the collection in ascending order and print the sorted collection to the console.

```java
import java.io.*;
import java.util.*;

class Task3 {

//    public static boolean checkNumber (int num) {
//        return
//    }

    public static void main (String[] args) {

        ArrayList<Integer> randomeIntegers = new ArrayList<Integer>();

        int MIN_RANDOM_LIMIT = 1;
        int MAX_RANDOME_LIMIT = 100;
        int i = 0;
        int step = 1;
        int randomeIntegersLength = 20;
        int sum = 0;

        while ( i < randomeIntegersLength ) {
            int randomNum = MIN_RANDOM_LIMIT + (int)( Math.random() * (MAX_RANDOME_LIMIT - MIN_RANDOM_LIMIT + 1));

            randomeIntegers.add(randomNum);

            i += step;
            sum += randomNum;
        }

        System.out.println(randomeIntegers);

        Collections.sort(randomeIntegers);

        System.out.println("Min value is: " + randomeIntegers.get(0));
        System.out.println("Max value is: " +randomeIntegers.get(randomeIntegersLength - 1));

        double average = sum / randomeIntegersLength;

        System.out.println("The average value is: " + average);

        ArrayList<Integer> randomeOddIntegers = new ArrayList<Integer>();

        for (int num : randomeIntegers) {
            if ( num % 2 != 0 ) {
                randomeOddIntegers.add(num);
            }
        }

            System.out.println("Randome integers without even values: " + randomeOddIntegers);
    }
}
```
