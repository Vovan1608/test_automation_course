Task 1

Calculation of the Final Product Price Including VAT

Create a program that asks the user for the price of a product excluding VAT and calculates the final cost including VAT (add 20% to the initial price). Display both prices — excluding VAT and including VAT. Use the Scanner to enter the initial price.

```java
import java.util.Scanner;

public class Task1 {

    static Scanner scanner = new Scanner(System.in);

    public static void main( String[] args ) {

        System.out.println( "Give me the price of a product excluding VAT: " );
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

public class Task2 {

    static Scanner scanner = new Scanner(System.in);

    public static void main( String[] args ) {

        float sumOfTemperatures = 0;
        int numberOfDays = 5;
        int numOfDay = 1;

        while (numOfDay <= numberOfDays) {
            System.out.println( "Take me  temperature for " + numOfDay + " day.");
            float temperatureForDay = scanner.nextFloat();
            sumOfTemperatures += temperatureForDay;
            numOfDay += 1;
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

    static Scanner scanner = new Scanner(System.in);

    public static void main( String[] args ) {

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

    static Scanner scanner = new Scanner(System.in);

    public static void main( String[] args ) {

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

public class Task5 {

    static Scanner scanner = new Scanner(System.in);

    public static void main( String[] args ) {

        System.out.println( "Give me a numerical score from 1 to 100." );
        int numericalScore = scanner.nextInt();
        String grade;

        if ( numericalScore > 0 & numericalScore < 21 ) {
            grade = "E";
        } else if (numericalScore > 20 & numericalScore < 41) {
            grade = "D";
        } else if (numericalScore > 40 & numericalScore < 61) {
            grade = "C";
        } else if (numericalScore > 60 & numericalScore < 81) {
            grade = "B";
        } else if (numericalScore > 80 & numericalScore < 101) {
            grade = "A";
        } else {
            grade = "Wrong income data!";
        }

        String resultMessage = grade.length() == 1 ? "Yuor grade is: " + grade : grade;

        System.out.println(resultMessage);
    }
```

Task 6

Simple Age Category Classifier

The program asks the user to input their age, and based on the age, it categorizes them as a child, teenager, adult, or senior. For example, 0-12 years could be a child, 13-19 a teenager, 20-59 an adult, and 60+ a senior.

```java
import java.util.Scanner;

public class Task6 {

    static Scanner scanner = new Scanner(System.in);

    public static void main( String[] args ) {

        System.out.println("Give me yuor age: ");
        double age = scanner.nextDouble();
        String ageCategory;

        if ( age > 0 & age < 13 ) {
            ageCategory = "child";
        } else if (age >= 13 & age < 20) {
            ageCategory = "teenager";
        } else if (age >= 20 & age < 59) {
            ageCategory = "adult";
        } else if (age >= 59) {
            ageCategory = "senior";
        } else {
            ageCategory = "Wrong income data!";
        }

        int teenagerWordLength = 8;

        String finalMessage = ageCategory.length() > teenagerWordLength ? ageCategory : "Your category is " + ageCategory;

        System.out.println(finalMessage);
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
import java.util.Scanner;

class Task7 {

    static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {

        double MAX_AMOUNT = 100;
        double MIN_AMOUNT = 20;
        double initialDepositAmount;
        boolean isInitialDepositAmount;

        do {
            System.out.println("Enter the initial deposit amount (max amount - 100, min amount - 20):");
            initialDepositAmount = scanner.nextDouble();
            isInitialDepositAmount = initialDepositAmount >= MIN_AMOUNT & initialDepositAmount <= MAX_AMOUNT;
        }

        while (!isInitialDepositAmount);

        double MAX_INTEREST = 0.1;
        double MIN_INTEREST = 0.03;
        double annualInterestRate;
        boolean isAnnualInterestRate;

        do {
            System.out.println("Enter the annual interest rate (max interest - 10%, min interest - 3%):");
            annualInterestRate = scanner.nextDouble() / 100;
            isAnnualInterestRate = annualInterestRate >= MIN_INTEREST & annualInterestRate <= MAX_INTEREST;
        }

        while (!isAnnualInterestRate);

        double MAX_YEARS = 10;
        double MIN_YEARS = 2;
        double numberOfYears;
        boolean isNumberOfYears;

        do {
            System.out.println("Enter the number of years (max years - 10, min years - 2):");
            numberOfYears = scanner.nextDouble();
            isNumberOfYears = numberOfYears >= MIN_YEARS & numberOfYears <= MAX_YEARS;
        }

        while (!isNumberOfYears);

        double finalAmount = initialDepositAmount * Math.pow(1 + annualInterestRate, numberOfYears);

        System.out.println("finalAmount: " + finalAmount + " c.u.");
    }
}
```

