Task 1

Calculation of the Final Product Price Including VAT

Create a program that asks the user for the price of a product excluding VAT and calculates the final cost including VAT (add 20% to the initial price). Display both prices — excluding VAT and including VAT. Use the Scanner to enter the initial price.

```java
import java.util.Scanner;

public class Task1
{
    public static void main( String[] args )
    {
        Scanner scanner = new Scanner(System.in);

        System.out.println( "Give me the price of a product excluding VAT: " );
        double priceWithoutVAT = scanner.nextDouble();
        double VAT = 0.2;
        double  priceWithVAT = priceWithoutVAT * (1 + VAT);

        System.out.println("The price of a product excluding VAT: " + priceWithoutVAT);
        System.out.println("The price of a product including VAT: " + priceWithVAT);
    }
}
```

Task 2

Average Temperature Calculation

Write a program that asks the user for the temperature for five days (use the Scanner to enter data) and calculates the average temperature over those days. Use the float variable type to store temperatures and arithmetic operators to compute the average value.

```java
import java.util.Scanner;

public class Task2
{
    public static void main( String[] args )
    {
        Scanner scanner = new Scanner(System.in);
        float sumOfTemperatures = 0;
        int numberOfDays = 5;

        for (int i = 1; i <= numberOfDays; i+= 1) {
            System.out.println( "Take me  temperature for " + i + " day.");
            float temperatureForDay = scanner.nextFloat();
            sumOfTemperatures += temperatureForDay;
        }

        float averageTemperature = sumOfTemperatures / numberOfDays;

        System.out.println("The average temperature over those days: " + averageTemperature);
    }
}
```

Task 3

Counting Vowels in a String

Write a program that asks the user to input a string. Then, using a loop, count how many vowels (a, e, i, o, u) are in the string. Output the total number of vowels found.

```java
import java.util.Scanner;

public class Task3 {

    public static void main( String[] args ) {

        Scanner scanner = new Scanner(System.in);

        System.out.println( "Give me the sentence." );

        char[] sentence = scanner.nextLine().toLowerCase().toCharArray();
        int sentenceLength = sentence.length;
        int countVowels = 0;
        char[] vowels = { 'a', 'e', 'i', 'o', 'u' };
        int vowelsLength = vowels.length;

        for ( int i = 0; i < sentenceLength; i += 1 ) {

            for ( int j = 0; j < vowelsLength; j += 1) {

                if (sentence[i] == vowels[j]) {
                    countVowels += 1;
                }
            }
        }

        System.out.println("The total number of vowels are " + countVowels);
    }
}
```

Task 4

Even or Odd Number Checker

Write a program that asks the user to enter a number. The program then determines whether the number is even or odd using a control statement and prints the result.

```java
import java.util.Scanner;

public class Task4 {

    public static void main( String[] args ) {

        Scanner scanner = new Scanner(System.in);

        System.out.println( "Enter the number: " );
        int number = scanner.nextInt();
        String evenOrOdd = (number % 2) == 0 ? "even" : "odd";

        System.out.println("Number " + number + " is " + evenOrOdd);
    }
}
```

Task 5

Grade Calculator

Write a program that takes a numerical score (like a test score out of 100) and outputs the corresponding letter grade (A, B, C, D, F). Define the grade boundaries yourself (for example, 90-100 is an A, 80-89 is a B, etc.).

```java
import java.util.Scanner;

public class Task5
{
    public static void main( String[] args )
    {
        Scanner scanner = new Scanner(System.in);

        System.out.println( "Give me a numerical score from 1 to 100." );
        int numericalScore = scanner.nextInt();
        String grade = " ";

        if ( numericalScore > 0 & numericalScore < 21 ) {
            grade = "E";
        } else if (numericalScore > 20 & numericalScore < 41) {
            grade = "D";
        } else if (numericalScore > 40 & numericalScore < 61) {
            grade = "C";
        } else if (numericalScore > 60 & numericalScore < 81) {
            grade = "B";
        } else {
            grade = "A";
        }

        System.out.println("Yuor grade is: " + grade);
    }
```

Task 6

Simple Age Category Classifier

The program asks the user to input their age, and based on the age, it categorizes them as a child, teenager, adult, or senior. For example, 0-12 years could be a child, 13-19 a teenager, 20-59 an adult, and 60+ a senior.

```java
import java.util.Scanner;

public class Task6
{
    public static void main( String[] args )
    {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Give me yuor age: ");
        double age = scanner.nextDouble();
        String ageCategory = " ";

        if ( age > 0 & age < 13 ) {
            ageCategory = "child";
        } else if (age >= 13 & age < 20) {
            ageCategory = "teenager";
        } else if (age >= 20 & age < 59) {
            ageCategory = "adult";
        } else {
            ageCategory = "senior";
        }

        System.out.println("Your category is " + ageCategory);
    }
}
```

Task 7

Interest Calculator

Write a program that calculates the final amount of a bank deposit after a given number of years at a given interest rate. The program should ask the user for the initial deposit amount, the annual interest rate, and the number of years. Use a loop to calculate compound interest for each year and output the result to the console.

Some information for solution

The formula for calculating the final amount of a bank deposit using compound interest is given by:

A=P×(1+r)t

where:

    - 'A' is the amount of money accumulated after n years, including interest.
    - 'P' is the principal amount (the initial amount of money).

    - 'r' is the annual interest rate (decimal).
    - 't' is the time the money is invested for, in years.

```java

```
