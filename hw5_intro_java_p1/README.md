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
