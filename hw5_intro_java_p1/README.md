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

        System.out.println( "Take me the price of a product excluding VAT: " );
        double priceWithoutVAT = scanner.nextDouble();
        double VAT = 0.2;
        double  priceWithVAT = priceWithoutVAT * (1 + VAT);

        System.out.println("the price of a product excluding VAT: " + priceWithoutVAT);
        System.out.println("the price of a product including VAT: " + priceWithVAT);
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