Task 8 (using Random)

Rock, Paper, Scissors Game: Create a simple rock, paper, scissors game against the computer. The computer randomly chooses rock, paper, or scissors, and the user inputs their choice. Use a loop to play multiple rounds and keep score until the user decides to quit.

```java
import java.util.Scanner;
import java.util.Random;

public class RockPaperScissor {

    public static void main(String[] args) {

        Scanner scn = new Scanner(System.in);

        while(true) {

            //1. RANDOMIZED COMPUTER MOVE

            // array of string containing available moves.
            String [] availableMoves = {"rock", "paper", "scissors"};

            // using Random() function on indices of array so that it chooses a random move.
            int indexAvailableMoves = new Random().nextInt(availableMoves.length);
            String computerMove = availableMoves[indexAvailableMoves];

            System.out.println("Computer has chosen it's move.");
            System.out.println();
            System.out.println("Now it's your turn to choose. Good Luck!");
            System.out.println();

            //2. PLAYER MOVE

            //input
            String userMove;

            // loop until the user chooses the correct move
            while(true) {
                System.out.println("Please choose your move from these available moves : 'Rock' 'Paper' 'Scissors' ");
                System.out.println("Enter the move you chose : ");
                userMove = scn.nextLine().toLowerCase();

                // checking if user's move is one of the available moves or not
                if(userMove.equals("rock") || userMove.equals("paper") || userMove.equals("scissors")){
                    System.out.println();
                    break;
                }

                // if user didn't enter a valid input
                System.out.println();
                System.out.println("Invalid Move!!");
                System.out.println("Please enter the move from the available moves only!");
                System.out.println();
            }

            //printing what computer chose
            System.out.println("Computer chose : " + computerMove);

            //3. COMPARING THE MOVES & DECIDING THE WINNER

            // checking for a tie

            if(userMove.equals(computerMove)) {
                System.out.println("Its a tie!");
            }

            //checking for all other moves possible

            else if(userMove.equals("rock")) {

                if(computerMove.equals("paper")) {
                    System.out.println("Computer won!");
                    System.out.println("Better luck next time!");
                }
                else if(computerMove.equals("scissors")) {
                    System.out.println("You won!");
                    System.out.println("Congratulations!");
                }
            }

            else if(userMove.equals("paper")) {

                if(computerMove.equals("rock")) {
                    System.out.println("You won!");
                    System.out.println("Congratulations!");
                }
                else if(computerMove.equals("scissors")) {
                    System.out.println("Computer won!");
                    System.out.println("Better luck next time!");
                }
            }

            else if(userMove.equals("scissors")) {

                if(computerMove.equals("paper")) {
                    System.out.println("You won!");
                    System.out.println("Congratulations!");
                }
                else if(computerMove.equals("rock")) {
                    System.out.println("Computer won!");
                    System.out.println("Better luck next time!");
                }
            }

            System.out.println();
            String playAgain;
            System.out.println("Do you want to play again? ");

            // loop until the user chooses the correct option
            while(true) {

                System.out.println("Type 'yes' or 'no' ");
                playAgain = scn.nextLine().toLowerCase();

                if(playAgain.equals("yes") || playAgain.equals("no")) {
                    System.out.println();
                    System.out.println("*****************************************************************************");
                    System.out.println();
                    break;
                }
                System.out.println();
                System.out.println("Invalid Input");
                System.out.println();
            }

            if(playAgain.equals("no")) {
                break;
            }
        }
    }
}
```
